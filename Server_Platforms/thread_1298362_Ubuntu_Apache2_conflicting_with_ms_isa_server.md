---
title: "Ubuntu Apache2 conflicting with ms isa server"
date: 2009-10-22
forum: Server Platforms
---

### Post by nathan2k on 2009-10-22
Hello,

I have setup a old dell poweredge server to with Ubuntu 9 Desktop LTS. The aim of the server is to host a basic website. It is just a one page site http site and all is working on the server with apcahe2. We have used port 808 as port 80 was taken. The machine has a static ip and other machines in the office can see the website.

However the office internet runs through a server with 2003 sbs with ISA server. This server also runs Microsoft SharePoint on port 80. It also runs remote desktop. ISA is the firewall for the office. People in the office access share point with a diffenernt domain name that I am using. There is no port forwarding setup in our adsl modem as ISA is handling it.

I have published the our static ip to our domain name. When we ping our domain we get our staic ip. However the page displayed is 403 isa server fobidend.

I have read on a isa server forum to create a web publishing rule and bridge to port 808 to the ubuntu machine. We have done this and get the 403 message still.

Can isa fireware talk to a linux box. Does apcahe need any extra settings to talk to the sbs server. Can isa server web publising rule work with an ubuntu apcahe2 server?

I have asked on the isa server forums but no one there knows about apache or ubuntu.

Nathan

---

