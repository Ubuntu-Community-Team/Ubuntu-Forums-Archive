---
title: "Commands not working"
date: 2006-09-03
forum: Server Platforms
---

### Post by Perrorist on 2006-09-03
I'm having difficulty with commands. For example, if I type:

sudo ndiswrapper -l

I get 'command not found', even though modinfo is able to find ndiswrapper.

When I try:

sudo apt-get install proftpd

I get told 'couldn't find package proftpd'. Same applies to other packages I've tried.

I can't see what I'm doing wrong. Can anyone help?

---

### Post by meng on 2006-09-03
Regarding the unfound packages, do you have extra repositories enabled? (particularly universe) You can search the wiki for help on repositories.

Regarding ndiswrapper, do you have ndiswrapper-utils installed?

---

### Post by Perrorist on 2006-09-03
> **meng said:**
> Regarding the unfound packages, do you have extra repositories enabled? (particularly universe) You can search the wiki for help on repositories.

Regarding ndiswrapper, do you have ndiswrapper-utils installed?

Thanks, I'll investigate. I've installed Ubuntu straight from the ISO image without making any changes apart from adding Gnome.

---

### Post by Perrorist on 2006-09-05
Thanks, Meng. Both suggestions worked a treat.

---

