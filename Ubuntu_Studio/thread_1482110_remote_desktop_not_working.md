---
title: "remote desktop not working"
date: 2010-05-13
forum: Ubuntu Studio
---

### Post by n45w73 on 2010-05-13
i installed  studio on clean hd, and i got a strange bug  remote desktop doesn't work ...

i start vnc from another machine and i got a part of the desktop background and every thing froze ... 
it seems im sending correctly mouse events through vnc cause when i switch back to my real monitor my random clicks worked but i can't see anything in vnc look like nothing sending back from desktop to remote desktop ...

on another hd on the same machine i got ubuntu lucid working fine thought vnc ...

any clues ?

---

### Post by snoopy66 on 2010-05-13
I'm having a similar problem.  It seems to have started when I upgraded to 10.04.  I'm working with three machines:

U32 = Ubuntu 10.04 LTS 32-bit Desktop Edition
U64 = Ubuntu 10.04 LTS 64-bit Desktop Edition
WXP = Windoze XP with VNC installed

The connections that work as expected are:

Client U32 <--> Server WXP
Client U64 <--> Server U32
Client U64 <--> Server WXP
Client WXP <--> Server U32

The two connections that work strangely are:

Client U32 <--> Server U64
Client WXP <--> Server U64

In both cases, when I walk over to the server, I can see that my mouse clicks and typing from the client are making their way through to the server, but the image on the client is not being updated.  Instead, the client displays a frozen image of the server from the time when the connection was first established.

Though more information is needed to be sure, I'm wondering if the problem is with the 64-bit server.

Is anyone else having this problem?  Has anyone found a solution?

Thanks.

---

### Post by Eric Davelaar on 2010-05-13
I also ran into a weird problem with Remote Desktop Viewer. I have Ubuntu 10.04 installed on 2 laptops, an ancient  Vaio I have been tinkering with since 8.04 and a Dell Latitude D600 I installed 9.04 on recently and then upgraded to 10.04.

The weird problem is with the Dell: As long as I have an incorrect password to connect to the remote  computer I'll get a message notifying me  of that condition (tried that on purpose) but as soon as I have the correct password  I get kicked to the Ubuntu login screen without warnings or asking if I want to logout.
I thought it was 'only' 10.04 but on the Vaio it is working fine. 

If anyone has an idea I can try out or needs anything I can run to compare the two machines I will be happy to contribute!

Thanks,
Eric

---

### Post by Eric Davelaar on 2010-05-19
I can now confirm the issue I have is related to the combination of 10.04  and 'something' on the DellI:
I fired up the Dell with 9.04 on a USB stick and had no problem running Remote Desktop Viewer.
Anyone who can help getting system information I can post for those with more knowledge and experience?

Thanks again,
Eric.

---

### Post by ak123 on 2010-05-31
i have a similar problem here...

i have a laptop running 32 bit UNR
and a desktop running 64 bit ubuntu desktop

the desktop has no trouble accessing the laptop..
but when trying to access the desktop from laptop, the server isnt sending back images...

---

### Post by Scott L on 2010-05-31
Would someone please file a bug on Launchpad?

Even if this gets solved here it would be useful to push this error (and possible solution) back upstream so that it gets fixed at the application level, which would hopefully eliminate problems for the future.

---

### Post by Eric Davelaar on 2010-06-01
Could this really be this simple?

I decided to play around with the program settings... got to checking the 'Scaling' option (on the Dell) and next thing I knew I connected successfully!
The Vaio does not have this option checked but there the remote desktop viewer still works without hick ups.

:confused:

For the moment I am happy since this is the machine I am taking on the road in a few weeks and need to be able to connect to the office and I was NOT  looking forward to using win/xp for this!

Eric.

---

