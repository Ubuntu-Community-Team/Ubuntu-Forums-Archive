---
title: "Hopefully easy question"
date: 2008-04-18
forum: Server Platforms
---

### Post by TuckLive on 2008-04-18
I have 7.10 Server running Citadel groupware on my home network now.  I want to share music, videos, etc. also.  I also want to be able to remote access into this box if I am at work or whatever.  What is the best way to do this and/or what application should I use?  I was thinking putty or winscp, but I am new at servers and remote access so I need suggestions and a point in the right direction.  Thanks

---

### Post by pseudo-random on 2008-04-18
For a console login: SSH
For a GUI: VNC

Putty would be the client you use on a windows box to access SSH on your ubuntu machine and likewise winSCP which is good.

```
sudo apt-get install ssh
```

Forward port 22 to something like 65022 with your router to keep all the kids from trying to get r00t on your box. Then just configure putty with your IP/domain and port 65022

---

### Post by ronald.higgins on 2008-04-18
For sharing your resources take a look at Samba,

For accessing your server via ssh you'll need to know the IP address your router is currently assigned, as most ISP assign IP's dynamically take a look at DynDNS, most routers support it and it will register your current IP to a DynDNS domain name so you'll only ever have to connect a a certain domain name. Then of course dont forget to port forward SSH (port 22) on your router to your server ;)

rH

---

### Post by TuckLive on 2008-04-18
How would SSH compare to VPN?  If I configure VPN would that make the outside computer seem as a local host and they could just simply type the IP of the server to get the webpage as I do now and browse the network as a local host would?  What would be the easiest way to access remotely (for my wife :))

I'm just confused on the difference of SSH and VPN and since we are talking about remote access I prefer the more secure way.  I also want to access the music files remotely also.  Thanks for your help.

---

### Post by pseudo-random on 2008-04-18
The best trade-off in terms of usability and security will be the afore mentioned SSH server with Putty client. For secure but slower file transfers you can use winSCP to your SSH server but if you want it faster then use FTP but this isn't secure and I recommend you lock it down to a shared folder rather than your entire drive and have your music etc in that folder.
Once set up it will be as easy as double clicking a desktop icon to explore the remote folder.

---

### Post by HermanAB on 2008-04-18
SSH is a 'VPN on Demand' and is commonly used to administer servers around the world.  It is immensely powerful, yet the basic functions are very easy to use.  For a complete reference on SSH, buy the Snail book.

You can use SSH to log into a remote machine and run text or graphical programs securely.  It does everything VNC or RDP does and more, securely.  

Cheers,

Herman

---

### Post by TuckLive on 2008-04-18
Thanks for the help.

---

### Post by TuckLive on 2008-04-19
Another question I have is that if I run putty and connect to the server hosting the web page how can I open the web page from the command line?

---

### Post by Dr Small on 2008-04-19
You can use a text based browser called w3m, or if you want to edit the webpage, simply use your favorite editor.

---

