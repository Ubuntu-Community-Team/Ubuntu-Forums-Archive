---
title: "Any chance of HPLIP getting updated?"
date: 2005-12-05
forum: Ubuntu Backports
---

### Post by eeclark on 2005-12-05
hplip 0.9.5 is out there but 0.9.6 has the fixes for Ubuntu users. The 0.9.7 is the newest rev.

Just would like at the very least the one for Ubuntu (0.9.6).

I'd make my own deb pkg but still new to debian.

---

### Post by ERam123 on 2005-12-06
any word on this?

---

### Post by eeclark on 2005-12-06
Nope

---

### Post by strikeforce on 2005-12-06
look in the request forum subsection.  I've replied to this post.

---

### Post by jdong on 2005-12-14
jdong@shuttle:~$ ubp hplip
     hplip |    0.9.7-4 |      unstable | source, i386
     hplip | 0.9.5-2ubuntu2 |        breezy | source, all
     hplip | 0.9.6-1ubuntu4 |        dapper | source, i386


0.9.7 not in Dapper.

There is evidence of some packaging changes (i386 vs all) in the current Dapper revision, so that'll take further testing.

---

### Post by kathymacau on 2005-12-15
[QUOTE=eeclark]hplip 0.9.5 is out there but 0.9.6 has the fixes for Ubuntu users. The 0.9.7 is the newest rev.

Just would like at the very least the one for Ubuntu (0.9.6).

I'd make my own deb pkg but still new to debian.[/QUOTE]

I downloaded 0.9.7 from the HP Printer Project on Sourceforge and have installed it (with a lot of tooing and frowing searching the forums as the error messages came up, I might add), but it's not showing up as installed in Synaptic, and the HPLIP Toolbox says I have no HP products .  I have managed to get Gimp to print.

Anyone know how I can get the printer recognised in the HPLIP Toolbox?

---

### Post by jdong on 2005-12-15
if you compile and install it yourself, it will not register in Synaptic. It is now YOUR task to recompile/remove it when doing your next system upgrade (when the current binaries are rendered incompatible with the system, or potentially the newer version hits Dapper).

Keep a list of everything you compiled yourself, or use **checkinstall**.

---

