---
title: "Hardy quality is VERY low for LTS..."
date: 2008-05-06
forum: Testimonials &amp; Experiences
---

### Post by PryGuy on 2008-05-06
Good day everyone!
This is what I think and I'm sure there are many people that will start arguing with me, but it is clear for me. I have found VERY serious bugs in Hardy that actually stop me from installing it on the clients' machines:

1. Layout switching problem (have to correct xorg.conf manually, layout indicator doesn't work if autologin turned on)
2. Firefox hangs for a few seconds periodically (was that really necessary to put Firefox 3 Beta5 in the 'stable' LTS build?)
3. Login window opens up after a great pause when I first launch it.
4. pptp-linux on hardy server seems to be broken, it says 'segmentation fault' in logs.

Canonical, what's wrong with you?!:evil:

---

### Post by SuperSon!c on 2008-05-06
1)  i don't have that problem.
2)  yep, known problem for a lot of people on ubuntu.
3)  see #1.
4)  dunno.

*sniff sniff*  i smell a recurring discussion alert coming on.

---

### Post by PryGuy on 2008-05-06
1. Do you use layout switching? You certainly don't if you have one layout only ;)

---

### Post by soapytheclown on 2008-05-06
if u dont like it so much stick with gutsy or what ever other version worked for you.. afaik they were asked by the mozilla team to include FF3B5 since FF2 is about to become unsuported in the upcoming months. Cant say i can replicate the login / layout issues u say uve had and ive not used the pptp stuff either.

---

### Post by Lod on 2008-05-06
I agree on the Firefox, why a beta version?

---

### Post by PryGuy on 2008-05-06
> **soapytheclown said:**
> if u dont like it so much stick with gutsy or what ever other version worked for you.. afaik they were asked by the mozilla team to include FF3B5 since FF2 is about to become unsuported in the upcoming months. Cant say i can replicate the login / layout issues u say uve had and ive not used the pptp stuff either.I thought it is stable because it's LTS... Of course I will stick to a previous working version until they (or I) fix the problems, but the question is why they called another buggy release LTS???!!!

---

### Post by samjh on 2008-05-06
Have you filed bug reports?  Have you searched the forums to check whether they are valid bugs or just problems on your clients' machine(s)?

If you don't do the former, those problems will never get noticed, let alone fixed.  If you don't do the latter, you risk crowding the bug tracker with useless bug reports.

Your problems seem quite obscure, so it is vital to give feedback in the bug tracker.

Seeing how you seem to be an IT professional, you've probably got some experience in dealing with and diagnosing these kinds of problems.  The Ubuntu developers need proper input from people with your expertise by way of bug reports at [https://bugs.launchpad.net/ubuntu/hardy/](https://bugs.launchpad.net/ubuntu/hardy/).

> I thought it is stable because it's LTS... Of course I will stick to a previous working version until they (or I) fix the problems, but the question is why they called another buggy release LTS???!!!It's not a buggy release, because Hardy works reasonably well for the majority of users.  If it was really buggy, then it would be delayed like Dapper was.

LTS doesn't mean super-stable.  It means that security updates and important bug-fixes will be provided for a lot longer period than normal releases, therefore making it attractive to commercial users.  It's stability is just same as any release.

Firefox 2 will become unsupported by the Mozilla/Firefox developers when Firefox 3 is released in June 2008.  It is essential that LTS includes releases that will be supported for as much of the LTS cycle as possible.  That's why Firefox 3 was included, even if it is only a beta release.

I suggest filing bug reports, providing feedback on those reports, and waiting until the 8.04.1 maintenance release rescheduled for July.

---

### Post by soapytheclown on 2008-05-06
file a bug report in launchpad if you've got issues but from the looks of it the only thing anyone has from those u've identified is FF being beta. for me personally Hardy has been great since alpha 4 100 times better than gutsy.. my laptop works out of the box on it and so do 3 more of the servers i administer all of which has issues of some sort previously.

-edit- samjh u got there b4 me :)

---

### Post by PryGuy on 2008-05-06
> **samjh said:**
> Have you filed bug reports?> **soapytheclown said:**
> file a bug report in launchpadThese bugs do exist on launchpad! the layout switching problem was there since beta release and they didn't fix it in final. There's no still fix now as far as I know. Really sorry to say that people but that reminds the of the famous Microsoft support more and more... :(

---

### Post by yopnono on 2008-05-06
2, Yes I have this issue. Have noticed that when kjournal is kicking in it freeze/hang the FX/system for a short period of time.

Yes I have filed a bug.

---

### Post by Joeb454 on 2008-05-06
> **PryGuy said:**
> 2. Firefox hangs for a few seconds periodically (was that really necessary to put Firefox 3 Beta5 in the 'stable' LTS build?)


> **Lod said:**
> I agree on the Firefox, why a beta version?

Basically - it's because it makes for an easier transition to Firefox 3 Final when it is released in the next month or 2.

Also Firefox 3 b5 is very stable for a lot of users - myself included. I've found it to be far faster and better than Firefox2, ever since beta 1 (when I started using it full time)

---

### Post by PryGuy on 2008-05-06
So if you don't believe me here are the links:
[Keyboard layout problem]("https://bugs.launchpad.net/xorg-server/+bug/196277")(watch the dates please)
[Login Window delay]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/204770")

---

### Post by samjh on 2008-05-06
> **PryGuy said:**
> These bugs do exist on launchpad! the layout switching problem was there since beta release and they didn't fix it in final. There's no still fix now as far as I know. Really sorry to say that people but that reminds the of the famous Microsoft support more and more... :(

Layout problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277)
That has been marked for 8.04.1, so you should get a fix by around July, when 8.04.1 is scheduled to be released.

I can't find anything about a long delay for login window.  Perhaps this is a unique problem for your clients' machine(s).

The PPTP problem: [https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/122844](https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/122844)
If that is the same issue as what you are having, please leave a message there with your stacktrace of the crash attached, and change the status of the bug to "Confirmed".

I'm afraid the Firefox problem is NOT something *everyone* can duplicate (it works perfectly for me), so probably won't be solved until the next release (which the is RC) or the final release. :(  **In the meantime, Firefox 2 is still available in the repositories.**

---

### Post by PryGuy on 2008-05-06
> **samjh said:**
> I can't find anything about a long delay for login window.  Perhaps this is a unique problem for your clients' machine(s).[Here you are please]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/204770")

---

### Post by samjh on 2008-05-06
> **PryGuy said:**
> [Here you are please]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/204770")

Does your client's installation have Tracker enabled?  If so, you could try turning it off.  I'm suggesting this because I have removed tracker from my machine (libtracker is still installed, however) and the problem doesn't happen.

That bug list shows that this problem has been earmarked for 8.04.1, so again, a fix should be available around the time of 8.04.1's release in July.

It is also an upstream problem with Gnome, so don't lay all the blame on Ubuntu developers. ;)

---

### Post by PryGuy on 2008-05-06
Anyway, think they shouldn't have called Hardy an LTS release... :(

---

### Post by samjh on 2008-05-06
LTS isn't supposed to be a super-stable release like Debian Stable.  It's just a release with extra-long support period.

It's quite stable for most people, so it's hardly fair to call it unstable.

---

### Post by PryGuy on 2008-05-06
As for pptp-linux... No, I couldn't find my bug on the launchpad, this is a PEBCAK thing probably, but look, I've got the settings files, I took them from Fiesty server, upgraded to Hardy server and copied them onto their places. Honestly, I'm lazy so script copies them for me.:oops: That excludes the user error on the other hand. So I did, it didn't work. pptp just hang and I couldn't see a proper output. I installed feisty again, copied them with the same script and it worked...

---

### Post by Sef on 2008-05-06
> 2. ... (was that really necessary to put Firefox 3 Beta5 in the 'stable' LTS build?)

Yes, Firefox 2 supported runs out well before the end of the LTS, which is April 2011 for the desktop.

---

### Post by 23meg on 2008-05-06
> **PryGuy said:**
> As for pptp-linux... No, I couldn't find my bug on the launchpad, this is a PEBCAK thing probably, but look, I've got the settings files, I took them from Fiesty server, upgraded to Hardy server and copied them onto their places. Honestly, I'm lazy so script copies them for me.:oops: That excludes the user error on the other hand. So I did, it didn't work. pptp just hang and I couldn't see a proper output. I installed feisty again, copied them with the same script and it worked...

So start a thread in the appropriate support forum and/or answers.launchpad.net and ask for help.

---

### Post by PryGuy on 2008-05-06
> **23meg said:**
> So start a thread in the appropriate support forum and/or answers.launchpad.net and ask for help.

[It was already started]("http://ubuntuforums.org/showthread.php?t=783780")

---

### Post by 23meg on 2008-05-06
Good, so wait.

---

### Post by ubuntu-freak on 2008-05-06
It's a new release, like all new releases there are going to be some issues. You seem to have a distorted view of what [LTS means](https://wiki.ubuntu.com/LTS).
 
Nathan

---

### Post by Chayak on 2008-05-10
> **reassuringlyoffensive said:**
> It's a new release, like all new releases there are going to be some issues. You seem to have a distorted view of what [LTS means](https://wiki.ubuntu.com/LTS).
 
Nathan

+1

Like just about any distro or product out there you only have a relatively small beta test group to get your release ready.  You can't test for every possible situation unless everyone that will use it is participating in the beta to iron out their issues early.

If you want fewer issues with new releases then don't get upgrade fever that seems to spread like wildfire when a new release comes around and stick to your current version for a month or so.  It would be a pipe dream to assume you won't have issues when a brand new release hits the street and comes across hardware configurations it was never tested with.

Yes, one can complain but are they really doing anything to correct the situation? Try submitting a bug report or adding the particulars of your own encounter to an existing bug report.  That way you can contribute to the solution of the problem even if you can't dig into the source code to work on it yourself.

---

### Post by fredbird67 on 2008-05-13
> Hardy quality is VERY low for LTS...
Tell me about it!

Trying to set up a 1024x768 screen resolution for both when I'm logged in as well as for the GDM screens was nothing but an exercise in futility for me, as I never could get anything higher than 800x600, never mind the fact that I got what I wanted in the screen resolution department under Gutsy.

For now I guess I'll just go back to Gutsy.  It seems like Hardy is to Linux what Vista is to Microsoft.  Given that comparison, this can't be good for widespread Linux adoption on the desktop. :(

In fact, something I think Canonical ought to do is drop the scheduled-release idea altogether and don't be releasing ANYTHING until it truly is ready for prime time.  Hardy Heron felt like nothing but an ALPHA quality release and like they were trying to rush Hardy Heron out the door before it was truly ready.  Not to mention, the timing with Mozilla Firefox couldn't have come at a worse time, either, since Mozilla plans to ditch all support for FF2 soon and pushed Canonical into including FF3 beta 5 in Hardy.  

Therefore, it only makes sense for Canonical to not have scheduled releases and save themselves the embarrassment, because they really came out with egg on their faces with Hardy Heron.  I just hope they can redeem themselves with Intrepid Ibex...

Fred

---

