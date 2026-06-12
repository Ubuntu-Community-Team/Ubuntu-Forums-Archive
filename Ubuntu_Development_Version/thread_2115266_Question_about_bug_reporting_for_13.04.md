---
title: "Question about bug reporting for 13.04"
date: 2013-02-12
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-02-12
Hi!
I had mentioned in my other thread (about my experiences thus far with 13.04 testing) about the bug i noticed in the touchpad settings where when you change the setting on the "pointer speed" it does not "lock in" and as soon as you close the program, it reverts back to the "default" setting...

I know others here mentioned that they noticed that too...and it is experienced both on live session and after installing...I did sign up for a launchpad account and made a bug report but it looks like i am the only one who reported it...

I'm afraid they may never look at it (because i was the only reporter) so is there any way i can contact or get the attention of an ubuntu developer to check it out...it's a pretty obvious flaw and i am a bit surprised they haven't noticed it themselves...

Also, another bug i noticed is that quicktime videos are not playing properly on the "i tunes movie trailer" website...they always worked well in ubuntu before (including 12.10) and i noticed it both on live session and installed as well...the sound is fine but the videos "break up"...i didn't report that and was wondering if anyone else has that on 13.04?  (i tried re-installing the quick time plug in but it did not help)...

Here is my bug report, by the way, in case anyone would like to add to it:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719)

Any suggestions would be welcome...Thanks ;)

---

### Post by dino99 on 2013-02-12
you can login on that page, then hit "contact this team's admin" on top right corner. Explain the situation & point to the report link.

[https://launchpad.net/~ubuntu-desktop](https://launchpad.net/~ubuntu-desktop)

---

### Post by cariboo on 2013-02-12
There isn't very much information in your bug, so unless you add more information, the bug will probably be marked invalid.

Normally when creating a bug report, we use apport, this tool attaches logs, and information about your system, so the devs/bug triagers get a better idea of what is happening.

to use the automagic bug reporting service, you would open a terminal, and type the following command:

```
ubuntu-bug gnome-control-center
```

For more information on reporting bugs, have a look at this wiki page:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Have look at how to add more information to your bug report [here]("https://help.ubuntu.com/community/ReportingBugs#Adding_apport-collect_information_to_an_existing_Launchpad_bug").

---

### Post by craig10x on 2013-02-12
Thanks guys...i contacted them through that link and i also posted it on "ask ubuntu" as they mention there that some developers do read and can respond to questions on there...

---

### Post by grahammechanical on 2013-02-13
> I know others here mentioned that they noticed that too...and it is experienced both on live session and after installing.

I do not have a touchpad. But I think that one of the reasons for the existence of Ubuntu+1 is for other testers to try to repeat the bug and confirm it.

If you have made a bug report you can also test the daily image and report the bug on the QA tracker. Your Lauchpad Single Sign On will let you log in to report a test pass or fail. There is also a section for making a comment.

Forgive me if you already know this stuff but it is useful if we can post a link to our hardware profile when reporting on QA Tracker. When we run Checkbox it creates a hardware profile (it may even test the trackpad - for all I know). The profile gets posted in a Launchpad account as well as sent to Ubuntu Friendly.

See this tutorial. Look for Step 2 - Hardware profile.

[https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-qa]("https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-qa")

Regards.

---

### Post by craig10x on 2013-02-13
Thanks...i wasn't aware of that :)

I guess i am surprised that no one else reported it, since it is readily noticeable if you move the levers in that touchpad adjustment in system settings...and the close the program and open it again, you see that it shot right back to the default...and the only way to keep it locked in (for the session) is to keep that touchpad window open (of course, then you have to do that again every time you re-boot)...

I was just trying to call their attention to it, in case they (the developers) had not noticed it themselves...

The other bug i have noticed is that quicktime videos are distorting on the itunes movie trailer website (that site needs quicktime to play the videos which we have in ubuntu's codecs)...this is the first time i ever encountered that on ubuntu (it always worked well on previous versions)...

Re-installing the quicktime plug in on package manager did not help at all...

These are the ONLY BUGS i have noticed since i have been running 13.04...otherwise, very smooth and stable...
Even all the updates have been fine (no breakage or problems so far) except for one broken package which i was easily able to fix using package manager...

Regarding the distortion on quicktime videos at the itunes movie trailer website, i would be curious to know if anyone else is experiencing that..if you haven't checked, just go to the itunes movie trailer site on your ubuntu 13.04 and see if a movie trailer video plays smoothly...and please post here and let me know...I normally use Google Chrome web brower but i checked Firefox also and it was the exact same thing...

---

### Post by mc4man on 2013-02-13
I don't know that you've ever clearly stated here or in bug report if - 
After adjusting in g-c-c panel to make slower (or faster), does that adjustment get changed back or is it just what's shown in the panel that gets changed back to default?

At least here it stays at whatever I adjusted to, ie. the cursor is faster than @ the default even when re-opening the panel which opens @ the default.

---

### Post by craig10x on 2013-02-13
> **mc4man said:**
> I don't know that you've ever clearly stated here or in bug report if - 
After adjusting in g-c-c panel to make slower (or faster), does that adjustment get changed back or is it just what's shown in the panel that gets changed back to default?

At least here it stays at whatever I adjusted to, ie. the cursor is faster than @ the default even when re-opening the panel which opens @ the default.

Oh..so are you saying that the setting you change it to locks in even though the slider shows that it is back at default?

Hmmm..not sure if that happens...i will check it further and report back....i set to the lowest setting, but when the slider goes back i think the pointer feels faster again...so i am not sure if it is really staying at my changed setting...i will play around with different settings on there and see,,,

Also, i hope some can check to see if their itunes movie trailer videos play properly (at the itunes movie trailer website)...

---

