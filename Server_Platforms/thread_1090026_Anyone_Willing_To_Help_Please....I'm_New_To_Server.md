---
title: "Anyone Willing To Help Please....I'm New To Servers ???"
date: 2009-03-07
forum: Server Platforms
---

### Post by jeffsa12 on 2009-03-07
I have a functional web page, jeffstory.org on my virtual server that is working fine, so I have figured out some basics. However, I have been searching for days without luck for the following.



What my question is and I can't figure out is I want to add "pages" to it so I guess it would be a website then?

EXAMPLE:

[http://jeffstory.org](http://jeffstory.org) takes you to my webpage.

I would like to add subdirectories with different content within [http://jeffstory.org](http://jeffstory.org)

Such as [http://jeffstory.org/secondpage.html](http://jeffstory.org/secondpage.html) would take you to a similar looking page with different text, and have the same link buttons to either return to the home page, or go to say thirdpage, etc, etc.


I have active links to completly different websites such as ubuntu.com, but I want to add active links to my own, additional pages.

Additional details on my previous post: 
[http://ubuntuforums.org/showthread.php?t=1087946](http://ubuntuforums.org/showthread.php?t=1087946)


Thanks in advance for any help with this!!

---

### Post by smooch101 on 2009-03-07
visit my guide on webservers in ubuntu if thats what you want:
[http://adsinoz.com/ubuntu-lamp.html](http://adsinoz.com/ubuntu-lamp.html)

---

### Post by Don1500 on 2009-03-07
> **smooch101 said:**
> visit my guide on webservers in ubuntu if thats what you want:
[http://adsinoz.com/ubuntu-lamp.html](http://adsinoz.com/ubuntu-lamp.html)

Well, that don't work.:(

---

### Post by ruipedroca on 2009-03-07
Maybe Joomla is what you're looking for?..
Or google for "wysiwyg".

---

### Post by Gramps on 2009-03-07
This should work create the file page2.html and put it in the same directory as your index.html file and use the following code to create the link on you page(s)

```
<a href="page1.html" accesskey="1" title="">Page 1</a>
```

You can name the pages anything you like, say about.html test.html etc

This might have been better posted in Development & Programming as this really isn't a server issue but a programing question.

---

### Post by Dr Small on 2009-03-07
> **Gramps said:**
> This should work create the file page2.html and put it in the same directory as your index.html file and use the following code to create the link on you page(s)

```
<a href="page1.html" accesskey="1" title="">Page 1</a>
```

You can name the pages anything you like, say about.html test.html etc

This might have been better posted in Development & Programming as this really isn't a server issue but a programing question.
err, what is the **accesskey="1"**? I've never heard of that.

---

### Post by lykwydchykyn on 2009-03-07
I made the mistake for years of doing all my web pages by hand in an HTML editor; I didn't know any better.  Don't do it that way.

You want to get a content management system for your site.  Either that or learn a web programming language like PHP and roll your own.  

Joomla was mentioned, php-nuke is another option, and there are tons of others.  There are also wikis as well.  You might just want to do a search on "content management system" and see what looks good to you, as they tend to vary greatly in features and target audiences.

---

### Post by mrsteveman1 on 2009-03-07
The path of least resistance is going to be [Wordpress]("http://wordpress.org/") for a new user, the others are great but Wordpress has a LARGE user base, very robust plugin support, and lots of support available. You can make fairly nice sites with Wordpress if you know what you are doing, and it has great editing tools. See the link in my signature to see what its possible with minimal effort.

---

### Post by hyper_ch on 2009-03-08
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read

---

### Post by koenn on 2009-03-08
> **lykwydchykyn said:**
> I made the mistake for years of doing all my web pages by hand in an HTML editor; I didn't know any better.  Don't do it that way.

You want to get a content management system for your site.  Either that or learn a web programming language like PHP and roll your own.  

Hand-coded html is an good way to learn html, and to get an understanding of how a web site works. Creating a (small) website by hand and learning how to reference pages in the same or other directories is an excellent excercise.

Knowing the basics is indispensible, even if you later switch to WYSIWYG drag'n'drop tools, content management systems, wiki's, etc.

"Learn PHP and roll your own [web content management system]" is not really useful advice for someone who doesn't know how to create a hyperlink.

---

### Post by drubin on 2009-03-08
> **Dr Small said:**
> err, what is the **accesskey="1"**? I've never heard of that.

It is xhtml standard it allows for shortcut keys being assigned to links. I haven't really see it being used with website only mobile's :)

---

### Post by jeffsa12 on 2009-03-08
I want to thank everyone who left a reply to this thread. I have got more than I hoped for regarding reference material locations and suggestions in general!!!

As for my problem with linking additional pages to my web page....The problem was me not knowing basic HTML and XHTML. I was off in the wrong direction looking for a problem in LAMP configuration, and spent a good deal of time looking before I came here for help. 

I'm going to slow down and try to learn website code basics, implementation, development, along with learning to utilize the LAMP tools and try to at least get a grasp on some basic PHP fundamentals.

I see this new direction my computer interests have taken me as quite challenging at this point!! As a hobby, I'll be happy if I just move forward without stopping the learning process, and stay interested long term, regardless of the length of time it takes. 

It appears mastering all this would take YEARS if I did it every day as a job. I just hope by the time I get a grasp on all this, the whole technology of TCP/IP doesn't get replaced by something completely different that renders all current website tools unusable!!

I want to leave a link to my other thread for any server/website newbies that may stumble upon this. Here's the link [http://ubuntuforums.org/showthread.php?t=1090026](http://ubuntuforums.org/showthread.php?t=1090026)

---

### Post by lykwydchykyn on 2009-03-08
> **koenn said:**
> 

"Learn PHP and roll your own [web content management system]" is not really useful advice for someone who doesn't know how to create a hyperlink.

It would have been useful advice to me before I found out about PHP.  Everyone's a critic I guess.

I'm not talking about HTML by hand.  I'm talking designing a site page-by-page in any kind of editor.  That's a dead end.  Learning experience?  I guess doing anything the wrong way is a learning experience.

---

### Post by koenn on 2009-03-09
> **lykwydchykyn said:**
> It would have been useful advice to me before I found out about PHP.  Everyone's a critic I guess.

I'm not talking about HTML by hand.  I'm talking designing a site page-by-page in any kind of editor.  That's a dead end.  Learning experience?  I guess doing anything the wrong way is a learning experience.
whatever.

---

### Post by windependence on 2009-03-10
I thought you were being sarcastic. You actually were serious. Coding by hand is the best thing you could do first to learn. When you use a WYSIWYG editor, you always have to tweak the code a bit to make things right. Hand coding experience is indispensable for this type of thing.

-Tim

---

### Post by lykwydchykyn on 2009-03-11
> **windependence said:**
> I thought you were being sarcastic. You actually were serious. Coding by hand is the best thing you could do first to learn. When you use a WYSIWYG editor, you always have to tweak the code a bit to make things right. Hand coding experience is indispensable for this type of thing.

-Tim


I did not mean hand coding HTML vs. WYSIWYG.  I explained myself poorly.  I meant doing a website one page at a time -- in any kind of editor.

The point is, I did a website years ago where I wanted it to be like every other website out there that had basically the same look and feel on every page, but just different content.  I knew nothing about php, content management systems, wikis, or any of that.  I knew about HTML.  SO I made a template and just copied in the different text for each page by hand.  

When I wanted to change out a graphic on the site, I had to change every page.  When I wanted to change a link in the navigation, had to change every page.  You get the picture.

After I gave up on doing that site, partly because the maintenance was so awful, I learned PHP and figured out how to make dynamic sites.  Even a small amount of PHP knowledge can go a long way.

(Actually I learned about server side includes before I learned about PHP, but that still meant having a separate .html file for every page on the site).

Obviously, you can't get much done with PHP if you don't know how to hand-code HTML.

Does that better explain what I meant?

---

### Post by windependence on 2009-03-13
Yep. Whew, for a minute there I thought you were actually serious and it didn't fit your normal posting here. I thought you forgot your coffee. :)

Yes, css helps immensely too, but PHP is da bomb in my book also.

-Tim

---

### Post by neilevan814 on 2009-03-13
Yeah PHP is awesome and I have finally started to really understand the language and build a content management system, but I started on my program language learning about 7 years ago with basic html hand coding and have slowly and steadily learned.  CSS is also a great accompaniment to any language.

---

