---
title: "[xubuntu] Qt5 location missing"
date: 2020-05-10
forum: Ubuntu Application Development
---

### Post by msauer75 on 2020-05-10
Hi,

some days ago I changed my linux to Xubuntu and I have a problem with my own developed programme (Qt5 / QML application). I used the Qt5 packages delivered with xubuntu. In Qt Creator I will get the following error messages

```

Project ERROR: Unknown module(s) in QT: location
Project ERROR: Unknown module(s) in QT: quick quickcontrols2 location

``` 

I use this option in my qmake project file:

```

QT          += core location

```


I installed all qt5 related location package:


[LIST]
[*]libqt5location5
[*]libqt5location5-plugin-mapboxgl
[*]libqt5location5-plugins
[/LIST]

Which packet I have to install, that I can compile my programme?

Thank you for your help
BR
martin

---

### Post by psabpisal on 2020-08-13
You could use Synaptic Package Manager to install Qt 5 Creator and it should work.

---

