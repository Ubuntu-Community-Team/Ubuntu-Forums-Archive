---
title: "Netbios name resolution and port forwarding"
date: 2008-05-26
forum: Server Platforms
---

### Post by __fastcall on 2008-05-26
I'm a new Ubuntu user and I've set up a home server that I'm mostly quite happy with.

I just have two remaining issues that prevent the server from being completely awesome (It's already pretty awesome), and they've been causing me some frustration over the past couple of weeks.

First, I've set up a samba share for my windows machines to access, and everything works fine if I try to access the shares using the machine's local IP address.  However, I only have intermittent access to the samba share from my windows machine via its netbios name.

As an example, I can always get to the share from my windows box by browsing to \\10.0.1.199\share, but \\ubuntu-server\share only works occasionally.

The only other datapoint I have is that if I run into this problem, I can get the netbios lookup to start working again by pinging the IP explicitly.

So, after a while, when I lose access to the machine by its netbios name, I can run "ping 10.0.1.199" from a Windows command prompt, and I'll regain access.

My second problem is with port forwarding on my router.   I want to tunnel SSH traffic to the ubuntu server through NAT, and it works when I initially apply the port forwarding rules on my router but it stops passing traffic after a little while.

I wouldn't even bring up the second issue, as it sounds like a problem with the router, but I've successfully set up port forwarding to both a windows and mac machines behind the same router without any problems, and the behavior of "works for a bit and then craps out" seems vaguely similar to the netbios issue, both of which seem like some kind of network broadcasting issue.

I spent a lot of time searching google and these forums looking for similar issues, and couldn't find anything that seemed to help, so I'm hoping you fine Ubuntu community members can help point me in the right direction towards some more debugging I can try.

Thanks, and any help is much appreciated. :KS

---

### Post by dmizer on 2008-05-26
please post your /etc/samba/smb.conf file from the ubuntu server.

regarding forwarding ssh:
if your external session is inactive for a period of time, the server will disconnect the session as a safety precaution.  you can disable this, but it's not really a good idea.  when accessing ssh from remote, your best bet is to ssh, do what you need to do, and disconnect.

the same thing will not happen when accessing your ssh server from your local (trusted) network.

---

### Post by windependence on 2008-05-27
Putting a dns entry in your windows host file may also help.It's in C:\WINDOWS\system32\drivers\etc\hosts. Edit the file with notepad and add this line:

ubuntu-server      10.0.1.199

Save the file and of course, reboot. :)

-Tim

---

