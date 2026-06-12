---
title: "External file transfers bogging down network"
date: 2009-09-21
forum: Server Platforms
---

### Post by alienatom on 2009-09-21
I was wondering... Is it normal for sftp transfers to slow a network down?

What I mean by that is if a user is accessing files via sftp which reside on my 9.04 box, should that reduce the connection speed of my entire home network when a user downloads a file? File sizes are around 200 to 400 megabytes in size.  Once the file is finished connectivity returns to optimal rates. 

I am doing this in a home environment (via cable internet) because I want to test out file transfers before I implement it in the "real world." 

I wasn't sure if it had anything to do with my internet provider or the asynchronous of upload/download speeds or it was some configuration withing the server itself that I can't seem to figure out to save my life.

Also, transferring files locally does not affect the network speed at all. Which most likely makes sense because I am not going off the network.

I suppose this is a start. If anyone could voice in, it would be much appreciated. 

Thanks in advance . . .

---

### Post by stlsaint on 2009-09-21
that would sound about right...as people download from your server they will be using bandwidth. The more people downloading the more bandwidth and the slower your connection will seem. Locally (in home) not so much!

---

### Post by alienatom on 2009-09-21
I probably should've clarified. Currently while I am testing, I am only using one user as a test subject. However, I am beginning to think that it is the limits of home use.

---

### Post by stlsaint on 2009-09-21
well in that case you need to start looking at what it is you are working with...what kind of server hardware do you have...is your internet the very basic...etc etc! these are variables that can effect your overall performance.

---

