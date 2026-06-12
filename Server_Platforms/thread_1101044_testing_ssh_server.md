---
title: "testing ssh server"
date: 2009-03-19
forum: Server Platforms
---

### Post by gibxam on 2009-03-19
I have created a hostname that uses my ip with dyndns.org (for example purposes it is test.homelinux.org). I have also created an ssh server with openssh.

When I test my connection by using the command
```
ssh max@localhost
``` I successfully connect to my desktop?/ssh server?/home server? I'm not exactly sure what I am connecting to.

However when I try the same method except using
```
 ssh max@test.homelinux.org 
``` then nothing happens.

Why is this happening? Perhaps the answer to the first question will already answer this second one but thank you for your time.

Max

---

### Post by Nxion on 2009-03-19
Well are you trying to access test.homelinux.org from inside or outside your network?

---

### Post by gibxam on 2009-03-19
From inside, I am just trying to see if it works.

---

### Post by hictio on 2009-03-19
> **gibxam said:**
> From inside, I am just trying to see if it works.

Ok, but, the IP address for 'test.homelinux.org' points to the private one (valid only inside your LAN), or the public one, accessible over the internet only?

---

### Post by dunkar70 on 2009-03-19
If you are using a router or if your cable/DSL modem has a built-in router, you need to set your router to forward port 22 to the computer to which you are trying to connect. The process varies with each router brand and model, so there is no single set of instructions that works for all routers. The manual for your router will provide some guidance to port forwarding.

The statement above assumes the text address (test.homelinux.org) is correctly configured and is resolving to the public IP address that your Internet service provider has assigned to you. Try running a trace route to your URL. You should see a hop for your router, assuming you do not have more than one router configured.

---

### Post by Dr Small on 2009-03-20
You need to know the LAN IP Address of your system running the SSH server. You will need to log into your Router and setup port forwarding from the public port of 22 to the private port of 22 on your system's LAN IP address. See Portforwad.com for specific instructions on your router:
[http://www.portforward.com/](http://www.portforward.com/)

Next, your DynDNS.org account hostname should point to your WAN (Public) IP Address, not the LAN (private) one. So, when you connect, it will resolve and transport like this:
```

++test.homelinux.org++
 +(Resolve Public IP Address)+
  +Connect to Public IP Address+
   +Connect to Router+
    +Forward INBOUND Connection to LAN IP on port 22+
     +Traffic is directed to SSH Server on LAN IP at port 22+

```

It is really, that simple.

---

### Post by gibxam on 2009-03-20
Thanks a lot for all your help everyone, everything is cleared up. I've also modified sshd_config to use a non-standard port and configured my linksys router to forward that port using the advice in this thread :)

Max

---

