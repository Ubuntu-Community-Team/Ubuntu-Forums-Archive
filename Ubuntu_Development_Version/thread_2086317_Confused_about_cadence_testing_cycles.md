---
title: "Confused about cadence testing cycles"
date: 2012-11-20
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2012-11-20
It looks like the first cycle will begin November 24th and run a full week. Is this correct?

If so are all iso/upgrade testers expected to test every day of that cycle?

Scary stuff to me as an **old** iso tester, and I might add that I'm the one that pushed for upgrade testing to be added to the testing criteria!

I know I can't maintain a test cycle like this ... I just can't! And I doubt that you'll find many independent testers that can!

But time will tell I guess ;)

---

### Post by ventrical on 2012-11-20
I am to understand (by your comment above)that the testing we are doing now is of absolutely  no use whatsoever ?

---

### Post by grahammechanical on 2012-11-20
Information in these quotes is all that I know about this subject. It might clear things up a bit.

**ISOs**

> Iso's will now be automatically 'smoke' tested before general release. No more completely broken installers on the published images! In addition, the iso's will be published daily as usual, but will not have typical milestones as mentioned above. Preference will be given to the daily iso -- the current one -- throughout the cycle. Testing will occur in a cadence instead of a milestone.

**Cadence**

> Rather than milestones, a bi-weekly cadence of testing will occur with the goal of assuring good quality throughout the release cycle. The cadence weeks will be scheduled and feature testing different pieces of ubuntu in a more focused manner. This includes things like unity, the installer, and new features landing in ubuntu, but will also be the target of feedback from the state of ubuntu quality.

**State of ubuntu Quality**

> A bold effort to generate a high level view of what needs testing and what is working well on a per image basis inside of ubuntu. This is an experimental idea whose implementation will garner feedback early in the cycle and will collect data and influence decisions for testing focus during the cycle. *fingers crossed*

[http://www.theorangenotebook.com/]("http://www.theorangenotebook.com/")

> Every 2 weeks as part of our testing cadence,, we download copies of the latest daily ISO images, burn them to CDs (or load them into VM's) and test them. This brings to light many issues that might have been missed by other early adopters and developers, especially in the CD builds and installers.

[https://wiki.ubuntu.com/Testing/Activities]("https://wiki.ubuntu.com/Testing/Activities")

As I understand things, and I am most likely wrong, we can test each image of each day of the week, starting from the Saturday. Or, we can test the image for just one day. I am hoping (no, I am expecting) that we can report our results any time during that week.

Up until now results for the testing of one daily image had to be posted before that image was superseded. Each daily image was superseded by another image every 24 hours. I do not think that this will apply during Cadence week although there will be new images every day.

Regards.

P.S. The testing that we are doing now keeps some of us from becoming brain dead. It certainly does that for me. :)

---

### Post by ventrical on 2012-11-20
> **grahammechanical said:**
> 

P.S. The testing that we are doing now keeps some of us from becoming brain dead. It certainly does that for me. :)


Very well put but I am still curious as to how our input here in U+1 forums is of any help , especially if the devs are not visiting these forums. I mean , yes , we help each other as a community however small or large but does our input have any influence on developers at large? Do we have any real influence on Canonical as a whole? And I wonder at times if there are commercial reasons for cadence testing? I know Canonical has to make money to support itself, pay it's employees and turn a profit on 'board day' but I am just concerned that the 'core' rolling system is being parried down  so that end_users will have to pay for apps and addendums if they want the "WOW" of a lickety-split Unity 3D system.

  One other commercial software OS and  a popular third party security program  which is free (supposedly)  now makes it virtually impossible to operate that program without having to bump into a reminder to "upgrade" and other bells and whistles that decieve one into thinking they are 'updating' when they are actually 'upgrading' to a trial version that will eventually ask for money after 30 days.

  Most likely my assumptions are not based on sound documentation but I often wonder why , for example, each version of the Nautilus file manager gets more and more sliced up and archaic and also what was done to Disk Usage Analyzer.  That little program was destroyed and makes absolutely no sense (to me at least) in it's present state.

 Testing kernel rcs does help keep me sane. I am thankful for that .. but .. frankly ... my thoughts are .. that with the new cadence testing .. the thrill is gone :) Gone will be the Ubuntu black-space, the lines of indecipherable code and broken systems. It will be a desert out there  and good bugs will be hard to find. Dog food will be an item of the past and overheated nVidia cards will be all but a ghost and a whisper.. perhaps leading to be one Unified Turing machine ... lol ... :)

---

### Post by zika on 2012-11-21
The Thrill Is Gone
[https://www.youtube.com/watch?v=4fk2prKnYnI](https://www.youtube.com/watch?v=4fk2prKnYnI)

---

### Post by ventrical on 2012-11-21
> **zika said:**
> The Thrill Is Gone
[https://www.youtube.com/watch?v=4fk2prKnYnI](https://www.youtube.com/watch?v=4fk2prKnYnI)

hahahaeeha .. you got it ..  :)

---

### Post by grahammechanical on 2012-11-21
@ventrical

>  Gone will be the Ubuntu black-space, the lines of indecipherable code and broken systems. It will be a desert out there and good bugs will be hard to find. Dog food will be an item of the past and overheated nVidia cards will be all but a ghost and a whisper.. perhaps leading to be one Unified Turing machine

I don't believe a word of it! Humans will always mess up. :) And so will the machines/software they make.

I do think that may be we should move further up steam in testing. I have tried to investigate testing things like Gnome, KDE and stuff like that. The problem I come up against is that those people only think of testing in terms of bug triaging and developing the software. And there is always this insistence in joining the team.

Regards.

---

### Post by Elfy on 2012-11-21
```
* elfy still doesn't understand all that cadence stuff 
<balloons> :-( I'm sorry elfy
<elfy> good job I'll be testing xubuntu 
<elfy> :)
<balloons> Well, what are you still missing?
<elfy> oh d'oh just realised I'll be doing arm as well ... lol
* cwayne (~cwayne@pool-98-118-37-160.bstnma.fios.verizon.net) has joined #ubuntu-quality
<elfy> balloons: I suspect what I am missing is the more normal term people would use :)
<balloons> elfy, sure sure
<balloons> basically we're going to have test-a-thons if you will every couple weeks
<balloons> each time we'll pick somethng else to focus on
<balloons> we'll pull the tests from the tracker and make a milestone for them and have people report on them
<elfy> ok - that makes sense :)
<balloons> so for next week I've got to pull the tests and make the milestone and announce i
<elfy> we'll not be doing that
<balloons> it's that simple
<balloons> everyone will have saturday - saturday to test and report
<elfy> well kind of we will - when we have something we need specifically testing then we'll be shouting 
<elfy> right - and then the 'other' week is not cadence testing, just normal dailies I assume 
* elfy likes the idea of that with arm 
<elfy> ty balloons :)
<balloons> the other week is an off week
<balloons> I'll be doing things like maintaining and updating tests, playing with bugs, etc, etc
<elfy> but dailies will be updated daily still?
<balloons> writing new tests
<balloons> yes dailies will update, and no one is stopping your from running them if you wish :-)
<elfy> okey doke
<balloons> our focus is just much wider than the iso's now
<elfy> yea - as it perhaps should be 
<balloons> <3
* alourie_lunch has quit (Remote host closed the connection)
<elfy> so it in effect gives people longer than a day to test - have the whole of a week to do so in 
<elfy> is that correct?
<balloons> yes, exactly
<balloons> flexibility
<balloons> we're spread out and it's so much easier for you to plan to help out at some point in 7 days, rather than 7 hours
<elfy> k - I will post that on the forum, bit of confusion I think 
* balloons hasn't been to the forum
<balloons> I've been a bit busy
<balloons> but I wanted to hop over there today
<elfy> balloons: has missed this then Confused about cadence testing cycles 
<balloons> gotcha..
<balloons> well let's try and clear everything up then
<balloons> I think it should be really understandable after our first (I hope)
<elfy> I'll just post this over there :)
```

I was a bit confused too - hope this helps a bit, bear in mind when I'm talking of we I mean Xubuntu ;)

>  If so are all iso/upgrade testers expected to test every day of that cycle?As far as I can see - it means you have a week to test in rather than a day.

---

### Post by ventrical on 2012-11-21
> **grahammechanical said:**
> @ventrical



I don't believe a word of it! Humans will always mess up. :) And so will the machines/software they make.

I do think that may be we should move further up steam in testing. I have tried to investigate testing things like Gnome, KDE and stuff like that. The problem I come up against is that those people only think of testing in terms of bug triaging and developing the software. And there is always this insistence in joining the team.

Regards.


   Yes... I see...  there is the control set of tests and then we have here; (ubuntu-forums). Here we are free to experiment and hack to our hearts content. With cadence testing the bit will be in the mouth (said with tounge in cheek) <no pun intended> :)

  I understand the demarcation line. It is a very definitive line, not imaginary. It all makes sense now. :)

Thanks

Regards...

---

### Post by ventrical on 2012-11-21
> **Elfy said:**
> [code]* elfy still doesn't understand all that cadence stuff 
<balloons> elfy, sure sure
<balloons> basically we're going to have test-a-thons if you will every couple weeks


Thanks elfy for making all of this very clear now :)

It's just amazing :)

Regards,

Ventrical

---

### Post by kansasnoob on 2012-11-21
> **Elfy said:**
> ```
* elfy still doesn't understand all that cadence stuff 
<balloons> :-( I'm sorry elfy
<elfy> good job I'll be testing xubuntu 
<elfy> :)
<balloons> Well, what are you still missing?
<elfy> oh d'oh just realised I'll be doing arm as well ... lol
* cwayne (~cwayne@pool-98-118-37-160.bstnma.fios.verizon.net) has joined #ubuntu-quality
<elfy> balloons: I suspect what I am missing is the more normal term people would use :)
<balloons> elfy, sure sure
<balloons> basically we're going to have test-a-thons if you will every couple weeks
<balloons> each time we'll pick somethng else to focus on
<balloons> we'll pull the tests from the tracker and make a milestone for them and have people report on them
<elfy> ok - that makes sense :)
<balloons> so for next week I've got to pull the tests and make the milestone and announce i
<elfy> we'll not be doing that
<balloons> it's that simple
<balloons> everyone will have saturday - saturday to test and report
<elfy> well kind of we will - when we have something we need specifically testing then we'll be shouting 
<elfy> right - and then the 'other' week is not cadence testing, just normal dailies I assume 
* elfy likes the idea of that with arm 
<elfy> ty balloons :)
<balloons> the other week is an off week
<balloons> I'll be doing things like maintaining and updating tests, playing with bugs, etc, etc
<elfy> but dailies will be updated daily still?
<balloons> writing new tests
<balloons> yes dailies will update, and no one is stopping your from running them if you wish :-)
<elfy> okey doke
<balloons> our focus is just much wider than the iso's now
<elfy> yea - as it perhaps should be 
<balloons> <3
* alourie_lunch has quit (Remote host closed the connection)
<elfy> so it in effect gives people longer than a day to test - have the whole of a week to do so in 
<elfy> is that correct?
<balloons> yes, exactly
<balloons> flexibility
<balloons> we're spread out and it's so much easier for you to plan to help out at some point in 7 days, rather than 7 hours
<elfy> k - I will post that on the forum, bit of confusion I think 
* balloons hasn't been to the forum
<balloons> I've been a bit busy
<balloons> but I wanted to hop over there today
<elfy> balloons: has missed this then Confused about cadence testing cycles 
<balloons> gotcha..
<balloons> well let's try and clear everything up then
<balloons> I think it should be really understandable after our first (I hope)
<elfy> I'll just post this over there :)
```

I was a bit confused too - hope this helps a bit, bear in mind when I'm talking of we I mean Xubuntu ;)

As far as I can see - it means you have a week to test in rather than a day.

I'll be testing Lubuntu here, not because I hate Unity, but I maintain over 20 PC's with P4M800 graphics that simply won't run either Compiz or Mutter in an acceptable manner :(

But I've been iso/upgrade testing since Hardy or Intrepid and I really don't get this change :confused:

When I started we'd typically have 3 or 4 days (generally about Monday thru Thursday) to test before each point-release and you could depend on the devs to fix any critical bugs, or at least set a target to have the bug fixed.

And the alphas were typically about 4 weeks apart, while the betas were closer together, and we'd generally even have an RC about a week before final. IMHO things have continued to go downhill ever since they dropped the RC.

Anyway it now sounds to me like no images will be frozen and they want testers to test each test case every day, seven days straight, every other week :eek:

Before I retired I worked in manufacturing engineering and I worked closely with the QA team to achieve ISO 9000 certification and I very strongly feel that this newest plan is an excellent example of letting the inmates run the asylum.

Or maybe Canonical wants to move all testing to "internal automated VM" which will mean even less testing on actual hardware ........... I don't know :confused:

I hope I'm wrong, maybe this will work out great ;)

---

### Post by kansasnoob on 2012-11-26
OK, this notification clears up a lot of my confusion:

> Ok, so we're a bit delayed in starting this because, well, there was a Holiday in North America called Thanksgiving. Forgive me. :-p

So, this week (through Saturday) is our first cadence week. What that means is we will be focusing testing specific packages (or isos) during the week. **What you can do to help is to run through a testcase (or a few :-) ) [COLOR="Red"]at some point during the next week[/COLOR] and report your results. The goal here is NOT to make all the tests green everyday.** Instead, we want to test on a deeper level and really look for bugs in the software (or even the testcases :-) ) so we can be confident in the health of the package(s) we are testing. To that end, there is no daily target -- rather we want to test through Saturday (whenever that is in your localtime ;-) ). Think quality, not quantity (I know, it's a bad pun.. quality quality...)

What this means practically is during the next week, try to execute some testcases for our week 1 targets (which are libreoffice, unity autopilot tests and the daily raring iso). You can find the wiki page detailing this here:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring/Week1](https://wiki.ubuntu.com/QATeam/Cadence/Raring/Week1)

The master schedule can be found here:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring](https://wiki.ubuntu.com/QATeam/Cadence/Raring)

Again, **[COLOR="Red"]I would suggest finding a day and time that works for you and adding your results[/COLOR]**. Feel free to use IRC (#ubuntu-quality on freenode) or this mailing list to discuss any bugs you may find. At the end of the week, I'll recap what we did (bugs, tests ran, etc), and we can evaluate the results to see if further followup and focus is needed or not. Now, our testing focus's each week will change in order to target packages that need more QA work, or new packages that recently landed in QA.

Now, this week I will also be posting the next bits in our autopilot series -- intending to teach you about running and writing autopilot testcases. Our cadence testing this cycle will include running both automated and manual tests -- we need both ;-) You'll note the autopilot unity testsuite is included this week. I hope our subsequent testing weeks can feature some new automated autopilot tests written by some of you :-) If writing automated tests aren't up your alley, don't worry we need manual testcases too!

Happy Testing everyone,

Nicholas

---

### Post by ventrical on 2012-11-26
I got time to check into that this week. Not sure why Nick did not post that here.

---

### Post by grahammechanical on 2012-11-26
I am trying to get in on this.

Just downloaded the 20121126 ISO image and during the second purple screen I do not get all the usual disk activity as the hardware is being detected. I then get a black screen with the error message "unable to find medium containing a live file system."

As regards those Autopilot tests beware. There are a lot of them. Note what is said by Nick on 20th November on this page:

[http://qa.ubuntu.com/]("http://qa.ubuntu.com/")

> As of this writing, I get 461 tests returned. Feel free to try and run them. Pick one from the list and see what happens. For example,

autopilot run unity.tests.test_dash.DashRevealTests.test_alt_f4_close_dash

Just make sure you run them in a guest session -- I don't want anyone's default desktop to get hammered by the tests!

If you are feeling adventurous, you can actually run all the unity testcases like this (this will take a LONG TIME!).

These tests are also supposed to be run on 12.10 or 13.04 and not 12.04.

Regards.

---

### Post by ventrical on 2012-11-26
> **grahammechanical said:**
> I am trying to get in on this.

Just downloaded the 20121126 ISO image and during the second purple screen I do not get all the usual disk activity as the hardware is being detected. I then get a black screen with the error message "unable to find medium containing a live file system."

As regards those Autopilot tests beware. There are a lot of them. Note what is said by Nick on 20th November on this page:

[http://qa.ubuntu.com/](http://qa.ubuntu.com/)



These tests are also supposed to be run on 12.10 or 13.04 and not 12.04.

Regards.

Ahhhhhhhhrrggg.... :)  I just logged on and ran the Unity AutoPilot .. and it just keeps on going .. also on one of my main *installs*! :)  I was just going to start a new thread about 'no heads up" but .. well .. here it is ! :)

 So far , so good.  Nice work on the Unity auto Pilot test. Behaves like a remote access. 

 I don't understand the code comming from terminal though .. ssssss...FF..ssss EE FE  .. etc... so I will just let the test run it's course. It it foobars my desktop, well.. then thats just the way it is.  :) 

 Umm.. thanks for the *heads up* Graham. :)

---

### Post by kansasnoob on 2012-11-26
My "normal" test box won't run Unity since they dropped Metacity/Unity-2D in favor of "llvmpipe+compiz" so I guess my testing is simple :)

All I need to do is test the installation of the available Lubuntu images and report pass or fail. Of course I'll have to file a bug report to mark a test failed but we'll see how this goes.

I should have some time to test an Lubuntu i386 iso this evening.

---

### Post by balloons on 2012-11-26
:-) Glad you guys are enjoying things! I hope all is clear now -- it's not gloom and doom at all! I hope the autopilot tests are the first of many.. 

If you run all of the unity autopilot tests, yes it will take a long time. I think I'm going to split up the tests and have people run them a bit differently with some heads-up. This is a learning process on this end too -- need to figure out the best way to run and report (these are a bit different than the manual tests), but we'll figure it out. Enjoy the testing guys!

---

### Post by ventrical on 2012-11-26
> **guitara said:**
> :-) This is a learning process on this end too -- need to figure out the best way to run and report (these are a bit different than the manual tests), but we'll figure it out. Enjoy the testing guys!


Whew..!. Good to know that we are not alone ! :)

---

### Post by Elfy on 2012-11-27
Be good to look at how other flavours can adapt these tests to suit their needs.

No unity here :)

---

### Post by ventrical on 2012-11-27
> **Elfy said:**
> Be good to look at how other flavours can adapt these tests to suit their needs.

No unity here :)

  There is lots of testing needed here also : [http://iso.qa.ubuntu.com/qatracker/milestones/243/builds](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds)

..all flavours.. looks like a gazzilion things to keep us busy :)

I guess it would have to be up to the devs of any particular flavour whether or not they are going to write an auto-pilot test for those DEs.

---

### Post by balloons on 2012-11-28
> **Elfy said:**
> Be good to look at how other flavours can adapt these tests to suit their needs.

No unity here :)

Yes, I want ubuntu to get a testsuite for the default desktop applications -- I think it would be an excellent thing for flavors to shoot for as well!

---

