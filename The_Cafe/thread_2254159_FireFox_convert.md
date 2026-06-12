---
title: "FireFox convert"
date: 2014-11-25
forum: The Cafe
---

### Post by pfeiffep on 2014-11-25
I have been a stick in the mud, not wishing to switch from Chromium. I am finding that Firefox is relatively easy to adopt and operates in a  similar fashion as Chromium. I have switched my default browser to  Firefox mainly due to the certificate security issue.         [TABLE]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[/TABLE]

This past weekend I was shocked to find that neither Chrome nor Chromium on Ubuntu LTS warned me about a certificate issue on a site. 

I am a technical advisor and member of a volunteer group; the site in question is a secure site used to log volunteer hours. I was contacted by another member (using Chrome on Windows) stating he received 'peer certificate has been revoked'.
I immediately went to the site using Ubuntu LTS and Chromium - I was NOT presented the same message and was logged in without issue. I further tested the login using Firefox on Ubuntu and received a similar message. I loaded Chrome 
and was logged in. Tried Opera and was denied. Used Windows 7 Chrome, Firefox, and Internet Explorer and was warned. Used my wife's Mac with Safari and was warned. 

**My concern is the Chromium / Chrome implementation on Ubuntu LTS**

         [TABLE]
[TR]
[TD="align: left"]**Denied**[/TD]
[TD="align: left"]**Accepted**[/TD]
[/TR]
[TR]
[TD="align: left"]Firefox Ubuntu[/TD]
[TD="align: left"]Chromium Ubuntu[/TD]
[/TR]
[TR]
[TD="align: left"]Opera Ubuntu[/TD]
[TD="align: left"]Chrome Ubuntu[/TD]
[/TR]
[TR]
[TD="align: left"]Chrome Win 7[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]Internet Explorer Win 7[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]Safari Mac[/TD]
[TD="align: left"][/TD]
[/TR]
[/TABLE]

---

### Post by Dragonbite on 2014-11-25
I ran across a site that would show the certificate error for my wife and I, but not for the gentleman whose site it was.  

It ended up that for some reason my browser would try to go to "http_s_://yadayadayada.com" which produced the certificate error, while his was going to "http://yadayadayada.com" ( no "s") and would not show the certificate error.

I don't know if it is a browser setting, something Linux adds to run automatically, or what.  Does this sound at all like what you are going through?

---

### Post by pfeiffep on 2014-11-25
> **Dragonbite said:**
> I ran across a site that would show the certificate error for my wife and I, but not for the gentleman whose site it was.  

It ended up that for some reason my browser would try to go to "http_s_://yadayadayada.com" which produced the certificate error, while his was going to "http://yadayadayada.com" ( no "s") and would not show the certificate error.

I don't know if it is a browser setting, something Linux adds to run automatically, or what.  Does this sound at all like what you are going through?
I tried both and neither was a recognized address so I'm assuming that the yadayada... wasn't the real url you were attempting. 

If you received a certificate error message when browsing with https and didn't with http that is 'normal' since http requests are NOT secure. 

The scenario I outlined is somewhat similar to what you've explained. As I noted this is related to the browser implementation on the operating system. I tested on the operating systems which were available to me. I wouldn't include all Linux however.

---

### Post by princecharming on 2014-11-28
Oh really, i was also listen about this that FireFox has been converted. But i do not seen what changes are add in this amazing Browser. I want to know that which thing are adding in FireFox as well as which things are removed. How much affected by that changes and how fast the speed is after that.

---

### Post by pfeiffep on 2014-11-28
> **princecharming said:**
> Oh really, i was also listen about this that FireFox has been converted. But i do not seen what changes are add in this amazing Browser. I want to know that which thing are adding in FireFox as well as which things are removed. How much affected by that changes and how fast the speed is after that.I am the Firefox convert - I was a died in the wool Chromium user but a have now made Firefox my default browser.

---

### Post by Dragonbite on 2014-11-28
Once I found out I can synchronize my bookmarks and such between computers with Firefox (and got it to work) I have used Chrome and Chromium very little lately.  They are handy to have around, though, such as when Flash goes "Pththth" and Chorme/Pepper are the only options for Linux.

I tried opening Chrome once in Incognito mode thinking it would only open the extensions set to run in that mode. I was wrong, it seemed to have fired up all of my extensions whether or not it was working.

---

### Post by mikodo on 2014-11-28
> **Dragonbite said:**
> Once I found out I can synchronize my bookmarks and such between computers with Firefox (and got it to work)

Syncing bookmarks, is something I plan to do in my next installs.

What else, can be synced (and such)?

---

### Post by pfeiffep on 2014-11-28
> **mikodo said:**
> Syncing bookmarks, is something I plan to do in my next installs.

What else, can be synced (and such)?Using preferences one is able to choose what to schronize from this list
[LIST=1]
[*]Tabs 
[*]Bookmarks 
[*]Passwords 
[*]HistoryTabs 
[*] Add-ons 
[*]Preferences 
[/LIST]

---

### Post by mikodo on 2014-11-28
> **pfeiffep said:**
> Using preferences one is able to choose what to schronize from this list
[LIST=1]
[*]Tabs 
[*]Bookmarks 
[*]Passwords 
[*]HistoryTabs 
[*] Add-ons 
[*]Preferences 
[/LIST]
Thank you.

I was only aware of backing up the Bookmarks.

I had only seen [Export Firefox bookmarks]("https://support.mozilla.org/en-US/kb/export-firefox-bookmarks-to-backup-or-transfer") before and sure enough, there is a link on that page for [Firefox Sync]("https://support.mozilla.org/en-US/products/firefox/sync") instructions.

---

### Post by Dragonbite on 2014-11-29
> **pfeiffep said:**
> Using preferences one is able to choose what to schronize from this list
[LIST=1]
[*]Tabs 
[*]Bookmarks 
[*]Passwords 
[*]HistoryTabs 
[*] Add-ons 
[*]Preferences 
[/LIST]

And it only does Passwords if you do not have the system set with a Master Password.

---

### Post by Tar_Ni on 2014-11-29
I used to be a Chromium user but I made to switch to Firefox as my main browser.. The fact that it is lagging behind Chorme in terms of updates, that pepperflash was recognized as being the older 11.2 plugin and that I couldn't use it on Windows all were contributing factor for me to go back to Firefox and it's philosophy.

---

### Post by seabird22 on 2014-12-03
Has anyone reported this issue to the chromium development team and has their been a response?

---

### Post by pfeiffep on 2014-12-03
By the time I thought about doing so (the next morning) the server maintenance crew had already fixed the problem. I was not comfortable reporting a "problem" that could no longer be duplicated.

---

