---
title: "Offline repository via cache good idea?"
date: 2016-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by mintmag on 2016-11-22
Hey guys. So I'd like your thoughts on something. I was trying to create a local repository with apt-mirror. There are two reasons for this. I like to be able to take my software with me, and the idea of having the entire repository on a hard drive just seemed really cool to me. My very own portable app store. Sure it's over 100 gigs but that's really nothing for today's hard drives. 


However apt-mirror wasn't doing it for me. I found it complicated and I just couldn't get it to work. So instead I opted to try something else. If apt can't find what what it needs from the repository it will look in the cache/archives for it instead. So I thought what if I downloaded every single .deb file from the repo and placed it into a cache and then configured that cache to be used on a mounted SSD drive. I created a 99config file in apt.conf.d with this code
```

dir::state::lists /home/mitmag/Desktop/pocket/LIST;
dir::cache::archives /home/mitmag/Desktop/pocket/DEBS;

```

It worked perfectly and I was really happy with the results. There was no tutorial on doing this either, I had to work this on my own. As long as you don't clean the cache you'll be fine. Otherwise you'll have to download all debs again. I was thinking of writing a tutorial on how to do this. Would anyone be interested?

---

### Post by vasa1 on 2016-11-22
> **mintmag said:**
> ... I was thinking of writing a tutorial on how to do this. Would anyone be interested?
A tutorial will be most appreciated. You may know that we have a special section for tutorials here: [Tutorials Sub-forum]("https://ubuntuforums.org/forumdisplay.php?f=100")

However, tutorials are expected to be of a high standard and the guidelines in [the sticky here]("https://ubuntuforums.org/showthread.php?t=2143602") should be followed strictly.

Needless to say, the tutorial should be about Ubuntu or any of its officially supported flavors. It should not be about other distros even if they are derived from or related to Ubuntu.

We would also expect you to keep your tutorial updated and we would expect you to be responsive to any queries relating to it.

Please note that one of the drawbacks of having offline repos, no matter which distro, is that these need to be kept updated for security purposes. It would not be advisable to have a tutorial that doesn't cover this vital aspect.

[CENTER]:::[/CENTER]
Thread re-opened at OP's request.

---

### Post by mintmag on 2016-11-22
Would anyone else be interested in this sort of thing?

---

### Post by mastablasta on 2016-11-23
it would make more sense to get KeryX maintained again: [SIZE=2]http://www.webupd8.org/2010/03/keryx-0924-offline-installer-for-apt.html

apton CD looks dead but method is worth a look: 
[SIZE=2]http://aptoncd.sourceforge.net/

another similar attempt: 
[SIZE=2]http://sushi-huh.sourceforge.net/





[/SIZE]



[/SIZE]



[/SIZE]

---

### Post by mintmag on 2016-11-23
That's probably not going to happen. also I don't think you can use those to save an entire 100 gig + repo.

---

### Post by mastablasta on 2016-11-23
how big is the whole official repo ? debian stable has 3 dvd images. for example AMD64: [SIZE=2]http://cdimage.debian.org/debian-cd/8.6.0/amd64/iso-dvd/
[/SIZE]

---

### Post by mintmag on 2016-11-23
It's a little over 100 gigs I think.

---

