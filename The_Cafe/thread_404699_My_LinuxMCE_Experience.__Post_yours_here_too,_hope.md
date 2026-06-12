---
title: "My LinuxMCE Experience.  Post yours here too, hopefully the Developers will read this"
date: 2007-04-08
forum: The Cafe
---

### Post by bobbob1016 on 2007-04-08
I decided to replace my Windows Media Center with LinuxMCE.  I took out the drive with Windows (so I wouldn't hurt anything), and installed Ubuntu on a new drive.  I have the PC in question hooked up to my HDTV, which caused enough problems of it's own to get the native 1366x768@60 resolution in Ubuntu.
After installing the drivers for my ATI card, gnome recognized the 1366x768@60 resolution.  I then went to install LinuxMCE.  After I downloaded the iso, and finished the install.  I told it not to be a DHCP server, but it didn't look like it listened, see below.  When it booted up, and changed my PC's name without asking, it didn't auto-login, or auto-start after I logged in.  After logging in, I see "Failed to initialize Hal", I reinstalled HAL (I've done this on my desktop ubuntu without problems).  I thought, "After the reboot, there'll be a few setup options, then I'll be done." this wasn't the case.
LinuxMCE didn't see my "1366x768@60" resolution, but after asking on the IRC channel, and making an idiot of myself, *(see edit)I thought "google LinuxMCE forums" and there they were, not easy to find on the site, but through google.  I found the answer was to go to the LinuxMCE's IP, and do some setup there.
Then I thought, ok, I'll play around with it a bit, and see what's where.  I tried my remote, the bias video (I don't think it was officially LinuxMCE's but still) said it would do it automatically, but no.  I had to navigate through menus with the keyboard.  The "Wizard" didn't set me up as a user either, which I did by accident when I went to the IP address before.  After looking around for how to watch TV (I have two tuners, an ATI TV Wonder, and HDTV Wonder, both of which MythTV support, but no auto-configuring here).  
Now I go to Media, and there isn't anything there, as I'd expect, but there isn't any "Add Media" button, and it didn't automatically find my FreeNAS, which the video said it would, I have the same login name on the FreeNAS that I gave to the Ubuntu and LinuxMCE install, but it didn't "auto-find" it.  Maybe that is because I didn't set it as a DHCP server, although since my computers can still connect to the internet with static IP's and my parents are yelling that they can't get online now, I guess LinuxMCE didn't listen.
When I go to setup MythTV in the hidden tab that I can't remember the name of, I get an onscreen keyboard, a part that says "Mouse" with Left and Right under it, and a dot with chevrons boxing it in, on the left.  How is that the MythTV setup?
When I try to exit LinuxMCE and get to my desktop I can't.  When I press the power button, all I get is the LinuxMCE startpage.

//End Rant.

I hope these issues get fixed, because LinuxMCE looks great, but still has to mature.

It is also great that they offer free skype tech support, maybe this means they know some of the issues I had.  I prefer to post them here though, because I can think about what to say, and make sure everything is there, and correct before anyone sees it.

Edit:  I wasn't angry when I posted this, I was frustrated.  What I left out was that it took me a day or two to get Ubuntu to show up on my TV properly.  My frustration might have been why I didn't see the "Forums" button on the right.  I'm not angry at them, I just saw a post by one of the developers looking for help on these forums, so I thought I'd post here, since they probably read these, instead of signing up for another forum just to post one thread.

---

### Post by DoctorMO on 2007-04-08
Er the developers arn't going to read your rant. the first point is to list out your problems in a form that is broken down:

1) Unable to locate forums through LinuxMCE website or MCE Software
Problem: During the course of trying to configure and set up the MCE system I was unable to find support and help for LinuxMCE as I would expect.
Solution: A kind person on IRC pointed me towards looking for the MCE forums through the google search engine.
Suggestion: Making an easy link from the main MCE website and from the MCE software it's self.

etc etc,

Then you must post this non rant form of your complaints in the bugs section or the forums where the MCE developers deal with their bug reports.

The last thing you want to do is get emotional, show that your angry or upset; don't insult their work by saying it's not mature or not good enough despite how tempting it is to do so.

Calm, collected and in the right place and the devs will attend to your problems as soon as they are able.

Ranting in a user forum won't really help anyone, that is the problem I have with 'Linux not readdy' threads too, they're expecting linux devs to browse and scry these forums and every user forum for tid bits of problems when it just isn't the case they have pre set ways of dealing with problems and bugs mostly bug trackers, email lists and sometimes their own forum.

Make it clear that your not looking for work arrounds you just letting them know these problems present a barrier to users when they first install.

Good luck

---

### Post by wjston on 2007-04-09
> **bobbob1016 said:**
>  after asking on the IRC channel, and making an idiot of myself, I thought "google LinuxMCE forums" and there they were, not easy to find on the site, but through google..

I too tried installing LinuxMCE on a spare computer, but was unable to get it working. However, to respond to the above comment about the forum not easy to find on the site - [ATTACH]29346[/ATTACH]. I realize this project promised "out of the box" workability, which definitely isn't the case; however, I do believe this may improve greatly in future releases. The person developing this software has put an enormous amount of work into this, and should not be blamed for something that you failed to see on what is a very well laid out web page.

That said, I believe that this is not a MCE software that should be installed by the inexperienced linux user or newbie - it is just not plug-&-play.

---

### Post by deadguy87 on 2007-04-27
Thanks for warnig people. I was think of forgoing my usual wait and intalling it today. Normally I wait till I see a 2.0. I will get it and set up my home to take full advantage of it. I have a camera on my front door and remote lights already to get a media center that controls all that and makes Win MCE look like web TV will rock,

---

