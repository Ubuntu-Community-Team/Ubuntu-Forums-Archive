---
title: "No display on boot after fresh install"
date: 2011-06-07
forum: Server Platforms
---

### Post by shasan on 2011-06-07
I just performed a fresh install of 11.04 Server. The installation went smoothly and as expected. As soon as I leave the BIOS and Ubuntu boots, however, I lose my display (my monitor says "Cannot display this video mode"). I am able to ssh into the machine just fine, so I know it is booting up fine; I just don't have a local console. 

Other threads related to this topic suggest adding something like "vga=771" to the boot options in grub/menu.lst, but I don't see that file anywhere in my 11.04 server install. Where can I configure display settings now?

I am using the following video card:

$ lspci -nn | grep VGA
01:04.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL [1002:4752] (rev 27)

Any suggestions?

---

### Post by hawk2010 on 2011-06-07
have you tried VESA

---

### Post by volkswagner on 2011-06-07
> **shasan said:**
> I just performed a fresh install of 11.04 Server. The installation went smoothly and as expected. As soon as I leave the BIOS and Ubuntu boots, however, I lose my display (my monitor says "Cannot display this video mode"). I am able to ssh into the machine just fine, so I know it is booting up fine; I just don't have a local console. 

Other threads related to this topic suggest adding something like "vga=771" to the boot options in grub/menu.lst, but I don't see that file anywhere in my 11.04 server install. Where can I configure display settings now?

I am using the following video card:

$ lspci -nn | grep VGA
01:04.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL [1002:4752] (rev 27)

Any suggestions?


The last few releases of Ubuntu have been using [Grub2]("https://help.ubuntu.com/community/Grub2").  There are many good how-to's about grub2.  There is no menu.list file as all edits should be done inside /etc/default/grub then run "sudo update-grub" for the changes to be made to grub.cfg.

If Ubuntu is the only operating system (most likely on a server), Grub will be hidden during boot.  To show the grub menu hit the shift key while booting.  From there you can press c for command options and add 

```
nomodeset
```

rather than the vga=771.

I had a similar issue, but I was plagued with the "blinking cursor".  See [this thread]("http://ubuntuforums.org/showthread.php?t=1484694") if the issue is related.

---

### Post by shasan on 2011-06-11
Thanks -- that seemed to be the issue. 

I was able to fix it by editing /etc/default/grub as follows:

```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600

```

and then running update-grub.

---

