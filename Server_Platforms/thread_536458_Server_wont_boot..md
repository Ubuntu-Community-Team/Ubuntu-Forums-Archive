---
title: "Server wont boot."
date: 2007-08-27
forum: Server Platforms
---

### Post by peterx2 on 2007-08-27
Downloaded 7.04 server edition. 

Chose LAMP option. for apache system
when booting (2 different machines) it gets stuck at

"running local boot scripts (/etc/rc.local) "
 just after starting apache2

what does this?
pete

---

### Post by southernman on 2007-08-27
Try hitting the enter key when it gets to that point... It should drop you into your login prompt then. I don't understand why it does this, but that's what I've found.

---

### Post by flipjarg on 2007-08-27
The same happens to me... give it a shot. I'm glad to know I'm not the only one.

---

### Post by peterx2 on 2007-08-27
I'll be darned.. Yes that works..
pete

---

### Post by cdenley on 2007-08-28
I think the problem is that some startup scripts are run after the login prompt. The login prompt is there, just not at the bottom.

---

