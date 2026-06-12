---
title: "Ubuntu 6.06 on Sun Blade 2000"
date: 2006-07-10
forum: Sun Sparc Users
---

### Post by magnum2000 on 2006-07-10
Hi all.
Hi have a Sun Blade 2000 Server ([http://www.sun.com/desktop/workstation/sunblade2000/]("http://www.sun.com/desktop/workstation/sunblade2000/"))
Can I install Ubuntu with "SPARC server install CD"?
How can I boot from the cd on the Sun?

Thanks

---

### Post by rooihond on 2006-07-10
Hi Magnum2000,

I also have a SB2000 (2X900,2X36GB,PGX32,DVD). Could not get it to boot the CD - or any CD (apart from Solaris ones). I resorted to doing a tftp netboot install from another system.I keep on getting a MMU miss error when trying to boot from CD.

The SB2000 seems to be running 6.06 real stable. I've loaded Gnome. I find that my PGX32 mixes up some colours in FireFox, have not had chance to investigate. The other bother is supported Ehternet adapters. I tried 2 of the later D-Link PCI cards that I had around, but could not get them going yet. The DGE528-T GigaEthernet card is detected, but I could not find the correct driver. And the DFE-520TX caused system crashes.

Rgds

Derek

---

### Post by magnum2000 on 2006-07-11
Thanks rooihond.
Then My only chance is a network installation... :-k

---

### Post by rooihond on 2006-07-11
Hi Magnum2000,

Yep, tftpboot is actually quite simple. There's a whole bunch of ways of doing it - depending on what OS/Setup you're booting from. Just trawl the forums for some options. (Or Google for it.)

I did it off a laptop running Suse 10 Professional. Setup Rarp, tftp server, created the config files and off you go.

Have a look here:
[http://www.ubuntuforums.org/archive/index.php/t-185136.html](http://www.ubuntuforums.org/archive/index.php/t-185136.html)
[http://www.debian.org/releases/stable/sparc/ch04s04.html.en](http://www.debian.org/releases/stable/sparc/ch04s04.html.en)
[http://www.gentoo.org/doc/en/gentoo-sparc-netboot-howto.xml](http://www.gentoo.org/doc/en/gentoo-sparc-netboot-howto.xml)
[http://www.ecs.soton.ac.uk/~mas01r/aurorafaq.html](http://www.ecs.soton.ac.uk/~mas01r/aurorafaq.html)

That should get you going.

Rgds

Derek

---

### Post by allen248 on 2007-03-05
Just in case it helps somebody else who hits this message.

I have a sunblade 2000 and I didn't have any trouble booting a CD.

Power off the machine.  Power it on.  Press stop-A as the machine boots up to get an OK prompt.  Once you are at the OK prompt, type 'boot cdrom'   It is required that you power off the machine and then catch the OK prompt before anything else happens.

This procedured worked for me...   I was able to do a server install, no problem.  Now, unhappily, I cannot get X windows to work with my video card/monitor/pci busiid.

---

### Post by devnullman on 2007-08-07
I don't know if this helps and I'm very new to Ubuntu so... I was getting the "Fast Data Access - MMU Miss" error when I tried to load up on an Ultra 10. The unit had Solaris 8 resident on IDE HDD. Allen248 was very correct in his instruction for proper booting. To make it clearer, I did the Stop-A during the memory check and entered the Boot CDROM command. The CPU then cycled another mem check and booted from the CD without incident. I did get a subsequent "PC rtc not found" error, but this timed out and the system loaded. Thanks Allen248 for the tip and I have to sork on getting X-Windows up too. Hope to chat with you guys again.

---

### Post by foxholeunder on 2007-08-09
I am not sure about the Blade 2000, however I would like to add that if after hitting 'stop+a' and typing 'boot cdrom' does not help you might need to try typing:
```

setenv boot-device cdrom

```

I have two sun systems and on one I need to change the command to the 'setenv boot-device' command and on the other system 'boot cdrom' works just fine.

After installation from cd and auto reboot; the system should go back to booting from disk0 on it's own.

If not, you will need to invoke:
```

setenv boot-device disk0

```

Or disk1 if that is where you installed Ubuntu.

---

