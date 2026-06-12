---
title: "transparent terminals not working."
date: 2014-02-24
forum: Ubuntu Development Version
---

### Post by beelzebufo on 2014-02-24
hello all, I just switched back to ubuntu gnome.. not sure why I ever left, I forgot how much I loved gnome shell, anyway, now that I have installed ubuntu gnome 14.04, I can't seem to make my terminals transparent like I usually do.  I go into the profile settings > background > transparent background, and then I adjust, but it always stays opaque.. not sure what I did differently, I installed over mint on accident (didn't reformat as I should have) but everything else seems fine.. I didn't notice until after I got things set up the way I wanted so I don't really want to reinstall again.  Any help would be greatly appreciated, seems like a silly little detail, but I gotta have my transparent terminals, it just feels wrong if I can't see through them.

thanks
beelze

I also don't seem to have colors enabled (it used to be that folders, executables, etc) were different colors, now it's all black and white..

---

### Post by sffvba[e0rt on 2014-02-24
*Thread moved to **Ubuntu +1**.*

---

### Post by 23dornot23d on 2014-02-24
I just tried it out to confirm that it is still working ......... although will try it out in a few sessions
this was in one that has nothing other than my docks in it ......

Short video ..... mine was upgraded too but not from mint ........  [http://youtu.be/_oY02VXftKw](http://youtu.be/_oY02VXftKw)

Make sure that you have the latest gnome-terminal

Then - edit - profiles - edit - backgrounds .......

____________________________________________________________ 

You are correct - something else happens in Gnome-Shell ............ it turns black - from whatever it was before when adjusting 
the slider ........... [http://youtu.be/nB3d-HE_8JA](http://youtu.be/nB3d-HE_8JA)

---

### Post by beelzebufo on 2014-02-24
thank you for the reply, unfortunately, that did not help.  I have the up to date gnome-terminal, and I can set the background to transparent, it just doesn't do anything, may be a bug, It slipped my mind that 14.04 is still in dev.

---

### Post by 23dornot23d on 2014-02-24
Yep - I just did another test in Gnome-shell - the first test was in one that only has the docks in it ..... 

You are correct - something else happens in Gnome-Shell ............ it  turns black - from whatever it was before when adjusting 
the slider ........... [http://youtu.be/nB3d-HE_8JA](http://youtu.be/nB3d-HE_8JA)

---

### Post by beelzebufo on 2014-02-24
ok, so it's not just me then, hmm, never submitted a bug report before, let's see how much they hate me by the time I am done lol.  Thanks again.

---

### Post by cariboo on 2014-02-25
I'm affected by this too, before creating your bug report, have a look [here]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by QDR06VV9 on 2014-02-25
For transparent terminal "sudo apt-get install terminator" Right click inside the terminal after launch select preferences, profiles, background. you can make the terminal transparent or insert a transparent .png see attach

---

### Post by cariboo on 2014-02-25
> **runrickus said:**
> For transparent terminal "sudo apt-get install terminator" Right click inside the terminal after launch select preferences, profiles, background. you can make the terminal transparent or insert a transparent .png see attach

That's not the point though, gnome-terminal transparency works the way it should when running Unity, but not when running gnome shell.

alexis is running unity, and redstone is running gnome shell.

---

### Post by QDR06VV9 on 2014-02-25
> **cariboo907 said:**
> That's not the point though, gnome-terminal transparency works the way it should when running Unity, but not when running gnome shell.

alexis is running unity, and redstone is running gnome shell.
For the sake of argument Title reads[ tansparent terminals]("http://ubuntuforums.org/showthread.php?t=2207704")
Just another option to get it done.
I Too run gnome-shell.

---

### Post by cariboo on 2014-02-25
I guess the op should have specified gnome-terminal. :)

---

### Post by mc4man on 2014-02-25
I believe Gnome removed transparency in gnome-terminal quite some time ago

see-
[https://bugzilla.gnome.org/show_bug.cgi?id=698544](https://bugzilla.gnome.org/show_bug.cgi?id=698544)

---

### Post by beelzebufo on 2014-02-25
the option is still there, it just doesn't make things transparent.

---

### Post by mc4man on 2014-02-25
> **beelzebufo said:**
> the option is still there, it just doesn't make things transparent.

I guess you didn't read thru bug report - small quote 
> I've spoken to Christian and he has filled me in on the background to this
issue.

The ability to set background transparency was removed as a part of a much
larger clean up of the gnome-terminal code base. This modernisation effort is
much needed and it should be remembered that the terminal has an old and
complicated code base. Background transparency was also known to cause a range
of performance issues, including slowness and memory leaks.

Given the number of active terminal developers, the need to clean up the code
base and known bugs with background transparency, it was decided that the
resources were not available to maintain background transparency and keep the
quality to the required level.

We understand that some users are disappointed by the disappearance of this
feature,.....

---

### Post by beelzebufo on 2014-02-26
I read it, but I thought it meant that the feature had been removed.  the first report stated that the background tab was gone, that was what I thought it meant.  If they removed the feature, I assumed (we all know what happens when you assume) that they had removed the ability to use said feature (the background tab or the option to make the terminal transparent.)  Anyway, it doesn't matter, if they want to remove transparent terminals, they still need to remove the transparent option and the slider from the terminal options.

---

### Post by cariboo on 2014-02-26
@beelzebufo, I think you may need to read the whole bug report, as it mentions in there that the Ubuntu devs included a work-a-round to get transparent terminals to work in Unity. With the shortage of manpower that Ubuntu Gnome is experiencing, it may be a while before they get around to fixing the problem in gnome-shell.

---

### Post by beelzebufo on 2014-02-26
I know for a fact that transparent terminials work on ubuntu gnome 13.10, and yes, I did read the bug report.

---

### Post by cariboo on 2014-02-27
> **beelzebufo said:**
> I know for a fact that transparent terminials work on ubuntu gnome 13.10, and yes, I did read the bug report.

So what is it that you want? This is Trusty 14.04 we are discussing here. What worked in the previous version, has no bearing on anything in this version.

---

### Post by beelzebufo on 2014-02-27
the bug report is from april of last year, 13.10 was october of last year, october is after april, your bug report has no bearing on this conversation.  This conversation is over.

---

### Post by cariboo on 2014-02-27
It seems we are missing something here. The bug report quoted is an upstream bug report. As you can see the Gnome developer is not going to fix the problem. The Ubuntu devs have come up with a work around, that makes transparent terminals work in Unity. It may be the the Ubuntu Gnome developer may not even be aware of the problem, so I'd suggest that you create a new bug report, so at least the developer is made aware of the problem.

If you aren't sure how to create a bug report, have a look at [this wiki page]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by mc4man on 2014-02-27
Probably good this 'conversation' is over, so final comment.
Of course the bug report is relevant, the date of really isn't, Ubuntu is quite some time behind Gnome.

As far as the option in an Ubuntu gnome-shell  session - 
It does work, just doesn't produce the results expected. Why?, personally don't care. If you do then you could - 
See what changed in Gs **&** 13.10 vs. Gs **&** 14.04
See how it works or doesn't on Fedora, try the current Fedora 20 live
File a launchpad bug

---

