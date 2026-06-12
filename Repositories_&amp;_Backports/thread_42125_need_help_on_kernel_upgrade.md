---
title: "need help on kernel upgrade"
date: 2005-06-16
forum: Repositories &amp; Backports
---

### Post by ssck on 2005-06-16
hi all,

need help on kernel upgrade :- 

i have the following error :

trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

what does it mean ? can't it be overwritten with the latest file ?

pls help.

tks

---

### Post by ssck on 2005-06-16
[QUOTE=ssck]hi all,

need help on kernel upgrade :- 

i have the following error :

trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

what does it mean ? can't it be overwritten with the latest file ?

pls help.

tks[/QUOTE]

must i uninstall ndiswrapper in order to upgrade the linux-image-2.6.10-5-386 file ?

is there a way of getting it to overwrite automatically ? what if i don't update this package ? what are the implications ?

thanks.

---

### Post by bertimus on 2005-06-16
I'm also having the same issue.  I installed ndiswrapper from source before testing to see if the default worked for me.  Now I can't upgrade the linux-image package. Oops!

Is there an easy way to revert back to the default (hoary) ndiswrapper package?

---

### Post by ssck on 2005-06-16
[QUOTE=bertimus]I'm also having the same issue.  I installed ndiswrapper from source before testing to see if the default worked for me.  Now I can't upgrade the linux-image package. Oops!

Is there an easy way to revert back to the default (hoary) ndiswrapper package?[/QUOTE]


can anyone out there help us ? or we really have to uninstall ndiswrapper ?? :neutral:

---

### Post by az on 2005-06-16
The thing is that the ndiswrapper modules package overwrites the one already there.  You are going to have to remove it and then reinstall it.

---

### Post by bertimus on 2005-06-16
[QUOTE=azz]The thing is that the ndiswrapper modules package overwrites the one already there.  You are going to have to remove it and then reinstall it.[/QUOTE]
Alright, here's where I'm at with this.  I've searched and read the forums for probably 3 hours now, and I've made some progress.  I'm still a little stuck, but I've gotten past the linux-image package failure.  Hopefully someone can fill in the blanks to hassle-free wireless.

I followed the thread at [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683) for the most part to reconfigure ndiswrapper - you'll need a hard-wired ethernet connection as a fallback while you do this (I set up my PowerBook to share its AirPort connection over Ethernet, then dusted off an old hub to connect to Ubuntu... oi!).  And that's it.  I'm back up and running wirelessly with Hoary's default ndiswrapper package and I was able to install the updated linux-image package without furthur issue.

Now, I'm stuck where a lot of others are, it seems.  When Ubuntu starts up and loads into Gnome, I need to manually open System > Administration > Networking to activate the the wireless connection.  I've searched on this topic as well, and haven't found anything to solve this problem.

ndiswrapper exists in /etc/modprobe.d/
ndiswrapper exists in /etc/modules
/etc/network/interfaces looks like this: 

```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid xxxxxx (my essid)
wireless-key xxxxxx (my wep key)

auto wlan0

```

What am I missing?

---

### Post by ssck on 2005-06-17
[QUOTE=azz]The thing is that the ndiswrapper modules package overwrites the one already there.  You are going to have to remove it and then reinstall it.[/QUOTE]

thanks.i removed the ndiswrapper and have done the kernel upgrade and everything is back to normal.the thing is, do i have to do this everytime there is a kernel upgrade ?

---

### Post by ssck on 2005-06-17
[QUOTE=bertimus]Alright, here's where I'm at with this.  I've searched and read the forums for probably 3 hours now, and I've made some progress.  I'm still a little stuck, but I've gotten past the linux-image package failure.  Hopefully someone can fill in the blanks to hassle-free wireless.

I followed the thread at [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683) for the most part to reconfigure ndiswrapper - you'll need a hard-wired ethernet connection as a fallback while you do this (I set up my PowerBook to share its AirPort connection over Ethernet, then dusted off an old hub to connect to Ubuntu... oi!).  And that's it.  I'm back up and running wirelessly with Hoary's default ndiswrapper package and I was able to install the updated linux-image package without furthur issue.

Now, I'm stuck where a lot of others are, it seems.  When Ubuntu starts up and loads into Gnome, I need to manually open System > Administration > Networking to activate the the wireless connection.  I've searched on this topic as well, and haven't found anything to solve this problem.

ndiswrapper exists in /etc/modprobe.d/
ndiswrapper exists in /etc/modules
/etc/network/interfaces looks like this: 

```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid xxxxxx (my essid)
wireless-key xxxxxx (my wep key)

auto wlan0

```

What am I missing?[/QUOTE]


try the gtkwifi tool.it is pretty good.

---

### Post by bertimus on 2005-06-17
[QUOTE=ssck]try the gtkwifi tool.it is pretty good.[/QUOTE]
 Hehe... I'm using GTKWifi.   I've narrowed it down to manually configuring my default gateway device every boot.  Grr....

About the kernel upgrade, I think if you've got wireless working again thru the default ndiswrapper, then all is well.  AFAIK the issue was caused in the first place by manually compiling the ndiswrapper package from source.

---

### Post by ssck on 2005-06-17
[QUOTE=bertimus]Hehe... I'm using GTKWifi.   I've narrowed it down to manually configuring my default gateway device every boot.  Grr....

About the kernel upgrade, I think if you've got wireless working again thru the default ndiswrapper, then all is well.  AFAIK the issue was caused in the first place by manually compiling the ndiswrapper package from source.[/QUOTE]

i suppose you are right.we'll know the next time there is another kernel update :)

---

### Post by bertimus on 2005-06-21
Well, I've finally given up with wireless on Hoary.  There are just too many 'variables' to constantly check on, too many tools to utilize to do so, and too many headaches compared to operating systems that 'just work' with the same hardware.

Linux has come a LONG way since I began toying with it 6 years ago.  It's *almost* there.  So close, I can feel it.

But, wireless headaches aside, I've gone hard-line (it's a desktop, anyway - just had to re-configure my LAN topology a bit) and it's smooth sailing so far.

Perhaps Breezy will make mucking around with wireless configuration a bit more transparent.

---

