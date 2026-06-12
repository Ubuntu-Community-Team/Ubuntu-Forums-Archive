---
title: "So much to choose from!"
date: 2008-07-22
forum: Server Platforms
---

### Post by John P on 2008-07-22
I am totally new to anything other than MS Windows, and I would like to use a semi-redundant machine as a server. I have a number of websites and I would like to try and run the less important ones from home to see if it is worth hosting all of those sites 'privately'.

My machine has a 1.35 GHz Athlon, 768 Mb RAM and a 120 Gb HDD. I am switching to an ISP which offers a static IP address, 17 Mb down and 1 Mb up, although I can up the upstream transfer rate at the expense of the downstream rate.

Nothing too difficult until I started reading all about the many choices available using Linux, which is definitely what I want to do. It seems that after I have read and chosen one particular option, something else crops up which looks better.

Can someone point me in the EASIEST direction? I have tried loading Ubuntu 8.04 server (more red screens than blue!), so I loaded 7.10 server (gutsy Gibbon) only to find it impossible to load a GUI. (I am not up to working only in text commands).

I would like an easily installed server, a 'lightweight' GUI and advice on how to protect it from the outside world.

With so many options, I am finding it impossible to settle on a realistically sensible option that a complete Newbie is capable of loading and running.

Many thanks

John P

---

### Post by govee on 2008-07-22
I was able to load Xubuntu on a 933Mhz machine with similar amount of RAM, as I also had some problems with the Ubuntu desktop.

---

### Post by f37u5g0d on 2008-07-22
xubuntu is probably the easiest way to get a lightweight gui.  I would say that the easiest web server out there is apache.  Although it was slightly problematic for me it isn't for everybody and all you really have to do is throw your website in /var/www/ and it will be served.

Be warned however there are no good gui's for web server software.  It is all altering configuration files.  Finding the one that is "easiest" to use is trivial when there is no gui as is the case with most of them.

Apache is good but you can also try lighttpd which a friend of mine suggested to me because of it's ease of use.  There are many others though!

---

### Post by cariboo on 2008-07-22
If you really need a gui, install as lightweight a desktop as possible. Consider fluxbox or windwmaker, both are highly configurable and easy to use. They are both available in the repositories for more info on fluxbox look here:

[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

Windowmaker here:

[http://www.windowmaker.info/](http://www.windowmaker.info/)

It doesn't look like there is much going on with windowmaker, but I see they are still adding support in the next version of Ubuntu.

Jim

---

### Post by John P on 2008-07-22
Jim,

Thanks to you for your reply.

Are you suggesting I load say, Gutsy Gibbon as the server and then fluxbox for the GUI? Would it be easier for someone with my lack of experience to load a desktop version and then install a LAMP server onto it?

I am trying also to learn the abbreviations you experienced people use. I imagine CLI is Command Line Interface? I really would struggle with that, and finding a well presented list of sudo commands in one place is not easy, so far. I'll keep looking!

Regards

John

---

