---
title: "Gnome shell: pressing windows key and typing application name crashes the shell?"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-02-19
Hello All

After today's updates, I'm on Gnome Shell package 3.2.2.1-0ubuntu1, and using the nvidia restricted drivers 295.20, kernel with 3.2.0-17-generic (64bit).

I can use the mouse to hit the upper right hot spot, then click icons to start applications.

I can bring up Activities by pressing the Windows key then use the mouse to find applications &C

If I try to tap the Windows key and type the name of the program, then press enter, the Activities overlay and top bar disappear. Sometimes Gnome Shell restarts, other times I'm left with just a bare desktop. Can't invoke terminal, so I actually had to reboot by pressing power switch to bring up the Shutdown dialog. First time I've had to do that this cycle.

Anyone else seeing this? Unity is working fine, rebooted a couple of times, can reproduce behaviour in Gnome Shell easily.

---

### Post by PaulW2U on 2012-02-19
Already being discussed at [http://ubuntuforums.org/showthread.php?t=1925811](http://ubuntuforums.org/showthread.php?t=1925811)

The only time I've witnessed a crash is once when I searched for a program that didn't exist.

---

### Post by keithpeter on 2012-02-19
Thanks

Looks like this one

[http://ubuntuforums.org/showpost.php?p=11695746&postcount=8](http://ubuntuforums.org/showpost.php?p=11695746&postcount=8)

but it is happening with any name that I type, correctly spelled or not. I use the British English locale.

Cheers

---

### Post by Woonjas on 2012-02-29
Same behavior for me on my Dell Lattitude E6520.
Really annoying, I don't want to have to switch back to Unity, but I might not have a choice until it gets fixed.

Is this filed as a bug yet?

---

### Post by jbicha on 2012-02-29
How about trying the open source nouveau drivers?

---

### Post by t.rei on 2012-02-29
Had the same thing, a workaround that works for me is to frequently move or delete the file 
*~/.local/share/recently-used.xbel* .

After that the search works wonderfully and is FAST.

---

### Post by kurt18947 on 2012-02-29
I've had the same problem.  I tried t.rei's fix and it didn't work.  It did however produce a message that package 'libxml2' was obsolete.  Went to Synaptic, found the package and sure enough, there was a newer version available.  Upgraded the package and so far so good.  I've been running updates daily and this package hasn't showed an upgrade available AFAIK.

---

### Post by skewty on 2012-02-29
I have experienced this today myself.  

What is the bug number / link?

---

### Post by sdowney717 on 2012-03-02
And yes it affects me too.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/936132](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/936132)

---

### Post by keithpeter on 2012-03-02
> **jbicha said:**
> How about trying the open source nouveau drivers?

Hello All

For the sake of testing 12.04 I'll do that on a usb stick install.

I hope for a fix as I would rather like to use graphics acceleration on the workstation. I realise video drivers are a bit of a saga.

**Edit**: installed gdm [as suggested by 3togo]("http://ubuntuforums.org/showpost.php?p=11733069&postcount=25") and Gnome Shell still falls over when using search but now restarts and does not leave me with a desktop with no panels or launcher.

Cheers

---

### Post by webster01 on 2012-03-02
i had the same problem in 11.10
so i installed 12.04 beta yesterday and installed gnome-shell using ubuntu software center
i have installed only nvidia driver using jockey  
now it crashes when i type in search box

[http://i.imgur.com/C6MTf.png](http://i.imgur.com/C6MTf.png)

[http://i.imgur.com/BFYlU.png](http://i.imgur.com/BFYlU.png)


how do i fix this problem

---

### Post by cariboo on 2012-03-03
Merged two threads on the same subject

---

### Post by bmbaker on 2012-03-03
why don't you upgrade the g-s to the latest 3.3.90 it is alot more up to date ?
its in the precise repos! i am using ricotz/testing ppa for awhile and its very stable as they are mainly doing small bug fixes.

---

### Post by keithpeter on 2012-03-03
> **bmbaker said:**
> why don't you upgrade the g-s to the latest 3.3.90 it is alot more up to date ? its in the precise repos! i am using ricotz/testing ppa for awhile and its very stable as they are mainly doing small bug fixes.

Hello bmbaker

How do I try replacing g-s 3.2.2.1-0ubuntu1 with g-s 3.3.90 on a 64 bit Precise installation?

apt-get cant find anything matching gnome-shell-3.3*

Cheers

---

### Post by Nipas on 2012-03-04
It seems that I have the same problem in 12.04 beta. When I start typing in the search box using gnome shell, it crashes and reloads aftersome seconds.. I hope the developers to pay attention to this as it is a major issue.

---

### Post by keithpeter on 2012-03-04
Hello Nipas

My work-around for Gnome Shell at present on my hardware (Xeon quad/64bit/nvidia GT520 card/Recommended restricted drivers installed via Jockey) is

[LIST=1]
[*]Install GDM as  the desktop manager [as suggested by 3togo]("http://ubuntuforums.org/showpost.php?p=11733069&postcount=25") :then I get the panels back when Gnome Shell crashes
[*]Delete the ~/.local/share/recently-used.xbel file as suggested by t.rei, then Gnome Shell seems to operate normally
[/LIST]

I'm sure the bug will get attention, but it could be an nvidia restricted driver issue.

PS: I'm also getting very restricted graphics with the default driver (assumed to be nouveau but need to check its not dropping to VESA) once I run a live session from a USB stick. Only Ubuntu 2d and no acceleration. I'll be investigating that issue with an 'install' to a USB stick later next week.

---

### Post by bmbaker on 2012-03-04
> **keithpeter said:**
> Hello bmbaker

How do I try replacing g-s 3.2.2.1-0ubuntu1 with g-s 3.3.90 on a 64 bit Precise installation?

apt-get cant find anything matching gnome-shell-3.3*

Cheers

Hi Hi :-)
add the gnome3-team/gnome3 ppa
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
```
this will give you G-S version 3.3.90-0ubuntu1~precise2
enjoy :-)

---

### Post by sdowney717 on 2012-03-05
Thanks, I got desperate enough to risk it.

I just did this restarted and the problem is gone away.
Fixed. Typing in the search box does not crash the system.
Everything is working.

---

