---
title: "Did I just upgrade my system by accident?"
date: 2011-02-11
forum: Server Platforms
---

### Post by TC!! on 2011-02-11
I was running 10.04 LTS and had decided to stick to the LTS versions as I'm now running my machine as a server and don't want to be updating regularly.

Every time I logged in via SSH I got a message telling me there where packages to update including a security update. So I did a search to find out how to perform an update on Ubuntu server from the command line. What I found was to do this:

sudo apt-get update
sudo apt-get dist-upgrade

After doing that I rebooted but now my machine gives me this message:
init: ureadahead-other main process (794) terminated with status 4
Your disk drives are being checked for errors, this may take some time
Press C to cancel all checks currently in progress

I'm not pressing C yet and leaving it alone to finish, but I noticed when the machine booted that one of the options for booting talked about Ubuntu 10.10, so I'm worried that I've updated from 10.04 LTS to 10.10 by accident?

Any help greatly appreciated.

---

### Post by BkkBonanza on 2011-02-11
Yes. "dist-upgrade" will upgrade your kernel and other files to the next or current distribution (which is 10.10 now). What you wanted to do after "update" was just "upgrade" (without dist).

I don't think it's too easy to reverse that. As far as I know it's a manual process but perhaps someone else knows better how to downgrade.

Well, it's not too hard to remove the kernel and at least go back to your previous one but if a bunch of other packages got upgraded too then it may be tricky to know what to reverse. I'd guess the logs could help with that.

Try looking in /var/log/dist-upgrade directory. And, /var/log/apt/history.log

---

### Post by TC!! on 2011-02-11
Now it's finished checking disks it tells me the version is 10.04.2 LTS. When I entered the dist-update command I saw the list of files to update and none of it looked to serious, things like mysql which is why I let it go ahead an do it. That's it, it said it would update about 60 odd packages and install 1 new one which didn't feel like a full update to me.

Any other way I can check, it seemed very quick to have done a full update.

/var/log/dist-upgrade is empty, /var/log/apt/history.log looks like this:

```
Start-Date: 2011-02-02  06:28:32
Install: linux-image-2.6.32-28-server (2.6.32-28.55), linux-headers-2.6.32-28-server (2.6.32-28.55), linux-headers-2.6.32-28 (2.6.32-28.55)Upgrade: linux-server (2.6.32.27.29, 2.6.32.28.32), subversion (1.6.6dfsg-2ubuntu1, 1.6.6dfsg-2ubuntu1.1), linux-headers-server (2.6.32.27.29, 2.6.32.28.32), libsvn1 (1.6.6dfsg-2ubuntu1, 1.6.6dfsg-2ubuntu1.1), linux-image-server (2.6.32.27.29, 2.6.32.28.32), linux-libc-dev (2.6.32-27.49, 2.6.32-28.55)
End-Date: 2011-02-02  06:29:39

Start-Date: 2011-02-04  06:29:14
Upgrade: libpq5 (8.4.5-0ubuntu10.04, 8.4.7-0ubuntu0.10.04)
End-Date: 2011-02-04  06:29:17

Start-Date: 2011-02-08  21:03:40
Install: rar (3.9.b2-1)End-Date: 2011-02-08  21:03:45

Start-Date: 2011-02-11  12:09:26
Install: bc (1.06.95-2)Upgrade: apt-transport-https (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), openssh-server (5.3p1-3ubuntu4, 5.3p1-3ubuntu5), libc-bin (2.11.1-0ubuntu7.7, 2.11.1-0ubuntu7.8), uuid-runtime (2.17.2-0ubuntu1.10.04.1, 2.17.2-0ubuntu1.10.04.2), base-files (5.0.0ubuntu20.10.04.2, 5.0.0ubuntu20.10.04.3), unattended-upgrades (0.55ubuntu4, 0.55ubuntu5), libblkid1 (2.17.2-0ubuntu1.10.04.1, 2.17.2-0ubuntu1.10.04.2), libcomerr2 (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1), smbclient (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), mysql-server (5.1.41-3ubunt
u12.8, 5.1.41-3ubuntu12.9), util-linux (2.17.2-0ubuntu1.10.04.1, 2.17.2-0ubuntu1.10.04.2), libapparmor-perl (2.5.1-0ubuntu0.10.04.2, 2.5.1-0ubuntu0.10.04.3), smbfs (3.4.7~dfsg-1ub
untu3.2, 3.4.7~dfsg-1ubuntu3.3), screen (4.0.3-14ubuntu1, 4.0.3-14ubuntu1.2), at (3.1.11-1ubuntu5, 3.1.11-1ubuntu5.1), libwbclient0 (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3),
 mysql-server-core-5.1 (5.1.41-3ubuntu12.8, 5.1.41-3ubuntu12.9), libpam-smbpass (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), libpam-ck-connector (0.4.1-3ubuntu1, 0.4.1-3ubuntu2
), e2fsprogs (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1), grub-pc (1.98-1ubuntu9, 1.98-1ubuntu10), libmysqlclient16 (5.1.41-3ubuntu12.8, 5.1.41-3ubuntu12.9), apt-utils (0.7.25.3ubuntu9
.1, 0.7.25.3ubuntu9.3), update-manager-core (0.134.10, 0.134.11), libck-connector0 (0.4.1-3ubuntu1, 0.4.1-3ubuntu2), linux-firmware (1.34.1, 1.34.3), samba-common (3.4.7~dfsg-1ubu
ntu3.2, 3.4.7~dfsg-1ubuntu3.3), coreutils (7.4-2ubuntu2, 7.4-2ubuntu3), udev (151-12, 151-12.3), apt (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), apparmor-utils (2.5.1-0ubuntu0.10.04.2
, 2.5.1-0ubuntu0.10.04.3), samba-doc (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), openssh-client (5.3p1-3ubuntu4, 5.3p1-3ubuntu5), bsdutils (2.17.2-0ubuntu1.10.04.1, 2.17.2-0ub
untu1.10.04.2), mysql-client-core-5.1 (5.1.41-3ubuntu12.8, 5.1.41-3ubuntu12.9), samba (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), nfs-kernel-server (1.2.0-4ubuntu4, 1.2.0-4ubu
ntu4.1), tar (1.22-2, 1.22-2ubuntu1), e2fslibs (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1), libapparmor1 (2.5.1-0ubuntu0.10.04.2, 2.5.1-0ubuntu0.10.04.3), libudev0 (151-12, 151-12.3), 
libplymouth2 (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2), libuuid1 (2.17.2-0ubuntu1.10.04.1, 2.17.2-0ubuntu1.10.04.2), libc6-dev (2.11.1-0ubuntu7.7, 2.11.1-0ubuntu7.8), apparmor (2.5.1-0ub
untu0.10.04.2, 2.5.1-0ubuntu0.10.04.3), tzdata (2010k-0ubuntu0.10.04, 2010o-0ubuntu0.10.04), plymouth-theme-ubuntu-text (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2), man-db (2.5.7-2, 2.5.7-
2ubuntu1), rsyslog (4.2.0-2ubuntu8, 4.2.0-2ubuntu8.1), mount (2.17.2-0ubuntu1.10.04.1, 2.17.2-0ubuntu1.10.04.2), libss2 (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1), samba-common-bin (3
.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), winbind (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.3), grub-common (1.98-1ubuntu9, 1.98-1ubuntu10), ureadahead (0.100.0-4.1.2, 0.100
.0-4.1.3), upstart (0.6.5-7, 0.6.5-8), libc-dev-bin (2.11.1-0ubuntu7.7, 2.11.1-0ubuntu7.8), mountall (2.15, 2.15.3), libc6 (2.11.1-0ubuntu7.7, 2.11.1-0ubuntu7.8), gzip (1.3.12-9ub
untu1, 1.3.12-9ubuntu1.1), portmap (6.0.0-1ubuntu2, 6.0.0-1ubuntu2.1), python-lazr.restfulclient (0.9.11-1ubuntu1, 0.9.11-1ubuntu1.1), nfs-common (1.2.0-4ubuntu4, 1.2.0-4ubuntu4.1
), mysql-common (5.1.41-3ubuntu12.8, 5.1.41-3ubuntu12.9), mysql-server-5.1 (5.1.41-3ubuntu12.8, 5.1.41-3ubuntu12.9), plymouth (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.2), mysql-client-5.1 
(5.1.41-3ubuntu12.8, 5.1.41-3ubuntu12.9), landscape-common (1.5.2.1-0ubuntu0.10.04.0, 1.5.5.1-0ubuntu0.10.04.0), consolekit (0.4.1-3ubuntu1, 0.4.1-3ubuntu2)
End-Date: 2011-02-11  12:49:00

```

---

### Post by ajgreeny on 2011-02-11
It sure sounds as if you just upgraded 10.04 to the newest version of 10.04.2.   How is your software sources update tab set, as you can choose what updates are shown there, as in my screenshot.  Mine is set to **Never** as I always do a clean install, though I am not sure if that overrides the command line upgrades.

You can also double check you OS version with command ```
lsb_release -a
```which should give output of```
username@ubuntu1004:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid
```

---

### Post by TC!! on 2011-02-11
I've got the same:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

I haven't installed the Desktop at all, I wanted my installation to be as simple as possible and do all my control via remote shell. I've looked at /etc/apt/sources.list and it all relates to lucid so I guess it wouldn't upgrade me to 10.10 because of that.

I just realised what might have happened, I've got two bootable Ubuntu drives in my machine and the other one is 10.10. Is the GRUB menu intelligent enough to pick that up?

---

### Post by iissmart on 2011-02-11
Check your /etc/apt/sources.list file. Doing 'apt-get dist-upgrade' will not "upgrade" your system to the newest Ubuntu version unless you modify that file to point to the new release. In my case I am running 8.04 LTS still and I do dist-upgrade all the time, but since my sources.list file points to 'hardy' it will remain at 8.04.

All dist-upgrade does is just do better dependency resolution when upgrading packages, and update to *minor* release versions like 8.04.1, 8.04.2, etc.

---

### Post by TC!! on 2011-02-11
> **iissmart said:**
> Check your /etc/apt/sources.list file. Doing 'apt-get dist-upgrade' will not "upgrade" your system to the newest Ubuntu version unless you modify that file to point to the new release. In my case I am running 8.04 LTS still and I do dist-upgrade all the time, but since my sources.list file points to 'hardy' it will remain at 8.04.

All dist-upgrade does is just do better dependency resolution when upgrading packages, and update to *minor* release versions like 8.04.1, 8.04.2, etc.

Superb, thanks for all the help, looks like I didn't do anything too stupid.

So in the future should I use dist-upgrade or just upgrade in the future?

---

### Post by iissmart on 2011-02-11
They're the same for the most part. If you run 'upgrade' and it complains about an incorrect dependency and won't install an update, running 'dist-upgrade' will fix that.

Personally, I always do 'dist-upgrade'. Can't hurt anything, it just avoids the extra step of running 'upgrade', noticing the conflict, then running 'dist-upgrade'.

---

### Post by snowpine on 2011-02-11
I always use "dist-upgrade" rather than "upgrade." Type "man apt-get" if you'd like to read the exact differences, but basically "dist-upgrade" upgrades everything (same as "aptitude full-upgrade") and "upgrade" skips any upgrades that require installing/removing a package, such as a new kernel version (same as "aptitude safe-upgrade").

The command to upgrade from 10.04 to 10.10 is "sudo do-release-upgrade".

---

