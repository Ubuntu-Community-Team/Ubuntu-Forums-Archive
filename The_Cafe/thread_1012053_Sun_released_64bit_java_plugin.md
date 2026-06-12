---
title: "Sun released 64bit java plugin"
date: 2008-12-15
forum: The Cafe
---

### Post by dixon on 2008-12-15
Sun has just released [64bit java plugin](http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ). I was thinking about switching to 64bit for a long time, I think this was the only thing what kept me back from switching. Do you miss some other software for 64bit ubuntu?

---

### Post by mips on 2008-12-15
> **dixon said:**
> Sun has just released [64bit java plugin](http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ). 

I was thinking about switching to 64bit for a long time, I think this was the only thing what kept me back from switching. 

Do you miss some other software for 64bit ubuntu?

There is also Iced Tea java plugin for 64bit.

No, I don't miss anything in 64bit but I use Arch.

---

### Post by Vince4Amy on 2008-12-15
Cool, it's all coming together now. Flash and now Java. Just ZSNES next then all my main apps will be native 64-bit.

---

### Post by bsharp on 2008-12-15
I've never had a problem with 64-bit in two years.

Flash/Java/WINE has always worked well for me (yes, that's with the workarounds)

---

### Post by mips on 2008-12-15
> **Vince4Amy said:**
> Just ZSNES next then all my main apps will be native 64-bit.

From what I have read you can make it work:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)
[http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

---

### Post by Vince4Amy on 2008-12-15
> **mips said:**
> From what I have read you can make it work:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)
[http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

Thanks, I've already got it running on 64-bit it would just be nice to have a native x64 version. On Slackware ZSNES runs out of the box because Slack is x86, but on OpenSUSE/Kubuntu I always have to use workarounds.

---

### Post by Therion on 2008-12-15
> **bsharp said:**
> I've never had a problem with 64-bit in two years.
Same here.  I've never really even understood what all the fuss was about regarding getting Flash and Java to work on 64bit.  

Like you in two years it's never been an issue.

---

### Post by cb951303 on 2008-12-15
> **Therion said:**
> Same here.  I've never really even understood what all the fuss was about regarding getting Flash and Java to work on 64bit.  

Like you in two years it's never been an issue.

you are lucky then. it never worked for me in 64 bit. they greyed out very often

---

### Post by Paqman on 2008-12-15
> **mips said:**
> There is also Iced Tea java plugin for 64bit.

No, I don't miss anything in 64bit but I use Arch.

Ditto for me on Ubuntu.

IMO, the user experience for 64-bit and 32-bit is now identical. When I first started using Ubuntu (on Dapper) we had to fuss about with 32-bit versions of Firefox and/or monstrosities like Automatix, but everything's been streamlined very nicely.

---

### Post by Ledger on 2008-12-16
Someone know how to install this?

---

### Post by dibuntux on 2008-12-16
What is the fuss about having native support for 64 bit? 
Just installed flash 10 alpha 64 bit from Adobe instead of Flash 9 32 bit with all the workarounds for my Ubuntu 7.10 64 bit ws.
It is at least twice as fast, much more stable and it works at full screen with my dual screen setup, not working before. 
Although Icetea 64 bit is cute, none of my financial apps works on it, many login on banks do not work and it often crash. 

So, indeed there's the need for this plugin - has someone, again, figure it how to install it on Firefox? TIA

---

### Post by samjh on 2008-12-16
> **dixon said:**
> Sun has just released [64bit java plugin](http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ). I was thinking about switching to 64bit for a long time, I think this was the only thing what kept me back from switching. Do you miss some other software for 64bit ubuntu?

64-bit Java plugin was the only one.  The IcedTea implementation made Firefox crash (and didn't work for the applets I was interested in).

Adobe has released 64-bit Flash, and now Sun has released 64-bit Java, so 64-bit is all rock and roll. :p

---

### Post by TheAL76 on 2008-12-16
> **Ledger said:**
> Someone know how to install this?

Per wd5gnr's post (found at this URL: [http://ubuntuforums.org/showpost.php?p=6373073&postcount=1](http://ubuntuforums.org/showpost.php?p=6373073&postcount=1))

> cd /opt
sudo sh ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin

So you wind up with /opt/jre1.6.0_12

cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so
(restart firefox)

I'm digging it thus far. Facebook photo application works beautifully now, it used to crash when using IcedTea. Good job, Sun.

---

