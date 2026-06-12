---
title: "Ports 80 and 443 open by default, potential security vulnerability?"
date: 2009-11-05
forum: Security
---

### Post by Jephir on 2009-11-05
I have a fresh install of Ubuntu 9.10 64-bit with no additional software installed, and I am behind a router. I did a scan on [ShieldsUp!]("https://www.grc.com/x/ne.dll?bh0bkyd2") and it shows that ports 80 and 443 are open on my computer.

Is having these ports open a potential security vulnerability? If so, how do I close these ports?

---

### Post by bodhi.zazen on 2009-11-05
ShieldsUp! is scanning your router.

See: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Personally I like this command to show open ports :

```
lsof -i -n -P
```

You can also use port scanners on your LAN.

---

### Post by lovinglinux on 2009-11-05
If you don't have a web server running, than is not an issue. Incoming connection requests will be rejected anyway, since there is no application listening to those ports. But if you do have a web server running AND don't want to allow external access to it, then yes. Nevertheless, I'm not sure why the test is telling you the port is open. If you don't have a web server, then it shouldn't be considered open, even if your firewall and router are allowing the traffic to reach your machine.

---

### Post by movieman on 2009-11-06
Are you sure that it's not seeing a web-server running on your router? I know some have web servers to allow remote access over the Internet.

---

### Post by Lars Noodén on 2009-11-06
> **bodhi.zazen said:**
> ShieldsUp! is scanning your router.

See: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Personally I like this command to show open ports :

```
lsof -i -n -P
```


The iptables suggestion is useful.  
lsof, however, seems to show only open or recently open TCP connections.  

nmap, or with the gui zenmap, from another machine will show open ports.  

However, the original question was how to close those ports 80 and 443.  Since it looks like it is your modem, router or switch that is getting scanned, that is where the ports should be closed.  While those get set, also make sure that the default password is not being used.

---

### Post by QLee on 2009-11-06
> **Jephir said:**
> I have a fresh install of Ubuntu 9.10 64-bit with no additional software installed, and I am behind a router. I did a scan on [ShieldsUp!]("https://www.grc.com/x/ne.dll?bh0bkyd2") and it shows that ports 80 and 443 are open on my computer.

Is having these ports open a potential security vulnerability? If so, how do I close these ports?

If you look up those port numbers you will find that port 80 is http and port 443 is https.

I note that When I run a scan at GRC my initial connection is with http and when doing their scan I have a https connection.

As was mentioned, a port being "open" is not as important as what is listening for connection on the port. If the router (is this a gateway, broadband modem/router combination) has an option in its firewall section to close ports (stealth I think is the way GRC calls it), you could do that but doing so does not contribute much to security from those you should be most afraid of. Once you make a request on a port (for example, browse to a site with http), it will be obvious that there is something at your IP, even if the port shows as closed.

As mentioned, if your router has a firewall and it is turned on, close the ports you want closed with the router interface, how to do that will be in the router documentation, it's not exactly the same for all routers.

---

### Post by cariboo on 2009-11-07
I would suggest the op turn off remote administration in the router management interface. Unless you plan changing your router setup from outside your internal network, you don't need it.

---

### Post by koenn on 2009-11-07
> **QLee said:**
> If you look up those port numbers you will find that port 80 is http and port 443 is https.

I note that When I run a scan at GRC my initial connection is with http and when doing their scan I have a https connection.

This is irrelevant. when *you* connect to GRC with http or https, you connect to *their* ports 80 and 443 - your computer will be using random high ports, and , secondly, your browser using those random ports would not respond to connection attempts.

---

### Post by QLee on 2009-11-08
[QUOTE=koenn]This is irrelevant.[/QUOTE]

Perhaps.

On the other hand, reading that and then reading the paragraph which follows it, one may have an insight. If they miss it then the post that just follows it might spur thinking. This is not the absolute beginner sub forum where posters often require the exact code to type in order to function. It is my opinion that people benefit most from learning to think through a problem, others have different opinions and styles.

---

### Post by koenn on 2009-11-08
> **QLee said:**
> Perhaps.

 ...
 It is my opinion that people benefit most from learning to think through a problem, ... 

```

:~$ netstat -n
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.7.7:37475     74.125.77.147:80        ESTABLISHED
tcp        0      0 192.168.7.7:52032     74.125.77.101:80        ESTABLISHED
```

If you think that connections initiated from ports 37475 and 52032  on my computer would have  any relation with whether there's a service accepting incoming connections on port 80 and/or 443 on my computer, so be it.

---

