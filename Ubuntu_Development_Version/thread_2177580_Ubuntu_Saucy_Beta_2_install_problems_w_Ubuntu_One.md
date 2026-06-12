---
title: "Ubuntu Saucy Beta 2 install problems w/ Ubuntu One"
date: 2013-09-29
forum: Ubuntu Development Version
---

### Post by taxman10m on 2013-09-29
At the part of the install where the user is prompted to enter Ubuntu One login info, I apparently typed the password wrong once.  Then typed what I thought was the password a second time.  The install appeared to freeze at that point.  I was doing the install on a Dell Inspiron 15R laptop and took a picture of the screen at that point.  I was connected to wifi at the time.

I then found out that if I moved the window off to the side there was another window behind it saying that Ubuntu had experienced an error and would I like to submit it.  I accepted that window and then there was a popup asking if I would also submit debug info.  I intended to do this, but unfortunately I didn't realize quick enough that the prompt is reversed from normal.  Instead of Yes and then No.  It is No and then Yes.  So I ended up not submitted the debug info.  (Later, I ran through the install again and clicked Yes to submit debug info but then got a message that I couldn't submit the bug twice.  Ah well...)

The error is fatal and aborts the install.  Running it a third time and selecting "Log in later" makes the install proceed fine.

---

### Post by jerrylamos on 2013-09-29
I never could get anywhere with Ubuntu One window.  I just select the left hand choice about doing it later (maybe years later, in my case).

---

### Post by grahammechanical on 2013-09-30
This has been known about since the feature was first introduced. It was still there with the daily image of the 25th. I did not see the crash report that you noticed but I could not continue with the install session until I clicked Login Later, and even then the install session was broken. Like you I was able to get past this blockage by clicking Login Later.

My guess is that the installer is not connectiing to the Ubuntu One database to either create a new account (which I have not tried to do) or verify the returned user. I am not sure if thrusting this screen into people's faces like this without any warning is a good way to go about getting people signed up to Ubuntu One logins, at least not with well thoughtout passwords.

Regards.

---

### Post by J._R._Menzie on 2013-10-02
I agree with you. I did the install a couple of times before I gave up. This should be fixed ASAP! Why introduce features that don't work? Ubuntu tends to do this. Either regression or broken system, at this point in the OS development cycle, unacceptable.

---

