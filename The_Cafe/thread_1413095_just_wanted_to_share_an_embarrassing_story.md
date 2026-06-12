---
title: "just wanted to share an embarrassing story"
date: 2010-02-22
forum: The Cafe
---

### Post by birnam on 2010-02-22
I am utterly humiliated. And I figure, if there's a lesson to be learned here, maybe I should share.  :D  Besides, it might cause a chuckle or two.

I'm running Kubuntu 9.10, and recently I'v gotten a little worried about the health of my system. I've got three physical drives hooked up with six or seven partitions, and one of my drives has been going crazy. CRAZY. For two or three hours at a time, I would hear absolutely constant hard drive chatter. It would stop randomly, and then start up again later.

It didn't seem to have anything to do with what I was working on. In fact, my system didn't seem to know what was going on. My CPU could be down around 3-6%, and my Disk I/O (as reported by conky) could be 0 - 24Kb/s or so. The system was responsive. Running iotop gave me nothing useful, just a bunch of zeros. I was baffled.

Keep in mind this is happening in the middle of a tight deadline. The thing is, if I was about to lose a hard drive to corruption, that would kill my deadline too. So I buckle down and got to fixing it.

I search everywhere online that I could find for other people with problems of continuous hard drive activity -- especially where io was still low. Nothing useful, just a couple dozen dead ends. I start going through my partitions, and unmounting them one at a time. No change. I run netstat to see if somebody else was doing this to my system -- nothing. I check my system's logs and my router's logs -- nothing out of the ordinary. I run chkrootkit to see if I'm infected with anything -- still nothing. I verify that my swap disk is correct in /etc/fstab; I even reformat my swap disk. Hard drive is still chugging away. I get around to the grub2 update I've been meaning to do. Still nothing.

I try running fsck on my disks and keep running into various problems with bad magic numbers, so I figure it's finally time to step back and start working externally. I download and burn a LiveCD to reboot the system into. 

I shut everything down for a reboot -- and in that brief second between when the fans shut down and they start whirring again, I could STILL hear the hard drive chugging along! I kill the reboot process and shut down the computer again. Fans are completely silent. All lights are off. Hard drive is still happily chattering away.

I start questioning my sanity at this point.  I've been working on this about three hours now. It's well past midnight.

Maybe it's the hard drive on my xbox? I didn't think the xbox was even on, but it is on the other side of my desk... Nope. It really was off.

But from my crouched position next to the xbox it suddenly seemed like the noise was coming from above me. I put my ear right next to my computer, and it still sounded like it was from above me. I look up... And reach up...

And with the lightest touch from one finger, the heat register on the ceiling stops buzzing. And there was complete silence.

](*,)

So here's the moral to the story: the easiest problems can seem insurmountable if you're looking for a solution in the wrong place.

---

### Post by cariboo on 2010-02-22
I'd like to use that meme, that we aren't supposed to use anymore, but I'm glad it worked out for the best. It's happened to us all at one time or another.

---

### Post by squilookle on 2010-02-22
When I first left home and moved into a student flat with some friends, an alarm went off at 4am on my first night there. I was groggy and thought my alarm clock was going off. So, I pressed snooze and it didn't stop. I turned off the switch at the back, and when that didn't do anything, unplugged it from the wall. I was now worried it was going to wake my housemates and started bashing the clock against the wall. 

That was the point where my housemate came into my room, asked me what I was doing, and pointed out it was the fire alarm.

---

### Post by gymophett on 2010-02-22
Doh!

---

### Post by The Real Dave on 2010-02-22
I hate then that happens. I run Squid on my server, and Squint to analyse the reports. One day it stoped working. I spent hours, late into the night, recompiling and re-configuring, changing cron jobs and directories. 

I finally gave up and went to bed. 

In the morning, I booted up and saw my mistake instantly. I changed "sh" to "bash" in the cron job, and the world was at peace again :)

---

### Post by crlang13 on 2010-02-22
I do stuff like that in programming all the time - misspelling variable names or commands...

grr.

---

### Post by nothingspecial on 2010-02-22
When I got my first computer, it had Feisty on it and the sound didn`t work.

 So I consulted google and went about recompiling alsa and modprobing this and that and editing alsa-base.conf and doing all kinds of fancy linux stuff.

It turned out, that you had to plug the speakers into the blue hole.

---

### Post by audiomick on 2010-02-22
During my years as a sound tech I have had any number of "what's that funny noise?" and "it worked after I  finally realised the cable wasn't plugged in" stories.

A favourite (because it wasn't my mistake...) is the time when someone came to me at the mixing desk and told me he could hear a signal tone further forwards towards the stage. I went looking, heard the tone, looked for it for a minute or two and finally tracked it down to a stage hand with a walkie talkie on his belt. The battery was low, the walkie talkie was emitting a constant loud tone, and the guy hadn't even noticed it.:D

---

### Post by dragos240 on 2010-02-22
> **cariboo907 said:**
> I'd like to use that meme, that we aren't supposed to use anymore, but I'm glad it worked out for the best. It's happened to us all at one time or another.

What one? I like memes. Do you think that CATS could be inside the...... wait.... nevermind.

---

### Post by koleoptero on 2010-02-22
Back in 2000 my brother gave me an old pc he had, and I was vastly dissappointed that it didn't have a modem.

2 years later I buy a new pc and I disassemble the old one for fun and it turns out that it did have a modem. For two years I didn't have an internet connection just because I thought it didn't have one. How lame is that?

---

