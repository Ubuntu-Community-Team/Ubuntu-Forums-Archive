---
title: "Is this a trojan horse?"
date: 2011-08-12
forum: Security
---

### Post by orangep on 2011-08-12
I just did a routine update of Ubuntu two days ago, using dselect, and now each time that I reboot and log in, a message pops up that says:

    *  System program problem detected
    *  Do you want to report the problem now?

If you answer "yes", you get:


    *  Please enter your password to access problem reports of system programs

Wow, does that sound like phishing. I enter a bogus password, and the
dialog box disappears, and nothing seems to happen.

Is this for real, or has a bug gotten into the system?

---

### Post by haqking on 2011-08-12
> **orangep said:**
> I just did a routine update of Ubuntu two days ago, using dselect, and now each time that I reboot and log in, a message pops up that says:

    *  System program problem detected
    *  Do you want to report the problem now?

If you answer "yes", you get:


    *  Please enter your password to access problem reports of system programs

Wow, does that sound like phishing. I enter a bogus password, and the
dialog box disappears, and nothing seems to happen.

Is this for real, or has a bug gotten into the system?

can you show us a screen dump ?

---

### Post by cariboo on 2011-08-13
> **orangep said:**
> I just did a routine update of Ubuntu two days ago, using dselect, and now each time that I reboot and log in, a message pops up that says:

    *  System program problem detected
    *  Do you want to report the problem now?

If you answer "yes", you get:


    *  Please enter your password to access problem reports of system programs

Wow, does that sound like phishing. I enter a bogus password, and the
dialog box disappears, and nothing seems to happen.

Is this for real, or has a bug gotten into the system?

Yes you ran into a bug, what you saw was the Ubuntu automated bug reporting system (apport) in action, if you had entered your password, you would have been taken to [bugs. launchpad.net]("https://bugs.launchpad.net"), if you don't have a Launchpad account all ready, you would have been asked to create an account, after you have logged in, you would have been asked to create a bug report.

---

### Post by orangep on 2011-08-16
Ah, thank you for the answer.

You know, the system programmers really should give a little more information there.  Or a lot more information. Just asking for someone's password looks for all the world like phishing:

"You have a virus in your system. Please type your password to get rid of it."

Oh well, thanks, and have a good day.

---

### Post by cariboo on 2011-08-16
You usually get a window popping up that a problem has occurre, it asks if you want to report it, or cancel.

Keep in mind that there are no active viruses for Linux at the moment, so there is no mechanism to report if one has been encountered. The majority of exploits on a Linux distribution are either social engineering, or faulty setup.

---

### Post by lazyr78 on 2011-08-24
The same has happened to both users on my Ubuntu 11.04 box today. One user got the message after installing the latest updates. The other user (me) got it after logging in. When I saw it, my gut reaction was also that it might be a trojan. I did not enter any password, but I will be sure to take a screenshot and try a fake password if it appears again.

The developers of this dialog -- if it is an authentic Ubuntu dialog -- should *really* work on making it look more convincing.

ps. I've added these two repositories to **/etc/apt/sources.list**, (for sun-java and spotify), and I figure an update from one of them *might* also be responsible.

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

Also, I've installed the latest ATI Catalyst drivers and all the games from the third Humble Bundle, so there are quite a few likely (and harmless) culprits that are not part of official Ubuntu.

---

### Post by lazyr78 on 2011-08-24
Logging out and back in again had the dialog reappear after a little while. There are several things I think stands out:

 - The window does not have any title.
 - It does not say what program had the problem.
 - It does not say what sort of problem.
 - If you select report problem, and type in a wrong password, both the password dialog and the first dialog disappears and *nothing* happens. No "wrong password, try again" and the first dialog with cancel/report choices is gone -- it's as if the problem never occurred.
 - On a positive note: both dialogs gets translated if the user language is altered.

I've made some further investigations:

 - The argv[0] of the program is update-notifier
 - /proc/<pid>/exe points to /usr/bin/update-notifier
 - its md5sum is 59dd11e0013e00babfa9ef592a739ebc (I've not checked if this is the md5sum its supposed to have)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200704&stc=1&d=1314209726[/IMG]

So in summary, these two dialogs manages to set off several of my rater well-honed trojan warning bells, but after investigating it seems rather likely to me it is just bad UI design.

---

### Post by MetapostAddict on 2012-08-15
definitely a poorly designed message box.  I got the same thing, and it immediately aroused my suspicion.

---

