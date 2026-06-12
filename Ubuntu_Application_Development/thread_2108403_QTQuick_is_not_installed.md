---
title: "QTQuick is not installed"
date: 2013-01-24
forum: Ubuntu Application Development
---

### Post by cg40k on 2013-01-24
So doing the Ubuntu App Developer tutorial and get
[B]
file:///home/chris/CurrencyConverter/CurrencyConverter.qml:1:1: module "QTQuick" is not installed 
     import QTQuick 2.0 [/B]

after I run this

```
import QTQuick 2.0
import Ubuntu.Components 0.1

Rectangle {
    id:root
    width: units.gu(60)
    height: units.gu(80)
    color: "lightgray"

    property real margins: units.gu(2)
    property real buttonWidth: units.gu(9)

    Label {
        id: title
        ItemStyle.class: "title"
        text: i18n.tr("Currency Converter")
        height: contentHeight + root.margins
        anchors {
            left: parent.left
            right: parent.right
            top: parent.top
        }
    }
}

```

So I know I need QTQuick 2.0, but cant seem to figure out how to get it. I followed the instructions on the UbuntuAppDeveloper Tutorial, but still get this. Wondering if any could help.

---

### Post by hortonew on 2013-04-09
Are you sure you're not importing another library that imports QtQuick 1.1?  That's what I ran into when I was following some other users tutorial.  It called an external library called JSONListModel, which had "import QtQuick 1.1" in it.  I changed that to "import QtQuick 2.0" and it fixed my issue.

If you are not importing something external, then I'm not sure what it could be.

---

