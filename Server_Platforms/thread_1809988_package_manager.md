---
title: "package manager"
date: 2011-07-22
forum: Server Platforms
---

### Post by DeepakAnandani on 2011-07-22
while trying to open synaptic package manager
i get the following errer

 "E: The package clamav-daemon needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

i m providing u with a screen shot plzz help me with the problem

[ATTACH]198079[/ATTACH]

---

### Post by DeepakAnandani on 2011-07-24
hey.... any1 der to solve ma problem.....
plzzz... help me out..... i m new to ubuntu...........

---

### Post by Gyokuro on 2011-07-24
you can try to run sudo apt-get clean && apt-get update && apt-get upgrade

---

### Post by DeepakAnandani on 2011-07-25
thankx.... i tried the command provided by u....
they error is still der....!!!!

root@ubuntucserver:~# sudo apt-get clean && apt-get update && apt-get upgrade
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package clamav-daemon needs to be reinstalled, but I can't find an archive for it.
root@ubuntucserver:~#

---

### Post by Gyokuro on 2011-07-25
Hi,

it seems your mixing lucid with maverick - can you please post your /etc/apt/sources.list ? Either go with lucid or maverick - do not mix them together.

---

### Post by DeepakAnandani on 2011-07-25
the problem was solved  by doing some changes in ''source.list''
file... plzz note this problem as solved... i m providing u with the information what changes i have made......

i took a back-up of ''source.list'' file..... and replaced the whole file with the following,.....


First try to set your sources server (from update-manager) to use the main server... and retry...
 if still don't works please
made a backup copy of your actual sources.list file and then
try to put some as my standard /etc/apt/sources.list
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) naverick-updates main restricted universe
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse main universe restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse




problem is solved....:guitar:

---

