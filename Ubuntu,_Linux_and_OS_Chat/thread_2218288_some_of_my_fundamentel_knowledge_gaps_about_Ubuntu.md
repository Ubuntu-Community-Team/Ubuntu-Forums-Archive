---
title: "some of my fundamentel knowledge gaps about Ubuntu and Linux"
date: 2014-04-20
forum: Ubuntu, Linux and OS Chat
---

### Post by martin88 on 2014-04-20
Hello Community,

I would like to share so fundamental Ubuntu/Linux questions with you. It is important for me to understand those few technical Details before I start useing Unbutu.

In the follwing section I will write down some statement and I would really apprectite if you can give me a yes or no indication, if my Statement are right or wrong. 

1) Ubuntu uses Unity as its desktop environment in the versions since 11.04. Is it possible to use any other  desktop environment like KDE, Gnome and so on in any versionnumber?

2) Will all Software (Applicaions) run under all desktop enviroments?

3) Does some Application need an explicite desktop enviroment? (For example Firefox22 runs only this Gnome3)

4) Does all "commando line" - Software tool work on all Linux-Systems if the Linux-Kerne is the same?

5) Is it possible to run Software that  requires a older Kernel-Version on an newer Version?

6) If different Software requires different Versions of System-Packages; Is it possible to run those Software parallel on the same System?   

I hope my questions are accurate enough to give a more or less clear yes or no as answer.

Best regards
Martin

---

### Post by nothingspecial on 2014-04-20
1- Yes
2- They will but gnome based ones will pull in a load of gnome dependencies if you install them when using kde and vice-versa, some will even pull in everything leaving you with a pretty messy system.
3- See above
4- For the most part but some package managers (for example) are distro specific so there are exceptions
5- If software requires a specific version of anything to run then you will need that version
6- Short answer is no, maybe you could run this software in a virtual machine if necessary

---

### Post by buzzingrobot on 2014-04-20
> **martin88 said:**
> Hello Community,

I would like to share so fundamental Ubuntu/Linux questions with you. It is important for me to understand those few technical Details before I start useing Unbutu.

In the follwing section I will write down some statement and I would really apprectite if you can give me a yes or no indication, if my Statement are right or wrong. 

1) Ubuntu uses Unity as its desktop environment in the versions since 11.04. Is it possible to use any other  desktop environment like KDE, Gnome and so on in any versionnumber?

Yes, they are available as addons to Ubuntu Unity or as separate affiliated derivative distributions. (Kubuntu=KDE; Xubuntu=XFCE; Lubuntu=LXDE; Ubuntu Gnome=Gnome) Other environments are offered in independent distributions based on Ubuntu.

> 2) Will all Software (Applicaions) run under all desktop enviroments? 

Usually, as long as the other software components they rely on are installed. These dependencies are installed automatically if Ubuntu's repositories and tools like Software Center are used to install them and if they are available there. 

Two major software toolkits are used in Linux to build environments like KDE and Gnome.  If, say, you install a major KDE package on Gnome, you may find that a considerable number of other KDE packages are installed to support it.  Or, vice versa.

> 3) Does some Application need an explicite desktop enviroment? (For example Firefox22 runs only this Gnome3) 

No, but see above. Applications can be designed and optimized for one environment, but will work elsewhere, sometimes with an altered appearance. Environments usually include tools specifically intended to configure and tune that environment, as well.

> 4) Does all "commando line" - Software tool work on all Linux-Systems if the Linux-Kerne is the same? 

Command line use does not depend on the kernel. When you enter commands in a terminal, they are passed to a program called a "shell" that interprets and acts on the commands.  Different shells exist.  The standard shell in Linux is 'bash' and it is used the same way on all distributions.

>  5) Is it possible to run Software that  requires a older Kernel-Version on an newer Version?

Yes, technically, because it is possible to install and boot different kernel versions.  However, users typically have no reason to do this. Except for some hardware drivers, packages are not tied to particular kernel versions. 


> 6) If different Software requires different Versions of System-Packages; Is it possible to run those Software parallel on the same System?   

So long as those packages can be installed and used without breaking the system, yes.  Users can also install and run virtual machine software that creates a separate virtual environment in which Linux or other OS's can be loaded and used in isolation from the underlying system.  That's probably the best approach to using anything that might conflict with your system.

---

### Post by bapoumba on 2014-04-20
Moved to Ubuntu, Linux & OS Chat.

---

### Post by martin88 on 2014-04-22
Hi,

thanks a lot for your answers. Now I Need a bit of time to understand and but things together.

I the next step I will install the "Standard" Ubuntu Environment and try to run and set up some alternative Desktop Environments to find out the look and feel.

Then I need to define Software (Applications) that I need or wanna use. 

In the last step I have to build up my own System with the prefered Desktop Enviroment, the Applications, the Data and the backup strategy.

May the time is perfect to start because of the new LTS-Version with gives me a chance to get a benefit of that initial work on the Long term.

The Forum here seems to be perfect to get answers on questions nearly immediately.

Thanks a lot and see you soon.

Best regards
Martin

---

### Post by mastablasta on 2014-04-24
> **martin88 said:**
> I the next step I will install the "Standard" Ubuntu Environment and try to run and set up some alternative Desktop Environments to find out the look and feel.


bear in mind that installing dekstops next to desktop will pull all dependencies as well as desktop programs. so you may end up with 2 network managers if oyu install kubuntu dekstop in gnome.

a best way is to test it out live on USB. you can create multiboot USB with Yumi.


KDE has many KDE apps thta are not there by default in Gnome. i would guess that biggest difference is KDE and Gnome. the rest mostly use parts from each (e.g. Razor Qt is like a light KDE, while Xubutnu is like light Gnome) and build a bit of their own stuff in the mix. KDE for example even has their own office suite (Calligra Suite). KDE aps will be more integrated into KDE system while Gnome apps will have better integration in Gnome. however i use KDE (Kubuntu) since i mostly like KDE applications. however, often i would also use Gnome applicaitons as well if they are good or better. and i use desktop integration so often the Gnome (GTK based) applications would look like they are part of KDE desktop.
i also use many KDE applicaitons on windows (kde4win project).

there are many widnows managers and desktops aside from official ones found in ubuntu.

---

