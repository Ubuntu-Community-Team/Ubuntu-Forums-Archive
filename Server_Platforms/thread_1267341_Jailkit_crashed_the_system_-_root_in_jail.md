---
title: "Jailkit crashed the system - root in jail?"
date: 2009-09-15
forum: Server Platforms
---

### Post by rozwell69 on 2009-09-15
Howdy!

I had well installed Ubuntu 9.04 with ISPConfig 3 and Jailkit 2.6 and everything was working fine.
Unfortunatelly when I've added new shell user with Jailkit option (in ispconfig, in the same time I was logged as root via ssh) root lost his ability to do anything. Of course system was not able to start so now it's mounted on the other system.
So I've got access to every file but cannot login using chroot:
```
# chroot /crashed_system
chroot: cannot run command `/bin/bash': No such file or directory
```

Checked and permissions are fine (unchanged I guess):
```
# ls -l /recovered_system/bin/bash
-rwxr-xr-x  1 root root 833592 Mar  2  2009 /recovered_system/bin/bash
```

Does anyone knows how to fix it?
or
purge jailkit from the system
or
make root able to login
or
configure jailkit to remove root from jail? (if it's in jail, because I don't know how to check it)

The case is really important so any suggestions are expected.


Cheers!
rozwell

**EDIT:**
I have recovered important data and will now reinstall the system but I still don't know the answer...

---

### Post by grigra on 2009-09-19
hy guys. I have the same problem. I've done the same steps and got the same error and my server is still not running correctly :(

any news about the problem? Is there a fix?

---

### Post by rozwell69 on 2009-09-20
Hell yeah!
I did some digging and found the solution. It's so simple that's almost stupid:
Edit file:
```
/etc/jailkit/jk_init.ini
```
And **comment** / change / remove lines:
```
users = root
groups = root
```
I suggest comment them in all sections. Just to make sure it won't be a problem anymore.
It's in:
```
[jk_lsh]
[basicshell]
[openvpn]
[apache]
```

Explanation from documentation:
```
The users and groups entries specify which users and groups that need to be present in <jail>/etc/passwd.
```

And that's it. Problem solved.

---

### Post by Balabaka on 2009-09-22
Doen't seem to work with my system :(

---

### Post by grigra on 2009-09-23
this fix also didn't work for me ... I had to set up my server again. But thanks for your help.

---

### Post by Freddy436 on 2009-12-22
Hello, I had the same issue with ISPConfig 3.0.1.4 and jailkit 2.8 on a debian lenny system (amd64).

You should check /lib for broken symlinks. In my case jailkit removed the folowing important libs:
/lib/ld-2.7.so
/lib/libnsl-2.7.so                       
/lib/libnss_compat-2.7.so         
/lib/libnss_dns-2.7.so               
/lib/libnss_files-2.7.so           
/lib/libnss_hesiod-2.7.so         
/lib/libnss_nisplus-2.7.so       
/lib/libnss_nis-2.7.so

It's a bug in jailkit 2.8 fixed in 2.9+

---

