---
title: "Can CUPS be configured to allow remote IP printing?"
date: 2007-03-15
forum: Server Platforms
---

### Post by nucklebone on 2007-03-15
Just wondering if this is possible. After much trial and error I am starting to assume, not.

I want to attach a USB printer to my Ubuntu machine (fixed IP address) and send print jobs to the Ubuntu machine (print sharing). BUT I want to be able to send print jobs to the Ubuntu machine from remote locations that are not on the same subnet.

I have successfully printed locally from the Ubuntu machine, also, my Macintosh that is on the same network/subnet can send jobs to the Ubuntu machine, but I have been very **unsuccessful** at sending print jobs from computers not located on the network/subnet.

This is a very simple task on my Macintosh that also uses CUPS. I just assume it works under GNU/Linux as well.

Anyone?

---

### Post by dashnak on 2007-03-15
Maye, off the top of my head, it has something to do with port-forwarding?

---

### Post by thomaswp on 2007-03-18
I have an old D-Link DP 101 print server.

After a little googleing I worked out that you use the UNIX LPD option with the IP address and the name of the queue as the two parameters.  

That worked fine for me but the ubuntu test page uses up a lot of coloured ink!!

---

