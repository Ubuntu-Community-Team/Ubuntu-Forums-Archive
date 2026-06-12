---
title: "setting up tftp server"
date: 2011-03-16
forum: Server Platforms
---

### Post by sergio_arod on 2011-03-16
Hi, I am fairly new to ubuntu server, I want to setup a tftp server to mount a new kernel in a DaVinci platform.
I was following the guide in this page [https://linuxlink.timesys.com/docs/linux_tftp](https://linuxlink.timesys.com/docs/linux_tftp), but accidentally I remove the xinetd.conf file. So I think that maybe removing and reinstalling xinetd the problem will be solved, but instead of that  I can't completely remove xinetd and the follow message is print in the terminal

Removing xinetd ...
invoke-rc.d: unknown initscript, /etc/init.d/xinetd not found.
dpkg: error processing xinetd (--remove):
 subprocess installed pre-removal script returned error exit status 100
invoke-rc.d: unknown initscript, /etc/init.d/xinetd not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 xinetd
E: Sub-process /usr/bin/dpkg returned an error code (1)

with that problem I can't start the service or stop it, I am blocked in the configuration of tftp server

I will be eternally grateful if you could help me

---

### Post by sherl0k on 2011-03-16
using tftpd-hpa as your server, xinetd isn't required.


my /etc/default/tftpd-hpa looks like this:

```
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="-s -vvv"
```

I created */var/lib/tftpboot* and chmod'd the files inside as needed for read/write/execute access.

one should be able to *touch /etc/init.d/xinetd* to at least create the file; this way dpkg won't yell about it not being there.

---

### Post by sergio_arod on 2011-03-17
Sherl0k thank you for answer so fast
I had install the thtpd-hpa package an edit the file /etc/default/thtpd-hpa

```
# /etc/default/tftpd-hpa

RUN_DAEMON="yes"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftpboot"
TFTP_ADDRESS="192.168.0.5:69"
TFTP_OPTIONS="-s -vvv"
```

but when I use the command ps aux | grep tftp

the terminal don't shown any server running. And also when I test the tftp with localhost, just get a transfer time out. What else I have to do to make the server to run

Thanks a lot for your help

---

### Post by Lars Noodén on 2011-03-18
I've used the built-in tftp server in [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) and the same program to serve the boot images.  Turning on tftp in dnsmasq is just a matter of uncommented 2 or 3 lines.

---

### Post by sergio_arod on 2011-03-18
Thanks Lars Noodén, with the dnsmasq the server is working

---

