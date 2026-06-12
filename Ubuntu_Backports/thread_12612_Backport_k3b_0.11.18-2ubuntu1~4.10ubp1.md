---
title: "Backport: k3b 0.11.18-2ubuntu1~4.10ubp1"
date: 2005-01-25
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-25
**Summary**
The previous K3b backport was a manually-debianized-from-old-patch hack. Now, a Ubuntu-ized K3b is available, with all sorts of fixes, including a Crash-on-Burn bugfix. It's time to get that to Warty -- K3b is still a part of the CD burner's vital toolkit, even for GNOME users.

**Packaging Status**
i386 -- Staging revision 15.

---

### Post by jdong on 2005-01-25
Ok, I have to create Release files. Apparently the "~4.10ubp1" makes the entire version number less than 0.11.18-*, so it thinks 0.11.18-0-4.10ubp1 is **LESS** than 0.11.18-2ubuntu1~4.10ubp1 -- what a pain!


Once I create release files, we can do an apt-get install k3b/warty-backports-staging to work around this!!

---

### Post by danola on 2005-01-26
[QUOTE=jdong]Ok, I have to create Release files. Apparently the "~4.10ubp1" makes the entire version number less than 0.11.18-*, so it thinks 0.11.18-0-4.10ubp1 is **LESS** than 0.11.18-2ubuntu1~4.10ubp1 -- what a pain![/QUOTE]

Just so you know: there's no mystery here. I assume you mean that 0.11.18-0-4.10ubp1 is **greater** than  0.11.18-2ubuntu1~4.10ubp1. Try it out with
```
 dpkg --compare-versions 0.11.18-0-4.10ubp1 gt 0.11.18-2ubuntu1~4.10ubp1 && echo ok
``` 

The first version has an "upstream_version" of 0.11.18-0 and a "debian_revision" of 4.10ubp1. The second has 0.11.18 and 2ubuntu1~4.10, respectively. Both of them are greater in the old version compared with the new.

See [http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version)

---

### Post by jdong on 2005-01-26
Thanks for clarifying this.

Fortunately, 0.11.19 is out.

---

### Post by jdong on 2005-02-14
stable.

---

### Post by Marquis_de_Carabas on 2005-02-20
Many thanks for this!

After repeatedly failing to burn an audio CD with Gnomebaker, the command line tools and a couple of other programs I forget the names of, I installed this backport and had my CD within minutes!

Keep up the good work :)

---

