project(qt_common)

QT5_ADD_RESOURCES(RESOURCES res/resources_common.qrc)

set_property(SOURCE qrc_resources_common.cpp PROPERTY SKIP_AUTOGEN ON)

set(SRC
  helpers.cpp
  helpers.hpp
  map_widget.cpp
  map_widget.hpp
  proxy_style.cpp
  proxy_style.hpp
  qtoglcontext.cpp
  qtoglcontext.hpp
  qtoglcontextfactory.cpp
  qtoglcontextfactory.hpp
  scale_slider.cpp
  scale_slider.hpp
  spinner.cpp
  spinner.hpp
)

omim_add_library(${PROJECT_NAME} ${SRC} ${RESOURCES})

set_target_properties(${PROJECT_NAME} PROPERTIES AUTOMOC ON)

target_compile_options(${PROJECT_NAME}
  PRIVATE
    $<$<CXX_COMPILER_ID:AppleClang,Clang>:-Wno-shorten-64-to-32>
    -Wno-deprecated-declarations
)

target_link_libraries(${PROJECT_NAME}
  map
  Qt5::Gui
  Qt5::Widgets
)
