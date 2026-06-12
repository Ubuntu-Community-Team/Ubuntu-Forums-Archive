---
title: "Bugging out over QA tracker failure &amp; ubiquity changes!"
date: 2012-09-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-04
I feel like I'm fighting a losing battle!

I try to report one of many bugs at the QA tracker but when I click on the test case to report results I first get the directions of how to test:

[http://iso.qa.ubuntu.com/qatracker/milestones/232/builds/22474/testcases/1302/results](http://iso.qa.ubuntu.com/qatracker/milestones/232/builds/22474/testcases/1302/results)

This has to be a joke, eh?

Test just my way, not your way, we don't care about actual results do we?

Think about this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

Why was it so hard to bust? Because devs test almost entirely in a VM:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418/comments/11](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418/comments/11)

What we need is more people testing on bare metal, but instead we have people changing the QA tracker in the middle of huge changes ](*,)

My testing ability is already cut in half because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

So sure this would be an excellent time to change things :mad:

Never mind that we're dealing with a major change in installation, and the expected bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045944](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045944)

I feel like I'm in the back of a bus with a bus driver that has no freaking idea where he's going and since I'm in the back I'm the last person he listens to ](*,)

There does come a point when enough is enough. I'm there!

It's time for a new generation of testers to take over!

---

### Post by mc4man on 2012-09-04
I think MS or whoever should take some funds & buy some of the key dev's a selection of various new & somewhat used hardware
(if they'd bother to use it

---

### Post by ventrical on 2012-09-04
I have 10 hard machines, No VMs. 7 towers and 3 laptops. (one tablet - don't count)

I can identify with kansasnoob and all.  I get frustrated too. However, breakage is part of the reason why I beta test. As for the q&a tracker.  I try when I can , when I have spare time. Otherwise I just post up bugs here as best as I can. When Ubiquity and the dailys are not working , I have to tell myself to move past it and work on a good install , take a break, and then go back to the busted install and try to look at the problem anew.

---

### Post by kansasnoob on 2012-09-05
Eh, I shouldn't get so miffed :redface:

The straw that really broke the camels back for me yesterday was opening the Ubuntu testcases and seeing that the page display had changed. Maybe it's unintentional breakage, I dunno :confused:

I first began to notice the new ubiquity bugs while testing Lubuntu but needed to cross-test Ubuntu to be sure it wasn't just an Lubuntu problem. Having only one machine to test with due to that xorg bug certainly makes things a lot tougher too :(

---

### Post by smartboyhw on 2012-09-05
> **kansasnoob said:**
> I feel like I'm fighting a losing battle!

I try to report one of many bugs at the QA tracker but when I click on the test case to report results I first get the directions of how to test:

[http://iso.qa.ubuntu.com/qatracker/milestones/232/builds/22474/testcases/1302/results](http://iso.qa.ubuntu.com/qatracker/milestones/232/builds/22474/testcases/1302/results)

This has to be a joke, eh?

Test just my way, not your way, we don't care about actual results do we?

Think about this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

Why was it so hard to bust? Because devs test almost entirely in a VM:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418/comments/11](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418/comments/11)

What we need is more people testing on bare metal, but instead we have people changing the QA tracker in the middle of huge changes ](*,)

My testing ability is already cut in half because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

So sure this would be an excellent time to change things :mad:

Never mind that we're dealing with a major change in installation, and the expected bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045944](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045944)

I feel like I'm in the back of a bus with a bus driver that has no freaking idea where he's going and since I'm in the back I'm the last person he listens to ](*,)

There does come a point when enough is enough. I'm there!

It's time for a new generation of testers to take over!

What?

1. You think that using the default instructions in the ISO QA Tracker is bad. I cannot agree, since there are actually people taking care of the testcases. There is a Ubuntu Testcase Admins Team formed by guitara (Nicholas Skaggs) with 6 people (including me) in there. We do spend time on working on those testcases. Also, really, we just want to unify it. Since if everyone has his or her own way then how can we know the way you test it to see if the result is a pass or a failure.

2. Sure, you can use real machines, I do encourage it. But then most of us ARE volunteers remember? And we just can't spend too many disk space or go to buy MANY computers just for testing. I only have ONE computer to do testing (since I'm 14), but then I do all my Ubuntu and Ubuntu Studio Testing work in there with a VM. So if you have enough machines use the real ones to test, but for some of us it is just VM.

3. New generation of testers. Hmm, I'm 14, so I think I can be counted in too.

So well actually your complaint applies to your world, but not others world.

Regards,
smartboyhw (Howard Chan)
Ubuntu Studio Team Member, Ubuntu Testcase Admins Team Member, Ubuntu Testing Team Member

---

### Post by arpanaut on 2012-09-05
@kansasnoob, thanks for your contribution over the years!
I hope your health continues to improve!

Remember that this is voluntary work, not obligatory...
Hope to see your continued participation in the future.
Honestly, You inspire me to do more for the cause.

Thank You!

---

### Post by ventrical on 2012-09-05
> **kansasnoob said:**
> Eh, I shouldn't get so miffed :redface:

The straw that really broke the camels back for me yesterday was opening the Ubuntu testcases and seeing that the page display had changed. Maybe it's unintentional breakage, I dunno :confused:

I first began to notice the new ubiquity bugs while testing Lubuntu but needed to cross-test Ubuntu to be sure it wasn't just an Lubuntu problem. Having only one machine to test with due to that xorg bug certainly makes things a lot tougher too :(


 I have to admit that I haven't done a zsync for about 3 days. But thats OK. I do not feel behind in my testing work.  Of course the past state of the dailys has been a mess and not much to talk about.  If the q&a testing team wants to do controlled testing in a VM then  there is not too much we can do about that. I just keep reporting. There are others here who are lurking and watching and reading and gleaning our reportage.  The down side of VM test reoporting is, is that  process of a Turing machine does not have the ability to conceptualize, never will.  Thats why we need real-time human content - to better understand and locate bugs. I think the work done here at ubuntuforums is  more valuable than what the trackers can produce. No offence to Nick's fine work and the q&a helm. Writing our bugs  out ina  sort of psudo_code helps better to understand and formulate  a flowchart, better enabling a programmer to identify the subroutine where the bug may lie as oppossed to scratching hex_code from a debugging utility.

  Quantal .iso Alpha 2 stage was just great, then , shortly after alpha 3  the stuff hit the fan so to speak.  I keep an eye on the regular contributors here and I have  learned when to "DUCK" :)

  Fortunately for me  I am surrounded by various hardware resources of all types and at no cost  (because I repair busted  MS installs) so I have a well of hdds and mobos.  But I pay a price also, in bandwidth downloading .isos and time at the keyboard.  For me , computers  and electronics has been a life's work so some of the stuff just comes naturally. 

  I really enjoy beta testing  Ubuntu. There is a certain freedom.  In fact there is a lot of freedom.  Mabey you could keep your eyes open for a secondary PC. Sort of put out the news that your looking for another one in your local area.

  Also , I agree with others here .. that we all need to take a break once in a while and come up for air.

---

### Post by ronacc on 2012-09-05
@kansasnoob I add my thanks for all your hard work , when they manage to run off an insightful  and dedicated tester like you it is not a good sign for Ubuntu . Best wishes for continued improvement of your health .

---

### Post by jerrylamos on 2012-09-05
From time to time over the years I do entries on QA tracker.  I never got any feedback on what good that was, or for that matter what development does with QA tracker if anything.

Six years of running new unstable ubuntu's the most I've seen from development is on some launchpad bugs.  Yes I get the ubuntu announcements and do browse Planet, Muktware, etc.

Ubiquity/Ubuntu/Unity changes I have no idea what development uses for user feedback and market direction.  Ubuntu is trying to use unity to gain market share vs. Android, Apple, Microsoft, Mint, ...  Personally I'm not impressed with Android so far.

You would think for valuable feedback from new ubuntu changes that install would be rock solid so that unity or whatever changes could be exposed.

Install seems to be far far down the priority list...the latest iso ubiquity is busted again, screen support very flaky, crashes when I select a partition.  Plus live/ubiquity won't connect with my wireless WPA so apport can't report the launchpad bug.  Oh, well, might get fixed, might not, I've an updated back level that still works.

Biggest reason I still use ubuntu with some desktop or other is the forums like this one where we help each other out.  Next best forum set to me is Raspberry Pi.

---

### Post by kansasnoob on 2012-09-05
> **ronacc said:**
> @kansasnoob I add my thanks for all your hard work , when they manage to run off an insightful  and dedicated tester like you it is not a good sign for Ubuntu . Best wishes for continued improvement of your health .

Health and ability are the big thing here ;)

I very much want to test ubiquity changes. 

Why?

Well, I'd tinkered with Linux beginning with [Lindows]("http://en.wikipedia.org/wiki/Microsoft_v._Lindows") but I fell in love with Ubuntu Gutsy!

Everything was simple, including installation! I'm a real dummy but I could just understand what was going to happen!

I really want everyone to fall in love with Ubuntu like I did, but if the installation eats your data you're likely to never return :(

Unfortunately I'm running out of gas due to age and health issues. That's OK on a personal level because we do all wear out at some point, but I want to be sure there are others in line to keep the installer devs (and the design team) in line :)

---

### Post by Stinger on 2012-09-05
> **kansasnoob said:**
> 
Unfortunately I'm running out of gas due to age and health
Sorry to hear that mate.
But you're right, "we do all wear out at some point".

It's quite ok with me to let out steam now and then, I do it a bit myself when the frustrations get to big.
I think of it as a sign of health, and that you are still alive and kicking ;)

We can not all be as smart as smartboy [-X
Cheers !

---

### Post by smartboyhw on 2012-09-05
> **Stinger said:**
> Sorry to hear that mate.
But you're right, "we do all wear out at some point".

It's quite ok with me to let out steam now and then, I do it a bit myself when the frustrations get to big.
I think of it as a sign of health, and that you are still alive and kicking ;)

We can not all be as smart as smartboy [-X
Cheers !

Well, anyway, back to the thread topic (name) I think.

Sure ubiquity will be experiencing bugs, since KVM and Install encrpytion and that sort of thing...I do get Ubuntu Studio builds failing to install...

---

### Post by cariboo on 2012-09-05
kansasnoob, thanks for all your hard work, and I hope you keep up some of the other projects you are involved with, 

Your work has improved ubiquity over the years, and we would be in much a worse state without you.

---

### Post by cortman on 2012-09-05
Just put in my word of thanks here too for all that kansasnoob has done for the forums and Ubuntu in general.
Keep a-going! I second Stinger's words. :)

---

### Post by kansasnoob on 2012-09-05
> **cariboo907 said:**
> kansasnoob, thanks for all your hard work, and I hope you keep up some of the other projects you are involved with, 

Your work has improved ubiquity over the years, and we would be in much a worse state without you.

Hells bells, I can't quit:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/8](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/8)

Some day I'll just poop my pants and fall face first into the keyboard ;)

As I do so I'll be cussing the design team :lolflag:

---

### Post by kansasnoob on 2012-09-05
I got scolded:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

Not sure if it was for too many CAPS or for saying, "IMHO Beta 1 should be held until the installer devs kick the living crap out of some stupid designers", or maybe, "I'd almost think the design team has been infiltrated by Win saboteurs".

Sadly I meant every word of it.

---

### Post by jerrylamos on 2012-09-05
> **kansasnoob said:**
> I got scolded:Ubuntu COC.  Do not comment on Ubuntu's decisions.  Only problem we have is finding out which decisions they care about and which just happened and they are not excited about.

Good luck.

---

### Post by ronacc on 2012-09-05
> **kansasnoob said:**
> I got scolded:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

Not sure if it was for too many CAPS or for saying, "IMHO Beta 1 should be held until the installer devs kick the living crap out of some stupid designers", or maybe, "I'd almost think the design team has been infiltrated by Win saboteurs".

Sadly I meant every word of it.

don't feel bad , consider it a merit badge , atleast they looked at your bug . several of mine this go around were rejected by the ( expletive deleted ) bot because apport itself was broken .

---

### Post by cariboo on 2012-09-05
> **jerrylamos said:**
> Ubuntu COC.  Do not comment on Ubuntu's decisions.  Only problem we have is finding out which decisions they care about and which just happened and they are not excited about.

Good luck.

**[offtopic] **jerrylamos, you see to blissfully unaware of the Ubuntu and Forum code of conduct, you can read the Ubuntu Code of Conduct [here]("http://www.ubuntu.com/project/about-ubuntu/conduct") and the Forum Code of Conduct [here]("http://ubuntuforums.org/index.php?page=policy")**[/offtopic]**

---

### Post by ronacc on 2012-09-05
> **cariboo907 said:**
> **[offtopic] **jerrylamos, you see to blissfully unaware of the Ubuntu and Forum code of conduct, you can read the Ubuntu Code of Conduct [here]("http://www.ubuntu.com/project/about-ubuntu/conduct") and the Forum Code of Conduct [here]("http://ubuntuforums.org/index.php?page=policy")**[/offtopic]**

it sometimes seems to us here in the hinterlands to be applied rather capriciously .

---

### Post by effenberg0x0 on 2012-09-05
I admit I hadn't read the CoC in years and only took some time to read it after Cariboo's post above (thanks!). When I read the first paragraph, it struck me that some developers are not following the CoC. Here's the paragraph I am talking about:

> Be considerate. Our work will be used by other people, and we in turn will depend on the work of others. Any decision we take will affect users and colleagues, and we should take those consequences into account when making decisions. Ubuntu has millions of users and thousands of contributors. Even if it's not obvious at the time, our contributions to Ubuntu will impact the work of others. For example, changes to code, infrastructure, policy, documentation, and translations during a release may negatively impact others' work.

Suppose I wanted to report some developers for breaking the CoC in the following events (just the examples that come to mind now):

- Pushing the current xserver from proposed to main, knowing it would break testers/early adopters installs (those with nvidia cards), thus halting testing. Just because;
- Dropping the alternate installer, which is considered by many as the only option to successfully install Ubuntu, without carefully investigating the situation.
 
Would you say I'm correct in reporting this? Who would I report it to? And what results should I expect (What happens when someones breaks the CoC and is reported? Does anything positive come out of it?)

Regards,
Effenberg

EDIT: How would a group of people collectively report CoC infringement?

---

### Post by mc4man on 2012-09-06
> **effenberg0x0 said:**
> 
- Pushing the current xserver from proposed to main, knowing it would break testers/early adopters installs (those with nvidia cards), thus halting testing. Just because;
- Dropping the alternate installer, which is considered by many as the only option to successfully install Ubuntu, without carefully investigating the situation.
 

Take this as you may - 
As far as the xserver/nvidia break - I actually 'read' it as there was surprise to the break, as in unexpected by those involved in that area.
If so then don't know what to make of that.

As far as the alt drop - that seemed to be planned on, just a matter of when. If it doesn't disappear shortly then possibly some of the concerns took hold. It does seem there has been a fair amount of investigating the situation though the user who can't get the live image to work is low on the pole, a bit plain jane I guess

(I do think that at times the very technically talented somehow miss the simple views

---

### Post by kansasnoob on 2012-09-06
> **effenberg0x0 said:**
> I admit I hadn't read the CoC in years and only took some time to read it after Cariboo's post above (thanks!). When I read the first paragraph, it struck me that some developers are not following the CoC. Here's the paragraph I am talking about:



Suppose I wanted to report some developers for breaking the CoC in the following events (just the examples that come to mind now):

- Pushing the current xserver from proposed to main, knowing it would break testers/early adopters installs (those with nvidia cards), thus halting testing. Just because;
- Dropping the alternate installer, which is considered by many as the only option to successfully install Ubuntu, without carefully investigating the situation.
 
Would you say I'm correct in reporting this? Who would I report it to? And what results should I expect (What happens when someones breaks the CoC and is reported? Does anything positive come out of it?)

Regards,
Effenberg

EDIT: How would a group of people collectively report CoC infringement?

Something I've noticed regarding ubiquity is that every time I struggle with "big" changes the standard reply is something like, "but that's what the new design spec calls for". Now compare the new "spec" to the "old" Precise version:

[ATTACH]223735[/ATTACH]

I suppose that just adding tool-tips to the "-", "+", and "gears" is one way of dealing with that, but what value did that change add?

IMHO if a change adds no value then it truly is just "change for change' sake".

I can very much imagine someone just clicking on "-" thinking it may shrink the selected partition but it actually deletes the selected partition w/o further warning.

Additionally the dialogue box that opens when clicking on the "gears" always says "Create partition" even if your intention is to only edit the existing partition. How confusing will that be for those intending to reuse an existing "/home"?

At least they're fixing this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1046175](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1046175)

BTW that earlier duplicate was my report, the one where my brain exploded when I noticed the QA tracker pages had changed mid-stream :(

---

### Post by effenberg0x0 on 2012-09-06
> **mc4man said:**
> Take this as you may - 
As far as the xserver/nvidia break - I actually 'read' it as there was surprise to the break, as in unexpected by those involved in that area.
If so then don't know what to make of that.

As far as the alt drop - that seemed to be planned on, just a matter of when. If it doesn't disappear shortly then possibly some of the concerns took hold. It does seem there has been a fair amount of investigating the situation though the user who can't get the live image to work is low on the pole, a bit plain jane I guess

(I do think that at times the very technically talented somehow miss the simple views

I think you may be right mc4man. But, at any rate, don't you feel like the examples I mentioned are infringements of the CoC, according to the paragraph I quoted and despite any possible interpretations? The only way I can believe in the CoC is if it's valid for everyone involved in Ubuntu: us, ordinary users and developers. Now, if everyone works according to the CoC except developers, than we have a much bigger problem in Ubuntu. I don't wanna create more problems, I know this is a dense topic. But if the CoC was made to protect Ubuntu,  we think things are going a little insane lately and we want to play by the rules, wouldn't a CoC infringement report be the the proper thing to do to get things back on a sane track and protect Ubuntu?

Regards,
Effenberg

---

### Post by Elfy on 2012-09-06
> **effenberg0x0 said:**
> ...

EDIT: How would a group of people collectively report CoC infringement?

I suspect that you'd not get far with it, however, the place to do so is

[https://wiki.ubuntu.com/CommunityCouncilAgenda](https://wiki.ubuntu.com/CommunityCouncilAgenda)


> 
The council is also responsible for the Code of Conduct and tasked with ensuring that community members follow its guidelines.

[http://www.ubuntu.com/project/about-ubuntu/governance](http://www.ubuntu.com/project/about-ubuntu/governance)

As you are ok with IRC - you might be better in the first instance trying to get hold of CC members, or even Jono,  on #ubuntu-community-team

---

### Post by kansasnoob on 2012-09-06
> **effenberg0x0 said:**
> I admit I hadn't read the CoC in years and only took some time to read it after Cariboo's post above (thanks!). When I read the first paragraph, it struck me that some developers are not following the CoC. Here's the paragraph I am talking about:



Suppose I wanted to report some developers for breaking the CoC in the following events (just the examples that come to mind now):

- Pushing the current xserver from proposed to main, knowing it would break testers/early adopters installs (those with nvidia cards), thus halting testing. Just because;
- Dropping the alternate installer, which is considered by many as the only option to successfully install Ubuntu, without carefully investigating the situation.
 
Would you say I'm correct in reporting this? Who would I report it to? And what results should I expect (What happens when someones breaks the CoC and is reported? Does anything positive come out of it?)

Regards,
Effenberg

EDIT: How would a group of people collectively report CoC infringement?

Just thinking a bit more about this while performing some additional testing :)

I really think you're onto something here. If a change appears to add no value, and by that I mean it does nothing at all to improve the related process, shouldn't there be a review process?

Replacing the simple text options in the manual installer is an excellent example of this. If a "mouse-over tool-tip" is required to explain what the widgets mean what was improved?

Certainly not all text can be removed from the installer so it's not a matter of simplifying language translations. And I seriously doubt that this was a random decision made by a rogue developer, in fact the dev involved said, "**[COLOR="Red"]per design spec[/COLOR]** all actions should appear as if they take immediate effect, but in actual fact are only executed upon clicking install.
.... but currently they are actually executed straight away with a delay. I will see if we can bring back tooltips or labels."

Since we're talking about the installation process I heard the same thing about eliminating the "use largest continuous free space" as an option when ubiquity was reworked in the Maverick dev cycle. It was stated that, "this option is seldom used" (paraphrasing but I'll be glad to pull up the actual quote and source), but that was NOT true!

I should also point out that the "use largest continuous free space" option does still exist in the alternate images which will soon no longer be available to Ubuntu users. So it's reasonable to think that a bug should be raised on that issue alone ;)

IMHO it seems like only the devs and us simple-minded end users/testers are held to the the CoC, but the designers get a pass. Don't get me wrong here, I'm not complaining about DE usability issues!

If I install a distro and simply hate it that's cool! But if I lose data (or an existing OS) during the installation process that's a big deal :mad:

I'll grant you it never happens to me personally because I've been playing with multi-boots for a very long time, but we do need to consider the first time, fresh out of the gate users!

So I violated the CoC:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/8](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/8)

But I just know that this is a huge mistake! **Not all end users are going to know that "-" means Delete!**

I'm going to list some "lost OS/data" bug links here for my own (or others) use:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

There are others but my "housekeeping" ain't that good, so I need to try and remember how I bookmarked things ;)

---

### Post by Stinger on 2012-09-06
I understand why there must be a COC and that we as testers and bug hunters must respect it( never signed it thoug ;) ).

But when you are continuously hitting a brick wall, that be:

[LIST]
[*]No action is taken when you report a bug ](*,)

[*]The dev's are playing ping pong with your report, sending it back and forth between various branches. ](*,)

[*]Or worse just marking it as invalid because it does'nt fit the design. ](*,)

[*]Me trying to get a complete upstream Gnome 3.6 experience in GNObuntu ](*,)
[/LIST]
You should be allowed to exercise your 'steam vent' to get the developers attention ( without getting mean or vicious ), 
and judging from your ['comment #8']("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/8") _they do actually allow it_, else I think the comment would have been deleted. :D

---

### Post by ventrical on 2012-09-06
> **effenberg0x0 said:**
> I think you may be right mc4man. But, at any rate, don't you feel like the examples I mentioned are infringements of the CoC, according to the paragraph I quoted and despite any possible interpretations? The only way I can believe in the CoC is if it's valid for everyone involved in Ubuntu: us, ordinary users and developers. Now, if everyone works according to the CoC except developers, than we have a much bigger problem in Ubuntu. I don't wanna create more problems, I know this is a dense topic. But if the CoC was made to protect Ubuntu,  we think things are going a little insane lately and we want to play by the rules, wouldn't a CoC infringement report be the the proper thing to do to get things back on a sane track and protect Ubuntu?

Regards,
Effenberg

 @effenberg,

 Al, You have my vote on this (if needed). Keep in mind though that I am not a member or staff, just regular user.   If I may offer  some words of calm- During my BBS/Fidonet career from 1990 on I had to learn to  shoulder stuff from the 'stuffs'.  It's just the way it was then (and perhaps is still the way it is now). Requesting some type of discipline for the offending 'devs' (or internal review) may make the chasm even wider between them and  the testing community. However, experience has shown that cooler heads will prevail.  I'm going to wear it for now and see what happens down the road. Just speaking from my own view I think that our power of example of being broad shouldered on this issue will go along way. Isn't that the Ubuntu way?

---

### Post by effenberg0x0 on 2012-09-06
> **ventrical said:**
> @effenberg,

 Al, You have my vote on this (if needed). Keep in mind though that I am not a member or staff, just regular user.   If I may offer  some words of calm- During my BBS/Fidonet career from 1990 on I had to learn to  shoulder stuff from the 'stuffs'.  It's just the way it was then (and perhaps is still the way it is now). Requesting some type of discipline for the offending 'devs' (or internal review) may make the chasm even wider between them and  the testing community. However, experience has shown that cooler heads will prevail.  I'm going to wear it for now and see what happens down the road. Just speaking from my own view I think that our power of example of being broad shouldered on this issue will go along way. Isn't that the Ubuntu way?

Thanks Dale :)
I may have confused people. I do not want to start a war and create a  testers vs devs situation. THat would be counterproductive. I'm thinking about the problems we had this cycle and the problems we had in the past. About all the fuzz when we embraced Unity, when we dropped 2D, current changes, etc. The conclusion I am getting to is that devs are actually *forced* to break the CoC if there's no formal/proper way/tool/process to work together with us, to spread info, plan, goals, transparently and no adequate way to communicate roadmaps to the larger community. 

More specifically: We have defended the need for better communication between testers and devs. We have asked many times to be heard, for our opinions to matter in the future of the OS. We don't know if they read our reports, if they even consider our opinions as valid. In a project as large as Ubuntu, with it's many subprojects, teams, leaders, etc it is impossible and utopic to expect everyone to talk to each other - some dudes will become early adopters today,they never heard of QA or Testing, they never went to UDS and they don't know me, you or the devs. They will report bugs about design choices. We need key-information to be public, posted in a single place. Otherwise we will create bug reports about things that are not bugs but development/design choices. We will be discussing things that make no sense for developers. 

Lack of information, misinformation creates conflict. It makes us feel like we were left out of the whole process. And, from our point of view, it can be qualified as an infringement of the CoC.

Therefore, either we have proper communication channels to store and distribute information in a proper way or we must rewrite the CoC (which would be absurd). 

I am looking at our demands from the past right now and almost all of them can be translated to a single need/request. If this request is not treated as a priority, we are all infringing the CoC. 

I'm putting that in an article, with examples, and I will present that to CC/TB, etc. I think we, the devs, Ubuntu Leaders, we are all wrong. There's no good guys / bad guys. 

I'll explain it better soon... thinking about it and implications right now. As a group, we must support the need for better communication and devs-testers integration because we want to trust, support and enforce the CoC. I'm writing the spec right now :) That's what I want us as a group to support in a report to CC. 

I'm sorry, I think it makes no sense at this point, I'll come up with a document with a clear description and a way for all people interested in it to sign up to this spec, support it, get involved. I think it's huge, it may be the answer to many problems, a good step towards a better Ubuntu.

Regards,
Effenberg

---

### Post by mc4man on 2012-09-06
> **effenberg0x0 said:**
>  But, at any rate, don't you feel like the examples I mentioned are infringements of the CoC, according to the paragraph I quoted and despite any possible interpretations? 


Not really though I guess if you feel someone specific lapsed in a specific instance ...

In the case of xserver/nvidia - 
Obviously there was a significant timeframe where anyone involved with those sources could have noticed the problem prior to the packages being released & taken appropriate action.
 Why that didn't happen I've no idea so can't really say if they lapsed in responsibility they accepted (paid or volunteered) or other human factors.

On the other hand this is a dev version & contrary to what MS may say users of should have not real expectation of being protected from inconvenient or worse occurrences or be relieved from paying attention or staying informed.
So in this case it ultimately  was no big deal, some users got their installs a bit messed up, such is & there were workarounds avail. till the bug got closed.

In general though it feels like the scope of Ubuntu may have exceeded the resources to deal with in timely or more complete or at all fashion 
(also limited by the rigid release schedule

As far as the parted symbolic style icons - edit - based on a clarification on the 'issue' which is appearance not function don't see any real problem. So  went & tried & the sym icons aren't that mysterious.
If tooltips make sense then maybe they'll be added. Doesn't seem to be the huge deal made out to be

---

### Post by jerrylamos on 2012-09-06
> - Pushing the current xserver from proposed to main, knowing it would break testers/early adopters installs (those with nvidia cards), thus halting testing. Just because;
- Dropping the alternate installer, which is considered by many as the only option to successfully install Ubuntu, without carefully investigating the situation.effenberg0x0, right on - over the last 6 years many cases where key development decisions are made without paying any regard to the consequences to us users.  Somebody(s) up there have the power to push their own agenda no matter what.  I'm not talking about the guy at the top, it's some of the people underneath carrying out their own vision.

So far, after some carnage and no admission, develpment has been able to keep ubuntu going.

What we the users do not see is the market penetration ebb and flow of ubuntu vs. mint, android, apple, microsoft, etc.  This ebb and flow is strongly affected by some of the unilateral decisions.  Right now it looks like android is growing leaps and bounds.  I haven't paid enough attention to know how the android ship is guided.

Perhaps some of the decisions will be correct in the long run, who knows.

Key to me is I still have choices.  I'd like to see ubuntu do well, but if they decide to shipwreck, so be it.  Their decison.  I have choices.

Not intending to infringe on the COC, just looking at it from the sidelines.  Best I do is alert launchpad on some bugs which sometimes are acted on, frequently not.

p.s.  Of course there are some things going on behind the scenes example the "discussions" between Linus Torvalds and gnome.  There are some power struggles going on....

---

### Post by ventrical on 2012-09-06
> **mc4man said:**
> Not really though I guess if you feel someone specific lapsed in a specific instance ...

In the case of xserver/nvidia - 
Obviously there was a significant timeframe where anyone involved with those sources could have noticed the problem prior to the packages being released & taken appropriate action.
 Why that didn't happen I've no idea so can't really say if they lapsed in responsibility they accepted (paid or volunteered) or other human factors.



  From my perspective on this matter, I agree with you mac. I was well aware that updating the nvidia-current/xorg would break my system and I made a concious desision to break three installs as I was myself engaged in an experiment. It's what I do. If I stop experimenting with breakage of that sort then I might as well resign from being a beta-tester.

Thank you for your remarks.

---

### Post by ronacc on 2012-09-06
A few years ago I attended one of the UDC's that occurred in Orlando , Florida , USA where I Happen to live , and  presented some of the points that effenberg0x0 and mc4man are making  in person at one of the sessions . Mainly from the point of view that Ubuntu is largely wasting a very good resource by not fostering better communication between the testers and dev's . I was assured at that time that better communication would be encouraged . With only a couple of shining exceptions this has not happened , and some of the  problems in this cycle can be blamed directly on that lack .

---

### Post by ventrical on 2012-09-06
@effenberg

Thank-you for your reply Al. If I could add one more thing as a suggestion. I know that Canonical staff are not allowed to become Ubuntu Members/Staff. I was wondering if you could suggest , perhaps , that the Ubuntu Council members may take up the idea of  allowing a Canonical Staff  member to be an UbuntuForums member whos' responsibilities would be to act as a sort of amabassador between  developers, Canonical Staff and UbuntuForums U+1 members, staff and end_users.  This may inspire a greater sense of  work ethic and trust between all of us and could perhaps help with communications in all aspects in the near future. Nick Scaggs had tired to do this is some ways or others although I am sure he has many other duties, but , as an example of what he has tried to do with q&a and communication it in practice, then such could be done with major changes to Ubuntu Frameworks as Canonical staff may have resources more readily available to them.

Regards,

Dale

---

### Post by castrojo on 2012-09-06
> **ventrical said:**
> @effenberg

Thank-you for your reply Al. If I could add one more thing as a suggestion. I know that Canonical staff are not allowed to become Ubuntu Members/Staff.

Lots of canonical staff are members (like me!)

> Then such could be done with major changes to Ubuntu Frameworks as Canonical staff may have resources more readily available to them.


Not really, we have the same resources as everyone else. What would you recommend this person do?

---

### Post by kansasnoob on 2012-09-06
> **kansasnoob said:**
> Something I've noticed regarding ubiquity is that every time I struggle with "big" changes the standard reply is something like, "but that's what the new design spec calls for". Now compare the new "spec" to the "old" Precise version:

[ATTACH]223735[/ATTACH]

I suppose that just adding tool-tips to the "-", "+", and "gears" is one way of dealing with that, but what value did that change add?

IMHO if a change adds no value then it truly is just "change for change' sake".

I can very much imagine someone just clicking on "-" thinking it may shrink the selected partition but it actually deletes the selected partition w/o further warning.

Additionally the dialogue box that opens when clicking on the "gears" always says "Create partition" even if your intention is to only edit the existing partition. How confusing will that be for those intending to reuse an existing "/home"?

At least they're fixing this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1046175](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1046175)

BTW that earlier duplicate was my report, the one where my brain exploded when I noticed the QA tracker pages had changed mid-stream :(

Just a quick follow-up on this, specifically regarding the replacement of simple text with symbolic icons.

Dev says;

> There is no change in the actions.
Only appearance. "Add/Edit/Remove Partition" are now symbolic icons.

And:

> bug 1045799 has not been fixed and **[COLOR="Red"]requires design changes before doing so[/COLOR]**.

Re:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/11](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/11)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1046175/comments/9](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1046175/comments/9)

So, can anyone point out how that change in any way improved the installation process?

I mean "-" certainly does not always mean delete. In fact if you click on the "gears" (which means Edit or Change) the next window specifically uses + and - to describe increasing or decreasing the size of the partition. (It also now always says "Create partition" even if you're editing an existing partition).

I'd suggest that design change is a much greater breach of the CoC than my rant. I'm just a worn out old tester who lacks the ability to spend unlimited hours trying to deal with the design team :(

---

### Post by kansasnoob on 2012-09-06
Somewhat interesting:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/13](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/13)

Be sure to check the new spec. They're tossing aside the "gears" and putting back "Change", but IMHO the "-" is the most worrisome because the "-" icon is not universally used to indicate "delete". As previously pointed out, in the edit/create screen "-" is used to describe reducing the size of a partition.

But I'm just not up to the battle anymore, color me burnt out and tired. It's time to let others fight the battles now :)

---

### Post by kansasnoob on 2012-09-06
Argh, thought I already cross posted this but evidently not:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/14](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/14)

> 

First of all I want to apologize again for my previous rant, that was clearly inappropriate.

Now on to the newest UI proposal;

You've dropped the gears icon in favor of the text message "Change" but my greatest concern is "-".

The symbolic icon "-" does NOT always mean "delete". In fact when you open the "change" dialogue to apply changes to a partition "-" clearly means reducing the size of the existing partition! This is true of many apps, typically "-" means shrink, lower, or reduce!

I've followed user errors a lot at Ubuntu forums down through the years and I'll assure you that anything that's even slightly confusing will ultimately result in user error, the worst of which is the loss of data or an existing OS.

So IMO using "-" to replace "delete" is a very bad UI change/decision :^(

BTW I only included that gparted screenshot in comment #8 to prove that if the installation process is "quit" no change is actually applied, but I fear that if someone were to click on "-" not knowing that it means "delete" they'd proceed with the actual desired changes and still end up deleting a partition they'd NOT intended to :^(

I hope that's clear, I really am getting old and tired, and I've been almost begging for someone else on the end-user end of testing to jump up to the plate to replace me.


It's hard to give up on something you love ;)

---

### Post by ventrical on 2012-09-06
> **castrojo said:**
> Lots of canonical staff are members (like me!)



Not really, we have the same resources as everyone else. What would you recommend this person do?

 Ahh .. yes .. my mistake .. 

Good to see you drop in...

---

### Post by kansasnoob on 2012-09-06
Now you can see I lost this argument:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/15](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/15)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/16](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/16)

A couple of quotes worth repeating:

> Ubuntu forums is self-selective and not representative.

> This is not a discussion forum.

So where does that rate on the CoC scale :confused:

When someone reports that they accidentally deleted a partition please point to that bug report. It's obvious that we mere mortals know nothing of value.

---

### Post by kansasnoob on 2012-09-06
Does anyone else see any irony between me being told:

> This is not a discussion forum. 

And then moments later the same person adding:

> I am just a coder, mpt did the design =) I implemented it poorly first
time around.

Outside of my "rant" how exactly were the rest of my opinions/comments any less relevant than that :confused:

Talk about getting a door slammed in your face :mad:

---

### Post by mips on 2012-09-06
Erm, if it was me I would tell them where to get off and stop testing. Pretty obvious that user input is not needed, they have a design plan and that's all they are working towards.

Who do you think you are anyway!? :biggrin:

---

### Post by kansasnoob on 2012-09-06
> **mips said:**
> Erm, if it was me I would tell them where to get off and stop testing. Pretty obvious that user input is not needed, they have a design plan and that's all they are working towards.

Who do you think you are anyway!? :biggrin:

No need to tell anyone anything, just time to stop filing bug reports and even giving a crap :(

I know enough to keep my own PC's going so it's just time to retire from testing and reporting bugs.

Maybe I'll find a young distro that appreciates an old farts input.

---

### Post by rtalcott on 2012-09-06
As George Carlin said..."It's a club and you are not in it."

---

### Post by ventrical on 2012-09-06
> **castrojo said:**
> 
Not really, we have the same resources as everyone else. What would you recommend this person do?

*Be active specifically in U+1 forums on a daily or even weekly basis.
*Divulge roadmap information as to where Canonical is going with it's testing program.
*Continue to proactively share proposals for changes to Ubuntu releases during a       development cycle with the U+1 community.

 * Most importantly, a connection should be maintained with ubuntuforums and Canonical staff so that  reasonable warnings of drastic changes can  be bulleted on the forums headers (as was suggested by Caribou907 sometime back).

  For myself I am not too worried what  the developers or staff do because I have a large array of hardware to test and  there is a wealth of Ubuntu genius here that usually effects a quick cure for the most busted system, however, newcommers and potential prospects may not have the usual resources that  a die-hard beta tester may have available. You commented that you have the same resources as the rest of us do. I wonder how you authenticate that as a Canonical staff member. Do you have one machine, several machines to test , do you test at all or are you running mostly virtual machines ?   Having one , fast, current PC running mostly virtual machines cannot give real time data as to the condition of , lets say , the Ubiquity Installer..

 Ya know .. I  have to share this ..   My brother started using PCs about 5 years ago. For that amount of time he got really good at it.  I told him about Ubuntu and sent him a USB with Precise Pangolin. He finally installed it and called me today and said "Wow  ... it works  like one of those little iPhones"...

---

### Post by fjgaude on 2012-09-06
"Wow ... it works like one of those little iPhones"...

Your brother hasn't seen an Android phone yet? They outsell iPhones nearly three-to-one, at last count.

---

### Post by ventrical on 2012-09-06
> **fjgaude said:**
> "Wow ... it works like one of those little iPhones"...

Your brother hasn't seen an Android phone yet? They outsell iPhones nearly three-to-one, at last count.

Point was , he was talking about the Unity-Ubuntu-Desktop.

---

### Post by ronacc on 2012-09-06
> **fjgaude said:**
> "Wow ... it works like one of those little iPhones"...

Your brother hasn't seen an Android phone yet? They outsell iPhones nearly three-to-one, at last count.

at last count it was 2 to 1 and that is dozens of android phones against 1 Iphone .

---

### Post by castrojo on 2012-09-06
> **ventrical said:**
> *Be active specifically in U+1 forums on a daily or even weekly basis.

I read the forums at least 3-4 times a day, and I know guitara does as well, I've seen a few others here and there too.

> 
*Divulge roadmap information as to where Canonical is going with it's testing program.


Everytime there's a new thing going on with the program guitara posts a thread about it. 

> 
*Continue to proactively share proposals for changes to Ubuntu releases during a       development cycle with the U+1 community.


Ubuntu development happens on the ubuntu-devel mailing list, I don't think it's too hard to ask testers to keep an eye on that mailing list along with all the other things that is a good idea when you're testing things. It's where this sort of thing is announced, and the launchpad blueprints have been published for months now. 

> 
 * Most importantly, a connection should be maintained with ubuntuforums and Canonical staff so that  reasonable warnings of drastic changes can  be bulleted on the forums headers (as was suggested by Caribou907 sometime back). 

Again, this sort of thing is already posted on the list, I usually learn it first by reading someone posting it here. 

> Do you have one machine, several machines to test , do you test at all or are you running mostly virtual machines ?   Having one , fast, current PC running mostly virtual machines cannot give real time data as to the condition of , lets say , the Ubiquity Installer..

I have 2 PCs with 12.10, a laptop with 12.10, and a server for 12.04.1 testing. I typically don't test the installer on a regular basis as it's not my area of focus, but I usually move at least one machine over to U+1 at around Alpha 1 and then progressively add more machines to it until by beta I am running it everywhere except my server.

---

### Post by ronacc on 2012-09-06
you and  guitara  are the only ones I recall seeing regularly . and you are both appreciated .

---

### Post by ventrical on 2012-09-07
> **ronacc said:**
> you and  guitara  are the only ones I recall seeing regularly . and you are both appreciated .


 I absolutely agree.

---

### Post by ventrical on 2012-09-07
> **castrojo said:**
> I read the forums at least 3-4 times a day, and I know guitara does as well, I've seen a few others here and there too.



Everytime there's a new thing going on with the program guitara posts a thread about it. 



Ubuntu development happens on the ubuntu-devel mailing list, I don't think it's too hard to ask testers to keep an eye on that mailing list along with all the other things that is a good idea when you're testing things. It's where this sort of thing is announced, and the launchpad blueprints have been published for months now. 



Again, this sort of thing is already posted on the list, I usually learn it first by reading someone posting it here. 



I have 2 PCs with 12.10, a laptop with 12.10, and a server for 12.04.1 testing. I typically don't test the installer on a regular basis as it's not my area of focus, but I usually move at least one machine over to U+1 at around Alpha 1 and then progressively add more machines to it until by beta I am running it everywhere except my server.


Not everyone has the same resources as you. Most people here have only 1 machine to work with. That is why it is so important for *them* to have a functioning daily, err, or at least the ones who have taken up the hobby of being a beta tester. I have encouraged them to try and find a second.

Secondly , yes, I had mentioned guitaras fine work here  with q&a and other projects but when the incident happened with xserver and nvidia-current blob it seemed  that there were some aspects there where he was left out of the loop, and , subsequently, we all got left out of the loop. Perhaps then I am wrong to assume then that there was a disconnect between Canonical staff and developers and testers?

"Ubuntu development happens on the ubuntu-devel mailing list, I don't  think it's too hard to ask testers to keep an eye on that mailing list  along with all the other things that is a good idea when you're testing  things."

  We testers are asked to work with a buggy apport reporting tool that was mostly non-functional this cycle and report our bugs (those which we can) to launchpad. Some have slower PCs to work with. Othertimes apport can present some real downtime difficulties and that equals our volunteer time spent in downtime  which can diminish the whole desktop experience and equal negative productivity. Guitara has done an extremely find job at bridging the gap here but he should not carry this burden alone nor should testers of novice or intermediate stature have to have surprises come down the pipe as was with this cycle so far. I think more of  you should partake more regularily.

For example , last cycle you were very active in trying to get rid of ccsm (which did not happen) but the point was that you gave us all a unique perspective from a devlopers point of veiw. This cycle you have been sort of like a *ghost* (and I do not say that to be insultory) . I mention this because your contributions give us a unique heads up, a preview, if you will, of a shape of things to come.  So then with this added participation we can focus more on the matters of testing in an uninterupted  process.

Thank you so much for your remarks.

Regards,

Ventrical

---

### Post by jbicha on 2012-09-07
The symbolic +/-/gear are being used a lot in GNOME. Disks uses it and is a similar app to Ubiquity. System Settings uses it in Appearance, gnome-online-accounts, Bluetooth, Network, Users, etc. Consistency is nice.

Although they look similar, there is a difference in widget layout for the add/delete usage from the combobox plus/minus usage. Specifically, the plus/minus case is built in to the right hand side of a box you put numbers in. Also, I don't know if it's a big deal but the GNOME examples have the add/delete buttons in a "gutter" but not the proposed Ubiquity.

---

