---
title: "whole subnet responds to ping scan???"
date: 2009-05-27
forum: Security
---

### Post by ronin2307 on 2009-05-27
I am sorry I am using an ubuntu forum for this question, but i hope that somebody here has enough knowledge to explain me a linux firewall issue (at least i think that is the root of this)
anyway, my company owns a subsidiary in italy and I need to have access to their servers. because the email communication flow is extremely slow i decided to do some investigative work myself. I have a vpn tunnel established with the site which is on the 192.168.3.0 subnet. I know that the site only has maybe 20 PCs so I was hoping that a nmap ping scan would reveal which IPs are alive and potentially narrow down my candidates for the windows server. 
To my surprise ping scan returned ALL IPs on that subnet as alive. First i thought I screwed something up (still a possibility), but I used other tools to do a ping sweep and they all return identical results. ALL IPs alive, with NO ports open. Not even the gateway/vpn server through which I am connecting.

What does this have to do with linux? well, I know that they are running a firewall on a linux server (no clue which distro, but apparently it is old from what I am being told). so my question is this: is there a tool/setting in linux which could be configured to return echo replies for any scanned IP regardless of the actual existence of that IP on the scanned network?

---

### Post by lensman3 on 2009-05-27
Look at a program called nmap.  It is available for both Linux and Windows.  One of the options is to return the OS and version.  If you are doing the "ping" option, then look at the other available options.  Nmap needs the subnet to be entered when you scan/ping other hosts.

Also if you are vpn'ed through to the .3 subnet, I don't think the firewall (which is the vpn tunnel  host) would even show up.  If you have access to the .3 subnet servers, you should be able to see the ipconfig and route(s) the server has installed using a dos window. 

Hope this helps.

---

### Post by ronin2307 on 2009-05-28
> **lensman3 said:**
> Look at a program called nmap.  It is available for both Linux and Windows.  One of the options is to return the OS and version.  If you are doing the "ping" option, then look at the other available options.  Nmap needs the subnet to be entered when you scan/ping other hosts.

Also if you are vpn'ed through to the .3 subnet, I don't think the firewall (which is the vpn tunnel  host) would even show up.  If you have access to the .3 subnet servers, you should be able to see the ipconfig and route(s) the server has installed using a dos window. 

Hope this helps.

nmap was one of the tools i used  :-)
at this point I just have to hope that I can get some real answers from my italian counterparts. thanx

---

