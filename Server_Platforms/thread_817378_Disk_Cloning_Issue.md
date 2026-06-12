---
title: "Disk Cloning Issue"
date: 2008-06-03
forum: Server Platforms
---

### Post by hypetech on 2008-06-03
I have 2 identical Dell Poweredge 1650 rack mount servers.  I installed Ubuntu and set up my basic configuration on one of these servers.  After the basic configuration was completed, I then made a backup image of the entire disk with Acronis.  When I restore that image to the 2nd identical server, everything seems to boot properly with the exception of an error while loading the network device.  The error I get is:

"eth0: ERROR while getting interface flags: No such device"

I ran a "lspci -v|grep -i ethernet"  on both machines, and they are both running identical Intel Corp 82544EI network cards (onboard).

I looked around a little on Google to see if I could find anything that tied the config to a specific MAC, and the only thing I could find was about the /etc/iftab file, that my system does not have.

I am running Ubuntu 8.04 LTS Server Edition.  Any help resolving this issue will be much appreciated :)

---

### Post by cdenley on 2008-06-03
/etc/iftab is not used in hardy. /etc/udev/rules.d/70-persistent-net.rules is. The "new" ethernet adapter will be assigned the next available id (eth2).
```

ifconfig -a

```

---

### Post by hypetech on 2008-06-03
hmm.  I did just noticed that the new server has eth2 and eth3 instead of 0 and 1.  Is there any way I can ensure that all of the images use 0 and 1 instead of 2 and 3?  I have some configs for snort that rely on eth0 and eth1 and having to change it on every server will defeat the purpose of having the image in the first place :(

---

### Post by cdenley on 2008-06-03
> **hypetech said:**
> hmm.  I did just noticed that the new server has eth2 and eth3 instead of 0 and 1.  Is there any way I can ensure that all of the images use 0 and 1 instead of 2 and 3?  I have some configs for snort that rely on eth0 and eth1 and having to change it on every server will defeat the purpose of having the image in the first place :(

Just clear the rules in /etc/udev/rules.d/70-persistent-net.rules before you clone the drive. Then when you boot the clone for the first time, it will create new ethernet assignments starting at eth0.

---

