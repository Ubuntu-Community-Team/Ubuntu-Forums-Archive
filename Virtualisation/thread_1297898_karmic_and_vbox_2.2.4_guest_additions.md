---
title: "karmic and vbox 2.2.4 guest additions"
date: 2009-10-22
forum: Virtualisation
---

### Post by virgil_machine on 2009-10-22
I have a karmic guest on a jaunty host running vbox 2.2.4.

Installation of guest additions fails...the log tells me to run "make oldconfig && make prepare"...I try that and get a message about an invalid target (or something).

I am wondering if there is a conflict between the 2.2.4 guest additions and the karmic linux kernel.

Can anyone give me some guidance? Will upgrading to 3.08 help, or do I have another problem?

I created a hardy vm on the same day (yesterday) and the vbox guest additions installed fine, as they have on all my other vms. Only karmic gives me grief.

---

### Post by virgil_machine on 2009-10-26
In case anyone cares, the answer appears to be that karmic does not like vbox 2.2.4, at least for guest additions.

I got the first machine I tried as a vmdk from a friend.  When that wouldn't work, I downloaded iso's for karmic 32 and 64 bit versions. Same result with those, so I gave in and upgraded to vbox 3.0.8.  Very painless upgrade, I just like to know why I need to do something.

---

