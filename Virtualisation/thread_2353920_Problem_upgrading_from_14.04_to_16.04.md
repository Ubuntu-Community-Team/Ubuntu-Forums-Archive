---
title: "Problem upgrading from 14.04 to 16.04"
date: 2017-02-26
forum: Virtualisation
---

### Post by chrille77 on 2017-02-26
Hi,

I have a 14.04.5 that I'm ready to lift to 16.04. But when running do-release-upgrade, at the first "config-file question", do I want to keep current or install new etc, when I press a key it goes to "Login incorrect. Give root password for maintenance (or type Control-D to continue)" and if I try to type the root password o press Control-D it just prompts again. If I hold Enter it eventually moves on but at the next config-file question it happens again. Any idea how to fix? It's a VM and I have reverted back to a working 14.04 snapshot so no panic, but I need to upgrade eventually.

[IMG]https://s23.postimg.org/70qfgyqmj/login_incorrect.jpg[/IMG]

---

### Post by howefield on 2017-02-26
Moved to the "*Virtualisation*" forum.

---

### Post by chrille77 on 2017-02-26
Even though it's a VM I don't think it's a VM problem?

---

### Post by Tadaen_Sylvermane on 2017-03-01
Never seen that before. Maybe try running your upgrade directly from the root user instead of sudo. (Assuming you ran the upgrade with sudo.)

```
sudo -i
```

---

### Post by jvaldry on 2017-04-03
I've also run into this problem.  Have you found a solution yet?  Mine is also a VM but it doesn't seem to be VM issue.  I've tried:

```
sudo -i do-release-upgrade
```

and

```
su root
do-release-upgrade
```

and 

logging in as root directly 


The only difference is mine is a different configuration file than yours.  This install is originally an upgrade from 12.04LTS.

-Jason

---

### Post by deadflowr on 2017-04-03
Press Enter, and take the default No.
 or press Y and then enter to take the maintainers version.
simple as that.
Shouldn't need to enter any password to deal with the config selections.
do-release-upgrade runs entirely as root, so unless you're prompted to change or set a password, no password should ever be needed.

---

### Post by jvaldry on 2017-04-03
Unfortunately every time I press a key, I get the staggered text prompting me to enter a password.  Eventually the console completely locks up and will no longer take any input except to change to another terminal.


```
Login incorrect.                 Give root password for maintenance
                                                  (or type Control-D to continue):
										  Login incorrect.
                     										  Give root password for maintenance
                                                                      								    (or type Control-D to continue):Login incorrect.                 Give root password for maintenance
                                                  (or type Control-D to continue):
										  Login incorrect.
                     										  Give root password for maintenance
                                                                      								    (or type Control-D to continue):Login incorrect.                 Give root password for maintenance
                                                  (or type Control-D to continue):
										  Login incorrect.
                     										  Give root password for maintenance
                                                                      								    (or type Control-D to continue):
```

---

### Post by jimbeck81 on 2017-04-04
I am also seeing this on one of our servers. I have attempted the upgrade on two servers (Both running on the same VMware ESXi 6.0 host.), one was successful, the other did this.

[IMG]https://s14.postimg.org/677o2scs1/do-release-upgrade-error.png[/IMG]

Has anybody had any luck solving this yet?

---

### Post by jimbeck81 on 2017-04-04
Does anybody who has this problem have the root account enabled? I was thinking of what the differences are between my two servers, and that was something. I locked the account ```
sudo passwd -l root
``` edited /etc/ssh/sshd_config, changing ```
PermitRootLogin yes
``` back to ```
PermitRootLogin without-password
```  and ran ```
do-release-update
``` again.

I was able to get past the point in my screenshot. The server immediately reset at this point - so it still hasn't updated properly - but I think this is progress. Going to try again and see if I can catch any error messages or find something in logs.

---

### Post by jvaldry on 2017-04-04
Yes, I enabled my root account in one of my tests and in my /etc/ssh/sshd_config file I do have 

```
PermitRootLogin without-password
```

same result.  :-(

However, I should note that I login to the console to do the upgrade, I don't remote in over SSH.

---

