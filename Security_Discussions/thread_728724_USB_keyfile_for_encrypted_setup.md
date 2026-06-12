---
title: "USB keyfile for encrypted setup"
date: 2008-03-19
forum: Security Discussions
---

### Post by karl_kashofer on 2008-03-19
Hi !

Does anyone know if the encrypted setup as performed by the alternate cd install (full encryption) will/does support using a keyfile on a USB stick in conjunction with a passphrase ?

Thanks,
Karl

---

### Post by hyper_ch on 2008-03-19
yes it will.... but first you need to provide a password... you can then add keyfile authentication later on :)

(I enter password for my main harddisk and then I use keyfiles on that harddisk to "unlock" my other harddisks)

---

### Post by karl_kashofer on 2008-03-24
Hi !

In the standard encrypted setup from the alternate cd all partitions of the system including swapspace are combined into a logical volume. You enter the passwort at boot and all partitions are unlocked. Thus even hibernation works fine.
My question is just if it is possible to have usb-keyfile+password for unlocking the lvm.

> **hyper_ch said:**
> 
(I enter password for my main harddisk and then I use keyfiles on that harddisk to "unlock" my other harddisks)

I dont think thats a very good setup. Anyone who gains access to your computer during runtime (eg a virus or malware or CIA) can steal your keyfiles and open the other harddisks without knowing your password.
 
Thanks anyway for your suggestion,
Cheers,
Karl

---

### Post by Dr Small on 2008-03-24
I would think that it is a very good setup, if he has a strong password. If I read that correctly, he enters his password, then uses the keyfiles from the hard disk that he just unlocked to unlock his other hard disks.

What is so insecure about that?

---

### Post by hyper_ch on 2008-03-24
> **karl_kashofer said:**
> I dont think thats a very good setup. Anyone who gains access to your computer during runtime (eg a virus or malware or CIA) can steal your keyfiles and open the other harddisks without knowing your password.

well, as my computer gets logged after 5min of inactivity with a strong password, how would they gain access?

---

### Post by Biochem on 2008-03-24
> **Dr Small said:**
> I would think that it is a very good setup, if he has a strong password. If I read that correctly, he enters his password, then uses the keyfiles from the hard disk that he just unlocked to unlock his other hard disks.

What is so insecure about that?

The security hole is IF the culprit has access to the system while running, all he has to do is read the /etc/crypttab and find the keyfiles. Since the keyfiles are not encrypted, then the culprit as access to the other hard-drive after a reboot. But if he has that kind of access what prevents him form copying the HD while the system is still open?

I have this set-up (crypttab is unreadable to users). It is more a protection against laptop thief getting personnal info than preventing the "CIA" from having access to my hardrive.

---

### Post by wieman01 on 2008-03-25
> **hyper_ch said:**
> well, as my computer gets logged after 5min of inactivity with a strong password, how would they gain access?
With physical access to your computer? A matter of minutes I would suppose:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")

Full protection is only given if you switch off your computer. Hibernating puts it at risk as well.

---

### Post by hyper_ch on 2008-03-25
> **wieman01 said:**
> With physical access to your computer? A matter of minutes I would suppose:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")

Full protection is only given if you switch off your computer. Hibernating puts it at risk as well.

Problem is, first they need to suspect that you encrypted all your drives.. then the question is whether this effort can be justified to be employed...not sure what kind of equipment would be needed but I just don't think it's a practical solution that can be employed on anyone (yet)

---

### Post by wieman01 on 2008-03-25
> **hyper_ch said:**
> Problem is, first they need to suspect that you encrypted all your drives.. then the question is whether this effort can be justified to be employed...not sure what kind of equipment would be needed but I just don't think it's a practical solution that can be employed on anyone (yet)
The report makes you think it is a fairly straight-forward procedure. The question is not whether they suspect it's enrypted or not, but rather if they like to get hold of your data. A precaution would be to proceed as described in the study and I understand that the materials used are freely available.

It is very practical (read the report, you'll see what I mean) and not as sophisticated as people might beliebe. You don't have to be a NSA agent to achieve it.

---

### Post by hyper_ch on 2008-03-25
Then I will have a closer look at the report... can non-tech-geeks actually understand what the report contains?

---

### Post by wieman01 on 2008-03-25
> **hyper_ch said:**
> Then I will have a closer look at the report... can non-tech-geeks actually understand what the report contains?
Oh, very much. The algebra may be a bit too much but I find it reasonably well explained and easy to follow even for noobs.

---

### Post by casperlingus on 2008-03-25
Didn't read the report (just glanced at this thread), but it should be noted that Firewire ports have direct-memory-access -- i.e. regardless of what OS is running, and even if your computer is locked, it is possible for someone to do a memory dump of your RAM via your firewire port, as long as your computer is on.

Therefore, if the key is in memory, it can be retrieved.  

Lesson:  disable your firewire ports if you don't use them.  I don't know how to do this, because I don't have any firewire ports, so I've never tried.

---

### Post by wieman01 on 2008-03-25
> **casperlingus said:**
> Didn't read the report (just glanced at this thread), but it should be noted that Firewire ports have direct-memory-access -- i.e. regardless of what OS is running, and even if your computer is locked, it is possible for someone to do a memory dump of your RAM via your firewire port, as long as your computer is on.

Therefore, if the key is in memory, it can be retrieved.  

Lesson:  disable your firewire ports if you don't use them.  I don't know how to do this, because I don't have any firewire ports, so I've never tried.
Heard about it too. Plain ridiculous when you think about it.

---

### Post by casperlingus on 2008-03-26
Yes, pretty ridiculous from a security perspective.  But, from any other perspective, it's easy to see there's a lot of overhead associated with asking the the OS for permission to access memory.  By accessing the memory directly, it's no wonder why firewire is so ridiculously fast.

---

