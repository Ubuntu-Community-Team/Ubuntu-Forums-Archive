---
title: "Particle Swarm Simulation help: Grouping"
date: 2009-06-10
forum: The Cafe
---

### Post by dracule on 2009-06-10
Hey all, 

I was trying to "group" particles together based on attributes (which are currently assigned randomly). 

Well I got it working in one dimension and two dimensions but I am running into a problem when I am applying this to my ultimate goal: Grouping users. The problem lies in the fact that not all users are active. Some users create an account and then leave it sit. Thus my algorithm is wasting resources computing their trajectory and what not.

So I ask you is there a current swarm model that is not time based? The current swarm models I have examined  work based on an arbitrary unit of a cycle: going through each particle one by one, once it has finished it has finished one cycle. But what I was hoping for was a model that worked based on activity e.g. when a user changes their attributes then the algorithm computes their trajectory and what not. That way it would not waste resources on "dead" users.

So if anyone has any suggestions I am open to them :)

---

### Post by extempore on 2010-08-23
Allow idle users to be eliminated from calculations / algorithms.
Criteria have yet to be determined ... e.g. no activity for a while, etc.

here is a proof of concept algorithm I wrote where particles not making the mark are recycled:

[http://74.68.149.182:8080/is/isapplet.html](http://74.68.149.182:8080/is/isapplet.html)

Cheers

---

