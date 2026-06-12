---
title: "Need help creating NAS/Print Server"
date: 2008-07-17
forum: Server Platforms
---

### Post by jmedina on 2008-07-17
I have an older Gateway that still works really good and I want to use it as a  NAS and Print server. Here is my long situation. I am going to have a computer upstairs which I am probably going to install a Wireless Card in. I have an ibook which already has a Wi-Fi card in it. I also have an older imac which is going to be downstairs next to the server and I am planning to hard wire it directly into the router. My router is 802.11G and it works good. I also already have a 6 dbi omni directional high gain antenna. Can I use Ubuntu Server with it? I was thinking maybe I should wait for Ubuntu Home Server to be released, but that probably wont be released for a long time. Also, did I leave anything out. Do I need to purchase anymore equipment? How should I start putting the whole network together? I am looking to do this within the next few months.

---

### Post by cariboo on 2008-07-18
If you are only going to use the computer as a print server and nas, there really is no need to install the server package as it will add apache2,mysql and php. The only package you will really need that isn't installed by defaut is samba and depending on the macs appletalk.
So find a really lightweight distribution install it, configure your printer, add some hard drives and your ready to go.

Jim

---

### Post by jmedina on 2008-07-18
Thanks! Should I wait for Ubuntu Home Server? Should I use Free NAS or stick with ubuntu server? Maybe I should go with Xubuntu.

---

### Post by jmedina on 2008-07-24
Am I missing anything? I have a router,ethernet cords,server,power cords. Do I need to buy a switch or anything like that? Does this website look helpful:[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

---

### Post by cariboo on 2008-07-25
it looks like you got everything you need. As to the web site for a step by step setup the web site doesn't look to bad. If you follow it exactly you should be up and running in no time.

If there are any problems, just come bacj here and we will help you resovle any problems.

Jim

---

### Post by TurboRush on 2008-07-25
Depending on how much of a challenge you want, there are a few Linux based OS' designed for NAS. I've never used any of them so I can't comment on the print portion of your request.

Some of them are Naslite, FreeNAS, ClarkConnect. However, openfiler looks pretty good ([http:///www.openfiler.com](http:///www.openfiler.com)) and ClarkConnect got some positive feedback for ease of use.

Again, I don't have any direct experience but have started doing some research over the past day or so because I'd like to get something similar running in my house.

---

### Post by Krupski on 2008-07-25
> **cariboo907 said:**
> If you are only going to use the computer as a print server and nas, there really is no need to install the server package as it will add apache2,mysql and php. 

Not really true. Ubuntu Server ASKS which packages you want to install.

For a machine as the OP wished to build, all he would need is Samba, CUPS and SSH (for remote administration).

I've built several NAS boxes just like this (minus the print server though) and Ubuntu Server works *just fine*.

There's no need to "wait" for anything to come out.

Only thing is... one better be comfortable at the command line, 'cause there's no GUI in Server.

-- Roger

---

