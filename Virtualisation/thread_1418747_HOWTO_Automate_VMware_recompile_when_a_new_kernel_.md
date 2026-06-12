---
title: "HOWTO Automate VMware recompile when a new kernel arrives"
date: 2010-03-01
forum: Virtualisation
---

### Post by dcstar on 2010-03-01
If you run VMware Server and install a new kernel, the VMware setup has to be run again to hook into the new kernel - here is a way to automate the process (I put all my scripts in my /home tree because that is preserved between Ubuntu installs in a separate filesystem):

On my Ubuntu 9.04 system I created a file (called "VMware-update.sh") in my Home folder tree where I keep all my scripts, then:

```
chmod 755 VMware-update.sh
```

Then put this in the file:
```
#!/bin/bash

if [ ! -e /lib/modules/`uname -r`/misc/.vmware_installed ]; then
        /usr/bin/vmware-config.pl -d EULA_AGREED=yes

        touch /lib/modules/`uname -r`/misc/.vmware_installed
fi
```
Then:
```
sudo gedit /etc/rc.local
```
and add this before the "exit 0" at the end of the file:
```
/home/your-home-path-to-script/VMware-update.sh
```
and save the changes.

Now on each boot-up it will quickly check for a new kernel and update your VMware Server setup to use it using default answers to all the prompts (the same answers you initially input when you last ran it manually).

You will only need to make the rc.local changes if you install a new Ubuntu version and retain your /home in a separate filesystem (like many of us do).

This probably should be added to the Mega-thread (if this info is not already there).

---

