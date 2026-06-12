---
title: "Lost connection to my server?"
date: 2011-10-10
forum: Server Platforms
---

### Post by ashgard on 2011-10-10
Hey 

I recently setup a server to host my own website, easy sharing of files and so on. Today I tried to connect to my server but somehow it wasnt working anymore. However, I havent changed anything. 

To troubleshoot the problem I did the following:
1. Tried to ping from a computer in my network to the server (with a fixed ip), but the destination host is unreachable.
2. Plugged a monitor + keyboard on the server and looked at the ipadres (ifconfig). The eth0 device still has the same ip as I set it to.

Now I already kind of run out of ideas on how to trouble shoot further. It seems that the pc is running and has the proper ip. What else can I check to see what is wrong? 

Thanks for your help.

---

### Post by arrrghhh on 2011-10-10
I would first ensure you have a link light on both sides - in the server and on the router/switch.  Assuming there's no layer-1 issues there, move up to the other layers.

Can you ping the gateway from the server?  How about other machines?  Anything on the internet?

---

