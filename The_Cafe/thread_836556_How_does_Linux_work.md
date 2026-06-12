---
title: "How does Linux work?"
date: 2008-06-21
forum: The Cafe
---

### Post by Kernel Sanders on 2008-06-21
I was thinking about this earlier. If I were to explain Windows to a n00b, i'd say:

> 
Windows has a core called a Kernel. On top of that this is all the eye candy that you see, called the GUI, or Graphical User Interface. This is called Explorer. The C: drive is your hard drive. Windows is located in the Windows folder in the C drive, all your programs are installed in the Program Files folder, and your documents folder is located in the Users folder. Some more programs and services run in the background, and Windows has a hidden registry where it keeps a list of what's installed along with some settings and configuration information.

You install a program by double clicking the .exe file and accepting the default settings if you've downloaded the file, or simple following the default settings that run automatically if you pop the CD in. This will install it into the Program Files folder we talked about earlier, and place some files in the registry and some icons in your start menu. You can uninstall a file by going to the control panel and add/remove programs, although expect some remnants of the program to remain the Program Files folder and the Registry.

Windows needs drivers in order to see and use devices. If you rightclick my computer and go to properties, device manager, you will see which has working drivers and which doesn't. You can go to the hardware manufacturers website if you need to and get drivers from there. Most of the time these will be in .exe files, so you just double click them and accept the default settings.


I'm a complete n00b myself, and even after a year or so of slowly developing my interest, I can't write a similar n00b friendly explanation of Linux :shock:

Can anyone help me with that, so that I may greater understand linux, along with the n00bs reading this thread? :)

---

### Post by Mateo on 2008-06-21
There's a mouse running on a wheel inside your computer case.

---

### Post by DrMega on 2008-06-21
> **Mateo said:**
> There's a mouse running on a wheel inside your computer case.

I read that it was a complex ant farm, where the ants are channeled down different tunnels in order to mimic complex abstract processes.

---

### Post by Ub1476 on 2008-06-21
> Linux is the kernel.

And there's many drivers built inside Linux which does so that your hardware operates correctly.

Then there's GUI, which is X.

Then there's a DE, a more advanced GUI, like GNOME and KDE.

And DEs has WM, which operates how the windows reacts and moves etc.

And there's repos, which is connected to a large server with a lot of applications. 

There comes a "packagemanager" with a distro, which can download and install applications from these repos.

How hard can it be?

---

### Post by freebeer on 2008-06-21
I wouldn't exactly say that the Windows GUI sits on top of the kernel... it's more like it's wedged into the kernel.  This is why quite often that should the GUI crash, you have to reboot Windows.

---

### Post by Kernel Sanders on 2008-06-21
Not in Vista :cool:

---

### Post by Vadi on 2008-06-21
Don't forget the CPU cooling by a penguin inside your comp.

---

### Post by stmiller on 2008-06-21
Windows is tied to the GUI. You can't have one without the other. However, Linux in its most simplistic form does not include a graphical interface. The desktop graphics part is not 'attached' to the Linux kernel.

Linux uses a monolithic kernel. It can get pretty deep, but wikipedia has good general info:

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

Linux is generally organized like this, though varies:

[http://www.slackware.com/config/rootdir.php](http://www.slackware.com/config/rootdir.php)

---

### Post by kinematic on 2008-06-21
> **Ub1476 said:**
> Then there's GUI, which is X.

X is not the gui. Xorg is the server on wich the gui or graphical app run....big difference.

---

### Post by koenn on 2008-06-21
> **Kernel Sanders said:**
> Not in Vista :cool:

Still, freebeer is right in that the Windows GUI is so much integrated with the rest of the system that you can't run Windows without the GUI (although MS made 1 version of Windows withiut GUI: Windows Server 2008 Core, meant as a virtualization platform. I doubt it's useful for anything else, as most Windows applications, even on servers,  *need* a GUI to be functional)
X, on the other hand, runs as any other application on Linux : you can stop and start it at will, you can uninstall it, you can replace it by an other application with similar functiionality, and so on.

---

### Post by richardjennings on 2008-06-21
Following your guidelines:

Gnu Linux is an operating system that combines the Linux kernel with a set of tools written by the GNU project. The Linux kernel and the tools installed can be customised and expanded to serve different requirements. In Ubuntu, the Xorg server and Gnome windows manager provide a graphical user enviroment. Support for hardware is either written into the Linux kernel, or can be provided as a module.

---

### Post by koenn on 2008-06-21
> **kinematic said:**
> X is not the gui. Xorg is the server on wich the gui or graphical app run....big difference.

Not exactly. 
X provides the infrastructure that a system need to be able to create a graphical display. 
Window Managers provide windows (borders, title bars with buttons, ...) and mechanism to manage windows (open, close, resize, move ...)
Applications display their graphical user interface inside the windows created by the WM.
A Desktop environment adds additional GUI elements not provided by the window manager, and provides integration and usually also some additional small programs to enhance the user experience.

---

### Post by DrMega on 2008-06-22
> **Kernel Sanders said:**
> Not in Vista :cool:

Ah yes, Vista. 7 years of development, ideas pinched from Linux, and they *still* managed to balls it up:)

---

### Post by Christmas on 2008-06-22
I think I'd first say that Linux is the kernel itself, but the term is also used to denote entire operating systems based on it. Then there are distributions, which take the Linux kernel, the GNU command line utilities, X Window System, a desktop environment (together with a window manager) and all the other GUI (graphical user interface) and CLI (command line interface) applications and tools, like Amarok, mplayer and so on.

Then I'd proceed on explaining how things work in Linux, why the command line is so powerful and how things usually work. But not in graphical mode, it's better for a new user to just get used to logging in, performing commands like date, cd or ls. And only after that I'd introduce him to the GUI and all that comes with it.

Next step would be to show how to get help: manual pages, tutorials, forums. I'd also mention GNU and eventually recommend both articles from Richard Stallman and Eric Steven Raymond. I'd let him choose which he agrees with. I'd also mention Linus Torvalds, the open development method generally used on Linux, the Tux mascot.

Finally, I'd point out for lack of support so he will understand it's not Linux's fault when there are no drivers available for some hardware or no games ported.

---

### Post by jbrice on 2008-06-22
Windows is one ungainly lump of programming - Linux is ten-thousand separate programs flying elegantly in formation. ;)
(With apologies to whoever coined the phrase "a million rivets flying in formation" to describe an airliner.)

James B.

---

