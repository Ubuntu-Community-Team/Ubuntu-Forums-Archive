---
title: "Full encrypt and reboot"
date: 2009-01-14
forum: Security
---

### Post by sampei7777 on 2009-01-14
Hi all.

I want to use ubuntu server for a website. I would like to have a full encrypted system because the server is in a server farm and I cannot access it, but others people can. So someone could use a live CD and read all my data. 

Now the problem is: if I install an encrypted system, it will prompt for a passphrase on boot. But I have not physical access to the sarver, so I cannot type the passphrase!

I could use a key on an USB stick, but this USB stick should be in the server farm with my server, so somebody else could use the key.

So, how to solve this?

Thank you.

---

### Post by Dr Small on 2009-01-14
Here's a guide by hyper_ch on this subject:
[http://ubuntuforums.org/showthread.php?t=829768](http://ubuntuforums.org/showthread.php?t=829768)

---

### Post by sampei7777 on 2009-01-15
> **Dr Small said:**
> Here's a guide by hyper_ch on this subject:
[http://ubuntuforums.org/showthread.php?t=829768](http://ubuntuforums.org/showthread.php?t=829768)
Yes, this could be a solution. 
But I also have the problem of a reboot. 
In the night, the server does a backup and then it reboots. 
At this point I have to type the password via ssh. . .

I would like it could reboot without human intervent.

Any ideas?

Thank You.

---

### Post by hyper_ch on 2009-01-15
rebooting an encrypted computer without human intervention that would make the whole encryption pointless...

---

### Post by sampei7777 on 2009-01-15
> **hyper_ch said:**
> rebooting an encrypted computer without human intervention that would make the whole encryption pointless...
Why?

If the OS is running, you will need a valid login to access data. If the OS is not running and you try to access by live CD, the data is encrypted.

I found something on [Loopback Encrypted Filesystem HOWTO]("http://tldp.org/HOWTO/archived/Loopback-Encrypted-Filesystem-HOWTO/"), but it is a very old document (1999) and I don't know if it does what I want.

Thank You

---

### Post by hyper_ch on 2009-01-15
if you can boot the encrypted system automatically you can access the keys from the ram and then you can unlock it from another device.

---

### Post by sampei7777 on 2009-01-15
> **hyper_ch said:**
> if you can boot the encrypted system automatically you can access the keys from the ram and then you can unlock it from another device.
And are the keys still available in the ram once booted? Or only in the boot process?

Another question:
I am not sure but it seems to me that Windows 2003 can boot from an encrypted disk automatically. How can it do?

If there is the same behaviour than this means that it could be possible to access to an encrypted w2k3 system...

Thank You.

---

### Post by hyper_ch on 2009-01-15
the keys stay in ram because everything read/written to the harddisk will need to be en/decrypted...

---

