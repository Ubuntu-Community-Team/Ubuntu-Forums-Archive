---
title: "is &quot;hibernate&quot; working yet?"
date: 2007-04-21
forum: The Cafe
---

### Post by evanc on 2007-04-21
sort of gave up on dapper drake once i dscovered that i couldn't get my laptop to hibernate....

combine that with the numerous windows apps i needed to run (which, i admit, ran pretty damn well in vmware) and i relegated ubuntu to media-server (where, by the way, i've got a 6 year old PC running ubuntu and democracy, replacing the old cable box....)

has this new release gotten any better at laptop support? the quick one-button hibernate i get with win xp still ( i think has no equal.... would love to be proven wrong.

---

### Post by prizrak on 2007-04-21
Depends on your hardware. My friend has pretty good results with OpenSuSE on a Dell (not sure of the model he just used a spare laptop at work for testing). If you are running nVidia with a binary driver it will likely not work. If you are running an Intel based solution it MAY work. It's all up to your hardware really, you might also want to try different distros as they all have different enough kernels to make a difference.

---

### Post by userundefine on 2007-04-21
On my dell inspiron 6000 it's worked since dapper.

---

### Post by jiminycricket on 2007-04-21
Before anyone blames Ubuntu severely, [URL="http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf"]Bill Gates wanted Linux to be incompatible with ACPI
[/URL]
Hopefully with OEM support from Dell, these problems should go away (on their machines at least).

My thinkpad works well with hibernate and suspend.  Apprently the binary drivers from ATI and nVidia don't fare as well though.

---

### Post by bran on 2007-04-21
> **userundefine said:**
> On my dell inspiron 6000 it's worked since dapper.
ditto on my Acer Aspire 9400

---

### Post by NikoC on 2007-04-21
Sony vaio vgn-s4hp doesn't hibernate on feisty... it never did on the previous releases either (started from warthy). Suspend does work now!

---

### Post by macogw on 2007-04-21
My Gateway works with Feisty.  It wasn't so lucky with Dapper.

---

### Post by jrb114 on 2007-04-21
My sony vaio FS315-S does hibernate on Feisty, but it doesn't suspend. Both work on Dapper, which means I'm limited to Dapper for now. That's using nvidia's binary driver. Although I did have to modify /etc/default/acpi-support to the attached file.

(N.B. If you want to use the attached file, remove the .txt from the end of it and put it in /etc/default/ but *backup* your existing one before doing this.)

If anyone has any ideas about getting feisty to suspend, I've tried /lots/ of work arounds...

J

---

### Post by OsakaWilson on 2007-04-21
Hibernate is working on my Acer Inspire 5100.

---

### Post by slimdog360 on 2007-04-21
it hibernates when told, it comes out of hibernate when told, but then after its out the X window system is screwy and needs a complete restart. bummer eh.

---

