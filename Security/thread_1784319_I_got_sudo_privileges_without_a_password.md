---
title: "I got sudo privileges without a password"
date: 2011-06-16
forum: Security
---

### Post by hubertofliege on 2011-06-16
I'm not an advanced user, but came across this accidentally.  

Something is wrong with my laptop, and it won't boot.  It gives some error message 18 about how the boot loader can't load the cylinder.  I thought I could fix the problem if I deleted the last few files downloaded, so I put in a live CD and it booted up.  I couldn't delete files though, until I switched into command line interface.  I navigated to the hard drive, then found I could run sudo commands without it asking for a password.  

Am I missing something?  This seems like a pretty big security threat.

---

### Post by Larkspur on 2011-06-16
> **hubertofliege said:**
> I'm not an advanced user, but came across this accidentally.  

Something is wrong with my laptop, and it won't boot.  It gives some  error message 18 about how the boot loader can't load the cylinder.  I  thought I could fix the problem if I deleted the last few files  downloaded, so I put in a live CD and it booted up.  I couldn't delete  files though, until I switched into command line interface.  I navigated  to the hard drive, then found I could run sudo commands without it  asking for a password.  

Am I missing something?  This seems like a pretty big security threat.

It is: LiveCD makes the user root, which means they have root access to  the computer that the LiveCD is running on, that means ALL your files  are available (even Windows if you have it installed).  

However, it only becomes a real threat if someone else has access to  your computer and also has a LiveCD.  As a lot of people here are fond  of saying: physical access is root access.

There are a few things you can do to mitigate this: 

1) Use BIOS passwords if your computer allows them
2) Make sure the boot order has HD before USB or CD
3) Encrypt all important files
4) Don't let other people have sole access to your computer for any length of time.

---

### Post by deconstrained on 2011-06-16
Every known operating system shares this "security threat". As mentioned, if you want additional protection for your system you should look into encrypting your hard drive partition(s) (the best way of doing this in Linux is with dm-crypt).

---

### Post by crispy_420 on 2011-06-17
If someone has physical access no security method will help you. You can do all you want with BIOS, boot orders and others but what if I steal the drive, what good did all of that do? Or if someone images your drive to dissect for information later. That way I have time to brute force or use rainbow tables to get your passwords. Then that way anything I do as recorded as you doing.

Encryption is good but also comes with risk too. Sure your data is secure but might also be non-recoverable by you too if something happens.

Like said before you can threats in anything if you look enough.

---

### Post by hubertofliege on 2011-06-17
Hmm.  Thank you both very much for the explanation.  I figured that this issue couldn't have been an oversight, and wondered if it was just inherent.  I never realized how compromising physical access is.

Do either of you encrypt your partition?  Is there a way to encrypt files and folders on my computer and password protect them?  I'd like to be able to save bank statements and porn without worrying that another user might find them if they need to use my computer for a bit.

---

### Post by Thewhistlingwind on 2011-06-17
> **hubertofliege said:**
> 

Do either of you encrypt your partition?  Is there a way to encrypt  files and folders on my computer and password protect them? 


OpenPGP/etc?

---

### Post by tgm4883 on 2011-06-18
Truecrypt.

If you encrypt your partition, then you wouldn't be able to use a live cd to view the files without the password

---

### Post by crispy_420 on 2011-06-18
Truecrypt would work well for this purpose and you don't need to encrypt an entire drive rather make an encrypted file container to secure your statements/porn from prying/judgmental eyes.

Then when you would to review your statements (or film collection) you open up truecrypt and "mount" (sorry thought this term appropriate for this topic) the file container created as a virtual drive. When done, dismount and you are free from digital evidence. These containers are also portable to other systems with truecrypt installed so you can securely share your banks statements or other stuff between other systems/people.

---

