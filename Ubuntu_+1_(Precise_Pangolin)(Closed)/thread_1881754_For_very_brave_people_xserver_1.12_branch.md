---
title: "For very brave people: xserver 1.12 branch"
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-16
Now there is one PPA, where xserver 1.12 branch (1.11.99) can already be downloaded and installed.
Just to remember that there was an ABI change from xserver 1.10 to xserver 1.11
and so is from xserver 1.11 to xserver 1.12.
This means you need to upgrade new xserver + xorg drivers + graphics drivers at the same time.
Xserver-xorg-core (1.10) provides xorg-input-abi-12 and xorg-video-abi-10
Xserver-xorg-core (1.11) provides xorg-input-abi-13 and xorg-video-abi-11
Xserver-xorg-core (1.12) provides xorg-input-abi-14 and xorg-video-abi-12
All X drivers must depend on these abi's.

The PPA is Ricotz Unstable PPA:
[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

Anyway, for xserver 1.12, this is still very early development phase.
This new xserver is planned to be released in early 2012 and I have read it contains the "smooth scrolling".

---

### Post by Starks on 2011-11-16
Played with this earlier but noticed that a lot of builds failed.
[https://launchpad.net/~ricotz/+archive/unstable/+packages](https://launchpad.net/~ricotz/+archive/unstable/+packages)

Will multi-touch be in the release?

---

### Post by ranch hand on 2011-11-16
I don't know about multi-touch but I do know that if you use fglrx I wouldn't do it.

It has been in the update list for me in Debian testing and Sid for some time now (6 weeks?) and still wants to remove fglrx.

I think it is compatible with nvidia and maybe intel.

Of coarse someone may have been working on it for the ppa so it may work.  You have been warned.

---

### Post by zika on 2011-11-16
Give us xorg-video-abi-13 so that breakage can start... **;)**

---

### Post by Harry33 on 2011-11-16
> **zika said:**
> Give us xorg-video-abi-13 so that breakage can start... **;)**

Yes sure it would :p

Anyway, we are using xorg-video-abi-10 at the moment in the official Precise, as we do not yet have xserver 1.11 pulled in.

---

### Post by Harry33 on 2011-11-16
> **ranch hand said:**
> I don't know about multi-touch but I do know that if you use fglrx I wouldn't do it.

It has been in the update list for me in Debian testing and Sid for some time now (6 weeks?) and still wants to remove fglrx.

I think it is compatible with nvidia and maybe intel.

Of coarse someone may have been working on it for the ppa so it may work.  You have been warned.

The newest AMD fglrx (11.11) supports video-abi-11, so it really is a "no go" for xserver 1.12.
In the Unstable PPA you will find nvidia-current built with the video-abi-12 dependency, but I haven't tried how it works. It might work ATM, because there is a lot ahead in the development of xserver 1.12 from now on.

---

### Post by zika on 2011-11-16
> **Harry33 said:**
> Yes for it would :p

Anyway, we are using xorg-video-abi-10 at the moment in the official Precise, as we do not yet have xserver 1.11 pulled in.After some handpicking through xserver-xorg-{video,input}-* it got installed... ;)
We will see.. ;)

---

### Post by zika on 2011-11-25
After a week of using 1.12 I got (with a certain amount of work involved) out of ricotz/unstable. Today it made X segfaulting and that was it... ;)
While struggling with that, with no extra cost, I've got out of xorg-edgers also. So, my Evince is working again... ;)

---

### Post by Harry33 on 2011-11-25
> **zika said:**
> After a week of using 1.12 I got (with a certain amount of work involved) out of ricotz/unstable. Today it made X segfaulting and that was it... ;)
While struggling with that, with no extra cost, I've got out of xorg-edgers also. So, my Evince is working again... ;)

That is easier, I mean xserver 1.10 series is easier.

Xserver 1.11.2 still does not have the multitouch support (hence the problems with evince -  if the new package libutouch-geis1 is installed).
The latest version working with evince is libutouch-geis1_2.1.2-0ubuntu4.

I am still using xorg-edgers and xserver 1.11.2, and with no problems.

---

### Post by ricotz on 2011-11-25
> **zika said:**
> After a week of using 1.12 I got (with a certain amount of work involved) out of ricotz/unstable. Today it made X segfaulting and that was it... ;)
While struggling with that, with no extra cost, I've got out of xorg-edgers also. So, my Evince is working again... ;)

Things breaking is pretty much expected here, but this specific problem wasn't ;). It should go away with the next update, hopefully soon. This is a small fallout of [http://cgit.freedesktop.org/xorg/xserver/commit/?id=d5c7338b3eaea55177ade6fcba71a47ccd5547f5](http://cgit.freedesktop.org/xorg/xserver/commit/?id=d5c7338b3eaea55177ade6fcba71a47ccd5547f5) 
Keep the PPA warning in mind! Stacktraces are welcome though.

---

### Post by Starks on 2011-11-25
1.12 will be a trivial release

Not worth hosing over

---

### Post by zika on 2011-11-25
> **ricotz said:**
> Things breaking is pretty much expected here, but this specific problem wasn't ;). It should go away with the next update, hopefully soon. This is a small fallout of [http://cgit.freedesktop.org/xorg/xserver/commit/?id=d5c7338b3eaea55177ade6fcba71a47ccd5547f5](http://cgit.freedesktop.org/xorg/xserver/commit/?id=d5c7338b3eaea55177ade6fcba71a47ccd5547f5) 
Keep the PPA warning in mind! Stacktraces are welcome though.
Keep up the good work and Thank You! I'll jump on the ship, again, soon... ;)
I had some important work to do so I had to make X work...
Once I've got X to work I thought, why not make evince work and make those readings easier. And, that started a chain reaction... ;)

---

