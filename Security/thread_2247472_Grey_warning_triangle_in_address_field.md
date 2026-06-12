---
title: "Grey warning triangle in address field"
date: 2014-10-08
forum: Security
---

### Post by peter147 on 2014-10-08
Hi,

I've been using Ubuntu for a few years, and a couple of months ago I deicided to install the latest 14.04 LTS version. Initially, I had some problems with the laptop losing the wi-fi connection every once in a while, but that sorted itself out somehow and has been fine since.

Couple of weeks ago, I noticed that when I went to the sign in page on ebay.co.uk, I no longer got the green "Ebay, INC.(US)" to the left of the "https://..." in the address field. I'm still getting that when on the ebay.com sign in page, and it looks like this:

[IMG]http://www.tappingfeet.com/Sign%20in%20ebay%202.JPG[/IMG]


When on the ebay.co.uk sign in page I get this:

[IMG]http://www.tappingfeet.com/Sign%20in%20grey%20triangle.JPG[/IMG]

I don't know enough about all of this to judge what this means apart from the information I get when clicking on the grey triangle: "This web site does not supply identity information. The connection to this web site is not fully secure because it contains unencrypted elements (such as pictures)."

I've tried the sign in pages on ebay.co.uk, ebay.ca, ebay.de, ebay.au and they're all dispalying the grey warning triangle on their sign in pages. It's only on the US (.com) ebay sign in page that I'm getting the appropriate green text, as displayed in my first picture above.

Would very much appreciate any input regarding this - what the implications might be and above all; what to do to about it?

I've erased cookies, cache, restarted Firefox etc, to no avail. If I run Windows 7 and Internet Explorer on my computer instead of Ubuntu, this problem doesn't exist.

Please bear in mind that I'm not at all knowledgeable with computers. Thanks!

---

### Post by Habitual on 2014-10-08
You may wish to clear your browser's cache.

I definitely get an ssl padlock at both sites, but I have never been there, so I have no cache

[ATTACH=CONFIG]257051[/ATTACH][ATTACH=CONFIG]257052[/ATTACH]

I hope that helps.

---

### Post by peter147 on 2014-10-08
Thanks. I've cleared the cache numerous times as well as cleared all cookies, restarting Firefox etc. Nothing I've done has had any impact on the grey warning triangle...

---

### Post by Habitual on 2014-10-08
Can you try another browser?

---

### Post by peter147 on 2014-10-08
Here' s what I get when using Chrome; a padlock with a yellow warning triangle on it:

[IMG]http://www.tappingfeet.com/Sign in chrome.JPG[/IMG]

...and the yellow triangle mans:

[IMG]http://www.tappingfeet.com/Sign in chrome 2.JPG[/IMG]

So, I'm assuming this means pretty much the same thing as the grey triangle in Fireox.

---

### Post by Habitual on 2014-10-08
I am stumped.
You have a router?

---

### Post by Habitual on 2014-10-08
> **peter147 said:**
> Thanks. I've cleared the cache numerous times as well as cleared all cookies, restarting Firefox etc.  Understood, but have you cleared these items and then restarted firefox?

Are you using a bookmark link to this login page(s) or are you plain navigating to say [http://www.ebay.co.uk/](http://www.ebay.co.uk/) and hitting the "Hello ([Sign in]("https://signin.ebay.co.uk/ws/eBayISAPI.dll?SignIn&_trksid=m570.l3348") to bid or buy) link?
I'd like to suggest starting in safe mode using 

In terminal > 
```
firefox -safe-mode
``` and try the sites again.

---

### Post by peter147 on 2014-10-08
Yes, I have a router

---

### Post by peter147 on 2014-10-08
Yes, cleared cache and cookies and then restarted Firefox.

Tried your suggestion:

 "In terminal > 
     Code:
     firefox -safe-mode

and try the sites again."


This is what I got back:

(process:7138): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
peter@P:~$

---

### Post by peter147 on 2014-10-09
> **Habitual said:**
> Understood, but have you cleared these items and then restarted firefox?

**Yes.**

Are you using a bookmark link to this login page(s) or are you plain navigating to say [http://www.ebay.co.uk/](http://www.ebay.co.uk/) and hitting the "Hello ([Sign in]("https://signin.ebay.co.uk/ws/eBayISAPI.dll?SignIn&_trksid=m570.l3348") to bid or buy) link?

**Plain navigating, using the Sign in, not a bookmark**

I'd like to suggest starting in safe mode using 

In terminal > 
```
firefox -safe-mode
``` and try the sites again.

[B]Here's what I got back when I did that:
[COLOR=#000000]
(process:7138): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed[/COLOR]
[COLOR=#000000]peter@P:~$

[/COLOR]Another thing that I've noticed is that when I have the grey warning triangle and press the page reload button, the green (correct ) "Ebay Inc. (US)" flashes by for a fraction of a second in the address bar, but is then always replaced by the grey triangle again.
[/B]

---

### Post by Habitual on 2014-10-09
I am stumped. Sorry, someone else with more knowledge.fu will be along to help out.

Have a Great Day!

---

### Post by untrustytahr on 2014-10-09
I can't say that I have any more knowledge than Habitual, but it looks like like a 'mixed content' message.   Mixed content means that not all the content that loaded on the page came from the server with the SSL certificate.  This can be for multiple reasons... some innocuous, some not.
 

 If you goto the page in question and click ctrl-shift-k to bring up the developer console in firefox the items in question should be highlighted in red.  Here is a somewhat outdated explanation [https://developer.mozilla.org/en-US/docs/Security/MixedContent](https://developer.mozilla.org/en-US/docs/Security/MixedContent) of what to look for.
 

 Are you using a caching proxy server?  I would guess that could cause something like this.

---

### Post by bashiergui on 2014-10-09
Agreed it's mixed content. You can use the developer tools to determine what elements are being requested over http. Another method would be to use noscripts in Firefox or notscripts in Chrome. Those addons will block javascripts being loaded. You'll see a list of scripts being requested and their origins.

Many things can cause the problem. One would be if the website developers coded the resource request to use http. There are methods developers can use to force the resources to use the same protocol as the rest of the page. But this isn't something you have control over. You could open a support ticket or bug report to ebay asking them to fix it.

---

### Post by peter147 on 2014-10-09
Thanks for all the input, but as I've explained, I'm not good with this sort of thing. What I cannot understand is that it worked correctly on all eBay login sites up until some time ago, and I haven't done/changed anything on my computer (at least not that I'm aware of). Also strange that it actually still works on the US site - [www.ebay.com]("http://www.ebay.com").
I contacted ebay about this and they just gave me the advice to clear the cache and cookies and restart Firefox, which I did.

Also strange that I don't have the problem when booting in Windows (7) and using Internet Explorer (which I don't want to use).

I'm at a loss here.

---

### Post by Habitual on 2014-10-09
Try a new firefox profile. Close firefox, open a terminal and issue:
```
firefox -ProfileManager
``` and create a new one, or allow firefox to do so, then check the site(s) again.

Please let us know.

---

### Post by bashiergui on 2014-10-09
Understand that the problem is most likely on Ebay's end. 

I found a potential work around that requires no technical saavy. Seems to fit your low-tech requirements:

[http://forums.mozillazine.org/viewtopic.php?f=38&t=2571791](http://forums.mozillazine.org/viewtopic.php?f=38&t=2571791)

"this is from the mixed content. When I go to https paypal with images off, I get the padlock on the main page. If I turn images on, I get the world icon. You can check for yourself, go to options -> content -> uncheck "load images automatically" and then go to ebay, paypal, etc, and you should see the padlock as normal.
(Note also that by happenstance, Adblock Plus also blocks the mixed content and gives the full padlock, in the cases I tried)."


Adblock is a browser addon that is really easy to use. It might solve the problem.

---

### Post by peter147 on 2014-10-10
> **bashiergui said:**
> Understand that the problem is most likely on Ebay's end. 

I found a potential work around that requires no technical saavy. Seems to fit your low-tech requirements:

[http://forums.mozillazine.org/viewtopic.php?f=38&t=2571791](http://forums.mozillazine.org/viewtopic.php?f=38&t=2571791)

"this is from the mixed content. When I go to https paypal with images off, I get the padlock on the main page. If I turn images on, I get the world icon. You can check for yourself, go to options -> content -> uncheck "load images automatically" and then go to ebay, paypal, etc, and you should see the padlock as normal.
(Note also that by happenstance, Adblock Plus also blocks the mixed content and gives the full padlock, in the cases I tried)."

I've tried that too - unchecked "load images automatically" - didn't solve the problem.


> Adblock is a browser addon that is really easy to use. It might solve the problem.

I have the latest Adblock+ installed already, so that's not a fix either unfortunately.

When using the Firefox web console on the ebay UK sign in page, I get the following in red lettering: 

"http://pics.ebaystatic.com/aw/pics/globalHeader/tn.png" and
 "Loading mixed (insecure) display content on a secure page "http://pics.ebaystatic.com/aw/pics/globalHeader/tn.png"

...so; does this mean that the above tn.png file (which I assume are pictures) are responsible for the "insecure" content on this page, due to its http:// status as opposed to [https://?](https://?)

[http://pics.ebaystatic.com/aw/pics/globalHeader/tn.png](http://pics.ebaystatic.com/aw/pics/globalHeader/tn.png) seems to be this picture:

[IMG]http://p.ebaystatic.com/aw/pics/globalheader/tn.png[/IMG]

The strange thing is that if I click on the "Register" button on eBay UK, I get a secure padlock instead of the grey warning triangle...probably because that picture isn't on that page(?).

As mentioned earlier; if I instead boot my laptop in Windows7 and use Internet Explorer on the UK eBay sign in page, I get the secure (padlocked) connection...go figure

---

### Post by untrustytahr on 2014-10-10
> **peter147 said:**
> https://?[/URL]



   Yes.  The loading of that individual image can be blocked.
 

 Click on the grey exclamation point-> click more information button ->click “Media” button on top-> Select that image  url in the address box (make sure it's highlighted) &#8594; check the box “Block images from *xyz *on the bottom of page.

 

 Clear cookies & cache and reload the page.  It should now work properly.
 

 Let us know how it comes out.

---

### Post by untrustytahr on 2014-10-10
> **peter147 said:**
> The strange thing is that if I click on the "Register" button on eBay UK, I get a secure padlock instead of the grey warning triangle.

As mentioned earlier; if I instead boot my laptop in Windows7 and use Internet Explorer on the UK eBay sign in page, I get the secure (padlocked) connection...go figure

1. The "Registier" button probaby takes you to a different page.
2. Different browsers handle mixed content and it's implications differently.  That's why developers test their work (or should) in all of them.

---

### Post by peter147 on 2014-10-10
He he...solved it - thanks to bashiergui :KS - right clicked on that particular picture on the eBay UK sign in page and had Adblock filter it out - now I get the green padlock and everything seems fine!

Thanks a lot for your helpful suggestions!

Cheers!

---

### Post by untrustytahr on 2014-10-10
Great!  Mark the thread as solved & help someone else to start using linux.  ;)

---

### Post by bashiergui on 2014-10-10
Glad to have helped.

Too bad the Ebay web developers aren't very good at developing for the web :-s

---

### Post by Habitual on 2014-10-10
> **peter147 said:**
> right clicked on that particular picture on the eBay UK sign in page and had Adblock filter it out - now I get the green padlock and everything seems fine! That's a new one. But then as Gilda Radner used to say "it's always 'something'"
Good Catch bashiergui!

---

