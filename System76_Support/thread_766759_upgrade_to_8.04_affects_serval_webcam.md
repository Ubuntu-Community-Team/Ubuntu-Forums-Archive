---
title: "upgrade to 8.04 affects serval webcam"
date: 2008-04-25
forum: System76 Support
---

### Post by deeGraYve on 2008-04-25
during upgrade motion was attempted to install which went into infinite loop of detection motion using my webcam. I had to ^C it and finish up upgrade without it. Once 8.04 was installed though - I could not access my webcam, none of the programs that used to work with webcam do that anymore. Cheeze, wxcam, skype - none of them work. What makes it even worse the project I worked on for a year and have to present in 3 days - stopped working as well. it uses opencv library to acquire video stream from the webcam.

should I go back to 7.10? did anyone else experience the same problem?

---

### Post by kobayashison on 2008-04-25
I had the same problem upgrading from gutsy to Hardy. In update-manager terminal window was possible to see output of "motion" and I needed to ^C too. After upgrade it was all ok.

---

### Post by deeGraYve on 2008-04-25
yes, i did the same, 8.04 is up and running
but either something has happened to my webcam driver or motion messed something up, because now i cannot grab webcam's stream from any other programs, even from motion that was happily detecting motion and saving the pictures infinitely during the upgrade...

---

### Post by 5of0 on 2008-07-13
> **deeGraYve said:**
> during upgrade motion was attempted to install which went into infinite loop of detection motion using my webcam. I had to ^C it and finish up upgrade without it. Once 8.04 was installed though - I could not access my webcam, none of the programs that used to work with webcam do that anymore. Cheeze, wxcam, skype - none of them work. What makes it even worse the project I worked on for a year and have to present in 3 days - stopped working as well. it uses opencv library to acquire video stream from the webcam.

should I go back to 7.10? did anyone else experience the same problem?

I had the same problem - upgraded to 8.04, had to ^C out of motion install, and my webcam wasn't working.  Cheese just showed a test pattern, and Camorama refused to work.  Motion wasn't even working - there was something about the webcam being busy.
I hadn't thought about a possible connection to the failed motion install, though, until I read your post.  Then, on a hunch, I did a
```
sudo killall motion
```
in a terminal.  After that, Cheese works flawlessly!  Camorama still doesn't, but it never did, anyway, even in 7.10.  Thanks for the post, and hopefully this will catch some Google results and help people in my situation.

For the record, and for Google, I'm on a Dell Vostro 1500 with an Omnivision built-in webcam, on which upgrading to Ubuntu 8.04 Hardy Heron broke my webcam, and it is now broken.
(Just a little keyword baiting there :P)
Some related bugs:
[https://bugs.launchpad.net/ubuntu/+source/motion/+bug/235599](https://bugs.launchpad.net/ubuntu/+source/motion/+bug/235599)
[https://bugs.launchpad.net/ubuntu/+source/motion/+bug/198292](https://bugs.launchpad.net/ubuntu/+source/motion/+bug/198292)
[https://bugs.launchpad.net/ubuntu/+source/motion/+bug/242459](https://bugs.launchpad.net/ubuntu/+source/motion/+bug/242459)
I am still not sure if this is a permanent fix, I'll post here if I find anything else out, and of course, anyone who knows more is welcome to weigh in :)

Edit: on a reboot, motion was still interfering.  After some googling, I decided to disable the service on startup.  To do so, run the SysV Runlevel config from a terminal:
```
sysv-rc-conf
```
You can then arrow down to motion and hit the spacebar to uncheck "motion" under each runlevel.  If you're curious as to what all the numbers are, check out the [wikipedia article]("http://en.wikipedia.org/wiki/Runlevel") on them.  Let me know if this helps!

---

