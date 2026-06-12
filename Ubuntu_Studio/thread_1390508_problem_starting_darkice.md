---
title: "problem starting darkice"
date: 2010-01-25
forum: Ubuntu Studio
---

### Post by gorditaz on 2010-01-25
Hi I'm getting the following error when starting darkice on my ubuntu machine

[I]Using config file: /etc/darkice.cfg
Using JACK audio server as input device.
Using POSIX real-time scheduling, priority 98
 Registering as JACK client darkice-14039
**DarkIce: LameLibEncoder.cpp:75: lame lib opening underlying sink error [0]**[/I]

I installed darkice with lame and jack support, I had to compile it as the one in the ubuntu repo didnt seem to support jack, jack could not see it. lame is installed and I think i have all the libraries needed (suggestions welcome). Jackd is running and i control it with qjackctrl. Password and mount point for the icecast server are fine, i searched the internet and the error seems to be that the connection isn't possible due to password but that isnt the case. What else can i check? 

this is my sound card:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

It'd be happy to send /etc/darkice.conf if you would like to have a look but the only thing that's relevant is that I'm using jack and not the sound card for the input and jackd is running.

thanks in advance 
gorditazz

---

### Post by burneverything on 2010-02-21
if your password is definitely right check you have the right port.

---

### Post by Darkish Dave on 2010-02-21
Also make sure your connecting to the right version of Icecast and it is running. i.e The header should be [icecast2-0] for Icecast2 and [icecast-0] for icecast1.x

---

