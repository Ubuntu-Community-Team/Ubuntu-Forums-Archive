---
title: "strange grep message after update-grub..."
date: 2011-12-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-12-17
```
Found memtest86+ image: /boot/memtest86+.bin
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
```

---

### Post by dino99 on 2011-12-17
so you might have several grub.cfg files with several dates

---

### Post by zika on 2011-12-17
> **dino99 said:**
> so you might have several grub.cfg files with several datesNot that I'm aware of:```
:~$ ls -alt /boot/grub/grub*.*
-r--r--r-- 1 root root 8541 Dec 17 15:39 /boot/grub/grub.cfg

```

---

### Post by tista on 2011-12-17
Same issue +1... :/

So I've noticed it within 1 or 2 days... anyway system goes well but that massage could not be matched to the actual system states, so I won't accept that change of source codes.. XS

Regards,
Tista

---

### Post by VinDSL on 2011-12-19
Looks like an upstream bug:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=651617](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=651617) (supposedly patched).

**Edit**

Here's the commit:  [http://git.savannah.gnu.org/cgit/grep.git/commit/?id=979592944f06bddb108458073239d2ff52d2c475&ss=1](http://git.savannah.gnu.org/cgit/grep.git/commit/?id=979592944f06bddb108458073239d2ff52d2c475&ss=1)

---

### Post by ventrical on 2011-12-19
> **zika said:**
> ```
Found memtest86+ image: /boot/memtest86+.bin
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
```

Just  got it  now after todays update.

---

