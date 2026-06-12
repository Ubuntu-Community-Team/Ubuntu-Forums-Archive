---
title: "Viewing forums in links"
date: 2006-05-17
forum: The Cafe
---

### Post by s|k on 2006-05-17
So I am viewing the forums in links right now. I have to say it is not so bad. I was able to login, that is something I can not even do with gmail.
I think though that the site could be made more text-only friendly, there is a lot of arrow keying to navigate. Overall though it is pretty nice and everything seems to work. :)

This is great for us ubuntu server users who only have a cli. When there are problems we can start links and search and use the forums for answers.

It's pretty cool! :D

---

### Post by MenZa on 2006-05-18
...you mean *lynx*, right?

---

### Post by mostwanted on 2006-05-18
[QUOTE=MenZa]...you mean *lynx*, right?[/QUOTE]

He probably means *links* if he says so?

---

### Post by aysiu on 2006-05-18
[QUOTE=mostwanted]He probably means *links* if he says so?[/QUOTE] It sounds like *lynx*, though.

---

### Post by bonzodog on 2006-05-18
heres the confusing bit, there is Links, links2, lynx, and elinks. All text based web browsers. I have found elinks to be the best at displaying the forums.

---

### Post by WildTangent on 2006-05-18
links2 works with my router's administration page somewhat...lynx doesn't. I occasionally attempt to connect to the forums from my cellphone, but end up giving up because of all the scrolling needed. Is there not a way to offer up a different stylesheet depending on user agent?

-Wild

---

### Post by void_false on 2006-05-18
How could you all forget about w3m?!?! :evil:

---

### Post by s|k on 2006-05-18
[QUOTE=MenZa]...you mean *lynx*, right?[/QUOTE]
No, I meant links. sudo apt-get install links.

It is an excellent browser, much better than lynx. It does javascript, cookies and is better with table layouts and such. I could never use these forums with lynx.

---

### Post by sktx on 2006-09-07
***first, a little background (not particularly relevant, but i'm feeling a bit --verbose, scroll down to the end and i'll summarize so you don't have to read my ramblings) ***....

yesterday i decided that i was going to give up my last small shred of dependence on the GUI (besides video :p) and finally learn to set up and use the console programs i've heard about that do everything i rely on X apps for. 

i narrowed down the set of apps i was going to learn to naim for instant messaging, pytone for music, mutt for email and elinks for a browser.  all of this being run on top of GNU screen, which is an incredibly cool app.  i'm pretty sure that if buddha, jesus, mohammed and hank williams all got together and decided to write some software, the end product would be GNU screen. anyway, moving on...

pytone came out of the box and with an enjoyable bit of tweaking on the rc file, was up and running easy and looking just how i wanted it to.  naim was giving me trouble but i quickly realized that i'd left a port that it needed unopened on my firewall, and now everything's coming along smoothly. the only major problem i've had so far came from elinks....

customizing and tweaking elinks was easy, the options function made it incredibly easy to configure, and i soon had everything working the way i wanted it to, with everything colored the way i wanted it to be colored.

then, i came to the forums to search out some opinions and howtos on console apps, where i ran into the first snag i couldn't solve.  


***PROBLEM: ***
i run elinks, from a new window in GNU screen and go straight to ubuntuforums.org ... using the arrow keys, i move to the "search" box, hit enter to activate, type my terms, and hit enter to release the box.  i hit the right arrow to follow the link, and say yes to the POST_DATA prompt..

on the first try it tells me that i can only perform one search every 15 seconds.  thinking that i have a cached copy of the repeated search, i go back and hit Ctrl-RightArrow to send the textbox data without using the cached copy of the page... same result.  

Tried a few different ways, uninstalled, purged, and reinstalled elinks, still no luck... 

google and forums haven't yielded anything that i've found.  anyone else had a similar problem?  or have any suggestions to read/search/try?


*thanks for taking the time to wade through my rambling text *:)

--ck[sktx];.

---

### Post by Kindred on 2006-09-07
> **sktx said:**
> ***first, a little background (not particularly relevant, but i'm feeling a bit --verbose, scroll down to the end and i'll summarize so you don't have to read my ramblings) ***....

yesterday i decided that i was going to give up my last small shred of dependence on the GUI (besides video :p) and finally learn to set up and use the console programs i've heard about that do everything i rely on X apps for. 

i narrowed down the set of apps i was going to learn to naim for instant messaging, pytone for music, mutt for email and elinks for a browser.  all of this being run on top of GNU screen, which is an incredibly cool app.  i'm pretty sure that if buddha, jesus, mohammed and hank williams all got together and decided to write some software, the end product would be GNU screen. anyway, moving on...

pytone came out of the box and with an enjoyable bit of tweaking on the rc file, was up and running easy and looking just how i wanted it to.  naim was giving me trouble but i quickly realized that i'd left a port that it needed unopened on my firewall, and now everything's coming along smoothly. the only major problem i've had so far came from elinks....

customizing and tweaking elinks was easy, the options function made it incredibly easy to configure, and i soon had everything working the way i wanted it to, with everything colored the way i wanted it to be colored.

then, i came to the forums to search out some opinions and howtos on console apps, where i ran into the first snag i couldn't solve.  


***PROBLEM: ***
i run elinks, from a new window in GNU screen and go straight to ubuntuforums.org ... using the arrow keys, i move to the "search" box, hit enter to activate, type my terms, and hit enter to release the box.  i hit the right arrow to follow the link, and say yes to the POST_DATA prompt..

on the first try it tells me that i can only perform one search every 15 seconds.  thinking that i have a cached copy of the repeated search, i go back and hit Ctrl-RightArrow to send the textbox data without using the cached copy of the page... same result.  

Tried a few different ways, uninstalled, purged, and reinstalled elinks, still no luck... 

google and forums haven't yielded anything that i've found.  anyone else had a similar problem?  or have any suggestions to read/search/try?


*thanks for taking the time to wade through my rambling text *:)

--ck[sktx];.

I just checked and I have the same problem with these forums in elinks also, odd.  

I also use a bunch of apps in screen (you're right it is incredible) but tend to neglect elinks in favour of firefox..

---

### Post by gorilla on 2006-09-07
Does anybody know how (if) it is possible to use links2 -g without being root? 
It does work as user when started under X, but not in a terminal

---

### Post by sktx on 2006-09-16
> **Kindred said:**
> I also use a bunch of apps in screen (you're right it is incredible) but tend to neglect elinks in favour of firefox..

I do as well when I'm running X, but I'm working on putting together a decent set of software to use from the console, so I only have to start X when I need video..

---

### Post by davebgimp on 2006-09-17
I've just tried links for the first time and I'm surprised at how well it works, though I cannot seem to log into this forum with it.

---

