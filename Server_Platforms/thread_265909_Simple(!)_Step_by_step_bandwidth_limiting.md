---
title: "Simple(?!) Step by step bandwidth limiting"
date: 2006-09-26
forum: Server Platforms
---

### Post by lozzd on 2006-09-26
Hello,

I have read through lots of posts reading about traffic shaping and QoS etc. Now I'm completely confused in a muddle of iptables, CBQ, tc, oh deary me.

Anyone really good with these things? Because all I want to do is limit inbound and outbound traffic on port 6969 on my server to 20 maybe 30kb/sec. 

Unfortuntely I don't have time to read through all the guides as my tracker on port 6969 is already leeching bandwidth and is costing me a fortune! Also, I'm not confident enough that I'm not going to cut off all access to my server (I only have remote SSH access)

Can anyone make this simple?!

Thanks in advance!
Laurie

---

### Post by lozzd on 2006-09-26
I managed to get CBQ "working". Doesn't seem to do what I want. 

Is there a way to limit bandwidth by application?

Thanks!

---

### Post by airtonix on 2007-04-14
yep get trickle.

> sudo apt-get install trickle

and to run it an example is : 
> trickle -d 20 -u 20 `command-of-program-you-want-to-shape --with-any-arguments-it-might-use`

i used it to shape firefox when my adsl gets shaped...wy? coz it increases lag in my world-of-warcraft session....if i dont.

---

