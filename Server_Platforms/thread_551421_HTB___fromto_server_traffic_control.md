---
title: "HTB  : from/to server traffic control"
date: 2007-09-15
forum: Server Platforms
---

### Post by IdealVithVodka on 2007-09-15
Hi,


I have a simple and at the same time complicated problem.
I can control the bandwidth of my users via htb. But I can't control the bandwidth of my server. I have an application running on it (bittorrent daemon). I would like to limit that applications download - I have tried layer7 but seems that my htb rules are wrong. 

Any idea how to control the traffic from server to internet ?




With Kind Regards
Matt

---

### Post by gombadi on 2007-09-15
Not sure what bittorrent client you are using but both rtorrent and bittornado have the ability to set upload and download rate limits.

Both are just an apt-get away :)

---

### Post by IdealVithVodka on 2007-09-16
HI,


Thanks for the reply.

I'm using bitflu

I want people from my house to be able to download any torrents they want. Bitflu  has a web gui so its easy for them to use.
I have setup samba to make it easier to exchange the files over my home network. That is why I need to "catch" bitflu packets somehow and force them to go somewhere where I can control them via htb.

Unless you know a bittorrent client that has web interface and is easy to setup.

Or just a script how to control the server traffic



--regards
MAtt

---

### Post by cypresstwist on 2008-06-16
Now, with [WebHTB]("http://www.mylro.org/content/view/929/57/") you can apply rules and do trafic shaping as you please, through a cool-looking AJAX-based web interface. Adding and deleting clients can be done in just a few clicks. Trafic shaping can be done with both public and private IP addresses.

---

