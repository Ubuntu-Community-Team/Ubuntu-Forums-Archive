---
title: "wut 2 do with old laptop"
date: 2006-12-25
forum: The Cafe
---

### Post by sailingboarder on 2006-12-25
so xmas came, and i got a new laptop (yea!), and though it has xp now(sux major @$$), will soon have ubuntu desktop

i still have my old IBM thinkpad (bout 6 years old now), and am thinking of changing it from ubuntu desktop to ubuntu server

wut i am asking, is would this laptop be able to run server(nothing major) and if so, wut type of server would u all recommend
i've thought about a making a file server to share music with the whole family, or maybe play around with a web server or something like that

basically, i'm going to use this more as a learning experience, but would still like to have something useful

wut r your suggestions?

---

### Post by John Fury on 2006-12-25
Well all I have is an old IBM thinkpad A20m. I'd assume it's about the same age as yours. It's running ubuntu Edgy Eft and it runs great. I have no idea how to make it a server but I'd use it as a web server so I could host websites.

---

### Post by PatrickMay16 on 2006-12-25
I don't think it would make a useful server. If I were you, I'd just give it to a friend or sell it on ebay.

---

### Post by sailingboarder on 2006-12-25
I don't need it to be a full fledged, professional grade server by any means

i'm just looking for something to play around with and maybe have it useful for me

basically i'm asking file server vs. webserver vs. some other type of server, which one would you recommend

---

### Post by sweemeng on 2006-12-25
plug you nic to a switch setup the iptables a little, the you got your self a firewall.
or turn it into a wireless access point(a little easier on the hardware side, but harder in software side)

---

### Post by sailingboarder on 2006-12-25
what would a wireless access point do for me?

---

### Post by Frak on 2006-12-25
I see no reason why you couldn't make a server with it, it should have more than enough specs for your intended/implied use.

---

### Post by zanglang on 2006-12-26
Why not? Depending on your needs you could:
- Put Firefly or Tangerine or Shoutcast on it to stream music to other computers
- Set up Apache, Rails or anything you'd like to learn web development on
- Set it up as a software router with DHCP, firewall, and maybe as a wireless access point
- Headless bittorrent with FTP access to your downloads
and so on and so forth... Just a few ideas.

---

### Post by sailingboarder on 2006-12-30
those are some good ideas, thanks

still not sure what a wireless access point is...could someone please explain that to me?

---

### Post by raul_ on 2006-12-30
You can always ship it to me. ..

---

### Post by zanglang on 2006-12-31
[http://www.answers.com/main/ntquery?s=access+point](http://www.answers.com/main/ntquery?s=access+point) ;)

Basically, it's the machine your laptop connects to via wifi for access to the wireless network.

---

### Post by viciouslime on 2006-12-31
> **raul_ said:**
> You can always ship it to me. ..

:p lol

---

### Post by sailingboarder on 2006-12-31
since we already have a wireless router, i don't really need a wireless access point

and my old computer does not have a lot of memory(40 gigs with an external usb hard drive, 8 gigs on the comp), so i don't think it's going to make the best file server

so i'm thinking about going with a webserver, just to sorta play around

i know that i can do all the stuff and view it as a localhost, but if i wanted other people, like friends and such, to be able to access my website(s), what would i have to do?

like dhcp, dns, register a domain, etc.
i know html and stuff like that, but i don't know the administrative side of a webserver, like how to get access to it from outside the network

could someone explain what i would need/ have to do if i wanted to run a webserver on my comp and have ppl be able to access it

---

### Post by BigDave708 on 2006-12-31
I'm currently making a Debian webserver to host, well, whatever I want.

Just try Googling it and you'll find plenty of resources.

---

### Post by yoshida on 2006-12-31
First of all you could install 6.10 server as LAMP. Second, you need to set port forwarding on the router. Third and last: buy a domain name for your ip address. A pall of mine is doing it too, on a 850mhz laptop, and he installed fluxbox (with xdm, not gdm) on the machine. Still runs like a pretty sweet desktop machine, regardless of server capacaties.

---

### Post by Stone123 on 2006-12-31
[http://www.grynx.com/projects/laptop-on-the-wall-walltop/]("http://www.grynx.com/projects/laptop-on-the-wall-walltop/")

Did this one my self too, now its in the junk. But a good idea to have wlan there . 
Ideas :

- Digital  Image Frame (i had debian potato on 486 )
- Streaming media server. Radio , music. (mythtv) , you need pcmcia remote or usb. 
- Arcade machine .  Xmame +mythtv [http://www.mame-arcade.fr/index_en.html]("http://www.mame-arcade.fr/index_en.html")

---

### Post by RandomJoe on 2006-12-31
What kind of Internet connection do you have?  To do a world-accessible web server properly, you need to have an IP that everyone can reach via port 80, but if you are running off of a typical residential cable/DSL/whatever connection odds are port 80 is blocked.  You can try running the server on a different port, but most residential contracts stipulate "no servers".  For the most part, this is usually overlooked unless/until you start becoming popular or just pushing a lot of data, but it is a point they could potentially use to shut down your connection.

You could change your contract to a fixed IP / servers allowed one, which would then let you do whatever you want, but those are usually considered "business" and come with a higher price tag.  If you do this, then register a domain name and such and you're in business.  (Or just give your friends the IP!)

That said, I have some things set up on my residential cable connection, and just use DynDNS to provide a domain name to access it in case the IP changes (I run a small script to notify DynDNS of the IP on my firewall computer, or some cable/DSL routers can do so for you) and use odd ports.  I'm not trying to be public-accessible, though, just lets me get access remotely, so I pretty much just do OpenVPN and SSH.  Once I have a VPN connection, I have full access to everything on my servers.

---

### Post by sanderella on 2006-12-31
Give it to the Salvation Army. They'll service it and send it to Africa for poor kids.:)

---

### Post by sailingboarder on 2006-12-31
i have earthlink dsl
does anyone know it's policies towards port blocking/servers?

---

