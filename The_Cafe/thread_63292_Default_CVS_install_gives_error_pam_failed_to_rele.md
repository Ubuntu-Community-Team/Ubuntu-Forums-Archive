---
title: "Default CVS install gives error: pam failed to release authenticator"
date: 2005-09-07
forum: The Cafe
---

### Post by navneet on 2005-09-07
Hi,

I did a default cvs install using apt-get and then installed cvsd
I changed the cvs directory in the /etc/cvsd/cvsd.conf and the /etc/cvs-cron.conf files to point to the CVS respoitory.

But, when i try to connect to the cvs server using the pserver protocol ... even for a login using a command like this:
```
cvs -d :pserver:navneet@localhost:/cvs login
```

After giving the password on the 
```
CVS password:
```
prompt, the message i get is:

```
PAM start error: Critical error - immediate abort
Fatal error, aborting.
cvs [login aborted]: unrecognized auth response from localhost: pam failed to release authenticator

```

Any help will be highly appeciated.

---

### Post by drewp on 2006-01-17
I had this problem too, and eventually found the following changes that made it work. My repo is called '/srcmirror' (it's a read-only repo that's periodically rsynced from the real repo).

Make /var/lib/cvsd/srcmirror/CVSROOT/config start like this:
  SystemAuth=no
  PamAuth=no

Add a cvs user called 'cvs':
  # cvsd-passwd /var/lib/cvsd/srcmirror cvs      
  /usr/sbin/cvsd-passwd: adding user 'cvs' to '/var/lib/cvsd/srcmirror/CVSROOT/passwd'
  Enter new password: <enter>
  Retype new password: <enter>

Make a link at /bin/cvs to /usr/bin/cvs (!), since cvsd was calling /bin/cvs for some reason, and I didn't want to figure out where that was set:
  # ln -s /usr/bin/cvs /bin/cvs

Finally, this minimal test worked:
  # cvs -d :pserver:cvs@bigasterisk.com:/srcmirror version
  Client: Concurrent Versions System (CVS) 1.12.9 (client/server)             
  Server: Concurrent Versions System (CVS) 1.12.9 (client/server)

---

### Post by GoneSouth on 2006-08-22
Hi Folks,

I had the same error. I had an existing cvs repository that I restored from backup into a directory that was *not* a subdirectory of the chroot jail. Thus, when cvsd ran, my <cvsroot>/CVSROOT/config file could not be found from the chroot jail and cvsd was not picking up my config settings (including PamAuth=no), and I got the notorious pam error.

Solution: 

1) Turn of the chroot jail by setting 
```
RootJail none
```
in /etc/cvsd/cvsd.conf, then set
```
PamAuth=no
```
in <cvsroot>/CVSROOT/config

or 2) set up your repository inside the chroot jail. (it occurred to me after, possibly I could have soft-linked my existing repository to the chroot jail, although I did not try this).

---

