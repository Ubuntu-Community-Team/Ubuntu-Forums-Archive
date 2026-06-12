---
title: "Karmic Koala brief rant/rave and sound advice...literally."
date: 2009-10-30
forum: Testimonials &amp; Experiences
---

### Post by Ghost|BTFH on 2009-10-30
I don't know about any of you, but I love the new features of 9.10.  There are a few pet peeves, like a super communication notifier that doesn't do anything at all (just sits there like a bump on a log, never notices mail, IMs, anything on my system - it's happened on other people's systems right out of the box, and they have it marked as a low priority, c'mon devs...if the thing doesn't work at all, that's not a low priority.)

Anyhow, I digress...the REAL ISSUE I have with our sweet cuddly Koala is he's using Pulse still.  Bad Koala! Put down the inferior sound server!

Just a suggestion to those who hate Pulse as much as I do (which would only be a scarce few in this world, I'm sure...) they have made it amazingly easy to take care of.

First, simply go into Synaptic Package Manager (System - Administration - Synaptic Package Manager for those of you who are new) and do a search for pulseaudio.  From this search, find PulseAudio and PulseAudio-utils and mark both for removal (don't panic when it tells you it's going to remove the desktop, it won't remove "the desktop").

After this, search for ALSA and install alsa-oss and (I personally do this even though it's not needed) alsa-tools.

Reboot.

You're now running a system without cracks, pops, hisses, lagging sound, lockups, audio mysteriously dropping out from one program but not another, etc etc etc.

With this setup I can run a game under wine (winecfg audio set for ALSA) listen to music on rhythmbox and still hear bloops from my instant messenger (Pidgin of course, who'd want to use Empathy until they add a feature to NOT LOG EVERY CONVERSATION YOU HAVE...silly devs)

This post has been part rant, part rave and part advice.  If the rant offended you, I apologize.  It's just my opinion.  If the rave excited you, it should!  Aside from a few issues, Karmic Koala is a beautiful build.  If the advice helped - awesome.  Glad to be of service.

For flames or anything else, I direct you to the "Reply" button...go ahead, you know you want to...it'll make you feel better in the end...you can go off and tell me how awesome Pulse is. ;)

Cheers,
Ghost|BTFH

---

### Post by 5nak3 on 2009-10-30
Hi there, this is an interesting post as I did notice a sound drop when trying to play Urban Terror, which made the game freeze and the only way to shutdown was through ctrl+alt+f1 and "killall" I did notice in this instance pulseaudio was also eating a lot of my resources as shown by my "top" list.

Another thing I've noticed in Karmic as opposed to Jaunty was in Karmic you cannot really control the individual controls for volume as Jaunty allowed e.g. Master, PCM, headphone etc were all controllable by the sound applet in the top panel in Karmic this is not the case. In fact the applet seems overly complicated.

I managed to correct this by installing GNOME Alsa Mixer although it is a clunky way of sorting out my sound.

So my question if you could answer is this:

Pulseaudio has only shown one problem for me so far (Urban Terror incident), it works without cracks and pops etc, would I benefit from Alsa instead of Pulse what is the underlying difference? And what was Jaunty using?

Many Thanks

---

### Post by Erszebet Lunah on 2009-10-30
Oooh such a nice reply button...must..resist...presssiiinggaaaaah! Too late ><

Also; pulse-*fweet*-audio ro-*krrrr*-cks !!


Since I can't risk losing a working system (read: no other OS installed...) I think I'll wait a little longer before an upgrade is in order...

---

### Post by Ghost|BTFH on 2009-10-31
> **5nak3 said:**
> So my question if you could answer is this:

Pulseaudio has only shown one problem for me so far (Urban Terror incident), it works without cracks and pops etc, would I benefit from Alsa instead of Pulse what is the underlying difference? And what was Jaunty using?

Many Thanks

Mmmm...well, at the risk of being flamed into oblivion, I'll tell you.  Pulseaudio is a clunky, inelegant resource hog of a sound server that couldn't graciously kill a process even if it went to assassination school for a year.

ALSA is professional, smooth, been around for years and years, isn't a resource hog, works fantastically, gives you more options for your hardware than you may ever want to see (depending on your hardware) and sounds beautiful.

Now, the downsides...Pulseaudio is a sound SERVER, which honestly is it's major malfunction.  It doesn't focus so much on doing one thing right, as it does doing half a dozen things wrong.

ALSA is NOT a sound SERVER.  It runs sound on YOUR system and YOUR system alone.  It is also closed source, not open source software.  And by that I mean there are a few drivers etc that they don't share the code for.

Now, if you are a purist who wants your system to be 100% pure open source (and just the fact that you want some decent sound on your system kind of defeats that whole idea right there) then you would NOT want ALSA, as it has some closed source elements.

So, to use the assassin analogy again, you may choose to use the 13 year old on a sugar high with a mail opener who will share all the gory details with you...

Or you may choose the professional gentleman from Italy who will not tell you how he did it, just that the job got done.

In short, ALSA will give you more system resources, cleaner sound and better responsiveness.

Jaunty was also using Pulseaudio...this ugly beast has been around for a few distros now and I fear it's not going away, even with all the people saying they hate it (and the majority finding ways to work around it as a 1st step in making the "perfect" desktop).  I think that there's enough developers and fans that quite frankly, those who make the big decisions on what goes into Ubuntu, never hear the dissent.

Cheers,
Ghost|BTFH

---

### Post by mellery on 2009-10-31
How do I use my laptops sound media keys (up, down, mute) and also my soundlevel in the taskbar have disappeared.  Do you know how I can get those back?  Removing pulsaaudio did fix all my sound playback problems though!

---

### Post by Ghost|BTFH on 2009-10-31
> **mellery said:**
> How do I use my laptops sound media keys (up, down, mute) and also my soundlevel in the taskbar have disappeared.  Do you know how I can get those back?  Removing pulsaaudio did fix all my sound playback problems though!

Try System -> Preferences -> Keyboard Shortcuts and see if those might just do the trick for you.

Cheers,
Ghost|BTFH

---

### Post by mellery on 2009-10-31
those look like they are set up right, but maybe they are still trying to change the volume with pulseaudio?

---

### Post by Ghost|BTFH on 2009-10-31
> **mellery said:**
> those look like they are set up right, but maybe they are still trying to change the volume with pulseaudio?

I wish I knew a lot about such things, but sadly I have limited knowledge in this area...

What I could suggest is trying to create some custom key commands:

System - Preferences - Keyboard Shortcuts

Click "Add"

Give it a name like: "ALSA Volume Up"
Give it a command of: "aumix -v +5"

Then bind it to your volume up button.

Then do the same thing (command being "aumix -v -5") for Volume Down

Then perhaps one for mute (command being simply "mute")

Not sure if these would work or not (as I have kicked Koala to the curb until they fix more bugs...like when Lucid comes out) but these are some suggestions that might help.

Cheers,
Ghost|BTFH

---

### Post by mellery on 2009-10-31
those work great! thanks again!  I'll try PA again next release, but its too much trouble trying to get it to work

---

### Post by Ghost|BTFH on 2009-10-31
> **mellery said:**
> those work great! thanks again!  I'll try PA again next release, but its too much trouble trying to get it to work

No problem, happy to help.  I have an older keyboard (from around y2k) that has a ton of multimedia keys, no branding, and letter keys that have almost turned pure black from excessive use.  There's a couple of the multimedia keys that I wanted to make useful again (Like the old DOS key I wanted to use to fire up my terminal, the phone button I wanted to set up for Skype, etc.) so I just did some simple study on it.

And yes, you could actually turn your volume up button to open email if you wanted.  It's really simple once you know the tricks.

Cheers,
Ghost|BTFH

---

### Post by solwic on 2009-10-31
> **mellery said:**
> How do I use my laptops sound media keys (up, down, mute) and also my soundlevel in the taskbar have disappeared.  Do you know how I can get those back?  Removing pulsaaudio did fix all my sound playback problems though!

You can remove pulse audio? How the #$@! do you do that?!?!?!

---

### Post by Ghost|BTFH on 2009-10-31
> **solwic said:**
> You can remove pulse audio? How the #$@! do you do that?!?!?!

Read the first posting...

:)

Cheers,
Ghost|BTFH

---

### Post by solwic on 2009-10-31
> **Ghost|BTFH said:**
> Read the first posting...

:)

Cheers,
Ghost|BTFH

Ahhh!  Well, the startup sound was crackling and messed up...but after boot, the sound is freaking amazing!

Thanks for the tip!  (Although, I couldn't find ESD or alsa-tools in synaptic....)

---

### Post by HappyFeet on 2009-10-31
> **solwic said:**
> Ahhh!  Well, the startup sound was crackling and messed up...but after boot, the sound is freaking amazing!

Thanks for the tip!  (Although, I couldn't find ESD or alsa-tools in synaptic....)

ESD is esound. It is in synaptic.

---

### Post by solwic on 2009-10-31
> **HappyFeet said:**
> ESD is esound. It is in synaptic.

I saw esound.  Didn't know it was the same.  Should I go ahead and remove it?

---

### Post by 3rdalbum on 2009-11-01
> **Ghost|BTFH said:**
> First, simply go into Synaptic Package Manager (System - Administration - Synaptic Package Manager for those of you who are new) and do a search for pulseaudio.  From this search, find PulseAudio and PulseAudio-utils and mark both for removal...

You're now running a system without cracks, pops, hisses, lagging sound, lockups, audio mysteriously dropping out from one program but not another, etc etc etc.

For sound cards that have well-written drivers or have been updated to fix the underlying issues exposed by Pulseaudio, you'll gain nothing and you'll lose the ability to properly control which sound devices get used by which programs; you'll also lose the individual volume controls on applications.

Don't get people into the habit of ripping out Pulseaudio every time. For a lot of people it works well out-of-the-box. For even more people, it works well with a little bit of configuration (which can be done without an extra download in Karmic). For even more people, it works well with a sound driver update.

---

### Post by nico.vanrensburg on 2009-11-01
um. i don't want do be the odd one out here, but...removing alsa and reinstalling pulse solved all of my problems. it might be heavier on resources but it's picking up the subwoofer on my lenovo without a problem. and being able to control individual application's volume is handy.. 

watcha gonna do :)

---

### Post by jackmetal on 2009-11-01
I may try removing pulse and see if alsa works for me.  Will alsa pick up my 7.1 system without doing any configuration, or is there something I'll probably need to edit for it to work?  

Right now, pulse only outputs sound to my front speakers and nothing from any of the others (although I have tried editing the config file, picking different drivers, etc..)  If alsa gets my 7.1 back, I'll be VERY happy with Karmic (other than the Remote Desktop/Compiz bug that's "STILL" around).  :-)

---

### Post by zampes on 2009-11-01
No thank-you for Ghost|BTFH; the only thing this has gotten me is absolutely NO sound and no recognition of my sound card by the system.
Geez, don't go around telling people to do stuff that doesn't work at all.

---

### Post by Nick Brohman on 2009-11-01
Thanks for the tip as it has restored my Skype volume. 

Mine disappeared after adding Ubuntu Restricted. 

I've only had 9.10 for just under 2 hours & am starting to like it...now where has the volume Control gone...manana, manana...

Cheers...Nicko

---

### Post by solwic on 2009-11-01
> **zampes said:**
> No thank-you for Ghost|BTFH; the only thing this has gotten me is absolutely NO sound and no recognition of my sound card by the system.
Geez, don't go around telling people to do stuff that doesn't work at all.

Worked great for me in Jaunty on my Acer Aspire 3680.  Yeah, it's a few years old, and nowhere near top of the line, but ditching pulse and adding alsa actually makes my system sound better.  And the glitches are gone, the hiccups, the lagging...all gone with pulse.  

But hey, use whatever works for you.  Just don't say this stuff "doesn't work at all"; it worked wonders for me.  :)

---

### Post by Nick Brohman on 2009-11-01
> **solwic said:**
> Worked great for me in Jaunty on my Acer Aspire 3680.  Yeah, it's a few years old, and nowhere near top of the line, but ditching pulse and adding alsa actually makes my system sound better.  And the glitches are gone, the hiccups, the lagging...all gone with pulse.  

But hey, use whatever works for you.  Just don't say this stuff "doesn't work at all"; it worked wonders for me.  :)

I'm with you solwic.

Further to my previous post I added Gnome Mixer ALSA from synaptics & all is OK.

One thing that I have found is that the Mic boosts will create snap, crackle & pop...I mute or turn down both boosts & I find this mixer to be a vast improvement on 9.04.

Cheers...Ncko :guitar:

---

### Post by Tamlynmac on 2009-11-01
> solwic
Worked great for me in Jaunty on my Acer Aspire 3680. Yeah, it's a few years old, and nowhere near top of the line, but ditching pulse and adding alsa actually makes my system sound better. And the glitches are gone, the hiccups, the lagging...all gone with pulse.

+2
Seems to be contagious.

---

### Post by Shelton2142 on 2009-11-01
The only sound related problem I've been having is with the speakers I have connected to the front ports on my system unit. I plug in and it doesn't have any sound coming out. The back ports seem to be functioning just fine, though. That's where my monitor's sound is hooked up. I use a 24-inch Acer LCD with built-in rear speakers.. I know it's specifically a problem with Karmic, because when I restart and boot with Windows XP, the speakers work again.

---

### Post by jackmetal on 2009-11-01
Unfortunately it didn't work for me.  :-(

It's crazy..  All of my speakers (7.1) worked fine in 8.10 (I managed to get them working fine in 9.04), but only the front work in 9.10.  Seems to be getting worse with each release.  LOL

---

### Post by michaelzap on 2009-11-01
> **jackmetal said:**
> Unfortunately it didn't work for me.  :-(
Didn't work for me either. I removed Pulseaudio and installed Alsa and after that I had no sound at all (and no devices listed). So I went back to the way it was before.

---

### Post by Zoot7 on 2009-11-01
> **zampes said:**
> No thank-you for Ghost|BTFH; the only thing this has gotten me is absolutely NO sound and no recognition of my sound card by the system.
Geez, don't go around telling people to do stuff that doesn't work at all.
Just reverse the changes made in synaptic and re-install what you removed in the line of pulseaudio packages, and everything should go back to as it once was. That's the beauty of using packages. ;)

---

### Post by damilaredavids on 2009-11-25
I have removed the pulseaudio and installed the alsa-oss as suggested but i still don not have sound from my external speakers. i can't even see the sound icon on the taskbar. System>Preferences>Sound does not bring any thing up...

What do i do pls...?

---

### Post by beniwtv on 2009-11-25
OK; I just can't resist jumping in this time :p

To all people that still get it wrong, PulseAudio is NOT an ALSA replacement. ALSA is also NOT a PulseAudio replacement. ALSA is NOT a sound server, PulseAudio IS a sound server.

In fact, they're completely different applications, on different layers that can't even be compared at all.

ALSA is the Advanced Linux Sound Architecture. This is a set of drivers and libraries that get your sound card working. Without ALSA, there would be no sound at all.

Many applications can speak to ALSA directly, outputting sound to your sound card. ALSA can even mix more than one application's output together, if your sound card has no mixer  (pretty common that onboard sound cards lack these).

ALSA can do some more things, but that practically is all what's to it. An API to input/output sound across many different devices and drivers.

However, in recent years, desktop operating systems like Windows or OS X have provided users with some advanced features, like network audio, audio volume control for each application, etc...

In Linux, we did have some applications that took care of providing "some" of these features, but they were either lacking in features or plain to difficult for a new user to configure.

So there comes PulseAudio. It's set out to provide many advanced features, whilst being easy to use for the user. Basically the idea was to "clean up" the Linux Audio sound server mess. 

Today, PulseAudio is a sound server operating ON TOP of ALSA with features like network audio, independent volume control for each application, grouping of sound cards, changing outputs of applications to a different sound card/output on the fly, and many more I probably forget here.

Now, every new technology has it's share of problems. PulseAudio was no different. In the first versions it was quite buggy and problematic, but these problems are largely solved in recent releases of PulseAudio & Ubuntu.

Nowadays, if you experience problems with PulseAudio, it's mostly because of buggy ALSA drivers, or your computer simply being too ancient to handle the load (and no, it's not much, I'm talking about _ancient_ computers with < 500 MHZ, not your 1.6 GHZ Pentium 4!).

Instead of whining here or elsewhere, which does not help at all, file bugs, help the developers of both ALSA and PulseAudio to solve these problems. Telling others to "drop it" because it's *** is not very constructive.

/Just my 2cents here...

PS: My PulseAudio in Ubuntu works just fine in Karmic. That being said, I never had any problems in Ubuntu with sound...

---

### Post by Ghost|BTFH on 2009-11-25
I do truly understand that, as I said in my original post - most feel Pulse is a fantastic little sound server.

To be fair, Pulse does a great job for most people, right up to the point where you decide to be silly and have more than one program grabbing for sound at the same time (usually 3 or more) at which point for my system at the very least, it hogs resources and generally tends to crash, leaving me with a lovely (and often loud) looping of sound similar to what I think an android would sound like having an epileptic seizure.

So, to those who feel it works perfectly, keep it and be happy.  For those who don't feel it works perfectly, what I suggested at the beginning worked fine for me - your mileage may vary! (I can't believe in this day and age I have to give that caveat...)

To those who tried this and suddenly have no sound at all, did you attempt to do this when you already had working sound that had no issues or did you have problems and wanted to fix them?

If it's the first one, shame on you - if it works, it's not broke, don't fix it!

If it's the second, my solution is not the ONLY solution, it's just what worked for me.  You try it, you win or you lose.  If you lose, you simply go back and put the same stuff in that you had before and you've hit square one again.

Now to those for whom this procedure has worked well - fantastic, glad I could help.

For those it has not helped at all - you have my sympathies. Not every solution works for every machine.

For those it ruined their lives, blew up their machine, or just generally made things worse - you have my sympathies.  Not every solution works for every machine.

For those who have jumped into the PulseAudio pulpit and spoken the holy words of faith in Pulse - Say what you want, my sound works, my system is stable and my resources aren't being hogged.

Finally, for those who say it's IMPOSSIBLE to do this - it's done.  It's on my computer, it works.  I don't care if it's not possible to be done, because I already went and did it. 

Cheers,
Ghost|BTFH

---

### Post by beniwtv on 2009-11-25
> **Ghost|BTFH said:**
> I do truly understand that, as I said in my original post - most feel Pulse is a fantastic little sound server.

Yes, I knew you know it - the post was not really directed to you, but more of a general calling out to people to help fix things so that PulseAudio and ALSA can work together even better.

> **Ghost|BTFH said:**
> 
To be fair, Pulse does a great job for most people, right up to the point where you decide to be silly and have more than one program grabbing for sound at the same time (usually 3 or more) at which point for my system at the very least, it hogs resources and generally tends to crash, leaving me with a lovely (and often loud) looping of sound similar to what I think an android would sound like having an epileptic seizure.

Incidentally, I never had this problem, but I hope you did report a bug so this can be looked at.

---

### Post by Ghost|BTFH on 2009-11-25
> **beniwtv said:**
> Incidentally, I never had this problem, but I hope you did report a bug so this can be looked at.

I'm sure you'll hate me for saying this, but I have little or no faith in the bug reports unless it is something seriously critical.

I've seen far too many bugs that people have even gone so far as to say "hey, I found the problem IN YOUR CODE, here's the solution" only to have it marked as Confirmed, Undecided for importance and Unassigned, even when the error makes the program UNUSABLE without the fix.

This tells me they either A) Have far far far bigger fish to fry and therefore don't have time for "trivial" stuff. or B) Really don't care unless it affects the majority.

Either way, I just opt to find my own solutions and toss it up on the forums when I've found something that works.

So in short, yes, I've CONFIRMED that I should write up a bug on PulseAudio, but I haven't decided the IMPORTANCE of the bug and I have yet to ASSIGN it to someone to report it.

I'll get around to it sometime in the 3rd quarter...of 2050.

Cheers,
Ghost|BTFH

---

