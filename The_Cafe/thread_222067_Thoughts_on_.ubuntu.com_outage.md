---
title: "Thoughts on *.ubuntu.com outage"
date: 2006-07-24
forum: The Cafe
---

### Post by GreenfrogCT on 2006-07-24
On Saturday I backed up my in-house development and testing box which had been running an old version of Mandrake and installed Dapper on it.  My plan for Sunday was to do all of the updates, install and configure the various services I use on it, etc.

Obviously those plans got changed.  ](*,) 

(For those who have not been following, the entire *.ubuntu.com domain was down for most of the day because of a power failure.)

The event brings up a very important issue as far as I am concerned.  If Ubuntu is to become a serious contender for business use (and I would love to see that happen) having only one repository that is a serious single-point-of-falure is simply unacceptable.

That is the only word for it:  Unacceptable.

For me yesterday all it meant is that I got to spend more time in the pool than I had originally intended.  :D   If I were using Ubuntu in a mission critical application and had planned to do a weekend upgrade I would have been a very unhappy camper, and would probably have reconsidered my choice.

In my business (I am a presales design engineer for a communications and networking company) a big part of what I do is design and recommend data and VOIP solutions for businesses and municipalites.  Having no single point of failure is key for most of the entities I deal with.

Isn't it time for an Ubuntu repository mirror in another location?

:mrgreen: Ribbitt

---

### Post by Redcard on 2006-07-24
Well, there are ways around that.  Most mission critical applications have redundant situations in play.  For example, I know there are quite a few debian boxes that were set up around here with very localised sources.  The same could be done with Ubuntu.  There's NOT a single repository for Ubuntu.  There are mirrors throughout the world.  

If I had a mission critical app, you can believe that I would have quite a few backup plans ready to fall over to another mirror if necessary.  It's what I did this weekend :)

[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

---

### Post by TravisNewman on 2006-07-24
Had it been me doing the weekend upgrade, I would have already known all support venues, so I would have gone to either #ubuntu or #ubuntuforums and found out that you could easily change your sources.list to uk or au, etc, and do the upgrades painlessly. I can understand how this can frustrate home users, but corporate users in mission critical settings have to have all their ducks in a row before taking on this kind of an upgrade. In this case, there would have been a 5 minute delay at most.

---

### Post by kigina on 2006-07-24
I think ubuntu.com is a lot better than microsoft.com, which probably has the slowest response time I have ever seen.

---

### Post by kanem on 2006-07-24
> **Redcard said:**
>  
If I had a mission critical app, you can believe that I would have quite a few backup plans ready to fall over to another mirror if necessary.  It's what I did this weekend :)

[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)
That's a lot of mirrors! And was it all of Ubuntu's official repositories that went down? Meaning did ca.archive.ubuntu.com and uk.archive.ubuntu.com etc. go down as well?

---

