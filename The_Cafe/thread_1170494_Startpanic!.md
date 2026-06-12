---
title: "Startpanic!"
date: 2009-05-26
forum: The Cafe
---

### Post by rax_m on 2009-05-26
Checkout [http://www.startpanic.com/](http://www.startpanic.com/)

Apparently all the main browsers allow a website to determine one's search history. I connected with Chromium and it definitely displayed my history. 

From the site:
> 
We are gathering petition signatures with the request to patch the privacy vulnerabilities of web different web browsers. This petition will be sent to the four major development companies - Mozilla Corp., Apple inc., Microsoft Corp. and Opera Software ASA. Join us for a safe and secure Internet!


How big a deal do you think this is?

---

### Post by -grubby on 2009-05-26
Oh shi-

---

### Post by pwnst*r on 2009-05-26
*very* interesting, although i'll wait till i get home to test this

---

### Post by hanzomon4 on 2009-05-26
this looks pretty suspect if you ask me

---

### Post by rax_m on 2009-05-26
The site or the browser issue?

---

### Post by MaxIBoy on 2009-05-26
NoScript is amazing. :p

---

### Post by Jesuses Left Leg on 2009-05-26
It didn't show me anything. I don't get it.
It just showed this once it was done loading.

"Correct? You bet. If you would like to protect your privacy online and want browser developers to patch this vulnerability, please sign our petition. Moreover, you can send your friend a special link via Startpanic.com mailing system. When your friend clicks it, you will receive the list of websites he has visited recently."
and "here we go in the lower box"

What was meant to happen?

---

### Post by pwnst*r on 2009-05-26
@maxi

it is, but you have to do another click to actually have it pull the info

---

### Post by rax_m on 2009-05-26
> **MaxIBoy said:**
> NoScript is amazing. :p


Yep I agree. Normally I use FF with noscript. But I've just been test running Chromium. ;)

---

### Post by imbjr on 2009-05-26
> **MaxIBoy said:**
> NoScript is amazing. :p

Damn. I thought I saw something on this recently that used CCS only - no need for JavaScript.

Now I can't find the link!

---

### Post by rax_m on 2009-05-26
> **imbjr said:**
> Damn. I thought I saw something on this recently that used CCS only - no need for JavaScript.

Now I can't find the link!

Perhaps this ?

[http://mybroadband.co.za/news/Internet/8187.html](http://mybroadband.co.za/news/Internet/8187.html)

---

### Post by Delever on 2009-05-26
Startpanic site exploits a:visited link tag to check if some site was visited. It can't list every site which was visited by user, because it checks sites against this database: [http://www.startpanic.com/db/db_en.txt](http://www.startpanic.com/db/db_en.txt).

How it works: when you click start, it uses javascript to retrieve site list. Then it prints hidden links in your window, and checks if browser changed link style for visited links. If it did, then those links are added to list.

Hope this clarifies how much a site can actually find.

Summary: If script doesn't know about your site, it can't check if you visited it.

EDIT: that list is awfully huge though... So most sites are checked.

---

### Post by Kareeser on 2009-05-26
Hm, that's a pretty roundabout way to find someone's internet history... and if that's true, a simple history cleaning, or emptying of /tmp should do the trick.

Had me going to think my internet history was somehow logged into some database online.

Oh wait, Google already does that with your search terms ;)

---

### Post by pwnst*r on 2009-05-26
> **Delever said:**
> Startpanic site exploits a:visited link tag to check if some site was visited. It can't list every site which was visited by user, because it checks sites against this database: [http://www.startpanic.com/db/db_en.txt](http://www.startpanic.com/db/db_en.txt).

How it works: when you click start, it uses javascript to retrieve site list. Then it prints hidden links in your window, and checks if browser changed link style for visited links. If it did, then those links are added to list.

Hope this clarifies how much a site can actually find.

Summary: If script doesn't know about your site, it can't check if you visited it.

EDIT: that list is awfully huge though... So most sites are checked.

nice info, thanks man

---

### Post by Delever on 2009-05-26
Someone needs to make plugin to disable visited/not visited style for links to site root: i.e do not highlight visited links to "ubuntu.com" but highlight links to "ubuntu.com/something".

---

### Post by hatten on 2009-05-26
No history saved+noscript=pwnd

---

### Post by pwnst*r on 2009-05-26
i'm gonna see what happens with chrome's incognito

---

### Post by ice60 on 2009-05-26
the petition is pointless and stupid, you should just learn how to secure your browsers. you'll always be vulnerable otherwise!

here are some cool filters to merge with proxomitron, it's far more powerful than no script -
[http://prxbx.com/forums/showthread.php?tid=970](http://prxbx.com/forums/showthread.php?tid=970)

---

### Post by pwnst*r on 2009-05-26
> **ice60 said:**
> the petition is pointless and stupid, you should just learn how to secure your browsers. you'll always be vulnerable otherwise!

here are some cool filters to merge with proxomitron, it's far more powerful than no script -
[http://prxbx.com/forums/showthread.php?tid=970](http://prxbx.com/forums/showthread.php?tid=970)

i'm not seeing anywhere in that thread that it's "far more powerful" than no script.  care to elaborate?

---

### Post by init1 on 2009-05-26
Eh, I'm not worried. I disabled history, so it's not showing me anything.

---

### Post by wirepuller134 on 2009-05-26
ditto

---

### Post by dragos240 on 2009-05-26
Holy ship! I want to protect myself!

---

### Post by samjh on 2009-05-27
Didn't work on mine.  If you clear your private data (assuming you use Firefox), it can't pull anything.

---

### Post by lisati on 2009-05-27
It didn't get everything (heh heh heh) but it does know about the forums......

---

### Post by ice60 on 2009-05-27
> **pwnst*r said:**
> i'm not seeing anywhere in that thread that it's "far more powerful" than no script.  care to elaborate?
yes, those are just one set of filters to be merged with other filters i.e. the latest sidki filters -
[http://prxbx.com/forums/showthread.php?tid=1261](http://prxbx.com/forums/showthread.php?tid=1261)

and here's a little about Proxomitron
[http://www.geocities.com/sidki3003/prox.html](http://www.geocities.com/sidki3003/prox.html)

you can also filter SSL connections too with proxomitron -
[http://www.wilderssecurity.com/showthread.php?t=31087](http://www.wilderssecurity.com/showthread.php?t=31087)

---

