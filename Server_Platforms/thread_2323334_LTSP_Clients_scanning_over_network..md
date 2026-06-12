---
title: "LTSP Clients scanning over network."
date: 2016-05-04
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2016-05-04
I've got my ltsp deployed and working quite nicely. Printing is working fine to my print server. I'm stuck on the scanner though. I'm trying to set it up to work over the network as it's an HP printer / scanner / copier.

Here is my files so far.

On Server:
```
jason@micromachine:~$ cat /etc/default/saned 
# Defaults for the saned initscript, from sane-utils


# Set to yes to start saned
RUN=yes


# Set to the user saned should run as
RUN_AS_USER=saned

```

In LTSP client chroot
```
jason@micromachine:~$ cat /opt/ltsp/amd64/etc/sane.d/net.conf 
# This is the net backend config file.


## net backend options
# Timeout for the initial connection to saned. This will prevent the backend
# from blocking for several minutes trying to connect to an unresponsive
# saned host (network outage, host down, ...). Value in seconds.
# connect_timeout = 60


## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
localhost
192.168.1.240 # server hosting scanner


```


Googling is leading me to the same answers but nothing seems to be working. I know I'm overlooking something small. Ideas or suggestions, or request more config files to look at would be appreciated.

---

### Post by Tadaen_Sylvermane on 2016-05-07
Update.

After much research all day and trying different configurations and toying about I have come to the conclusion that the Sane backend needs a usb connected printer / scanner to function properly. Cups works fine with my printer being connected wirelessly over the network but nothing i try is happening with the scanner. If someone has gotten it to work I'd love to hear it. Otherwise leaving this alone till the functionality is added or I find something new to try.

---

### Post by Tadaen_Sylvermane on 2016-05-16
Updating and marking as solved.

In my case I had to install the hplip package in my chroot. I didn't have to add the printer to the user in the ltsp server, just the driver and it recognized the scanner over the network and works great.

---

