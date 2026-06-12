---
title: "FTP Not Working Behind Router"
date: 2007-10-18
forum: Server Platforms
---

### Post by austin987 on 2007-10-18
I've setup proftpd using Gproftpd and all has been working fine for several months. A couple weeks ago (not sure why, still trying to figure out what changed), no one can access the server from outside the firewall. I initially thought it was a DNS issue, and DYNDNS hadn't updated yet, but trying the IP address directly doesn't work either. Behind the firewall works fine. I've checked the router and set the server (192.168.1.200) to be the DMZ, so all open ports are sent there. Firestarter is set to have 20-21 and 60000-61000 open to everyone. If I'm on a computer behind the firewall and use [ftp://192.168.1.200](ftp://192.168.1.200), it works fine, but using [ftp://75.109.xxx.xxx](ftp://75.109.xxx.xxx) (public IP), it fails. Same goes for dyndns address.

Anyone got any ideas?

---

### Post by mkzimms on 2007-10-18
whos your service provider?  i know with my cablevision account they block most of the good ports.. 80, 8080, 21, 20, 25.... you may have to change the port proftpd is using and just come in on that port instead when you connect.  i use 521.  It also seems like it worked for you at one point, but maybe you should try using pasv too.  make sure your pasv ports are open as well.

---

### Post by MJN on 2007-10-18
Are you using passive or active FTP?

(If you're not sure what I mean check out [http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html) for a good explanation of the significance, and pain, of this - strange though that things **were** working and now they're not so I'd suspect some explicit change rather than bad config)

It would also be useful to know in exactly what way the connection is failing i.e. how far you're getting.

Mathew

---

### Post by austin987 on 2007-10-19
Suddenlink, when trying with 521, not much happens:

Status:	Connecting to xx.dyndns.org:521 ...
Error:	Unable to connect!


Port 21 gets a bit further:
Status:	Connecting to xx.dyndns.org ...
Status:	Connected with xx.dyndns.org. Waiting for welcome message...
Then stalls for a minute or so, and fails.

---

### Post by MJN on 2007-10-19
Port 521 would only work if you'd set the FTP server to use that port.

Do your FTP logs say anything? Certainly enable verbose logging (in the server and client) and post the output.

Are you using passive or active FTP? If passive have you set the FTP server to always use a particular port/range (I see your firewall has been configured with this in mind so I'm assuming this is the case). Speaking of firewalls, I take it you've tried connecting with it disabled?

Mathew

---

### Post by austin987 on 2007-10-19
I changed the FTP server to use 521 when I attempted that, as well as opening it in the firewall. It worked behind the router again, but still not when attempting to go over the internet rather than intranet. I'll check the logs and see if I can enable verbose logging and report back.

It was using passive, but I've tried active as well. Same result.

I'll also try with disabled firewall and see if that helps.

---

### Post by austin987 on 2007-10-19
Disabling the firewall made no difference. Logs don't show anything interesting.

---

### Post by MJN on 2007-10-19
What's interesting? Did the server show any connection at all?

If the logs aren't showing anything then you're best running a packet sniffer at the client and server end - you will then be able to see what packets are being sent and tally these against what's being received. The responses can be similarly analysed which should hopefully pin point exactly what is happening (or more likely what is *not* happening!).

If you're happy to share your IP (privately) I can attempt a connection from here and at least see things from the client perspective (no need to divulge any user credentials as it's clear it's not even getting that far).

Mathew

---

### Post by MJN on 2007-10-21
Thanks for the IP.

I'm able to connect okay:

```
$ ftp ###.###.###.###
Connected to ###.###.###.###.
220 ######## FTP Server
Name (###.###.###.###:#####): anonymous
331 Password required for anonymous.
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> disconnect
221 Goodbye.
ftp> quit

```Of course without any account credentials I can't go further (which is quite significant with FTP given the use of a seperate DATA port file transfers) however as I can seemingly get further than you've been seeing so far I suspect either the problem is fixed or the cause is with your clients...

Mathew

---

### Post by austin987 on 2007-10-21
Yes, I got a hold of someone at linksys support that actually  knew a thing or two. They didn't know why it was silently dropping the traffic, but suggested I try changing the MTU from Auto (1500) to manual, and set it at 1300. After that, it started working again. Doesn't explain what caused it, and it may reduce bandwith a bit, but at least my FTP is working again.

Thanks for all the help!

---

### Post by MJN on 2007-10-21
That's great news - good to hear it's now working.

The cause will likely have been that fact that your end-to-end connection could not support the default 1500-byte MTU and that the router (or indeed some other router, or firewall) was not allowing the 'fragmentation needed' ICMP packets back hence the end points were blissfully unaware that their packets weren't getting through.

Mathew

---

### Post by dmizer on 2007-10-22
> **austin987 said:**
> I've checked the router and set the server (192.168.1.200) to be the DMZ, so all open ports are sent there.

just fyi ... (in your router's case) setting a DMZ means that no ports are filtered.  it does /not/ mean that all ports are forwarded.

the distinction is that incoming packets on port 21 are not filtered so they can enter your network. but if port forwarding is not set, the packets do not have a destination so they are dropped.

a DMZ is desirable in a gaming situation where outgoing packet replies may return on many different ports.  in this case, the incoming packet is a response to a request, so the router knows where to forward it.

but in the case of an ftp server, incoming packets are not a response to a request, so your router doesn't know what to do with them unless you explicitly define it.

---

### Post by MJN on 2007-10-22
> **dmizer said:**
> just fyi ... (in your router's case) setting a DMZ means that no ports are filtered. it does /not/ mean that all ports are forwarded.
 
That's not true in the case of Linksys routers. On a Linksys all ports that aren't explicitly set for forwarding elsewhere are forwarded to the DMZ host, if specified.
 
> but in the case of an ftp server, incoming packets are not a response to a request, so your router doesn't know what to do with them unless you explicitly define it.
 
The OP already has ports 60000-61000 forwarded to the FTP server and presumably the config is set to direct the client to use a data port from this range.
 
This is all a moot point now however as now that the OP has lowered the MTU it's all back up-and-running.
 
Mathew

---

### Post by austin987 on 2007-10-29
Apparently off site users are still having problems. I can access the site from within the network using the internal IP/external IP/dyndns address. When an offsite user attempts, here is what they get:

When I try user:  wrong_password I get  “530 Login incorrect”

 

When I try user : correct_password I get “The connection to the server was reset while the page was loading”


Anyone got any ideas? I'm stumped on this. MTU is still set to 1300, and this computer is still the DMZ.

---

### Post by austin987 on 2007-10-29
Got some more info, seems he cannot connect with passive, but active is working. I've opened ports 20-21 for FTP, as well as 60000-61000 in the firewall, and set them to be the passive range in the proftpd.conf file.

---

