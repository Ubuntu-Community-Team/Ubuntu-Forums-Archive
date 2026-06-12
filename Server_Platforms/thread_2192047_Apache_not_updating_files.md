---
title: "Apache not updating files"
date: 2013-12-05
forum: Server Platforms
---

### Post by 14.rileyevans on 2013-12-05
hi
I'm using apache2 to host a website on my computer. when i first used it everything was fine, but when I came to change the pages for an update they didn't change I managed to get it too work eventually b[FONT=arial][/FONT]ut I had to remove it and reinstall it. This doesn't seem right to me. Now I've come to update it again and its still not updating. what am I doing wrong, I'm putting all the files in the www folder and restarting apache. The web address is kvjuniors.zapto.org if the page is orange then it hasn't updated it should be grey atm. please try and keep your answers simple in a bit of a newbie.

---

### Post by tgalati4 on 2013-12-05
Sometimes you have to clear the cache within the browser to get the updated page to load correctly.  It can be a pain if you are making a lot of small changes.  The alternative is to use 4 browsers:  opera, chrome, chromium, firefox, and rotate between them for each update.

---

### Post by 14.rileyevans on 2013-12-08
ive tried that several times and nothing has happened its still the same if you visit this link   then the colours should be grey and red but they are orange and red which is the bit ive changed you check to see if its cache because you wont have viewed the website before

---

### Post by bigmonmulgrew on 2013-12-09
It appears to be down completely at them moment. I'd agree on using multiple browsers in general as well as to help with your problem. I always test on IE, FF and Chrome as a minimum.

Are you hand coding this or are you using some form of CMS. Just wondering because if your using a CMS the CMS may be caching the page rather than the browser. It does sound like your hand coding though when you said change the pages. Do you have anything that caches pages internally on the sever in your website code if not using a CMS.

---

### Post by 14.rileyevans on 2013-12-10
Fixed the website didn't set the dns redirect to update automatically. Im hand coding this and Im not aware of anything that caches pages unless its a default in apache I've just installed it and put the files in the folder and used it. I've tried restarting it. as far as i know there is nothing that caches the website page unless dreamweaver has added it. I've looked through the code and I have have found some things that might be it but im not sure
```
<html lang="en" class=" js flexbox canvas canvastext webgl no-touch geolocation postmessage websqldatabase 
indexeddb hashchange history draganddrop websockets rgba hsla multiplebgs backgroundsize borderimage borderradius 
boxshadow textshadow opacity cssanimations csscolumns cssgradients cssreflections csstransforms csstransforms3d 
csstransitions fontface video audio [COLOR=#ff0000]localstorage sessionstorage[/COLOR] webworkers[COLOR=#ff0000] applicationcache[/COLOR] svg inlinesvg smil svgclippaths">
```
the 'local storage' , 'sessionstorage' and 'applicationcache' concern me would this be caching the page I didnt add this.

---

### Post by sandyd on 2013-12-11
> **14.rileyevans said:**
> hi
I'm using apache2 to host a website on my computer. when i first used it everything was fine, but when I came to change the pages for an update they didn't change I managed to get it too work eventually b[FONT=arial][/FONT]ut I had to remove it and reinstall it. This doesn't seem right to me. Now I've come to update it again and its still not updating. what am I doing wrong, I'm putting all the files in the www folder and restarting apache. The web address is kvjuniors.zapto.org if the page is orange then it hasn't updated it should be grey atm. please try and keep your answers simple in a bit of a newbie.

Where are you placing the files - it seems Ubuntu is using the default welcome page right now

---

### Post by 14.rileyevans on 2013-12-11
> **sandyd said:**
> Where are you placing the files - it seems Ubuntu is using the default welcome page right now
they are in the www folder my index.html had just got deleted by mistake should be working now

---

### Post by bigmonmulgrew on 2013-12-11
its grey here

---

### Post by 14.rileyevans on 2013-12-11
> **bigmonmulgrew said:**
> its grey here
yeah ive reinstalled the server again to get it to work i think apache is caching files automatically with out me knowing is there any settings that i should change. it seems to be on as default and i dont know how to disable it

---

### Post by bigmonmulgrew on 2013-12-11
Have you tried making a change and checking it form another web browser or device? 

The default settings should be fine. I think Apache has the cache turned off by default anyway but you can check by going to /etc/apache2/mods-enables and see whats there. List whats in that directory and post the results but none of the cache stuff should be turned on by default.

---

