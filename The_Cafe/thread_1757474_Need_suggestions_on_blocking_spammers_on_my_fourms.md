---
title: "Need suggestions on blocking spammers on my fourms"
date: 2011-05-13
forum: The Cafe
---

### Post by zealibib slaughter on 2011-05-13
Hey everybody, 
Ive gotta forums section on my website and I am constantly having spammers register. Anyone have any suggestions on how to limit this?
 
This is the site [http://www.greenvilleparanormal.org/forums](http://www.greenvilleparanormal.org/forums)
 
Its a simple machines forums hosted on a shared server with hostgator.
These are the mods installed
Social networks profile block
reCAPTCHA for SMF
Bot buster

---

### Post by lisati on 2011-05-13
> **zealibib slaughter said:**
> Hey everybody, 
Ive gotta forums section on my website and I am constantly having spammers register.  Anyone have any suggestions on how to limit this?
 
This is the site [http://www.greenvilleparanormal.org/forums](http://www.greenvilleparanormal.org/forums)

If you are hosting your forum yourself, you might want to consider installing [mod_defensible]("http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch") on your server.

The following message is noted, with the observation that I don't use anonymising proxy - I use [Squid]("https://help.ubuntu.com/community/Squid") to help speed things up when I'm surfing:
> Sorry, but the administrator has blocked access by proxies. Other causes of this error include using an intranet (school connections), registering on a cell phone, or using a browser that does not support compression or does not accept encoding.

---

### Post by fballem on 2011-05-13
Another option is to generate characters in an image that cannot be remotely scanned.

The user has to manually type in the characters and have them verified before the registration is accepted. No idea how difficult this is to do.

Hope this helps,

---

### Post by zealibib slaughter on 2011-05-13
My next goal is to move my site to a server which I control but unfortunately I am on a shared hosting plan through hostgator with no root shell access.  
 
I installed the proxy blocker in hopes to stem the tide but It didn't do anything except make it impossible for me to use my phone and the site so its coming off today.
 
I looked at mod_defensible and liked what I saw so when I get my own server set up thats one thing I am using, thanks for the suggestion.:)

---

### Post by zealibib slaughter on 2011-05-13
> **fballem said:**
> Another option is to generate characters in an image that cannot be remotely scanned.
 
The user has to manually type in the characters and have them verified before the registration is accepted. No idea how difficult this is to do.
 
Hope this helps,
 
 
I've got recapatcha set up to no avail.

---

### Post by Maheriano on 2011-05-13
I run some other forums and solved this problem myself but I had FTP access to modify the files. My suggestion would be to rip out your current forums and install something like PHPBB3 so you can install any of the community plugins made specifically for this.

---

### Post by zealibib slaughter on 2011-05-13
> **Maheriano said:**
> I run some other forums and solved this problem myself but I had FTP access to modify the files. My suggestion would be to rip out your current forums and install something like PHPBB3 so you can install any of the community plugins made specifically for this.
 
I was considering this earlier and may do exactly that.

---

### Post by Maheriano on 2011-05-13
> **zealibib slaughter said:**
> I was considering this earlier and may do exactly that.

I'm well adversed with PHPBB, if you have any questions you can send them my way or post them here. Another alternative is to buy vBulletin which may be easier if you're not a programmer.

---

### Post by Macskeeball on 2011-05-13
> **zealibib slaughter said:**
> I've got recapatcha set up to no avail.

Yeah, people have figured out two ways around CAPTCHAs: (1) [optical character recognition](http://en.wikipedia.org/wiki/Optical_character_recognition) which is imperfect but can do a pretty good job and (2) copying a captcha image from a real site and displaying it on a porn site to trick a human into entering the code. So CAPTCHAs are they're less effective than some people think, but they're still annoying for users.

---

### Post by zealibib slaughter on 2011-05-13
> **Macskeeball said:**
> Yeah, people have figured out two ways around CAPTCHAs: (1) [optical character recognition]("http://en.wikipedia.org/wiki/Optical_character_recognition") which is imperfect but can do a pretty good job and (2) copying a captcha image from a real site and displaying it on a porn site to trick a human into entering the code. So CAPTCHAs are they're less effective than some people think, but they're still annoying for users.
 
 
I agree I hate CAPTCHAs personally but it did cut down the number of spammers registering from 100 a day to 4 a day.  I want to get rid of some of the blocks I've got in place and have the forum more open, but keep the ****** ads out.  (wow maybe i should add that pill for men to the censored word list in my forums.)

---

### Post by catlover2 on 2011-05-13
hello, I have never set up, (or even thought about), setting up a forum, but when i registered on the dd-wrt forum, i saw an interesting way they have to stop spam.

[http://www.dd-wrt.com/phpBB2/profile_sec.php?mode=register_wtf&wtf=true](http://www.dd-wrt.com/phpBB2/profile_sec.php?mode=register_wtf&wtf=true)

---

### Post by Lucradia on 2011-05-13
Turn on COPPA if you can, as well as robots.txt

---

### Post by jerenept on 2011-05-13
You can require that the first 3 to 5 posts by a user be mod-approved.
Seems to work over on that other forum.....
foldingforum.org does this as well, I think.

---

### Post by zealibib slaughter on 2011-05-13
> **catlover2 said:**
> hello, I have never set up, (or even thought about), setting up a forum, but when i registered on the dd-wrt forum, i saw an interesting way they have to stop spam.

[http://www.dd-wrt.com/phpBB2/profile_sec.php?mode=register_wtf&wtf=true](http://www.dd-wrt.com/phpBB2/profile_sec.php?mode=register_wtf&wtf=true)

man thats cool. I never would have thought of that.

---

### Post by zealibib slaughter on 2011-05-13
thanks for all the help im gonna work on it some more in the morning.

---

### Post by catlover2 on 2011-05-13
yea, i wonder how (if?) *any* bots get around that?

---

