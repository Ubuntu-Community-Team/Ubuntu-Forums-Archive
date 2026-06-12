---
title: "Virtualbox 4.1.12 - USB still no show on Guest OS"
date: 2012-08-16
forum: Virtualisation
---

### Post by manuleka on 2012-08-16
Platform:
Ubuntu 12.04
VirtualBox 4.1.12 (incl. Virtualbox-Guest-Additions)
Windows 7 32bit (Guest OS)

Just installed Virtualbox 4.1.12 and Guest-additions from software center

Fired it up and installed Windows 7 32bit
I added usb vbox to my username 

When i ran my Guest there was no internet so i had to change Network to bridged eth0 and that fixed it

Issue:I can add my usb on USB settings for the Guest OS but it wouldn't appear on the Guest... when i go to my computer on Windows 7 there's no extra drive on it

help please... is there some other settings i need to look into to make my USB usable on my Guest?

---

### Post by albandy on 2012-08-16
type id in a terminal and post the result.

---

### Post by manuleka on 2012-08-16
id result:
uid=1000(blakmunky) gid=1000(blakmunky) groups=1000(blakmunky),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),121(sambashare),122(vboxusers)

---

### Post by smartboyhw on 2012-08-16
1. Did you install Guest Additions?
2. Upgrade to 4.1.18.

---

### Post by albandy on 2012-08-16
OK, this look right.

You installed from software center. Let's try directly from oracle:

First remove your virtualbox installation (this will not erase your virtual machine)

then install the oracle ppa:
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

sudo su -c "echo deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib > /etc/apt/sources.list.d/virtualbox.list"

sudo apt-get update
sudo apt-get install virtualbox-4.1

then download the extension pack from oracle:
[http://download.virtualbox.org/virtualbox/4.1.18/Oracle_VM_VirtualBox_Extension_Pack-4.1.18-78361.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.18/Oracle_VM_VirtualBox_Extension_Pack-4.1.18-78361.vbox-extpack)

Open virtualbox and install the extension pack you have downloaded: File --> preferences --> Extensions

reboot your system.

---

### Post by manuleka on 2012-08-16
> **smartboyhw said:**
> 1. Did you install Guest Additions?
2. Upgrade to 4.1.18.

guest additions are on... 

i will try what albandy has suggested... reason i installed the one from software center is because i've installed 4.1.18 before on a LinuxMint 13 Cinnamon and it had same problem

so i thought maybe the version on software center would work better

---

### Post by manuleka on 2012-08-16
realise after installing guest additions i can't copy and paste between the guest and host....


so maybe its a guest addition issue... i'll attempt installing the 4.1.18 soon

---

### Post by albandy on 2012-08-16
> **manuleka said:**
> realise after installing guest additions i can't copy and paste between the guest and host....


so maybe its a guest addition issue... i'll attempt installing the 4.1.18 soon

Did you installed the extension pack?

---

### Post by manuleka on 2012-08-16
> **albandy said:**
> Did you installed the extension pack?

do you mean extension pack for VBox 4.1.12? NO

how would i do that?

i haven't tried installing VBox 4.1.18 yet

thank you, appreciate the help

---

### Post by albandy on 2012-08-16
> **manuleka said:**
> do you mean extension pack for VBox 4.1.12? NO

how would i do that?

i haven't tried installing VBox 4.1.18 yet

thank you, appreciate the help

This may help you:
[http://www.youtube.com/watch?v=XV0kS5gHjtg&feature=youtu.be](http://www.youtube.com/watch?v=XV0kS5gHjtg&feature=youtu.be)

---

### Post by CharlesA on 2012-08-16
See here too:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by manuleka on 2012-08-17
thanks guys... tried the weget -q [http://download](http://download) ... and i get a gpg: non valid OpenPGP data found.

now i tried to follow the debian instructions on [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

but i get a no command deb found... so i'm abit confused now

---

### Post by CharlesA on 2012-08-17
You add:

```
deb http://download.virtualbox.org/virtualbox/debian precise contrib
```

To /etc/apt/sources.list

Then run:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.1
```

---

### Post by manuleka on 2012-08-17
> **CharlesA said:**
> You add:

```
deb http://download.virtualbox.org/virtualbox/debian precise contrib
```

To /etc/apt/sources.list

Then run:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.1
```

thanks worked... i think my earlier failure was due to typo

this installed virtualbox 4.1.12 still and now i'm downloaded extension pack 4.1.18... would they work?

---

### Post by manuleka on 2012-08-17
nope... after reinstalling from Oracle (4.1.12) and installing extensionpack 4.1.18

it seems not to help at all...

i've created a share folder on the host so i use it as a dropbox between host and guess since i can't use my usb :(

---

### Post by CharlesA on 2012-08-17
Uninstall virtualbox and then reinstall the latest version.

---

### Post by manuleka on 2012-08-17
ok will do that now... that would be 4.1.18

---

### Post by manuleka on 2012-08-17
> **CharlesA said:**
> Uninstall virtualbox and then reinstall the latest version.

installed 4.1.18 + ExtensionPack + GuestAdditions 

still no luck :( 

SOS please hehe

---

### Post by manuleka on 2012-08-17
Thanks guys.... FIXED IT 

all i needed to do was enable USB 2.0 Controller --- ???

thank you so much for all your help

---

### Post by smartboyhw on 2012-08-17
> **manuleka said:**
> Thanks guys.... FIXED IT 
 
all i needed to do was enable USB 2.0 Controller --- ???
 
thank you so much for all your help
 Don't forget to change prefix to [solved] .

---

### Post by cforput on 2012-11-20
I know this is a few months old but I'm haveing similar problems. Installed VBOX, Guest Adds, extension pack. Added myself to vbox users but I'm not sure how you enable the USB 2.0 controller. Can someone give me some directions?

I've tried 3 different USB drives. They work fine in Ubuntu. In VBOX, they show up if I click Devices then USB. I put a check mark next to them but still they don't show up in windows. Only my C drive and D: for Guest Adds.

---

### Post by cforput on 2012-11-20
SOLVED AGAIN

I didn't realize that I hadn't checked the 2.0 USB controller. I found the setting and all is working.

---

### Post by pbhj on 2013-05-25
I had to run services.msc in the Guest OS (Win XP) and enable "plug and play". Microsoft instruct that a reboot is then necessary but it worked for me without. The device manager was then used and it showed that the USB drive was in an error state, selected it and chose to update the driver and used the internet to do automatic update. Worked from then on, no reboots.

---

### Post by Timmy0829 on 2013-05-27
I have the same error. I have everything what i need ticked in and so on. But when i have to add which usb i want to use, nothing is coming up, like i dont have anything plugged in.... But I have usb 3.0 in my laptop. Can that be a problem? Because I can just enable usb 2.0 in the settings....

---

