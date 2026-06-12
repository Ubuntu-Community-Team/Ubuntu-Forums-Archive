---
title: "Volunteers to test from outside my lan..."
date: 2007-08-20
forum: Server Platforms
---

### Post by southernman on 2007-08-20
Ok folks, I just want to test and see if the server is actually reachable from outside my lan. You won't see any fancy web page, just the default It works page is all.

I'll leave it open for the next 30 minutes to an hour depending on how many hits I see come through.

Server is an old PII 350 so take it easy on her... a little anyway.

I'd really appreciate if you would hit it and maybe refresh a few times.

[Test me please]("http://steveh.homedns.org")

If you will also leave a quick note to say if you were able to get to me... or not.

Much appreciated!

*mutters... here goes nothing!*

---

### Post by moore.bryan on 2007-08-20
*checked it a couple times for you, with success...*

---

### Post by southernman on 2007-08-20
I hope it's ok to post this here. I posted in the server section, but am being impatient I suppose.

Ok folks, I just want to test and see if the server is actually reachable from outside my lan. You won't see any fancy web page, just the default It works page is all.

I'll leave it open for the next 30 minutes to an hour depending on how many hits I see come through.

Server is an old PII 350 so take it easy on her... a little anyway.

I'd really appreciate if you would hit it and maybe refresh a few times.

[Test me please]("http://steveh.homedns.org")

If you will also leave a quick note to say if you were able to get to me... or not.

Much appreciated!

*mutters... here goes nothing!*

---

### Post by futz on 2007-08-20
It connects, but there's no html there at all. I just get a blank page. When I view source, it's blank.

---

### Post by jakev383 on 2007-08-20
All I got was a zero sized reply.  I turned off squid, and got a blank page here. I'm on a TWC business cable modem.

---

### Post by jgrabham on 2007-08-20
> **futz said:**
> It connects, but there's no html there at all. I just get a blank page. When I view source, it's blank.

Yup, same here.

---

### Post by futz on 2007-08-20
You fixed it. Works now!

---

### Post by gnuman on 2007-08-20
[SIZE="6"]It works![/SIZE]:)

---

### Post by southernman on 2007-08-20
> **jgrabham said:**
> Yup, same here.
Dang... wonder why!? Thanks for the heads up and helping out!

---

### Post by southernman on 2007-08-20
> **moore.bryan said:**
> *checked it a couple times for you, with success...*

So you acutally got the It Works page?

Thanks for giving me a hand! You and Jake both.

---

### Post by qpieus on 2007-08-20
it works

---

### Post by southernman on 2007-08-20
Thanks to you all, one step down... a millon more to go!

I appreciate your time!!! :) *shakes hands* don't worry, I washed 'em!

---

### Post by edd07 on 2007-08-20
Worked for me too. :D

---

### Post by southernman on 2007-08-20
Thanks to you all for lending a hand. One step down and a millon more to go!

edd07 - love the siggy man!

I appreciate your time! *shakes hand* don't worry I washed em!

---

### Post by p_quarles on 2007-08-20
"It Works!"

By the way, I've found that it's possible to test this oneself, too. I've asked other people to test my own page, and there is a 100% correlation between it working for others and it working for me when I plug in my current public IP address.

---

### Post by southernman on 2007-08-20
Thanks for the confirmation. I had tried that but wasn't sure if it was just cached, or actually routing out and back in again.

In a few days, I'll actually put something heavier on it and see what it'll do with a normal sized load... maybe a word press to get a better ideal of loads and responsiveness. A lot of reading, double, triple checking to do still.

btw.. she's unplugged for the time being.

---

### Post by p_quarles on 2007-08-20
> **southernman said:**
> Thanks for the confirmation. I had tried that but wasn't sure if it was just cached, or actually routing out and back in again.

In a few days, I'll actually put something heavier on it and see what it'll do with a normal sized load... maybe a word press to get a better ideal of loads and responsiveness. A lot of reading, double, triple checking to do still.

btw.. she's unplugged for the time being.
Apache is pretty damn efficient. I don't know what your specs are, but it handles quite a load on my low-end server box, when I want it to. It's definitely a lot of fun to experiment with, too.

On caching, by the way: I don't know about all browsers, but Firefox definitely ties cached files to specific IP addresses. So if you load a page using the LAN IP, and then look for it with the public IP, it will completely reload it. This comes in handy when testing connections.

---

### Post by edd07 on 2007-08-20
> **p_quarles said:**
> 
By the way, I've found that it's possible to test this oneself, too. I've asked other people to test my own page, and there is a 100% correlation between it working for others and it working for me when I plug in my current public IP address.
Yeah, but it's better to be sure. When I was setting up my server we tried that and didn't work outside the LAN. Anyway, we must've been doing something wrong, because we managed to get it working. If only I'd thought of posting a similar thread back then...we wouldn't have had to phone friends at 5am to test it :lolflag:

> **southernman said:**
> 
edd07 - love the siggy man!


Thanks! :)

---

### Post by p_quarles on 2007-08-20
> Yeah, but it's better to be sure. When I was setting up my server we tried that and didn't work outside the LAN. Anyway, we must've been doing something wrong, because we managed to get it working. If only I'd thought of posting a similar thread back then...we wouldn't have had to phone friends at 5am to test it
Oh, I agree completely. I called friends to test my site too (okay, partly to show off). I hope my post didn't come across as suggesting it wasn't worthwhile to test connections with truly remote computers. I only meant to say that plugging in the public IP is a pretty reliable test. I wouldn't trust that test in any critical application, though.

---

### Post by southernman on 2007-08-20
> **p_quarles said:**
> Apache is pretty damn efficient. I don't know what your specs are, but it handles quite a load on my low-end server box, when I want it to. It's definitely a lot of fun to experiment with, too.

On caching, by the way: I don't know about all browsers, but Firefox definitely ties cached files to specific IP addresses. So if you load a page using the LAN IP, and then look for it with the public IP, it will completely reload it. This comes in handy when testing connections.

It's old as dirt damn near!

Dell Dimension v350
PII 350
192MB RAM (It only had 32MB when I got it and I had to dig deep into my old stash to get up to 192)
hda @ 10GB:
hda1 /boot ext2
hda2 /var ext3
hda4 swap (set to 1gb since I aim to buy 3 sticks of 128 <--- it's max possible)

hdb @ 9GB
hdb1 / ext3

I am aware that static pages require very little ram, which is why I will install word press and then come back asking for help to test it and watch the load run up on the server. The biggest part of load just a few moments ago came from me watching the box through server-status. Load never got to .01 according to top on the system console, but server status showed fluctuations around .2 to .3

Right now, the box only has apache, php, mysql, but I'll put postfix and a couple of extra monitoring tools. Still researching on exactly what though.

Undecided about rootkit stuff and the like.. as of yet. I've read it's not really called for and then I've read just the opposite too. *shrugs*

---

### Post by jakev383 on 2007-08-22
> **southernman said:**
> It's old as dirt damn near!

Dell Dimension v350
PII 350
192MB RAM (It only had 32MB when I got it and I had to dig deep into my old stash to get up to 192)
hda @ 10GB:
hda1 /boot ext2
hda2 /var ext3
hda4 swap (set to 1gb since I aim to buy 3 sticks of 128 <--- it's max possible)

hdb @ 9GB
hdb1 / ext3

I am aware that static pages require very little ram, which is why I will install word press and then come back asking for help to test it and watch the load run up on the server. The biggest part of load just a few moments ago came from me watching the box through server-status. Load never got to .01 according to top on the system console, but server status showed fluctuations around .2 to .3

Right now, the box only has apache, php, mysql, but I'll put postfix and a couple of extra monitoring tools. Still researching on exactly what though.

Undecided about rootkit stuff and the like.. as of yet. I've read it's not really called for and then I've read just the opposite too. *shrugs*

I was AFK yesterday, but there's nothing showing on your site now.
And those are fine specs.  I run a wiki (wiki.qmailtoaster.com) and several other websites that have large files to download (qmtiso.com) on this box:

P3-1Ghz
756M RAM (PC 133)
100G Seagate IDE HD

With hardly any load.  Look at the wiki stats page ([http://wiki.qmailtoaster.com/index.php/Special:Statistics](http://wiki.qmailtoaster.com/index.php/Special:Statistics)) and while it's not a large load, remember that this is one of about 12 different sites on this machine.  You should be fine with a personal blog and photos or whatever.  Your biggest bottle-neck will be your Internet connection.
Enjoy!

---

### Post by southernman on 2007-08-22
Hey Jake,

Thanks for that. Yeah, I don't like leaving the box facing for to terribly long atm. 

Your site seemed to load lickety-split. :)

---

### Post by jakev383 on 2007-08-22
> **southernman said:**
> Hey Jake,

Thanks for that. Yeah, I don't like leaving the box facing for to terribly long atm. 

Your site seemed to load lickety-split. :)

No problem.  That machine is on a bonded T1, with 3M/3M speeds.  One running on a cable/DSL will have slower download speeds - here on a TWC Business class cable modem (home office) I get 5M down by 768K up.  Far cry from 3M up....  But I don't serve pages off of it either (okay, I actually do - I run Zina to serve my MP3's to me while away, and I run an Asterisk box for my house/office phones, and when I'm gone and staying in hotels I stream MythTV recorded shows to my laptop, but I won't count those :) )

---

