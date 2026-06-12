---
title: "Firestarter  showing attack from samba service"
date: 2010-03-17
forum: Security
---

### Post by dinw3 on 2010-03-17
I got alarm on Firestarter  showing attack from samba service on port 139 . Is that ok for my host computer ? or a serious attack .

---

### Post by cdenley on 2010-03-17
That is very common. Even if you installed samba, I don't believe it allows internet traffic by default. There will be attempts to connect to services on your IP all day. Scripts and bots scan IP's at random. Watching firestarter like that is a waste of time in my opinion. Just make sure you don't allow access to any services, then you don't need to worry about what firestarter filters.

---

### Post by bodhi.zazen on 2010-03-17
> **dinw3 said:**
> I got alarm on Firestarter  showing attack from samba service on port 139 . Is that ok for my host computer ? or a serious attack .

Nobody can answer that question , Firestarter does not give sufficient information.

You would need to tell us a lot more about your network configuration, computer on the LAN, ports forwarded etc etc.

If you want to know, you will need to anlayze the traffic, and now you are taking snort or wireshark or similar.

As pointed out by cdenley, I get thousands of blocked packets on my server and thus tools like snort to analyze the traffic ...

The dropped packet could be almost anything, including normal network traffic.

---

### Post by dinw3 on 2010-03-23
By the way , i have installed tor on my host computer which turn out latter that some service start opening port like FTP and telnet .That made me to remove the tor . any ideas ?

---

### Post by cdenley on 2010-03-23
> **dinw3 said:**
> By the way , i have installed tor on my host computer which turn out latter that some service start opening port like FTP and telnet .That made me to remove the tor . any ideas ?

What do you mean "some service start opening port" and how is it related to this thread? Do you mean somebody is attempting to establish connections on those ports remotely, or something on your system is listening for connections?

---

### Post by dinw3 on 2010-03-23
I noticed that some service are running like FTP and telnet when i installed tor , i kept cheeking Firestarter traffic .

---

### Post by cdenley on 2010-03-23
> **dinw3 said:**
> I noticed that some service are running like FTP and telnet when i installed tor , i kept cheeking Firestarter traffic .

How did you establish that FTP and telnet services were running, and how does that relate to firestarter's filtered traffic?
```

sudo netstat -tlnp

```

---

### Post by dinw3 on 2010-03-23
i removed one week ago , it was a wried traffic .

---

### Post by cdenley on 2010-03-23
> **dinw3 said:**
> i removed one week ago , it was a wried traffic .

Doesn't answer any questions. I can only assume you don't know what you are talking about.

---

### Post by dinw3 on 2010-03-23
I am still newbie .

---

### Post by doas777 on 2010-03-23
tor does not include telnet or ftp. those were not installed as part of tor. 

are you behind a router, or directly connected to the internet?
if you are behind a router, you are probably fine, unless you have configured your firewall to pass smb data (which would be silly). the traffic is likely from your own PCs.
if you are not behind a router, uninstall samba and any other network services that you do not need, including telnet and ftp. telnet is definetly not safe to expose to the web and ftp is problematic unless done carefully.

NetBIOS (samba is an open implementation of smb/netbios) is derived from an older network-only protocol called netbui, and uses many of it's name resolution mechanisms, including local network broadcasts on port 139. also, netbios uses an "election" system to select the master browsers for a network, which also manifests as smb traffic.
[http://technet.microsoft.com/en-us/library/cc958811.aspx](http://technet.microsoft.com/en-us/library/cc958811.aspx)

---

### Post by cdenley on 2010-03-23
> **dinw3 said:**
> I am still newbie .

Well then, I am guessing you didn't have any FTP or telnet services listening for connections. Somebody attempted to establish connections on your system using TCP port 21 and 23 (typically used for FTP and telnet). The connection attempts were filtered by firestarter's rules. Even if it were not, the connection would have been rejected anyway, assuming you didn't install anything to handle those connections.

---

### Post by costre on 2010-04-01
I'm just throwing this in here :)

I am running a Tor bridge, and since I installed Firestarter, it's blocking the Tor-requests. 

I can't really allow certain ports, since the Tor connections are coming on different ports according to the log in Firestarter, but I was hoping I could simply "allow Tor to connect however it wants"?

Is this possible?

---

### Post by cdenley on 2010-04-01
> **costre said:**
> I'm just throwing this in here :)

I am running a Tor bridge, and since I installed Firestarter, it's blocking the Tor-requests. 

I can't really allow certain ports, since the Tor connections are coming on different ports according to the log in Firestarter, but I was hoping I could simply "allow Tor to connect however it wants"?

Is this possible?

I'm pretty sure incoming connections to a tor bridge would only be established on a single port, typically either 443 or 9001. Tor connections on other ports must be outgoing.
```

sudo netstat -tlnp

```

---

### Post by Enigmapond on 2010-04-01
This just an FYI for those who aren't aware. Firestarter is a deprecated programme. There have been no updates on it since early 2005. If you need a GUI for iptables, really the best is gufw...I'm sure a lot of your firewall issues will cease once you get rid of Firestarter.

Cheers!

---

