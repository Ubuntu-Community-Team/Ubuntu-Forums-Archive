---
title: "Listen to sound from microphone connected to remote computer through ssh?"
date: 2006-11-27
forum: The Cafe
---

### Post by PatrickMay16 on 2006-11-27
Hey guys.

I have two computers connected by network. I'm wondering if it's possible to connect a microphone to one of them, and listen to what the microphone is picking up on the other computer. 

I've been playing around with setting up my webcam up on my other computer, and watching through it while in another room. So I thought it'd be pretty cool to have sound with this.

---

### Post by Jussi Kukkonen on 2006-11-27
ESD can do remote sounds:

On the local machine start ESD like this:
```
esd -tcp -public
```
SSH into the remote machine and set the esd speaker:
```
export ESPEAKER=192.168.22.77
```

Then you'll just have to get the mic sounds to ESD (can't help with that, sorry).

---

### Post by DoctorMO on 2006-11-27
you'll require compression too, wav can be a bit big if you have video going too.

---

### Post by PatrickMay16 on 2006-11-28
I found a way to do it, though it's a bit of an odd way. 

I shared my /dev/ with samba, then mounted it using smbfs on the remote machine and did "cat /dev/dsp > dsp". It seems to work alright!

---

### Post by adam.tropics on 2006-11-28
> **PatrickMay16 said:**
> Hey guys.

I have two computers connected by network. I'm wondering if it's possible to connect a microphone to one of them, and listen to what the microphone is picking up on the other computer. 

I've been playing around with setting up my webcam up on my other computer, and watching through it while in another room. So I thought it'd be pretty cool to have sound with this.

So this is for either 

a) fun, 
b) security or 
c) you need arresting? lol

---

### Post by PatrickMay16 on 2006-11-28
> **adam.tropics said:**
> So this is for either 

a) fun, 
b) security or 
c) you need arresting? lol

Hah, just a bit of fun.

---

### Post by carsonrose on 2010-08-24
Just install twinkle or ekiga on both machines, set the one you want to monitor to auto answer........... done deal. Works like a charm.

;)

---

### Post by CharlesA on 2010-08-24
4 year old thread. O_o

---

### Post by FuturePilot on 2010-08-24
> **CharlesA said:**
> 4 year old thread. O_o

:shock:

---

### Post by carsonrose on 2010-08-24
What can I say :)

---

### Post by cariboo on 2010-08-24
You could have started a new thread. This one is Closed.

---

