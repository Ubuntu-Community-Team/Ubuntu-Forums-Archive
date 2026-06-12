---
title: "Very slow speeds with Mac Pro talking to a Ubuntu Raid Server"
date: 2009-10-01
forum: Server Platforms
---

### Post by gelek on 2009-10-01
So I have an environment where mainly macs and a couple Windows PCs use a Ubuntu Raid 50 file server. When attempting to access the server the Mac Pros take typically 1 minute to view the file structure and sometimes timeout, the Windows machines take about 1 second. Also this seems to affect copying and deleting which takes much longer from the Mac side. The server is setup simply with a samba mount to allow access.
 
Any suggestions for how I can attack this issue? Any help would be greatly appreciated.
 
Colin
 
Ubuntu 8.04.1

---

### Post by openfly on 2009-10-01
I'd share to the macs via NFS.

Samba is kinda sketchy on the macs as they hacked it up something awful to make open directory work.

---

### Post by Xianath on 2009-10-02
Grab a network capture with Wireshark (on the Mac and Windows) or tcpdump (on the Ubuntu server) and let's have a look at what the two clients are doing differently. Or, like the other poster said, use NFS. Your best shot might as well be AFP as provided by the netatalk package (see [http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)). Or you may want to give another CIFS client a shot, e.g. Sharity ([http://www.obdev.at/products/sharity/index.html](http://www.obdev.at/products/sharity/index.html)). You have a lot of options -- gotta love the open source world :)

HTH,
Peter

---

### Post by gelek on 2009-10-08
I setup nfs and it increased speeds by about 20% but that is still substancially slower then the other machines.  I guess I will try your other suggestion.
 
Colin

---

