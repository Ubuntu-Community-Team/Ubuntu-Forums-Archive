---
title: "Setting up home server, lots of questions"
date: 2008-05-16
forum: Server Platforms
---

### Post by BuRn_sLuG on 2008-05-16
Hey guys,

Have been using Ubuntu for a while now, both on my laptop (primary PC) and my desktop (now my server). I have been wanting to set up my desktop to be used as a server for use with my laptop, but have quite a few specific requirements. The server will stream all media to the laptop, as well as being the primary place where all my work and media is saved, and backups are stored. Here goes...

[B]The Server;
[/B]
AMD 4200+, 2GB RAM, 250GB Storage (Will be upgraded to 2 x 1 Terabyte drives later on).

Wanting the server to be _completely_ headless, administered via ssh. Will have 2 partitions, a "/" (25GB), the rest "/media". Will not be using a swapfile as 2GB of RAM will suffice. Need to have as much of the filesystem encrypted as possible (strong encryption ONLY, I have used Truecrypt, but cannot do full disc encryption with it). 

The server connects to the laptop directly via a crossover cable. I have set up the server's eth0 IP, Subnet and default gateway to match that of eth0's on the laptop (with the default gateway being the laptop's LAN IP). 

I currently have an NFS set up with /media (on the server), but it is unencrypted. To access the server currently, I would ssh into it from the laptop, and to mount the media I would use "sudo mount XX.XX.XX.XX:/media /sharedmedia". 

Bear in mind that the laptop connects to the internet through Wifi, as does the server. I need to have the server connected to Wifi at boot, so it can update programs when needed (note that the data shared between the laptop and server will go via the crossover cable, however, due to Wifi being slow).

So the questions I have;
[LIST]
[*]How can I setup full disc encryption on the server (Can format, and have access to 8.04 Alternative)?

[*]Can the disc encryption be decrypted through ssh to be mounted as an NFS?

[*]Is it possible to have the server connect to the Wireless router at boot time (the password will need to be stored encrypted, which I believe can be done if I can encrypt the entire filesystem)?

[*]What is the bare minimum software you would recommend having on the server?
[/LIST]

Thanks in advance (because you guys are awesome :KS).

---

### Post by hyper_ch on 2008-05-16
> **BuRn_sLuG said:**
> How can I setup full disc encryption on the server (Can format, and have access to 8.04 Alternative)?
Well, with full disc encryption you will "uncrypt/make transparent" the data during boot up, so I'm not sure if that's what you're looking for...
an option I see is to have an unencrypted system and once that runs you can mount the encrypted one as root and also encrypt swap... however I've never tried to mount an encrypted filesystem as "/" on a running computer....

> **BuRn_sLuG said:**
> Can the disc encryption be decrypted through ssh to be mounted as an NFS?
It can :) but when you are so keen on encryption, why not using SSHFS instead of NFS?

> **BuRn_sLuG said:**
> Is it possible to have the server connect to the Wireless router at boot time (the password will need to be stored encrypted, which I believe can be done if I can encrypt the entire filesystem)?
As said, on a fully encrypted system you'll need to enter the password at boot up to uncrypt the root partition.... wifi password will be stored there so it's encrypted....

> **BuRn_sLuG said:**
> What is the bare minimum software you would recommend having on the server?
Install from the server cd, add openssh-server and add the rest on a "per need basis"...

---

### Post by BuRn_sLuG on 2008-05-16
Thanks for the response, so I would setup encryption [_like so?_](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/) Does the server CD install just like alternative? And how strong is the encryption used in this method? Truecrypt (AES etc) strong?

---

### Post by hyper_ch on 2008-05-16
You can use the server cd to setup a fully encrypted system also. There are different cyphers which you can select, when you select manual encryption... dunno what it will chose when you select guided encrypted...

---

### Post by nineowls on 2008-05-16
> **hyper_ch said:**
>  ...using SSHFS instead of NFS...

definitely use sshfs

---

### Post by BuRn_sLuG on 2008-05-17
Have successfully installed the server and setup encrypted filesystem.

Server can ping my notebook and "iwconfig" returns wlan0 as being up (so it supports my card). However, I am not sure how I would go about connecting to my WAP via a command line. Can anyone help me with this? 

If this is not possible, would I be able to use my notebook as a DNS server for my server, so that my server can update? And if so, how would I go about doing that (only if I cannot connect to the WAP via command line and if it is a better option).

Thanks for the input so far guys.

---

### Post by hyper_ch on 2008-05-17
what encryption do you use on the access point?

---

### Post by BuRn_sLuG on 2008-05-17
Wpa2-psk

---

### Post by hyper_ch on 2008-05-17
you have another (linux) computer that use wpa2-psk and which is connected?

---

### Post by BuRn_sLuG on 2008-05-17
Yes, my notebook.

---

### Post by hyper_ch on 2008-05-17
not sure about wpa stuff.... but I'd try this:

(1) in the notebook copy and paste
/etc/network/interfaces
(I assume it's all dhcp there)

(2) in the server
- find out what the wifi interface is called by issuing ifconfig (it's wlan0 I think)
- edit /etc/network/interfaces and paste there the info you have from the notebook.. just make sure, the wifi device is right...

(3) in the server
- restart the network by issuing
```

sudo /etc/init.d/networking restart

```

---

### Post by BuRn_sLuG on 2008-05-18
Unfortunately there was nothing in my notebook's /etc/network/interfaces relating to the WAP (or wlan0 for that matter). Does anyone know how to set it up for the server?

---

### Post by hyper_ch on 2008-05-18
oh well... I don't encrypt my wifi at all...

---

### Post by BuRn_sLuG on 2008-05-20
Does anyone have a solution for this?

---

### Post by eniacpx on 2008-05-20
Start here:
[http://wiki.archlinux.org/index.php/Wpa_supplicant](http://wiki.archlinux.org/index.php/Wpa_supplicant)

You might be able to use wpa_supplicant and the included wpa_cli tool to make your wireless connection. 

This is an interesting project and I am very eager to see the outcome!

---

