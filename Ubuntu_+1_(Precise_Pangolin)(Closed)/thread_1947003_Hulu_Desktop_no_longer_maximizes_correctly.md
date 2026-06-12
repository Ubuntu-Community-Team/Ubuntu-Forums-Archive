---
title: "Hulu Desktop no longer maximizes correctly"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dsfitzpat on 2012-03-25
The Hulu Desktop program (for accessing Hulu videos in the US) used to run full-screen on Ubuntu 11.10 and earlier; this was the default behaviour when the 'maximize' button was pressed.
In 12.04 the video is no longer full-screen when maximized - it doesn't cover the top panel, and if the launcher is not set to autohide, it will not cover that either.
Has anyone else noticed this? (I guess the intersection of the sets of beta testers and Hulu desktop users is probably pretty small, but you never know...)
I'll try reinstalling or digging around in the .huludesktop settings file to see if I can change anything; if I have no luck I guess the best bet will be to return to running full-screen flash off of the Hulu website.
(The desktop program is also flash-based but has some extra tools for interacting with a remote control.)

---

### Post by wojox on 2012-03-26
I concur. Plugged my laptop into my big screen last night and noticed this. I thought is was an issue with my video drivers and the tv.

If anyone else may know. If the package is not in the repo's and you download the .deb from the hulu site, where would you file a bug?

---

### Post by cariboo on 2012-03-26
There should be a file in /usr/share/doc/whatever-the-applications-name-is. The authors name should be in the copyright file.

---

### Post by x-shaney-x on 2012-03-26
A few apps aren't maximizing fully for me in Unity 3D though all are working in 2D.
Try 2D and see if it maximizes correctly there?

---

### Post by dsfitzpat on 2012-03-26
I can confirm that the old behaviour still persists in Unity 2D - it runs properly at full screen there. I also checked that this is a compiz problem and not just a Unity problem - running Gnome Classic with compiz enabled, full-screen does not cover the panels and comes with window decorations. I'll attach screen shots for Unity 2D and 3D.

On the Hulu Labs website there's a discussion forum where you can leave comments. I think these are actually read by the people developing this program for Hulu but I'm not 100% sure.

---

### Post by wojox on 2012-03-27
> **cariboo907 said:**
> There should be a file in /usr/share/doc/whatever-the-applications-name-is. The authors name should be in the copyright file.
:oops: Forgot about that. The control file has <support@hulu.com>

It's all binary as well so no patching the source and building. :mad:

> **dsfitzpat said:**
> 
On the Hulu Labs website there's a discussion forum where you can leave comments. I think these are actually read by the people developing this program for Hulu but I'm not 100% sure.
I'll post a thread @ the discussion forum. :KS

---

### Post by dsfitzpat on 2012-04-01
I didn't notice anything posted so far on the discussion forum, so I added a post. The forum is here: [http://www.hulu.com/discussions/19](http://www.hulu.com/discussions/19)
The developers for Hulu Desktop seem to be pretty good about responding, so I'll update here if I hear anything.

---

### Post by wojox on 2012-04-01
I sent an email. Sorry about that. Haven't heard anything. 

Now it's segfaulting on me. I'm wondering if it has to do with the Gnome 3.4 release?

---

