---
title: "Get the Facts Straight"
date: 2007-04-17
forum: Testimonials &amp; Experiences
---

### Post by handyguy33 on 2007-04-17
I just looked into  the M$ "Get the Facts" campaign, and I have to say: $40+ billion and Gates and Company are actually scared enough of Linux to start a completely unsubstantiated and biased smear campaign? How can a free, open source OS get a reaction like that? Bottom line, if you want to use windows, go ahead. But don't try and convince me that windows will ever make a better server than Linux. When I started as netadmin at the company I am at, we used Windows server, and had no end of strife. Eight months ago, we switched to Ubuntu server, and the only times that we have had to reboot, has been for physical maintenance and cleaning. Aren't three quarters of the world's websites running on LAMP servers? Does that sound like an unreliable program (or a reason to trash-talk a reliable one)?

Get the facts, Microsoft. Nobody stole source code to create my OS.

---

### Post by wheels. on 2007-04-17
too funny.
I remember reading that article not so long ago and laughing to myself.

heres a couple links for everyone to read
microsoft story
[http://www.microsoft.com/windowsserver/facts/default.mspx](http://www.microsoft.com/windowsserver/facts/default.mspx)

[http://www.eweek.com/article2/0,1759,1925503,00.asp](http://www.eweek.com/article2/0,1759,1925503,00.asp)

Company telling M$ to fix ads
http://news.com.com/Ad+watchdog+warns+Microsoft+to+'Get+the+Facts'/2100-1016_3-5323672.html

---

### Post by Geekkit on 2007-04-18
I think the one that really caught my attention was the article (or one of the articles) on security. I was at a Sourceforge page and saw an ad from Google on the page that contains the caption "The facts on Linux vs. Microsoft". At first I had actually thought this was another left over from April fools.

I clicked on the link and went to the section about security. I really couldn't believe what I was reading. I mean the author of the article was actually serious. He was writing about Windows being more secure than Linux.

I became baffled with this and thought "there's no chance anyone's going to fall for this malarky." Then I realized that thousands of people buy lottery tickets, send money to 419 scams, buy hair restore potions from China, and figure they'll never get addicted to crystal meth.

It's going to be an uphill battle methinks. *sigh*

 :-?

---

### Post by r3m0t on 2007-04-18
The MS campaign is awful. They usually compare a very carefully tuned Microsoft server to a Linux one with (approximately) all the wrong choices.

For example, there was one a long time ago (posted to Slashdot) on webservers. The first test was for static webpages.

For Windows they went into the registry and edited an option so that NTFS would not store the "last access time". (I didn't know about this change until I saw this report.) They also did a lot of other tuning for the filesystem.

For Linux they used the default file system, ext3 (while any sysadmin could tell you they should have changed it to a faster filesystem). They also failed to add "noatime" to /etc/fstab (another change any sysadmin could suggest).

In other words, every time a web page was served, Windows only had to *read* data from the disk, and Linux also had to *write* data (which is many times slower).


For another test, they tested serving webpages over HTTPS. The report said, "the webservers were generally set to the highest security available". "Generally" = "Windows gets to use MD5 (super fast, insecure by modern standards) while Linux gets to use the slow Diffie-Hellman (sp?) key exchange (perhaps 50 times slower, but secure)".

Somehow this reporting company didn't see any problem with selecting the defaults for Linux, while somebody at Microsoft gave them hours worth of beneficial hacks and mods for the Windows server.



Sorry for that rant, just had to get it off my chest... Microsoft are lying scum.

---

### Post by rillip on 2007-04-18
You really have to admire their ability to spin.

Take the statement from AMD. They might be getting "five nines" off of Linux, but their Windows performance is good too (who knows, they don't address Linux at all).  All that AMD said is that Windows is nice.  I can accept that.

The very next statement is someone else saying Linux has a long learning curve. He doesn't say Window's doesn't, or that you can even do what he's proposing in Linux, he just says setting up a Linux cluster is hard.  I can accept that.

But the effect of all these unrelated statments being grouped together like this is to make it look like everyone loves Windows and thinks Linux is hard, even though if you posed that question to any of these people, I would gaurentee they would not make that statement.

Random statements does not a fact make.

---

### Post by earobinson on 2007-04-18
glad to know I have been wrong all these years

---

### Post by earobinson on 2007-04-18
glad to know I have been wrong all these years

---

