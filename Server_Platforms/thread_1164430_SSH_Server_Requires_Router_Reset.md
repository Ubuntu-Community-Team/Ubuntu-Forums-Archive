---
title: "SSH Server Requires Router Reset?"
date: 2009-05-19
forum: Server Platforms
---

### Post by bluedrgn on 2009-05-19
Hello all, first post here and I'm just getting started with setting up an Ubuntu SSH server on an old machine I've had sitting around.

It seems to be working perfectly whenever I connect from within the network, no gripes there. However, when connecting using my external IP it only sometimes works. This seemed really strange to me so I did some troubleshooting.

Turns out that I can access the server from my external IP only within the space of a few minutes after resetting my router, then the connection starts timing out and I cannot get it back without resetting the router once again. There could be other cases, but this is the one that works consistantly.

I have the server configured to listen on port 2222 and my router is set to forward all requests made on that port to my external IP to a static local IP corresponding to my server. 

My ISP does assign me a dynamic IP, but it hasn't changed over the course of my testing this issue. I plan on hooking into a dynamic IP update service once I get this running. 

Now, I know that various routers will not allow looping back for locally originating requests so I used grc.com's port scan to check if port 2222 was even considered "closed" from an external network. The test told me that I was "stealthed," meaning it got absolutely nothing back. 

I have read quite a few posts all over the place and the most I can figure is that there is some vague problem with how my modem is configured.

So I'm baffled. I'm pretty sure that I've got everything set up correctly. What am I missing? Thanks for your help!

---

