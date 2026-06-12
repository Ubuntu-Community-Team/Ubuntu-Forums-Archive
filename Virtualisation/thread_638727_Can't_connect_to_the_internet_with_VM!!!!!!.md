---
title: "Can't connect to the internet with VM!!!!!!"
date: 2007-12-12
forum: Virtualisation
---

### Post by cousin-it on 2007-12-12
I am running Ubuntu 7.10 on a Dell laptop. I have VMWare 2.0Beta running with Windows XP Pro. Everything works except internet on the XP VM. It will browse the network. It will even resolve IP's when you do a ping and try to go to a webpage. But it won't go to a web site. It is just times out and gives me a "Page Cannot Be Displayed error". Has anybody else had this problem? If so, how do I fix it? I am fairly new to Ubuntu and definitely new to VMWare. Please help me to get this running.

---

### Post by cousin-it on 2007-12-12
Sorry for the trouble. I figured it out. Thanks anyway.

---

### Post by johnnybirdman on 2007-12-12
> **cousin-it said:**
> Sorry for the trouble. I figured it out. Thanks anyway.

I was going to try to get this same setup running today.  what documentation or guide did you use.  what was the solution to your problem for future users knowledge??

Thanks,
J

---

### Post by cousin-it on 2007-12-12
i used the documentation on this post to set up my VMWare server and install windows XP Pro [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

My problem with the internet was my firewall was blocking http traffic for my IP address. (duh, i should have seen that earlier)

Everything is working fine now. I got the best of both worlds.

---

### Post by johnnybirdman on 2007-12-12
> **cousin-it said:**
> i used the documentation on this post to set up my VMWare server and install windows XP Pro [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

My problem with the internet was my firewall was blocking http traffic for my IP address. (duh, i should have seen that earlier)

Everything is working fine now. I got the best of both worlds.

Thanks for the response.

Does the virtual (guest) OS get it's own IP, or does i have the same IP as the host?  

I'm thinking about may trying to run a server but don't know if that is supported under vmware, I know it's not under virtualbox according to their website.

---

### Post by cousin-it on 2007-12-12
My guest OS got a different IP from the Host OS. 
I think servers are supported in VMWare. I am new to all of this, so I am not sure.

---

### Post by johnnybirdman on 2007-12-12
> **cousin-it said:**
> My guest OS got a different IP from the Host OS. 
I think servers are supported in VMWare. I am new to all of this, so I am not sure.

Thanks.  I'm also (obviously) new to this as well.  Looking forward to giving it a try.

---

### Post by Blown306 on 2007-12-13
> **johnnybirdman said:**
> Thanks for the response.

Does the virtual (guest) OS get it's own IP, or does i have the same IP as the host?  

I'm thinking about may trying to run a server but don't know if that is supported under vmware, I know it's not under virtualbox according to their website.

With VMWare you can run your virtualized with bridged or NAT networking.  With bridged, you assign IP's to the virtual nic's out of your subnet (either DHCP or static).  NAT will use the host's IP address and translate it to each virtual.

I run virtualized Windows 2003 Servers, bridged with static IP's on an Ubuntu host with no problems...

---

