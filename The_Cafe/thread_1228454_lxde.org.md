---
title: "lxde.org?"
date: 2009-07-31
forum: The Cafe
---

### Post by lykwydchykyn on 2009-07-31
For the last three days, I've been trying each day to get to [www.lxde.org](www.lxde.org) to get information on LXDE.  It has seemed to be down every time I tried, and when I checked at downforeveryoneorjustme.com, it confirmed the site seemed to be down.

I figured they were just having network troubles, until I noticed tonight that Google's cache of the main page is from LAST NIGHT, just before midnight.

I'm using opendns for dns, but it will not resolve lxde.org.  If I do "host lxde.org" I get "connection timeout, no servers could be reached".  I get the same from my ISP's DNS servers, and the DNS servers for lxde.org's ISP.

So, is anyone else able to get to the site?  If so, what country are you in?
Should I get my tinfoil hat on?

---

### Post by FuturePilot on 2009-07-31
Can't get to it here. DNS isn't resolving. I'm using my ISP's DNS servers.

---

### Post by Dullstar on 2009-07-31
Here.  Try this.  You said, "information on LXDE."

[_LXDE_](www.en.wikipedia.org/wiki/LXDE)

---

### Post by NovaAesa on 2009-07-31
> Address Not Found
Firefox can't find the server at [www.lxde.org](www.lxde.org).
Looks like it's down.

---

### Post by lykwydchykyn on 2009-07-31
> **Dullstar said:**
> Here.  Try this.  You said, "information on LXDE."

[_LXDE_](www.en.wikipedia.org/wiki/LXDE)

Well, thanks; but I was looking for specific info from the site.  The sourceforge page is still up and working, I notice.

Is the URL resolving for you Dullstar?

---

### Post by Dullstar on 2009-07-31
I shall check.

---

### Post by OutOfReach on 2009-07-31
Down for me too, it's giving me an "Unknown host" error, saying it doesn't exist.

---

### Post by Dullstar on 2009-07-31
It's down...

---

### Post by Chemical Imbalance on 2009-07-31
Not loading for me either. Connection timeout.  Using OpenDNS.

It's down: [http://downforeveryoneorjustme.com/lxde.org](http://downforeveryoneorjustme.com/lxde.org)

---

### Post by lykwydchykyn on 2009-07-31
So the million dollar question... if it's been down like this since at least wednesday....

How is Google still caching it?

---

### Post by Dullstar on 2009-07-31
They're caching it with their nonexistent magic powers!  lol

---

### Post by sashoalm on 2009-08-01
Down for me, too.

---

### Post by earthpigg on 2009-08-01
over the last 2-3 days, it seems to be down half the time.

:(

anyone got the scoop on what the deal is with that?

edit:
for lazyness -
[http://www.lxde.org/](http://www.lxde.org/)
[http://wiki.lxde.org/](http://wiki.lxde.org/)


edit2:
just saw the other thread on this issue. feel free to delete this thread or, if others post in it before that happens, to merge it into the other one.

---

### Post by heroidi on 2009-08-01
have noticed this yesterday and they just hit the version 0.5 WTF!

---

### Post by unknownPoster on 2009-08-01
```
root@li51-129:~# ping -c 3 http://www.lxde.org
ping: unknown host http://www.lxde.org
```
I ran this from one of my servers.

---

### Post by bailout on 2009-08-01
Perhaps the project is dead? I looked into lxde a few months ago when investigating options to install on a netbook. I thought it had potential but all the releases available and the news on the site were quite old and gave the impression that not much was going on.

---

### Post by mikewhatever on 2009-08-01
Don't be paranoid. The site is up and running, no problems.

---

### Post by dragos240 on 2009-08-01
Orly?

---

### Post by lykwydchykyn on 2009-08-01
> **mikewhatever said:**
> Don't be paranoid. The site is up and running, no problems.

Still not coming up here.  Which is why I'm paranoid.  Well, not to any great extent...

What is the IP of the site, since you can bring it up where you are?

[quote=bailout]
Perhaps the project is dead? I looked into lxde a few months ago when investigating options to install on a netbook. I thought it had potential but all the releases available and the news on the site were quite old and gave the impression that not much was going on.
[/quote]
No, it's not dead.  The sourceforge page shows plenty of activity, and lxpanel 0.5 was just released last week.

---

### Post by Dullstar on 2009-08-01
On the bright side, it wasn't that good.

---

### Post by mikewhatever on 2009-08-01
> **lykwydchykyn said:**
> Still not coming up here.  Which is why I'm paranoid.  Well, not to any great extent...

What is the IP of the site, since you can bring it up where you are?

Just checked it again, the site is ok. I've no idea what's the IP.

> **Dullstar said:**
> On the bright side, it wasn't that good.

I think it's excelent.

---

### Post by Dark Aspect on 2009-08-01
Down for me too,

ping lxde.org
```
ping: unknown host lxde.org
```

host lxde.org
```
;; connection timed out; no servers could be reached
```

---

### Post by lykwydchykyn on 2009-08-01
> **mikewhatever said:**
> Just checked it again, the site is ok. I've no idea what's the IP.


Kindly type the following into a terminal and tell us the output.  

```

host www.lxde.org

```

Many thanks.

---

### Post by mikewhatever on 2009-08-01
> **lykwydchykyn said:**
> Kindly type the following into a terminal and tell us the output.  

```

host www.lxde.org

```

Many thanks.

host lxde.org
lxde.org has address 210.240.39.7
;; connection timed out; no servers could be reached
lxde.org mail is handled by 5 ALT1.ASPMX.L.GOOGLE.COM.
lxde.org mail is handled by 5 ALT2.ASPMX.L.GOOGLE.COM.
lxde.org mail is handled by 10 ASPMX2.GOOGLEMAIL.COM.
lxde.org mail is handled by 1 ASPMX.L.GOOGLE.COM.

I don't know what the deal with 'connection timed out' is, the site opens just fine in the web browser.

---

### Post by FuturePilot on 2009-08-01
```
$ host www.lxde.org
;; connection timed out; no servers could be reached

```

---

### Post by dragos240 on 2009-08-01
host lxde.org
Host lxde.org not found: 3(NXDOMAIN)

---

### Post by XubuRoxMySox on 2009-08-01
Good grief, the project is hardly "old," nor "dead." It's quite new, actually, and undergoing heavy development. More and more of the "lightweight" distros are using it as their default d.e.

It's just been a problem with their server or something. I'm sure they are aware of it... their forums have been *very* active right up 'til the server crashed or whatever.

-Robin

---

### Post by oupsemma on 2009-08-03
Same here, I've been trying many times a day to get informations about lxde tweakings, and it was totally impossible to reach the site these last 3 days.

And the Lxde project is not dead, there are some nice distros running it that have been released recently; among them PCLXDE, a nice tiny PCLinuxOS running Lxde with a GUI for Lxde Control Center.

---

### Post by HappinessNow on 2009-08-03
lxde is quite dead for me.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123413&d=1249287534[/IMG]

---

### Post by wpeckham on 2011-11-17
It is now two years later and I still cannot connect to LXDE.ORG.
It does nor appear to be down, blocked rather.  
I wish I could tell who was blocking it. 
Better, I wish they would STOP!

---

### Post by epp on 2011-11-17
The site had been up, but I have not been able to reach anything in the lxde.org domain (forum, www, wiki) all week.

---

### Post by Elfy on 2011-11-18
It goes up and down a lot apparently - there is a newer thread here - [http://ubuntuforums.org/showthread.php?t=1882394](http://ubuntuforums.org/showthread.php?t=1882394)

This one can close

---

