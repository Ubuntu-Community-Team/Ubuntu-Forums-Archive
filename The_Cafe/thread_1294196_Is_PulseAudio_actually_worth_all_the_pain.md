---
title: "Is PulseAudio actually worth all the pain?"
date: 2009-10-18
forum: The Cafe
---

### Post by edin9 on 2009-10-18
The old scars still aren't healed I see. I installed 9.10 BETA yesterday (after a self imposed exile to Kubuntu), and tried ET:QW on it. Surprise surprise I get distorted, crackling audio. I remove PulseAudio, and the problem goes away. The same thing happens in VLC. With Pulse I get broken, crackling audio, without no issue. PulseAudio is the sole reason I exiled to Kubuntu. An OS that has OOtB trouble free audio. I know Pulse has a point, but I don't know if it's worth the trouble in the long run.

---

### Post by anonymous_user on 2009-10-18
What wrong with just removing pulse audio? You don't need to switch distros.

---

### Post by cariboo on 2009-10-18
The only problem I've had with pulse was during the alpha versions of Januty and Karmic, and they were more a problem with alsa than anything else. THe alsa devs seem to want to make it hard for the pulse devs to keep up.

---

### Post by edin9 on 2009-10-18
> **cariboo907 said:**
> The only problem I've had with pulse was during the alpha versions of Januty and Karmic, and they were more a problem with alsa than anything else. THe alsa devs seem to want to make it hard for the pulse devs to keep up.

 How so?

---

### Post by Exodist on 2009-10-18
I been using GNU/Linux since 1998. Why the hell do we even need Pulse? Do we really need to keep throwing junk into the distro thats Beta at best.
ALSA is fine, works great. Why the change?

---

### Post by JillSwift on 2009-10-18
Pulse brings some nifty toys to the table.

If you like pulse generally, but have apps and games that get upset about it, there is a nice little command that you will find useful: **pasuspender**.

```
pasuspender ~/etqw-full/etqw-rthread
```
Pulse is brought back to life when you quit the game/application.

---

### Post by starcannon on 2009-10-18
The problem as I see it with Pulse and Ubuntu is that Pulse is being used as a kludge to attempt the impossible; the attempt to fit all the different sound servers together. It needs more time in the oven, indeed the whole "sound server" issue needs sorted in Linux. Fine, fine, let there be half a dozen sound server projects going in as many directions, but should not the major distributions decide on one, and pool their collective resources into just one? Or make it 2 if the advantages of competition are to be sought after, let KDE try their luck with one, and let Gnome try their luck with one; but trying to fit them all under one roof, good grief, "herding cats" becomes an understatement.

---

### Post by coldReactive on 2009-10-18
Granted that in Karmic and future releases of Ubuntu, pulse will be more integrated, and harder to remove in the future.

Someone told me this in esound installation threads.

---

### Post by bobbocanfly on 2009-10-18
Pulseaudio is fiddly but it's great when it works. I had a "home theater" (read computer next to my bed) that didn't have any speakers attached, so I just used Pulse to send the audio to my main computer's speakers a few metres away. Works perfectly. Granted, most people probably don't need it, but when it works, it's definitely worth the pain.

---

### Post by samjh on 2009-10-18
I haven't had any problems with PulseAudio since Ubuntu 8.10.

In the long run, I think it is "worth all the pain".  The problem is that of support by application developers.  When you have a brand new backend system for anything, adoption is slow, and therefore it takes a long time to mature.  Support for PulseAudio has only really been spreading this year.  Within another year or two, I think PulseAudio will not be painful at all for most users.

---

### Post by kevdog on 2009-10-18
The last time I checked pulse audio breaks the pidgeon voice and video capabilities.  Why does this matter?? I believe pidgeon is included by default in the installation.

---

### Post by 23meg on 2009-10-18
> **Exodist said:**
> I been using GNU/Linux since 1998. Why the hell do we even need Pulse? Do we really need to keep throwing junk into the distro thats Beta at best.
ALSA is fine, works great. Why the change?

Read [this]("http://0pointer.de/blog/projects/jeffrey-stedfast.html").

---

### Post by coldReactive on 2009-10-18
> **23meg said:**
> Read [this]("http://0pointer.de/blog/projects/jeffrey-stedfast.html").

I LOVE how rude this line is:
> Fixed 3 months ago. It is certainly not my fault that this isn't available in Jeffrey's distro.

This used to happen to me a lot with linux.

---

### Post by Ric_NYC on 2009-10-18
If the people responsible for the distro put two things together, and those things don't work well together, that's not the user's fault.
That's my opinion.

BTW, **this is 2009**. It is time to have the sound working properly in the operating system.

---

### Post by 23meg on 2009-10-18
> **coldReactive said:**
> I LOVE how rude this line is:


This used to happen to me a lot with linux.

While it certainly is true that it's not an upstream developer's fault if a particular bug she fixed isn't fixed in a specific distribution, I would skip the personal parts; I meant to point to the "Why PulseAudio?" part, but there's no way to link to that specific heading.

---

### Post by 23meg on 2009-10-18
> **Ric_NYC said:**
> 
BTW, **this is 2009**. It is time to have the sound working properly in the operating system.

[Works for me]("http://ubuntuforums.org/showthread.php?t=1293324").

---

### Post by Ric_NYC on 2009-10-18
> **23meg said:**
> [Works for me]("http://ubuntuforums.org/showthread.php?t=1293324").


Some people chew tobacco... That works for them.
I'm talking about something that really works for all.

---

### Post by Slug71 on 2009-10-18
PulseAudio in Karmic is better than PA has ever been in Ubuntu since 8.04 IMO. Sure it still needs some work/tweaking but its come a long way. My guess is that for 10.04 it will be working near perfect.

---

### Post by Regenweald on 2009-10-18
> **coldReactive said:**
> I LOVE how rude this line is:



I don't see how it is rude though ;) upstream fixed, distro packagers did not package. How is it upstream's fault? I think the statement is more factual than anything else.

We can't expect an upstream developer to fix then chase down the 1000+ distros to make sure they include new features/fixes....

On another note, i think it has just become cool to bash without really knowing anything about audio programming in general. If pulse was so horrible distro's would have opted not to use it, and it is exactly the opposite: [http://www.cio.com.au/article/320807/open_source_identity_pulseaudio_creator_lennart_poettering](http://www.cio.com.au/article/320807/open_source_identity_pulseaudio_creator_lennart_poettering)

---

### Post by dragos240 on 2009-10-18
I never even installed it on my archbox. Maybe it'll be better in a few years.

---

### Post by 23meg on 2009-10-18
> **Ric_NYC said:**
> Some people chew tobacco... That works for them.
I'm talking about something that really works for all.

Sound wasn't "something that worked for all" before PulseAudio either. And there's a lot of software that's part of Ubuntu that doesn't "work for all", due to the diversity of combinations of hardware, and shortage of support and testing. Not every part of every other operating system "works for all" either, despite much better vendor support.

[There's no flawless victory]("http://mdzlog.alcor.net/2008/10/29/ubuntu-quality/"), and "works for all" is not a realistic goal.

---

### Post by coldReactive on 2009-10-18
> **23meg said:**
> Sound wasn't "something that worked for all" before PulseAudio either. And there's a lot of software that's part of Ubuntu that doesn't "work for all", due to the diversity of combinations of hardware, and shortage of support and testing. Not every part of every other operating system "works for all" either, despite much better vendor support.

[There's no flawless victory]("http://mdzlog.alcor.net/2008/10/29/ubuntu-quality/"), and "works for all" is not a realistic goal.

Heck, even windows doesn't "work for all."

---

### Post by Ric_NYC on 2009-10-18
"Works for all" was an exaggeration.
Anyway. I think PulseAudio is a defective product. Many people complaining about it in the forum.

---

### Post by coldReactive on 2009-10-18
> **Ric_NYC said:**
> "Works for all" was an exaggeration.
Anyway. I think PulseAudio is a defective product. Many people complaining about it in the forum.

*sighs*

Works for me. Even though I really DON'T want to say that, it does, it works for me, even with flash. Right out of the box.

---

### Post by 23meg on 2009-10-18
> **Ric_NYC said:**
> "Works for all" was an exaggeration.
Anyway. I think PulseAudio is a defective product. Many people complaining about it in the forum.

Welcome to the Internet.

---

### Post by Ric_NYC on 2009-10-18
> **coldReactive said:**
> *sighs*

Works for me. Even though I really DON'T want to say that, it does, it works for me, even with flash. Right out of the box.

Congratulations. The sound works for you in 2009 in a modern operation system.

---

### Post by Lightstar on 2009-10-18
I still have to switch to windows for some voice chat.

When linux has a solid and compatible sound system, then I will remove windows.

---

### Post by Mr. Picklesworth on 2009-10-18
> **Exodist said:**
> I been using GNU/Linux since 1998. Why the hell do we even need Pulse? Do we really need to keep throwing junk into the distro thats Beta at best.
ALSA is fine, works great. Why the change?

Bluetooth audio, USB audio devices, transparently moving audio streams between devices, streaming over a network (with AirTunes support, to boot), better integration (note that Rhythmbox's volume control directly changes its PulseAudio stream now, so you don't have three volume controls to worry about in two different places), automatic detection and configuration of audio devices based on what kind of device they are, automatically treating certain audio streams differently based on what type of stream they are. (For example, Pulse can lower the volume of everything else when you are talking on the phone). 150% volume.

Your crackly audio issues are more likely produced by bad drivers which don't support all the features PulseAudio needs. This tends to be the culprit, as it was with some Intel HDA devices in Jaunty.

Don't just blame the sound server outright for your problems, as it *does* work. (If it didn't, would it be in use on Palm's WebOS?).
What you are seeing is a compatibility issue, which could be occurring anywhere in your audio stack.

---

### Post by darthmob on 2009-10-18
> **JillSwift said:**
> Pulse brings some nifty toys to the table.

If you like pulse generally, but have apps and games that get upset about it, there is a nice little command that you will find useful: **pasuspender**.

```
pasuspender ~/etqw-full/etqw-rthread
```
Pulse is brought back to life when you quit the game/application.Nice, I didn't know that one. :)

---

### Post by -grubby on 2009-10-18
PulseAudio has never, ever worked correctly for me. Sometimes, it wouldn't play sounds at all, other times it would crackle and pop, and still other times the audio server would randomly crash.

Removing it, however, fixes everything.

I realize that PulseAudio may work for you, but still, it was a disappointment to me, and I'm still a little steamed about that.

---

### Post by FuturePilot on 2009-10-18
> **Mr. Picklesworth said:**
> Bluetooth audio, USB audio devices, transparently moving audio streams between devices, streaming over a network (with AirTunes support, to boot), better integration (note that Rhythmbox's volume control directly changes its PulseAudio stream now, so you don't have three volume controls to worry about in two different places), automatic detection and configuration of audio devices based on what kind of device they are, automatically treating certain audio streams differently based on what type of stream they are. (For example, Pulse can lower the volume of everything else when you are talking on the phone). 150% volume.

Your crackly audio issues are more likely produced by bad drivers which don't support all the features PulseAudio needs. This tends to be the culprit, as it was with some Intel HDA devices in Jaunty.

Don't just blame the sound server outright for your problems, as it *does* work. (If it didn't, would it be in use on Palm's WebOS?).
What you are seeing is a compatibility issue, which could be occurring anywhere in your audio stack.

This

---

### Post by GMU_DodgyHodgy on 2009-10-18
I have never had a problem with Pulse Audio since it came out.  I never put much thought to it. The problems associated with it could be related to drivers.

I have been using a Creative sound card for the past four years and it never tripped up on Pulse.

---

### Post by Bruce H on 2009-10-31
I'm running Ubuntu 9.10 (x86_64) on a Dell Insprion 530m. 

I'm using an integrated Intel HDA soundcard, and pulseaudio give me no end of difficulty. It's completely useless for audio chats. Skype, GTalk, SL Voice... none of these work with pulseaudio for me. However, removing pulseaudio and relying on ALSA works fine, albeit I can only use one of those services at a time. With pulseaudio, sound is very choppy, almost unusable. Recording lags badly. After just a few minutes, the person on the other end receives my voice 30 seconds later, or more.

So the answer seems to be to remove pulseaudio, but the ubuntu-desktop package requires pulseaudio, and Ubuntu recommends that I not remove that package because it is also used during upgrades. I removed it anyway.

I have a PCI SoundBlaster card that works fine, but if I use that, I wouldn't be able to use the front microphone/headphone jacks. And I'm not convinced that pulseaudio won't have the same problems with that.

All in all, I'm not very happy with sound in Ubuntu. If the problem is my Intel sound card, then why does ALSA work fine with it and not pulseaudio?

---

### Post by phrostbyte on 2009-10-31
PulseAudio (not ALSA) is the source for many of the problems people are having. ALSA has it's own problems, but PulseAudio is a major contributor.

IMO Audio has overtaken Wifi as the weakest link in the desktop experience.

I had software mixing issues in 8.04, but since then no problems, but TBH I'm just lucky in this. There are a lot of people having problems.

---

### Post by hellion0 on 2009-10-31
Pulse gave me issues, not wanting to play nice with my ALI M5451, but a "sudo apt-get remove pulseaudio" fixed things for me.

---

### Post by Exodist on 2009-10-31
Sad part is if the Ubuntu Devs would just talk with the Pulse Audio Devs for a few hours. The issues with Pulse Audio would prob get solved. Even the lead PA dev said that the problem is with the way Ubuntu is trying to implement PA. I am not sure exactly how he ment that. But if both sides would just freaking communicate and work together this issue would get resolved. Case closed!

---

### Post by 23meg on 2009-10-31
> **Exodist said:**
> Sad part is if the Ubuntu Devs would just talk with the Pulse Audio Devs for a few hours. The issues with Pulse Audio would prob get solved. Even the lead PA dev said that the problem is with the way Ubuntu is trying to implement PA. I am not sure exactly how he ment that. But if both sides would just freaking communicate and work together this issue would get resolved. Case closed!

[http://ubuntuforums.org/showpost.php?p=8147632&postcount=26](http://ubuntuforums.org/showpost.php?p=8147632&postcount=26)
[http://ubuntuforums.org/showpost.php?p=8193167&postcount=46](http://ubuntuforums.org/showpost.php?p=8193167&postcount=46)

---

### Post by MindFlayer on 2009-10-31
5.1 Surround sound through S/PDIF *still* didn't work for me with Karmic and its Pulseaudio... Reverting back to Alsa once again until this is resolved. :(

---

### Post by koleoptero on 2009-10-31
No pain for pulseaudio here. Everything worked fine since the beginning.

---

### Post by Exodist on 2009-10-31
> **23meg said:**
> [http://ubuntuforums.org/showpost.php?p=8147632&postcount=26](http://ubuntuforums.org/showpost.php?p=8147632&postcount=26)
[http://ubuntuforums.org/showpost.php?p=8193167&postcount=46](http://ubuntuforums.org/showpost.php?p=8193167&postcount=46)
> we discussed how to better communicate needs between pulse and Ubuntu.

Indeed. Understand I am not trying to complain. I am just pointing out what needs to be done. Thus discussing how to better communicate and actually doing it are two different things.

---

### Post by gradinaruvasile on 2009-10-31
Sadly i think PA is not ready (Jaunty + up to Karmic rc its broken on every system i tested it on). 
I mean it works great BUT ONLY A HANDFUL of applications are 100% compatible with it. Heck, even totem hangs/crashes with it. Tried on NVidia (older+newer), HDA Intel chipsets, all computers i had available (10 i think). 
It was not stable on ANY OF THEM.

I am aware of PA's virtues, but consider that many new people try Ubuntu nowadays and EVERY ONE OF THEM needs audio. Here in our office 3 of 4 of us use Ubuntu 9.04. We all removed PulseAudio because it crashed all the time/hogged CPU. We are in the IT department btw and have experience in general Linux stuff. 

But the newcomers are left out there. Most people dont ever come to the forums with their problems. Its a big problem not having a stable audio system OOTB. The frustrating part is that THERE IS ONE and its name is ALSA - I am aware of the advantages op PA, but let it be optional to install for those who really need it. I dont and noone i know REALLY needs it.

Even in Karmic if i removed PulseAudio the sound came back to normal. But had to use alsamixer (i use it nonetheless cause thats the best way to control everything, the GUI is broken sometimes) in terminal if u remove PA. Its a non-ergonomic/geeky interface, not suited at all for newcomers.

[COLOR="Red"]BTW the above mentioned newcomers (and me included in this case) dont really care about who's fault is the unstability/brokenness of a major component of the OS. 
[/COLOR]

Its just that Linux is unstable/broken - thats their impression. They dont want to fiddle with terminal commands/workarounds they dont understand to make something basic to work.

Thats the ugly truth.

---

### Post by koleoptero on 2009-10-31
> **gradinaruvasile said:**
> Heck, even totem hangs/crashes with it.
No it doesn't.

---

### Post by Xbehave on 2009-10-31
Yes, It's a sane audio design for the modern desktop, some of the features should be stripped out to make a pa-lite, however it's core function is mixing and this is best done in the userspace daemon. While i have had more problems with PA than alsa, they are also easier to resolve
```
alias restart-pulse="pulseaduio -k && nohup pulseaudio &"
```
(i'm still not sure how to fix alsa as removing and replacing all the modules is pretty tricky)
The features that interest desktop users are (IMHO):
[LIST]
[*]Mixing moved to userspace, improving kernel stability/relibabilty
[*]per-app volume controls
[*]Powersaving, tell music programs and cards to sleep when they have nothing to do
[*]Between pulseaduio & xorg+kms it, desktop Linux will be designed securely without a need for root permissions.
[/LIST]
there are plenty of other benefits too but these seam to be the design & practical benefits that affect desktop users.

No pain, no gain and PA is definitely worth it.

---

### Post by Zaq on 2009-11-01
I updated to 9.10 and everything was horribly broken.. yet again.
It was the same thing when I bumped Ubuntu in to 9.04, except this time I didn't have the patience to mess around for hours with and without knowledgeable unix friends trying to fix things. So I just removed pulseaudio completely. It's hard to describe how happy I am now that it's gone. It never worked that well in 9.04, but I learned how to live with its quirks. 

Sure, individual stream audio volume settings are nice, but I never used it. All PA did for me, like someone mentioned earlier or in another thread, add another volume settings to work with.
PA volume control on its own I found was pretty useless, I always had gnome-volume-control open so I could actually change the ALSA settings running in the background. If I wanted to watch flash/youtube stuff, or DVDs or whatever, the range of volume settings were pretty bad with just PA.

And now the 'new PA' was even worse this time around instead of better like I had hoped. Not sure if it was a bug or some such, but I couldn't find almost any audio settings. All I had was balance left/right and volume. :confused:
But what I did find that I had lost my nerve with PA completely, and I'm really glad it's gone.

PS. 
I can understand people whining is annoying to listen to, but perhaps even more annoying is when people shrug it off with "works for me"
PA is not just an isolated problem for a fringe group of users it's a significant problem for a significant portion of people. And it should be addressed as such.

PPS.
Ah, I at least feel better for getting to vent all that out :D

---

### Post by Johnsie on 2009-11-01
Dont wanna be rude, but the interface looks tacky and is not very user friendly.

---

### Post by Mornedhel on 2009-11-01
The main problem for me is that the Gnome volume control applet lost all support for anything that isn't PulseAudio. I used to be able to control ALSA with it once I'd uninstalled PulseAudio; now when I remove PulseAudio I have to write a shell script (granted, a simple one) to control and display volume from my media keys...

Well, actually the main problem might be that removing PulseAudio and falling back to ALSA was the simplest way to get sound working reliably, without crackling or crashing (sometimes taking down sound-using applications with it).

---

### Post by HeWhoE on 2009-11-01
I've been experiencing failure in pulseaudio since I installed 9.10 yesterday.  Audio plays fine for a few minutes and then stops as pulseaudio really starts pushing the CPU.  

[IMG]http://i49.photobucket.com/albums/f259/HeWhoE/Screenshot-Terminal.png[/IMG]

I'm on a Dell Dimension 4500s with a 2.40GHz P4, and a C-Media Electronics Inc CM8738 (rev 10) audio controller card installed.

---

### Post by Xbehave on 2009-11-01
> **HeWhoE said:**
> I've been experiencing failure in pulseaudio since I installed 9.10 yesterday.  Audio plays fine for a few minutes and then stops as pulseaudio really starts pushing the CPU.
pulseaduio -k && nohup pulseaudio &, will restart PA, however this really shouldn't happen, what media player are you using (with which engine if there are multiple choices), several engines require special settings to work right with PA (shouldn't be needed, but in reality it is :()

---

### Post by Saptrans on 2009-11-02
> **Xbehave said:**
> Yes, It's a sane audio design for the modern desktop, some of the features should be stripped out to make a pa-lite, however it's core function is mixing and this is best done in the userspace daemon.

Well, why should mixing be done in userspace, if soundcard has a hardware mixing, for example? I don't get it.

Also, I'm seeing there "works for me" in this topic, but nobody said what *exactly* works for him/her. Some of us have special needs and some - not.

And my main point is "I don't need it". Why can't I *choose* between alsa and pulseaudio with Gnome 2.28.0? That is what disturbing me most.

---

### Post by papangul on 2009-11-02
> **HeWhoE said:**
> 
I'm on a Dell Dimension 4500s with a 2.40GHz P4, and a C-Media Electronics Inc CM8738 (rev 10) audio controller card installed.
I have the same card and experienced this problem continiuously for the last few months on karmic.See the first comment on this page:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407647)

I had also filed a bug report at alsaproject:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646)

---

### Post by VertexPusher on 2009-11-02
> **papangul said:**
> I had also filed a bug report at alsaproject:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646)
Why do you file PulseAudio bug reports to the ALSA bug tracker?

---

### Post by papangul on 2009-11-02
> **VertexPusher said:**
> Why do you file PulseAudio bug reports to the ALSA bug tracker?
Because this message appears in my syslog when sound fails.
```
Jul 23 17:25:38 ubuntu pulseaudio[5062]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jul 23 17:25:38 ubuntu pulseaudio[5062]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_cmipci'. Please report this issue to the ALSA developers.
Jul 23 17:25:38 ubuntu pulseaudio[5062]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jul 23 17:28:05 ubuntu pulseaudio[5062]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 3103772180 bytes (17595080 ms).
Jul 23 17:28:05 ubuntu pulseaudio[5062]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_cmipci'. Please report this issue to the ALSA developers.
Jul 23 17:28:05 ubuntu pulseaudio[5062]: alsa-util.c: snd_pcm_dump():
```

---

### Post by MorphingDragon on 2009-11-02
> **Exodist said:**
> I been using GNU/Linux since 1998. Why the hell do we even need Pulse? Do we really need to keep throwing junk into the distro thats Beta at best.
ALSA is fine, works great. Why the change?

Because until PA, Linux/BSD never had a good of sound server as Windows/Mac OSX. The crackling is actually a problem with the ALSA libraries. It is fixed by going pure PA or Pure ALSA.

---

### Post by Exodist on 2009-11-02
> **MorphingDragon said:**
> Because until PA, Linux/BSD never had a good of sound server as Windows/Mac OSX. The crackling is actually a problem with the ALSA libraries. It is fixed by going pure PA or Pure ALSA.
Which brings the point why both on Ubuntu if they are cuasing so many issues.
Debian for example is staying with ALSA until all the issues are worked out with PA.

---

### Post by 3rdalbum on 2009-11-02
Crackling, distorted audio is the fault of your PCM channel being up too high. Turn it down to 95% or lower and you'll be fine.

The issues with Pulseaudio can only be caused by, as is often said, PA's use of functions that were never properly tested in the audio drivers.

Because I don't have these problems with Pulse. It adds a bit of audio latency to one game that I sometimes play, but in return I get an awesome amount of control over what programs get sound from where, and I get individual volume controls for each application; anyone who watches DVDs or Blu-rays while keeping an instant messenger open in the background will REALLY appreciate that feature.

---

### Post by VertexPusher on 2009-11-02
> **3rdalbum said:**
> I get individual volume controls for each application; anyone who watches DVDs or Blu-rays while keeping an instant messenger open in the background will REALLY appreciate that feature.
Totem has a buit-in volume control.
VLC has a built-in volume control.
MPlayer has a built-in volume control.
Xine has a built-in volume control.
Any Flash-based media player has a built-in volume control.

What am I missing?

---

### Post by Xbehave on 2009-11-02
> **Saptrans said:**
> Well, why should mixing be done in userspace, if soundcard has a hardware mixing, for example? I don't get it.
If the soundcard has real hardware mixing, then the mixing is done on the card if it does not then mixing is done in software, neither of these need much kernel interaction. Now cards with real hardware mixing are special cases, but it is not worth a distro having 2 different install bases one for cards w/ HW mixing and another for those without.

> And my main point is "I don't need it". Why can't I *choose* between alsa and pulseaudio with Gnome 2.28.0? That is what disturbing me most.
At the moment, that is a problem with the ubuntu packaging not with pulseaduio. Eventually it will be because gnome is using pulseaudio features* and the developers can't be bothered to maintain support for depreciated APIs, if enough people care they will maintain it themselves.

*The particular feature that will be used soon is positional sound to get stereo sound for simple event.

Regarding "I don't need it", do you not want powersaving?
[LIST]
[*]**MPlayer has a built-in volume control.** - Mplayer does not have built-in volume it, unless you launch it with softvol, it changes the volume of PCM
[*]**Any Flash-based media player has a built-in volume control.** - Some do, many don't particularly games and websites.
[/LIST]
And many programs such as, instant messenger clients (that 3rdalbum mentions), system notifications, etc do not have volume controls, so you can't turn the volume down in them while turning your music/video program's high

I am concerned that adding yet another volume control is going to make everything even more complicated (I'm sure i'm not the only person that has had audio problems because one of the 100s of bars in alsamixer was set to 0), I think for a lot of software it is needed. Additionally it doesn't make sense for every app to do its own software volume, when it can be done once across all applications by a sound daemon. To prevent confusion the apps you list can drop their softvol code and simply provide access to the PA control for the app. Implementing all softvols in the same place means that if softvol get improved, for example by making 0% mute sound or doing non-linear scaling (we don't hear linearly). Implementing it in PA (or OSS4 or ALSA) means that it can take advantage of HW mixing if its available.

---

### Post by VertexPusher on 2009-11-02
> **Xbehave said:**
> The particular feature that will be used soon is positional sound to get stereo sound for simple event.
One more proof that PulseAudio is a solution desperately looking for a problem. I'm sure people will appreciate being notified in stereo when PulseAudio has sucked their laptop batteries dry.

> Regarding "I don't need it", do you not want powersaving?
Running at 100% CPU for the most basic audio operations is not exactly a powersaving feature. By the way, ALSA in 9.10 does powersaving [just fine](https://lists.ubuntu.com/archives/ubuntu-devel/2009-May/028264.html).

> Mplayer does not have built-in volume it, unless you launch it with softvol, it changes the volume of PCM
Nothing keeps you (or the package maintainer) from making -softvol a default setting.

---

### Post by Xbehave on 2009-11-02
> **VertexPusher said:**
> One more proof that PulseAudio is a solution desperately looking for a problem. I'm sure people will appreciate being notified in stereo when PulseAudio has sucked their laptop batteries dry.
I'm not a fan of the feature but it is basically free for pulseaudio to do as its just mixing.


> Running at 100% CPU for the most basic audio operations is not exactly a powersaving feature.
That's a bug, all software has them, personally I've never seen it, all I've seen is pa crash a few times on suspend/resume and that never worked before so i can't say if it's better/worse than just alsa.

> By the way, ALSA in 9.10 does powersaving [just fine](https://lists.ubuntu.com/archives/ubuntu-devel/2009-May/028264.html).
That only works when there is no incoming audio for 10 seconds, sound servers allow you to switch it of as soon as you know there will be no sound and it improve CPU usage of programs by releasing sound in buffered bursts

> Nothing keeps you (or the package maintainer) from making -softvol a default setting.True but then every single program has to implement it's own softvol, IM clients, flash games, system-alerts, email clients, etc all have to implement redundant code instead of handing it off to a sound server.

---

### Post by VertexPusher on 2009-11-03
> **Xbehave said:**
> I'm not a fan of the feature but it is basically free for pulseaudio to do as its just mixing.
Fine. Then OpenAL can do it, too.

> That's a bug, all software has them, personally I've never seen it, all I've seen is pa crash a few times on suspend/resume and that never worked before so i can't say if it's better/worse than just alsa.
There are two problems with PulseAudio bugs in general:
[LIST=1]
[*]The fanboys deny their existence. ("I've never seen that happen here. You must be making that up.")
[*]The PulseAudio developers developed a habit of assigning blame to everyone but themselves. ("That's a driver bug. That's an application bug. That's none of our business.") Yet as soon as PA is removed from the picture, all the bugs magically disappear.
[/LIST]
> That only works when there is no incoming audio for 10 seconds, sound servers allow you to switch it of as soon as you know there will be no sound and it improve CPU usage of programs by releasing sound in buffered bursts
Sorry, but that's utter nonsense. Nothing keeps ALSA from doing the same and turning the amplifier off "as soon as you know there will be no sound". The reason why they keep it on for 10 seconds is because of the audible popping sound that occurs every time the amplifier is switched on/off. If they could, they would even turn it on a few seconds **before** a sound occurs, but unfortunately no one has a crystal ball to predict the future. So the 10 seconds timeout is a good solution that was chosen on purpose.

> True but then every single program has to implement it's own softvol, IM clients, flash games, system-alerts, email clients, etc all have to implement redundant code instead of handing it off to a sound server.
[LIST=1]
[*]They need softvol anyway because they can't rely on PA being available (e.g. in Debian or Kubuntu). The only thing they can count on is ALSA.
[*]They need not implement redundant code. For example, GStreamer has a softvol element. In fact PulseAudio itself is adding redundancy because it reimplements existing features such as ALSA's dmix plugin. I wouldn't mind if their reimplementation was actually an improvement, but apparently it is not. All it does is introduce new bugs to an otherwise perfectly stable and mature architecture.
[/LIST]

---

### Post by Xbehave on 2009-11-03
> **VertexPusher said:**
> Fine. Then OpenAL can do it, too.
Your point? 

There are two problems with PulseAudio bugs in general:
> The fanboys deny their existence. ("I've never seen that happen here. You must be making that up.")
And the people that dislike it exagurate them, pretending that everybody has problems with it.
> The PulseAudio developers developed a habit of assigning blame to everyone but themselves. ("That's a driver bug. That's an application bug. That's none of our business.") Yet as soon as PA is removed from the picture, all the bugs magically disappear.
Actually it's usually "That's a driver bug/"That's an application bug" because it is, the "it's none of our business" stuff is just FUD, they do fix problems in pulseaudio, but they also blame others when others are to blame. For example the skype betas had a bug that would trigger a bug in PA, so the PA-devs told skype and skype fixed their code, while the PA devs fixed theirs. 
[/LIST]

> but unfortunately no one has a crystal ball to predict the future. So the 10 seconds timeout is a good solution that was chosen on purpose.
Actually that is exactly what pulseaudio does have, it has a buffer of audio from all the programs, and so it can see when there is going to be no sound. Now this buffer could be implemented in ALSA but the problem is that because ALSA shouldn't do complex mixing, if a new sound comes into the buffer ALSA can't handle it gracefully, so it's better for PA to keep track of the premixed audio so when "new sound" comes along it can make a new buffer gracefully.

> They need softvol anyway because they can't rely on PA being available (e.g. in Debian or Kubuntu). The only thing they can count on is ALSA.

So every single program that uses sound, firefox, kopete, duluge, games, etc needs to implement not only softvol but also a gui to give users control?
> They need not implement redundant code. For example, GStreamer has a softvol element.
This ignores the need for a GUI and the fact that as  PA is doing mixing anyway, there is no need do softvol when it will just be redone when the mixing comes.
> In fact PulseAudio itself is adding redundancy because it reimplements existing features such as ALSA's dmix plugin.
According to various sites, dmix
1) doesn't preserve audio quality
2) should not be done in the kernel
3) is an ugly work around (for example AFAIK there is no GUI to give access to dmix's softvols because it does not keep track of which volumes inputs are running)

> I wouldn't mind if their reimplementation was actually an improvement, but apparently it is not. All it does is introduce new bugs to an otherwise perfectly stable and mature architecture.
But so many of the bugs are just exposing bugs in ALSA and applications, ignorance is bliss I suppose.
Additionally when it comes to next gen systems with things like bluetooth speakers and networked audio streamers, ALSA gets ugly (apparently, this is just what i've read, but basically shuffling sound around various kernel subsystems is a bad idea because floating code is messy) so either ubuntu (and linux in general) has to maintain 2 separate sound systems one for new systems/mobile devices/etc and one for desktop systems. The general consensus amongst those that maintain distros seams to be that this 2 sound systems is a terrible idea, so it's worth the pain of getting PA working just to avoid having a separate system for fancy audio configurations and desktop systems

---

### Post by VertexPusher on 2009-11-03
> **Xbehave said:**
> And the people that dislike it exagurate them, pretending that everybody has problems with it.
If PulseAudio was optional, the way it is in Debian, we would not be arguing here. I don't deny that PA may be working for some combinations of hardware and software. But that's not good enough.

The problem is that for the past two years, Ubuntu (and therefore Linux in general) has earned a reputation for having a broken sound system. People who try Ubuntu for the first time and then discover that sound doesn't work the way they know it from Windows will be discouraged. PulseAudio should be an optional add-on, not a default component that needs to be removed if it doesn't work.

> Actually it's usually "That's a driver bug/"That's an application bug" because it is, the "it's none of our business" stuff is just FUD, they do fix problems in pulseaudio, but they also blame others when others are to blame.
If PulseAudio is unable to emulate ALSA transparently so that it works without modifiying existing drivers and applications, then it's a bug in PulseAudio, not elsewhere. To the developers of ALSA, PulseAudio is a misbehaving client application. Why should they make modifications to ALSA just because of PA, if all the other client apps work fine?

> For example the skype betas had a bug that would trigger a bug in PA, so the PA-devs told skype and skype fixed their code, while the PA devs fixed theirs. 

Yet for some reason, Skype never caused issues with ALSA. The trouble was due to PA's compatibility layer, which is just not compatible enough!

> Actually that is exactly what pulseaudio does have, it has a buffer of audio from all the programs, and so it can see when there is going to be no sound. Now this buffer could be implemented in ALSA
ALSA has been using such a buffer for at least five years. It's documented [here](http://alsa.opensrc.org/index.php/Dmix). How else do you think they achieved mixing in software? The interesting thing is that they managed to implement it without spawning a daemon process. Any application talking to the "default" device automatically uses ALSA's software mixer. It's completely transparent.

> So every single program that uses sound, firefox, kopete, duluge, games, etc needs to implement not only softvol but also a gui to give users control?
Most of these did so long ago. By the way, GUI controls can be wrapped in libraries and reused multiple times. Sound systems should be designed to work independent of GUIs anyway. What if there is no GUI because the system is running in headless mode, e.g. as a MIDI synthesizer/sound module such as Receptor or Plugzilla?

> According to various sites, dmix
1) doesn't preserve audio quality
Neither does PulseAudio. If you mix audio streams from multiple sources, you always have to do sample rate conversion and channel up/downmixing, because CD playback is 44.1kHz stereo, DVD playback is 48kHz 5.1 surrond, TV playback may be 32kHz mono, VoIP may even be 8kHz mono. ALSA's sample rate converter is based on libsamplerate, and that's currently the best option available. Anyone who thinks PulseAudio can do it better clearly has no understanding of audio mixing. The only way to achieve total transparency is to bypass any mixer and talk to ALSA's "hw" PCM devices directly. In that case, samplerate conversion is up to the application. The benefit is a much lower latency. Jack is taking advantage of that.

> 2) should not be done in the kernel
It's not done in the kernel anyway.

> 3) is an ugly work around
Nonsense. Even Lennart himself called dmix a "nifty piece of engineering".

> Additionally when it comes to next gen systems with things like bluetooth speakers and networked audio streamers, ALSA gets ugly (apparently, this is just what i've read, but basically shuffling sound around various kernel subsystems is a bad idea because floating code is messy)
I'll just insert a quote from [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices) here:

*"Note that there are a few approaches for a2dp (alsa, gstreamer, pulse?), maybe two for sco (alsa, pulse?). Alsa is the simplest and should support the greater variety of audio clients directly."*

That does not exactly sound like "it's ugly", does it?

> The general consensus amongst those that maintain distros seams to be that this 2 sound systems is a terrible idea, so it's worth the pain of getting PA working just to avoid having a separate system for fancy audio configurations and desktop systems
Nonsense. PA is running on top of ALSA, so you have at least these two. And then there is Jack, which PA is not designed to replace.

Currently the pain is on the users' side. PulseAudio has the potential to push people away from Linux. The current situation is totally unacceptable because bad reputations, once built up, are hard to get rid of.

---

### Post by ratcheer on 2009-11-03
I agree with VertexPusher. PA has become a PITA.

Tim

---

### Post by Xbehave on 2009-11-03
> **VertexPusher said:**
> If PulseAudio was optional, the way it is in Debian, we would not be arguing here.
> The problem is that for the past two years, Ubuntu (and therefore Linux in general) ...
That is a problem with ubuntu packaging not pulseadudio.

> If PulseAudio is unable to emulate ALSA transparently so that it works without modifiying existing drivers and applications, then it's a bug in PulseAudio, not elsewhere.
If PulseAudio supports what ALSA should be doing, but the programs are using ALSA in a way that ALSA shouldn't behave then the problem is with the app, PulseAudio will often try and offer a work around at thier level but fundamentally its the APP that's broken, so instead of just implementing all the bugs in ALSA, like wine does for windows, the PA devs do say when it's an APP problem.

> To the developers of ALSA, PulseAudio is a misbehaving client application. Why should they make modifications to ALSA just because of PA, if all the other client apps work fine?
Because that's not what's happening, PulseAudio is putting sound out in a way that ALSA says it can handle, it turns out that ALSA can't handle those methods, it's clearly ALSAs problem. PA can be fixed by not calling stuff ALSA can't handle, but ALSA should also start doing what it says it can.

> Yet for some reason, Skype never caused issues with ALSA. The trouble was due to PA's compatibility layer, which is just not compatible enough!
Being compatible != Copying bugs, skype was putting invalid data to ALSA, this worked on ALSA for some reason, however it was still a bug in skype. Pulseaudio was assuming that programs where outputing sane data, that was a bug in pulseaduio. Both bugs have now been fixed by thier respective developers.

> ALSA has been using such a buffer for at least five years. It's documented [here](http://alsa.opensrc.org/index.php/Dmix). How else do you think they achieved mixing in software? The interesting thing is that they managed to implement it without spawning a daemon process. Any application talking to the "default" device automatically uses ALSA's software mixer. It's completely transparent.
They managed to do it without spawning a daemon process by doing floating point operations in kernelspace, it works but it's not as good as NOT doing floating point operations in kernelspace. Firstly, getting as much stuff out of the kernel as possible makes a system much more secure. Then there is desktop/tty switching, the kernel shouldn't care who the current active user is (e.g if you switch to TTY1 and login as root), but if you don't have a sound daemon (arts/esd/pulseaudio) then your computer will keep playing sounds from all users (or have to mess around with kernel stuff every time somebody logs in). Additionally Kernel memory is valuable, it takes a lot more effort to swap out parts of the kernel, so holding lots of buffers in the kernel is not a good situation. So while dmix is a great piece of software and it's not designed well.

> Most of these did so long ago.
Where? No non-audio application on my desktop has an audio slider, where is the softvol setting in firefox?

> By the way, GUI controls can be wrapped in libraries and reused multiple times.
You can't just stick a volume slider on the interface, you end up with stupid UIs like that

> Sound systems should be designed to work independent of GUIs anyway.
Exactly, what better independence than having no sound GUI in non-sound apps

> What if there is no GUI because the system is running in headless mode, 
That's not what I'm talking about we both know ALSA/PA/etc all work perfectly fine without a GUI, but i think providing a unified GUI for volume controls is a good idea, this has not been done for dmix+per program softvols)

> Neither does PulseAudio....
Fair enough, I'm not going to pretend i know much about audio mixing, as I said this is just what I've read at various sites.

> It's not done in the kernel anyway.
Where is it done then? I thought ALSA was in the kernel so without using CUSE, once programs feed sound into ALSA it is processed in the kernel

> Nonsense. Even Lennart himself called dmix a "nifty piece of engineering".
I'm under the impression that it is a nifty piece of engineering but it's design is ugly (something akin devfs)

> That does not exactly sound like "it's ugly", does it?Yes it does, every program needs to have its settings changed to use the new device (which itself has to be created, followed by getting ALSA to register the new device, does that require an ALSA restart or is it automatic?). While PA-bluez is still under development, the instructions are simply having correct versions of both stacks (something that the distro should do for you), once the development is stabilised it will work OOB.

> Nonsense. PA is running on top of ALSA, so you have at least these two. And then there is Jack, which PA is not designed to replace.
ALSA is just one of the outputs PA can use, getting software to go through PA means it can output sound to devices ALSA isn't **designed** to handle (networked/bluetooth/etc). In the backend ALSA isn't going away but the API is what is being replaced by PulseAudio complient code (which can use much of the ALSA api, just a more strict implementation)

When networkmanager first came out it was buggy as hell, people cried and wanted to go back to wpasupplicant &co. Eventually everything started working and people realised that networkmanager makes network management a lot simpler and has a much better design than handfuls of scripts based around wpasupplicant, IMO the same is true of PulseAudio. (With NM many, including me felt it was pushed into ubuntu too soon and without enough testing)

---

### Post by VertexPusher on 2009-11-03
> **Xbehave said:**
> That is a problem with ubuntu packaging not pulseadudio.
Yeah, we all know that by now. For some weird reason, no distro ever got PA's packaging right. But even Fedora users report the same issues as we do, despite the fact that Lennart is on Red Hat's payroll and maintaining PA on Fedora. That should tell you something.

> Because that's not what's happening, PulseAudio is putting sound out in a way that ALSA says it can handle, it turns out that ALSA can't handle those methods, it's clearly ALSAs problem. PA can be fixed by not calling stuff ALSA can't handle, but ALSA should also start doing what it says it can.
No. If the PulseAudio guys know what's wrong with ALSA, they should submit patches instead of pointing fingers. Obviously they are requesting features that no other client application ever used or needed.

> skype was putting invalid data to ALSA, this worked on ALSA for some reason
Exactly, and Lennart wants it **not** to work so that ALSA becomes more like PA's compatibility layer. That's totally backwards, it's the tail wagging the dog. He should try to find out why ALSA does **not** fail, and mimic its behaviour.

> They managed to do it without spawning a daemon process by doing floating point operations in kernelspace
Dmix is a userspace module. ALSA does not do mixing in kernelspace. I think you are confusing this with OSS4.

Look, I'm just pointing out that PulseAudio is totally missing its original goals:
[LIST]
[*]Lennart keeps saying that glitch-free audio is PA's killer feature, yet people complain about glitches more than ever before. For some reason, dmix does a much better job at being glitch-free. According to Lennart this should not happen, yet it does.
[*]Lennart says that a misbehaving application should not affect sound in other applications. Yet a single misbehaving application can bring the entire PA system down. It's the exact opposite of ALSA which is rock-solid in comparison.
[*]Lennart says that powersaving is one of PA's goals, yet you hear people complain about 100% CPU load with PA. Lennart's most reliable powersaving feature so far is his method of pointing fingers at other developers who, from his point of view, seem to do it all wrong.
[/LIST]

---

### Post by Technoviking on 2009-11-03
I think we are getting close with Pulse audio. IN Ubuntu 9.10 I had zeo trouble on my computer getting pulse to work output or input.

T-V

---

### Post by edin9 on 2009-11-03
> **Technoviking said:**
> I think we are getting close with Pulse audio. In Ubuntu 9.10 I had zero trouble on my computer getting pulse to work output or input.

T-V

Lucky you.

---

### Post by Xbehave on 2009-11-03
> **VertexPusher said:**
> Yeah, we all know that by now. For some weird reason, no distro ever got PA's packaging right. But even Fedora users report the same issues as we do, despite the fact that Lennart is on Red Hat's payroll and maintaining PA on Fedora. That should tell you something.
My point was about not being able to remove PA on fedora this is fairly easy.

> No. If the PulseAudio guys know what's wrong with ALSA, they should submit patches instead of pointing fingers. Obviously they are requesting features that no other client application ever used or needed.

It is mostly hw specific bugs (e.g i've not run into any problems on my hardware), if ALSA offers a feature but its untested on hw ALSA supports it is a bug not a feature request.

> Exactly, and Lennart wants it **not** to work so that ALSA becomes more like PA's compatibility layer. That's totally backwards, it's the tail wagging the dog. He should try to find out why ALSA does **not** fail, and mimic its behaviour.
Alsa has a set API (even if it is only in the code documentation), if a program doesn't conform to this API, it's stupid to blame PA for not being compatible with programs that use ALSA bugs. While you could aim for bug4bug compatibility (like wine) supporting the specification and getting programs to support the spec is a much better plan otherwise your just reimplementing ALSA.

> Dmix is a userspace module. ALSA does not do mixing in kernelspace. I think you are confusing this with OSS4.
I thought you said it didn't spawn any outside processes? 

> Lennart keeps saying that glitch-free audio is PA's killer feature, yet people complain about glitches more than ever before. For some reason, dmix does a much better job at being glitch-free. According to Lennart this should not happen, yet it does.

glitch-free audio is a stupid name for the feature as it has little to do with glitchs. While it does have bugs, it is getting better pretending PA is getting worse is disingenuous.
 
> Lennart says that a misbehaving application should not affect sound in other applications. Yet a single misbehaving application can bring the entire PA system down.
These are PA bugs and need to be fixed, however I'm yet to see one

> It's the exact opposite of ALSA which is rock-solid in comparison.
Sounds like you got lucky with ALSA, when it stumbled into a bug it messed up the kernel fairly badly, to fix it i would always have to reboot, a PA bug is shallow by comparison
> Lennart says that powersaving is one of PA's goals, yet you hear people complain about 100% CPU load with PA.
Again this is a bug, yet another one I have never seen, but you've already attacked the powersaving for having bugs. Just because a new-feature has bugs doesn't mean everybody should give up and go home.

> Lennart's most reliable powersaving feature so far is his method of pointing fingers at other developers who, from his point of view, seem to do it all wrong.
I couldn't care less how much of a prick he is, I mean look at linus attacking ck and alan cox. The points Lennart makes regarding audio architecture are fairly valid (i'm not an expert on audio) and the future of linux audio is pulse, there is little dobut that all the big distros will shift to PA once its ready because it has a better design (debian hasn't adopted it yet but it also took it's time about NetworkManager).

---

### Post by gradinaruvasile on 2009-11-03
So much arguments... 

Guys, these do not matter to the average users.
What matter is that they have a sound system that doesnt work right.
Period.

---

### Post by gradinaruvasile on 2009-11-03
> **koleoptero said:**
> No it doesn't.

Yes it did for me (and wasnt alone either).
Until i got rid of PulseAudio...):P

---

### Post by akoskm on 2009-11-19
It should be removed from the default installation. Never happened with ALSA that I get 98 CPU usage from the soud system.
Later I've figured out that the high CPU usage was caused by a PulseAudio thread what name was **(null)**. :|
It's not a Bug, it's a Feature!

---

### Post by VertexPusher on 2009-11-19
PulseAudio is only the beginning. Watch out for the next stupid "feature" that Ubuntu will adopt from Fedora:

[http://linux.slashdot.org/story/09/11/18/2039229/Fedora-12-Lets-Users-Install-Signed-Packages-Sans-Root-Privileges](http://linux.slashdot.org/story/09/11/18/2039229/Fedora-12-Lets-Users-Install-Signed-Packages-Sans-Root-Privileges)

---

### Post by akoskm on 2009-11-19
> **VertexPusher said:**
> PulseAudio is only the beginning. Watch out for the next stupid "feature" that Ubuntu will adopt from Fedora:

[http://linux.slashdot.org/story/09/11/18/2039229/Fedora-12-Lets-Users-Install-Signed-Packages-Sans-Root-Privileges](http://linux.slashdot.org/story/09/11/18/2039229/Fedora-12-Lets-Users-Install-Signed-Packages-Sans-Root-Privileges)

I can't believe that a true linux dev cames up with an idea like this.

---

### Post by Sin@Sin-Sacrifice on 2009-11-19
I think both sides are right. I, personally, have pulseaudio kicking *** on this system but my last PC and many others that I have set up couldn't do PA. I like it when it works and hate it when it doesn't. It just needs a little more refinement before it becomes the standard. When, though, it does work it's the best. I never want to be without PA ever again. Hopefully I won't have to.

---

### Post by koleoptero on 2009-11-19
> **akoskm said:**
> I can't believe that a true linux dev cames up with an idea like this.

They had to come up with something.

---

### Post by Mortus Pryde on 2009-11-19
> **MorphingDragon said:**
> Because until PA, Linux/BSD never had a good of sound server as Windows/Mac OSX. The crackling is actually a problem with the ALSA libraries. It is fixed by going pure PA or Pure ALSA.

Oh, I think some one finally put 1 and 1 together, most others seem to just toss blame.

Here is my experience with dinkering around with SecondLife to get stable sound. If it's configured to use PulseAudio only sound is stable, if it uses the ALSA Plugin it crashes PulseAudo. So the problem squarely lays in bridging the two, now on which side of that bridge lays the problem, I don't know, but that is the problem, not "XXXX system sucks! Why do we need it?".

---

### Post by SunnyRabbiera on 2009-11-19
I think Pulse is going to improve, its better off now then it was a few years back.

---

### Post by alexfish on 2009-11-19
a pain and what a pain it was

 got it working under my own steam 
 
 basic configurations could have been done through the distro  ( Ubuntu 9.10)

 a little heavy on cpu  / Intel atom330  old  hercules sound card lists as CM8738
        didn't like intel  on board sound

how ever i am pleased with it results

---

### Post by ad_267 on 2009-11-19
Pulse is great for most desktop applications.

If you want to play games, run them with pasuspender. I set ETQW to use OSS and it works perfectly.

---

