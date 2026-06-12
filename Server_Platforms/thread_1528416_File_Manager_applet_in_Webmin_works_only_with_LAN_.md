---
title: "File Manager applet in Webmin works only with LAN IP"
date: 2010-07-10
forum: Server Platforms
---

### Post by kayjaygee_13 on 2010-07-10
Hi, when I connect to Webmin using [https://domainname.com:10000]("https://domainname.com:10000/"), I  cannot get the File Manager Java applet to work. If I connect from within my LAN  using [https://192.168.0.100:10000]("https://192.168.0.100:10000/"), the applet works. Any ideas? Thank  you in advance.

---

### Post by Vegan on 2010-07-10
Are you sure that is right machine IP address?

---

### Post by kayjaygee_13 on 2010-07-10
Yes, the internal IP address on the LAN is 192.168.0.100. To access Webmin via the Internet, I use the URL [https://hostname.homelinux.org:10000](https://hostname.homelinux.org:10000).

---

### Post by kevinthecomputerguy on 2010-07-13
You could compare your setings to mine here
[http://woodel.com](http://woodel.com)
 
Also...
The File Manager uses Java. Make sure Java is installed on every computer you try it from. [http://java.com](http://java.com)
 
Do you have a port forward in your router from external 10000 to internal 10000
 
Also check, Webmin \ Webmin Configuration \ IP Access Control.
Blank that out if anything is listed and try again.
-Kev

---

### Post by kayjaygee_13 on 2010-07-13
Kev, I have a desktop (LAN IP is 192.168.0.103) and a laptop (LAN IP 192.168.0.102) and both have Java installed and working properly. Both machines can use the File Manager applet (and the SSH2 Login applet) if I connect to Webmin using the LAN IP of the server, which is 192.168.0.100. However, if I use the host name to access Webmin, the File Manager applet won't work, BUT the SSH2 Login applet works, which proves that Java is working. It might be worth mentioning that the desktop is running Windows 7 and the laptop is running Vista (both are 64-bit). My computer at work is running XP 64-bit and when I connect using the host name, both applets work perfectly. Strange, wouldn't you say?

Edit : IP Access Control does not have any entries.

---

### Post by kevinthecomputerguy on 2010-07-13
Oh, I think im on the right page now.
So you are having internal naming problems then? Basically your webmin box is named, lets say fred.
And internally you cant get to [https://fred:10000](https://fred:10000) but you can get to fred's IP [https://192.168.0.100:10000](https://192.168.0.100:10000) is that what you are saying?
 
If thats what you meant, This is pretty common when you mix Linux and Windows. The easy fix is to edit the c:\windows\system32\drivers\etc\hosts file on all of your internal windows boxes, and make an entry like this (there will be examples in there)
192.168.0.100 fred
 
This will force your windows box to locally resolve that name to that IP address.
Thats the quick and easy fix. 
 
The next fix is a little harder, checkout page 96, 97, and 98 of my guide, (the PDF version), it will show you what changes you can do on your linux box to help ( [http://woodel.com](http://woodel.com) ) Pages 96 and 97 for sure, but careful with page 98, if that looks weird to you, skip it for now, you will lose your internet connection if you dont know what to put in there. If this all started when you switched from a DHCP address to a static address, then those pages will help. Then reboot.
 
The next fix is a little harder still. Make sure your DNS server is a local IP address. This might sounds french to you, or way off base because you probably dont have a DNS server, but alot of people put static openDNS entries in their routers config page, which causes their main DNS entry to be a public one. Do an ipconfig /all from your windows box, and make sure your first DNS entry is your routers private IP address. Then reboot everything on your network, all computers routers printer etc..
 
The real fix is to setup a DNS server. That is also covered in the guide on my website, but is overkill on a small network.
 
Anyway, if im way off, let me know :- )
 
*Thats hosts file will be hidden and read only, dont forget to change it back.

---

### Post by kayjaygee_13 on 2010-07-13
Kev, I didn't know [http://woodel.com](http://woodel.com) belonged to you. I actually used your guide to get my server up and running, so thank you for that fantastic document. :)

To answer your questions, let's say my host name is fred.homelinux.org (I'm not sure if it's a good idea to post my real host name in a public forum). Basically, my host name looks exactly like that except, "fred" is replaced by my first name.

I can connect to my server using [https://fred.homelinux.org:10000](https://fred.homelinux.org:10000) from any computer (outside of my home) via the Internet and all the Webmin utilities work flawlessly. DHCP on my router has my server's internal IP bound to 192.168.0.100. While I'm at home, if I use my desktop or laptop to connect to [https://fred.homelinux.org:10000](https://fred.homelinux.org:10000), the File Manager applet doesn't work. Everything else in Webmin works fine, including the SSH2 Login applet under the "Others" menu in Webmin. On the other hand, if I connect using [https://192.168.0.100:10000](https://192.168.0.100:10000) on my desktop/laptop, Webmin works flawlessly (including both the File Manager and SSH2 applets).

One thing I haven't tried yet is using my laptop to connect to [https://fred.homelinux.org:10000](https://fred.homelinux.org:10000) from outside my home, but like I said, I have tested it from other machines and it works perfectly. Also, as I've mentioned in my previous post, Java is working correctly on both the laptop and desktop, so I don't think that's the issue.

A Google search yielded this link, although I'm not sure if it is of any relevance : [http://copilotco.com/mail-archives/webmin.2009/msg00601.html](http://copilotco.com/mail-archives/webmin.2009/msg00601.html)

I hope my description above wasn't too confusing. Let me know if it is. Thanks again for your guide and the help.

---

### Post by kevinthecomputerguy on 2010-07-13
[FONT=Times New Roman][SIZE=3]Thanks !!![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]That&#8217;s funny, small world : )[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I swing by the Ubuntu Forums every so often to pay my thanks. I have actually had some forums kick me off, label me a spammer, and say im trying to advertise my woodel website. Can you imagine ! I was like ummm&#8230; have you looked at my site you idiots !![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Anyway, Ubuntu Forums has been extra cool to me, so I swing by to see if I can help anybody.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]That is a weird problem, where the File Manager wont work, but everything else does. I have only seen that a few times.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Once I was messing around with the &#8220;trusted refers&#8221; in Webmin, trying to tunnel the file manager through one central webmin server, controlling many other webmin servers. I jacked that up and had to reformat. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The other time I saw that was on a 64 bit machine, the Java pluggin would only go to the 32 bit browser, so I had to go to the start menu \ programs, and choose internet explorer 32, because 64 bit wouldn&#8217;t bring up the file manager.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Anyway, try&#8230;[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Try it with just the computer name, leaving off the domain. Example : [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]https://fred:10000[/SIZE][/FONT]]("https://fred:10000/")[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Try your internet explorer 32 bit browser.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]And try that hosts file thing, that should force it to act the way you want to. Treating the name the same way it would treat the IP.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]But yep, that&#8217;s a weird one. I&#8217;m running out of idea&#8217;s of what it could be.[/SIZE][/FONT]

---

### Post by kayjaygee_13 on 2010-07-13
Thanks Kev. I'm using 32-bit Firefox; I'm not sure whether IE is 32 or 64-bit because I rarely use it, but it displays the same behavior. The one thing I haven't tried yet is using my laptop from outside my LAN to see if the applet works when connecting to Webmin using the host name, although I have my doubts. I'll try that tomorrow from work and see what happens. I hope it works because I'll be out of the country next month for a couple weeks and I would really like to have full Webmin functionality with the laptop. If not, I guess I'll have to learn the command line.

---

### Post by kevinthecomputerguy on 2010-07-13
Try I.E. 32
And visit Java.com before hand. I do have SSL and https cert issues with firefox, so that would be a good path to take.
 
*Webmin works from my cell phone, so keep trying, hopefully its something with your desktop install (hopefully)
 
Keep us updated \ keep up the good trouble shooting.
-Kev

---

### Post by kayjaygee_13 on 2010-07-14
Alright, I don't understand why the File Manager applet behaves the way it does, but my problem is solved. Here's what I found.

When I'm browsing the Internet on my home network with my laptop, I can connect to [https://192.168.0.100:10000](https://192.168.0.100:10000) and everything in Webmin works flawlessly, including the File Manager and SSH2 Login applets. However, if I log in to Webmin using [https://fred.homelinux.org:10000](https://fred.homelinux.org:10000), the File Manager applet does not open, but everything else in Webmin works perfectly.

Today, I took my laptop to work and connected using [https://fred.homelinux.org:10000](https://fred.homelinux.org:10000) and EVERYTHING worked, even File Manager.

Apparently, when connected to the same network as the server, the server IP needs to be used to log in to Webmin. Using the host name somehow causes File Manager to malfunction. It doesn't make sense.

---

### Post by kevinthecomputerguy on 2010-07-14
[FONT=Calibri][SIZE=3]Interesting, I don&#8217;t have that problem, but I have a local dns server.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Did you try editing the hosts file on the windows computers?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Something like[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]192.168.0.100                     fred[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Also, did you try leaving off the domain name, [/SIZE][/FONT][[FONT=Calibri][SIZE=3][COLOR=#0000ff]https://fred:10000[/COLOR][/SIZE][/FONT]]("https://fred:10000/")
[FONT=Calibri][SIZE=3]I tend to use the IP, or a bookmark, even though I know the name, so I agree with your solution.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Kev[/SIZE][/FONT]

---

### Post by kayjaygee_13 on 2010-07-14
Thanks for the help Kev. Adding "192.168.0.100  fred.homelinux.org" to the hosts files on my laptop fixed the problem. Now the File Manager applet works whether I use the IP, the entire host name (fred.homelinux.org) or just "fred".

The one step that I ignored in your guide is assigning a static IP to my server using the instructions on page 49. I used DHCP on my router coupled with the server's MAC address to assign a static IP. Could this be the reason for this issue?

---

### Post by kevinthecomputerguy on 2010-07-14
Awesome! this will be a realy good fix for a small network.
Yes, the DHCP reservation can totally be the culprit, it will over-ride some of your local dns settings the guide has you do.
 
But DNS issues are a pain, change the host files on the (2) windows computer and run away :- )
keep up the good work man! spread the Webmin love
-Kev

---

### Post by kayjaygee_13 on 2010-07-14
One last question Kev. I just thought about this, but if I have the entry "192.168.0.100  fred.homelinux.org" in my laptop's hosts file, wouldn't I face a problem when trying to connect from external networks since that host name is now bound to an internal IP? This might a dumb question, but I'm not sure I understand the function of the hosts files completely.

---

### Post by kevinthecomputerguy on 2010-07-14
Use only the name fred in the hosts file, and leave off the domain name.
When at home, type [https://fred:10000](https://fred:10000) 
When away type [https://fred.homelinux.org:10000](https://fred.homelinux.org:10000)
 
You can also totally lie in the host file. You can put
192.168.0.100 hotchick
 
And when at home, use [https://hotchick:10000](https://hotchick:10000)
and when away, use the real name.
 
But thats just fun, the first suggestion should work.
-Kev

---

### Post by kayjaygee_13 on 2010-07-14
Ah I see. Thank you very much for all the help. I really appreciate it. :D

---

### Post by kevinthecomputerguy on 2010-07-14
Anytime.
You know you want to name your server hotchick !
:- )
Take it easy
-Kev

---

### Post by MrCrumbly on 2012-11-17
Hi there

An interesting observation sometime after the event - but somebody might have an answer.  A windows network 192.168.100... DHCP behind a router and firewall operates webmin perfectly if I put in the IP address of the external domain. (I was using Chrome browser)

A Samsung Chromebook (last year's model) will also run webmin but when it comes to Filemanager it complains there is no extension to run the app - maybe a permissions problem? 

The page tries to load a java applet called filemanager and then complains that chromebook doesn't support java.  I thought the webserver was supposed to do that?  Surely chromebook wouldn't run Java client side?  The idea is not to setup software on the client device if I understand it correctly.

I have no access to a hosts file on this computer.  It is connected to a 3G modem 192.168.100.1

I have had no problem connecting with Shift-Edit to the new site,   so I will probably be able to manage when I know where everything is.  

The chromebook will run the bash shell with ssh so I have command line access to the server.  Sorry the chromebook's not Ubuntu, but it is a Unix os under the hood.  I am trying to set up my development environment totally cloud based without recourse to a conventional laptop or lan based desktop.

Thanks 
Mr Crumbly

---

