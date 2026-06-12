---
title: "SunBlade100 install hangs."
date: 2006-08-04
forum: Sun Sparc Users
---

### Post by jbirch on 2006-08-04
Trying to install the latest server build on a SB100.  Boot from the cdrom, pulls dhcp address, then proceeds to hang at the detecting hardware screen.  

About the only non-standard thing in it is a smart card reader .  Any ideas ?  I'll disconnect the Smart card reader and try again.  Any install switches available ?

Cheers.
a googling i go .... ;-)

---

### Post by jbirch on 2006-08-04
Well after another 10 attempts with hangs in various places it started the install.  I reseated the memory and anything else that could be reseated.  

Might of be having some hardware issues, a few times on boot from the cdrom it would crash out after creating the ram disk "Illegal Operation".  Freezing after looking for a cdrom that it just booted from etc.... Trying to give this box a second life.  It's not being overly co-operative :!:  

Left the install running when i left, we'll see how it went on Monday i guess.

---

### Post by Delta_Farce on 2006-08-05
I've been trying to get various distros onto a Sunblade 150 over the last few weeks. There's a couple of things I've found that might help you:

1) Upgrade your OBP:
You'll need an OS on the machine to do this (I used Solaris 10). Then you just grab the firmware, put it into the root directory and run this command from the ok prompt:

ok boot disk /<directory>/<file name>

in my case this was:

ok boot disk /flash/flash-update-Sunblade100-Sunblade150-latest

This should take care of the memory issues that you're having and may also help with the hardware detection.

Please note that if your hard disk has existing BSD or Linux partitions, Solaris may not be able to format the drive. I had to zero mine after FreeBSD locked it down.

2) Pass the ide=nodma argument to the SILO boot prompt

Sunblade 100'sand 150's seem to crash if you don't pass the ide=nodma argument to them. I tried a Gentoo install and it recommended using this option. Ubuntu server needs it too as it'll crash regularly otherwise.

Depending on what install you want to run (press Tab at the boot prompt to see the options) just append ide=nodma afterwards.

I used: Linux ide=nodma and it worked flawlessly.

You'll also need to add the 'append' string to your /boot/silo.conf

```
image=/vmlinuz
        label=Linux
        append="ide=nodma"
        initrd=/initrd.img
```

Hope this helps,

Mark

---

### Post by jbirch on 2006-08-08
Thanks for the information, i'll have to give that OBP update a go.  The install did run over the weekend but failed to write the boot loader at the end of the install. So'm i'm back to trying again.  Not very failiar with the Sun hardware so it been a bit of a learning curve here. Not too linux literate either but that's another problem ;-)

The box regularly hangs on the detecting hardware screen at this point trying rescue or reinstall methods.  

Guess i'll find a Solarias disk and at least get an OS back on it that i can do the OBP update, then try again.

Cheers.

---

### Post by jbirch on 2006-08-13
Just thought i'd update the thread for other Sunblade 100 folks.  

The Ubuntu server install did work without an OBP update.  It was just the **append ide=nodma** boot option that got it going past the random crashes.  

Now I made the mistake of loading ubuntu-desktop and am battling gdm monitor refresh rates ... doh !! ](*,)

Thanks again Delta_Farce.

---

