---
title: "Photoshop crashes my system after upgrade to 9.04"
date: 2009-05-24
forum: Wine
---

### Post by emotionlovesyou on 2009-05-24
I used to run Photoshop CS and Photoshop 7.0 just fine via WINE. But after I upgraded my OS to 9.04, every time I run or try to install either, my system freezes up. I think it's a graphics issue. Any ideas?

---

### Post by lithorus on 2009-05-25
From [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318)
> **What does not**
Installation currently fails under wine versions later than 1.1.17 due to bug 18228 (which might be duplicate of [FONT=monospace]18070).[/FONT]     

   Hence, the applications was installed using 1.1.17, not 1.1.20.                                         

 
Maybe this is affecting you?
Link to bug report :
[http://bugs.winehq.org/show_bug.cgi?id=18070](http://bugs.winehq.org/show_bug.cgi?id=18070)

---

### Post by hikaricore on 2009-05-25
If you believe you are having video driver issues you should resolve them before even thinking troubleshooting applications.

---

### Post by growled on 2009-05-25
I use Photoshop 7 everyday with Kubuntu Jaunty and Wine latest (1.1.22). Works perfectly here. It is not a Wine issue.

---

### Post by krazyd on 2009-05-25
@emotionlovesyou

Have you got nvidia graphics?

---

### Post by emotionlovesyou on 2009-05-25
> **krazyd said:**
> @emotionlovesyou

Have you got nvidia graphics?

Yes and I've never been too impressed. Hehe. Do you think that's my problem? What should I do to fix it?

---

### Post by krazyd on 2009-05-26
Probably. Since wine runs as User, it's unlikely to be causing system crashes, while nvidia graphics are known to be a little crashy ;)

All I can suggest is to switch driver versions. Try upgrading to the latest from the nvidia website.

---

