---
title: "Qt Creator - module &quot;Ubuntu.WebApps&quot; is not installed"
date: 2016-01-03
forum: Ubuntu Application Development
---

### Post by dragonfly41 on 2016-01-03
I am trying Ubuntu SDK IDE (Qt Creator) on Ubuntu-14.04.

Installed and launched Ubuntu SDK IDE.

Created a first test html5app in Qt Creator.

After Run html5app ... encountered this error message ...

```

[COLOR=#0000aa]Starting /usr/bin/ubuntu-html5-app-launcher...[/COLOR]
[COLOR=#aa0000]Setting import path to:  /home/user/QT Creator Projects/html5app/www/../lib/i386-linux-gnu [/COLOR]
[COLOR=#aa0000]file:///usr/share/ubuntu-html5-app-launcher/qml/main.qml:21:1: module "Ubuntu.WebApps" is not installed [/COLOR]
[COLOR=#aa0000]     import Ubuntu.WebApps 0.1 [/COLOR]
[COLOR=#aa0000]     ^ [/COLOR]
[COLOR=#aa0000]Main application component cannot be loaded. [/COLOR]
[COLOR=#0000aa]/usr/bin/ubuntu-html5-app-launcher exited with code 1[/COLOR]

```

Inspected head of /usr/share/ubuntu-html5-app-launcher/qml/main.qml

```

import QtQuick 2.0
import Ubuntu.Components 0.1
import Ubuntu.WebApps 0.1

```

My QtCreator is version 3.5.0 based on Qt 5.4.2.

Another Ubuntu-14.04 user has reported same problem.

[https://bugs.launchpad.net/unity-webapps-qml/+bug/1518532](https://bugs.launchpad.net/unity-webapps-qml/+bug/1518532)

Perhaps I should post question on  Qt forum.

[https://forum.qt.io/search](https://forum.qt.io/search)

---

