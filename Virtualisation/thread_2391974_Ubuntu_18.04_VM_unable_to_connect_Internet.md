---
title: "Ubuntu 18.04 VM unable to connect Internet"
date: 2018-05-15
forum: Virtualisation
---

### Post by satimis on 2018-05-15
Hi all,

Host - ubuntu 16.04 desktop
VM - ubuntu 18.04 desktop
Oracle VirtualBox

VM can ping Host and gateway, but unable to connect Internet.  Finally I found the solution on following link;
Virtualbox Ubuntu 17.04 cannot connect to the internet
[https://askubuntu.com/questions/950470/virtualbox-ubuntu-17-04-cannot-connect-to-the-internet](https://askubuntu.com/questions/950470/virtualbox-ubuntu-17-04-cannot-connect-to-the-internet)

After running;
$ sudo ifconfig enp0s3 up
and
$ sudo dhclient enp0s3 -v
(enp0s3 in my case)

then VM can connect Internet.

Each time after booting up the VM I need to run those commands again.  Is there any file where I can put those commands and they'll be evoked on booting.
(remark: rc.local is not on Ubuntu 18.04)

Thanks in advance

It happens the same on KVM.

Regards
satimis

---

### Post by satimis on 2018-05-15
Hi all,

Problem solved!

Please refers to following article;
How to Enable /etc/rc.local with Systemd
[https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)

Re: The Solution

My /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig enp0s3 up

dhclient enp0s3 -v
exit 0

```

On booting rc.local will be executed

Regards
satimis

---

