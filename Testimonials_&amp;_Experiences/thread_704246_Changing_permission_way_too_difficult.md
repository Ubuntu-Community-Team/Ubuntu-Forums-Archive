---
title: "Changing permission way too difficult"
date: 2008-02-22
forum: Testimonials &amp; Experiences
---

### Post by mikasjoman on 2008-02-22
Hi (READ MY SECOND ANSWER, THEN YOU REALLY GET MY POINT)

I wanted to change permissions for a folder. I hate the terminal, so I just refuse to go over there, I´m one of those human beings you know... Simple as that.

So I right click the folder, see the permission exactly like in OS X, but now there is a very sad difference. I cant change the permission, WTF! I see the permissions in menus and a disturbing message that I can not change the permissions. Hey - this is my computer!

So my question to you is, who should I talk with if I want the developers to copy Apples small button (Authenticate to change)?

This is so disturbing I can not get it out in text. Thanks!

---

### Post by u-foka on 2008-02-22
It may be possible with the new policy kit what will be included in hardy, but it isn't implemented yet... but anyway, you can press alt+f2 enter "gksudo nautilus" and press enter, then it ask's for your password, and you got a file manager window as root, then you can change anything ;) But bee carefull with it ;) because you can break anything too :lolflag:

---

### Post by mikasjoman on 2008-02-22
Actually Ill tell you what I am trying to do. Its so simple, but I cant get it  done = I can´t get on to build homepages since /var/www is locked.

I almost want to log this as a bug, because this is so tremendously stupid. I am almost crying how bad this is.

About 50% of all Ubuntu users may want to do home-pages. And when I try to save in the www folder (that took me loooooong time to find), I can´t save!. My god!  Isn´t this just someting of the most stupid thing you ever heard of? Locking out non command line users from developing homepages on Ubuntu.

Talk about non user friendly for web-developers!

I stick to my guns, I will not use any command line commands for a task that should be as easy as save and done. Could it be fixed in hardy?

---

### Post by u-foka on 2008-02-22
Well, when you run a server, like apache, you need to install it, you can't do that as a simple user, you have to be root to install it, simple right? And you need to configure it too, and remember, it's a system service, so it need's to be root too... You can replace /var/www with a simlink somewhere into your home, or change apache configuration... AS ROOT... And it's correct thet way...

---

### Post by weresheep on 2008-02-22
Ugh. /var/www is a system directory and has its permissions set up like that for good reasons.

Also, there is a reason that changing the permissions of a directory you (your user account) do not own is not a simple task, thats because its a very bad idea.

I believe Apache supports serving web pages from a directory in your home folder. I would suggest searching for some documentation on how to do that rather than trying to force /var/www to use world accessible.

A quick google search found [this](http://httpd.apache.org/docs/2.2/howto/public_html.html) page that details how to serve web pages from your home directory.

-weresheep

---

### Post by gtrtx on 2008-02-22
> **mikasjoman said:**
> My god!  Isn´t this just someting of the most stupid thing you ever heard of?

Not any more stupid than almost crying and declaring that something is "stupid" because you don't know how to properly use it.

---

### Post by mikasjoman on 2008-02-22
Well I can tell you that if I did not call my friend, and he told me that I should create a public_html folder.

it took me five hours! as an experienced computer user for 20 years to start web developing (coming from the os x camp). 

That is just insane. 

Solution: Have the Public_html folder there by default, like it is on the mac (it feels totally natural to just have it there). 
New people to web-development should not have to look or create anything else than their homepages to get started.

Five hours god damit! This should be a 2 minute fix for Hardy that would save thousands of hours for new people to Ubuntu.

Personally I think like this: an ubuntu machine should be delivered like the mac with apache/php from start with a public_html folder by default in your home folder. 
For new webdevelopers it should just be to get started nothing more. This is technology from the 90-s, come on. It should be there from start, not require installation. Everybody does home pages today.

---

### Post by LaRoza on 2008-02-22
Changing permissions is extremely easy from the command line and from the GUI.

(Hint, run Nautilus or whatever file manager you use as root, and change the owner of the /var/www directory. That is usually a bad idea for security reasons.)

Since this is not a support forum, and this thread is has no testimonial value, except that using Apache and Unix based operating systems requires you to know what you are doing, just like every other server and operating system, I am closing this thread.

Keep in mind servers do not typically have GUI's, as it is a waste of resources. If you want to manage an Apache server on a *nix, you will have to learn how.

---

