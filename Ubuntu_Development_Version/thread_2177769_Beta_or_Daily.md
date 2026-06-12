---
title: "Beta or Daily"
date: 2013-09-30
forum: Ubuntu Development Version
---

### Post by den_ on 2013-09-30
I am going to do a small hardware upgrade to friend's machine at end of this week. At the moment he is using NVidia intregrated graphics, and I'll give him a Radeon 4350 HD, and I found 4*1GB RAM for 20€.

Now I am also going to suggest him to try Ubuntu. I am still not sure what would be better to recommend/install, a LTS, 13.04, or 13.10. 13.10 is my favorite option at the moment (I think I read about radeon driver got some improvements in the last time.), since I was having good experience with last betas.

Would it be better to use daily of that day, or to use offical Beta as an installation media, if we decide to give a 13.10 a try first? Also IIRC, in last betas the repositories would switch to stable automatically, after release. Is this still the case, or one has to manually change something?

Thanks in advance

Denis

---

### Post by mörgæs on 2013-09-30
If your friend is completely green to Ubuntu I think you should aim for stability, that is 13.04 and not a beta.

---

### Post by den_ on 2013-09-30
Thanks for your reply.

That makes sense, that's why I am thinking about LTS, but on the other hand I would like to squeeze every bit out of his radeon card. And usually (at least in my case with intel graphics.) I had no problems in running beta. One just applies updates, and that's it. I could also leave a temporary SSH setup, to be able to log in and fix if issues occur.

---

### Post by den_ on 2013-09-30
Can anyone tell me more about state of radeon driver, and difference between 12.04 LTS and the one to be expected in 13.10. I presume, I could also add xorg-edgers ppa (that is what I am using, and it is rock stable on my sandy bridge platform.) if there are significant improvements in the last version of the driver. I would also like him to have last LibreOffice, but there is a ppa for that too. I'll probably go with LTS.

---

### Post by grahammechanical on 2013-09-30
Will you be explaining to your friend how to Upgrade? He will have to do it not too many months from now because 13.04 and 13.10 only have 9 months of support. So, he will have to upgrade to 14.04  a few weeks after it is released.

I tell you now, I would not want a friend like you. You are planning on turning his machine into a test bed for experimental software. You will turn your friend off Ubuntu.

Regards.

---

### Post by craig10x on 2013-09-30
On the other hand, at this point in time, 13.10 is pretty darn stable and has only a bit over 2 weeks to final release, at which time an installed 13.10 development will automatically become the final release (no action is necessary for that...action is only needed to have it roll into 14.04 development which you aren't planning on doing anyway)...And there has been a lot of improvements since 12.04, 12.10 and 13.04 so personally, at this point, i'd go with a 13.10 daily build iso (which would be up to date as of today) and use that to install...but run it in live session first of course to see if everything runs ok...

When 14.04 arrives, i would make sure he has his important data backed up an external drive (i have mine backed up on a 32 gb flash drive myself)...and have him do an upgrade to 14.04 final upon release, using the "upgrade directly from the live iso installer" method...in my experience, that has been the most reliable...

---

### Post by den_ on 2013-09-30
craig10x, thanks for your opinion. Me my self never had problems with updating. I always use an installer way, it is the most simple one, and it worked for me.

My responce to grahammechanical has been deleted by admin I presume. He/she obviously didn't like how I express my opinion about people who are too concerned not to turn off someone off Ubuntu.

---

### Post by ventrical on 2013-09-30
> **grahammechanical said:**
> Will you be explaining to your friend how to Upgrade? He will have to do it not too many months from now because 13.04 and 13.10 only have 9 months of support. So, he will have to upgrade to 14.04  a few weeks after it is released.

I tell you now, I would not want a friend like you. You are planning on turning his machine into a test bed for experimental software. You will turn your friend off Ubuntu.

Regards.

+1

  I am working on a new convert that has no ubuntu/linux experience at all. I actually sent this person 12.04 on a CD (and Lucid also) but they decided not to try it. Now they want to try it and so I think the only best advice is the 12.04 LTS. Once they get comfortable with that then they can decide if they want to go to development release. 

  I did do a Raring install for one of my clients but she is much more savy now after 1 1/2 years of Lucid.

Regards..

---

### Post by craig10x on 2013-09-30
@ den_: Glad to be of help...i got on 13.10 development by doing an upgrade using the iso installer and it worked out very well (still, i always have my important data backed up on a flash drive just in case...lol)...
and once 13.10 finalizes, i will stay with it until 14.04 and upgrade using the same method again...:)

I decided not to "roll with development" but rather "roll from final to final" of each new version of ubuntu...
At this point in time, 13.10 is pretty stable so i think it is not really a test bed at this point...in fact i got into development about 2 months ago and have not had a major problem and this IS my main and "everyday use" installation...i have no others...the updates will automatically "finalize" my install of 13.10 and then i will stay on final releases from this point on...

---

### Post by den_ on 2013-09-30
craig10x,

yes, Ubuntu development branch is usually quite stable around beta, at least on my hardware. It always depends on system setup. And it is still test bad, there is no contradiction.

---

### Post by ventrical on 2013-09-30
> **den_ said:**
> I am going to do a small hardware upgrade to friend's machine at end of this week. At the moment he is using NVidia intregrated graphics, and I'll give him a Radeon 4350 HD, and I found 4*1GB RAM for 20€.

Now I am also going to suggest him to try Ubuntu. I am still not sure what would be better to recommend/install, a LTS, 13.04, or 13.10. ,snip> 

 We assumed you were asking an open question. Conventional wisdom for noobs is to install the LTS version which currently is 12.04. 

Regards..

---

### Post by jerrylamos on 2013-10-01
> **ventrical said:**
> We assumed you were asking an open question. Conventional wisdom for noobs is to install the LTS version which currently is 12.04. 
Regards..

I rattle back and forth over several releases, ubuntu and otherwise.  Of late I've found 13.04 pretty solid.  Try

[http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)

example

ubuntu-13.04-desktop-i386.iso 

Now that's dated 24 April 

which I usually would install then

sudo apt-get update
sudo apt-get dist-upgrade

Have fun.  I've run both 12.04 and 13.04 today.

---

### Post by ventrical on 2013-10-02
> **jerrylamos said:**
> I rattle back and forth over several releases, ubuntu and otherwise.  Of late I've found 13.04 pretty solid.  Try

[http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)

example

ubuntu-13.04-desktop-i386.iso 

Now that's dated 24 April 

which I usually would install then

sudo apt-get update
sudo apt-get dist-upgrade

Have fun.  I've run both 12.04 and 13.04 today.

 But  you are not a new user. You are an 8 year veteran. You have all that experience.

Regards..

---

