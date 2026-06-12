---
title: "Can't boot guest centos in graphic mode"
date: 2017-11-01
forum: Virtualisation
---

### Post by danielsender on 2017-11-01
I had a perfectly running 5.0.40_Ubuntu r115130 in my 16.04 system. The guest is Centos 7. After a Centos update, the guest refuses to boot in graphic mode, the console jumps back and forth between different window sizes. I can access the guest by ssh into its fixed IP. I tried mounting the guest additions but I keep getting the error [COLOR=#000000][FONT=&quot]NS_ERROR_FAILURE (0x80004005).
[/FONT][/COLOR]
I read about running '/etc/init.d/vboxdrv setup' but is not installed in my host. I attached the Xorg.0.log file in [http://paste.ubuntu.com/25866782/](http://paste.ubuntu.com/25866782/) and the /var/log/messages is in [http://http://pastebin.centos.org/409496/](http://http://pastebin.centos.org/409496/) .

Many thanks in advance.

---

### Post by danielsender on 2017-11-01
I uploaded the latest VM log file in [http://paste.ubuntu.com/25867834/](http://paste.ubuntu.com/25867834/), perhaps an expert can figure this out.

Thanks.

---

### Post by &amp;KyT$0P# on 2017-11-01
That version of VirtualBox is too old to run the latest CentOS 7.  You need [the latest VirtualBox 5.1.x version]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_1").

You will need to completely purge the installed VirtualBox before installing VirtualBox 5.1.  This should not delete your VMs.

---

### Post by danielsender on 2017-11-01
As I said before, Centos 7 was running fine with 5.0 prior to the Centos update. I see listed in synaptic virtualbox up to 5.2 however the other packages such the extension pack and guest additions only show up to 5.0

---

### Post by danielsender on 2017-11-01
Can some expert take a look at the VM log file that I uploaded and tell me what the problem is?

Thanks.

---

### Post by &amp;KyT$0P# on 2017-11-02
> **danielsender said:**
> As I said before, Centos 7 was running fine with 5.0 prior to the Centos update. 
Yep, it would (more on this in a moment).

> I see listed in synaptic virtualbox up to 5.2 however the other packages such the extension pack and guest additions only show up to 5.0
Do you have Oracle's repository set up?  If so, the package you're looking for is [FONT=Courier New]virtualbox-5.1[/FONT].  Nearly all the other VirtualBox packages are included directly in this one.  Only the Extension Pack will need to be downloaded and installed separately, from the link I posted.

> **danielsender said:**
> Can some expert take a look at the VM log file that I uploaded and tell me what the problem is?

Thanks.
The old version of VirtualBox Guest Additions is incompatible with the latest CentOS 7.  Again, you need to upgrade VirtualBox.

---

### Post by danielsender on 2017-11-02
OK - I will set up the VM repository and upgrade. I see that the latest version is 5.2, is that also OK for Centos 7?

---

### Post by ajgreeny on 2017-11-02
I do not know about CentOS but I could not get the guest additions of 5.2 to work properly with Debian 9. Whatever I tried it would not go to full screen which is how I like to run my VMs.
I did follow the info about the guest additions failing in 5.2 and used the updated GA ISO available direct from Oracle but still no luck so I went back to VBox 5.1 which works properly for all my 6 VMs.

---

### Post by danielsender on 2017-11-02
I installed 5.1.30 from the oracle site and the installation, including its extension pack went OK, however the behavior is exactly the same as before. As it was booting I tried to install the guest additions but I was never able to see if it did. The black screen jumps between two sizes and it never settles. I uploaded the VBox.log in [http://paste.ubuntu.com/25873861/](http://paste.ubuntu.com/25873861/) and the Xorg.0.log of the guest in [http://paste.ubuntu.com/25873904/](http://paste.ubuntu.com/25873904/). I'm really hard pressed to do work on this machine so I would really appreciate any help.

Daniel

---

### Post by &amp;KyT$0P# on 2017-11-02
> **danielsender said:**
> As it was booting I tried to install the guest additions but I was never able to see if it did. 
Can you try installing the 5.1.30 Guest Additions from text mode?  Insert the Guest Additions CD into the VM, manually mount it if it doesn't auto-mount, then just run the [FONT=Courier New]VBoxLinuxAdditions.run[/FONT] script as root.  When it's done, eject the Guest Additions CD and reboot the guest.

---

### Post by danielsender on 2017-11-02
I ran the script three times, the first time gives the following transaction: ```
sudo ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 5.1.30 Guest Additions for Linux...........
This program must be run with administrator privileges.  Aborting
[daniel@vivaldi mnt]$ sudo !!
sudo ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 5.1.30 Guest Additions for Linux...........
VirtualBox Guest Additions installer
Removing installed version 5.0.40 of VirtualBox Guest Additions...
Removing existing VirtualBox non-DKMS kernel modules[  OK  ]


Broadcast message from systemd-journald@vivaldi (Thu 2017-11-02 16:10:57 PDT):


dracut[6869]: dracut: creation of /boot/initramfs-3.10.0-327.28.3.el7.x86_64.img failed




Message from syslogd@vivaldi at Nov  2 16:10:57 ...
 dracut:dracut: creation of /boot/initramfs-3.10.0-327.28.3.el7.x86_64.img faile
```

The other two times was the same except that I was not getting the "dracut" message. But in all these cases I had to kill the process since it was hanging for ever.

---

### Post by QIII on 2017-11-02
Since Centos was updated, it might be worth your while to review [https://www.if-not-true-then-false.com/2010/install-virtualbox-guest-additions-on-fedora-centos-red-hat-rhel/](https://www.if-not-true-then-false.com/2010/install-virtualbox-guest-additions-on-fedora-centos-red-hat-rhel/) to ensure you have covered all the bases.

---

### Post by danielsender on 2017-11-02
The fourth attempt to install appeared to be succesful, it took 20 minutes and gave me the following output: ```
sudo ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 5.1.30 Guest Additions for Linux...........
VirtualBox Guest Additions installer
Removing installed version 5.0.40 of VirtualBox Guest Additions...
Removing existing VirtualBox non-DKMS kernel modules[  OK  ]
Copying additional installer modules ...
Installing additional modules ...
vboxadd.sh: Starting the VirtualBox Guest Additions



```

I proceeded to unmount the guest additions image and restarted the VM. The only difference is that one of the sizes of the screens is larger than before, probably the same size that I had configured when it was working.

---

### Post by danielsender on 2017-11-02
Although I don't know how to interpret the contents of the Xorg.0.log file ([http://paste.ubuntu.com/25876346/](http://paste.ubuntu.com/25876346/)) I can see that is flipping from one size to the other and it also appears that there are a few errors (EE). But I don't know which one is causing the problem.

---

