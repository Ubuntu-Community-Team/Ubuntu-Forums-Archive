---
title: "Apport doesn't let me report a bug"
date: 2015-06-14
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-06-14
Sometimes a crash occurs on my Xubuntu and Apport reports it to me. 

On Ubuntu, when I choose to report the bug, apport opens a Firefox's window in Launchpad where it collects the data and lets me enter more details about the crash. On Xubuntu I can't do this. Apport reports the crash to me, but when I choose to report it nothing happens. No firefox tab is opened and I suppose the bug is not really reported in Launchpad.

Is it a bug? I wasn't able to report a bug with 15.04 too

---

### Post by dino99 on 2015-06-14
chown that crash file to your user

---

### Post by enricobe on 2015-06-14
> **dino99 said:**
> chown that crash file to your user

What? Sorry but I can't understand what do you mean :)

---

### Post by dino99 on 2015-06-14
s> udo chown user:user /var/crash/crashfile  (replace user & crashfile by the required names)

---

### Post by enricobe on 2015-06-14
> **dino99 said:**
> s  (replace user & crashfile by the required names)

When I launch the command 

```
enrico@enrico-linux:/var/crash$ sudo chown user:enrico /var/crash/_usr_bin_calibre.1000.crash 
```

returns

```
chown: utente non valido: "user:enrico"
```

that means "enrico is not a valid user". Really strange.


Anyway, why I need to own the crash file? Can this help me to understand why I can't automatically report a bug on launchpad? Thanks a lot for your help

---

### Post by dino99 on 2015-06-14
try:
> sudo chown enrico:enrico /var/crash/*
supposing 'enrico' is your login name

---

### Post by enricobe on 2015-06-14
> **dino99 said:**
> try:

supposing 'enrico' is your login name

Thank you, the command worked fine. What can I do now?

---

### Post by cariboo on 2015-06-14
You can't create a bug report against calibre, as it isn't installed as a normal package from the repositories. If you want to create a bug report against it, see [here]("http://calibre-ebook.com/bugs").

---

### Post by mc4man on 2015-06-14
Your post is a bit confusing, at least to me. You say Ubuntu opens LP reports on crashers. If you mean on Ubuntu wily or even vivid then apport LP reporting has been disabled. It generally isn't re-enabled in the -dev package till later in dev process.
Till it's re-enabled  apport crashers go to a db (whoopsie

ex.
> apport (2.17.2-0ubuntu1) vivid; urgency=medium

 -clipped
  * Disable Launchpad crash upload for final Ubuntu 15.04.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 16 Apr 2015 17:51:18 -0500

---

### Post by dino99 on 2015-06-14
> **cariboo said:**
> You can't create a bug report against calibre, as it isn't installed as a normal package from the repositories. If you want to create a bug report against it, see [here]("http://calibre-ebook.com/bugs").

I's a normal ubuntu package, found in the archive; so ubuntu-bug can be used i suppose, like with any other package

[https://launchpad.net/ubuntu/+source/calibre](https://launchpad.net/ubuntu/+source/calibre)

---

### Post by enricobe on 2015-06-14
Maybe I was not so clear describing the problem. I don't want to report a calibre bug, the bug report (apport) doesn't work on my notebook.

On ubuntu:
-A program crashes
-Apport automatically opens a screen like [this]("http://2.bp.blogspot.com/-Sp7jXNrF1fA/T-CNOEkuj1I/AAAAAAAAJI0/0pv01MhnwVU/s1600/ubuntu-apport.png") (random image from the web)
-When I press CONTINUE, the window closes and a Firefox tab is opened on Launchpad.
-From Launchpad's web page I can add all the details about the bug and submit the bug

On Xubuntu:
-A program crashes
-Apport automatically opens a screen like [this]("http://2.bp.blogspot.com/-Sp7jXNrF1fA/T-CNOEkuj1I/AAAAAAAAJI0/0pv01MhnwVU/s1600/ubuntu-apport.png") (random image from the web)
-When I press CONTINUE, the window closes and nothing happens

---

### Post by Mateusz Stachowski on 2015-06-14
You are running now the development release or a stable release. If it is stable release then the crash is [sent automatically]("https://wiki.ubuntu.com/ErrorTracker") to errors.ubuntu.com (see the "Anatomy of a crash, in detail" on that linked web page) and you won't get web page to report bug.

Check the /var/crash directory and see if there are any files with .upload and .uploaded extension besides the .crash one.

Also you could report the bug manually:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

> cd /var/crash
ubuntu-bug my_crash_report.crash

---

### Post by enricobe on 2015-06-14
> **Mateusz Stachowski said:**
> You are running now the development release or a stable release. If it is stable release then the crash is [sent automatically]("https://wiki.ubuntu.com/ErrorTracker") to errors.ubuntu.com (see the "Anatomy of a crash, in detail" on that linked web page) and you won't get web page to report bug.

Check the /var/crash directory and see if there are any files with .upload and .uploaded extension besides the .crash one.

Also you could report the bug manually:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I'm using 15.10, development version. Very interesting page, I'll read it more carefully when I have some free time. Thank you ;) So it seems this is the normal behavior... Now I can't understand why when I was using ubuntu it always opened a Firefox page for add details...

---

### Post by mc4man on 2015-06-14
> **enricobe said:**
> I'm using 15.10, development version. Very interesting page, I'll read it more carefully when I have some free time. Thank you ;) So it seems this is the normal behavior... Now I can't understand why when I was using ubuntu it always opened a Firefox page for add details...
That is in 12.04 where apport is a bit different & apparently doesn't use the db judging from what you've said. All the more recent Ubuntu releases will only open LP reports on crashes during a limited period in the dev. 
(ubuntu-bug always opens a LP report but that's not the question here.

---

### Post by MikeMecanic on 2015-06-14
Check if APPORT is enable? Under Ubuntu it's most of the time enable.  Enabled=1 /To turn it off make it:  Enabled=0

```
sudo -i gedit /etc/default/apport
```
or 
```
sudo nano /etc/default/apport
```

You must also enable *send error reports to Canonical* in Privacy.   

Regards,

---

### Post by mc4man on 2015-06-14
It's a single line in a file that controls this. No sense mentioning as that would sort of defeat the purpose of not spamming LP with bug reports early in dev or at /  after release. That's really the whole deal...

---

### Post by enricobe on 2015-06-15
I've understood that this is the right behavior of Apport, isn't it?

If a program crashes, an apport window opens up and lets the user choose if send the report or not. When the user press Continue no other window should open.

---

### Post by dino99 on 2015-06-15
> **enricobe said:**
> I've understood that this is the right behavior of Apport, isn't it?

If a program crashes, an apport window opens up and lets the user choose if send the report or not. When the user press Continue no other window should open.

As previously said, with a dev release like Wily, apport is deactivated to stop useless reports being sent, at least the 2 first months of development.

---

### Post by MikeMecanic on 2015-06-15
> apport is deactivated to stop useless reports

In the huge Ubuntu Wily Werewolf Data Base, there ain't no useless reports, t_here's a team working on it every single morning_. **Enable it!**  Your testing Wily Werewolf future.  In my case, it's always enable and I do the inverse when I play in deep settings: Edit enable=0


All the best,

---

### Post by MikeMecanic on 2015-06-15
> apport is deactivated to stop useless reports

In the huge Ubuntu Wily Werewolf Data Base, there ain't no useless reports, t_here's a team working on it every single morning_. **Enable it!**  Your testing Wiliy werewolf.  In my case, it's always enable and I do the inverse when I play in deep settings: Edit enable=0


All the best,

---

### Post by MikeMecanic on 2015-06-15
> apport is deactivated to stop useless reports

In the huge Ubuntu Wily Werewolf Data Base, there ain't no useless reports, t_here's a team working on it every single morning_. **Enable it!**  Your testing Wily werewolf.  


All the best,

---

### Post by mc4man on 2015-06-16
> **enricobe said:**
> I've understood that this is the right behavior of Apport, isn't it?

If a program crashes, an apport window opens up and lets the user choose if send the report or not. When the user press Continue no other window should open.
Yes, you've got it.. apport *is* enabled & will upload your crash report to a db. 
At some point crashers will start opening a LP report, till then the ^ applies.

---

