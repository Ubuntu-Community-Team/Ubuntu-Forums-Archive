---
title: "Check for iso integrity downloaded from Microsoft for support on client machines that"
date: 2018-02-08
forum: Windows
---

### Post by espectro2 on 2018-02-08
When a client  has a computer with windows pre installed this iso image that came from  the factory even formatting reset restoring system does not work well ie  windows does not work well with iso that came from factory as I can  check the integrity of microsoft iso in ubuntu to know if there was no violation in the downloaded iso image?
How to check the integrity of iso windows on Ubuntu.
Thanks for listening.

---

### Post by wildmanne39 on 2018-02-08
*Thread moved to **Windows, a more appropriate forum**.*

---

### Post by Habitual on 2018-02-09
In Ubuntu terminal,
```
sudo md5sum /path/to/file.iso
``` and press enter
Minutes later...google the hash md5sum gives you. 


Verification is another story.
Get it from MS directly?

---

### Post by Frogs Hair on 2018-02-09
Keep in mind this is probably an OEM supplied ISO and could include software not native to Windows. It's likely only the OEM could provide the ISO checksum.

---

### Post by espectro2 on 2018-02-09
technically  I have a client with windows installed already I made recovery process  through the manufacturer's recovery to do a clean installation I can  download an iso do the installation can not?
my  doubt is with microsoft iso in ubuntu how to check for integrity ie if  Iso was not corrupted during download do this with an ISO windows using  ubuntu?

---

### Post by espectro2 on 2018-02-09
in case with this command I can check the integrity of an iso already recorded on DVD in case I already downloaded and already recorded in the mediaI do not think it should be changed from topic I want to check an iso image of windows inside ubuntu I use ubuntu 16.04Thanks for listening
after downloaded iso how to confirm integrity if there was no iso violation during download?


 this command resolves sudo md5sum /path/to/file.iso
[https://www.microsoft.com/pt-br/software-download/windows10ISO](https://www.microsoft.com/pt-br/software-download/windows10ISO)
[https://answers.microsoft.com/en-us/windows/forum/windows_tp-winipp/is-there-built-in-checksum-for-win-10/8dba82be-f036-4460-b427-954e057b678a?auth=1](https://answers.microsoft.com/en-us/windows/forum/windows_tp-winipp/is-there-built-in-checksum-for-win-10/8dba82be-f036-4460-b427-954e057b678a?auth=1)

---

### Post by yancek on 2018-02-10
Verifying an iso on Ubuntu or Linux was explained to you in post #3 above.  That command, run properly will produce an md5sum which you then compare to the md5sum for that specific iso file which is going to be available from and on the microsoft site and nowhere else.

---

### Post by espectro2 on 2018-02-10
I understood this command
sudo md5sum /path/to/file.iso
thanks for listening

---

### Post by deadflowr on 2018-02-10
You should be able to run checksums without root or sudo on any file that's readable by you normally.
Example: I can run without root to see the hash for my .conkyrc file
```
sha256sum .conkyrc
befddf2b16e4e2b380ed100f36ee8bfb0eccc0328fe95d1245e85c665602599b  .conkyrc
```

but if I try a checksum on a file that requires root to view then i get something this:
```
sha256sum /etc/shadow
sha256sum: /etc/shadow: Permission denied
```
(I used the shadow file since that's a known file that is only readable by root.)

Even though I used sha256sum, the same applies to any checksum.

---

