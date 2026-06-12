---
title: "How to watch and control inbound and outbond connections"
date: 2014-05-05
forum: Security
---

### Post by LastDino on 2014-05-05
Well, due to curtsey of this forum I've come to realize that my network (My Xubuntu desktop directly (cable/LAN) connected through TP-link wifi to host router by cable/LAN) is quite insecure. I've done some research and installed GUFW on my desktop and turned it on to default profile settings.  Now, after doing some further research I've come to realized that you can block inbound and outbound connections by identifying the IP addresses and so on..
  
What I would like to know is how to identify the correct ones? And how? Of course, not interrupting any network functioning and if possible future sharing using samba (work there is in progress as I'm still in process of reading things on subject of file sharing between machines on my network and main host router network). Well, you should get the picture from this.


I'm not sure if I'm making lot of sense but if you get where this newibe is coming from, do help me/point me in right direction ;)

---

### Post by pqwoerituytrueiwoq on 2014-05-05
to monitor traffic you can use [wireshark](apt:wireshark)
this will show a snapshot of your network connections
```
netstat -nputw
```

---

### Post by cariboo on 2014-05-05
removed duplicate post.

---

### Post by LastDino on 2014-05-05
> **pqwoerituytrueiwoq said:**
> to monitor traffic you can use [wireshark]("apt:wireshark")
this will show a snapshot of your network connections
```
netstat -nputw
```

Thanks a bunch, I had to run command as root to see process names though :) 

Now, how do I block certain addresses from making outbound or inbound connections for that matter? Directly into GUFW?

Also, I came across this ''listening ports'' option in GUFW and I can see list of ''ports'' as well as IP's, what is the difference and how do I know which ports are secure?

---

### Post by thnewguy on 2014-05-06
An IP address is used to identify a computer (typically). A port is a way to identify a particular service on a computer. It might help to think of it this way: Let's say you go to an apartment building. The IP address a computer uses is sort of like the civic address to an apartment building. The port number is like an apartment number, it tells you which door to go to within that apartment building.

So if someone wants to connect to a service on your computer they need your IP address (which identifies your computer) and they need to know which service (port) to talk to.

By default, Ubuntu does not leave any ports open and so you generally do not need to run a firewall. There are no "doors" for people to enter. However, if you start running services (like Samba) then you should do two things.
1. Open the Samba port to everyone on your local network. This means allowing certain known IP address, computers you know to be friendly.
2. Everything else should be blocked from making incoming connections.

Most of the time people do not block outgoing connections on their home computers. blocking outgoing connections is usually just used in office environments where administrators want to prevent users from using certain services or visiting particular websites.

---

### Post by LastDino on 2014-05-06
> **thnewguy said:**
> An IP address is used to identify a computer (typically). A port is a way to identify a particular service on a computer. It might help to think of it this way: Let's say you go to an apartment building. The IP address a computer uses is sort of like the civic address to an apartment building. The port number is like an apartment number, it tells you which door to go to within that apartment building.

So if someone wants to connect to a service on your computer they need your IP address (which identifies your computer) and they need to know which service (port) to talk to.

By default, Ubuntu does not leave any ports open and so you generally do not need to run a firewall. There are no "doors" for people to enter. However, if you start running services (like Samba) then you should do two things.
1. Open the Samba port to everyone on your local network. This means allowing certain known IP address, computers you know to be friendly.
2. Everything else should be blocked from making incoming connections.

Most of the time people do not block outgoing connections on their home computers. blocking outgoing connections is usually just used in office environments where administrators want to prevent users from using certain services or visiting particular websites.

That was quite informative and thank you for simplified explanation. 

So, basically, I should make a list of all the PC's on my ''WORKGROUP'' and allow their IP's if sharing is enabled, if not then block them, right? 


You mentioned Samba, which I'm trying to use to set-up network sharing with windows PC (I posted different thread for this), so I need to change my firewall settings to allow that PC's IP. I didn't knew that, thanks!

---

