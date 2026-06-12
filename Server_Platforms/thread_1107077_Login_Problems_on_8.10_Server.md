---
title: "Login Problems on 8.10 Server"
date: 2009-03-26
forum: Server Platforms
---

### Post by mikey73 on 2009-03-26
Hi Guys

Just posting this for my work colleague really. I run 8.10 Desktop but he has the server edition running. 

The problem he is having is that when he boots to the login screen it says localhost.localdomain at the bottom right corner instead of his usual andy.server

Now every time he tries to login with his usual username and password, it lets him in but he can't sudo or su at all.

Any ideas on how to get the andy.server back so he can login normally would be appreciated as we're both stumped.

If all else fails he's going to have to backup up his data and do a fresh install, which he doesn't want to do.

Out of interest, would updating to 9.04 next month reset everything back to normal because he says he can wait until then if it would.

Cheers

Mikey

---

### Post by Xiong Chiamiov on 2009-03-27
What happens when he tries to su or sudo?

What do you get from
```

groups

```

What are the contents of /etc/sudoers?

---

### Post by ddoom on 2009-03-27
I had a similar problem trying to login to an Ubuntu 8.10 server machine without a GUI.

If ssh is installed on that machine, ssh into it and try run a command as sudo. If you get a Segmentation Fault, the solution for me was to reboot the machine into recovery mode and purge the samba, samba-common and libpam-smbpass packages. Then reinstall them.

[FONT="Courier New"]apt-get purge -y samba samba-common libpam-smbpass[/FONT]

[FONT="Courier New"]apt-get install -y samba samba-common libpam-smbpass[/FONT]

Resume the boot and you should be able to login as usual.

Note: This will replace your samba configuration file (/etc/samba/smb.conf) so you may want to back this up first.


Good luck

---

