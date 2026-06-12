---
title: "Screen Won't Turn Off"
date: 2014-10-01
forum: Ubuntu Development Version
---

### Post by craig10x on 2014-10-01
I upgraded from 14.04 to 14.10 today and it worked very well...The only bug i spotted is that i normally have my screen set to turn off after 30 minutes (go to black), and it doesn't do that now...in fact, i tried a few settings, like 10 minutes and even 1 minute, but it won't go to black...is this a bug that should get corrected soon?  Or is the some simple fix for this type of problem?...
Hardware is a Toshiba 17" laptop with i3 core intel processor...

Everything else seems to be working great...as far as i can tell, this is probably the only bug i am getting...Any ideas appreciated...;)
Would be a shame to have to do a clean install to possibly fix the problem...I wouldn't want to do anything that might mess things up more but if there are any simple (non-dangerous) things i could try?

---

### Post by craig10x on 2014-10-02
Anyone have any suggestions? (other then to do a clean install..i will if i need to but was hoping to avoid that)...

---

### Post by craig10x on 2014-10-04
Seems like no one has any ideas on fixing this, so i will be doing a clean re-install on 14.10 as it would seem like the only way i can get that feature to work again...
Oh well :sad: It's a shame because everything else works great...but i need to get that working...

---

### Post by rockorequin on 2014-10-04
Did a reinstall help? I have the same problem in 14.10. The screen doesn't turn off or lock after the designated time (CTRL-ALT-L doesn't make it lock, either)

However, Lock Screen from the system menu does turn on the lock screen, and the screen turns off shortly after this.

Edit: CTRL-ALT-L didn't lock it because the keyboard shortcut had changed to Super-L. Changing it back to CTRL-ALT-L makes it work again (and the screen blanks shortly after the lock screen appears). So the problem is that the auto-screen lock doesn't work.

---

### Post by d-cosner on 2014-10-04
Did you upgrade or do a clean install?

---

### Post by craig10x on 2014-10-04
@rockorequin: I haven't done the clean install as of yet...but was wondering (as d-cosner mentioned)...did you do a clean install or did you upgrade into 14.10?
I'm going to check to see if it works on mine (screen turning off when using lock function) on mine...i hadn't tried that...and once you do it that way, does it stay set to turn off the screen at the specific time you set it to, each time you boot up?

Edit: Mine works like yours...but bottom line is, screen won't turn off at time i set it to in system setttings, so i guess i will have to go ahead and do a clean install...hope it won't be for naught...
I'll post back after i do it but i am assuming you upgraded also?  (otherwise, why would you be asking if a clean install would fix it?)...

---

### Post by rockorequin on 2014-10-04
I did the upgrade from 14.04, that's why I'm interested to know if the screen lock works from a clean install.

The upgrade was fun in itself - the computer locked up completely half-way through (I couldn't even get a tty console) and corrupted the root partition's superblock so I had to rollback to the last snapshot; when I tried again the computer locked up completely again. This time the superblock was OK but the computer would only reboot into a command console. But I was able to complete the install with dpkg --configure all and apt-get -f install.

I haven't been able to figure out what's responsible for locking the screen. You used to be able to choose the unity locker or lightdm locker (see [http://www.webupd8.org/2014/03/how-to-switch-between-new-unity.html](http://www.webupd8.org/2014/03/how-to-switch-between-new-unity.html)) but that option has disappeared from CCSM in 14.10. I see there though that compiz has its own screen lock key combination (Super-L) so both Super-L and CTRL-ALT-DELETE now lock my screen manually.

---

### Post by craig10x on 2014-10-04
Thanks for confirming...i figured you probably upgraded like me...I know it works fine when i run a live session (on the daily build iso) so i am assuming that something must have gotten messed up on the upgrade and that hopefully, a clean install will straighten it out...i will be doing it today and will let you know later ;)

Other then this, the upgrade was perfect...just our luck it had to be on something that we both use and need...I always have my screen go to black after 30 minutes and i can't do that right now...
So, i figured that a clean install would be the only shot at getting it back since it doesn't appear to be a general bug since no one else has commented or mentioned having an experience with the problem on 14.10...

---

### Post by Doug S on 2014-10-04
My issues with screen blanking sound a little different than you, but I'll post here anyhow:

My issues started during 14.04 development cycle, specifically on or about 2014.03.12 (March 12th, 2014). My issues persist, both on 14.04 and 14.10. After updating my 14.10 desktop VM today the screen does not go blank at all. Note this was a new 14.10 VM created on September 16th.

I use a different screen blank time and session lock time. Until today, the screen would go blank after the screen blank time, but then turn back on, and stay on, after the additional lock time.

Now, after the applying updates today (which includes a few days of updates, as I didn't use this VM for a few days) the screen never blanks and the session never locks.

Old Reference: [https://bugs.launchpad.net/oem-priority/trusty/+bug/1292041](https://bugs.launchpad.net/oem-priority/trusty/+bug/1292041) (although I was told my issue was different (I don't think so, actually))

---

### Post by ventrical on 2014-10-04
> **craig10x said:**
> Seems like no one has any ideas on fixing this, so i will be doing a clean re-install on 14.10 as it would seem like the only way i can get that feature to work again...
Oh well :sad: It's a shame because everything else works great...but i need to get that working...

Definitely busted.  I usually set my setting to 'Never' as I have my machines on the go and testing video. I just tried to set it for one minute on one (hard) install (Not VM) and the screen will not turn off.

  I would wait until release candidate before fresh install. I think this is a gnome-settings bug.

I don't know what the bug is .. but there is probably one out there.

Show me the bug report and I will confirm or , any suggestions of what program to file against?

---

### Post by craig10x on 2014-10-04
@ventrical: I did the clean install and funny part is, it worked initially but when i did the updates, now it seems to not be working again! 
I wonder if there are any bug reports on this...i guess i should have waited for release before upgrading...not sure what i should do now...perhaps go back to 14.04 for now and do the upgrade after the final release...
I wish i had read Doug S and ventrical's post before i wiped out the upgrade :rolleyes:

---

### Post by ventrical on 2014-10-04
> **craig10x said:**
> @ventrical: I did the clean install and funny part is, it worked initially but when i did the updates, now it seems to not be working again! 
I wonder if there are any bug reports on this...i guess i should have waited for release before upgrading...not sure what i should do now...perhaps go back to 14.04 for now and do the upgrade after the final release...
I wish i had read Doug S and ventrical's post before i wiped out the upgrade :rolleyes:

ya know .... after you brought up this bug .. I am now motivated to try this out in a perfect 14.04 install and see what happens there.

brb! :)

edit:

ok .. works perfectly in trusty.  There has been no daily-live/current/ zsync  updates for a while now .. so we may have to just wait it out.. until RC..

---

### Post by Doug S on 2014-10-04
I have been looking, but haven't yet found a bug report. Also, this recent version of the issue is after 2014.09.30 11:05 (my time UTC-7).

@criag10x: did you install from a new daily ISO from today, or and older iso? I assume an older one, and the updates introduced the (new) issue, just as in my case.

---

### Post by craig10x on 2014-10-04
@ Doug S: I installed from friday's daily build...and it worked on live session and after i initially installed...but right after doing the updates (when software updater came up) that's when it stopped working again...
So, apparently my upgrade was 100% perfect (i thought that it got broke in the upgrade) and wiped everything out to do this clean install without a good payoff....

Now...i am trying to figure out what to do...stay with this and hope it gets fixed soon... or go back to 14.04...
@ventrical: do you think i should keep this 14.10 installed and that hopefully it will get corrected before the final release?

---

### Post by Doug S on 2014-10-04
well, that sure narrows down the introduction of the issue, to after the daily iso of yesterday.

---

### Post by sammiev on 2014-10-04
I just tried it on Ubuntu Gnome 14.10 and the screen blanking and password startup on return and it works perfect. I will try Xubuntu 14.10 shortly.
What flavor are you using?

Edit: Works perfect like above with Xubuntu also.

---

### Post by craig10x on 2014-10-04
@sammiev: I'm using the main edition (ubuntu with unity)...I wonder if there are any bug reports on this...I'm not really a tester, just jumped in a bit early...Perhaps one of you guys can file a bug report on this and provide a link to it here...i would be happy to me too it and add some comments on it...

As far as what i will do, i guess i might as well keep this install and finish putting my stuff on...problem with me going back to 14.04 is i have that multimedia problem with the old 3.13 kernel and 14.04 won't get Utopic's patched 3.16 until next february....so i guess i will have to stay with this and when i want to make the screen go black for an extended period of time, hit the "lock" from the top panel to make it and then log in when i want the screen to come back on...And keep my fingers crossed that this gets fixed between now and final release...

---

### Post by ventrical on 2014-10-04
> **craig10x said:**
> @ Doug S: I installed from friday's daily build...and it worked on live session and after i initially installed...but right after doing the updates (when software updater came up) that's when it stopped working again...
So, apparently my upgrade was 100% perfect (i thought that it got broke in the upgrade) and wiped everything out to do this clean install without a good payoff....

Now...i am trying to figure out what to do...stay with this and hope it gets fixed soon... or go back to 14.04...
@ventrical: do you think i should keep this 14.10 installed and that hopefully it will get corrected before the final release?


Well.. yeah.. I mean that's part of why we are here in development. I have about 10 utopic installs on several different machines and I usually nurse them through to final. I would say it should be corrected by final .. and you could always install Trusty if the bug is not fixed.  it is not a serious bug <ubuntu-unity> here. I think it is more cosmetic. Hopefully the devs will take note and build a patch before release.

---

### Post by ventrical on 2014-10-04
> **sammiev said:**
> I just tried it on Ubuntu Gnome 14.10 and the screen blanking and password startup on return and it works perfect. I will try Xubuntu 14.10 shortly.
What flavor are you using?

Edit: Works perfect like above with Xubuntu also.

He's using ubuntu-unity .. see the prefix :)

---

### Post by craig10x on 2014-10-04
@ventrical: Thanks, buddy :D
I'll do that then...and finish putting on my stuff on this 14.10...i hadn't been in development in some time, so i sort of forgot that things can sometimes break in updates but usually eventually they get sorted out...;)
After the release, if it isn't fixed, i could always return to trusty if necessary...no point in re-installing it right now...

---

### Post by jerrylamos on 2014-10-04
> **craig10x said:**
> Seems like no one has any ideas on fixing this, so i will be doing a clean re-install on 14.10 as it would seem like the only way i can get that feature to work again...
Oh well :sad: It's a shame because everything else works great...but i need to get that working...

Clean 14.10 amd64 install including update today didn't fix the bug here.  I'm set for 5 minutes the default and utopic is considering that as never.
BTW, I'm using an external monitor with separate power off so I do that sometimes.

I've the opposite problem with utopic lubuntu - screen turns off, insists on login and password even though it's set to not require that.

---

### Post by ventrical on 2014-10-04
> **craig10x said:**
> @ventrical: Thanks, buddy :D
I'll do that then...and finish putting on my stuff on this 14.10...i hadn't been in development in some time, .

:)

 I have been so busy all summer it's unbelievable. Any spare time I have had I had spent here. I finally got a stretch where  I have been finally catching up on a little bit.

Regards..

btw .. thanks for reporting this *bug*  We should nickname you 'Hawkeye' :) lol

---

### Post by craig10x on 2014-10-04
You're very welcome...too funny :biggrin:

---

### Post by rockorequin on 2014-10-04
Did anyone actually submit a bug report for this? In case not, I did here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1377537](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1377537)

---

### Post by craig10x on 2014-10-04
Thanks for submitting the bug report...added myself to the "affects me too" and also added comments backing up the same problems you mentioned...and that it does it on both upgrades AND clean installs...
Hope others here will go to your link and add on to it...the more, the merrier ;)

I had forgotten i once set up a launchpad account and actually, anyone with an ubuntu log in for this forum can log into that too...

---

### Post by Doug S on 2014-10-04
Thanks for creating the bug report. I have added to it.

---

### Post by ventrical on 2014-10-05
+1 .. me tooed it!:)

---

### Post by craig10x on 2014-10-05
Very Cool ;)
Let's get everyone in on it :D
The more that add to it, the quicker they will look at the problem...

---

### Post by craig10x on 2014-10-07
I see about 6 of us has reported this..what i am curious about is, are we the only ones that are getting the bug?  No one else here that is running 14.10 (ubuntu w/unity) is experiencing it since last week or so of updates? (when it was apparently introduced as my clean install did not have the bug until i did the mass of updates that came in AFTER installation...if that is the case, it does seem rather odd.
Meanwhile...anyone else experiencing it PLEASE add your "affects me" to the link above for the bug report...the more there is, the better the chance of it getting fixed soon...

---

### Post by ventrical on 2014-10-08
This cycle has been one of the slowest cycles I have seen in regards to drumming up chatter and bugs. After the problems with unity-next, unity8 it became very much  like a respin of trusty.

 .. and after all .. it's been a long summer..  :)

---

### Post by craig10x on 2014-10-08
@ventrical: And i just jumped in toward the end (hoping to escape any bugs) and got "hit" with one...figures ;) :D

---

### Post by ventrical on 2014-10-08
Big batch of updates .. no fix.  Utopic certainly not for the power_save crowd. :)

Regards..

---

### Post by jerrylamos on 2014-10-08
> **ventrical said:**
> Big batch of updates .. no fix.  Utopic certainly not for the power_save crowd. :)

Regards..
Nor the screen save crowd.  

Just did an install, now at 3.16.0-21, even left 5 min default lock screen "on".  Couple hours later still no turn off no lock screen.  I usually turn lock off I'm the only one using my computers.

BTW, utopic Lubuntu has the opposite problem.  Turns off and locks after 5 min no matter what the settings are....

---

### Post by craig10x on 2014-10-08
And just out of curiousity, i downloaded today's daily build and ran it live session...guess what? screen will not go to black no matter what you set it for!
A week ago, when i installed 14.10, i ran that live session and at that time, it worked fine....Once i installed and ran the updates, that is when it broke...so this confirms that the bug ocurred in the downloads from the last week or so...

---

### Post by ventrical on 2014-10-08
I believe that this is one of those general watermark bugs that the devs will remove come RC. There is no way they can leave this in. From a marketing aspect , it will compromise the whole of the convergence project.

 Then again I am  sure that there are not many ubuntu hobbyists who are concerned currently about the greater scheme of things at this stage of the game.. but I will bet that in a  few weeks we will get a bigger part of the unity8  project. This should bring some more genuine breakage, however, as evident in this cycle, I would think that it will not be a warm and fuzzy rolling release model. We will see . :)lol

Regards..

---

### Post by mc4man on 2014-10-08
Bug here, should be fixed shortly
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1377847](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1377847)

---

### Post by craig10x on 2014-10-08
@mc4man: Thanks so much for posting that...that is great (i see it is assigned and has critical status) so we should have the fix soon :D
You were right as usual, ventrical ;)

---

### Post by sammiev on 2014-10-08
I'm not looking forward to this release at all. Too many bugs every where.

---

### Post by jerrylamos on 2014-10-08
> **sammiev said:**
> I'm not looking forward to this release at all. Too many bugs every where.

That's what we're supposed to be doing, highlighting bugs instead of waiting for the RC code to get the same  bugs with a lot of people......

---

### Post by ventrical on 2014-10-08
> **jerrylamos said:**
> That's what we're supposed to be doing, highlighting bugs instead of waiting for the RC code to get the same  bugs with a lot of people......

+++! :)

---

### Post by ventrical on 2014-10-08
> **craig10x said:**
> @mc4man: Thanks so much for posting that...that is great (i see it is assigned and has critical status) so we should have the fix soon :D
You were right as usual, ventrical ;)


... I see how this got a little confused .. [s] because I think the bug was originally filed against the unity-desktop and actually it is gnome-desktop3 settings...[/s]

edit..

my mistake .. actually it was the unity-settings-dameon

Great work! :)

---

### Post by ventrical on 2014-10-08
> **sammiev said:**
> I'm not looking forward to this release at all. Too many bugs every where.

 but I think we are going to have some fun with next release with unity8 (next and convergence) at least I hope so.   I need some new code to tear apart .. I'm starving .. :) lol

---

### Post by sammiev on 2014-10-08
> **ventrical said:**
> but I think we are going to have some fun with next release with unity8 (next and convergence) at least I hope so.   I need some new code to tear apart .. I'm starving .. :) lol

unity8 I will play with for sure.

---

### Post by motang on 2014-10-09
Well clean install on two of my machines has this same issue. I am assuming this will be worked out via a system update. Just have to wait and see. Might have to file a bug.

---

### Post by craig10x on 2014-10-09
It's been assigned so hopefully it will get fixed soon and i would imagine it would come down in the updates once it is fixed...i check the bug report each day and once it says "fixed" then we should start looking for it in the updates...
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1377847](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1377847)

---

### Post by cariboo on 2014-10-09
> **craig10x said:**
> It's been assigned so hopefully it will get fixed soon and i would imagine it would come down in the updates once it is fixed...i check the bug report each day and once it says "fixed" then we should start looking for it in the updates...
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1377847](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/1377847)

You could just subscribe to the bug email list, and get automatic notification when the bug gets fixed.

---

### Post by craig10x on 2014-10-09
@cariboo907: I wasn't aware of that...just did that...thanks for calling to my attention ;)

From the comments of developer Tim who is working on it, it sounds like he fixed it but initially it occasionally crashed but he fixed the crashing also and i guess they are testing it to make sure it stays stable before deeming it as fixed and sending the fix down through the updater...

---

### Post by Smask on 2014-10-11
```
[FONT=fixedsys]This bug was fixed in the package unity-settings-daemon - 14.04.0+14.10.20141010-0ubuntu1
[/FONT]
[FONT=fixedsys]---------------
unity-settings-daemon (14.04.0+14.10.20141010-0ubuntu1) utopic; urgency=low[/FONT]
[FONT=fixedsys]  [ Tim Lunn ]
  * Copy in Idle Monitor from 3.10 and hook up dbus interface (LP:
    #1377847)
 -- Ubuntu daily release <email address hidden>   Fri, 10 Oct 2014 08:06:04 +0000[/FONT]




[TABLE="class: bug-activity"]
[TR]
[TD="colspan: 2"][FONT=fixedsys]Changed in unity-settings-daemon (Ubuntu Utopic): [/FONT][/TD]
[/TR]
[TR]
[TD="align: right"][FONT=fixedsys]         **status**:       [/FONT][/TD]
[TD][FONT=fixedsys]         Confirmed &#8594; Fix Released       [/FONT][/TD]
[/TR]
[/TABLE]

```

---

### Post by craig10x on 2014-10-11
Great News ;) I got an e-mail for the bug report a little while ago saying that also...
I would imagine it will probably come down in the next set of updates...will have to watch out for it...

---

### Post by craig10x on 2014-10-11
Fix Is Here :D 
 Run your software updater and it should pop in there...I ran it about 20 minutes ago and there it was...I had it install and just to make sure, re-booted my computer...set it for 5 minutes and the screen faded and went black as it should...i just set in for my normal 30 minutes off and should be all set now...

---

### Post by jerrylamos on 2014-10-11
Yep, updated today to 3.16.0-22 and screen goes black in 5 minutes O,J,  Comes up with no lock as I have it set.

BTW, Compiz still crashing....

---

### Post by Doug S on 2014-10-11
Yes, the screen goes blank for me now also.
However, it turns on again after the additional lock time, but that is a different issue that started for me on March12th 2014, as mentioned in [post 9]("http://ubuntuforums.org/showthread.php?t=2246601&p=13135750#post13135750")
... hmmm I was just about to hit "submit" and noticed my screen (another computer) went blank. O.K. not sure what the time was, but it wasn't what I had set. ...

---

### Post by Smask on 2014-10-11
"The software on this computer is up to date" 

You're lying!

(Checking Software and Updates)

 Ah! The Swedish mirror hasn't synced yet. 

(Switching to main server)

Much better!

---

### Post by craig10x on 2014-10-11
Working perfect here...i set for 30 minutes, it goes dark at 30 minutes...didn't check the lock feature but i never use that anyway...

---

