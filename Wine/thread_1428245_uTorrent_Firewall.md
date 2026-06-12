---
title: "uTorrent Firewall?"
date: 2010-03-12
forum: Wine
---

### Post by grnorris on 2010-03-12
First off, this is my first post here and since I'm not to well known yet I feel I should warn you that I ramble a bit.  If someone wishes to clarify/simplify my post please do.

I've been using uTorrent on Ubuntu for probably a month in combination with Your-Freedom (your-freedom.net) without any issues but recently it's started telling me that I'm behind a firewall and uTorrent is limited (and instead of 30Kb/s d-load I'm getting 10).  I paid for vouchers so I could get the better download speeds on days when I'm stuck in school for 6 hours (well, I'm actually in school 6 hours 4 days a week but there's only a couple days a week I have enough time between classes to recharge my battery).  I've tried other proxies before and found that your-freedom is the only one that can get around the routers and doesn't either limit me to 1kb/s (which might get me some tracker data) or cost me an arm and a leg.

Please note:  The Basic package on Your-Freedom gives you 256 KB/s download but, uTorrent is limited to about 30Kb/s with it (probably has something to do with trackers).  The free version is 56K but actually gives me about 8K.  All aspects of uTorrent have to go through my proxy to work and I won't stop using uTorrent because I have my Ubuntu and Windows copies synchronized.

Edit:  Forgot to mention I've been reading these forums for a while and have used Ubuntu before.  Unfortunately Ubuntu 8 didn't work with my wireless card which is my primary (and pretty much my only) way of connecting to the net.

---

### Post by grnorris on 2010-03-24
It seems my speeds are back to normal (after a few days) but, uTorrent still says something about a firewall.  Any idea's?

---

### Post by Cabs21 on 2010-03-24
you could try port forwarding if you can gain access to the router.  If not then try disabling any firewalls while using uTorrent.

---

### Post by grnorris on 2010-03-27
> **Cabs21 said:**
> you could try port forwarding if you can gain access to the router.  If not then try disabling any firewalls while using uTorrent.

 Only the most expensive version of the your-freedom allows port forwarding so I can't really do that.  I've not had any issues with my speeds for a while so I'm not really sure that has anything to do with it after all.  It may have just happened that I didn't notice the firewall thing until I had been having issues with speeds for a couple of days.

I'm also thinking that uTorrent may be thinking I'm behind a firewall because of the stream limits (I'm too lazy to change all my stream settings back a forth each time I switch between free-freedom, basic-freedom, and no proxy).

---

### Post by i_love_it on 2010-03-28
Your-Freedom basic packet provides 256kbits/s which is equal to 32KByte/s so I think you've already max your speed.
There's nothing wrong with wine or utorrent, you were behind Your-Freedom firewall, so utorrent just reported so.

---

### Post by grnorris on 2010-03-31
> **i_love_it said:**
> Your-Freedom basic packet provides 256kbits/s which is equal to 32KByte/s so I think you've already max your speed.
There's nothing wrong with wine or utorrent, you were behind Your-Freedom firewall, so utorrent just reported so.

I realized after the first post that uTorrent reports KB and Your-Freedom reports Kb but, when I was having issues with my speeds they were down to 10KB when I was using the Basic package (about 2 days in a row).  I've still not had any issues since though uTorrents firewall indicator may very well be confused by Your-Freedom.  At this point I'm thinking it was just an issue with the network either at my school or at the Your-Freedom servers that's since been resolved.

---

