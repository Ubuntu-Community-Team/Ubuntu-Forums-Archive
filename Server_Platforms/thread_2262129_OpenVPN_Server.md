---
title: "OpenVPN Server"
date: 2015-01-23
forum: Server Platforms
---

### Post by Fleckens on 2015-01-23
Hi,

I'm kind of new to the "Ubuntu Scene" and searched a lot for the answers on my questions on the internet, but couldn't find them. I'm dealing with the problem that I want to setup a(n) (open)vpn server on an ubuntu server and sell/give out the clients. What I want to do is add multiple geo-locations to it and (auto)make multiple log-ins. My problem is that I can't find a way to set this up and find what the best setup is for this kind of server because I want to invest some money in a dedicated server to make this work. So my question is if anybody could explain this to me;

- Adding Geo-locations/IP's through OpenVPN
- Setting it up on a server
- Best (Ubuntu) Setup (specifications/ram etc. what I got to look for)

I hope anyone could help me out.

I'm new to this forum so please tell me if I've placed this subject in the wrong subforum.

Kind regards,

Fleckens.

---

### Post by volkswagner on 2015-01-24
[OpenVPN.net]("http://openvpn.net/index.php/access-server/docs/admin-guides-sp-859543150.html") has excellent tutorials for setting up server and client.

I'm not sure what you mean by "Adding Geo-locations/IP's through OpenVPN".

You asked "Best (Ubuntu) Setup (specifications/ram etc. what I got to look for)"
How many concurrent users do you expect to have? How many clients do you expect (10's, 100's, 1,000's)?
What type of bandwidth will be available to the server up/down speed?
I'm no expert but unless you have a gigabit WAN pipe, you can do this without high-end hardware.
I assume your WAN pipe will be the limiting factor on scalability if you choose an energy efficient Celeron with 8gigs of RAM and a well supported ethernet card(s).
What type of connection will you be offering? Are you going to have the clients redirect the gateway to your server?

Here is an [interesting thread]("http://serverfault.com/questions/439848/openvpn-performance-how-many-concurrent-clients-are-possible") that has some useful info.

---

