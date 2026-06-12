---
title: "Add library to .click package"
date: 2015-04-02
forum: Ubuntu Application Development
---

### Post by mkamenjak on 2015-04-02
I am developing an app in qml with the SDK.And I am using a library that is not used in the SDK,let's say this one:
import QtQuick.Dialogs 1.0

And I also want to use:
```
FileDialog {
        id: fileDialog
        title: "Please choose a file(.mp4)"
        Component.onCompleted: visible = true
    }
```
Now my questions are where can I find the library on my laptop and how do I import it into the click package and into the actual code?

---

