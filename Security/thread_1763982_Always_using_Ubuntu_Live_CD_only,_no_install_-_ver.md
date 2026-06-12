---
title: "Always using Ubuntu Live CD only, no install - very safe?"
date: 2011-05-21
forum: Security
---

### Post by 0Io1 on 2011-05-21
I've been doing something I think is very safe. I abandoned Windows, now I'm only using Ubuntu. But I'm also only using the Ubtunu Live CD 11.04 every time.

That's right, I only run from the Live CD, never install it, it never saves anything ever on the computer. When I shut down the PC, turn it on again, the CD is brand new... like I just bought it off the store shelf every time. Repeat every day.

I just visit some websites on its Firefox every day, so this works for me.

Don't you consider that very safe? I do. :) No download can touch me, not that I download anyway. The OS isn't even installed. Seems safe to me.

Your opinions.

---

### Post by eddie3000 on 2011-05-21
What about security updates? I have no idea about ubuntu and the possible bugs in it, but what if there's a (hypothetical) bug that screams out your email, ebay or bank account passwords to the entire world each time you type them in? Security updates might fix that (hypothetical) bug, while the live cd would be permanently bugged.

---

### Post by Rasa1111 on 2011-05-21
Yes, I also consider that "safe".
Probably about as "safe" as one can get in soo few 'steps'. lol

I wonder if you have noticed that running from the LiveCD is quite a bit slower than an actual install?

If so,
 The best solution for that is to use a USB drive, make it as a "LiveCD" , and boot from that, instead of the CD.  It's the same exact thing.. Only much faster! 

I guess if one doesnt need plugins and codecs.., music/video,  flash/java, etc...
It could be a good option. 

But Ubuntu is quite safe as it is... 
So with Ubuntu, and with my own security applied..
Im not worried.  :)


> What about security updates? I have no idea about ubuntu and the  possible bugs in it, but what if there's a (hypothetical) bug that  screams out your email, ebay or bank account passwords to the entire  world each time you type them in? Security updates might fix that  (hypothetical) bug, while the live cd would be permanently bugged.

Good point.

---

### Post by prshah on 2011-05-21
> **0Io1 said:**
> Seems safe to me.
Your opinions.

Seems paranoid to me :) but hey, what works, works.

---

### Post by tubbygweilo on 2011-05-21
Working from a live CD is quite safe but please remember that the codebase does not reflect the latest security patches whereas running from a guest account will have all latest securituy patches (if applied to your OS). I expect mode of runnimng be safer and much faster than running from a live cd.

---

### Post by Dave_L on 2011-05-21
Another disadvantage (to the Live CD) is the lack of security enhancements such as the Firefox add-on Noscript, and the use of Apparmor to confine applications.

---

### Post by bodhi.zazen on 2011-05-21
> **Dave_L said:**
> Another disadvantage (to the Live CD) is the lack of security enhancements such as the Firefox add-on Noscript, and the use of Apparmor to confine applications.

Unless you spin a custom CD with those tools in it.

In general a live CD is not going to be more secure then an installation due to the lack up updates to the live CD.

IMHO the people who advise using a live CD for security do not understand security, and do not want to learn security, and thus "trust" a live CD.

To be more specific, what is your security concern and what do you hope to accomplish with a live CD that can not be better accomplished by a live installation?

---

### Post by ChrisWells on 2011-05-22
The only way a livecd would be more secure is not storing any data. Encryption on an install would be more secure, as you'd have all the security updates installed. Would also be 100x faster. I think you should just install it, especially if you're just browsing the web. Security updates for firefox and system ones would be safer than running an out of date livecd each time. I'd find it a pain loading it up all the time as well, takes what ~5 mins to get to the desktop from a dvd :(

---

### Post by Larkspur on 2011-05-22
I second tubbygweilo's advice to use a guest session on an installed Ubuntu.  It combines the safety of a Live CD (it doesn't write to disk) with the extra safety of security updates.  Also, it is protected by an apparmor profile.

---

### Post by MaxDeviant on 2011-05-22
It seems pretty safe to me, albeit a little excessive. I think there's a balance between security and practicality. I like the freedom of being able to customize my Ubuntu exactly the way I want to, and I do so without feeling compromised in my security. But hey, whatever floats your boat.

---

### Post by Starfleet on 2011-05-24
> **0Io1 said:**
> I've been doing something I think is very safe. I abandoned Windows, now I'm only using Ubuntu. But I'm also only using the Ubtunu Live CD 11.04 every time.

That's right, I only run from the Live CD, never install it, it never saves anything ever on the computer. When I shut down the PC, turn it on again, the CD is brand new... like I just bought it off the store shelf every time. Repeat every day.

I just visit some websites on its Firefox every day, so this works for me.

Don't you consider that very safe? I do. :) No download can touch me, not that I download anyway. The OS isn't even installed. Seems safe to me.

Your opinions.

My advice would be to install it. In tests we did at our labs there was no difference in security between a live cd and an installed version but the installed version ran hugely better and much much faster. Remember, Linux is the safest Operating System in the world. I've run it installed for years online 20 hours per day for every conceivable task and never had a problem of any kind.

---

### Post by handy on 2011-05-24
My limited security understanding tells me that an HDD installation gives me far greater power than just sticking in & booting from "live media".

With a "real" installation, I can at least run the likes of Addblock +, Beef Taco, BetterPrivacy, GreaseMonkey with the googlePrivacy script, NoScript, & add the following to the Firefox about:config (quoted from spriralinear.org):

[i]By setting network.http.sendRefererHeader in Firefox preferences (about:config) to zero, then whenever you visit a link from one site, the destination site doesn't know the original site you were referred from.

This in effect makes the Firefox add-on RefControl redundant.

Also, by setting network.prefetch-next to false it brings about the following:

Link prefetching is when a web page hints to the browser that certain pages are likely to be visited, so the browser downloads them immediately so they can be displayed immediately when the user requests it. This preference controls whether link prefetching is enabled.

I prefer this disabled personally, for a variety of reasons.[/i]
____________

The following from tjwoosta, on changing your useragent string in Firefox. Which is well worthwhile, as it is used to identify & track web users, & Linux users stand out far more than do Windows users, so I use a Windows userargent string:

[i]To override the useragent via about:config you just need to add a new key general.useragent.override (assuming you don't already have it from in the past) and set it to whatever string you want to use. You should be able to find one here [http://www.useragentstring.com/pages/useragentstring.php](http://www.useragentstring.com/pages/useragentstring.php)

If you want to undo the override just right click the key and choose reset. [/i]
____________


These are worth a look also:

[http://www.gethifi.com/blog/browser-rest-http-accept-headers](http://www.gethifi.com/blog/browser-rest-http-accept-headers)

I'm still waiting for an Firefox 4.0.1 update on the next one:

[https://addons.mozilla.org/en-us/firefox/addon/modify-headers/](https://addons.mozilla.org/en-us/firefox/addon/modify-headers/)

This site gives a much more thorough & accurate test than that of the EFF's Panopticlick test:
 
[http://browserspy.dk/](http://browserspy.dk/)

---

