---
title: "ATI repository"
date: 2008-02-02
forum: The Cafe
---

### Post by forrestcupp on 2008-02-02
When we install the latest ATI drivers from AMD's web site, part of the process is converting it to a deb, then installing.  So if everyone is already making debs, why hasn't someone made a repository that always has the latest ATI drivers so it could just be automatically updated for us?

---

### Post by ~LoKe on 2008-02-02
I'm sure someone has.  Have you looked?

---

### Post by bufsabre666 on 2008-02-02
cause you can just use envy for the latest, the new release is usually only a day or 2 after the driver release

---

### Post by Xbehave on 2008-02-02
> **forrestcupp said:**
> When we install the latest ATI drivers from AMD's web site, part of the process is converting it to a deb, then installing.  So if everyone is already making debs, why hasn't someone made a repository that always has the latest ATI drivers so it could just be automatically updated for us?

because most people wont be making the right deb, to compile software for multiple platforms ect you need to use specific flags and stuff. if i compiled myself some drivers i wouldn't be confident they would work on the computers of others!

---

### Post by forrestcupp on 2008-02-02
> **~LoKe said:**
> I'm sure someone has.  Have you looked?
If someone did something that useful, everyone would know about it and be using it.

> **bufsabre666 said:**
> cause you can just use envy for the latest, the new release is usually only a day or 2 after the driver release
I'm using Envy right now.  But the problem with that is when you upgrade the kernel or distro version, you either have to uninstall it first and reinstall it again afterward, or you have to fix it from the command line after X crashes.  How is that easier?

> **Xbehave said:**
> because most people wont be making the right deb, to compile software for multiple platforms ect you need to use specific flags and stuff. if i compiled myself some drivers i wouldn't be confident they would work on the computers of others!
What do you think the Restricted Drivers Manager uses?  It uses precompiled debs that are in the repositories.  They just aren't kept up to date.

I really think someone who knows what they are doing could do this easily.  I just don't know what I'm doing.  Even if I did, I don't have server space for something like that.

---

### Post by FuturePilot on 2008-02-02
> **forrestcupp said:**
> 


What do you think the Restricted Drivers Manager uses?  It uses precompiled debs that are in the repositories.  They just aren't kept up to date.


True but they are properly built. It's a bit more difficult than it might appear to build a truly proper deb.

---

### Post by bufsabre666 on 2008-02-02
> **forrestcupp said:**
> 
I'm using Envy right now.  But the problem with that is when you upgrade the kernel or distro version, you either have to uninstall it first and reinstall it again afterward, or you have to fix it from the command line after X crashes.  How is that easier?


because even with the debs you have to uninstall it anyways, atleast this way theres a nice gui, i use the text version of envy anyways

---

### Post by forrestcupp on 2008-05-13
Well, I'm using nvidia now.  But thankfully in Hardy, EnvyNG actually does what I was looking for in my original post through the Proposed updates.  It automatically updates nvidia and ati drivers with EnvyNG built debs.

Thank you to Alberto Milone and the Ubuntu devs for working together to accomplish such a useful task.

---

### Post by Dubious9 on 2011-02-25
> **bufsabre666 said:**
> cause you can just use envy for the latest, the new release is usually only a day or 2 after the driver release

Envy is no longer supported as of Ubuntu 10.04 which was released April 29th 2010

---

### Post by cariboo on 2011-02-25
This thread is over three years old, a lot has changed since then. Closed.

---

