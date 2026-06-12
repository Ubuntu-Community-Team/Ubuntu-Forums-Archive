---
title: "dell inspiron security related question"
date: 2011-04-17
forum: Security
---

### Post by werty2010 on 2011-04-17
on the bios of my dell inspiron i have the option among others to set a password on my hdd.
so my questions are:
which exacly is the point of this?
does it encrypt my hdd in any way?
if someone has physical access on my computer and takes out the hdd,could he gain access?

im a regular home user but im very curius to know

---

### Post by Joe of loath on 2011-04-17
according to the manual for mine, it works at a bios level, so doesn't encrypt the data, but should stop it from being mounted by the bios.

not sure if it's good enough to be relied on, though.

---

### Post by Rubi1200 on 2011-04-17
> if someone has physical access on my computer and takes out the hdd,could he gain access?
I believe the answer to that is yes. Physical access = root access, but others may know more.

---

### Post by werty2010 on 2011-04-17
thank you for the replies
but an opinion from a more experienced user would be welcome too...

---

### Post by dfreer on 2011-04-17
Are we sure that this isn't the BIOS password (reworded different), and actually a password for the hard drive?

---

### Post by DodgeV83 on 2011-04-18
> **werty2010 said:**
> on the bios of my dell inspiron i have the option among others to set a password on my hdd.
so my questions are:
which exacly is the point of this?
does it encrypt my hdd in any way?
if someone has physical access on my computer and takes out the hdd,could he gain access?

im a regular home user but im very curius to know

It does not encrypt your hard drive.

It is different than the normal bios boot hard drive.

If someone has physical access, and you haven't enabled the Ubuntu home drive encryption, all of your files will be immediately accessible.

The point?  You can set it to require two different passwords (the normal boot password and the hard drive password) to start the computer up. If someone only has the first password, but not the HD password, they can boot to CD or USB, but not your HD.

I'm not sure if omitting the HD password will prevent the HD from being mounted from a Live-CD, but I doubt it.

Long story short, encrypt the drive.

---

### Post by werty2010 on 2011-04-18
> **DodgeV83 said:**
> It does not encrypt your hard drive.

It is different than the normal bios boot hard drive.

If someone has physical access, and you haven't enabled the Ubuntu home drive encryption, all of your files will be immediately accessible.

The point?  You can set it to require two different passwords (the normal boot password and the hard drive password) to start the computer up. If someone only has the first password, but not the HD password, they can boot to CD or USB, but not your HD.

I'm not sure if omitting the HD password will prevent the HD from being mounted from a Live-CD, but I doubt it.

Long story short, encrypt the drive.

ok,so how to encrypt it without reinstalling everything?
(im kind of newbe here)

---

### Post by bodhi.zazen on 2011-04-18
> **werty2010 said:**
> ok,so how to encrypt it without reinstalling everything?
(im kind of newbe here)

Can't , encryption writes random data to the disk.

---

### Post by werty2010 on 2011-04-18
> **bodhi.zazen said:**
> Can't , encryption writes random data to the disk.

oh no....
i was hoping for a different answer

i suppose with this method everything will be encrypted on the fly,doesn't this mean that it will consume more resources?
or it doesn't matter at all?

---

### Post by werty2010 on 2011-04-18
also id like to know which version should i download?
(i think this is the alternate install CDbut im not sure)

---

### Post by bodhi.zazen on 2011-04-18
If you want full system encrytpion, use the alternate CD.

If you simply want to encrypt a directory you can use cryptkeeper, it is in the repos.

Encryption adds about 1 % overload, most people do not notice it with most desktop tasks.

---

