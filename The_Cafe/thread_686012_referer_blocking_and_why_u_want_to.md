---
title: "referer blocking and why u want to"
date: 2008-02-02
forum: The Cafe
---

### Post by nowshining on 2008-02-02
u see every site u visit, and then click on a link, to go to another, the new site u just visited now knows what site u last visited, if u search via a search engine, they know ur previous visits, :( and what u maybe were searching for.

Some sites require it, that's why i posted this because I found this great tool  that lets u disable referers and allow/and forget referers for sites, forge meaning it will send a referer but it will only show that sites url as the last visited link. Also included is a test i set up 


go here and download it: javascript required - noscript users

[http://www.stardrifter.org/refcontrol/](http://www.stardrifter.org/refcontrol/)

if u get an error on downloading, close out the add-on box, right click the download link and save it to ur desktop, next press ctrl + o on ur keyboard, find the .xpi and install it from there, restart.

in the url bar type:

about:config

find these two & do the following:

network.http.sendRefererHeader > double click the 2 and change it to 0 then click ok

&

network.http.sendSecureXSiteReferrer > double click true to false


okay if u want more info on what each does - look under the picture at the refcontrol program/add-on main site 


to test


I was wondering why images/screenshots didn't download :( even tho i knew the images is from the main site  no adblock probs either,

so after forging a refer with this program, it now shows up - and the site i'm going to send u to which is site 2, said that's it's good on refer - it don't send  green smiley means ur alright...


Site1: with refering turned off only visit (yes this is a recent game i downloading for my palm)



[http://www.freewarepalm.com/games/hangman.shtml](http://www.freewarepalm.com/games/hangman.shtml)

u should see no screenshot of the program :(


2.)right-click anywhere on the site and find Refcontrol options for this site,

bubble forge and click ok 

Refresh the freewarepalm page, now the image should show up 


Site2: [http://www.pcflank.com/browser_test1.htm](http://www.pcflank.com/browser_test1.htm)

click start test, then click continue after veryifing ur ip is correct 

Now under cookies - u may see a :( sad face - that means that ur allowing globally cookies to be randomly stored on ur computer - if u see a  happy face - that means that ur allowing on a site per site basis and u haven't allowed pcflank - no need except for the forums of course, but we are concerned with 

Referrer check

u chould see a smiley face - meaning that u have **NOT** sent any referers  and ur privacy is protected  even tho u allowed freewarepalm to see a referrel and u used forge - refcontrol works to control which sites see a refer or which ones u customized and or chosen to send, if not a trusted site then they see nothing of what previous sites u visited.


adding: oh and if u want u can remove the freewarepalm site :)

---

### Post by LookTJ on 2008-02-02
Already installed it, use it, and  block all sites. :D Great addon.

---

### Post by Shazaam on 2008-02-02
+2 :)

---

### Post by macogw on 2008-02-02
I like being able to see where my blog's visitors come from.  It seems most of them are from Google for my Beryl post, but I've also noticed that I get a lot more hits on days when I post on Slashdot because my link is in my profile on there (I see the hits coming from *.slashdot.org/*).  That tells me posting to /. is good for my blog :)

I don't think it's possible to see anything more than exactly from what site you clicked to reach that site.  If you type the URL into the location bar, the referer will be blank.  Sites before the one that linked you to the site should also not be passed.  I don't really see this as something to worry about.

---

### Post by Dr Small on 2008-02-02
Awesome addon, I just installed it!

---

