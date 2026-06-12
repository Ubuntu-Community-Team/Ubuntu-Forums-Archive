---
title: "Ode to kde-core.. a faster KDE"
date: 2006-10-13
forum: The Cafe
---

### Post by aysiu on 2006-10-13
Only a handful of us have done [benchmarks on *kde-core* versus *kubuntu-desktop*](http://ubuntuforums.org/showthread.php?t=270326), but the consensus so far appears to be that *kde-core* is much faster than *kubuntu-desktop*.

Instructions for getting *kde-core*:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by kerry_s on 2006-10-14
Kde-core is faster to me, i moved away from kde long ago because it was slow. Now that i've learned to use the server install i've come full circle. I've tried all the desktops & wm's and found that the kde-core can be just as fast as those light weight systems. Kde has always had fantastic dual monitor support that's missing in the other wm's & de's. It's so fast sometimes the window will jump up faster than i can move the mouse to the other screen, i have mine setup to open on the screen the mouse is on. I just got up so forgive the rambling. ;)

---

### Post by aysiu on 2006-10-14
> **kerry_s said:**
> I just got up so forgive the rambling. ;) The rambling's fine. Good to know *kde-core* works well for you.

---

### Post by slimdog360 on 2006-10-14
> **kerry_s said:**
> Kde-core is faster to me, i moved away from kde long ago because it was slow. Now that i've learned to use the server install i've come full circle. I've tried all the desktops & wm's and found that the kde-core can be just as fast as those light weight systems. Kde has always had fantastic dual monitor support that's missing in the other wm's & de's. It's so fast sometimes the window will jump up faster than i can move the mouse to the other screen, i have mine setup to open on the screen the mouse is on. I just got up so forgive the rambling. ;)
server install all the way. Being able to eliminate all the stuff that I dont want/need, my kde desktop has never been so fast. Comparable to, if not faster then zenwalk.

---

### Post by fuscia on 2006-10-14
ihave been using kubuntu lately, but when i saw this thread, i decided to install kde-core and see if i thought it was faster (i had already done a clean install of ubuntu last night and only had gnome installed). it does seem faster, to me.

---

### Post by Jucato on 2006-10-14
Installing kde-core is indeed way faster than the stock kubuntu-desktop. I've tried this before and was impressed with the speed difference. However, I had more random app crashes (mostly Konqueror) using kde-core. I'm not sure why, though.

A word of caution though: using kde-core really just installs the "barebones" KDE. Some of the probably important things that won't get installed are HAL (Hardware Abstraction Layer), D-Bus (not sure how essential this one is), ACPI, CUPS, etc. These things may or may not be essential, depending on the user. The point is that you should know what you are doing or what you really need/want if you take this path.

---

### Post by aysiu on 2006-10-14
Jucato's right--*kde-core* is faster because it has a lot fewer services running than *kubuntu-desktop*, but it may not also have the full functionality you need.

If you're an advanced user or into researching what packages you need in addition to *kde-core*, go for it!

---

### Post by elettronicha on 2006-10-14
> **Jucato said:**
> Some of the probably important things that won't get installed are HAL (Hardware Abstraction Layer), D-Bus (not sure how essential this one is), ACPI, CUPS, etc. These things may or may not be essential, depending on the user. The point is that you should know what you are doing or what you really need/want if you take this path.
And that's why it's faster! Faster but also less services and stuff loaded and using RAM, obviously that's not good if I need them. I'm fairly sure kubuntu-desktop would reach those performances, if many things were disabled.

It would be interesting to know what are the differences between the two installations in terms of packages, loaded services and configurations.

---

### Post by aysiu on 2006-10-14
> **elettronicha said:**
> 
It would be interesting to know what are the differences between the two installations in terms of packages, loaded services and configurations. The difference is in the first post of this thread.

---

### Post by elettronicha on 2006-10-14
> **aysiu said:**
> The difference is in the first post of this thread.
Sorry, you're right and I'm not stupid, too. :D 
In the attachment there is what I've seen with Konqueror. So I've seen only 10 programs and I've suspected that there should be some other difference. And of course, if I open the page with Firefox, now I see the rest of the differences...

---

### Post by aysiu on 2006-10-14
> **elettronicha said:**
> Sorry, you're right and I'm not stupid, too. :D 
In the attachment there is what I've seen with Konqueror. So I've seen only 10 programs and I've suspected that there should be some other difference. And of course, if I open the page with Firefox, now I see the rest of the differences...
If you want an easier view of it, go here:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by maniacmusician on 2006-10-14
do you know if kde is any faster/better than kubuntu? most of those services listed are pretty essential for me, so i cant do with just the barebones. I'd rather just remove services later.

also, server installs are hard for me to do, because my wireless card doesn't work out of the box with dapper. probably wont with edgy either. so i have to do ndiswrapper first, and i dunno if i'm comfortable enough with that yet to do it all from the command line. anyways...is the kde package any better than kubuntu?

---

### Post by Bloodfen Razormaw on 2006-10-14
Kubuntu's slowness has nothing to do with services.  You can load those same services in KDE and it will run much faster than in Kubuntu.  Kubuntu is slow because it just breaks everything.

---

### Post by maniacmusician on 2006-10-14
right. i think i'll try going with the kde package on my edgy install.

---

### Post by claydoh on 2006-10-14
having used edgy for the past month or so, it feels like KDE gets to the desktop much faster than in dapper, the "status" icons in the spash don't seem to hang there, so I imagine they have done some good tweaks to building KDE. KDE itself does not feel any faster or slower than Dapper as far as I can tell.

I have not done any testing, but Edgy also boots much much faster. But I still turn off some things I will never use, such as hplip.

---

### Post by aysiu on 2006-10-14
> **Bloodfen Razormaw said:**
> Kubuntu's slowness has nothing to do with services.  You can load those same services in KDE and it will run much faster than in Kubuntu.  Kubuntu is slow because it just breaks everything.
What does it break? Kubuntu doesn't appear to have broken anything for me. Can you be more specific or link to a few threads?

---

### Post by 3rdalbum on 2006-10-15
Forget kde-core - On my Gnome machine I installed kdebase-bin and kdebase-data, plus Konqueror, and it rocks! (admittedly, it's nowhere near as fast as ubuntu-desktop)

---

### Post by elettronicha on 2006-10-15
> **aysiu said:**
> Kubuntu doesn't appear to have broken anything for me.
Same thing here... And I'm using Edgy. Something has still to be tuned, but I get no crashes at least and never got with Dapper.

---

### Post by chaosgeisterchen on 2006-10-15
Myths everywhere? 

I will try out with Edgy and kde-core-3.5.5

---

### Post by greggh on 2006-10-15
Well I haven't tried KDE-core yet, but I do have Kubuntu-desktop installed on my Ubuntu. The Ubuntu Gnome desktop I find very stable, practically no crashes. But whenever I log into Kubuntu KDE I get Sig11 crashes very often. I've stopped using Kubuntu and only use Ubuntu because of it. I'm going to try a fresh server install with KDE-core to see if I can run KDE on Ubuntu without all those Sig11 crashes.

---

### Post by ComplexNumber on 2006-10-15
> But whenever I log into Kubuntu KDE I get Sig11 crashes very often.tell me about it. that happens on most kde's. it happens all the time on fedora, with konqueror being the worst offender. kde and kde apps on suse crashes now and again, but not as much as others that i've tried.

---

### Post by arox on 2006-10-15
Anyone uded KDE Light?

Openbox instead of Kwin, fbpanel instead of kicker

---

### Post by awakatanka on 2006-10-15
> **ComplexNumber said:**
> tell me about it. that happens on most kde's. it happens all the time on fedora, with konqueror being the worst offender. kde and kde apps on suse crashes now and again, but not as much as others that i've tried.
Using only kde and never have seen that error.

I'm interested in a speed test between  kubuntu and kde-core against Mepis 6. It has a ubuntu base.

What kind of measure appz you used Aysiu? our was it plain old stopwatch? I wanna try a test between them.

---

### Post by aysiu on 2006-10-15
Plain, old stop-watch. I'm old school. So, there's probably a margin of error of a second or two.

---

### Post by mips on 2006-10-17
I'm gonna do this when edgy is released.

We just need a nice Sabayon like theme with cool fonts for it though.

Edit: I'm even considering straight Debian (etch)

---

### Post by mips on 2006-10-17
> **aysiu said:**
> 
If you want to start from scratch, you can do a server install from the Alternate CD and then 
```
sudo aptitude update && sudo aptitude install kde-core
sudo /etc/init.d/kdm start
``` 


Stupid question but what about Xorg ?

I'm busy downloading Debian Etch netinstall iso and I'm keen to try a kde-core install.

---

### Post by aysiu on 2006-10-17
I would assume a desktop environment would have Xorg as a dependency. Try it out.

---

### Post by chaosgeisterchen on 2006-10-17
Hmh.. dependencies are very hard to find out if they have several levels.

But I assume **aysiu** is completely right. It won't run otherwise, so Ubuntu will certainly want to install it.

---

### Post by kerry_s on 2006-10-17
No, xorg is not a dependency, i'll usally install x-window-system-core. I usally do this on a server install->

sudo su
nano /etc/apt/sources.list  <-(#)out the cdrom and un(#) all repos.
apt-get install x-window-system-core xterm kdm kde-core synaptic


on any server install i'll usally always start with "apt-get install x-window-system-core xterm" to make sure i get all the x stuff needed.

example:
apt-get install x-window-system-core xterm (xdm,wdm,gdm,kdm, or none) (DE or WM-> fluxbox,openbox,blackbox,icewm,wmaker,gnome-core,kde-core,..)

---

### Post by chaosgeisterchen on 2006-10-17
Oh. I did not know that. Thanks for informing me :)

---

### Post by aysiu on 2006-10-17
I also didn't know that. Good to know.

---

### Post by kerry_s on 2006-10-17
Well, i only do server install and build up now. I haven't installed a full desktop in ages. ;)  I love customizing my system to me.

---

### Post by Jucato on 2006-10-17
Just a little tip of my own:

- The default KControl does not contain some of the modules that people might have gotten used to, like Display, User Accounts, etc. To have this, you must install the *kde-guidance* package. 

- installing kde-core, the only apps you would find on the K Menu are Konsole, Konqueror, KInrfoCenter, KSysGuar, KControl, Kate, KJobViewer, KTip, KHelp, and KFind. Of course, there are other apps installed, but they might not be visible (like KWin, Kicker, etc.)

- last time I tried this, KDM was not installed together with kde-core, so you would have to install it yourself to. Package name is *kdm*.

So basically, starting from a server (minimal) install, you would do this:

```
sudo apt-get install x-window-system-core kde-core kdm
```

---

### Post by aysiu on 2006-10-17
*kdm*, at least as of Dapper, is definitely a dependency of *kde-core*'s. No need to install that separately.

---

### Post by Bloodfen Razormaw on 2006-10-17
> What does it break? Kubuntu doesn't appear to have broken anything for me. Can you be more specific or link to a few threads?
For one example, Konqueror is deliberately broken to make many features inaccessible in an apparent effort to make it "simpler."  They apparently are not aware of the usability tests openusability has done on Konqueror which found that users were very comfortable with it.

> kdm, at least as of Dapper, is definitely a dependency of kde-core's. No need to install that separately.
I think it actually is a recommend in Dapper, not a dependency.  If you use aptitude with default settings (which treat recommends as dependencies) you will get kdm.  If you use apt-get or aptitude with Recommends-Important=false, you won't get it automatically.

To be sure, standard KDE is much more than kde-core.  Ubuntu has packages for all the standard KDE software and metapackage for its modules.  "kde-core" is the Debian metapackage for wrapping around the official KDE module kdebase.  To go really slimmed down you can pick and choose individual software from within kdebase (this doesn't save much space, but it does save a lot of menu clutter).  ksmserver/kdm is necessary for working kdm if you do that.

On the other end of the spectrum, since many people seem to want a non-kubuntu KDE desktop but want something complete out of the box, "aptitude install kde" will get you a full standard KDE install.  Install the recommends with it and you should get all the services like HAL/dbus you would have on kubuntu, but it should still be faster.

---

### Post by aysiu on 2006-10-17
You're right--KDM's a recommend. I didn't notice the green diamond next to it.

---

### Post by maniacmusician on 2006-10-18
using aptitude would automaticall install the recommends, yes? unless you have Recommends-Important=false?

---

### Post by Bloodfen Razormaw on 2006-10-18
Right.  Adding
```
Aptitude::Recommends-Important "false";
```
to apt.conf makes it treat recommends normally.  Otherwise it treats them as dependencies.  Good way to choose if you want slim or full-featured defaults.

Edit: Also add Aptitude::Keep-Recommends "true"; if you make recommends unimportant.  That way you can manually install recommends and set them to auto without them being uninstalled right away, but they will be uninstalled if everything that recommends them get uninstalled.

---

### Post by chaosgeisterchen on 2006-10-18
Hmh, it would be unlogical to create a dependency on kdm by kde-core - as it also works with xdm and gdm as well.

---

### Post by aysiu on 2006-10-18
Kubuntu works with XDM and GDM as well, but *kubuntu-desktop* depends on KDM.

---

### Post by chaosgeisterchen on 2006-10-18
Hmh, are we talking about kde-core or kubuntu-desktop here?

**kubuntu-desktop** is some metapackages with aim to provide a full KDE solution. It clearly wants to use KDM to keep it all KDE-only.

---

### Post by Bloodfen Razormaw on 2006-10-18
> kubuntu-desktop is some metapackages with aim to provide a full KDE solution. It clearly wants to use KDM to keep it all KDE-only.
Kubuntu doesn't use exclusively KDE software, e.g. it uses oo.o for its office suite.  You can get a non-kubuntu desktop that includes kdm with the kde-desktop task.

---

### Post by chaosgeisterchen on 2006-10-18
*sigh* you're right. But they are strictly against using KOffice as it is inferior.

But there aren't any GTK-dependancies.

---

### Post by ashrack on 2006-10-23
I did a server install and then install KDE-CORE!
I must say I like my system now much better and its also less slugish!
Onto my question:
How do I get the SYSTEM SETTINGS in K MENU back? I know this was in KUBUNTU-DEKSTOP?

---

### Post by fuscia on 2006-10-23
> **ashrack said:**
> I did a server install and then install KDE-CORE!
I must say I like my system now much better and its also less slugish!
Onto my question:
How do I get the SYSTEM SETTINGS in K MENU back? I know this was in KUBUNTU-DEKSTOP?

you have to add it from the package manager as it is not part of kde-core by default. once you do, it will appear in your menu.

---

### Post by Jucato on 2006-10-23
> **ashrack said:**
> I did a server install and then install KDE-CORE!
I must say I like my system now much better and its also less slugish!
Onto my question:
How do I get the SYSTEM SETTINGS in K MENU back? I know this was in KUBUNTU-DEKSTOP?

What is installed with kde-core is the original KDE Control Center, **KContro**. To get System Settings, you need to install the package *kde-systemsettings*. You might also need to install Adept or Synaptic if you want an APT frontend. kde-core doesn't install anything like that.

---

### Post by ashrack on 2006-10-23
@JUCATO
I've installed SYNAPTIC, FIREFOX,OOO the second that KDE-CORE was installed!
Tanx for the name of the package for SYSTEM-SETTINGS!

@ALL
I reLLY liked the theme that KUBUNTU had! And thus I've install KUBUNTU ARTSWORK but in KCONTROL I still can't find any new themes. How do I go about doing this?

---

### Post by chaosgeisterchen on 2006-10-23
You have to install the window decorations 'crystal' from kde-look.org.

---

### Post by mips on 2006-10-23
Has anyone tried this on Edgy yet ? Is there still a big difference ?

I'm about to dl the Edgy alternate cd, close enough to official release for me.

---

### Post by maniacmusician on 2006-10-23
i'm trying to do a server install with xubuntu edgy alternate cd, but it's not happening. the latest xubuntu edgy available is beta, and it just doesnt work for me. When i download, the md5sum checks out for me, but when i use it in vmware and "check cd for defects" it says the file is corrupted, and the install won't work. doesn't work if I burn it and use it that way either. but since it's just a server install, i guess i  can use the alternate cd from any derivate and it will end up being the same.

---

### Post by ashrack on 2006-10-24
> **mips said:**
> Has anyone tried this on Edgy yet ? Is there still a big difference ?

I'm about to dl the Edgy alternate cd, close enough to official release for me.

I tried it on EDGY RC 3ago! And yes, there's still a big difference! 
I must say that Im rather enjoying this new SLIMMED down KUBUNTU! Be4 I always had to remove A LOT of packages but now I only install what I want/need.

---

### Post by mips on 2006-10-24
Strange, I just installed edgy+kde-core and it does not feel any faster. If anything the bootup feels slower.

kde-core is going to require a lot of fiddling/customisation to get it to a pleasant desktop experience for me.

Oh well, no going back now, the egit that I am I downloaded the wrong edgy iso. I downloaded ubuntu instead of kubuntu ](*,)  And i'm not installing the kubuntu-desktop of the net as it takes to much bandwidth.

Another thing, the cli install did not give me a option for grub but instead installed LILO, why ???

I will have to start a new thread in order to figure out how to get certain functionality back. Stuff like my display setting in control centre, session end to take me back to the login screen instead of the cli.

---

### Post by kerry_s on 2006-10-24
> **mips said:**
> Strange, I just installed edgy+kde-core and it does not feel any faster. If anything the bootup feels slower.

kde-core is going to require a lot of fiddling/customisation to get it to a pleasant desktop experience for me.

Oh well, no going back now, the egit that I am I downloaded the wrong edgy iso. I downloaded ubuntu instead of kubuntu ](*,)  And i'm not installing the kubuntu-desktop of the net as it takes to much bandwidth.

Another thing, the cli install did not give me a option for grub but instead installed LILO, why ???

I will have to start a new thread in order to figure out how to get certain functionality back. Stuff like my display setting in control centre, session end to take me back to the login screen instead of the cli.


What file system did you use? If i remember right if you use xfs it will select lilo because grub is incompatiable with xfs. I use JFS, the installer errors the first time, just go back and try again and it will install the second time(bug?)

For display-> apt-get install kde-guidance

Login screen-> did you install kdm?-> apt-get install kdm

Pic of my edgy+kdecore->

---

### Post by mips on 2006-10-24
> **kerry_s said:**
> What file system did you use? If i remember right if you use xfs it will select lilo because grub is incompatiable with xfs. I use JFS, the installer errors the first time, just go back and try again and it will install the second time(bug?)

For display-> apt-get install kde-guidance

Login screen-> did you install kdm?-> apt-get install kdm

Pic of my edgy+kdecore->

Well I had /boot which is ext3 then my other partitions are xfs. This has worked for me before on every occasion. Why now does it not want to work ?

Thanks for the display tip.

I have subsequently been experiencing kernel panicks. THis is gonna be a long day :mad:

---

### Post by hopstah on 2006-10-24
can anybody explain to me why loading this page in firefox crashes kde?  but i can view it in konqueror just fine?  does anybody else have this problem?

---

### Post by kerry_s on 2006-10-24
> **hopstah said:**
> can anybody explain to me why loading this page in firefox crashes kde?  but i can view it in konqueror just fine?  does anybody else have this problem?

Nope, works here->

---

### Post by kerry_s on 2006-10-24
> **mips said:**
> Well I had /boot which is ext3 then my other partitions are xfs. This has worked for me before on every occasion. Why now does it not want to work ?

Thanks for the display tip.

I have subsequently been experiencing kernel panicks. THis is gonna be a long day :mad:


Did you make sure you selected your boot partion during install? I would just format the partions and try again. Some times the installer can be a bit buggy, it took me 3 tries to get a working edgy rc install. I hope the release is better, i plan on wiping all my drives so i can clean up my setup.

---

### Post by mips on 2006-10-24
> **kerry_s said:**
> Did you make sure you selected your boot partion during install? I would just format the partions and try again. Some times the installer can be a bit buggy, it took me 3 tries to get a working edgy rc install. I hope the release is better, i plan on wiping all my drives so i can clean up my setup.

Ok, finally some success. I always format my partitions and make sure the mount points and file system type is specified.

I remembered that I installed a 10gb drive recently while dapper was installed to be used for bsd. Dapper was fine with it. My main drives are sata. The 10gb ata drive was seen as hd0 and somehow i think it screwed around with the installer.

On my 4th try installing edgy I disconnected the drive beforehand and everything worked like a charm.

---

### Post by Somal on 2006-10-25
hi, i new here, but i have also tried server install + kde-core and it feels faster than kubuntu. But how do i get kde-core to 3.5.5? My kde is only 3.5.2 now.

---

### Post by mips on 2006-10-25
> **Somal said:**
> hi, i new here, but i have also tried server install + kde-core and it feels faster than kubuntu. But how do i get kde-core to 3.5.5? My kde is only 3.5.2 now.

I assume you are using Dapper ??? 
Try [http://kubuntu.org/announcements/kde-355.php](http://kubuntu.org/announcements/kde-355.php) and then see if you can upgrade your existing kde-core from there.

I installed Edgy Eft beta which is about 1 day away from official release. 
Edgy already has 3.5.5 in the repositories so you might want to consider installing edgy server + kde-core as an alternative way of getting 3.5.5.

---

### Post by Somal on 2006-10-25
wow edgy 1 day from release? then maybe i wait :D

---

### Post by mips on 2006-10-25
> **Somal said:**
> wow edgy 1 day from release? then maybe i wait :D

Eh, they have moved release dates before so don't blame me if it's not available on the 26th. Either way it should be out before end Oct.

---

### Post by chaosgeisterchen on 2006-10-25
I am confident edgy is fully on **current** schedule.

---

### Post by ashrack on 2006-10-25
definetly EDGY is gonna get released with in the designated time! THey really cant reschedule it 1 day B4 the release and also they have to get back into GNOME schedule

---

### Post by ahaslam on 2006-10-25
Hi, 

I installed 'kdebase' & it felt much quicker than kde-desktop.
Kdebase is the minimal package set necessary to run KDE as a desktop environment, what does 'kde-core' add? - I certainly wouldn't want any more apps. Kdebase still appears heavyweight compared to gnome, but it actually feels a little quicker & has a few extra options.

Cheers,

Tony.

---

### Post by Jucato on 2006-10-26
Anthony, you can look at the depends of kdebase and kde-core to see what kde-core adds. AFAIK, kde-core installs kdebase plus a few others.

I really want to do a kde-core install again. The only thing that's holding me back is the thought of not being able to answer support questions, just because I don't have the Kubuntu defaults installed.

Btw, have you noticed other things that might be important, but wasn't installed with kde-core? I noticed CUPS, HAL, and DCOP (or was it DBus) not being installed.

---

### Post by mips on 2006-10-26
I found that to get kde-core to the where i wanted it was going to take me to much time and use to much bandwidth (which I don't understand)

Weird thing is kubuntu-desktop was about a 200mb download, which was less than if i added various packages individually. I did dummy aptitude runs to measure bandwidth required and then cancelled the install when prompted for yes/no. Can someone please explain this to me as it does not make sense.

kde-core is much faster than kubuntu-desktop I must say. Kubuntu Edgy still boots in 34secs which is great.


> **Jucato said:**
> Anthony, you can look at the depends of kdebase and kde-core to see what kde-core adds. AFAIK, kde-core installs kdebase plus a few others.

I really want to do a kde-core install again. The only thing that's holding me back is the thought of not being able to answer support questions, just because I don't have the Kubuntu defaults installed.

Btw, have you noticed other things that might be important, but wasn't installed with kde-core? I noticed CUPS, HAL, and DCOP (or was it DBus) not being installed.

---

### Post by mips on 2006-10-26
> **Somal said:**
> wow edgy 1 day from release? then maybe i wait :D

Edgy is out so your wait is over ;)

---

### Post by ashrack on 2006-10-26
> **mips said:**
> I found that to get kde-core to the where i wanted it was going to take me to much time and use to much bandwidth (which I don't understand)

Weird thing is kubuntu-desktop was about a 200mb download, which was less than if i added various packages individually. I did dummy aptitude runs to measure bandwidth required and then cancelled the install when prompted for yes/no. Can someone please explain this to me as it does not make sense.

kde-core is much faster than kubuntu-desktop I must say. Kubuntu Edgy still boots in 34secs which is great.
Because KUBUNTU is installed of the CD! But when U install KDE-CORE U do a server install and then u COMMENT the CDROM in sources.list and thus it installs the packages that are on the CDROM from the internet!
I set my sources.list to also have the CDROM in and thus it only installs the changes from the net

---

### Post by ashrack on 2006-10-26
1.
I installed:
```
kubuntu-default-settings
```
because I like the kUBUNTU ICONS and its look! But I hate the NEW K MENU that cames with it. How can I revert back to the K MENU that KDE-CORE package use?

2.
I really miss COPY-TO dialog in KONQUERER from which U could just right click on a file and then select COPY-TO and then the path to where U want it installed! How can I get this option in KDE-CORE?

---

### Post by maniacmusician on 2006-10-26
kubuntu-default-settings probably cripples konqueror as well...bad move IMHO. there was probably another way you could've gotten the icons.

---

### Post by GeneralZod on 2006-10-26
> **ashrack said:**
> 
2.
I really miss COPY-TO dialog in KONQUERER from which U could just right click on a file and then select COPY-TO and then the path to where U want it installed! How can I get this option in KDE-CORE?

I'm fairly sure this is the "Kuick" plug-in, and is contained in the konq-plugins package.

---

### Post by ashrack on 2006-10-26
> **maniacmusician said:**
> kubuntu-default-settings probably cripples konqueror as well...bad move IMHO. there was probably another way you could've gotten the icons.
I basicly just installed it so I could copy off all the theming and icons! And will remove it soon.
But still I would like to know how to revert to the old K MENU? Since some of my buddies would like the old K MENU on their KUBUNTU install?

> **GeneralZod said:**
> I'm fairly sure this is the "Kuick" plug-in, and is contained in the konq-plugins package.
Thank U, worked like charm!

@ALL
Just found out another thing that I just can't live without:
When I inserted a CDROM I had to manually mount it! What must I do so the CDROM or any other removable device(USB) will get automounted and placed on the desktop?

ps. I'm just loving this KDE-CORE ride! Since I can install just the things I want!

---

### Post by mips on 2006-10-26
> **ashrack said:**
> Because KUBUNTU is installed of the CD! But when U install KDE-CORE U do a server install and then u COMMENT the CDROM in sources.list and thus it installs the packages that are on the CDROM from the internet!
I set my sources.list to also have the CDROM in and thus it only installs the changes from the net

Wrong. I did this from the **Ubuntu** alternate cd and not the kubuntu one.

---

### Post by ashrack on 2006-10-27
yes I know! U installed it from the alternative CD and U chose the COMMAND LINE! And then U uncommented the SOURCES.LIST and did 
apt-get install KDE-CORE!
But If U would left UBUNTU CDROM in the SOURCES.LIST it would only DL packages that arent on the KUBUNTU alternative CD

---

### Post by mips on 2006-10-27
> **ashrack said:**
> yes I know! U installed it from the alternative CD and U chose the COMMAND LINE! And then U uncommented the SOURCES.LIST and did 
apt-get install KDE-CORE!
But If U would left UBUNTU CDROM in the SOURCES.LIST it would only DL packages that arent on the KUBUNTU alternative CD

I don't think you read my post correctly.
I used the Ubuntu alternate cd and NOT the Kubuntu one.
The ubuntu cd rom IS still in the sources list.

Nevermind, it's not important now as it's installed.

---

### Post by ashrack on 2006-10-27
aha, my bad. Should've read more carefuly! Well if U used the UBUNTU ALTERNATIVE CD than its normal that it had to DL all of the packages for KDE since only GNOME is on the UBUNTU cd!

---

### Post by ashrack on 2006-10-27
Anyone knows how to do the following with KDE-CORE:
1. How can I revert back to the K MENU that KDE-CORE package use?

2.When I inserted a CDROM I had to manually mount it, but I want it automounted and the icon placed on desktop! How can I do this, its a MUST!!

---

### Post by Jucato on 2006-10-27
> **ashrack said:**
> Anyone knows how to do the following with KDE-CORE:
1. How can I revert back to the K MENU that KDE-CORE package use?

2.When I inserted a CDROM I had to manually mount it, but I want it automounted and the icon placed on desktop! How can I do this, its a MUST!!

1. The K Menu used by kde-core is simply your regular K Menu with 5 recently used apps at the top, with Settings and System menu near the bottom, and with the default KDE 3.5 side image.

2. I'm not sure if this is the right answer, but you might have to install *hal*. I have that, and my CD's mount properly and appear on the desktop.

---

### Post by vayu on 2006-10-28
> **ComplexNumber said:**
> tell me about it. that happens on most kde's. it happens all the time on fedora, with konqueror being the worst offender. kde and kde apps on suse crashes now and again, but not as much as others that i've tried.

I have a very solid KDE setup with Dapper, and similar stability with lightning speed in FreeBSD.

For me KDE rocks.  I like Gnome too, but it's slow, and like the Mac there's this simplicity thing going on that's ok, but there are too many times that I can't get it to do what I want.

---

### Post by vayu on 2006-10-28
Personally, even though everyone ravs about it I always think it's all the python stuff.  Does anyone know how fast is python compared to whatever the DE base programs are written in (I would think c or c++)?

---

### Post by ashrack on 2006-10-28
> > **Jucato said:**
> 1. The K Menu used by kde-core is simply your regular K Menu with 5 recently used apps at the top, with Settings and System menu near the bottom, and with the default KDE 3.5 side image.
I like that 5recently APPS on top. So how can I get that back?

[QUOTE]2. I'm not sure if this is the right answer, but you might have to install *hal*. I have that, and my CD's mount properly and appear on the desktop.
[/QUOTE]
I already installed it but CDROM still wont automount!
Any other ideas

---

### Post by ComplexNumber on 2006-10-28
> **vayu said:**
> Personally, even though everyone ravs about it I always think it's all the python stuff.  Does anyone know how fast is python compared to whatever the DE base programs are written in (I would think c or c++)?
python is a lot slower.

---

### Post by kuja on 2006-10-28
> **vayu said:**
> Personally, even though everyone ravs about it I always think it's all the python stuff.  Does anyone know how fast is python compared to whatever the DE base programs are written in (I would think c or c++)?
GNOME = C, KDE = C++, generally
> **ComplexNumber said:**
> python is a lot slower.
And by A LOT at that. Then again, not an entirely fair comparison either. Kind of like comparing C to a shell script, it's really not a fair comparison to compare a compiled language to an interpreted language.

---

### Post by Jucato on 2006-10-28
> **ashrack said:**
> I already installed it but CDROM still wont automount!
Any other ideas

Check if *pmount* was installed. It should have been installed together with HAL. Other than that, I'm at a loss. I didn't have this problem.

Oh, you might want to check out your fstab, too.

---

### Post by GeneralZod on 2006-10-29
On Python vs C/C++ for desktop apps: It's worth noting that the majority of most apps spend 90% of their time either waiting for user input, or in the C/C++ libraries (GNOME libs; GTK libs; Qt libs; KDE libs, etc) so while Python is definitely far slower than C/C++, in practise it tends to make not as much difference as you'd think as "less" Python code tends to be run in comparison to the supporting C/C++ code.

---

### Post by geearf on 2006-10-31
I'm flagging this cause I'm interested :)

Kubuntu is really too slow :(

---

### Post by GarethMB on 2006-11-13
Anyone know the names of the modules that control suspend and hibernate??

---

### Post by chaosgeisterchen on 2006-11-13
I assume that it is called **ksuspend**...

---

### Post by ashrack on 2006-11-13
I've done this procedure on two installation already and its great when U have internet conectivity!
But if U are without internet than there is no KDE-CORE package! And what do I do  then?
I tried installing KDM,KWIN, XORG, KICKER, KONSOLE and their recomandations in APTITUDE... Whatever I did I couldn't get to the desktop! ONly the KDM opens and when I typed my USERNAME and PASS I would only get a green background.

---

### Post by kuja on 2006-11-13
Rather than having internet connectivity, use the DVD to do the install. It is quite a bit more comprehensive when it comes to what packages it includes. To be honest, the DVD isn't even full though, a pity really. One thing I liked about Debian was that its installation came on two DVDs, both of them completely full.

---

### Post by Sushi on 2006-11-13
> **GeneralZod said:**
> On Python vs C/C++ for desktop apps: It's worth noting that the majority of most apps spend 90% of their time either waiting for user input, or in the C/C++ libraries (GNOME libs; GTK libs; Qt libs; KDE libs, etc) so while Python is definitely far slower than C/C++, in practise it tends to make not as much difference as you'd think as "less" Python code tends to be run in comparison to the supporting C/C++ code.

Well, that's not really valid. I mean, when I'm typing or clicking something I'm not thinking that "damn this thing is slow". But when I'm waiting for the app to load, or do the things I told it to do, THEN I might be thinking just that. And if Python is slower, that's where it would show.

---

### Post by shining on 2006-11-13
> **Sushi said:**
> I mean, when I'm typing or clicking something I'm not thinking that "damn this thing is slow".

That's exactly the point.

---

### Post by ashrack on 2006-11-13
> **kuja said:**
> Rather than having internet connectivity, use the DVD to do the install. It is quite a bit more comprehensive when it comes to what packages it includes. To be honest, the DVD isn't even full though, a pity really. One thing I liked about Debian was that its installation came on two DVDs, both of them completely full.

But what if a DVD reader isnt present! How else can U do KDE-CORE install?

---

### Post by kuja on 2006-11-13
If a DVD reader isn't present, why not shell out $15 to get one? It's not like it's expensive, like the $700+ bluray drives.

---

### Post by Brando569 on 2006-11-16
edited, nevermind

---

### Post by Brando569 on 2006-11-17
i tried this in edgy and wow what a difference, i think im gonna use this as my main system (i have a kubuntu installation from like a few days ago)

---

### Post by chaosgeisterchen on 2006-11-17
The speed improvements are significant, aren't they? Well, I strive for a better download limit to try it out for myself :(

---

### Post by Brando569 on 2006-11-17
i have a big problem, when i restarted kde kdepanel doesnt wanna launch anymore so i dont have a k menu :?

---

### Post by nickless on 2006-11-17
> **Bloodfen Razormaw said:**
> 
On the other end of the spectrum, since many people seem to want a non-kubuntu KDE desktop but want something complete out of the box, "aptitude install kde" will get you a full standard KDE install.  Install the recommends with it and you should get all the services like HAL/dbus you would have on kubuntu, but it should still be faster.

Is this true? :D Im pretty lazy. 
I will probably need most of the packages anyway and kubuntu-desktop is maybe alright, too... but if its faster with kde or kde-core... you almost always get me with speed :-| 
So, did anyone try that?

---

### Post by podunk on 2006-11-17
I have Kubuntu Dapper, and it ran OK. I tried to compile and install a game, and Adept said I had a broken package.

While I was looking through Adept chasing down the broken libray file - I saw a whole bunch of stuff that had kde in it that wasn't installed.

Reading around, I found some kubuntu repositories, added them and installled *everything* that KDE in it. KDE core, kde-admin, kelibs, kde-games - just everything I could find.

Ran like a charm! Fixed the broken libray file and actually sped computer up.

Konqueror is just the most amazing application I've ever seen. File browser, web browser, hell it even checks your spelling.

Plus, the little icons bounce up and down when you open an app. :-)

---

### Post by mips on 2006-11-17
> **podunk said:**
> 

Plus, the little icons bounce up and down when you open an app. :-)

lol, I find that annoying and is the first thing i switch off.

---

### Post by ashrack on 2006-11-17
> **kuja said:**
> If a DVD reader isn't present, why not shell out $15 to get one? It's not like it's expensive, like the $700+ bluray drives.
Whatever! I just want to know how to install KDE-CORE without an inet connection? And please stop with the u can get a DVD-rom for very little

---

### Post by mips on 2006-11-17
> **ashrack said:**
> Whatever! I just want to know how to install KDE-CORE without an inet connection? And please stop with the u can get a DVD-rom for very little

I'm not sure but maybe you can insert the cd, add it to your repos if it's not already there and uninstall the kubuntu desktop, then add kde-core.

---

### Post by ashrack on 2006-11-17
MIPS
It would be a fresh install of OS! 
And I already have set the CDROM in the APT/sources!

---

### Post by shining on 2006-11-17
> **mips said:**
> lol, I find that annoying and is the first thing i switch off.

eheh, me too. That and the system sounds also.

---

### Post by chaosgeisterchen on 2006-11-17
> **shining said:**
> eheh, me too. That and the system sounds also.

Good point, I do that as well. Just after setting KDE to start with an empty session every time I start it up.

---

### Post by shining on 2006-11-17
> **chaosgeisterchen said:**
> Good point, I do that as well. Just after setting KDE to start with an empty session every time I start it up.

Ah well, restoring the previous session used to annoy me at the beginning, especially because I left several windows opened, that I wouldn't need at next boot.
So now, I just close every apps before shutdown, except the few ones I might want at next boot, like amarok.

---

### Post by chaosgeisterchen on 2006-11-17
> **shining said:**
> Ah well, restoring the previous session used to annoy me at the beginning, especially because I left several windows opened, that I wouldn't need at next boot.
So now, I just close every apps before shutdown, except the few ones I might want at next boot, like amarok.

I also have those. But they always have a symlink in **~/.kde/Autostart/**.

The likelihood of corrupt processes dragged along when always using a already used session is  far too high for me. I just want a clean KDE started every time - with the applications I want it to load on startup.

---

### Post by kverde on 2006-11-18
I just tried this and it does make things snappier.  

The only complaint I have is that fonts look pretty bad.  Any tips on improving the look of the fonts?

---

### Post by fuscia on 2006-11-18
> **kverde said:**
> I just tried this and it does make things snappier.  

The only complaint I have is that fonts look pretty bad.  Any tips on improving the look of the fonts?


do you have anti-aliasing turned on?

---

### Post by mips on 2006-11-18
> **kverde said:**
> I just tried this and it does make things snappier.  

The only complaint I have is that fonts look pretty bad.  Any tips on improving the look of the fonts?

Make sure you use the same fonts as the defaults in Dapper/Edgy and turn on anti-aliasing as suggested above.

---

### Post by garba on 2006-11-18
actually, kde-core brings in way too much stuff for my tastes, if you really want to start from scratch just install kdelibs4c2a and kdebase-bin, this way you'll get rid of useless junk such as ktip kpersonalizer and so on... and most of all, i would suggest you take a peek into /usr/bin/startkde and the messy X session configuration files, you can learn a lot browsing through those files ;)

---

### Post by shining on 2006-11-19
> **chaosgeisterchen said:**
> I also have those. But they always have a symlink in **~/.kde/Autostart/**.

The likelihood of corrupt processes dragged along when always using a already used session is  far too high for me. I just want a clean KDE started every time - with the applications I want it to load on startup.

I don't think I ever had corrupt processes dragged along, but I can't tell for sure. I never noticed it.
But well, I configured it like you, just to be on the safe side :)

---

### Post by Jucato on 2006-11-25
**My kde-core Adventures**

I should have already written and posted this weeks ago. But lazy as I am, I only finished this lately. Anyway, for your enjoyment (hopefully):

[http://jucato.org/kde/kde-core.html](http://jucato.org/kde/kde-core.html)

EDIT: changed the URL

---

### Post by Brando569 on 2006-11-30
i just did an x64 server install of edgy and it is freaking amazing! its so fast

---

### Post by ashrack on 2006-12-01
Me aswell  couldn't believe the speed difference. 
But now am trying GENTOO and the speed is greater than even with KDE-CORE

---

### Post by greggh on 2006-12-01
> **garba said:**
> actually, kde-core brings in way too much stuff for my tastes, if you really want to start from scratch just install kdelibs4c2a and kdebase-bin, this way you'll get rid of useless junk such as ktip kpersonalizer and so on... and most of all, i would suggest you take a peek into /usr/bin/startkde and the messy X session configuration files, you can learn a lot browsing through those files ;)

Has anyone else compared going with just kdelibs4c2a (every library that all kde apps require) and kdebase-bin, as opposed to installing the bigger kde-core? I'm trying to decide which one is the better install method.

---

### Post by fuscia on 2006-12-01
> **greggh said:**
> Has anyone else compared going with just kdelibs4c2a (every library that all kde apps require) and kdebase-bin, as opposed to installing the bigger kde-core? I'm trying to decide which one is the better install method.

after reading your post, i just installed kde-base and a few apps (amarok, a couple of games, kwifimanager and the like). seems fine and seems fast (but that could be just gas).

---

### Post by Brando569 on 2006-12-01
as someone mentioned earlier, doing an edgy server install and then kde-core crashes alot. they arent deadly crashes, just odd/annoying ones like when i close kaffiene it will be like "kaffiene crashed" or when i got to any myspace page that has music/flash it will go crazy and freeze since i have neither flash or mplayer installed (i decided to try out edgy 64) if i could get rid of these crashes it would be amazing. the wierdest crash that i get is "an unknown applications had crashed" and nothing happens and it will happen like three or four times in a row, pretty odd i must say myself

---

### Post by fuscia on 2006-12-01
> **Brando569 said:**
> as someone mentioned earlier, doing an edgy server install and then kde-core crashes alot. they arent deadly crashes, just odd/annoying ones like when i close kaffiene it will be like "kaffiene crashed" or when i got to any myspace page that has music/flash it will go crazy and freeze since i have neither flash or mplayer installed (i decided to try out edgy 64) if i could get rid of these crashes it would be amazing. the wierdest crash that i get is "an unknown applications had crashed" and nothing happens and it will happen like three or four times in a row, pretty odd i must say myself

i'll bet kaffeine is the culprit. i was fine until i installed it, then 'crasherooni'. i dumped it and am back to trim bliss.

---

### Post by jordoex on 2006-12-09
kde-core is also faster and much more complete than even xubuntu desktop, especially since you have more control over what fancy stuff you have enabled. I'm running it very well on my P2 128 MB.

---

### Post by GSF1200S on 2007-05-04
I like KDE the best, and it seems installing the KDE core and building from there provides the fastest KDE.

I love Ubuntu/Kubuntu. I want to stick with this community and build on it. But, I want a very basic install that I can build on.

Where might I find info on a server install? Is it noticeably faster than a KDE core install?

Thanks...

---

### Post by aysiu on 2007-05-04
Start here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

It is definitely faster than KDE, since KDE is a full desktop environment. A server install has no GUI (graphical user interface), and a barebones install will use a lightweight window manager like IceWM or Fluxbox.

---

### Post by GSF1200S on 2007-05-04
Also, Im a little confused about the Kubuntu download.. It only shows AMD64 and i386 in the download list, but I have a dualcore, which I think would need an i686 download or generic.. I missing something?

Im really going for an optimized KDE here.

Ill even try 64 bit.. ill have to do some research though :)

---

### Post by aysiu on 2007-05-04
Well, there is basically i386 and AMD64.

Unless you have a 64-bit processor, you want i386.

Have you tried following these instructions?
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by GSF1200S on 2007-05-04
> **aysiu said:**
> Start here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

It is definitely faster than KDE, since KDE is a full desktop environment. A server install has no GUI (graphical user interface), and a barebones install will use a lightweight window manager like IceWM or Fluxbox.

hmm ok.. Ive got the system for KDE, so Im going to stick with that.. i was just going to use the KDE core method you listed and install the basic programs I need, so as to eliminate unnecessary stuff and bring my speed up.. I was actually planning to install KDE core from a server install on the same partition I already have Ubuntu on (effectively remove and install KDE core kubuntu from server install). 

I just dont know whats up with the i386 listed as a download, and Ill have to do some googling for the method on a KDE core server install. Thanks for this thread, as well as the one you just listed... This is EXACTLY where i want to take ubuntu...

Cheers!

---

### Post by aysiu on 2007-05-04
You may want to take a look at [this post](http://ubuntuforums.org/showpost.php?p=1578193&postcount=24) for some extra performance tweaks on KDE.

---

### Post by GSF1200S on 2007-05-04
> **aysiu said:**
> Well, there is basically i386 and AMD64.

Unless you have a 64-bit processor, you want i386.

Have you tried following these instructions?
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

Another awesome page...

Well heres the meat and potatoes.. I started off with GNOME ubuntu. Ive tried XFCE, GNOME, Flux, and KDE.. I like KDE and it works with my system. So right now, Ive got all these unnecessary packages floating around, as well as kubuntu desktop with a bunch of apps I dont use. It may be best for me to just wipe it all and go with a KDE core install, building from there.

Oh and about the i386 thing. I remember only being able to use one core of my processor until I switched to the generic kernel image.. maybe that has nothing to do with the download? 

Thanks for the info.. :)

---

### Post by GSF1200S on 2007-05-04
> **aysiu said:**
> You may want to take a look at [this post](http://ubuntuforums.org/showpost.php?p=1578193&postcount=24) for some extra performance tweaks on KDE.

Nice.. this is what I used to do to Windows XP to make it faster... I just didnt know the KDE equivalents....

---

### Post by Cypher2 on 2009-12-18
This is a little custom install script I've taken the time to write after coming back to KDE recently and looking for the lightest custom server install possible:

ENJOY!

p.s.: make sure you know how to work it since this script first and foremost converts all package dependecies to the APTITUDE package management system (it ain't got supercow but it sure digs apt to its grave)...


_______________________________________________________________

```
#!/bin/bash
echo "* Setting Aptitude as system default..."
sudo aptitude keep-all
sudo aptitude update
echo "* Installing upgrades..."
sudo aptitude -y dist-upgrade
echo "* Cleaning up..."
sudo aptitude -y autoclean
echo "* Installing system essentials..."
sudo aptitude -y install acpi-support \
cups \
samba \
sun-java6-bin \
xserver-xorg \
xinit
echo "* Installing OpenOffice.org for KDE..."
sudo aptitude --without-recommends -y install openoffice.org-base \
openoffice.org-calc \
openoffice.org-draw \
openoffice.org-impress \
openoffice.org-math \
openoffice.org-writer \
openoffice.org-kde \
openoffice.org-style-oxygen
echo "* Installing Ubuntu components..."
sudo aptitude --without-recommends -y install usplash \
usplash-theme-ubuntu
echo "* Installing Debian desktop maintenance essentials for KDE..."
sudo aptitude -y install adept \
gdebi-kde \
kdebluetooth \
kdm \
rar \
update-manager-kde \
update-notifier-kde \
usb-creator-kde \
zip
echo "* Installing K Desktop Environement components..."
echo "* Parsing..."
echo "* Installing kdeadmin package components..."
sudo aptitude -y install kcron \
ksystemlog \
kuser \
system-config-printer-kde
echo "* Installing kdeartwork package components..."
sudo aptitude -y install kdeartwork-emoticons \
kdeartwork-style \
kdeartwork-theme-icon \
kdewallpapers \
kscreensaver \
plasma-desktopthemes-artwork
echo "* Installing kdebase package components..."
sudo aptitude -y install dolphin \
kappfinder \
kdepasswd \
kfind \
konqueror \
konsole \
plasma-widget-folderview
echo "* Installing kdebase-runtime package components..."
sudo aptitude -y install kdebase-runtime
echo "* Installing kdebase-workspace package components..."
sudo aptitude -y install klipper \
ksysguard \
kde-window-manager \
systemsettings
echo "* Installing kdebindings package components..."
sudo aptitude -y install kdebindings-kde4
echo "* Installing kdegraphics package components..."
sudo aptitude -y install kamera \
kcolorchooser \
kruler \
ksnapshot \
okular \
skanlite
echo "* Installing kdelibs package components..."
sudo aptitude -y install kdelibs5
echo "* Installing kdemultimedia package components..."
sudo aptitude -y install amarok \
dragonplayer \
dvd+rw-tools \
k3b \
kdemultimedia-kio-plugins \
kmix
echo "* Installing kdenetwork package components..."
sudo aptitude -y install kopete \
krdc \
krfb \
ktorrent \
kdenetwork-filesharing \
plasma-widget-networkmanagement
echo "* Installing kdepim package components..."
sudo aptitude -y install kaddressbook \
kalarm \
kmail \
kontact
echo "* Installing kdepimlibs package components..."
sudo aptitude -y install kdepimlibs5
echo "* Installing kdepim-runtime package components..."
sudo aptitude -y install kdepim-runtime
echo "* Installing kdeplasma-addons components..."
sudo aptitude -y install plasma-runners-addons \
plasma-wallpapers-addons
sudo aptitude --without-recommends -y install plasma-widgets-addons
echo "* Installing kdesdk package components..."
sudo aptitude -y install kate
echo "* Installing kdeutils package components..."
sudo aptitude -y install ark \
kcalc \
kcharselect \
kdessh \
krename \
kwalletmanager \
sweeper \
printer-applet
echo "* Installing oxygen-icons package components..."
sudo aptitude -y install kde-icons-oxygen \
oxygen-cursor-theme \
oxygen-cursor-theme-extra
echo "* Installing plugin essentials..."
sudo aptitude -y install gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly \
gstreamer0.10-ffmpeg \
flashplugin-nonfree
echo "* Installing virtualization components..."
sudo aptitude -y install virtualbox-ose
echo "Creating Extra Home Directories..."
sudo mkdir --mode=777 /home/$USER/Downloads 
sudo mkdir --mode=777 /home/$USER/Documents 
sudo mkdir --mode=777 /home/$USER/Music
sudo mkdir --mode=777 /home/$USER/Pictures
sudo mkdir --mode=777 /home/$USER/Video
echo "* Cleaning up..."
sudo aptitude -y autoclean
echo "* Restarting..."
sudo reboot
```

_______________________________________________________________

---

### Post by Shibblet on 2009-12-18
How does kde-core compare to kde-minimal?

---

