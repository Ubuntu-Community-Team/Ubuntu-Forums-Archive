---
title: "[Python] Qt4 based program in System tray and Unity"
date: 2012-08-20
forum: Ubuntu Dev Link Forum
---

### Post by BigBen93 on 2012-08-20
Hi

I'm trying write program who will appear in system tray, but it doesn't work. On my friend's computer with KDE it works without problem. How can I add my program to Unity System Tray using PyQT4/PySide?

Here is example code, who works on KDE:

```

import sys
from PyQt4 import QtCore
from PyQt4 import QtGui


class SystemTrayIcon(QtGui.QSystemTrayIcon):
    def __init__(self, parent=None):
        QtGui.QSystemTrayIcon.__init__(self, parent)

        self.setIcon(QtGui.QIcon("icon.jpg"))

        self.iconMenu = QtGui.QMenu(parent)
        appabout = self.iconMenu.addAction("About")
        appexit = self.iconMenu.addAction("Exit")
        self.setContextMenu(self.iconMenu)

        self.connect(appabout,QtCore.SIGNAL('triggered()'),self.showAbout)
        self.connect(appexit,QtCore.SIGNAL('triggered()'),self.appExit)

        self.show()


    def showAbout(self):
        QtGui.QMessageBox.information(QtGui.QWidget(), self.tr("About Tunarium"), self.tr("Your text here."))

    def appExit(self):
        sys.exit()

if __name__ == "__main__":
    app = QtGui.QApplication(sys.argv)

    trayIcon = SystemTrayIcon()
    trayIcon.show()

    sys.exit(app.exec_())

```

THX for any help.

---

