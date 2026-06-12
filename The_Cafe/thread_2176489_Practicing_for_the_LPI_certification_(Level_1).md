---
title: "Practicing for the LPI certification (Level 1)"
date: 2013-09-24
forum: The Cafe
---

### Post by mynamesalex on 2013-09-24
I've beens studying from Ubuntu Unleashed for a while, and then somehow got my hands on a copy of the latest edition of 'Linux Essential - The LPI Introductory Programme' on my phone as an ebook.  I still wanna buy the hardcopy though, I can't stand reading ebooks, I guess mostly cause I don't see the book sitting in my living room staring at me waiting to be picked up.

I took a practice exam at penguintutor.com and only got 36%, but I still haven't covered a lot of the topics, like boot process, and haven't spent enough time on a number of command line functions, among other topics I don't even know about :P

Hopefully I do can improve, I'm gonna try the practice exam again in another month and see how I improve.  Does anyone have any suggestions for the exam?

Care to share your stories about taking the LPI certifications?  Any level is fine, I just wanna talk about this more with people who actually care about it.  I have few-no friends who understand or care about linux.  Such is the real world.

---

### Post by TheFu on 2013-09-24
As to Linux friends - no local LUG?  No college or university nearby with a computer group?  My LUG meets at the local Technical University and we are friendly towards the 5+ other LUGs in the metro area - lots of cross-knowledge sharing and transfer.  Then you can add in all the F/LOSS programming groups - python, php, ruby, perl ... each has their own group here.

Congratulations on having a task and keeping with it.  I took classes to be a CNE in the mid-90s. What I learned besides all about Netware was that I never wanted to have a full-time job like that.  In my part of the world, there are questions about pure-SysAdmins being desired, since "DevOps" has taken over the Cloud world - that means more of a scripting person with expertise is needed than someone with huge hardware knowledge.

BTW, I have the O'Reilly LPI book here - read about 3 chapters and got frustrated with coverage of stuff that NOBODY uses in the real world.  Honestly, when was the last time anyone used the /etc/host.conf file?

I had a slight interest in getting certified, but at my level, certifications don't mean too much AND each can be a hindrance for the real job I want.

Anyway, good luck finding what you seek.

---

### Post by mynamesalex on 2013-09-24
Thanks.  I've been checking out groups and stuff, but here in Vancouver I could only find one LUG, and they meet about once a month, maybe twice.  I've been trying to get out to the meetings, but I usually work when they meet, and since their meetups aren't scheduled very far in advance, it's harder for me to get the day off last minute.

I'm working on it though.  I haven't actually been into Linux for very long, only a couple months, and I popped open a Python textbook less than 4 weeks ago.  And yes, I too get frustrated by the amount of coverage on silly things, like huge sections about simple commands like ls, and cd, when I'm really struggling with topics like fsck.

---

### Post by TheFu on 2013-09-25
**FSCK**
fsck is simple. "file system check"  Things to know.
* it is not safe to run on a mounted file system.
* to run it on /, boot off a flash/cdrom, liveCD and manually run it or **sudo touch /forcefsck** and it will run at the next reboot.
* to run it on other file systems, those must be unmounted.  The easiest way that I know to ensure it is safe is to drop to single-user mode (sudo telinit S) then umount /whatever/the/mount/point ... then run fsck on the device.
* if fsck can't automatically figure out what the file system type is, look for superblock errors. That's a different command.
* fsck of non-journaled file system sucks. - hours - days - weeks.  For journaled file systems, it should be seconds/minutes regardless of size.

**LUGs**
Most LUGs meet on a schedule - mine is the 2nd Thursday of the month - set your calendar - we will meet.  We don't always get a presenter until the last second, so we don't advertise until a few days before.  Some of the best meetings have been without any presenters - just show-n-tell.  You can set your calendar for the next 5 yrs now, **2nd Thursday of the month**.  Of course, the LUG in your area(s) probably has a different meeting schedule, so fine out how they communicate and GET INTO THE LOOP.  My LUG only communicates via email. No G+, Tweeter, RSS, website - just email.  Sometimes we have to move the scheduled date, but that hardly ever happens.  We did reschedule around Valentine's Day ... that's an example.

We also have an informal meeting every Sunday at a nearby pizza place.  This is advertised on meetup.com. We are outgrowing the pizza place ... had 10 people show up last week.

I'm lucky - there is a scripting or Linux meeting almost every week. A few groups do free training every other Saturday - the Ruby guys are like that. Basically, they follow a book and lead noobs to Ruby through it with full sessions on TDD and git along the way. It really is a complete how-to-become-a-ruby-programmer course .... all for free.  Last year, they started recording the sessions, but not until we were 50% done. Since Ruby and/or Rails completely changes every 2 years, it is hard to stay current.  Last year we used v1.9.3 and Rails 3.0.  This year we are using Ruby v2.0.0 and Rails 4.0.0.  Enough has changed to make using the new environments a challenge.  Plus my 5 Ruby/Rails books are all out of date now ... er ... AGAIN.

I bet if you setup a meetup just to go over LPI training and setup a google group + weekly chats, people would come.

---

### Post by mynamesalex on 2013-09-28
> **TheFu said:**
> I bet if you setup a meetup just to go over LPI training and setup a google group + weekly chats, people would come.

I really like that idea.  If I just post it on the meetup site and call for a LPI training / study group, that should be easy.  I'll figure out where and when I wanna do it.  Thanks for the tips.

---

