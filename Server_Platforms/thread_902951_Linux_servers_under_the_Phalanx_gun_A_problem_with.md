---
title: "Linux servers under the Phalanx gun: A problem with people, not code"
date: 2008-08-27
forum: Server Platforms
---

### Post by kustomjs on 2008-08-27
Hi Guys
I was just reading this topic at:[http://blogs.zdnet.com/security/?p=1803](http://blogs.zdnet.com/security/?p=1803) is ubuntu going to fix this problem? because I closed off my port 22 connection onto my router can hackers still get through my port 22 even if I closed it off?

---

### Post by cariboo on 2008-08-28
If you port is closed you shouldn't have anything  to worry about

---

### Post by windependence on 2008-08-28
Cariboo is right. This is one of the reasons I recommend a hardware firewall over a software firewall among others. Having a software firewall as your only means of protection also means if someone sends enough junk your way to keep your firewall so busy it consumes all the system resources, they just took your system down, even though they weren't able to break in. Although this can happen to hardware boxes also, it takes much more traffic to make the hardware box skip a beat.

Please note what this article says before you get scared:

> The attack appears to initially use stolen SSH keys to gain access to a system, and then uses local kernel exploits to gain root access.

They have to steal your ssh keys first, not an east thing if you are set up right.

If you REALLY want to get scared, read this week's Windoze vulnerablilities........and there will be another next week, and the next, and the next, and the....well you get my point. These exploits don't happen often in *nix.

-Tim

---

