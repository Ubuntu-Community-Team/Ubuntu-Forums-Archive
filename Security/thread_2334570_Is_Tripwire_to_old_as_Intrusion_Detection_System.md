---
title: "Is Tripwire to old as Intrusion Detection System?"
date: 2016-08-20
forum: Security
---

### Post by patrikmellq on 2016-08-20
Is Tripwire to old as Intrusion Detection System?
I can see that Tripwire has been last updated 2013-08-05

Even if Tripwire has not been updated i have a hard time understand why it should not be valid monitoring system of your operating system.
The thing is that if you install the databas on removable media i can't understand or see how any hacker could hide an intrusion.

Feel free to put some light on this! Should i trusth the integrity of Tripwire even if it has not been updated or improved.
If there was a way around to avoid trace against Tripwire, would not the Linux Community discover such a thing and be all over internet or least some one mention it.

Cheers

---

### Post by ghb321-gmail on 2016-08-21
Use snort :)

---

### Post by deadflowr on 2016-08-21
> **ghb321-gmail said:**
> Use snort :)

Different means.
tripwire is a host intrusion detection utility.
snort is a network intrusion detection utility.

Both serve different purposes.

> Feel free to put some light on this! Should i trusth the integrity of Tripwire even if it has not been updated or improved.
Does it need to be updated, constantly?

It's not like a virus scanner where you need to update both the database and the engine to run the scanner properly.
The tripwire database is of your own making.
And tripwire runs it's checks against said database.
So I see no real reason not to trust it, currently.

If you find anything that will help improve it, you can always report a bug or ask the developers in charge, to think about adding your suggested improvement.

---

### Post by ghb321-gmail on 2016-08-23
Ok. You have right. But what you thing about rkhunter? Is this the same as Tripwire?

---

### Post by lisati on 2016-08-23
> **ghb321-gmail said:**
> Ok. You have right. But what you thing about rkhunter? Is this the same as Tripwire?

As I understand it, rkhunter has a different purpose again, and is designed for examining the contents of files on your system, as distinct from detecting bad behaviour by systems that connect to yours.

---

