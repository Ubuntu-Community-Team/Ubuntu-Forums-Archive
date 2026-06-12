---
title: "Private Radio"
date: 2009-07-02
forum: Server Platforms
---

### Post by Pyker on 2009-07-02
Hi everyone.

I am planning to make a home server. It will be running Ubuntu Server Jaunty.
I've got it all covered (Apache,SSH,FTP,etc) except for the radio part.

The computer will be connected to a wireless router. The other computers will access the computer's local IP to access it.

I want to make a radio that works only on my local network, that is, no internet access, however, I am totally new at this radio stuff.

Also, the radio stream has to work on Windows computers (I tried to convince then to use Ubuntu :)), and must have some sort of API.

I've heard of ShoutCast, and I've already found an API for it, however, I am not sure if it works without advertising the radio on shoutcast's website.

Any help would be appreciated.

Thanks,
Pedro Cunha

---

### Post by windependence on 2009-07-03
It would be best if we had at least some idea of what you are trying to do. As you describe it, I have no idea.

-Tim

---

### Post by arijit on 2009-07-03
I think he wants to setup a radio streaming server which should not be accessible outside his LAN. His streaming server will be setup on Ubuntu and other listener PCs may run non-Linux OS.

I don't know much about setting up a radio streaming server, but look at IceCast ([www.icecast.org](www.icecast.org))

---

### Post by Pyker on 2009-07-03
I'm planning to do exactly like arijit said.
Thanks for the link, I'll give it a look.

---

### Post by johnh10000 on 2009-07-14
[QUOTE=Pyker;7553731]Hi everyone.

I am planning to make a home server. It will be running Ubuntu Server Jaunty.
I've got it all covered (Apache,SSH,FTP,etc) except for the radio part.

How did you get on with icecast?  I am planing to do the samething.  All bar, I will probabbly be broadcasting to the net sometime soon.

Want to know how to use the thing first.

---

### Post by Pyker on 2009-07-17
Icecast is kinda easy to work with.

The main problem that I'm trying to solve is that, when I connect to the radio, the sound that I hear is not live, that is, it's recorded (to a file, that is later read by the server).

---

### Post by johnh10000 on 2009-07-17
> **Pyker said:**
> Icecast is kinda easy to work with.

The main problem that I'm trying to solve is that, when I connect to the radio, the sound that I hear is not live, that is, it's recorded (to a file, that is later read by the server).

Well I can talk to the thing now.  

Next tpo persuade ices, to serve files I think.

Then serve live-ish audio,

I seem only to beable to captur mik, cd or aux.

Anyway to capture the whole audio output?  without sending it out aof line out and grabing it on line in. messy

---

