---
title: "How can I tell if I have PUEL or OSE of Virtualbox"
date: 2009-07-04
forum: Virtualisation
---

### Post by irv on 2009-07-04
Here is the splash screen of the one I am using:
[ATTACH]119906[/ATTACH] 
I thought 3.0 was PUEL, or am I wrong.
The reason I am asking is I can not get the USB to work no matter what I try.

---

### Post by carml on 2009-07-04
I think your is the OSE version,because mine is different (me too I have 3.0).

---

### Post by memilanuk on 2009-07-04
I thought the OSE versions only came as source code... if you installed it via debs, it is most likely the PUEL version.  

Have you tried installing the guest additions for linux?  Not much experience w/ them myself.

---

### Post by howefield on 2009-07-04
Screenshot is exactly the same as mine, and I have PUEL.

If it comes to it, easy enough to uninstall and put it back. You won't lose your VMs.

---

### Post by scorp123 on 2009-07-04
> **irv said:**
> Here is the splash screen  Why not simply ask the package manager (assuming you installed a *.deb and/or via the package manager):

```
dpkg -l virtualbox*
```

If I do that here I get this:

```
> dpkg -l virtualbox*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
un  virtualbox                     <none>                         (no description available)
rc  virtualbox-2.2                 2.2.4-47978_Ubuntu_jaunty      Sun VirtualBox
ii  **virtualbox-3.0**                 3.0.0-49315_Ubuntu_jaunty      **Sun VirtualBox** 
```

The OSE packages are named differently ("virtualbox-ose"), so the above definitely is the PUEL release.

```
> apt-cache search virtualbox

**virtualbox-ose** - x86 virtualization solution - binaries
virtualbox-ose-dbg - x86 virtualization solution - debugging symbols
virtualbox-ose-guest-source - x86 virtualization solution - guest addition module source
virtualbox-ose-guest-utils - x86 virtualization solution - guest utilities
virtualbox-ose-source - x86 virtualization solution - kernel module source
virtualbox-2.2 - Sun VirtualBox
**virtualbox-3.0** - Sun VirtualBox
```

---

### Post by irv on 2009-07-04
> **carml said:**
> I think your is the OSE version,because mine is different (me too I have 3.0).

Can you send me a link to the download you did? Also can you clip your splash screen from Virtualbox so I can see what it looks like.

---

### Post by irv on 2009-07-04
My out-put for dpkg -l virtualbox looks the same:
> dpkg -l virtualbox*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  virtualbox     <none>         (no description available)
ii  virtualbox-3.0 3.0.0-49315_Ub Sun VirtualBox
pn  virtualbox-ose <none>         (no description available)
pn  virtualbox-ose <none>         (no description available)
pn  virtualbox-ose <none>         (no description available)
pn  virtualbox-ose <none>         (no description available)
un  virtualbox-sou <none>         (no description available)
irv@irv-new-laptop:~$ 

This is crazy why my USB doesn't work. All my devices come up in the list, but they are all greyed out. Also the little USB icon at the bottom says "No USB devices", and I have a USB keyboard and mouse hooked up that are working fine but I can't get my USB drive to work. They are in the greyed out list, but not available in WinXP, and I have no way of selecting them for the greyed out list.

---

### Post by carml on 2009-07-04
Here's the link[HTML]http://www.virtualbox.org/wiki/Downloads[/HTML],I cannot have a decent screenshoy of Virtualbox,sorry.

---

### Post by irv on 2009-07-04
> **carml said:**
> Here's the link[HTML]http://www.virtualbox.org/wiki/Downloads[/HTML],I cannot have a decent screenshoy of Virtualbox,sorry.

We must have the same one, because I downloaded the same one you did.
I did the VirtualBox binaries, VirtualBox 3.0.0 for Linux hosts which took me to [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") and I downloaded the Ubuntu 9.04 version.
This is the file I downloaded and installed. [ATTACH]119911[/ATTACH]
So it must be the PUEL.

---

### Post by carml on 2009-07-04
Somewhere in the forum speaked of the way to obtain the use of USB under the PuEL version of Virtualbox,if I find something I'll post here the link.

---

### Post by RadarBat on 2009-07-04
I was under the impression that Guest Appliances only came with the Enterprize Edition (The one you pay for.)

EDIT: I was wrong. the VirtualboxGuestAdditions.iso is under the File System>usr>share>VirtualBox directory.

---

### Post by irv on 2009-07-05
> **irv said:**
> This is crazy why my USB doesn't work. All my devices come up in the list, but they are all greyed out. Also the little USB icon at the bottom says "No USB devices", and I have a USB keyboard and mouse hooked up that are working fine but I can't get my USB drive to work. They are in the greyed out list, but not available in WinXP, and I have no way of selecting them for the greyed out list.

I finely got my USB to work. Here is what I had to do:
System>Administration>User and Groups
Went to Manage Groups select the vboxusers group check properties and wrote down the Group ID number. My number was 127.
I then went to a terminal and typed
```
sudo gedit /etc/fstab
``` and made a change to the following line.
> none    /proc/bus/usb    usbfs    devgid=85,devmode=664   0  0
Changing the devgid=85 to devgid=127.
Saved the file and shutdown all the running apps and restarted the system. After booting up I went to Virtualbox open up WinXP and everything was not grayed out. I click on the USB drive I wanted and it loaded the driver and it worked great.:p
I hope all this effort will help someone else out.
Thanks for all the input for all out here and on the Virtualbox forum. ;)****

---

### Post by peepingtom on 2009-07-06
Are you sure the line in fstab is necessary?

In my experience, it's only necessary to add your user to the "vboxusers" group, you can do this in gnome using the "Users and Groups" app in the system administration menu.I ran into this a few months ago and it's a good lesson to learn, this type of permission setting is only going to become more common to prevent people from using sudo so flippantly.

Anyway good luck, spread the gospel.

---

### Post by irv on 2009-07-06
> **peepingtom said:**
> Are you sure the line in fstab is necessary?

In my experience, it's only necessary to add your user to the "vboxusers" group, you can do this in gnome using the "Users and Groups" app in the system administration menu.I ran into this a few months ago and it's a good lesson to learn, this type of permission setting is only going to become more common to prevent people from using sudo so flippantly.

Anyway good luck, spread the gospel.
I had my name in the "vboxusers" group, but everything was still grayed out Until I corrected the line. Maybe there is something unique to my install. I don't know for sure, but I know this it works. And yes, I will keep spreading the gospel. Amen):P

---

### Post by irv on 2009-07-06
I guess I found out the dumbest thing. In Ubuntu users and groups when your name appears in a group and has no check mark you are part of the group, but if you put a check mark on it, it take you out of the group. I was thinking the opposite. I thought when you put a check mark by your name you were part of that group. When I took the check mark off then it worked. I changed my fstab back to the way it was and now everything works.

---

### Post by yesint on 2009-07-06
> **irv said:**
> I guess I found out the dumbest thing. In Ubuntu users and groups when your name appears in a group and has no check mark you are part of the group, but if you put a check mark on it, it take you out of the group. I was thinking the opposite. I thought when you put a check mark by your name you were part of that group. When I took the check mark off then it worked. I changed my fstab back to the way it was and now everything works.

Sorry, but you are wrong as far as I understand. If it is checked then you are a member of the group (at least for me). I suspect that you screwed up something...

---

### Post by irv on 2009-07-06
> **yesint said:**
> Sorry, but you are wrong as far as I understand. If it is checked then you are a member of the group (at least for me). I suspect that you screwed up something...

I wish I knew what I screwed up, because I had to take the check mark off all the groups I was in, even the user group.

---

### Post by begkev5 on 2009-07-10
Just to confirm irv's last posting...I experienced the same thing with the check box.  USB support was enabled after I unchecked the box next to my username in the vboxusers group.

---

### Post by irv on 2009-07-11
> **begkev5 said:**
> Just to confirm irv's last posting...I experienced the same thing with the check box.  USB support was enabled after I unchecked the box next to my username in the vboxusers group.

I reverted back to what I did in my 12th post, so disregard post 15. I now have a check mark in vboxusers by my name and everything is working. 
By the way I went through the list and took the check mark off by my name, don't ever do this I locked myself out of admin rights. Here is the fix if you ever do this:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")
So yesint is right in post 16, If it is checked then you are a member of the group.

---

