---
title: "subdirectories within /smb via autofs"
date: 2007-04-08
forum: Server Platforms
---

### Post by snarkus on 2007-04-08
i'm using smb via autofs to back up a network of windows pc's.  since i'm backing up mostly the same directories on all of them, i'd like to create a hierarchy under /smb to make navigation easier.  that is, if i'm backing up the DocsAndSettings directory for machines named "office" and "admin", i'd like to have it mount those dirs as /smb/office/DocsAndSettings and /smb/admin/DocsAndSettings.  

i'm using auto.smb to achieve the automounting.  so i have entries like:

admindocs -fstype=smbfs,username=NFS ...  ://admin/DocsAndSettings

this mounts the DocsAndSettings share from admin on /smb/admindocs

i tried adding an entry like:

admin/DocsAndSettings  -fstype=smbfs,username=NFS ...  ://admin/DocsAndSettings

to get what i want, but it fails.  the /smb/admin directory is created, but nothing is in it, and i see in syslog:

failed to mount /smb/admin/DocsAndSettings

so, after all of that long winded preamble, my question is, how do i set things up to get what i'm looking for?

thanks

---

### Post by Ateo on 2007-04-11
What is up with autofs and ubuntu? My configuration works just peachy on my gentoo laptop....

/etc/auto.master
> /network/argon	/etc/auto.dracco

/etc/auto.dracco
> multimedia      -fstype=cifs,credentials=/home/dracco/.smb.auth,uid=1000,dmask=0777,fmask=0777,rw       ://argon/multimedia
dracco          -fstype=cifs,credentials=/home/dracco/.smb.auth,uid=1000,dmask=0777,fmask=0777,rw       ://argon/dracco
public          -fstype=cifs,credentials=/home/dracco/.smb.auth,uid=1000,dmask=0777,fmask=0777,rw       ://argon/public
www             -fstype=cifs,credentials=/home/dracco/.smb.auth,uid=1000,dmask=0777,fmask=0777,rw       ://argon/httpd

A copy and paste should work, in theory, but does not. What is so radically different between installs?

NOTE: using 7.04_beta but this seems to affect other versions too.

---

### Post by Ateo on 2007-04-11
From dmesg:> [ 3599.476000]  CIFS VFS: No username specified
[ 3599.476000]  CIFS VFS: cifs_mount failed w/return code = -22


Does ubuntu's version of cifs not support the 'credentials' parameter? I can't think of anything else.....

---

