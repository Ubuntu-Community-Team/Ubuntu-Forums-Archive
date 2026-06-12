---
title: "Jaunty sucks (I'm switch back to hardy)"
date: 2009-06-03
forum: Testimonials &amp; Experiences
---

### Post by KeyserSoze93 on 2009-06-03
I am a full time Ubuntu user, and have been since October 2007. I consider myself pretty savvy with Ubuntu, and can see no reason I would stop using it in the future... What I will stop using, however, is the abysmal Ubuntu Jaunty... For some stupid reason, I decided to stop using my perfectly fine, perfectly stable Hardy install on my laptop and upgrade the damn thing the Jaunty... Why I did this, I don't know, but today or tommorow I will be doing a complete reinstall (including having to remake my home partition, since I switched it to ext4 which will not work with Hardy)

My machine: 512 MB Ram, Intel Pentium M 1.6 GHz, Dell Latitude D600, ATI graphics card.

This is why I am severely pissed off with Jaunty:

Network Manager - Wired network no longer connects, I am currently using WICD.

QEMU - New version is utter crap, and left me in a situation of not being able to do my volunteer work today, since I had to test a distro on a virtual machine, and the damn thing never booted.

Mplayer - Works, but sometimes gets strange messages about freeing IOCTL.

The main problem, though is the fact that it takes several seconds to switch between an xterm and firefox... Yes, just normal alt-tab. And no, no Compiz, I am using Fluxbox so there is absolutely no reason for the slowdown. I have just had to hard reboot my laptop out of complete disgust when switching apps got stuck in a loop where the two windows kept swapping focus and the machine wouldn't answer any keyboard or mouse control.

So, off comes my carefully customized, yet now ruined system, and my home partition, and on goes a fresh install of Hardy, which I will not be touching until atleast the next L.T.S. version.

---

### Post by philinux on 2009-06-03
Could be ati graphics related. Since I'm running nVidia I've not looked into it other than seen comments on here and in the karmic forum.

---

### Post by connorh123 on 2009-06-03
I agree Keyser. I have the same problems.
I have to put in my wireless code in order to get on the internet everytime I boot up my computer. I also have an ATI Radeon 7500.

---

### Post by XCan on 2009-06-03
Not to forget, the 'remote desktop' is a joke. No sign of intention to fix it either from the devs. But then again, have they ever fixed any bug in a release that isn't security related? ;)

---

### Post by Mirge on 2009-06-03
So, not to be rude (not my intention)... but was this just a rant about Ubuntu 9.04? Or did you actually want some help?

---

### Post by Tibuda on 2009-06-03
This is why old versions are still supported. You don't have to upgrade.

---

### Post by albinootje on 2009-06-03
> **KeyserSoze93 said:**
> 
The main problem, though is the fact that it takes several seconds to switch between an xterm and firefox... 

Problems on various ATI and Intel cards are known to happen with the newer Xorg version in Jaunty.
There are work-arounds and solutions on the net though.

I came across one (slowness) problem with an ATI card on one machine, for which I changed xorg.conf settings, but the slowness problem was reported days later on again, so I need to look at that again.
On another machine with an ATI card everything seemed to work great, until I rebooted the machine, and ever since the gdm login screen is not visible, only a messed up screen is shown.
For that I found a possible solution, but in the meantime I've switched that machine back to Hardy.

I'm also quite frustrated about the problems with ATI cards, and I'd like to have my users use newer software, and the same Ubuntu release, but I guess it needs tweaking, or... another video card :(

Your story also sounds like there's a Xorg related problem concerning your ATI card.

---

### Post by Jazzy_Jeff on 2009-06-03
Doing a clean install is usually a better option. I have had problems in the past with upgrades. But with the clean install of 9.04 everything works great. And I would not use ext4 until I know all the bugs are worked out.

---

### Post by savsav on 2009-06-03
The OP's problems are ATI related -- most likely.

I had plenty of problems with a desktop which uses an ATI card.

In fact, I eventually gave up on Ubuntu 9.04 on my desktop. I installed
Kubuntu 9.04 instead. It works perfectly.

I installed Ubuntu 9.04 on my laptop, which has an Nvidia card.
It works perfectly.

So the OP  should consider this: change to an Nvidia card. 

Nvidia just seems to work well with ubuntu -- and many other linux
distros as well.

---

### Post by Soul-Sing on 2009-06-03
```
Doing a clean install is usually a better option
```
+1

Jaunty on ext4 does rawks here....

---

### Post by andyprough on 2009-06-03
> **KeyserSoze93 said:**
>  My machine: 512 MB Ram, Intel Pentium M 1.6 GHz, Dell Latitude D600, ATI graphics card. 

That's not really enough ram to be trying to run Jaunty plus virtualization. I think you are right, you might be better running older software, that could be lighter on your memory and graphics resources. Any chance you could double the ram in that machine, and see if you could get a better performance?

---

### Post by albinootje on 2009-06-03
> **savsav said:**
> 
I had plenty of problems with a desktop which uses an ATI card.

In fact, I eventually gave up on Ubuntu 9.04 on my desktop. I installed Kubuntu 9.04 instead. It works perfectly.

Is "a desktop" the same as "my desktop" in this case ? 
If so, then that sounds like an oxymoron, or as an unrelated argument :)
> 
Nvidia just seems to work well with ubuntu -- and many other linux distros as well.

+1 Indeed. I'm very happy to use Nvidia on my desktop since years (although I don't use effects and don't play (3D) games normally).

---

### Post by Mirge on 2009-06-03
I also had some problems with freezing & usability in Ubuntu 9.04, switched to Kubuntu 9.04 and didn't look back. Zero issues so far! Oh, and I use Ext4 on all 4 comps here... no issues with that either (yet--knock on wood).

---

### Post by Bearly Able on 2009-06-03
> **savsav said:**
> 
Nvidia just seems to work well with ubuntu -- and many other linux
distros as well.

Nvidia worked just great for me under 8.04, but if I try to use the recommended driver in 9.04, I also get freezes and crashes.  I've been trying for days to find an answer to this problem, but without success. :(

---

### Post by Neobuntu on 2009-06-14
> **danielrmt said:**
> This is why old versions are still supported. You don't have to upgrade.

Well, that may be informative but it's an excuse for not building a better OS.

Plus, packages I needed were left BEHIND! They were only available in 9.04. Opps!

Currently, Kubuntu has problems with consistent stability. It seems like too many things require custom repair. While NO OS is perfect (By far), (K)Ubuntu is no longer leading. What happened?

We simply aren't going to make it into the hearts and minds of most users; when we only have some stability about 3 months after a "release".

Something at the top decision making level, has to change.

---

### Post by TrakerJon on 2009-06-14
> **Jazzy_Jeff said:**
> Doing a clean install is usually a better option. I have had problems in the past with upgrades. But with the clean install of 9.04 everything works great. And I would not use ext4 until I know all the bugs are worked out.


Give this man five gold stars for the best answer.

---

### Post by QIII on 2009-06-14
My two cents ...

I have an ATI card.  It worked absolutely fine from the start, with the exception of 3D.  I installed Catalyst 9.5 from AMD/ATI, and have had absolutely no problems whatsoever.

That said, I had bought a brand new AMD Phenom II quad core computer with 8GB of memory, installed a new drive and set up a dual boot with a fresh install of Jaunty -- an early release candidate.

Network manager is fine.  I'm using my wired network now.  Compiz works fine.  I'm running it now.  No problems with Firefox or any other application.  No problem switching between applications.

As for the developers, you all have to understand that this is not a product that has the massive resources of Redmond.  Volunteers keep this thing alive.  They cannot possibly cover every possible combination of hardware that could ever be put together.

Couple that with the fact that hardware manufacturers jealously guard their drivers and often do not make open-source versions, and you have plenty of opportunity for things not to work, despite everyone's best efforts to create a stable OS.

Your pissing and moaning does no good after the fact.  Get involved in testing and be part of the process of making things better.  If Jaunty "sucks", it's because you didn't bother to give your valuable input to those who needed it during development.  This is an ongoing community project.

---

### Post by tgalati4 on 2009-06-14
There's a reason to dual-boot:  keep your working distro and put the newer distro on a second partition or second hard disk.  When you have problems with the new distro, you can always boot back into your original distro--and not lose all of your customizations!

It's also a good excuse to get a faster/larger hard disk for the laptop.

---

### Post by HappyFeet on 2009-06-14
> **leoquant said:**
> ```
Doing a clean install is usually a better option
```
+1

Jaunty on ext4 does rawks here....

For me too. But right now I'm going to start testing Karmic and do some bug reporting. I suggest those with some free disk space and time, do the same. Let's all pitch in and help. :D

---

### Post by triswandani on 2009-07-27
Hi, I'm new here. Seems like I got somekind of solution of for this jaunty sucks. The solution is somehow simple, alsa's jaunty repository package is still in rc3, so I want to tell the problem I managed to solved too.

I upgraded from intrepid to jaunty, and I must admit that jaunty sucks. When I watch videos, it's just a mess. I searched forum, bloggers, bugs report, etc but I cannot find the for the stuttering in my video. I use totem and vlc. I thought this is about video so I installed something that checks my video, use several possibility from audetect to something else. It didn't work.

Then I try to listen some music, it still stuttering. I realised that somehow this isn't video related. I searched again, and found out about CPU performance that you can configure. Maybe my totem/vlc doesn't get enough resources that they should have. So I configure my CPU to be conservative at 2.1 GHz. It didn't work.

So I let go the whole video thing and focus my searched at audio. I found something that ubuntu jaunty used alsa 1.0.18rc3. This is somehow troublesome and I must check kernel version, download alsa that fits from its official website through ftp, manually install it with configure make make install, etc. I found the tutorial and used alsa* version 1.0.20. Audio works fine after I finished.

Fortunately this automatically fix the stuttering at my video too. I can somehow comfortably watch videos with my jaunty. Anyone responsible for ubuntu jaunty repositories, please update the alsa*, for ubuntu users' sake.

Thank you.

---

### Post by HappyFeet on 2009-07-27
> **triswandani said:**
> Hi, I'm new here. Seems like I got somekind of solution of for this jaunty sucks. The solution is somehow simple, alsa's jaunty repository package is still in rc3, so I want to tell the problem I managed to solved too.

I upgraded from intrepid to jaunty, and I must admit that jaunty sucks. When I watch videos, it's just a mess. I searched forum, bloggers, bugs report, etc but I cannot find the for the stuttering in my video. I use totem and vlc. I thought this is about video so I installed something that checks my video, use several possibility from audetect to something else. It didn't work.

Then I try to listen some music, it still stuttering. I realised that somehow this isn't video related. I searched again, and found out about CPU performance that you can configure. Maybe my totem/vlc doesn't get enough resources that they should have. So I configure my CPU to be conservative at 2.1 GHz. It didn't work.

So I let go the whole video thing and focus my searched at audio. I found something that ubuntu jaunty used alsa 1.0.18rc3. This is somehow troublesome and I must check kernel version, download alsa that fits from its official website through ftp, manually install it with configure make make install, etc. I found the tutorial and used alsa* version 1.0.20. Audio works fine after I finished.

Fortunately this automatically fix the stuttering at my video too. I can somehow comfortably watch videos with my jaunty. Anyone responsible for ubuntu jaunty repositories, please update the alsa*, for ubuntu users' sake.

Thank you.

If you upgraded through the update manager, then you are just begging for problems. Clean install is always best. Try it next time before you pass judgment on the next release. Upgrading on top of a previous release can cause problems for any OS, not just ubuntu.

---

### Post by Arthur_D on 2009-07-27
Then I've begged for problems several times, but not got any.
Amazing, isn't it? :D

---

### Post by HappyFeet on 2009-07-27
> **Arthur_D said:**
> Then I've begged for problems several times, but not got any.
Amazing, isn't it? :D

I realize that many people have upgraded without any problems, but on the other hand, many have also *had* problems. I choose not to take that chance.

---

### Post by Tamlynmac on 2009-07-27
> Neobuntu
Well, that may be informative but it's an excuse for not building a better OS.

Plus, packages I needed were left BEHIND! They were only available in 9.04. Opps!

Currently, Kubuntu has problems with consistent stability. It seems like too many things require custom repair. While NO OS is perfect (By far), (K)Ubuntu is no longer leading. What happened?

We simply aren't going to make it into the hearts and minds of most users; when we only have some stability about 3 months after a "release".

Something at the top decision making level, has to change. 	

The Face of Entitlement:

IMHO
It's a free OS and should you have problems using this free OS, then as HappyFeet suggests, "get involved". if one doesn't wish to be involved than I suggest using a different product. As a community we are responsibile for sharing and/or modifying our  environment. Not just ranting or complaining, but by becoming involved in problem resolution.

It's been my experience that complaining never solves anything. Problem resolution requires action and involvement. It's simple to complain, only requires a few key strokes.

Perhaps, all of us should heed the wisdom of HappyFeet:
> For me too. But right now I'm going to start testing Karmic and do some bug reporting. I suggest those with some free disk space and time, do the same. Let's all pitch in and help. :grin:
Step up and get involved. If it's a community, then any failure is the result of the community, not just so called decision makers. IMO blaming others rarely if ever solves anything. By sharing the responsibility, we could all make a difference. :-k

*This is not meant to be offensive, only my interruption of the situation. As in my $0.02.

---

### Post by Arthur_D on 2009-07-27
> **HappyFeet said:**
> I realize that many people have upgraded without any problems, but on the other hand, many have also *had* problems. I choose not to take that chance.
Don't see how it's better to assume something will go wrong, instead of trying, and then reinstall if necessary.
But yeah, I know you probably didn't mean it that way. :)

---

### Post by cariboo on 2009-07-27
I suggest that anyone planning on upgrading, read the release notes first. That way there are no surprises.

---

### Post by HappyFeet on 2009-07-28
> **Arthur_D said:**
> Don't see how it's better to assume something will go wrong, instead of trying, and then reinstall if necessary.
But yeah, I know you probably didn't mean it that way. :)

*I* have always preferred clean installs no matter what OS I was using. There is something reassuring to me, knowing it is clean and fresh, and free of cruft. And possibly less than desirable config files. But that's just *me*, do what *you* want.

---

### Post by Lavaeagle on 2009-07-28
> **danielrmt said:**
> This is why old versions are still supported. You don't have to upgrade.

I would suggest Newegg.com to be the next website in your mind to visit as it sounds like you're computer can't handle jaunty.

---

### Post by Tamlynmac on 2009-07-28
> happyfeet
but that's just *me*, do what *you* want. 	

+1

---

### Post by Michl on 2009-07-29
> **QIII said:**
> My two cents ...
Your pissing and moaning does no good after the fact.  Get involved in testing and be part of the process of making things better.  If Jaunty "sucks", it's because you didn't bother to give your valuable input to those who needed it during development.  This is an ongoing community project.

Well, this is a major problem for an OS that
aims to serve ordinary users.  A consequence
of your suggestion is that ubuntu is only for
computer hobbyists and professionals.  Certainly
that's not the message canonical is sending on
ubuntu.com.  I'd say your snide comments are
even less helpful.

---

### Post by Grenage on 2009-07-29
Less helpful perhaps, but apt none the less.

---

### Post by magmon on 2009-07-29
I couldn't get wireless working at all after a fresh install, I think I'll upgrade just to see what happens though lol. I agree that 9.04 sucks at the moment, maybe an update will be released in the near future that will fix these problems, but for the moment, it seems that 9.04 is totally useless.

---

### Post by HappyFeet on 2009-07-29
> **magmon said:**
> it seems that 9.04 is totally useless.

For *you*. Please emphasize that in the future. Not everyone feels that way.

"it seems that 9.04 is totally useless *for me*" That will keep people from thinking you're a troll. Thank you.

---

### Post by Maheriano on 2009-07-29
I was wondering why it took so long to switch to a Firefox window and now I have found my answer. Thank you random complainer on the internet!

---

### Post by Tamlynmac on 2009-07-29
> Michl
Well, this is a major problem for an OS that
aims to serve ordinary users.  A consequence
of your suggestion is that ubuntu is only for
computer hobbyists and professionals.  Certainly
that's not the message canonical is sending on
ubuntu.com.  I'd say your snide comments are
even less helpful. 	

As preferred to a message of support for whiners and complainers. Perhaps, when put in perspective the message Canoncial ia sending is one of freedom. As in free to use, modify or enhance - at your own desecration. I don't recall reading anything from Canoncial that mandates use by or targets any specific group.

Your suggestion that **QIII**'s statements insinuate Ubuntu is for hobbyist and pros is misguided (IMO). I believe the response is intended to point out the obvious option of becoming involved, rather than simply complaining. Multiple options are available (example: use of a different OS) and should one decide to not participate, those options can easily be implemented.

**QIII**'s opinion is reasonable and to some extent logical. IMHO, if one chooses to use Ubuntu without becoming involved, then one should not complain. Only through involvement can one influence change or impact outcome. Complaining rarely solves anything, only when we take some form of action does resolution become an option. Some may argue that complaining is an action - I would disagree. Complaining, reeks of entitlement and places emphasis on others to resolve the issue at no cost (monetary or effort) to the complainer. As in a lack of responsibility. The complainer distances themselves from issue resolution while at the same time using words to imply dissatisfaction, based on usage of the free product.

Instead of attempting to interrupt Canoncial's messages, logic might suggest we make a concerted effort (as a community) to actively participate in issue resolution, rather than simply whine & complain. IMHO we all have the mandate of participating in issue resolution, should we choose continued use of the free OS. If some would invest half the energy in issue resolution as they do in complaining, it's reasonable to assume that fewer issues would exist.

By installing 9.04 (newest version) one must expect some bugs and issues. Should you not choose to participate in issue resolution, then it's only logical one remain in an LTS environment and not accept updates without understanding what said updates modify. By installing 9.04 one should understand that this is the most recently available release and as with any new release of software - issues are probable. If one desires a long term extremely stable platform, then logic suggests one doesn't install the newest release of anything.

I have no idea what an "ordinary user" is. It's been my experience that users differ significantly and many have different computing objectives. Defining ordinary users may be complicated as the term "average user" means little to individuals that don't fit in the curve. Internet browsing, e-mail, etc. are actions most of us share. However, computing requirements may vary significantly beyond the scope of basic usage. Perhaps, you might define your interruption of who the "ordinary user" represents and what their requirements are beyond the scope of basic usage. For example, small business owners that use Ubuntu/Linux or student that prepare term papers, etc. I've always been interested in the term "average (ordinary) user" as defined by others. Is your definition of the  "ordinary user" based solely on your own personal experiences or on the opinions of others? Is it supported by quantitative data or is it simply an opinion? I'm not being sarcastic, I'm truly interested in how others use this term in support of their arguments and if they have actually investigated said term, as it applies to their arguments.

Just my $0.02

---

### Post by Michel1 on 2009-09-18
Jaunty is not a perfect system when it comes to remote connections and hardware handling.I switched from windows to Ubuntu four years ago and right now I'm ready to go back to Xp. With jaunty ,nothing is simple and the forum are just full of smart asses that most of the time don't or do understand (but don't really share)  what they are doing.I think i will wait for 9.10 but this will be my last shot. Hardy was way better than jaunty.Now I,m afraid that  the incoming 9.10 will look like Jaunty. Linux has to be more open minded to become a major operating system. Free is great,  so is profit. Nothing is wrong with non free softwares when they don't imply a monetary participation from the user.

---

### Post by SeePU on 2009-09-18
> **KeyserSoze93 said:**
> 

My machine: 512 MB Ram, Intel Pentium M 1.6 GHz, Dell Latitude D600, ATI graphics card.

This is why I am severely pissed off with Jaunty:

Network Manager - Wired network no longer connects, I am currently using WICD.

QEMU - New version is utter crap, and left me in a situation of not being able to do my volunteer work today, since I had to test a distro on a virtual machine, and the damn thing never booted.

Try Karmic then.  I bet you can boot but it soon crashes.  Try to start Firefox and watch the entire system freeze!  Is your ATI graphics the Radeon Mobility 9000 or 9600?   I have the 9000 in my Thinkpad T41 and the Karmic 9.10 Live Cd is unusable.  Oddly enough, Jaunty boots up fine and I could install it.  I might...

---

