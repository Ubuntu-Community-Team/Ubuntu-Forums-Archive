---
title: "QtCreator hangs upon starting in Virtualbox Ubuntu 16.04 LTS quest"
date: 2017-06-23
forum: Ubuntu Application Development
---

### Post by JGMS on 2017-06-23
Hi all,

I have installed the Ubuntu SDK (QtCreator) with all its updates, but it freezes as soon as it is started.
After deleting the QtCreator.ini file I was able to install the so-called Kits for the Ubuntu 16.04 emulator and for the Ubuntu Touch device (15.04).
I had to drag the dialog forms from behind the frozen QtCreator program to get this done. It took me some time to find that there were hidden dialogs behind the frozen panel to enter system passwords and the like. Nevertheless, despite of lot of trials, it keeps starting into death.

When I start it in the termninal I get the following messages
[INDENT][I]
jan@jan-VirtualBox:~$ ubuntu-sdk
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:26: Failed to read element \"value\"."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:57: Failed to read element \"value\"."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:100: Failed to read element \"value\"."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:143: Failed to read element \"value\"."
Running  "/usr/bin/usdk-target"
OpenGL Warning: glXCreatePbuffer not implemented by Chromium
file:///usr/ubuntu-sdk-ide/lib/Qt/qml/QtQuick/Controls/ToolBar.qml:143:9: QML Item: Binding loop detected for property "layoutHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:170:13: QML ToolBar: Binding loop detected for property "implicitHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:170:13: QML ToolBar: Binding loop detected for property "implicitHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:170:13: QML ToolBar: Binding loop detected for property "width"
qml: Page_QMLTYPE_229(0x2ebf400)"Ubuntu Publish": In Ubuntu.Components 1.3, the use of Page.title, Page.flickable and Page.head is deprecated. Use Page.header and the PageHeader component instead.
OpenGL Warning: glXCreatePbuffer not implemented by Chromium
QOpenGLFramebufferObject: Unsupported framebuffer format.
QProcess: Destroyed while process ("/usr/bin/usdk-target") is still running.
QProcess: Destroyed while process ("/usr/bin/usdk-target") is still running.
"The command \"/qmake\" could not be started."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:26: Failed to read element \"value\"."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:57: Failed to read element \"value\"."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:100: Failed to read element \"value\"."
"Warning reading /home/jan/.config/QtProject/qtcreator/profiles.xml:143: Failed to read element \"value\"."
file:///usr/ubuntu-sdk-ide/lib/Qt/qml/QtQuick/Controls/ToolBar.qml:143:9: QML Item: Binding loop detected for property "layoutHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:238:25: QML ToolBar: Binding loop detected for property "implicitHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:238:25: QML ToolBar: Binding loop detected for property "implicitHeight"
file:///usr/ubuntu-sdk-ide/lib/Qt/qml/QtQuick/Controls/ToolBar.qml:143:9: QML Item: Binding loop detected for property "layoutHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:238:25: QML ToolBar: Binding loop detected for property "implicitHeight"
file:///usr/ubuntu-sdk-ide/share/qtcreator/ubuntu/qml/DevicesPage/DevicePage.qml:238:25: QML ToolBar: Binding loop detected for property "implicitHeight"
QTextCursor::setPosition: Position '153' out of range
QOpenGLFramebufferObject: Unsupported framebuffer format.
/usr/bin/ubuntu-sdk: regel 6:  4370 Segmentatiefout         (geheugendump gemaakt) $BINDIR/qtcreator -platformtheme appmenu-qt5 ${1+"$@"}
jan@jan-VirtualBox:~$ [/I][/INDENT]

Could anyone give me a clue how to proceed?

Many thanks ahead.

Jan

---

