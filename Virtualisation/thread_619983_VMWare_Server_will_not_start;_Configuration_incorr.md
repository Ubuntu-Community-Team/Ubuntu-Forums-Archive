---
title: "VMWare Server will not start; Configuration incorrect message; Gutsy"
date: 2007-11-22
forum: Virtualisation
---

### Post by tak1150 on 2007-11-22
Hi,

I just installed VMWare server 1.0.4 using [this guide]("https://help.ubuntu.com/community/VMware/Server"). Apparently it installed without a hitch, but when I try to start it, I get this message:

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

but when I re-configure this thing, all the processes finish (or so it seems to me) and I still get the same message as above when i type "vmware".
Thanks for your input!

Tak

---

### Post by Delvien on 2007-11-22
Download and run the following file (after extracted)

with the "./" precursor. It will execute the config.pl file.

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

Also, make sure you have your linux headers installed for your kernel.

---

### Post by tak1150 on 2007-11-22
> **Delvien said:**
> Download and run the following file (after extracted)

with the "./" precursor. It will execute the config.pl file.

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

Also, make sure you have your linux headers installed for your kernel.

Thanks for replying.
Sorry I forgot to add the link for the guide I used.
I actually did use that patch and it still did not work :(

---

