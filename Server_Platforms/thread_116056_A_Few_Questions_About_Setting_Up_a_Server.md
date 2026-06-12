---
title: "A Few Questions About Setting Up a Server"
date: 2006-01-11
forum: Server Platforms
---

### Post by noob_Lance on 2006-01-11
Hey,
i am wanting to set up a server, with Web, FTP, and Mail. How Hard Will This be to do behind a router. second of all... i dont want to use any dns service, will i still be able to set up a mail server? i know with ftp and web it wont. 

Any Info on that is appreciated :) thanks :)

~Lance

---

### Post by srt4play on 2006-01-11
You can set up any kind of server you want as long as you forward the apporpriate ports in the router.  Just access via IP address.

---

### Post by spade_shark on 2006-01-12
> ...Web, FTP, and Mail. How Hard Will This be to do behind a router 
Not any harder than setting it up in front of a router :)  A router will forward all traffic by it nature, that is what it does.  BUT a server behind a router leaves all ports exposed to the outside WAN (Internet), not the right way.  If I may, and what you may already have an mean to ask, put a firewall infront of the server - behind the router, or put a software firewall on the server.  The end goal is just to open several ports to the WAN: (web 80, 443; ftp 21; mail 110,25,143, etc).

> i dont want to use any dns service, will i still be able to set up a mail server? i know with ftp and web it wont.  If you don't do DNS you will not have mail.  Period...no dns records=no mail.  That doesn't mean you couldn't pay $5.00 US /yr for a hosting company to host your dns and therefore *you've got mail*.  DNS is just as easy to do as the other services are.  Good Luck.  Ask around here for help.  Too, please be more specific on your questions and we can give you more specific answers.

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=spade_shark]Not any harder than setting it up in front of a router :)[/quote]Not if it does NAT.  That makes FTP nearly impossible to do right, unless the router does FTP proxying.

 > BUT a server behind a router leaves all ports exposed to the outside WAN (Internet), not the right way.I've yet to see a consumer router that does this because they *all* do NAT.  In fact, most of them don't even allow you to shut it off.  I've seen very few that do, and those that do allow it only for wireless bridge operation.

> The end goal is just to open several ports to the WAN: (web 80, 443; ftp 21; mail 110,25,143, etc).You have to open many more ports for FTP.

My recommendation would be to avoid FTP anyway and use SFTP, unless you have a very strong reason not to.  For starters, it's easy to forward across NAT.

---

### Post by noob_Lance on 2006-01-12
hm... well mail will have to wait a bit then lol.. as for web and ftp... i can still do... how do i make it sftp tho?? Mohawk college (my school) uses it on there red hat server... but i got no clue how they got set it up.. anything?

~Lance

---

### Post by LordHunter317 on 2006-01-12
You install and forward sshd.  SFTP is a part of the SSH protocol.

If you have people you want to allow SFTP only, install rssh(1) and it will allow you to limit them.

---

### Post by az on 2006-01-12
[QUOTE=noob_Lance]hm... well mail will have to wait a bit then lol.. 
~Lance[/QUOTE]
Maybe you need a dynamic DNS?

Dyndns.org offer a mail-hop service (you need to pay for it - I forget how much it is.  It's not that much) which allows you to use dynamic dns for mail.

I don't know the specifics of what your needs are but maybe that helps.

---

### Post by noob_Lance on 2006-01-12
The limit people connecting... yes that would work... as i am going to let a few people access it, mainly it will only be myself. I have a few friends who want custom hosting so im gunna set up a server to host. the ftp.. they will get limitations.. but myself i will give myself full access.. 

As for mail... well i cant afford anything... i just droped about 320$ on textbooks in the last 3 days.. so a payed service it out of the picutre for now lol. unless... would it work with no-ip.com??

---

### Post by MJN on 2006-01-13
For your DNS I can highly recommended [www.zoneedit.com]("http://www.zoneedit.com") - it works well, is easy to use, and it's free (for upto 5 domains). It works extremely well if you've got a dynamic IP address - I use the simple python script Zoneclient ([zoneclient.sourceforge.net]("http://zoneclient.sourceforge.net/")) that runs every hour to update the DNS if necessary.

Zoneedit also provide additional services at a notional cost such as backup mail servers, additional name servers etc (although I don't consider either of these necessary).

I recommend taking a look.

Mathew

P.S. My first post here - woohoo! :D

---

