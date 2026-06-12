---
title: "Slow sudo after accidental change"
date: 2010-02-05
forum: Server Platforms
---

### Post by BasicInc on 2010-02-05
Hi all.

My first post. I've been using Ubuntu Server edition (Hardy) happily for some time now.

I use sudo regularly during configuration of new services. It always works/authorises within seconds, however, it recently became very slow, to the point of being nearly unusable.

In /var/log/auth.log I noticed a regular working pattern like this:

Feb  3 14:07:20 kanyo sudo:      lee : TTY=pts/1 ; PWD=/usr/share/obm/www ; USER=root ; COMMAND=/etc/init.d/apache2 restart
Feb  3 14:07:25 kanyo sudo: pam_unix(sudo:session): session opened for user root by lee(uid=0)
Feb  3 14:07:30 kanyo sudo: pam_unix(sudo:session): session closed for user root

Unfortunately now, they look the same, but the timestamps are much wider apart (minutes). This occured after running synaptic and dpkg-reconfigure obm-conf. I was trying to remove 'OBM' ([http://www.obm.org/doku.php?id=docs:install:ubuntuhardy](http://www.obm.org/doku.php?id=docs:install:ubuntuhardy)) completely as I'd messed up (just OBM) while trying to fix a minor-looking misconfiguration.

Any idea what I've broken and how to fix it?
------------
ASIDE:
I noticed that every time I come to use sudo after a delay (the auth timed out) I get a line like this:

Feb  3 14:13:15 kanyo sudo: pam_smbpass(sudo:auth): unrecognized option [missingok]

But this also occured prior to it going wrong.
------------

Any help much appreciated.

Regards,

Lee

---

### Post by noway2 on 2010-02-05
Probably not much help, but the one thing that I have found makes sudo really slow is if there is a network problem at which point any time that I enter a sudo command it complains that it can't resolve its own hostname.  By network problem I mean one where the network configuration (resolv.conf or /network/interfaces) gets screwed up and the machine can't locate DHCP, DNS, etc.

---

### Post by fang0654 on 2010-02-05
It sounds like you ended up with some extra entries in your pam.d config files.  the pam_smbpass is for authenticating to samba servers, which probably has something to do with obm.  I've run into similar situations setting up servers to communicate with Active Directory, where when I go to sudo, it would first check samba.. wait.. wait.. wait.. finally timeout, then continue as normal.

Check the files in /etc/pam.d

---

### Post by BasicInc on 2010-02-08
Thanks for your input fang0654 / noway2.

I've looked into both points mentioned, but cannot see anything amiss - files in pam.d have not been modified and network config has not changed.

I notice sudo and su both are slow in the same way, and it's not just suing to root - it occurs on sudo -u anyuser. Another thing I noticed was that sudo's password prompt is fast (implies pam_unix is okay), but it hangs at the point of actually switching user - almost as if the shell is not responding to sudo's completion. It's a tricky problem!

In searching for files which got modified at the time the problem arose I found a few empty lock files knocking about - they don't look like they could be related, but clutching at straws, I'll delete these and reboot when I can take it offline.

Thanks again.

---

### Post by luke_lukem on 2010-06-27
----------  Edit -------------------
Don't do anything yet, i did not fix it !
-------------------------------------
Hi everyone,
i tried something that seems to render sudo more usable:
i checked the places mentioned here, and looked at:
/etc/pam.d/samba:
```
#%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so
```

The last two lines seem something added by an update, 
so i commented them, and restarted the samba daemon.
It's only been a few minutes from this, but i noticed that now i can use gksu without issues

Note: Previously, gksu would hang, and i had been using all the sudo command-line equivalents.

I don't know exactly what i did with that file,
so if someone more knowledgeable sees this, any help is welcome.

----------  Edit -------------------
Don't do anything yet, i did not fix it !
-------------------------------------

---

