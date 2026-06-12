---
title: "Trying to set up home server."
date: 2009-12-18
forum: Server Platforms
---

### Post by ram4nd on 2009-12-18
I am trying to set up a small home server by this tutorial:
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

I did as guided, but I can access my server only from local host. I am also using dyndns on speedtouch router.

---

### Post by cj13579 on 2009-12-18
Have you forwarded the relevant ports on your router? 

The standard ports are 22 for ssh 21 for ftp and 5900 for VNC if you have a desktop installed?

---

### Post by Lars Noodén on 2009-12-19
Skip the part at the end of the tutorial regarding ftp and don't open those ports, unless you plan to allow public download via ftp.  For upload, use SFTP, which is a well-tested, secure protocol for file transfer.  The old protocol, FTP, sends everything unencrypted.  SSH / SFTP both use port 22. 

If you follow the steps in the tutorial, then you have OpenSSH server already installed and that has sftp built in.  So you can point your favorite tool (Konqueror, Dolphin, Filezilla, Nautilus, etc) to the server and access it via SFTP.

That will save a lot of configuration effort and headache.

---

### Post by BkkBonanza on 2009-12-19
Also note that many routers will not route back using their public IP even if the ports are forwarded. That would be the next check if you are sure you have forwarded correctly. Use a free proxy website on the net to check if your url is working.

---

### Post by ram4nd on 2009-12-19
Got it to work, at least the admin panel, nothing to do with ports. Just my /etc/host had wrong ip address in it.

---

### Post by confusedstingray on 2009-12-22
did you configure machine to be static IP 
if not you might want to do this so for eg: set the server to 192.168.1.4
then you can get to your server via web interface like webmin

---

### Post by ram4nd on 2009-12-27
I use dyndns, so my ip is not static.

---

### Post by confusedstingray on 2009-12-27
ok i think i understand what you are trying to do 

to make things stay the same I would set you servers ip to a static ip like it suggested in the tutorial (step 7) set the ip to match your network if you are using 192.168.1.xx (change xx to match your network) or what you have used. Now on your router, depending on your router you have to allow port 80 to go through to your server.(if you are servering web pages) this is in the port foward area on your router.(if you need help just need to now the make and model of router). dyndns is just allowing you to have static WWW ip. This ip will be sent to you now through your router and server you will allow or not allow things to happen by opening ports such as mail Port 25 and 110. also i would suggest to allow your router to do DHCP for the rest of your network.  


dydnsip -------router-----server   server is behind the router to help with security

hope this helps if you need more help pls let me know more than willing to help with i can. I'm doing the same thing and it took abit to get the bugs worked out

---

### Post by ram4nd on 2009-12-30
Yes I wanted to do that, since I got my 192.168.0.x ip back I cant redirect any ports to my device. But ill try to fix that and then ill see what happens next. Port 80 is blocked by my isp.

---

### Post by confusedstingray on 2009-12-30
ok if you get the ip changed. there is a port 80 work around using you dyndns
here is the page from dyndns 
[ ]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html")
the idea is you set apache to listen on a different port besides 80. Eg
*[www.mydomain.com:456](www.mydomain.com:456)*  this will show your web page but so people don't have to type the :456 evertime dynDns will set that when someone types *[www.mydomain.com](www.mydomain.com)* it redirected to* [www.mydomain.com:456](www.mydomain.com:456)*

---

### Post by confusedstingray on 2009-12-30
[http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html ]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html")
oops sorry

---

### Post by lisati on 2009-12-31
> **ram4nd said:**
> I am trying to set up a small home server by this tutorial:
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

I did as guided, but I can access my server only from local host. I am also using dyndns on speedtouch router.

Is that a router by Thomson? Mine (a Thomson 585 Speedtouch router/modem) has options for entering no-ip account details, so I don't really need to use the noip2 client available from no-ip (but it doesn't hurt). It also has an option on its toolbox->game & application sharing menu for assigning specific ports to specific devices.

---

