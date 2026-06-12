---
title: "Allowing a client to change their website"
date: 2010-01-20
forum: The Cafe
---

### Post by blazemore on 2010-01-20
Hi all,

I run a small website for a client, and he often needs to put bulletins up on the home page, just simple things like "Sorry, we're closed tomorrow night"

At the moment, he emails me and I edit the page and put it up. Waste of everyone's time.
What's the easiest way to allow him to have a bulletin at the top of the page that he can change really easily (preferably by emailing a special address), bearing in mind this guy knows NOTHING about computers.

My initial ideas are Twitter (Message length too restricted)
and Cutenews (Too complicated / overkill)
A custom solution (I'd have to learn PHP)

---

### Post by airtonix on 2010-01-20
nevermind.

---

### Post by Nerd King on 2010-01-20
I've given clients a simple php-driven admin area for years, and even the clueless ones didn't manage to mess anything up too badly :)

---

### Post by blazemore on 2010-01-20
I can't justify porting a site over to a new CMS

---

### Post by Xbehave on 2010-01-20
[LIST]
[*]Php/python/etc to parse a file (at runtime)
[*]An existing CMS
[*]A simple script that (at "compile" time to create a valid HTML file that is displayed (preferably in a frame to isolate errors))
[/LIST]

---

### Post by NoaHall on 2010-01-20
Make a small form for him, with a password to use, and then either read from a file and put it on the site where you want, or use a database.

---

### Post by whiskeylover on 2010-01-20
blogger.com
Open a new blog, change its template to match your website's. Then have him add blog entries to it.
You can enable/disable archives, comments etc.

Blogger lets you **email **your post too. They give you a custom email address that you send an email to from the specified email address. It automatically gets posted on the blog.

---

### Post by ukripper on 2010-01-20
[http://tips.webdesign10.com/drupal/about-drupal-311.html](http://tips.webdesign10.com/drupal/about-drupal-311.html)

---

### Post by Techsnap on 2010-01-20
The best thing you can do lock template elements and give him the corresonding page to edit where he can only edit the text. The CSS and everything else will be uneditable, sure it can still break but it's less likely too and then at least it's only one page.

If you want to be real prehistoric you could use iframes! :?

To those who have suggested changing the whole site:

> **I can't justify porting a site over to a new CMS**

---

### Post by whiskeylover on 2010-01-20
Just use blogger. You wont have to touch your existing website. All you would need to do would be to create a blog, and make it look like your website (including navigation links and all.) You can also use wordpress instead of blogger, by the way.

---

### Post by lovinglinux on 2010-01-20
I thought about twitter too. There are several CMS platforms with twitter interaction. I'm currently using it on my site to post quick news about my application development. It is quicker than logging into the CMS and creating an article.

---

### Post by hessiess on 2010-01-20
I know you have already said you don't want to use a CMS, but if you want to alow any sort of end user editiability, it is the only way. Additionally static HTML websites are an absolute nightmare to maintain at the best of times.

---

### Post by aysiu on 2010-01-20
I've set up Wordpress blogs for folks (if you have your own server, it's a snap to upload the free Wordpress files for a MySQL database, and the software is self-updating).

It's really easy then for clients to create new entries, add in images, edit text, etc.

---

### Post by Onyros on 2010-01-20
shtml and server-side includes?

That's the easiest way not to mess too much with an existing static site.

For the .inc file manipulation there are simple and lean PHP scripts out there for the taking.

---

### Post by Frak on 2010-01-20
Learn PHP and make it dynamic. Trust me, it's worth it. All you need is a CRUD (Create, Read, Update, Delete) system.

---

### Post by blazemore on 2010-01-22
I'm using Cutenews, very VERY cut down.
I need to buy a license to remove the "Powered by cutenews" though, it looks silly underneath 1 line of text.

---

### Post by NoaHall on 2010-01-22
> **blazemore said:**
> I'm using Cutenews, very VERY cut down.
I need to buy a license to remove the "Powered by cutenews" though, it looks silly underneath 1 line of text.

You know, it'd be worth it to learn php instead. You don't have to spend money now, and then you can get more jobs in the future.

---

### Post by blazemore on 2010-01-22
Well, I'm starting a module called Web Programming & Scripting in... 3 days.
But my University teaches Python and django I think.

---

