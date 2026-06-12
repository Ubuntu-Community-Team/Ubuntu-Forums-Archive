---
title: "Searching for a CMS"
date: 2009-08-28
forum: The Cafe
---

### Post by silicoid on 2009-08-28
Hi *,

I'm looking for a CMS for quite some time but didn't find anything that meets my requirements. Well, basically I have only one real requirement: I want the CMS to generate the complete site in static html. No comments, guestbooks ot anything like that. Just plain simple html. 

I want to install it on my little server at home, edit websites via browser and let it generate static html sites. Either the CMS itself or a little CGI script would than publish it to the real webserver (ftp or rsync).

There are two resons why I wan't static html:
1. Performance
Right now I have a website with static html. The webserver I'm running on has a lot of domains (> 1000) on it. Every christmas the sites with CMS systems are realy slow or don't work at all. My static html sites run smoothly. 
I don't update my site very much, maybe three to four times a month. Why should the webserver have to go through a interpreter everytime a page is loaded. Smaller footprint -> Less power consumption -> Green IT ;-)

2. Security
Every software has bugs. Static html will never have a security bug and can't be hacked. I can "secure" the CMS at home via htaccess unusual webserver ports and other stuff. So the chance of getting that hacked is quite low.

So does anybody know a simple CMS system for private use that can do static html output? I know that there is a module for typo3 but typo3 is just way to complex and ugly for my taste.

Thanks,
Andreas

---

### Post by Viva on 2009-08-28
What you're looking at is a WYSIWYG editor, not a CMS.

---

### Post by silicoid on 2009-08-28
No, because I don't care about WYSIWYG. I do care about templates. That is the difference between an editor and a CMS. You can do a lot of these things with CSS but not all of it. If i have the typical navigation bar and I add or delete a tree to my site I would have to edit all the other sites.

---

### Post by hessiess on 2009-08-28
> **silicoid said:**
> No, because I don't care about WYSIWYG. I do care about templates. That is the difference between an editor and a CMS. You can do a lot of these things with CSS but not all of it. If i have the typical navigation bar and I add or delete a tree to my site I would have to edit all the other sites.

Write your own, it shouldn't be to hard to make any CMS dump all of the pages to disk. You could even use the Scrapbook addon for firefox to do this.

You could also use PHP to break the site into logical separate chunks using a hand full of include statements, which wouldn't create any noticeable slowdown. Though if you want to be able to edit it in-browser the best option would be to use a templating system which caches compiled pages, and serves from the static cache.

---

### Post by DeadSuperHero on 2009-08-28
I'm a big fan of Joomla! and XOOPS Myself.

---

### Post by silicoid on 2009-08-28
> **hessiess said:**
> Write your own, it shouldn't be to hard to make any CMS dump all of the pages to disk.

I tried that, but to be honest I simply don't have the time and my web application skills aren't that good.

> **hessiess said:**
> 
 You could even use the Scrapbook addon for firefox to do this.


But than I have them on the system where I run firefox. When I access this CMS from work (behind a firewall) I couldn't upload it to the webserver

> **hessiess said:**
> 
You could also use PHP to break the site into logical separate chunks using a hand full of include statements, which wouldn't create any noticeable slowdown. Though if you want to be able to edit it in-browser the best option would be to use a templating system which caches compiled pages, and serves from the static cache.

There would be a slow down. Especially under high load. The other thing is my security point. Having the CMS on the public webserver is a much higher risk than at a private at home.

> **Mr. Psychopath said:**
> I'm a big fan of Joomla! and XOOPS Myself.

They can create static html sites?

---

### Post by Dragonbite on 2009-08-29
> **silicoid said:**
> No, because I don't care about WYSIWYG. I do care about templates. That is the difference between an editor and a CMS. You can do a lot of these things with CSS but not all of it. If i have the typical navigation bar and I add or delete a tree to my site I would have to edit all the other sites.

Yeah, my first thought was an IDE that provides for publishing myself, but if you are looking for templates i am not sure how that all fits in.  

Of course, since I do ASP.NET at work, the fist thing that comes to mind is Visual Studio with Master Pages and publishing features.  Don't know of a non-MS based equivalent.

---

### Post by hessiess on 2009-08-29
> **silicoid said:**
> 
But than I have them on the system where I run firefox. When I access this CMS from work (behind a firewall) I couldn't upload it to the webserver...

... Having the CMS on the public webserver is a much higher risk than at a private at home.

You just contradicted yourself, If you want to be able to edit from anywehere then the CMS HAS to be on a public server.

---

### Post by Mr. Picklesworth on 2009-08-29
[Django]("http://www.djangoproject.com/") is a nice choice here. It is a nice web framework using Python. You can run a small test server locally specifically for your project; no need to install Apache / PHP. It has an incredibly awesome template language, it's flexible, it's easy, it's well designed, well documented and well maintained.

Now, throw in [StaticGenerator for Django]("http://superjared.com/projects/static-generator/") and you're done!

---

