---
title: "Major issues (defaults to Xfce - ugly!)"
date: 2011-12-12
forum: Ubuntu Studio
---

### Post by Voluntarist on 2011-12-12
I have had a terrible time with both the vanilla Ubuntu 11.10 and Studio in terms of graphics. When I boot up studio my monitor says "Out of Range." After a few seconds the login screen comes up in with an ugly pink background, and the only option is Xfce. I've updated all packages and used the recommended graphics driver.

My hardware is a custom built computer that is about four years old. It's an AMD Phenom quad-core, 2gb RAM, and a Gigabyte mobo. I don't remember any more details off the top of my head, if you need some please ask me.

---

### Post by Bucky Ball on 2011-12-12
When at the grub menu list at boot, choose the studio install but hit 'e' to edit it rather than 'enter' to boot it. At the end of the kernel line (which probably has 'splash' or 'nosplash' at the end, add, 'nomodset' to the end of that line. Follow the instructions at the bottom of screen to then boot (can't remember which key you press).

If that gets you in, get online, update, check System>Admin>Additional Drivers. Is there a driver there for your graphics? If so, enable it. Reboot and see what happens.

---

### Post by Voluntarist on 2011-12-12
> **Bucky Ball said:**
> When at the grub menu list at boot, choose the studio install but hit 'e' to edit it rather than 'enter' to boot it. At the end of the kernel line (which probably has 'splash' or 'nosplash' at the end, add, 'nomodset' to the end of that line. Follow the instructions at the bottom of screen to then boot (can't remember which key you press).

If that gets you in, get online, update, check System>Admin>Additional Drivers. Is there a driver there for your graphics? If so, enable it. Reboot and see what happens.
A problem: My screen does not function at all until it reaches the login screen.

Should I try and do it blind without visual confirmation? Is that possible?

---

### Post by Bucky Ball on 2011-12-12
Ah, you are not getting a choice? Try hitting either escape or shift (can't remember which, it changed one release) and see if that gives you the grub boot options. You can also install Grub Customizer and change the time for the grub menu list at boot (it is probably set to zero). You can do this via the terminal but this is easier and you can do a few other neat things with Grub Customizer, too. 

I think it is in Synaptics Package Manager (or Software Centre if you're using 11.10).

PS: If you're wanting to create a serious multimedia production box you wouldn't use anything but the release designed for production machines and with three year support, the LTS releases. Currently that's 10.04 LTS. If you're a hobbyist experimenting, then use what you like, but be prepared to perhaps do more fixing that recording and mixing. ;)

PPS: Why are you defaulting to Xfce? You installed that DE? Ubuntu Studio does not use that DE by default, although you can add it later (as I have as I prefer it). If you've done a clean install of Ubuntu Studio on a blank partition or hard drive, then something is amiss. Xfce shouldn't be an option and shouldn't be installed at all as part of Studio install.

---

### Post by Voluntarist on 2011-12-12
> **Bucky Ball said:**
> Ah, you are not getting a choice? Try hitting either escape or shift (can't remember which, it changed one release) and see if that gives you the grub boot options. You can also install Grub Customizer and change the time for the grub menu list at boot (it is probably set to zero). You can do this via the terminal but this is easier and you can do a few other neat things with Grub Customizer, too. 

I think it is in Synaptics Package Manager (or Software Centre if you're using 11.10).

PS: If you're wanting to create a serious multimedia production box you wouldn't use anything but the release designed for production machines and with three year support, the LTS releases. Currently that's 10.04 LTS. If you're a hobbyist experimenting, then use what you like, but be prepared to perhaps do more fixing that recording and mixing. ;)

PPS: Why are you defaulting to Xfce? You installed that DE? Ubuntu Studio does not use that DE by default, although you can add it later (as I have as I prefer it). If you've done a clean install of Ubuntu Studio on a blank partition or hard drive, then something is amiss. Xfce shouldn't be an option and shouldn't be installed at all as part of Studio install.

For some reason all that shows up is Synaptic, even though it's a fresh install of 11.10. I couldn't find anything called "Grub Customizer," but I did find startuptools which I installed and changed the color depth setting for Grub from 8 to 24 bit, and the resolution to the proper resolution. I am now welcomed with the proper booting splash screen, but still no Grub, and it defaults to the same ugly login window with the only desktop environment option being Xfce.

If it helps at all here is what the Nvidia program said my on-board GPU is:
GeForce 6150SE nForce 430 (GPU 0)

Should I try 11.04 instead?

---

### Post by jejeman on 2011-12-12
> Why are you defaulting to Xfce? Ubuntu studio 11.10 use xfce as default DE. And for the "uglyness" you should read release notes.

If you have only one OS installed there shall be no grub showing by default. 
Give us output from
```
cat /etc/default/grub
```

p.s.
Friendly advice > do not use "helpers" (e.g. Grub Customizer) to config youre system. Edit the config files by your self. It's much more safer, plus you will know what has been changed.

---

### Post by Voluntarist on 2011-12-12
> **jejeman said:**
> Ubuntu studio 11.10 use xfce as default DE. And for the "uglyness" you should red release notes.

If you have only one OS installed there shall be no grub showing by default. 
Give us output from
```
cat /etc/default/grub
```p.s.
Friendly advice > do not use "helpers" (e.g. Grub Customizer) to config youre system. Edit the config files by your self. It's much more safer, plus you will know what has been changed.

Here's my output:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=795"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I really like Gnome better, so I might end up switching back a release.

---

### Post by jejeman on 2011-12-12
How many OS do you have installed? From grub config I can see that you probably have just one, because it's not set to show.
If you want to make grub show you need to add comment to this line
GRUB_HIDDEN_TIMEOUT=0
like this
#GRUB_HIDDEN_TIMEOUT=0

also you need to change the resolution of grub here
#GRUB_GFXMODE=640x480
just uncomment the line, like this
GRUB_GFXMODE=640x480

You have two times "splash" erase the one from here
GRUB_CMDLINE_LINUX=" splash vga=795"
to look like this
GRUB_CMDLINE_LINUX="vga=795"


Save the file and update grub, like this
```
sudo update-grub
```

---

### Post by Bucky Ball on 2011-12-12
> **jejeman said:**
> 
If you want to make grub show you need to add comment to this line
GRUB_HIDDEN_TIMEOUT=0
like this
#GRUB_HIDDEN_TIMEOUT=0



```
GRUB_HIDDEN_TIMEOUT=10
```

... you mean and the hash tag needs to be removed.

With one install you are still going to get a list. The regular and recovery kernel.

---

### Post by jejeman on 2011-12-12
If you comment out GRUB_HIDDEN_TIMEOUT=0 grub will show.
If you add value for GRUB_HIDDEN_TIMEOUT=10 grub will not show, but count to 10, with black screen. One need to press shift in that period in order to show grub.

---

### Post by Bucky Ball on 2011-12-12
```
GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="5"


```That's mine. I get grub options at boot no problem. That should make things clearer for OP.

---

### Post by jejeman on 2011-12-12
Of course, you have comment on
#GRUB_HIDDEN_TIMEOUT="0"
just like I said.

---

### Post by Bucky Ball on 2011-12-12
> **jejeman said:**
> Of course, you have comment on
#GRUB_HIDDEN_TIMEOUT="0"
just like I said.

Sure, but all OP needs to do is make sure their's looks the same as my full output in my last post. Saves explaining. ;)

---

### Post by johnmr on 2012-01-02
If you comment out GRUB_HIDDEN_TIMEOUT=0 grub will show.
If you add value for GRUB_HIDDEN_TIMEOUT=10 grub will not show, but count to 10, with black screen. One need to press shift in that period in order to show grub.

---

### Post by kr651129 on 2012-01-03
I'm having the same problem on my dell 1545 using the x64 Ubuntu Studio 11.10

Holding down shift will bring up the grub as it always has and I get the standard ubuntu studio splash screen.  Once I get to the login page it defaults to xfce with no other choice.  I'm downloading the LTS right now to rule that out but I wouldn't think I would have to many problems as I've been running Ubuntu 11.10 x64 since it was released.

---

### Post by jejeman on 2012-01-03
> Once I get to the login page it defaults to xfce with no other choice. As I said it before, Ubuntu studio 11.10 use xfce as default DE. So that is normal to not have anything but Xfce.

---

### Post by kr651129 on 2012-01-03
> **jejeman said:**
> As I said it before, Ubuntu studio 11.10 use xfce as default DE. So that is normal to not have anything but Xfce.

Gotcha, that's what I get for skipping posts.

Sugestions on how to make my install look like the screenshots on ubuntustudio.org ?

---

### Post by jejeman on 2012-01-03
Those screenshots are from 2008. Where there was different gdm, and of course, gnome 2 as DE.
So, it can't look like that.

All you can do is to learn how to customize Xfce. There is, however, a window theme called ubuntustudio, you can choose it, and that's it.
You should read release notes for Ubuntu Studio 11.10, to realise that this version is not complete.

---

### Post by kr651129 on 2012-01-03
Ok so I figured it out, I did the "upgrade" from vanilla Ubuntu 11.10 x64 and it looked HORRIBLE, it installed all the icons, sounds, software, and whatnot.  And Unity ran but looked so bad, but I did a fresh Ubuntu Studio THEN installed Unity

```
sudo apt-get install ubuntu-desktop
```

And it looks great, try it out.

---

### Post by Bucky Ball on 2012-01-03
You did install Unity but you also installed ubuntu-desktop which drags in a ton of other apps and stuff. You only needed to install the Unity DE. ;)

It's in Synaptics or if you haven't got that then Software Centre. Search for 'unity' and there it is. You don't need all the stuff that comes with ubuntu-desktop.

---

