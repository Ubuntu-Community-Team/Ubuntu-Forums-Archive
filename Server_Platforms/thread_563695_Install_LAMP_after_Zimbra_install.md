---
title: "Install LAMP after Zimbra install"
date: 2007-09-30
forum: Server Platforms
---

### Post by scsever on 2007-09-30
I have installed Zimbra Server on Ubuntu Feisty and is working fine.  I now want to install LAMP but I am a little concerned about breaking my Zimbra setup so looking for advice before starting.  
**Here is some information and concerns:**
This is not a production machine, I am installing and running this to gain knowledge/experience.
I have next to no web server experience.
My vision is that when someone in my LAN points to the server they will see a home page that will include a link to my Zimbra server.
I am concerned about LAMP configuration causing conflicts with Tomcat configuration.  Should I be?
I can get to Zimbra by pointing my browser to my server IP.  Will that change after a LAMP install and if so how can I fix it?
I have seen people suggest to run Tomcat within Apache2 using a mod_jk module.  Any tips/suggestions about that idea?

Thanks,
Steve

---

### Post by Brazen on 2007-09-30
The one thing I hate about Zimbra, is it installs it's own modified version of dependant applications, including apache.  Zimbra's modified Apache and the Apache installed from the Ubuntu repository might cause conflicts with each other.  As such, I would highly suggest using your Zimbra server for nothing but Zimbra.  Install a second server (you can save hardware using virtual machines on Virtual Box) to use as your front end web server and link to your Zimbra machine.

---

### Post by jimbo99 on 2007-10-17
> **scsever said:**
> I have installed Zimbra Server on Ubuntu Feisty and is working fine.  I now want to install LAMP but I am a little concerned about breaking my Zimbra setup so looking for advice before starting.  
**Here is some information and concerns:**
This is not a production machine, I am installing and running this to gain knowledge/experience.
I have next to no web server experience.
My vision is that when someone in my LAN points to the server they will see a home page that will include a link to my Zimbra server.
I am concerned about LAMP configuration causing conflicts with Tomcat configuration.  Should I be?
I can get to Zimbra by pointing my browser to my server IP.  Will that change after a LAMP install and if so how can I fix it?
I have seen people suggest to run Tomcat within Apache2 using a mod_jk module.  Any tips/suggestions about that idea?

Thanks,
Steve

I have found the only guides for installing Zimbra to be vague and confusing at best.  Do you have a good guide or a solid way in which to get this done with as few steps as possible?

I need to get this set up and working and working reliably.  I see guides for prior versions of ubuntu but none for feisty fawn.  I think it will only get more confusing when the time comes to upgrade to the 7.10 version.

There are many confusing statements in the guides I've seen and some assume certain knowledge.  I'm sure someone has a guide that does every step outlined that tells exactly what to type letter for letter since it should be the same for ever single solitary ubuntu feisty fawn install (except servernames, ips, etc.).

Anyway, after much frustration I am glad to see you have it installed but could use a pointer to a solid guide geared for feisty fawn instead of to the older versions.

---

### Post by reckless2k2 on 2007-10-17
i have this setup on my machine and it's not hard to do. in the zimbra wiki they talk about running apache and zimbra as well and such. for instance, i just run zimbra only on https so it doesn't conflict with apache on 80. starting to get the idea?

they have ways to run on the same port as well with stuff. it's not difficult to understand. it's right in the zimbra wiki.

---

### Post by KCPokes on 2007-10-17
As Reckless stated, you can do it following the instuctions on the Zimbra Wiki.  Another option to consider is setting up a virtual IP on your box and binding Zimbra components to one IP (which they have a HOW-TO in their Wiki) while binding your LAMP components to the second IP.

---

