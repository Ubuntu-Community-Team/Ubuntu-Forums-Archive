---
title: "Explain me like I'm five: what are GNOME and KDE?"
date: 2013-10-25
forum: Ubuntu, Linux and OS Chat
---

### Post by sha1sum on 2013-10-25
What is GNOME and KDE? So far I've figured out that they are desktop environments, but I have no idea what that means. Can somebody explain it to me?

---

### Post by Habitual on 2013-10-25
[http://en.wikipedia.org/wiki/Desktop_environments](http://en.wikipedia.org/wiki/Desktop_environments)

---

### Post by sha1sum on 2013-10-25
You know, I do search before I start a thread. I have checked wikipedia. It's just that this didn't help me much:

In graphical computing, a **desktop environment** (**DE**) is an implementation of a desktop metaphor graphical user interface (GUI). The desktop environment was seen on most personal computers until the rise of mobile computing.[1][2] Desktop GUIs help the user in easily accessing, configuring and modifying many important and frequently accessed specific operating system (OS) features. The GUI usually does not afford access to all the many features found in an OS. Instead, the traditional command-line interface (CLI) is still used when full control over the OS is required in such cases.

---

### Post by vasa1 on 2013-10-25
> **sha1sum said:**
> You know, I do search before I start a thread. I have checked wikipedia. It's just that this didn't help me much:....
Why don't you ask a more focused question?

---

### Post by sha1sum on 2013-10-25
"What is a desktop environment?"

Is that an unfocused question?

---

### Post by PaulW2U on 2013-10-25
> **sha1sum said:**
> You know, I do search before I start a thread. I have checked wikipedia. It's just that this didn't help me much:

You asked a question with only a few words but the answer could run to several thousand.

Take a look at the links in my signature. For GNOME look at Ubuntu and Ubuntu GNOME, for KDE look at Kubuntu. In very simplistic terms KDE and Gnome are what you see, the GUI or the applications that those desktop environments make available to their users.

---

### Post by vasa1 on 2013-10-25
> **sha1sum said:**
> "What is a desktop environment?"

Is that an unfocused question?
All the best.

---

### Post by sha1sum on 2013-10-25
> **PaulW2U said:**
> In very simplistic terms KDE and Gnome are what you see, the GUI or the applications that those desktop environments make available to their users.Okay I see. So does that include things like the launcher and dash home?

---

### Post by PaulW2U on 2013-10-25
> **sha1sum said:**
> Okay I see. So does that include things like the launcher and dash home?

Yes, the various desktop environments will have different ways of starting programs.

The 'dash' and 'launcher' are specific to Unity while KDE has 'Kickoff'.

---

### Post by Johan De Cauwer on 2013-10-25
> **sha1sum said:**
> Okay I see. So does that include things like the launcher and dash home?

No, because that's not included in KDE or Gnome. But then again, if you want the easiest answer, they are all the same. Under all, the same Linux kernel and the same GNU. And with libraries (who cares what that means) they all run the same programs.

Beware, there is an OS called Windows and that's not exactly the same... ;-)

---

### Post by Bashing-om on 2013-10-25
sha1sum; Hi !

Consider it like so:
The common element in all linux distributions is the kernel. That piece of software that is the intermediator between the hardware(s) and you.
Onto this kernel are several layers, one of those layers is the GUI - the windows manager, Xorg. A window manager controls the placement and appearance of windows within a graphical user interface. 
Now this GUI can take several forms.
Gnome is used for ubuntu,
Kde is used for (k)ubuntu,
Lxde is used for (l)ubuntu
and many other spins exist.. such as xfce, Openbox, IceWM, Fluxbox, FVWM-Crystal just to name a few of the more popular.

It all depends on how you want to relate to the kernel within this Graphical User Interface.

[INDENT][INDENT]clear as mud ?
[/INDENT][/INDENT]

---

### Post by oldos2er on 2013-10-25
> **sha1sum said:**
> Okay I see. So does that include things like the launcher and dash home?

Yes, it includes everything. Desktop environments are "kitchen sinks" in that they include a variety of programs e.g. text editors, email clients, web browsers, file managers, etc., in addition to [window managers. ]("https://wiki.archlinux.org/index.php/Window_Manager") A window manager is software that's responsible for drawing windows on the desktop, and for window controls, title bars, and the like. I think all the major DEs also have a [compositor]("http://en.wikipedia.org/wiki/Compositing_window_manager") that may or may not be separate from the window manager. A compositor provides "eye candy" effects.

Unlike Windows, Linux has many different graphical interfaces one can choose to run. You can see a comparison between some of them [here]("http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available").

---

### Post by philinux on 2013-10-25
> **sha1sum said:**
> Okay I see. So does that include things like the launcher and dash home?

That s unity.

[http://en.m.wikipedia.org/wiki/Unity_(user_interface)](http://en.m.wikipedia.org/wiki/Unity_(user_interface))

Have a look at the development link.

---

### Post by sha1sum on 2013-10-25
Sweet, awesome answers.

I think I'm getting it.

So to recap: 

 
[LIST]
[*]There is the kernel, which runs the hardware (the CPU and the RAM). The kernel is what all Linux distros have in common. 
[/LIST]


[LIST]
[*]Then  on top of that there is the desktop environment, which is different for  every distribution. Ubuntu has unity, Kubuntu has KDE. Is it correct to say that the desktop environment allows the user to  communicate with the kernel? 
[/LIST]
 
Were the kernel and the desktop environment developed at the same time, or did people in the old days have to work with the kernel directly? ie: the first operating systems, did they have a very crude desktop environment, or not one at all?

---

### Post by Bashing-om on 2013-10-25
sha1sum;

Now we are getting into history and development .. the linux kernel is in a constant state of development... but the kernel was first, the GUI is a rather resent addition - Hey, look what we can do ! .. And yes this desktop environment is also in constant development to meet the want to of the users !
-now we have touch screens ! -
open source, the platform to
[INDENT][INDENT][INDENT]see what you can do[/INDENT][/INDENT][/INDENT]

---

### Post by sha1sum on 2013-10-25
I understand it all a bit better now. I'll be back with more questions, but for now I'm good. :p Thanks guys. Y'all rock. :cool:

---

### Post by mayagrafix on 2013-10-25
> **sha1sum said:**
>  
Were the kernel and the desktop environment developed at the same time, or did people in the old days have to work with the kernel directly? ie: the first operating systems, did they have a very crude desktop environment, or not one at all?

Very succinctly, first there were PUNCH cards (circa 1960) were u asked or tasked a computer via cards full of holes. Then there was (and still is) the Command Line. That means a screen with text only, and every time u wanted to do something a lot of typing was involved. Then came the Graphical User Interface (think Apple Mac) where orders were transmitted to the computer via mouse and menus on the screen.

The different desktops are like cars, they all have 4 wheels and a motor, and they do the same thing (transport u from A to B), but they are different in many ways. i.e VW Beetle (with motor in the back). and a Cadillac (lots of chrome and leather) or a Jaguar XKE (very fast but not confortable).

Thus Unity is full of modern gizmo's while Mint is very classic and KDE has whole 'nother way of doing things, but they all get u there ):P

---

### Post by VMC on 2013-10-25
Both have different frameworks. Its just not the user experience that's different.
When I find a program in Kubuntu that I really like, unless its recompiled in GTK, I have to load a truckload of libraries for it to work in GNOME.
K9copy is one example, that I prefer over Brasero.
KDE uses QT framework and GNOME uses GTK+. One was originally developed using C++, the other using 'C'. This only means something if you want to run KDE programs on GNOME platform.

---

### Post by T_Giegler on 2013-10-25
> **sha1sum said:**
> 
Were the kernel and the desktop environment developed at the same time, or did people in the old days have to work with the kernel directly? ie: the first operating systems, did they have a very crude desktop environment, or not one at all?

No, they were not developed at the same time. Users used to only have something similar to the terminal. Now the Terminal is a program run by the GUI Graphic User Interface (GMONE & KDE) for processes that still do not have GUI compatible programs written for them. I don't know much terminal language, and it does seem like a seperate language. I remember my oldest brother working on a Comidor when they had floppy disks 5.5 inces square insted of CDs or thumb drives.

---

### Post by buzzingrobot on 2013-10-25
The style and approach of the Windows 7 interface can be considered a destop environment. Ditto Windows 8.

in Linux, such things are independent of the core operating system.  You can install one, decide you don't like it, and install another.

typically, they also offer a suite of basic applications: file manager, editor, mail, etc.  You are not confined to using only them, however.

Altho appearances differ, they are not to be confused with mere themes.  Gnome and KDE, for example, both install support libraries on which they depend for their functionality.

---

### Post by cariboo on 2013-10-25
THis really isn't a support question. Moved.

---

### Post by craig10x on 2013-10-25
Linux is flexible though with programs....kde programs can be installed on gnome and gnome programs can be installed in kde...
For example, Ubuntu is a gnome environment and has the unity desktop of course....some people like kde's disc burner k3b better then gnome's Brasero disc burner...so they install k3b in ubuntu (you would find it in the software center)....mostly i stick to gnome programs myself...in fact i use to use k3b when Brasero wasn't working too well but i notice it greatly improved in more recent times, so i went back to using that...

But the desktop Look and set-up is different between say Ubuntu and Kubuntu (kde)...Kubuntu looks more like windows..Ubuntu w/unity more "mac like"...
In Gnome there are many different desktop environments like Unity, Gnome Shell, Cinnamon, to give a few examples...
KDE doesn't have different desktops...

I prefer gnome myself (and especially ubuntu w/unity) it's more simple in it's layout i think...

---

