---
title: "netbios resolution"
date: 2006-06-26
forum: Server Platforms
---

### Post by ashrack on 2006-06-26
My home network consists of 5 computers. This one has UBUNTU DAPPER and is used as a server. The other 4 are a mixed Windows/Ubuntu. 
Clients IPs are assigned thru DHCP. 
But the problem is that the machines only see each other thru IP numbers and not by their name.

What must I do?

---

### Post by spifbv on 2006-06-26
[QUOTE=ashrack]My home network consists of 5 computers. This one has UBUNTU DAPPER and is used as a server. The other 4 are a mixed Windows/Ubuntu. 
Clients IPs are assigned thru DHCP. 
But the problem is that the machines only see each other thru IP numbers and not by their name.

What must I do?[/QUOTE]

Well, you could set "wins support = yes" in /etc/samba/smb.conf on the server and restart samba.  If you don't have samba installed already, do that first, of course.  Then you'll need to configure the server as your WINS server on the Windows clients, and install winbind on the Ubuntu clients per the following procedure:

[http://www.ubuntuforums.org/archive/index.php/t-88206.html](http://www.ubuntuforums.org/archive/index.php/t-88206.html)

Or set up a DNS server (Google for "Ubuntu DNS server" for tutorials).

---

### Post by LordHunter317 on 2006-06-26
***No, do not setup WINS.  Do not use that abomination unless you must.***

Any Windows post NT4 will do name resolution through DNS just fine.  I recommend that route.  Anyway, are you having problems with browsing (i.e., 'My NEtwork Places') or with NetBIOS name resolution (i.e., ''\\machine\share" in Run or an explorer window)?  The two are differnet problems with different solutions.

---

### Post by ashrack on 2006-06-27
[QUOTE=LordHunter317]***No, do not setup WINS.  Do not use that abomination unless you must.***[/QUOTE]

Curious why is a WINS server bad, because its microsoft or something else??

> Any Windows post NT4 will do name resolution through DNS just fine.  I recommend that route.  Anyway, are you having problems with browsing (i.e., 'My NEtwork Places') or with NetBIOS name resolution (i.e., ''\\machine\share" in Run or an explorer window)?  The two are differnet problems with different solutions.

I will go with DNS server route. Im having problems with netbios. Since machine can only be 'pinged' thru their IP numbers. Which sucks since its a DHCP network.

For DNS server I found this guide:
[https://help.ubuntu.com/ubuntu/serverguide/C/dns.html](https://help.ubuntu.com/ubuntu/serverguide/C/dns.html)
is it the correct one??
And also if I set up DNS server can I still use the ISP's DNS server for the internet instead of my own??

---

### Post by LordHunter317 on 2006-06-27
[QUOTE=ashrack]Curious why is a WINS server bad, because its microsoft or something else??[/quote]Because the protocol is a hack on-top-of a hack.

---

### Post by ashrack on 2006-06-27
I've installed BIND9 and set up:
'/etc/bind/named.conf.options'
to this:
> options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
	 	193.189.160.13;
		193.189.160.23;
	};

	auth-nxdomain no;    # conform to RFC1035

};


and on the client machines I can now ping 'www.yahoo.com' with their DNS pointed to this server.

---

### Post by ashrack on 2006-06-28
Ive setup DNS SERVER and samba on the server so clients can connect to server's share. 
But I still can only ping clients by their IP and not by their name. What else must I set  up??

---

### Post by Iowan on 2006-06-28
There are more informative posts around -  but in a nutshell, the DHCP client must send the server it's name.

---

### Post by ashrack on 2006-06-28
Ive been searching the board for any info but cant find anything.
The clients are able to ping 'server' by its hostname
But the clients are unable to ping amongs themself by hostname. Which is what I need

---

### Post by Iowan on 2006-06-28
[http://www.ubuntuforums.org/showthread.php?t=200855&highlight=send+hostname]("http://www.ubuntuforums.org/showthread.php?t=200855&highlight=send+hostname") 
[http://www.ubuntuforums.org/showthread.php?t=184710&highlight=send+hostname+DHCP+client]("http://www.ubuntuforums.org/showthread.php?t=184710&highlight=send+hostname+DHCP+client")
[http://www.ubuntuforums.org/showthread.php?p=712958#post712958]("http://www.ubuntuforums.org/showthread.php?p=712958#post712958")


Here's a few!

---

### Post by ashrack on 2006-06-28
Tried this:
[http://www.ubuntuforums.org/showpost.php?p=686287&postcount=12](http://www.ubuntuforums.org/showpost.php?p=686287&postcount=12)
but doesnt help.
Any other ideas or is my only alternative a WINS server?

---

### Post by ashrack on 2006-06-29
come on, anyone??

---

### Post by robertmcox on 2006-06-30
How about one more post on "how to resolve names using NetBIOS"

Install winbind:

```
sudo apt-get install winbind
```

Now edit your /etc/nsswitch.conf to add "wins" to your "hosts" line:

```
hosts:          files dns mdns wins
```

You're done!

Note that this does *not* configure a WINS server nor a WINS client, this configures NetBIOS resolution, answering the original post (and ashrack's "c'mon").

As for WINS, ashrack is correct that it's an abomination!  Add chitter-chatter and slow convergence to the list of why.  (NetBIOS chitter-chatters, too)

Now if you want other computers (Windows or Linux) to resolve *your* name using NetBIOS, you must install Samba.

```
sudo apt-get install samba
```

You should configure Samba to have the appropriate hostname.  Configure the workgroup, too, to make network browsing easy.  This controls what shows up under "Network Neighborhood" on Windows computers.  Edit /etc/samba/smb.conf:

```
   netbios name = myname
   server string = mydescription
   workgroup = MYWORKGROUP
```

Note that you do not need to share any folders or printers using Samba.  

Note that the previously mentioned Samba and BIND configurations may solve your problem, but do not provide NetBIOS resolution, which is the topic of this post.

I use this setup both on my home network (3 Ubuntu, 2 XP) and my office network (1 Ubuntu, 10 XP, 1 Win2k, 3 Win2k3 :-O) and it works great!

In summary, 3 solutions:

1 - WINS Server and Samba WINS client - This does not solve the original poster's requirement of pinging a computer by hostname.  This solution also uses WINS, a deprecated (by Microsoft, no doubt) protocol.

2 - Install a BIND server and use DNS resolution - a great solution for a larger network.  Does not support NT4 (without further configuration), Windows 9x clients (period), or Linux (without further configuration).  This solution will work out-of-the-box for Windows 2000 and newer.

3 - Use NetBIOS - a great solution for a small network.  Works cross-platform, but does *not* work across routers, so make sure all the computers that will resolve names using this method are on the same IP subnet.  This protocol also wastes bandwidth in a linear manner as more computers join the wire, so only use it for small networks (less than 50 computers) on a single IP subnet.

---

### Post by ashrack on 2006-07-02
thank U! all I had to do was install WINBIND on the server machine and now I have name resolution on all of the clients without changing a single setting.  Probably beceuse I already had WINBIND set on the LINUX clients. thank U again

---

### Post by foolishchild on 2006-07-27
Deleted because robertmcox  already answered it better two posts above ;)

---

### Post by LordMerlin on 2006-07-29
This solution only works for Windows PC's on the LAN. 

I have a DHCP network, with DNS, but DNS is mainly for internet. How would I be able to see the Linux machines on the LAN, without having to register all their names in the DNS pool? winbind doesn't seem to work with the Linux PC's

---

