---
title: "HOWTO: Perform AVG updates without the need for (gk)sudo"
date: 2008-08-14
forum: Security
---

### Post by lisati on 2008-08-14
**Important: this advice applies to version 7.5 of AVG free.**

Recently I've notice a number of people apparently having trouble with updating the AVG virus scanner. The solution is simple. Once you have downloaded the Linux version of AVG from [http://free.avg.com/ww.download?prd=afl]("http://free.avg.com/ww.download?prd=afl") and installed it, perform the following steps:

[LIST=1]
[*]Add your username to the avg user group
[*]log off
[*]log on
[/LIST]

This will avoid the need to mess around with sudo or its variants.

EDIT: GRISOFT seems to have withdrawn support for AVG version 7.5. see [here]("http://ubuntuforums.org/showpost.php?p=5939398&postcount=10")

---

### Post by Szyfrow on 2008-08-17
Thanks very much, it did the job!

---

### Post by AlanR8 on 2008-08-17
Sorry, but why do you want to run virus software in a Linux environment? Have been running Kubuntu for over two years now on five machines without an issue.........

---

### Post by Nepherte on 2008-08-17
There are several valid reasons where an antivirus software might come in handy.

[LIST]
[*]You could scan your windows hard drive from linux if you have a dual boot setup.
[*]Your linux box acts as afile server where windows clients have access to.
[*]...
[/LIST]

---

### Post by cariboo on 2008-08-17
On the other hand if your Windows clients are set up properly, with up to date antivirus and antispyware packages and some common sense, you shouldn't have to worry about it.

Jim

---

### Post by Szyfrow on 2008-08-17
Yeah, an old debate going on for a while now. But OK, here we go. What if I just wanted to experiment with a virus scanner? Or what if I would like to see if AVG can find any nasties on a Win system that may be compromised?

---

### Post by lisati on 2008-08-17
> **AlanR8 said:**
> Sorry, but why do you want to run virus software in a Linux environment? Have been running Kubuntu for over two years now on five machines without an issue.........

> **Nepherte said:**
> There are several valid reasons where an antivirus software might come in handy.

[LIST]
[*]You could scan your windows hard drive from linux if you have a dual boot setup.
[*]Your linux box acts as afile server where windows clients have access to.
[*]...
[/LIST]

There's also not wanting to violate the part of the "fine print" that some ISPs and email providers have about not passing on malware through their servers. Although I haven't encountered it myself, I've heard of nasty stuff being hidden in MS Word ".DOC" files and more recently PDF files.

---

### Post by Nepherte on 2008-08-18
Anyways, I think we can save this discussion for another thread. This tip is very useful for people that do use AVG, whether it is for valid reasons or not.

---

### Post by lisati on 2008-10-07
If you've been to the AVG website looking for the Linux-friendly version of AVG anti-virus, but couldn't find it, check [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by lisati on 2008-10-10
I just found [this announcement]("http://freeforum.avg.com/read.php?3,136697,backpage=,sv=") at the AVG forums website
> Support for AVG 7.5 Free Edition is planned to end on 31st August 2008. 

No more virus updates are planned for after that date. 

Note that no more 'program' updates are due! Only virus updates will continue until the end date. 

AVG 7.5 Paid version will be supported until 31/12/08.

This will probably mean a rethink of options for those of us who use the Linux version (which I think stopped at 7.5)

---

### Post by lisati on 2008-10-10
> **lqyromeo said:**
> thanks for your posting info, but i usually use computer in the envirnment of windows XP. i am not familiar with Unix system.

I don't use Unix either: this thread applies to using AVG with Linux.

---

### Post by lisati on 2009-07-14
From [http://free.avg.com/help:](http://free.avg.com/help:)
> End of 7.5 version support
Support for AVG 7.5 products ended on April 30, 2009. This support covers all home and SMB/enterprise solutions, and includes all updates and 24/7 technical and sales support.

---

### Post by cariboo on 2009-07-14
Closed by request of the op.

---

