---
title: "Please Help Get This Bug Fixed in Ubuntu 13.04"
date: 2013-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2013-06-01
I filed the bug report 4 months ago and it has not been assigned...would appreciate it if everyone would log into launchpad (and if you aren't registered, please register) and just hit "this affects me" on the upper left side of the page...you can add any comments also if you want but make sure to hit the "affects me" button...i figure, the more of those, the better the chance they will look at it....

Frankly, i can't imagine why they (the developers) have never noticed it!

The bug is that when you change the settings in the mouse/touchpad settings, they don't "lock in"....as soon as you close the program, it resets to the default settings...

From what i understand, everyone has this bug (not just myself) as i asked others when i was running 13.04 development and all agreed they notice it too...

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719)

Thanks in advance... :D

---

### Post by Cheesehead on 2013-06-01
Yes, click "Affects me too"
Yes, subscribe to the bug.
Yes, help maintain the bug report.
No,  **DO NOT** leave "Me too" comments. They do not get the bug addressed faster, and the noise obscures real progress on the bug.

Quite the opposite - like trying to talk in a very loud room, the triager or developer may spend as little time as possible on a noisy bug. It's no fun to page through page after page of worthless comments looking for nuggets of useful clues, nor to get their inbox spammed by each worthless "me too" comment.

But let's get back to your bug. Your bug sure looks a lot like [Bug #865791]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/865791"). If it is a duplicate, please mark it so.

Bug #865791 was upstreamed to Gnome. You can get a bug addressed by upstream developers much faster if you upstream the bug yourself instead of waiting for a volunteer triager to do it for you. Upstreaming and checking for duplicates yourself can save you a lot of unnecessary work, speeds up the process, and helps volunteer triagers and developers to concentrate on actual bugs. Remember to point the Launchpad "remote bug watch" feature to the upstream bug report so resolutions and information get passed.

The upstream Gnome bug was marked as a duplicate of [Gnome Bug #699015]("https://bugzilla.gnome.org/show_bug.cgi?id=699015"), which was fixed with the recent release of Gnome 3.8. Take a look and see if your problem matches that bug report, and to see if Gnome 3.8 fixes the problem.

If so, please help maintain the bug: Mark your bug a duplicate on launchpad, and please fix the tracked Gnome Bug number so Launchpad is tracking the correct status on the correct Gnome Bug. Helping to maintain the bug like this is another way to get the problem to developers faster, and to get the bug fixed faster.

If your bug is different from Gnome Bug #699015, please edit your bug description to be very very clear how your bug is different. They look the same to me.

---

### Post by craig10x on 2013-06-01
@Cheesehead:  Hey...thanks....you are really good at checking these things in depth (i am kind of an amateur at it because i just subscribed to it recently)...
Yes....reading Bug #699015 seems to match what i was describing (about the pointer speed in the touchpad settings reverts back to the default every time you close the program...
So then it sounds like it was fixed by the Gnome developer in Gnome 3.8...

I'd mark it as a duplicate, though hesitate a bit just in case it isn't what i think it is...though it sure does sound like it and indicates it was fixed....maybe i should just leave it alone as mine doesn't generate much activity on it and far as posting comments...

That is great...i was curious as to when ubuntu would be getting Gnome 3.8....when and in which version of ubuntu...anyone know?

---

### Post by Cheesehead on 2013-06-01
Don't hesitate on bug maintenance. Make the changes and subscribe to the bugs.
If you get feedback from someone else to revert the changes, you can can do that easily.
If you don't make the changes, then these bugs will remain open and orphaned. Eventually a volunteer will close the bugs...but they should be closed as Fixed, not Invalid. So it's better that you do it - you already know the issue.

For Gnome 3.8, see the packages of gnome-shell [http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gnome-shell](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gnome-shell)
You can see the progression of Gnome 3.4 and 3.6. Since Gnome has not been added to 13.10 (Saucy) yet, but 3.8 has been released, look for the Gnomebuntu team to push 3.8 into 13.10 soon.

Also, see [http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome](http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome) for a Gnome 3.8 PPA that you can use in Ubuntu 13.04.

---

### Post by craig10x on 2013-06-01
Thanks...and someone just posted on the ubuntu+1 section that Gnome 3.8 was just added to Ubuntu 13.10 in the latest updates....so i probably should download a daily build and check it...though probably best to wait another day or two to make sure the update is on there...

Sure would be nice to know that the ONLY bug i am experiencing on 13.04 will be corrected in 13.10 ;)

---

### Post by cariboo on 2013-06-02
Just a note about upstreaming bugs. Just because the bug was sent upstream, don't expect it to be fixed in a timely manner. I sent a bug upstream about 4 years ago, and it was just finally fixed during the Quantal release cycle. It was one of those bugs that didn't affect operation, but it annoyed me to no end when it showed up.

---

### Post by craig10x on 2013-06-02
Thanks...i think i will download a daily build iso of 13.10 on monday and check to see if it has actually been fixed yet....that way i will know whether or not to mark my report as a dup or not...
Still can't figure why the developers didn't catch it early....it's kind of an obvious one...

Status: Resolved  Resolution: Fixed  is what it says on the original reported bug report (which mine is likely a dup of) on my issue by the Gnome Team and supposed to have been corrected in gnome 3.8 version which of course, 13.04 didn't have...But i am going to take a look at it on live session of 13.10 now that they just added gnome 3.8 to it, and check to see if, indeed it is fixed...

---

### Post by Cheesehead on 2013-06-03
> **cariboo907 said:**
> I sent a bug upstream about 4 years ago, and it was just finally fixed during the Quantal release cycle.

Great point!
Of course, four years is still faster than never...which is the timeframe if the bug is not upstreamed at all.


> **craig10x said:**
> Status: Resolved  Resolution: Fixed  is what it says on the original reported bug report (which mine is likely a dup of) on my issue by the Gnome Team and supposed to have been corrected in gnome 3.8 version which of course, 13.04 didn't have...But i am going to take a look at it on live session of 13.10 now that they just added gnome 3.8 to it, and check to see if, indeed it is fixed...

Helpful and responsible participation! Excellent!
You can see how simply cleaning up (maintaining) the bugs and testing the fixes makes a *huge* difference to the developers and the rest of the community. Developers are more likely to work maintained bugs. And users are less likely to get frustrated.

---

### Post by craig10x on 2013-06-03
I checked today...doesn't seem to be fixed in ubuntu even though gnome has supposedly fixed it....so then, even if ubuntu 13.10 has gnome 3.8 it could still take more time before the actual fix filters down into ubuntu, perhaps?

I guess i will have to wait until close to the 13.10 release to check again....meanwhile, while it's only a minor nuisance, i'd sure like to see it go ;)

---

### Post by Cheesehead on 2013-06-03
If it's not fixed in Gnome 3.8, then say so on the Gnome bug report.
Be very specific. Explain exactly which version of Gnome you used, where you got it from, and exactly how you tested it.

Then contact the developer who marked it fixed on the bug report, and repeat the whole story with a positive spin: "Hey, this bug is marked fixed, but I can still reproduce it in Gnome 3.8....I'm willing to help debug and test, what would you like me to do first?" 

The developer may not respond immediately. They have lives and jobs and different time zones.
The developer may ask a bunch of questions. Answer fully, and don't be afraid to ask (positive) questions back.
The developer may explain that it's really a different bug, and you should resubmit a new bug report. Ask them back for the best way to explain this bug so it doesn't get confused again.
The developer may ask you to install a debugger or install a test version. It's a pain, sure, but do it anyway. They *need* the help.
Hey, if you do get a developer to look at the problem, I'm sure you will help them as much as you can.

---

### Post by craig10x on 2013-06-03
Thanks...will do...by the way, one of the people who was on that original bug report actually put a brief screen video that shows what happens...you can see it here:
[https://bug699015.bugzilla-attachments.gnome.org/attachment.cgi?id=242639](https://bug699015.bugzilla-attachments.gnome.org/attachment.cgi?id=242639)

As far as i know, everyone running 13.04 who checks this will see this bug (i mean main edition ubuntu w/unity of course)...

Also, do you mean that if he says it was fixed in gnome 3.8, if we don't see it working in ubuntu as such (in 13.10 which just added in gnome 3.8) does that mean the big wasn't fixed or could it mean ubuntu has  not incorporated all the new features and fixes it contains into 13.10 yet...that is the part i am confused about...

---

### Post by Cheesehead on 2013-06-04
Ubuntu 13.10 seems to be running Gnome 3.8.2.
Incorporating new features and fixes was done when Gnome was updated from 3.6.3 to 3.8.2.

If the bug report says it's fixed in Gnome 3.8.x, but you can still reproduce the bug in Ubuntu 13.10, then either 
1) the bug is not fixed, or 
2) the fix was (unintentionally) reverted, or 
3) your problem is a different bug.

---

