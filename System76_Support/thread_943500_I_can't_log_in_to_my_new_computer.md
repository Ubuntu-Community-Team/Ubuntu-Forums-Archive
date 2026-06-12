---
title: "I can't log in to my new computer"
date: 2008-10-10
forum: System76 Support
---

### Post by Modax42 on 2008-10-10
It started when I figured I would try the 8.10 beta live CD with my Darter Ultra.  It didn't boot from the CD and went straight to the normal login page.  Now, whenever I enter my user name, it just hangs, and all I can do is either reboot or ctrl+alt+backspace to try to login again.  I've tried it about 10+ times now, including from a cold boot a couple of times. when I enter a username other than my REAL username, I get prompted for a password, but with my actual login it justs hangs, and the username text appears grey.

I can't get it to boot from the live CD.  On my compaq, it would automatically boot from the DVD drive, but my darter always boots straight from the HDD.  I have tried trying to boot into my regular account with no DVD in the drive, but it made no difference.  I have looked at all the threads with similar names, but they don't seem to be having the same problem.

You guys are wonderful, you've all been extremely patient with all of my stupid questions, but this time I really need help!

---

### Post by Modax42 on 2008-10-10
I found these instructions at this website:
[http://techteam.wordpress.com/2007/01/30/i-cant-log-into-ubuntu/](http://techteam.wordpress.com/2007/01/30/i-cant-log-into-ubuntu/)

>  Step 1) Start the PC in recovery mode: This is done by re-booting and pressing the esc key and selecting (recovery mode) from the start up menu. This opens a terminal session as root.

Step 2) Add a new user at the command line: You know the drill

I don't know the drill. What's the command to add a user in the terminal?

---

### Post by Modax42 on 2008-10-10
Okay.  I created a new user account, gave it admin priviledges, and now it lets me log in. :guitar:

Now I'm really curious:

what went wrong?
How can I fix my old account?

---

### Post by thomasaaron on 2008-10-10
Slow down just a bit. It sounds like you're somewhat new to Ubuntu, so I would definitely avoid trying a whole lot of random things when you encounter a problem. That's a great way to really hose something.

You also might want to just email me directly (support(at)system76(dot)com for a faster turn-around on support. You can also call me (phone # is on the website).

First, it sounds like you have the fingerprint reader activated. When it grays out on the login screen, try swiping your finger over the reader.

Second, to boot from a live CD you have to go into your BIOS and set your dvd drive up as your first boot device. If you created your live cd as an image, it will boot. If you saved it as a data file, it will not.

---

### Post by Modax42 on 2008-10-10
Yep, that was it!  I back in my regular account now.  What a relief.  That gave my a real scare, there.  Since there is no prompt telling you to swipe your finger, I never thought of doing so, as I had had no success in getting it to recognize my fingerprint once it had scanned it.  Once I started panicking, the fingerprint reader was the last thing on my mind!

Thank you so much for your patience.

---

### Post by thomasaaron on 2008-10-10
No problem.

I had a customer send a machine in for repair, and the same thing happened when I tried to log into her account to check things out.

It definitely makes it look like something is badly hosed if you're not expecting it. Multiply that by 10 if you haven't had your morning coffee yet.

Let me know if you need anything else.

---

