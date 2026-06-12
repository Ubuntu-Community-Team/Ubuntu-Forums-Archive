---
title: "please help with cs 1.6 server"
date: 2009-06-13
forum: Server Platforms
---

### Post by Mykle87 on 2009-06-13
Basically my server launches but no one can cannot to it over the internet. I can connect via the lan. I use this string to start it:
./hlds_run -game cstrike -autoupdate +internal_ip 
The server starts up and it says VAC secured. I have forwarded the ports on my router. What am I missing?

---

### Post by cariboo on 2009-06-14
To make sure you have the correct ports forwarded, and to check if your isp blocks any ports try [canyouseeme]("http:///www.canyouseeme.org/").

---

### Post by littlegreiger on 2009-06-14
Make sure you have all the ports forwarded. I've tested a CS source server and I'm pretty sure that it needed a couple different ports open, both TCP and UDP. 
The ones I have forwarded are 27000-27039 on TCP and 1200, 27000-27039 on UDP. These should be the same ports you need to forward. 

If forwarding these ports doesn't work then I'd suggest looking on google. I know there's a site just for linux dedicated servers for cs.

---

### Post by Mykle87 on 2009-06-14
> **cariboo907 said:**
> To make sure you have the correct ports forwarded, and to check if your isp blocks any ports try [canyouseeme]("http:///www.canyouseeme.org/").

Could I somehow do this using Ubuntu Server command line only?


> **littlegreiger said:**
> Make sure you have all the ports forwarded. I've tested a CS source server and I'm pretty sure that it needed a couple different ports open, both TCP and UDP. 
The ones I have forwarded are 27000-27039 on TCP and 1200, 27000-27039 on UDP. These should be the same ports you need to forward. 

If forwarding these ports doesn't work then I'd suggest looking on google. I know there's a site just for linux dedicated servers for cs.

I have those ports forwarded for UDP and TCP. I followed [this tutorial]("http://news.softpedia.com/news/How-to-set-up-a-Counter-Strike-1-6-dedicated-server-under-Linux-35607.shtml") and referenced other tutorials and forums. I'm starting to think it is my loving Comcast ISP.

---

### Post by Mykle87 on 2009-06-14
Ok I just set up hlds and srds on my windows 7 box and port forwarded and disabled windows firewall. Here are the results from canyouseeme.com:

When cs 1.6 is running: Error: I could not see your service on 68.44.63.187 on port (27015)
Reason: Connection timed out

When cs source server is running: Success: I can see your service on 68.44.63.187 on port (27015)
Your ISP is not blocking port 27015

My friends cannot connect to either one over internet.

How could this be? Did steam fubar hlds? Anyone?

---

### Post by cariboo on 2009-06-14
You could get a friend to do a port scan of your router from outside your network, to chceck if the proper ports are open.

---

### Post by Mykle87 on 2009-06-14
Well according to canyouseeme, even though the port is open, people cannot connect to the counter-strike source server when it is running.

---

### Post by (Corndog) on 2009-06-14
Have you tried, adding something like this to the start-up command +hostip YOUR.WAN.IP.ADDY -ip YOUR.LAN.IP.ADDY +hostport 27016 +clientport 27006 , I've ran into problems like this before, and changing the start-up command seemed to help me..

---

### Post by Mykle87 on 2009-06-14
> **(Corndog) said:**
> Have you tried, adding something like this to the start-up command +hostip YOUR.WAN.IP.ADDY -ip YOUR.LAN.IP.ADDY +hostport 27016 +clientport 27006 , I've ran into problems like this before, and changing the start-up command seemed to help me..

Interesting. I will give this a try. Instead of WAN IP, could I use my dyndns address since I have a dynamic ip? I will test it out and report back.

---

### Post by (Corndog) on 2009-06-14
I'm guessing you could, haven't tried hosting a server with dyndns. I suppose it would act the same.

---

### Post by Mykle87 on 2009-06-14
Didn't work. Here is the end of the output:

```
Could not establish connection to Steam servers.
cminterface.cpp (599) : Assertion Failed: NULL != m_hConnection
```

---

### Post by v3xtra on 2009-06-14
> **Mykle87 said:**
> Interesting. I will give this a try. Instead of WAN IP, could I use my dyndns address since I have a dynamic ip? I will test it out and report back.

You don't need to use your DYNDNS address, you just need to use the address that the DynDNS is using to forward to.  If you put the IP of the server as your WAN IP, then that ip is equal to the dynDNS address that you gave it, so that people can either use the WAN IP (***.***.***.***) or just your DynDNS address ( what.ever.dyndns.org ).

Have you googled that error, because I just did and found some interesting information on the error.  It seems to be relatively frequent and there seem to be multiple reasons why it happens, but it would seem as though mainly it is just port forwarding that causes this.  I would try googling what ports NEED to be open for hosting a secure counter-strike server.  :)

---

### Post by Mykle87 on 2009-06-15
Alright. I'm going to put the computer in a dmz on my router and see if people can connect then. I probably should have tried this earlier. I just really feel uncomfortable with a dmz. But if its for testing purposes I'll do it.

---

### Post by Mykle87 on 2009-06-15
Ok I put my router in a dmz and launched the server with hostip and ip and changed the port several and no one can connect. This is a good sign though:
```
Connection to Steam servers successful.
   VAC secure mode is activated.
```
Do I just assume now that comcast is not allowing me to host a server?

---

### Post by v3xtra on 2009-06-15
I would ask comcast and see if they have the ports open on their side to allow you to host a server.  If they do, then maybe ask them if there is anything that you need to do special to get it to work.

The other thing that I would try and do is to make SURE that you have opened the ports on your computer, because if you are on the DMZ, you should be able to connect.  This command will hopefully show you all open ports on your computer, and the ports that you need open are hopefully on there. If not, you may need to find out how to open them.

```
sudo nmap -T Aggressive -A -v 127.0.0.1 -p 1-65000
```

Hope that helps!

---

### Post by Mykle87 on 2009-06-15
I will try a port scan. It is just weird because my friends can connect to me via at least port 22 and 8080 over the internet. I cannot understand why this is such an issue.

---

### Post by Mykle87 on 2009-06-15
> **v3xtra said:**
> ```
sudo nmap -T Aggressive -A -v 127.0.0.1 -p 1-65000
```

Ok after running this command with and without the server running, here is part of my output:
```

Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 64993 closed ports
PORT      STATE SERVICE     VERSION
22/tcp    open  ssh          (protocol 2.0)
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
631/tcp   open  ipp         CUPS 1.3.9
8080/tcp  open  http        Jetty httpd 6.1.x
9412/tcp  open  unknown
52627/tcp open  unknown

```
So basically the default ubuntu server firewall (iptables) is not allowing people to connect to my cs server even though I can connect on my lan?

---

### Post by (Corndog) on 2009-06-15
Have you added the ports to the firewall rules? If not do so, I would suggest shorewall instead of the default ubuntu firewall tho, just my two cents.

---

### Post by Mykle87 on 2009-06-15
I briefly looked into how to use iptables and it looks really complicated. Is there anyway to disable it? What I don't understand is why can I connect on my lan. The software firewall should prevent both lan and wan.

---

### Post by Mykle87 on 2009-06-17
I typed this:
```
iptables -t filter -I INPUT -j ACCEPT -p udp --dport 27015
```
Computer still in dmz. Still no one can connect. Nmap doesn't list the counter-strike service as running. Does anyone understand this? I am not going to give up on this.

---

