---
title: "Go Away Grub"
date: 2010-02-07
forum: Server Platforms
---

### Post by icehole on 2010-02-07
Googled & searched & it seems that everyone has the exact opposite problem with grub as I do.. Most people want it to boot windows 1st & it just auto boots into linux for em instead.. well for me I am running this on a headless server with ubuntu only & the grub screen never changes till I manually hit enter.. On top of that the /boot/grub/menu.lst does not exist & from everything I can find the grub magic happens there.. 

Running 9.10 its a fresh install on a single 1tb drive. only partitioned for root, home & swap

What am I missing?

---

### Post by amsterdamharu on 2010-02-07
Ubuntu 9 uses grub2, it uses grub.conf but you are not supposed to edit it.

There is a gnome tool called startupmanager but you might not have gnome.

[http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg)

---

### Post by icehole on 2010-02-07
Cant test it for a couple hours as the server is busy, but that looks like it will do the trick.. 

Thanks

---

### Post by Iowan on 2010-02-07
[Here]("https://help.ubuntu.com/community/Grub2") is a help page for Grub2.

---

### Post by icehole on 2010-02-07
well it doesn't matter now.. The whole thing just pooped out giving me kernel panics & uncompression errors. This is the 2nd time I have had ubuntu up & running just to have it die in the last week for no apparent reason..

---

### Post by amsterdamharu on 2010-02-07
Did you edit the grub.conf? Maybe the kernel cannot find root filesystem because it has the wrong uuid.

Can you boot from live CD and try to run update-grub?

---

