---
title: "dyndns behind a router"
date: 2007-08-02
forum: Server Platforms
---

### Post by infinitezero on 2007-08-02
Has anyone had any issues with dyndns behind a router or is there any extra configing (I know that is not word, but hey) that needs to be done.





Thanks,
iz

---

### Post by Mr. C. on 2007-08-03
Are you actually experiencing a problem, or just probing ?  If you could refine your question a bit more, it might help.

MrC

---

### Post by infinitezero on 2007-08-03
I am probing at the moment. I will be setting up a network in the very near future and will need a service that provides Dynamic IP Updating. I just want to make sure the software that updates IP will work behind a router.


Thanks,
iz

---

### Post by Nuverde on 2007-08-03
I have used dyndns.org with a network that is behind a linksys router in the past.  There are a few scripts/programs out there that will either get the real world IP from the router itself or by bouncing off of an external web server.  Most of them also work with dyndns.org to keep the IP up to date automagically.  Some of these will run as services and some you can set up as cron jobs.  Sorry I don't have any specific names right now, but I know they are out there.   But my point is that you should have no problems with this type of setup.  I would just google for dyndns, linux and your router name.

---

### Post by Viruk on 2007-08-03
I can't see that you'll have a problem with this. 

You'll need to port forward on the router so that incoming traffic is passed to the relevant server. 

The updates to your IP will be sent out of your system to dyndns so you shouldn't have any problems there either. 

I use a modem/router in half bridge mode and have a smoothwall as my firewall. Smoothwall has a section for dyndns and it pretty much takes care of it all. The last thing I do is forward the required port to the required server in my DMZ and it all works nicely. 

The only time you may need to do anything is if your IP stays the same for over a month, then you occasionally have to "force" the update - a click of a button in the smoothwall interface but I'm not sure how other software deals with this as I've never needed anything else.

---

### Post by infinitezero on 2007-08-03
Thanks for the info, that is the feedback I was after.


Thanks,
iz

---

### Post by perspectoff on 2007-08-03
Make sure the ddclient package or ipcheck package are installed.

For more info, see the UbuntuGuide at:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

