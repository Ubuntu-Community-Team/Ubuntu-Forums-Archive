---
title: "Unknown ports open"
date: 2009-08-06
forum: Security
---

### Post by crocos on 2009-08-06
Hello everyone.

This is my first post to Ubuntu forums. I finally made the switch from windows ( Although I have Vista as a VM for now? 

Today at work I got a visit from someone from the IT department who said suspicious traffic had been coming from my laptop. He said it looked like it may be part of a botnet. So I wanted to see if any ports were open that a malicious program might be using. so I did a port scan using the network tools GUI. I would get 631, which I belive is OK and is to do with printing. I would also get between 1-3 other ports that changed each time I did a scan, eg. 44817, 44817, 55651, . When I tried to find out what was using these ports using 'sudo netstat -anp|grep(port number)' I get the follwing outut with all these varying ports:

:~$ sudo netstat -anp|grep 33969
tcp6       0      0 ::1:33969               ::1:33969               TIME_WAIT 

Is this OK?

One more thing. When I looked at active connections in firestarter I noticed a connection to 94.23.197.115 using the service HTTP and the wget program (something being downloaded?) The site is BISSLabs Nginx. I've never heard of this site, and have never knowingly browsed to there.

Is this any cause for concern?

Hope someone can shed some light.

I'm using 9.04 thats fully patched.

Cheers,

croco


EDIT:

So after the IT department sent me a description of the problem, it seems like my computer was not compromised. I had used a firefox addon called Down Them All, which I used to get all the PDFs off a webpage. The Website owners contacted my institution to tell them that suspected spider activity was coming from my computer.  Problem solved.

---

### Post by prshah on 2009-08-06
> **crocos said:**
> Although I have Vista as a VM for now? 

$ sudo netstat -anp|grep 33969
tcp6       0      0 ::1:33969               ::1:33969               TIME_WAIT 


I typically get similar entries when I have a torrent client running (rtorrent in my case). Maybe you have a torrent client and/or a P2P program running?

---

### Post by XCan on 2009-08-06
If port 631 is open and you believe it is related to printing, why is it open? Are you running a printer server? Ports in Ubuntu would only be open if you are running a server.

---

### Post by cdenley on 2009-08-06
A default ubuntu configuration includes cups, a print server. By default, it binds to 127.0.0.1. It is not "open" to remote computers, only locally. As for the random ports showing up as "open" in gnome's port scan tool, that sounds like a bug.
[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042)
[http://bugzilla.gnome.org/show_bug.cgi?id=547598](http://bugzilla.gnome.org/show_bug.cgi?id=547598)

If you are worried about processes which are listening for external connections, use this command:
```

sudo netstat -tulnp

```
There should only be cups on TCP port 127.0.0.1:631, then avahi and dhclient listening on UDP ports.

---

### Post by sasho_zl on 2009-08-06
This command can help identify the service -** lsof -i -n -P**

---

### Post by crocos on 2009-08-06
> **cdenley said:**
> A default ubuntu configuration includes cups, a print server. By default, it binds to 127.0.0.1. It is not "open" to remote computers, only locally. As for the random ports showing up as "open" in gnome's port scan tool, that sounds like a bug.
[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042)
[http://bugzilla.gnome.org/show_bug.cgi?id=547598](http://bugzilla.gnome.org/show_bug.cgi?id=547598)

If you are worried about processes which are listening for external connections, use this command:
```

sudo netstat -tulnp

```There should only be cups on TCP port 127.0.0.1:631, then avahi and dhclient listening on UDP ports.

The output of sudo netstat -tulnp:

[LEFT]Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:111             0.0.0.0:*                 LISTEN       2396/portmap    
tcp        0      0 127.0.0.1:631           0.0.0.0:*                 LISTEN      3744/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*                 LISTEN       3332/exim4      
tcp        0      0 0.0.0.0:46652           0.0.0.0:*                 LISTEN      2417/rpc.statd  
tcp        0      0 127.0.0.1:30814         0.0.0.0:*               LISTEN      5618/gdl_indexer
tcp6       0      0 ::1:631                   :::*                          LISTEN      3744/cupsd      
udp        0      0 0.0.0.0:897             0.0.0.0:*                                   2417/rpc.statd  
udp        0      0 0.0.0.0:68                 0.0.0.0:*                                  26925/dhclient  
udp        0      0 0.0.0.0:47701           0.0.0.0:*                                 2417/rpc.statd  
udp        0      0 0.0.0.0:49884           0.0.0.0:*                                 3712/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                                  3712/avahi-daemon: 
udp        0      0 0.0.0.0:111             0.0.0.0:*                                   2396/portmap    
udp        0      0 0.0.0.0:631             0.0.0.0:*                                   3744/cupsd      
[/LEFT]


Does this OK?

Thanks for your swift replies everyone.

Crocos

---

### Post by jerome1232 on 2009-08-06
That all looks fine to me, anything listening to 127.0.0.1 can be ignored, that's just your own computer, everything else is pretty standard except I noticed you have cupsd listening to connections to the internet, unless your computer is sharing a printer I would reconfigure cups do disable that. (I believe [http://localhost:631](http://localhost:631) will get you to the config page).

---

