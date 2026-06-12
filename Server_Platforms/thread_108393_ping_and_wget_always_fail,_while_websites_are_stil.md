---
title: "ping and wget always fail, while websites are still accessible"
date: 2005-12-25
forum: Server Platforms
---

### Post by OneSeventeen on 2005-12-25
I can still access the websites on my ubuntu webserver, and can SSH in, FTP in, and even connect remotely to a few databases.

Unfortunately anything "outgoing" such as ping and wget fail.

Well, actually I can ping the servers on the network fine, I just can't seem to get out of the network.  (I can even ping servers on different subnets)

if I ping an outside source such as ubuntu.com or google.com, it looks up the IP, and gives me the IP just fine, but can't seem to ping it.

I did set my static IP, Subnet Mask, Gateway, and Broadcast, and still can't seem to get out of the network.

I can SSH to it from outside the network, and the websites are publically viewable... so I'm at a loss.

I'm assuming this is an issue with the network that the server is on, but wanted to check first to see if it might be a network configuration error.

---

### Post by xmastree on 2005-12-26
It sounds like your isp has something strange going on. Are you using a proxy server with your browser? Try to disable it, you should still be able to access web pages. If you can't, it looks like everything must pass through their proxy.
I've had similar problems before, it was the isp's problem.

---

### Post by OneSeventeen on 2005-12-26
It is a server at a university that does not use a proxy server (at least it didn't before, I'll ask the network admins if they added one for some weird reason.)

I don't have a GUI, so I'm doing everything via SSH, which is what makes it seem odd to me.  I can view the websites from home that the server is hosting, and I can SSH into the server just fine.  But when I try to wget (such as when trying to apt-get install) I just get errors.

Up until now, I can say for sure that there was no proxy server, and I doubt they have one in place now, but I wouldn't be surprised if they did anything else odd with their network.  (odd meaning something I don't know of, since I'm not the network admin there, I'm just a web developer with a server)

I wouldn't be surprised if it was a network configuration issue, but I can't see what I could be doing wrong.

---

