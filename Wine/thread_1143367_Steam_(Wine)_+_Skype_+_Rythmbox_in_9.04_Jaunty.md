---
title: "Steam (Wine) + Skype + Rythmbox in 9.04 Jaunty"
date: 2009-04-29
forum: Wine
---

### Post by Caedis on 2009-04-29
Okay, after weeks of trolling Google and these very forums I have yet to find a solution. I have literally used Ubuntu for years now and have ALWAYS found a solution to any and every problem I've had by doing searches. You'll notice my account here has been in effect for a while with very few posts. I'm a big believer in Google and the search function of our lovely forums here, but no one has come to a consensus on this issue.

I just need to get Source based games to share the adapter with my native apps. Skype and Rhythmbox. 

At a bare minimum I need Skype and Steam (specifically Left 4 Dead and other source games like Gmod, Counter Strike, and HL2) working simultaneously. I'll cover what I've done thus far.

Set all Steam games launch parameters to &#8220;-windowed 1 -dxlevel 81&#8221; 
	-this worked at getting sound back to my steam games, as I had lost sound during a steam/wine patch a month ago. (Sound is choppy and barely comprehensible, but I can deal with it if I can just get Skype working)
	-Set my Wine sound settings to ONLY ALSA, everything else unchecked. (also tried every other config) Default same rate 44100 with Driver emulation and Emulated hardware acceleration. 16 Bits per sample.

I have the latest stable wine build as of this writing (1.1.20)

My build:
Linux 2.6.28-11-generic #42-Ubuntu SMP x86_64 GNU/Linux

I also should note that my sound works fine with other wine games, (TES Oblivion, World of Warcraft, Spore) and when I say fine, I mean perfectly clear crisp sound... but if I start Skype or Rhythmbox I don't get sound until I kill all three and start the game first. The sound adapter must be monopolized by wine or it wont output. 

Additionally testing the sound in Wine has never worked, with or without games or native apps running.

[IMG]http://caedis.files.wordpress.com/2009/04/winesoundfailed.jpg[/IMG]

If anyone needs debugging output I'd be happy to oblige.

---

