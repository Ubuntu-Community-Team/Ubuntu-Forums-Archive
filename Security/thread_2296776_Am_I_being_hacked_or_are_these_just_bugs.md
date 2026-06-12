---
title: "Am I being hacked or are these just bugs?"
date: 2015-09-28
forum: Security
---

### Post by tdvreel on 2015-09-28
Ok, I'm going to try and keep this simple and list some of the random occurrences then give a bit of the story later.


[LIST]
[*]Bluetooth won't stay turned off
[*]Clicking sporadically won't work properly
[*]Dash opens automatically randomly
[*]A distorted noise came through the speakers (freaked me out)
[*]Apps switch focus randomly
[*]Gnome glitched out (this is Ubuntu gnome 15.04)
[*]Windows 10 said my time was 4 hours ahead than what it actually was
[*]My Linux partitions appeared as unallocated space in windows disk management
[/LIST]

This all happened on the day I installed it.

Now for a bit of background. To put it bluntly, this has happened before on Ubuntu 15.04 (Unity). Earlier this year on my old laptop to be exact. This has only happened in Ubuntu 15.04, never in 14.04 or any other distribution. At first I assumed I was hacked so I got rid of Ubuntu and never looked back, until recently that is. I was using Ubuntu 14.04 without a problem for a while but I wanted to use Gnome 3 ( I know I'm weird). So I installed Ubuntu Gnome 15.04 yesterday and the weirdness that I use to assume to be someone hacking me reoccurred. The only difference between now and the old laptop is that the old laptop didn&#8217;t do this on its first day of Ubuntu 15.04, it took it awhile.

I no longer think it to be a hacker, as its only happening in Ubuntu 15.04 and none else and no other computer in my house seems to be affected, but I don't dismiss it completely. So I want your take on all of this. Do you think its a hacker? Can this be explained? The noise freaked me out the most both times and its what lead me to think it was a hacker.

---

### Post by CharlesA on 2015-09-28
Windows cannot read linux file systems, so that is why your linux partition shows up the way it does.

The time is probably due to the way Linux vs Windows handles time. Linux assumes the time is UTC and adjusts that according to the time zone.

As for your other issues, sounds more like your hardware doesn't particularly like 15.04.

---

### Post by tdvreel on 2015-09-29
So you don't believe I'm being hacked? As I've said nothing else has been compromised, not a computer nor an account I have. And for those other two things, windows disk management has always shown my linux partitions as primary partitions before never as unallocated space. And as for the time, I've never seen that happen before so I wouldn't know why it would happen now.

---

### Post by ian-weisser on 2015-09-29
Doesn't seem like any hacking I've ever heard of.
Could be hardware failure. Since three of your problems can be explained by spurious clicks, perhaps an intermittent short in the vicinity of the touchpad. Flimsy plastic laptop cases bend when your wrists rest near there....

Are you really sure it happens with only one OS/release? If not, hardware. If so, hardware settings.

A successful malicious break-in to someone else's machine requires cleverness, patience, and the skills to hide your presence. 
You describe an intrusion by someone with the cleverness and attention span of Scooby Doo.
A hack seems rather unlikely.

---

### Post by tdvreel on 2015-09-29
That's what I thought too, but everything seemed too coincidental for my comfort. However things like the noise that I heard seems to be an unusual bug, but I guess it doesn't make sense for hacker to make noise to your speakers either. Why would this only happen in 15.04 and not any other distribution, including 14.04? Also if it is just 15.04 acting up on usually how come it's happened on two different computers, I haven't seen anyone else online have the problems I've been experiencing.

---

### Post by mystics on 2015-09-29
If a hacker goes through the trouble to hack into your computer, it certainly isn't to just mess with your mind. The only place you see that is Facebook "hacking", and that isn't even real hacking. It's people being foolish enough to trust their friends near someone else's logged-in Facebook account. Real hacking generally has the hacker wanting to get something for their effort (even if to satisfy curiosity), and they certainly don't want that payoff to be an arrest for being detected.

That said, check your trackpad and focus settings. I'm not sure exactly where these are in GNOME, but it is possible you have options like tap-to-click or focus-follows-mouse turned on. The former can be annoying if you accidentally hit the touchpad a lot (like me). The latter will cause an application to come into focus when the mouse hovers over it rather than waiting for a click. I personally like it, but it can lead to some unexpected changes if you let the mouse stray to another application. This may fix the random app switching problem.

---

### Post by Habitual on 2015-09-29
> **ian-weisser said:**
> A successful malicious break-in to someone else's machine requires cleverness, patience, and the skills to hide your presence. 
You describe an intrusion by someone with the cleverness and attention span of Scooby Doo.
A hack seems rather unlikely.I agree. All that "noise" is the opposite of stealth.
Hackers love to hide and not be found.
***IF*** that is a hacker, and I don't think it is, [s]he ought to keep his/her day job.

---

### Post by matt_symes on 2015-09-29
Hi

> **tdvreel said:**
> That's what I thought too, but everything seemed too coincidental for my comfort.

Honestly, the only coincidence I see here is that it happened after you installed 15.04.

Check your log files; syslog and Xorg.0.log. ~/xsession-errors may point to something as well.

As for the windows issues, CharlesA has explained them.

Kind regards

---

### Post by The Cog on 2015-09-29
It may not be coincidence. It may be a genuine incompatibility between the hardware and 15.04 drivers.
However, I am quite sure it's not hackers. 
And I think it might be worth running the memory test that the live CD/stick offers, because the symptoms are quite diverse and don't appear limited to a particular aspect of the hardware.

---

### Post by tdvreel on 2015-09-29
OK, from what I gathered its definitely not hacker, which is good thing. Thanks for calming my vivid paranoia, it'll believe anything it cant immediately explain. I know its not the trackpad settings per se because I go through all the settings when I install a distribution and adjust them accordingly. However I tried booting elementary from a live USB last night and I gotta say I've never seen my trackpad be so wonky, which is weird cause its never been like that, not even on my old computer. I know it wasn't the settings either so I'm guessing I just have a horrendous trackpad. And as I said no problems in windows or 14.04, so it be a distribution specific ordeal. I haven't mentioned this before but it's a fairly cheap laptop, so I guess I shouldn't be too surprised if everything doesn't run too smoothly.

So I guess if it can be explained by hardware incompatibilities, my only questions left are is why is it happening in 15.04 and not 14.04. And also can the noise be explained, you know,  as opposed of me just going crazy of course. I'm quite certain what I heard was of this reality and not of my subconscious. However I should say it definitely did not sound like a voice, rather it sounded like a random distortion, kinda like a buzz mixed with three taps.

Also sorry for any grammatical errors, this was all typed with my phone.

---

### Post by ian-weisser on 2015-09-29
> **tdvreel said:**
> why is it happening in 15.04 and not 14.04

You tell us.
I see only possibilities.
1) It did happen in 14.04, but you didn't trigger the problem, or you didn't notice.
2) Some environmental difference between usage 14.04 and 15.04 (on battery, different room, external mouse, different season, etc.)
3) The 15.04 kernel introduced a bug or regression.

See what you can prove or disprove.
Does the problem occur if you run 14.04 and 15.05 from a LiveUSB?
Has anyone with similar hardware reported similar problems?
Has anyone opened a bug report for similar symptoms?

---

### Post by tdvreel on 2015-09-29
I haven't seen anyone online describe similar problems at all, much less people with similar hardware. And I know for a fact it didn't happen in 14.04, I've used it for way longer than I had with 15.04 and never have I faced bugs of the sort. As I've said,  this occurred on two different, albeit similar laptops, and as I have reiterated many times before  it's only happened on 15.04. That's the only real difference, no environmental difference of any kind. Also I never needed to use a live USB long enough to see any problems occur. I'm not very knowledgeable on the technical behalf of Linux, but why would a more updated and advanced kernel have a regression towards a newer computer rather than the old kernel. It would seem to me that 15.04 should be more compatible with my computer than 14.04 would be but that is not the case here.

---

### Post by ian-weisser on 2015-09-29
> **tdvreel said:**
> It would seem to me that 15.04 should be more compatible with my computer than 14.04 would be but that is not the case here.
That is why the class of bug where something stops working properly is called a *regression*.

I'm satisfied that you have identified a regression in the kernel on your specific hardware. I might be wrong, of course.
But that's the easy part.

In the Free Software community, most bugs get fixed by a skilled user who discovers the problem, identifies the issue in the source code, creates and tests a patch to fix the problem, and forwards the problem and solution (in one tidy package) to the developer. Fewer but more critical bugs get fixed by paid staff at Canonical and other contributing organizations.

In other words, it's not enough to discover the bug. You may wish to report the bug properly. If you report the bug, you may be asked by the bug Triager and Developer to help identify the cause and test the fix. They probably have different equipment than you do, and may be unable to reproduce the issue on their hardware.

In the past, when I have helped identify bugs and test patches, it's been annoying and cumbersome. A lot of work for little gain...but I'm still happy to do it - my responsibility as an adult is to contribute to the community. And, in the end, worthwhile.

The place to start to learn how to report it properly is [https://wiki.ubuntu.com/Kernel/Bugs#Filing_Kernel_Bug_reports](https://wiki.ubuntu.com/Kernel/Bugs#Filing_Kernel_Bug_reports)
You should add the tag 'regression-release' to the bug report.

---

### Post by tdvreel on 2015-09-30
I don't know if I want to get too involved in the situation as I'd rather just stop using 15.04, as selfish as that may sound. It seems to me that this is not a big enough problem to other people and it just so happened to be a problem for me. Do you think these problems will persist in later iterations of Ubuntu such as 15.10? I love the idea of using Linux and having an operating system that I can customize to my will that also works outside of the box as is. I want to continue using Linux but I don't want to have to stick with older distributions, I'm just kind of the person who wants to have the new and shiny thing. However it seems that there are more problems than stability in my experience with Linux.

Also please, can the noise be explained whatsoever???

---

### Post by ian-weisser on 2015-09-30
> **tdvreel said:**
> Do you think these problems will persist in later iterations of Ubuntu such as 15.10?

If you don't mow your lawn, there's always a chance that your neighbor will...but it's not a high probability.

The bug may be reported, identified, and fixed by deliberate action of a sufferer...or it may be accidentally fixed by a different patch. The latter happens, but is unlikely.

Insufficient data to predict if your problem will continue in later releases of Ubuntu.

---

### Post by buzzingrobot on 2015-09-30
Re: That bit about bluetooth not staying turned off...

If the OP is going by the bluetooth toggle in Settings, I've noticed that in Gnome on Ubuntu and Fedora it defaults to "on", and moves back to "on" after I move it to "off" and start a new session. This machine has no bluetooth hardware, so, I'd say, the option should be greyed out anyway (as it is in 15.10 Unity here).

---

### Post by tdvreel on 2015-09-30
The think I'm just going to stop Linux for awhile and wait to see how 15.10 does on my computer, if it works, then great, if it doesn't, well I'm not sure I'll continue using Linux seeing as the most used distribution didn't even work properly. And once again, can the noise be explained, it was too peculiar to be just a bug...

---

### Post by mystics on 2015-09-30
The noise was no doubt due to the ghosts out to get you!

But really, I'm not sure we can determine the cause of the noise without a lot more information about hardware and what was going on at the time. It could have been early signs of speaker failure. It could have been a normal noise that was supposed to play but got distorted in the process for some reason. It could have just been compatibility issues. Whatever the case, I seriously doubt it was a hacker, as that doesn't really fit within the behavior of someone who's trying to hack a computer. Why would they even want to send a distorted sound through the speaker anyways? It makes no sense, especially within the scope of what hackers are trying to accomplish as outlined in a few posts above.

---

### Post by tdvreel on 2015-09-30
THISTHIS POST IS THE RIGHT POST - That's what I thought as well but I couldn't understand why my speakers would make a random noise unexpectedly while idle. To me it doesn't make sense as to why a bug or a hacker would make such a noise, but there has to be some reason for it to happen. Especially on one specific distro. It wasn't like the speakers worked incorrectly, they worked perfectly fine on both computers, except for the fact a mysterious noise happened when there shouldn't of been any sound at all. Have you ever heard of this happening in any operating system before, where it hasn't been something like a virus?

---

### Post by mystics on 2015-10-01
Are you sure no sounds were supposed to be playing? I know I've had stuff running in the background that randomly made a noise for whatever reasons. Also not sure, but GNOME or some software may have a couple settings regarding sounds for different events, and if one of those events triggered, it may have caused a sound. I guess it could also be a bug, as there's virtually no limit to what those things can do.

Other than that, like I said, it may have been a hardware problem. I haven't had it happen so much with computers, but I have had it happen with other speakers, and it isn't always a constant problem. Was this something that happened multiple times when using Ubuntu GNOME, or was it a one-time deal?

Overall, like I said, this just doesn't seem to be the work of a hacker or virus. It just doesn't coincide with the behavior of either. Furthermore, this all happened the day you installed it! It is very unlikely the system was compromised in that short amount of time. The only way I can think of that happening is if you downloaded the ISO from an untrusted source or someone managed to hijack the connection and send you a malicious ISO, but I'd imagine we'd be hearing a lot more about those happening if that were the case. 

Really, the most likely scenario is that this was a software or hardware problem. Either can, and does, cause distorted sounds at time. Hackers and viruses don't behave like that.

---

### Post by tdvreel on 2015-10-01
It was Ubuntu gnome and standard Ubuntu 15.04, two different laptops, two different time spans (gnome last week, unity months ago), and two very similar noises. They were both under the same circumstances, they were idle, and no software was running during the time, and suddenly a random noise came through the speakers. I don't think it was triggered by some sort of normal event, as the noise was atypical and distorted and there wasn't any notification of an event that coincided with it. It never happened on any other distribution, only on 15.04 for both computers. I've never had heard of anyone having random noises happen like this before, even outside of 15.04.

 I just don't understand what could of made those noises, I know a hacker would try to remain as low key as possible, but I don't know how something like that noise could be triggered by nothing or a bug. I just can't believe it happened for no reason. I'm extremely paranoid to the extent of foolishness and it always assumes the improbable...but the logical side knows its not a hacker, it just can't explain it at all.

It's the strangest thing, II truly do believe all these bugs and glitches to be the doing of  hardware incompatibilities, but I just can't get part to myself to stop thinking it was a hacker, even if everything says it wasn't.

And I know the ISOs were safe, they both came from their respective sites.

---

### Post by tdvreel on 2015-10-01
Also if I were to have a hacker, how would I get rid of them?

---

### Post by QIII on 2015-10-01
When actually compromised, the best course of action is to wipe, reinstall/recover using known good backups and employ more aggressive security.  Don't leave the same locks on the doors or the bandits will come right in again.

Don't drop any nukes just yet, though.

---

### Post by tdvreel on 2015-10-01
Wouldnt nuking/dbanning work though? I thought wiping is not as thorough as dban is.

---

### Post by CharlesA on 2015-10-01
> **tdvreel said:**
> Wouldnt nuking/dbanning work though? I thought wiping is not as thorough as dban is.

It is a figure of speech.

If you want to nuke the drive with dban or whatever before you install, go for it. I doubt it will make much of a difference if your hardware doesn't like 15.04.

---

### Post by tdvreel on 2015-10-01
Nah, I'm not going to reinstall Ubuntu 15.04 at all. I was asking how I would get rid of a hacker if I were to have one, and I was suggested to wipe the drive and reinstall an operating system however he said not to nuke just yet. I asked if nuking would be just b as good if not better than wiping the hdd as it is much more thorough.

So what would be the best way to get rid of a hacker if the system was compromised? DBAN?

---

### Post by ian-weisser on 2015-10-01
> **tdvreel said:**
> So what would be the best way to get rid of a hacker if the system was compromised?

Usually, you merely reinstall to eliminate any mischief they have caused, and close any windows they may have opened.
When setting up anew, be sure to learn from whatever mistake let them in.

---

### Post by tdvreel on 2015-10-01
OK, well if the situation arises, I now have the knowledge of what to do as opposed to resorting to blind panic as I would normally do. I think I'm going to take a break from Linux for awhile, until 15.10. If that doesn't  work I'll try 16.04, and if that doesn't work I think that'll be my retirement from Linux altogether, at least until my next computer (which I hopefully will assure is Ubuntu compatible). I'm only knowledgeable in Ubuntu based distros and seeing how they are the most popular and most supported, I don't think I'll have much luck with non-Ubuntu based distros.

If anyone has a reasonable explanation for the noises or any other bug that occurred, please let me know. It'll put my mind at peace and I am greatly appreciative of that, so I'll be checking back here often. As for now, I'm going to nuke my computer and reinstall Windows, and hopefully one day Ubuntu. I know, I know, even if there isn't a hacker, there's not much harm in wiping the computer and it will put my mind at peace.

PS - this is completely off topic but I'd like to know. Are Chromebooks more compatible with Ubuntu and other distros than Windows computers? Seeing as how Chrome OS is based off Linux, I figured the hardware would be better suited than regular PCs. Remember to let me know if you know anything about the bugs or anything about the Chromebooks.

---

### Post by oldos2er on 2015-10-02
Please start a new thread for your chromebooks question.

---

