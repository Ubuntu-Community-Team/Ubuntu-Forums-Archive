---
title: "Does anybody know a good phone with openssh?"
date: 2009-07-15
forum: The Cafe
---

### Post by wsonar on 2009-07-15
I've seen the iphone can install openssh does anybody know of any others to idealy remote into your server from your phone if you wanted?

---

### Post by estamand on 2009-07-15
Blackberry phones have SSH apps available.

---

### Post by Mehall on 2009-07-15
There are tons of ssh clients, generally FOSS, even for "dumbphones", in the J2ME format. ( .jar, basically.)

---

### Post by thisllub on 2009-07-16
I have putty on my E71 Nokia

---

### Post by kernelhaxor on 2009-07-16
Android phones like the G1

---

### Post by binbash on 2009-07-16
all s60 phones can install putty and connect to your server.

---

### Post by wsonar on 2009-08-07
> **kernelhaxor said:**
> Android phones like the G1

Got the G1 and can't quit raping about how awesome it is.

got ssh working along with all the other cool features and apps

It was exactly what I was looking for.


about to buy the 16mb card for it

now they just need to make the battery life technology a little better.

I've heard of a phone that they are working on that can charge the battery through radio waves.

---

### Post by Post Monkeh on 2009-08-07
> **wsonar said:**
> Got the G1 and can't quit raping about how awesome it is.

got ssh working along with all the other cool features and apps

It was exactly what I was looking for.


about to buy the 16mb card for it

now they just need to make the battery life technology a little better.

I've heard of a phone that they are working on that can charge the battery through radio waves.

there's work going on to provide wireless power to all appliances, including mobiles. i think you still need to be near a power outlet and the psu for the device, but instead of the power being sent down the wire, it gets sent over a short distance (1 - 2 M) via magnetic fields.

---

### Post by kernelhaxor on 2009-08-07
> **wsonar said:**
> Got the G1 and can't quit raping about how awesome it is.

got ssh working along with all the other cool features and apps

It was exactly what I was looking for.


about to buy the 16mb card for it

now they just need to make the battery life technology a little better.

I've heard of a phone that they are working on that can charge the battery through radio waves.

I had the G1 and I loved it too .. but then I felt it was too bulky ..  Moved to the iphone ..
You should check out the mytouch 3g .. it looks awesome as well .. looks like a lot of android devices are coming out this and next year.. I might switch back to Android ..

---

### Post by plb on 2009-08-07
I just got the HTC Hero and it's best phone I've had by far =)

---

### Post by Master One on 2009-08-20
I've just put [PuTTY](http://s2putty.sourceforge.net) on my Nokia E61i. It works, but is there really no scrollback possible? I mean, what is it good for, if you make somethink simple as "ls", the output scrolls off the tiny screen, and you can not scroll up to view the output? Seriously, either I am missing something, or that's pretty much unusable.

I also tried [MidpSSH](http://xk72.com/midpssh/index.php), but that one is utterly broken on the Nokia E61i. I tried the actual development version, but the QWERTY keyboard is not supported by the interface (as also mentioned on the supported-devices-page).

And then there is [PaderSyncSSH](http://www.pader-sync.com/products.html?mobile_ssh_client), which is pretty feature-rich, supports scrollback, but is kind of slow, and does not have such nice fonts and font-size-selection as PuTTY.

I would prefer PuTTY, but only if it supports scrollback.

---

### Post by amitabhishek on 2009-08-20
If you still curious; try Openmoko's Freerunner. The bundled OS on this phone is [FYP]("http://wiki.openmoko.org/wiki/Fyp")- Free your phone. This is a Debian fork...this device can SSH and can be SSHed from any Linux host.

---

### Post by dppowell on 2009-09-20
> **Master One said:**
> I've just put [PuTTY](http://s2putty.sourceforge.net) on my Nokia E61i. It works, but is there really no scrollback possible? I mean, what is it good for, if you make somethink simple as "ls", the output scrolls off the tiny screen, and you can not scroll up to view the output? Seriously, either I am missing something, or that's pretty much unusable.

It's not scrollback, but ```
ls |more
``` would solve this problem...

---

