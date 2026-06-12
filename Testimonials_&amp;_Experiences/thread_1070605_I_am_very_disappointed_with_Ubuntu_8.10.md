---
title: "I am very disappointed with Ubuntu 8.10"
date: 2009-02-15
forum: Testimonials &amp; Experiences
---

### Post by Olnex on 2009-02-15
Today I installed Ubuntu 8.10 and did an update, before I was using Archlinux, which is OK for me, I just do not want to spend much time configuring the system, so I installed Ubuntu.

After the update, the sound does not work, whatever I tried, it does not work. Finally I removed all packages that contain "pulse", then it works, why an update gives me problem other than better functionalities?

With Arch, I do not use pulseaudio because I do not want to configure it(this is one of the reasons I installed Ubuntu), and rolling -release tends to be more fragile when update, however, the fact is, I did several updates(include kernel updates) under Arch, and got no problem at all, whereas Ubuntu creates problems after update.

Maybe one day I'll go back to Ubuntu.

---

### Post by mikewhatever on 2009-02-15
> **Olnex said:**
> 

Maybe one day I'll go back to Ubuntu.

Yeah, may be. Perhaps one day, you'll also stop complaining. It might not be evident, but ranting is not appreciated, especially in help & support sections.

---

### Post by Perfect Storm on 2009-02-15
Thread moved

---

### Post by YaroMan86 on 2009-02-15
> **Olnex said:**
> Today I installed Ubuntu 8.10 and did an update, before I was using Archlinux, which is OK for me, I just do not want to spend much time configuring the system, so I installed Ubuntu.

I actually switched *from* Ubuntu *to* Arch because I felt that the Ubuntu dev team has stopped being very proficient on getting bugs. It seemed they kept on focusing way too much on features and ignored gaping problems in the codebase. When they added a sound server (Pulse Audio) that is nowhere near ready, I felt my time with Ubuntu was drawing to a close. Then 8.10 came out and proved to be very unstable, slow, and unreliable. So I switched to Arch because it allowed me **complete** control over my packages and what is on my system. It may not be as "intuitive" as Ubuntu, but at least it'll never make the same mistakes like Ubuntu did with Pulse Audio. And thanks to a rolling release cycle I can be sue the updated packages are actually tested with my distribution before coming downstream to me.

> **Olnex said:**
> After the update, the sound does not work, whatever I tried, it does not work. Finally I removed all packages that contain "pulse", then it works, why an update gives me problem other than better functionalities?

This is because PulseAudio helps nothing and breaks most everything else: If you liked using Skype, Audacity, WINE, or anything else that worked perfectly fine with OSS, ALSA, or ESD, then you'll be miserable with PA. I think Canonical should have waited until PA was at least version 1.0 before ruining sound in Ubuntu with it the way they did starting in 8.04.

Of course, there will be a lot of apologists about this forum who will say crap like "We want PulseAudio because it's not Linux-specific like ALSA so we can get more applications."

I am going to tell you right now that's crap. If we want something not Linux specific, then lets use OSS4! It's actually stable and it ACTUALLY works! And guess what, it's also cross platform.

I've also noticed that most cross-platform audio developers had little to no problems porting their apps for work with ALSA. This stupid "lets expect application developers to abandon a stable codebase for experimental crap like Pulse Audio" needs to stop! They want something stable and not obscure like PA.

Pulse Audio is a failed experiment for Ubuntu, get over it, and I hope before long you'll get rid of it. Maybe then people will actually start to think of Linux as valid for the desktop. Not think of it as some radical Windows alternative that breaks things for experimental purposes.

Don't feed me the "software mixing" BS, either. If Canonical REALLY wanted to win over audiophiles with working software mixing they would have put their focus on dmix getting configured properly, which works with ALSA which, unlike PulseAudio, actually works.

Ubuntu was very close to proving Linux's sound capability was caught up with all the others, and then Pulse Audio came along. Thank God I use Arch and never have to deal with a fundamentally broken system like PA.

> **Olnex said:**
> With Arch, I do not use pulseaudio because I do not want to configure it(this is one of the reasons I installed Ubuntu), and rolling -release tends to be more fragile when update, however, the fact is, I did several updates(include kernel updates) under Arch, and got no problem at all, whereas Ubuntu creates problems after update.[/QUOT]

I find rolling release to be less problematic than a tightly controlled discrete release cycle, because now the devs can actually focus on bugs instead of features, which Ubuntu loves to emphasize and ignore bugs as a result.

[QUOTE=Olnex;6738958]Maybe one day I'll go back to Ubuntu.

Maybe I will too: When they fix major problems and then worry about features. I feel the problem with a locked-in 6 month cycle is they don't allow themselves any real time to give it real QA. Debian may sometimes take years for a new stable release, but we can be assured Debian stable would be more reliable than the latest Ubuntu.

For me to come back to Ubuntu a few things have to happen, first:

1. They have to get rid of PulseAudio.

2. They need to make more bug-centric releases, wherein no actual new features are put in, but all medium-to-critical bugs are at least quelled, if not eliminated outright.

3. The next release is boasting web-integrated apps as one of its features. This must not happen. If there's anythign we learned from the late nineties early 2000s is that web-based apps running on the desktop are slow as hell, buggy, bloated, and make the user want to poke their eye out violently with an ice pick.

4. Ubuntu needs to break free from a discrete cycle and either go rolling release or just simply say "Next version of ubuntu comes when it is ready" because all this 6-month pandering does is introduce more big bugs on top of all the other big bugs.

**Edit**

I also think Ubuntu is still following a little too closely to a Stallmanist agenda. It's nice to have ideals, but I think gNewSense is already showing us how lousy a 100% "free as defined by Richard Stallman" system can be. We should have already learned this lesson with the failure of Gobuntu which was trying to do what gNewSense is failing at now: Being a functional 100% "free" system.

Stallman is trying to force Linux into being GNU simply because the real GNU failed before it could even get completed: The HURD is absent, the GNU tools are used by everyone, not just Linux, and RMS has basically gone around preaching at everyone he can about things that he thinks are "evil" and crap like that. And he's trying to take credit for Linux with this "GNU/Linux" naming crap.

I'll probably get flamed or talked down for this addendum, but RMS is operating off an obsolete definition of Operating System and may or may not be aware of it. The operating system is only the kernel, drivers, and things that run in kernel space that manage hardware and the execution of processes. Nothign more, nothing less.

This does not include the GNU C library or the GNU toolchain, which neither operate in kernel space nor manage hardware or processes. They make a good OPERATING ENVIRONMENT, yes, but that's not the operating system and the operating system doesn't need an operating environment to run. Yes, a SYSTEM DISTRIBUTION requires an operating environment, but not an operating system.

Stallman is incorrectly defining an operating system as what a CONTROL SYSTEM is now defined: The operating system and the operating environment combined with the essential hardware of a computer system. Unfortunately this still does not result in a "GNU/Linux" naming for the control system, as the operating system comes first and the operating environment second, so it could be "Linux/GNU."

But the problem is the GNU toolchain is actually a very small part of the operating environment. It's outnumbered by many other libraries, daemons and servers that are NOT done by the GNU Project that we can't accurately describe a Linux-based control system as "Linux/GNU" either. Nor can we say the shell o application layers of a system distribution for Linux as GNU-controlled. We have BASH... Okay, great. We have GNOME. Okay, great. We also have CSH, KDE, ZSH, XFCE, and any number of non-GNU shells available to the user by any distribution. And yes... Xorg itself is NOT GNU! And the GNU Project is too busy wasting its time ruining XFree86 to notice most distributions are actually using Xorg, the de facto standard X server for Linux and most other UNIX, too!

Nor can we call an entire system distribution GNU either, as GNU never made a Linux distribution. Ubuntu's not GNU/Linux. It's Linux-based, but it's just Ubuntu, as that's what the makers call it. Not Ubuntu GNU/Linux... not GNU Ubuntu. Not even Linux Ubuntu or Ubutnu Linux, just Ubuntu, which is Linux based, NOT GNU BASED.

A lot of Stallmanists are trying to revise history, too. Are you even aware that over ten years ago Richard Stallman felt Linux was a waste of time and wanted people to develop instead for the failed GNU operating system driven by HURD? You won't hear that from Stallman now that he realizes he's a failed developer and is now trying to claim Linux is GNU and take credit from Torvalds and actual Linux developers and put it on him.

Don't give me the inane "Stallmanix" line, either. All the needed was to put GNU somewhere in the Linux name, being the head of the GNU Project, to claim credit for it.

Keep in mind Linus himself didn't want to call it Linux, he wanted to call it Freax, but his FTP host liked Linux better. Note also that the FTP host actually gave Linus credit for what is actually his creation.

Linus didn't create Linux to make a political statement the way Stallman did with GNU. He used the GPL for convenience and practicality, not ideals.

We thank you for the GNU tools, Stallman. I love GCC, I like GNOME a bit, too, but that's all you've actually done for Linux, and they're all optional parts, too, as there's alternatives to everything GNU in a Linux distribution, even the GNU C Library, even replaced by those of Linus Torvalds' own creation.

Sorry to burst the Stallmanist reality distortion bubble that Linux is a GNU system, but the reality is that all GNU has to do with Linux is providing a license and some tools. It is far from the actual essence of Linux. But it's the stupid "Linux is GNU" that is contributing to the average user of computers to not take Linux seriously.

Now. Cue the rabid GNU/FSF/Stallman devotees who delude themselves into thinking everything RMS says about Linux as gospel to start flaming me.

---

### Post by solwic on 2009-02-15
> **YaroMan86 said:**
> I actually switched *from* Ubuntu *to* Arch because I felt that the Ubuntu dev team has stopped being very proficient on getting bugs. It seemed they kept on focusing way too much on features and ignored gaping problems in the codebase. When they added a sound server (Pulse Audio) that is nowhere near ready, I felt my time with Ubuntu was drawing to a close. Then 8.10 came out and proved to be very unstable, slow, and unreliable. So I switched to Arch because it allowed me **complete** control over my packages and what is on my system. It may not be as "intuitive" as Ubuntu, but at least it'll never make the same mistakes like Ubuntu did with Pulse Audio. And thanks to a rolling release cycle I can be sue the updated packages are actually tested with my distribution before coming downstream to me.

..........



No, seriously.  Tell us how you really feel....

---

### Post by bruce89 on 2009-02-15
> **YaroMan86 said:**
> (snip)

Actually, upstream is moving to PulseAudio. Ubuntu is being too slow to take it up I'd say.

> **Olnex said:**
> For me to come back to Ubuntu a few things have to happen, first:

1. They have to get rid of PulseAudio.


Not going to happen because of upstream.

> **Olnex said:**
> 2. They need to make more bug-centric releases, wherein no actual new features are put in, but all medium-to-critical bugs are at least quelled, if not eliminated outright.

Again, upstream won't have this.

> **Olnex said:**
> 3. The next release is boasting web-integrated apps as one of its features. This must not happen. If there's anythign we learned from the late nineties early 2000s is that web-based apps running on the desktop are slow as hell, buggy, bloated, and make the user want to poke their eye out violently with an ice pick.

I have not seen that at all.

> **Olnex said:**
> 4. Ubuntu needs to break free from a discrete cycle and either go rolling release or just simply say "Next version of ubuntu comes when it is ready" because all this 6-month pandering does is introduce more big bugs on top of all the other big bugs.

Enter Debian.

> **Olnex said:**
> I also think Ubuntu is still following a little too closely to a Stallmanist agenda. It's nice to have ideals, but I think gNewSense is already showing us how lousy a 100% "free as defined by Richard Stallman" system can be. We should have already learned this lesson with the failure of Gobuntu which was trying to do what gNewSense is failing at now: Being a functional 100% "free" system.

You've got to be kidding if you think Ubuntu is 100% free.

The rest is too long to bother with.

---

### Post by mikewhatever on 2009-02-15
> **YaroMan86 said:**
> I actually switched *from* Ubuntu *to* Arch.... bla bla bla ....

Hope you'll like Arch. :lolflag:

---

### Post by Tamlynmac on 2009-02-15
> mikewhatever
Hope you'll like Arch. :lolflag:

I hope if they don't - they complain there. :-k

I often considered the complexities of endeavouring to satisfy everyone. Doubt it would ever be feasible.

---

### Post by SeePU on 2009-02-15
I find a lot of things break in *buntu but one of the reasons is because a lot of packages are up-to-date and like someone said, they don't always do a good job finding the bugs or getting them fixed.  Despite what the fan boys say here, that is the case.

I had sound break on me because of a kernel update but someone has found a 'solution' for now.  You use alsamixer and mute one of the settings.

The good thing about *buntu being popular is that you are more likely to find some article/post/report of some issue being 'fixed' since the number of users are so high.

---

### Post by YaroMan86 on 2009-02-15
> **SeePU said:**
> I find a lot of things break in *buntu but one of the reasons is because a lot of packages are up-to-date and like someone said, they don't always do a good job finding the bugs or getting them fixed.  Despite what the fan boys say here, that is the case.

I've found recently that Ubuntu devs completely ignore most bugs until people loudly complain about them on Launchpad... and then only ten it only raises the chance of the bug getting fixed to say 5%.

The other problem is that Ubuntu doesn't actually use that many up-to-date packages as you might think. Ubuntu gets revision releases of the Linux kernel maybe a month or two at a time. And the point release isn't even seen until the next release.

In Arch, it's a matter of days before the newest revision comes downstream to the users. I can't say for point releases as I haven't used Arch long enough to see 2.6.29 come downstream yet. But I do know that unless there's a critical bug release coming out, you don't see any real NEW versions of packages until the next release with Ubuntu.

Thus, the failure of a discrete release cycle. Arch is actual bleeding edge, but usually "stable" bleeding edge stuff, as in, versions of something that are deemed stable enough by the author to be released as something other than a nightly build, like Compiz Fusion.

> **SeePU said:**
> I had sound break on me because of a kernel update but someone has found a 'solution' for now.  You use alsamixer and mute one of the settings.

In other words: you circumvent the thing that broke sound in the first place: Pulse Audio.

> **SeePU said:**
> The good thing about *buntu being popular is that you are more likely to find some article/post/report of some issue being 'fixed' since the number of users are so high.

True. The problem is it's not actual bug fixes. You reinstall Ubuntu or go up to a new version your woerkarounds are gone and its broken again. The Ubuntu devs have become notorious both upstream and downstream as ones who tend to get carried away with features and totally ignoring bugs.

[QUOTE]Actually, upstream is moving to PulseAudio. Ubuntu is being too slow to take it up I'd say.[/QUOTE[]

Ubuntu's upstream is Debian. Unless Linus Torvalds says "Lets bundle Pulse Audio into the kernel." it won't get much further upstream then that. The only other codebases that bother with the broken Pulse Audio system is Fedora (Which is notorious, like Ubuntu, for being broken in many ways.) and SuSE (I think.) and that distro is in the hands of a Microsoft shill like de Icaza. All three of them don't have massive codebases based off of them.

Please tell me you're not suggesting every last distribution developer suddenly lost their sanity and said "Lets integrate a sound server that is notoriously unstable and unreliable." Because I doubt you'll be seeing much outside Ubuntu, Fedora, or SuSE wasting their time with Pulse Audio until it's actually ready for use, which it isn't.

And again, I tell myself "thank goodness I use Arch and don't have to put up with Pulse Audio ever again. Or Mono, either.

"I have not seen that at all."

Obviously you were asleep during those days, where developers suddenly had the stupid idea that Java and HTML were a good basis for apps. I wen through it. If you though Ubuntu was slow now, it'll be even slower once this goes through.

You put too much stock in Debian being THE Linux. In fact, I keep reading on /. and elsewhere that Debian's development is slowly going to hell. I'm not based off of Debian. I use Arch, it's its own codebase. And it only installs a core so I don't have to put up with stupid decisions like the one you're defending.

As for Ubuntu being 100% free, that's not quite what I said. I said it needed to stop being afraid to take its own course just because Richard Stallman gets obsessed with calling innocent things evil. It doesn't allow me to use the closed source driver without intervention (Granted, Arch doesn't install it either, by default, but it doesn't install any driver besides vesa by default because it wants to give users the option of using X.)

But I see so many distros that stop worrying about what Stallman would say if they bundled MP3 playback or binary blobs. I like open source, I prefer to use it, but I would use a distro that would rather just give me what I actually want, not what Stallman wants.

Arch doesn't provide these either at the start, but for different reasons: It just installs a core, it has no reason to include anything proprietary as the core is alread covered by "free" software. But it doesn't base it's repository components over how "evil" packages are (Main - "Free", Supported, Restricted - "Non-free", Supported, Universe "Free", Supported, Multiverse "Non-free," Unsupported.) the way Ubuntu does.

The only two distros I said were 100% free were Gobuntu and gNewSense.  And they are both abysmal flops compared to distros that actually allow "non-free" bits. Pay attention to what I say.

You want a usable system people will really flock to: Don't make the mistakes Ubuntu and gNewSense do: No Pulse Audio, no over-zealous obsession with "free," a "when its ready" or rolling release cycle.

I find it hilarious you suggest that assuming that just because Debian will get Pulse Audio it'll suddenly become Linux standard. It just means an entire Linux codebase will suddenly have really screwed up sound now. Give it another year and you'll see even more people leave Ubuntu as we see even the Debian devs can't fix the brain damages of PA.

ALSA works. Pulse Audio doesn't. PA being broken isn't unique to Ubuntu. I have friends who use SuSE and Fedora who, immediately after installing, remove PA and configure ALSA just so they can actually have good sound.

Pulse Audio sucks. Canonical's "late" adoption of Pulse Audio (Whatever you say. It's early until it's actually stable and ready.) has already shown the Linux world that PA was a bad experiment made worse by ignorant statements like what you said there.

People dont care about "being adopted upstream" they care about their stuff working.

So yes. Go ahead and say Debian will "fix" PulseAudio. It's only when PA is actually working without screwing over everyone I'll shut up about it. Talk is cheap. Has anyone actually tried improving Pulse Audio? All I see PA's dev doing is badmouthing ALSA, pining for OSS, and then breaking more crap in Linux sound.

So go ahead and defend PA. I'll use something that actually works.

---

### Post by Tamlynmac on 2009-02-15
Yawn.

As the incessant drone continues.](*,)

---

### Post by YaroMan86 on 2009-02-15
> **Tamlynmac said:**
> Yawn.

As the incessant drone continues.](*,)

See, it's that attitude right there that so many people leave Ubuntu. Whenever someone criticizes it, it's a rant. When called to fix a problem, you say "upstream will do it."

In case Ubuntu fanboys haven't noticed, upstream hates Ubuntu right now because they **** everything up and expect upstream to fix their problems magically.

---

### Post by Simian Man on 2009-02-15
> **YaroMan86 said:**
> 
Linus didn't create Linux to make a political statement the way Stallman did with GNU. He used the GPL for convenience and practicality, not ideals.

We thank you for the GNU tools, Stallman. I love GCC, I like GNOME a bit, too, but that's all you've actually done for Linux, and they're all optional parts, too, as there's alternatives to everything GNU in a Linux distribution, even the GNU C Library, even replaced by those of Linus Torvalds' own creation.

Sorry to burst the Stallmanist reality distortion bubble that Linux is a GNU system, but the reality is that all GNU has to do with Linux is providing a license and some tools. It is far from the actual essence of Linux. But it's the stupid "Linux is GNU" that is contributing to the average user of computers to not take Linux seriously.


Thank you for saying that, I couldn't agree more.  The worst thing is that people like Stallman who are so vocal are perceived to be the "leaders of Linux" when, in reality, it is people like Linus and all of the developers I've never even heard of who are doing the most for Linux.

And if you want a stable, reliable system, I wouldn't choose Ubuntu or Arch.

---

### Post by Tamlynmac on 2009-02-15
> YaroMan86
See, it's that attitude right there that so many people leave Ubuntu. Whenever someone criticizes it, it's a rant"

Or potentially, they leave because of the ranting. Please share you data with respect to supporting this statement. Or is it simply another of your opinions.

Two "Yawns"

---

### Post by YaroMan86 on 2009-02-15
> **Tamlynmac said:**
> Or potentially, they leave because of the ranting. Please share you data with respect to supporting this statement. Or is it simply another of your opinions.

Two "Yawns"

You don't get out of this forum much, do you? Have you never Googled "Ubuntu sucks" or "I left Ubuntu for (Insert name of distro here.)"

Yawn all you like, I'm not going to wipe your *** or use Google for you. People have left Ubuntu because of the same exact reasons I did. 

Hell, looks around this forum, read all the departure posts and see what they say.

Nope, I don't care for the burden of proof argument. I don't have to hand deliver evidence to those who don't even look around the Internet.

---

### Post by solwic on 2009-02-15
> **YaroMan86 said:**
> You don't get out of this forum much, do you? Have you never Googled "Ubuntu sucks" or "I left Ubuntu for (Insert name of distro here.)"

Yawn all you like, I'm not going to wipe your *** or use Google for you. People have left Ubuntu because of the same exact reasons I did. 

Hell, looks around this forum, read all the departure posts and see what they say.

Nope, I don't care for the burden of proof argument. I don't have to hand deliver evidence to those who don't even look around the Internet.

You have anger management issues, don't you?  If Ubuntu doesn't work for you, don't use it.  We're not holding a gun to your head.  

Use what works for you and let others do the same.  Why rant?

---

### Post by David2009 on 2009-02-15
I just got here.  I have not had success with connecting my Toshiba A300 64-bit laptop via wireless with OpenSuse.  Just as a test, I put in the Ubuntu 8.1 Live CD.  I've been connected for a while now, and I have sound, too.  Or, at least I heard the start-up sounds.  I can't put a CD in, since I have the Live CD running now.

I'm wondering about installing it over my OpenSuse 11.1.  Hummm....

But, from hearing the opening sounds as the OS booted up, to the internet connection, to how the package of programs is working, I have no complaints.

---

### Post by Bios Element on 2009-02-15
> **YaroMan86 said:**
> You don't get out of this forum much, do you? Have you never Googled "Ubuntu sucks" or "I left Ubuntu for (Insert name of distro here.)"

Yawn all you like, I'm not going to wipe your *** or use Google for you. People have left Ubuntu because of the same exact reasons I did. 

Hell, looks around this forum, read all the departure posts and see what they say.

Nope, I don't care for the burden of proof argument. I don't have to hand deliver evidence to those who don't even look around the Internet.

The people who are mad are ALWAYS more vocal then the ones who stay. It's a proven FACT that content users are not likely to state they are content. I'm not going to wipe your *** or use Google for you.

Try google "I left (insert name of distro here.) for Ubuntu. Have fun with your future rants about how evil and ignorant I am btw. I look forward to them. :)

---

### Post by wolfen69 on 2009-02-15
> **YaroMan86 said:**
> See, it's that attitude right there that so many people leave Ubuntu.

what attitude? he was just yawning. give a break and don't try and read too much into it. there's no reason for anyone to get uptight. 

if you don't like something, you can do like in the song *I Love my Computer*, "I just click, and you just go away." 

it's a damn operating system for christs sake. not war or famine. everyone should just lighten up a little. there's no real reason for animosity and tension. i'm starting to develop thick skin around here, which is a good thing i think. enjoy what ever os you are using, and peace.

---

### Post by Rumbl3 on 2009-02-15
hmmm i haven't had many problems at all. I guess that's why linux is nice tons of flavors for everyone to be happy. So i don't really see what all the warfare is about. If this was M$ then I expect flaming and fighting because your stuck period with what u get. 

just my 2cents before another wall of text crit's my eyes for 10,000 damage! hehe


EDIT: btw you can google anything that imo is got some popularity or gaining mainstream popularity fast, and u will find a thousand links about how much someone hates it, so that's not very good example imo.

---

### Post by Tamlynmac on 2009-02-16
> YaroMan86
You don't get out of this forum much, do you? Have you never Googled "Ubuntu sucks" or "I left Ubuntu for (Insert name of distro here.)"

Yawn all you like, I'm not going to wipe your *** or use Google for you. People have left Ubuntu because of the same exact reasons I did. 

Hell, looks around this forum, read all the departure posts and see what they say.

Nope, I don't care for the burden of proof argument. I don't have to hand deliver evidence to those who don't even look around the Internet. 

Anger & hostility - I'm shocked.

Just by reading a few website, I could compile enough data to know precisely the reasons why people have left the community. I'm certain specific patterns would emerge that could reduce the study down to some or most peoples motives. 

Considering, the mass exodus that's occurring (forum membership of 770,030 and increasing) I have no choice but to concur.:-k

You've have simply overwhelmed me with logic.

Yawn.

---

### Post by wolfen69 on 2009-02-16
> **Tamlynmac said:**
> Anger & hostility - I'm shocked.



don't you love it when someone acts like there's a prize to be won if they're "right"? thumping their chest and proclaiming  righteousness in the name of all that is good and holy. if someone came from another planet and saw these discussions, they would think this is a religious cult or something.

it's actually pretty entertaining. tamlynmac: don't bother with some of these people. they only see things as they want.  i see certain people making my ignore list real soon.

---

### Post by Tamlynmac on 2009-02-16
wolfen69

I'm still believe the forum needs an Envy section. Where people can drone on without alternative opinions. A section where only the OP's opinions are factual and written arguments are forbidden.:lolflag:

---

### Post by jdong on 2009-02-16
Ok, no Ubuntu, Pulse sucks, we like Arch. Us Ubuntu devs sit around and brainstorm new ways to break existing features while simultaneously ignoring launchpad bugs.

I don't think there's anything possibly productive that could come out of this thread -- the frustrations have been voiced and are here for everyone to listen to. Let's move on.

---

