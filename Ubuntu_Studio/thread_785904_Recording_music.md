---
title: "Recording music"
date: 2008-05-07
forum: Ubuntu Studio
---

### Post by linux_newf on 2008-05-07
Hey guys, i've always played guitar but recently i've become very interested in using my PC to record some of my own songs.

I know very little about using a PC for this purpose and was wondering if i should even attempt to record my own stuff on ubuntu?

I'm very serious about this and plan to have my own mini studio sometime in the future.

I assume for this purpose it might be better to go with a more mainstream system.

This for instance is a actual studio type PC for Midi files and the like.
[http://www.zzounds.com/item--RAILIVEBOOKL6](http://www.zzounds.com/item--RAILIVEBOOKL6)

Any info related to this thread would be great.

---

### Post by Stochastic on 2008-05-07
UbuntuStudio is a fully capable studio operating system, infact it is more customizable for audio than either windows or osx.  The downside is that many mainstream apps and plugins have not been ported to linux; however, in most cases there is equivalent open-source software around (not always though).  If you want to create a mini studio, I'd personally recommend UbuntuStudio as then a larger portion of your budget can be dedicated to hardware improvements in the studio (acoustics, mics, soundcard, etc...).

To start, you should get Jack up and running (see qjackctl) then try a simple recording app such as Audacity or Rezound.  When you really want to record and edit, you'll want to get Ardour running, but it can be a bit heavy for a beginner.

---

### Post by linux_newf on 2008-05-07
> **Stochastic said:**
> UbuntuStudio is a fully capable studio operating system, infact it is more customizable for audio than either windows or osx.  The downside is that many mainstream apps and plugins have not been ported to linux; however, in most cases there is equivalent open-source software around (not always though).  If you want to create a mini studio, I'd personally recommend UbuntuStudio as then a larger portion of your budget can be dedicated to hardware improvements in the studio (acoustics, mics, soundcard, etc...).

To start, you should get Jack up and running (see qjackctl) then try a simple recording app such as Audacity or Rezound.  When you really want to record and edit, you'll want to get Ardour running, but it can be a bit heavy for a beginner.

Thanks, i assume the basic Ubuntu OS using audio record/playback software would also work fine? The 3 year support on 8.04 was a major reason i installed Ubuntu.

Something like getting these apps up and working:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

---

### Post by gs_berg on 2008-05-07
That is not right.  Ubuntu Studio has the proper kernel adequate for full audio production.  Sooner or later, depending what you do, you may find basic Ubuntu not appropriate.  It is better to free some space on your disk and make a separate Ubuntu Studio partition if you would like to keep standard Ubuntu.

---

### Post by Stochastic on 2008-05-07
> **gs_berg said:**
> That is not right.  Ubuntu Studio has the proper kernel adequate for full audio production.  Sooner or later, depending what you do, you may find basic Ubuntu not appropriate.  It is better to free some space on your disk and make a separate Ubuntu Studio partition if you would like to keep standard Ubuntu.

That's only partly correct.  In reality there's no reason to do a new partition, you can even upgrade your current Ubuntu install to an UbuntuStudio install by installing the metapackages (do "apt-cache search ubuntustudio" to see the metapackages).  Recording is possible with plain ubuntu, but you'll notice a lot more issues and errors.  You can even install both the realtime kernel that comes with UbuntuStudio and the normal kernel; grub will allow you to set a default and it'll give you a menu on startup for you to select which kernel to use.  Essentially you can put the UbuntuStudio packages on top of any regular Ubuntu install (and that would be one of the first steps to getting your recording studio going).  But Audacity should work in regular Ubuntu too.

---

### Post by linux_newf on 2008-05-07
> **Stochastic said:**
> That's only partly correct.  In reality there's no reason to do a new partition, you can even upgrade your current Ubuntu install to an UbuntuStudio install by installing the metapackages (do "apt-cache search ubuntustudio" to see the metapackages).  Recording is possible with plain ubuntu, but you'll notice a lot more issues and errors.  You can even install both the realtime kernel that comes with UbuntuStudio and the normal kernel; grub will allow you to set a default and it'll give you a menu on startup for you to select which kernel to use.  Essentially you can put the UbuntuStudio packages on top of any regular Ubuntu install (and that would be one of the first steps to getting your recording studio going).  But Audacity should work in regular Ubuntu too.

I just installed the UbuntuStudio packages on top of my current OS.

---

### Post by warbread on 2008-05-08
Don't overlook three very important steps:

```

:-$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'

```

If you're using the 64-bit version, you'll need to up that last number (for memlock), but these three steps allow you to use the real time kernel.  Log out and log back in after these are done and you can set jack up for real time processing.

[[SOURCE]]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

---

### Post by Stochastic on 2008-05-08
> **warbread said:**
> Don't overlook three very important steps:

```

:-$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'

```

Out of curiosity, what do the bottom two do?  I've got a fresh UbuntuStudio hardy install and only the first one is listed in /etc/security/limits.conf by default.

---

### Post by warbread on 2008-05-08
I believe the middle one removes any nice restrictions from a program in the audio group, allowing them to take control of the CPU more often.  The last one specifies how much system memory can be locked for use by programs in the audio group.  I don't think these are of critical importance, but on a system with limited resources, it could mean a lot in terms of xruns.

---

### Post by hurtstotalktoyou on 2008-05-08
I'm sorry to suddenly go against the flow, but I do not think Linux is capable of being a good home studio workstation at the present time.  It's not a problem with the OS itself, but rather an issue of having insufficient software support.  Quite frankly, neither Audacity nor Ardour are even close to satisfactory when it comes to semi-pro audio production.

Ideally, you'd want a Mac running Protools.  This of course is insanely expensive, and therefore not really a practical option.

A better solution is to get Adobe Audition for Windows.  The MSRP for the latest version (Adobe Audition 3.0) is $349.  That's pretty expensive, I know, but then, you don't really *need* the latest version.

I suggest getting Cool Edit Pro (the same software, but with a different name before Adobe bought it out and called it Audition) [from Ebay](http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&from=R40&satitle=cool+edit+pro&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=89701&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2).  You can probably nab it for less than $50.

Obviously it would be nice if you could run a Linux system for free, but this is not feasible for semipro audio uses.

---

### Post by Stochastic on 2008-05-08
> **hurtstotalktoyou said:**
> I'm sorry to suddenly go against the flow, but I do not think Linux is capable of being a good home studio workstation at the present time.  It's not a problem with the OS itself, but rather an issue of having insufficient software support.  Quite frankly, neither Audacity nor Ardour are even close to satisfactory when it comes to semi-pro audio production.

Ideally, you'd want a Mac running Protools.  This of course is insanely expensive, and therefore not really a practical option.

A better solution is to get Adobe Audition for Windows.  The MSRP for the latest version (Adobe Audition 3.0) is $349.  That's pretty expensive, I know, but then, you don't really *need* the latest version.

I suggest getting Cool Edit Pro (the same software, but with a different name before Adobe bought it out and called it Audition) [from Ebay](http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&from=R40&satitle=cool+edit+pro&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=89701&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2).  You can probably nab it for less than $50.

Obviously it would be nice if you could run a Linux system for free, but this is not feasible for semipro audio uses.

I personally think that's a steaming pile of bul****t.  I don't mean that as a personal attack, but merely a judgment of your opinion. Ardour slaughters Adobe Audition/Cool Edit.  Furthermore the number of other tools on the linux platform are so vast it would cost tens-to-hundreds of thousands to get a similar array of tools at an equal quality level on any closed-source platform.  I think Ardour rivals pro-tools, but doesn't yet beat it.  No, there aren't all-in-one apps on Linux, but all the different apps connect easily to one another, giving much more flexibility and resource control.  Do you know how much a closed source version of the LADSPA set would cost?  For anyone on a budget, Linux can do a wonderful job of professional audio.


Edit: Oh and Warbread, I'm pretty sure that last line about memlock is the old way of doing things (gutsy & earlier) as in hardy there's now a percentage setting in the UbuntuStudio controls (see the administration menu).  I'm not sure if the old way still works or not.

---

### Post by warbread on 2008-05-08
> **Stochastic said:**
> I personally think that's a steaming pile of bul****t.  I don't mean that as a personal attack, but merely a judgment of your opinion. Ardour slaughters Adobe Audition/Cool Edit.  Furthermore the number of other tools on the linux platform are so vast it would cost tens-to-hundreds of thousands to get a similar array of tools at an equal quality level on any closed-source platform.  I think Ardour rivals pro-tools, but doesn't yet beat it.  No, there aren't all-in-one apps on Linux, but all the different apps connect easily to one another, giving much more flexibility and resource control.  Do you know how much a closed source version of the LADSPA set would cost?  For anyone on a budget, Linux can do a wonderful job of professional audio.

Yup, pretty much.  

I've used Ardour for a few months now, and am consistently impressed with the fidelity of the recordings.  What comes out sounds like what went in.  Now, what went in doesn't sound so great because I'm using a POS mic and don't have an isolation cabinet built to record acceptable guitars, but the software channels all sound pristine.  

And that's just the hard disk recorder!  Zynaddsub, Sooperlooper and Alsa mod synth rival almost anything that Reason 4 and Fruity Loops can do (I'm checking up on other synth packages) and Hydrogen is still the best drum machine I've ever used, hands down.  The LADSPA plugins are sometimes not so good, but mostly they work like a charm.  VST support is getting better every day.  Paying for a similar setup would be extraordinarily expensive, and less flexible.  

That's not to say there aren't things that proprietary systems can do that the Linux suite of apps can't.  I'd like a good beat slicer, and [Freecycle's]("http://freecycle.redsteamrecords.com/") development is slow coming (though promising!).  A good sidechaining compressor would be nice, but if I ever really need to record drums, I'll get a rackmount with 16 inputs.  Fruity loops has a **really** nice *looking* eq, but jamin's works well enough for me.  If I had my druthers, I'd druther that Zynaddsub had a slicker interface and that LMMS didn't crash all the time.   But  I have many complaints about  what I'd rather commercial software be able to do, too.  Life is good with Linux Audio.  

:guitar:

> 
Edit: Oh and Warbread, I'm pretty sure that last line about memlock is the old way of doing things (gutsy & earlier) as in hardy there's now a percentage setting in the UbuntuStudio controls (see the administration menu).  I'm not sure if the old way still works or not.

Oye!  That's hot!  It lets you set a percentage instead of a set value.  Very nice.

---

### Post by Stochastic on 2008-05-09
> **warbread said:**
> A good sidechaining compressor would be nice
Check out the SC2 and SC3 compressors, they both have sidechain inputs.

And yeah, Linux looks a bit uglier, but it's flexibility blows the other guys out of the water.  Oh and as for the exact sound quality of Ardour, it is actually a little bit less than pro tools (yet also possibly better at the same time).  Here's what their website explains in technical details: > In conjunction with its support for a wide range of audio hardware, Ardour offers you sample rate neutral facilities (ie. any sample rate is supported to the extent of your hardware's capabilities). All sample data is maintained internally in 32 bit floating point format for maximum headroom and fidelity. Native file format is industry standard IEEE 32 bit floating point Broadcast WAVE or WAVE. Play or record any number of tracks with bit-perfect quality (what comes in is what goes out). 

Pro Tools has 48-bit internal floating point accuracy, but through a few different points internally it is dithered and truncated to 24-bits, therefore Pro Tools could be argued to truly have worse sound quality than Ardour (but at certain points better).

That being said, for someone who's wanting to start a mini recording studio in their house, Ardour is so good it could be seen as overkill.

---

### Post by ironflippy on 2008-05-09
The main issue i face with recording in linux is with the plugins. AFAIK, there aren't any good colored compressors, EQs, etc. I find that there are two different types of effects, ones that you can have a ton of control over but sound rather bland, and ones that impart a nice coloration on the sound, but are more of a one trick pony. LADSPA has plenty of the former, but lacks the latter. In a truely professional setup, the "colored" effects would be in outboard gear, but that isn't possible for most of us. There are some really good VST freebies out there that just sound fantastic. I know VST support is being worked on, but I'd really like to see some LADSPA plugs that do something similar.

I feel the most impressive part about linux audio is how everything is routed through jack. I'm still amazed how quickly I can set up my MIDI controller with a synth (zynaddsubfx is amazing!) and then plug it into whichever program I want. It's the most intuitive way to approach audio production, especially for audio guys who are already familiar with patch bays but get confused with configuring software and drivers (*coughcough* like me).

I really wish Ubuntu Studio came with better out of the box support for PureData, but hopefully that will come some day.

---

### Post by SynthesizersFTW on 2008-05-09
ironflippy,

I might have a fix for your coloration quandary: convolution plugins that can do reverb with room impulses can also use impulse responses of other things too...like outboard gear.  A little Googling can get you a lot of different impulse responses from much-sought-after vintage gear.  I have a suspicion that many commercial plugins like Antares mic modeler and the Line6 amp sims are doing just that...

If you've never heard of convolution reverb, for a good idea about what I'm talking about, check out Audio Ease Altiverb to see the power of this stuff (they explain the method as it applies to reverb on their website). 

While the processing overhead for realtime convolution can be steep, you can always do things track-at-a-time and bounce down.  And there's always the option of applying effects outside of Ardour in not-so-real-time.  There are a number of good convolution engines out there, there should be something out there that can use whatever impulse file you want - it'd be worth looking into if you're looking for more one-trick ponies.  I think there is a convolution Pd external out there, never tried it.  As far as Pd goes, I'm still scratching my head over that.  Someone who knows what they're doing needs to update the documentation, as it stands now, you have to cobble answers together from all over.  That fact, and general GUI unfriendliness is a huge barrier to entry vs. Max/MSP for new users.

And not to get too far off-topic, I concur about the ProTools comment.  Why waste the money on ProTools software AND get locked into their hardware, when you can get a RME or (even cheaper but still good quality) Delta1010 card?  Spend the money on a good interface and you're most of the way there.  Do the math and there's no contest.  Ardour is a great DAW and more than powerful enough for home studio recordings.

Peace

---

### Post by hurtstotalktoyou on 2008-05-09
> **Stochastic said:**
> I personally think that's a steaming pile of bul****t.  I don't mean that as a personal attack, but merely a judgment of your opinion.

No offense taken.

> Ardour slaughters Adobe Audition/Cool Edit.

How so?

For me, the biggest problem with Linux tools is lack of audio effects.  The last time I checked, Ardour did not seem to include any effects processing options at all.  Most importantly, Audition offers fantastic dynamic compression, as well as something they call "hard limiting," which essentially allows one to flatten a waveform without clipping.  These two functions are absolutely essential to music production, yet as far as I can tell are absent from Ardour--and for that matter any other Linux application.

The icing on the cake is Audition's user-friendliness.  One needn't worry about things like creating tracks (cf. Ardour), and saving individual tracks is no problem whatsoever (cf. Audacity).  The edit/multitrack toggle is unparalleled on Linux.

Anyway, that's what I like about Audition, and dislike about Ardour/Audacity.  Would you mind sharing your own reasoning?

> Furthermore the number of other tools on the linux platform are so vast it would cost tens-to-hundreds of thousands to get a similar array of tools at an equal quality level on any closed-source platform.

There are a lot of open-source and otherwise free software options for Windows, you know.  Can you give an example of Linux audio production freeware which has no comparable free or low-cost alternative on the Windows platform?

> I think Ardour rivals pro-tools, but doesn't yet beat it.  No, there aren't all-in-one apps on Linux, but all the different apps connect easily to one another, giving much more flexibility and resource control.

I'm curious what you mean by this.  Personally, I think it's a pain in the *** to juggle between Jack, ALSA and PulseAudio.  And although I've never really had occasion to try it, I can't imagine why I would want to multitrack in one app and process effects in another, as opposed to doing both in the same environment.

> Do you know how much a closed source version of the LADSPA set would cost?

No--but I do know that the Windows platform is doing just fine without it.

> For anyone on a budget, Linux can do a wonderful job of professional audio.

So you say.  However, I have yet to discover the tools I need to match what I do in Windows.

---

### Post by hurtstotalktoyou on 2008-05-09
> **Stochastic said:**
> Check out the SC2 and SC3 compressors, they both have sidechain inputs.

Last time I tried using them, neither SC2 nor SC3 (nor SC4, for that matter) had lookahead processing, which made them useless to me, sidechaining or not.

> And yeah, Linux looks a bit uglier, but it's flexibility blows the other guys out of the water.

What do you mean, "flexibility"?

> Oh and as for the exact sound quality of Ardour, it is actually a little bit less than pro tools (yet also possibly better at the same time).  Here's what their website explains in technical details: 

Pro Tools has 48-bit internal floating point accuracy, but through a few different points internally it is dithered and truncated to 24-bits, therefore Pro Tools could be argued to truly have worse sound quality than Ardour (but at certain points better).

That being said, for someone who's wanting to start a mini recording studio in their house, Ardour is so good it could be seen as overkill.

The sound quality in Ardour seems fine, but I can't hear any difference between it and something recorded through Audition.  This seems to be expected, given that the sound card, and not the software, is responsible for A>D conversion.

---

### Post by ironflippy on 2008-05-09
> **SynthesizersFTW said:**
> ironflippy,

I might have a fix for your coloration quandary: convolution plugins that can do reverb with room impulses can also use impulse responses of other things too...like outboard gear.  A little Googling can get you a lot of different impulse responses from much-sought-after vintage gear.  I have a suspicion that many commercial plugins like Antares mic modeler and the Line6 amp sims are doing just that...

If you've never heard of convolution reverb, for a good idea about what I'm talking about, check out Audio Ease Altiverb to see the power of this stuff (they explain the method as it applies to reverb on their website). 

While the processing overhead for realtime convolution can be steep, you can always do things track-at-a-time and bounce down.  And there's always the option of applying effects outside of Ardour in not-so-real-time.  There are a number of good convolution engines out there, there should be something out there that can use whatever impulse file you want - it'd be worth looking into if you're looking for more one-trick ponies.  I think there is a convolution Pd external out there, never tried it.  As far as Pd goes, I'm still scratching my head over that.  Someone who knows what they're doing needs to update the documentation, as it stands now, you have to cobble answers together from all over.  That fact, and general GUI unfriendliness is a huge barrier to entry vs. Max/MSP for new users.

And not to get too far off-topic, I concur about the ProTools comment.  Why waste the money on ProTools software AND get locked into their hardware, when you can get a RME or (even cheaper but still good quality) Delta1010 card?  Spend the money on a good interface and you're most of the way there.  Do the math and there's no contest.  Ardour is a great DAW and more than powerful enough for home studio recordings.

Peace

Yea, I've thought about using IRs of gear, but it's more of a workaround than I'd like it to be. Plus, convolution is static, whereas changing the settings on say, a dbx165, changes the type of coloration it imparts on the signal. Maybe I'm asking for too much from so few people. If my coding were any good I'd write them myself, or if I had enough free time.

And I totally agree about the Pd thing. I used Max first and found that the documentation they provide is both complete and easy to understand. But for a newcomer to audio "coding", it can be an incredibly intimidating experience to use Pd.

---

### Post by robeast on 2008-05-09
A little off topic now, but I think it's important to mention this:

> **warbread said:**
> I believe the middle one removes any nice restrictions from a program in the audio group, allowing them to take control of the CPU more often.  The last one specifies how much system memory can be locked for use by programs in the audio group.  I don't think these are of critical importance, but on a system with limited resources, it could mean a lot in terms of xruns.

I *need* to set my memlock to unlimited in /etc/security/limits.conf or else I get program crashes or whole OS freezes. Even setting it to use all of my RAM is not good enough, it needs to be "unlimited". I have Hardy running on an Athlon64 3000+ and 1.5gb RAM, so not the fastest system but ample.

Oh yeah, and for all of you out there baggin' on the LADSPA plugins, use the money you save with Linux and buy quality outboard gear. That's where it's at anyway.

---

### Post by robeast on 2008-05-09
> **Stochastic said:**
> Edit: Oh and Warbread, I'm pretty sure that last line about memlock is the old way of doing things (gutsy & earlier) as in hardy there's now a percentage setting in the UbuntuStudio controls (see the administration menu).  I'm not sure if the old way still works or not.

The Ubuntu Studio controls crash every now and then for me, and I needed to edit the /etc/security/limits.conf by hand with unlimited because locking 100% in Ubuntu Studio controls didn't do the trick!

---

### Post by ironflippy on 2008-05-09
> **hurtstotalktoyou said:**
> For me, the biggest problem with Linux tools is lack of audio effects.  The last time I checked, Ardour did not seem to include any effects processing options at all.  Most importantly, Audition offers fantastic dynamic compression, as well as something they call "hard limiting," which essentially allows one to flatten a waveform without clipping.  These two functions are absolutely essential to music production, yet as far as I can tell are absent from Ardour--and for that matter any other Linux application.

The icing on the cake is Audition's user-friendliness.  One needn't worry about things like creating tracks (cf. Ardour), and saving individual tracks is no problem whatsoever (cf. Audacity).  The edit/multitrack toggle is unparalleled on Linux.

Anyway, that's what I like about Audition, and dislike about Ardour/Audacity.  Would you mind sharing your own reasoning?
Maybe I'm not understanding your concern, but there are LADSPA plugins that do just what you're looking for. They can be pulled up in Ardour no problem.

---

### Post by hurtstotalktoyou on 2008-05-09
> **ironflippy said:**
> Maybe I'm not understanding your concern, but there are LADSPA plugins that do just what you're looking for. They can be pulled up in Ardour no problem.

If that's the case, I'd very much like to try it.  My first concern is finding a compressor with lookahead.  To my knowledge, none such exists for Linux.  Do you know how I might import one into Ardour?

---

### Post by ironflippy on 2008-05-09
> **hurtstotalktoyou said:**
> If that's the case, I'd very much like to try it.  My first concern is finding a compressor with lookahead.  To my knowledge, none such exists for Linux.  Do you know how I might import one into Ardour?

I know that there's a look ahead limiter, but I've never used it so I don't know if it will do what you'd like it to. A work around that may work for you would be to copy the track you'd like to compress and push it backwards in time by a few ms, insert a side chain compressor on the original and set the side chain input to the copied track. It's not exactly the same effect, but it might work for what you need it for. However, if you're more comfortable in Audition, then there's no reason to switch!

---

### Post by hurtstotalktoyou on 2008-05-09
> **ironflippy said:**
> I know that there's a look ahead limiter, but I've never used it so I don't know if it will do what you'd like it to.

I don't think there is.  If you know of one, I'd very much like to get my hands on it.  Even though I use Audition on my main system, I have Ubuntu running on my bedroom PC, and so I am quite interested in getting Ardour to work better than it currently does.

> A work around that may work for you would be to copy the track you'd like to compress and push it backwards in time by a few ms, insert a side chain compressor on the original and set the side chain input to the copied track. It's not exactly the same effect, but it might work for what you need it for. However, if you're more comfortable in Audition, then there's no reason to switch!

I think Audition would be more comfortable than that workaround for *anyone*, which is just another example of the reasons I mentioned for Audition's apparent superiority.

---

### Post by nalmeth on 2008-05-09
> For me, the biggest problem with Linux tools is lack of audio effects. The last time I checked, Ardour did not seem to include any effects processing options at all.
Install the LADSPA set, or you can compile Ardour to use VST

> The icing on the cake is Audition's user-friendliness. One needn't worry about things like creating tracks (cf. Ardour), and saving individual tracks is no problem whatsoever (cf. Audacity). The edit/multitrack toggle is unparalleled on Linux.
Different workflow.. So what?

> I'm curious what you mean by this. Personally, I think it's a pain in the *** to juggle between Jack, ALSA and PulseAudio. And although I've never really had occasion to try it, I can't imagine why I would want to multitrack in one app and process effects in another, as opposed to doing both in the same environment.
Its the mentality of Free Software development. It usually isn't monolithic like in closed-source development. 
Let us have a level platform to connect on, and let each application do what it does best, and let it share its data with every other application on the platform. 
If Ardour does editing best, and Hydrogen does drum tracks the best, I can't imagine why I would want to make drum tracks in Ardour!
The fact that you aren't used to a dynamic audio server doesn't make it worse.

> Do you know how much a closed source version of the LADSPA set would cost?
No--but I do know that the Windows platform is doing just fine without it.
Thats because everyone is paying for VST's (or pirating them). No one said everyone *needs* LADSPA plugins. 

> I think Audition would be more comfortable than that workaround for *anyone*, which is just another example of the reasons I mentioned for Audition's apparent superiority. 	
The superiority is only apparent to you here, my friend. And the fellow was simply explaining how it could be done without a plugin. 

No one has told you to use Ardour instead of your preferred software. Use whatever you're comfortable with, and people here will try help you with any problems you run into should you want a studio setup in Ubuntu.

I don't have a solution for your look-ahead limiter (haven't needed it), and I haven't used Audition so I can't make feature-by-feature comparisons with you, but I think a lot of your points are along the lines of "it doesn't work the same way as it does in Audition". Why the hell should it? :)

---

### Post by SynthesizersFTW on 2008-05-10
hurts,

> **hurtstotalktoyou said:**
> 

For me, the biggest problem with Linux tools is lack of audio effects.  The last time I checked, Ardour did not seem to include any effects processing options at all.  Most importantly, Audition offers fantastic dynamic compression, as well as something they call "hard limiting," which essentially allows one to flatten a waveform without clipping.  These two functions are absolutely essential to music production, yet as far as I can tell are absent from Ardour--and for that matter any other Linux application. 

On the first point, you can cover most all of the bases with the popular LADSPA plugin packages, Steve Harris's set is nice.  Tick a box in Synaptic (search 'ladspa'), and in no time you have just about everything you would ever need in Ardour (a LADSPA host app).  Free!  Once they are installed, right click in the black spot above the fader in mixer view, and you can scroll through or search for what you need in seconds.

Sure, commercial plugins have nice little GUIs, but who cares?  It's about the sound!!! You can even save settings of LADSPA plugins as presets.  The effects parameters can even be automated in the timeline.  What more do you need?  It sounds like you have only scratched the surface of what Ardour can do for you before passing judgment.

I can barely code in C, and even I can crank out decent LADSPA effects.  I get a lot more satisfaction learning how to do something than throwing money at a problem.  It's the linux DIY mentality that you are not getting—if something is absent, it gets discussed within the community and you go get your hands dirty.  If you can't/don't want to code, you can always volunteer to test things out, it's always appreciated.

On the second point, why would you ever need lookahead limiting to record a track?  If you clip the signal, turn the input gain down.  It's called *dynamic range* - recordings before the early 90's had it.  What's the point of having 16+ bit audio if you only use the topmost few bits?  Take a look at this educational site:

[http://turnmeup.org/](http://turnmeup.org/)

<RANT>
The loudness war has gone far enough.  Nobody really *needs* a brickwall in the signal chain.  Mix properly and things can sound great.  Squash everything into oblivion and your music will cause massive ear fatigue.  That's why people still sit around reminiscing about how "listenable" Pink Floyd mixes sound.
</END RANT>

Take a second look at Ardour and I know you'll see the light!  Any questions, ask away...that's what these forums are for.

---

### Post by SynthesizersFTW on 2008-05-10
@nalmeth:

You took the words right out of my mouth.  I should have read the whole thread before replying, but I couldn't resist hitting the button.

Echoing what you said about workflows, I couldn't agree more.  It's why people get married to any environment (free or non-free), they are used to "how ProTools/Cubase/Sonar/Logic/etc. does it" or whatever.  It's only after you objectively try another way of doing things that you can discover the merits of a different approach.  As Yoda said, "you must unlearn what you have learned."

Yoda: "A very powerful and flexible DAW Ardour is."
hurtstotalktoyou: "I can't believe it."
Yoda: "And that is why you fail."

hurts, you will soon be an Ubuntu Jedi.  Continue the training!!!

---

### Post by robeast on 2008-05-11
> **SynthesizersFTW said:**
> It's called *dynamic range* - recordings before the early 90's had it.

I was wondering where that went!

> Echoing what you said about workflows...It's why people get married to any environment (free or non-free), they are used to "how ProTools/Cubase/Sonar/Logic/etc. does it" or whatever.

Supposedly most people become beginner users of a program very quickly (if it is intuitive to use). Some continue to learn new things here and there until they are intermediates. Very, VERY few have the desire or need to become advanced users.

I think people who are adept with Linux often come down hard on new users because using most applications require general computer knowledge in many potential areas: command line, troubleshooting--an often overlooked skill, locations of conf files, hardware knowledge, installing packages, compiling from source, etc. This is exacerbated when using complex software suites such as our beloved audio apps. 

So becoming a beginner in using Linux alone takes some significant effort--not necessarily, but often. When  one gets past some of that and tries to use a program like Ardour, which is incredibly dense, and can't figure out how to get some dsp going...I can see how one might revert back to something familiar.

And you know what? If you already paid for a solid audio program, it makes sense to use it and get your money's worth. But since you have an interest in Linux already you should simply use both. There are plenty of ways that they will both be useful to you. So record your tracks in Audition and use your look-ahead compressor, send the tracks over to Ardour and use your new favorite LADSPA plugin and put it over some Hydrogen beats! 

Part of finding software useful is finding your own niche within its features.

---

### Post by nalmeth on 2008-05-12
> 
Echoing what you said about workflows, I couldn't agree more. It's why people get married to any environment (free or non-free), they are used to "how ProTools/Cubase/Sonar/Logic/etc. does it" or whatever. It's only after you objectively try another way of doing things that you can discover the merits of a different approach. As Yoda said, "you must unlearn what you have learned."
Definitely, theres always a sense of frustration when doing something you're normally used to, but with a different tool. 
GIMP vs Photoshop comes to mind as a similar example. 

There is no 'right' or 'wrong' way, as long as you find 'your' way.

I'm no different, I feel like I'm married to JACK & Ardour, and it would take a significant amount of adjustment to use another DAW for the same tasks. 

> ... command line, troubleshooting--an often overlooked skill, locations of conf files, hardware knowledge, installing packages, compiling from source, etc. This is exacerbated when using complex software suites such as our beloved audio apps.
Yeah, learning a new DAW is probably hard enough, having to learn a new OS makes the adjustment all the more difficult. 
It all comes with time and persistence though! 

"You shouldn't take it so hard!" K. Richards

---

### Post by thorgal on 2008-05-12
... mmmm ... thre IS a fast lookahead limiter in the ladspa suite, made by Steve Harris. If you go type 'limiter' in the search field of ardour's plugin manager, it shows up right away. As for compression, try the lapsa comp SC4 (there's a mono and stereo version).

And if ot's not enough, use Jamin, the mastering tool, for all sorts of dynamic effect proc.

---

