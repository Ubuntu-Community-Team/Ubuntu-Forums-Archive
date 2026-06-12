---
title: "Which Groupware Server?"
date: 2008-05-31
forum: Server Platforms
---

### Post by jrollf on 2008-05-31
I would like to set up a groupware server on my Hardy Server Platform with clients on Vista, Windows XP, and other Ubuntu PCs, and ideally the ability to sync with Pocket PCs (WinMobile 2003 2nd edition) would be desirable as well.  The Windows PC clients don't have to be Outlook, but would be nice.  There will be approximately 5 users.

I'm looking to support calendaring, notes, tasks (toDo's), and e-mail.  The data needs to stay "on the server" so that a client from any of the computers will see the same information.

There seems to be a quite a few choices, any suggestions on which ones are easiest to operate/maintain/setup? 

Thanks,
John

---

### Post by windependence on 2008-05-31
> **jrollf said:**
> I would like to set up a groupware server on my Hardy Server Platform with clients on Vista, Windows XP, and other Ubuntu PCs, and ideally the ability to sync with Pocket PCs (WinMobile 2003 2nd edition) would be desirable as well.  The Windows PC clients don't have to be Outlook, but would be nice.  There will be approximately 5 users.

I'm looking to support calendaring, notes, tasks (toDo's), and e-mail.  The data needs to stay "on the server" so that a client from any of the computers will see the same information.

There seems to be a quite a few choices, any suggestions on which ones are easiest to operate/maintain/setup? 

Thanks,
John

Take a look at Zimbra, or Citadel. I like Zimbra myself, very robust AJAX interface. They have both a paid version and an open source version. Both work extremely well.

-Tim

---

### Post by emilije on 2008-05-31
check out eGroupware

---

### Post by windependence on 2008-05-31
> **emilije said:**
> check out eGroupware
Very good as well. I forgot that one. :)

-Tim

---

### Post by Wizard of Aahz on 2008-06-01
Citadel with Easy Install is a snap to get running. Literally push a button and all the pieces automatically happen. Multiple clients and it's all open source. No functionality that requires payment. It's all one piece. 

It does everything you listed above. 

[www.citadel.org](www.citadel.org)

-Aahz

---

### Post by emilije on 2008-06-01
We conclude and that there are several (more than good) open source options for your purpose. 
Citadel, eGroupware, and so on... are good, but final decision is on you :) 
look at the documentation of every groupware what they offer, are they complicated, free, take look at some screenshots...

---

### Post by jrollf on 2008-06-01
Thanks for all the input.  I'm currently trying Citadel and have it up and running.  I can access it from withing my LAN, but I'm having problems getting to it from across the internet.  I think I'm having a problem with my ATT U-verse router, I can ping the related ports, but when I try to connect to my server, it times out.

I'll have keep working at it!

Thanks everyone

---

### Post by jrollf on 2008-06-02
Citadel seems to be working great.  For some reason I can't access Citadel using my Internet/Public IP Address (ie I can only use my local Lan IP) from any computer on my home network.  But if I'm on a computer elsewhere in the world, it connects great.

Is there anyway to "connect" from a computer on my home network by going across the internet to see how the server behaves on the "public/internet" side.

Thanks,

---

### Post by windependence on 2008-06-02
> **jrollf said:**
> Citadel seems to be working great.  For some reason I can't access Citadel using my Internet/Public IP Address (ie I can only use my local Lan IP) from any computer on my home network.  But if I'm on a computer elsewhere in the world, it connects great.

Is there anyway to "connect" from a computer on my home network by going across the internet to see how the server behaves on the "public/internet" side.

Thanks,

No, you would have to be outside the network to really test it.

The problem you are having though is you cannot access your server inside the network using [www.myserver.com](www.myserver.com) but you can acces it using it's IP sddress. You can solve that by putting an alias in your hosts file like so:

192.168.0.2   [www.myserver.com](www.myserver.com)   myserver

Replace the IP address with the actual address of your server inside your network.

-Tim

---

### Post by Grandma_DOG on 2008-07-01
I'm having to pick groupware for a small company this week. 3 people currently, but they are ramping up to possibly 10 and 6 will be off site.

Any recommendations?  I'm looking at eGroupware right now.

---

### Post by windependence on 2008-07-01
Fortunately, there are lots of great choices out there. Let us know how it goes.

-Tim

---

### Post by jrollf on 2008-07-01
I had Citadel setup and running great after some configuration work with my router.  Then my server's power supply went south and took the motherboard with it ](*,)

R.I.P.  One nearly ten year old computer... Guess I got my milage out of it.

I'm re-building the server and plan to use Citadel again.

See my sig for my new rig!

---

