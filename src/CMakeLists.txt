qt4_wrap_ui(SOURCES_UI_H mainwindow.ui addtransformdialog.ui additemdialog.ui)
add_subdirectory(plugins)
include_directories(${CMAKE_CURRENT_BINARY_DIR}) #to be able to include ui_mainwindow.h
rock_library(envire_visualizer 
             MOC     EnvireVisualizerWindow.hpp
                     EnvireGraphVisualizer.hpp
                     TransformModel.hpp
                     DoubleSpinboxItemDelegate.hpp
                     AddTransformDialog.hpp
                     AddItemDialog.hpp
                     ItemTableModel.hpp
                     ItemManipulatorWidget.hpp
             HEADERS Vizkit3dPluginInformation.hpp
                     Helpers.hpp
                     EnvireVisualizerWindow.hpp
                     EnvireGraphVisualizer.hpp
                     TransformModel.hpp
                     DoubleSpinboxItemDelegate.hpp
                     AddTransformDialog.hpp
                     AddItemDialog.hpp
                     ItemTableModel.hpp
                     plugins/ItemFactoryInterface.hpp
                     ItemManipulatorWidget.hpp
                     ${SOURCES_UI_H}
             SOURCES EnvireGraphVisualizer.cpp
                     Vizkit3dPluginInformation.cpp
                     TransformModel.cpp
                     DoubleSpinboxItemDelegate.cpp
                     AddTransformDialog.cpp
                     AddItemDialog.cpp
                     ItemTableModel.cpp
                     EnvireVisualizerWindow.cpp
                     ItemManipulatorWidget.cpp
                     ${SOURCES_MOC}
                     #add ui files to create a dependency and regen if the ui changes
                     mainwindow.ui 
                     addtransformdialog.ui
                     additemdialog.ui
             DEPS envire_visualizer_pcl_plugin
                  envire_visualizer_smurf_plugin
             DEPS_PKGCONFIG vizkit3d envire_core envire_2D_structure_widget
             DEPS_PKGCONFIG base-lib)    
             
rock_executable(envire_visualizer_bin
                SOURCES VisualizerMain.cpp
                DEPS envire_visualizer
)
             
