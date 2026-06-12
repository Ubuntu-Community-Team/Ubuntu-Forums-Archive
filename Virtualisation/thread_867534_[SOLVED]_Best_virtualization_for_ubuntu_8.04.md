---
title: "[SOLVED] ???Best virtualization for ubuntu 8.04???"
date: 2008-07-23
forum: Virtualisation
---

### Post by jeantasse on 2008-07-23
Hello, can anyone guide me to the best virtualization product for the 8.04 distro.  One that is stable, because its to use in a productive enviroment.  I dont mind working hard, but i need this thing to work for my starting compagny to save money on machine, hardware etc...  

I have tried in the past xen, i was never able to start a machine.

Then Virtualbox ose 1.6.2; error cannot find an important file,
  
And for the virtualbox trial edition 1.6.2; it work but after a while the vm guest where sort of reset and it did that after 10 min of intance testing.  For me it was unreliable in a server enviroment.

I tried the one suggested in the ubuntu server 8.04 instruction, and again it fail to start, with a message error.

My cpu is compatible with the vm technologie, so what is the problem

Am i too dum to use virtualization, or is it normal that its so hard to make it work on a linux platform???

---

### Post by tamoneya on 2008-07-23
if you are doing any sort of production environment I would use vmware.  I like virtual box more myself but only when I am playing with stuff (intrepid).  At work I am currently setting up a new virtualization system and we are using vmware because it is more fault tolerant and scalable.

---

### Post by jeantasse on 2008-07-23
Please tell me, the free server edition or the paying workstation edition.  And if you say the free, i have no clue for how long its free?  Can you help me?

---

### Post by tamoneya on 2008-07-23
the free version only allows you to run machines it doesnt allow you to make anything.  It is however free (as in beer) indefinitely.  You will at some point need to get the pay version.  You will need at least workstation.  What you ultimately get though depends on your needs.  If you could specify more what you are trying to do I could try to be more specific.  At my office we are looking at the enterprise version of VMWare infrastructure.  It is much more expensive but it fits our needs (clustering and high uptime).  As for you I know you will need at least vmware workstation because otherwise you wont be able to make any machines.  If you just want to make one machine and then run it then you can download the test version (30 days) of vmware workstation and make the machine and run it in vmware player (free version for as long as you want).

The more specific you can be the more specific I can be.

---

### Post by jeantasse on 2008-07-23
for me its to take my ubuntu 8.04 server machine (with apache2,vsftp, postfix and dovecot) and make a vm out of it and being able to make other vm server to test patch's upgrade etc.  Also a Windows vm so i dont have to reboot in one or an other.  For now my main server is an AMD Duron 1000mhz whit 256ram, but my dual boot machine with Xp is a AMDx2 4400+ with 1 gig of ram.  I still need xp for web software etc....

---

### Post by tamoneya on 2008-07-23
its sound like your needs are fairly basic but it also seems like it isnt a one time thing.  I think you want to get vmware workstation: [http://www.vmware.com/products/ws/](http://www.vmware.com/products/ws/).  its almost $200 though so just use the trial of VM workstation for 30 days to see if you can get everything working correctly.  Then if all goes well you should buy it.

---

### Post by jeantasse on 2008-07-23
Thank you for your advices, i will give it a try!!!


JF

---

