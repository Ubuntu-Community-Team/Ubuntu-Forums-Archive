---
title: "help installing Debian through Sun xVM"
date: 2008-08-09
forum: Virtualisation
---

### Post by eival on 2008-08-09
ive already successfully installed windows xp thorugh the VM a few weeks ago, an now i wanted to try out some more os' so i ran the manager it asked if i wanted to install in my current vdi(which already has windows) or create a new one(i didnt see any prompts telling me 2 os' in the same virtual hdd would conflict/cause problems) so i chose to use the current one.

i then set up everything teh same way as i had windows
Base - 900mb ram
Virtual - 50mb
boot order - cd-rom,harddisk
ACPI - enabled
IDE Primary master - linux.vdi [Normal 10.00GB]
CDROM host drive - mounted
Network adapter - enabled

i then put in my CD-R with debian 4.0r4(the latest version which i downloaded strait from debian.org) and ubuntu read/opened it up so i know the iso file was burned properly.

i then started my new debian vdi and after the initial SUN boot screen i got this

FATAL:no bootbable medium found! system halted.

im assuming what its trying to tell me is that there is no os isntalled? but i assumed just like with ubuntu and windows i would get a prompt to "press any key to boot from cd"

or my only other thought is perhaps its cause i have it installed in the same vhdd as windows?


im using Ubuntu Hardy 8.04 32bit

---

