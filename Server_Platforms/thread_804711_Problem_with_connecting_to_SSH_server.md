---
title: "Problem with connecting to SSH server"
date: 2008-05-23
forum: Server Platforms
---

### Post by hwang251 on 2008-05-23
I created an openssh-server on ubuntu, but when I try to ssh it from another computer I get this message:

ssh: connect to host "ip_address" port 22: No route to host

where ip_address is my the server's ip_address

---

### Post by NateMan on 2008-05-23
Well that message is telling you that the ip address of the server your connecting to isn't there or the port your attempting to connect to isn't open. How did you enter the command? was it in the form of ssh usrname@host/ipaddress? Is your ssh set to a different port than default or are you going through a firewall? Is the software firewall on your ubuntu box turned on? Give me a little more info and this should be easy to fix.

---

### Post by hwang251 on 2008-05-23
> **NateMan said:**
> Well that message is telling you that the ip address of the server your connecting to isn't there or the port your attempting to connect to isn't open. How did you enter the command? was it in the form of ssh usrname@host/ipaddress? Is your ssh set to a different port than default or are you going through a firewall? Is the software firewall on your ubuntu box turned on? Give me a little more info and this should be easy to fix.

I entered the command in the terminal and in the form of ssh usrname@host/ipaddress. 

There is no firewall and the port is set to 22.

And the software firewall is not turned on

---

### Post by tigerplug on 2008-05-23
Can you ping the hostname/ip address?

---

### Post by NateMan on 2008-05-23
Is the server on the local network or are you trying to connect to a remote server? pinging is a good next step.

---

### Post by hwang251 on 2008-05-23
> **tigerplug said:**
> Can you ping the hostname/ip address?

no

but the connection on the server is working, because I can ping a website

---

### Post by NateMan on 2008-05-23
can you get on the machine locally and check the ip address with ifconfig? I've had one reset a static ip address before I rebooted it for the first time before.

---

### Post by hwang251 on 2008-05-23
> **NateMan said:**
> can you get on the machine locally and check the ip address with ifconfig? I've had one reset a static ip address before I rebooted it for the first time before.

Yes I can get on the machine locally and the ip address is still the same

---

### Post by NateMan on 2008-05-23
have you checked your /etc/network/interfaces,  /etc/hostname, and /etc/resolv.conf? They should all match. also did you use the computers hostname or its ip address?

---

### Post by NateMan on 2008-05-23
Also have you tried a reboot? I know that is frowned on, but sometimes if the problem is really odd and can't be fixed by normal means, then it might help.

---

### Post by hwang251 on 2008-05-23
> **NateMan said:**
> have you checked your /etc/network/interfaces,  /etc/hostname, and /etc/resolv.conf? They should all match. also did you use the computers hostname or its ip address?

They matched

And I used the computer's ip address

---

### Post by NateMan on 2008-05-23
Well... can you ping out from the server? try to ping [www.google.com](www.google.com) or something. If that doesn't work, have you rebooted it since setting it up? Its worth a shot. I'd also check physical connections, although that is highly unlikely. What about pinging it from another machine on the network? What sort of box are you pinging from? I'd look at your local machine if you can ping out, but not into the box.

---

### Post by MJN on 2008-05-23
> **hwang251 said:**
> [I][can you ping the hostname/ip address?]

[/I]no

but the connection on the server is working

You need to find out why. If there's no firewall running then you should be able to ping. If you can't then you won't be able to SSH in either.

Describe your network layout, including all IP address and subnet mask details.

Mathew

---

### Post by hwang251 on 2008-05-23
> **MJN said:**
> You need to find out why. If there's no firewall running then you should be able to ping. If you can't then you won't be able to SSH in either.

Describe your network layout, including all IP address and subnet mask details.

Mathew

The network is through the school's network I'm at.

The ip address is the one found in ifconfig

---

### Post by MJN on 2008-05-23
That's no help at all unfortunately...

What is the IP address and mask of the client? And the server? 

Also show the output of **ip route** on both machines.

A traceroute from the client to the server might also be useful too (**traceroute <server ip>**)

Mathew

---

### Post by NateMan on 2008-05-23
Yes please post the information about the network. There shouldn't be anything of a security risk in that at all, since we would need the public ip address. That's on your router. Your on a school network? Do you know what their firewall does? It may not allow pc to pc connections of any kind.

---

### Post by hwang251 on 2008-05-23
For security I got rid of the traceroute

---

### Post by hwang251 on 2008-05-23
And when I run traceroute from server to client I get
all stars ***

---

### Post by MJN on 2008-05-23
Given the client and server are on completely seperate networks it looks like there are restrictions in place controlling what traffic types can be transited. ICMP ping restrictions are commonplace, but you would need to check with your network administrator whether SSH access to your server is allowed.

Mathew

---

### Post by NateMan on 2008-05-23
Yeah... that's because those are private addresses and traceroute only shows so many of those, obviously enough that it never gets to the non-private ones from the server. Please post your network information if you want accurate help. However, since that works, I imagine that your not allowed over the schools network to ssh into other boxes, if everything is setup correctly on your end. School networks are normally NOT designed to have people throwing up their own servers and eating up all that juicy bandwidth.

---

### Post by hwang251 on 2008-05-23
> **MJN said:**
> Given the client and server are on completely seperate networks it looks like there are restrictions in place controlling what traffic types can be transited. ICMP ping restrictions are commonplace, but you would need to check with your network administrator whether SSH access to your server is allowed.

Mathew

Even though we setup the server ourselves?

---

### Post by NateMan on 2008-05-23
also, I personally wouldn't post a traceroute from my box in a forum. That's public ips. You wouldn't even post your local network information.

---

### Post by MJN on 2008-05-23
> **NateMan said:**
> That's public ips.

Exactly, hence there is no security in trying to keep them 'secret'.

[quote=hwang251]Even though we setup the server ourselves?[/quote]

Yes. It sounds like it's a network issue (most likely by design given you've confirmed both machines have got network access). I trust you've confirmed the SSH server is working by SSH'ing to localhost on the server? (not that this would produce the same error)

Mathew

---

### Post by MJN on 2008-05-23
> **NateMan said:**
> Yeah... that's because those are private addresses and traceroute only shows so many of those, obviously enough that it never gets to the non-private ones from the server. 

They are not private addresses. The stars indicate a timeout i.e. the absence of an ICMP echo response within an acceptable time limit. The most likely cause for this is the (common) blocking of ICMP traffic on many Internet-connected routers. This is why the usefulness of ping is limited these days (whilst a positive response can be helpful a negative one means very little).

Mathew

---

### Post by NateMan on 2008-05-23
My bad, I meant private jumps, as in they were blocked. I personally wouldn't want to draw any attention to my specific server on a school network, just because of  temptation to other students on the local network. Every campus has some issues with this.

---

