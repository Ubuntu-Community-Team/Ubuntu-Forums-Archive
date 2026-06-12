---
title: "cleaning sources and repository lists"
date: 2015-01-04
forum: Repositories &amp; Backports
---

### Post by Jonners59 on 2015-01-04
I have been searching and trying numerous threads on tidying up/cleaning up the repository/sources lists.  Bar a manual step by step, which is working out almost impossible on the machine I am working on, there does not seem to be any simple way of doing this, which surprises me given that when trying anything alerts and messages are always popping up.

Does anyone know how to clean these lists up, please and retain all the correct ones for the many apps installed?  Gets very confusing.

My last attempt has just resulted in making a mess of my machine, as unwanted updates have been installed leaving it only booting in to cmd screen...

---

### Post by Bashing-om on 2015-01-04
Jonners59; Hey ..

The 1st thing is to show us what you are working with.
```

lsb-release -a
cat /etc/issue
uname -a
cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

Then we consider IF the better thing is to just get a new 'sourceslist' file or work with what is.

just a text file ->
[INDENT][INDENT][INDENT]but it sure is important
[/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-04
Hiya Bashing-om
Happy New Year, it has been a couple since you last helped me.  I know i am in good hands...

Hope you are around for a while.  Been a bad weekend:  The PC in question, after a reboot would not load up properly, it goes in to the blank screen after Grub.  I can access via terminal using ctrl+alt+f2, but no more, and now another machine has done the same,the one I am on at present. Maybe something to do with the latest upgrade.  I have tghis one in desktop, but need to try and fix it permanently, then I'll pop over to the other one.

---

### Post by Bashing-om on 2015-01-04
Jonners59; Yeaya ..

We try and make your NewYear better.

Been there too .. 2nd machine messing up when you have to fix the 1st ..

OK, 2nd machine not booting to the GUI.
Have you tried booting with the "nomodeset" boot parameter - ATI/Nvidia only ?
Have you tried booting in the "recovery" console ?

Are you running proprietary graphics driver such that an update broke that non-ubuntu stuff ?

[INDENT][INDENT]we get to the bottom of things
[INDENT][INDENT][INDENT]one way or another[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-04
Back on 1st machine as I was getting nowhere on the 2nd, and it wanted to upgrade (not just update) and given it's state I thought i would let it, and see what we have tomorrow - I think I know what caused it...  The update to the Virtual Box...

Machine 1
Tried everything.  It is an NVidia card and tried nomodeset, acpi=off, and loads of other stuff like
[HTML]Using the terminal:
If you've got to a blank screen while booting up, press CTRL + ALT + F1 to access the terminal.
Then, depending on your desktop environment, terminate the X using:
For Gnome (Ubuntu): sudo /etc/init.d/gdm stopFor KDE (Kubuntu): sudo /etc/init.d/kdm stopFor Xfce (Xubuntu): sudo /etc/init.d/xdm stopFor the reconfiguration process:
sudo dpkg-reconfigure xserver-xorg
Note: A backup is always recommended before running the configuration, so you can do it using:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backupRestart the GUI:
Again, this depends on the desktop environment, so:
For Gnome (Ubuntu): sudo /etc/init.d/gdm startFor KDE (Kubuntu): sudo /etc/init.d/kdm startFor Xfce (Xubuntu): sudo /etc/init.d/xdm start
Maybe there are broken packages and you can repair this with
Code:
sudo apt-get -f install 
sudo dpkg --configure -a 
sudo apt-get update 
sudo apt-get upgrade



$sudo apt-get dist-upgrade

Make sure everything is installed by :
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop (or kubuntu-desktop / edubuntu-desktop / xubuntu-desktop)

Now do a reboot :
$sudo reboot
[/HTML]
[COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR]
[HTML]Use the parameter related to the brand or chipset of your video card . pe.: use nouveau  or nvidiafor nvidia based cards (proprietary driver, just nv in some linux distributions, nouveau driver is the default in Mint) ), use radeon for amd/ati cards, i915 for intel based motherboards, ,,,  These are the most common examples.nvidia.modeset=0nouveau.modeset=0radeon.modeset=0i915.modeset=0 r128.modeset=0  (for very old ati rage 128 cards...)If you don't know the brand you may use just one word:   nomodesetYour will find the full range of drivers and more info at Xorg.org wikiPress [Ctrl]+[X] to boot with this added parameter. This parameter will not be saved, just used in this single boot and nothing is damaged. To cancel without changes press [Esc].Hopefully, the system will boot into a default graphical environment and you will be able to install/reinstall driver or configuration packages. In my case I solved my issues in a old nvidia cards (Quadro NVS 280 and geforce 7300LE) using a legacy nvidia 96 or 173 drivers, respectively, in place of nouveau. And nvidia-settings package.Desperate Mode. If you cannot get a graphical user interface with this parameter and/or an 'Monitor frequency error'  there is an alternate way (as always in linux). This situation may happen if you have replaced your video card, or the the driver needs additional parameters (I suffered it with a intel chipset)Use a lower resolution but highly compatible vesa driver. In the same line described in step 3 add this second video mode parameter (grub_gfxmode=). You may use one of themgrub_gfxmode=1280x1024x24      (in most large modern monitors)grub_gfxmode=1024x768x16        (1024x768 is safer in older or smaller systems)Many other settings are possible as: grub_gfxmode=vesa  (...or vga)For those brave enough, more detailed help may be found at Grub2 help in Ubuntu(Solved) Update 2014: My Mint Mate LTS 17.0 re-install (Nvidia Quadro FX1400 dual monitor 19'' 1280x1024x24)Let any Linux distribution 'mature': I waited 1 month before installing this new Mint version. Mate is just for me, and I will try to stick to this LTS. Live is too short to re-install too many times.Black screen or color squares in the first boot after install. Only able to run a 'text' login with nomodeset. Many restarts tried, butNouveau was taking control over display even after blacklisting it in /etc/modprobe.d/blacklist.conf: Ough!Solution as in this tutorial:While system booting menu (Grub) type e to edit the first grub line (Linux Mint ...)add to the linux parameters line 2 flags:  nomodeset  grub_gfxmode=1280x1024x24You will boot with a Linux command line. Don't be annoyed by error screens. Keep calm.Just in case (Linux is still maturing) update your system to get last fixes (this is the first run of the recent distribution !). Just do it.apt-get updateapt-get upgrade[/HTML]

And in recovery it will only go into shell

ARRRGGGHhhh

---

### Post by Jonners59 on 2015-01-04
If in the shell I try ```
sudo service lightdm start
``` then it flashes briefly and I get a lit up blank (black) screen.  I then need to ctrl+alt+f2 to get beck to shell

Have been able to find out some info as requested:
```
lsb_release -a
```
[HTML]No LSB modules are available
Distributor ID = Ubuntu
Description = Ubuntu 14:10
Release = 14:10
Codename = utopic[/HTML]

```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/issue[/FONT][/COLOR]
```
[HTML]Ubuntu 14:10 \n \1[/HTML]

```
uname -a
```
[HTML]Linux mediaserver 3.19.0-031900rc2-generic #201412290135 SMP Mon Dec 29 01:36:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux[/HTML]

---

### Post by Bashing-om on 2015-01-04
Jonners59; One machine at a time, Focus.

machine 1:
what returns from terminal commands:
```

lsb-release -a
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
see what is, then what is to be cleaned up, then start again from anew.

[INDENT][INDENT]back up 3 yards, and punt
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-04
> **Bashing-om said:**
> Jonners59; One machine at a time, Focus.

machine 1:
what returns from terminal commands:
```

lsb-release -a
```
See below


> **Bashing-om said:**
> ```
lspci -nnk | grep -iA3 vga
```
01:00:0 VGA compatible controller [0300]:NVIDIA Corporation GF108 [GFORCE GT 430] 10de:0de1] (rev a1)
Subsystem: Device [196e:0828]
kernel driver in use nouveau
01:00.1 Audio Device [0403]:NVIDIA Corporation GF108 HIGH Definition Audio Controller [10de:0bea] (rev  a1)

> **Bashing-om said:**
> ```
sudo lshw -C display
```
*-display
description:VGA compatible controller
product: GF108 [GFORCE GT 430]
Vendor : NVIDIA Corp
Physical ID; 0
Bus Info: pci@0000:01:00.0
Version: a1
width: 64bits
clock 33MHz
capabilities:pm msi pciexpress vga_controller bus_master cap_list rom
configuration: driver=nouveau latency=0
resources: irq:86 memory:fa000000-faffffff memory:f0000000-f7fffffff memory:f8000000--f9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff

That's it, all copies by hand!!!!

---

### Post by Jonners59 on 2015-01-04
Bashing-om
Have you gone for the night?

Jonners :)

Sorry
I have to hit the sack.  I'll pick this up tomorrow morning if I can...  Many thanks :)

---

### Post by Bashing-om on 2015-01-04
Jonners59; Naw .. still here.

Working several threads and just making my rounds.

OK, on machine 1 there is a Nvidia card, and the open source driver is loaded.
Should workie great. 

So what is ?
What release are we working with and what Desktop Environment ?
Post back:
```

lsb_release -a
echo $DESKTOP_SESSION
ls /usr/share/xsessions
echo $XDG_CURRENT_DESKTOP

```

And we see what we can get when we start the DE from terminal .

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-04
Thought you had to go away...  I was about to hit the sack.  It's quite late here and I have to copy all the info off the screen and type on to this one.  Not fun

1st cmd = 
No LSB modules are available
Distributor ID = Ubuntu
Description = Ubuntu 14:10
Release = 14:10
Codename = utopic

```
[COLOR=#000000][FONT=Ubuntu Mono]echo $DESKTOP_SESSION[/FONT][/COLOR]
``` = blank line/nothing at all

```
[COLOR=#000000][FONT=Ubuntu Mono]ls /usr/share/xsessions[/FONT][/COLOR]
```
gnome.desktop     gnome-fallback.desktop   gnome-flashback-compiz.desktop   Lubuntu-desktop   Lubuntu-Netbook.desktop  openbox.desktop  ubuntu.desktop  xfce.desktop

```
[COLOR=#000000][FONT=Ubuntu Mono]echo $XDG_CURRENT_DESKTOP[/FONT][/COLOR]
``` = also a blank/nothing at all line

---

### Post by Jonners59 on 2015-01-04
Bashin-om
I need to hit the sack.  Can you, please leave me any cmds (home work) I need to do and I'll try and get to the PC before any of the boys get to the Tv (The monitor for this PC) first thing, or evening.....

Good night

Jonners

---

### Post by Bashing-om on 2015-01-04
Jonners59; yikes 

with all these :
> 
gnome.desktop gnome-fallback.desktop gnome-flashback-compiz.desktop Lubuntu-desktop Lubuntu-Netbook.desktop openbox.desktop ubuntu.desktop xfce.desktop

and no DE loaded, we are going to have to tell the system what to load ..

Which is the DeskTop you prefer ? - I do not see unity (lightdm) in any of that bunch , hummm -> maybe falls under "ubuntu.desktop" ?

Consider perhaps getting unity as the default DE ?

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
Xfce.desktop  these all loaded as patt of the cd I used. Was good, it slloeed me to play with them side by a ide. I now/did have it set up to load xfce automatically. 

Unity,  probably is...

dso what next,  Bashing-om...?

---

### Post by Bashing-om on 2015-01-05
Jonners59; Welp;

Let's see what results, and what errors are generated by the system when we start xfce from the terminal.

Boot to terminal and issue terminal command:
```

startxfce4

```

Maybe it is but the Display Manager not knowing what to do. 
I too am getting into a learning mode here; how to find what/where for a Display Manager .


[INDENT]slowly, step by step
[/INDENT]

---

### Post by Jonners59 on 2015-01-05
Thanks Bashing-om
Tried it and it says...

[HTML]/usr/bin/startxfce4: Starting x server
(EE)
Fatal server error:
(EE) Server is already active for display 0
IF THE SERVER IS NOLONGER RUNNING REMOVE /tmp/.XO-lock and start again
(EE)
(EE)
Please consult the x-foundation support... blah, blah, blah...
(EE)
Invalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error[/HTML]

So something must be wrong - again with x-org.conf??????

What next?

---

### Post by Bashing-om on 2015-01-05
Jonners59; Well;

At least it is something ...

What about that advisory for " /tmp/.XO-lock " ; does the file exist ?
```

ls -al /tmp/.XO-lock

```

[INDENT][INDENT]progress made, slowly
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
> **Bashing-om said:**
> Jonners59; Well;

At least it is something ...

What about that advisory for " /tmp/.XO-lock " ; does the file exist ?
```

ls -al /tmp/.XO-lock

```
[INDENT][INDENT]progress made, slowly
[/INDENT]
[/INDENT]


Con not access /tmp/.XO-lock, no such file or directory... :)  Getting somewhere, yes?

---

### Post by Bashing-om on 2015-01-05
Jonners59; Ummphh !

Not what I had anticipated.
OK, even though that file does not exist then. now try:
```

sudo rm /tmp/.XO-lock
sudo rm ~/.Xauthotity

```

Reboot and see if/what starts for the desktop.

Else next we stop the DMs and try then to start xfce.

[INDENT][INDENT]where there is a will there is  a way
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
Sorry, no change....

---

### Post by Bashing-om on 2015-01-05
Jonners59; shucks:

Let's stop the DM - that is to this time unidentified - so we poke .
```

sudo service lightdm stop
startxfce4

```

No still ? Reboot and try as ->
```

sudo service gdm stop
startxfce4

```

else we go to work and find out how to identify the Desktop Manager in play here .

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
Sorry, still no...

The first says "unable to connect to upstart:  Failed to connect to socket /com/ubuntu/upstart: connection failed"

The second gdm is an "unrecognised service"

:(

---

### Post by Bashing-om on 2015-01-05
Jonners59; Hummm ..

So much for my theory .. Making little sense now.
Punting:
What is to start xfce ? Does this file:
```

ls -al .xinitrc

```
exist ?
If so what is it's contents .
easy way to relay:
```

sudo apt-get install pastebinit
cat .xinitrc | pastebinit

```
the output is a URL. pass that URL back here and we take a look at that file ( IF it exist !) .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT][INDENT]othertimes, I just do not know[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
don't exist   Oh my what's up, Doc?!?!?!?!?!?!?

---

### Post by Bashing-om on 2015-01-05
Jonners59; Aaawwww .. 

Again surprised, not what I had expected again, and again ..

However. What do we have ?
```

cat /etc/X11/default-display-manager | pastebinit

``` try'n to see how this relates to xfce .

[INDENT][INDENT][INDENT]it's in a file, somewhere
[/INDENT][/INDENT][/INDENT]

---

### Post by Elfy on 2015-01-05
lightdm not gdm

:)

---

### Post by Jonners59 on 2015-01-05
I am just experimenting with renaming the current x.config and using a config from the past (backed up) version.... ah, didn't work.

Note, and sorry, I forgot to mention, the boot screen shows Xubuntu 14:10.... 

```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/X11/default-display-manager | pastebinit[/FONT][/COLOR]
```

output:
[HTML]/usr/sbin/lightdm
cat: pastebinit: no such file or directory[/HTML]

It does not seem to recognise pastebinit

Isn't there a way of purging the current install and reinstalling and configuring?  Just seems that whatever is there is very broken.

---

### Post by Jonners59 on 2015-01-05
> **Elfy said:**
> lightdm not gdm

:)

Elfy
Thanks for joining.  Your comment lightdm not gdm, is that in relationship to the output I posted?  It is not clear.

The comment was the output from the commands typed in, not what I typed.  Also we have been trying every combination and none work.  Any ideas.

---

### Post by Elfy on 2015-01-05
xubuntu uses lightdm - there's ref in the posts about gdm - not going to work ;)

(Not had time to look properly tbh - will later)

---

### Post by Bashing-om on 2015-01-05
@Elfy Hello, hello !

This is starting to get my goat. Multiple desk tops installed, so what process starts xfce ?

@ Jonners59; Yuk, We keep running into road blocks. And yes, there is always that nuclear solution - (RE-)install that always works. But we learn little by using that option. This to me is still a small matter of starting the display with the correct manager/management. Your preference being xfce. Mind you I do run xfce as my preferred DeskTop but nothing on my system relates to how your system operates as I only run xfce, booting to terminal,  and have no need of a login manager. How I start xfce is not how you start it on your system . We know that because the files to start xfce like I do are not present on your system .

So let us poke at it in another direction:
```

cat /etc/lightdm/lightdm.conf

```
we take Elfy's direction that Xubuntu uses lighdm as the DM. How I do not know yet as my xfce DM is xfwm4.

[INDENT][INDENT]all we want to do is
[INDENT][INDENT][INDENT][INDENT]start the desktop [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
Mmmm  but lightdm is just not working for us either.  that is where we started.

---

### Post by ian-weisser on 2015-01-05
> **Jonners59 said:**
> cat: pastebinit: no such file or directory

Pastebinit is provided by the 'pastebinit' package, which you seem to not have installed yet.


> **Jonners59 said:**
>  Isn't there a way of purging the current install and reinstalling and configuring?

Sure there is. Just dig out the DVD/USB you originally used to install. Or download ubuntu and create a new one.
Do you know how to prevent the problem from recurring? I like knowing the cause, so I think Bashing-om's troubleshooting is the right way.


XFCE is started by lightdm, which replaced gdm a couple years ago. See /etc/init/lightdm.conf
At boot, plymouth (system start and splash screen) hands over to lightdm (login screen). lightdm starts X, and also starts a user-level Upstart daemon for all the user-level tasks (which, in turn, loads the user desktop, spawns a dbus session, etc).

---

### Post by Jonners59 on 2015-01-05
> **Bashing-om said:**
> @Elfy Hello, hello !

This is starting to get my goat. Multiple desk tops installed, so what process starts xfce ?

@ Jonners59; Yuk, We keep running into road blocks. And yes, there is always that nuclear solution - (RE-)install that always works. But we learn little by using that option. This to me is still a small matter of starting the display with the correct manager/management. Your preference being xfce. Mind you I do run xfce as my preferred DeskTop but nothing on my system relates to how your system operates as I only run xfce, booting to terminal,  and have no need of a login manager. How I start xfce is not how you start it on your system . We know that because the files to start xfce like I do are not present on your system .

So let us poke at it in another direction:
```

cat /etc/lightdm/lightdm.conf

```
we take Elfy's direction that Xubuntu uses lighdm as the DM. How I do not know yet as my xfce DM is xfwm4.
[INDENT][INDENT]all we want to do is[INDENT][INDENT][INDENT][INDENT]start the desktop [/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Getting my goat too, and not started on cleaning the sources yet!!!!!  This was built on a Ubuntu CD.  I only wanted xfce, but it, by default installed the works.  Good thing was it allowed me to play with different flavours.  And yes, xfce was my fav too.

OK, back to the plot.

tried the cmd and got
[SeatDefaults]
allow-guest=false
autologin-user=mediaserver
autologin-user-timeout=0

Hope this helps

---

### Post by Jonners59 on 2015-01-05
> **ian-weisser said:**
> Pastebinit is provided by the 'pastebinit' package, which you seem to not have installed yet..
I did with the cmds Bashing-om gave, and it did seem to download.
I'll try again -----  update.  tried again and it confirms it is already installed.

The other problem is I have to hand type everything between machines, including all the outputs..

> **ian-weisser said:**
> Sure there is. Just dig out the DVD/USB you originally used to install. Or download ubuntu and create a new one.
Do you know how to prevent the problem from recurring? I like knowing the cause, so I think Bashing-om's troubleshooting is the right way.
I don't disagree, but it is taking up much more time than I expected and the actual problem, that probably caused all this, the sources being messed up and then updating has yet to be resolved....  Just a thought, but if they were cleared and the default installed, then updated, could that reinstall the correct bits n bobs????


> **ian-weisser said:**
> XFCE is started by lightdm, which replaced gdm a couple years ago. See /etc/init/lightdm.conf
At boot, plymouth (system start and splash screen) hands over to lightdm (login screen). lightdm starts X, and also starts a user-level Upstart daemon for all the user-level tasks (which, in turn, loads the user desktop, spawns a dbus session, etc).
Thanks.  I think i understand that.  Always confuses me how we have graphics issues with the fully up system, yet the demos, and boot screens all work fine.

Does it make a difference that I am using an HDMI cable to our TV, which is our monitor - yes, the kids are giving me grief!!!!  ha ha, dad's revenge.

---

### Post by Bashing-om on 2015-01-05
Jonners59; Thin'in !

In the file " /etc/lightdm/lightdm.conf " there is no user-session defined ... 
Think'n should be something like:
```

[SeatDefaults]
autologin-user=<USERNAME>
autologin-user-timeout=0
user-session=xubuntu
greeter-session=lightdm-gtk-greeter

```

Try'n to think my way through this, perhaps we need to (re)install lightdm ?? Before making this edit .
If we take the sledge hammer approach - install xubuntu-desktop - would that not also install/take care of lighdm ?
--- maybe looking at the source list files has gained in priority ?


[INDENT][INDENT]Google to my rescue[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
My concern is ending up rebuilding a machine that has taken 6 months to get to a stage where I have all the apps I want and all setup as I want - bar a couple of bibs n bobs....  Otherwise I would wipe the lot and start again.

The start of this thread, I think may be the clue.  I had masses of mess and alerts in my respository/sources updates, and I was trying to tidy them up and doing updates at the same time when this happened.  I think it broke the PC.  My graphics was always flaky, another thread I have out, now closed it started to only load in low graphics mode/default, which i fixed, I also, yet to be fixed have an issue with Skype, Kaffine, and Netflix etc where sound is out of sync with video, and at the same time as this, and maybe also related playing DVDs stopped working!!!
So I have a strong belief that the messing with sources and then the subsequent update/upgrade killed the PC...

---

### Post by Elfy on 2015-01-05
> **Jonners59 said:**
> My concern is ending up rebuilding a machine that has taken 6 months to get to a stage where I have all the apps I want and all setup as I want - bar a couple of bibs n bobs....  Otherwise I would wipe the lot and start again.

The start of this thread, I think may be the clue.  I had masses of mess and alerts in my respository/sources updates, and I was trying to tidy them up and doing updates at the same time when this happened.  I think it broke the PC.  My graphics was always flaky, another thread I have out, now closed it started to only load in low graphics mode/default, which i fixed, I also, yet to be fixed have an issue with Skype, Kaffine, and Netflix etc where sound is out of sync with video, and at the same time as this, and maybe also related playing DVDs stopped working!!!
So I have a strong belief that the messing with sources and then the subsequent update/upgrade killed the PC...

Why don't you just post the sources that you've got.

If you can't do so easily with the current situation, boot a live session, mount it and then post them from there. 

Sounds like possibly you've got PPA's kicking about which don't have utopic available.

Once we know what they are - hopefully we can ppa purge them.

Then try and get you to a stable setup.

---

### Post by Jonners59 on 2015-01-05
> **Elfy said:**
> Why don't you just post the sources that you've got.

If you can't do so easily with the current situation, boot a live session, mount it and then post them from there. 

Sounds like possibly you've got PPA's kicking about which don't have utopic available.

Once we know what they are - hopefully we can ppa purge them.

Then try and get you to a stable setup.
BRILLIANT idea.....
Here you are....

[HTML]#############################################################
################### OFFICIAL UBUNTU REPOS ###################

###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ utopic main restricted multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu/ utopic main restricted multiverse
###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ utopic-security main restricted multiverse
deb http://uk.archive.ubuntu.com/ubuntu/ utopic-updates main restricted multiverse
deb http://uk.archive.ubuntu.com/ubuntu/ utopic-backports main restricted multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu/ utopic-security main restricted multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu/ utopic-updates main restricted multiverse
deb-src http://uk.archive.ubuntu.com/ubuntu/ utopic-backports main restricted multiverse
###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu utopic partner
deb-src http://archive.canonical.com/ubuntu utopic partner
###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu utopic main
##############################################################
##################### UNOFFICIAL  REPOS ######################
###### 3rd Party Binary Repos
#### Banshee PPA - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### BitTorrent Sync - http://www.bittorrent.com/sync
## Run this command: sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 6BF18B15
deb http://debian.yeasoft.net/btsync utopic main # disabled on upgrade to utopic
#### Boomaga PPA - https://launchpad.net/~boomaga/+archive/ubuntu/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6DAEA80
deb http://ppa.launchpad.net/boomaga/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Claws Mail PPA - http://www.claws-mail.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ED1D082  
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Clementine PPA - http://www.clementine-player.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu utopic main # disabled on upgrade to utopic
#### Dropbox - http://dropbox.com
## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
#### Equinox PPA - https://launchpad.net/~tiheum/+archive/equinox
## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme    
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu utopic main # disabled on upgrade to utopic
#### exFAT PPA - https://launchpad.net/~relan/+archive/exfat
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A252A784
deb http://ppa.launchpad.net/relan/exfat/ubuntu utopic main # disabled on upgrade to utopic
#### Flacon PPA - http://kde-apps.org/content/show.php?content=113388
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb http://ppa.launchpad.net/flacon/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu trusty-getdeb apps # disabled on upgrade to utopic
#### Gimp PPA - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu utopic main # disabled on upgrade to utopic
#### GNOME3 Extra Apps PPA - https://launchpad.net/~gnome3-team/+archive/gnome3
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main # disabled on upgrade to utopic
#### Google Chrome Browser - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to utopic
#### Google Earth - http://www.google.com/linuxrepositories/
deb http://dl.google.com/linux/earth/deb/ stable main # disabled on upgrade to utopic
#### JDownloader PPA - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu utopic main # disabled on upgrade to utopic
#### Kubuntu Backports PPA - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu utopic main # disabled on upgrade to utopic
#### Kubuntu Beta Backports PPA - https://launchpad.net/~kubuntu-ppa/+archive/beta
deb http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu utopic main # disabled on upgrade to utopic
#### Kubuntu Updates PPA - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa
#### Lazarus - http://www.lazarus.freepascal.org/
## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
deb http://www.hu.freepascal.org/lazarus/ lazarus-stable universe # disabled on upgrade to utopic
#### Lazarus (Testing) - http://www.lazarus.freepascal.org/
#### LibreOffice PPA - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### MariaDB - https://mariadb.org
## Run this command: apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
deb http://mirrors.coreix.net/mariadb/repo/10.1/ubuntu utopic main # disabled on upgrade to utopic
#### Midori PPA - https://launchpad.net/~midori/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb http://ppa.launchpad.net/midori/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### MKVToolnix - http://www.bunkus.org/videotools/mkvtoolnix/
## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
#### MongoDB - http://www.mongodb.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen # disabled on upgrade to utopic
#### Mozilla Daily Build Team PPA - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### muCommander - http://www.mucommander.com/
## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
deb http://apt.mucommander.com stable main non-free contrib # disabled on upgrade to utopic
#### muCommander (unstable) - http://www.mucommander.com/
#### MultiSystem - http://liveusb.info/dotclear/
## Run this command: wget -q http://liveusb.info/multisystem/depot/multisystem.asc -O- | sudo apt-key add -
deb http://liveusb.info/multisystem/depot all main # disabled on upgrade to utopic
#### Opera - http://www.opera.com/
## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
#### Opera Beta - http://www.opera.com/
#### Oracle Java (JDK) Installer PPA - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
#### ownCloud Desktop Client - http://owncloud.org/
## Run this command: wget -q http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_14.04/Release.key -O- | sudo apt-key add -
deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/ / # disabled on upgrade to utopic
#### Paissad's PS3 Media Server - http://deb.paissad.net
## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
deb http://deb.paissad.net unstable main contrib non-free personal # disabled on upgrade to utopic
#### Pidgin PPA - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### PlayDeb - http://www.playdeb.net/
## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu trusty-getdeb games # disabled on upgrade to utopic
#### Plex Media Center - http://www.plexapp.com
## Run this command: wget -q http://plexapp.com/plex_pub_key.pub -O- | sudo apt-key add -
deb http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo lucid main # disabled on upgrade to utopic
#### SABnzbd PPA - http://sabnzbd.org/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Samsung Unified Linux Driver Repository (SULDR) - http://www.bchemnet.com/suldr/index.html
## Run this command: wget -O - http://www.bchemnet.com/suldr/suldr.gpg | apt-key add -
deb http://www.bchemnet.com/suldr/ debian extra # disabled on upgrade to utopic
#### SimpleScreenRecorder PPA - http://www.maartenbaert.be/simplescreenrecorder/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 283EC8CD
#### SMPlayer2 PPA - https://launchpad.net/~smplayer2/+archive/daily
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3A17F739
deb http://ppa.launchpad.net/smplayer2/daily/ubuntu utopic main # disabled on upgrade to utopic
#### Spotify for Linux Preview - http://www.spotify.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
deb http://repository.spotify.com stable non-free # disabled on upgrade to utopic
#### Steam for Linux - http://store.steampowered.com/about/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7
deb [arch=i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to utopic
#### SwissSign - http://swisssign.com/en
## Run this command: http://update.swisssign.com/media/stick/repository/PublicKey -O- | sudo apt-key add -
deb http://update.swisssign.com/media/stick/repository utopic free non-free # disabled on upgrade to utopic
#### Tor: anonymity online - http://www.torproject.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 886DDD89  | sudo apt-key add -
deb http://deb.torproject.org/torproject.org utopic main # disabled on upgrade to utopic
#### Ubuntu Tweak PPA - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu utopic main # disabled on upgrade to utopic
#### UNetbootin PPA - http://unetbootin.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Unsettings PPA - http://www.florian-diesch.de/software/unsettings/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
deb http://ppa.launchpad.net/diesch/testing/ubuntu utopic main # disabled on upgrade to utopic
#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib # disabled on upgrade to utopic
#### WebUpd8 PPA - http://www.webupd8.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu utopic main # disabled on upgrade to utopic
#### WebUpd8 Unstable PPA - http://www.webupd8.org/
deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu utopic main # disabled on upgrade to utopic
#### Wine PPA - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
#### X Updates PPA - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu utopic main # disabled on upgrade to utopic
#### Xorg Edgers PPA - https://launchpad.net/~xorg-edgers
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Yuuguu - http://yuuguu.com
deb http://update.yuuguu.com/repositories/apt hardy multiverse # disabled on upgrade to utopic
####### 3rd Party Source Repos
#### Banshee PPA (Source) - https://edge.launchpad.net/~banshee-team
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### BitTorrent Sync (Source) - http://www.bittorrent.com/sync
deb-src http://debian.yeasoft.net/btsync utopic main # disabled on upgrade to utopic
#### Boomaga PPA (Source) - https://launchpad.net/~boomaga/+archive/ubuntu/ppa
deb-src http://ppa.launchpad.net/boomaga/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Claws Mail PPA (Source) - http://www.claws-mail.org/
deb-src http://ppa.launchpad.net/claws-mail/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Clementine PPA (Source) - http://www.clementine-player.org/
deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu utopic main # disabled on upgrade to utopic
#### Equinox PPA (Source) - https://launchpad.net/~tiheum/+archive/equinox
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu utopic main # disabled on upgrade to utopic
#### exFAT PPA (Source) - https://launchpad.net/~relan/+archive/exfat
#### Flacon PPA (Source) - http://kde-apps.org/content/show.php?content=113388
deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Gimp PPA (Source) - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu utopic main # disabled on upgrade to utopic
#### GNOME3 Extra Apps PPA (Source) - https://launchpad.net/~gnome3-team/+archive/gnome3
#### JDownloader PPA (Source) - https://launchpad.net/~jd-team
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu utopic main # disabled on upgrade to utopic
#### Kubuntu Backports PPA (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu utopic main # disabled on upgrade to utopic
#### Kubuntu Beta Backports PPA (Source) - https://launchpad.net/~kubuntu-ppa/+archive/beta
deb-src http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu utopic main # disabled on upgrade to utopic
#### Kubuntu Updates PPA (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa
#### LibreOffice PPA (Source) - http://www.documentfoundation.org/download/
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### MariaDB (Source) - https://mariadb.org
#### Midori PPA (Source) - https://launchpad.net/~midori/+archive/ppa
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### MKVToolnix (Source) - http://www.bunkus.org/videotools/mkvtoolnix/
#### Mozilla Daily Build Team PPA (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Oracle Java (JDK) Installer PPA (Source) - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
#### Paissad's PS3 Media Server (Source) - http://deb.paissad.net
deb-src http://deb.paissad.net unstable main contrib non-free personal # disabled on upgrade to utopic
#### Pidgin PPA (Source) - http://pidgin.im
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### SimpleScreenRecorder PPA (Source) - http://www.maartenbaert.be/simplescreenrecorder/
#### SMPlayer2 PPA (Source) - https://launchpad.net/~smplayer2/+archive/daily
deb-src http://ppa.launchpad.net/smplayer2/daily/ubuntu utopic main # disabled on upgrade to utopic
#### Tor: anonymity online (Source) - http://www.torproject.org/
deb-src http://deb.torproject.org/torproject.org utopic main # disabled on upgrade to utopic
#### Ubuntu Tweak PPA (Source) - http://ubuntu-tweak.com/
deb-src http://ppa.launchpad.net/tualatrix/ubuntu utopic main # disabled on upgrade to utopic
#### UNetbootin PPA (Source) - http://unetbootin.sourceforge.net/
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu utopic main # disabled on upgrade to utopic
#### Unsettings PPA (Source) - http://www.florian-diesch.de/software/unsettings/
deb-src http://ppa.launchpad.net/diesch/testing/ubuntu utopic main # disabled on upgrade to utopic
#### WebUpd8 PPA (Source) - http://www.webupd8.org/
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu utopic main # disabled on upgrade to utopic
#### WebUpd8 Unstable PPA (Source) - http://www.webupd8.org/
deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu utopic main # disabled on upgrade to utopic
#### Wine PPA (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
#### X Updates PPA (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu utopic main # disabled on upgrade to utopic
deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main # disabled on upgrade to utopic[/HTML]

[HTML]deb http://ppa.launchpad.net/app-review-board/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/benoitfra/google2ubuntu/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/darkxst/gdm-prime/ubuntu utopic main # disabled on upgrade to utopic
deb-src http://ppa.launchpad.net/darkxst/gdm-prime/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/docky-core/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu utopic main
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu utopic main # disabled on upgrade to utopic
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu utopic main # disabled on upgrade to utopic
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu utopic main
deb http://ppa.launchpad.net/flozz/flozz/ubuntu utopic main # disabled on upgrade to utopic
deb http://archive.getdeb.net/ubuntu trusty-getdeb apps # disabled on upgrade to utopic
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to utopic
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/graysky/utils/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu trusty main
deb ftp://ftp.videolan.org/pub/debian/stable ./ # disabled on upgrade to utopic
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu utopic main # disabled on upgrade to utopic
deb http://liquorix.net/debian sid main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu utopic main # disabled on upgrade to utopic
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://ppa.launchpad.net/me-tv-development/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb-src http://ppa.launchpad.net/me-tv-development/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/pipelight/stable/ubuntu utopic main # disabled on upgrade to utopic
deb http://archive.getdeb.net/ubuntu trusty-getdeb games # disabled on upgrade to utopic
deb http://ppa.launchpad.net/plexapp/plexht/ubuntu utopic main # disabled on upgrade to utopic
deb http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo lucid main # disabled on upgrade to utopic
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/mycraft/ubuntu utopic main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to utopic
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to utopic
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu utopic main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to utopic
deb http://ppa.launchpad.net/pulse-eight/libcec/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/shutter/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb http://download.skype.com/linux/repos/debian/ stable non-free #Repository for Skype (stable) disabled on upgrade to utopic
deb http://repository.spotify.com stable non-free
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to utopic
deb http://repo.steampowered.com/steamos/ alchemist main non-free contrib
deb http://ppa.launchpad.net/synapse-core/testing/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/webupd8team/gthumb/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/webupd8team/nemo/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu utopic main # disabled on upgrade to utopic
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu utopic main
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu utopic main # disabled on upgrade to utopic 
[/HTML]

PS:  CD perfect graphics...
PPS:  Surprised there isn't a tool or comd to compaire and tidy these up.

---

### Post by Bashing-om on 2015-01-05
+1 for getting the sources lists straightened out.. We will need the package manager soonest now.

---

### Post by Jonners59 on 2015-01-05
> **Bashing-om said:**
> +1 for getting the sources lists straightened out.. We will need the package manager soonest now.

?  How do I do that?

---

### Post by Bashing-om on 2015-01-05
Jonners59; Hey.

Let's do a number like unto this:
```

cat -n /etc/apt/sources.list | pastebinit
cat /etc/apt/sources.list.d/*.list | pastebinit

```
the outputs are URLs. pass the URL back here and we see what the source list files look like.


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
Very odd,given I used the CD to find these files, but both cmds come back wth an error message, Directory does not exist.  I shall boot back in to the CD and try again.

---

### Post by Elfy on 2015-01-05
> **Jonners59 said:**
> Very odd,given I used the CD to find these files, but both cmds come back wth an error message, Directory does not exist.  I shall boot back in to the CD and try again.

You need to mount the / partition - maybe /mnt

If the partition is sda1

```
sudo mount /dev/sda1 /mnt
```

Then


```
cat -n /mnt/etc/apt/sources.list | pastebinit
cat /mnt/etc/apt/sources.list.d/*.list | pastebinit
```

Just running it as in previous post will get the sources for the livecd

---

### Post by Bashing-om on 2015-01-05
Jonners59; Yukkie !

Most disconcerting !

Boot the install to terminal:
what returns ?
```

ls -al /etc/apt/sources.list

```
That we can take care of .. but the 3rd party directory .. not possible to rebuild it if it is missing !
```

ls -al /etc/apt/sources.list.d/

```

[INDENT][INDENT][INDENT]Ho Boy, fingers are crossed
[/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
> **Elfy said:**
> You need to mount the / partition - maybe /mnt

If the partition is sda1

```
sudo mount /dev/sda1 /mnt
```

Then


```
cat -n /mnt/etc/apt/sources.list | pastebinit
cat /mnt/etc/apt/sources.list.d/*.list | pastebinit
```

Just running it as in previous post will get the sources for the livecd

[http://paste.ubuntu.com/9678669/](http://paste.ubuntu.com/9678669/)

[http://paste.ubuntu.com/9678673/](http://paste.ubuntu.com/9678673/)

Hope this is OK...  They should look like the outputs below.... 45 minutes ago.

---

### Post by Bashing-om on 2015-01-05
Jonners59; Yikes !

A lot of PPAs, this will take some time to go through ,, and you can bet you have exceeded that 40 key limit .

[INDENT][INDENT]meanwhile
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
> **Bashing-om said:**
> Jonners59; Yikes !

A lot of PPAs, this will take some time to go through ,, and you can bet you have exceeded that 40 key limit .[INDENT][INDENT]meanwhile[INDENT][INDENT][INDENT]back at the ranch
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I said it was a mess..!.  And that is why I was surprised there was/is no tool to clean up automatically, especially as when doing a update it gives a log...

Shall I shutdown and log off for the eveing if it's going to take a long time?  I have a long day job hunting tomorrow.

---

### Post by Bashing-om on 2015-01-05
et al; Yikes, yikes !


My findings ->


NOT supported in utopic:
[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)
[http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu)
[http://ppa.launchpad.net/relan/exfat/ubuntu](http://ppa.launchpad.net/relan/exfat/ubuntu)
[http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu)
[http://ppa.launchpad.net/smplayer2/daily/ubuntu](http://ppa.launchpad.net/smplayer2/daily/ubuntu)
[http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)
[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)
[http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu)
[http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) (source)
[http://ppa.launchpad.net/smplayer2/daily/ubuntu](http://ppa.launchpad.net/smplayer2/daily/ubuntu) (source)
[http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) (source)
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) (source)

uncertain. nothing new in some time:
[http://www.hu.freepascal.org/lazarus/](http://www.hu.freepascal.org/lazarus/) lazarus-stable
[http://downloads-distro.mongodb.org/repo/ubuntu-upstart](http://downloads-distro.mongodb.org/repo/ubuntu-upstart)
[http://apt.mucommander.com](http://apt.mucommander.com)



What this means for the present Operating System too soon to say .
[http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/](http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/)
[http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib
deb [http://update.yuuguu.com/repositories/apt](http://update.yuuguu.com/repositories/apt) hardy multiverse
[http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/)

can not say:
deb [http://deb.paissad.net](http://deb.paissad.net) unstable main contrib non-free personal
[http://deb.paissad.net](http://deb.paissad.net) unstable main contrib non-free personal (source)


Not found:
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
[http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo](http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo) lucid main



Research, no longer supported ?
[http://repository.spotify.com](http://repository.spotify.com)

Research and update:
deb [arch=i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
----------------------------------------
That is but page one, should we continue ??
Mixed releases - as far back as hardy -, mixed distributions ... I do think you are better served to wipe this install and start all over again. I do not have the skills personally to cope with debian, sarge and opensusie thrown into the mix. But I asked for a learning experience, and this might be a real learning experience !

What say you all ?

[INDENT][INDENT]where there is a will there is a way
[INDENT][INDENT][INDENT][INDENT]but it sure will not be easy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-05
Yowza!
Put like that it is even worse.  Given I built this from scratch on a 13:10 CD, I am amazed about the old stuff and the mix.  I am trying to run Tvs, media centres, DVD/CD playback, Satellite and game emulators from this, hence media centre.  Hence the very high spec machine: Ausus Rampage IV Extreme, 32Gb RAM, Intel i7 8 core processor, and 2 x 1Tb HDs. Not really found a nice way to do it though.

I am out job hunting tomorrow and then mum over so little time to play, and about to hit the sack right now, so if you feel like a challenge, who am I to say no, but if it is easier and you don't want the challenge then I am just as OK with a clean sweep.  I just need advise about keeping the apps up todate that are not in the basic pack.....

---

### Post by oldfred on 2015-01-05
I have this in my notes on creating a new sources list. Never tried, but if thinking of re-installing any way it maybe worth a try. Be sure to have good backups.

 Best command to reset apt sources to distro release defaults?
[http://ubuntuforums.org/showthread.php?t=1858451](http://ubuntuforums.org/showthread.php?t=1858451)
Also discussion of ppa-purge and apt-setup

      
 Ubuntu Sources List Generator
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Jonners59 on 2015-01-05
Hello or should I say good evening Oldfred
I have collected all my ex helpers in one.  Great to hear from you.  :) and thanks for popping in.

Before digging in to this, I will let Bashing-om decide what he wants to do :)  he likes and asked for a challenge.

---

### Post by Bashing-om on 2015-01-05
Jonners59; Hey ;

It depends on the amount of time and effort you can expend in attempting to salvage this install. I am more than willing to see where this leads.
Even when we get the sources workable, there is still the desk top to get activated. We do not know what impact opensussie may have on it !
But to the problem at hand, will be of interest to see how much pruning we will have to do to get under that 40 key limitation.
For background discussion, see:
[http://ubuntuforums.org/showthread.php?t=2195579](http://ubuntuforums.org/showthread.php?t=2195579)
what returns from terminal command:
```

ls /etc/apt/trusted.gpg.d | wc -l

```
which will show how many keys are installed.

I say again -> it is a whole lot easier to build up
[INDENT][INDENT][INDENT][INDENT]than it is to tear down
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-01-05
> **Jonners59 said:**
>  I am just as OK with a clean sweep.  I just need advise about keeping the apps up todate that are not in the basic pack.....

Here's how I keep all the stuff I experiment with from taking over the world and breaking my system. You may have a better system:

1) I use the current release of Ubuntu, and update every 6 months. This keeps the number of PPAs and other software to a minimum.

2) When Software-updater prompts me weekly, I look at the list of applications it wants to update. If I don't use that application, I uninstall it. I can always reinstall it later. This helps me fight the system bloating up as I install (and then forget that I installed) new software to try.

3) When I upgrade to the next release of Ubuntu, I scrub all the non-Ubuntu software: I deactivate older non-Ubuntu sources and PPAs, and uninstall their software completely. This prevents two types of common upgrade failures.

4) I keep a journal -just a simple text file- of what I install (packages) or customize (scripts and cron jobs), when I did it, how I did it, and the link to the instructions I followed. I assume that in six months I will completely forget what I did. The journal tells me how to uninstall it or reinstall it. I'd have reinstalled a couple times in the past year...if my notes hadn't saved me.

5) I do regular data backups. Just data, not packages nor package lists nor other customizations. I don't need to back those up...since I have my notes.

6) I do much of my experimenting in *containers* or VMs. Example: Last week, I needed to test a Wordpress theme. I started a container (lxc), installed a cloud image of Ubuntu, installed a LAMP stack, installed Wordpress, installed the theme. I made my changes, ran my tests, finished and uploaded my work...and then erased the container. My /etc and /home are safely unpolluted by all that installing and uninstalling. I can recreate the container in about 15 minutes if needed, thanks to my notes.

---

### Post by Jonners59 on 2015-01-06
Ok. Bashing-om. 
Lets go for a fresh sources...  how do we go about this? Adding back anything relevant that missing we can cover later. ..

---

### Post by ajgreeny on 2015-01-06
Try that repogen link given by **oldfred**, it lets you choose options of what is needed by you, including many ppa repos  but forget those at the moment and just go for the standard repos, including universe and multiverse, but no others.  Add in the updates repos except perhaps for proposed and backports which you can add later if you need to, and unless you have good reason to need them, don't add any source repos; they are a bit OTT at this stage of problem solving.

That will then make a new text file that you can download and use to replace your current sources.list file, but back that up first as it may be useful when you want to see all the added repos you used in this problem install.

Looking at the list of PPAs that you have I suspect that your problem sources.list file may have been generated by a rather demanding but perhaps over-ambitious person using that repogen site, as all the PPAs seem to be in the same order as they are offered on that site.

Good luck!

---

### Post by schragge on 2015-01-06
> **ajgreeny said:**
> Looking at the list of PPAs that you have I suspect that your problem sources.list file may have been generated by a rather demanding but perhaps over-ambitious person using that repogen site, as all the PPAs seem to be in the same order as they are offered on that site. Good catch! The general file structure (first all the 3rd part deb entries, then all the deb-src entries) and comments support this, too.

 Also, some of the entries in */etc/apt/sources.list* have duplicates under */etc/apt/sources.list.d/*.list* (e.g. Google Chrome, GetDeb, Spotify, etc.). Cannot speak for all of them, but at least Google Chrome package *may* automatically create */etc/apt/sources.list.d/google-chrome.list* on install if the file doesn't already exist. This means that enabling Chrome through repogen in the main /etc/apt/sources.list, then installing Chrome with a package manager will create the duplicate entry for it in */etc/apt/sources.list.d/google-chrome.list* unless you explicitly disable this behaviour by creating */etc/default/google-chrome* with the following contents
```
repo_add_once=false
```  *before* installing Chrome. Unfortunately, by doing this you'll also prevent the GPG key for Google repository from being automatically added to the GPG database on install. Thus, the preferred way for installing Chrome is just by downloading the .deb package for it from the Google website. After having been installed once, it will be updated automatically through APT.

  And interestingly enough, official Ubuntu **universe** repository doesn't appear anywhere in the list. Perhaps enabling it would seriously decrease the need in PPAs.

---

### Post by Bashing-om on 2015-01-06
et al;

^^ great advise all ... Keep in mind the integrity of the keyring system. need to get under that 40 GPG limit.
```

ls /etc/apt/trusted.gpg.d | wc -l

```

Community projects are great fun

---

### Post by Jonners59 on 2015-01-06
OMG guys....  A lot for a plonker like me to take on board...

I shall not be doing anything this evening but will give Bashing-om's cmd  ```
[COLOR=#000000][FONT=Ubuntu Mono]ls /etc/apt/trusted.gpg.d | wc -l[/FONT][/COLOR]
``` a go tomorrow.

Question.  Do I run this in the terminal after booting in to live CD or boot the machine and use the , is it called headless state?????

I guess, also, are there any other cmds I should run after.  I might as well get the list of them!!!!

SOme of the stuff I have picked out of below...
```
[COLOR=#000000][FONT=Ubuntu Mono]ls /etc/apt/trusted.gpg.d | wc -l[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Ubuntu Mono]repo_add_once=false[/FONT][/COLOR]
```

[HTML]command to reset apt sources to distro release defaults?
http://ubuntuforums.org/showthread.php?t=1858451
Also discussion of ppa-purge and apt-setup


schragge
Thanks...  I think examples like that are a real issue and for novices like me, a major cause of our headaches.....
Ubuntu Sources List Generator
http://repogen.simplylinux.ch/[/HTML]

---

### Post by Elfy on 2015-01-06
Regarding the commands.

If you run them as they are in the livesession - they will report the livesession - not what you want.

So - and this would work for anything.

Mount your partition - for this example I will assume that what you want to look at is on sda1

```
sudo mount /dev/sda1 /mnt
```

This mounts your install to /mnt

So your home (assuming username) would be at 

```
/mnt/home/jonners
```

Sliding back to the command you would, AFTER mounting it

```
ls /mnt/etc/apt/trusted.gpg.d | wc -l
```

Editing anything can be done in the livesession in the same way.

```
sudo nano /etc/fstab
```

would get you nowhere

```
sudo nano /mnt/etc/fstab
```

has helped me before :)

---

### Post by Jonners59 on 2015-01-07
> **Elfy said:**
> Regarding the commands.

If you run them as they are in the livesession - they will report the livesession - not what you want.

So - and this would work for anything.

Mount your partition - for this example I will assume that what you want to look at is on sda1

```
sudo mount /dev/sda1 /mnt
```

This mounts your install to /mnt

So your home (assuming username) would be at 

```
/mnt/home/jonners
```

Sliding back to the command you would, AFTER mounting it

```
ls /mnt/etc/apt/trusted.gpg.d | wc -l
```

Editing anything can be done in the livesession in the same way.

```
sudo nano /etc/fstab
```

would get you nowhere

```
sudo nano /mnt/etc/fstab
```

has helped me before :)

Elfy
Many thanks for that, was what I had suspected and the confirmation enabled me to carry all this out.  Incidentally, the drive can be mounted simply by double clicking the desktop icon.  It then also has it's address, which can be coppied or noted, I found it to be /media/ubuntu/xxxx on mine

Also, FYI: I am using /sdb1 and the machine name is mediaserver.

OK
so I carried out all this, creating a new sources list and synaptic sources list...  Actually I used this before, that is how I got my list.  I am surprised that there isn't a tool or a cmd that just simply scans the PC for installed apps and cross references to the db this list is created from, and create/check the lists and create them..  even if it has to single out as unknown app for those it does not recognise.

Next there is also a list of cmds for the KEYs...  Not sure how I do these given my circumstances and the size of the list?  I have pasted below.
Then, if I recall, there is also another list somewhere else.  Isn't this where the conflict/issues really are?  How do I resolve that list?

Then how do I "activate" it, if that is the correct term/I am understood.
?????

Naturally, I still can not login.

Also, I still have a question in my head, something I really don't understand.  The PC runs GREAT from the CD, so what is so different?  Can anything, be coppied across?  This is something that has had me curious for the past couiple of years.  See so many threads re not able to boot after install, yet CD was fine/demo.  Sureley that says the drivers and settinsg are fine.

Anyway...  What next, please?


[HTML]sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 6BF18B15
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6DAEA80
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ED1D082  
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
 gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
wget -q http://liveusb.info/multisystem/depot/multisystem.asc -O- | sudo apt-key add -
sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
wget -q http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_14.04/Release.key -O- | sudo apt-key add -
wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
wget -q http://plexapp.com/plex_pub_key.pub -O- | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 283EC8CD
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
[/HTML]

---

### Post by Bashing-om on 2015-01-07
Jonners59; Hang'n in here ...

My thought process remains to get the PPAs trimmed down to something manageable .
I still want to see what is:
```

ls /mnt/etc/apt/trusted.gpg.d | wc -l

```

Then I think we need to focus on reverting all the PPA's we can back to the versions available in the software repository. 
Remove all that are no longer supported ..

as to this:
> 
Also, I still have a question in my head, something I really don't understand. The PC runs GREAT from the CD, so what is so different? Can anything, be coppied across? This is something that has had me curious for the past couiple of years. See so many threads re not able to boot after install, yet CD was fine/demo. Sureley that says the drivers and settinsg are fine.


There are a number of required differences in the environments of the liveDVD and the actual install . Mostly configurations and drivers.
The live environment is decompressed into ram, the real install is further copied to disk. That changes a whole bunch of things. The kernel goes hunting up what it needs in order to boot up from the hardware it detects on the system - for the given environment it is going to work in.

Copying  files from the liveDVD to the install: yes and no .. the liveDVD is staid -what was .. updates and upgrades in the install changes many things. Though the file system format remains the same, the files MAY be different . Configurations are definitely different .
If it works in the liveDVD, we can make it work in the install ; sometimes the kernel needs a helping hand.

It is a complex system, and all has to work together or ya get this present circumstance, the GUI will not start .

[INDENT][INDENT]fault isolation to restoration
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-07
Thanks Bashin-om
PS: I tried that cmd earlier and it just gave a number - 24.  I will try again.
Best
J

---

### Post by Bashing-om on 2015-01-07
Jonners59; Good !

That you get the '24' as an response. Well under the limit. That is a relieve to me.
 
So, where now do we stand ? Have you disabled these:
> 
NOT supported in utopic:
[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)
[http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu)
[http://ppa.launchpad.net/relan/exfat/ubuntu](http://ppa.launchpad.net/relan/exfat/ubuntu)
[http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu)
[http://ppa.launchpad.net/smplayer2/daily/ubuntu](http://ppa.launchpad.net/smplayer2/daily/ubuntu)
[http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)
[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)
[http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu)
[http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) (source)
[http://ppa.launchpad.net/smplayer2/daily/ubuntu](http://ppa.launchpad.net/smplayer2/daily/ubuntu) (source)
[http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) (source)
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) (source)


we do this in small steps ? Then take a look at what the package manager thinks ?
[INDENT][INDENT]even small steps, we get to the journey's end
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-01-08
Hiya
Was actually 29 when I managed to get in again, this am.

I can not disable those repos as I can't get into the package manager.  How do I do that?  I am running in cmd with no desktop GUI.

I ran sudo apt-get update and got a list of duplicates too, which is 100s x smaller than it was.  How do I remove these babes:

dropbox
webup8team
plexmediaserver
simplescreenrecorder
repository-spotify/non-free
steampowered
not the full address!!!!

Still hangin' in there!

---

### Post by Elfy on 2015-01-08
There's probably a way to do so from the command line - but it's early morning and I've not got enough tea in me yet to even dig out google-fu.

You CAN disable manually.

Use sudo nano and you don't need a gui.

Edit the ppa sources. 

```
ls /etc/apt/sources.list.d
```

To get the source file list

Then open each and edit.

```
sudo nano /etc/apt/sources.list.d/nameofppa
```

put a # in front of each line and then save Ctrl+O then Ctrl+X

Once you've done them all - update the sources.

---

### Post by Jonners59 on 2015-01-08
> **Elfy said:**
> There's probably a way to do so from the command line - but it's early morning and I've not got enough tea in me yet to even dig out google-fu.

You CAN disable manually.

Use sudo nano and you don't need a gui.

Edit the ppa sources. 

```
ls /etc/apt/sources.list.d
```

To get the source file list

Then open each and edit.

```
sudo nano /etc/apt/sources.list.d/nameofppa
```

put a # in front of each line and then save Ctrl+O then Ctrl+X

Once you've done them all - update the sources.
Thanks Elfy

This is scary...  I just took a brief look at this on another PC and compared the lists and actual folder view, of course the file name is not the same as the ppa listed below and being unable to open the directory on the faulty PC, this is going to be fun!!!!!   I guess I could run something like```
ls /etc/apt/sources.list.d/
```, at least I'd have a list to keep referring back to.

If I can get on the PC, I'll have a bash tonight.

---

### Post by Elfy on 2015-01-08
Given that this has taken long enough to do a clean install about 100 times so far - I wonder if you're going to be better of just biting the bullet and doing a clean install ...

Just a thought.

---

### Post by Bashing-om on 2015-01-08
Jonners59; Hello,

I too am just getting started for the day here on the forum.
As many 'src' sources as you have ,, I had the thought that you were quite comfortable with a terminal and a terminal editor; and programming in general.
Keep in mind, there is nothing you do from the GUI one can not do in the CLI . Just different tools and a different perspective to work with.

Always, always make a back up of any file you are going to edit. -1st law ! Disaster can strike from any direction.

Have you now commented out those PPAs that are no longer supported .... commented out the duplicates source "fetches".
Are we now ready to move on to 'ppa-purge' ?
If you do not need it, get rid of it .

Keep in mind  schragge's catch:
> 
And interestingly enough, official Ubuntu universe repository doesn't appear anywhere in the list. Perhaps enabling it would seriously decrease the need in PPAs.

post #56 - bears re-reading and adhering to.

We get the sources.list files(s) all straightened out, and the package manager in a happy state, then we go back to finding out why the GUI fails to launch. That be what I have in mind, that be my plan.

A long process and a tall order
[INDENT][INDENT][INDENT]we can work through it [/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-01-08
I just found in another thread a complaint about the red icon. I also had that but ignored it as I thought it was related to printer. When I checked I had several PPAs that were invalid.

So I went into synaptic, unchecked them there and updated. I had not any issues with updates other than when I manually ran the update it did tell my my PPAs were invalid.

So synaptic is another way to edit out PPAs.

---

### Post by Jonners59 on 2015-01-09
Sorry for disappearing guys...  Been playing catchup on loads of things, plus I took Elfy's advise and started over.  Not least as I have two machines to get up and running, family giving me grief over this and a job to find.  However, IT DID highlight some issues.

So as recommended I installed a clean version in both machines...  Note the second machine had NO ISSUES or sudo apt-get update error messages, duplicated, failed or anything.  BOTH failed after an automated upgrade.  I think that is significant, because, on installing the new install on a second partition on machine one, and having it all perfect...  I was in Synaptic Manager, and as suggested at some point I should look in the Filters.  I did that.  I added the " recommended" items, about 10 and committed them.  It failed, said there were broken packages.  Tried the repair.  That failed to work, so I went to the "Broken Packages" filter, there were two...  One GRUB and one for a n other app.  I unticked them and ran the install.  It failed again, said broken packages.  Tried the fix.  Failed again.  Went to the filter and there there were about 5 new apps.  unticked them and completed the install.  AFter a reboot, I now can not get in to the machine.  GRUB failure.
I had not added anything of note....  this implies to me that there maybe an issue with broken packages in the default install.

Anyway now trying to burn a new Boot-Repair CD, and HOPEFULLY that will work and I will be able to fix GRUB and get back in.  AT the moment it goes in to GRUB RESCUE, says XXXX directory can not be found so it looks like it may just need a sudo grub-update.

Will get back.

---

### Post by oldfred on 2015-01-09
The grub package and install is essential for a good reboot.
Boot-Repair may fix it, if not run the summary report.

Some also use Supergrub to boot and repair from inside the install.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I keep Boot-Repair, Supergrub, Knoppix, gparted ISO, and parted magic as well as Ubuntu live installer as ISO so I can boot any of them. Good to have at least a couple repair tools in tool box, some like a lot. :)

---

### Post by Jonners59 on 2015-01-09
I love Boot-Repair... <3

So, I now have the machine 1 up and running with a good sources list.  It is still 14.04, so I will gingerly upgrade the moment I am allowed on it again.

I will then clean up the desktop and layout and then reinstall all the Game Emulators...

I then need to find a way to protect it or at least recover without a full rebuild going forward.  It takes an age.

Machine 2, I have to find a way to get the VM image back and working.  I don't want to have to try and rebuild that baby!!!!  Maybe another thread.

Subject to all these going to plan and no more hiccups, I will close this thread.

> **oldfred said:**
> 
Some also use Supergrub to boot and repair from inside the install.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I keep Boot-Repair, Supergrub, Knoppix, gparted ISO, and parted magic as well as Ubuntu live installer as ISO so I can boot any of them. Good to have at least a couple repair tools in tool box, some like a lot. :)  - Thanks OldFred.  SOme new toys to look out for!

---

### Post by Jonners59 on 2015-01-15
Well, not really sure what to write here.

Have both machines running now after fresh installs.  Neither is as it was and struggling to get them there again - not happy about that.  There must be a way of saving all the installed apps and their configs (including fstab, smb, soduers, gnome, panels, desktop) , including the desktop, and any scripts (Virtual Machine auto start, VM auto shutdown, no-ip start, Stunnel, DNLA) without having to go back to scratch and try and recover from memory.

And why does a new install also not recognise that an existing Home Directory is available...  It could quite easily offer to use it and just upgrade/reinstall any requirements...

There are real problems with this latest "upgrade".  after the rebuild, from the start there were broken sources and problems, without anything being changed.  And the problem that caused both machines to crash after rebuild seems to be a known bug with more incidents being added daily, c3,000 currently.  All to do with the nvidia drivers and the new kernel.

So not happy about that.

I have fixed the problem, but not by cleaning out the sources effectively, but starting from scratch, so the thread is NOT Solved, just closed.

I do appreciated the fantastic support from everyone, just disappointed I was not able to resolve the thread and more serious problems then manifested themselves as part of the latest upgrade. - holding back on the last couple of machines until I see these bugs have gone away.

---

### Post by Jonners59 on 2015-08-06
Bashing-on, Elfy and Oldfred
I am having install/update issues - same machine - again.

I got in to synaptic and try and install vlc (typical app so no issues expected) but it will not install, says "unmet dependencies".  I do an update and key apps are listed for removal.  I have gone to the repository builder site and created a new repository and installed - backed up the old (:D), but still get the same problems.

Any ideas.....  If need be I shall start a new thread and run any cmd to get info.
[ATTACH=CONFIG]263678[/ATTACH][ATTACH=CONFIG]263679[/ATTACH]

---

### Post by Bashing-om on 2015-08-06
Jonners59; Hey ;

Long time no hear, I trust things have been well.

If you start a new thread you will gain a broader audience, but I am willing to work on this. the thread we have worked.
I do require to work from terminal, and all results posted from the terminal. Much much easier and the more informative to work with.
Please post back the outputs - Between Code Tags - the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```
To see the state of the package manager, and what hints there are to make it happy.
Also want to take a look at the source fetch files:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


Then we can look at what the cause of the vnc installation difficulties are.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-08-07
> **Bashing-om said:**
> Jonners59; Hey ;

Long time no hear, I trust things have been well.

Yes, it has.  Still having a go and still managing to mess things up and have a go :-)
I do have a couple of threads out...  Just to keep in touch and you guys on your toes.  I know you like a challenge.

You good?

> **Bashing-om said:**
> 
If you start a new thread you will gain a broader audience, but I am willing to work on this. the thread we have worked.
I do require to work from terminal, and all results posted from the  terminal. Much much easier and the more informative to work with.
Please post back the outputs - Between Code Tags - the outputs of terminal commands:
```
sudo apt-get update
```

There is more than the original as I used the sources rebuild tool ([http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) )   .....
```
(gedit:15054): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:15054): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:15054): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:15054): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:15054): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:15054): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
mediaserver@SERVER:~/Desktop$ sudo gedit /etc/apt/sources.list

(gedit:15063): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:15063): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:15063): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:15063): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:15063): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:15063): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
mediaserver@SERVER:~/Desktop$ sudo gedit /etc/apt/gpg_keys.txt 

** (gedit:15078): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:15078): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:15078): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
mediaserver@SERVER:~/Desktop$ sudo gedit /etc/apt/gpg_keys.txt 

(gedit:15089): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:15089): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:15089): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:15089): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:15089): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

(gedit:15089): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:15089): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:15089): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:15089): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
mediaserver@SERVER:~/Desktop$ sudo apt-get update
Ign http://ppa.launchpad.net vivid InRelease
Ign http://archive.canonical.com vivid InRelease                               
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://dl.google.com stable InRelease                                      
Hit http://archive.canonical.com vivid Release.gpg                             
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://mega.nz ./ InRelease                                                
Hit http://archive.canonical.com vivid Release                                 
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:1 http://mirrors.coreix.net vivid InRelease [2,487 B]                      
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://mirrors.coreix.net vivid InRelease                                  
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://mirrors.coreix.net vivid/main Sources/DiffIndex                     
Get:2 http://mega.nz ./ Release.gpg [189 B]                                    
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:3 http://mega.nz ./ Release [967 B]                                        
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid/partner Sources                         
Ign http://mega.nz ./ Release                                                  
Hit http://dl.google.com stable Release.gpg                                    
Ign http://mirrors.coreix.net vivid/main amd64 Packages/DiffIndex              
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Hit http://repo.daniil.it lenny InRelease                                      
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid/partner i386 Packages                   
Ign http://mirrors.coreix.net vivid/main i386 Packages/DiffIndex               
Hit http://dl.google.com stable Release                                        
Ign http://uk.archive.ubuntu.com vivid InRelease                               
Ign http://downloads-distro.mongodb.org dist InRelease                         
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid/partner Translation-en                  
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://uk.archive.ubuntu.com vivid-security InRelease                      
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://apt.mucommander.com stable InRelease                                
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:4 http://repo.daniil.it lenny/main amd64 Packages [1,113 B]                
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Ign http://linux.dropbox.com vivid InRelease                                   
Ign http://www.hu.freepascal.org lazarus-stable InRelease                      
Ign http://liveusb.info all InRelease                                          
Get:5 http://dl.google.com stable/main amd64 Packages [469 B]                  
Ign http://uk.archive.ubuntu.com vivid-updates InRelease                       
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:6 http://dl.google.com stable/main i386 Packages [464 B]                   
Ign http://www.hu.freepascal.org lazarus-testing InRelease                     
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:7 http://repo.daniil.it lenny/main i386 Packages [1,113 B]                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://deb.opera.com stable InRelease                                      
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:8 http://www.hu.freepascal.org lazarus-stable Release.gpg [191 B]          
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Ign http://uk.archive.ubuntu.com vivid-backports InRelease                     
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://linux.dropbox.com vivid Release.gpg                                 
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:9 http://www.hu.freepascal.org lazarus-testing Release.gpg [191 B]         
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://www.hu.freepascal.org lazarus-stable Release                        
Ign http://www.hu.freepascal.org lazarus-stable Release                        
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://uk.archive.ubuntu.com vivid Release.gpg                             
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:10 http://www.hu.freepascal.org lazarus-testing Release [1,432 B]          
Ign http://www.hu.freepascal.org lazarus-testing Release                       
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Ign http://www.hu.freepascal.org lazarus-stable/universe amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Get:11 http://uk.archive.ubuntu.com vivid-security Release.gpg [933 B]         
Ign http://download.opensuse.org  InRelease                                    
Ign http://www.hu.freepascal.org lazarus-stable/universe i386 Packages/DiffIndex
Hit http://ppa.launchpad.net vivid Release                                     
Get:12 http://mega.nz ./ Packages [1,179 B]                                    
Hit http://ppa.launchpad.net vivid Release                                     
Get:13 http://uk.archive.ubuntu.com vivid-updates Release.gpg [933 B]          
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://linux.dropbox.com vivid Release                                     
Get:14 http://www.hu.freepascal.org lazarus-testing/universe amd64 Packages [5,402 B]
Hit http://uk.archive.ubuntu.com vivid-backports Release.gpg                   
Ign http://mirrors.coreix.net vivid/main Translation-en_GB                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://mirrors.coreix.net vivid/main Translation-en                        
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://mega.nz ./ Translation-en_GB                                        
Get:15 http://www.hu.freepascal.org lazarus-testing/universe i386 Packages [5,742 B]
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://mirrors.coreix.net vivid/main Sources                               
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://dl.google.com stable/main Translation-en                            
Hit http://uk.archive.ubuntu.com vivid Release                                 
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://mirrors.coreix.net vivid/main amd64 Packages                        
Ign http://mega.nz ./ Translation-en                                           
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://mirrors.coreix.net vivid/main i386 Packages                         
Ign http://dl.google.com stable/main Translation-en                            
Get:16 http://uk.archive.ubuntu.com vivid-security Release [63.5 kB]           
Get:17 http://linux.dropbox.com vivid/main amd64 Packages [1,159 B]            
Get:18 http://linux.dropbox.com vivid/main i386 Packages [1,159 B]             
Hit http://www.hu.freepascal.org lazarus-stable/universe amd64 Packages        
Get:19 http://uk.archive.ubuntu.com vivid-updates Release [63.5 kB]            
Hit http://www.hu.freepascal.org lazarus-stable/universe i386 Packages         
Hit http://uk.archive.ubuntu.com vivid-backports Release                       
Ign http://repo.daniil.it lenny/main Translation-en_GB                         
Ign http://repo.daniil.it lenny/main Translation-en                            
Get:20 http://ppa.launchpad.net vivid/main Sources [1,073 B]                   
Ign http://www.hu.freepascal.org lazarus-stable/universe Translation-en_GB     
Ign http://www.hu.freepascal.org lazarus-stable/universe Translation-en        
Ign http://www.hu.freepascal.org lazarus-testing/universe Translation-en_GB    
Ign http://www.hu.freepascal.org lazarus-testing/universe Translation-en       
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Ign http://linux.dropbox.com vivid/main Translation-en_GB                      
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Ign http://linux.dropbox.com vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Get:21 http://uk.archive.ubuntu.com vivid-security/main Sources [36.0 kB]      
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Get:22 http://uk.archive.ubuntu.com vivid-security/restricted Sources [28 B]   
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Get:23 http://uk.archive.ubuntu.com vivid-security/universe Sources [14.6 kB]  
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Get:24 http://uk.archive.ubuntu.com vivid-security/multiverse Sources [1,957 B]
Get:25 http://uk.archive.ubuntu.com vivid-security/main amd64 Packages [99.8 kB]
Get:26 http://uk.archive.ubuntu.com vivid-security/restricted amd64 Packages [28 B]
Get:27 http://uk.archive.ubuntu.com vivid-security/universe amd64 Packages [49.2 kB]
Get:28 http://uk.archive.ubuntu.com vivid-security/multiverse amd64 Packages [3,494 B]
Get:29 http://uk.archive.ubuntu.com vivid-security/main i386 Packages [99.0 kB]
Get:30 http://uk.archive.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:31 http://uk.archive.ubuntu.com vivid-security/universe i386 Packages [49.1 kB]
Get:32 http://uk.archive.ubuntu.com vivid-security/multiverse i386 Packages [3,675 B]
Hit http://uk.archive.ubuntu.com vivid-security/restricted Translation-en      
Get:33 http://uk.archive.ubuntu.com vivid-updates/main Sources [72.5 kB]       
Get:34 http://uk.archive.ubuntu.com vivid-updates/restricted Sources [28 B]    
Get:35 http://uk.archive.ubuntu.com vivid-updates/universe Sources [32.4 kB]   
Get:36 http://uk.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B] 
Get:37 http://uk.archive.ubuntu.com vivid-updates/main amd64 Packages [171 kB] 
Get:38 http://uk.archive.ubuntu.com vivid-updates/restricted amd64 Packages [28 B]
Get:39 http://uk.archive.ubuntu.com vivid-updates/universe amd64 Packages [96.6 kB]
Get:40 http://uk.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3,494 B]
Get:41 http://uk.archive.ubuntu.com vivid-updates/main i386 Packages [169 kB]  
Get:42 http://uk.archive.ubuntu.com vivid-updates/restricted i386 Packages [28 B]
Get:43 http://uk.archive.ubuntu.com vivid-updates/universe i386 Packages [96.3 kB]
Get:44 http://uk.archive.ubuntu.com vivid-updates/multiverse i386 Packages [3,675 B]
Hit http://uk.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://uk.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://uk.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://uk.archive.ubuntu.com vivid-backports/main amd64 Packages           
Hit http://uk.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Hit http://uk.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://uk.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://uk.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://uk.archive.ubuntu.com vivid-backports/restricted Translation-en     
Hit http://uk.archive.ubuntu.com vivid/main Sources                            
Hit http://uk.archive.ubuntu.com vivid/restricted Sources                      
Hit http://uk.archive.ubuntu.com vivid/universe Sources                        
Hit http://uk.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://uk.archive.ubuntu.com vivid/main amd64 Packages                     
Hit http://uk.archive.ubuntu.com vivid/restricted amd64 Packages     
Hit http://uk.archive.ubuntu.com vivid/universe amd64 Packages       
Hit http://uk.archive.ubuntu.com vivid/multiverse amd64 Packages     
Hit http://uk.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://uk.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://uk.archive.ubuntu.com vivid/universe i386 Packages         
Hit http://uk.archive.ubuntu.com vivid/multiverse i386 Packages       
Hit http://uk.archive.ubuntu.com vivid/main Translation-en_GB         
Hit http://uk.archive.ubuntu.com vivid/main Translation-en                     
Hit http://uk.archive.ubuntu.com vivid/multiverse Translation-en_GB            
Hit http://uk.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://uk.archive.ubuntu.com vivid/restricted Translation-en_GB   
Hit http://uk.archive.ubuntu.com vivid/restricted Translation-en      
Hit http://uk.archive.ubuntu.com vivid/universe Translation-en_GB     
Hit http://uk.archive.ubuntu.com vivid/universe Translation-en                 
Hit http://uk.archive.ubuntu.com vivid-security/main Translation-en            
Hit http://uk.archive.ubuntu.com vivid-security/multiverse Translation-en      
Hit http://uk.archive.ubuntu.com vivid-security/universe Translation-en        
Hit http://uk.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://uk.archive.ubuntu.com vivid-updates/multiverse Translation-en    
Hit http://uk.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://uk.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://uk.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://uk.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://uk.archive.ubuntu.com vivid-backports/universe Translation-en       
Err http://deb.paissad.net unstable InRelease                                  
  
Ign http://plex.r.worldssl.net lucid InRelease     
Hit http://repo.steampowered.com precise InRelease
Hit http://deb.torproject.org vivid InRelease                   
Hit http://download.virtualbox.org vivid InRelease                   
Ign http://update.yuuguu.com hardy InRelease                   
Hit http://www.deb-multimedia.org wheezy InRelease
Hit http://shell.ninthgate.se wheezy InRelease                  
Hit http://archive.getdeb.net vivid-getdeb InRelease                
Ign http://archive.getdeb.net vivd-getdeb InRelease
Hit http://downloads-distro.mongodb.org dist Release.gpg       
Hit http://apt.mucommander.com stable/non-free amd64 Packages  
Hit http://apt.mucommander.com stable/contrib amd64 Packages
Hit http://apt.mucommander.com stable/non-free i386 Packages
Hit http://apt.mucommander.com stable/contrib i386 Packages
Hit http://liveusb.info all Release.gpg  
Hit http://download.opensuse.org  Release.gpg
Err http://deb.paissad.net unstable Release.gpg
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Ign http://plex.r.worldssl.net lucid Release.gpg
Get:45 http://repo.steampowered.com precise/steam amd64 Packages [606 B]
Get:46 http://repo.steampowered.com precise/steam i386 Packages [805 B]
Get:47 http://download.virtualbox.org vivid/contrib amd64 Packages [1,541 B]
Get:48 http://download.virtualbox.org vivid/contrib i386 Packages [1,572 B]
Get:49 http://update.yuuguu.com hardy Release.gpg [197 B]                      
Get:50 http://archive.getdeb.net vivid-getdeb/apps amd64 Packages [64.3 kB]    
Get:51 http://archive.getdeb.net vivid-getdeb/apps i386 Packages [65.1 kB]     
Ign http://archive.getdeb.net vivd-getdeb Release.gpg                          
Hit http://downloads-distro.mongodb.org dist Release                           
Hit http://apt.mucommander.com stable/main amd64 Packages                      
Hit http://apt.mucommander.com stable/main i386 Packages                       
Hit http://liveusb.info all Release                                            
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://download.opensuse.org  Release                                      
Ign http://deb.paissad.net unstable Release                                    
Ign http://plex.r.worldssl.net lucid Release                                   
Hit http://deb.torproject.org vivid/main Sources                               
Hit http://deb.torproject.org vivid/main amd64 Packages                        
Hit http://deb.torproject.org vivid/main i386 Packages                         
Hit http://update.yuuguu.com hardy Release                                     
Ign http://update.yuuguu.com hardy Release                                     
Hit http://www.deb-multimedia.org wheezy/main amd64 Packages                   
Hit http://www.deb-multimedia.org wheezy/non-free amd64 Packages               
Hit http://www.deb-multimedia.org wheezy/main i386 Packages                    
Hit http://www.deb-multimedia.org wheezy/non-free i386 Packages                
Hit http://shell.ninthgate.se wheezy/main amd64 Packages                       
Hit http://shell.ninthgate.se wheezy/main i386 Packages                        
Ign http://archive.getdeb.net vivd-getdeb Release                              
Ign http://update.yuuguu.com hardy/multiverse amd64 Packages/DiffIndex         
Ign http://update.yuuguu.com hardy/multiverse i386 Packages/DiffIndex          
Err http://archive.getdeb.net vivd-getdeb/games amd64 Packages                 
  
Err http://archive.getdeb.net vivd-getdeb/games i386 Packages                  
  
Hit http://downloads-distro.mongodb.org dist/10gen amd64 Packages              
Hit http://downloads-distro.mongodb.org dist/10gen i386 Packages               
Hit http://liveusb.info all/main amd64 Packages                                
Hit http://liveusb.info all/main i386 Packages                                 
Hit http://download.opensuse.org  Packages                                     
Err http://archive.getdeb.net vivd-getdeb/games amd64 Packages                 
  
Ign http://apt.mucommander.com stable/contrib Translation-en_GB                
Ign http://apt.mucommander.com stable/contrib Translation-en                   
Ign http://apt.mucommander.com stable/main Translation-en_GB                   
Ign http://apt.mucommander.com stable/main Translation-en                      
Ign http://apt.mucommander.com stable/non-free Translation-en_GB               
Ign http://apt.mucommander.com stable/non-free Translation-en                  
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://deb.torproject.org vivid/main Translation-en_GB                     
Ign http://deb.torproject.org vivid/main Translation-en                        
Ign http://download.virtualbox.org vivid/contrib Translation-en_GB             
Ign http://download.virtualbox.org vivid/contrib Translation-en                
Ign http://www.deb-multimedia.org wheezy/main Translation-en_GB
Ign http://www.deb-multimedia.org wheezy/main Translation-en
Ign http://www.deb-multimedia.org wheezy/non-free Translation-en_GB
Ign http://www.deb-multimedia.org wheezy/non-free Translation-en
Ign http://shell.ninthgate.se wheezy/main Translation-en_GB
Ign http://shell.ninthgate.se wheezy/main Translation-en
Ign http://archive.getdeb.net vivid-getdeb/apps Translation-en_GB
Ign http://archive.getdeb.net vivid-getdeb/apps Translation-en
Err http://archive.getdeb.net vivd-getdeb/games amd64 Packages
  
Err http://archive.getdeb.net vivd-getdeb/games i386 Packages
  
Err http://archive.getdeb.net vivd-getdeb/games amd64 Packages 
  
Err http://archive.getdeb.net vivd-getdeb/games i386 Packages
  
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en_GB
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en
Ign http://liveusb.info all/main Translation-en_GB
Ign http://liveusb.info all/main Translation-en
Ign http://download.opensuse.org  Translation-en_GB
Ign http://download.opensuse.org  Translation-en
Err http://deb.paissad.net unstable/main Sources
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/contrib Sources
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/non-free Sources
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/personal Sources
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/main amd64 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/contrib amd64 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/non-free amd64 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/personal amd64 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/main i386 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/contrib i386 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/non-free i386 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/personal i386 Packages
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/contrib Translation-en_GB
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/contrib Translation-en
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/main Translation-en_GB
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/main Translation-en
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/non-free Translation-en_GB
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/non-free Translation-en
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/personal Translation-en_GB
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://deb.paissad.net unstable/personal Translation-en
  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]
Err http://plex.r.worldssl.net lucid/main amd64 Packages
  404  Not Found [IP: 195.135.221.134 80]
Err http://plex.r.worldssl.net lucid/main i386 Packages
  404  Not Found [IP: 195.135.221.134 80]
Ign http://plex.r.worldssl.net lucid/main Translation-en_GB
Ign http://plex.r.worldssl.net lucid/main Translation-en
Get:52 http://update.yuuguu.com hardy/multiverse amd64 Packages [456 B]
Get:53 http://update.yuuguu.com hardy/multiverse i386 Packages [453 B]
Ign http://update.yuuguu.com hardy/multiverse Translation-en_GB
Ign http://update.yuuguu.com hardy/multiverse Translation-en
Err http://archive.getdeb.net vivd-getdeb/games amd64 Packages                 
  404  Not Found [IP: 195.135.221.134 80]
Err http://archive.getdeb.net vivd-getdeb/games i386 Packages                  
  404  Not Found [IP: 195.135.221.134 80]
Ign http://archive.getdeb.net vivd-getdeb/games Translation-en_GB              
Ign http://archive.getdeb.net vivd-getdeb/games Translation-en                 
Fetched 1,159 kB in 2min 38s (7,303 B/s)                                       
Reading package lists... Done
W: GPG error: http://mirrors.coreix.net vivid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBCB082A1BB943DB
W: GPG error: http://mega.nz ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B258DF0B4D70F67A
W: GPG error: http://www.hu.freepascal.org lazarus-stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 670C48C26A11800F
W: GPG error: http://www.hu.freepascal.org lazarus-testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 670C48C26A11800F
W: GPG error: http://update.yuuguu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 483881FD2506E8CC
W: Failed to fetch http://deb.paissad.net/dists/unstable/InRelease  

W: Failed to fetch http://deb.paissad.net/dists/unstable/Release.gpg  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/main/source/Sources  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/contrib/source/Sources  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/non-free/source/Sources  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/personal/source/Sources  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/main/binary-amd64/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/contrib/binary-amd64/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/non-free/binary-amd64/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/personal/binary-amd64/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/main/binary-i386/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/contrib/binary-i386/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/non-free/binary-i386/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/personal/binary-i386/Packages  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/contrib/i18n/Translation-en_GB  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/contrib/i18n/Translation-en  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/main/i18n/Translation-en_GB  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/main/i18n/Translation-en  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/non-free/i18n/Translation-en_GB  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/non-free/i18n/Translation-en  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/personal/i18n/Translation-en_GB  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://deb.paissad.net/dists/unstable/personal/i18n/Translation-en  Unable to connect to deb.paissad.net:http: [IP: 195.135.221.134 80]

W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-amd64/Packages  404  Not Found [IP: 195.135.221.134 80]

W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-i386/Packages  404  Not Found [IP: 195.135.221.134 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/vivd-getdeb/games/binary-amd64/Packages  404  Not Found [IP: 195.135.221.134 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/vivd-getdeb/games/binary-i386/Packages  404  Not Found [IP: 195.135.221.134 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://linux.dropbox.com/ubuntu/ vivid/main amd64 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_vivid_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://linux.dropbox.com/ubuntu/ vivid/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_vivid_main_binary-i386_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry http://repo.steampowered.com/steam/ precise/steam i386 Packages (/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages)
```


> **Bashing-om said:**
> 
```
sudo apt-get upgrade
```
Not done this as it will remove key apps - the reason for the thread....  Unless there is a way of preventing this.


> **Bashing-om said:**
> 
```
sudo apt-get dist-upgrade
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  libvlc5 libvlccore5
Use 'apt-get autoremove' to remove them.
Done
The following packages will be REMOVED
  gnome-media-player kaffeine kaffeine-dbg libxine2 libxine2-ffmpeg
  libxine2-misc-plugins libxine2-plugins libxine2-x
The following NEW packages will be installed
  libmariadbclient18 mariadb-common
The following packages have been kept back:
  libav-tools
The following packages will be upgraded:
  apport apport-gtk libgdict-common libmysqlclient18 libreoffice-help-it
  libunity-settings-daemon1 libxine2-bin mysql-common python3-apport
  python3-problem-report unity-settings-daemon
11 to upgrade, 2 to newly install, 8 to remove and 1 not to upgrade.
2 not fully installed or removed.
Need to get 5,810 kB/6,393 kB of archives.
After this operation, 13.8 MB disk space will be freed.
```
 I said "NO" as above it would remove key apps.

Did also run this:
```
sudo apt-get  autoremove
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 18 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox (4.3.26-dfsg-2ubuntu2) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.26-dfsg-2ubuntu2); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.

dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



> **Bashing-om said:**
> 
```
sudo apt-get -f install
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 18 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox (4.3.26-dfsg-2ubuntu2) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.26-dfsg-2ubuntu2); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.

dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

> **Bashing-om said:**
> 
```
sudo dpkg -C
```
```
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 virtualbox-qt        x86 virtualization solution - Qt based user interface

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 virtualbox           x86 virtualization solution - base binaries
```


> **Bashing-om said:**
> 
To see the state of the package manager, and what hints there are to make it happy.
Also want to take a look at the source fetch files:
```
cat -n /etc/apt/sources.list
```
```
     1    #------------------------------------------------------------------------------#
     2    #                            OFFICIAL UBUNTU REPOS                             #
     3    #------------------------------------------------------------------------------#
     4    
     5    
     6    ###### Ubuntu Main Repos
     7    deb http://uk.archive.ubuntu.com/ubuntu/ vivid main restricted universe multiverse 
     8    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid main restricted universe multiverse 
     9    
    10    ###### Ubuntu Update Repos
    11    deb http://uk.archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse 
    12    deb http://uk.archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse 
    13    deb http://uk.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse 
    14    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse 
    15    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse 
    16    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse 
    17    
    18    ###### Ubuntu Partner Repo
    19    deb http://archive.canonical.com/ubuntu vivid partner
    20    deb-src http://archive.canonical.com/ubuntu vivid partner
    21    
    22    #------------------------------------------------------------------------------#
    23    #                           UNOFFICIAL UBUNTU REPOS                            #
    24    #------------------------------------------------------------------------------#
    25    
    26    
    27    ###### 3rd Party Binary Repos
    28    
    29    #### Boomaga PPA - https://launchpad.net/~boomaga/+archive/ubuntu/ppa
    30    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6DAEA80
    31    deb http://ppa.launchpad.net/boomaga/ppa/ubuntu vivid main
    32    
    33    #### Clementine PPA - http://www.clementine-player.org/
    34    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
    35    deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu vivid main
    36    
    37    #### Daniil's Bash Video Download - http://daniil.it
    38    ## Run this command: wget -q -O - http://dano.cu.cc/1Aci9Qp | sudo apt-key add - && sudo apt-get update
    39    deb http://repo.daniil.it lenny main
    40    
    41    #### Dropbox PPA - http://dropbox.com
    42    ## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
    43    deb http://linux.dropbox.com/ubuntu/ vivid main
    44    
    45    #### Flacon PPA - http://kde-apps.org/content/show.php?content=113388
    46    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
    47    deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main
    48    
    49    #### GetDeb - http://www.getdeb.net
    50    ## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
    51    deb http://archive.getdeb.net/ubuntu vivid-getdeb apps
    52    
    53    #### Gimp PPA - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
    54    ## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
    55    deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
    56    
    57    #### GNOME3 Extra Apps PPA - https://launchpad.net/~gnome3-team/+archive/gnome3
    58    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
    59    deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main
    60    
    61    #### Google Chrome Browser - http://www.google.com/linuxrepositories/
    62    ## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
    63    deb http://dl.google.com/linux/chrome/deb/ stable main
    64    
    65    #### Google Earth - http://www.google.com/linuxrepositories/
    66    ## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
    67    deb http://dl.google.com/linux/earth/deb/ stable main
    68    
    69    #### Highly Explosive PPA - https://launchpad.net/~dhor/+archive/myway
    70    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93330B78
    71    deb http://ppa.launchpad.net/dhor/myway/ubuntu vivid main
    72    
    73    #### JDownloader PPA - https://launchpad.net/~jd-team
    74    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
    75    deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu vivid main
    76    
    77    #### Kubuntu Backports PPA - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
    78    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
    79    deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu vivid main
    80    
    81    #### Lazarus - http://www.lazarus.freepascal.org/
    82    ## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
    83    deb http://www.hu.freepascal.org/lazarus/ lazarus-stable universe
    84    
    85    #### Lazarus (Testing) - http://www.lazarus.freepascal.org/
    86    ## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
    87    deb http://www.hu.freepascal.org/lazarus/ lazarus-testing universe
    88    
    89    #### LibreOffice PPA - http://www.documentfoundation.org/download/
    90    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
    91    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu vivid main
    92    
    93    #### MariaDB - https://mariadb.org
    94    ## Run this command: apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
    95    deb http://mirrors.coreix.net/mariadb/repo/10.1/ubuntu vivid main
    96    
    97    #### MEGA Sync Client - https://mega.co.nz/
    98    deb http://mega.nz/linux/MEGAsync/xUbuntu_15.04/ ./
    99    
   100    #### Midori PPA - https://launchpad.net/~midori/+archive/ppa
   101    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
   102    deb http://ppa.launchpad.net/midori/ppa/ubuntu vivid main
   103    
   104    #### MongoDB - http://www.mongodb.org/
   105    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
   106    deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
   107    
   108    #### Mozilla Daily Build Team PPA - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
   109    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
   110    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu vivid main
   111    
   112    #### muCommander - http://www.mucommander.com/
   113    ## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
   114    deb http://apt.mucommander.com stable main non-free contrib  
   115    
   116    #### MultiSystem - http://liveusb.info/dotclear/
   117    ## Run this command: wget -q http://liveusb.info/multisystem/depot/multisystem.asc -O- | sudo apt-key add -
   118    deb http://liveusb.info/multisystem/depot all main
   119    
   120    #### Opera - http://www.opera.com/
   121    ## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
   122    deb http://deb.opera.com/opera/ stable non-free
   123    
   124    #### Oracle Java (JDK) Installer PPA - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
   125    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   126    deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main
   127    
   128    #### ownCloud Desktop Client - http://owncloud.org/
   129    ## Run this command: wget -q http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_14.04/Release.key -O- | sudo apt-key add -
   130    deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_15.04/ /
   131    
   132    #### Paissad's PS3 Media Server - http://deb.paissad.net
   133    ## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
   134    deb http://deb.paissad.net unstable main contrib non-free personal
   135    
   136    #### PlayDeb - http://www.playdeb.net/
   137    ## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
   138    deb http://archive.getdeb.net/ubuntu vivd-getdeb games
   139    
   140    #### Plex Media Center - http://www.plexapp.com
   141    ## Run this command: wget -q http://plexapp.com/plex_pub_key.pub -O- | sudo apt-key add -
   142    deb http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo lucid main
   143    
   144    #### SimpleScreenRecorder PPA - http://www.maartenbaert.be/simplescreenrecorder/
   145    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 283EC8CD
   146    deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu vivid main
   147    
   148    #### Steam for Linux - http://store.steampowered.com/about/
   149    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7
   150    deb [arch=i386] http://repo.steampowered.com/steam/ precise steam
   151    
   152    #### Tor: anonymity online - https://www.torproject.org
   153    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89
   154    deb http://deb.torproject.org/torproject.org vivid main
   155    
   156    #### VirtualBox - http://www.virtualbox.org
   157    ## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
   158    deb http://download.virtualbox.org/virtualbox/debian vivid contrib
   159    
   160    #### WebUpd8 Unstable PPA - http://www.webupd8.org/
   161    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   162    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu vivid main
   163    
   164    #### Wine PPA - https://launchpad.net/~ubuntu-wine/+archive/ppa/
   165    ## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
   166    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main
   167    
   168    #### Xorg Edgers PPA - https://launchpad.net/~xorg-edgers
   169    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
   170    deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu vivid main
   171    
   172    #### Yuuguu - http://yuuguu.com
   173    deb http://update.yuuguu.com/repositories/apt hardy multiverse
   174    
   175    
   176    ####### 3rd Party Source Repos
   177    
   178    #### Boomaga PPA (Source) - https://launchpad.net/~boomaga/+archive/ubuntu/ppa
   179    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6DAEA80
   180    deb-src http://ppa.launchpad.net/boomaga/ppa/ubuntu vivid main
   181    
   182    #### Clementine PPA (Source) - http://www.clementine-player.org/
   183    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
   184    deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu vivid main
   185    
   186    #### Flacon PPA (Source) - http://kde-apps.org/content/show.php?content=113388
   187    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
   188    deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main
   189    
   190    #### Gimp PPA (Source) - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
   191    ## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
   192    deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
   193    
   194    #### GNOME3 Extra Apps PPA (Source) - https://launchpad.net/~gnome3-team/+archive/gnome3
   195    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
   196    deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main
   197    
   198    #### Highly Explosive PPA (Source) - https://launchpad.net/~dhor/+archive/myway
   199    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93330B78
   200    deb-src http://ppa.launchpad.net/dhor/myway/ubuntu vivid main 
   201    
   202    #### JDownloader PPA (Source) - https://launchpad.net/~jd-team
   203    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
   204    deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu vivid main
   205    
   206    #### Kubuntu Backports PPA (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
   207    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
   208    deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu vivid main
   209    
   210    #### LibreOffice PPA (Source) - http://www.documentfoundation.org/download/
   211    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
   212    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu vivid main
   213    
   214    #### MariaDB (Source) - https://mariadb.org
   215    ## Run this command: apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
   216    deb-src http://mirrors.coreix.net/mariadb/repo/10.1/ubuntu vivid main
   217    
   218    #### Midori PPA (Source) - https://launchpad.net/~midori/+archive/ppa
   219    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
   220    deb-src http://ppa.launchpad.net/midori/ppa/ubuntu vivid main
   221    
   222    #### Mozilla Daily Build Team PPA (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
   223    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
   224    deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu vivid main
   225    
   226    #### Oracle Java (JDK) Installer PPA (Source) - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
   227    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   228    deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main
   229    
   230    #### Paissad's PS3 Media Server (Source) - http://deb.paissad.net
   231    ## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
   232    deb-src http://deb.paissad.net unstable main contrib non-free personal
   233    
   234    #### SimpleScreenRecorder PPA (Source) - http://www.maartenbaert.be/simplescreenrecorder/
   235    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 283EC8CD
   236    deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu vivid main
   237    
   238    #### Tor: anonymity online (Source) - https://www.torproject.org
   239    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89
   240    deb-src http://deb.torproject.org/torproject.org vivid main
   241    
   242    #### WebUpd8 Unstable PPA (Source) - http://www.webupd8.org/
   243    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   244    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu vivid main
   245    
   246    #### Wine PPA (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
   247    ## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
   248    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main
   249    
   250    #### Xorg Edgers PPA (Source) - https://launchpad.net/~xorg-edgers
   251    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
   252    deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu vivid main
   253    
   254    
   255    
```


This is the origional....
[HTML]# deb cdrom:[Xubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422.1)]/ vivid main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main multiverse restricted universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main multiverse restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://security.ubuntu.com/ubuntu vivid-security main multiverse restricted universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu vivid-security universe
deb http://security.ubuntu.com/ubuntu vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu vivid partner
deb-src http://archive.canonical.com/ubuntu vivid partner
deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main
deb http://ppa.launchpad.net/plexapp/plexht/ubuntu vivid main
deb-src http://ppa.launchpad.net/plexapp/plexht/ubuntu vivid main[/HTML]

> **Bashing-om said:**
> 
```
tail -v -n +1 /etc/apt/sources.list.d/*
```
[HTML]==> /etc/apt/sources.list.d/deb-multimedia.list <==
deb http://www.deb-multimedia.org wheezy main non-free

==> /etc/apt/sources.list.d/deb-multimedia.list.save <==
deb http://www.deb-multimedia.org wheezy main non-free

==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu vivid main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu vivid main

==> /etc/apt/sources.list.d/ehoover-ubuntu-compholio-vivid.list <==
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main

==> /etc/apt/sources.list.d/ehoover-ubuntu-compholio-vivid.list.save <==
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main

==> /etc/apt/sources.list.d/glennric-ubuntu-dolphin-emu-vivid.list <==
deb http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main
deb-src http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main

==> /etc/apt/sources.list.d/glennric-ubuntu-dolphin-emu-vivid.list.save <==
deb http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main
deb-src http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list.save <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/plex.list <==
deb http://shell.ninthgate.se/packages/debian wheezy main

==> /etc/apt/sources.list.d/plex.list.save <==
deb http://shell.ninthgate.se/packages/debian wheezy main

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

[/HTML]

---

### Post by Jonners59 on 2015-08-07
removed the duplicates.......

---

### Post by oldfred on 2015-08-07
Not sure where you are at, but errors from sources that were not vivid. And some of source lists or errors showed hardy, lucid, trusty, wheezy?
You need to remove or comment out any sources that do not have vivid, do not just change as they may not have vivid and will throw errors.

You do have a lot of ppa and external sources.

---

### Post by Jonners59 on 2015-08-07
> **oldfred said:**
> Not sure where you are at, but errors from sources that were not vivid. And some of source lists or errors showed hardy, lucid, trusty, wheezy?
You need to remove or comment out any sources that do not have vivid, do not just change as they may not have vivid and will throw errors.

You do have a lot of ppa and external sources.

The list was generated via the official sources list generator, as per link.  I kept my original too, as per below, and relabelled it *.bak...  I will make the changes suggested, but does not solve the upgrade deleting wanted apps such as kaffeine and the inability to install the ones I want, such as vlc...

---

### Post by Jonners59 on 2015-08-07
OK, done some tidying up, but apps like Libra not working.  Say not installed properly, and still getting errors...  So, what next????

```
sudo apt-get update
```

```
Ign http://ppa.launchpad.net vivid InRelease
Ign http://archive.canonical.com vivid InRelease                               
Ign http://mega.nz ./ InRelease                                                
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid Release.gpg                             
Hit http://deb.opera.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Ign http://liveusb.info all InRelease                                          
Hit http://apt.mucommander.com stable InRelease                                
Hit http://repo.daniil.it lenny InRelease                                      
Hit http://archive.canonical.com vivid Release                                 
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://liveusb.info all Release.gpg                                        
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://dl.google.com stable InRelease                                      
Get:1 http://repo.daniil.it lenny/main amd64 Packages [1,113 B]                
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://uk.archive.ubuntu.com vivid InRelease                               
Hit http://liveusb.info all Release                                            
Get:2 http://mega.nz ./ Release.gpg [189 B]                                    
Get:3 http://repo.daniil.it lenny/main i386 Packages [1,113 B]                 
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://dl.google.com stable Release.gpg                                    
Ign http://uk.archive.ubuntu.com vivid-security InRelease                      
Hit http://apt.mucommander.com stable/non-free amd64 Packages                  
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://uk.archive.ubuntu.com vivid-updates InRelease                       
Get:4 http://mega.nz ./ Release [967 B]                                        
Ign http://mega.nz ./ Release                                                  
Hit http://apt.mucommander.com stable/contrib amd64 Packages                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://dl.google.com stable Release.gpg                                    
Ign http://uk.archive.ubuntu.com vivid-backports InRelease                     
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid/partner Sources                         
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://mega.nz ./ Packages/DiffIndex                                       
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Hit http://uk.archive.ubuntu.com vivid Release.gpg                             
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://apt.mucommander.com stable/non-free i386 Packages                   
Hit http://archive.canonical.com vivid/partner i386 Packages                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:5 http://uk.archive.ubuntu.com vivid-security Release.gpg [933 B]          
Ign http://downloads-distro.mongodb.org dist InRelease                         
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://apt.mucommander.com stable/contrib i386 Packages                    
Get:6 http://uk.archive.ubuntu.com vivid-updates Release.gpg [933 B]           
Hit http://liveusb.info all/main amd64 Packages                                
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://archive.canonical.com vivid/partner Translation-en                  
Hit http://uk.archive.ubuntu.com vivid-backports Release.gpg                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://dl.google.com stable Release                                        
Hit http://liveusb.info all/main i386 Packages                                 
Ign http://repo.daniil.it lenny/main Translation-en_GB                         
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://uk.archive.ubuntu.com vivid Release                                 
Ign http://repo.daniil.it lenny/main Translation-en                            
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:7 http://uk.archive.ubuntu.com vivid-security Release [63.5 kB]            
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:8 http://dl.google.com stable/main amd64 Packages [469 B]                  
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:9 http://uk.archive.ubuntu.com vivid-updates Release [63.5 kB]             
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:10 http://dl.google.com stable/main i386 Packages [464 B]                  
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://apt.mucommander.com stable/main amd64 Packages                      
Hit http://downloads-distro.mongodb.org dist Release.gpg                       
Hit http://uk.archive.ubuntu.com vivid-backports Release                       
Hit http://apt.mucommander.com stable/main i386 Packages                       
Ign http://liveusb.info all/main Translation-en_GB                             
Ign http://liveusb.info all/main Translation-en                                
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://downloads-distro.mongodb.org dist Release                           
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://download.opensuse.org  InRelease                                    
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://apt.mucommander.com stable/contrib Translation-en_GB                
Hit http://deb.torproject.org vivid InRelease                                  
Get:11 http://mega.nz ./ Packages [1,179 B]                                    
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://apt.mucommander.com stable/contrib Translation-en                   
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://mega.nz ./ Translation-en_GB                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://apt.mucommander.com stable/main Translation-en_GB                   
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://apt.mucommander.com stable/main Translation-en                      
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://download.virtualbox.org vivid InRelease                             
Ign http://apt.mucommander.com stable/non-free Translation-en_GB               
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://mega.nz ./ Translation-en                                           
Hit http://ppa.launchpad.net vivid Release                                     
Ign http://apt.mucommander.com stable/non-free Translation-en                  
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://dl.google.com stable/main i386 Packages                             
Get:12 http://uk.archive.ubuntu.com vivid-security/main Sources [36.0 kB]      
Get:13 http://uk.archive.ubuntu.com vivid-security/restricted Sources [28 B]   
Get:14 http://uk.archive.ubuntu.com vivid-security/universe Sources [14.6 kB]  
Get:15 http://uk.archive.ubuntu.com vivid-security/multiverse Sources [1,957 B]
Get:16 http://uk.archive.ubuntu.com vivid-security/main amd64 Packages [99.8 kB]
Ign http://linux.dropbox.com vivid InRelease                                   
Get:17 http://uk.archive.ubuntu.com vivid-security/restricted amd64 Packages [28 B]
Get:18 http://uk.archive.ubuntu.com vivid-security/universe amd64 Packages [49.2 kB]
Ign http://dl.google.com stable/main Translation-en_GB                         
Get:19 http://uk.archive.ubuntu.com vivid-security/multiverse amd64 Packages [3,494 B]
Ign http://dl.google.com stable/main Translation-en                            
Get:20 http://uk.archive.ubuntu.com vivid-security/main i386 Packages [98.9 kB]
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://downloads-distro.mongodb.org dist/10gen amd64 Packages              
Ign http://dl.google.com stable/main Translation-en                            
Get:21 http://uk.archive.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:22 http://uk.archive.ubuntu.com vivid-security/universe i386 Packages [49.2 kB]
Get:23 http://uk.archive.ubuntu.com vivid-security/multiverse i386 Packages [3,675 B]
Hit http://uk.archive.ubuntu.com vivid-security/restricted Translation-en      
Hit http://downloads-distro.mongodb.org dist/10gen i386 Packages               
Get:24 http://uk.archive.ubuntu.com vivid-updates/main Sources [72.5 kB]       
Get:25 http://uk.archive.ubuntu.com vivid-updates/restricted Sources [28 B]    
Get:26 http://uk.archive.ubuntu.com vivid-updates/universe Sources [32.4 kB]   
Get:27 http://uk.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B] 
Get:28 http://uk.archive.ubuntu.com vivid-updates/main amd64 Packages [171 kB] 
Get:29 http://uk.archive.ubuntu.com vivid-updates/restricted amd64 Packages [28 B]
Get:30 http://uk.archive.ubuntu.com vivid-updates/universe amd64 Packages [96.3 kB]
Hit http://download.opensuse.org  Release.gpg                                  
Get:31 http://uk.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3,494 B]
Get:32 http://uk.archive.ubuntu.com vivid-updates/main i386 Packages [169 kB]  
Get:33 http://uk.archive.ubuntu.com vivid-updates/restricted i386 Packages [28 B]
Get:34 http://uk.archive.ubuntu.com vivid-updates/universe i386 Packages [96.3 kB]
Ign http://archive.getdeb.net vivd-getdeb InRelease                            
Get:35 http://uk.archive.ubuntu.com vivid-updates/multiverse i386 Packages [3,675 B]
Hit http://uk.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://uk.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://uk.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://uk.archive.ubuntu.com vivid-backports/main amd64 Packages           
Hit http://uk.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Hit http://uk.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://uk.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Get:36 http://download.virtualbox.org vivid/contrib amd64 Packages [1,541 B]   
Hit http://uk.archive.ubuntu.com vivid-backports/main Translation-en           
Get:37 http://download.virtualbox.org vivid/contrib i386 Packages [1,572 B]    
Hit http://uk.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://uk.archive.ubuntu.com vivid-backports/restricted Translation-en     
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://uk.archive.ubuntu.com vivid/main Sources                            
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://uk.archive.ubuntu.com vivid/restricted Sources                      
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://uk.archive.ubuntu.com vivid/universe Sources                        
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://uk.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://uk.archive.ubuntu.com vivid/main amd64 Packages                     
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://uk.archive.ubuntu.com vivid/restricted amd64 Packages               
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://uk.archive.ubuntu.com vivid/universe amd64 Packages                 
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://uk.archive.ubuntu.com vivid/multiverse amd64 Packages               
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en_GB           
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://uk.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://uk.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://uk.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://uk.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://uk.archive.ubuntu.com vivid/main Translation-en_GB                  
Hit http://uk.archive.ubuntu.com vivid/main Translation-en                     
Hit http://uk.archive.ubuntu.com vivid/multiverse Translation-en_GB            
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en              
Hit http://uk.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://uk.archive.ubuntu.com vivid/restricted Translation-en_GB            
Hit http://uk.archive.ubuntu.com vivid/restricted Translation-en  
Hit http://uk.archive.ubuntu.com vivid/universe Translation-en_GB              
Hit http://uk.archive.ubuntu.com vivid/universe Translation-en                 
Hit http://uk.archive.ubuntu.com vivid-security/main Translation-en            
Hit http://uk.archive.ubuntu.com vivid-security/multiverse Translation-en      
Hit http://uk.archive.ubuntu.com vivid-security/universe Translation-en
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://uk.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://ppa.launchpad.net vivid/main amd64 Packages              
Hit http://uk.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://uk.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://uk.archive.ubuntu.com vivid-backports/universe Sources
Hit http://ppa.launchpad.net vivid/main Sources                
Hit http://uk.archive.ubuntu.com vivid-backports/universe amd64 Packages
Hit http://ppa.launchpad.net vivid/main amd64 Packages         
Hit http://ppa.launchpad.net vivid/main i386 Packages              
Hit http://uk.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://uk.archive.ubuntu.com vivid-backports/universe Translation-en       
Hit http://ppa.launchpad.net vivid/main Sources                                
Hit http://ppa.launchpad.net vivid/main amd64 Packages             
Hit http://ppa.launchpad.net vivid/main i386 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages             
Hit http://ppa.launchpad.net vivid/main i386 Packages              
Hit http://ppa.launchpad.net vivid/main Translation-en             
Hit http://ppa.launchpad.net vivid/main Sources                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main i386 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en             
Hit http://ppa.launchpad.net vivid/main Sources                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main i386 Packages              
Hit http://ppa.launchpad.net vivid/main Translation-en             
Hit http://ppa.launchpad.net vivid/main Sources                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages             
Hit http://ppa.launchpad.net vivid/main i386 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages         
Hit http://ppa.launchpad.net vivid/main i386 Packages                
Hit http://ppa.launchpad.net vivid/main Translation-en         
Hit http://ppa.launchpad.net vivid/main Sources                     
Hit http://ppa.launchpad.net vivid/main amd64 Packages              
Hit http://ppa.launchpad.net vivid/main i386 Packages          
Hit http://ppa.launchpad.net vivid/main Translation-en         
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main i386 Packages              
Hit http://ppa.launchpad.net vivid/main Translation-en             
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main i386 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main i386 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://ppa.launchpad.net vivid/main Sources
Hit http://ppa.launchpad.net vivid/main amd64 Packages
Hit http://ppa.launchpad.net vivid/main i386 Packages
Hit http://ppa.launchpad.net vivid/main Translation-en
Hit http://linux.dropbox.com vivid Release.gpg                                 
Hit http://download.opensuse.org  Release                                      
Hit http://deb.torproject.org vivid/main Sources                               
Hit http://deb.torproject.org vivid/main amd64 Packages                        
Hit http://deb.torproject.org vivid/main i386 Packages                         
Hit http://linux.dropbox.com vivid Release                                     
Ign http://archive.getdeb.net vivd-getdeb Release.gpg                          
Get:38 http://linux.dropbox.com vivid/main amd64 Packages [1,159 B]            
Get:39 http://linux.dropbox.com vivid/main i386 Packages [1,159 B]             
Hit http://download.opensuse.org  Packages                                     
Ign http://archive.getdeb.net vivd-getdeb Release                              
Ign http://deb.torproject.org vivid/main Translation-en_GB                     
Ign http://deb.torproject.org vivid/main Translation-en                        
Ign http://download.virtualbox.org vivid/contrib Translation-en_GB             
Ign http://download.virtualbox.org vivid/contrib Translation-en                
Ign http://download.opensuse.org  Translation-en_GB                            
Ign http://download.opensuse.org  Translation-en                               
Ign http://linux.dropbox.com vivid/main Translation-en_GB                      
Ign http://linux.dropbox.com vivid/main Translation-en                         
Err http://archive.getdeb.net vivd-getdeb/games amd64 Packages                 
  404  Not Found [IP: 108.160.172.206 80]
Err http://archive.getdeb.net vivd-getdeb/games i386 Packages
  404  Not Found [IP: 108.160.172.206 80]
Ign http://archive.getdeb.net vivd-getdeb/games Translation-en_GB
Ign http://archive.getdeb.net vivd-getdeb/games Translation-en
Fetched 1,142 kB in 32s (34.6 kB/s)
W: GPG error: http://mega.nz ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B258DF0B4D70F67A
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/vivd-getdeb/games/binary-amd64/Packages  404  Not Found [IP: 108.160.172.206 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/vivd-getdeb/games/binary-i386/Packages  404  Not Found [IP: 108.160.172.206 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

```
sudo apt-get upgrade
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.26-dfsg-2ubuntu2) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.26-dfsg-2ubuntu2); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.

dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
sudo apt-get dist-upgrade
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.26-dfsg-2ubuntu2) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.26-dfsg-2ubuntu2); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.

dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
sudo apt-get -f install
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox (4.3.26-dfsg-2ubuntu2) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.26-dfsg-2ubuntu2); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.

dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
sudo dpkg -C
```

```
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 virtualbox-qt        x86 virtualization solution - Qt based user interface

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 virtualbox           x86 virtualization solution - base binaries
```

```
cat -n /etc/apt/sources.list
```
```
     1    #------------------------------------------------------------------------------#
     2    #                            OFFICIAL UBUNTU REPOS                             #
     3    #------------------------------------------------------------------------------#
     4    
     5    
     6    ###### Ubuntu Main Repos
     7    deb http://uk.archive.ubuntu.com/ubuntu/ vivid main restricted universe multiverse
     8    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid main restricted universe multiverse
     9    
    10    ###### Ubuntu Update Repos
    11    deb http://uk.archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse
    12    deb http://uk.archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
    13    deb http://uk.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    14    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse
    15    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
    16    deb-src http://uk.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    17    
    18    ###### Ubuntu Partner Repo
    19    deb http://archive.canonical.com/ubuntu vivid partner
    20    deb-src http://archive.canonical.com/ubuntu vivid partner
    21    
    22    #------------------------------------------------------------------------------#
    23    #                           UNOFFICIAL UBUNTU REPOS                            #
    24    #------------------------------------------------------------------------------#
    25    
    26    
    27    ###### 3rd Party Binary Repos
    28    
    29    #### Boomaga PPA - https://launchpad.net/~boomaga/+archive/ubuntu/ppa
    30    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6DAEA80
    31    deb http://ppa.launchpad.net/boomaga/ppa/ubuntu vivid main
    32    
    33    #### Clementine PPA - http://www.clementine-player.org/
    34    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
    35    deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu vivid main
    36    
    37    #### Daniil's Bash Video Download - http://daniil.it
    38    ## Run this command: wget -q -O - http://dano.cu.cc/1Aci9Qp | sudo apt-key add - && sudo apt-get update
    39    deb http://repo.daniil.it lenny main
    40    
    41    #### Dropbox PPA - http://dropbox.com
    42    ## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
    43    ## deb http://linux.dropbox.com/ubuntu/ vivid main
    44    
    45    #### Flacon PPA - http://kde-apps.org/content/show.php?content=113388
    46    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
    47    deb http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main
    48    
    49    #### GetDeb - http://www.getdeb.net
    50    ## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
    51    
    52    #### Gimp PPA - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
    53    ## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
    54    deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
    55    
    56    #### GNOME3 Extra Apps PPA - https://launchpad.net/~gnome3-team/+archive/gnome3
    57    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
    58    deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main
    59    
    60    #### Google Chrome Browser - http://www.google.com/linuxrepositories/
    61    ## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
    62    ## deb http://dl.google.com/linux/chrome/deb/ stable main
    63    
    64    #### Google Earth - http://www.google.com/linuxrepositories/
    65    ## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
    66    deb http://dl.google.com/linux/earth/deb/ stable main
    67    
    68    #### Highly Explosive PPA - https://launchpad.net/~dhor/+archive/myway
    69    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93330B78
    70    deb http://ppa.launchpad.net/dhor/myway/ubuntu vivid main
    71    
    72    #### JDownloader PPA - https://launchpad.net/~jd-team
    73    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
    74    deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu vivid main
    75    
    76    #### Kubuntu Backports PPA - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports[CODE]
    77    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
    78    deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu vivid main
    79    
    80    #### Lazarus - http://www.lazarus.freepascal.org/
    81    ## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
    82    
    83    #### Lazarus (Testing) - http://www.lazarus.freepascal.org/
    84    ## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
    85    
    86    #### LibreOffice PPA - http://www.documentfoundation.org/download/
    87    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
    88    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu vivid main
    89    
    90    #### MariaDB - https://mariadb.org
    91    ## Run this command: apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
    92    
    93    #### MEGA Sync Client - https://mega.co.nz/[CODE]
    94    deb http://mega.nz/linux/MEGAsync/xUbuntu_15.04/ ./
    95    
    96    #### Midori PPA - https://launchpad.net/~midori/+archive/ppa
    97    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
    98    deb http://ppa.launchpad.net/midori/ppa/ubuntu vivid main
    99    
   100    #### MongoDB - http://www.mongodb.org/
   101    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
   102    deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
   103    
   104    #### Mozilla Daily Build Team PPA - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
   105    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
   106    deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu vivid main
   107    
   108    #### muCommander - http://www.mucommander.com/
   109    ## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
   110    deb http://apt.mucommander.com stable main non-free contrib
   111    
   112    #### MultiSystem - http://liveusb.info/dotclear/
   113    ## Run this command: wget -q http://liveusb.info/multisystem/depot/multisystem.asc -O- | sudo apt-key add -
   114    deb http://liveusb.info/multisystem/depot all main
   115    
   116    #### Opera - http://www.opera.com/
   117    ## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
   118    deb http://deb.opera.com/opera/ stable non-free
   119    
   120    #### Oracle Java (JDK) Installer PPA - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
   121    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   122    deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main
   123    
   124    #### ownCloud Desktop Client - http://owncloud.org/
   125    ## Run this command: wget -q http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_14.04/Release.key -O- | sudo apt-key add -
   126    deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_15.04/ /
   127    
   128    #### Paissad's PS3 Media Server - http://deb.paissad.net
   129    ## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
   130    
   131    #### PlayDeb - http://www.playdeb.net/
   132    ## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
   133    deb http://archive.getdeb.net/ubuntu vivd-getdeb games
   134    
   135    #### Plex Media Center - http://www.plexapp.com
   136    ## Run this command: wget -q http://plexapp.com/plex_pub_key.pub -O- | sudo apt-key add -
   137    
   138    #### SimpleScreenRecorder PPA - http://www.maartenbaert.be/simplescreenrecorder/
   139    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 283EC8CD
   140    deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu vivid main
   141    
   142    #### Steam for Linux - http://store.steampowered.com/about/
   143    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7
   144    ## deb [arch=i386] http://repo.steampowered.com/steam/ precise steam
   145    
   146    #### Tor: anonymity online - https://www.torproject.org
   147    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89
   148    deb http://deb.torproject.org/torproject.org vivid main
   149    
   150    #### VirtualBox - http://www.virtualbox.org
   151    ## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
   152    deb http://download.virtualbox.org/virtualbox/debian vivid contrib
   153    
   154    #### WebUpd8 Unstable PPA - http://www.webupd8.org/
   155    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   156    deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu vivid main
   157    
   158    #### Wine PPA - https://launchpad.net/~ubuntu-wine/+archive/ppa/
   159    ## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
   160    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main
   161    
   162    #### Xorg Edgers PPA - https://launchpad.net/~xorg-edgers
   163    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
   164    deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu vivid main
   165    
   166    #### Yuuguu - http://yuuguu.com
   167    
   168    
   169    ####### 3rd Party Source Repos
   170    
   171    #### Boomaga PPA (Source) - https://launchpad.net/~boomaga/+archive/ubuntu/ppa
   172    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6DAEA80
   173    deb-src http://ppa.launchpad.net/boomaga/ppa/ubuntu vivid main
   174    
   175    #### Clementine PPA (Source) - http://www.clementine-player.org/
   176    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
   177    deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu vivid main
   178    
   179    #### Flacon PPA (Source) - http://kde-apps.org/content/show.php?content=113388
   180    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
   181    deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu vivid main
   182    
   183    #### Gimp PPA (Source) - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
   184    ## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
   185    deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main
   186    
   187    #### GNOME3 Extra Apps PPA (Source) - https://launchpad.net/~gnome3-team/+archive/gnome3
   188    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
   189    deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main
   190    
   191    #### Highly Explosive PPA (Source) - https://launchpad.net/~dhor/+archive/myway
   192    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93330B78
   193    deb-src http://ppa.launchpad.net/dhor/myway/ubuntu vivid main
   194    
   195    #### JDownloader PPA (Source) - https://launchpad.net/~jd-team
   196    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
   197    deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu vivid main
   198    
   199    #### Kubuntu Backports PPA (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
   200    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
   201    deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu vivid main
   202    
   203    #### LibreOffice PPA (Source) - http://www.documentfoundation.org/download/
   204    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
   205    deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu vivid main
   206    
   207    #### MariaDB (Source) - https://mariadb.org
   208    ## Run this command: apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
   209    
   210    #### Midori PPA (Source) - https://launchpad.net/~midori/+archive/ppa
   211    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
   212    deb-src http://ppa.launchpad.net/midori/ppa/ubuntu vivid main
   213    
   214    #### Mozilla Daily Build Team PPA (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
   215    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
   216    deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu vivid main
   217    
   218    #### Oracle Java (JDK) Installer PPA (Source) - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
   219    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   220    deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main
   221    
   222    #### Paissad's PS3 Media Server (Source) - http://deb.paissad.net
   223    ## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
   224    
   225    #### SimpleScreenRecorder PPA (Source) - http://www.maartenbaert.be/simplescreenrecorder/
   226    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 283EC8CD
   227    deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu vivid main
   228    
   229    #### Tor: anonymity online (Source) - https://www.torproject.org
   230    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89
   231    deb-src http://deb.torproject.org/torproject.org vivid main
   232    
   233    #### WebUpd8 Unstable PPA (Source) - http://www.webupd8.org/
   234    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
   235    deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu vivid main
   236    
   237    #### Wine PPA (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
   238    ## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
   239    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu vivid main
   240    
   241    #### Xorg Edgers PPA (Source) - https://launchpad.net/~xorg-edgers
   242    ## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
   243    deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu vivid main
   244    
   245    
   246    
```

```

tail -v -n +1 /etc/apt/sources.list.d/*
```

```
==> /etc/apt/sources.list.d/deb-multimedia.list <==

==> /etc/apt/sources.list.d/deb-multimedia.list.save <==

==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu vivid main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu vivid main

==> /etc/apt/sources.list.d/ehoover-ubuntu-compholio-vivid.list <==
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main

==> /etc/apt/sources.list.d/ehoover-ubuntu-compholio-vivid.list.save <==
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main

==> /etc/apt/sources.list.d/glennric-ubuntu-dolphin-emu-vivid.list <==
deb http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main
deb-src http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main

==> /etc/apt/sources.list.d/glennric-ubuntu-dolphin-emu-vivid.list.save <==
deb http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main
deb-src http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list.save <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/plex.list <==

==> /etc/apt/sources.list.d/plex.list.save <==

==> /etc/apt/sources.list.d/steam.list <==

==> /etc/apt/sources.list.d/steam.list.save <==
```

---

### Post by oldfred on 2015-08-07
TMI, This may be all that is important, unless others also.

Err [http://archive.getdeb.net](http://archive.getdeb.net) vivd-getdeb/games amd64 Packages                 
  404  Not Found [IP: 108.160.172.206 80]

You need to remove getdeb.net also.

---

### Post by Bashing-om on 2015-08-07
Jonners59; Yuk;

All those PPAs, and mixing distributions ( lenney as well as others) Will lead to the package manager being in a corrupted state !


There is a limit to how many PPAs the system supports, have you reached this limit ?
```

ls /etc/apt/trusted.gpg.d | wc -l

```
You must go through the PPAs and ppa-purge/remove those that are not valid for 'vivid' and not supported in 'vivid. Several of the PPAs have seen no activity for an extended period of time. I would question that these old PPAs are compatible with 15.04's init system, systemd.

Our goal is to get the package manager in a happy state.

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-08-07
> **oldfred said:**
> TMI, This may be all that is important, unless others also.

Err [http://archive.getdeb.net](http://archive.getdeb.net) vivd-getdeb/games amd64 Packages                 
  404  Not Found [IP: 108.160.172.206 80]

You need to remove getdeb.net also.

Thanks oldfred

Did that but still won't work

---

### Post by oldfred on 2015-08-07
You might want to comment out all ppa, then add each back until you find problem. 
Are you getting any other errors?

---

### Post by Jonners59 on 2015-08-08
Thanks oldfred and Basing-om
This is the list created by the official sources build site, not my original, which also didn't work....  I don't know which to delete or how to identify what is "out of date"
```
ls /etc/apt/trusted.gpg.d | wc -l
9
```

I'll try blanking out all and adding one at a time...  I turned off all, made no difference.
Below an attempt to install vlc

 ```
vlc-data (=2.2.0-1) but 1:2.0.6-dmo3 is to be installed
```

```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

and it removes gnome-mediaplayer

Attempt to reinstall virtualbox

```
sudo apt-get install virtualbox
[sudo] password for mediaserver: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  vde2 virtualbox-guest-additions-iso
Recommended packages:
  virtualbox-dkms virtualbox-source virtualbox-qt
The following NEW packages will be installed
  virtualbox
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 15.9 MB of archives.
After this operation, 63.2 MB of additional disk space will be used.
Get:1 http://uk.archive.ubuntu.com/ubuntu/ vivid-security/multiverse virtualbox amd64 4.3.26-dfsg-2ubuntu2 [15.9 MB]
Fetched 15.9 MB in 15s (1,017 kB/s)                                            
Selecting previously unselected package virtualbox.
(Reading database ... 554914 files and directories currently installed.)
Preparing to unpack .../virtualbox_4.3.26-dfsg-2ubuntu2_amd64.deb ...
Unpacking virtualbox (4.3.26-dfsg-2ubuntu2) ...
Processing triggers for systemd (219-7ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up virtualbox (4.3.26-dfsg-2ubuntu2) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for systemd (219-7ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 virtualbox
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Jonners59 on 2015-08-08
I put the origional sources list back and unchecked all bar the security and base...  Same problems

```
 ls /etc/apt/trusted.gpg.d | wc -l
```
```
9
```

```
sudo apt-get upgrade
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

```
sudo apt-get update
```
```
Ign http://archive.canonical.com vivid InRelease
Hit http://archive.canonical.com vivid Release.gpg                             
Hit http://archive.canonical.com vivid Release                                 
Hit http://archive.canonical.com vivid/partner Sources                         
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Hit http://archive.canonical.com vivid/partner i386 Packages                   
Ign http://gb.archive.ubuntu.com vivid InRelease                               
Ign http://gb.archive.ubuntu.com vivid-updates InRelease                       
Ign http://gb.archive.ubuntu.com vivid-backports InRelease            
Ign http://archive.canonical.com vivid/partner Translation-en         
Hit http://gb.archive.ubuntu.com vivid Release.gpg                    
Hit http://gb.archive.ubuntu.com vivid-updates Release.gpg            
Hit http://gb.archive.ubuntu.com vivid-backports Release.gpg
Ign http://security.ubuntu.com vivid-security InRelease
Ign http://us.archive.ubuntu.com lucid-security InRelease
Hit http://gb.archive.ubuntu.com vivid Release  
Hit http://gb.archive.ubuntu.com vivid-updates Release                         
Hit http://gb.archive.ubuntu.com vivid-backports Release                       
Hit http://gb.archive.ubuntu.com vivid/main Sources                            
Hit http://gb.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://gb.archive.ubuntu.com vivid/restricted Sources                      
Get:1 http://security.ubuntu.com vivid-security Release.gpg [933 B]
Hit http://gb.archive.ubuntu.com vivid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid-security Release.gpg        
Hit http://gb.archive.ubuntu.com vivid/main amd64 Packages         
Hit http://gb.archive.ubuntu.com vivid/restricted amd64 Packages   
Hit http://gb.archive.ubuntu.com vivid/universe amd64 Packages     
Hit http://gb.archive.ubuntu.com vivid/multiverse amd64 Packages               
Hit http://gb.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://gb.archive.ubuntu.com vivid/restricted i386 Packages                
Get:2 http://security.ubuntu.com vivid-security Release [63.5 kB] 
Hit http://us.archive.ubuntu.com lucid-security Release                        
Hit http://gb.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://gb.archive.ubuntu.com vivid/multiverse i386 Packages            
Hit http://us.archive.ubuntu.com lucid-security/main Sources               
Hit http://gb.archive.ubuntu.com vivid/main Translation-en_GB              
Hit http://gb.archive.ubuntu.com vivid/main Translation-en                 
Hit http://gb.archive.ubuntu.com vivid/multiverse Translation-en_GB        
Hit http://gb.archive.ubuntu.com vivid/multiverse Translation-en           
Hit http://gb.archive.ubuntu.com vivid/restricted Translation-en_GB        
Hit http://gb.archive.ubuntu.com vivid/restricted Translation-en           
Hit http://us.archive.ubuntu.com lucid-security/main amd64 Packages        
Hit http://gb.archive.ubuntu.com vivid/universe Translation-en_GB           
Hit http://gb.archive.ubuntu.com vivid/universe Translation-en              
Hit http://gb.archive.ubuntu.com vivid-updates/main Sources                 
Hit http://gb.archive.ubuntu.com vivid-updates/multiverse Sources           
Hit http://gb.archive.ubuntu.com vivid-updates/restricted Sources           
Hit http://gb.archive.ubuntu.com vivid-updates/universe Sources             
Hit http://gb.archive.ubuntu.com vivid-updates/main amd64 Packages             
Hit http://us.archive.ubuntu.com lucid-security/main i386 Packages
Hit http://gb.archive.ubuntu.com vivid-updates/restricted amd64 Packages       
Hit http://gb.archive.ubuntu.com vivid-updates/universe amd64 Packages         
Hit http://gb.archive.ubuntu.com vivid-updates/multiverse amd64 Packages
Get:3 http://security.ubuntu.com vivid-security/main Sources [36.0 kB]
Hit http://gb.archive.ubuntu.com vivid-updates/main i386 Packages              
Hit http://gb.archive.ubuntu.com vivid-updates/restricted i386 Packages        
Hit http://gb.archive.ubuntu.com vivid-updates/universe i386 Packages         
Hit http://gb.archive.ubuntu.com vivid-updates/multiverse i386 Packages       
Hit http://gb.archive.ubuntu.com vivid-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://gb.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://gb.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://gb.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://gb.archive.ubuntu.com vivid-backports/restricted Sources
Hit http://gb.archive.ubuntu.com vivid-backports/universe Sources  
Get:4 http://security.ubuntu.com vivid-security/multiverse Sources [1,957 B]
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://gb.archive.ubuntu.com vivid-backports/main amd64 Packages           
Hit http://gb.archive.ubuntu.com vivid-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com vivid-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com vivid-backports/main i386 Packages
Get:5 http://security.ubuntu.com vivid-security/restricted Sources [28 B]
Hit http://gb.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://gb.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse i386 Packages
Get:6 http://security.ubuntu.com vivid-security/universe Sources [15.6 kB]
Hit http://gb.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com vivid-backports/universe Translation-en
Get:7 http://security.ubuntu.com vivid-security/main amd64 Packages [99.8 kB]
Get:8 http://security.ubuntu.com vivid-security/restricted amd64 Packages [28 B]
Get:9 http://security.ubuntu.com vivid-security/universe amd64 Packages [50.1 kB]
Ign http://us.archive.ubuntu.com lucid-security/main Translation-en_GB       
Get:10 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [3,494 B]
Ign http://us.archive.ubuntu.com lucid-security/main Translation-en            
Get:11 http://security.ubuntu.com vivid-security/main i386 Packages [98.9 kB]
Get:12 http://security.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:13 http://security.ubuntu.com vivid-security/universe i386 Packages [50.1 kB]
Get:14 http://security.ubuntu.com vivid-security/multiverse i386 Packages [3,675 B]
Hit http://security.ubuntu.com vivid-security/main Translation-en             
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Hit http://security.ubuntu.com vivid-security/universe Translation-en
Fetched 424 kB in 2s (154 kB/s)          
Reading package lists... Done
mediaserver@SERVER:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

```
sudo apt-get dist-upgrade
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
mediaserver@SERVER:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

 ```
sudo dpkg -C
```

 ```
cat -n /etc/apt/sources.list
```
```
     1    # deb cdrom:[Xubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422.1)]/ vivid main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
     6    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main multiverse restricted universe #Added by software-properties
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    11    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main multiverse restricted universe #Added by software-properties
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
    17    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
    18    
    19    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20    ## team, and may not be under a free licence. Please satisfy yourself as to 
    21    ## your rights to use the software. Also, please note that software in 
    22    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23    ## security team.
    24    deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
    25    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    26    
    27    ## N.B. software from this repository may not have been tested as
    28    ## extensively as that contained in the main release, although it includes
    29    ## newer versions of some applications which may provide useful features.
    30    ## Also, please note that software in backports WILL NOT receive any review
    31    ## or updates from the Ubuntu security team.
    32    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    33    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse #Added by software-properties
    34    
    35    deb http://security.ubuntu.com/ubuntu vivid-security main restricted
    36    deb-src http://security.ubuntu.com/ubuntu vivid-security main multiverse restricted universe #Added by software-properties
    37    deb http://security.ubuntu.com/ubuntu vivid-security universe
    38    deb http://security.ubuntu.com/ubuntu vivid-security multiverse
    39    
    40    ## Uncomment the following two lines to add software from Canonical's
    41    ## 'partner' repository.
    42    ## This software is not part of Ubuntu, but is offered by Canonical and the
    43    ## respective vendors as a service to Ubuntu users.
    44    deb http://archive.canonical.com/ubuntu vivid partner
    45    deb-src http://archive.canonical.com/ubuntu vivid partner
    46    # deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main
    47    deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main
    48    deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main
    49    # deb http://ppa.launchpad.net/plexapp/plexht/ubuntu vivid main
    50    # deb-src http://ppa.launchpad.net/plexapp/plexht/ubuntu vivid main
```

 ```
tail -v -n +1 /etc/apt/sources.list.d/*
```
```
==> /etc/apt/sources.list.d/deb-multimedia.list <==

==> /etc/apt/sources.list.d/deb-multimedia.list.save <==

==> /etc/apt/sources.list.d/dropbox.list <==
# deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu vivid main

==> /etc/apt/sources.list.d/dropbox.list.save <==
# deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu vivid main

==> /etc/apt/sources.list.d/ehoover-ubuntu-compholio-vivid.list <==
# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main

==> /etc/apt/sources.list.d/ehoover-ubuntu-compholio-vivid.list.save <==
# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu vivid main

==> /etc/apt/sources.list.d/glennric-ubuntu-dolphin-emu-vivid.list <==
# deb http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main
# deb-src http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main

==> /etc/apt/sources.list.d/glennric-ubuntu-dolphin-emu-vivid.list.save <==
# deb http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main
# deb-src http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu vivid main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list.save <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/plex.list <==

==> /etc/apt/sources.list.d/plex.list.save <==

==> /etc/apt/sources.list.d/steam.list <==

==> /etc/apt/sources.list.d/steam.list.save <==
```

---

### Post by Jonners59 on 2015-08-08
So, I copied the etc/apt/ directory from another machine and placed it on this machine (having backed up the old first :-) I am learning ) and tried again - same problem... so something else is the problem

Something not used in a while...  noticed Ubuntu Software Centre crashes when it tries to install apps

---

### Post by ian-weisser on 2015-08-08
I'm confused now. Your post #86 seems to show no problems anymore...
I thought this was looking solved.

---

### Post by Jonners59 on 2015-08-09
> **ian-weisser said:**
> I'm confused now. Your post #86 seems to show no problems anymore...
I thought this was looking solved.
Thanks for coming on board Ian
It would seam that the repositories are ok, BUT I still can't install key apps.  Such as VLC, says they are broken....  or dependent upon apps not installed, and if I try and install these they either do not exist or are broken too

---

### Post by oldfred on 2015-08-09
Is your post of sources list the most current? It still shows Lucid entries?

That Software center does not work would be normal. Software Center, synaptic & command line all are using same files for updating and basically are front ends for apt-get on command line.

---

### Post by Jonners59 on 2015-08-09
Thought it was,,,,,

```
 cat -n /etc/apt/sources.list
     1    # deb cdrom:[Xubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422.1)]/ vivid main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
     6    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    11    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
    17    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid universe
    18    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
    19    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
    27    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
    28    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    29    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    37    deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu vivid-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
    41    deb http://security.ubuntu.com/ubuntu vivid-security universe
    42    deb-src http://security.ubuntu.com/ubuntu vivid-security universe
    43    deb http://security.ubuntu.com/ubuntu vivid-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu vivid partner
    51    deb-src http://archive.canonical.com/ubuntu vivid partner
    52    deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main
    53    # deb http://deb.opera.com/opera/ stable non-free


```

---

### Post by oldfred on 2015-08-09
I do not know about the debian entry, but now everything looks like vivid or is commented out.

---

### Post by Jonners59 on 2015-08-09
> **oldfred said:**
> I do not know about the debian entry, but now everything looks like vivid or is commented out.

Yes, but it doesn't work...  There are conflicts...  I can't install VLC for instance.  Netfix has errors and repeated alerets not installed properly.  Libre also will not load or install.

---

### Post by oldfred on 2015-08-09
Try this set of commands. Normally after a chroot to make repairs, but if you can boot you can just run them all. Either sudo on each line or the sudo  -i
If you get an error stop & post details.

 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

---

### Post by Jonners59 on 2015-08-10
> **oldfred said:**
> Try this set of commands. Normally after a chroot to make repairs, but if you can boot you can just run them all. Either sudo on each line or the sudo  -i
If you get an error stop & post details.

 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

Thanks ldFred
Have run those cmd before, shall do so again, see below.

Have this thread out too, which is probably related.
[http://ubuntuforums.org/showthread.php?t=2282306](http://ubuntuforums.org/showthread.php?t=2282306)

[PHP]Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

wine-browser-installer, lovefilm-desktop, maxdome-desktop, wine-mpg2splt-installer, wine-silverlight5.1-installer, netflix-desktop, sumo-tv2-desktop, redbox-desktop

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

[/PHP]


```
sudo -i apt-get autoclean
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

```
 sudo -i apt-get clean
```
no output

```
sudo -i apt-get update
```
```
Ign http://ppa.launchpad.net vivid InRelease
Ign http://archive.canonical.com vivid InRelease                               
Ign http://gb.archive.ubuntu.com vivid InRelease                               
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:1 http://deb.opera.com stable InRelease [2,590 B]                          
Hit http://archive.canonical.com vivid Release.gpg                             
Ign http://gb.archive.ubuntu.com vivid-updates InRelease                       
Ign http://ppa.launchpad.net vivid InRelease                                   
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com vivid Release                                 
Ign http://gb.archive.ubuntu.com vivid-backports InRelease                     
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://gb.archive.ubuntu.com vivid Release.gpg                             
Hit http://archive.canonical.com vivid/partner Sources                         
Ign http://ppa.launchpad.net vivid InRelease                                   
Get:2 http://gb.archive.ubuntu.com vivid-updates Release.gpg [933 B]           
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://archive.canonical.com vivid/partner amd64 Packages                  
Hit http://gb.archive.ubuntu.com vivid-backports Release.gpg                   
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://archive.canonical.com vivid/partner i386 Packages                   
Hit http://gb.archive.ubuntu.com vivid Release                                 
Ign http://ppa.launchpad.net vivid Release.gpg                                 
Get:3 http://gb.archive.ubuntu.com vivid-updates Release [63.5 kB]             
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Get:4 http://ppa.launchpad.net vivid Release.gpg [316 B]                       
Ign http://archive.canonical.com vivid/partner Translation-en                  
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                 
Ign http://security.ubuntu.com vivid-security InRelease                        
Hit http://gb.archive.ubuntu.com vivid-backports Release                       
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://gb.archive.ubuntu.com vivid/restricted Sources                      
Ign http://ppa.launchpad.net vivid Release                                     
Hit http://gb.archive.ubuntu.com vivid/main Sources                            
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://gb.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://gb.archive.ubuntu.com vivid/universe Sources                        
Hit http://gb.archive.ubuntu.com vivid/main amd64 Packages                     
Hit http://gb.archive.ubuntu.com vivid/restricted amd64 Packages               
Get:5 http://security.ubuntu.com vivid-security Release.gpg [933 B]            
Hit http://gb.archive.ubuntu.com vivid/universe amd64 Packages                 
Hit http://gb.archive.ubuntu.com vivid/multiverse amd64 Packages               
Get:6 http://deb.opera.com stable/non-free amd64 Packages [1,765 B]            
Get:7 http://ppa.launchpad.net vivid Release [15.1 kB]                         
Hit http://gb.archive.ubuntu.com vivid/main i386 Packages                      
Get:8 http://deb.opera.com stable/non-free i386 Packages [1,448 B]             
Hit http://gb.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid Release                                     
Hit http://ppa.launchpad.net vivid/main Sources                                
Get:9 http://security.ubuntu.com vivid-security Release [63.5 kB]              
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Hit http://gb.archive.ubuntu.com vivid/universe i386 Packages                  
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://gb.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://gb.archive.ubuntu.com vivid/main Translation-en_GB                  
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://gb.archive.ubuntu.com vivid/main Translation-en                     
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://gb.archive.ubuntu.com vivid/multiverse Translation-en_GB            
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://gb.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://gb.archive.ubuntu.com vivid/restricted Translation-en_GB            
Hit http://gb.archive.ubuntu.com vivid/restricted Translation-en               
Hit http://gb.archive.ubuntu.com vivid/universe Translation-en_GB              
Hit http://gb.archive.ubuntu.com vivid/universe Translation-en                 
Get:10 http://gb.archive.ubuntu.com vivid-updates/restricted Sources [28 B]    
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Hit http://ppa.launchpad.net vivid/main Sources                                
Get:11 http://gb.archive.ubuntu.com vivid-updates/main Sources [72.5 kB]       
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Get:12 http://gb.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B] 
Get:13 http://gb.archive.ubuntu.com vivid-updates/universe Sources [33.4 kB]   
Get:14 http://ppa.launchpad.net vivid/main Sources [2,710 B]                   
Get:15 http://gb.archive.ubuntu.com vivid-updates/main amd64 Packages [171 kB] 
Get:16 http://ppa.launchpad.net vivid/main amd64 Packages [5,076 B]            
Get:17 http://security.ubuntu.com vivid-security/restricted Sources [28 B]     
Get:18 http://ppa.launchpad.net vivid/main i386 Packages [5,078 B]             
Get:19 http://ppa.launchpad.net vivid/main Translation-en [2,974 B]            
Get:20 http://gb.archive.ubuntu.com vivid-updates/restricted amd64 Packages [28 B]
Get:21 http://ppa.launchpad.net vivid/main Sources [1,583 B]                   
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Get:22 http://gb.archive.ubuntu.com vivid-updates/universe amd64 Packages [97.6 kB]
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Get:23 http://gb.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3,494 B]
Get:24 http://security.ubuntu.com vivid-security/main Sources [36.0 kB]        
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://ppa.launchpad.net vivid/main amd64 Packages                         
Get:25 http://gb.archive.ubuntu.com vivid-updates/main i386 Packages [169 kB]  
Hit http://download.ebz.epson.net lsb3.2 Release.gpg                           
Hit http://ppa.launchpad.net vivid/main i386 Packages                          
Hit http://ppa.launchpad.net vivid/main Translation-en                         
Get:26 http://security.ubuntu.com vivid-security/multiverse Sources [1,957 B]  
Get:27 http://gb.archive.ubuntu.com vivid-updates/restricted i386 Packages [28 B]
Get:28 http://gb.archive.ubuntu.com vivid-updates/universe i386 Packages [97.1 kB]
Get:29 http://gb.archive.ubuntu.com vivid-updates/multiverse i386 Packages [3,675 B]
Hit http://gb.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://gb.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://gb.archive.ubuntu.com vivid-updates/restricted Translation-en       
Get:30 http://security.ubuntu.com vivid-security/universe Sources [15.6 kB]    
Hit http://gb.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://gb.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://gb.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://gb.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://gb.archive.ubuntu.com vivid-backports/main amd64 Packages           
Get:31 http://security.ubuntu.com vivid-security/main amd64 Packages [99.8 kB] 
Hit http://gb.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://gb.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Err http://ppa.launchpad.net vivid/main Sources                                
  404  Not Found
Hit http://download.ebz.epson.net lsb3.2 Release                               
Hit http://gb.archive.ubuntu.com vivid-backports/main i386 Packages            
Err http://ppa.launchpad.net vivid/main amd64 Packages                         
  404  Not Found
Hit http://gb.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Err http://ppa.launchpad.net vivid/main i386 Packages                          
  404  Not Found
Hit http://gb.archive.ubuntu.com vivid-backports/universe i386 Packages        
Ign http://ppa.launchpad.net vivid/main Translation-en_GB                      
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Ign http://ppa.launchpad.net vivid/main Translation-en                         
Hit http://gb.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://gb.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com vivid-backports/restricted Translation-en
Get:32 http://security.ubuntu.com vivid-security/restricted amd64 Packages [28 B]
Hit http://gb.archive.ubuntu.com vivid-backports/universe Translation-en       
Get:33 http://security.ubuntu.com vivid-security/universe amd64 Packages [50.1 kB]
Hit http://download.ebz.epson.net lsb3.2/main amd64 Packages                   
Get:34 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [3,494 B]
Get:35 http://security.ubuntu.com vivid-security/main i386 Packages [98.9 kB]  
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages                 
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB             
Get:36 http://security.ubuntu.com vivid-security/restricted i386 Packages [28 B]
Get:37 http://security.ubuntu.com vivid-security/universe i386 Packages [50.1 kB]
Hit http://download.ebz.epson.net lsb3.2/main Translation-en                   
Get:38 http://security.ubuntu.com vivid-security/multiverse i386 Packages [3,675 B]
Hit http://security.ubuntu.com vivid-security/main Translation-en          
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Hit http://security.ubuntu.com vivid-security/universe Translation-en
Fetched 1,177 kB in 2s (402 kB/s)
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
W: Failed to fetch http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/vivid/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

```
 sudo -i apt-get autoremove
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 20 not to upgrade.

```

```
sudo -i apt-get -f install
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 20 not to upgrade.

```

```
 sudo -i apt-get upgrade
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine-staging wine-staging-amd64 wine-staging-dbg wine-staging-i386:i386
The following packages will be upgraded:
  libegl1-mesa libgbm1 libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-dri:i386
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386
  libgles1-mesa libgles2-mesa libosmesa6 libosmesa6:i386 libwayland-egl1-mesa
  libxatracker2 mesa-common-dev
16 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.
Need to get 12.9 MB of archives.
After this operation, 389 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libwayland-egl1-mesa amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [46.0 kB]
Get:2 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libegl1-mesa amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [101 kB]
Get:3 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgbm1 amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [62.9 kB]
Get:4 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgl1-mesa-dri i386 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [4,415 kB]
Get:5 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgl1-mesa-dri amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [3,814 kB]
Get:6 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgles2-mesa amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [51.7 kB]
Get:7 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgles1-mesa amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [49.3 kB]
Get:8 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libosmesa6 i386 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [1,201 kB]
Get:9 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libosmesa6 amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [1,146 kB]
Get:10 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgl1-mesa-dev amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [44.6 kB]
Get:11 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgl1-mesa-glx i386 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [193 kB]
Get:12 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libgl1-mesa-glx amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [185 kB]
Get:13 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libglapi-mesa amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [61.5 kB]
Get:14 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libglapi-mesa i386 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [61.5 kB]
Get:15 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main mesa-common-dev amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [473 kB]
Get:16 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ vivid/main libxatracker2 amd64 10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid [950 kB]
Fetched 12.9 MB in 6s (2,078 kB/s)                                             
(Reading database ... 554199 files and directories currently installed.)
Preparing to unpack .../libwayland-egl1-mesa_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libwayland-egl1-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libegl1-mesa_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libegl1-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgbm1_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libgbm1:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgl1-mesa-dri_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
De-configuring libgl1-mesa-dri:i386 (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Unpacking libgl1-mesa-dri:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgl1-mesa-dri_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_i386.deb ...
Unpacking libgl1-mesa-dri:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgl1-mesa-dev_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libgl1-mesa-dev:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../mesa-common-dev_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking mesa-common-dev:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libosmesa6_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_i386.deb ...
De-configuring libosmesa6:amd64 (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Unpacking libosmesa6:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libosmesa6_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libosmesa6:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgles2-mesa_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libgles2-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgl1-mesa-glx_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_i386.deb ...
De-configuring libgl1-mesa-glx:amd64 (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Unpacking libgl1-mesa-glx:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgl1-mesa-glx_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libgles1-mesa_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libgles1-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libglapi-mesa_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
De-configuring libglapi-mesa:i386 (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Unpacking libglapi-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libglapi-mesa_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_i386.deb ...
Unpacking libglapi-mesa:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Preparing to unpack .../libxatracker2_10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid_amd64.deb ...
Unpacking libxatracker2:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) over (10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~vivid) ...
Setting up libgl1-mesa-dri:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgl1-mesa-dri:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgbm1:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libegl1-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libwayland-egl1-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up mesa-common-dev:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libglapi-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libglapi-mesa:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgl1-mesa-glx:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgl1-mesa-glx:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgl1-mesa-dev:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libosmesa6:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libosmesa6:i386 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgles2-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libgles1-mesa:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Setting up libxatracker2:amd64 (10.6.3+git20150809+10.6.736f6e16-0ubuntu0ricotz~vivid) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...

```

```
 sudo -i apt-get dist-upgrade
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  libdatrie1:i386 libthai0:i386
The following packages will be upgraded:
  wine-staging wine-staging-amd64 wine-staging-dbg wine-staging-i386:i386
4 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Need to get 78.0 MB of archives.
After this operation, 10.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main wine-staging amd64 1.7.49~ubuntu15.04.1 [2,681 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ vivid/main libdatrie1 i386 0.2.8-1 [17.3 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ vivid/main libthai0 i386 0.1.21-1 [18.0 kB]
Get:4 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main wine-staging-dbg amd64 1.7.49~ubuntu15.04.1 [35.9 MB]
Get:5 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main wine-staging-i386 i386 1.7.49~ubuntu15.04.1 [19.3 MB]
Get:6 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main wine-staging-amd64 amd64 1.7.49~ubuntu15.04.1 [20.1 MB]
Fetched 78.0 MB in 47s (1,636 kB/s)                                            
Selecting previously unselected package libdatrie1:i386.
(Reading database ... 554257 files and directories currently installed.)
Preparing to unpack .../libdatrie1_0.2.8-1_i386.deb ...
Unpacking libdatrie1:i386 (0.2.8-1) ...
Selecting previously unselected package libthai0:i386.
Preparing to unpack .../libthai0_0.1.21-1_i386.deb ...
Unpacking libthai0:i386 (0.1.21-1) ...
Preparing to unpack .../wine-staging_1.7.49~ubuntu15.04.1_amd64.deb ...
Unpacking wine-staging (1.7.49~ubuntu15.04.1) over (1.7.48~ubuntu15.04.1) ...
Preparing to unpack .../wine-staging-dbg_1.7.49~ubuntu15.04.1_amd64.deb ...
Unpacking wine-staging-dbg:amd64 (1.7.49~ubuntu15.04.1) over (1.7.48~ubuntu15.04.1) ...
Preparing to unpack .../wine-staging-i386_1.7.49~ubuntu15.04.1_i386.deb ...
Unpacking wine-staging-i386 (1.7.49~ubuntu15.04.1) over (1.7.48~ubuntu15.04.1) ...
Preparing to unpack .../wine-staging-amd64_1.7.49~ubuntu15.04.1_amd64.deb ...
Unpacking wine-staging-amd64 (1.7.49~ubuntu15.04.1) over (1.7.48~ubuntu15.04.1) ...
Setting up libdatrie1:i386 (0.2.8-1) ...
Setting up libthai0:i386 (0.1.21-1) ...
Setting up wine-staging-amd64 (1.7.49~ubuntu15.04.1) ...
Setting up wine-staging-i386 (1.7.49~ubuntu15.04.1) ...
Setting up wine-staging (1.7.49~ubuntu15.04.1) ...
Setting up wine-staging-dbg:amd64 (1.7.49~ubuntu15.04.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...

```

```
 sudo -i dpkg --configure -a
```
no output

Will now try to install vlc

No change...
```
 E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

---

### Post by oldfred on 2015-08-10
As long as you have any Failed to fetch it is not going to work. That is always the first thing you have to fix. Just because you changed to vivid, does not mean every ppa then has vivid available.

> Failed to fetch [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

---

### Post by Jonners59 on 2015-08-10
> **oldfred said:**
> As long as you have any Failed to fetch it is not going to work. That is always the first thing you have to fix. Just because you changed to vivid, does not mean every ppa then has vivid available.

OldFred
I took that one out and Opera Stable and tried again...  But still does not work.  Same problem

What next, please?????

---

### Post by oldfred on 2015-08-10
What error are you now getting. Just post error, not every bit of output.

---

### Post by Jonners59 on 2015-08-10
> **oldfred said:**
> What error are you now getting. Just post error, not every bit of output.

Well just installing VLC

```
sudo apt-get install vlc && apt-get install vlc-nox && apt-get install vlc-plugin-notify && apt-get install vlc-plugin-samba && apt-get install libvlccore8
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 2.2.0-1) but it is not going to be installed
       Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.2.0-1) but it is not going to be installed
       Recommends: vlc-plugin-samba (= 2.2.0-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by oldfred on 2015-08-10
Did you install from some other source before?
You install with && is installing each as separate lines. 
What does this give?
sudo apt-get install vlc vlc-nox vlc-plugin-notify vlc-plugin-samba libvlccore8

Have you tried using synaptic? And tick just vlc?

---

### Post by Jonners59 on 2015-08-11
> **oldfred said:**
> Did you install from some other source before?
No.

> **oldfred said:**
>  
What does this give?
sudo apt-get install vlc vlc-nox vlc-plugin-notify vlc-plugin-samba libvlccore8
```
sudo apt-get install vlc vlc-nox vlc-plugin-notify vlc-plugin-samba libvlccore8
```
```
[sudo] password for mediaserver: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libvlccore8 : Depends: vlc-data (= 2.2.0-1) but 1:2.0.6-dmo3 is to be installed
E: Unable to correct problems, you have held broken packages.
```


> **oldfred said:**
> Have you tried using synaptic? And tick just vlc?
Yes, always.  Ran the cmd line only to show you an output...

Also Update Information is still throwing up warnings about these same apps...
```
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

wine-browser-installer, lovefilm-desktop, maxdome-desktop, wine-mpg2splt-installer, wine-silverlight5.1-installer, netflix-desktop, sumo-tv2-desktop, redbox-desktop

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.


```

Interestingly, I installed these in another, similar configured machine and it gets the same messages.
Also, seems that all the errors/problems are media related, BUT that may be a red herring as I am only looking at media apps on this machine.......

So what next?

---

### Post by oldfred on 2015-08-11
Try again without  libvlccore8.

Run these first.
sudo apt-get autoremove[COLOR=#FF0000]
[/COLOR]sudo apt-get -f install

---

### Post by Jonners59 on 2015-08-11
> **oldfred said:**
> Try again without  libvlccore8.

Run these first.
sudo apt-get autoremove[COLOR=#FF0000]
[/COLOR]sudo apt-get -f install

:-(
No didn't work....
```
sudo apt-get install vlc vlc-nox vlc-plugin-notify vlc-plugin-samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
 vlc-nox : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
 vlc-plugin-notify : Depends: libvlccore8 (>= 2.0.0) but it is not going to be installed
 vlc-plugin-samba : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by oldfred on 2015-08-11
I am lost on where we are at.

I just checked my install.
I am running 14.04 and have vlc installed, but it uses  libvlccore7.

---

### Post by Jonners59 on 2015-08-11
> **oldfred said:**
> I am lost on where we are at.

I just checked my install.
I am running 14.04 and have vlc installed, but it uses  libvlccore7.

I don't know, what can I say.  This is why I am on the forum seeking help.  Should I purge and delete "something" to clear it all out, but if so what??????  There is clearly something broken.

---

### Post by oldfred on 2015-08-11
What version of Ubuntu?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
If 14.10 then it has reached end of life and that is why we cannot update?

---

### Post by Jonners59 on 2015-08-12
> **oldfred said:**
> What version of Ubuntu?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
If 14.10 then it has reached end of life and that is why we cannot update?

No it's 15.04
```
lsb_release -a
```
```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
```
```
 uname -a
```
```
linux SERVER 3.19.0-26-generic #27-Ubuntu SMP Tue Jul 28 18:27:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by oldfred on 2015-08-12
I normally am in my 14.04 install, but do have a 15.04 install on hard drive.
Have not used it for several months, but booted into it, updated it and then just did this:
sudo apt-get install vlc

And it installed a lot of supporting files. I go no conflicts or issues.

---

### Post by Jonners59 on 2015-08-12
> **oldfred said:**
> I normally am in my 14.04 install, but do have a 15.04 install on hard drive.
Have not used it for several months, but booted into it, updated it and then just did this:
sudo apt-get install vlc

And it installed a lot of supporting files. I go no conflicts or issues.

Thanks OldFred for taking the time and trouble.  Me too on two other machines (bar the silverlight/netflix alert), but it doesn't help getting to the bottom of this problem on this machine.

Any ideas?  Should I re-install, and if so how do I do so without having to rebuild everything.....?

---

### Post by oldfred on 2015-08-12
Re-install is always last resort.
Your last try seemed to only have errors on libvlccore8?
Can you try to purge & reinstall that?
sudo apt-get update
sudo apt-get upgrade
 sudo apt-get purge libvlccore8



But you should have backups so that a new clean install can be quickly restored.
Some like images, but I believe those are out of date quickly and users will not regularly make them. If just making image to restore that may be different.

My restore is a new install and copy /home back, reinstall all apps from list of installed apps. I have a few settings in /etc like grub that I have manually changed, so I copy those into /home so my regular backup includes those.

---

### Post by Jonners59 on 2015-08-12
> **oldfred said:**
> Re-install is always last resort.
Your last try seemed to only have errors on libvlccore8?
Can you try to purge & reinstall that?
sudo apt-get update
sudo apt-get upgrade
 sudo apt-get purge libvlccore8



But you should have backups so that a new clean install can be quickly restored.
Some like images, but I believe those are out of date quickly and users will not regularly make them. If just making image to restore that may be different.

My restore is a new install and copy /home back, reinstall all apps from list of installed apps. I have a few settings in /etc like grub that I have manually changed, so I copy those into /home so my regular backup includes those.
No, that didn't work either
```
sudo apt-get purge libvlccore8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libvlccore8*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 554345 files and directories currently installed.)
Removing libvlccore8 (2.2.0-1) ...
Purging configuration files for libvlccore8 (2.2.0-1) ...
mediaserver@SERVER:~/Desktop$ sudo apt-get install vlc vlc-nox vlc-plugin-notify vlc-plugin-samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
 vlc-nox : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
 vlc-plugin-notify : Depends: libvlccore8 (>= 2.0.0) but it is not going to be installed
 vlc-plugin-samba : Depends: libvlccore8 (>= 2.2.0~pre1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

And yes, I did the other two cmd first....   Bahhhhhh

---

### Post by oldfred on 2015-08-12
I am assuming that somewhere with all the ppas you had installed that it got something out of sync.
The version of libvlccore8 you uninstalled to me reads >= to required version?

---

### Post by Jonners59 on 2015-08-12
> **oldfred said:**
> I am assuming that somewhere with all the ppas you had installed that it got something out of sync.
The version of libvlccore8 you uninstalled to me reads >= to required version?

don't understand...  what do i do?

---

### Post by oldfred on 2015-08-12
At this point I thought we housecleaned out all the issues, but still you seem to have them. 
I am out of ideas. :(

---

### Post by Jonners59 on 2015-08-15
Gave up and rebuilt the machine......
Copied the sources.list, and backedup the synaptic marked, copied over etc/fstab and etc/samba/smb.conf
all back and running....  few other probs to sort out mostly around sharing from one pc to another...

---

