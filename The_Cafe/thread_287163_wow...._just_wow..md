---
title: "wow.... just wow."
date: 2006-10-28
forum: The Cafe
---

### Post by Polygon on 2006-10-28
Ok... so i decided to upgrade to edgy this weekend. Kinda bad idea...

i did the "gksu update-manager -c" command. It worked well enough, except it downloaded at appro 10-15 kb/s... it would of finished in like a day. So i searched for other mirrors and i found some faster ones that averaged at around 30-40 kb/s.  It installed... and i was told to restart the computer

uh oh! 

when i restarted i got some weird error saying that fsck died with error status 8 and it couldent resolve some UUID thing....

so i popped in my edgy live cd to backup all of my stuff as i was planning on doing a fresh reformat later this week anyway and i installed edgy using the live cd

This part was kinda my fault, i had to do a little dance with grub since i didnt format my /boot partiton and it still had some old paths in there that were incorrect and it couldent find the kernel images.

But then even then after i got that fixed. it STILL gave me this fsck died with error status 8.... but when i actually got dropped down to the cli and i typed reboot, it dropped me to the GUI login screen.

so i tried to login and and it gave me some weird error that it couldent find my home folder and a bunch of other stuff, so i said "screw this" and loaded my dapper live cd and reinstalled dapper.

I dunno if this is a problem with just my computer, but i defenitly felt "edgy" today.

---

### Post by .t. on 2006-10-28
Bad luck. Always been good news for me. Just started using the Feisty repos earlier, so I'm waiting for something more than a base-files update, but I don't expect that sooner than after UDS Mt. View.

---

### Post by ~LoKe on 2006-10-28
Sup Poly.

I would suggest a clean Edgy install.  It's not meant to be a "stable" distro, but it works pretty damn well.  You could try doing another dist-upgrade, chances are you just had bad luck.

---

### Post by fuscia on 2006-10-28
i had problem with the upgrade, so i ended up doing a clean install, as well, and it's all rosey and good.

---

### Post by KaroSHi on 2006-10-28
I too had problems when trying to upgrade, i will be waiting a while after reading this thread. Good luck to all with problems!

---

### Post by Steveire on 2006-10-28
Did you read the bit about pressing control-D to continue boot?
[http://ubuntuforums.org/showthread.php?t=272763](http://ubuntuforums.org/showthread.php?t=272763)
Install/upgrade again without dancing with grub should sort you out. If you get the same situation, edit fstab to use /dev/hdax instead of the UUID for the boot(or other problem) partition. UUIDs are quite useful I understand, but dancing around with partitions and that seems to break them.

That might also explain why you couldn't get to your home folder etc also.

---

