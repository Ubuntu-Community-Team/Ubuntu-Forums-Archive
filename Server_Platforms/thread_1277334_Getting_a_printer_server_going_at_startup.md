---
title: "Getting a printer server going at startup"
date: 2009-09-28
forum: Server Platforms
---

### Post by Frodgey on 2009-09-28
I have a desktop version of Jaunty running as I wish.

However other members of my family want to be able to use my printer over our home network.

I don't want them to have a login to my PC.

How can I setup the print server so that it runs without the need to be logged in?

---

### Post by scrooge_74 on 2009-09-28
You just need to tell cups to share the printer and to advertise it, basically all the other PCs will be able to see it and add it. Is kind of magic. 

You can do it manually also, if not mistaken prior versions of Ubuntu did not manage this very well and I ended up doing it over the browser just type localhost:631 and you get the admin page of cups.

I saw 9.04 a few days ago and I saw that it detects the network printers much better than before

---

### Post by Frodgey on 2009-09-29
That is/has been working since I moved away from windows.

However, if I am not around (e.g. at work) and they turn on my computer to be able to print - the printer does not appear on the network.

That is the bit of automation that I am looking for.

I don't want to leave my PC on the whole time.

Thanks

---

### Post by scrooge_74 on 2009-09-29
You need configure it properly first. When you have time get all of the PCs on  and configure yours to properly offer the printer, then go into each one and tell them to look for the printer in the network (in case they havent).

After all of this is done, CUPS in each machine will remember the setting. That way next time they want to print they boot yours and the printer and it should be available. I'm not sure if is just a few secs or mins before the broadcast is sent to the entire network.

Something I did notice is that if one of my kids is using Open Office and they want to print and my PC was not on I had to boot it (plus the printer), then ater it was on they had to go out of Open Office and back in for it to see the printer (no need for user to log off session) 

This is no longer an issue for me since now I have a server and it shares the printer printer with everyone, they just need to power the printer when they want to print something.

---

### Post by Frodgey on 2009-09-30
That does seem to work - thanks.

Although one of the Vista PCs seems querky - but that is his problem!!

---

### Post by scrooge_74 on 2009-09-30
I think I read somewhere Vista gives some issues, I don't remember exactly what needed to be configure since I don't have any Vista PCs.

Glad you got it working

---

