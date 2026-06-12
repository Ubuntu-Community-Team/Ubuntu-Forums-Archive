---
title: "/tmp partition only 1M?"
date: 2009-02-12
forum: System76 Support
---

### Post by bspeakmon on 2009-02-12
This is the partition setup on my spanking-new Serpal:

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   14G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  112K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda3             200G  1.5G  188G   1% /home
overflow              1.0M  1.0M     0 100% /tmp
```

This can't be right. 1M is ridiculously small for /tmp. synaptic can't install or configure anything greater than a few hundred K.

I feel like I'm missing something. Is this how it's supposed to work and I'm not understanding why? If not, what do I do?

Thanks!

---

### Post by Guille Damke on 2009-02-12
From what I see, you don't have space in the partition /dev/sda1 where root "/" is mounted. I think that's why you see an "overflow" being mounted in /tmp. Have you installed too many/big packages recently? You can delete some of them to free space.
Other think you could do is to resize the partitions (wait for someone to tell how to do it) I see that you have 188GB available in the /dev/sda3, where /home (thus your personal files) are.
Guille.

---

### Post by bspeakmon on 2009-02-12
You pointed me in the right direction. Turns out I had some epic log files that were taking up almost 9 GB in /var. I think it's related to some CD driver issues I'm having. Once I cleaned those out, things worked fine. 

Thanks for the help.

---

### Post by Guille Damke on 2009-02-12
You are welcome.
I have read some comments (I think from Thomasaaron) about a bug that creates those epic log files.
Guille.

---

### Post by thomasaaron on 2009-02-12
Yes, there is some sort of bug out there that does that, although I'm not sure what is causing it.

I've heard some people say Samba is causing it (or something about the way shares are defined in /etc/fstab). 

Are you using Samba?

---

