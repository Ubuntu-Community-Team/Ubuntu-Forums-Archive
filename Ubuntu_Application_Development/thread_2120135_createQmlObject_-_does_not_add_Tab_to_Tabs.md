---
title: "createQmlObject - does not add Tab to Tabs"
date: 2013-02-25
forum: Ubuntu Application Development
---

### Post by morchuboo on 2013-02-25
I have the following snippet from my qml app. Can anyone explain why the second tab does not show. There is no error reported.

```
    Tabs {
        id: tabs
        anchors.fill: parent
        Component.onCompleted: {
        mainView.initializeDB();
        var feedTab = Qt.createQmlObject('import QtQuick 2.0;import Ubuntu.Components 0.1;Tab {anchors.fill: parent;objectName: "Tab";title: i18n.tr("Tab");page: Page {anchors.margins: units.gu(2);Column {anchors.centerIn: parent;Label {id: label;objectName: "label";text: i18n.tr("Tab");}}}}',tabs,"feedTab");
        }
        
        Tab {
            id: tabFrontPage
            objectName: "tabFrontPage"
            
            title: i18n.tr("Front Page")
            
            // Tab content begins here
            page: Page {
                Column {
                    anchors.centerIn: parent
                    Label {
                        id: labelFrontPage
                        text: i18n.tr("This will be the front page \n An aggregation of the top stories from each feed")
                    }
                }
            }
        }
    }
```

---

### Post by mhall119 on 2013-02-25
Tabs contains a VisualItemModel called tabsModel,so maybe you need to use tabs.tabsModel as the parent object?

---

### Post by morchuboo on 2013-02-26
> **mhall119 said:**
> Tabs contains a VisualItemModel called tabsModel,so maybe you need to use tabs.tabsModel as the parent object?

I tried tabs.__tabsModel (as well as tabs.__tabs) but same issue - no error reported and no additional tab...

---

### Post by morchuboo on 2013-02-27
See my question on askubuntu:
[http://askubuntu.com/questions/261489/dynamically-adding-tab-to-tabs]("http://askubuntu.com/questions/261489/dynamically-adding-tab-to-tabs")
VisualItemModel, upon which Tabs component is implemented does not currently support appending so cannot be done.
My workaround is to generate the whole Tabs collection in a function. Messy but works until functionality is added upstream.

---

