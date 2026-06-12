---
title: "lubuntu 12.04 help please"
date: 2011-11-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ronacc on 2011-11-20
has anyone got the lubuntu (64bit) 12.04 daily's to give an install that will boot all the way to desktop ? I have been reinstalling every 2 days or so with the current daily and have yet to get beyond a blank screen right after ( or about) the greeter should appear , I have tried starting various services from console on the occasions ( about 1/2 the time ) when I can get to one . lxde and lxdm return unknown service , lghtdm usually claims to be running , start x fails after searcing for the NV driver ( no longer in the repos ) and the Nvidia 173 legacy driver which is definitively wrong for my card  (7600GS) . installing nvidia-current from terminal with apt-get appears to work, dkms reports sucess but I still cannot get to desktop . hand installing the 180.13 driver by hand also no help ,and after installing either startx reports an error in /home/ron/.xauthority and /tmp/.XO-lock

---

### Post by effenberg0x0 on 2011-11-20
> **ronacc said:**
> has anyone got the lubuntu (64bit) 12.04 daily's to give an install that will boot all the way to desktop ? I have been reinstalling every 2 days or so with the current daily and have yet to get beyond a blank screen right after ( or about) the greeter should appear , I have tried starting various services from console on the occasions ( about 1/2 the time ) when I can get to one . lxde and lxdm return unknown service , lghtdm usually claims to be running , start x fails after searcing for the NV driver ( no longer in the repos ) and the Nvidia 173 legacy driver which is definitively wrong for my card  (7600GS) . installing nvidia-current from terminal with apt-get appears to work, dkms reports sucess but I still cannot get to desktop . hand installing the 180.13 driver by hand also no help ,and after installing either startx reports an error in /home/ron/.xauthority and /tmp/.XO-lock

I'll give it a try now and report back here. You are getting from [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/) right?

---

### Post by ronacc on 2011-11-20
yes thats the one , precise-desktop-amd64 is the flavor . I d/l a new one about once a week and zsync in between .the 18th was the last one I tried ,I beat on them for a couple of days before I give up and try again . thanks for the effort .

---

### Post by effenberg0x0 on 2011-11-20
> **ronacc said:**
> yes thats the one , precise-desktop-amd64 is the flavor . I d/l a new one about once a week and zsync in between .the 18th was the last one I tried ,I beat on them for a couple of days before I give up and try again . thanks for the effort .

**Log**
ISO booted OK. 

New to me: Right on the first select language screen, there was a link saying that I could update the installer. I clicked on it, saw network activity, but nothing seems to have happened. It may have download a new script or something. I'll continue the install.
 
There's the option to download updates while installing and download third party software. As I usually do, I left these unchecked.

Picked up Name, login, passwd, unchecked "Encrypt Home Folder" and "Login Automatically".

Weird install. Got stuck an unusual amount of time in laptop-detect or something like that. 

Try 1: Failed. After boot screen flickers repeatedly for about 30seconds and get completely black. Due to Plymouth I couldn't see what the error was. Will investigate via Recovery.

Got to recovery, mounted / rw, used dhclient to get an IP, now using ftp to download Nvidia-Proprietary. Haven't looked at logs yet. I believe it's just the lack of VGA drivers so far.

Had to install build-essential to be able to install nvidia, of course. Took the opportunity to update/upgrade.

Found it. unity-greeter is segfaulting at libgio-2.0.so.0.3000.1.
Working on a solution

When installing libgio*, more than 100 packages were downloaded and installed, including some very critical packages. It makes me think the setup failed to install critical packages. Otherwise, these packages wouldn't be downloaded/reinstalled now, not without a warning at least.

Believing in this thesis, I'll dpkg reconfigure all just to be sure before attempting a new X session.

/var/run/utmp is not created during install, causing the boot process to stall for a long while. One can create it manually.

libgio-2.0.20 and libgio02.0-so.0 are links to libgio-2.0.so.0.3000.1 both in Ubuntu PP and Lubuntu PP. Versions and MD5 are the same. Why won't it work?

line 47 of /etc/init/lightdm is questionably wrong.

$DISPLAY is not exported. One less X complain. Checking other env vars.

---

### Post by ronacc on 2011-11-20
at least I now know I'm not the only one :lolflag: I was getting the same thing sometimes the screen would flicker lubuntu blue a few times before black screening on me . I tried removing the quiet from the boot line but couldn't find anything usefull , where did you see the greeter segfaulting I never saw that on the console output .

---

### Post by effenberg0x0 on 2011-11-20
> **ronacc said:**
> at least I now know I'm not the only one :lolflag: I was getting the same thing sometimes the screen would flicker lubuntu blue a few times before black screening on me . I tried removing the quiet from the boot line but couldn't find anything usefull , where did you see the greeter segfaulting I never saw that on the console output .

Hey, I greped all logs in search of anything useful... 
I'm gonna sleep (early meeting tomorrow) but will continue playing with this thing tomorrow.

---

### Post by ronacc on 2011-11-20
yes get some zzz's no hurry I'm just playing with lubuntu as well as ubuntu , the ubuntu dailys install fine with no glitches so far ( except for the edit to /lib/partman/choose-partition/do-option ). I had looked at the boot log and xlog but not the syslog , once you tipped me what to look for I loaded them up in gedit from my ubuntu precise install and searced on segfault and found it in syslog .

---

### Post by teh603 on 2011-11-20
> **effenberg0x0 said:**
> 
Found it. unity-greeter is segfaulting at libgio-2.0.so.0.3000.1.

Wait, Unity? What the heck is that doing in Lubuntu? Shouldn't it be using LXDE-specific stuff?

---

### Post by ronacc on 2011-11-20
> **teh603 said:**
> Wait, Unity? What the heck is that doing in Lubuntu? Shouldn't it be using LXDE-specific stuff?

Mabye the lubuntu stuff kicks in after login like when you choose which DE you want in the regular ubuntu greeter ( gnome(shell) , unity , unity-2d etc ) . anyway here it is frome my lubuntu syslog ```
Nov 20 17:05:01 ron-desktop2 kernel: [   92.875657] unity-greeter[3499]: segfault at 0 ip 00007f2193f5eb70 sp 00007fffbe737698 error 4 in libgio-2.0.so.0.3000.1[7f2193ec5000+13b000]
```

---

### Post by teh603 on 2011-11-20
Odd. It doesn't seem to be installed in Kubuntu.

---

### Post by effenberg0x0 on 2011-11-21
Aaaaaaaannnnnd he... Scooooreessss!!!!!!!!!!!!!!!!!

[ATTACH]207703[/ATTACH]

---

### Post by effenberg0x0 on 2011-11-21
Here's the trick: 

Go with the install normally, let it partition the disk, etc
Select your language, continue, etc, until you enter you desired login name and password.
At this point, you may want to disable plymouth and be able to see whats going on on boot. If so, edit /target/boot/grub/grub.cfg to remove quiet splash from the kernel line. You will be using sudo, but there's no password (press enter) for this user (user ubuntu).

You'll notice your newly created home directory has nothing useful inside it, so do a sudo cp -axRf /home/ubuntu/* /target/home/<your_user>
At this point I wanted to sudo chown 1000:1000 /target/home/<your login> -R && sudo chmod 775 /target/home/<your login>/* -R, but for some reason you can't. Only some files are altered. Go with it.

You'll boot to a flickering or black screen, still not OK, but close. Switch to a VT with Ctrl+Alt+F6 and run:
sudo apt-get update
sudo apt-get remove unity-greeter
sudo apt-get install --reinstall lxdm
In the next screen, choose lxdm.
sudo service lxdm start

Bingo.

---

### Post by ronacc on 2011-11-21
that got it thanks , I had already removed quiet splash from the boot line , I always do first thing when I have a problem booting to DT because I want to see what is going on plus I have had troubles with plymouth in the past . sudo service lxdm start didn't work but a reboot did .

---

### Post by teh603 on 2011-11-21
> **effenberg0x0 said:**
> Switch to a VT with Ctrl+Alt+F6 and run:
sudo apt-get update
sudo apt-get remove unity-greeter
sudo apt-get install --reinstall lxdm
In the next screen, choose lxdm.
sudo service lxdm start

Bingo.Had a hunch that unity-greeter wasn't supposed to be in there. Someone sent a message to the Lubuntu devs to get it removed so this thing can build properly?

---

### Post by effenberg0x0 on 2011-11-21
I am not a Lubuntu user. I never really spent more than a couple minutes on it (besides installing it here and there). But, looking at the way some files are set in /etc, X, etc... I do believe they wanted lightdm to be there. Maybe they want to create a uniform boot experience up to the DM?

**EDIT: **Well it seems lightdm on lubuntu was only news to me: [http://lubuntublog.blogspot.com/2011/07/lightdm-on-lubuntu.html](http://lubuntublog.blogspot.com/2011/07/lightdm-on-lubuntu.html) 
unity-greeter probably is supposed to be there, also.

---

### Post by teh603 on 2011-11-21
> **effenberg0x0 said:**
> I am not a Lubuntu user. I never really spent more than a couple minutes on it (besides installing it here and there). But, looking at the way some files are set in /etc, X, etc... I do believe they wanted lightdm to be there. Maybe they want to create a uniform boot experience up to the DM?

**EDIT: **Well it seems lightdm on lubuntu was only news to me: [http://lubuntublog.blogspot.com/2011/07/lightdm-on-lubuntu.html](http://lubuntublog.blogspot.com/2011/07/lightdm-on-lubuntu.html) 
unity-greeter probably is supposed to be there, also.Well, so much for keeping Unity confined to the main trunk. Hope it doesn't cause as many crashes as Plymouth did; I can remember when mountall was rewritten to check for Plymouth's process because people were removing it because of all the crashes that somehow went away when they removed it.

---

### Post by cariboo on 2011-11-21
> **teh603 said:**
> Well, so much for keeping Unity confined to the main trunk. Hope it doesn't cause as many crashes as Plymouth did; I can remember when mountall was rewritten to check for Plymouth's process because people were removing it because of all the crashes that somehow went away when they removed it.

What does lightdm have to do with Unity? It's a desktop manager, nothing more, it is highly customizable, the only thing it has to do with Untiy is the name of the configuration file, it could have been called ubuntu-greeter.conf, and it still would have been the  same thing.

These anti Untiy comments are just getting silly, and should have no place in any of the threads in this sub-forum.

---

### Post by ronacc on 2011-11-21
you can call it ubuntu-greeter or you can call it unity greeter or you can call it fred , removing it cures the problem and since the referenced blog indicates that the rational for using it was to maintain commonality with the parent (ubuntu) and therefore unity I agree with  teh603 that it is cross pollution from unity creeping everywhere .

---

### Post by cariboo on 2011-11-22
> **ronacc said:**
> you can call it ubuntu-greeter or you can call it unity greeter or you can call it fred , removing it cures the problem and since the referenced blog indicates that the rational for using it was to maintain commonality with the parent (ubuntu) and therefore unity I agree with  teh603 that it is cross pollution from unity creeping everywhere .

If you really feel that way, why bother? Unity isn't going to go away, no matter how much you want it to. Most of you are acting like someone took your favorite toy away, and you're going to hold your breath, until they give it back. 

Your help in testing is valued, but this constant sniping is just getting tiring.

---

### Post by ronacc on 2011-11-22
I just state things as I see them . I was not sniping at unity I don,t care about it I use gnome shell .I was supporting  teh603 in the observation that unity greeter or whatever you wish to call it should be  (and In fact is ) unnecessary in lubuntu . in calling unity greeter pollution I was not denegrating unity , what else would you call something from a foreign environment that damages the native one ?

---

### Post by ranch hand on 2011-11-22
> **ronacc said:**
> you can call it ubuntu-greeter or you can call it unity greeter or you can call it fred , removing it cures the problem and since the referenced blog indicates that the rational for using it was to maintain commonality with the parent (ubuntu) and therefore unity I agree with  teh603 that it is cross pollution from unity creeping everywhere .
What a naughty boy.

---

### Post by cariboo on 2011-11-22
> **ranch hand said:**
> What a naughty boy.

If you saw things from our end, you'd say a lot worse. :)

---

### Post by Harry33 on 2011-11-22
> **cariboo907 said:**
> What does lightdm have to do with Unity? It's a desktop manager, nothing more, it is highly customizable, the only thing it has to do with Untiy is the name of the configuration file, it could have been called ubuntu-greeter.conf, and it still would have been the  same thing.

These anti Untiy comments are just getting silly, and should have no place in any of the threads in this sub-forum.

[FONT=Arial]Just a comment on Unity-greeter.
The name better be Unity-greeter because, like it says, is "[FONT=Verdana][SIZE=2]The greeter for the Unity desktop[/SIZE][/FONT]".
See here:
[https://launchpad.net/ubuntu/oneiric/amd64/unity-greeter/0.1.1-0ubuntu1](https://launchpad.net/ubuntu/oneiric/amd64/unity-greeter/0.1.1-0ubuntu1)

About LightDM,
it recommends unity-greeter.

I do not use it, I use lightdm-gtk-greeter, which is "[/FONT]A LightDM greeter that uses the GTK+ toolkit[FONT=Arial]"
[/FONT]

---

### Post by effenberg0x0 on 2011-11-22
Guys, again, not a lubuntu experienced user here ok? 

Had a deep look at system-wide config files for the DE, DM, etc before wiping this Lubuntu VM.

My opinion? They did something I do all the time: Copied a previous file over to the system in order to customize it and forgot to rename it. Since it's a daily build in pre-alpha stage, it wouldn't be hard for this to happen.

Since a lot of time and contributions went to unity-greeter, and it became the de-facto greeter for lightdm, why code a greeter from start when you can just change a couple lines of it to match Lubuntu visual requirements? I think that's the rationale of the developer. We just happen to find the file in the ISO before they finished it and remembered to rename it to lubuntu-greeter. I thinks that's all this is.

There are no other traces of unity in the file. You can be sure of it. 

So, just to clarify, the solution I proposed, although it enabled us to use the desktop in this broken daily build, is wrong. I reinstalled lxdm, while we know it will use lightdm, once a not-broke, customized greeter for it exists.

**EDIT: **You all know I use and support Unity. But, I'm not a radical. I really enjoyed many aspects of current Lubuntu and thus requested further testings to be done on it, to see if / how it can be used with some of our software and how end-users react to it. It got me thinking, lxdm files are so small, a Lubuntu session should be pre-bundled into Ubuntu DVD in the future.

---

### Post by ronacc on 2011-11-22
thanks again for you help in getting installs from the current lubuntu dailys to get to desktop , I had no intention of this descending into a diatribe when I started this thread . It was an honest plea for help and you provided it .

---

### Post by effenberg0x0 on 2011-11-22
> **ronacc said:**
> thanks again for you help in getting installs from the current lubuntu dailys to get to desktop , I had no intention of this descending into a diatribe when I started this thread . It was an honest plea for help and you provided it .

You're welcome, you know I love the challenges lol :P There's nothing cooler than broken things...

---

### Post by teh603 on 2011-11-22
> **Harry33 said:**
> 
it recommends unity-greeter.

I do not use it, I use lightdm-gtk-greeter, which is "A LightDM greeter that uses the GTK+ toolkit"
So it looks like this was prolly another case of the installer treating "recommends" as "depends upon"? That's kinda annoying since unity-greeter isn't actually required and is causing all these crashes.

I don't see it as much of an issue of "contamination" or even a Unity issue at all, as much as one where people are taking something that works and replacing it with a package that doesn't work as well as what it replaced, and then possibly recoding software to depend on the new broken package. What ever happened to "if it ain't broke, don't fix it"?

---

### Post by cariboo on 2011-11-22
To me it's always GDM/KDM/XDM that has been broken, as soon as you install a different DE, that particular display manager seems to take over, no matter what my preferences are. The only way to get rid of it is to uninstall it, and replace it with the the display manager I want to use. 

Personally I'd like to see the display manager look the same no matter what desktop environment I use, the only change should be the version and version number in the lower left corner.

---

### Post by Harry33 on 2011-11-23
> **teh603 said:**
> So it looks like this was prolly another case of the installer treating "recommends" as "depends upon"? That's kinda annoying since unity-greeter isn't actually required and is causing all these crashes.

I don't see it as much of an issue of "contamination" or even a Unity issue at all, as much as one where people are taking something that works and replacing it with a package that doesn't work as well as what it replaced, and then possibly recoding software to depend on the new broken package. What ever happened to "if it ain't broke, don't fix it"?

The Installer will install also the recommended packages.
Note, that Synaptic does this too, unless you change the settings not to do so.

---

### Post by teh603 on 2011-11-23
> **cariboo907 said:**
> To me it's always GDM/KDM/XDM that has been broken, as soon as you install a different DE, that particular display manager seems to take over, no matter what my preferences are. The only way to get rid of it is to uninstall it, and replace it with the the display manager I want to use. 
There isn't any way to encapsulate each DE so each's dependencies don't tamper with each other? I'd have figured that'd be a priority, to ensure the best performance from each.

---

### Post by effenberg0x0 on 2011-11-23
> **cariboo907 said:**
> Personally I'd like to see the display manager look the same no matter what desktop environment I use, the only change should be the version and version number in the lower left corner.

Agreed, I think it tends to that. lightdm seems to be the chosen one, and it could be provided with no dep to any greeter. 

This is a close of latest lightdm sources:
```

[11:18 AM][ahsl:AL-DESK:~/dev/lightdm/lightdm]
$ ls
AUTHORS       COPYING   liblightdm-gobject  Makefile.am  src
autogen.sh    data      liblightdm-qt       NEWS         tests
ChangeLog     doc       lightdm.doap        po           utils
configure.ac  greeters  m4                  README

[11:18 AM][ahsl:AL-DESK:~/dev/lightdm/lightdm]
$ grep -inHr "unity" *
$

```From lightdm-set-defaults.c
```

...
    const gchar    *gdm_conf_file = CONFIG_DIR "/lightdm.conf";
...
    gchar          *default_session = NULL;
    gchar          *default_greeter = NULL;

```From configure.ac
```

...
                    Light Display Manager $VERSION
                    ===========================

        prefix:                   $prefix
        Greeter session:          $GREETER_SESSION
        Greeter user:             $GREETER_USER
        User session:             $USER_SESSION
        liblightdm-gobject:       $compile_liblightdm_gobject
        GObject introspection:    $found_introspection
        liblightdm-qt:            $compile_liblightdm_qt
        GTK+ Greeter:             $compile_gtk_greeter
        Qt Greeter:               $compile_qt_greeter
        Enable tests:             $enable_tests
...

```So, code-wise, it's greeter-agnostic.

---

### Post by kansasnoob on 2011-12-13
I happened to read about [**[COLOR="Red"]bug #899742[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/899742") on the Lubuntu desktop mailing list and I see that it references this thread.

But I know I performed iso-testing on the i386 version of Alpha 1:

[http://iso.qa.ubuntu.com/qatracker/milestones/205/builds/7279/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/205/builds/7279/testcases)

And you can see there that I encountered only one critical bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/894768](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/894768)

So, I'm just trying to get up to speed here and see if I can help troubleshoot what's going on, any thoughts?

---

### Post by ronacc on 2011-12-13
sounds like a dupe of a bug I filed that also effects regular ubuntu , dkms/jockey tries to install the wrong nvidia driver and fails , the fix is hand install the correct driver from nvidia  or else purge nvidia current and reinstall ( reported to work but I haven't tried it ) , installing the 290.10 driver from nvidia does work .

---

### Post by amjjawad on 2011-12-14
> **teh603 said:**
> Had a hunch that unity-greeter wasn't supposed to be in there. Someone sent a message to the Lubuntu devs to get it removed so this thing can build properly?

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/903895](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/903895)

Don't worry, Lubuntu has nothing to do with Unity and Unity has nothing to do with Lubuntu.

No need to panic :)

I'm not a developer but a member of the team.

---

### Post by amjjawad on 2011-12-14
ronacc,

I read through this thread and I noticed that part of the solution is to do some installation. I can't connect to any wired network, I can ONLY connect to wireless and I have no clue how to do that from CLI.
I'm not even sure if my problem is the same as yours? I can't get a desktop and all what I get is a black screen with some lines.

I'll see what else I can do to get this thing work. Or maybe I better wait for Beta Version because it will give less headache, I guess.

Edit:
I have a Multi-Booting System and Lubuntu 12.04 Alpha 1 is installed on /dev/sda9.

---

### Post by ronacc on 2011-12-14
what I do if I don't want to drag a cable over and connect wired is use another install or even the live cd to download the driver and then copy it to my /home on the install and then you don't need to be able to connect from the term , just boot to the blank screen , get to a terminal and cd to your / home and run the installer .

---

### Post by cariboo on 2011-12-15
There is a good howto to manually set up wireless [here.]("http://ubuntuforums.org/showthread.php?t=571188")

I used a PCI wireless card on my server for years, using a similar method.

---

### Post by amjjawad on 2011-12-15
> **ronacc said:**
> just boot to the blank screen , get to a terminal and cd to your / home and run the installer .

Just to make sure we are on the same page ... we are trying to fix the black screen issue, right?

How to run the installer? and we are trying to do that to install whatever we need, right?

---

### Post by amjjawad on 2011-12-15
> **cariboo907 said:**
> There is a good howto to manually set up wireless [here.]("http://ubuntuforums.org/showthread.php?t=571188")

I used a PCI wireless card on my server for years, using a similar method.

Bookmarked, thanks a lot :)

---

### Post by ronacc on 2011-12-15
> **amjjawad said:**
> Just to make sure we are on the same page ... we are trying to fix the black screen issue, right?

How to run the installer? and we are trying to do that to install whatever we need, right?

yes the black screen . I thought I saw somewhere that you have Nvidia graphics , which have been blackscreening after install for some people . The driver I refered to was the Nvidia graphics driver for current cards ( not legacy ) . The driver I use for my 7600gs  is the 290.10 one . to run the installer cd to the directory where you copied it to and run ```
 sudo sh NVIDIA<tab to complete> 
``` and it will build the driver .

USE THIS ONLY IF YOU HAVE NVIDIA GRAPHICS that require nvidia-current.

---

### Post by amjjawad on 2011-12-15
> **ronacc said:**
> yes the black screen . I thought I saw somewhere that you have Nvidia graphics , which have been blackscreening after install for some people . The driver I refered to was the Nvidia graphics driver for current cards ( not legacy ) . The driver I use for my 7600gs  is the 290.10 one . to run the installer cd to the directory where you copied it to and run ```
 sudo sh NVIDIA<tab to complete> 
``` and it will build the driver .

USE THIS ONLY IF YOU HAVE NVIDIA GRAPHICS that require nvidia-current.

No, I don't have Nvidia.

```
*-display               
       description: VGA compatible controller
       product: [COLOR=Red]**RC410 [Radeon Xpress 200]**[/COLOR]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: **[COLOR=Red]driver=radeon[/COLOR]** latency=64 mingnt=8
       resources: irq:17 memory:f0000000-f7ffffff(prefetchable) ioport:ee00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff(prefetchable)

```

---

### Post by ronacc on 2011-12-15
sorry I misunderstood . do you know what is stopping you from getting to desktop ? Try hitting e when the grub menu comes up and remove quiet and splash from the boot line so you can see what is going on during boot and where it stops , also you can access your logs by booting another install if you have one on that box and checking in /var/log for the install that won't boot , you can also use the live cd to do the same .

---

### Post by amjjawad on 2011-12-15
> **ronacc said:**
> sorry I misunderstood . do you know what is stopping you from getting to desktop ? Try hitting e when the grub menu comes up and remove quiet and splash from the boot line so you can see what is going on during boot and where it stops , also you can access your logs by booting another install if you have one on that box and checking in /var/log for the install that won't boot , you can also use the live cd to do the same .

No need to be sorry, it's ok :)

No, I don't really know what is stopping me to see or get to the Desktop.
I already removed "quiet splash" but can't remember what I got?!

Yes, I have a Multi-Booting System:



This is my Test PC and I'm doing lots of tests on it.

As for the log, are we talking about dmesg log? or another one?
Sorry, I'm not good at these stuff because I usually don't face such problems.

---

### Post by ronacc on 2011-12-15
start with your boot.log also dmesg kernel and jockey logs look for any thing that looks suspicious or any "fails" also the last few lines of the boot.log may show why it stopped .

---

### Post by amjjawad on 2011-12-15
> **ronacc said:**
> start with your boot.log also dmesg kernel and jockey logs look for any thing that looks suspicious or any "fails" also the last few lines of the boot.log may show why it stopped .

```
fsck from util-linux 2.19.1 
/dev/sda9: clean, 113813/327680 files, 482580/1310720 blocks 
 * Starting AppArmor profiles       [160G  [154G[ OK ] 
 * Setting sensors limits       [160G  [154G[ OK ] 
 * Starting NTP server ntpd       [160G  [154G[ OK ] 
 * Starting bluetooth       [160G  [154G[ OK ] 
saned disabled; edit /etc/default/saned
```


/etc/default/saned (which I have no idea what is it?

```
# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=no

# Set to the user saned should run as
RUN_AS_USER=saned
```

dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-3-generic (buildd@rothera) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-5ubuntu1) ) #9-Ubuntu SMP Wed Dec 7 21:05:04 UTC 2011 (Ubuntu 3.2.0-3.9-generic 3.2.0-rc4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001def0000 (usable)
[    0.000000]  BIOS-e820: 000000001def0000 - 000000001def3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001def3000 - 000000001df00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI:                  /D101GGC                        , BIOS GC11010N.86A.0311.2006.0420.1525 04/20/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1def0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-F7FFF uncachable
[    0.000000]   F8000-FBFFF write-protect
[    0.000000]   FC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 01E000000 mask FFE000000 write-combining
[    0.000000]   2 base 01DF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f5e30] f5e30
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001def0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001dc00000 page 2M
[    0.000000]  001dc00000 - 001def0000 page 4k
[    0.000000] kernel direct mapping tables up to 1def0000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1c89c000 - 1d5f1000
[    0.000000] ACPI: RSDP 000f7d10 00014 (v00 ATi   )
[    0.000000] ACPI: RSDT 1def3040 00030 (v01 ATi    AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 1def30c0 00074 (v01 ATi    AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 1def3180 03B02 (v01 ATI    AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 1def0000 00040
[    0.000000] ACPI: MCFG 1def6e00 0003C (v01 ATi    AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 1def6d00 00084 (v01 ATi    AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 478MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1def0000
[    0.000000]   low ram: 0 - 1def0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001def0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001def0
[    0.000000] On node 0 totalpages: 122495
[    0.000000] free_area_init_node: node 0, pgdat c1817b00, node_mem_map ddb2f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 926 pages used for memmap
[    0.000000]   Normal zone: 117586 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1df00000 (gap: 1df00000:c2100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @dc400000 s31424 r0 d21824 u1048576
[    0.000000] pcpu-alloc: s31424 r0 d21824 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121537
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-3-generic root=UUID=0d53840d-76a4-49d5-a6d6-6994e1aa19b0 ro vt.handoff=7
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1961472 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 459968k/490432k available (5595k kernel code, 30012k reserved, 2741k data, 712k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xde6f0000 - 0xff7fe000   ( 529 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xddef0000   ( 478 MB)
[    0.000000]       .init : 0xc1825000 - 0xc18d7000   ( 712 kB)
[    0.000000]       .data : 0xc1576c84 - 0xc1824280   (2741 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1576c84   (5595 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=dc00a000 soft=dc00c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3066.844 MHz processor.
[    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6133.68 BogoMIPS (lpj=12267376)
[    0.008010] pid_max: default: 32768 minimum: 301
[    0.008041] Security Framework initialized
[    0.008065] AppArmor: AppArmor initialized
[    0.008068] Yama: becoming mindful.
[    0.008149] Mount-cache hash table entries: 512
[    0.008346] Initializing cgroup subsys cpuacct
[    0.008356] Initializing cgroup subsys memory
[    0.008370] Initializing cgroup subsys devices
[    0.008374] Initializing cgroup subsys freezer
[    0.008378] Initializing cgroup subsys net_cls
[    0.008381] Initializing cgroup subsys blkio
[    0.008393] Initializing cgroup subsys perf_event
[    0.008438] CPU: Physical Processor ID: 0
[    0.008442] CPU: Processor Core ID: 0
[    0.008446] mce: CPU supports 4 MCE banks
[    0.008461] CPU0: Thermal monitoring enabled (TM2)
[    0.008467] using mwait in idle threads.
[    0.013356] ACPI: Core revision 20110623
[    0.020020] ftrace: allocating 25810 entries in 51 pages
[    0.024107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024564] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066204] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.068003] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      18
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             0000007fffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000003ffff
[    0.068003] CPU 1 irqstacks, hard=dc0b0000 soft=dc0b2000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9b000
[    0.012000] Initializing CPU#1
[    0.156036] Brought up 2 CPUs
[    0.156044] Total of 2 processors activated (12267.63 BogoMIPS).
[    0.156885] devtmpfs: initialized
[    0.156885] EVM: security.selinux
[    0.156885] EVM: security.SMACK64
[    0.156885] EVM: security.capability
[    0.156885] PM: Registering ACPI NVS region at 1def0000 (12288 bytes)
[    0.160696] print_constraints: dummy: 
[    0.160746] RTC time: 20:32:22, date: 12/14/11
[    0.160805] NET: Registered protocol family 16
[    0.160926] Trying to unpack rootfs image as initramfs...
[    0.161095] EISA bus registered
[    0.161164] ACPI: bus type pci registered
[    0.161304] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.161312] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.161317] PCI: Using MMCONFIG for extended config space
[    0.161321] PCI: Using configuration type 1 for base access
[    0.176466] bio: create slab <bio-0> at 0
[    0.176466] ACPI: Added _OSI(Module Device)
[    0.176466] ACPI: Added _OSI(Processor Device)
[    0.176466] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176469] ACPI: Added _OSI(Processor Aggregator Device)
[    0.178245] ACPI: EC: Look up EC in DSDT
[    0.185806] ACPI: Interpreter enabled
[    0.185826] ACPI: (supports S0 S1 S3 S4 S5)
[    0.185879] ACPI: Using IOAPIC for interrupt routing
[    0.193330] ACPI: No dock devices found.
[    0.193339] HEST: Table not found.
[    0.193349] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.193506] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.193770] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.193778] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.193784] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.193790] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.193796] pci_root PNP0A03:00: host bridge window [mem 0x1e000000-0xfebfffff] (ignored)
[    0.193821] pci 0000:00:00.0: [1002:5a33] type 0 class 0x000600
[    0.193874] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.193917] pci 0000:00:01.0: [1002:5a3f] type 1 class 0x000604
[    0.194037] pci 0000:00:11.0: [1002:437a] type 0 class 0x000101
[    0.194078] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.194099] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.194120] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.194140] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.194161] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.194182] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f1ff]
[    0.194203] pci 0000:00:11.0: reg 30: [mem 0xfdf80000-0xfdffffff pref]
[    0.194253] pci 0000:00:11.0: supports D1 D2
[    0.194311] pci 0000:00:12.0: [1002:4379] type 0 class 0x000101
[    0.194352] pci 0000:00:12.0: reg 10: [io  0xfa00-0xfa07]
[    0.194373] pci 0000:00:12.0: reg 14: [io  0xf900-0xf903]
[    0.194394] pci 0000:00:12.0: reg 18: [io  0xf800-0xf807]
[    0.194414] pci 0000:00:12.0: reg 1c: [io  0xf700-0xf703]
[    0.194435] pci 0000:00:12.0: reg 20: [io  0xf600-0xf60f]
[    0.194456] pci 0000:00:12.0: reg 24: [mem 0xfe02e000-0xfe02e1ff]
[    0.194476] pci 0000:00:12.0: reg 30: [mem 0xfdf80000-0xfdffffff pref]
[    0.194527] pci 0000:00:12.0: supports D1 D2
[    0.194567] pci 0000:00:13.0: [1002:4374] type 0 class 0x000c03
[    0.194603] pci 0000:00:13.0: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.194768] pci 0000:00:13.1: [1002:4375] type 0 class 0x000c03
[    0.194812] pci 0000:00:13.1: reg 10: [mem 0xfe02c000-0xfe02cfff]
[    0.194988] pci 0000:00:13.2: [1002:4373] type 0 class 0x000c03
[    0.195029] pci 0000:00:13.2: reg 10: [mem 0xfe02b000-0xfe02bfff]
[    0.195172] pci 0000:00:13.2: supports D1 D2
[    0.195177] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.195187] pci 0000:00:13.2: PME# disabled
[    0.195232] pci 0000:00:14.0: [1002:4372] type 0 class 0x000c05
[    0.195259] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    0.195280] pci 0000:00:14.0: reg 14: [mem 0xfe02a000-0xfe02a3ff]
[    0.195380] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.195419] pci 0000:00:14.1: [1002:4376] type 0 class 0x000101
[    0.195455] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.195476] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.195497] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.195517] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.195537] pci 0000:00:14.1: reg 20: [io  0xf400-0xf40f]
[    0.195645] pci 0000:00:14.2: [1002:437b] type 0 class 0x000403
[    0.195695] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.195839] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.195851] pci 0000:00:14.2: PME# disabled
[    0.195885] pci 0000:00:14.3: [1002:4377] type 0 class 0x000601
[    0.196064] pci 0000:00:14.4: [1002:4371] type 1 class 0x000604
[    0.196217] pci 0000:01:05.0: [1002:5a61] type 0 class 0x000300
[    0.196241] pci 0000:01:05.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.196254] pci 0000:01:05.0: reg 14: [io  0xee00-0xeeff]
[    0.196267] pci 0000:01:05.0: reg 18: [mem 0xfdef0000-0xfdefffff]
[    0.196303] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.196330] pci 0000:01:05.0: supports D1 D2
[    0.196374] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.196383] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.196391] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.196398] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff pref]
[    0.196460] pci 0000:02:02.0: [10ec:8139] type 0 class 0x000200
[    0.196503] pci 0000:02:02.0: reg 10: [io  0xde00-0xdeff]
[    0.196528] pci 0000:02:02.0: reg 14: [mem 0xfddff000-0xfddff0ff]
[    0.196675] pci 0000:02:02.0: supports D1 D2
[    0.196682] pci 0000:02:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.196694] pci 0000:02:02.0: PME# disabled
[    0.196735] pci 0000:02:03.0: [1814:0302] type 0 class 0x000280
[    0.196776] pci 0000:02:03.0: reg 10: [mem 0xfddf0000-0xfddf7fff]
[    0.197022] pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
[    0.197038] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.197047] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.197057] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.197063] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.197069] pci 0000:00:14.4:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.197092] pci_bus 0000:00: on NUMA node 0
[    0.197110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.197492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.197707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.197802]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.197812]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.197817] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.210946] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.211063] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.211173] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.211309] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.211419] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.211529] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11)
[    0.211637] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.211780] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11)
[    0.212079] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.212089] vgaarb: loaded
[    0.212093] vgaarb: bridge control possible 0000:01:05.0
[    0.212385] i2c-core: driver [aat2870] using legacy suspend method
[    0.212390] i2c-core: driver [aat2870] using legacy resume method
[    0.212587] SCSI subsystem initialized
[    0.212737] libata version 3.00 loaded.
[    0.212851] usbcore: registered new interface driver usbfs
[    0.212880] usbcore: registered new interface driver hub
[    0.212938] usbcore: registered new device driver usb
[    0.213181] PCI: Using ACPI for IRQ routing
[    0.230418] PCI: pci_cache_line_size set to 64 bytes
[    0.230448] pci 0000:00:00.0: address space collision: [mem 0xe0000000-0xffffffff 64bit] conflicts with PCI Bus 0000:01 [mem 0xf0000000-0xf7ffffff pref]
[    0.230574] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.230581] reserve RAM buffer: 000000001def0000 - 000000001fffffff 
[    0.230867] NetLabel: Initializing
[    0.230873] NetLabel:  domain hash size = 128
[    0.230876] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.230914] NetLabel:  unlabeled traffic allowed by default
[    0.250590] AppArmor: AppArmor Filesystem Enabled
[    0.250659] pnp: PnP ACPI init
[    0.250730] ACPI: bus type pnp registered
[    0.250990] pnp 00:00: [bus 00-ff]
[    0.250997] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.251002] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.251007] pnp 00:00: [io  0x0d00-0xffff window]
[    0.251012] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.251018] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.251023] pnp 00:00: [mem 0x1e000000-0xfebfffff window]
[    0.251139] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.251825] pnp 00:01: [io  0x0228-0x022f]
[    0.251831] pnp 00:01: [io  0x040b]
[    0.251835] pnp 00:01: [io  0x04d6]
[    0.251839] pnp 00:01: [io  0x0c00-0x0c01]
[    0.251843] pnp 00:01: [io  0x0c14]
[    0.251847] pnp 00:01: [io  0x0c50-0x0c52]
[    0.251852] pnp 00:01: [io  0x0c6c-0x0c6d]
[    0.251856] pnp 00:01: [io  0x0c6f]
[    0.251860] pnp 00:01: [io  0x0cd4-0x0cdf]
[    0.251864] pnp 00:01: [io  0x4000-0x40fe]
[    0.251869] pnp 00:01: [io  0x4210-0x4217]
[    0.251874] pnp 00:01: [mem 0x00000000-0x00000fff window]
[    0.251879] pnp 00:01: [mem 0xfee00400-0xfee00fff window]
[    0.251896] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.251954] pnp 00:01: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.252057] system 00:01: [io  0x0228-0x022f] has been reserved
[    0.252063] system 00:01: [io  0x040b] has been reserved
[    0.252069] system 00:01: [io  0x04d6] has been reserved
[    0.252075] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.252080] system 00:01: [io  0x0c14] has been reserved
[    0.252086] system 00:01: [io  0x0c50-0x0c52] has been reserved
[    0.252092] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
[    0.252097] system 00:01: [io  0x0c6f] has been reserved
[    0.252103] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
[    0.252109] system 00:01: [io  0x4000-0x40fe] has been reserved
[    0.252115] system 00:01: [io  0x4210-0x4217] has been reserved
[    0.252123] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.252132] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.252416] pnp 00:02: [dma 4]
[    0.252422] pnp 00:02: [io  0x0000-0x000f]
[    0.252427] pnp 00:02: [io  0x0080-0x0090]
[    0.252431] pnp 00:02: [io  0x0094-0x009f]
[    0.252436] pnp 00:02: [io  0x00c0-0x00df]
[    0.252510] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.252536] pnp 00:03: [io  0x0070-0x0073]
[    0.252561] pnp 00:03: [irq 8]
[    0.252631] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.252653] pnp 00:04: [io  0x0061]
[    0.252754] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.252775] pnp 00:05: [io  0x00f0-0x00ff]
[    0.252787] pnp 00:05: [irq 13]
[    0.252858] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.252948] pnp 00:06: [io  0x0010-0x001f]
[    0.252953] pnp 00:06: [io  0x0022-0x003f]
[    0.252958] pnp 00:06: [io  0x0044-0x005f]
[    0.252962] pnp 00:06: [io  0x0062-0x0063]
[    0.252967] pnp 00:06: [io  0x0065-0x006f]
[    0.252971] pnp 00:06: [io  0x0074-0x007f]
[    0.252975] pnp 00:06: [io  0x0091-0x0093]
[    0.252980] pnp 00:06: [io  0x00a2-0x00bf]
[    0.252984] pnp 00:06: [io  0x00e0-0x00ef]
[    0.252989] pnp 00:06: [io  0x04d0-0x04d1]
[    0.252993] pnp 00:06: [io  0x0800-0x087f]
[    0.253003] pnp 00:06: [io  0x0880-0x088f]
[    0.253163] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.253171] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.253176] system 00:06: [io  0x0880-0x088f] has been reserved
[    0.253184] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.253600] pnp 00:07: [io  0x03f8-0x03ff]
[    0.253613] pnp 00:07: [irq 4]
[    0.253740] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.254297] pnp 00:08: [io  0x0378-0x037f]
[    0.254302] pnp 00:08: [io  0x0778-0x077b]
[    0.254313] pnp 00:08: [irq 7]
[    0.254318] pnp 00:08: [dma 3]
[    0.254443] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.254548] pnp 00:09: [io  0x0060]
[    0.254553] pnp 00:09: [io  0x0064]
[    0.254564] pnp 00:09: [irq 1]
[    0.254669] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.254745] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.254864] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.254873] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.255173] pnp 00:0b: [mem 0x000cc000-0x000cffff]
[    0.255179] pnp 00:0b: [mem 0x000f0000-0x000f7fff]
[    0.255184] pnp 00:0b: [mem 0x000f8000-0x000fbfff]
[    0.255189] pnp 00:0b: [mem 0x000fc000-0x000fffff]
[    0.255193] pnp 00:0b: [mem 0x1df00000-0x1dffffff]
[    0.255198] pnp 00:0b: [mem 0x1def0000-0x1defffff]
[    0.255203] pnp 00:0b: [mem 0xffff0000-0xffffffff]
[    0.255207] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.255212] pnp 00:0b: [mem 0x00100000-0x1deeffff]
[    0.255217] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.255222] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.255226] pnp 00:0b: [mem 0xfff80000-0xfffeffff]
[    0.255238] pnp 00:0b: disabling [mem 0x000cc000-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255247] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255255] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255262] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255270] pnp 00:0b: disabling [mem 0x1df00000-0x1dffffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255278] pnp 00:0b: disabling [mem 0x1def0000-0x1defffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255285] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255293] pnp 00:0b: disabling [mem 0x00100000-0x1deeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.255459] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.255466] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.255473] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.255479] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.255487] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.255507] pnp: PnP ACPI: found 12 devices
[    0.255511] ACPI: ACPI bus type pnp unregistered
[    0.255519] PnPBIOS: Disabled by ACPI PNP
[    0.294626] Switching to clocksource acpi_pm
[    0.294713] pci 0000:00:12.0: address space collision: [mem 0xfdf80000-0xfdffffff pref] conflicts with 0000:00:11.0 [mem 0xfdf80000-0xfdffffff pref]
[    0.294740] PCI: max bus depth: 1 pci_try_num: 2
[    0.294772] pci 0000:00:12.0: BAR 6: assigned [mem 0x20000000-0x2007ffff pref]
[    0.294782] pci 0000:01:05.0: BAR 6: assigned [mem 0xfde00000-0xfde1ffff pref]
[    0.294788] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.294795] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.294803] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.294811] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff pref]
[    0.294822] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[    0.294830] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.294842] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.294852] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.294892] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.294898] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.294903] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.294908] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.294914] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff pref]
[    0.294919] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.294924] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.294929] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.294934] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.294939] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.295070] NET: Registered protocol family 2
[    0.295229] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.295673] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.295823] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.296001] TCP: Hash tables configured (established 16384 bind 16384)
[    0.296001] TCP reno registered
[    0.296001] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.296001] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.296001] NET: Registered protocol family 1
[    0.296001] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.296001] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.428164] pci 0000:01:05.0: Boot video device
[    0.428185] PCI: CLS 32 bytes, default 64
[    0.429063] audit: initializing netlink socket (disabled)
[    0.429089] type=2000 audit(1323894741.424:1): initialized
[    0.465191] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.469481] VFS: Disk quotas dquot_6.5.2
[    0.469631] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.470964] fuse init (API version 7.17)
[    0.471168] msgmni has been set to 898
[    0.471974] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.472092] io scheduler noop registered
[    0.472097] io scheduler deadline registered
[    0.472114] io scheduler cfq registered (default)
[    0.472428] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.472498] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.472844] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.472857] ACPI: Power Button [PWRB]
[    0.472981] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.472989] ACPI: Power Button [PWRF]
[    0.473111] ACPI: Fan [FAN] (on)
[    0.477410] thermal LNXTHERM:00: registered as thermal_zone0
[    0.477418] ACPI: Thermal Zone [THRM] (40 C)
[    0.477526] ERST: Table is not found!
[    0.477530] GHES: HEST is not enabled!
[    0.477701] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.498491] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.498976] isapnp: Scanning for PnP cards...
[    0.718614] Freeing initrd memory: 13652k freed
[    0.854161] isapnp: No Plug & Play device found
[    0.929129] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.944444] Linux agpgart interface v0.103
[    0.947348] brd: module loaded
[    0.948845] loop: module loaded
[    0.949196] pata_acpi 0000:00:11.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.949318] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.949374] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.949998] Fixed MDIO Bus: probed
[    0.950033] tun: Universal TUN/TAP device driver, 1.6
[    0.950036] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.950142] arcnet loaded.
[    0.950147] PPP generic driver version 2.4.2
[    0.950361] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.950397] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.950426] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.950524] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.950629] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02b000
[    0.960054] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.960334] hub 1-0:1.0: USB hub found
[    0.960342] hub 1-0:1.0: 8 ports detected
[    0.960488] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.960511] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.960527] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.960627] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.960653] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02d000
[    1.020247] hub 2-0:1.0: USB hub found
[    1.020259] hub 2-0:1.0: 4 ports detected
[    1.020371] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.020387] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.020477] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.020502] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02c000
[    1.080223] hub 3-0:1.0: USB hub found
[    1.080235] hub 3-0:1.0: 4 ports detected
[    1.080347] uhci_hcd: USB Universal Host Controller Interface driver
[    1.080473] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.080477] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.081199] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.081420] mousedev: PS/2 mouse device common for all mice
[    1.081718] rtc_cmos 00:03: RTC can wake from S4
[    1.081918] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.081954] rtc0: alarms up to one month, 242 bytes nvram
[    1.082068] device-mapper: uevent: version 1.0.3
[    1.082213] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.082267] EISA: Probing bus 0 at eisa.0
[    1.082294] Cannot allocate resource for EISA slot 4
[    1.082318] EISA: Detected 0 cards.
[    1.082335] cpufreq-nforce2: No nForce2 chipset.
[    1.082340] cpuidle: using governor ladder
[    1.082343] cpuidle: using governor menu
[    1.082346] EFI Variables Facility v0.08 2004-May-17
[    1.082787] TCP cubic registered
[    1.082980] NET: Registered protocol family 10
[    1.083864] NET: Registered protocol family 17
[    1.083890] Registering the dns_resolver key type
[    1.083931] Using IPI No-Shortcut mode
[    1.084196] PM: Hibernation image not present or could not be loaded.
[    1.084217] registered taskstats version 1
[    1.094609]   Magic number: 7:688:548
[    1.094646] tty ttyS24: hash matches
[    1.094769] rtc_cmos 00:03: setting system clock to 2011-12-14 20:32:23 UTC (1323894743)
[    1.094806] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.094809] EDD information not available.
[    1.095008] Freeing unused kernel memory: 712k freed
[    1.095871] Write protecting the kernel text: 5596k
[    1.095944] Write protecting the kernel read-only data: 2316k
[    1.109919] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.123587] udevd[81]: starting version 175
[    1.264908] scsi0 : pata_atiixp
[    1.265323] scsi1 : pata_atiixp
[    1.267167] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    1.267177] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    1.267639] sata_sil 0000:00:11.0: version 2.4
[    1.271731] scsi2 : sata_sil
[    1.274606] scsi3 : sata_sil
[    1.275038] ata3: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 23
[    1.275050] ata4: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 23
[    1.278914] scsi4 : sata_sil
[    1.280245] scsi5 : sata_sil
[    1.280631] ata5: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 22
[    1.280641] ata6: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 22
[    1.307491] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.307542] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.452647] ata2.00: ATAPI: HL-DT-ST RW/DVD GCC-4522B, 1.08, max UDMA/33
[    1.452802] ata2.01: ATA-6: SAMSUNG SV0221H, SJ100-01, max UDMA/100
[    1.452806] ata2.01: 39179952 sectors, multi 0: LBA 
[    1.452815] ata2.01: limited to UDMA/33 due to 40-wire cable
[    1.456051] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.460093] Refined TSC clocksource calibration: 3066.779 MHz.
[    1.460105] Switching to clocksource tsc
[    1.469175] ata1.00: ATA-7: ST3802110A, 3.AAJ, max UDMA/100
[    1.469180] ata1.00: 156301488 sectors, multi 1: LBA48 
[    1.484553] ata2.00: configured for UDMA/33
[    1.492692] ata2.01: configured for UDMA/33
[    1.535634] ata1.00: configured for UDMA/100
[    1.535864] scsi 0:0:0:0: Direct-Access     ATA      ST3802110A       3.AA PQ: 0 ANSI: 5
[    1.536329] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.536352] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.536487] sd 0:0:0:0: [sda] Write Protect is off
[    1.536495] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.536562] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.537469] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4522B 1.08 PQ: 0 ANSI: 5
[    1.538873] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    1.538880] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.539148] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.539425] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.539761] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG SV0221H  SJ10 PQ: 0 ANSI: 5
[    1.540124] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.540321] sd 1:0:1:0: [sdb] 39179952 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.540401] sd 1:0:1:0: [sdb] Write Protect is off
[    1.540406] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.540438] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.552081]  sdb:
[    1.552394] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.596045] ata3: SATA link down (SStatus 0 SControl 310)
[    1.600043] ata5: SATA link down (SStatus 0 SControl 310)
[    1.688932]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
[    1.690317] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.916047] ata4: SATA link down (SStatus 0 SControl 310)
[    2.236043] ata6: SATA link down (SStatus 0 SControl 310)
[    2.237633] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.237747] 8139too 0000:02:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.241046] 8139too 0000:02:02.0: eth0: RealTek RTL8139 at 0xde00, 00:16:76:85:ad:92, IRQ 21
[    2.246848] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input3
[    2.247622] generic-usb 0003:045E:0084.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:13.1-1/input0
[    2.247670] usbcore: registered new interface driver usbhid
[    2.247675] usbhid: USB HID core driver
[    3.958437] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[    9.355530] udevd[288]: starting version 175
[    9.380234] Adding 1048572k swap on /dev/sda2.  Priority:-1 extents:1 across:1048572k 
[    9.424878] lp: driver loaded but no devices found
[    9.511822] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.552776] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.588892] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[    9.735164] [drm] Initialized drm 1.1.0 20060810
[    9.813438] parport_pc 00:08: reported by Plug and Play ACPI
[    9.813531] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.903795] [drm] radeon defaulting to kernel modesetting.
[    9.903802] [drm] radeon kernel modesetting enabled.
[    9.903952] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.943245] type=1400 audit(1323894752.341:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=495 comm="apparmor_parser"
[    9.944268] type=1400 audit(1323894752.345:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=495 comm="apparmor_parser"
[    9.944903] type=1400 audit(1323894752.345:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=495 comm="apparmor_parser"
[    9.956724] type=1400 audit(1323894752.357:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=496 comm="apparmor_parser"
[    9.958146] lp0: using parport0 (interrupt-driven).
[   10.002544] [drm] initializing kernel modesetting (RS400 0x1002:0x5A61 0x8086:0xD600).
[   10.002597] [drm] register mmio base: 0xFDEF0000
[   10.002602] [drm] register mmio size: 65536
[   10.002828] [drm] Generation 2 PCI interface, using max accessible memory
[   10.002840] radeon 0000:01:05.0: VRAM: 32M 0x000000001E000000 - 0x000000001FFFFFFF (32M used)
[   10.002846] radeon 0000:01:05.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   10.002884] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.002889] [drm] Driver supports precise vblank timestamp query.
[   10.002944] [drm] radeon: irq initialized.
[   10.003412] [drm] Detected VRAM RAM=32M, BAR=128M
[   10.003420] [drm] RAM width 128bits DDR
[   10.014734] [TTM] Zone  kernel: Available graphics memory: 237166 kiB.
[   10.014741] [TTM] Initializing pool allocator.
[   10.014796] [drm] radeon: 32M of VRAM memory ready
[   10.014801] [drm] radeon: 512M of GTT memory ready.
[   10.014852] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.046615] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
[   10.061256] [drm] PCIE GART of 512M enabled (table at 0x000000001AA00000).
[   10.167118] cfg80211: Calling CRDA to update world regulatory domain
[   10.224946] rt61pci 0000:02:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.238896] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.238905] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238911] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.238918] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238923] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.238929] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238934] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.238940] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238944] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.238950] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238954] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.238960] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238965] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.238971] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238975] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.238981] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238986] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.238992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.238997] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.239003] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.239008] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.239014] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.239019] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.239024] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   10.239029] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.239034] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   10.239039] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.239045] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   10.260678] radeon 0000:01:05.0: WB enabled
[   10.265656] [drm] Loading R300 Microcode
[   10.288929] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.295506] Registered led device: rt61pci-phy0::radio
[   10.295621] Registered led device: rt61pci-phy0::assoc
[   10.311335] 8139too 0000:02:02.0: eth0: link down
[   10.311840] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.382142] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.750996] ppdev: user-space parallel port driver
[   10.800441] [drm] radeon: ring at 0x0000000020001000
[   10.800469] [drm] ring test succeeded in 1 usecs
[   10.800764] [drm] radeon: ib pool ready.
[   10.800934] [drm] ib test succeeded in 0 usecs
[   10.802187] [drm] Radeon Display Connectors
[   10.802196] [drm] Connector 0:
[   10.802201] [drm]   VGA
[   10.802207] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   10.802212] [drm]   Encoders:
[   10.802216] [drm]     CRT1: INTERNAL_DAC2
[   10.802220] [drm] Connector 1:
[   10.802225] [drm]   S-video
[   10.802230] [drm]   Encoders:
[   10.802234] [drm]     TV1: INTERNAL_DAC2
[   10.856321] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.891193] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.891203] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891209] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.891217] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891222] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.891228] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891233] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.891240] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891245] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.891251] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891257] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.891264] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891270] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.891275] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891280] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.891287] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891291] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.891297] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891302] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.891311] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891316] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.891322] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891329] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.891335] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.891340] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.891346] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.891352] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.891358] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.891364] cfg80211: World regulatory domain updated:
[   10.891368] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.891373] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891380] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.891385] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.891391] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.891400] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.953532] init: failsafe main process (674) killed by TERM signal
[   11.041668] type=1400 audit(1323894753.441:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=720 comm="apparmor_parser"
[   11.043172] type=1400 audit(1323894753.441:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=720 comm="apparmor_parser"
[   11.043734] type=1400 audit(1323894753.441:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=720 comm="apparmor_parser"
[   11.043908] type=1400 audit(1323894753.441:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=719 comm="apparmor_parser"
[   11.084261] type=1400 audit(1323894753.485:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=721 comm="apparmor_parser"
[   11.088717] type=1400 audit(1323894753.489:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=723 comm="apparmor_parser"
[   11.115329] [drm] fb mappable at 0xF0040000
[   11.115335] [drm] vram apper at 0xF0000000
[   11.115339] [drm] size 1310720
[   11.115342] [drm] fb depth is 8
[   11.115346] [drm]    pitch is 1280
[   11.119515] fbcon: radeondrmfb (fb0) is primary device
[   11.123401] Console: switching to colour frame buffer device 160x64
[   11.123473] fb0: radeondrmfb frame buffer device
[   11.123477] drm: registered panic notifier
[   11.123507] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   12.025731] Bluetooth: Core ver 2.16
[   12.026077] NET: Registered protocol family 31
[   12.026083] Bluetooth: HCI device and connection manager initialized
[   12.026091] Bluetooth: HCI socket layer initialized
[   12.026096] Bluetooth: L2CAP socket layer initialized
[   12.026938] Bluetooth: SCO socket layer initialized
[   12.032298] Bluetooth: RFCOMM TTY layer initialized
[   12.032311] Bluetooth: RFCOMM socket layer initialized
[   12.032315] Bluetooth: RFCOMM ver 1.11
[   12.045235] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.045242] Bluetooth: BNEP filters: protocol multicast
```


I think I have a good homework for tonight :)
Will have a deeper look myself and see if I can figure out what is going on!

---

### Post by ronacc on 2011-12-15
sane is the scanner package ,saned is part of that .

---

### Post by ronacc on 2011-12-15
did you try the steps in post 12 of this thread ?

---

### Post by amjjawad on 2011-12-16
> **ronacc said:**
> did you try the steps in post 12 of this thread ?


> **effenberg0x0 said:**
> Here's the trick: 

Go with the install normally, let it partition the disk, etc
Select your language, continue, etc, until you enter you desired login name and password.
At this point, you may want to disable plymouth and be able to see whats  going on on boot. If so, edit /target/boot/grub/grub.cfg to remove  quiet splash from the kernel line. You will be using sudo, but there's  no password (press enter) for this user (user ubuntu).

You'll notice your newly created home directory has nothing useful  inside it, so do a sudo cp -axRf /home/ubuntu/*  /target/home/<your_user>
At this point I wanted to sudo chown 1000:1000 /target/home/<your  login> -R && sudo chmod 775 /target/home/<your login>/*  -R, but for some reason you can't. Only some files are altered. Go with  it.

You'll boot to a flickering or black screen, still not OK, but close. Switch to a VT with Ctrl+Alt+F6 and run:
sudo apt-get update
sudo apt-get remove unity-greeter
sudo apt-get install --reinstall lxdm
In the next screen, choose lxdm.
sudo service lxdm start

Bingo.

I have tried the first part but it didn't help and when I noticed that I need an internet access, I stopped because I was unable to connect via LAN.

I'll give it another try today (hopefully) my way and if I failed, I'll follow the above steps. I'll do some tries until I reach a dead end and ask for help/suggestions

Thank you for your help :)

---

