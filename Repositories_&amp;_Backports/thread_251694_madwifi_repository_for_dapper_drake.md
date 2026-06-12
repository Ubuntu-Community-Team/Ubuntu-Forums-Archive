---
title: "madwifi repository for dapper drake"
date: 2006-09-05
forum: Repositories &amp; Backports
---

### Post by cccc on 2006-09-05
hi

I'm lokking for the madwifi or madwifi-ng repository to install on dapper drake

could I use madwifi repository for debian ?```

deb ftp://debian.marlow.dk/ sid madwifi deb-src ftp://debian.marlow.dk/ sid madwifi
```

greetings
cccc

---

### Post by superm1 on 2006-09-08
The linux2go repo actually has a ubuntu madwifi-ng pacakge.  It works for me except that suspend didn't go.  I am looking for another one as well.

---

### Post by yopnono on 2006-09-08
> **superm1 said:**
> The linux2go repo actually has a ubuntu madwifi-ng pacakge.  It works for me except that suspend didn't go.  I am looking for another one as well.

Yes I also use the linux2go package. But I have network activity all the time, if i check the network monitor.

It's from 0 - 40% activity, but in the system monitor it's only 900bytes to 1.1Kb. Even if the monitor say 40%. Strange..

Anyhow, my lan speed when using the old madwifi driver in the kernel was at maximum 1.1Mb, now it's 2.9Mb when using the new madwifi in the kernel.

---

### Post by superm1 on 2006-09-08
Does he provide sources for the linux2go package?

I might use his sources and build a svn version.

According to: [http://madwifi.org/ticket/201](http://madwifi.org/ticket/201), patch 671 has improved suspend support.  It's in SVN.

---

### Post by yopnono on 2006-09-08
> **superm1 said:**
> Does he provide sources for the linux2go package?

I might use his sources and build a svn version.

According to: [http://madwifi.org/ticket/201](http://madwifi.org/ticket/201), patch 671 has improved suspend support.  It's in SVN.

Don't know who you are asking.. But the linux2go package don't have any drivers. It only unload the old madwifi driver in the dapper kernel and load the new madwifi drivers in the dapper kernel.

And you don't need this (madwifi-ng) package if you are building new drivers from madwifi.org, it replaces the dapper driver new and old.

---

### Post by superm1 on 2006-09-08
doh.... I should have looked at the sources for his package and whats actually going on when using it.  

After work, I'll see what I come up with.

---

### Post by yopnono on 2006-09-08
> **superm1 said:**
> doh.... I should have looked at the sources for his package and whats actually going on when using it.  

After work, I'll see what I come up with.

Well it's easy, just follow the instructions at madwifi.org to remove the old drivers from the dapper kernel and build the new one from their site.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Also you should get the new wpa_supplicant as well if you are using wpa and wireless.

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

Or use this wpa_supplicant

[https://launchpad.net/distros/ubuntu/dapper/+source/wpasupplicant/+bug/47144](https://launchpad.net/distros/ubuntu/dapper/+source/wpasupplicant/+bug/47144)

---

