---
title: "Pidgin 2.3.0 is out!!!"
date: 2007-11-26
forum: The Cafe
---

### Post by Chang An on 2007-11-26
And you know what?  I'm not downloading it.  
They have been saying for over several months they would fix this bug [http://developer.pidgin.im/ticket/783](http://developer.pidgin.im/ticket/783)
They keep getting my hopes up but them move the ticket back.  When they say their going to fix something and move it back I can forgive them a couple times but its been so long.  Its now set to 2.3.1.  Lets see if its fixed then.  Probably not, but hey ones got to keep their hopes up.  sigh, one day.

But seriously I love Pidgin.  I just wish the devs treated the broken qq protocol equally as the MSN or AOL protocols.  How long long do you think a bug that would make it so you could not log into MSN or AOL would go unchecked? 

Here is my original thread on the issue too.
[http://ubuntuforums.org/showthread.php?p=3471812#post3471812](http://ubuntuforums.org/showthread.php?p=3471812#post3471812)

---

### Post by Chang An on 2007-11-26
Ok, its seems to work for some people since 2.2.1.  If the people who have it working could post their logs and other useful info that would be great

---

### Post by Polygon on 2007-11-26
from the looks of that dev report, it seems that there is only one guy working on the qq protocol and he seems really busy with school and exams and such

actually, the previous maintainer of that protocol left...so now i dont think there is anyone working on it

> 
09/30/2007 12:42:54 AM changed by mhuetsch  ¶

    * owner deleted.
    * status changed from assigned to new.

My sincerest apologies, but I simply haven't had time to work on this that I thought I would, and don't foresee having the time. I've attached a Wireshark protocol dissector I've written, but haven't updated in many months. It, combined with the already existing code in pidgin, contains most of my knowledge of the protocol. Hopefully somebody else will have the time to fix and maintain this.


and for anyone who wants it, the change log:

[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

---

### Post by mustang on 2007-11-26
> **Polygon said:**
> from the looks of that dev report, it seems that there is only one guy working on the qq protocol and he seems really busy with school and exams and such

actually, the previous maintainer of that protocol left...so now i dont think there is anyone working on it



and for anyone who wants it, the change log:

[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

Thanks for the link. I wish they would fix pidgin so that it would automatically reconnect after a suspend (like adium).

---

### Post by akiratheoni on 2007-11-26
Is there a .deb for this? I could compile it from source, but I really don't feel like it right now.

---

### Post by Polygon on 2007-11-26
I thought it does reconnect after your computer goes into suspend then comes out....just because it disconnects and it keeps trying to reconect anytime that you disconnect from the server

---

### Post by FLCLFan on 2007-11-26
Does anyone know where i can see the process of the official ubuntu pidgin update?

---

### Post by mustang on 2007-11-27
> **Polygon said:**
> I thought it does reconnect after your computer goes into suspend then comes out....just because it disconnects and it keeps trying to reconect anytime that you disconnect from the server

Actually you're right but it doesn't refresh the buddy list.

---

### Post by trash on 2008-02-03
> **Polygon said:**
> I thought it does reconnect after your computer goes into suspend then comes out....just because it disconnects and it keeps trying to reconect anytime that you disconnect from the server

There is still a problem somewhere, I have a satellite connection, runing Amsn and Pidgin, if i lose the connection ONLY Amsn reconnects while Pidgin waits for me to reconnect manually... so annoying!

---

