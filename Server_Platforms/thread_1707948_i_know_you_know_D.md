---
title: "i know you know :D"
date: 2011-03-16
forum: Server Platforms
---

### Post by zachery on 2011-03-16
ok guys i got my apache2 server all setup and what not but how do i set  it up so that other people can access it? I know i need a domain name  but i tryed to register for a cc.co and it wouldnt let me use my ip  address so im not sure how to go about it :sad:

any help would be awesome!


thanks!

---

### Post by garfonzo on 2011-03-16
If you can see your webpage from your LAN (you get the wonderful "It Works!" page) then do this:

[LIST=1]
[*]Buy your domain name.cc.co or whatever you wanted
[*]From that domain name registrar, you have to setup a DNS record so that your_domain.com will point to the IP address of your modem. Presumably your ISP will provide you with a static IP, or you are paying for that option. You will log into your domain account and setup an "A record" which points to your static IP address.
[*]Setup the router so that all incoming requests on port 80 are sent to the IP address of your server (192.168.XYZ.ABC)
[/LIST]

---

