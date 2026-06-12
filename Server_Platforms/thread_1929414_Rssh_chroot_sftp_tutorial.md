---
title: "Rssh chroot sftp tutorial"
date: 2012-02-22
forum: Server Platforms
---

### Post by MILxDOT on 2012-02-22
```

RSSH CHROOT SFTP TUTORIAL

INSTALL UBUNTU SERVER 11.10 amd64 WITH ONLY OPTIONAL OPENSSH PACKAGE

ESCALATE TO SUPER USER
sudo -i

APPLY ALL AVAILABLE UPDATES
apt-get update
apt-get dist-upgrade

RESTART THE SERVER
/sbin/shutdown now -r

ESCALATE TO SUPER USER
sudo -i

REMOVE ANY OLD PACKAGES
apt-get update
apt-get dist-upgrade
apt-get autoremove

INSTALL RSSH
apt-get install rssh

CONFIGURE RSSH
vi /etc/rssh.conf
uncomment
allowsftp

uncomment and change chrootpath to:
chrootpath = /home/chroot

CHANGE TO /root directory
cd /root

COPY THE EXAMPLE mkchroot.sh SCRIPT TO ROOT DIR
cp /usr/share/doc/rssh/examples/mkchroot.sh .

CHANGE PERMISSION ON THIS SCRIPT
chmod 755 mkchroot.sh

CREATE THE CHROOT DIRECTORY
mkdir -p /home/chroot

EDIT THE mkchroot.sh SCRIPT AND MODIFY THE LIBNSS STUFF FOR UBUNTU 11.10
replace all instances related to libnss from:
/lib/libnss_compat*:
/lib/libnss_files*:

TO:

/lib/x86_64-linux-gnu/libnss_compat*:
/lib/x86_64-linux-gnu/libnss_files*:

save and exit

RUN THE SCRIPT TO CREATE THE CHROOT FILES
./mkchroot.sh /home/chroot

Now make rssh a valid shell by running the command:
add-shell /usr/bin/rssh

CREATE THE NEW HOME DIR WITHIN THE CHROOT DIR
mkdir /home/chroot/home

ADD A TEST USER
useradd -m -d /home/chroot/home/joe -s /usr/bin/rssh joe

passwd joe

COPY THAT LAST LINE OF ETC PASSWD TO THE ETC PASSWD WITHIN CHROOT ETC
tail -1 /etc/passwd >> /home/chroot/etc/passwd

Next we need to set up logging:
vi /etc/default/rsyslog

CHANGE THIS:
RSYSLOGD_OPTIONS="-c5"

TO:

RSYSLOGD_OPTIONS="-c5 /home/chroot/dev/log"

RESTART RSYSLOGD:
/etc/init.d/rsyslog restart

CHANGE PERMISSIONS ON RSSH_CHROOT_HELPER
chmod u+s /usr/lib/rssh/rssh_chroot_helper

SET THE HOME-CHROOT-HOME DIRECTORY TO 711 SO THAT USERS CANNOT SEE WHO ELSE IS ON THE SYSTEM VIA SFTP
chmod 711 /home/chroot/home

Also set your user's home directories to chmod 771 after you add them

MAKE SURE YOU EDIT THE ETC PASSWD FILE IN CHROOT AND REMOVE ANY REGULAR USER AND SYSTEM ACCOUNTS FOR ADDED SECURITY

Feel free to critique or contribute


```

---

### Post by MILxDOT on 2012-02-23
Disregard the above rssh tutorial and just use the built in SFTP subsystem per this tutorial:

[http://www.serverubuntu.it/SFTP-chroot](http://www.serverubuntu.it/SFTP-chroot)

It is better because the sftp user will not even have access the the files that mkchroot.sh creates in the above rssh tutorial that I did.

---

### Post by Lars Noodén on 2012-02-23
Just to note from the manual page for [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) ,"*All components of the pathname must be root-owned directories that are not writable by any other user or group.*"  It's not mentioned in the tutorial but is important when getting chroot to work.  Often, chrooting to /home is enough.

---

### Post by c_schmitz on 2012-02-24
Yeah, but using the OpenSSH SFTP limits you to SFTP and cannot be RSYNC'd which is a major letdown. 

I wish there would be proper instructions out there how to get RSSH properly working on Ubuntu - all instructions i found so far ended that I either was not able to login (this one) or was able to login but not jailed in CHROOT as expected :(

Thank you for trying, though.

---

### Post by Lars Noodén on 2012-02-25
You can still chroot rsync, but you have to include all the dependencies in the chroot tree.

---

