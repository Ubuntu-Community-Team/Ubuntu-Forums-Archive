---
title: "Default ecosystem for desktop application"
date: 2017-01-16
forum: Ubuntu Application Development
---

### Post by jason.jackal on 2017-01-16
Is there a default ecosystem for application develop in Unity?

I am coming from Windows, which heavily uses the .net framework and due to the latter - does Unity support a default ecosystem or API for desktop development?

Thank you
JJ

---

### Post by TheFu on 2017-01-17
Start here: [http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users)
Then ... [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Then start going crazy with the package manager looking at different packages with -dev in the name.

Guess it depends on what "Default ecosystem for desktop application" means.

In the Unix world, we have lots and lots of choices. Same stuff happens on Windows, but there isn't 1 company driving all the choices. Picking the best choice for your needs requires a little research. This doesn't prevent using other valid choices. 1, 2, 10, 20 different base libraries can be used. It just sucks up more RAM. 

If you want to be a software developer, then people usually pick between either Qt or GTK libraries.  Qt is KDE and most KDE-based applications will use the Qt libraries.  Gnome-based applications tend to use GTK or GTK+ libraries.

As for distribution of their programs/libraries, in the debian world, we use .deb files and PPAs for repositories.  These are sorta like setup.exe for Windows, but it is not usually a good idea to directly install .deb files. This is especially good advice for new-to-linux people. Doing so has repercussions that aren't always obvious for a few months. Be careful. Best to only use official repos or trusted PPAs.

---

### Post by jason.jackal on 2017-01-18
But what is the default language of choice that Cononical promotes? I understand that Qt is normally C++ (other bindings capable) and GTK/GTK+ is normally C; however, both these GUI framework libraries can be leveraged for other languages. For example: I have used GTK-Perl to build applications for CentOS and Fedora. The latter were just small desktop applications that I mainly did for myself; however, I am looking into the Ubuntu ecosystem for long term applications, which I would release for public use.

I guess what I do not get is the language used on the developer site. [https://developer.ubuntu.com/en/?_ga=1.142101874.1701471003.1484761456](https://developer.ubuntu.com/en/?_ga=1.142101874.1701471003.1484761456)

"Choose native or HTML5 and get started with the Ubuntu SDK".

I can always code a C application with GTK; however, I would not necessary go that route if I wanted to code for KDE, which runs on the Qt/C++ framework (ecosystem) - since all the general libraries are all ready installed.

Thank you

---

### Post by TheFu on 2017-01-18
Did you review those links already provided? They try to explain these differences in culture.  Linux HAS a culture.

The freedom to choose is yours. Ubuntu isn't Apple trying to force specific languages (swift/objectiveC) or MSFT wanting us to use their proprietary languages (C#, VB) and extensions (.NET).  

On Linux, both C and C++ are well supported by the community.  So is python.  I'm a Perl guy too, but haven't written any perl guy apps using the available GUI bindings. GTK+ is C++, not C, but has APIs for lots and lots of other languages [https://www.gtk.org/language-bindings.php](https://www.gtk.org/language-bindings.php) .  For webapps, I use either perl or ruby and avoid php due to my lack of knowledge on how to secure it properly.

Ubuntu doesn't make **any** of those tools.  They are created by other projects.
If I were doing a little trivial interface app over some library where performance isn't needed, then I'd probably use python (I'd have to learn the language first).  If I were writing an enterprise app, then I'd use C++.  In both cases, I'd use GTK+ for a number of reasons - some probably don't matter to most people.  There is history around Qt that I find distasteful and avoid, but many people wouldn't care. That isn't to say that KDE isn't nice.

And just to be clear, nobody here works for Canonical. We are just volunteers with opinions and sometimes facts.  I prefer cross-platform solutions when the native solution traps us for a single platform.  That often isn't important to some people.

---

### Post by jason.jackal on 2017-01-18
I understand completely what you are saying about selecting the language that you are familiar with; however, you still not have answered my question and confusion about the HTML5 or the SDK that is mentioned on the Ubuntu Development link. You have just pointed out that a number of languages can be used, which can be argued "that is the benefit of Linux/Unix". Due to the latter, that is why I am confused at the software path provided by Ubuntu with the SDK and HTML5 application development.

I don't want to argue; however, GTK+ is the current name of the GTK project. GTK is deprecated, and GTK+ is the new name, and GTK/GTK+ is still C default; however it will do C++ with the GTKmm bindings, that is support in GNOME, but that is not the point. What is the point... does Ubuntu at a company Canonical promote the SDK/HTML5 over other languages?

---

### Post by jason.jackal on 2017-01-18
I found what i was looking for.

[https://developer.ubuntu.com/en/phone/apps/qml/tutorials/building-your-first-qml-app/](https://developer.ubuntu.com/en/phone/apps/qml/tutorials/building-your-first-qml-app/)

So they use the Qt framework, thus C++ hooked in code if required.

---

### Post by TheFu on 2017-01-18
Happy you found what you wanted. Didn't see that you cared about the phone/tablet stuff.  Just be aware that "paused" is the state of development for those other devices. [http://www.omgubuntu.co.uk/2017/01/shooting-the-messenger](http://www.omgubuntu.co.uk/2017/01/shooting-the-messenger)

Unity is just a GUI, not the OS. There are many different desktops for all Linux systems.  Most of the Linux users I know do NOT use Unity and I'm a LUG organizer.

Found this enlightening: [https://askubuntu.com/questions/447091/difference-between-qt-creator-and-ubuntu-sdk](https://askubuntu.com/questions/447091/difference-between-qt-creator-and-ubuntu-sdk) 

Guess it just depends on how tightly integrated/dependent on the default Ubuntu desktop you want to be?

---

### Post by ian-weisser on 2017-01-18
> **jason.jackal said:**
> So they use the Qt framework, thus C++ hooked in code if required.

That's what some developers are using this year for converged (desktop and phone) GUIs that run in Unity 8.
In the past, lots of Canonical applications were written in Python and C, some in Go and Vala and Perl. Languages go in and out of fashion.

---

