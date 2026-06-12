---
title: "Server security issues"
date: 2009-08-22
forum: The Cafe
---

### Post by dragos240 on 2009-08-22
I asked the community to find a way to crash my server, here is a member's response:
> I'd write a script that continuously writes to disk until your hard disk ran out of space & your system comes to a halt.

Also, If I run 50 processes which allocate large amounts of memory, that'll bring your system down as well.

The first one I solved with userquotas. But the second one.... i'm not sure how to fix.

---

### Post by overdrank on 2009-08-22
> **dragos240 said:**
> I asked the community to find a way to crash my server, here is a member's response:


The first one I solved with userquotas. But the second one.... i'm not sure how to fix.

I thought [this]("http://ubuntuforums.org/showthread.php?t=1246988") was the last thread you would start on the server. :P

---

### Post by MaxIBoy on 2009-08-22
Try not allowing access to your server. You're doing the equivalent of letting people drive your car and finding ways to prevent people from damaging it. Your best bet is to simply... not let people drive your car.

---

### Post by dragos240 on 2009-08-22
> **overdrank said:**
> I thought [this]("http://ubuntuforums.org/showthread.php?t=1246988") was the last thread you would start on the server. :P

Well yes, but this isn't about it being up, it's more about security.

> Try not allowing access to your server. You're doing the equivalent of letting people drive your car and finding ways to prevent people from damaging it. Your best bet is to simply... not let people drive your car.

Well yes, but that wouldn't fix the problem would it?

---

### Post by sefs on 2009-08-22
maybe you can write a script that monitors memory usage, like how conky does and forcibly kill or suspend any bad behave memory hogs.  somewhat like throttling.

---

### Post by dragos240 on 2009-08-22
> **sefs said:**
> maybe you can write a script that monitors memory usage, like how conky does and forcibly kill or suspend any bad behave memory hogs.  somewhat like throttling.

Nah, I'm not too skilled at scripting.....

---

### Post by Yes on 2009-08-22
I haven't read all the way through it, but this might be what you're looking for - [http://www.seifried.org/lasg/users/](http://www.seifried.org/lasg/users/)

---

### Post by 3rdalbum on 2009-08-23
Give each user their own virtual machine with a set amount of memory. If they crash their virtual machine, then it doesn't affect anyone else.

---

### Post by sefs on 2009-08-23
> **Yes said:**
> I haven't read all the way through it, but this might be what you're looking for - [http://www.seifried.org/lasg/users/](http://www.seifried.org/lasg/users/)

This puts Linux and Chuck Norris on par.  Is there anything that they cannot do?

---

