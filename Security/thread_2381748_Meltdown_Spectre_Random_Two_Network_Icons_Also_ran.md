---
title: "Meltdown? Spectre? Random Two Network Icons? Also random accounts."
date: 2018-01-05
forum: Security
---

### Post by xRedex on 2018-01-05
Hi there everyone. 

I had installed lubuntu onto a usb stick  using the latest artful aardvark .iso from lubuntu.me, & universal  USB installer from pendrivelinux.com.
When I booted the usb stick,  there was only one network icon. Next I wanted to use that usb to  install lubuntu onto a netbook that a friend had, because windows was  slow.
I booted to lubuntu ( still one network icon ) and pressed  install. It started installing to the usb stick because linux would not  see the harddrive.

Next, I canceled the installation, & shut  down the netbook. I then tried booting up the netbook again, and it had  an error. This is when I noticed accounts there that I was unsure of.

Here's a list of them:

Invalid-user: ssl-cert
root:root
Root:shadow
Lubuntu
Lubuntu.lubuntu

Sudo: unknown uid: who are you?

I'm wondering because I didn't root this distro & because of how many there were.

I  had to re-install lubuntu on the usb drive because of the error. I did  this the next day using the same .iso and usb drive installer.
When I did this, and booted up, it suddenly had two network icons instead of one. Both show the different wireless networks.
I  then deleted the lubuntu.iso & universal usb installer on my  computer, & re-downloaded them. This time when I booted up, it had  one network icon.

I got lubuntu to install to the hard drive. It  had one network icon for a couple days. ( It didn't have internet at all  because it wouldn't connect. )

My friend said that when they  were typing their book on the netbook, it gave an error, and started  typing random gibberish into abword.

After that happened, it had two network icons again.

Can someone explain to me why this happened?

Do  you know if it has anything to do with the meltdown, & spectre  vulnerabilities in intel, amd & arm processors that was in the news?

I don't think it should have two network icons.

Thanks! I hope that you guys can help. =)

---

### Post by patrickscarroll on 2018-01-05
If you are worried about those vulnerabilities than you should run Windows as it is patched there,  Ubuntu patches are still in development.

---

### Post by CharlesA on 2018-01-05
> **patrickscarroll said:**
> If you are worried about those vulnerabilities than you should run Windows as it is patched there,  Ubuntu patches are still in development.

True, but you'll have to track them down, which is fairly easy via Google. Otherwise they'll be officially released on patch Tuesday via Windows Update.

As far Ubuntu, you can find up-to-date info here: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown)

This doesn't really sound like a compromise to me, more like funky hardware support, especially if the network interface isn't working.

---

### Post by Habitual on 2018-01-05
> **xRedex said:**
> Hi there everyone. 

I had installed lubuntu onto a usb stick  using the latest artful aardvark .iso from lubuntu.me, & universal  USB installer from pendrivelinux.com.
When I booted the usb stick,  there was only one network icon. Next I wanted to use that usb to  install lubuntu onto a netbook that a friend had, because windows was  slow.
I booted to lubuntu ( still one network icon ) and pressed  install. It started installing to the usb stick because linux would not  see the harddrive.

Next, I canceled the installation, & shut  down the netbook. I then tried booting up the netbook again, and it had  an error. This is when I noticed accounts there that I was unsure of.

Here's a list of them:

Invalid-user: ssl-cert
root:root
Root:shadow
Lubuntu
Lubuntu.lubuntu

Sudo: unknown uid: who are you?

I'm wondering because I didn't root this distro & because of how many there were.
Did you try to sudo during an install-but-canceled session?
Don't see any UIDs I'm afraid :)
Sounds like you partially installed to the local hard drive.

---

### Post by poorguy on 2018-01-05
I'm curious are these fixes just going to be for 64 bit users or will these also cover 32 bit users also or is it still to soon to know.

---

### Post by Frogs Hair on 2018-01-05
> **poorguy said:**
> I'm curious are these fixes just going to be for 64 bit users or will these also cover 32 bit users also or is it still to soon to know. Only 64 Bit was addressed at the link below.


[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)

---

### Post by poorguy on 2018-01-05
> **Frogs Hair said:**
> Only 64 Bit was addressed at the link below.


[https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/](https://insights.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities/)

Kinda what I thought.

I may wait a couple of weeks and see before I install more ram and install 64bit Lubuntu 16.04.

Thanks Frogs Hair.

---

