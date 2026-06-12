---
title: "fai -setup can't find release"
date: 2010-02-26
forum: Server Platforms
---

### Post by abraxas334 on 2010-02-26
I am trying to use fai to install a beowuld cluster, which may be a bit ambitious as I am not a very experienced linux person.
I am trying to roughly follow this guide:

[http://globopt.dsi.unifi.it/gol/cluster.html](http://globopt.dsi.unifi.it/gol/cluster.html)

but I already fail on page 3. I need to create a local debian(ubuntu) mirror, which i think i have succeeded in doing, tho i am not sure how to check that other than there are some files in the directory I have created for the mirror (7.9GB are used in my root directory which seems a little small for a mirror)

But now to the actual problem when i run fai-setup -v (which is a result of the previous miscallibration i guess)
This is the ourput i get
> 
Account $LOGUSER=fai already exists.
Make sure that all install clients can
log into this account without a password.
/var/log/fai/.ssh/known_hosts remained unchanged.
/var/log/fai/.ssh/authorized_keys created.
User account fai set up.
Using configuration files from /etc/fai
Creating FAI nfsroot in /srv/fai/nfsroot/live/filesystem.dir.
By default it needs more than 380 MBytes disk space.
This may take a long time.
Creating base system using debootstrap version 1.0.20
Calling debootstrap lenny /srv/fai/nfsroot/live/filesystem.dir [http://cdn.debian.net/debian](http://cdn.debian.net/debian)  
I: Retrieving Release
//here after a while appears an error message along the line sof
E: failed to retrieve release...

it can't retrieve the release i.e. the local mirror?

in the guide mentioned above it says something about editing two files:
> 
-> /etc/fai/fai.conf : hostname, mirror siteaddress, use of ssh activated
-> /etc/fai/make-fai-nfsroot.conf: local network iprange

how should i edit this file?
The original one looks like this:
```
# $Id: fai.conf 5526 2009-09-28 08:29:37Z lange $

# /etc/fai/fai.conf -- configuration for FAI (Fully Automatic Installation)

# how to access the fai config space
# If undefined here, make-fai-nfsroot/fai-setup will use default value
# nfs://<install server>/$FAI_CONFIGDIR
# supported URL-types: nfs, file, cvs, cvs+ssh, svn+file, svn+http,
# git, git+http, hg+http
#FAI_CONFIG_SRC=nfs://yourservername/path/to/config/space

# LOGUSER: an account on the install server which saves all log-files
# and which can change the kernel that is booted via network.
# Configure .rhosts for this account and PAM, so that root can log in
# from all install clients without password. This account should have
# write permissions for /srv/tftp/fai. For example, you can use write
# permissions for the group linuxadm. chgrp linuxadm /srv/tftp/fai;chmod
# g+w /srv/tftp/fai. If the variable is undefined, this feature is disabled.
# Define it, to enable it, eg. LOGUSER=fai
LOGUSER=

# set protocol type for saving logs. Values: ssh, rsh, ftp
FAI_LOGPROTO=ssh

# Access to Debian mirror via NFS mounted directory
# If FAI_DEBMIRROR is defined, install clients mount it to $MNTPOINT
#FAI_DEBMIRROR=yournfs debianmirror:/path/to/debianmirror


# The following variables are read only for almost every user.
# Do not change them unless you know what you are doing!

# mount point where the mirror will be mounted
MNTPOINT=/media/mirror

# the local configuration directory on the install client
FAI=/var/lib/fai/config

```

I tried chaning things but somehow it didn't work and I don't really understand the documentation. 
Any help would be greatly appreciated! Thanks :)

---

### Post by surfer on 2010-05-19
i'm also currently struggling to get ubuntu lucid installed via FAI.

you did not seem to adjust /etc/fai/apt/sources.list . there you should enter your apt-mirror. this will most likely be something of the form
```
deb http://your.mirror.host/ubuntu/ lucid main restricted universe multiverse
```
and more lines like it.

---

