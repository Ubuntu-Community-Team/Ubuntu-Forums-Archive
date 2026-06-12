---
title: "Mac Address Filtering and Hidden Network Overkill?"
date: 2013-02-26
forum: The Cafe
---

### Post by mamamia88 on 2013-02-26
As the title goes to secure a network is that overkill? It's not that I don't trust my neighbors it's that I'm resetting my network to clear out the config.  I'm setting hostnames for all my devices so they don't appear as unknown devices etc.  I'm using wpa2 btw.

---

### Post by ssam on 2013-02-26
you might want to have a read through this recent discusion.
[http://ask.slashdot.org/story/13/02/20/2058235/ask-slashdot-dealing-with-an-advanced-wi-fi-leech](http://ask.slashdot.org/story/13/02/20/2058235/ask-slashdot-dealing-with-an-advanced-wi-fi-leech)

some points worth noting:
* MAC addresses are easy to discover and fake.
* Hidden networks are easy to see
So neither of those methods will stop (or even significantly slow) a determined leecher.

---

### Post by mamamia88 on 2013-02-26
> **ssam said:**
> you might want to have a read through this recent discusion.
[http://ask.slashdot.org/story/13/02/20/2058235/ask-slashdot-dealing-with-an-advanced-wi-fi-leech](http://ask.slashdot.org/story/13/02/20/2058235/ask-slashdot-dealing-with-an-advanced-wi-fi-leech)

some points worth noting:
* MAC addresses are easy to discover and fake.
* Hidden networks are easy to see
So neither of those methods will stop (or even significantly slow) a determined leecher.

Yeah probably there is a way around anytning if you are determined enough.  But from where i'm sitting there are 3 unsecured broadcasted wifi networks that I'm sure hackers would try first.   And the only neighbors tech savy enough to maybe get in are across the street and they have better internet than me and I trust them.  Kinda of a pita to enter all the info into my configuration for all my devices but you only have to do it once so it's not that big of a deal.

---

### Post by mips on 2013-02-26
Your ideas of security seem better than that of most people. You could also look at running VPNs over wireless which would be way more secure but that's taking it to another level.

---

### Post by mckenna1977 on 2013-02-26
MAC address filtering, hidden network and a decent WPA2 passphrase make it reasonably secure and you've to only configure that once. 

You might also want to change the passphrase periodically (but for a home user with a few systems that can be a pain). The other easy security is to switch is off when you're away on weekends or holidays...

---

### Post by mamamia88 on 2013-02-26
> **mckenna1977 said:**
> MAC address filtering, hidden network and a decent WPA2 passphrase make it reasonably secure and you've to only configure that once. 

You might also want to change the passphrase periodically (but for a home user with a few systems that can be a pain). The other easy security is to switch is off when you're away on weekends or holidays...

Yeah I think I got a pretty good passphrase.  It's 10 numbers only though.  Should probably change it up but I've already connected my phone, nexus7, latpop, ps vita, ps3,kindle, and xbox 360.    Don't really feel like going back and retyping it right now.

---

### Post by sandyd on 2013-02-26
If your bored and seriously want to go overkill, check this out :D
[http://www.ciscopress.com/articles/article.asp?p=1576225](http://www.ciscopress.com/articles/article.asp?p=1576225)

---

### Post by CharlesA on 2013-02-26
> **sandyd said:**
> If your bored and seriously want to go overkill, check this out :D
[http://www.ciscopress.com/articles/article.asp?p=1576225](http://www.ciscopress.com/articles/article.asp?p=1576225)
Mmm RADIUS.

But yeah, I have my passphrase using all available characters. It is a pain in the butt to type in the first time, but it means I don't have to worry about rainbow tables or someone trying to bruteforce my wifi.

---

### Post by haqking on 2013-02-26
> **mamamia88 said:**
> Yeah I think I got a pretty good passphrase.  It's 10 numbers only though.  Should probably change it up but I've already connected my phone, nexus7, latpop, ps vita, ps3,kindle, and xbox 360.    Don't really feel like going back and retyping it right now.

you realise that 10 numerals takes about 10 seconds if not instant to crack right ?

numerals are fine to add padding to increase entropy but useless standing alone

---

### Post by mamamia88 on 2013-02-26
> **haqking said:**
> you realise that 10 numerals takes about 10 seconds if not instant to crack right ?

numerals are fine to add padding to increase entropy but useless standing alone

probably but i know my neighbors and i really don't feel like anyone is actually going to try to brute force my wifi.  that being said you have any reccomendations for chosing a better phrase?

---

### Post by CharlesA on 2013-02-26
> **mamamia88 said:**
> probably but i know my neighbors and i really don't feel like anyone is actually going to try to brute force my wifi.  that being said you have any reccomendations for chosing a better phrase?
[http://www.infosecisland.com/blogview/12701-Wireless-Security--Choosing-the-Best-Wi-Fi-Password.html](http://www.infosecisland.com/blogview/12701-Wireless-Security--Choosing-the-Best-Wi-Fi-Password.html)

Read that ^.

I use a password generator to generate the key I have now, but you can make it anything from a sentience or the name of a movie.

Spoilers (maybe):
```
WhyisAGoodDayToDieHardNotReallyADieHardMovie?BecuzitisaSpyMovie
```

63 characters and (hopefully) easily remembered.

---

### Post by mamamia88 on 2013-02-26
> **CharlesA said:**
> [http://www.infosecisland.com/blogview/12701-Wireless-Security--Choosing-the-Best-Wi-Fi-Password.html](http://www.infosecisland.com/blogview/12701-Wireless-Security--Choosing-the-Best-Wi-Fi-Password.html)

Read that ^.

I use a password generator to generate the key I have now, but you can make it anything from a sentience or the name of a movie.

Spoilers (maybe):
```
WhyisAGoodDayToDieHardNotReallyADieHardMovie?BecuzitisaSpyMovie
```

63 characters and (hopefully) easily remembered.

Isn't that easy to break though since it's a sentence?  I'm thinking of using a generator then copying the output into a text file and using that for my android devices and laptop with copy and paste.  Then plug in a keyboard and type it into my ps3 and 360. Only hard part would really be the kindle and vita. Also what generator did you use?  want to find something that is actually random

---

### Post by CharlesA on 2013-02-26
> **mamamia88 said:**
> Isn't that easy to break though since it's a sentence?  I'm thinking of using a generator then copying the output into a text file and using that for my android devices and laptop with copy and paste.  Then plug in a keyboard and type it into my ps3 and 360. Only hard part would really be the kindle and vita. Also what generator did you use?  want to find something that is actually random

It's all about the entropy. The longer the better.

To generate the key, I used KeePass.

---

### Post by mamamia88 on 2013-02-26
> **mamamia88 said:**
> Isn't that easy to break though since it's a sentence?  I'm thinking of using a generator then copying the output into a text file and using that for my android devices and laptop with copy and paste.  Then plug in a keyboard and type it into my ps3 and 360. Only hard part would really be the kindle and vita. Also what generator did you use?  want to find something that is actually random

I used this.  Is that a reputable site?  Not hard at all to copy and paste on adroid/linux.  Setting up the consoles might be a pain but at least you only enter it once.  [http://www.yellowpipe.com/yis/tools/WPA_key/generator.php](http://www.yellowpipe.com/yis/tools/WPA_key/generator.php)

---

### Post by mamamia88 on 2013-02-27
UCK for some reason my wifi password is showing up in plain site on my routers configuration page and the very front page.  Is that something for me to see just on my network or would that be easy for a hacker to see?  I'm hoping it's just a fluke.  I managed to get all my devices up and runnign with a 64 random password and don't want to type it all in again. Gave up on the whole hidden network thingy though.   One more thing is wifi protected setup bad?   I'm lazy and didn't want to type it all out on my vita so I used it.   Took me at least 5 tries to get it all right on my 360 lol.

---

### Post by CharlesA on 2013-02-27
> **mamamia88 said:**
> I used this.  Is that a reputable site?  Not hard at all to copy and paste on adroid/linux.  Setting up the consoles might be a pain but at least you only enter it once.  [http://www.yellowpipe.com/yis/tools/WPA_key/generator.php](http://www.yellowpipe.com/yis/tools/WPA_key/generator.php)

I don't use online generators. I prefer to stick to KeePass (it's in the repos last time I checked).

> **mamamia88 said:**
> UCK for some reason my wifi password is showing up in plain site on my routers configuration page and the very front page.  Is that something for me to see just on my network or would that be easy for a hacker to see?  I'm hoping it's just a fluke.  I managed to get all my devices up and runnign with a 64 random password and don't want to type it all in again. Gave up on the whole hidden network thingy though.   One more thing is wifi protected setup bad?   I'm lazy and didn't want to type it all out on my vita so I used it.   Took me at least 5 tries to get it all right on my 360 lol.

It's still protected behind a login screen isn't it? I don't use WPS, so I have it disabled, but I can see where it can be useful for people who aren't very technically savvy.

---

### Post by lisati on 2013-02-27
> **CharlesA said:**
> I don't use WPS, so I have it disabled, but I can see where it can be useful for people who aren't very technically savvy.
WPS, yuck! Yet another opportunity for vulnerability!

---

### Post by cariboo on 2013-02-27
> **lisati said:**
> WPS, yuck! Yet another opportunity for vulnerability!

@lisati, that's WPA, not WPS. :-D

You can generate your own passwords locally by using pwgen, using:

```
pwgen 16
```

results in a list that should look something like this:

```
eeyiekaesa5cohFo Ixae1eh7oi0aiK5a iGeiKahgohngael9 quu3Chei3dohso6n
Xi5ooqu4iewoo6xi aeliec0ahn5ooMae vieTh6zeengiepei oi4fai2eeQu8Baep
Pheox8dah8Thoumi aace3jie7Ooxuqu4 aejiaHuu4bai6eem EecieG0Boudaihee
Quei9ao1gu9Aaxut pie1jif6Xu1ziiru Ciechae2OoDupiex oozaimoxoh6mai0P
da3quei3eiGhahde Iushe7aefeWobeeV ies7ohNgaed1Ahqu Hootu7ood3Heo5Ai
phahRio2eeyeudae ahso6feeQuaiv9ie APiexieseuy4iefe Etuqueigh8Ahphah
Nah6mee5BeepieTh WaikeSiv5vai4aey iyeideeVaiChee2o ayoJ9feis1ooThee
kolaaNgi8ahSh4qu riash3ohWog1eish dahngigha3Ichoos ohca7ooj0raiko3O
raquipaWi1zahWee yah6Faebeeshai8e Gazoosie2phoocha Haih2hohGhiefohj
tich3Eipheinoohu ahn2eiJeeFaew1oh GeeSheech7Ohph5a Seexothoe1oG2jej
kee8iesh9zooHe6a eiZ2le8heef7viim aiveebi9ewei6Foe daebohK4zu1upi5F
Ochahf5jaaR8Ahji tai6iaNg1eong5ne ih8EiPh6cae7soa2 bu1ohd3EiWieh0xe
thai2bu3ohGh1eig giezoongiug6Hooc Oochiozai3IexaeM kie4OoKee8oVieTi
iechoow8moh9eeSh ELahjaighiophee3 giet4ein5ahQuoh1 Ahshute3JahLoop2
aigoo0aeV3foo6iu zi0ieQu7ieng5Uwo Zohtiv8Chup1iubu phaephia2ao3Aej9
too8faingahg9Mii Eav2aesheesheiko co0Quo1toh4xe6au ui3Iupicha8Quauy
ohxahW2rie6laeph faiR3eeSh6Pahbee yue6meeGhepae8me zo4zuu9yoakauQue
giegeigauChae2tu ijieCozeich1Jib6 jieyo7aeGh9ecach ohnaig3ees6sheaV
eaz6Ahsahxi8sohg ceuJ3iehaesi9jai ThiethahBaeshus2 quavaeshul1dooG9
Uheengoh0shahtee theiTh0ahdoo2eeb ohdii7BahFieSh8k raath3Oothie2zi1
```

---

### Post by CharlesA on 2013-02-27
I've used this to generate passwords before. It might not be that secure, but it's manageable.

```
date +%s | sha256sum | base64 | head -c 32 ; echo
```

If anyone is wondering %s returns the number of seconds since 1970-01-01 00:00:00 UTC.
[http://unixhelp.ed.ac.uk/CGI/man-cgi?date](http://unixhelp.ed.ac.uk/CGI/man-cgi?date)

---

### Post by lisati on 2013-02-27
> **cariboo907 said:**
> @lisati, that's WPA, not WPS. :-D
:lolflag:
I was thinking of [this]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup"). My current router has it as an option, and it's normally switched off, but we digress.....

---

### Post by mamamia88 on 2013-02-27
> **CharlesA said:**
> I don't use online generators. I prefer to stick to KeePass (it's in the repos last time I checked).



It's still protected behind a login screen isn't it? I don't use WPS, so I have it disabled, but I can see where it can be useful for people who aren't very technically savvy.

It's useful for people who are tech savy too.  Entering 64 random digits some upper case and some lower case is really hard to get perfectly.  Managed to mess it up quite a lot.  Well anyway i just found out that yes you can use WPS and then turn it off but still have the settings work.   Just saves you a lot of headaches.  and no i'm not logged in at all when i access my router config page and right there on front page is my wifi key. Kinda freaking me out.  For example a tiny snippit of the front page of router config

---

### Post by CharlesA on 2013-02-27
Wow, what brand of router is it? The ones I've used by Belkin, Linksys and Dlink all had the key stored behind a login page and usually with the other wireless settings.

On the other hand, you would need to gain access to the router to get the key, so I guess it isn't that much of a risk, but that is still not a good way to handle it.

---

### Post by mamamia88 on 2013-02-27
> **CharlesA said:**
> Wow, what brand of router is it? The ones I've used by Belkin, Linksys and Dlink all had the key stored behind a login page and usually with the other wireless settings.

On the other hand, you would need to gain access to the router to get the key, so I guess it isn't that much of a risk, but that is still not a good way to handle it.

It's a pace 411n supplied by ATT.  And it was never that way before I reset the thing to factory defaults today.

---

### Post by Paqman on 2013-02-27
> **mamamia88 said:**
> Isn't that easy to break though since it's a sentence?

As always, xkcd provides:
[img]http://imgs.xkcd.com/comics/password_strength.png[/img]

Although it is correct that four random words are better than a sentence, as sentence structure tends to follow some statistical patterns.

---

