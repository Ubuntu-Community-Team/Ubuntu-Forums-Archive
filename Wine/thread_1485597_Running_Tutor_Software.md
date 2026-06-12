---
title: "Running Tutor Software"
date: 2010-05-17
forum: Wine
---

### Post by trevzilla on 2010-05-17
Hi!  First off, I want to mention that I am a complete newbie to Ubuntu, and Wine.  So, sorry if this is a silly question.

I work through tutor.com, and they have proprietary software that supposedly only works on Windows.  They say that you can't run it on a Mac, however there is no documentation about running it in Ubuntu.  I figured it might work in Wine, but so far haven't had much luck.  I was wondering if there are more things I can try to get this software running or if I am SOL.

I installed the .msi installer file through wine, and everything seemed to install fine.  I got to a window that said the software installation was successful.  When I try to run it however, a tab saying "Starting Tutor.com Classroom" opens on the taskbar.  My screen does a quick flicker to black, then the whole thing pauses for a second and the tab disappears.  After that, nothing happens.  The tutoring software does not open.

Any thoughts on what the problem could be?  Or if it will even work in the first place?

Thanks!
Trevor

---

### Post by asdfoo on 2010-05-18
> **trevzilla said:**
> Hi!  First off, I want to mention that I am a complete newbie to Ubuntu, and Wine.  So, sorry if this is a silly question.

I work through tutor.com, and they have proprietary software that supposedly only works on Windows.  They say that you can't run it on a Mac, however there is no documentation about running it in Ubuntu.  I figured it might work in Wine, but so far haven't had much luck.  I was wondering if there are more things I can try to get this software running or if I am SOL.

I installed the .msi installer file through wine, and everything seemed to install fine.  I got to a window that said the software installation was successful.  When I try to run it however, a tab saying "Starting Tutor.com Classroom" opens on the taskbar.  My screen does a quick flicker to black, then the whole thing pauses for a second and the tab disappears.  After that, nothing happens.  The tutoring software does not open.

Any thoughts on what the problem could be?  Or if it will even work in the first place?

Thanks!
Trevor

Hi Trevor

Does this program work with firefox or opera on windows?  

If so, you should install the windows version of either of these in Wine along with the tutor software.  Start the Windows version of the browser through Wine and the plugin should work.

If you have already tried this then also make sure you are testing with a recent version of Wine. 1.1.44 is the most recent.

If it does not work with 1.1.44 then you could try submitting a bug report at the main winehq website and a developer may assist.

---

### Post by beastrace91 on 2010-05-19
IF you cannot get it working through Wine a Windows VM is another option for non-3d Windows software you need under Ubuntu/Linux.

~Jeff

---

### Post by trevzilla on 2010-05-19
> **asdfoo said:**
> 

Does this program work with firefox or opera on windows?  



Well, the software is not run through a browser.  The student does open a browser to get tutoring help, but the tutor simply opens a program called "the classroom."  It does however somehow use Internet Explorer as a default browser.  For example, if I log in to change my hours, the classroom opens IE so I can view my hours, even though Google Chrome is my default browser.

I'm checked that I am running the latest version of Wine also.

I'll give Windows VM a try, and also maybe submit a bug report.  Thanks for the suggestions!

Trevor

---

### Post by nicopotus on 2011-02-09
Did you guys succeed?

---

### Post by ari.maidana on 2011-02-10
I installed it successfully under Crossover Linux Standard, but it doesn't run (I just get an error message when I try to start it).

---

