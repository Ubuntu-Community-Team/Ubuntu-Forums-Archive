---
title: "Sharing files between host (Ubuntu) and guest (XP)"
date: 2010-11-24
forum: Virtualisation
---

### Post by mikmalot on 2010-11-24
Hi all, I'm still pretty new to Ubuntu (and Linux/Unix in general)

This may not be necessary info, but in the interest of giving as much information as possible, I'll start here: I'm trying to make my Zune run in Ubuntu so I can finally stop dual-booting. After a lot of lurking and digging I found that it looks like the best (and possibly only) way to do so is to run a virtual machine (specifically Oracle Virtual Box).

So I have a virtual machine running XP on my system. Now, what I'm trying to do is find a way to access the music on my Ubuntu system using my virtual machine so I can sync it with my Zune.

I've thus far used two methods, neither of which have worked.

Mostly using this ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) How-To, I've set up Samba, wit the exception of using a Samba GUI recommended by a friend. I've tried using Samba, but I keep getting the error message in XP saying that the network path I've designated can not be found. One last thing: I've been attempting the method that does not use WINS.

The second method I used was more simple, in theory. I simply tried sharing between the two machines, but could not get it to work, as my shared Ubuntu folder will not show up in XP.

Any help that can be given on either method would be appreciated

---

### Post by lmarmisa on 2010-11-24
Welcome to the Ubuntu forums.

You tried to use Samba with no success. The reason can be you are using NAT on the network adapter of your XP virtual machine. I recommend to switch to Bridged Adapter. After this change, your XP virtual machine will be a new computer attached to your LAN. This new virtual computer will behave like any other computer on the LAN. Therefore, you will be able to connect to samba services offered by other computers (and vice versa).

A second alternative is to use the Shared folders feature of VirtualBox. You should install the GuestAdditions on your XP guest system for using this feature. GuestAdditions is highly recommended to install in any case. 

If you are interested in VB Shared folders, this link can help you:

[]("http://www.virtualbox.org/manual/ch03.html#id460108")[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

Kind regards,

Luis

---

### Post by mikmalot on 2010-11-25
I tried the Bridge Adapter, but that didnt work. However, I installed GuestAdditions and it worked like a charm! When I get home this weekend I'll make sure my Zune will sync, but so far so good!

Thanks a bunch!

---

