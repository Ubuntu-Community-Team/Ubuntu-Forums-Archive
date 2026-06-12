---
title: "backports mirror"
date: 2005-05-15
forum: Ubuntu Backports
---

### Post by Gandalf on 2005-05-15
Hello,
the backports mirror is so slow, maybe because there's a lot of pressure on it,
i can offer a mirror if the admins want to, i'll give it with pleasure (hope it's not too much space (not above 5gb) )... if admins agree thx for contacting me by PM

---

### Post by TravisNewman on 2005-05-15
The backports server had to be capped because it was going over montly restrictions, just so you know. I'm sure a mirror would be welcome. I don't have any authority over it whatsoever, but out of curiosity, what kind of server/bandwidth will you be hosting on?

---

### Post by Gandalf on 2005-05-15
[QUOTE=panickedthumb]The backports server had to be capped because it was going over montly restrictions, just so you know. I'm sure a mirror would be welcome. I don't have any authority over it whatsoever, but out of curiosity, what kind of server/bandwidth will you be hosting on?[/QUOTE]
 well it's on my server, i have unlimited bandwith but unfortunately it's a 1Mb upload connection, 20Mb download connection so i guess it could be a bit slow for guys with download connection higher than 1.5Mb

---

### Post by AgenT on 2005-05-15
Backports is 5GB I think. Check out the [website]("http://backports.ubuntuforums.org/") as it states the size there (it timesout for me as of writing this).

---

### Post by Gandalf on 2005-05-15
[QUOTE=AgenT]Backports is 5GB I think. Check out the [website]("http://backports.ubuntuforums.org/") as it states the size there (it timesout for me as of writing this).[/QUOTE]
 exactly it timesout for me too, BTW the backports aren't on the same server as the forum ?? *-)

---

### Post by Gandalf on 2005-05-15
hmmmmmm... the size is 13Gb i can't afford this size now :/ maybe i can mirror only hoary not warty

//EDIT: maybe i can on my sda i have 90 GB of free space

---

### Post by TravisNewman on 2005-05-15
They are two physical servers for forums and backports, but they're on the same domain.

---

### Post by Gandalf on 2005-05-15
[QUOTE=panickedthumb]They are two physical servers for forums and backports, but they're on the same domain.[/QUOTE]
 oh ok i thought they are on one server

---

### Post by AgenT on 2005-05-15
[QUOTE=Gandalf]hmmmmmm... the size is 13Gb i can't afford this size now :/ maybe i can mirror only hoary not warty

//EDIT: maybe i can on my sda i have 90 GB of free space[/QUOTE]

Just mirror Hoary if you can (or the latest distro once the newer one comes out) since that is what causes most of the traffic anyway.

---

### Post by Gandalf on 2005-05-15
[QUOTE=AgenT]Just mirror Hoary if you can (or the latest distro once the newer one comes out) since that is what causes most of the traffic anyway.[/QUOTE]
 well need to talk to ubuntu-geek first

---

### Post by RastaMahata on 2005-05-15
this miror idea would be excellent! would this require us to change our sources.list?

---

### Post by liwyatan on 2005-05-15
We have an ftp connected to Internet with 100Mpbs. (up and down) connection and 300Gb+ free hard disk space if that's enough...  ;-)

---

### Post by TravisNewman on 2005-05-15
[QUOTE=RastaMahata]this miror idea would be excellent! would this require us to change our sources.list?[/QUOTE]
 depends on how it's done

---

### Post by guardian653 on 2005-05-15
a mirror would be nice. btw has anyone else here been given a 503 error? I can't update.

---

### Post by Gandalf on 2005-05-15
[QUOTE=guardian653]a mirror would be nice. btw has anyone else here been given a 503 error? I can't update.[/QUOTE]
 exactly, that's why we suggest a mirror because ubuntuforums cannot affors all the traffic and need mirror so everyone that can have a mirror thx to post in this topic so ubuntu-geek can decide

---

### Post by jdong on 2005-05-15
Thanks for the enthusiasm, but a 1MBit pipeline will be crushed within a couple of minutes. Cloud9 (the server before UbuntuForums) had a 6MBit Business DSL line, and that got to the point that all other shared sites were "down".


The real repository size is like 3-5GB, 13GB is including Subversion metadata. I'll also need to work out a mirroring technique (maybe just a subversion checkout...)


If you're interested in continuing, please e-mail/PM me.

---

### Post by Gandalf on 2005-05-15
[QUOTE=jdong]Thanks for the enthusiasm, but a 1MBit pipeline will be crushed within a couple of minutes. Cloud9 (the server before UbuntuForums) had a 6MBit Business DSL line, and that got to the point that all other shared sites were "down".


The real repository size is like 3-5GB, 13GB is including Subversion metadata. I'll also need to work out a mirroring technique (maybe just a subversion checkout...)


If you're interested in continuing, please e-mail/PM me.[/QUOTE]
 what is the average daily bandwith??

there's also someone above suggested with a 100 mbit connection

---

### Post by jodef on 2005-05-15
[QUOTE=RastaMahata]this miror idea would be excellent! would this require us to change our sources.list?[/QUOTE]Yeah the backports are a crucial part of the Hoary experience.

---

### Post by noderat on 2005-05-15
[QUOTE=jdong]The real repository size is like 3-5GB, 13GB is including Subversion metadata. I'll also need to work out a mirroring technique (maybe just a subversion checkout...)
[/QUOTE]

Well you already have subversion read only access set up. Perhaps you should protect it for a few hours while an authorized mirror checkouts the current svn repo (that way you have all avaiable bandwidth for checkout) and then the mirrors can just svn update every day or so.

Also perhaps a URL scheme likehttp://[location].backports.ubuntuforums.org/ would be useful. Users would be able to pick a mirror nearby to them and then enjoy speedy goodness. $0.02

---

### Post by XDevHald on 2005-05-15
[QUOTE=noderat]Well you already have subversion read only access set up. Perhaps you should protect it for a few hours while an authorized mirror checkouts the current svn repo (that way you have all avaiable bandwidth for checkout) and then the mirrors can just svn update every day or so.

Also perhaps a URL scheme likehttp://[location].backports.ubuntuforums.org/ would be useful. Users would be able to pick a mirror nearby to them and then enjoy speedy goodness. $0.02[/QUOTE]
 Are you talking about 2cents for the connection? or am I just acting drunk?

---

### Post by noderat on 2005-05-15
You're drunk.

---

### Post by AgenT on 2005-05-16
[QUOTE=noderat]You're drunk.[/QUOTE]

[-X

---

### Post by ubuntu-geek on 2005-05-16
Good news I might have us a unmetered server :) More to come shortly.

---

### Post by XDevHald on 2005-05-16
[QUOTE=AgenT][-X[/QUOTE]
 Ha , naughty naughty noderat, [color=Navy][color=Black]AgenT[/color] [/color]will take you down ;):roll:

**Edit$: ~ **Good to hear u-g!! hope everything goes well :D :D

---

### Post by harryc on 2005-05-16
The new mirror is very fast. I just downloaded a bunch of updates at 480 to 500 kbps. Thanks to all involved!

---

### Post by Gandalf on 2005-05-16
who gave a mirror?

---

### Post by kleeman on 2005-05-16
Yeah much faster. Check the backports page for the mirror address. Damn now it will slow down  :)  :)  :)

---

### Post by jdong on 2005-05-16
Guys, I certainly hope Ubuntu Backports didn't clog a 100MBit pipeline within hours of announcement....


Forget slashdotting... UBP'ing is the new term that sends chills down any netadmin's spine.....

---

### Post by bored2k on 2005-05-16
[QUOTE=jdong]Guys, I certainly hope Ubuntu Backports didn't clog a 100MBit pipeline within hours of announcement....


Forget slashdotting... UBP'ing is the new term that sends chills down any netadmin's spine.....[/QUOTE]
 What in the world are people downloading so much !? Maybe every ubuntu user is downloading your **thick** Java .debs :\

---

### Post by harryc on 2005-05-16
[QUOTE=bored2k]What in the world are people downloading so much !? Maybe every ubuntu user is downloading your **thick** Java .debs :\[/QUOTE]Well lets see, today....Gaim 1.3.0, Gimp 2.2.7-1, Mono 1.1.7, xchat 2.4.3-0. Couldn't resist Mono since I run Beagle and Tomboy.  :-P

---

### Post by AgenT on 2005-05-19
Good job guys on setting up the mirror!

For those that are yet unaware, visit the [Backports Mirror page]("http://backports.ubuntuforums.org/url.php") for more info.


And on behalf of everyone, 

[size=5]THANK YOU **liwyatan** FOR THE MIRROR[/size]. 

And [size=4]thanks to  the University of **Catalunya **[/size]for providing the hardware/bandwidth.

:D     ;)      :D

---

### Post by XDevHald on 2005-05-19
[QUOTE=AgenT]Good job guys on setting up the mirror!

For those that are yet unaware, visit the [Backports Mirror page]("http://backports.ubuntuforums.org/url.php") for more info.


And on behalf of everyone, 

[size=5]THANK YOU **liwyatan** FOR THE MIRROR[/size]. 

And [size=4]thanks to  the University of **Catalunya **[/size]for providing the hardware/bandwidth.

:D     ;)      :D[/QUOTE]
 Amen! hehe

---

### Post by ubuntu-geek on 2005-05-19
We'll have another mirror soon :)

---

### Post by liwyatan on 2005-05-20
[QUOTE=AgenT]Good job guys on setting up the mirror!

For those that are yet unaware, visit the [Backports Mirror page]("http://backports.ubuntuforums.org/url.php") for more info.


And on behalf of everyone, 

[size=5]THANK YOU **liwyatan** FOR THE MIRROR[/size]. 

And [size=4]thanks to  the University of **Catalunya **[/size]for providing the hardware/bandwidth.

:D     ;)      :D[/QUOTE]

Well to be fair, thanks to [Caliu]("http://caliu.info") for providing the hardware, thanks to the UPC (Universitat Politècnica de Catalunya) for providing the bandwith... and thanks to me for... for reading this forum?  :D

---

### Post by Gandalf on 2005-05-20
[QUOTE=liwyatan]Well to be fair, thanks to [Caliu]("http://caliu.info") for providing the hardware, thanks to the UPC (Universitat Politècnica de Catalunya) for providing the bandwith... and thanks to me for... for reading this forum?  :D[/QUOTE]
 thanks man for providing the mirror
cheers

---

### Post by hardawayd on 2005-05-20
[QUOTE=AgenT]Good job guys on setting up the mirror!

For those that are yet unaware, visit the [Backports Mirror page]("http://backports.ubuntuforums.org/url.php") for more info.


And on behalf of everyone, 

[size=5]THANK YOU **liwyatan** FOR THE MIRROR[/size]. 

And [size=4]thanks to  the University of **Catalunya **[/size]for providing the hardware/bandwidth.

:D     ;)      :D[/QUOTE]

Could you please offer the exact line that needs to be inserted in the sources.list file to get it to work.

thank you.

---

### Post by Gandalf on 2005-05-20
[QUOTE=hardawayd]Could you please offer the exact line that needs to be inserted in the sources.list file to get it to work.

thank you.[/QUOTE]
 here's the whole possibility but it is not recommanded to include staging though
# ubuntuforums.org backports mirror
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

---

### Post by hardawayd on 2005-05-20
Thank you very much  :grin:

---

### Post by ubuntu-geek on 2005-05-22
We now have another mirror which will soon appear on the backports website the address is:

[http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/)

Enjoy :)

---

### Post by ubuntu-geek on 2005-05-24
We now have yet another mirror :)

[http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/")

---

### Post by XDevHald on 2005-05-24
> Originally Posted by **ubuntu-geek**
We now have yet another mirror :)
 
 [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") 

lol, keep'em coming u-g!!

---

### Post by AgenT on 2005-05-24
[QUOTE=ubuntu-geek]We now have yet another mirror :)

[http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/")[/QUOTE]

YAY :razz:

---

### Post by Zhukov on 2005-06-10
Maybe i can try to create a mirror in Portugal, with all the backports, with a large bandwith (university). I'll see what i can do.

---

