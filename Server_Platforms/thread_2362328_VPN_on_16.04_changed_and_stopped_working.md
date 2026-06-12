---
title: "VPN on 16.04 changed and stopped working"
date: 2017-05-26
forum: Server Platforms
---

### Post by absolutezer02 on 2017-05-26
Since buying a VPN service I wanted to make some profiles I can activate  on my Laptop, but I ran into issues, always saying that the connection  couldn't be established and my "Configure VPN ..." button was always  gray and couldn't be pressed. After reinstalling Ubuntu I was able to  fix that, the button worked and I was able to connect to a server. After  a few days, I wanted to add a new profile, but suddenly I ran into the  same problem, grayed out button and when I add a PPTP I get the same  error as before... Strangely, I am still able to connect to the previous  setup I made... Can anyone please somehow explain me why there is such a  "bug"?

---

### Post by wildmanne39 on 2017-05-26
*Thread moved to **Server Platforms**.*

---

### Post by absolutezer02 on 2017-05-28
[http://paste.ubuntu.com/24693480/](http://paste.ubuntu.com/24693480/)
Here are results of the Wireless Script.
Sorry I haven't done it before, didn't know about it. I will keep it in mind for the future.

---

### Post by darkod on 2017-05-28
How about if you click the Network Manager icon, then Edit Connections - Add. Does that allow you adding new VPN connection?

On my desktop the Cinfigure VPN is also gray, but I can add new connection in Edit Connections.

In fact I believe that is how you should be adding connections, the Configure VPN might be something else.

---

### Post by absolutezer02 on 2017-05-28
Well, that's how I added my new connection. The adding part isn't  problem. But whenever I try to connect to the new ones, it fails. I would have thought if it was bcs of the VPN service, but it has worked and on a friends PC, which runs 14.04 LTS it works right away!

---

### Post by darkod on 2017-05-28
Have you looked at the logs? I guess there should be some info in /var/log/syslog regarding the issue it is preventing it to connect.

I can't help too much since I rarely use PPTP VPN, I usually use only OpenVPN. And connections for it are created in a different way.

One way or another you need to find some error messages and then use that to google around. Unfortunately just saying vpn doesn't connect doesn't help much... It could be DNS issue, routing issue, vpn issue, etc...

If this is the same vpn service you are talking about (only one service), what kind of different profiles do you need? Maybe that is creating the problem? For one service it is usually eanough one connections to be working, and according to you you do have one connection that is working.

---

