---
title: "Firefox launcher problem"
date: 2012-12-06
forum: Ubuntu Development Version
---

### Post by sgage on 2012-12-06
Suddenly Firefox will not launch from the launcher. It starts going, there as an indication of something going on in the top panel, and then it's gone. But it leaves behind a couple of firefox processes.

It will launch just fine from a term or Alt-F2. After I deleted my profile and created a new one, it worked for a while, but is now doing the same thing again.

Any one else seeing this? Any ideas?

---

### Post by Harry33 on 2012-12-06
> **sgage said:**
> Suddenly Firefox will not launch from the launcher. It starts going, there as an indication of something going on in the top panel, and then it's gone. But it leaves behind a couple of firefox processes.

It will launch just fine from a term or Alt-F2. After I deleted my profile and created a new one, it worked for a while, but is now doing the same thing again.

Any one else seeing this? Any ideas?

What version of FF are you running?
Is it 18.0~b2+build1-0ubuntu1?
You could try stable version.
I am using the stable quantal version 17.0.1+build1-0ubuntu0.12.10.1
and that runs well.

---

### Post by lonniehenry on 2012-12-06
I have had programs that after updating will not launch from the launcher.  I just unlock from the launcher.  Start the program from dash or terminal and then lock the new instance to the launcher.

---

### Post by sgage on 2012-12-06
> **lonniehenry said:**
> I have had programs that after updating will not launch from the launcher.  I just unlock from the launcher.  Start the program from dash or terminal and then lock the new instance to the launcher.

I tried that first thing. No joy. I deleted the profile and had FF generate a new one, and it worked fine for a while, but then started failing again.

---

### Post by sgage on 2012-12-06
> **Harry33 said:**
> What version of FF are you running?
Is it 18.0~b2+build1-0ubuntu1?
You could try stable version.
I am using the stable quantal version 17.0.1+build1-0ubuntu0.12.10.1
and that runs well.

Yes, I'm using the 18.0 beta that Raring installs normally. I may try the quantal version. The odd thing is that it works just fine from terminal or Alt-F2.

---

### Post by jerrylamos on 2012-12-06
Having trouble with launcher Firefox on three pc's - netbook, notebook, tower.  Right click and select Firefox Web Browser usually works.  This bug popped up on Ringtail unstable (of course) a few days ago and still persists.

---

### Post by sgage on 2012-12-06
> **jerrylamos said:**
> Having trouble with launcher Firefox on three pc's - netbook, notebook, tower.  Right click and select Firefox Web Browser usually works.  This bug popped up on Ringtail unstable (of course) a few days ago and still persists.

Thanks for the confirmation, Jerry.

Not sure what the mechanism might be for this glitch, but I'm sure it will clear up soon enough. Some malformed .desktop file? who knows?

---

### Post by serdotlinecho on 2012-12-07
I don't have any problem to launch Firefox from Unity launcher but i get this square hole bug when bootup.

[IMG]http://ubuntuone.com/53J7L32e3nTDw7Zjt88wDx[/IMG]

Here's the video:
[http://www.youtube.com/watch?v=DOgAkxIeiO4&feature=youtu.be](http://www.youtube.com/watch?v=DOgAkxIeiO4&feature=youtu.be)

```
apt-cache policy unity compiz xorg firefox
unity:
  Installed: 6.12.0daily12.12.05-0ubuntu1
  Candidate: 6.12.0daily12.12.05-0ubuntu1
  Version table:
 *** 6.12.0daily12.12.05-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
compiz:
  Installed: 1:0.9.9~daily12.12.05-0ubuntu1
  Candidate: 1:0.9.9~daily12.12.05-0ubuntu1
  Version table:
 *** 1:0.9.9~daily12.12.05-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
xorg:
  Installed: 1:7.7+1ubuntu4
  Candidate: 1:7.7+1ubuntu4
  Version table:
 *** 1:7.7+1ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
firefox:
  Installed: 18.0~b2+build1-0ubuntu1
  Candidate: 18.0~b2+build1-0ubuntu1
  Version table:
 *** 18.0~b2+build1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by zika on 2012-12-07
What are these numbers on icons on the launcher?
I did not notice that at my place...

---

### Post by serdotlinecho on 2012-12-07
> What are these numbers on icons on the launcher?
I did not notice that at my place...

Unity shortcut hint overlay. Hold superkey and tap the number on keyboard :)

[IMG]http://i.imgur.com/rKGXm.png[/IMG]

---

### Post by zika on 2012-12-07
> **serdotlinecho said:**
> Unity shortcut hint overlay. Hold superkey and tap the number on keyboard :)

[IMG]http://i.imgur.com/rKGXm.png[/IMG]I do not have Super key... Old IBM keyboard, pre-pre-Win... I'll have to assign one... Thank You...
BTW how am I now going to add a new keyboard layout? It doesn't happen in SystemSettings, I should obviously have privilege... New teaser... I'll wait until I have enough time for that...

Update&#8321;: OK, I've changed Super to another combination and I can now test hints in Launcher... But the question about adding keyboard layout still stands (moved to a new thread: [http://ubuntuforums.org/showthread.php?t=2092243](http://ubuntuforums.org/showthread.php?t=2092243))...
(I must admit that most of the time I spend in dwm, spectrwm, fvwm so  I'm used to change keyboard layout through setxkbmap, but of course this  GUI way worked for me earlier, I do not know if it worked in RR...)
Thank You for heads up about new feature. I even like it... **Excuse me for off-topic here...**

---

### Post by cecilpierce on 2012-12-07
I get that square box up in the corner to for about 5 seconds !

---

### Post by sgage on 2012-12-09
I reinstalled Raring yesterday, and the FF launcher problem was still there. So I went to /usr/share/applications and had a look at firefox.desktop - figured I'd trim it down until it work. 

Phase 1 was to simply remove all the other languages from Name, Comment, Generic Name, etc., besides the first default entry, to make it easier to work with. Tried it out, and voila! It works as expected!

It seems like something among all those language choices is causing a problem...

[Edited: Ack! Spoke too soon! It only worked once, and then exhibited the same behavior. I cut it down to rock-bottom minimum, and it seems to work repeatedly now. I'll add in the other lines until it fails. I'd really like to know what's going on.]

[Edit 2: Got it in one - it was the line 'StartupNotify=true']

---

### Post by sgage on 2012-12-09
> **cecilpierce said:**
> I get that square box up in the corner to for about 5 seconds !

I get the square box at startup, too, but only for less than a second.

---

### Post by zika on 2012-12-09
Did You try disabling all add-ons that come about integrating Firefox to Ubunty, Unity,... and then re-enabling one by one, if You need them?

---

### Post by cecilpierce on 2013-02-08
Whats with that black box in the corner :mad:

---

