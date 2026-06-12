---
title: "Configuring which interface for ntpd"
date: 2009-12-25
forum: Server Platforms
---

### Post by memilanuk on 2009-12-25
Hello,

I installed ntpd on my U9.10 server.  I set the upstream servers to what I wanted in /etc/ntp.conf, but I can't find anyplace to limit what interface it listens on.  Judging by the below, it seems to be 'attached' to both eth0 (192.168.11.14), eth1 (10.0.0.1) and l0 (127.0.0.1), but I'm not sure if it's 'listening' or not since it doesn't have a 'LISTEN' under 'State'... but then again dnsmasq isn't listed as 'LISTEN' for bootp/dhcp (tcp67/68), but I know thats working...

```

root@rahvin:~# netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1329/dnsmasq    
tcp        0      0 10.0.0.1:22             0.0.0.0:*               LISTEN      1033/sshd       
tcp6       0      0 :::53                   :::*                    LISTEN      1329/dnsmasq    
udp        0      0 10.0.0.1:123            0.0.0.0:*                           1454/ntpd       
udp        0      0 192.168.11.14:123       0.0.0.0:*                           1454/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1454/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1454/ntpd       
udp        0      0 0.0.0.0:53              0.0.0.0:*                           1329/dnsmasq    
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1329/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           739/dhclient3   
udp6       0      0 fe80::a00:27ff:feff:123 :::*                                1454/ntpd       
udp6       0      0 fe80::a00:27ff:fe2e:123 :::*                                1454/ntpd       
udp6       0      0 ::1:123                 :::*                                1454/ntpd       
udp6       0      0 :::123                  :::*                                1454/ntpd       
udp6       0      0 :::53                   :::*                                1329/dnsmasq    
root@rahvin:~# 

```

If you have any ideas how to limit what interface ntpd listens or offers services on, I'd appreciate it.  If I'm misreading the above please point me in the right direction ;)

TIA,

Monte

---

### Post by HighCommander540 on 2009-12-25
> **memilanuk said:**
> Hello,

I installed ntpd on my U9.10 server.  I set the upstream servers to what I wanted in /etc/ntp.conf, but I can't find anyplace to limit what interface it listens on.  Judging by the below, it seems to be 'attached' to both eth0 (192.168.11.14), eth1 (10.0.0.1) and l0 (127.0.0.1), but I'm not sure if it's 'listening' or not since it doesn't have a 'LISTEN' under 'State'... but then again dnsmasq isn't listed as 'LISTEN' for bootp/dhcp (tcp67/68), but I know thats working...

```

root@rahvin:~# netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1329/dnsmasq    
tcp        0      0 10.0.0.1:22             0.0.0.0:*               LISTEN      1033/sshd       
tcp6       0      0 :::53                   :::*                    LISTEN      1329/dnsmasq    
udp        0      0 10.0.0.1:123            0.0.0.0:*                           1454/ntpd       
udp        0      0 192.168.11.14:123       0.0.0.0:*                           1454/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1454/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1454/ntpd       
udp        0      0 0.0.0.0:53              0.0.0.0:*                           1329/dnsmasq    
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1329/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           739/dhclient3   
udp6       0      0 fe80::a00:27ff:feff:123 :::*                                1454/ntpd       
udp6       0      0 fe80::a00:27ff:fe2e:123 :::*                                1454/ntpd       
udp6       0      0 ::1:123                 :::*                                1454/ntpd       
udp6       0      0 :::123                  :::*                                1454/ntpd       
udp6       0      0 :::53                   :::*                                1329/dnsmasq    
root@rahvin:~# 

```

If you have any ideas how to limit what interface ntpd listens or offers services on, I'd appreciate it.  If I'm misreading the above please point me in the right direction ;)

TIA,

Monte

I am pretty sure that it is not actually listening or doing anything on your connections. NTPD doesn't listen for information usually. When the timer goes off for it to check if your time is correct it turns on a connection and asks for the information. There is never (well shouldn't be unless someone is trying to hack your NTPD) an inbound connection that NTPD doesn't start itself.  As to on which interface. You don't need to specify one. NTPD just searches each on until it finds a valid connection to the timeserver you are asking it to you. Then it does it's thing.

---

### Post by memilanuk on 2009-12-25
> **HighCommander540 said:**
> I am pretty sure that it is not actually listening or doing anything on your connections. NTPD doesn't listen for information usually. When the timer goes off for it to check if your time is correct it turns on a connection and asks for the information. There is never (well shouldn't be unless someone is trying to hack your NTPD) an inbound connection that NTPD doesn't start itself. 

How would it act as a server for my network if it doesn't listen for connections?  That was the primary reason for my installing it.


> 
 As to on which interface. You don't need to specify one. NTPD just searches each on until it finds a valid connection to the timeserver you are asking it to you. Then it does it's thing.

That... doesn't make a lot of sense.  Why would it search on the *loopback* interface for an upstream timeserver?

---

### Post by koenn on 2009-12-25
> **memilanuk said:**
> How would it act as a server for my network if it doesn't listen for connections?  That was the primary reason for my installing it.


udp applications don't "listen", do only 'send' or 'receive'. 


don't know if you can actually bind the ntp daemon to a network interface. 
What you probably want is to have some control over which servers it receives time from, and which network(s) it gives time to. You can configure that in /etc/ntpd.conf

```

man ntpd
man 5 ntpd.conf

```

---

### Post by memilanuk on 2009-12-25
koenn,

I had already configured which upstream public time servers I wanted this machine to use: 0.us.pool.ntp.org, 1.us.pool.ntp.org, etc. so I think I had that part taken care of.

Not trying to argue with you per se, but the man page talks about it 'listening'.  Maybe a question of semantics?

>        
*listen on address*
Specify  a  local  IP  address  or a hostname the ntpd(8)daemon should listen on. 


I'll have to go back and look at the config file on my machine; I don't recall how the 'Listen' clauses are set up or if there are any listed by default.

Thanks,

Monte

---

### Post by HighCommander540 on 2009-12-26
> **memilanuk said:**
> How would it act as a server for my network if it doesn't listen for connections?  That was the primary reason for my installing it.

Because the point is that NTPD, doesn't serve anything to anyone. It is just a service that's used to set the computer date/time periodically. It doesn't wait for information to be sent to it (that is what listening mean). What it does it every once in awhile (you set the time), it will check the server's for the correct time.

Do you realize how stupid listening would be for a program like this? The time server's would have to have have to have the IP addresses saved of anyone in the world that would want to use them and send out a mass data burst every 5 mins. That would just be the stupidest thing ever.


> **memilanuk said:**
> 

Because...Its programmed to just find the server. It can't tell the difference between loopback and otherwise. It just sees a connection. Computer's are stupid unless you tell then not to be.

[QUOTE=memilanuk;8559630]koenn,

I had already configured which upstream public time servers I wanted this machine to use: 0.us.pool.ntp.org, 1.us.pool.ntp.org, etc. so I think I had that part taken care of.

Not trying to argue with you per se, but the man page talks about it 'listening'.  Maybe a question of semantics?

I'll have to go back and look at the config file on my machine; I don't recall how the 'Listen' clauses are set up or if there are any listed by default.

Thanks,

Monte

All the configuration file means by listen. Is what port to use when trying to get the date and time. Not actually listen.

Honestly its a question of...Why fix what's not broken? If it works then why are you complaining?

---

### Post by koenn on 2009-12-26
> **memilanuk said:**
> 
Not trying to argue with you per se, but the man page talks about it 'listening'.  Maybe a question of semantics?

Yes, it's semantics, as HighCommander540 points out.
The "LISTEN" state shown in netstat is the state of a given tcp socket. udp sockets don't have state, they only send and receive. 

The "listen" in a daemon config file usually means what interface/adres/port number the daemon should use to communicate with the network. In stead of "listen", you often see "bind to" for these cases.

---

### Post by memilanuk on 2009-12-26
> **HighCommander540 said:**
> Because the point is that NTPD, doesn't serve anything to anyone. 

Really.  So it's not possible to set up your own local timeserver and have local clients get their time from that machine, rather than having *all* of them trying to contact an upstream public server.  Right...

---

### Post by memilanuk on 2009-12-26
> **koenn said:**
> 
The "listen" in a daemon config file usually means what interface/adres/port number the daemon should use to communicate with the network. In stead of "listen", you often see "bind to" for these cases.

Gotcha.  I do find it somewhat interesting that the Ubuntu default installed package 'ntp' doesn't have *any* option for listen, etc. but the alternate 'openntpd' does... and I sure would be curious to see if it changes what I see when running netstat on the system (as far as whats listening/bound where).  Unfortunately it returns a number of errors during installation and won't start cleanly either.  Given its about bedtime, I'll have to leave that little mystery for another time and place.

Thanks,

Monte

---

### Post by koenn on 2009-12-26
> **memilanuk said:**
> Really.  So it's not possible to set up your own local timeserver and have local clients get their time from that machine, rather than having *all* of them trying to contact an upstream public server.  Right...
this is usually done client-side, eg Windows domain members always assume their domain controller is also their time server, unless you tell them otherwise. You can also pass ntp server addresses to clients as a dhcp option.

You can also tell your ntpd that it should *broadcast* to a given network - but that's something different from telling it which network interface it should use.

---

### Post by HighCommander540 on 2009-12-26
> **memilanuk said:**
> Really.  So it's not possible to set up your own local timeserver and have local clients get their time from that machine, rather than having *all* of them trying to contact an upstream public server.  Right...

Wow, you are really going to argue with the dude that is trying to help you on software you don't know about...By default NTPD does nothing but set your own time. And you have to do a whole bunch of other stuff to set it up to give the information to the rest of the network.

> **memilanuk said:**
> Gotcha.  I do find it somewhat interesting that the Ubuntu default installed package 'ntp' doesn't have *any* option for listen, etc. but the alternate 'openntpd' does... and I sure would be curious to see if it changes what I see when running netstat on the system (as far as whats listening/bound where).  Unfortunately it returns a number of errors during installation and won't start cleanly either.  Given its about bedtime, I'll have to leave that little mystery for another time and place.

Thanks,

Monte

The reason for this is that NTPD is not made to do anything but set YOUR time. NTP was a program made for distributed time keeping over all of their time servers. So that USERS can get the time whenever they need it and for it to be correct. It wasn't a program made to distribute time for other things. They added remedial support, because people asked for it. THeir point is to have all over their own trusted time servers. Why would they make it so that their own time servers were useless?

> **koenn said:**
> this is usually done client-side, eg Windows domain members always assume their domain controller is also their time server, unless you tell them otherwise. You can also pass ntp server addresses to clients as a dhcp option.

You can also tell your ntpd that it should *broadcast* to a given network - but that's something different from telling it which network interface it should use.

Thanks, I have been trying to say this for a long time....

---

### Post by ratcheer on 2009-12-26
You certainly can use your Linux host with ntpd as the time server for the other nodes on your LAN. In fact, if you have a static IP, you can even become an internet time server as part of the public NTP pools. I am serving the time from my ntpd to the rest of my LAN nodes.

Tim

---

### Post by memilanuk on 2009-12-26
> 
By default NTPD does nothing but set your own time.


In that, you are absolutely correct.  No disagreement here about what it does 'by default'.  

> 
And you have to do a whole bunch of other stuff to set it up to give the information to the rest of the network.


I'm trying to look beyond the simple default behavior towards a specific infrastructure arrangement I wish to set up.  Before I get to that point, I wanted to tidy up a few items.  To me, it seems... messy that ntpd 'listens' or 'binds' to everything in sight, and for such a mature protocol I find that rather improbable, though not impossible.  In the past when I set things up I just was happy if they worked at all... these days I'm a bit more curious - and wary - about what ports are opened up, whats listening or binding to where, etc.

> 
Wow, you are really going to argue with the dude that is trying to help you on software you don't know about...


I do appreciate the willingness to help and the spirit in which the advice is given... but when your 'help' apparently contradicts things that I've seen done in the past (such as setting up local ntpd servers for a LAN), what do you expect me to do?  Blindly accept whatever you tell me, or persist until things clear up? 

Let me ask you this... you seem to be adamant that its more normal to have all the clients inside a LAN running ntpd for their own use only, and syncing directly with an upstream pool server(s) outside the network?  You've never worked with setting up a local ntpd server, either inside the LAN or on the firewall machine itself, and have only that machine connect to the upstream servers?  That is in essence where I want to go with this... its really not that uncommon from my understanding.  As koenn mentioned, from that point passing the info for the local ntpd server via dhcp to the LAN clients isn't a big deal... and it should minimize un-necessary traffic through the firewall to the outside network.

---

### Post by HighCommander540 on 2009-12-26
> **memilanuk said:**
> In that, you are absolutely correct.  No disagreement here about what it does 'by default'.

I'm trying to look beyond the simple default behavior towards a specific infrastructure arrangement I wish to set up.  Before I get to that point, I wanted to tidy up a few items.  To me, it seems... messy that ntpd 'listens' or 'binds' to everything in sight, and for such a mature protocol I find that rather improbable, though not impossible.  In the past when I set things up I just was happy if they worked at all... these days I'm a bit more curious - and wary - about what ports are opened up, whats listening or binding to where, etc.

I do appreciate the willingness to help and the spirit in which the advice is given... but when your 'help' apparently contradicts things that I've seen done in the past (such as setting up local ntpd servers for a LAN), what do you expect me to do?  Blindly accept whatever you tell me, or persist until things clear up? 

Let me ask you this... you seem to be adamant that its more normal to have all the clients inside a LAN running ntpd for their own use only, and syncing directly with an upstream pool server(s) outside the network?  You've never worked with setting up a local ntpd server, either inside the LAN or on the firewall machine itself, and have only that machine connect to the upstream servers?  That is in essence where I want to go with this... its really not that uncommon from my understanding.  As koenn mentioned, from that point passing the info for the local ntpd server via dhcp to the LAN clients isn't a big deal... and it should minimize un-necessary traffic through the firewall to the outside network.

I was never saying that you can't do it, but you were asking how to set to an interface for listening as a time updater. You mentioned that you had added some time servers. SO that means you wanted to use it to get the time. I was just saying that from what you told us in the thread first. You said nothing about setting up your own time server until just now. Its hard to help when you ask for help on one thing, when you want to do something else.

Also, I would like to mention that being your own time server is actually a very stupid idea. Unless you have one of the vacuum sealed time keepers, you would have to keep updating your time server's time with time from the pool. So what is the point of doing all this. There really isn't one. If all computer's could actually keep time there would be no reason to have a NTPD. You would only need to use NTP once at the beginning. 

No matter what one computer is going to have to connect outside your firewall. Because it has to get the time at some point. What's the difference if all the computer's get their own time? It will be more accurate if they do this, because even if your time server updated its time within the last 5 minutes, it will be off time by some.

On the note of the port and the interface binding. Its just something you have to deal with. It only uses one port if you have set it too, and it will use all interfaces because it just needs to find the upstream servers. If there is only one way out then it wont matter. It checking the other interfaces will just do nothing.

---

### Post by memilanuk on 2009-12-26
> 
You said nothing about setting up your own time server until just now. Its hard to help when you ask for help on one thing, when you want to do something else.


True.  To me, it was 'obvious'... why else would I care about what interface ntpd was going to 'listen on' or 'bind to' on a server with multiple NICs, unless I intend to use it as a time server?  Hindsight being 20/20, I realize you probably couldn't hear the rocks rolling around in my head from where you are (thats a joke ;) )

As to whether keeping a local ntpd server is a good or bad idea... well, lets just say opinions vary and leave it at that.

---

### Post by greenthumbtacks on 2012-12-13
I know this is an old post but for anyone wandering here they should be aware that many (if not all) of HighCommander540's statements about NTPD are completely false.  By default, out of the box, NTPD will SERVE time on the network by LISTENING for packets on port 123.  The entire point of NTPD is to both calculate reliable time from network sources and also serve that time to the rest of the network.  NTPD is ALWAYS listening for packets.  If you use ntpq to check the status of your NTPD process, ntpq sends a packet to NTPD, which is listening for packets, and NTPD sends a response back to ntpq.  Of course you can prevent serving time by using the "restrict" configuration directive.  Regardless, NTPD will be bound, 24/7 to port 123, which means listening for packets.  Just because it is using udp communication does not make it listen any less.  There simply will be no transport layer connection associated with incoming packets as opposed to tcp.  Therefore there is no LISTEN connection state in netstat for example, because there is no connection state.  It is simply always listening.

> **HighCommander540 said:**
> Because the point is that NTPD, doesn't serve anything to anyone. It is just a service that's used to set the computer date/time periodically. It doesn't wait for information to be sent to it (that is what listening mean). What it does it every once in awhile (you set the time), it will check the server's for the correct time.

Do you realize how stupid listening would be for a program like this? The time server's would have to have have to have the IP addresses saved of anyone in the world that would want to use them and send out a mass data burst every 5 mins. That would just be the stupidest thing ever.




Because...Its programmed to just find the server. It can't tell the difference between loopback and otherwise. It just sees a connection. Computer's are stupid unless you tell then not to be.



All the configuration file means by listen. Is what port to use when trying to get the date and time. Not actually listen.

Honestly its a question of...Why fix what's not broken? If it works then why are you complaining?

---

### Post by greenthumbtacks on 2012-12-13
The following is an actual answer / solution to the OP's question.

You can limit which interfaces NTPD will listen on by passing the -I <interface> argument to the daemon using /etc/default/ntp (see: man ntpd).  In your case you would use "-I lo -I eth0".  The -I lo isn't technically needed as NTPD will always listen on the loopback interface no matter what (which you want anyway).  You will also still see the process bound to all interfaces in netstat.  However, if you check syslog output you will see that the daemon has "disabled" using the other interfaces (eth1 for example), which means packets on those interfaces will be discarded.  This is not ideal, but the best you can get with NTPD.

You can also use the "restrict" directive in ntp.conf (see: man ntp.conf) to restrict various levels of access from specific IPs.  A line such as "restrict 127.0.0.1" means allow full access from localhost, so keep that in mind.  The default configuration should allow serving time to any IP but will not allow remote status query, peer association, or remote configuration changes.

Regarding not seeing "LISTENING" in netstat, udp connections do not have connection states like tcp.  Any udp connection listed will accept packets on that port, so it can be considered as listening.

> **memilanuk said:**
> Hello,

I installed ntpd on my U9.10 server.  I set the upstream servers to what I wanted in /etc/ntp.conf, but I can't find anyplace to limit what interface it listens on.  Judging by the below, it seems to be 'attached' to both eth0 (192.168.11.14), eth1 (10.0.0.1) and l0 (127.0.0.1), but I'm not sure if it's 'listening' or not since it doesn't have a 'LISTEN' under 'State'... but then again dnsmasq isn't listed as 'LISTEN' for bootp/dhcp (tcp67/68), but I know thats working...

```

root@rahvin:~# netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1329/dnsmasq    
tcp        0      0 10.0.0.1:22             0.0.0.0:*               LISTEN      1033/sshd       
tcp6       0      0 :::53                   :::*                    LISTEN      1329/dnsmasq    
udp        0      0 10.0.0.1:123            0.0.0.0:*                           1454/ntpd       
udp        0      0 192.168.11.14:123       0.0.0.0:*                           1454/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1454/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1454/ntpd       
udp        0      0 0.0.0.0:53              0.0.0.0:*                           1329/dnsmasq    
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1329/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           739/dhclient3   
udp6       0      0 fe80::a00:27ff:feff:123 :::*                                1454/ntpd       
udp6       0      0 fe80::a00:27ff:fe2e:123 :::*                                1454/ntpd       
udp6       0      0 ::1:123                 :::*                                1454/ntpd       
udp6       0      0 :::123                  :::*                                1454/ntpd       
udp6       0      0 :::53                   :::*                                1329/dnsmasq    
root@rahvin:~# 

```

If you have any ideas how to limit what interface ntpd listens or offers services on, I'd appreciate it.  If I'm misreading the above please point me in the right direction ;)

TIA,

Monte

---

