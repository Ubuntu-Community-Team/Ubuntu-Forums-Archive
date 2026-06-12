---
title: "How to reboot headless server with passphrase?"
date: 2009-12-21
forum: Server Platforms
---

### Post by BioGeek on 2009-12-21
I have an old desktop computer that I want to start using as a headless server.

With a monitor and a screen attached, I installed Ubuntu Server edition with encrypted LVM on the machine. After installation I rebooted and, still with the monitor and keyboard attached, filled out the passphrase and was able to login. I was able to login to the server from my laptop. So far so good.

Then I disconnected the monitor and keyboard and rebooted the desktop remotely over ssh from the laptop. Upon rebooting I heard two beeps. When I tried to login again via ssh I got the message:

```
$ ssh plectrophenax.local
ssh: Could not resolve hostname plectrophenax.local: Name or service not known
```

When I reattached the monitor to the server, I saw the message

```
Grub loading
Unlocking the disk /dev/disk/by-uuid/de99e2c0-56d7-473b-f134FF5bd634 (sda1_crypt)
Enter passphrase:
```

So apparently it was waiting for me to enter my passphrase before it would boot up.

So how do I enter this passphrase remotely?

---

### Post by cdenley on 2009-12-21
It's not easy, since any network service which would need to listen for your connection would reside on the encrypted volume which would need to be decrypted before you can make a connection remotely.
[http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu](http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu)

---

### Post by BioGeek on 2009-12-21
Thanks!

---

