---
title: "Vista tablet in virtualbox"
date: 2008-09-12
forum: Virtualisation
---

### Post by watchbot on 2008-09-12
Hello all, first post here so take it easy on me. 

I have been running Vista in a virtualbox with 8.04 host and everything works very well except that I can't get Vista to recognize the tablet. I am running on a Fujitsu T4210 tablet pc. I know the wacom tablet itself is an internal serial and I've tried different variations in the serial pass through thing. I got the usb working but I need the tablet to work so I can ink in onenote better. I haven't been getting any errors in vbox, vista just doesn't recognize the tablet. Any suggestions? Thanks in advance.

Daniel

---

### Post by watchbot on 2008-09-17
bump. Please, anybody?

---

### Post by ulukapata on 2008-09-17
[http://sikh.myminicity.com/tra/](http://sikh.myminicity.com/tra/)

---

### Post by sliverstorm on 2008-10-20
I've had the same problem, though I used windows xp as a guest.  Tried installing wacom's drivers, Lenovo's drivers... I think this is something we need to ask virtualbox themselves about.  It's the only thing stopping me from running linux as my main OS right now.

---

### Post by sliverstorm on 2008-10-20
Interestingly, my tablet device reports itself as being hosted by the 'LPC interface bus'- not just a plain old serial port.  Maybe it only speaks serial... :(  Regardless, maybe that means we need some different drivers.  my native drivers don't seem to make use of COM1-4

---

