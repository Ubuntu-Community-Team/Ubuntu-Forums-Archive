---
title: "Grub 2 and FQDN problems."
date: 2010-04-21
forum: Server Platforms
---

### Post by Squeazer on 2010-04-21
Hey, i'm having a few problems with my Ubuntu server (9.04 or 9.1, not sure). Umm, when i reboot, it stalls and gives out a message:

```
Kernel panic - Not syncing: IO + Timed doesn't work! Boot with apic=debug, and send a report. Then try booting with the 'noapic' option.
```

That's the first problem, and i have no idea how to add the "noapic" option to Grub 2. How can i do that, or is there anything else i can do?
Oh and when i stall at that error, i can reset my virtual machine (windows hyper-v) and it will boot normally.

The second thing is my hostname. At first it was UBUNTU-PGM and my FQDN was UBUNTU-PGM.ubuntu. Since i didnt like that i changed id to something else and i apperently screwed something up in the my hosts file, which now looks like this:

```
127.0.0.1       UBUNTU-PGM localhost
193.2.129.180   UBUNTU-PGM.ubuntu UBUNTU-PGM

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

What should i change to make my hostname (i'm guessing /etc/hostname) prvi-dijak and my FQDN prvi-dijak.si

Oh and the reason i know i did something wrong is that when i restart apache it says it couldn't reliably determine my FQDN and it will use 127.0.0.1


Now there is another "problem" that i have, with my OpenLDAP installation. When i boot i gives out a lot of errors that it couldn't connect to the database. I don't know if i should be concerned by this, since the database does work when the whole system boots.

Thanks for any support! :KS

---

### Post by alarme on 2010-04-21
Hi,

this is my /etc/hosts:

127.0.0.1   alr-44.lan alr-44 localhost.localdomain localhost

and my /etc/hostmane:

alr-44

bye

---

### Post by Squeazer on 2010-04-21
Hey it worked! Thanks a lot ^^

```
127.0.0.1       UBUNTU-PGM.ubuntu UBUNTU-PGM localhost.localdomain localhost
193.2.129.180   UBUNTU-PGM

```

---

