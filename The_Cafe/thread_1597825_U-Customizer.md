---
title: "U-Customizer"
date: 2010-10-15
forum: The Cafe
---

### Post by xakepa on 2010-10-15
Here is my Ubuntu LiveCD customization tool. With it you can build own distro using Ubuntu-Mini-Remix ISO-image ( [http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/) ) or regular Ubuntu ISO.

  Customizer project at GitHub.com:
[https://github.com/fluxer/Customizer]("https://github.com/fluxer/Customizer")

:popcorn:

---

### Post by xakepa on 2010-10-24
come ooon.. nobody wants to try it and share his expirience with it.. :confused:

---

### Post by xakepa on 2010-11-03
U-Customizer v1.8.0 with GUI and more flexible then ever. Try it or die.. :)

---

### Post by EnGorDiaz on 2010-11-03
> **xakepa said:**
> U-Customizer v1.8.0 with GUI and more flexible then ever. Try it or die.. :)

*dies instead*

---

### Post by NightwishFan on 2010-11-03
How mean, I might give it a go in a virtual environment some time. I have been busy lately.

---

### Post by jmehdi on 2010-11-04
great work!

I'd use your tool if it meets my requirements, so I'd like to be able to:
- save different projects (for example, for 32 and 64bits ISO)
- install standalone .deb packages
- automatically copy files from the host to the root filesystem or ISO
- automatically execute commands in chrooted environment
- automatically add apt repositories
- remove packages (as you don't debootstrap but start from an existing ISO)

could I already do that? or do you have plans to support that?
Thanks

---

### Post by Lucradia on 2010-11-04
> **xakepa said:**
> I've tested it without any problems on:
[COLOR=Red]Ubuntu 10.04 + Gnome[/COLOR]

Does it have gnome dependencies?

---

### Post by Rodney9 on 2010-11-04
I installed it, how do I run it ?

---

### Post by xakepa on 2010-11-04
**JMEHDI:**

1. No, you can't save to project file. The configs are the same ( APPLIST for an example ) so if you start new project you can do it almost like the previuos so no need to do this.
2. Yes, you can do that. It's in the extras.
3. You can do it manually by clicking **Browse Filesystem** but i will add **Browse ISO Folder**
4. I will add that kind of script
5. You can edit manually the **sources.list**
6. Aftter i add auto exec commands script this can be done throug it. You can use Ubuntu-Mini-Remix ISO so you don't have to remove unwanted packages.


**LUCRADIA:**

No, no Gnome dependencies, I just test it on that kind of platforms. In future I'll test it on more platforms.

The tools are installed automaticly by clicking the **Install Tools** button (should that if you run it for first time) and all the dependencies to run the GUI are **gambas2-runtime, gambas2-gb-form, gambas2-gb-gui** and they are installed by the deb package.

[B]RODNEY9:

[/B]After installation there is a link in *System Tools *in your menu.

PS: Thanks for replyes. Every one of your post is precious for me to add stuff and make my tool better.

---

### Post by xakepa on 2010-11-04
New version released :popcorn:

---

### Post by jmehdi on 2010-11-05
> **xakepa said:**
> New version released :popcorn:
You should post a changelog so we know what to test ;)

---

### Post by xakepa on 2010-11-05
tnx for that and sry if i write something wrong or missed to write it in the thread. This is because I'm the only one who is working to debug, expand, changing online threads for the tool, testing it and that kind of stuff. The job isn't easy for only one person. I must think about everything and I've to go to work from time to time :P. So excuse me if i missed something but reply me imidiatly to make the corrections.

tnx again.

---

### Post by returnofnights on 2010-11-06
LastOS from Cyvoc here, I just thought I'd say I've been away from linux for a long time now, but I'll try out your tools, does it come with source code?

I'll leave you some feedback here when I give it a good testing :)

---

### Post by Sean Moran on 2010-11-06
> **xakepa said:**
> come ooon.. nobody wants to try it and share his expirience with it.. :confused:
Thanks mate.  I'm still mucking around with my same old bash scripts and chroot and stuff.  This is something I'm keen to test out tomorrow, and if it looks good, I'm on your side.
:popcorn:

---

### Post by xakepa on 2010-11-07
First I wanna say that everyone that used my tool may list the issues, what he like, what didn't and a wish list to add more features into my tool.

Second, I didn't do a big tested on version 1.8.2 but after I start working on v1.8.3 and many test i realized that there are many issues,sry for that but my PC is too slow to test every thing but from now on I will slow down the release dates to test that every thing is working. In v1.8.3 many fixes will be done and I will release it tonight maybe ( if don't have much work to do ). NO MORE BUGGY RELEASES!

Third, every feature release will come with source code for the GUI and the tool itself so everyone ( not only Ubuntu user ) shall use it,try it and modify something if they wanna do so.

---

### Post by xakepa on 2010-11-08
**NEW** version available with deb package and source codes :popcorn:

---

### Post by xakepa on 2010-11-17
NEW RELEASE WITH BIG LIST OF CHANGES!

:popcorn:

---

### Post by jmehdi on 2010-11-21
Just tested quickly (I will test deeply asap), but a lot of improvements! Keep up the good work :popcorn:

(I've found a bug: "wizard" takes only one z :D:D)

---

### Post by xakepa on 2010-11-21
tnx for the tip ;)

From now on U-Customizer has a official website (on free domain server):
[http://u-customizer.eu5.org/](http://u-customizer.eu5.org/)

You can visit and U-Customizer project at SourceForge.net:
[https://sourceforge.net/projects/u-customizer/](https://sourceforge.net/projects/u-customizer/)

---

### Post by fremantle on 2011-05-29
this is freakin awesome! there are a lot of remaster tools out there, but this is the most convenient and useful one i've stumbled upon. lets me do EXACTLY what i want. THANK YOU for this and keep developing it.

---

### Post by fremantle on 2011-05-29
couple of questions

when i run qemu and change the desktop look does that automagically carry on to the built distro?

also, is there any way one can COMPLETELY rebrand a ubuntu iso, such as remove "ubuntu" from grub/ubiquity and show my distro name? if not, consider adding this feature.

also, does the remastered ubuntu iso come with wubi support?

---

### Post by Lucradia on 2011-05-31
> **fremantle said:**
> couple of questions

when i run qemu and change the desktop look does that automagically carry on to the built distro?

also, is there any way one can COMPLETELY rebrand a ubuntu iso, such as remove "ubuntu" from grub/ubiquity and show my distro name? if not, consider adding this feature.

also, does the remastered ubuntu iso come with wubi support?

1. Over six months old.

2. [http://u-customizer.eu5.org/](http://u-customizer.eu5.org/) is 403 forbidden.

3. ubiquity is a Canonical project, you can find it's code here and change it yourself: [https://code.launchpad.net/ubiquity](https://code.launchpad.net/ubiquity)

---

### Post by Bandit on 2011-05-31
Gonna have to try this out.

---

### Post by xakepa on 2011-06-07
> when i run qemu and change the desktop look does that automagically carry on to the built distro?
no, qemu is like virtualbox and vmware (if you have heard about them..), it can setup a virtual machine and emulating the iso to try it out as you will on your current machine but without the need to reboot, setup in BIOS etc. I'd read somewhere that it can be used to customize an iso image (combined with ssh) however i don't know the details because i was not interested in such a method to do that.


> also, is there any way one can COMPLETELY rebrand a ubuntu iso, such as remove "ubuntu" from grub/ubiquity and show my distro name? if not, consider adding this feature.
i'm on it ;)

> also, does the remastered ubuntu iso come with wubi support?
wubi automaticly downloads the files needed to install Ubuntu (as far as i know, it's been a while since i've tried it), if wubi had an option to choose iso as source then you can install *buntu using the iso you've customized

---

### Post by Hylas de Niall on 2011-11-01
Xakepa, your software is featured in issue 11 of 'Ubuntu User'!
...it's a shame you've stopped developing it though :(

---

### Post by BrokenKingpin on 2011-11-01
For people looking for this type of tool there is always remastersys.

---

### Post by xakepa on 2011-11-01
> **Hylas de Niall said:**
> Xakepa, your software is featured in issue 11 of 'Ubuntu User'!
...it's a shame you've stopped developing it though :(
Well, I'm no longer interested in Ubuntu and its derivatives. If the live-build project didn't existed I'd be moving to support Debian instead of Ubuntu but because LB already supports many advanced features and customization Customizer is doomed unless someone wants to take-over the development.

[QUOTE=BrokenKingpin]
For people looking for this type of tool there is always remastersys.     
[/QUOTE]
Tried, never liked it. However this is the world of GNU/Linux, we have the power of choice ;)

---

