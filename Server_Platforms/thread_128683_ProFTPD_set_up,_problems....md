---
title: "ProFTPD set up, problems..."
date: 2006-02-12
forum: Server Platforms
---

### Post by wilsonisme on 2006-02-12
Problem fixed - thanks guys!

---

### Post by simon_is_learning on 2006-02-12
I think that you must set up Port-forwarding in the firewall (if you have any)

On my server it's called "Virtual Server". There you have to choose which IP that has the FTP-server so when you connect to your IP given to you by your ISP. The virtual server translates your local IP (192.168.1.102) to your official IP

And it's also so that when somebody else is connecting to youre server. It's safer (I think) to use an FTP-client. The client lets them fill in the IP, username and password.

If they're using Windows. SmartFTP is an option.

---

### Post by wilsonisme on 2006-02-12
I already have that though... "MasqueradeAddress 67.164.97.204"
and my router is set to forward the port needed. But is there a way I can set it up so someone in IE is prompted for user name and password, without having to install extra software? :-?

---

### Post by wilsonisme on 2006-02-12
Okay I got it to work inside and outside my house! Yay! I would like to know if it would be possible to use a web browser as a client though? A lot of time I would need to use the server, installing software (ftp client) would not be an option :(

---

### Post by Hanj on 2006-02-12
wilsonisme, how did you make it work? I have exactly the same problem. I can connect to my ftp server from a computer in the local network (for instance by entering [ftp://192.168.0.3](ftp://192.168.0.3) in a webbrowser), but when I try to do the same from outside the network it's unable to connect. I have a Di-604 router and I have set it up to forward port 21.

---

### Post by simon_is_learning on 2006-02-12
well yes, I know it works in Internet explorer anyway.

just type ftp://"IP-ADDRESS PROVIDED BY ISP"

e.g.

[ftp://192.168.0.101](ftp://192.168.0.101)
[ftp://201.202.91.143](ftp://201.202.91.143)

Hanj:

Do you connect to your internal or external IP??

---

### Post by Hanj on 2006-02-12
> Do you connect to your internal or external IP??When I connect to my internal IP it works, but not when I connect to my external. Even though I have set up port forwarding.

---

### Post by wilsonisme on 2006-02-12
I made it work by forwarding the passive ports too, dunno if that even mattered. Then on the computers outside my network I just used a regular FTP client, provided my ISP IP, port, username, password, and it worked without a hitch, permsissions too.
Also "MasqueradeAddress -your external ip-" is important if you are behind a NAT I believe.

---

### Post by Hanj on 2006-02-13
Well, it doesn't work for me. I tried changing port on ProFTPD, and now I get this far (using FileZilla):
Status:	Connecting to x.x.x.x:2021 ...
Status:	Connected with x.x.x.x:2021. Waiting for welcome message...
Response:	220 ProFTPD 1.2.10 Server (Vladimir) [192.168.0.3]
Command:	USER anonymous
Error:	Timeout detected!
Error:	Unable to connect!

If I connect directly to 192.168.0.3 it works fine. Any clues?

---

### Post by steve_250 on 2006-02-14
Alas, I am still having the same problem.
I used to be able to ftp in from INSIDE my house but not from outside my home net.
I do have the ports forwarded in the router.

At the moment, in GFTP it sits there and says "Receiving file names".
Won't get the names...
This is another problem in addition to the first one (above).

---

