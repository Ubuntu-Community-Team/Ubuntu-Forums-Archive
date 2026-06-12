---
title: "configure project : app using QTquick modules and shared libraries"
date: 2015-07-25
forum: Ubuntu Application Development
---

### Post by epsilon777 on 2015-07-25
Hi,
Is there a possibility, within ubuntu-sdk (qt-creator), to create apps with that structure :
MyProject
|
|--sharedlib1 ( use any of sharedlibrary i created )
|--sharedlib2 (use any of sharedlibrary i created )
|--sharedlib3 (use any of sharedlibrary i created )
|--qtquick2Plugin1  (use any of sharedlibrary or plugin i created )  --> use sharedlib1 in my example
|--qtquick2Plugin2  (use any of sharedlibrary or plugin i created )
|--app1 (qml app use any lib or plugin) --> use qtquick2Plugin1 and sharedlib2
|--app2 (qml app use any lib or plugin)

(no cycle in the use)

Actually I can create shared libs and modules, but when running the first app (  with : 'import "../qtquick2Plugin1" 1.0' inside), the app quit with an error message : 
...Main.qml:7 plugin cannot be loaded for module "...MyProject.qtquick2Plugin1Plugin": Impossible de charger la bibliothèque...MyProject/qtquick2Plugin1/libqtquick2Plugin1Plugin.so : (libsharedlib1.so.1: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type)
(I change the message accordingly to my example of project)


If it is not too much to ask, is somebody might  create such a "foo project", i'm stuck with those problems ( i don't want to copy my libs somewwhere manualy in order to get the build/install process clean), in a second hand is there an existing project wich is structured like that but which one...?
From my point of view it might be in the app1.qmlproject i may declare the libs but how...?

Regards.

---

