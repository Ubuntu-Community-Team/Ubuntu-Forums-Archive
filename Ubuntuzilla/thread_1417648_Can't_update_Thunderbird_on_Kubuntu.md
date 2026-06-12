---
title: "Can't update Thunderbird on Kubuntu"
date: 2010-02-27
forum: Ubuntuzilla
---

### Post by linuxwizard on 2010-02-27
Used Ubuntuzilla to install Thunderbird 3 on Kubuntu 9.10 and LinuxMint 8 KDE both system can not update Thunderbird 3.0.1 to 3.0.2. Shows no update available. Using lastest version of Ubuntuzilla 4.8.3. To check for updates I used kdesudo thunderbird &.I think I ran into to this issue before back on Feisty or Gusty Kubuntu but can not remember what I did to fix it so I could update. Ubuntu 9.10 updated with no issues using Ubuntuzilla.

---

### Post by nanotube on 2010-02-27
> **linuxwizard said:**
> Used Ubuntuzilla to install Thunderbird 3 on Kubuntu 9.10 and LinuxMint 8 KDE both system can not update Thunderbird 3.0.1 to 3.0.2. Shows no update available. Using lastest version of Ubuntuzilla 4.8.3. To check for updates I used kdesudo thunderbird &.I think I ran into to this issue before back on Feisty or Gusty Kubuntu but can not remember what I did to fix it so I could update. Ubuntu 9.10 updated with no issues using Ubuntuzilla.

Hi,
no idea why that may be... if you're using 32bit OS, then I suggest you start using the new ubuntuzilla repository rather than the installer script. 

see the documentation on [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by linuxwizard on 2010-02-27
Hi nanotube
Yes I am using 32 bit. I know I had this issue before. Been using Ubuntuzilla since Dapper on just about every version since. But the issue has only showed up on Kubuntu with Thumderbird never on Ubuntu. I can't remember what I did to fix it so it will update. I thought you might know what to do. Guess I will just uninstall Ubuntuzilla version of Thunderbird than reinstall Thunderbird to home or opt.

---

### Post by nanotube on 2010-02-27
> **linuxwizard said:**
> Hi nanotube
Yes I am using 32 bit. I know I had this issue before. Been using Ubuntuzilla since Dapper on just about every version since. But the issue has only showed up on Kubuntu with Thumderbird never on Ubuntu. 

well, the only reason it won't show up in thunderbird's 'check for updates' function is if the update hasn't yet been pushed out to the mozilla update queue... nothing that ubuntuzilla can do about it from the outside.

> 
I can't remember what I did to fix it so it will update. I thought you might know what to do. Guess I will just uninstall Ubuntuzilla version of Thunderbird than reinstall Thunderbird to home or opt.

if you use the ubuntuzilla repository, you don't have to install manually. just add the ppa repo line, and install the appropriate package.

---

### Post by linuxwizard on 2010-02-27
I know the update has already been released from Mozilla because I update my Ubuntu 9.04, Ubuntu 9.10, and Xubuntu 9.10 a couple days ago using Ubuntuzilla for Thunderbird. I don't add extra repo to my source list beside I don't see where that would fix issue, since I see Ubuntuzilla update notifier telling me to update but it will not let me. I already removed/uninstall Ubuntuzilla Thunderbird and installed Thunderbird to /opt so I can control update. Thanks for help and input

---

### Post by nanotube on 2010-02-28
> **linuxwizard said:**
> I know the update has already been released from Mozilla because I update my Ubuntu 9.04, Ubuntu 9.10, and Xubuntu 9.10 a couple days ago using Ubuntuzilla for Thunderbird. 

hrm, weird...

> 
I don't add extra repo to my source list beside I don't see where that would fix issue, since I see Ubuntuzilla update notifier telling me to update but it will not let me. 

the ubuntuzilla repo contains actual thunderbird packages, and the current thunderbird version in the repo is 3.0.2. so it would have helped. :)

> 
I already removed/uninstall Ubuntuzilla Thunderbird and installed Thunderbird to /opt so I can control update. Thanks for help and input

well, whatever works is good. ;) cheers!

---

