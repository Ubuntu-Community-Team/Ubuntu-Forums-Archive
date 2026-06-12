---
title: "install ubuntu eee"
date: 2008-12-25
forum: The Cafe
---

### Post by myusername on 2008-12-25
i got an eee for christmas. and its XP i wanna install ubuntu (btw which is better? ubuntu-eee or eeebuntu?) but i dont have a portable cd drive and i have a usb drive thats only 256mb. is there any way to install it?

---

### Post by easybake on 2008-12-25
First of all congrats I'm sure you're really going to like it.

You are really hurting your options with only having a 256mb flash drive. Both eeebuntu and Ubuntu-eee core installs are over 500mb. 

You have a few options. You could do a Wubi install but you are going to suffer some cpu usage from it.
 
You could also just do a [Minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") which I bet you could use with Unetbootin.

As for which one is best, I'm am pretty sure you would be safe with either one. I even did a standard Ubuntu install using Unetbootin (on an Aspire One which I'm typing on right now) and only had to do some minor tweaking.

---

### Post by dominiquec on 2008-12-25
I'd recommend Ubuntu-Eee ([http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)).  Already sold my EeePC 4G but prior to that I had Ubuntu running on it.

Consider buying at least a 1GB flash drive, though.  It's not that expensive anymore (here in the Philippines, 1GB is around $3.)

---

### Post by BigSilly on 2008-12-25
I tried Ubuntu-EEE but couldn't get it to install. Kept getting an initramfs error and a busy box. As it turns out, it was a good thing, as I discovered [EEEBuntu]("http://www.eeebuntu.org/") afterwards and it's a revelation. It's based on Intrepid and the Netbook Remix, and the latest iso only came out about a week or so ago.

We just got a 701 for the youngest for Christmas, and after not having much joy accessing the wireless router with the Xandros that comes pre-installed I decided it had to go. EEEBuntu is a way superior choice for the Eee imho. Please give it a try. I reckon you'll love it. My daughter's absolutely thrilled with it, and even though she's only 9 she's pretty Ubuntu-literate. If she can use it, so can you!

---

### Post by billgoldberg on 2008-12-25
> **myusername said:**
> i got an eee for christmas. and its XP i wanna install ubuntu (btw which is better? ubuntu-eee or eeebuntu?) but i dont have a portable cd drive and i have a usb drive thats only 256mb. is there any way to install it?

I installed eeebuntu on mine eeepc 900 and it works really well.

Xp on my eeepc was unusable.

After installing a few apps, xp was constantly complaining it didn't have enough space.

I used an external hdd to install it.

If you have one of those, make a new partition, format as fat32 using gparted and add a boot flag.

Use unetbootin to copy the iso to the partition.

Boot the asus for usb and install as usual.

--

A one gb usb drive goes for 10 bucks.

--

After isntalling (eee)ubuntu(-eee), there is a good guide on tombuntu.com for tweaking it for ssd drives.

---

### Post by myusername on 2008-12-25
thanks for all the suggestions guys. i bought a 2gb jump drive so i have eeebuntu installing now

---

### Post by I-75 on 2008-12-25
> **myusername said:**
> thanks for all the suggestions guys. i bought a 2gb jump drive so i have eeebuntu installing now

Keep us posted and let us know how it all works out...

---

### Post by myusername on 2008-12-25
actually everything on the 904HA model works out of the box. except the extra keys. eeebuntu is great except it replaced the whole desktop folder to just my home folder. so everything in my home folder is shown on the desktop. its really annoying. can someone tell me how to turn it off?

---

### Post by billgoldberg on 2008-12-25
> **myusername said:**
> actually everything on the 904HA model works out of the box. except the extra keys. eeebuntu is great except it replaced the whole desktop folder to just my home folder. so everything in my home folder is shown on the desktop. its really annoying. can someone tell me how to turn it off?

I don't really know, try making a new "Desktop" folder in home and log out and back in to see if that fixes things.

Or use something else to manage your desktop (like compiz fusion, there are others).

---

### Post by Sand &amp; Mercury on 2008-12-25
> **myusername said:**
> actually everything on the 904HA model works out of the box. except the extra keys. eeebuntu is great except it replaced the whole desktop folder to just my home folder. so everything in my home folder is shown on the desktop. its really annoying. can someone tell me how to turn it off?
Makde a new Desktop folder in your home directory. Then Alt-F2 and run 'gedit ~/.config/user-dirs.dirs', make sure you've got 

XDG_DESKTOP_DIR="$HOME/Desktop"

there. Right now yours probably looks like 

XDG_DESKTOP_DIR="$HOME/"

Log out and in again and you should be right again.

---

