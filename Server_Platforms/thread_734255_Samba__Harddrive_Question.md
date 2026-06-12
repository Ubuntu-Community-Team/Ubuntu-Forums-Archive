---
title: "Samba / Harddrive Question"
date: 2008-03-24
forum: Server Platforms
---

### Post by jseiser on 2008-03-24
I want the First Master drive to be my main HD, its going to keep running arch.  The second harddrive i want to set up so my PC can store files there, as well as my girlfriends PC.  Can i install say centos on that slave drive, set up samba on it, and then boot back into my arch isntall, and still be able to access that HD?  Or do i need to format that drive, mount it in arch, and then install samba to arch and configure it?  I would rather do it the first way, but then i realized if im booted into the master drive, is the slave active?  Sorry if this is confusing, i pretty much want the second drive to act as a server.  (

---

### Post by dmizer on 2008-03-26
the way you describe this, you're looking at having two computers running at the same time.

you can run arch, or you can run centos.  but the only way you can run both at the same time is if you virtualize one or the other ... in which case, you're not using a physical disk.

so to answer your question directly:
yes, you will need to format, mount, and share the drive from arch (if you want to use arch as your primary OS).

---

### Post by leohart on 2008-03-26
Why would you want to run Samba from Centos and not Arch?

Running Samba from Arch and then mount your 2nd drive as a folder. Then setup Samba to share that folder on the network. That way your gf and your other machine can be running Windows, OSX or Linux and still be able to access it.

---

