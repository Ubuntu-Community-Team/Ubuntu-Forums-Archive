---
title: "How to &quot;turn&quot; desktop edition into server edition?"
date: 2008-08-05
forum: Server Platforms
---

### Post by kpatz on 2008-08-05
I have a box that is primarily a firewall/email server/DNS server running 8.04 Desktop edition (GNOME).

Reading here, it sounds like the Server Edition is faster and uses less RAM.  I have 384 MB on this box and a fair amount of swap is being used.  So, I don't really need the GUI on this box.

Can I simply change the scripts to not start gdm on boot, to make Desktop more like Server?  Or are there other things I should change as well?

I don't want to uninstall the gnome packages, since I use some of the apps remotely via a ssh tunnel and Cygwin.  So I need the X/Gnome clients but not the X server running all the time.

Suggestions?

---

### Post by Qchan on 2008-08-05
> **kpatz said:**
> I have a box that is primarily a firewall/email server/DNS server running 8.04 Desktop edition (GNOME).

Reading here, it sounds like the Server Edition is faster and uses less RAM.  I have 384 MB on this box and a fair amount of swap is being used.  So, I don't really need the GUI on this box.

Can I simply change the scripts to not start gdm on boot, to make Desktop more like Server?  Or are there other things I should change as well?

I don't want to uninstall the gnome packages, since I use some of the apps remotely via a ssh tunnel and Cygwin.  So I need the X/Gnome clients but not the X server running all the time.

Suggestions?

[b][color=darkred]
I'm not too sure if this will work, but try:

> 
sudo apt-get remove gdm

[/b][/color]

---

### Post by ibutho on 2008-08-05
You can disable the GUI from automatically starting by running
```
sudo update-rc.d -f gdm remove
```

---

