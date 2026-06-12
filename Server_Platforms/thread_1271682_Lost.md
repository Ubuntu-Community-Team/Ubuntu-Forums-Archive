---
title: "Lost"
date: 2009-09-21
forum: Server Platforms
---

### Post by illogical on 2009-09-21
That's it in one I'm lost, here's the situation.
Myself and 3 other people co-own a website, I do the day to day admin tasks, my friend Erik setup the whole thing, customised some code etc etc, the other 2 basically just socialize and make things plesant for members.
Now the problem, unfortunately Erik died 2 weeks ago he was suffering from Hodgkin's disease which was only discovered in June this year in very late stages.
So to the point of this post, I have built a basic second PC and installed Ubuntu AMD64 0n it.
I have 100% backup of site, what I want to do is have the site running from that PC, just for me to do testing and learn, phpBB, mysql or whatever I need to continue the work Erik had started.
Also this will help in dealing with any problems we may get on the real world site also.
What do I need to install to launch the site, do I need more software like Apache etc, I am at a loss how where or when.
Any help will be greatly appreciated.

---

### Post by fela on 2009-09-21
To get a basic web server running all you need is LAMP:

Linux, Apache, MySQL and PHP.

Search for these packages (of course not Linux, you already have that ;)) in Synaptic on the server, install them and try and access [http://localhost](http://localhost) on the server. It should say something like 'It Works!'. If so it's all setup and all you need to do is place your website files in /var/www on the server, and you're good to go.

If you want to do some web coding you should learn PHP, HTML, Javascript etc although none of it is really necessary to create a website using something like [drupal.]("http://www.drupal.org") It is good to learn though. You should also learn the basic syntax of MySQL (administrative commands) just so it's easier to administrate your mysql (database) server.

---

### Post by Bachstelze on 2009-09-21
If it's just phpBB, you'll need a compatible web server (e.g. Apache), PHP and a compatible SQL database (e.g. MySQL or PostgreSQL). Then you can just install another instance of phpBB on your test server, and restore the database from your backup so you will have an exact cpy of your live webside.

---

### Post by illogical on 2009-09-21
Unbelievable how quick you folks are, superb!!
Here's a screnshot of what I have saved.
[IMG]http://img.villagephotos.com/p/2004-10/847577/DIR.jpg[/IMG]
Fela, do I copy the whole lot of that into the directory you specified ?
I used cPanel to make a current backup, downloaded it, then extracted and that lot is the result.
So I'm guessing once I install the needed software, Apache etc, I could just extract the downloaded backup TAR file into, /var/www
Is that directory on the harddrive or do I create it, sorry for not looking but don't have access to that machine right now.

---

### Post by fela on 2009-09-21
I don't think all that should go in /var/www, well it should but I don't think you can just dump it all in there...I need to know the configuration of your website to know where to put it all.

And yeah, /var/www will be there automatically if you have Apache - it might even be there as soon as you install Linux (I think it is actually).

---

### Post by illogical on 2009-09-22
Ok here's a link;
[http://www.genesis-sp.org/social/index.php](http://www.genesis-sp.org/social/index.php)
You will see the links from there to the various sections/boards, in addition we have a fourth board for Administrators and Moderators to post which is only visible to those with permissions set, this is the stuff I do day to day using the ACP.
C Panel etc and the Parallels Power panel are a whole new ball game, my aim is to see on my PC more or less the same as on the Vps/Parallels Panel, so I can learn without destroying the real world site.
The list I posted was showing the extracted data from a full system backup, there are options to do selective backups from cPanel if thats any use.
Thank you for your time replying to this.

---

