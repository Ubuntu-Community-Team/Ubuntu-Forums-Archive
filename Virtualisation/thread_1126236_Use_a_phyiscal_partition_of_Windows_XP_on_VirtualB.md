---
title: "Use a phyiscal partition of Windows XP on VirtualBox"
date: 2009-04-15
forum: Virtualisation
---

### Post by Teufel on 2009-04-15
Hello,

I have both Ubuntu and Windows XP Prof SP2 installed on my laptop, a Thinkpad r61i.
Windows was installed first and is mounted on /dev/sda1.
Now I would like to be able to start up VirtualBox and then boot the existing Windows in there.

I googled a lot, but either the threads/solutions I found were very old, or they did not work. So if anyone has a solution, I'd be very grateful!

Thanks!

---

### Post by dusan.saiko on 2009-04-16
There is raw disk feature in VirtualBox, see for example 

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

But Windows can be confused by having different hardware and needing different drivers.

---

### Post by bodhi.zazen on 2009-04-16
There are two threads here walking you through how to do this. Either see the sticky at the top of these forums or search for them ;)

---

### Post by Greyed on 2009-04-17
> **dusan.saiko said:**
> There is raw disk feature in VirtualBox, see for example 

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

But Windows can be confused by having different hardware and needing different drivers.

Vista, yes.  XP, as he stated, no.  To XP they are different hardware profiles.  As long as one uses that feature in XP it works fine.  Why they decided to chuck it in Vista is a question for the... oh, right, Microsoft and Vista, carry on.

---

