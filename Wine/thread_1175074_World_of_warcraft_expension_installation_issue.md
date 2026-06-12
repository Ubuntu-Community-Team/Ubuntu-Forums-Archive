---
title: "World of warcraft expension installation issue"
date: 2009-05-31
forum: Wine
---

### Post by gimpy42 on 2009-05-31
I tried to install burning crusade by copying the dvd on my hard drive like the fist dvd original one but it doesnt work...

I have the worl of warcraft original installed

And I fallowed that tread ;
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

so when i start the process for the second DVD 
First when i umount my DVD and try to mount it without hidden files it shows me that:

sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and the other thing i tryied is to copy directly the file from the DVD to my hard drive and it shows me that:

Error while copying.

The folder "DirectX" cannot be handled because you do not have permissions to read it.

And if I try to change permission it doesnt change anything...

Im on ubuntu 9.04 could try to help me solve that problem?

EDIT:
I find how to copy the file on my computer by that command;
sudo cp -r /media/cdrom0* /home/gimpy/Desktop/burning/

but when i do wine Installer.exe it shows me that:
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
wine: could not load L"Z:\\home\\gimpy\\Desktop\\burning\\cdrom0\\Installer.exe": Module not found



PS: sorry if i dont write proprely im french and it not easy ;)

---

### Post by NightMKoder on 2009-05-31
I think your disk is the problem. Consider just downloading the game from blizzard's website. Might be slow, but itll definitely work.

---

### Post by gimpy42 on 2009-05-31
snif i took the downloader manager ... i click to install burning crusade but the button agre never show up even if i scroll down i will post to them if they can solve the problem of that

---

### Post by hikaricore on 2009-05-31
WINE version?

This was a bug awhile back that has since been resolved.

---

### Post by gimpy42 on 2009-05-31
I think the version is 1.0.1... any way i don see any upgrade of it on download manager ;s

---

### Post by hikaricore on 2009-05-31
There's a sticky about how to update..

Here's direct link to the info: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

