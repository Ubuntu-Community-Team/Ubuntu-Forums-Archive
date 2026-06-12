---
title: "LMMS always kicked by jack"
date: 2010-02-14
forum: Ubuntu Studio
---

### Post by AudioDef on 2010-02-14
That about says it all. Has anyone resolved this problem?

---

### Post by eric71 on 2010-02-15
I don't use LMMS, but I have had problems with programs being dropped by Jack. Increasing the timeout setting in qjackctl solved those problems. Try 5000 ms or more. If you go too hight, jack won't start anymore.

---

### Post by AutoStatic on 2010-02-15
Hello AudioDef, you should indeed raise your timeout setting. The problem itself is in the code, LMMS uses some routines that do not fully comply with the JACK API rules. But the LMMS devs have been notified and hopefully they will pick it up in the near future. It doesn't have top priority for them though.

More info: [http://forum.linuxmusicians.com/viewtopic.php?f=24&t=2368](http://forum.linuxmusicians.com/viewtopic.php?f=24&t=2368)

---

### Post by AudioDef on 2010-02-16
Thanks, guys. I was having a similar problem with Rosegarden, and increasing the timeout helped. I'll change the TO if I need to for LMMS.

---

