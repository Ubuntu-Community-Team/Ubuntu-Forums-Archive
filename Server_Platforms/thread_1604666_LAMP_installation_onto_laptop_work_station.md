---
title: "LAMP installation onto laptop work station"
date: 2010-10-24
forum: Server Platforms
---

### Post by jauntybluefish on 2010-10-24
Hi,
I hope that this is in the right forum.
I tried installing LAMP onto my Jaunty laptop and it went horribly wrong so I now have a clean install with Lucid and want to try again.

I just want to make sure I have the right idea here.
I want to use my laptop to develop web sites and test them locally on the same machine.
Is that the proper use of LAMP? Should I actually install it on another computer?
I want to test mainly Wordpress and Joomla! installations, but also some static sites too.

Grateful for any replies.
Andy

---

### Post by gyussz on 2010-10-24
Hey!

Try this way, easy and great: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by krishnandu.sarkar on 2010-10-24
I'd suggest not to go with XAMPP in Linux. Better use sudo tasksel install lamp-server.

If you want to do everything manually look at this : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by gyussz on 2010-10-24
> **krishnandu.sarkar said:**
> I'd suggest not to go with XAMPP in Linux.

Why not?

---

### Post by jauntybluefish on 2010-10-24
Thank you for that. It looks simple enough.

Just a couple of questions I did not see answers to on the Xampp page, just to settle my mind on those things.

If I install through sudo apt-get I believe it goes into a folder called www.
Why does installing xampp the way shown on the linked page not do the same?

Also, last time when I had problems I could only start my Desktop from a reboot or log out via a terminal by using  the command 'xstart'. 
The commands shown to stop xampp on the linked page are most likely what I should have used but I did not know. Does that sound likely.


Thanks again
Andy

Boy you guys are fast...so there are two different ways.
Which one to go for though.!!

---

### Post by krishnandu.sarkar on 2010-10-24
> **gyussz said:**
> Why not?

Well...XAMPP is mainly intended for Windows. And why to depend on some 3rd Party packages..??

We can keep ourself upgraded using LAMP stack.

XAMPP is not at all LAMP.

And we are bound in many ways in XAMPP. In LAMP everything is in our hand.

And the main thing is support. Ubuntu forums or IRC channels won't help us if anything goes wrong with XAMPP or even if we want any other help. As it's a 3rd Party package.

---

### Post by gyussz on 2010-10-24
> **jauntybluefish said:**
> If I install through sudo apt-get I believe it goes into a folder called www.
Why does installing xampp the way shown on the linked page not do the same?

XAMPP using htdocs as the www folder, which could be changed to anything. I was just suggesting it because I've been using it for years, without any problems. 

Of course different people, different needs, etc. :)

---

### Post by jauntybluefish on 2010-10-24
Thank you both. I believe I will go for LAMP, but it is always good to know about the alternatives.
.

I reckon it must be possible to run multiple sites using Wordpress or whatever. Just takes a little thought to make it well organised I suppose.

Andy

---

### Post by krishnandu.sarkar on 2010-10-24
> **gyussz said:**
> XAMPP using htdocs as the www folder, which could be changed to anything. I was just suggesting it because I've been using it for years, without any problems. 

Of course different people, different needs, etc. :)

Well...I'm not saying XAMPP is not good. But it's primarily for windows. And if we use ubuntu's repo packages we'll get updates and bug fixes though update manager. But in case of XAMPP we need to depend on them.

> **jauntybluefish said:**
> Thank you both. I believe I will go for LAMP, but it is always good to know about the alternatives.
.

I reckon it must be possible to run multiple sites using Wordpress or whatever. Just takes a little thought to make it well organised I suppose.

Andy

Yes of course. Just use diff folders at /var/www for diff sites.

---

