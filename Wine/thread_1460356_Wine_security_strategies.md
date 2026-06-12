---
title: "Wine security strategies"
date: 2010-04-22
forum: Wine
---

### Post by Tom_ZeCat on 2010-04-22
I've read some of the old posts on keeping Wine secure.  Based on that advice, I'm going to limit Wines access to only certain folders and will be very careful what I run under it.  I've never used Wine before, preferring to find Linux-based applications.  However, I'm considering using Wine for a few apps that there are no Linux versions for.  

What I wonder is this: Is it possible to tell Wine something to the effect of, "these are the only Windows apps I'm ever going to run.  Don't run or install anything else."  I think that would nail down security pretty well if that could be done.  

Also, is it possible to run a Windows-based antivirus program under Wine such as Kapersky?  I'm thinking maybe I will just keep Wine shut off when I don't need the Windows-based apps, but then maybe when I need them I could stay safe by running a Windows-based AV prog only when Wine is turned on.  On the other hand, I wonder if I'm just inviting major configuration headaches.

---

### Post by cogadh on 2010-04-22
Considering that Wine doesn't actually "run" unless you are actively running a Windows app, you really don't need to be all that concerned about it. Wine really isn't that big of a risk. It isn't run with root or sudo permissions, so the worst it can possibly do (if you haven't already configured it securely) is screw up your home directory. If it is configured correctly, the worst it can do is screw up its own .wine directory, which you can easily fix by simply deleting it and re-creating it. Additionally, if you are that concerned about it, rather than trying to run a Windows anti-virus in Wine, you can just run a Linux native anti-virus and it will accomplish the same thing. Remember, a Windows virus cannot affect Linux at all, but if you are interacting with Windows machines on your Linux machine, you might want anti-virus to protect them, rather than you.

---

### Post by asdfoo on 2010-04-23
cogadh is pretty much right, people who do not trust the programs they run in Wine use an extra layer of indirection, which is to run Wine in a virtual machine, like qemu or virtualbox, but this is more or less only done by people who research viruses or malware.

---

### Post by Brebs on 2010-04-23
> **Tom_ZeCat said:**
> limit Wine's access to only certain folders
Good first step:

```
rm ~/.wine/dosdevices/z:
```

---

