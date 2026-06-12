---
title: "Does the wipe command use the Gutmann method?"
date: 2016-06-15
forum: Security
---

### Post by SpaceManJack on 2016-06-15
I read this article on how to use wipe to wipe your HDD [http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/) but I read somewhere else that wipe uses the Gutmann method. Is there an expert here that knows for sure if thats true? (i googled it and nothing came up). Basically I am afraid of initiating wipe and then waiting for 72 hours to let it finish. Has anyone here used wipe? And yes I know about dban and dd and shred and all the others but I am wondering about wipe so please answer my very specific questions thanks.

---

### Post by Irihapeti on 2016-06-15
I'm not an expert. However, I've found that the wipe man page [http://manpages.ubuntu.com/manpages/xenial/en/man1/wipe.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/wipe.1.html) mentions that the default setting is 34 passes.

If you use the -q option, you can reduce that to 4.

---

### Post by cariboo on 2016-06-15
The Gutmann method is no longer valid, see [here]("http://www.dban.org/node/40").

---

### Post by Irihapeti on 2016-06-16
I also found:

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)
[https://digital-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/](https://digital-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/)

A more recent item is [https://digital-forensics.sans.org/blog/2016/05/23/lets-talk-about-data-recovery](https://digital-forensics.sans.org/blog/2016/05/23/lets-talk-about-data-recovery), in particular the author's reply to a reader's comment.

None of them see recovery of overwritten data as workable.

---

### Post by SpaceManJack on 2016-06-21
could you please save me time and just give me the command to enter with the -q in it please? So you are sure that the default wipe command will do 34 passes then but using the -q I can set it to whatever I want?

---

### Post by Irihapeti on 2016-06-21
I'm reluctant to do that, because I've not used wipe myself for many years, if at all, and I would hate to make a mistake. Have a look at the man page (link in post #2), particularly the examples given near the bottom.

---

### Post by HermanAB on 2016-06-21
Gutman, shred etc are a bit of a myth.

All disk drive controllers have a low level erase function built in that you can activate with hdparm.  This is the only way to erase a disk properly, since the controller is the only thing that can change the motor step size to erase between the tracks also.

---

