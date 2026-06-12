---
title: "AMD64 and PPC backports"
date: 2005-06-05
forum: Ubuntu Backports
---

### Post by thephotoman on 2005-06-05
I've noticed that most of the mirrors, while they list the complete x86 set of backports, don't list any of the AMD64 and PPC backports.  Where can I gain access to these repositories, as I have an AMD64 machine that I'd like to get current on everything, but Gaim is a bit hard to compile with full support for everything, Firefox has no binaries for AMD64 (and Mozilla's sources aren't exactly easy to figure out), and I'd rather just keep everything within the package system for the GIMP and Abiword.

---

### Post by Technoviking on 2005-06-06
Many of the backport have be updated to PPC thanks to Slo Mo Snail. I do not think any of the current backport developer have access to a AMD64 based machine. If anyone with AMD64 machine would like to help, I would suggest contactimng jdong :).

Thanks,
Mike

---

### Post by Slo Mo Snail on 2005-06-06
Beginning with this weekend I'll try to backport the stuff which is in i386 but is missing for ppc ;) Well... If you two don't upload too much i386 stuff :P

---

### Post by jdong on 2005-06-07
Slo Mo Snail has been doing a wonderful job bringing ppc in sync with i386. As others have mentioned, I have no amd64 build machines.


When we move over to the official Ubuntu build systems, this will be resolved :)

---

### Post by Gnobody on 2005-06-08
I can help with AMD64.  I have already made newer packages for Gaim, Wesnoth, TVTime, InitNG, GStreamer 0.8.9 etc.

---

### Post by jdong on 2005-06-08
do you really think it's worth catching up with i386, when the Ubuntu build engine will take care of it in a week or two?

---

### Post by Slo Mo Snail on 2005-06-08
[QUOTE=jdong]do you really think it's worth catching up with i386, when the Ubuntu build engine will take care of it in a week or two?[/QUOTE]

No, after thinking about this I came to the result, that I'll better wait until then, backport the new stuff or needed stuff now and when we use the ubuntu build engine I'll create backports of the remaining extras-packages

should be the most effective way for now

---

