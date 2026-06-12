---
title: "Can not create a server"
date: 2010-07-12
forum: Server Platforms
---

### Post by Kognit on 2010-07-12
Hi

I am a total newbie regarding creating home servers.
I want to create a server on my laptop. I tried to create it with the "proftpd", but the filezilla just couldn' connect it. I did port forwarding in my router (interesting, when i added a password in router regarding portforwarding, the password was changed on my Ubuntu 10.04 too). I used guidelines in [http://www.ubuntugeek.com/setting-up-a-proftp-server.html]("http://www.ubuntugeek.com/setting-up-a-proftp-server.html") and it just doesn't want to connect.

Any solutions?

thx

---

### Post by fcefan00 on 2010-07-12
Is proftp running? Have you checked the logs and open ports with netstat?

---

### Post by Kognit on 2010-07-12
hi

thx for reply

proftd is running. How can i check it with netstat?

My goal is that on my laptop (which i use everyday) some space would serve as a  server (on Ubuntu 10.04 (desktop edition), not on Ubuntu Server). I configured proftpd as a standalone.
I determined user, server name, directory,... on router i determined port forwarding i think i had configured it properly, i enabled virtual server too and assign my local IP. I really don't know what is it.

---

### Post by tyleruk on 2010-07-12
open your console and type: > sudo nmap 127.0.0.1 to see if your ftp port is open? 




If the ftp port is open try: > ftp 127.0.0.1 on your ubuntu computer to see if you can get connected localy?

---

### Post by Kognit on 2010-07-12
hi

thx for reply



When i do sudo nmap 127.0.0.1 :
```
Starting Nmap 5.00 ( http://nmap.org ) at 2010-07-12 19:18 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 997 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
80/tcp  open  http
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds


```

ftp 127.0.0.1 
```
Connected to 127.0.0.1.
220 Perunika
Name (127.0.0.1:saso): 


```

---

### Post by arrrghhh on 2010-07-12
Looks good, so you can't connect from the outside?  Because that looks like you can connect locally.

Do you have UFW enabled?  ```
sudo ufw status
```  to check.  If not, then I'd bet it's on the router (I assume you're trying to connect from outside your local network?).  It could also be your ISP blocking traffic to port 21.

---

### Post by Kognit on 2010-07-12
Hi

ufw is inactive.

I can't connect externally  with the filezilla.

In my router i enabled virtual server, assigned my ip and the port, ... Nothing yet

Maybe i should configure radius in router?

I have Firestarter on. Is this a problem?

---

### Post by arrrghhh on 2010-07-12
Ok since you can connect on localhost, and UFW is not enabled it's either the router or your ISP.  Try to connect another PC on your LAN, see if that works.

---

### Post by Kognit on 2010-07-12
Sory, but i temporarly can't connect any computer to th LAN. Is there any other way possibly?

---

### Post by arrrghhh on 2010-07-12
Well you can go to a site like [ShieldsUp!](https://www.grc.com/x/ne.dll?bh0bkyd2) to see what ports are open on that machine...

Your unwillingness to troubleshoot is going to make things difficult to narrow down.  So far you can connect on the localmachine so the service is running.  I'm just going to assume that you can connect on your LAN, and probably the issue is WAN related.

I didn't ask, are you connecting (on the WAN to your server) via IP or thru a DNS friendly name?

---

### Post by Kognit on 2010-07-12
I am willing but i don't have any other computer at my home. Just my laptop.

When i was connecting on local machine i was connecting on my laptop which i use right now. 

I have wireless router and i am connect via ip.

I will visit your link tommorow because i am in hurry right now. 

Sorry to trouble, but i am really a newbie regarding networks and servers.

---

### Post by arrrghhh on 2010-07-12
No trouble, it just makes it difficult when you cannot perform certain troubleshooting steps.  I was just trying to narrow down where your issue was occuring.

That link will test all the open ports on your network - if it doesn't see 21 as open, either your router config is wrong or your ISP blocks the traffic to that port!

---

### Post by Kognit on 2010-07-12
I have just remember, that about 2 years ago when i didn't have a router (i was on LAN) i could access to my computer via public IP. So it has to be something with the router. Most certainly i have misconfigure it.

---

### Post by arrrghhh on 2010-07-12
That sounds like a great place to check.  If you do solve it, please post back what the solution was and use the "Thread Tools" drop down to mark the thread [SOLVED]!

---

### Post by Kognit on 2010-07-13
Here is the report from the Shield page:

GRC Port Authority Report created on UTC: 2010-07-13 at 08:55:11

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.


--------------

Common ports:

GRC Port Authority Report created on UTC: 2010-07-13 at 09:00:05

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    0 Ports Open
    0 Ports Closed
   26 Ports Stealth
---------------------
   26 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.



TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

---

### Post by tyleruk on 2010-07-13
It defiantly looks like a misconfigured router, sheildpage should see Port 21 as open. You need to forward all traffic on port 21 from your router to your servers IP address. The routers manual should explain port forwarding, if not a good tutorial can be found at [http://lifehacker.com/127276/geek-to-live--how-to-access-a-home-server-behind-a-routerfirewall]("http://lifehacker.com/127276/geek-to-live--how-to-access-a-home-server-behind-a-routerfirewall")

---

### Post by Kognit on 2010-07-13
I did port forwarding. What about this configuration - should i enable "Enable Web Access from WAN?". I did this too, but nothings happens.

---

### Post by tyleruk on 2010-07-13
I'm not familiar with ASUS routers, however access from WAN usually gives people on the internet access to your router settings page, and I doubt you want, so keep it set to no.

You should run another Shield page test to see if port 21 is now open, if it is your ftp server should work.

---

### Post by noway2 on 2010-07-13
Normally your router will only allow you to access the configuration page via a local, non public, IP address.  This helps to ensure that only you can make changes to it.  Enabling "web access from WAN" is probably enabling remote access, which would be unwise.

I didn't see anything super telling in your attachment as far as where to set the port forwarding, but it may be under the NAT section.  You should see something where it defines a service name, a port, and the IP address to forward it to, as well as protocol (TCP/UDP/Both).  You will want to set this to forward port 21 to the local IP of your server.  In some routers this is done in one place and in others two.  For example, in the netgear fvs318 series you define the service as the port, protocol, and IP and then you enable it under a different menu.  In other words, you may need to look in multiple places.

Once you get it up, the shields up site should see port 21 open.

---

### Post by Kognit on 2010-07-13
Hi

21 port is still stealth. Here are various attachments from my router, hope this will help. Damn it hurts to be newbie :)

---

### Post by tyleruk on 2010-07-13
Disable your dmz, this could make your ftp server vulnerable to attacks.

It looks like the settings on your port trigger are causing you problems, it should read

Trigger Port - 21
Protocol - TCP
Incoming port - 20:21
Protocol TCP

---

### Post by Kognit on 2010-07-13
Nothing new. I have Firestarter on, but though i disable the Firestarter, port 21is still stealth. Any suggestions?

---

### Post by Kognit on 2010-07-13
Perhaps some change here?

---

### Post by Kognit on 2010-07-13
If i enable virtual DMZ, my port is opened and friend can now access my server. Is this a solution?

---

### Post by arrrghhh on 2010-07-13
> **Kognit said:**
> If i enable virtual DMZ, my port is opened and friend can now access my server. Is this a solution?

Well... not really.  It literally is like just putting your server on the internet with no hardware firewall in front of it.  So it opens up ALL ports.  So if you have ssh enabled, or anything else... anyone can then access it easily.

The best would be to figure out why it's not being forwarded correctly.

Perhaps it would be best to do a reset on your router - there's a pin somewhere on the back usually that you hit with a pen and it resets the router back to factory defaults - yes, you will have to set everything back up again with your wireless, but there may be some setting in your router that's messing it up.  Have you been to portforward.com?  They have great guides, and pretty much every single router model out there you can imagine.  The site will walk you thru how to properly forward ports.  I don't think in your case it's under the port trigger section, it's probably virtual server or something like that...

Like I said, go to portforward.com, and find your router make/model on that site.  They will guide you how to properly forward ports.  Using a DMZ is not a good idea, because it exposes your system to attack.

Also, it looks like your DHCP pool may be stomping on your static IP range.  Is your server IP static, and 192.168.1.2?  If so, I'd set my DHCP pool to start higher.  Mine for example starts at .100.

---

### Post by Kognit on 2010-07-13
Well, that is not good. If my friend want to access my server i have to disable firestarter too. 

I tried everything. I assign static IP and so on. I think i configured everything fine. I really don't know. Maybe router upgrade?

---

### Post by arrrghhh on 2010-07-13
> **Kognit said:**
> Well, that is not good. If my friend want to access my server i have to disable firestarter too. 

I tried everything. I assign static IP and so on. I think i configured everything fine. I really don't know. Maybe router upgrade?

Did you not read my suggestions **at all**?  Because it's REALLY difficult to help someone who it unwilling to help themselves.  Your router is fine, your configuration on your router is BAD.

You can get this configured, you just have to take some time maybe do some reading.

---

### Post by Kognit on 2010-07-13
OK. Finally did it and **it works**, though i visited that page before and didn't worked because i configure something else too (i have then enabled "port forwarding" tab). 

So, i did the following according to your web page:
i disabled port forwarding (because on that page they didn't enabled port forwarding tab), and only enable virtual server. My virtual server is a bit different from the virtual server from the link (it's really funny, because i have chosen the right model). In the portforward.com web page you gave me, you have option "both" under the protocol ([click]("http://portforward.com/english/routers/port_forwarding/Asus/WL-520GC/FTP.htm")) in virtual server tab, but mine has only option TCP or UDP. I have chosen TCP and it works. I think that is nothing wrong, right? After all it works. 

So, thank you and sorry for troubles i made. This is my first time. A lot of problem for my late server working is also the fact that i have ran Firestarter and he blocked my port and the web port check report different status.

So, thx again for your patience.

Bye

---

