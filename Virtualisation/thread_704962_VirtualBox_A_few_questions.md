---
title: "VirtualBox: A few questions"
date: 2008-02-22
forum: Virtualisation
---

### Post by Tylerofl on 2008-02-22
I tried search for these things, no dice. What I want to do is load up VirtualBox on startup, on a specific screen. That shouldn't be too hard, I heard about a program called Devil's Pie that can do that.

It would be nice to be able to run Windows XP on one desktop, in fullscreen, and be able to Ctrl+Alt+Left/Right between the two. I know it'd be easy to switch over TO Windows, but how would I get from Windows to Ubuntu, without having to exit fullscreen? Seamless transitions between Linux and Windows would be awesome!

---

### Post by H_out on 2008-02-23
I use a setup where I have Xubuntu on viewport 0 and WindowsXP in full screen mode (not seamless) on viewport 1.

To load up VirtualBox on a specific screen or viewport, I use Compiz-Fusion.  It's either Window Placement or Window Rules.

The way I switch between viewports is Control+Mouse Wheel.  My viewport-switching shortcut is still accessible while I'm in the WindowsXP viewport.  I have Guest Additions installed with my VirtualBox, and my mouse is integrated into the virtual machine I'm running.  When I switch viewports, I don't have to exit full screen mode.

---

### Post by sites on 2008-02-28
Sorry to hi-jack this thread, but i'm trying to accomplish the same actions with VMware Workstation.  I've successfully mapped several apps to certain viewports, but all attempts to do so with VMware have failed.

So far i've tried the following....

title=vmware
title=VMware
program=vmware
title=Windows (the vm i'm running is titled "Windows XP Professional")



anyone have an idea?

---

### Post by fjgaude on 2008-02-28
> **Tylerofl said:**
> I tried search for these things, no dice. What I want to do is load up VirtualBox on startup, on a specific screen. That shouldn't be too hard, I heard about a program called Devil's Pie that can do that.

It would be nice to be able to run Windows XP on one desktop, in fullscreen, and be able to Ctrl+Alt+Left/Right between the two. I know it'd be easy to switch over TO Windows, but how would I get from Windows to Ubuntu, without having to exit fullscreen? Seamless transitions between Linux and Windows would be awesome!

Gosh, each desktop has its apps set the way you wish. CTRL-ALt-left/right gets to one or the other desktop in Gusty. Can't remember it was that way in Feisty.

I run five desktops with programs loaded on each set the way I want them to do my work.

It is all seamless!

---

### Post by daqron on 2010-05-16
> **sites said:**
> Sorry to hi-jack this thread, but i'm trying to accomplish the same actions with VMware Workstation.  I've successfully mapped several apps to certain viewports, but all attempts to do so with VMware have failed.

So far i've tried the following....

title=vmware
title=VMware
program=vmware
title=Windows (the vm i'm running is titled "Windows XP Professional")



anyone have an idea?
sites (and Googlers): I think I have solved this [in this thread]("http://ubuntuforums.org/showthread.php?p=9311334#post9311334"). It's a total hack but it works for me :)

---

### Post by opacatica on 2010-05-21
Your setup is probably working fine, but remember that your keyboard is tied to only one OS at a time.  Assuming you still use left-Ctrl (default) as your VBox control key, try pressing left-Ctrl once before your keystroke shortcut.  What happens is that once Microshit Windows gets focus, VBox sends keyboard actions to Windows, which have no idea what to do with your keystroke and thus disregards.  Pressing the left Ctrl key once tells VBox to togle between your host/guest OS, thus the next keystroke will be sent to Ubuntu instead which should switch workspace.  I have used this for over a year and works for me.

---

