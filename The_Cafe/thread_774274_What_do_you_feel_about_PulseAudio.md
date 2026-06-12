---
title: "What do you feel about PulseAudio?"
date: 2008-04-29
forum: The Cafe
---

### Post by vishzilla on 2008-04-29
Well, I have been playing around PulseAudio to see how it works. I realized its impossible to play 2 audio streams at the same point. Under System>Prefs>Sound I selected ALSA for all the devices and I managed to play 2 audio streams.

Then I browsed through PulseAudio website for a guide and I came across a Perfect Setup guide. The guide mentioned to install all the GUIs required to configure PulseAudio. I installed them and checked all the options, there was a lot of stuff and I didn't want to mess my system up further.

After all this, I am wondering why the devs have included PulseAudio in a LTS release. Is there any advantage PulseAudio can give that ALSA cannot. On 7.10, ALSA didn't give any problems, so why is PulseAudio installed by default.

---

### Post by twright on 2008-04-29
it has lots of cool low level stuff

the comparison is like xine and gstreamer, xine was initially better supported but gstreamer is fundamentally better

pulseaudio should support it, i suggest you submit a bug report

run the command pavucotrol to see one of the cool things based on it

---

### Post by Ozor Mox on 2008-04-29
I am having some sound issues with Hardy, and I assume this is to do with this new PulseAudio. I'm unable to play different audio streams at once, for example if I'm playing a YouTube video I don't hear any sounds from any other apps. After the videos have finished and I close YouTube, sound still doesn't work until I reboot. Really annoying, have you reverted to ALSA somehow? I have never had these problems in any previous releases.

Edit: Submitted this post and I was looking at other posts in silence and suddenly my computer went "BAABUMTSCHCHHTSCHHBUMMBAAMMTSCCHH" (a mix of a constant beep and the Ubuntu login sound if you couldn't tell!) and almost killed me it scared me so much! Got to get this little problem sorted!

---

### Post by twright on 2008-04-29
you need to type these line into terminal (one by one) to fix flash
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

```

---

### Post by vishzilla on 2008-04-29
> **Ozor Mox said:**
> I am having some sound issues with Hardy, and I assume this is to do with this new PulseAudio. I'm unable to play different audio streams at once, for example if I'm playing a YouTube video I don't hear any sounds from any other apps. After the videos have finished and I close YouTube, sound still doesn't work until I reboot. Really annoying, have you reverted to ALSA somehow? I have never had these problems in any previous releases.

Under System>Prefs>Sound I have chosen ALSA instead of the default "Autodetect" to play all the sound events. With this I can play multiple streams

---

### Post by vishzilla on 2008-04-29
> **twright said:**
> you need to type these line into terminal (one by one) to fix flash
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz .tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

```

Thanks! I will try it

---

### Post by Ozor Mox on 2008-04-29
> **twright said:**
> you need to type these line into terminal (one by one) to fix flash
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

```

Thanks for that it worked great! This version of the Flash plugin should really be offered for download by Firefox and/or be in the repositories since it is needed for it to work properly.

---

### Post by twright on 2008-04-29
sorry, it is in the repos as [URL="apt://libflashsupport"]libflashsupport
[/URL] 
it should really be a dependency for flash

---

### Post by swoll1980 on 2008-04-29
I haven't had any problems with it so I don't mind it, but I was curious as to what it's purpose is as well.

---

### Post by Lostincyberspace on 2008-04-29
You can play multiple streams I had that problem with Alsa but pulse audio fixed that..

There are many other benefits to pulse audio since you can "merge" sound cards to act as one so you can be hooked up to a headphone jack and everyone else can listen through a speaker set so you can preview songs or other audio files. It is really great for Digital Dj's.

---

### Post by amar on 2008-04-29
I think it was, though they removed the dependancy part just before recease (again I THINK)

not too sure why - I think there were other problems and removing it was the lesser of 2 evils

---

### Post by swoll1980 on 2008-04-29
> **twright said:**
> sorry, it is in the repos as [URL="apt://libflashsupport"]libflashsupport
[/URL] 
it should really be a dependency for flash

if you install the pulse configuration app and check the box under simultaneous output it will fix the 2 apps playing at the same time problem. I uninstalled libflashsupport as a work around for the flash bug and installed the flashplayer from adobe and have not had a flash bug crash in over a week audio works fine

---

### Post by vishzilla on 2008-04-29
libflashsupport actually solved the problem. Why it isn't installed by default and why was it removed?

---

### Post by vishzilla on 2008-04-29
> **swoll1980 said:**
> if you install the pulse configuration app and check the box under simultaneous output it will fix the 2 apps playing at the same time problem. I uninstalled libflashsupport as a work around for the flash bug and installed the flashplayer from adobe and have not had a flash bug crash in over a week audio works fine

I have checked the option for Simultaneous Output, it didn't make any difference. :confused:

---

### Post by swoll1980 on 2008-04-29
that libflashsupport is what causes the flash crashes when I had it installed I had 50/50 chance of a flash video crashing firefox (at least 10 a day) since the uninstallation I have gone a week without 1 single crash. I feel bad that you can't get it to work with out libflashsupport, because without the flash crashes Ubuntu seems to be 100% better

---

### Post by swoll1980 on 2008-04-29
uninstall libflashsupport go to usr/lib/firefox/plugins delete the flash plugin
download the flash.tar.gz from adobe extract it open the folder and drag the plugin from it to your usr/lib/firefox/plugins folder log out then log back in see if it works

---

### Post by isaacj87 on 2008-04-29
> **swoll1980 said:**
> if you install the pulse configuration app and check the box under simultaneous output it will fix the 2 apps playing at the same time problem. I uninstalled libflashsupport as a work around for the flash bug and installed the flashplayer from adobe and have not had a flash bug crash in over a week audio works fine

I've done this as well, but it didn't work...was there something else you did as well?

---

### Post by Mr. Picklesworth on 2008-04-29
Personal bluetooth device tied to my user + computer attached to every speaker + PulseAudio + BlueProximity == Joy.
(If you haven't guessed, I wired up a few computers with big speakers so that I could have music follow wherever I was. It was completely pointless, but it worked!)

As for Flash, have you guys tried swfdec? It has weird problems here and there, but it happily plays most videos I have thrown at it, and does so considerably better than the non-free Flash player.

---

### Post by vishzilla on 2008-04-29
libflashsupport does crash a lot according to some of the posts here in the forum. Some bugs in Adobe's flash is causing PulseAudio to crash thats why they removed libflashsupport in some of the updates about a week back. Flash was always a crappy piece of software on Linux and I hope something is done about this. Flash audio works with ALSA when more than 1 stream is played. BTW, multiple streams can be played with PulseAudio that doesn't include Flash audio sounds, so that's a relief. In the end, I will give PulseAudio another chance.

---

### Post by swoll1980 on 2008-04-29
try a restart see if that helps the only other thing I can think of is that I upgraded rather than installed the new version of Ubuntu

---

### Post by foska on 2008-04-29
I am not feeling very good about it right now! In order to get my audio to play properly on my system, I had to install Pulseaudio. In Gutsy, I did not have to do all of this. And to top it off I still can't get Youtube to work! Aaargh!

---

### Post by novus721 on 2008-04-29
How do I feel about PulseAudio?

I HATE IT!

I have been working for two days trying to get sound back on my box, everything was fine in 7.10 but now all I get is a loud scratchy sound when my ubuntu loads. It should NOT have been made an integrated part of the OS yet, as I know I am not alone on this. If anyone has had any similar problems and fixed them please let me know, because I have tried countless things and we are still coming up short.

WHY DID YOU LEAVE US ALSA, WHY?!?!:sad::frown:

---

### Post by swoll1980 on 2008-04-29
can't you just uninstall it?

---

### Post by novus721 on 2008-04-29
> **swoll1980 said:**
> can't you just uninstall it?

No, because whenever you remove Pulse it automatically removes ubuntu-desk, which seems like it is somewhat necessary. I tried to get rid of it, but I can't reinstall ubuntu-desk without Pulse along with it.

Unless I completely missed something...am I wrong here?

---

### Post by foska on 2008-04-29
Well I just did (uninstalled pulseaudio and all references to including ubuntu-desktop) and guess what YouTube is working again.  I won't advise anyone to try that though. I think I am going to fiddle with it some more before I reinstall unbuntu-desktop. All audio programs are working again too even the little drum roll is back on startup!

Anyone have any ideas as to why this is happening?

BTW: All of this was done by Synaptic Package Manager!

---

### Post by novus721 on 2008-04-29
That's how I did it too, but it didn't get rid of the background noise for me so I left it as I found it

---

### Post by novus721 on 2008-04-30
MAYBE found a solution!

I was fooling around with my settings, and I went into Volume Control and went to the Switches tab and unchecked my output jack - youtube works!

Trying to continue the progress, god I hope they get a fix for this soon!

---

### Post by rajeev1204 on 2008-04-30
Pulse audio is not an audio library like alsa or oss.

Ubuntu hardy is still using alsa for playback.Pulse audio is kind of an audio sync which uses alsa to playback audio streams.


Its a minimalistic implementation in hardy so we dont have too many issues.


Its supposed to be a good way in bringing professional level audio functionality in linux ,using multiple audio cards etc.



I hope i got that right.



regards

rajeev

---

### Post by toupeiro on 2008-04-30
Verdict is out for me still.  I've had mix of good and not-so-good experiences depending on what I am doing and/or which apps or combination of apps I am using.  That within itself makes me wish it was not enabled as the default audio "driver" or "library" or whatever you want to call it, but I was able to correct all my problems thus far with padsp or aoss wrappers on some things, or specifically setting the audio driver to within the application for those applications which support that. (e.g. hydrogen, amarok, etc etc.)

I see this as more of a win, and a candidate for a default install on the Ubuntu Studio distro, which is a distro geared towards people more prone to take advantage of what PulseAudio has to offer, but in the LTS I am not so sure.

---

### Post by warbread on 2008-04-30
Has anyone had any experience using Jack with pulseaudio?  I'm curious what can be done with that.

---

### Post by Hells_Dark on 2008-04-30
All seems to work perfectly here.
Btw, it's new and it's the way to go..

---

### Post by twright on 2008-04-30
in five years probably every other distro will include pulseaudio so it was necessary to include it

if only ubuntu studio used it it would never get supported> **toupeiro said:**
> Verdict is out for me still.  I've had mix of good and not-so-good experiences depending on what I am doing and/or which apps or combination of apps I am using.  That within itself makes me wish it was not enabled as the default audio "driver" or "library" or whatever you want to call it, but I was able to correct all my problems thus far with padsp or aoss wrappers on some things, or specifically setting the audio driver to within the application for those applications which support that. (e.g. hydrogen, amarok, etc etc.)

I see this as more of a win, and a candidate for a default install on the Ubuntu Studio distro, which is a distro geared towards people more prone to take advantage of what PulseAudio has to offer, but in the LTS I am not so sure.

---

### Post by 01mf02 on 2008-04-30
I find it cool that Ubuntu tries to go new ways in the Sound department, but unfortunately I came to conclude that PulseAudio is not yet ripe enough to be included in the *default* installation - several programs (Flash, SOX' play etc.) stopped working, which led me to use ALSA and forget about PulseAudio for the moment.

Of course PulseAudio has its right to exist (e.g. network streaming), but as I don't use that anyhow (and I doubt many people here do), I fail to see how PulseAudio suits Ubuntu as a "mainstream" distribution.

---

### Post by herbster on 2008-04-30
I have ALSA working with stereo sound upmixed to 5 channels, full 5.1 works great, any number of apps can use sound simultaneously-- it does everything I can think that I need at the moment. I'm curious, haven't looked into it yet, is there any benefit for me to use Pulse Audio?

---

### Post by insane_alien on 2008-04-30
pulse audio is good once you get it going right. atm i wouldn't have put it as default.

but it is fun to play around with.

---

### Post by forrestcupp on 2008-04-30
Pulse Audio is worthless to me.  It causes more problems than it could possibly be worth.  I also switched everything to ALSA and ditched it.  I think it's crazy that they introduced it with an LTS.

---

### Post by GavinZac on 2008-04-30
> **novus721 said:**
> No, because whenever you remove Pulse it automatically removes ubuntu-desk, which seems like it is somewhat necessary. I tried to get rid of it, but I can't reinstall ubuntu-desk without Pulse along with it.

Unless I completely missed something...am I wrong here?

Its ok to remove ubuntu-desktop. It doesn't do anything, its a "meta-package", just the default collection of ubuntu packages. If you don't have pulse, then you don't have all of the default ubuntu packages. Installing ubuntu-desktop gives you all the standard ubuntu apps. Removing it does not remove all of them.

---

### Post by twright on 2008-04-30
pulseaudio provides really essential low level tools and it is probably the future of linux audio

it had to be in lts as if it wasn't in 5 years hardy would be obsolete (not good for lts)

it's just one bug in hardy's implementation, fedora has no such problems

---

### Post by toupeiro on 2008-04-30
> **twright said:**
> in five years probably every other distro will include pulseaudio so it was necessary to include it

if only ubuntu studio used it it would never get supported

As accurate as you may be on this point, keep in mind that 8.04 is to be an LTS (in some circles this also means more stable than other releases.)  A business, behind a firewall controlling their own package management will likely deploy an LTS rather than the 6-month cycle release.  Now, 5 years is a long time for something to develop.  I see nothing wrong with keeping pulse audio in the repos for an LTS,  and keeping them updated (this would afterall, still be "including" it), but to default to it for an LTS may be a mistake IMO... RHEL is Fedora's distant equivalent of an LTS (not necessarily from a means of licensing but a means of support), and no pulseaudio is not default for it. :) Its not an irreversable decision by any means, but I think its something that anyone involved with QA on a long term release should be considering.  Imagine them trying to default to whatever alpha state compiz was in with 6.06 LTS just because "probably every other distro would include it".  I think that mindset somewhat jeopardizes the credibility of a long term support version.  I would not be of this opinion whatsoever if this was done in 8.10

anyway, just my opinion :)  I still think 8.04 is a great success regardless of pulseaudio.

---

### Post by tbroderick on 2008-04-30
> **toupeiro said:**
> As accurate as you may be on this point, keep in mind that 8.04 is to be an LTS (in some circles this also means more stable than other releases.)  

But LTS doesn't mean more stable.

---

### Post by toupeiro on 2008-04-30
I disagree.  It means longer supported.  Generally the two go hand in hand in almost every other facet of software releases you look at.  If LTS is no more stable than the 6 month "latest" image, why even maintain an LTS.  If you look at ubuntu's main site as we speak you will see various nice little advertisement graphics, one in which the very first slogan says "Built for Stability!"  How are users supposed to interpret that if the community doesn't back that idea?

>  from tbroderick:

But LTS doesn't mean more stable.



---

### Post by twright on 2008-05-01
no business would deploy this soon after a release, they will deploy in a few months when (i hope) this bug will be fixed. i think if you do a fresh install now you will not experience the problem.

gutsy had some terrible problems as ATI did not support SLUB but now they have fixed it it means memory allocation is 2x as fast and my suspend is finally reliable. and compiz was initially poorly supported and broke stuff.

as long as it is patched promptly there is no problem and we get our cool new sound backend. the bug is tiny but it is in flash, one of the most used applications. It is both adobes fault and adobe's responsability (that doesn't stop us from working arround it).

hardy only has one major bug for me (which seems to be fixed now), that makes it the best release i have seen so far, i have been dreaming of having stable suspend and hibernate since fiesty> **toupeiro said:**
> As accurate as you may be on this point, keep in mind that 8.04 is to be an LTS (in some circles this also means more stable than other releases.)  A business, behind a firewall controlling their own package management will likely deploy an LTS rather than the 6-month cycle release.  Now, 5 years is a long time for something to develop.  I see nothing wrong with keeping pulse audio in the repos for an LTS,  and keeping them updated (this would afterall, still be "including" it), but to default to it for an LTS may be a mistake IMO... RHEL is Fedora's distant equivalent of an LTS (not necessarily from a means of licensing but a means of support), and no pulseaudio is not default for it. :) Its not an irreversable decision by any means, but I think its something that anyone involved with QA on a long term release should be considering.  Imagine them trying to default to whatever alpha state compiz was in with 6.06 LTS just because "probably every other distro would include it".  I think that mindset somewhat jeopardizes the credibility of a long term support version.  I would not be of this opinion whatsoever if this was done in 8.10

anyway, just my opinion :)  I still think 8.04 is a great success regardless of pulseaudio.

---

### Post by stoffe on 2008-05-01
Pulse in itself has been fantastic for me. It has worked at every turn, no problem. Two issues has come up: flash, which did work perfectly and stopped around Firefox beta 5 (first crash, then support removed), and that is completely in libflashsupport's ballpark, second audacity which is a universe app and had a 2-second workaround that was easy to find.

Right now I can't play Youtube effortlessly. That is totally worth what Pulse can bring.

And yes, people misinterpret Long Term Support for Works Perfectly Right Now. Understandable mistake, but no, all it says is: "we'll fix things for a longer time".

Have some faith, eh?

---

### Post by stoffe on 2008-05-01
> **twright said:**
> you need to type these line into terminal (one by one) to fix flash
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

```

Tried this. Just as the libflashsupport in the repos, it brings back the frequent crashes for any flash content. So that's no fix, or rather, for those lucky enough to not have crashes from libflashsupport, they might as well get it from the repos.

---

### Post by twright on 2008-05-01
i originally posted it in the wiki for gutsy users trying pulse, didn't know it had been packaged

i love pulseaudio also but i have had to disable it due to the issues (it doesn't survive a suspend well, and now i can actually get suspend to work this is a big issue for me)> **stoffe said:**
> Tried this. Just as the libflashsupport in the repos, it brings back the frequent crashes for any flash content. So that's no fix, or rather, for those lucky enough to not have crashes from libflashsupport, they might as well get it from the repos.

---

### Post by toni_uk on 2008-05-06
Lazy user here - have to say that I really can't do with Pulse as it stands. Actually, I have now decided that after days of trying to get Pulse working/switched off (failed with both) I am back on 7.10 where everything worked perfectly. 

For me the 4 big changes in 8.04 were Firefox 3 (having bugs though), new Nautilus (loved it), Open Office 2.4 (2.3 works as well for home use) and Pulse (not working on either laptop or desktop). Mint by the way has got a better way of switching off Pulse one tick and back to ALSA - don't like Desktop though.

Will be waiting for the next UBUNTU release and upgrade then. Guess Pulse will have been sorted in 6 months time. Also tried Mandriva One 2008 , SUSE 11beta and both have the same problem with Pulse. UBUNTU 8.10 - I am waiting for you!

---

### Post by Samhain13 on 2008-05-06
Just installed Hardy last night and now testing these new things.
Now using PulseAudio and fortunately, I am able to play multiple steams. For example: music from RhythmBox and a movie in VLC. One thing I noticed though is, when playing music, the volume decreases when a movie is opened. But the normal volume for the music comes back when the movie is closed.

---

### Post by Ozor Mox on 2008-05-06
> Actually, I have now decided that after days of trying to get Pulse working/switched off (failed with both) I am back on 7.10 where everything worked perfectly.

You can switch your audio back to the old ALSA in System > Preferences > Sound on 8.04, no need to revert to 7.10.

---

### Post by toni_uk on 2008-05-06
> **Ozor Mox said:**
> You can switch your audio back to the old ALSA in System > Preferences > Sound on 8.04, no need to revert to 7.10.

Yes, tried that - changed all to ALSA. Still did not work, seems there must be a seperate problem with my audio which did not exist pre 8.04. Could not find out what it was. Seems to be with all distros with Pulse but Mint - switched Pulse off and everything worked fine there. Rather use 7.10 than Mint though. Changing distro because of one thing is a bit drastic anyway.

---

