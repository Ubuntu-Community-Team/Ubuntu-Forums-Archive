---
title: "Mounting USB for Apple Time Machine BackUps"
date: 2011-05-01
forum: Server Platforms
---

### Post by Sulcalibur on 2011-05-01
I'm trying to follow various ways to setup a Time Machine drive on my Ubuntu 'natty' server. I am at the stage now though where I can't seem to find the external USB HDD anywhere. I have it partitioned into two and cannot find anything to do with it.

When I check ot doesn't show up in the memory either. Is there a way to mount it or find it?

Thanks

---

### Post by Lars Noodén on 2011-05-02
Do you have HFS support set up?  That is the first step;

If not, the packages hfsplus, hftsutils and hfsprogs provide it.

---

### Post by topnaught on 2011-05-02
If you haven't already seen it, I found the tutorial "How to Make Ubuntu A Perfect Mac File Server and Time Machine Volume" on Kremalicious to very helpful to setting up a pair of Time Machine volumes on an Xubuntu machine.  Originally done under Xubuntu 10.10, now upgraded to Xubuntu 11.04.

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)[URL="http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/"]
[/URL]

---

### Post by Lars Noodén on 2011-05-02
> **topnaught said:**
> If you haven't already seen it, I found the tutorial "How to Make Ubuntu A Perfect Mac File Server and Time Machine Volume" on Kremalicious to very helpful to setting up a pair of Time Machine volumes on an Xubuntu machine.  Originally done under Xubuntu 10.10, now upgraded to Xubuntu 11.04.

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)[URL="http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/"]
[/URL]

That's an interesting solution using Netatalk instead of HFS.

---

