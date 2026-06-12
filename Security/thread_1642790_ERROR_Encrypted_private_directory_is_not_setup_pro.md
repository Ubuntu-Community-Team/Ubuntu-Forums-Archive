---
title: "ERROR: Encrypted private directory is not setup properly"
date: 2010-12-10
forum: Security
---

### Post by proch04 on 2010-12-10
Long story short:

I opted to encrypt my home, enter the passphrase and soon as I log out and rebooted, I got stuck with a message about 
/var/lib/ICEauthority file and other messages.

So I've been trying to fix one issue at the time. 

The bottom line is that I'm trying to get to my private folder. 

Dropped in recovery mode:

```
 
username@username:~$ sudo -i encryptfs-mount-private
Enter Passphrase: passphrase
ERROR: Encrypted private directory is not setup properly

```

I have done quite a bit of reading including  these posts

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

[http://bodhizazen.net/Tutorials/Ecryptfs/]("http://bodhizazen.net/Tutorials/Ecryptfs/")
and this one as well: [http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/]("http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/")


I need your help

Thank You

---

### Post by FuturePilot on 2010-12-10
In recovery mode 'su' to your user before running encryptfs-mount-private

---

### Post by proch04 on 2010-12-11
Yes I did that

In recovery mode to normal boot running ubuntu 10.10

```

username@username:~$ ecryptfs-mount-private
Enter your login passphrase: passphrase
Inserted auth tok with sig [23b52e146e76aee03] into user session keyring
mount: Operation not permitted

```

 I used sudo -i  ecryptfs-mount-private in my previous attempt to get a different result that what I've just got above.

Any other suggestions?


Quite frankly, this type of situation is a productivity killer. I followed the instruction that the system told me to do and rebooted. Now, I can't use it. I want to take responsibility for my own screw up, but in this case, there is definitely something wrong with the encryption of  the private folder

Thank you all for helping out.

---

### Post by COKEDUDE on 2010-12-12
Have you tried this guide? 

[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)

---

### Post by xrhettx on 2011-11-11
> **FuturePilot said:**
> In recovery mode 'su' to your user before running encryptfs-mount-private

Thank you!!!!!

---

