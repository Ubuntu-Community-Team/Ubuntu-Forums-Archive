---
title: "Our Own Web Server"
date: 2007-12-10
forum: Server Platforms
---

### Post by hwheeler43 on 2007-12-10
Our small company has a Windows 2003 server that we are renting off site for our web server.  We are planning to have a server built and then install Ubuntu server and move our web server in house.  Thanks to answers to some of the other posts we feel that it will be a good move.  I have some limited unix experience and have played with linux for a while.  We would not have to be in a hurry as we can keep the off site link until we get everything going in house.  I think we can figure out most of what we would need to do and if needed hire a linux expert for a few weeks to help with the setup.  My thought process is that we can get it all functioning and tested and then have the dns change made by our isp.  We keep a lot of pictures and pdf files on our web site.  I was just wondering if anyone thinks this would be a bad move on our part.

---

### Post by koenn on 2007-12-10
Kinda depends on a few things.
I don't doubt you're capable of (learning to) run a web server. And technically, if your server is performant enough and your bandwidth sufficient to handle the anticipated load, you'll do fine. 
The only thing to consider is ... how important is this web site you're running. If, for some silly reason such as a hardware failure, the site's ofline for a day, is that a problem ? Or if something goes bad during the weekend, can it wait 'till Monday ? If not, who's going to come fix it on Saterday and Sunday ? you ? 

The benefit of external hosting is that you can offload that sort of worries to your hosting provider.

---

### Post by leg on 2007-12-10
Seems to make sense to me. Make sure you are up to speed on managing the server before you go live. Practice back ups, recovering using back ups etc. Don't wait for your first emergency to try and figure out how to recover. But I am sure you thought of that.

---

### Post by hwheeler43 on 2007-12-10
All of that makes perfect sense.  Our off site does not do backups and that worries me quite a bit.  Also,  the off site server does not have a very big hard drive.  I also plan to run the email server from on site on the same box.  I would be the one having to fix it.  I was thinking that the advantages of being able to do my own backups and touching the box might be big enough to make this a real consideration.

---

### Post by hwheeler43 on 2007-12-10
Does anyone have any recommendations for a good email server software package that will support Web mail and Windows clients?  Spam blocking would be nice as well.

---

### Post by dboot on 2007-12-10
Try out citadel. It's very easy to install and comes with a lot of useful features. I suggest installing it with "Easy Install" documentation and not the ubuntu packages.

[http://www.citadel.org/doku.php?id=start]("http://www.citadel.org/doku.php?id=start")

I just installed it on my server along with [RoundCube]("http://roundcube.net/") IMAP webmail and love it.

---

### Post by hwheeler43 on 2007-12-10
Sounds great.  After my post I did a search and found citadel mentioned in another post.  It may well be what we are looking for.  Thank you all.:)

---

