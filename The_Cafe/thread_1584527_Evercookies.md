---
title: "Evercookies"
date: 2010-09-29
forum: The Cafe
---

### Post by zer010 on 2010-09-29
If you're not aware there is a new cookie out now, the evercookie. [http://samy.pl/evercookie/](http://samy.pl/evercookie/) Does anyone know where all these cookies are hidden and a good way to remove them?  I've heard that Chrome's Incognito mode deters them, but seeing how I use FF, I was wondering if the Private Browsing option does the same.

---

### Post by sydbat on 2010-09-29
> **zer010 said:**
> If you're not aware there is a new cookie out now, the evercookie. [http://samy.pl/evercookie/](http://samy.pl/evercookie/) Does anyone know where all these cookies are hidden and a good way to remove them?  I've heard that Chrome's Incognito mode deters them, but seeing how I use FF, I was wondering if the Private Browsing option does the same.Just set FF to drop all cookies when you close it. Should do the job.

EDIT - Oh, and your link goes to the site of the developer, which is dodgy at best.

---

### Post by Andrew.Z on 2010-09-29
> **sydbat said:**
> Just set FF to drop all cookies when you close it. Should do the job.

Absolutely not enough!  Evercookies hide in multiple places, and you only cover 1 of the current 8 places.  The current implementation includes HTTP cookies, HTML5 cookies, Flash cookies, and several other places. If you delete any one of the places (or even all the places except one), all the others regenerate.  By using Flash cookies also, the evercookie system can track you BETWEEN browsers on the same computer/user profile (which is traditionally hard to do).

[BleachBit 0.8.1 beta deletes evercookies in Firefox, Google Chrome, Opera, and Adobe Flash.](http://bleachbit.sourceforge.net/news/test-bleachbit-081-beta)

---

### Post by t0p on 2010-09-29
But hey, if you have not done anything wrong, there's no need to worry about "evercookies".  Only child pornographers, gangsters and drug dealers have any need to privacy.  The average citizen doesn't care if other people read their mail, track their browsing habits, share your secrets with the world.  Only evil terrorists and kiddie-fiddlers want to keep their private lives private.

Does anyone here keep "dream diaries"?  Well, don't keep them secret: share every gory detail with friends/colleagues/bosses/teachers/neighbours/strangers they meet in the street.  Only crooks and perverts have secrets.

:p

---

### Post by sydbat on 2010-09-29
All I can find about this "evercookie" relates to Windows users. Makes me wonder if it can do anything on non-Windows boxen.

Also, every "story" about it is mostly a copy-paste job of all the other stories.

---

### Post by Lucradia on 2010-09-29
> **sydbat said:**
> All I can find about this "evercookie" relates to Windows users. Makes me wonder if it can do anything on non-Windows boxen.

Also, every "story" about it is mostly a copy-paste job of all the other stories.

windows users can also take advantage of the hosts file blocking as well. So even if you have evercookies, chances are that if you know about them, it doesn't really effect you. :|

Also, who uses LSOs nowadays? Flash does, and I have my flash set to store nothing.

---

### Post by Andrew.Z on 2010-09-29
> **sydbat said:**
> All I can find about this "evercookie" relates to Windows users. Makes me wonder if it can do anything on non-Windows boxen.

It affects all modern browsers with or without Adobe Flash.  In other words, it could affect you if you use Firefox, Opera, Chrome, Konqueror, etc---even if you clear the HTTP cookies and disable Flash LSO.

> **t0p said:**
> But hey, if you have not done anything wrong, there's no need to worry about "evercookies".  

I don't mind most cookies except

1. The creepy advertisements for one camping store that suddenly show up on every other site after I visited that one camping store once
2. Attempts to circumvent privacy methods.  I don't usually clear cookies, but I don't want someone trying to find a way to track me if I do.

---

### Post by BigSilly on 2010-09-29
Whatever it is they do, it can't be a Good Thing because they have to hide them in this manner.

---

### Post by Calash on 2010-09-29
> But hey, if you have not done anything wrong, there's no need to worry about "evercookies".  Only child pornographers, gangsters and drug dealers have any need to privacy.  The average citizen doesn't care if other people read their mail, track their browsing habits, share your secrets with the world.  Only evil terrorists and kiddie-fiddlers want to keep their private lives private.

Does anyone here keep "dream diaries"?  Well, don't keep them secret: share every gory detail with friends/colleagues/bosses/teachers/neighbours/strangers they meet in the street.  Only crooks and perverts have secrets.

:p

> 
Whatever it is they do, it can't be a Good Thing because they have to hide them in this manner.


Oooh....Irony. :P

---

### Post by tjeremiah on 2010-09-29
> **t0p said:**
>  Only child pornographers, gangsters and drug dealers have any need to privacy.  

stupid post is stupid :P

---

### Post by NightwishFan on 2010-09-29
I love bleachbit. I would delete these evercookies on principle. My browsing history has nothing to hide though.

---

### Post by zer010 on 2010-09-30
> **NightwishFan said:**
> I love bleachbit. I would delete these evercookies on principle. My browsing history has nothing to hide though.

I totally agree. Even though I have nothing to hide, I think it IS an issue of principle. 
I installed bleachbit, but I'm not sure if it gets rid of all the instances of evercookies.  I have read that they are in the process of dealing with them.

---

### Post by Andrew.Z on 2010-09-30
> **zer010 said:**
> I totally agree. Even though I have nothing to hide, I think it IS an issue of principle. 
I installed bleachbit, but I'm not sure if it gets rid of all the instances of evercookies.  I have read that they are in the process of dealing with them.

I too agree with the principal.  

Now, I am the author of BleachBit and can tell you [BleachBit 0.8.1 deletes evercookie tracking in Firefox, Google Chrome, Opera, Safari, and Internet Explorer.](http://bleachbit.sourceforge.net/news/test-bleachbit-081-beta) It only took a relatively small change for each browser (deleting DOM Storage) that would have been made even if evercookie was not announced.

Try it yourself: there are BleachBit .deb packages for Ubuntu (including the latest 10.10) on that link.  Visit the evercookie site, create a cookie, run BleachBit to clean the browser *and* Flash, and revisit the evercookie site.  The site should confirm the cookie is gone.  If you are paranoid, do this as a separate user account (guest account) or inside a virtual machine (e.g., VirtualBox).

---

### Post by zer010 on 2010-10-01
Awesome! This is what I LOVE about Linux and Open Source! The chance to hear from the actual authors of favorite apps. Thanks, dude! You rock!:guitar:

---

### Post by metalf8801 on 2010-10-07
BleachBit sounds great but what boxes need to be check to delete the evercookie? If I check all of them I'll lose my firefox bookmarks do I really need to do that?

Thank you
Dan

---

### Post by Andrew.Z on 2010-10-07
> **metalf8801 said:**
> BleachBit sounds great but what boxes need to be check to delete the evercookie? If I check all of them I'll lose my firefox bookmarks do I really need to do that?

Assuming you don't use any other web browsers, you need to delete
* Firefox cache
* Firefox cookies
* Firefox URL history
* Firefox DOM Storage
* Adobe Flash cookies

IIRC, that's it, but you can check yourself on the evercookie site. You definitely do NOT need to delete bookmarks (the "Places" option) or vacuum*.

* Though vacuuming can make or keep a certain part of Firefox running smoothly because it compacts and fragments a file which sometimes gets very bloated.  Vacuuming doesn't delete any data, so it's safe.

---

### Post by MasterNetra on 2010-10-07
Clean with Bleachbit (or your perfered cleaner) if on windows I would recommend CCleaner as a free cleaner. Cleans your system and has a good registry cleaner as well.

Also as suggested set your browser to not save cookies and to clear them out at close. Be warned though at this time browsers do not clear flash cookies, in fact they generally don't even as much know where they are at. If your using firefox you can install better privacy and it will clear those for you at close *(be sure to close any mini windows first such as your addons window as better privacy doesn't trigger if your addon or simlair small window is the last to close. odd but thats how it is.)* 

Initially better privacy will be asking you if you want to clear whatever flash cookies are present *(if any, if none it won't do anything)*, until you let it know you want it to do it automatically, and if their are flash cookies you do want to keep you can go into better privacy and have it keep them.

For any other browser I would recommend periodically running your cleaner, and running a cleaner before your about to do something online that is sensitive (ex. Using your credit card, or logging into your bank account) then running the cleaner afterwards. heh, then again you may wish to do that regardless of what your browser is.

---

### Post by drawkcab on 2010-10-07
> **t0p said:**
> But hey, if you have not done anything wrong, there's no need to worry about "evercookies".  Only child pornographers, gangsters and drug dealers have any need to privacy.  The average citizen doesn't care if other people read their mail, track their browsing habits, share your secrets with the world.  Only evil terrorists and kiddie-fiddlers want to keep their private lives private.

Does anyone here keep "dream diaries"?  Well, don't keep them secret: share every gory detail with friends/colleagues/bosses/teachers/neighbours/strangers they meet in the street.  Only crooks and perverts have secrets.

:p

[IMG]http://www.netcharles.com/orwell/pics/1984/1984-signet1981.jpg[/IMG]

---

### Post by areteichi on 2010-10-17
I discovered this thread as I was looking up 'evercookie' after reading these news articles:
[LIST]
[*][The cookie that never crumbles]("http://www.economist.com/blogs/babbage/2010/10/browsers_track_eternally")
[*][New Web Code Draws Concern Over Privacy Risks]("http://www.nytimes.com/2010/10/11/business/media/11privacy.html?_r=1&hp=&pagewanted=all")
[/LIST]
I agree with the comments that are already made ;)
I think it is rather naive to think that unless one is a pedophile, gang member, drug dealer, etc., there is no reason to be worried about these privacy issues. One can well be manipulated simply in overt ways that do not involve such extreme cases. People are already bombarded by advertisements and political propagandas that their mode of thinking is distorted and skewed in ways that serve those who feed these contents.

While it is important not to condemn innovations (such as HTML5) solely based on privacy concerns, I also think it is important to raise awareness of potential risks they can pose on us.

---

### Post by Austin25 on 2010-10-17
> **areteichi said:**
> I discovered this thread as I was looking up 'evercookie' after reading these news articles:
[LIST]
[*][The cookie that never crumbles]("http://www.economist.com/blogs/babbage/2010/10/browsers_track_eternally")
[*][New Web Code Draws Concern Over Privacy Risks]("http://www.nytimes.com/2010/10/11/business/media/11privacy.html?_r=1&hp=&pagewanted=all")
[/LIST]
I agree with the comments that are already made ;)
I think it is rather naive to think that unless one is a pedophile, gang member, drug dealer, etc., there is no reason to be worried about these privacy issues. One can well be manipulated simply in overt ways that do not involve such extreme cases. People are already bombarded by advertisements and political propagandas that their mode of thinking is distorted and skewed in ways that serve those who feed these contents.

While it is important not to condemn innovations (such as HTML5) solely based on privacy concerns, I also think it is important to raise awareness of potential risks they can pose on us.
Yes, it is wrong to think people don't need privacy. An example: imagine you're an inventor researching a way to accomplish your next invention, and some schmuck tracking where you're going puts together what you're doing, and takes it to the patent office. Then the inventor has to start over.

---

### Post by robsoles on 2010-10-17
+1 bleachbit.

+1 1984.


It wouldn't be so bad if it was all benevolent corporations just trying to figure out what we really might want so as to offer it to us as a bargain in a webpage we will visit soon but even the most altruistic corporation is subject to internal sabotage and external exploits.

---

