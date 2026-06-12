---
title: "How do I find information about a website?"
date: 2006-12-11
forum: The Cafe
---

### Post by jingo811 on 2006-12-11
There's a not so well known website that I want to shop from.  So I want to enter their web adress into somewhere like System>Admin>[Network Tools] 
in order to find as much information about their business and who and where the owner is registered as.

Is there some network tools that can do this in Ubuntu?  If so how should I do it?
From the past I've bookmarked a page called Server IP info or something where you just pasted in the web adress to find out the credibility of the site owner.  But the site has stopped working :-( so now I have to learn how to do it by local tools.

---

### Post by taurus on 2006-12-11
Move to Cafe.

---

### Post by potrick on 2006-12-11
open a terminal, and type whois followed by the name of the site. So, for example "whois ubuntuforums.org" gives you information about this site. Try it out.

---

### Post by jingo811 on 2006-12-11
:-D Linux is way cool.  I guess it's true like somebody wrote in the 90s somewhere on the net.  Linux is a Porsche compared to Windows's Horse & Carriage.  Tnx, whois is a fun command.

---

### Post by jingo811 on 2007-10-04
[SIZE="4"]New question.[/SIZE]

When I do this in terminal things seem to work.
```
whois ubuntuforums.org
```
But when I try it on my own website or some other well known websites like
```
$ whois gamespy.com
$ whois yahoo.com

Timeout.
```
It runs for some minute without results and I get a Timeout echo.  Why is that?

---

### Post by dptxp on 2007-10-04
If you make a google search on the word whois, you will find quite a few sites that give information on domain names.

---

### Post by helliewm on 2007-10-04
[www.dnsstuff.com](www.dnsstuff.com) should help.

Helen

---

### Post by mdsmedia on 2007-10-04
> **dptxp said:**
> If you make a google search on the word whois, you will find quite a few sites that give information on domain names.
Completely off topic, but dptxp...are they Cavaliers in your avatar? I had a Cavalier  in my previous relationship...left him with my ex...but love the breed. Sorry to hijack the thread.

---

### Post by jingo811 on 2007-10-05
tnx.

---

### Post by FranMichaels on 2007-10-05
Try this too.

*dig [www.ubuntuforums.org](www.ubuntuforums.org)*

*tracepath [www.google.com](www.google.com)*

tracepath is really cool, it shows how you connect to that site, all the servers it passes through to get there. 
:)

---

### Post by jingo811 on 2007-10-05
Cool tnx :)

---

### Post by dptxp on 2007-10-07
> **mdsmedia said:**
> Completely off topic, but dptxp...are they Cavaliers in your avatar? I had a Cavalier  in my previous relationship...left him with my ex...but love the breed. Sorry to hijack the thread.

they are, 
unfortunately they are not mine.:(

---

