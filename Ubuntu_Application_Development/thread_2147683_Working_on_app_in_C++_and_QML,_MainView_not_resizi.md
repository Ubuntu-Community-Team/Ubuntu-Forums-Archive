---
title: "Working on app in C++ and QML, MainView not resizing with window"
date: 2013-05-22
forum: Ubuntu Application Development
---

### Post by KoRnKloWn on 2013-05-22
OK, so I was working on an app in GTK3, but for various reasons I  decided to switch it to Qml, with how it was going my GUI needed a huge  overhaul anyways, and I really want my app to work across all Ubuntu  form factors when they are available. So, the main section of my app is  in C, I already figured out how to mix it with Qml, I just created a  little C++ Qt wrapper, simple enough, so far so good.

OK, now,  the issue I'm currently having is having it style correctly for the  desktop, specifically, when I resize the main window, none of the  contents resize with it, I'm assuming it's the MainView component that's  keeping it's size and not allowing it to resize with the window,  however there's basically no documentation on the MainView.

Here's my Qml file:
```

import QtQuick 2.0
import Ubuntu.Components 0.1
import Ubuntu.Components.ListItems 0.1 as ListItem

import QmlConnect 1.0

MainView {
    objectName: "mainView"
//    applicationName: "MyApp"
    id: root
    
    width: units.gu(100)
    height: units.gu(80)
    
    property real margins: units.gu(2)
    property real buttonWidth: units.gu(9)
    
    /* Instantiate QmlConnect */
    QmlConnect {
        id: qmlConnect
        onDataListChanged: {
            console.log("DATA LIST CHANGED\n");
        }
    }
    
    /* Leftmost column for library and data lists */
    Column {
        id: libraryColumn
        ListItem.Header {text: "Library"}
        ListItem.Standard {text: "Title1"}
        ListItem.Standard {text: "Title2"}
        ListItem.Divider {}
        ListItem.Header {text: "Title3"}
    
        width: units.gu(10)
        anchors {
            left: parent.left
            top: parent.top
            bottom: parent.bottom
        }
    }

    /* Model used to store data */
    ListModel {
        id: myModel
        // Load data into model
        Component.onCompleted: {
            var data_list = qmlConnect.getDataList();
            for(var i = 0; i < data_list.length; i++) {
                var thumb_path = qmlConnect.confDir + "/thumbnails/" + data_list[i]["Group"] + 
                        " - " + data_list[i]["Title"] + ".jpg";
                myModel.append({
                    thumbnail: thumb_path,
                    path: data_list[i]["Title"]
                });
                console.log(data_list[i]["Title"]);
            }
        }
    }

    /* Delegate for displaying data in GridView */
    Component {
        id: browserDelegate
        Item {
            width: browserGrid.cellWidth
            height: browserGrid.cellHeight
            Column {
                anchors.fill: parent
                Image {
                    id: cover
                    source: encodeURIComponent(thumbnail)
                    sourceSize.width: units.gu(16)
                    sourceSize.height: units.gu(25)
                    anchors.horizontalCenter: parent.horizontalCenter
                }
                Text {
                    id: caption
                    text: path
                    width: cover.width
                    wrapMode: Text.Wrap
                    elide: Text.ElideLeft
                    horizontalAlignment: Text.AlignHCenter
                    anchors.horizontalCenter: parent.horizontalCenter
                }
            }
        }
    }

    /* Grid view used to display data */
    GridView {
        id: browserGrid
        model: myModel
        cellWidth: units.gu(25)
        cellHeight: units.gu(35)
        anchors {
            left: libraryColumn.right
            right: parent.right
            top: parent.top
            bottom: parent.bottom
        }
        delegate: browserDelegate
    }
}

```

As  you can see I'm trying to develop a library app, I changed some names  of things in this post as to not totally give  away what I'm working on, if I manage to finish this app I'd like it to  be somewhat a surprise ;P if I accidentally missed a bracket or  something in my copy/paste please ignore that, my app is working fine, I  have no bugs so-to-speak, I just need help getting my app to style  correctly for the desktop. I need the contents to resize with the  window, that's the imediate issue I'm having.

---

### Post by KoRnKloWn on 2013-05-23
Well, I found an answer to my own question. The problem was I was  assuming this was associated with Qml, when it was actually the  QQuickView, which I am using to connect my Qml GUI to the rest of my  app. All I needed to do was set the QQuickView's resize mode as so: 
```

//  Prepare QT C++ for import in QML
     qmlRegisterType("QmlConnect", 1, 0, "QmlConnect"); // Set QML source
     view.setSource(QUrl::fromLocalFile(bin_dir + "/gui.qml"));
     view.setResizeMode(QQuickView::SizeRootObjectToView); // Right here we set the MainView (root) to resize with the window :D
     view.show();

```

---

### Post by KoRnKloWn on 2013-05-23
[s]Of course I realize now I really didn't name this thread correctly -_-
I was very tired when I started it, should have labled it "Using C++ & Qml, MainView will not resize with window", or something along those lines...
If anyone happens upon this that knows how to rename threads please do tell.[/s]

**UPDATE:** Nevermind :P

---

