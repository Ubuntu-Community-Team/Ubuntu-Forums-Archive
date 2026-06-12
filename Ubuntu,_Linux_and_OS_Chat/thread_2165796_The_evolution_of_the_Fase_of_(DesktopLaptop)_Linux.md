---
title: "The evolution of the Fase of (Desktop/Laptop) Linux OS - Question(s)?"
date: 2013-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Nikolai D. on 2013-08-06
Hi there,

I was wondering,

With the recent news mentioning the move of Unity interface to Qt libs making it Unity Next.
And since KDE is written in Qt to, and most of the software that would be included in lets say in Kubuntu would be Qt based to.
This looks to me like its a good move for lets say KDE. Making it all more uniform. Isnt it?
(im actually pretty much interested how this would evaluate)

But then, there are news on those two different other things. Where GUIs rely on. The Wayland and Mir. What is there so different about Mir that KDE team is being concerned about? I mean lets say Ubuntu moves to Mir. And Kubuntu want to use Wayland. Wouldnt that be possible? To just use both of them on a new Ubuntu?

p.s. And another interesting thing. Why is it nowadays popular to move to Qt? Is that because Qt is now completely free? And there is kind of no need for Gtk anymore? Like it was before. What is the place of Gtk then after that?
I mean if it works, why fix it?

I would really appreciate comments on what you know/think about this topics.

Thank you,
Nikolai

---

### Post by Irihapeti on 2013-08-06
*Not a request for support. Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by lykwydchykyn on 2013-08-07
> **Nikolai D. said:**
> 
p.s. And another interesting thing. Why is it nowadays popular to move to Qt? Is that because Qt is now completely free? And there is kind of no need for Gtk anymore? Like it was before. What is the place of Gtk then after that?
I mean if it works, why fix it?


Qt is a great set of libraries, very mature now and has a good history on mobile platforms; it was owned by Nokia for several years, after all.  This likely factors in to Ubuntu's interest in it, but honestly at this point it's just more mature than Gtk3.  It also has a new "sub-language" called QML that makes GUI development more like working with HTML5, which is awesome for mobile development.

The one doesn't completely displace the other, though.

Qt is not just a GUI library; it has core classes like strings and numeric objects, network access classes, database drivers, threading libraries, audio, etc.  GTK is more of just a gui library.

Qt is also C++ based; it has bindings for other high-level languages like python, ruby, javascript, etc, but I'm not sure it's even possible to  write Qt applications in C.  GTK is based on C, which is still popular with a lot of FOSS guys.

There's also a whole heck of a lot of code written for both; one doesn't just port software between GUI libraries in a weekend.

Qt and GTK just basically take a different approach to a lot of things, and many developers find that one library or another just clicks with them.

---

### Post by grahammechanical on 2013-08-07
To understand the direction Ubuntu is going you need to think beyond the desktop and understand what Canonical means when it speaks of a convergence strategy. See what one of MIR's developers says about why MIR is being developed.

[http://www.olli-ries.com/mir-unity-qml-unity-apis-unity/](http://www.olli-ries.com/mir-unity-qml-unity-apis-unity/)

And Mark Shuttleworth

[http://www.markshuttleworth.com/archives/1269](http://www.markshuttleworth.com/archives/1269)

AS for the KDE developers you best ask them about it. Have you?

[http://community.kde.org/KWin/Wayland](http://community.kde.org/KWin/Wayland)

Do not expect too much from KDE and Wayland. Note these comments.

> Another reason is that the KWin development team does not have the  manpower to maintain an independent X11 window manager and a Wayland  compositor. Starting a new Wayland compositor would mean to stop the  work on the X11 window manager, which would be a bad move as we cannot  know yet whether Wayland will succeed and will be supported on all  hardware. Also in future KDE will have to provide an X11 window manager.

> Writing a new Wayland Compositor would require to rewrite the complete  X11 workspace in one go. This includes not only the Window Manager, but  also parts of Plasma, KDM, Screen Locker and many, many more. This would  take a long development time and the transition would not be smooth,  very likely buggy and with regressions like the 4.0 introduction. We do  not want to break the desktop!

It seems to me that KDE will have a harder time moving completely to Wayland than Kubuntu will have using MIR. I am already running Kubuntu on Xmir. The platform is stable. There are issues. which is to be expected from development code but the platform is stable and usable.

Regards.

---

### Post by Nikolai D. on 2013-08-20
What is very interesting that i have recently discovered. 
Im studying some C sharp now. (dont ask why :D ) And a friend who is already further then i am in C sharp was asking if i knew what GDI+ was. So i have read about it somewhat here [http://en.wikipedia.org/wiki/Graphics_Device_Interface](http://en.wikipedia.org/wiki/Graphics_Device_Interface)
And while reading about it i discovered that the GDK actually is replaced by Cairo for some time already. [http://en.wikipedia.org/wiki/GDK](http://en.wikipedia.org/wiki/GDK)
Because recently i was thinking that now that Qt is completely open sourced by Nokia and is superior to the hack named GDK it would be logical to move on to Qt. And GTK is kinda less relevant.
But it looks like Cairo is maybe even technologically superior somewhat somewhere. And not an old hack that GDK is.
And actually since the Qt is still kind of dual licensed. The fact that Nokia open sourced it makes it better. Ideologically maybe. But there still stays some licensing disagreements. (between the Qt and GTK camps)
So basically nothing has changed. GTK is still ideological alternative to the technological Qt.
As i see it at least.
Here is another interesting question about this things
[http://ubuntuforums.org/showthread.php?t=2169014](http://ubuntuforums.org/showthread.php?t=2169014)

have a nice day :)

---

