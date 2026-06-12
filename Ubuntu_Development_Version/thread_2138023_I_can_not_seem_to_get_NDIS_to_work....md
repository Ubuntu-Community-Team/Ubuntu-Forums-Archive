---
title: "I can not seem to get NDIS to work..."
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by Silverflyer on 2013-04-22
I took a leap and upgraded to 13.04.  So far I really like it, overall my computer is working better than before in 12.04.  The one thing that is not working is ndiswrapper.  I got it working in 12.04 by getting the NDIS 1.58 because 1.57 in the software center was not working.  I tried both the software center version and making 1.58 as before.  Software center says it is installed but it is not in the list of applications.  Without ndiswrapper, I have no wifi connection.

Thanks.

---

### Post by cariboo on 2013-04-22
Ndiswrapper was removed from the repositories, back in November, as it wasn't supported as a kernel module any more. What wireless device do you have that still needs ndiswrapper?

---

### Post by Silverflyer on 2013-04-22
Netgear WNA3100 USB Wireless adapter.  If it won't work, that will be a showstopper for me.

---

### Post by cariboo on 2013-04-23
I just did a check, and even though on the developer mailing list ndiwrapper was supposed to be removed form the repositories, it's still there. See here:

[http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=raring&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=raring&section=all)

You may need to install dkms and fakeroot, in order to install ndiswrapper.

---

### Post by Silverflyer on 2013-04-23
> **cariboo907 said:**
> I just did a check, and even though on the developer mailing list ndiwrapper was supposed to be removed form the repositories, it's still there. See here:

[http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=raring&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=raring&section=all)

You may need to install dkms and fakeroot, in order to install ndiswrapper.

That did it.  I went into Synaptic and installed ndis and all the dependencies along with fakeroot and it worked just fine.

Thank you for the help.

---

