---
title: "run my vista in a Virt?"
date: 2010-01-14
forum: Virtualisation
---

### Post by wlraider70 on 2010-01-14
Sorry, im a noob to most of this.

I have a dual boot vista and ubuntu.

is it possible to run my vista with all my programs inside a virtualization from ubuntu?

---

### Post by studmf on 2010-01-14
Yes, there are alot of guides out there.  I suggest you use virtualbox.  You can download the newest .deb package directly from their site 3.1.2.  It is not very difficult and in my opinion much more convenient than dual booting.  If you get hung up, ask; however, there are many guides with enough detail to where you should have no issues.

*** Oops....think I misread what you were asking.  You want to know if you can use the system already installed on a partition as your guest?

---

### Post by studmf on 2010-01-14
This may give you a starting point.
[URL="http://ubuntuforums.org/showthread.php?t=769883"]
http://ubuntuforums.org/showthread.php?t=769883[/URL]

---

### Post by SchizmWolf on 2010-01-14
I also highly recommend Sun VirtualBox. Though, as a personal recommendation, if at all possible you should either upgrade to Win7 or WinXP. In my experience, Vista is a beast to run virtually. But that's just my experience.:D

---

### Post by wlraider70 on 2010-01-14
studmf, i read some of that guide, ill need more time to really look more into it.

However, am i correct in understanding that if i follow that method i will NOT be able to boot windows normally after making th changes?

Also i had read somewhere that it can me damaging to NTFS partitions to be continually accessed from Linux. 
Is this true and would Virt prevent this?

---

### Post by fouadatmeh on 2010-01-15
Hello,
You should be able to boot windows normally but you will have to select the hardware profile "physical" you created in step 3 to boot it normally..

as for NTFS, I personally have been using it with ubuntu (several versions) and I didn't face any issues..

---

