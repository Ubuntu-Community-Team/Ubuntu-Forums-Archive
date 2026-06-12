---
title: "LTSP Autologin with refreshed clean desktop"
date: 2018-06-06
forum: Server Platforms
---

### Post by revmarkp on 2018-06-06
I've been carefully following this post about LTSP in public environment: [https://ubuntuforums.org/showthread.php?t=2177959](https://ubuntuforums.org/showthread.php?t=2177959)

I've got it working to the extent that my 12 PCs now autologin, per mac address, each to their own account. However I can't get the /opt/ltsp/ltsp-session.sh script for overwriting the individual users desktop, from the template one upon each boot, to work. 
It's implemented by 
[Default]
LDM_XSESSION = /opt/ltsp/ltsp-session.sh

in /var/lib/tftpboot/ltsp/fat_amd64/lts.conf 

When I turn that on the boot of the client gets so far then hangs. 

I'm using ubuntu server 16.04 and have created a fat amd64 client image. All the basics work fine.

Anyone else got an LTSP setup working with a clean/refreshed desktop upon boot (copied from a template?) working?

---

### Post by Emblem Parade on 2018-06-10
I'm sorry, but I haven't tried my previous work on this in several years...

Perhaps newer versions of the packages work differently. I suggest delving into the documentation and troubleshooting with the simplest setup first.

---

