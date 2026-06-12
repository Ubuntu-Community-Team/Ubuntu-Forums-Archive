---
title: "Apache accessing remote Ubuntu machine"
date: 2005-12-21
forum: Server Platforms
---

### Post by jaykup on 2005-12-21
I would like an apache server box to be able to access another apache box through the lan and route it out its internet connection.

This is my current setup

Internetx1 > Ubuntu apache box 1> (local network) -|
Internetx2 > Ubuntu apache box 2> (local network) -|

(local network) is all connected together, and the internet lines are seperate (different lines).

Thats very basic, there are routers, etc, but you get the idea.

I basically want to set up a mirror between the two sites, but don't want to have the two boxes having the same data (too much of it)

How can I make it so Ubuntu apache box 1 can load apache box 2's site through the lan, then send it out its internet connection (NOT a redirect)

This is for network load balancing.

Or maybe there is an easier way to do this?

---

### Post by jaykup on 2005-12-22
Just set up NFS...

Did that and everything works the way I wanted.

---

