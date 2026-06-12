---
title: "Linux through Windows??"
date: 2007-11-02
forum: The Cafe
---

### Post by Anthrax9 on 2007-11-02
I have a Dual boot XP and Ubuntu system
Is it possible to use this Linux from Windows using programs like KevTerm??:confused:

---

### Post by Anthrax9 on 2007-11-02
did not know where to put this:confused:

---

### Post by n3tfury on 2007-11-02
here

[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

---

### Post by aaaantoine on 2007-11-02
You want to run your existing Ubuntu installation through Windows?  I don't know if it's possible...

But if I'm wrong, I would certainly like to try it myself, except I would run Windows in Ubuntu. :)

---

### Post by anaconda on 2007-11-02
> **aaaantoine said:**
> You want to run your existing Ubuntu installation through Windows?  I don't know if it's possible...

But if I'm wrong, I would certainly like to try it myself, except I would run Windows in Ubuntu. :)

VMWare can do that..  it IS possible to run a windows from a real partition using vmware. But I prefer having windows just in a virtualmachine. 

I bet the same would work the othew way eg. running an existing ubuntu from vmware in windows.

---

### Post by coffeecat on 2007-11-02
**Anthrax9**, you need virtualisation software. You can use Windows as the host and Linux as the guest, or vice-versa. Search the forum or google for Qemu, VMWare or Virtual Box.

I've never used it, but I've read on another forum that Virtual Box is easy to set up and use. I don't know whether it's in the Ubuntu repositories and I can't check because I'm in Gentoo atm, but it wouldn't take long for you to look in Synaptic. :wink:

Good luck.

---

### Post by stimpack on 2007-11-02
I don't know if that's possible in VB, running off a raw partition. I'm pretty sure the windows installation would not be happy about the massive hardware change it finds running virtually though.

Run with an image instead, I do this with VirtualBox, it is a *very* good solution, I get no drawbacks than when running native. (games excluded, virtual graphics cards are poop)

---

### Post by popch on 2007-11-02
There are some very useful guides on VirtualBox's web site on
- Running a vrtual machine off a real partition
- Preparing an existing VM or Partition for use in VirtualBox

VirtualBox is in the repos. I have installed it in Gutsy without any problems and use it to run Win2k and WinXP under Ubuntu.

---

### Post by anaconda on 2007-11-02
> **stimpack said:**
> I don't know if that's possible in VB, running off a raw partition. I'm pretty sure the windows installation would not be happy about the massive hardware change it finds running virtually though.)

It is possible.
 But the hardware change is a problem, because then windows will ask you to re-activate your copy of windows, and in some cases it wants you to reactivate after each different boot. 

In xp you can make different hardware profiles and then you have to select which one you boot to..

---

### Post by djsroknrol on 2007-11-02
I believe you could convert your Linux partition with VMware converter and run it through VMware. It worked with my WIN2000PRO partition...no reason why it wouldn't work in reverse....

---

### Post by Anthrax9 on 2007-11-02
KevTerm is a basic terminal program to access a working Linux (or other) server via a network connection
so is it possible to start the Linux server in Windows and then connect to this working server via KevTerm so that it would be posssible for Linux and XP to run at the same time... simultaneously!!:-\"

---

### Post by Anthrax9 on 2007-11-02
any way of doing this without virtualization???:confused:

---

### Post by BetaguyGZT on 2007-11-02
There are a few solutions to this question. One of the most widely-used solutions is [CoLinux](http://www.colinux.org/), but it can be difficult to set up.

Based upon that, there's [andLinux](http://www.andlinux.org/), although it's not been updated for some time it's the easiest and most straightforward way for **me** to get stuff working. It pretty much contains everything you need to get it running quickly. Moreover, it's based on Xubuntu Edgy, so it's a decent choice (I believe you can update the packages yourself -- just don't update the kernel!).

Hope this helps. :guitar:

---

### Post by Anthrax9 on 2007-11-03
thnx a lot will try with both of them
would you recommend [wubi]("http://wubi-installer.org/")
It treats linux as an application on windows
this is what one of my friends told me

---

### Post by FuturePilot on 2007-11-03
> **Anthrax9 said:**
> thnx a lot will try with both of them
would you recommend [wubi]("http://wubi-installer.org/")
It treats linux as an application on windows
this is what one of my friends told me

Actually Wubi installs Ubuntu on the same partition as Windows from within Windows, but it still acts as a true dual boot. You can't run it from inside Windows.

---

### Post by Anthrax9 on 2007-11-03
thnx for the info 
i wanted to run linux along with windows as in virtualization but without using virtualization is there anyway to boot windows and the linux kernel at the same time???:confused:

---

### Post by BetaguyGZT on 2007-11-03
> 19 Hours Ago 01:09 AM
Anthrax9 	

thnx for the info
i wanted to run linux along with windows as in virtualization but without using virtualization is there anyway to boot windows and the linux kernel at the same time???

That's what CoLinux (and hence andLinux) does -- it runs the Linux lernel as a process on Windows.

---

### Post by Anthrax9 on 2007-11-04
Thanks i will try andLinux any way this can be done with Ubuntu???

---

### Post by BetaguyGZT on 2007-11-04
andLinux **IS** Ubuntu -- Xubuntu Edgy to be exact. I've got it installed and updated it to the most current (Edgy) packages available. I do **not** recommend a dist-upgrade -- you can be sure that chaos and breakage will ensue if you do.

Having said that, there's a ton of stuff that's been backported to Edgy from Feisty, and you should end up with pretty up-to-date stuff. I cannot stress enough the need to be careful: anything that updates the kernel is no good. Updating X seems to be ok though, but that one is dodgy since X is hacked to death in andLinux. There's a lot that can go wrong, so be careful -- and if it's bad enough, it can (and **will**) affect Windows.

So, yeah. Have fun with it, but be careful not to push it too far.

---

### Post by BetaguyGZT on 2007-11-05
Just a little update -- following the instructions given [here](http://www.joachim-gehweiler.de/en/software/andlinux.php), I've got it running as a service and I'm using the launcher. Tweaked the theme a bit (among some other things like installing Tahoma, etc), and the system is happy as a clam. Running it as a service seems to have improved its' speed also, because it's running at almost-native speed.

Best part of all, the menu is totally configurable and items are added via the **menu.txt** file.

Enjoy! :guitar:

---

### Post by Anthrax9 on 2007-11-05
Thanks a lot BetaguyGZT the link you gave was very very very helpful
Thanks!!!!!!!!\\:D/\\:D/

---

### Post by BetaguyGZT on 2007-11-05
Sure thing. :D

---

