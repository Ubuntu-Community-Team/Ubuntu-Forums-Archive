---
title: "Webserver Config"
date: 2013-08-30
forum: Server Platforms
---

### Post by Greg_Nemecek on 2013-08-30
Good afternoon all,
I had a web server built that is running Unbuntu and using Apache to serve (actually two) websites.  
This box is to replacing an existing Windows machine that has hosted the sites for a number of years. 
 The guy helping me with this build has become UN-available and my old server crashed last week leaving me without a way to host our sites.

I've got the new linux box up and running. However the website (only one of them) is visible to computers *on my local* network. Some machines see it via the wireless connection while others can see it over the wired (again internal) network.  If I try to check the site from outside the local network I can't see it.   Even if I try to check it via IP.

I know this is a stretch but I'm reaching out to see if anyone can help me with getting it 'visible' to the outside world. 

Any help would be greatly appreciated. 
I'm at work on break so I won't be able to check back for a few hours. 
Again thanks for any help.

Nemo

---

### Post by coffeecat on 2013-08-30
Not a Forum Feedback & Help thread.

*Thread moved to **Server Platforms**.*

---

### Post by houstonbofh on 2013-08-30
It is likely a router problem, not a server problem.  Is the new server on the same internal IP as the old one?  Does your router have port forwarding to it?

---

### Post by CharlesA on 2013-08-30
> **houstonbofh said:**
> It is likely a router problem, not a server problem.  Is the new server on the same internal IP as the old one?  Does your router have port forwarding to it?

Port forwarding issue more than likely, depending on how the web server is configured.

---

### Post by nerdtron on 2013-08-30
What is the IP of the Web Server? If it is a private IP, then you need port forwarding on the router or the webserver config for the it to be accessible on the outside world. Or you can put a Public IP address on the webserver and let it interface to the outside world. You might want to secure the server if you do this.

---

### Post by Greg_Nemecek on 2013-08-30
Thanks for all the responses. But after thinking about this would not (if the server was setup the same as the windows machine) the port forwarding already be set on the router? I'll still look into it in the AM.  
Houstonbofh -> Yes... as far as I know it is set with the same IP.   I'm assuming a bit now but will check in the morning. Prior to building this machine he had the old one and pulled all the IP information from it. So I'm pretty certain it's the same. 
Nerdtron ->  I believe the IP is a public one. 72.35.35.199 and yes... one of the last things he said to me was that he wanted to secure the machine 'a little more' before deploying it...  
This is a start...  I'll look into the port forwarding in the morning..

---

### Post by SeijiSensei on 2013-08-30
Here's an nmap scan of that address; you have a awful lot of filtered ports.

Starting Nmap 6.00 ( [http://nmap.org](http://nmap.org) ) at 2013-08-30 21:28 EDT
Nmap scan report for mail.cfachurch.org (72.35.35.199)
Host is up (0.082s latency).
Not shown: 988 closed ports
PORT     STATE    SERVICE
20/tcp   filtered ftp-data
21/tcp   filtered ftp
25/tcp   filtered smtp
80/tcp   filtered http
110/tcp  filtered pop3
111/tcp  open     rpcbind
1720/tcp filtered H.323/Q.931
5500/tcp filtered hotline
5800/tcp filtered vnc-http
5900/tcp filtered vnc
8000/tcp filtered http-alt
8001/tcp filtered vcom-tunnel

There is some type of firewalling between this machine and the Internet.  

If you are going to be running a public server, and you only intend to offer HTTP and maybe HTTPS, I would wall off everything except ports 80 and, if appropriate, 443.  VNC is the last thing you want to be running on an Internet-facing server. However since the server is called "mail.cfachurch.org" I assume you want ports 25 and 110 open as well.  If you're really acceping mail on port 25, make darn sure that you have configured Postfix or sendmail properly so that spammers won't exploit the machine as an "open relay."

---

### Post by CharlesA on 2013-08-30
I wonder why port 111/tcp open rpcbind is open. I seem to recall it having something to do with NFS.

---

### Post by Greg_Nemecek on 2013-09-03
I saw that the server is set up as 'mail.cfachurch.org' and am not sure why..... The old server did have mail running on it but no one ever check the mail that was coming into the accounts setup on it so I shut the mail side of it down.     I can see that I'm am really gonna need to spend some time on this. I was hoping that I wouldn't need to get so involved with this project. I have too many things going already. 
  Thanks much for all your responses. It's greatly appreciated.   If anyone could point me to a step by step process of 'setting up a web server' it would be very helpful. I know how to navigate and modify files in linux... I'm simply not aware of what needs to be configured for a web server.  This will not be running mail... just hosting two websites. Thanks again everyone. The Linux world ROCKS!

---

### Post by CharlesA on 2013-09-03
Run this:

```
hostname
```

```
hostname -f
```

---

### Post by SeijiSensei on 2013-09-03
$ host 72.35.35.199
199.35.35.72.in-addr.arpa domain name pointer mail.cfachurch.org.

Your ISP has a "PTR" record for that address that maps back to mail.cfachurch.org.  That was probably set up long ago.

I did a lookup at ARIN for that address:  [http://whois.arin.net/rest/net/NET-72-35-32-0-2/pft](http://whois.arin.net/rest/net/NET-72-35-32-0-2/pft)

Your provider appears to be Allendale Telephone.  If you want to rename the server, you should give them a call and ask to have the PTR record changed to whatever you want the machine's name to be.  Since the PTR record is supposed to point to the server's "canonical" name, you should designate one of the two web site names as the primary.

Or you could just leave it as mail.cfachurch.org.  For web service, it doesn't really matter what the machine itself is called because you will be using "virtual" hosting based on the site's name, not the server's name.  

Having the forward and reverse DNS lookups match is of greater importance for mail servers.  A machine sending mail that claims to be mail.example.com, but whose PTR record returns a different name, may have problems with deliveries to servers with strong anti-spam rules in place.

---

### Post by CharlesA on 2013-09-03
> **SeijiSensei said:**
> 
Or you could just leave it as mail.cfachurch.org.  For web service, it doesn't really matter what the machine itself is called because you will be using "virtual" hosting based on the site's name, not the server's name.  

Having the forward and reverse DNS lookups match is of greater importance for mail servers.  A machine sending mail that claims to be mail.example.com, but whose PTR record returns a different name, may have problems with deliveries to servers with strong anti-spam rules in place.

+1. I have my mail server set up to be accessible via mail.charlesa.net, but I have DNS set up to resolve to the server's actual hostname.

---

### Post by Greg_Nemecek on 2013-09-05
OK here's an update on the server issues I'm having:
I was able to get to looking into the port forwarding on the router:
The services (on the router) showed that it was looking for ports being forwarded from:
192.168.1.45

SO....
First I did was an 'ifconfig -a'[COLOR=#000000][FONT=times new roman]It returned:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Eth0 (not configured  and showed no IP)
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Eth1  72.35.35.199    (which after talking with my ISP was incorrect)  
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]___________________________________________________________

[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]After seeing what the 'ifconfig -a' returned I went to:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]/etc/network/ and found two files in that directory
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]interfaces[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]interfaces~[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]The 'interfaces' file was as follows:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Eth0 
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]IP:                192.168.1.44[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Subnet:        255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Gateway:    192.168.1.1
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]______________________________________
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]The 'interfaces~' file was as follows:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]IP:                192.168.1.44[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Subnet:         255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Gateway:       192.168.1.1[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]And has a statement 'Eth0  Static IP'  at the bottom of it.
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]______________________________________________[/FONT][/COLOR]

[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I changed the 'interfaces' file to the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Eht0              changed 0 to 1
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]IP:                192.168.1.45     <---- This is the IP that the router is looking to receive the port forwards from.
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Subnet:         255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Gateway:       192.168.1.1    <------ Which is the router[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Restarted the machine.   I checked the ifconfig -a again...[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]It reported Eth1: 192.168.1.45[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Immediately I found the web site visible from the web. 
SO.. that problem SEEMED to be fixed.

_____________________________________________________

Next I checked the Anavah site ([www.anavah.org]("http://www.anavah.org")) but it was dropping me right back on the CFA site.
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]So looking in the Apache2 folder I found two folders:
sites-available & sites-enabled:  
In each folder I found a 'default' file.  In THAT file I found the anavah site was configured as anavah.com     It's supposed to be anavah.org
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I changed that line in both 'default' files (in the sites-available & sites-enabled directories)  and rebooted.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]And low and behold the ethernet interfaces are both down again. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I tried for an hour and a half to get them back up to no avail.

I also tried to configure the nics thru the gui but no success. 
I'm wondering if there's more to setting the IP address than just what I find in the /etc/network/ folder.
The reason I'm wondering that is because the IP I originally found in the 'ifconfig -a' showed an address that was not in either of the /etc/network/interfaces files...
Thoughts?


Nemo
[/FONT][/COLOR]

---

### Post by CharlesA on 2013-09-05
What is the output of ifconfig -a and what happens if you try to bring up the interface manually?

```
sudo ifup eth1
```

Also, please post the contents of your interfaces file.

---

### Post by Greg_Nemecek on 2013-09-05
Sorry for not posting the contents of the files.... I should have done that in my last post.
In any case......  
So the guy helping me out with the build got in touch with me... 
He headed out to work on the server and here's what we discovered. 

So he ran the 'ifconfig -a' again and it returned that both interfaces were down.

He looked into the /etc/network/interfaces file... and the file was EMPTY... nada.. nothing in it.

He re-populated the file with the correct information and cha-ching! It's up again.  And with the added changes I made to the sites-available / sites-enabled files the second site is up as well.

Now I could just walk away and say "It's up and running and I don't need to think about it anymore"  .... but that's not me. I still have some questions. These two probably the ones bothering me the most... 

1.  How could the ifconfig -a return 72.35.35.199 on eth1 when neither of the 'interfaces' (eth0 or eth1) files had any of those values in it?

2.  After I edited the 'interfaces' file and did the 'esc,wq' I did a 'cat' on the file to see if my changes were kept.... and they were.   Is there some place in the OS that can override what is in the interfaces file? And would a restart initiate that?


Thanks for all of your help!   Nemo

---

### Post by CharlesA on 2013-09-06
If the interface was brought up before the interfaces file was changed, it would still have whatever settings were originally assigned.

I think network manager messes with the interfaces file, but that shouldn't be an issue with a server install.

---

### Post by Greg_Nemecek on 2013-09-15
Thanks so much for all the help.
All the changes that I made were correct. Including the multiple domain fixes.  But I had somehow inadvertently wiped out all the information in the 'Interfaces' file thus the eth1 & eth0 interfaces showing as not configured.

Along with that we discovered that the aftermarket NIC for some reason has failed. So we are using the on-board NIC.  Once the Interfaces file was corrected and the eth service restarted it popped up. 

Thanks again for all the shortcuts and helpful instruction.

---

