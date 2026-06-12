---
title: "Ubuntu 8.04 (Beta) on Pangolin"
date: 2008-03-24
forum: System76 Support
---

### Post by Gonzell on 2008-03-24
I've recently installed the new Ubuntu 8.04 (Beta) and I've been having quite a few issues. I'm just going to list them here.

- Suspend no longer works. It will not respond to anything once suspended

- Mic still sounds horrible

- Webcam is now very slow in Cheese

- Extremely slow startup times

- The Ubuntu startup loading graphic doesn't load, instead I get a flickering cursor that moves around...

- Sometimes freezes when trying to restart

- Compiz fusion no longer will start, I get this error:
chesley@chezb-ubuntu-m:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

- Browser rendering seems to be a bit quirky (tried Firefox and Epiphany). I'm not even quite sure how to explain it...

Anyway, this was way more than what I was expecting. I use my laptop too much to deal with these issues right now. Is it possible to revert back to my stable 7.10?

Thanks

---

### Post by thomasaaron on 2008-03-25
Most of that should be fixed by the System76 driver when we update it.
Also, regarding suspend... Did you load 64-bit or 32-bit?

And, you didn't say which Pangolin you have. That could make a big difference in the fixes for some of those issues.

---

### Post by Gonzell on 2008-03-25
How do I check what system76 Pangolin model I have? When I run the System76 Driver program now, it won't work now that I have 8.04.

I run 64bit Ubuntu.

Is there any safe way for me to roll back to 7.10? I don't want to lose anything in my home directory.

---

### Post by thomasaaron on 2008-03-25
> How do I check what system76 Pangolin model I have? 

What is the model number on the bottom of the computer? With that info I can tell you.

> When I run the System76 Driver program now, it won't work now that I have 8.04.

The driver will not work on Hardy until we have finished testing and Hardy is officially released (i.e. the end of April).

> Is there any safe way for me to roll back to 7.10? I don't want to lose anything in my home directory.

You will either have to install 7.10 on a separate partition or do a fresh install on it.
If you do a fresh install, just copy your home directory to an external storage device. NOTE: It's not a good idea to keep all of your configuration files from version to version. Sometimes doing so can cause problems.

---

### Post by Gonzell on 2008-03-26
I don't think I'm going to go through the trouble of re-installing Ubuntu now. Things are starting to look up. Compiz is working again and so is Suspend (however Hibernation is not...the computer never shuts off).

The webcam is still horribly slow in Cheese...I haven't tried it in anything else yet. Hopefully this is fixed soon because I do use my webcam for conferencing a fair bit. As well as I hope you guys get the mic working correctly because it's getting pretty darn annoying.

The Ubuntu start up time isn't as bad anymore, however the loading graphic still flakes and disappears to a blinking cursor.

My model number is FL90.

---

### Post by Gonzell on 2008-03-26
I'm still having no luck with getting my microphone to be clear. And I've also noticed that since my update to 8.04, I can no longer play music and have an audio conference at the same time.

Note that I'm hoping that by posting these problems here that system76 will ensure these issues are resolved when 8.04 rolls out.

---

### Post by thomasaaron on 2008-03-27
Testing begins on Monday and will run through to Hardy's release.
We are indeed keeping an eye on the forums.

I would ask that you guys not post Hardy-related bug reports to our Launchpad site. Our testing procedure is very thorough, and it doesn't really make sense for us to take time away from that procedure to try to squash bugs this early in the game.

Most of them will probably just go away anyway between now and Hardy's release. Or they will be solved during our testing process.

Maybe a dedicated thread based on your Hardy issues (like this one, but not just for Pangolins) would be a good idea.

---

### Post by Gonzell on 2008-04-01
Hmm...just going to point this out here I guess...browsing folders has gotten very slow for me since my update to Hardy. Has this happened to anyone else?

---

### Post by Gonzell on 2008-04-02
I've noticed something very irritating today. When my batter is low...my laptop makes these very LOUD beeps....it's like crazy loud and sounds horrible. What kind of feature is this...and how is it disabled? Also...my laptop is suppose to Hibernate when the batter gets so low (Hibernate doesn't work properly to begin with, but that's another story), but instead it simple shuts off.

Oh...and whenever I use Shutdown...the laptop makes another horrendous BEEP. Once again...how do you disable this?

I'm still using the Hardy Beta, so I'm being understanding of the lack of Suspend and Hibernate functionality.

On a side note...has anyone noticed that the new Pidgin is fairly unstable?

---

### Post by thomasaaron on 2008-04-03
That's the first I've heard about the loud beep.
We've not seen it yet in testing.

Is there by chance a setting for it in System > Prefs > Power Management?

---

### Post by Vadi on 2008-04-03
I thought of doing my own testing too, but decided that it's better for system76 to do that and lemme know when it's OK to upgrade.

Good luck to you though... hope you get it in a usable state, since as I understand, that's your production machine :|

---

### Post by Gonzell on 2008-04-03
Thanks Vadi. My laptop is still "usable" per say....just a lot of things are broken that would really make my day if they weren't. (Oh, and I noticed you're using my Avatar, heh heh, w00t)

The only thing I noticed in "Power Management Preferences" was under General, "Use sound to notify in event of an error". I haven't tried disabling it yet...but in all fairness...I would like a sound to be made if there is any "Errors", just preferably with the laptop speakers and not the motherboard speaker...

I've also noticed that the laptop does not go to "Sleep" as I have set under "On Battery Power" -> Put computer to sleep when inactive for 15 minutes. As of right now...this is probably a good thing that this does not work because Suspend still isn't functioning perfect. When I resume from suspend sound doesn't work until I restart the computer and certain applications crash that were left open...such as Pidgin and Eclipse...maybe even Firefox...can't remember now.

---

### Post by thomasaaron on 2008-04-04
Do you get a white screen when you resume from suspend? If you do, try typing your password and hitting enter. This is a bug with Hardy on nVidia machines.

---

### Post by Gonzell on 2008-04-04
The white screen thing has happened to me a few times....I think it only happens when I use "Switch User" though. I figured out that I only had to type in my password already though ^_^

---

### Post by Gonzell on 2008-04-26
Now that 8.04 has been released and I've done a fresh install of it, things are looking a lot better. Most of the problems I was having have been resolved.

However, one really nasty problem still exist. When I resume from Suspend, my sound is no longer working.

Any ideas? What other information should I provide?

EDIT:
Other problems that still exist:
- Skype cannot use audio while another program is using the device
- Microphone still has the crappiest quality I have ever heard before

---

### Post by Vadi on 2008-04-26
Same issue here. I've tried searching on how to restart the pulseaudio thing, but no luck so far.

---

### Post by thomasaaron on 2008-04-28
Please file a bug report on that one, if you don't mind.
Very interesting. We'll try to duplicate. Include your computer model (i.e. which Pangolin do you have?).

[https://launchpad.net/system76](https://launchpad.net/system76)

---

