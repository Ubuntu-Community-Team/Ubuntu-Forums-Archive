---
title: "sources.list -- should i modify?"
date: 2011-05-30
forum: Server Platforms
---

### Post by sneakyimp on 2011-05-30
I've got an amazon EC2 instance running Natty 11.04.  I want to harden this server and make sure it's very secure as I ultimately will be handling sensitive data.  I'm wondering what should be in /etc/apt/sources.list.  Can anyone comment on these contents?  Or, better yet, recommend a good secure sources.list file?

```

## Note, this file is written by cloud-init on first boot of an instance
## modifications made here will not survive a re-bundle.
## if you wish to make changes you can:
## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
##     or do the same in user-data
## b.) add sources in /etc/apt/sources.list.d
## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
#

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty main
deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-updates main
deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty universe
deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty multiverse
# deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty multiverse
# deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-updates multiverse
# deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us-west-1.ec2.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

deb http://security.ubuntu.com/ubuntu natty-security main
deb-src http://security.ubuntu.com/ubuntu natty-security main
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
# deb http://security.ubuntu.com/ubuntu natty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

```

---

