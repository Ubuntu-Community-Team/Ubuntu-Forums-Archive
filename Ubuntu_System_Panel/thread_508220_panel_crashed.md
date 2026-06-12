---
title: "panel crashed"
date: 2007-07-23
forum: Ubuntu System Panel
---

### Post by jimhce on 2007-07-23
Hi,

My Ubuntu 7.04 on x86 desktop ran well until this morning. I created 2 workplace window, each contained 4 xterms. When I logged in to the machine this morning, I found that all XTERM's frames gone. I can still use ls or vim to edit file, doing things, but cannot move the xterm window, nor close it. The same problem happed on evolution email and firefox windows. I switched the machine off, and restarted again, it is same. How can I fixed it? 

Thank you.

Jim

---

### Post by smartboyathome on 2007-07-24
Are you running anything like Compiz Fusion or Beryl? If so, use alt+f2 (or a terminal) and type metacity --replace.

---

### Post by jimhce on 2007-07-25
No, I am not running any of Compiz Fusion or Bery. I have to manually start the metacity everytime when I login,  and I've already deleted all .gnome*, did not help either.

---

### Post by smartboyathome on 2007-07-26
using the session manager (system>preferences>sessions), put metacity as a new item to startup using the following:

Name: give it whatever name you want
command: metacity --replace

---

### Post by jimhce on 2007-07-26
Thank you smartboyathome, that works. Just wondering how the session setup could lose the metacity and not be able to recover it (has to be edited manually)? It was working fine utile this week.

Thank you.

Jim

---

