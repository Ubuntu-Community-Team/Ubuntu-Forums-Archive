---
title: "General web design question"
date: 2010-01-12
forum: The Cafe
---

### Post by Arbiter on 2010-01-12
Hi all-

I'm getting into web design - I've already taught myself HTML/CSS and am getting started into PHP/MYSQL.

I have a question related more to updating website content than anything else.  I have a website for my band and I simply want to be able to post updates without having to keep on going back and modifying code.  I know companies have websites that get updated through systems called CMS's that are way over my head- all I want to do is be able to issue updates to my website.  What tools allow me to do this with an existing site that I don't have to retool?

I appreciate everyone's help and insight in advance for this. :D

---

### Post by Arbiter on 2010-01-12
Anyone?

---

### Post by sandyd on 2010-01-12
-> Joomla or some other open source cms

---

### Post by lykwydchykyn on 2010-01-12
A CMS really isn't that hard to set up, though it does mean redoing the site from scratch.  Once you've done it, though, updates are pretty easy and you get the option of having a lot of things you probably wouldn't want to code on your own like forums, blogs, rss, e-commerce, etc.

Drupal is pretty decent and not hard to set up.  I've been helping our public library work up a drupal site, and it's pretty good.

That said, if you really like what you've got already, you can always start inserting bits of php to automate parts you'd rather not mess with.  In this case, what you're really doing is building your own CMS from scratch.  Honestly, it's not that hard to do if you're inclined towards programming; I've built two or three CMS systems for websites I've worked on.  They were all very limited and somewhat buggy though, so I don't recommend that route unless you just want the exercise.

I don't know of any packaged tools to magically automate a static site.  Can you be more specific of what you're envisioning?

---

### Post by AllRadioisDead on 2010-01-12
Without a CMS, you'd have to code some sort of backend for the site where you can administrate it from.

---

### Post by Frak on 2010-01-12
Wordpress, [the best CMS around]("http://www.packtpub.com/award"), and it isn't even a CMS.

---

### Post by MasterNetra on 2010-01-12
OpenLaszlo as a possible replacement for Flash.

---

### Post by Arbiter on 2010-01-14
Well I guess that I could redo the page as it is not all too terribly complex at this point.  I've decided to give Drupal a whirl (hey, if its good enough for the White House, its good enough for me).

I just wish this stuff was simpler to muck about through- I'm learning as I'm creating and while its the best way to do things IMHO, there's a LOT to be said about a well written, concise, manual (something that the Linux community has yet to be able to create).

---

### Post by Matt_Johnson on 2010-01-14
Joomla and Wordpress are the too main very popular ones, but im sure there are some third party or independent programmer that has an open source script.

---

### Post by hessiess on 2010-01-14
> 
I just wish this stuff was simpler to muck about through- I'm learning as I'm creating and while its the best way to do things IMHO, there's a LOT to be said about a well written, concise, manual (something that the Linux community has yet to be able to create).


The problem here is that the web is a combination of multiple different languages which was not designed, it evolved over time from multiple peoples innervations.

If you don't already have one, set up a development server on your local comp.

---

### Post by Mr. Picklesworth on 2010-01-14
> **Arbiter said:**
> Hi all-

I'm getting into web design - I've already taught myself HTML/CSS and am getting started into PHP/MYSQL.

I have a question related more to updating website content than anything else.  I have a website for my band and I simply want to be able to post updates without having to keep on going back and modifying code.  I know companies have websites that get updated through systems called CMS's that are way over my head- all I want to do is be able to issue updates to my website.  What tools allow me to do this with an existing site that I don't have to retool?

I appreciate everyone's help and insight in advance for this. :D

There is an option beyond the crazy complicated CMSs. (Not a fan :P). check out the [Django web framework]("http://www.djangoproject.com/") - or Ruby on Rails if you prefer.

For my [last web site]("http://stuartmccall.ca/"), I used Hyde, which makes use of Django (and is closely derived from AYM CMS). The beautiful thing is that it produces static web pages, so you don't need fancy dynamic web hosting (and it is super efficient if you happen to have a high traffic web site where that matters). It uses Django's templating engine so that it's really easy to manipulate your content and build the site again.

For that web site I did, for example, a new gallery page can be added by creating a single file. That file doesn't contain a line of HTML; just a list of images in YAML format, a title and a summary. My gallery template does the rest. (All the other pages are done more conventionally, with HTML). The navigation is automatically updated to match when I run Hyde's generator.

AYM CMS: [http://aymcms.com/](http://aymcms.com/)
Hyde: [http://ringce.com/hyde](http://ringce.com/hyde)

---

### Post by ronniestamps on 2010-01-14
> **Mr. Picklesworth said:**
> There is an option beyond the crazy complicated CMSs.

Only complicated IF you are designing the CMS yourself. Joomla/Drupal take that out of the equation.

> **Mr. Picklesworth said:**
> The beautiful thing is that it produces static web pages, so you don't need fancy dynamic web hosting (and it is super efficient if you happen to have a high traffic web site where that matters). 

All you need is a web server that runs php and mysql. 99.99999% hosts provide that. Nothing fancy about that at all.

Setting up a Joomla site is scary easy. So easy that I feel bad for charging my clients to build them. Takes almost no knowledge and less than 20 minutes to setup, including file upload time.

To even further simplify the process, there are tons of templates available, some free and some paid.

Templates:
[www.rockettheme.com](www.rockettheme.com)
[www.shape5.com](www.shape5.com)
[www.joomlabamboo.com](www.joomlabamboo.com)

And further more, if you go to extensions.joomla.org you will find THOUSANDS of extensions to do WHATEVER you need, from ecommerce to real estate to whatever else you can think of. BTW, everything I said also applies to Drupal, I just chose Joomla as my platform. And since you are getting into php/mysql, you can start by writing your own extensions.

While everything Mr. Picklesworth has stated about ruby on rails and such is valid, for a beginner or even intermediate to professional, Joomla/Drupal are major contenders and should be HIGHLY considered before you determine your direction. Especially considering you already know half of what those 2 are based on and are getting into EXACTLY what they are based on... php/mysql.

---

### Post by 23meg on 2010-01-14
If you want it simple, take a look at [Texty]("http://www.texty.com/"), and [Unify]("http://unify.unitinteractive.com/").

---

### Post by hessiess on 2010-01-14
> 
Only complicated IF you are designing the CMS yourself. Joomla/Drupal take that out of the equation.

And add a significant amount of useless `feature' bloat which is of no use whatsoever unless you were developing a large, complicated website.

---

### Post by SeanHodges on 2010-01-14
> **Arbiter said:**
> I just wish this stuff was simpler to muck about through- I'm learning as I'm creating and while its the best way to do things IMHO, there's a LOT to be said about a well written, concise, manual (something that the Linux community has yet to be able to create).

There are many well written, concise, manuals for all sorts of open-source software. But you have to pay for them because they cost time and money to produce.

This might be what you're looking for:

[http://www.amazon.com/Drupal-Dummies-Lynn-Beighley/dp/0470556110/ref=sr_1_7?ie=UTF8&s=books&qid=1263465549&sr=1-7](http://www.amazon.com/Drupal-Dummies-Lynn-Beighley/dp/0470556110/ref=sr_1_7?ie=UTF8&s=books&qid=1263465549&sr=1-7)

---

