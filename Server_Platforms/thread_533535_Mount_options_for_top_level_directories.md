---
title: "Mount options for top level directories"
date: 2007-08-24
forum: Server Platforms
---

### Post by Lars Noodén on 2007-08-24
I'm looking at the top of the directory tree in a fresh installation of Kubuntu 7.04 and wonder about the minimum mount options (e.g. from /etc/fstab) needed for each.  The idea would be to then group them onto separate partitions according to required mount options -- without breaking anything.

e.g. /home and /var can be rw,noexec,nodev

Some require read/write, others exec, others devices.  What are the requirements for these directories?  Or where can I find the requirements?

        /
        /opt
        /boot
        /sys
        /usr
        /media
        /dev
        /lost+found
        /proc
        /root
        /lib
        /sbin
        /mnt
        /etc
        /initrd
        /srv
        /home
        /bin

---

### Post by kidders on 2007-08-25
Hi there,

There is only a very limited number of situations where doing something like this would be sensible, so hopefully you know what you're doing! In general terms, Ubuntu is probably the wrong distro to be doing this sort of thing with.

> **Lars Noodén said:**
> e.g. /home and /var can be rw,noexec,nodevOrdinarily, neither of these should be "noexec", unless you are running a server on which you wish to *very* heavily curtail the kinds of things people can do.

Additionally, you should not attempt to create /etc/fstab entries for the following:
[LIST]
[*]/media
[*]         /lost+found
[*]         /mnt[/LIST]
A few common security-oriented mount options are...

**[no]dev**
[SIZE=1]You need to give a moment's consideration to applying "nodev" to something. Using it is generally unnecessary, in any case.[/SIZE]

**[no]exec**
[SIZE=1]Whether "noexec" is appropriate is another one that isn't always immediately obvious. For instance, it may or may not be wise to apply it to /etc. Note that it *is* possible to maliciously circumvent this mount option.[/SIZE]

**[no]auto**
[SIZE=1]"noauto" is most commonly applied to /boot, although Ubuntu may behave unpredictably if you do so.[/SIZE]

**[no]suid**
[SIZE=1]If you want to cripple unprivileged users (which is quite possible on highly sensitive servers), you could consider applying "nosuid" to a few things.[/SIZE]

[B]rw/ro
[/B][SIZE=1]Aside from /boot, these options are not normally used outside of the bootup process. They are handy for high-risk data recovery, etc.[/SIZE]

Is that any help?

---

