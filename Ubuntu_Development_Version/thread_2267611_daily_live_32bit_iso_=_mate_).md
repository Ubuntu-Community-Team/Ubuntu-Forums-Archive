---
title: "daily live 32bit iso = mate :)"
date: 2015-03-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-03-02
I downloaded the daily live mate 32bit iso. Booted it and got "Install Lubuntu" ??

---

### Post by sammiev on 2015-03-02
Oh My! The one I'm testing is good.

---

### Post by ventrical on 2015-03-02
I'll try again. Maybe something I did or did not do .. and it would not boot either.

---

### Post by sammiev on 2015-03-02
Mine is a few days old. Just wasn't expecting what happen to you. 
Now that would be some bug.

---

### Post by ventrical on 2015-03-02
wow .. awesome .my bad .. I had some Lubuntu.iso in the que

---

### Post by ventrical on 2015-03-02
I assuming that mate is for older PCs?

---

### Post by grahammechanical on 2015-03-02
> [COLOR=#000000]I had some Lubuntu.iso in the que[/COLOR]

I can't type for laughing . :) :)

That beats my recent dullness of brain when I thought that my Nvidia driver was giving GPU lock up just like the Nouveau driver. And I hadn't switched drivers.

Ubuntu Mate minimum requirements

[https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

Regards - still chuckling.

---

### Post by ventrical on 2015-03-02
This is a very egnimatic OS. :) It is actually funny .. even with all it's bugs and non-bugs.

---

### Post by ventrical on 2015-03-02
> **grahammechanical said:**
> I can't type for laughing . :) :)

That beats my recent dullness of brain when I thought that my Nvidia driver was giving GPU lock up just like the Nouveau driver. And I hadn't switched drivers.

Ubuntu Mate minimum requirements

[https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

Regards - still chuckling.

It's been along day here too. :)lol

---

### Post by ventrical on 2015-03-02
Thanks graham... there it is:


[LIST]
[*]Restore the halcyon days of Ubuntu before [Unity]("https://unity.ubuntu.com/") was introduced.
[/LIST]

They obsoleteted that desktop way too soon. Mabey this  is the Ubuntu Windows 10 outreach thingy that MS did when they realized that Win 8 metro was a non starter :)

  This is a real improvement from 14.10!!

---

### Post by sammiev on 2015-03-02
I kind of like it, will keep it in VM for a while and play.

---

### Post by ventrical on 2015-03-03
I have this huge tower a little more than a decade old with the clear pexi-glass case covering and the lighted fan and all the fanfare and eye candy  that I am going to try and revive. When I get it going I'll put up a pic.:)lol

---

### Post by raptir on 2015-03-03
> **ventrical said:**
> I assuming that mate is for older PCs?

Eh, not specifically. It's certainly lighter than Unity or KDE but it's not as light on resources as Xfce or lxde. It's really meant to be a full-featured desktop that sticks to the older UI standards from GNOME 2. From their website...

> The MATE Desktop Environment is the continuation of GNOME 2. It provides an intuitive and attractive desktop environment using traditional metaphors for Linux and other Unix-like operating systems.

---

### Post by ventrical on 2015-03-04
The 32bit version of Mate  gave me too many errors installing on an older system so I will try Lubuntu. Sorry ! :) can't show a pic of Mate running on old super-tower :)

---

### Post by ventrical on 2015-03-14
I was able to get Mate to work on  old HP pavillion with older nVidia driver using i386. it first ran with llvmpipe and then I just updated a while ago and it blew out llvmpipe for nouveau !! I then though I would try nvidia 304 (update) from additional drivers and it is now installed and working ... so more amazing stuff comming down the pipe  with all the ubuntus :)

@graham

You may find this interesting?

on systemD
```

ventrical@ventrical-RK574AA-ABA-a1730n:~$ uname -a
Linux ventrical-RK574AA-ABA-a1730n 3.19.0-9-generic #9-Ubuntu SMP Wed Mar 11 17:50:01 UTC 2015 i686 athlon i686 GNU/Linux
ventrical@ventrical-RK574AA-ABA-a1730n:~$ 


```

EDIT:

Ok... the driver(s) install but it breaks a pipe in upstart and  gives me a verbose APCI error at start up ... looking for some probe..on both systemD and upstart. I would not recomend to use nVida drivers on 3.19.n-9, at least on Ubuntu Mate.

---

