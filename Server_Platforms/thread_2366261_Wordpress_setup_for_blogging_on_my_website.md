---
title: "Wordpress setup for blogging on my website"
date: 2017-07-15
forum: Server Platforms
---

### Post by Michael_McKenney on 2017-07-15
I need a better way to blog than writing html5 code on my website.  I keep reading about Wordpress for it.   I see I can configure it for Ubuntu.   Does any use it?  Can I look at your site?  If you can't post it on this site, email me the link at <snip>

---

### Post by RobGoss on 2017-07-15
Hello and welcome, WordPress is the best option for just about any website you can think of. I have been using it for years on a self hosting service

It's best if you use a self hosting service to ensure your website stability 

>  I need a better way to blog than writing html5 code on my website   

What do you mean by this? are you writing your own HTML pages? if so were are you hosting them

---

### Post by Michael_McKenney on 2017-07-15
I have a web server at my house.   It holds 4 virtual web sites.  I put them on my HP DL360e Gen8 server under VMware 6 standalone.  email me for a list of them, <snip>].  Last time I posted them the Admins deleted them.   I write a lot of content in HTML5.  I started producing and adding video content in Sony Vegas Movie Studio 14.   I am actually going to start fixing my daugher's videos that were turned sideway by my using my Galaxy.  I can flip them around.   I want a better tool to write and publish to the web site a daily blog.   My blog page got more traffic than I thought it would during Trump's victory over Hilderbeast.

---

### Post by Bucky Ball on 2017-07-15
You can [go to their website and learn all about it]("https://wordpress.com/"). You'll find plenty of examples there. ;)

---

### Post by Michael_McKenney on 2017-07-15
I was curious on how users setup their pages to maximize traffic and the WOW! factor.  I have been on their pages reading everything.

---

### Post by RobGoss on 2017-07-15
> **Michael_McKenney said:**
> I was curious on how users setup their pages to maximize traffic and the WOW! factor.  I have been on their pages reading everything.

If you are truly interested in building your website using **WordPress,** then you'll want to use **WordPress.org **not **WordPress.com** which that link that was provided is their FREE service and you can't do much. If you wanted to keep your content safe then use [WordPress.org ]("https://wordpress.org/") you can read about the different between the two services

With **WordPress.com **you don't need a hosting service, the free service will give you a limited amount of **space** and they will restrict most of the services and features you would get with the WordPress.org service 

Let's just say if you were to pick a hosting service for about **$8.00** bucks a month, once you're all signed up you can then install WordPress in your **C- pane**l in your hosting account  with a one click installation and you get all the WordPress features at no charge. WordPress is FREE but the WordPress.org needs to be hosted with a hosting service

I hope this helps you understand between the two

---

### Post by Habitual on 2017-07-16
[https://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install](https://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install)
[https://codex.wordpress.org/Hardening_WordPress](https://codex.wordpress.org/Hardening_WordPress)

---

### Post by Doug S on 2017-07-16
There is a relatively new section on wordpress in the [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/wordpress.html"). The last time (it was awhile ago) I proof read / tested the section it worked fine.

---

### Post by mastablasta on 2017-07-17
> **Michael_McKenney said:**
> I was curious on how users setup their pages to maximize traffic and the WOW! factor.  I have been on their pages reading everything.

wordpress has plenty plugins. i suggest to install Sucuri, Wordfence and a backup plugin. this should reduce the hackign chances, becuase wordpress sites have ocnstant attacs. 

then you have various SEO plugins such as YOAST. they will help you with maximizing traffic. the most important thing is the text/topic. it should be something that people are interested in. and the better that it is all made (the more relevant it is)  the higher rank you will get in search engine when searching for specific topics.

it helps if you add some pictures. make sure the website is optimised for web (Google Analytics and Pagespeed will help you with all that). Google Analytics will also help you gfind out what people are searching for yon your website and what else they are interested in so you can offer them what they want. 

good luck with your website(s).

---

### Post by Michael_McKenney on 2017-07-17
It will be on my web server at home.  So I was looking for better ways to secure the Ubuntu 16.04 LTS server.   It is behind a Fortinet 60E firewall.  I was going to get their security license package when I renew support.   I have been working on changing pictures and video to lower resolution to get better performance.   I have Google Analytics on one of the 4 virtual servers.   I was trying to get webalizer to work on the four sites.  What is pagespeed?

---

### Post by mastablasta on 2017-07-18
google pagespeed will test your website and let you know where and what you need to optimise.

otherwise general ubuntu hardening should do.

install is easy, like i wrote check a few plugins as the ymake life easier. don't install too many, and definitelly install security plugins. i was hacked on hosted server via wordpress. the host had security in place, but wordpress still needs it's own stuff (at least to monitor the events and to backup).

---

### Post by Michael_McKenney on 2017-07-18
I am going through everything posted so far to make sure I have everything in order.   Any sites to check what I need to hardened on my Ubuntu server first?

---

### Post by SeijiSensei on 2017-07-19
"Hardening" your Ubuntu server is not really the issue with WordPress.  You need to be vigilant about installing upgrades to the WP software when they are released.  Usually they contain security fixes.  WP sites are attacked all the time.  I have posted some more detailed suggestions about WP security here: [https://ubuntuforums.org/showthread.php?t=2356584&p=13626346&viewfull=1#post13626346](https://ubuntuforums.org/showthread.php?t=2356584&p=13626346&viewfull=1#post13626346)

---

### Post by RobGoss on 2017-07-19
Keeping WordPress updated is pretty simple, you can set it up to automatically update when the latest version is released within the WordPress dashboard

---

### Post by mastablasta on 2017-07-19
> **Michael_McKenney said:**
> I am going through everything posted so far to make sure I have everything in order.   Any sites to check what I need to hardened on my Ubuntu server first?

internet is full of such advices. it depends how far you plan to go and what kind of things you have on server i guess.

for example at home i have a personal server which is meant only for specific people (IPs).

so what i did is:
1. automated security updates (unnatended updates)
2. fail2ban with blacklisting setup (1 and up to 3 errors and you are banned - depending on the attempted action)
3. NAT on router allows only certain ports through
4. apache server - access allowed to only a handfull of IPs
5. files and directories are locked down as much as possible
6. admin (sudo) user is separated from other users
7. using SSH with keys & password for sensitive parts like OS access.
8 a few other measures i won't disclose.

it works like this:
if you try to login from wrong IP, you are banned. 
if you managed to get the IP and spoofed it, you need to then guess the user name. if you guessed the username, you need to guess a password,. if you guessed both you still need the key to access it. 2 attempts go wrong and you are banned.

anyway if somoene really went after the server and dedicated time they could probably hack it. but the measures defend against scripted attacks.

---

### Post by SeijiSensei on 2017-07-19
> **RobGoss said:**
> Keeping WordPress updated is pretty simple, you can set it up to automatically update when the latest version is released within the WordPress dashboard

My implementation (see the [link]("https://ubuntuforums.org/showthread.php?t=2356584&p=13626346&viewfull=1#post13626346") I posted above) does not permit the Apache user ("www-data") to write into any of the WP directories except wp-content/uploads/.  This protects the site from being defaced by attackers but also disables automatic updates.  So, in my case, I first run the script described in that link to change the permissions on the WP installation, then run the update manually, then run another script to reset the permissions.

---

### Post by Michael_McKenney on 2017-07-19
I did not think about blacklisting on my site.   I am going to get the UTM licenses for my 60E.   The Fortinet 60E is a great firewall that does a lot of this in the UTM license.

---

