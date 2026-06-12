---
title: "Authorization to Install Drivers"
date: 2009-11-17
forum: Security
---

### Post by FelixS on 2009-11-17
When I tried to enable the drivers of my video card to use the visual effects and some 3D applications, appears a window saying to me that I don't have authorization for this. I can't understand why, because I'm the one user in this computer and I'm the administrator.

---

### Post by cariboo on 2009-11-18
This really isn't a security question, but. Go to System-->Administration-->Hardware Drivers to install the restricted graphics driver. The utility should ask you to enter a password, use the one you setup when you installed Ubuntu.

Linux is designed from the ground up to be a multi-user system. The only way you can change/modify files is in your home directory, anywhere else on the system you need to be root to accomplish anything. To install programs, you need to enter your password, as files are written to the hard drive in directories other than your own.

I would suggest you download and read [The Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/index_main.html"). it is a free download.

---

### Post by EJeanmaire on 2009-11-18
> **FelixS said:**
> When I tried to enable the drivers of my video card to use the visual effects and some 3D applications, appears a window saying to me that I don't have authorization for this. I can't understand why, because I'm the one user in this computer and I'm the administrator.

Your 'user' account may have administrator privileges, but unlike Windows (until recently), they aren't turned on 24x7... You have to 'escalate' your privileges to perform admin tasks.

---

