---
title: "Intermitent problem to login after a OpenLDAP + samba + bind configuration (7.10)"
date: 2008-01-22
forum: Server Platforms
---

### Post by Aristo on 2008-01-22
According to the setup of a Ubuntu server 7.10 following from:
[http://howtoforge.net/openldap-samba-domain-controller-ubuntu7.10](http://howtoforge.net/openldap-samba-domain-controller-ubuntu7.10)

Hello,

I follow the HowTo exactly and tried with multiples installations from scratch but I always have the same problem: Problem to login.

I now know that I got an Intermitent problem.

At boot, sometimes, the boot process stuck at bind startup. If I press enter, I got the login prompt. If I tried to login the login process will freeze the tty1. I've tried with all tty* and it does the same.

So I reboot (and now I got an error that OpenLDAP is not start and he can't communicate with the port 953 on 127.0.0.1 RNDC).

After the reboot, sometimes bind start normally and all the process boot normally: Like openldap, samba, sshd, apache2, etc. So now I can boot, because my openldap is startup and nsswitch.conf authenticate with it.

I search for logs, daemon logs, syslog, message, dmesg, nothing.. just a little error message from message: Kernel: Faillure registering capabilities with primary security module.

And that is related (I think) with SElinux that is disable by default on Ubuntu.


Thank you in advance for your help!

---

