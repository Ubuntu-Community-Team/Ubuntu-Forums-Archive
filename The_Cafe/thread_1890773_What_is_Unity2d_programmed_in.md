---
title: "What is Unity2d programmed in?"
date: 2011-12-04
forum: The Cafe
---

### Post by keithpeter on 2011-12-04
Hello All

[http://irclogs.ubuntu.com/2011/11/23/%23ubuntu-classroom.html#t15:00](http://irclogs.ubuntu.com/2011/11/23/%23ubuntu-classroom.html#t15:00)

at around 15:28 there is the following question and answer (thanks to bodhi.zen for quoting this log in another thread).

> **Andy80** asked: taking in consideration all the improvements incoming to Qt (with the release of Qt5), since we could have the same (or even better) effetcs in QML than we have now in Unity-3D, all of this maintaining the compatibility with non-3D computers, don't you think that keep developing two versions of Unity is a "waste" of resources? Would not be better to concentrate the effort just on the QML/Qt version of Unity?

> **sabdfl**: could be, andy. the unity-3d team need to show that it's worth keeping both versions in play, and the -2d team need to show they can deliver the slick vision we have for unity	think of it as a bit of a race. contribute where you think you can make the biggest impact

Is Unity 2d programmed in QML/Qt?

[http://www.jonobacon.org/2011/12/04/ubuntu-and-qml/](http://www.jonobacon.org/2011/12/04/ubuntu-and-qml/)

QML looks interesting for small 'app' development.

---

### Post by smellyman on 2011-12-04
qt

---

### Post by BrokenKingpin on 2011-12-05
Yes, it is developed in QT. I stated above, I really don't get managing two separate code bases for 2D/3D when QT can do it all. They should drop the 3d version and just add the effects to the 2D version with QT.

---

### Post by collisionystm on 2011-12-05
I was doing benchmarks with glxgears with DE's and i found Unity 2D to be the slowest out of all of them. Even KDE with graphics  turned on churned out twice the FPS

---

### Post by kio_http on 2011-12-05
> **collisionystm said:**
> I was doing benchmarks with glxgears with DE's and i found Unity 2D to be the slowest out of all of them. Even KDE with graphics  turned on churned out twice the FPS

At the moment although Gnome 3 uses less memory, KDE 4 performs much better for me.

---

### Post by screaminj3sus on 2011-12-05
Managing to totally different implementations for unity is pointless extra work. We should have one unity codebase that can handle 3d and 2d.

---

### Post by collisionystm on 2011-12-05
> **screaminj3sus said:**
> Managing to totally different implementations for unity is pointless extra work. We should have one unity codebase that can handle 3d and 2d.


The only thing that makes any kind of difference between 2D and 3D is the aero snap feature.

There is nothing else that makes 3D even worth it. Compiz is just a hog. Its a shame the 'aero snap' feature cant be simplified to not even need compiz

---

### Post by keithpeter on 2011-12-05
Hello All

I appreciate the need to perhaps focus resources and eliminate support for two sets of libraries.

@collisionystm

Any ideas why Unity 2d is slow compared with others? Is it an issue with the qt library or simply to do with the choice of algorithm made by the Unity programmers?

I do admit that I find Unity 2d 'snappier' on most of the hardware I use. I also prefer the alt-tab behaviour in 11.10.

---

### Post by screaminj3sus on 2011-12-05
> **collisionystm said:**
> The only thing that makes any kind of difference between 2D and 3D is the aero snap feature.

There is nothing else that makes 3D even worth it. Compiz is just a hog. Its a shame the 'aero snap' feature cant be simplified to not even need compiz

Does unity 2d have any compositing? For me compositing -is- worth it. Animations are something I expect to be there, and more importantly compositing eliminates tearing when scrolling, moving windows ect...

Also I believe in 12.04 we are supposed to finally have anti-aliased window borders via compiz which sounds like a small thing, but is an important part of the look and feel thats been neglected for too long IMO.

I do agree compiz has gotten piggish though. Has anyone noticed that recent versions of compiz (since 0.9.x) has been getting SLOWER? On all the hardware I've tested compiz 0.8.x is significantly more responsive and generally works better, and window resizing in normal mode also works properly (its horribly laggy in newer compiz versions, I have to use rectangle or stretch). I've been super disappointed with compiz performance lately, gnome 3's mutter seems much more responsive, and ironically they ditched mutter for compiz because it was too slow lol...

---

### Post by jjex22 on 2011-12-05
I'm very new to programming - I've been teaching myself C++ for 6 months in my spare time, so I'm very basic (Basically I'm warning you that my next statement may well be foolish), so I was also wondering why 2d is in QT, but the default 3d is in GTK+. Is it because GTK+ 3.x is currently less stable than QT 4.7? so that 2d is like a back up? or is it just that QT is better suited? 

(Also am I making a mistake in assuming the stability's of Gnome 3.2 and KDE 4.7 are directly related to GTK+ 3.2 and QT 4.7 .. or is this unrelated?)

---

### Post by screaminj3sus on 2011-12-05
> **jjex22 said:**
> I'm very new to programming - I've been teaching myself C++ for 6 months in my spare time, so I'm very basic (Basically I'm warning you that my next statement may well be foolish), so I was also wondering why 2d is in QT, but the default 3d is in GTK+. Is it because GTK+ 3.x is currently less stable than QT 4.7? so that 2d is like a back up? or is it just that QT is better suited? 

(Also am I making a mistake in assuming the stability's of Gnome 3.2 and KDE 4.7 are directly related to GTK+ 3.2 and QT 4.7 .. or is this unrelated?)

The current unity3d is implemented as a compiz plugin, not GTK3. Unity 2d doesn't use compiz (as its meant to be a 2d fallback) and is implemented via QT.

---

### Post by jjex22 on 2011-12-05
> **screaminj3sus said:**
> The current unity3d is implemented as a compiz plugin, not GTK3. Unity 2d doesn't use compiz (as its meant to be a 2d fallback) and is implemented via QT.

Thanks for clearing that up screaminj3sus! I think I'm still struggling with how the Unity shell relates to gnome  - I can get round it in my head, but as all things with programming languages and code, I'm very much out of my depth; 1 year of computer classes at high school taught us to use MS Office and Paint - everything you'll ever need!  

Still working to correct that knowledge gap slowly - I can only afford an average of 45mins of coding a day, (realistically equates to 3 hours of learning something new on a sunday afternoon, and a few bits of playing with it during the week :D

Edit: had a fun flashback - The school had got a newer version of office.. I'd guess at 97 (though could have been 95).. so the IT teacher not only let us have the old version but also use their computers to copy the floppies between the three of us - joke was on us they'd only run on NT machines, but still, can't imagine a school these days allowing you to clone microsoft disks on their machines!

---

### Post by screaminj3sus on 2011-12-05
> **jjex22 said:**
> Thanks for clearing that up screaminj3sus! I think I'm still struggling with how the Unity shell relates to gnome  - I can get round it in my head, but as all things with programming languages and code, I'm very much out of my depth; 1 year of computer classes at high school taught us to use MS Office and Paint - everything you'll ever need!  

Still working to correct that knowledge gap slowly - I can only afford an average of 45mins of coding a day, (realistically equates to 3 hours of learning something new on a sunday afternoon, and a few bits of playing with it during the week :D

Basically Unity and Gnome-Shell are different shells that are running on top of the base gnome 3 libraries. Gnome 2's shell was the gnome-panel/metacity.

Unity runs on top of gnome 3 as a compiz plugin. I know compiz is c++, but I'm not totally sure on the rest of the languages and technologies they've used. Gnome-shell is implemented using mostly javascript and css, and using the "mutter" window manager/compositer.

---

### Post by jjex22 on 2011-12-05
> **screaminj3sus said:**
> Basically Unity and Gnome-Shell are different shells that are running on top of the base gnome 3 libraries. Gnome 2's shell was the gnome-panel/metacity.

Unity runs on top of gnome 3 as a compiz plugin. I know compiz is c++, but I'm not totally sure on the rest of the languages and technologies they've used. Gnome-shell is implemented using mostly javascript and css, and using the "mutter" window manager/compositer.

Thanks again screaminj3sus! That's what I love about these forums, I learn something new every day :)

---

### Post by capink on 2011-12-06
The thing that puzzles me is why didn't they create unity in top of gnome-shell using its extension system? It would have much less effort and easier to maintain.

---

### Post by Paqman on 2011-12-06
> **capink said:**
> The thing that puzzles me is why didn't they create unity in top of gnome-shell using its extension system? It would have much less effort and easier to maintain.

Unity was originally a project for a hardware vendor (for a project that seems to have never launched) and has been around for quite a while. At the time they were developing Unity Gnome Shell was still a long way away from being a stable target, and there was a difference of opinion between Ubuntu and Gnome about some of the choices of technology that Gnome Shell was built with. So Ubuntu went and did their own thing instead.

---

