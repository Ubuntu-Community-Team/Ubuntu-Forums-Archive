---
title: "Uninstall VMware Player"
date: 2009-12-25
forum: Virtualisation
---

### Post by emoguitarist06 on 2009-12-25
Please read this post to understand my problem:
[http://ubuntuforums.org/showthread.php?p=8558892]("http://ubuntuforums.org/showthread.php?p=8558892")

Basically I haven't been successful in removing VMware player 3.0

How do I do it?

---

### Post by fjgaude on 2009-12-26
It's in the Help file of a running Player, at a command line:

```
vmware-installer -u vmware-player
```

Answer the question: Yes.

---

### Post by emoguitarist06 on 2009-12-26
> **fjgaude said:**
> It's in the Help file of a running Player, at a command line:

```
vmware-installer -u vmware-player
```

Answer the question: Yes.

I love you!

Thank You!

---

### Post by baldeante on 2010-03-09
Thanks fjgaude ... and Thank Google that took me over here :D

---

### Post by kniwor on 2010-11-06
This was useful. Thanks.

---

### Post by ampc on 2011-01-24
It helped me too. Thank you all.

---

### Post by xardic on 2011-03-21
I wrote the code as you say


vmware-installer -u vmware-player

but what ubuntu response is ?


root access is required for the operations you have chosen

---

### Post by fjgaude on 2011-03-21
> **xardic said:**
> I wrote the code as you say

vmware-installer -u vmware-player

but what ubuntu response is ?

root access is required for the operations you have chosen

Here use this in a terminal, and enter your password when prompted:

```
sudo vmware-installer -u vmware-player
```

---

### Post by sri4985 on 2011-04-27
thank u very much.

---

### Post by talzz2 on 2011-07-19
Thank you for this, it really helped..

---

### Post by wquiles on 2011-08-27
Thanks as well - very helpful!

---

### Post by another_sam on 2012-01-23
sudo vmware-installer -u vmware-player

perfect!! thanks.

---

### Post by mohamed_en on 2012-03-25
Thanks for that post and replies solution helped me alot

---

### Post by nothingspecial on 2012-03-26
Old Thread.

Closed.

---

