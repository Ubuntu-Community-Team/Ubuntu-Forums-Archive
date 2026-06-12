---
title: "unity8 in Ubuntu 13.10 in VirtualBox"
date: 2013-09-12
forum: Virtualisation
---

### Post by catalyst1987 on 2013-09-12
Hello,
     I am currently running 13.10 in VirtualBox.  When I try to launch unity8, the QML phone shell just gives a black screen.

Has anyone else had this problem?  Here is my debug log:

unity::action::ActionManager::ActionManager(QObject*):
    Could not determine application identifier. HUD will not work properly.
    Provide your application identifier in $APP_ID environment variable.

** (process:3752): WARNING **: Unable to get a HUD proxy: Error calling StartServiceByName for com.canonical.hud: Timeout was reached
file:///usr/share/unity8/Shell.qml:712:5: QML Binding: Binding loop detected for property "target"
file:///usr/share/unity8/Hud/HudParametrizedActionsPage.qml:138:5: QML Item: Binding loop detected for property "width"
libpng error: Not a PNG file
file:///usr/share/unity8/Shell.qml:147:5: QML QQuickImage: Invalid image data: file:///usr/share/backgrounds/warty-final-ubuntu.png
file:///usr/share/unity8/Shell.qml:147:5: QML QQuickImage: Binding loop detected for property "source"
libpng error: Not a PNG file
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/MainView.qml:192:5: QML StyledItem: Binding loop detected for property "style"
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:61:20: QML QQuickImage: Failed to get image from provider: image://theme/firefox
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:61:20: QML QQuickImage: Failed to get image from provider: image://theme/firefox
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:61:20: QML QQuickImage: Failed to get image from provider: image://theme/firefox
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:61:20: QML QQuickImage: Failed to get image from provider: image://theme/preferences-system
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:61:20: QML QQuickImage: Failed to get image from provider: image://theme/preferences-system
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:61:20: QML QQuickImage: Failed to get image from provider: image://theme/preferences-system
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Icon.qml:77:5: QML Image: Failed to get image from provider: image://theme/phone-app-call-symbolic
file:///usr/share/unity8/Components/CrossFadeImage.qml:39: Unable to assign QSize to QSizeF
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/MainView.qml:250:39: Unable to assign Tabs_QMLTYPE_74 to Page_QMLTYPE_64
file:///usr/share/unity8/Components/CrossFadeImage.qml:39: Unable to assign QSize to QSizeF
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
OpenGL Warning: XGetVisualInfo returned 0 visuals for 0x326f1c0
OpenGL Warning: Retry with 0x8002 returned 0 visuals
OpenGL Warning: glXGetFBConfigAttrib for 0x326f1c0, failed to get XVisualInfo
Unrecognized OpenGL version
Unrecognized OpenGL version
OpenGL Warning: glXChooseFBConfig returning NULL, due to attrib=0xc, next=0x18
OpenGL Warning: glXChooseFBConfig returning NULL, due to attrib=0xc, next=0x18
Unrecognized OpenGL version
Unrecognized OpenGL version
file:///usr/share/unity8//Panel/Indicators/DefaultIndicatorWidget2.qml:65:17: QML QQuickImage: Failed to get image from provider: image://theme/audio-volume-low-panel,audio-volume-low,audio-volume,audio
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/folder-download,folder
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/application-x-deb,package-x-generic
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/qmlscene
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Failed to get image from provider: image://theme/applications-other
file:///usr/share/unity8/Components/Tile.qml:39:16: QML QQuickImage: Error downloading [http://i.ytimg.com/vi/seX7jYI96GE/movieposter.jpg](http://i.ytimg.com/vi/seX7jYI96GE/movieposter.jpg) - server replied: Not Found

** (process:3752): CRITICAL **: Unable to get session bus: Error calling StartServiceByName for com.canonical.hud: Timeout was reached
WARN  2013-09-12 19:16:46 unity.dash.scopeproxy ScopeProxy.cpp:611 Connection state changed for social.scope => disconnected
WARN  2013-09-12 19:16:49 unity.dash.scopeproxy ScopeProxy.cpp:611 Connection state changed for social.scope => connected
WARN  2013-09-12 19:18:19 unity.dash.scopeproxy ScopeProxy.cpp:611 Connection state changed for social.scope => disconnected
WARN  2013-09-12 19:18:22 unity.dash.scopeproxy ScopeProxy.cpp:611 Connection state changed for social.scope => connected
WARN  2013-09-12 19:19:52 unity.dash.scopeproxy ScopeProxy.cpp:611 Connection state changed for social.scope => disconnected
WARN  2013-09-12 19:19:55 unity.dash.scopeproxy ScopeProxy.cpp:611 Connection state changed for social.scope => connected

---

