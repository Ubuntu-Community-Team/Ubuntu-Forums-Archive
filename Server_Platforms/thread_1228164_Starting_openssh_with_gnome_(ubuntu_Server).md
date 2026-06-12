---
title: "Starting openssh with gnome (ubuntu Server)"
date: 2009-07-31
forum: Server Platforms
---

### Post by rnovak on 2009-07-31
Hi,

I have ubuntu server running on a machine at home, and i installed X for gui administration (i know its not the ideal, but its for home) when i'm around. 

my problem is, when the machine is restarted SSH service doesn't start with/before gnome, so i can't administer it remotely, i need to "physically" login.

been poking around but haven't figured it out. any ideas?

Thanks!

R.

---

### Post by cdenley on 2009-07-31
It should start at boot, unless you changed something. How do you start it after you physically login?
```

ls -l /etc/rc*.d/*ssh
sudo /etc/init.d/ssh restart

```

---

### Post by wojox on 2009-07-31
The only thing I could thing of besides removing that GUI, would be to Enable Automatic Login 

System > Administration > Login Window > Security  also change Remote tab Style: to Same as local.

---

