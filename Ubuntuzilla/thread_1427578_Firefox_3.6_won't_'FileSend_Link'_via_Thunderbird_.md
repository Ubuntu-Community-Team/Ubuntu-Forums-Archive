---
title: "Firefox 3.6 won't 'File/Send Link' via Thunderbird 3.0.3"
date: 2010-03-11
forum: Ubuntuzilla
---

### Post by mlnease on 2010-03-11
Hello,

Just upgraded to Firefox 3.6 and Thunderbird 3.0.3 in Karmic--thanks, Ubuntuzilla.  All went smoothly except that I can't email links via 'File/Send Link' as before.

I opened both from the command line and tried again; there was zero command line output.

Any ideas?

Thanks in advance.

mike

---

### Post by rewyllys on 2010-03-12
> **mlnease said:**
> . . . . All went smoothly except that I can't email links via 'File/Send Link' as before. . . .

Just a few minutes ago I encountered this same problem.  It's definitely associated with Firefox/Swiftox 3.6, to which I upgraded from 3.5.something just two days ago.

---

### Post by rewyllys on 2010-03-12
After browsing through other reports of similar problems (as yielded from a Google search), I think I've found the answer.

In Firefox [or Swiftfox], you go to Edit > Preferences > Applications.  Scroll down to "mailto" and click on the drop-down sign; then choose your preferred application.  If your preferred application is not already in the list under drop-down, choose "Use other...".   

If you've had to choose "Use other...", what comes next?  Here's an example of how to proceed.  

Suppose, for example, that your preferred application is Thunderbird (and that it is not in the list under drop-down).  Then the next thing to do is to find out where Thunderbird is.  Open a Terminal window, and issue the command "whereis thunderbird".  You'll probably see a number of responses, such as "/usr/bin/thunderbird", "/usr/lib/thunderbird", and so on.  I first checked on /usr/bin/thunderbird and learned that it was just a symbolic link to /usr/bin/thunderbird, so I figured that the latter choice would be the slightly faster one to use.

Knowing this, I opened the "Select Helper Application" window, and went to Filesystem > usr > lib > thunderbird .  At this point, I clicked on the "Open" option in the "Select Helper Application" window, and thus made my choice.  The result was that the "mailto" line in my "Firefox [or Swiftfox] Applications" window reads "Use thunderbird".

---

### Post by mlnease on 2010-03-20
Hi rewyllys,

> **rewyllys said:**
> After browsing through other reports of similar problems (as yielded from a Google search), I think I've found the answer.

In Firefox [or Swiftfox], you go to Edit > Preferences > Applications.  Scroll down to "mailto" and click on the drop-down sign; then choose your preferred application.  If your preferred application is not already in the list under drop-down, choose "Use other...".   

If you've had to choose "Use other...", what comes next?  Here's an example of how to proceed.  

Suppose, for example, that your preferred application is Thunderbird (and that it is not in the list under drop-down).  Then the next thing to do is to find out where Thunderbird is.  Open a Terminal window, and issue the command "whereis thunderbird".  You'll probably see a number of responses, such as "/usr/bin/thunderbird", "/usr/lib/thunderbird", and so on.  I first checked on /usr/bin/thunderbird and learned that it was just a symbolic link to /usr/bin/thunderbird, so I figured that the latter choice would be the slightly faster one to use.

Knowing this, I opened the "Select Helper Application" window, and went to Filesystem > usr > lib > thunderbird .  At this point, I clicked on the "Open" option in the "Select Helper Application" window, and thus made my choice.  The result was that the "mailto" line in my "Firefox [or Swiftfox] Applications" window reads "Use thunderbird".

Thanks for your response, somehow I missed it.  I figured out today, though, that yes, the solution is in selecting the correct application in System > Preferences > Preferred Applications > Mail Reader--pretty much the same thing you've done from a slightly different angle.  Done and done.

Thanks again for your time and attention.

mike

---

