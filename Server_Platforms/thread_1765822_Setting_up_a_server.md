---
title: "Setting up a server"
date: 2011-05-23
forum: Server Platforms
---

### Post by Gr72 on 2011-05-23
Hello,
I am a partial newb to linux as well as networking. I tried setting up my own server before but could not understand port forwarding. So I used hamtachi to set up my server and run it. could someone explain ho to set up prt forwarding when you have an IP from an ISP? Thank You soo much.

---

### Post by arrrghhh on 2011-05-23
> **Gr72 said:**
> Hello,
I am a partial newb to linux as well as networking. I tried setting up my own server before but could not understand port forwarding. So I used hamtachi to set up my server and run it. could someone explain ho to set up prt forwarding when you have an IP from an ISP? Thank You soo much.

Port forwarding is done on your router, not your server...

So go to [www.portforward.com](www.portforward.com), find your router make/model and they should have a walkthru on how to setup port forwarding on your router...

Assuming your server is vanilla, it doesn't have a firewall activated - so there's no need to change anything on the server.  However, I recommend enabling the firewall to ensure only the traffic you want going into the box actually gets there, and unwanted traffic is blocked/filtered.

---

### Post by papibe on 2011-05-23
There are several things you need to do to make it work, and that implies understanding several concepts like static vs. dynamic IP addreses, DNS, etc.

This is a [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.

---

### Post by Gr72 on 2011-05-23
Thanks Guys for your replies, so I guess I should have told you guys that I know the port forwarding is done within the router, and I understand static and dynamic IP's, I had already made a forward on my NetGear Router, but the problem was noone could connect to it, even when I had my server running, I could connect to it but anyone outside of my LAN couldn't.

---

### Post by Gr72 on 2011-05-23
ok, I watched your video Papide and it makes a little more sense, but do you have to have dyndns client or something similar?

---

### Post by papibe on 2011-05-24
> **Gr72 said:**
> ...but do you have to have dyndns client or something similar?
Yes. The good news it is on the repositories, and you can install it using apt-get. It's called ddclient. The installation process will ask for all the Dyndns data, so you first have to create your account and domain (all free).

There's an alternative. Some routers have an integrated dynamic DNS client. That would be not only easiest but a bit more efficient.

Note that in the case of Ubuntu (all Linux really), just by installing openssh server, you'll have both remote access and file services (using sftp). For the last one you can use graphical clients, like Filezila both in Windows and Ubuntu, WinSCP for Windows (I recommend this one), or the multiplataform FireFTP add-on for Firefox. 

Good Luck!

---

### Post by garycahill on 2011-05-24
Very nice tip, I hadn't heard of ddclient before.

Gary

---

### Post by Off Topic on 2011-05-24
I use a static IP from my ISP,  its an extra charge as normally my ISP uses dynamic IPs.  Right now the $10 a month is a bit much but it makes things easier for me,  no extra software,  no extra configuring.  If I need to access my server its an IP address away.

---

### Post by arrrghhh on 2011-05-24
> **Off Topic said:**
> I use a static IP from my ISP,  its an extra charge as normally my ISP uses dynamic IPs.  Right now the $10 a month is a bit much but it makes things easier for me,  no extra software,  no extra configuring.  If I need to access my server its an IP address away.

Hence why so many people use Dyndns.  I'm too cheap to pay for a static IP, and this way I only need to remember the domain - no need to memorize the IP.

I think you'll find whenever your ISP goes to IPv6 it's going to be very difficult to do what you're doing :p.

---

