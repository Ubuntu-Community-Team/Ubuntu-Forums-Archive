---
title: "How to  securely wipe your memory"
date: 2009-04-09
forum: Security
---

### Post by yeehi on 2009-04-09
SD memory retains the data, even after the power has been switched off.

Is it possible to have the data in memory always encrypted?
How can we (easily!:) perform a secure wipe of our memory?

Thank you!

---

### Post by Backharlow on 2009-04-09
smem (1)             - secure memory wiper (secure_deletion toolkit)
srm (1)              - secure remove (secure_deletion toolkit)
sswap (1)            - secure swap wiper (secure_deletion toolkit)

These are in the repos

---

### Post by yeehi on 2009-04-09
Backharlow:guitar:

---

### Post by Backharlow on 2009-04-09
The package is called secure-delete.
I use the srm to "shred" my trash and it works.
As for RAM, I know that encrypting memory is possible, but when you turn the computer off you don't need anything to reside there anymore anyway so even if it could be retained in encrypted form, there is still something for an intruder to steal, so just securely erasing it before shutdown makes sense.:popcorn:

---

### Post by yeehi on 2009-04-10
I tried the smem command at the prompt and received the following error message:

> Warning: Could not reset ulimit for mem locked

---

### Post by YosefKaro on 2009-11-14
I am receiving this same warning:

Could not reset ulimit for mem locked

Is this normal when running smem from secure-delete ?

-Yos

--Now I just got this message: Terminated by signal. Clean exit.

What am I doing wrong ?

---

### Post by SuperSonic4 on 2009-11-14
> **yeehi said:**
> 
How can we (easily!:) perform a secure wipe of our memory?

Thank you!

Physically destroy the medium

---

### Post by YosefKaro on 2009-11-14
Ha ha you are right...that is the only way to be 100% certain.  But for someone who doesn't need to take such drastic measures...

-Yos

---

### Post by wojox on 2009-11-14
```
man smem
```

---

### Post by Norm24 on 2009-11-14
> **Backharlow said:**
> The package is called secure-delete.
I use the srm to "shred" my trash and it works.
As for RAM, I know that encrypting memory is possible, but when you turn the computer off you don't need anything to reside there anymore anyway so even if it could be retained in encrypted form, there is still something for an intruder to steal, so just securely erasing it before shutdown makes sense.:popcorn:

I installed secure-delete and can not find it anywhere on my system.Where is it installed to?Would love to add a launcher for this to the panel.

Thanks in advance.

---

### Post by YosefKaro on 2009-11-14
You have to run it from the terminal.  Here is a [link]("http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/") for you.

-Yos

---

### Post by Norm24 on 2009-11-14
> **YosefKaro said:**
> You have to run it from the terminal.  Here is a [link]("http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/") for you.

-Yos

Thanks Yos.

Didn't realise this was a command line program.

---

