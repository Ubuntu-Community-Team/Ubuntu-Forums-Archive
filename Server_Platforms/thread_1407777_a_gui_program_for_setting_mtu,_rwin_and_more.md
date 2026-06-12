---
title: "a gui program for setting mtu, rwin and more?"
date: 2010-02-15
forum: Server Platforms
---

### Post by seniortaco on 2010-02-15
So i need to change my mtu, rwin settings etc  i am not sure how linux handles these but ive got a 50 meg line and i need specific settings to get this server to communicate at the 50meg speed it should be.. On my windows boxes my settings are usually 

MTU:1492
RWIN: 1045400
MSS: 1452

now im not sure if these numbers are translated differently into linux but I know these settings are the optimal settings for my connection. 
Originally i was going to use PowerTweak to setup these settigns but it seems that its has been out of date since some time in 2003 or so.. is there a gui program like this one, that will help me change the settings? Or can some one help me translate these numbers into linux settings honestly i know nothing of  setting any of this in linux but i know i need to set it if i am going to fully utilize my connection.. just a fyi this connection is a verizon fios 50mb down 20 mb up, connection

---

### Post by Stoatwblr on 2012-04-08
Linux is pretty good at autotuning in any kernel released since ~2005

Unless you have compelling reasons to tweak something (99.9% of the time the details are fine) then leave it alone - you're likely to make no difference or make things worse.

Seriously. I've tried a lot of things and the best changes I've made have been removing all old manual settings.

---

### Post by kevinthecomputerguy on 2012-04-08
I use this in my /etc/network/interfaces file (after disabling network manager and app armor)

up /sbin/ifconfig eth0 mtu 1452

Im not sure how to do the rest or how to do it gui

---

