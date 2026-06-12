---
title: "SSH, FTP, SMB lockup"
date: 2007-05-22
forum: Server Platforms
---

### Post by Endless Bard on 2007-05-22
I'm running 7.04 server on an old 500mhz/512MB box, and I'm having some troubles.  The point of this machine is as a multipurpose server; I have apache, openssh-server (sshd), vsftp, samba and openvpn installed on it.  The machine sits behind a separate router with a dynamic DNS entry.

Everything connects as expected, and I'm able to connect to the various services without any difficulty both from within the network (LAN and VPN both) and from the Outside.  However, I'm experiencing two problems:

1) Periodically, at irregular intervals, ssh connections get dumped with a "Network caused software reset" error (on PuTTY).  I can immediately reconnect to the server by opening another PuTTY window, so it's more like a "hiccup" than anything else.  Annoying, though, and I can't seem to figure out why it's happening. 

2) When files are being transferred via SMB, rsync or ftp, after an arbitrary amount of data transferred, the connection either resets or simply freezes.  The amount of data transferred before the lockup, as I mentioned, seems arbitrary and is different from occurrence to occurrence, but is usually around 2 - 5 MB.  Again, I'm able to reconnect and retry immediately, but the problem generally recurs.

It might be important to note that these connection "hiccups" do not affect the VPN software, nor do they disconnect other active connections (an ftp "hiccup" doesn't cause an SSH session to terminate, for example).  Also, the VPN can handle any amount of data transfer, as can the web server.  The problem occurs from all three networks (LAN, VPN and Outside) and seems to happen regardless of whether the connection is wired or wireless.

I've done some googling and looked through the log files, but there isn't anything that jumps out at me as being the likely culprit.  Is there anyone here who can offer me some assistance?

Thanks
EB

---

### Post by craigp84 on 2007-05-23
Hi Endless Bard,

Looks like a really annoying wee problem. But they're the most fun to solve :-)

Ok, we're going to need more visibility of whats going on - looks like you've checked through the basics so next step is to fire up tcpdump (or wireshark) on the server. We want to capture everything around a "hiccup" - preferably capture  a few of them, and we can see exactly what's going on.

Other things you could do as well would be to enable verbose logging on the sshd. You can do this by entering the following commands:

```
sudo killall sshd
sudo /usr/sbin/sshd -vvv
```

I suspect that it may only show a timeout or similar rather than anything useful.

Also check your NICs for errors: ```
ifconfig -a
```

Lastly, double check your "dmesg" and /var/log/messages for anything at all around the times of the failures.

I previously experienced similar issues first hand, and traced it to a bug in the Broadcom b44 driver. Rather than wrestle with broadcom sh1t, i swapped it out for another type of card and live happily ever after.

Other things to consider may be any switches or routers on your lan, i've seen badly behaved switches causing glitches like this.

Hope this helps,

-c

p.s. if you're having trouble figuring out what's going wrong from tcpdump during a glitch, post here for more assistance

---

### Post by Endless Bard on 2007-05-24
Hiya.

You said the magic words -- "interface problem."  I should have figured that out since it was cross-application, but for some reason, it didn't occur to me...

Anyway, I switched default interface and now the thing works fine -- no interruptions, no hiccups.  Either the card I was using initially was faulty, or the rest of the hardware just isn't able to handle 100mbps (the new card is 10).

Thanks very much for your assistance!

Cheers,
EB

---

### Post by craigp84 on 2007-05-25
> the rest of the hardware just isn't able to handle 100mbps

A 500Mhz box should be quite capable of fully saturating a 100Mbps pipe (all other things being equal).

-c

---

