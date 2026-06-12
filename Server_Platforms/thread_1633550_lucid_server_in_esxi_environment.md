---
title: "lucid server in esxi environment"
date: 2010-11-29
forum: Server Platforms
---

### Post by inphektion on 2010-11-29
I have a few linux servers in esxi and unlike in windows where i always install the vmware tools, i never do in linux.  
for the linux servers i don't need any video drivers or mouse integration (there is just a console and i only ssh in) but is there still a benefit maybe kernel/networking wise to install the vmware tools?

and what about linux-image-virtual kernel?  I never use that either but is it recommended for all servers running virtually?  any downsides to using it on a server?

---

### Post by samosamo on 2010-11-29
The virtual kernel is only for servers.  Use ubuntu-vm-builder to create vm images.  It is available in the repo's but I suggest you use the author's PPA.

Incorporate an exec script to perform the following command:
```
apt-get install --no-install-recommends linux-headers-virtual open-vm-dkms open-vm-tools
```

Reference here: [https://confluence.terena.org/display/~visser/open-vm-tools+in+Ubuntu+Lucid](https://confluence.terena.org/display/~visser/open-vm-tools+in+Ubuntu+Lucid)

---

### Post by inphektion on 2010-11-29
so you really like the open vm tools better than the ones from vmware?
even with your esx 4.1 issues?
luckily i'm still on 4.0 u1 but seems a bit hacked.

---

### Post by samosamo on 2010-12-16
I can't speak for the Desktop edition because other things come into play (Video, USB, etc drivers), but for the server edition open-vm-tools is 100% perfect.  Specifically, the Paravirtual SCSI driver and VMXNET3.  My favorite part about it is how it stays up-to-date even with kernel changes.

---

