---
title: "non static ip problem caused by provider"
date: 2007-01-14
forum: Server Platforms
---

### Post by damichi84 on 2007-01-14
I want to access my unbuntu server from outside my homenetwork the problem is my global ip changes because of the restrictions of my provider. It reconnects every 24 hours and changes the global ip. Is there a possibiltiy to grab that ip and email it tomyself or load it up to another external ftp or sth? I can acces the new Ip address by the control panel of my router (WRT 54 G)
[http://110.110.110.254/Status_Router.asp](http://110.110.110.254/Status_Router.asp)

maybe I can dowload that side automatically and email it?

THX 4 your help

---

### Post by chrisfay on 2007-01-14
I'd recommend signing up a free account with zoneedit.com for dynamic dns and configuring ddclient on your server to update the account whenever your IP changes.  I personally use their services to host around 15 domains on a dynamic IP and it works flawlessly updating all zones anytime my IP changes. The first five domains are free fyi....

---

