---
title: "need help on running webserver on virtualbox"
date: 2009-07-20
forum: Virtualisation
---

### Post by Meow27 on 2009-07-20
im on my laptop and i dont feel like going through the hassle of installing [L]AMP on my host, id rather have my guest feel all the stress. (lets just keep the discussion to that please)

after installing apache on my ubuntu 9.04 guest, i run "ifconfig" and copy/paste the ip on the host browser (to get the apache homepage "it works!", but i get nothing. i ping the IP and nothing comes back. 


as you can see, i dont know what im doing. help or guidance would be much appreciated. 
thanks 

-meow

---

### Post by bodhi.zazen on 2009-07-20
How did you configure your networking ? NAT (default) I am guessing.

Shut down the guest and use bridged or host only networking.

---

### Post by whoop on 2009-07-20
> **Meow27 said:**
> im on my laptop and i dont feel like going through the hassle of installing [L]AMP on my host, id rather have my guest feel all the stress. (lets just keep the discussion to that please)

after installing apache on my ubuntu 9.04 guest, i run "ifconfig" and copy/paste the ip on the host browser (to get the apache homepage "it works!", but i get nothing. i ping the IP and nothing comes back. 


as you can see, i dont know what im doing. help or guidance would be much appreciated. 
thanks 

-meow
Does it run on the guest (server)? As you probably don't have a window manager running try a command line browser like lynx

---

### Post by Meow27 on 2009-07-23
> **bodhi.zazen said:**
>  host only networking.

did the job. thanks!

---

### Post by bodhi.zazen on 2009-07-23
glad you are set up then. And thank you for posting the solution, it helps others with similar questions.

---

