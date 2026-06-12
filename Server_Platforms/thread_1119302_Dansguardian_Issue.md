---
title: "Dansguardian Issue?"
date: 2009-04-07
forum: Server Platforms
---

### Post by testsubjectmonkey on 2009-04-07
Maybe some one had already came across this and I am just not looking at the right place for a solution.  I just got done installing squid and dansguardian on ubuntu 8.10 server and everything seems to be working fine.  The proxy server blocks or allows any site I set it up to do so.  But when I go to msdn.microsoft.com it seems like the graphics and menu are not loading (activeX issue?).  The same site loads fine if I remove the proxy.  This is the only site I am have trouble with. I can go to another site with .aspx extension and have no problem.  Any help is greatly appreciated!

---

### Post by calibrettokid on 2009-04-09
I have a similar problem with VirtualBox and getting WinXP to update.

I went into /etc/dansguardian/bannedextensionlist

and just commented out this section
```

.msc  # Microsoft Common Console document
# .msi  # Microsoft Windows Installer package
# .msp  # Microsoft Windows Installer patch
.mst  # Microsoft Visual Test source files
```

It still doesn't appear to be working. I thought that maybe something inside the extensionlist has an activex protocol to it. But I am wondering if it's Squid that is doing this...

---

### Post by testsubjectmonkey on 2009-04-28
I'm not sure if this is the answer, but the issue seems to be with squid 3.  I uninstalled it (using apt-get autoremove squid3) and installed squid.  I checked the version and it says 2.7 stabled.  I went to the mentioned site and everything seems to be working fine.

---

