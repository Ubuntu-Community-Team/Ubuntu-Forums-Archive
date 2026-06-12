---
title: "A few questions regarding recently completed server build"
date: 2009-01-23
forum: Server Platforms
---

### Post by Chris of Arabia on 2009-01-23
I've finally got my LAMP server (home network - not publically accessible) to the state where I more or less want it (8.04 LTS server with KDE desktop added), but over the course of getting it where I want it, I've accumulated a few questions and minor issues that I'd now like to tidy up. In no particular order then:

[LIST=1]
[*]When working directly on the server box, if I try to log out [K Menu | Log Out... | Log out], rather than return me to a log in screen, the display just goes black and displays nothing. Anyone have any suggestions as to what might fix this.
[*]When creating my base build, I set it up on with the soft-RAID 0 on a pair of 500Gb disks using this tutorial as a guide - [Setting up software RAID in Ubuntu Server]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") - Whilst the RAID itself is set-up quite nicely, one of the recommended steps is in regard to "Making every drive bootable". I wasn't able to complete that one though as on each attempt to load the "Rescue a broken system", I'd get a message saying that it was unable to load the drivers for the CD-ROM drive. No amount of drive swapping (whether IDE or SATA) would get the rescue software installed. SO I stil remain with the MBR available on only one f the two disks. At the moment, with it all being a fairly newly constructed box, it isn't really something that's likely to trouble me in the near future, I would though like to tidy this up to prevent the inevitable. Any suggestions?
[*]Like many I suspect, I used this tutorial - [The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") - as a guide to build it. I did though ignore the instruction to install the LAMP components individually , but I did set a '*root*' password and disabled '*apparmor*'. Given that I now recognise that neither of these are necessarily a good step, what would be the best approach to rectifying this?
[*]Finally, for the moment, I set-up '*vsftpd*' without too many problems, but in order to allow FTP access to /var/www, I had to change that folders ownership to a group containing 'administrator' and another test user I created an account for. This allowed me to drop files in and out of that folder as desired, but in doing that the files I'm putting in there (mainly PHP) pick up that ownership and won't run when called remotely. It's easy enough to extend the privilages to 'Group' and 'Others' as needed after I've FTP'd them across, but it's a bit of a PITA to do with every file I put in there. This is obviously something to do with the folder ownership, but I'm not sure the best way of configuring the permissions to allow access via FTP whilst giving remote users access from their browsers. Any suggestions?
[/LIST]
Any feedback on the above would be appreciated.

---

### Post by HavocXphere on 2009-01-23
1. I'd guess this is a gfx driver issue. i.e. its loading the login screen, but not displaying it. Try typing in your password anyway. For some reason, the login screen sometimes uses a different gfx config than the main desktop. e.g. different res & refreshHZ. Not exactly sure where each one is controlled though.

2. I'd guess the "Making every drive bootable" thing only works on raid 1. Anyway, since raid 0 is striped, if one of the two drives fail, all is lost anyway...with or without multiple MBRs. Remember to do them Backups regularly.;)

3. & 4. Not sure.

---

### Post by Chris of Arabia on 2009-01-23
My mistake, I meant RAID 1

I tried what you suggested on item 1, but it just sat there ignoring me, so I had to resort to the usual option of a hard re-boot.

---

### Post by Iowan on 2009-01-23
Depending on how **apparmor** was disabled, you should be able to re-enable it.  My server has a root account - I also built it from a "Perfect Server" article.  Although you can (re)disable root login - or give it a "dummy shell", I prefer to just leave it alone.  **sudo** still works like it did.

---

### Post by Chris of Arabia on 2009-01-24
OK, item 3 is sorted.

Any more offers on the others?

---

