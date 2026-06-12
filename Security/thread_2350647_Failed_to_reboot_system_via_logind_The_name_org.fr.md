---
title: "Failed to reboot system via logind: The name org.freedesktop.PolicyKit1 was not provi"
date: 2017-01-26
forum: Security
---

### Post by milty456 on 2017-01-26
Hi,

I'm trying to run a script that reboots my system from a non root user.
I was informed that the following should work:

Script file:
#!/bin/bash
sudo reboot

I edited the sudoers file with this:
openhab  ALL:NOPASSWD: /sbin/reboot

I also set the UID on the script file like this:
[http://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/](http://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/)

The file will not run under the openhab user's context:
richard@odroid:~$ sudo --user=openhab reboot
Failed to set wall message, ignoring: The name org.freedesktop.PolicyKit1 was not provided by any .service files
Failed to reboot system via logind: The name org.freedesktop.PolicyKit1 was not provided by any .service files
Failed to start reboot.target: The name org.freedesktop.PolicyKit1 was not provided by any .service files
See system logs and 'systemctl status reboot.target' for details.
Failed to open /dev/initctl: Permission denied
Failed to talk to init daemon.


I don't think i have polkit installed; do i need it installed?  will it need further configuration to work?
I looked into polkit, and the directory where it is supposed to be is not present.  Unsure what I'm doing at this juncture.

Thanks

---

### Post by ajgreeny on 2017-01-26
Hi milty456, and welcome to the forums.
Which version of Ubuntu is this, and is it a server with no GUI to use as GUI commands will not need root permissions for a non admin user to shutdown or reboot as far as I'm aware.

GUI or not, as soon as you added **sudo** to the **reboot** command in the script it became a one that needs root permissions, and though you have tried to remove the need for a password in your /etc/sudoers file something appears to have gone wrong.
I am no expert in editing sudoers to change such things so will leave that to others

However, in 16.04 a user can simply issue the command **reboot** without the sudo requirement, to reboot the machine.
There are situations where it will still not work, for example if other users are still logged in, but if nothing untoward is going on you may find that the command **reboot** in the script will do what you want.

---

### Post by milty456 on 2017-01-26
Thanks for the reply
Ubuntu 16.04 with no gui

I tried that and it didn't work either.

Essentially i run my automation system on this box.  It has a user "openhab" that it runs under.
I can execute other scripts right now(general file copy stuff) via shell scripts through the automation system
This one has been a problem.

---

