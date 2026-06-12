---
title: "SSH fails over WAN"
date: 2009-06-18
forum: System76 Support
---

### Post by ctsdownloads on 2009-06-18
Not having any luck with this, spent the better part of three days on it and I am at my wits end.

SSH works in LAN, fails outside of LAN. Different ports, same thing.

Tested port 23, it does not time out and gives me the ever helpful connection refused message. Both /etc/hosts.deny and /etc/hosts.allow are correct, too.

> ssh -p 23 user@WAN-IP -v

OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to WAN-IP-Address [WAN-IP-Address] port 23.
debug1: Connection established.
debug1: identity file /home/uzer/.ssh/identity type -1
debug1: identity file /home/uzer/.ssh/id_rsa type -1
debug1: identity file /home/uzer/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host


Now with more details, can someone point me in the right direction?

For testing purposes, I am just using the password for entry, as I deleted everything from the ~./ssh folder(s).


Also, when I am successfully connecting to the same box over the LAN, I get the same as above, but with this right before asking for a password.

> debug1: Next authentication method: password

So, it stops before asking for a password when accessing via the WAN??

Router is working with ports forwarded, too. And based on the above, it's connecting....

---

### Post by albinootje on 2009-06-18
> **ctsdownloads said:**
> 
Tested port 23

Why are you using port 23 ? That is the default telnet port, which might be blocked/filtered by your ISP or router.

And are you using denyhosts or fail2ban on your ssh-server based machine ?

Did you look at /var/log/auth.log ?

---

### Post by ctsdownloads on 2009-06-18
> **albinootje said:**
> Why are you using port 23 ? That is the default telnet port, which might be blocked/filtered by your ISP or router.

And are you using denyhosts or fail2ban on your ssh-server based machine ?

Did you look at /var/log/auth.log ?

I did look into the log and I am using 23 as it has yielded some signs of life over the WAN while 22, 2222, and pretty much everything else is DOA.

On the LAN, 22 and 23 both work perfectly....yet according to my verbose output, it's not a connection issue with 23 and 22 just times out with nothing.

---

### Post by thomasaaron on 2009-06-19
Is this issue still open? Looked like you fixed it here...
[http://forums.verizon.com/vrzn/board/message?board.id=FiOS_Internet&thread.id=5346](http://forums.verizon.com/vrzn/board/message?board.id=FiOS_Internet&thread.id=5346)

---

### Post by Derath on 2009-06-19
Out of mild curiosity (and not trying to make assumptions or inferences) are your systems behind a router? If they are you need to open that port on the router and tell it which system to connect to (see port forwarding on your specific router).

Also on another note, if you are opening an ssh port to the Internet, I would also suggest changing the port number to something non-default (i.e. to port 1000, 8000, 8080, etc). When I had a server with ssh accessing from the net, I got all sorts of virus and hacker attempts to access my box. Once I changed ports to something other than standard access ports (i.e. something other than 22, 23, 80, 143, etc) I seriously cut the traffic and hack/crack attempts from 50+/day to 3/day (those three are from port scanners and proxy attempts)

---

### Post by ctsdownloads on 2009-06-19
> **thomasaaron said:**
> Is this issue still open? Looked like you fixed it here...
[http://forums.verizon.com/vrzn/board/message?board.id=FiOS_Internet&thread.id=5346](http://forums.verizon.com/vrzn/board/message?board.id=FiOS_Internet&thread.id=5346)

Yeah, it was resolved. :) As stated in the above post, it was determined very quickly to be the router due to testing off of my FiOS WAN and the fact that it was working fine "in LAN".

What the magic bullet? Simple, I had messed up my port forwarding. While most routers would never make this a problem, the crappy Verizon router is very specific.

So I had TCP 22 -> 22 . This is wrong. It needed to be TCP **Any** -> 22 .

That single changed had things working outside of the LAN. Total newbie mistake....really embarrassing. Also, I run the Verizon FiOS router with a Draytek router in bridge mode for stability and ethernet ports, better wifi, etc.

---

### Post by ctsdownloads on 2009-06-19
> **Derath said:**
> Out of mild curiosity (and not trying to make assumptions or inferences) are your systems behind a router? If they are you need to open that port on the router and tell it which system to connect to (see port forwarding on your specific router).

Also on another note, if you are opening an ssh port to the Internet, I would also suggest changing the port number to something non-default (i.e. to port 1000, 8000, 8080, etc). When I had a server with ssh accessing from the net, I got all sorts of virus and hacker attempts to access my box. Once I changed ports to something other than standard access ports (i.e. something other than 22, 23, 80, 143, etc) I seriously cut the traffic and hack/crack attempts from 50+/day to 3/day (those three are from port scanners and proxy attempts)


Totally agree. I only use 22 for initial setup, then I change the port over to 2222 in most cases. Using 23 however, is "okay" (telnet), but you are 110% right about using less used ports. :)

---

### Post by Derath on 2009-06-19
No problem, believe me, we've all made ones like that before. I'll even share one, I was upgrading my home server from Fedora 1 to Fedora 3, and the server wouldn't read the disk. Rebooted several times, even went so far as changing the drive out thinking the servo or lens or something was going bad.

Three hours later I'm frustrated and annoyed when I look at the disk and it dawns on me, I'm trying to use a DVD in a CD drive...

DOH! #-o#-o#-o :oops: ](*,)

---

### Post by clancyhood on 2010-11-16
To add my 2c

Having configured my ports correctly and tested working on lan, port forwarding tested and working well with apache (80) and wake-on-lan (9), I kept getting "connection refused" when trying

```

ssh -p {my-port-no} {my-extenal-ip}

```

... to find that my router (netgear DG834G) had trouble when forwarding internal -> external -> internal.  When I ssh'd into a vps I run, and ssh'd back from that shell, I got in.  

If you don't have an external machine to ssh into to test out your ssh port forwarding and you're having problems on this router, you might have to take your laptop to an internet cafe or ask a friend to test it out or something.

---

