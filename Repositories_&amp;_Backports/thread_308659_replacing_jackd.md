---
title: "replacing jackd"
date: 2006-11-28
forum: Repositories &amp; Backports
---

### Post by mpvano on 2006-11-28
Hi:

I've been experimenting with installing freebob on the standard 6.10 release and have it working nicely, but have run into a problem using programs compiled for the standard jackd package and libjack.

How can I build a later version of libjack and jackd and install them so that they REPLACE the dependencies in the standard system. (Ubuntu conveniently built the jack daemon with no support for firewire audio).

I'm currently building and installing packages with "checkboot", and everything works fine for new builds of applications, but synaptic won't let anything using jack be installed without blowing away my new version! I'm sure there's a way to tell it that the new build is compatible (I believe that it is).

thanks,

Mario Vano

---

### Post by mudfly on 2006-12-31
Hey man if you find out a solution to this I would be very interested. I have a Presonus Firepod that I want to run with Jokosher and Ardour. So far it has been no go.

---

### Post by vivichrist on 2007-03-06
I also have a firepod and have had jackd connecting through freebob in feisty:) 

on the other hand check out the "dapper and freebob" thread, also has references to edgy

---

### Post by mudfly on 2007-03-06
Thanks for the reply vivichrist, I have been waiting for the release of Feisty before I give this another go.

---

