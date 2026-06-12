---
title: "Weird: avahi-daemon asking for Disk password"
date: 2019-03-31
forum: Security
---

### Post by thaier on 2019-03-31
Hi everyone!

I just came across a weird behavior under ubuntu 18.04 which I don't understand, so I thought maybe someone here can reproduce it and/or explain what's going on.

When I execute this command: ```
sudo service avahi-daemon stop
``` I get this prompt:

```
Please enter passphrase for disk XXXXXX (sdb1_crypt) on /home/thomas/UltraHDD!
``` (I replaced the disk name with XXXX)

I am using full disk encryption using LUKS. The partition that the passphrase is asked for is not the main partition, but an external one.

What I am wondering about: Why does Avahi-daemon ask for the password? After all the disk is mounted already and I also don't get why Avahi-daemon needs the password in the first place. Also: I notice that it is irrelevant, what password I enter, the following behaviour is the same. I get this on the next step:

```
Warning: Stopping avahi-daemon.service, but it can still be activated by:
  avahi-daemon.socket
```

If I abort the command using Ctrl+C i get this when typing a character:
[HTML]Failed to query password: Input/output error
Failed to show password: Input/output error[/HTML]

Thanks for your help!
Thomas

PS: Since this command was executed for the first time (this happened through airmon-ng check kill) the partition is not auto mounted at startup anymore, even though it is in crypttab and fstab and worked until now.

---

