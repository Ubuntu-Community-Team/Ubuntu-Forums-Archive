---
title: "Reduced version of ubuntu-minimal for virtual servers"
date: 2006-03-13
forum: Server Platforms
---

### Post by steven_ellis on 2006-03-13
Currently running a couple of Ubuntu Breezy based servers under Xen 2.0.7 (shortly to be migrated to Xen 3.0.1). I used debstrap to create these environments as some of the tools in Ubuntu are at a much better level than Debian Sarge.

My only problem is that ubuntu-minimal is quite handy but pulls in a lot of extra packages i don't really need. For example becase the environment is virtualised i don't need wireless tools or alsa.

Is there an alternative to ubuntu-minimal that has an even more reduced package set for virtualised or server environments?

Steve

---

### Post by Glut on 2006-03-13
I suggest the server install, then adding any gui tools required.

---

### Post by steven_ellis on 2006-03-13
Don't need any GUI components. This is a pure headless server environment to do tasks like run databases or webservers.

In the case of this environment the baseline ubuntu-server install would be serious overkill.

On the ubuntu Xen VM

```
# dpkg -l | wc -l
224
```

On an equivalent Debian Xen VM
```
# dpkg -l | wc -l
166
```

So i've got a lot less packages to worry about on the debian box.

Hence i'm after a true "minimal" definition thats enought to boot and not much more. For example to boot a server I don't need alsa.

Steve

---

### Post by drakkan on 2006-03-13
I agree,

I hope final dapper release would have a really minimal profile, I think things such as nfs utilities, ppp,alsa and so on aren't needed in a minimal enviroment, 

I would like a just bootable system, after installation I install the software needed if any (think about a firewall, just a bootable system and iptables)

---

