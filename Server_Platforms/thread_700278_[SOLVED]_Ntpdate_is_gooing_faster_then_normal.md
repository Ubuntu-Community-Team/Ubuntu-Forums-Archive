---
title: "[SOLVED] Ntpdate is gooing faster then normal"
date: 2008-02-18
forum: Server Platforms
---

### Post by trymbill on 2008-02-18
I'm running Ubuntu 6.06 server and I'm getting a very strange problem.  My NTPDATE seems to be running 10 seconds for every 1 real second.  So when I issue the command: "ntpdate ntp.ubuntu.com" it shows me the correct date and time, but 10 seconds later, if I run "ntpdate" is shows me date and time almost a minute later then it should be.

So, as I said, it seems like my NTPDATE thinks every 1 second is 10 seconds (aprox.) and I've got no clue why this is happening :)

I'm running Ubuntu 6.06 server on M$ Virtual Server 2005.  If anyone has some info on this, please let me know! :confused:

---

### Post by trymbill on 2008-02-18
I found this article: [http://support.microsoft.com/Default.aspx?kbid=918461](http://support.microsoft.com/Default.aspx?kbid=918461)

I think it explains a solution to my problem :)

---

