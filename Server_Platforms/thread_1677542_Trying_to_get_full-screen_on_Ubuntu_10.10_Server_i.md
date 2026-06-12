---
title: "Trying to get full-screen on Ubuntu 10.10 Server in VirtualBox"
date: 2011-01-28
forum: Server Platforms
---

### Post by majikmerlin on 2011-01-28
I've got Ubuntu 10.10 Server installed in a VirtualBox.  I'm stuck in 640x480 screen resolution when I put VirtualBox in full-screen mode.

How can I change the startup resolution on Ubuntu so say, 1152x864 and make it stick upon reboot?

I found a thread here on the forums a while ago but I cannot find it anymore...

---

### Post by CharlesA on 2011-01-28
> **CharlesA said:**
> I haven't found a way to adjust the console size on Ubuntu server running in VirtualBox, so I just SSH in and maximize that window.

Same should apply to Vmware.

See above. ^

---

### Post by majikmerlin on 2011-01-29
Perhaps, but there IS a way.  I actually have the an Ubuntu Server VM running at a higher resolution on my office machine.  I'll post the solution here when I find the resolution, but there IS a way. :)

Thanks though!

---

### Post by Smika on 2012-02-05
Did you find the solution?

---

### Post by CharlesA on 2012-02-06
> **Smika said:**
> Did you find the solution?
I think they just SSHed in and left it at that.

I don't know of any way to adjust the console resolution itself.

---

### Post by Murdock304 on 2012-06-05
I just went through this on 12.04, hopefully this will help the next person. On VirtualBox v4.1, setting up Ubuntu server 12.04, this is all that's required (or at least on my setup):

```
#Add kernel option for 1024x768 resolution to GRUB
sudo sed -i "s/GRUB_CMDLINE_LINUX=\"/GRUB_CMDLINE_LINUX=\"vga=0x0305 /" /etc/default/grub
#Run update-grub for the new setting to take effect
sudo update-grub
```

---

