---
title: "multiple ssh servers"
date: 2016-01-20
forum: Server Platforms
---

### Post by matt18 on 2016-01-20
I have an idea i want to try out. I have finished making the ssh server and things are working good for now. i may redo things later on. However, here is my idea. I want to create 7 ssh servers. Each will be a different location. I would like it so when im on the host machine, and i create an ssh connection for tunneling http(i use public hotspots all the time), that the data is randomly sent through the 7 servers. I know it will slow down my browsing experience but i want to see if i can accomplish said task. if not, thats cool. 

thanks

---

### Post by MAFoElffen on 2016-01-20
You know the concept of a client/server model right? Server run services (which ssh server is just one of many server services) which open a listener for that service on a port (which in the case of ssh is port 22) ... which a client initiates a call to connect to that service.

The best explanation I've seen on how ssh works/communicates is [here]("http://h71000.www7.hp.com/doc/83final/ba548_90007/ch01s04.html"). I run an ssh service on all of my servers, immaterial if Unix, Linux , or Win. You can tunnel unencrypted data though a secure shell tunnel. Although you could do http tunneled through ssh, why do that? Do you have local network or local domain app's and pages using http? If so, then you could set domain policies to allow hhtp into your net, but not out. Or if you have to allow some http out, but others as local, you can set read permission to these page to a local user group... right? What about using https and certs? There are other ways. And those do not add to your overhead or degrade performance and network load.

If you are doing other stuff and thinking about strengthening up your security, then maybe you might think about VPN(?) Or are you just doing things to learn? 

Because, your comment on a safe way "to use public Hotspots"... the key term therm where that falls apart is "public"... a tunnel needs two sides of the tunnel that are talking the same language. One side speaking only Yiddish and the other speaking only Mandarin ... doesn't work out well. Public Hotspots do not use ssh. So you have no other ride to your tunnel with that.

My questions are:
(a) What are you trying to accomplish?
(b) What are your requirements?
(c) What is your scope and boundaries?

Just presenting some things to think about. You could always do what you want, but you need to be informed enough to make your decision.

---

### Post by matt18 on 2016-01-21
my goal is

 I want multiple ssh servers so that the data from my host is randomly sent through the 7 ssh servers. onion routing in a way

thanks for the above info:)

---

### Post by MAFoElffen on 2016-01-22
> **matt18 said:**
> I want multiple ssh servers so that the data from my host is randomly sent through the 7 ssh servers. onion routing in a way

You still didn't say who the clients are and if they are on the same NID as the host (local) or external.

---

### Post by matt18 on 2016-01-24
thats because i wasnt paying attention, i was in calc 3 class when i saw this haha.. anyway. as of right now, there will be one client and thats me. no matter where i am in the world, i will be the only client. 

define NID. im guessing network ID. I do not know exactly how to anser this because my ultimate goal is to have an ssh server at 7 different friends house and then no matter where i am in the world be it someones house or public hotspot, i can tunnle in for a browsing session. So to answer if we will be on same NID, no, most likely not. Even if i set up all the ssh servers at my house, i would not tunnel into them, i would just use my wired connection

thank you:)

---

