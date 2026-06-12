---
title: "A Graphical Grub editor by default."
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by vikari_metal on 2007-10-21
If one of the objectives of Ubuntu is to make linux  easier to the beginner user, I think that the new version should have a graphical grub editor to configurate this more easy.
I know that now is already easy to configurate the grub, but if you can make it easier than now, awesome.
What do you think about ?
Adéu.

PD. Sorry for my english.

---

### Post by rybu on 2007-10-22
I think there already is one -- System -> Administration -> Startup Manager.  No?

---

### Post by tubasoldier on 2007-10-22
PClinuxOS has one. It works for both grub and lilo. I do believe that Fedora and Suse have one as well.

---

### Post by Lozz on 2007-10-22
Something we most definitely sorely need.

---

### Post by glotz on 2007-10-22
I think people who cannot use the command line shouldn't definitely meddle with grub...

Very low priority in my opinion.

---

### Post by amano on 2007-10-23
> **tubasoldier said:**
> PClinuxOS has one. It works for both grub and lilo. I do believe that Fedora and Suse have one as well.

Maybe this can be ported? Is that Qt? Maybe it can be ported to gtk+?

> I think people who cannot use the command line shouldn't definitely meddle with grub...
I think that especially dual-booters and thus rather Linux novices will (be forced to) edit the grub file. Eg. to make windows again their default OS after any kernel upgrade. A Linux-only user will probably touch the grub file rather seldomly.

At least changing the defaults should be done by a small UI. And it should be safe even for novices to use. You can mess up your grub with the CLI much more, eventually with Linux not booting at all anymore!

This very high priority in my opinion because it involves fresh Linux users editing critical system files by hand.

---

### Post by altonbr on 2007-10-23
> **rybu said:**
> I think there already is one -- System -> Administration -> Startup Manager.  No?

True and I use it, but you have to install it from the command line. It's not installed by default (unless something got messed up from the alpha Gusty's to the official release).

```
$ sudo aptitude install startupmanager
```

---

### Post by ezak on 2007-10-23
Yes, as stated by rybu, there is a grub-editor/boot-editor called startupmanager in the Ubuntu packages also know as SUM. 

sudo apt-get install startupmanager

It allows you to configure which kernels are displayed in the grub screen,  and to configure the time to display them and so on. Upon a few other useful options like password protection so you don't get unauthorized logins or changes on your system, you can also change usplash screens. Pretty handy little app, just make sure you use it wisely.

---

### Post by glotz on 2007-10-23
[QUOTE=amano]I think that especially dual-booters and thus rather Linux novices will (be forced to) edit the grub file. Eg. to make windows again their default OS after any kernel upgrade. A Linux-only user will probably touch the grub file rather seldomly.[/QUOTE]Interesting point I didn't think of. I guess there is a fair number of dual booters. But then shouldn't the kernel upgrading process rather be changed? Why does it change the default setting?

---

### Post by desperado666 on 2007-10-23
[http://flomertens.free.fr/disk-manager/index.html](http://flomertens.free.fr/disk-manager/index.html)

---

### Post by stchman on 2007-10-23
> **glotz said:**
> I think people who cannot use the command line shouldn't definitely meddle with grub...

Very low priority in my opinion.

I somewhat feel the same way, but Ubuntu needs to be more widespread to get the stuff we want (better drivers, more drivers, etc.).

Having a GRUB GUI editor would be nice IMO.

---

### Post by smartboyathome on 2007-10-23
> **amano said:**
> Maybe this can be ported? Is that Qt? Maybe it can be ported to gtk+?

SAM Linux (based on PCLOS) has a GTK+ version of it already. Basically, you can port the one from them instead of re-inventing the wheel. :)

---

### Post by glotz on 2007-10-23
Is it good? if not, then it's better to reinvent...

---

### Post by smartboyathome on 2007-10-23
> **glotz said:**
> Is it good? if not, then it's better to reinvent...

Of course. That is the one thing that I think is BEST about the PCLOS series (the whole control center, the Grub editor is just one part of it).

---

### Post by Perpetual on 2007-10-23
> **altonbr said:**
> True and I use it, but you have to install it from the command line. It's not installed by default (unless something got messed up from the alpha Gusty's to the official release).

```
$ sudo aptitude install startupmanager
```

I just installed Startup Manager and it's exactly what I was wishing was already there.  Seems this should be available as a default.  There is nothing there that can really damage the GRUB.

---

### Post by altonbr on 2007-10-23
> **desperado666 said:**
> [http://flomertens.free.fr/disk-manager/index.html](http://flomertens.free.fr/disk-manager/index.html)

Wow. Now that's impressive. I love the integration with Ubuntu. Do you know anything about its implementation progress for Hardy?

---

### Post by amano on 2007-10-24
Well, Flo Mertens' Disk Manager is nice, but doesn't handle Grub entries. At lest not according to the feature list on his site...

---

### Post by suchawato on 2007-10-25
> **glotz said:**
> I think people who cannot use the command line shouldn't definitely meddle with grub...

Very low priority in my opinion.
Not true.
Anyone with multiple partitions would find this nice.
I use Super Grub Disc to switch between my Windows and GNU/Linux  partitions. This is because this method has proved to be the fastest.
If GRUB had a 16 or 8 bit simple GUI with an easy confuguration tool for setting up multiple partitions and harddrives with different OS', this would be greatly apprecieated. 
In any case, it isn't the job of the OS to tell the user what to do with it. A warning/danger message should be included, but not unavailable.
Also, the point of a GUI would be to provide default configuration settings that work, not nesisicarily text line editing.

---

### Post by Martje_001 on 2007-10-25
> **rybu said:**
> I think there already is one -- System -> Administration -> Startup Manager.  No?
That doesn't work. It removes my Windows entries :(

[suchawato:]("http://ubuntuforums.org/member.php?u=299054")
Very good idea!

---

### Post by amano on 2007-10-28
To wait until grub gets becomes something more than it is now, doesn't seem a good idea. Grub 1 is ancient code and worth to really touch it anymore and grub 2 doesn't seem to be ready in the near future.


 I'd rather want to see a small simple foolproof GUI that let's me hide some grub entries and make one of the OSes the default.

---

### Post by EXCiD3 on 2007-10-28
I also think that something like Startup Manager should be included in the installation program.

---

### Post by kragen on 2007-10-28
> **glotz said:**
> I think people who cannot use the command line shouldn't definitely meddle with grub...

Very low priority in my opinion.

Simple things, (like changing the default boot option, changing the name of the boot option, changing the delay before booting etc...) should be possible really - a GUI would make things like this safer, easier and less daunting for users unused to the command line, and a simple gui to perform these tasks wouldnt take long to produce.

The GUI doesnt need to do much more than this really - anyone who needs anything more complicated is better served with a text editor.

---

### Post by stomponthis on 2007-10-29
I think its a good idea, many new users are baffled by the grub file.  I have never used the Start Up manager, maybe it should be a default.
I would never use it, but I think it would be helpful to many users.

---

### Post by Bruce M. on 2007-10-30
> **ezak said:**
> Yes, as stated by rybu, there is a grub-editor/boot-editor called startupmanager in the Ubuntu packages also know as SUM. 

sudo apt-get install startupmanager

It allows you to configure which kernels are displayed in the grub screen,  and to configure the time to display them and so on. Upon a few other useful options like password protection so you don't get unauthorized logins or changes on your system, you can also change usplash screens. Pretty handy little app, just make sure you use it wisely.

bruloo@The-Team:~$ sudo aptitude install startupmanager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "startupmanager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
bruloo@The-Team:~$ 


bruloo@The-Team:~$ sudo apt-get install startupmanager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager
bruloo@The-Team:~$

Is it a Gutsy thing?
I'm using Feisty

---

### Post by smartboyathome on 2007-10-30
it is called startup-manager.

---

### Post by Bruce M. on 2007-10-30
> **smartboyathome said:**
> it is called startup-manager.

bruloo@The-Team:~$ sudo apt-get install startup-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startup-manager
bruloo@The-Team:~$ 

This is a joke right?
And this newbie fell for it.

---

### Post by smartboyathome on 2007-10-30
> **Bruce M. said:**
> bruloo@The-Team:~$ sudo apt-get install startup-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startup-manager
bruloo@The-Team:~$ 

This is a joke right?
And this newbie fell for it.

No it wasn't a joke, I am sorry. Try searching using synaptic.

---

### Post by glotz on 2007-10-30
It's in the **gutsy** repos guys.

---

### Post by BlueSkyNIS on 2007-10-31
> **rybu said:**
> I think there already is one -- System -> Administration -> Startup Manager.  No?

I had a problem using this app. I have had disabled memtest option and after that, my ubuntu never booted up. :( Even a boot screen wont show. ](*,) I got a kernel panic "cannot mount VFS" or something "please specify you root drive".

root was correctly specified in menu.lst but kernel just didn't want to boot up. ](*,) #-o I have tried /dev/sda values, UUID values but nothing helped. I think (correct me if I'm wrong) the problem was in initrd. :-k

I have a SATA II hard disk on intel 945P chipset. Don't know for sure where the problem was. Anyway I have just reinstalled the whole Ubuntu.

Sorry for my english, it's not my native language.

---

### Post by altonbr on 2007-10-31
> **amano said:**
> To wait until grub gets becomes something more than it is now, doesn't seem a good idea. Grub 1 is ancient code and worth to really touch it anymore and grub 2 doesn't seem to be ready in the near future.


 I'd rather want to see a small simple foolproof GUI that let's me hide some grub entries and make one of the OSes the default.

They are working on optimizing grub: [https://blueprints.launchpad.net/ubuntu/+spec/grub-configuration-improvements](https://blueprints.launchpad.net/ubuntu/+spec/grub-configuration-improvements)

> **glotz said:**
> It's in the **gutsy** repos guys.

+1.

---

### Post by coolen on 2007-10-31
This, along with an Xorg graphical configuration, are two of the features I've been wanting most out of Ubuntu. They've addressed the second one (although an advanced option would be nice), and apparently a good option already exists for this.
Startup Manager default for Hardy: +1

---

### Post by Bruce M. on 2007-10-31
> **smartboyathome said:**
> No it wasn't a joke, I am sorry. Try searching using synaptic.

Re: startup-manager

Nothing.
I tried:
startup - nothing about GRUB
manager - a long list, nothing refering to GRUB
startup manager - I get: evolution and wmanager
startup-manager - a blank screen
startupmanager - a blank screen

Oh, and just so you know, I have 3 GRUB menu.lst backup files from using: sudo gedit /boot/grub/menu.lst, so it's not like I don't know how.  I just want to see this GUI manager.
But I can't find it.  :(

---

### Post by smartboyathome on 2007-10-31
> **Bruce M. said:**
> Re: startup-manager

Nothing.
I tried:
startup - nothing about GRUB
manager - a long list, nothing refering to GRUB
startup manager - I get: evolution and wmanager
startup-manager - a blank screen
startupmanager - a blank screen

Oh, and just so you know, I have 3 GRUB menu.lst backup files from using: sudo gedit /boot/grub/menu.lst, so it's not like I don't know how.  I just want to see this GUI manager.
But I can't find it.  :(

I forgot, but as posted before, it is only available for Gutsy. :(

---

### Post by LaserJock on 2007-10-31
To throw more fuel on the fire this summer I mentored a Google Summer of Code student writing a Grub config GUI for Ubuntu. The project page is at [https://edge.launchpad.net/ubuntu-bootloader-manager](https://edge.launchpad.net/ubuntu-bootloader-manager) and the spec is at [https://wiki.ubuntu.com/BootloaderManager](https://wiki.ubuntu.com/BootloaderManager) . The last I blogged about it was [http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/](http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/) but there has been significant UI changes since then.

I think the lack of projects is not the issue here :) but rather getting good ones integrated into Ubuntu and packaged up.

-LaserJock

---

### Post by Bruce M. on 2007-10-31
> **glotz said:**
> It's in the **gutsy** repos guys.

Me in #24
Is it a Gutsy thing?
I'm using Feisty

And as I'm spending time in Synaptic searching for every different ways to put in startup manager, AMANO posts this.

Well, at least I'm not going crazy.  :)

---

### Post by altonbr on 2007-10-31
> **Bruce M. said:**
> Me in #24
Is it a Gutsy thing?
I'm using Feisty

And as I'm spending time in Synaptic searching for every different ways to put in startup manager, AMANO posts this.

Well, at least I'm not going crazy.  :)

Gusty only.

> **LaserJock said:**
> To throw more fuel on the fire this summer I mentored a Google Summer of Code student writing a Grub config GUI for Ubuntu. The project page is at [https://edge.launchpad.net/ubuntu-bootloader-manager](https://edge.launchpad.net/ubuntu-bootloader-manager) and the spec is at [https://wiki.ubuntu.com/BootloaderManager](https://wiki.ubuntu.com/BootloaderManager) . The last I blogged about it was [http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/](http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/) but there has been significant UI changes since then.

I think the lack of projects is not the issue here :) but rather getting good ones integrated into Ubuntu and packaged up.

-LaserJock

What's wrong with SUM?

---

### Post by LaserJock on 2007-11-01
> **altonbr said:**
> 
What's wrong with SUM?

Nothing but the fact that it wasn't in the repos and neither the student nor the mentor (me) knew it existed until **after** the project was accepted and started.

That said, the Summer of Code project turned into more of a config interface like what you'd see in System->Administration rather than a standalone app. It's also got some nice automatic detection of other OSs. It allows you to also add and remove OS entries and it shows a preview of the appearance. I think it also has more configurability, but I'm not sure

Overall I'd love to see all these various efforts pooled together into one or two **good** ones. A common failing, IMO, is that they all try to just GUIfy a text config file. This is really not much help to new users. Many people don't know what a "bootloader" is or does or many of the options/jargon these config GUIs tend to want to throw at people. I also want to see integration into logout management so you can select an OS to reboot into. 

Simply having a GUI frontend to menu.lst isn't going to get you very far, we need something really cool to make it into Ubuntu proper and maybe even the installer.

-LaserJock

---

### Post by kragen on 2007-11-02
Hmm, unless i've missed anything, the two contenders are:

**Bootloader Manager** (The google code project)
[http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/](http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/)

**StartUp-Manager** (In Gutsy Repo's)
For those too lazy to install it / those running feisty, I've taken some quick screenshots:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48784&stc=1&d=1193997962[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=48785&stc=1&d=1193997962[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48786&stc=1&d=1193997962[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=48787&stc=1&d=1193997962[/IMG]

Personally my first impression of SUM (Startup Manager) was that it was fairly cluttered, and it doesn't have the ability to add and remove boot options, however pretty much everything else is there.

I cant find Bootloader manager to install it and have a go, but from the screenshots it looks to have more options - you can add and remove boot options on this one for example, but like LaserJock says, it's very much just a GUI frontend to menu.lst.

At the moment, I've gotta say that neither of them are really as user-friendly as they should be, although for the moment I don't really have any suggestions on how to fix this, except to think about user cases
In particular it might be worth thinking a little about how grub itself is configured - many users might want to perform simple tasks (like change their desktop to boot windows / Ubuntu by default), but dont want to be exposed to the complications of different kernel versions.
In my mind, (this isnt really possible under the current GRUB) there should be an option per OS on the main grub screen (Ubuntu, WIndows Vista etc...), and advanced options like kernels / memory tests etc.. should be hidden in a sub-menu under the Ubuntu item.

An idea I have just had - produce an app that looks like grub will - users right-click on the background to change it, (and so will be able to see what grub will look like), click near the timer to change how long the menu will wait for etc...

---

### Post by the yawner on 2007-11-03
For Feisty users, SUM's available at [getdeb.net]("http://www.getdeb.net/app.php?name=Startup+Manager").
I've used this little app in Feisty just so I can change the usplash without opening a terminal.

---

### Post by amiga_os on 2007-11-03
> **glotz said:**
> I think people who cannot use the command line shouldn't definitely meddle with grub...

Very low priority in my opinion.

I really am sorry but I disagree with the spirit of this statement.  We should be careful when using this kind of logic, as it is a potential hindrance to new users of Ubuntu.  In fact, making statements like this has been a criticism of our community by some on the outside (I don't have a link to hand, sorry).

(Let me be clear - I totally respect your reasons for making the statement, but I disagree)

Long winded explanation follows:

There have been some great French philosophers - I haven't agreed with everything they've said - but there's been some great French thinkers in the last century.  However, despite my British GCSE in French, I don't understand enough French to read those French philosophers.  But - just because I don't communicate in their language, doesn't mean I can't or even shouldn't engage with their ideas through translation.  e.g. my reading of Satre when translated into English.

In the same way, the most immense barriers of Linux to me, weren't "not knowing what I was doing on a command line", it was "not knowing the correct *syntax* on the command line".  It's like moving from C++ to Python to Java... many of the same concepts in play (and many different ones), but the syntax is different, and therefore what I'm able to do in the different language is significantly below my competence level.

Someone who doesn't have a working knowledge of a *nix bash shell doesn't necessarily lack the understanding to usefully configure grub/lilo for his/her system.

Therefore... I think it's important to strive for a GUI replacement for virtually everything on our Ubuntu system.  Including making Start Up Manager available by default... and the user will get a warning about using it - and have to type their password.

GUI is slower and less effecient *if you know what the correct commands are*, but it does remove the barrier of knowledge - fishing around for the right dialogue to change something really does take less time than scouring man pages to find the right command.

So - I totally understand your concern (we don't want people screwing up their systems for just being curious!), but I really don't think that's a reason to hold back a good GUI.

---

### Post by masmre on 2007-11-03
Look this:
[http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391](http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391)
Very good editor, best at the moment...

sorry my englisch

---

### Post by Jimmy_r on 2007-11-18
> **Martje_001 said:**
> That doesn't work. It removes my Windows entries :(

SUM never removes anything.
Update-grub does though.

Please see this bugreport:
[https://bugs.launchpad.net/startup-manager/+bug/162074](https://bugs.launchpad.net/startup-manager/+bug/162074)

---

### Post by Jimmy_r on 2007-11-18
> **BlueSkyNIS said:**
> I had a problem using this app. I have had disabled memtest option and after that, my ubuntu never booted up. :( Even a boot screen wont show. ](*,) I got a kernel panic "cannot mount VFS" or something "please specify you root drive".

root was correctly specified in menu.lst but kernel just didn't want to boot up. ](*,) #-o I have tried /dev/sda values, UUID values but nothing helped. I think (correct me if I'm wrong) the problem was in initrd. :-k

I have a SATA II hard disk on intel 945P chipset. Don't know for sure where the problem was. Anyway I have just reinstalled the whole Ubuntu.

Sorry for my english, it's not my native language.

Hm, everything sum does when you use it to disable memtest86 is to open menu.lst, find the line looking like this:

# memtest86=true

It changes it to look like this:

# memtest86=false

And then it runs update-grub.
So the bug should be at a lower level in the system.

---

### Post by Jimmy_r on 2007-11-18
> **LaserJock said:**
> To throw more fuel on the fire this summer I mentored a Google Summer of Code student writing a Grub config GUI for Ubuntu. The project page is at [https://edge.launchpad.net/ubuntu-bootloader-manager](https://edge.launchpad.net/ubuntu-bootloader-manager) and the spec is at [https://wiki.ubuntu.com/BootloaderManager](https://wiki.ubuntu.com/BootloaderManager) . The last I blogged about it was [http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/](http://laserjock.wordpress.com/2007/08/18/gsoc-ubuntu-bootloader-manager-02/) but there has been significant UI changes since then.

I think the lack of projects is not the issue here :) but rather getting good ones integrated into Ubuntu and packaged up.

-LaserJock

It would be great if Bootloader Manager could cooperate with update-grub. As it is now, a run of update-grub will remove many of the changes done through Bootloader Manager.
That was also the reason that "[Kubuntu Grub Configuration Module]("https://blueprints.launchpad.net/ubuntu/+spec/kubuntu-grubconfig")" was deferred.

Cooperating with update-grub will, on the other hand, prevent editing of individual boot options(as is the case with SUM).

---

### Post by kornelix on 2007-11-19
I tend to install new distros to try them out and check if my software runs OK on them. I get sick of having to boot a grub CD-ROM to recover my boot menu with the many distros that were lost when the latest distro decided it was the only distro I wanted to boot.

I would like the Grub CD to have a 1-step wizard that looked at all partitions, found all existing distros, and made a boot menu containing all of them (and Windows too if present). Then it should display the menu and let me edit if I want to.

---

### Post by kreamibhutt on 2008-05-16
> **glotz said:**
> I think people who cannot use the command line shouldn't definitely meddle with grub...

Very low priority in my opinion.

He didn't ask you for your approval, he said he wanted decent tutorials on it.

If you can't contribute - then keep out of the functions and stay in the opinions.

---

### Post by BlueSkyNIS on 2008-05-16
> **Jimmy_r said:**
> Hm, everything sum does when you use it to disable memtest86 is to open menu.lst, find the line looking like this:

# memtest86=true

It changes it to look like this:

# memtest86=false

And then it runs update-grub.
So the bug should be at a lower level in the system.

Then is it possible that a bug in update-grub ruined my system back then, as you said before?

---

### Post by Niniel on 2008-07-11
Btw, I found this neat program, seems to be working ok, no negative side effects yet:
KGrubEditor
v0.5 is in the repos.
I essentially got it to set a background image... works well, if you can find a good image, of which there are not so many. Making one yourself is a bit tricky.
Still, cool piece of software.

---

### Post by smartboyathome on 2008-07-12
Not gonna be in Ubuntu though, Qt, not GTK. Still, I stand by if the person doesn't know how to edit grub, they shouldn't.

---

