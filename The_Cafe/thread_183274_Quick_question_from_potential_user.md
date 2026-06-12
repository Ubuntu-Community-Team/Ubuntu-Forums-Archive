---
title: "Quick question from potential user"
date: 2006-05-27
forum: The Cafe
---

### Post by Michael_aust on 2006-05-27
I have a few questions, im not new to Linux I have been running straight Debian for almost a year now, but am yet to try out Ubuntu.

The situation is I am intending to install xubuntu when it is released as stable on the 1st as my sisters machine is not exactly modern, and the xfce desktop would fit nicely for it.  She uses a dlink dwl-g122 b version, it uses the RT2500 chipset wireless usb stick to connect to my router downstairs.  I see from the wiki that as of the breezy release the RT2500 driver is already included in the kernel, so it should work out of the box.

Now my question is, will xubuntu include a gui network configuration tool because I see from th wiki they are trying not to include and gnome specific application in order to cut down on memory usage.  If such a gui tool is included in the stock install, would I be able to configure wpa from it or would it just be wep and for wpa I would have to to the command line?

My second question is, I have never ever attempted to set up a wireless networking device on a Linux desktop, would ubuntu auto connect with the router each time the machine starts, or would I need to use the gui to enable the connection on each boot or the command line etc?  If not would there be a way to anable it, writing a shell script or something?

I have only just decided that Linux should go on the machine as windows ME has magically corrupted its self so that you cannot shut it don from within its self.

Any answers on the the questions abouve would be greatly appreciated.

Thanks in advance

Michael.

note:  If this is posted in the wrong section, I appologise, please feel free to do as ou deem appropriate with the thread.  This seemed like a logical place to put it from looking at the forum catagories.

---

### Post by SteveHoffmanUK on 2006-05-27
I'm a newbie, so can't answer most of your questions, but regarding the wireless connection, I have Ubuntu Dapper Duck beta installed on an ageing Dell laptop, using a Belkin wireless PCMCIA card, linked to two Windows XP machines via a wireless router/ADSL modem, and it connects automatically as soon as I log in. I can "see" both XP machines and access their files (read-only of course because they're NTFS systems). Works a treat. If I can do it, I'm sure you can with your Debian experience.

---

### Post by IYY on 2006-05-27
> Now my question is, will xubuntu include a gui network configuration tool because I see from th wiki they are trying not to include and gnome specific application in order to cut down on memory usage. If such a gui tool is included in the stock install, would I be able to configure wpa from it or would it just be wep and for wpa I would have to to the command line?


I'm not sure, but I know that if you'll need to install it you can do so without installing gnome. The GUI allows configuration of wpa.

> My second question is, I have never ever attempted to set up a wireless networking device on a Linux desktop, would ubuntu auto connect with the router each time the machine starts, or would I need to use the gui to enable the connection on each boot or the command line etc? If not would there be a way to anable it, writing a shell script or something?

It should autoconnect (mine does). I'd just try the LiveCD if I were you.

---

### Post by Michael_aust on 2006-05-27
thanks for the reply, so it conencts on log in then.  Its about time i gave ubuntu a try.

---

### Post by Super King on 2006-05-27
There actually is a Xubuntu-specific network tool (xubuntu-system-tools) but last time I tried a live CD of Xubuntu they didn't have it installed by default (you needed a network connection to install it, which sucks).

---

