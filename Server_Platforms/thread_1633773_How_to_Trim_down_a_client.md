---
title: "How to Trim down a client"
date: 2010-11-29
forum: Server Platforms
---

### Post by jgeissin on 2010-11-29
Built a LTSP.  Works great right out of the box!  Used the Alternate CD and followed the instructions, for once things went as advertized!  Updates take awhile in that they go into the client build!
Using older Neoware ThinClient, boots and runs fine, but it is SLOW.  I know this is a slow processor.
How do I pare down the sessions so that I can get better performance, run only Firefox and local printing (USB) so that I can use these devices as applicances in a point of sale type environment?
I am going to bond the server NICs to help.
Should I use a local drive for swap and temp?
Thoughts?
This is an 'on the cheap' project.  I'm trying to avoid a WinDOZE client and make the terminal as slim as possible.
My thanks in advance!

---

### Post by SeijiSensei on 2010-11-29
I believe LTSP sessions run on the server and are merely displayed on the client.  You probably need a heftier machine as a server, or perhaps just a lot more memory.  What are the server's specs?

---

### Post by jgeissin on 2010-11-30
Supermicro 5013C-i
P4 3G
2G RAM

I'm feeling that the best alternative is a itx based client that is stripped down to just what is needed.

Thanks for the quick response!

---

