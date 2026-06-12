---
title: "firewall blocking torrents:|"
date: 2006-06-10
forum: Server Platforms
---

### Post by raffytaffy on 2006-06-10
Im have firestarter instaled as the gui for iptables..all of a sudden im getting events on port 6881 (bittorrent) and none of my torrents are d/ling..how do i open port 6881-6889. i looked and looked and cant find an answer

---

### Post by Azrael on 2006-06-11
FTFM: "Select the Policy page, right click on   the list marked *Forward service* and select *Add rule*. You will be presented   with a dialog for creating a new policy rule. Select BitTorrent from the service drop-down,   fill in the IP of the client and you're done. Click the *Apply Policy* button to   apply the changes."

PS: Unless you installed unreliable networking software on your machine I think it is pretty pointles to run a personal firewall in Ubuntu (I see no need for a block by default rule when ports are already closed).

---

### Post by JARofHERB on 2006-06-23
raffytaffy, I wouldnt even use ports 6881-6889. Almost all Isp's monitor thoes ports for traffic, and not to mention who they might pass that info too!! Anyhow use ports 50000-60000 for torrent traffic, its much safer,, peace out!

---

### Post by njzillest on 2006-06-28
really? I didnt know that lol. Thanks for the information


RaffyTaffy, are you from Wardlaw Hartridge, because i Know a kid with the name Raffy from there lol

---

### Post by MJN on 2006-06-29
[quote=JARofHERB]raffytaffy, I wouldnt even use ports 6881-6889. Almost all Isp's monitor thoes ports for traffic, and not to mention who they might pass that info too!! Anyhow use ports 50000-60000 for torrent traffic, its much safer,, peace out![/quote]

If you think torrent traffic can be hidden from your ISP by moving the ports you're very much mistaken.

Besides which, why try and hide it if all your downloads are legal? ;)

Mathew

---

### Post by DavidFL on 2006-07-11
> **MJN said:**
> If you think torrent traffic can be hidden from your ISP by moving the ports you're very much mistaken.

Besides which, why try and hide it if all your downloads are legal? ;)

Mathew

Sometimes it isn't your ISP rather it is others who will block certain ports, even outbound. As such sometimes I will set bittorrent to listen on port 21 (ftp) or port (80).  So in that case it more looks like the other guy is just contacting a FTP or web server.  I suspect it might also help with basic traffic shaping as well.

You are very right though that there are other ways to analyze and shape traffic other than relying strictly on the port number.

---

