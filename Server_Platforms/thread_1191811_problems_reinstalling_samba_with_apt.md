---
title: "problems reinstalling samba with apt"
date: 2009-06-19
forum: Server Platforms
---

### Post by th3 mant1s on 2009-06-19
Hi Everyone, 

Could someone please help me recover from a bad package manager Uninstall/Reinstall of Samba through apt-get? I've also tried aptitude which may have conflicted with the other Package Manager.

Basically I did this
```


apt-get remove --purge samba
apt-get clean
apt-get install samba 


```

and I got this error...

```


After this operation, 0B of additional disk space will be used.
Setting up samba (3.0.28a-1ubuntu4.7) ...
 * Starting Samba daemons
   ...fail!
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

anyone got any ideas?

-M

---

### Post by th3 mant1s on 2009-06-19
I think I fixed it by rebuilding the /etc/samba directory and making a new smb.conf file. Hopefully once I edit the smb.conf file it will pull together.

Silly mistake on my end...

-M

---

