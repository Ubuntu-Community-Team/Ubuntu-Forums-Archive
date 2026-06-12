---
title: "[SOLVED] Enable Domain Active Directory Authentication to VMWare Server 1.0.6"
date: 2008-08-07
forum: Security
---

### Post by gkaragoulis on 2008-08-07
Does anyone know how to configure VMware Server running on an Ubuntu host to authenticate using Active Directory?  I will try and figure this out today and post my results...unless someone beats me to it.

---

### Post by HermanAB on 2008-08-07
Here is something that may help:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by gkaragoulis on 2008-08-07
> **HermanAB said:**
> Here is something that may help:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman
Thank you Herman, but I have already made it that far.  I have successfully joined my Ubuntu machine to the Active Directory Domain, and now i want to use Domain credentials to login to the VMWare server console.  I'm assuming I do this with PAM...

---

### Post by HermanAB on 2008-08-07
Hmm, I seldom run the VMware console.  I SSH into the Linux VMs or RDP into the Windows VMs.

The VMware console is just an application on the host server, so I think that all you need to do is enable AD on the host server itself.

---

### Post by gkaragoulis on 2008-08-11
Ok I was able to get this working.  I'm sure there are a few ways to do it, but this worked for me:

NOTE: Your Linux machine must already be joined to the Domain for this to work!

VMware authenticates with the file: /etc/pam.d/vmware-authd, so the first thing is to backup this file!  Call it vmware-authd.bak or something.  I made /etc/pam.d/vmware-authd look like this:

```
#%PAM-1.0
auth       sufficient       /usr/lib/vmware/lib/libpam.so.0/security/pam_unix.so shadow nullok
auth	   sufficient	    /lib/security/pam_winbind.so use_first_pass
auth       required         /usr/lib/vmware/lib/libpam.so.0/security/pam_unix_auth.so shadow nullok

account    sufficient       /usr/lib/vmware/lib/libpam.so.0/security/pam_unix.so
account	   sufficient	    /lib/security/pam_winbind.so
account    required         /usr/lib/vmware/lib/libpam.so.0/security/pam_unix_acct.so
```

Note that this differs from the regular 'vmware-authd' by the addition of the 'pam_winbind' module.  Also on some of the lines, 'pam_unix' was changed from 'pam_unix2', because that doesn't exist on my ubuntu machine.

ATTENTION 64 BIT USERS: While trying to implement this on my 64-bit servers I ran into problems, and they boil down to vmware requiring the 32-bit pam library.  Normally vmware comes with its own 32-bit pam library, but that doesn't include the pam_winbind module.  So to get this to work I just copied the pam_winbind module from my 32-bit server to my 64-bit server into a folder I made called /lib/security-32 and used that module instead.  That worked like a charm.

---

### Post by gkaragoulis on 2008-08-14
I hate to keep this thread going, but I also ran into problems with the Name Service Cache Daemon while implementing this on one of my servers.  I had PAM configured exactly as the others and it still didn't work.  /var/log/auth.log said that getpwnam(<myname>) couldn't find me.  I resolved this by restarting nscd: '/etc/init.d/nscd restart'

Another cool thing I was able to do with this was to deny/allow access to specific domain groups.  The pam_winbind module has an argument called 'require_membership_of=<SUID>' that will only allow access if the user is in the group defined by '<SUID>'.  You can determine a group's SUID from just their name by executing 'wbinfo -n <group_name>'.

Very Cool!  Now the authorization to vmware server is controlled by my Domain Controller!

---

