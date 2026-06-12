---
title: "MEIZU MX4&#65292;the transparent background can't work"
date: 2016-02-05
forum: Ubuntu Phone and Tablet
---

### Post by wjk1988311 on 2016-02-05
as a new ubuntu app developer,it's difficult to use qml or js to develop app.
and now many effects written by qt can't port to ubuntu phones.
i hope one day i can use qt instead of the qml or js to develop ubuntu app.


i wrote a test program on MEIZU MX4 when MEIZU MX4 published.
transparent home screen like android does

piece of code:


import QtQuick 2.0
import Ubuntu.Components 1.1
import QtQuick.Window 2.1

Window {
    ......
    color:"transparent"
    ......
}

it worked fine.
but after system updated,it can't work.
the other parts of the code is ok ,except the root Window.

the color of the root window turns to black when set the color property to "transparent".
someone says it's caused by the qmlscene.
any solutions?

---

