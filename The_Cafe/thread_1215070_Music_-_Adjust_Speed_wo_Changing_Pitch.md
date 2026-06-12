---
title: "Music - Adjust Speed w/o Changing Pitch?"
date: 2009-07-16
forum: The Cafe
---

### Post by XubuRoxMySox on 2009-07-16
In WinXP I used to use a FOSS program called [clogamp]("http://clogamp.com") to slow music down and speed it up on demand (without changing the pitch - no super-deep or chipmunk voices) in my dance class... it kinda sorta works in Ubuntu with Wine, but I'd rather use something that works in Linux. I'm aware of one from the Ubuntu repos, and I played with it a little but it's not as good as clogamp in Wine. Soes anyone know of another I should try?

Thanks,
Robin

---

### Post by dragos240 on 2009-07-16
Well, you can do this in audacity, and play it there. Easy. But I know thats not what you mean.

---

### Post by doorknob60 on 2009-07-16
It works in Audacity. I think it's called change Tempo (I think there's also one that does pitch). I like playing around with Audacity sometimes, it's fun :P

EDIT: Yeah, just import the file, press CTLR-A to select all, then go Effect > Change Tempo

Click [here]("apt:audacity") to install it (in Ubuntu)

EDIT2: Looks like clogamp should compile in Linux, give it a try!

---

### Post by Chilli Bob on 2009-07-16
Alsaplayer can change the speed, but I can't remember if it maintains the pitch.

---

### Post by Kopachris on 2009-07-16
> **doorknob60 said:**
> It works in Audacity. I think it's called change Tempo (I think there's also one that does pitch). I like playing around with Audacity sometimes, it's fun :P

EDIT: Yeah, just import the file, press CTLR-A to select all, then go Effect > Change Tempo

Click [here]("apt:audacity") to install it (in Ubuntu)

EDIT2: Looks like clogamp should compile in Linux, give it a try!
+1.  Ditto about Audacity.  I've played around in it a little (made some binaural beat tracks).  Audacity can definitely change tempo without changing pitch.

---

### Post by init1 on 2009-07-16
> **Chilli Bob said:**
> Alsaplayer can change the speed, but I can't remember if it maintains the pitch.
Alsaplayer changes the pitch (great audio player btw)

---

### Post by XubuRoxMySox on 2009-07-17
Thanks, everyone. Very helpful! I've been hoping to dump Winblows from the laptop I use for the dance class, and this was the last hurdle. I can be Windows free now! Yippieeee!

-Robin

---

### Post by Ndlovu on 2009-07-30
I was actually looking for a way to do something similar (I need to play interview transcripts slowly enough to catch what's being said but still be able to recognise people's voices). I figured out how to do it with mplayer, together with the tap-pitch plugin. Unfortunately I can only get it working from the commandline, but if you're happy with that, it might work for you. It has the advantage that you don't need to actually alter the file - it just works as a filter to change the playing parameters. It won't work for you if you need to change things dynamically (increase or decrease tempo while the music is playing). You can look at my notes to see if it might be useful:
[http://ubuntuforums.org/showthread.php?t=1226982](http://ubuntuforums.org/showthread.php?t=1226982)

---

