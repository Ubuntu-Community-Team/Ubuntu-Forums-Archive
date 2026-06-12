---
title: "Slight interest in developing for Ubuntu Mobile, but where do I begin?"
date: 2013-02-23
forum: Ubuntu Application Development
---

### Post by Espionage724 on 2013-02-23
To put it simply, I have no useful coding experience (I coded a C++ calculator years ago, that's about it), but I am interested in trying to learn how to start developing for Ubuntu Mobile (I have a Nexus 10 tablet).

Is there any guides or something for a **total** beginner?

I'm also looking for a bit more info on QML. Is it mobile-specific, or can apps made with it also work on Desktop? Can 2d/3d apps be created with QML, or is it mainly for interfaces?

---

### Post by morchuboo on 2013-02-26
The best starting place for ubuntu mobile apps would be [http://developer.ubuntu.com/get-started/gomobile/]("http://developer.ubuntu.com/get-started/gomobile/").
Once you have the SDK installed you can begin experimenting with QML.
QML is not mobile specific. It is part of Qt under QtQuick. You can develop applications for desktop or anywhere else Qt runs. For general learning of Qt Quick this looks a good place to start: [http://qt-project.org/wiki/Developer-Guides#7f78a82c525d6a17d477021eaed1ead3]("http://qt-project.org/wiki/Developer-Guides#7f78a82c525d6a17d477021eaed1ead3").
Finally be aware that some of the tutorials and examples around the web are for Qt Quick 1 which while will still be useful to learn about declarative programming, ubuntu mobile uses Qt Quick 2 that is part of Qt5 so choose those tutorials if you can.

Dont worry about having little experience, we all started somewhere with a desire to "get into" something. There are plenty of people who will help you out (visit #ubuntu-touch IRC channel among others). 
Also developing with Qt Quick is very different from traditional imperative programming - something im wrapping my noodle around now...

---

