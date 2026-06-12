---
title: "BluHell Firewall (for Firefox browser)"
date: 2015-03-07
forum: The Cafe
---

### Post by Tar_Ni on 2015-03-07
Hi,

I discovered this extension recently, and I wanted to share it with you guys, for those who don't know. Basically BluHell Firewall is an extremely lightweight adblocker developped by Diego Casorran available for the Firefox browser. It's very easy on ressource and will block 80-90% of all ads. If you intend to try it, note  that BluHell DOES NOT block random in-page elements, (such as the ones you see on Facebook, or Gmail or Bing Search for exemple but these are really not bothersome in my view..) but uses just 7 hard-coded blocking rules, covering about 8000 .com and .net domain using the Easylist+EasyPrivacy which will remove the vast majority of ads and web trackers.

If you're like me are looking for a good compromise between adblocking, privacy and *performance* first and foremost, this extentsion is for you.

I had forgotten Firefox could be that fast. Adblock Plus considerably slow down a browser. I am no longer using it.

[I]''All we know the availability of popular AdBlockers lying around... but  frankly, these are too bloated with several features and options which  most of us don't use beyond the defaults. So, this extension was made  for those of us who don't care about all that stuff but does about just  getting rid of all the nasty resources being loaded by websites.

This  is a lightweight extension (ie, 30KB compared to ~700KB of other  popular adblockers), which was made with performance in mind. No  configurable options, subscriptions, additional features, etc It just  block what can go to hell ;-)

How this is achieved is thanks to just seven  hard-coded blocking rules covering about 8400 .com and .net domains,  these were auto-generated from Easylist. That means, every time a  certain resource wants to be loaded we will have to iterate through a  list of seven compiled patterns, rather than for each entry from a  common Easylist which contains hundreds of different items to check...  You can now figure things out for yourself...

Next i'll let you decide if this is for you... as long performance is in your mind, it should.[/I]''

Link: [https://addons.mozilla.org/fr/firefox/addon/bluhell-firewall/](https://addons.mozilla.org/fr/firefox/addon/bluhell-firewall/)

---

### Post by Mike_Walsh on 2015-03-07
Hey there, Tar_Ni.

I've been using using BluHell firewall in FF17ESR (on a 'Puppy' Linux install) for a while now.....mainly because you can't get AdBlock Plus OR Ghostery (which I also use) for a version that old.

I tend to use Chromium most of the time. I know you've got a bit of a 'thing' about Google, and Chrome/Chromium (so I'm not going there!) However, just out of curiosity, I removed AdBlock Plus from my Chromium install the other day.....and was astounded by how much faster it ran without it. WITH ABP, startup time (to being logged in, and starting up LastPass) is normally about a minute. Without ABP, that's dropped down to about 20-odd seconds. I'D forgotten how fast Chromium can be, under the right circumstances...

I'm going to remove ABP from MY FF36.....and try BluHell out in that. Thanks for reminding me about it! I don't use that particular 'Puppy' very much nowadays.....because most of the apps are rather dated.


Regards,

Mike. ;)

---

### Post by Tar_Ni on 2015-03-08
> **Mike_Walsh said:**
> I tend to use Chromium most of the time. I know you've got a bit of a 'thing' about Google, and Chrome/Chromium (so I'm not going there!) However, just out of curiosity, I removed AdBlock Plus from my Chromium install the other day.....and was astounded by how much faster it ran without it. WITH ABP, startup time (to being logged in, and starting up LastPass) is normally about a minute. Without ABP, that's dropped down to about 20-odd seconds. I'D forgotten how fast Chromium can be, under the right circumstances...

I am a critic of Google's privacy policies but there is no doubt that Chromium is an excellent browser. I won't use Google Chrome but Chromium is my back-up browser on Xubuntu. The fact that it is is fully open source and that I can turn off the Google-oriented features makes it a very good choice of browser, second behind Firefox in my mind. :)

But BluHell Firewall is indeed not available for Chromium. The dev is focusing on Firefox addons instead. Therefore I would recommend uBlock for Chromium, which is much lighter than ABP, though not as light as BlueHell.

[https://chrome.google.com/webstore/detail/%C2%B5block/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=fr](https://chrome.google.com/webstore/detail/%C2%B5block/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=fr)

> **Mike_Walsh said:**
> I'm going to remove ABP from MY FF36.....and try BluHell out in that. Thanks for reminding me about it! I don't use that particular 'Puppy' very much nowadays.....because most of the apps are rather dated.

Mozilla has conducted some research on the impact of ABP on Firefox and published it's findings here: [https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/)

It's simply unbelievable. This extension is a memory hog. I have tolerated the tradeoff, no ads vs slowing down Firefox for years but now that I found BluHell, I am not looking behind. This extension fully deserves my 10$ donation.

*''One Mozilla developer took a look at AdBlock Plus' effect on Firefox'  RAM usage and found that for every ad the extension blocks, it uses up a  little bit more memory. That accumulates for every ad on every site  until the amount of space occupied by ads may be much higher than it is  without the ad blocker:*

           *Second,  there's an overhead of about 4 MiB per iframe, which is mostly due to  ABP injecting a giant stylesheet into every iframe. Many pages have  multiple iframes, so this can add up quickly. For example, if I load  TechCrunch and roll over the social buttons on every story (thus  triggering the loading of lots of extra JS code), without ABP, Firefox  uses about 194 MiB of physical memory. With ABP, that number more than  doubles, to 417 MiB. This is despite the fact that ABP prevents some  page elements (ads!) from being loaded.'*'

Link: [http://lifehacker.com/adblock-plus-once-again-found-to-dramatically-increase-1576341872](http://lifehacker.com/adblock-plus-once-again-found-to-dramatically-increase-1576341872)

---

### Post by Mike_Walsh on 2015-03-09
Hey, Tar_Ni.

Talking of memory hogs.....

I have two machines. I'm not in the fortunate position of being able to update my hardware whenever the whim takes me, so I make do with hand-me-downs from other family members who are firmly on the MS treadmill, and more or less HAVE to upgrade every time they switch O/Ss.

My 'main' box is a 10-yr old Compaq Presario desktop. Came with 1 GB RAM, which I've upgraded to 3 GB....and XP. I ran that till May last year, when I switched to Linux, and after much distro-hopping, settled down quite happily with Ubuntu & Puppy Linux. The other machine is an even older Dell laptop; an original Inspiron 1100, from 2002. IT only had 128 MB RAM when I received it; I wasted no time maxing it to ! GB RAM, almost as soon as I got it. It, too, was running XP.....molasses ran faster, especially with the 'P4-generation' Celeron it has.

I always loathed IE, and used FF for some years. At some point, I switched AVs, from Norton's 360 to Comodo's CIS suite.....a brilliant, if slightly complex, free AV suite. Along with the install, you used to get Comodo's 'Dragon' browser.....which is their own version of Chrome; with all sorts of security stuff (including ad-blockers) BUILT-IN.....they were using sandboxes long before Chrome cottoned on to them, along with a permanent connection through their OWN secure DNS servers. I decided to give it a go, since it was, quite literally, a 'freebie' supplied WITH a freebie ...

This thing used to make IE look fast, incredibly. I found out by dint of some research that where the current version of Chrome uses something like 180+ MB, this thing (some years ago now), was using over 500 MB RAM! On a I GB machine, with a slow CPU (only SSE2's, along with a very small, 128KB L2 cache), this slowed it down like crazy. Paint dried faster..! It wasn't long before I wiped it off the system, and went back to using FF...


Regards,

Mike. :p

---

### Post by flaymond on 2015-03-18
Bluhell Fire is a very nice add-ons. It's very lightweight, and I can see the major difference of both.

---

