---
title: "NDM data push tool"
date: 2010-03-08
forum: Server Platforms
---

### Post by s9841121 on 2010-03-08
Hi,

I need to push files from several large servers to a mainframe directory using NDM.

Is there a free ubuntu/linux equivalent of connect:direct?

Thanks,
John.

---

### Post by kiranmurari on 2010-03-08
Hi,

   You can use LinuxDC++, which is a port of DC++ for Linux. For more info see: [https://launchpad.net/linuxdcpp](https://launchpad.net/linuxdcpp)
This already present in the repositories and you can install it from synaptic or
> $ sudo apt-get install linuxdcppAlso, you can try DCTC (Direct Connect Text Client). But this is non-interactive (No GUI/CLI) and can be used by other programs. For more info see: [http://ac2i.homelinux.com/dctc/#dctc](http://ac2i.homelinux.com/dctc/#dctc)

Hope this helps.

---

### Post by s9841121 on 2010-03-08
Apologies i take that back - after taking a look it appears this is a linux p2p protocol! Sorry but that is of no use.

I am looking for something that can do NDM file push. NDM is connect:direct, *not* direct:connect

This is old IBM mainframe protocol.

[http://en.wikipedia.org/wiki/NDM](http://en.wikipedia.org/wiki/NDM)

---

### Post by Xianath on 2010-03-09
I don't think there's a free C:D API. The ones one I've seen requires an actual C:D installation to link against. I guess it's part of the Sterling business model to vendor-lock shops using a proprietary protocol and closed-source implementation. They're still the largest fish in the segment so I guess it's worked out for them just as well as it has for you-know-who.

Do you absolutely have to use NDM? FTP/S and SFTP are both viable options for secure file transfers to and from a mainframe (FTP/S requiring some tinkering with SITE commands but you would know that). Unless you're locked out by the firewall (not uncommon in mainframe shops) you're better off with open protocols.

Cheers,
Peter

---

### Post by s9841121 on 2010-03-09
Thanks Peter.

Your right - we are currently in discussions with the fw folks.

Thanks for the advice - i thought it was worth a shot looking for an OSS option.

---

