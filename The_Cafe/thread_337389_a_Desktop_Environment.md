---
title: "a Desktop Environment"
date: 2007-01-12
forum: The Cafe
---

### Post by maniacmusician on 2007-01-12
What are the components of a DE? what makes a DE a DE?

So far, I've got:

> Window Manager

File Manager

Maybe i'm just getting tired, but I can't think of anything else...so I'm asking :) What are the integral parts of a Desktop Environment?

---

### Post by Polygon on 2007-01-12
this is basically what makes up GNOME, the different components (taken from wikipedia)

> GNOME is built from a large number of different projects. A few of the major ones are listed below:

    * Bonobo — a compound document technology.
    * GConf — for storing application settings.
    * GNOME VFS — a virtual file system.
    * GNOME Keyring — for storing encryption keys and security information.
    * GNOME Translation Project — translate documentation and applications into different languages.
    * GTK+ — a widget toolkit used for constructing graphical applications. The use of GTK+ as the base widget toolkit allows GNOME to benefit from certain features such as theming (the ability to change the look of an application), smooth anti-aliased graphics. Sub-projects of GTK+ provide object oriented programming support (GObjects), extensive support of international character sets and text layout (Pango) and accessibility (ATK). GTK+ reduces the amount of work required to port GNOME applications to other platforms such as Windows and Mac OS X.
    * Human Interface Guidelines (HIG) — research and documentation on building easy-to-use GNOME applications.
    * LibXML — an XML library.
    * ORBit — a CORBA ORB for software componentry.

A number of language bindings are available allowing applications to be written in a variety of programming languages, such as C++ (gtkmm), Java (Java-GNOME), Ruby (ruby-gnome2), C# (Gtk#), Python (PyGTK), Perl (gtk2-perl) and many others. The only languages currently used in applications that are part of an official GNOME desktop release are C, C# and Python.[11]

all you really do see is a desktop / file manager / the panels and whatnot, but i guess it is a lot more 'behind the scenes"

---

### Post by ComplexNumber on 2007-01-12
> **maniacmusician said:**
> What are the components of a DE? what makes a DE a DE?

So far, I've got:



Maybe i'm just getting tired, but I can't think of anything else...so I'm asking :) What are the integral parts of a Desktop Environment?
i guess it depeneds what type of desktop. if you're wanting to know what makes a desktop environment, as a minimum. it will probably have the following: sound server(arts, alsa, etc), toolkit(qt/gtk/whatever), graphics library(imlib, cairo, etc), hardware device detection(eg HAL), a component system(kparts, bobobo, etc), theming engines, icon theme,  etc.

---

### Post by maniacmusician on 2007-01-12
I'm writing a comprehensive, full-of-information, and educational guide for new linux users. 

I don't want all the behind the scenes stuff in there, but some of it is important.

I'll be including GUI toolkit, sound server, theming engines in addition to what I have

ComplexNumber, I'm pretty sure HAL is not part of the DE but rather the OS? and I don't know enough about component systems to write about them.

Thanks for that list Polygon

---

### Post by Polygon on 2007-01-12
your welcome :D

im pretty sure HAL (hardware abstraction layer) is part of the kernel, but im pretty sure that gnome hooks into it for stuff like rendering, sound engine etc

here is the kde list if it has anything that the gnome one missed

>     * aRts - soundserver
    * DCOP - system for communication between processes
    * KHTML - HTML engine
    * KIO - extensible network-transparent file access for KDE applications
    * Kiosk - disable features within KDE to create a more controlled environment
    * KParts - lightweight in-process graphical component framework
    * KWin - window manager
    * KConfigXT - takes an XML file and produces source code to manage configuration options, including classes to glue the resulting code to configuration dialogs.
    * Qt - cross-platform graphical widget toolkit
    * XMLGUI - allows defining UI elements such as menus and toolbars via XML files

[edit] 

---

### Post by maniacmusician on 2007-01-12
thanks!

I didn't see a sound server in Gnome's list. So does it use alsa instead of aRts?

And does every DE use a different sound server? XFCE probably uses the same as Gnome...what about Enlightenment? 

other DEs?

also, this is asking a bit much, I know, but what's the basic difference between sound servers? how would aRts differ from alsa? why do different DEs need different protocols? and a sound server just basically controls how sound is input-ed and output-ed from your system right?

---

### Post by Polygon on 2007-01-12
im thinking that alsa is kernel level and something else is at gnome's level that takes all the request for sound and whatnot and sends it to alsa...

cause wikipedia says that alsa is kernel level and provides drivers, and with google searches they talk about "gnome sound server"

---

### Post by ComplexNumber on 2007-01-12
> ComplexNumber, I'm pretty sure HAL is not part of the DE but rather the OS? and I don't know enough about component systems to write about them.i'm certain that its  part of the DE. i mean, what do you think solid is? solid is going to be  specific to kde and is the near-equivelent to HAL

---

### Post by Polygon on 2007-01-12
actually i take back what i said about hal being kernel level. its "inbetween" the kernel and the actual OS... so im not sure

hardware abstraction layer (HAL) is an abstraction layer, implemented in software, between the physical hardware of a computer and the software that runs on that computer. Its function is to hide differences in hardware from most of the operating system kernel, so that most of the kernel-mode code does not need to be changed to run on systems with different hardware. A HAL allows instructions from higher level computer languages to communicate with lower level components, such as directly with hardware.

---

### Post by maniacmusician on 2007-01-12
yup, I know what HAL is, I'm more confused about the sounds server.

ComplexNumber: KDE also has kde-hal-device-manager, or something like that. I'm going to have to confirm this then; I was always sure that HAL was in between the kernel and the OS, as Polygon said. 

any clarification on sound servers from my post #6?

---

### Post by ComplexNumber on 2007-01-12
>  KDE also has kde-hal-device-manager, or something like that.kde 3.x does. the reason why kde also has that is to do with the freedesktop.org which is trying to make both desktops have common standards. kde4 will break away from that by introducing solid instead.

---

### Post by maniacmusician on 2007-01-13
interesting, I didn't know that...what about the sound server stuff?

---

### Post by ComplexNumber on 2007-01-13
> **maniacmusician said:**
> interesting, I didn't know that...what about the sound server stuff?
kde (presently) has its own - arts. as for gnome, i think it used to be esd.  i don't think its default now, though. i'm still a little unclear about sound servers and sound drivers, and the difference between the 2. alsa, as i understand it, isn't a sound server, but a sound driver. gstreamer is a multimedia framework.

---

### Post by maniacmusician on 2007-01-13
ah, alright, thanks.

---

### Post by NeoChaosX on 2007-01-13
> **ComplexNumber said:**
> kde 3.x does. the reason why kde also has that is to do with the freedesktop.org which is trying to make both desktops have common standards. kde4 will break away from that by introducing solid instead.

Actually, no, Solid isn't breaking away from HAL. It's an abstraction layer that gets information about the hardware regardless of what OS it's running on (since KDE4 is supposed to be ported to Mac and Windows as well) and sends to KDE4 applications. In Linux, Solid will actually use HAL to get information about the hardware.

---

### Post by ComplexNumber on 2007-01-13
> **NeoChaosX said:**
> Actually, no, Solid isn't breaking away from HAL. It's an abstraction layer that gets information about the hardware regardless of what OS it's running on (since KDE4 is supposed to be ported to Mac and Windows as well) and sends to KDE4 applications. In Linux, Solid will actually use HAL to get information about the hardware.
actually, yes. you seem to have misunderstood the concept. 
[this]("http://solid.kde.org/cms/1050") tells you about solid. compare with hal [here]("http://freedesktop.org/wiki/Software_2fHalFAQ").

to clarify, see the screenshot. notice that there is a kde interface(ie kde-hal-device-manager) to hal and a gnome interface (ie hal-device-manager) to hal. the latter will be replaced with solid in kde4.

---

### Post by qalimas on 2007-01-13
I'd say the main thing that makes it a desktop *environment* is the fact that everything works well together.  In Gnome, everything looks the same, acts the same, feels the same.  A KDE application inside of it feels... dirty.  The same goes the other way around, in KDE, everything feels the same, acts the same, etc.  So I suppose integration with it's applications and a consistant experience defines a DE.

---

### Post by NeoChaosX on 2007-01-13
> **ComplexNumber said:**
> actually, yes. you seem to have misunderstood the concept. 
[this]("http://solid.kde.org/cms/1050") tells you about solid. compare with hal [here]("http://freedesktop.org/wiki/Software_2fHalFAQ").

to clarify, see the screenshot. notice that there is a kde interface(ie kde-hal-device-manager) to hal and a gnome interface (ie hal-device-manager) to hal. the latter, together with hal, will be replaced with solid in kde4.

Funny, because I did some research on the relationship between HAL and Solid and found it to say otherwise:

[http://lwn.net/Articles/166318/](http://lwn.net/Articles/166318/)
[http://ervin.ipsquad.net/index.php/2006/01/04/44-solid](http://ervin.ipsquad.net/index.php/2006/01/04/44-solid)

Both links indicate that Solid is supposed to be an abstraction layer on top of hardware-probing layers like HAL. The fact that the second link notes that there's a HAL backend for Solid definately suggests to me that it's not at all supposed to replace it. It uses HAL to collect information about the hardware and can send that information to KDE 4 apps.

---

### Post by ComplexNumber on 2007-01-13
> **NeoChaosX said:**
> Funny, because I did some research on the relationship between HAL and Solid and found it to say otherwise:

then you found wrong. re-read about solid.

---

### Post by Erunno on 2007-01-13
[http://dot.kde.org/1136389547/]("http://dot.kde.org/1136389547/")

> After a lot of hacking behind the scenes, a new initiative to improve KDE's interaction with network and hardware devices has been launched. Solid will provide a robust basis for the dynamic modern desktop in KDE, which needs to be aware of available hardware and networks, paving the way for innovative functionality. Users should see KDE applications taking advantage of Solid in KDE 4, from the most basic Plasma applets and complex applications to desktop-wide awareness. Developers will be able to take advantage of a robust, flexible and portable API and will be integrated into the Plasma engine. **It will make use of existing technologies like HAL**. Solid will also include a knowledge base providing a way for users to easily provide feedback on incorrect behaviour. 

As far as I understand Solid, like Phonon, is a stable API for KDE applications.

Regards,
Erunno

---

### Post by Bloodfen Razormaw on 2007-01-13
We need to start a new sport here, where teams compete to see how many times in one day they can get ComplexNumber to go into denial when he is proved wrong about some uninformed thing he has claimed.

NeoChaosX is completely correct.  Solid is a high level abstraction over an operating system's native HAL.  Solid means that first time a desktop will be able to work just as well with the Linux HAL as it does with the Windows HAL as it does with the Solaris HAL as it does with FreeBSD's devctl.

---

### Post by ComplexNumber on 2007-01-13
> **Bloodfen Razormaw said:**
> We need to start a new sport here, where teams compete to see how many times in one day they can get ComplexNumber to go into denial when he is proved wrong about some uninformed thing he has claimed.

NeoChaosX is completely correct.  Solid is a high level abstraction over an operating system's native HAL.  Solid means that first time a desktop will be able to work just as well with the Linux HAL as it does with the Windows HAL as it does with the Solaris HAL as it does with FreeBSD's devctl.
thats rich coming from you. there's no need for a new sport because we already have one  - count the number of inaccuracies and percentage level of kde fanaticism in Bloodfen Razormaw's typical posts to the nearest 100. i have been 'proved' wrong nowhere.

---

### Post by Erunno on 2007-01-13
> **ComplexNumber said:**
> i have been 'proved' wrong nowhere.

Which part of **"It will make use of existing technologies like HAL"** is so difficult to grasp ?

---

### Post by maniacmusician on 2007-01-13
god damn, don't start a *****ng flamewar in my thread. Please stay on topic or refrain from posting!

On a brighter note, thanks for all the useful information. If anyone wants to clarify anything (esp about sound servers; dont know a lot about them), feel free.

---

