---
title: "Nagios and Postfix"
date: 2012-02-07
forum: Server Platforms
---

### Post by cryptoparrot on 2012-02-07
Hi Everyone,

I'm fairly new to the world of Linux - so bear with me. 

I've installed and conifgured Nagios on my Ubuntu box and everything is working fine, it's monitoring my windows boxes perfectly. 

I'm trying to setup Postfix for the E-mail notifications and I can't get it to work (I tested by killing explorer.exe on my windows box). 

In Nagios I've defined 2 contacts and added them to the Nagios Admin group. 
The explorer service is set to notify these 2 contacts (If I click on Notifications in the GUI you can see it's returning messages saying we should have been notified)

The problem must lay with my Postfix installation but I'm not sure where to troubleshoot it and I'm not too clued up on the config depite reading the documentation. Ideally I want to send my message through my Exchange providers SMTP site. I'm very unsure on the settings for domains, destinations, relay hosts etc... 

I'm willing to start again with Postfix, can I just --purge it and start from scratch? 

Thanks

---

### Post by cryptoparrot on 2012-02-08
Just to be a bit more specific: 

I've found out I can't use my Exchange server anymore (It's hosted externally and they won't allow mail relay). Can I set Postfix up to send straight from the Ubuntu machine? I literally only need it for Nagios notifications, nothing will be incoming...

I was also a little confused as to what I should put for my hostname - if I hostname -f I just get 'nagios' returned. 

Thanks

---

