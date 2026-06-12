---
title: "So much for Ubuntu"
date: 2008-11-11
forum: Testimonials &amp; Experiences
---

### Post by Feanor's Curse on 2008-11-11
Hi

First of all I'd like to say I was a big fan of ubuntu and really appreciate all the effort put into it. That being said, I am now switching to another distro (probably debian), because after 8.04 and 8.10 I've had it. Now, this is not intended to be a random rant, but I would like to point out the reasons why I think that ubuntu got worse with every recent release and maybe this will help change the policies behind it.

Enough introduction. My point being is that ubuntu has become *incredibly* buggy to the point of being almost unusable for me. Some examples (this list could be much longer indeed):
[LIST]
[*]I upgraded my office computer. After some hours, suddenly sudo segfaulted and after reboot, everything related to login was no longer working. Rescue shell did the trick, but still, even there sudo to a system user failed. So I had to make a fresh install.
[*]Now, I can no longer use the office printer (worked before, in 8.04). Seems like I am by far not the only person having printer problems.
[*]SSH/SFTP no longer is able to modify/create files. Nautilus, gedit, name any application. This makes working on a distant computer incredibly difficult.
[*]On my other PC, suddenly sound stopped working (again, other users having this problem). I don't know if this is connected to the Skype installation or the totally rushed PulseAudio (see 8.04, though never had much problems with it myself until now), but is rendering the machine pretty much unusable again.
[*]Nautilus Samba integration is not working properly, though I found a workaround using smbmount.
[*]...
[/LIST]

Bugs can happen. But the new version is so incredibly buggy, I find new problems every day and when searching the internet, I am rarely alone with that. Well, I guess you could say why not use 8.04, the LTS version? Because, in fact, this was the most buggy version up to 8.10 (and that really started pissing me of). Conclusion: I will switch to a stable distro like Debian. It may not have all the nice features, and not be as up-to-date as ubuntu, but at least it's stable and not just rushed out - it's done, when it's done and not like - hey, let's release a new version in six month, regardless of it being tested or stable enough. If I want to test releases for the developers, I could as well switch to windows.

Enough said, thanks for the work (no irony), I was a really big fan up to 7.10. And now I will move on. Maybe, if things change, I will one day consider coming back. So long,
FC

---

### Post by wolfen69 on 2008-11-11
i find ibex to be the best yet. to each his/her own. use what works for you. no hard feelings here.

---

### Post by Tamlynmac on 2008-11-11
Almost every new release, a number of similar posts appear. They don't add anything new, just same old rederrick. Considering this is their first post I must ask where they went to get assistance with 8.04 issues?

One must ask what would inspire someone to log on to the forums and write this as their first post. Appears they might have an agenda. Trolls often do endeavor to disrupt and degrade that which upsets them. But it would help if they would posts a number of assistance requests prior to writing similar diatribes. Just some advice to future trolls. Don't just join the forum and a few months later write derogatory posts that endeavor to excite forum members in an attempt to illicit inflammatory responses.

Just my observation.

---

### Post by drvista on 2008-11-11
> I upgraded my office computer. After some hours, suddenly sudo segfaulted and after reboot, everything related to login was no longer working. Rescue shell did the trick, but still, even there sudo to a system user failed. So I had to make a fresh install.

no need to reinstall you just need to add your user to sudo group
ctrl+alt+f2
login as root
 adduser name_of_user admin
reboot 
> Now, I can no longer use the office printer (worked before, in 8.04). Seems like I am by far not the only person having printer problems.

if your system is working why upgrade to unstable version 
ubuntu non LTS usually not suitable for production machines

---

### Post by Feanor's Curse on 2008-11-12
> **Tamlynmac said:**
> Almost every new release, a number of similar posts appear. They don't add anything new, just same old rederrick. Considering this is their first post I must ask where they went to get assistance with 8.04 issues?

One must ask what would inspire someone to log on to the forums and write this as their first post. Appears they might have an agenda. Trolls often do endeavor to disrupt and degrade that which upsets them. But it would help if they would posts a number of assistance requests prior to writing similar diatribes. Just some advice to future trolls. Don't just join the forum and a few months later write derogatory posts that endeavor to excite forum members in an attempt to illicit inflammatory responses.

Just my observation.

I certainly know what it looks like since this is my first post. But actually I always looked for advice (if necessary) around the internet and was always able to solve any major problems. It's just that there were way to many problems now, some even listed as bugs at launchpad or other bug tracking systems without any solution available. As I wrote, I did not post here to do some rants or being a troll, I wanted to make clear what should be changed/improved. I really like ubuntu and did not want to leave it without giving any reasons, because it's important for me.

EDIT: You know, you can put down any criticism by just calling every person a troll. I think, there was some constructive criticism in my post and not just blame. And this was my first post, because there is not only this forum on the internet and I don't see the need to register, when I had already found a solution somewhere else. I registered now, because this was the logical place to write what I had to say about the issues of ubuntu.

> **drvista said:**
> no need to reinstall you just need to add your user to sudo group
ctrl+alt+f2
login as root
 adduser name_of_user admin
reboot

That was not the problem, the user was part of the sudo group and even if not that would not lead to sudo segfaulting. All login-related mechanisms were severely broken. Thanks anyway.


> **drvista said:**
> 
if your system is working why upgrade to unstable version 
ubuntu non LTS usually not suitable for production machines

Because there were also some things I did not like about 8.04 and since I already had a machine running 8.10 successful (well, until sound dropped at least) I upgraded. Everything was backuped anyway.

---

### Post by 3rdalbum on 2008-11-12
Absolutely something must be done to try and combat regressions. I dislike Intrepid because of some annoying problems that weren't present in Hardy. If I were in charge of Ubuntu, I would immediately remove Pulseaudio, or at least provide a way for users to run with absolutely no Pulseaudio at all; it's actually more messed-up than it was in Hardy.

I realise that suspend and hibernate are implemented differently on every motherboard, and that reverse-engineering support for these things is difficult - but it was working perfectly in Ubuntu 8.04 for me, and now it's instagib in 8.10.

I upgraded with the hope that my wireless would be more reliable, my Xorg wouldn't crash so often, and that audio programs would no longer interfere with eachother. I'm not suffering any X crashes anymore, but now my wireless is worse and there's so much audio latency it's ridiculous.

I'm updating every day with the Proposed repository, hoping that there will be some fixes coming down the pipeline... but only one problem (DVD tray going back in) has been fixed there.

Yes, I should do more to help with alpha and beta testing, but how do these regressions happen in the first place? How is this stuff getting messed up in Ubuntu, and not so much in other distributions?

I'm worried, because the Debian pastures are looking mighty green.

---

### Post by remoon on 2008-11-12
im using intrepid ibex, just installed kde 4.1.3 Their on the right path with the new KDE desktop, but it is still sooo sluggish, apps take ages to load. :-(

---

### Post by ukripper on 2008-11-12
> **wolfen69 said:**
> i find ibex to be the best yet. to each his/her own. use what works for you. no hard feelings here.

+1..using ibex is like dream come true...

---

### Post by Sealbhach on 2008-11-12
For me, Ibex fixed a lot of things that weren't working in Hardy. 

++1.

Sorry things didn't work out for OP.

.

---

### Post by Feanor's Curse on 2008-11-12
> **3rdalbum said:**
> Absolutely something must be done to try and combat regressions. I dislike Intrepid because of some annoying problems that weren't present in Hardy. If I were in charge of Ubuntu, I would immediately remove Pulseaudio, or at least provide a way for users to run with absolutely no Pulseaudio at all; it's actually more messed-up than it was in Hardy.

I realise that suspend and hibernate are implemented differently on every motherboard, and that reverse-engineering support for these things is difficult - but it was working perfectly in Ubuntu 8.04 for me, and now it's instagib in 8.10.

I upgraded with the hope that my wireless would be more reliable, my Xorg wouldn't crash so often, and that audio programs would no longer interfere with eachother. I'm not suffering any X crashes anymore, but now my wireless is worse and there's so much audio latency it's ridiculous.

I'm updating every day with the Proposed repository, hoping that there will be some fixes coming down the pipeline... but only one problem (DVD tray going back in) has been fixed there.

Yes, I should do more to help with alpha and beta testing, but how do these regressions happen in the first place? How is this stuff getting messed up in Ubuntu, and not so much in other distributions?

I'm worried, because the Debian pastures are looking mighty green.

Absolutely my point, thanks for the comment! *Regression* is the word I was looking for. This is what I described as being released without proper testing, unlike debian. Having bugs can never be avoided, but when so many things (also for colleagues of mine) that worked before just stop working then something is clearly wrong.

---

### Post by cardinals_fan on 2008-11-12
> **3rdalbum said:**
> Absolutely something must be done to try and combat regressions. I dislike Intrepid because of some annoying problems that weren't present in Hardy. If I were in charge of Ubuntu, I would immediately remove Pulseaudio, or at least provide a way for users to run with absolutely no Pulseaudio at all; it's actually more messed-up than it was in Hardy.

I often wonder why Pulseaudio was implemented (a term used very loosely) by default in the first place.

---

### Post by tvtech on 2008-11-12
> **cardinals_fan said:**
> I often wonder why Pulseaudio was implemented (a term used very loosely) by default in the first place.


for OOOOOO AAAAAAWWWEEE affect!

---

### Post by cardinals_fan on 2008-11-12
> **tvtech said:**
> for OOOOOO AAAAAAWWWEEE affect!
...and it'd be just terrible to include something a bit later than Fedora, wouldn't it? ;)

---

### Post by steveneddy on 2008-11-12
My only observation would be to ask why you would install the experimental version on a work PC?

8.04 is the version that was meant to be used in a professional environment. If it was working for you before, just stay with the version that works.

I have to use my laptop daily for work and I will keep it on 8.04 because it is stable and works well on my laptop.

Jut my .02

---

### Post by Feanor's Curse on 2008-11-13
Thanks for the comments. But c'mon, I already answered the question about LTS two times.

---

### Post by ugm6hr on 2008-11-13
> **Feanor's Curse said:**
> Absolutely my point, thanks for the comment! *Regression* is the word I was looking for. This is what I described as being released without proper testing, unlike debian. Having bugs can never be avoided, but when so many things (also for colleagues of mine) that worked before just stop working then something is clearly wrong.

The usual bleeding edge vs stable argument.

Freedom means you get to pick where in the spectrum you fall.  If Ubuntu's latest incarnation doesn't fit the bill, the previous LTS is an option (that you have discarded), so Debian stable is exactly that - stable.  Hope that works better for you.

---

### Post by Feanor's Curse on 2008-11-13
Thanks. I guess that's a good conclusion.

---

### Post by DrMega on 2008-11-13
> **Tamlynmac said:**
> Almost every new release, a number of similar posts appear. They don't add anything new, just same old rederrick. Considering this is their first post I must ask where they went to get assistance with 8.04 issues?

One must ask what would inspire someone to log on to the forums and write this as their first post. Appears they might have an agenda. Trolls often do endeavor to disrupt and degrade that which upsets them. But it would help if they would posts a number of assistance requests prior to writing similar diatribes. Just some advice to future trolls. Don't just join the forum and a few months later write derogatory posts that endeavor to excite forum members in an attempt to illicit inflammatory responses.

Just my observation.

What is it with the "Ubuntu community" these days? Why is it that anyone who dares to point out that the almighty Ubuntu hasn't worked for them is automatically a troll, has the wrong hardware, or should have stuck with some other OS (suggesting don't try anything new, ever)?

Then we see post counts being used against such people. Why is that? Is Ubuntu Forums the only place in the entire world where someone might seek advice? What if they are already a Linux guru from other distros and fancied trying the almighty Ubuntu that is steaming ahead in popularity polls? What if they are long standard members of other Linux forums, or even unofficial Ubuntu forums? What if they scoured the internet, found this forum and found posts from others that reported the same problems and followed the advice in those posts?

You really can't win on here. If Ubuntu works, great, your in the gang. If it doesn't, it is because you are a troll or have the wrong hardware. If you ask questions that have already been asked many times, you get slated for not checking if your question has already been asked and answered. If you don't ask, you get slated for giving up without asking.

---

