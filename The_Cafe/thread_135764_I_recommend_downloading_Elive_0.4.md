---
title: "I recommend downloading Elive 0.4"
date: 2006-02-24
forum: The Cafe
---

### Post by mostwanted on 2006-02-24
It's a *great* LIVE cd, it sets up stuff properly (or so it seems), automounts all partitions, boots pretty fast, includes proprietary drivers for graphics cards and has the sexy, sexy Enlightenment R17 with lots of bling bling.

[http://www.elivecd.org/gb/Download/0.4/](http://www.elivecd.org/gb/Download/0.4/)

On top of that you can install to your harddisk from the LIVE cd itself, which I'm doing currently ;)

---

### Post by Iandefor on 2006-02-24
[quote=mostwanted]It's a *great* LIVE cd, it sets up stuff properly (or so it seems), automounts all partitions, boots pretty fast, includes proprietary drivers for graphics cards and has the sexy, sexy Enlightenment R17 with lots of bling bling.

[http://www.elivecd.org/gb/Download/0.4/]("http://www.elivecd.org/gb/Download/0.4/")

On top of that you can install to your harddisk from the LIVE cd itself, which I'm doing currently ;)[/quote] Yeah, Elive is a pretty awesome distro. E17 is one of my favorite DE's (Such a shame it isn't stable!).

---

### Post by mostwanted on 2006-02-24
I'll change the subject of this topic slightly.

I got it installed now but GRUB still uses the same old Ubuntu list. Anyone have any experience adding other distros to the boot list? I could use some help with this :-k

---

### Post by jasay on 2006-02-24
Well, I'm hardly the expert, but I would ```
sudo gedit /boot/grub/menu.lst
``` and scroll down 'til I see something like:
```
title		Ubuntu Breezy Badger, kernel 2.6.12-10-686-smp 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

```I would copy/paste those lines and change title to something about elive, it doesn't matter what.  Change root to the correct hd and partition (where the first harddrive is hd0, second is hd1, etc. and the first partition is 0, second is 1, etc.)  Then I would open nautilus to poke around in /boot of the partition that elive is installed on (after mounting of course).  Replace vmlinuz* and initrd.img* with whatever version are in the elive partition and make sure root=/dev/eliveroot.  I don't know what options can be used with elive so I would get rid of at least splash and maybe quiet.

**Usually warning about don't do anything I say because it might destroy your computer, though in reality I don't see how it could becaues you should still be able to boot the other OS's:rolleyes: .**

---

### Post by WalterDirt on 2006-02-24
Does anyone know where you can get that background in this screenshot?

[http://www.elivecd.org/gb/Main/Screenshots/_previews/demos-1.jpg.html](http://www.elivecd.org/gb/Main/Screenshots/_previews/demos-1.jpg.html)

---

### Post by Bandit on 2006-02-24
[QUOTE=WalterDirt]Does anyone know where you can get that background in this screenshot?

[http://www.elivecd.org/gb/Main/Screenshots/_previews/demos-1.jpg.html](http://www.elivecd.org/gb/Main/Screenshots/_previews/demos-1.jpg.html)[/QUOTE]
Thats a E17 background. It should come with the E17 theme files.

---

### Post by Alpha_toxic on 2006-02-25
WOW, this really looks cool!!! :D

---

### Post by exkalibur on 2006-02-26
It looks good and the install is pretty simple but, after spending a day with it.... I missed ubuntu.... Getting spoiled I guess....;)

---

### Post by joplass on 2006-03-09
I wonder what is happening to ebuntu.

---

### Post by Klejs on 2006-03-09
Looks nice, but I'm not an fan of the EDE

---

### Post by darkmatter on 2006-03-09
[QUOTE=WalterDirt]Does anyone know where you can get that background in this screenshot?

[http://www.elivecd.org/gb/Main/Screenshots/_previews/demos-1.jpg.html](http://www.elivecd.org/gb/Main/Screenshots/_previews/demos-1.jpg.html)[/QUOTE]

[http://www3.get-e.org/Backgrounds/Static/](http://www3.get-e.org/Backgrounds/Static/)

Scroll down ;)

---

### Post by bonzodog on 2006-03-09
[QUOTE=mostwanted]
I got it installed now but GRUB still uses the same old Ubuntu list. Anyone have any experience adding other distros to the boot list? I could use some help with this :-k[/QUOTE]

Try running ```
$sudo update-grub
``` from ubuntu.

---

### Post by Jucato on 2006-03-09
E17 on the Live CD is really cool. Their E Panel (or whatever the control panel is called) is very, very nice. Too bad, they only install E16. :(
Is E17 now considered a desktop environment, or still remains within the window manager category?

---

### Post by Bandit on 2006-03-09
[QUOTE=Fenyx]E17 on the Live CD is really cool. Their E Panel (or whatever the control panel is called) is very, very nice. Too bad, they only install E16. :(
Is E17 now considered a desktop environment, or still remains within the window manager category?[/QUOTE]
I may be wrong, but I think they are aiming it at being a desktop enviroment.
I am going to try to download it now and try it also..

---

### Post by Jucato on 2006-03-09
Well, so far I don't think they're there yet. I just noticed that most of the stuff in E17 are GNOME apps. But I'm not really 100% sure about it. If somehow I could get KDE + E17 + XGL all in one OS, then that would be wow! Eye-candy extreme! :D

---

### Post by Rev. Nathan on 2006-03-10
I was using an earlier version, when I saw it as a stable project on distrowatch. Seeing another update, they have added a buttload since. I'm stoked; this could end up being a pretty decent OS! :)

---

### Post by Duncan_Idaho on 2006-03-16
[QUOTE=Bandit]I may be wrong, but I think they are aiming it at being a desktop enviroment.[/QUOTE]

they use the term "desktop shell"
maybe it's somethig in between a DE and a WM

---

