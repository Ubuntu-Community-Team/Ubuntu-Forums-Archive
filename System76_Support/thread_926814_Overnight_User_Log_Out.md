---
title: "Overnight User Log Out"
date: 2008-09-22
forum: System76 Support
---

### Post by jpoRS on 2008-09-22
Hey,

This is my first issue with my new System76, so if I forget to give you some commonly expected information, sorry.

I got my panp4i last week, and everything that should be working fine is, however whenever I leave some process running overnight, I get logged out and wake up to the log in screen.  I would really like that to not happen because it is going to take a couple hours for me to transfer files off of my old computer and I would like to get that done with.

It isn't some effect of the file transfer, because I didn't try to run a transfer last night, and it still logged me out.

Thanks for your help,
jim

---

### Post by thomasaaron on 2008-09-22
Hi, Jim.

There are a number of things that might be causing that.

Check in System > Prefs > Screensaver to make sure you don't have "Lock screen when screensaver is active" selected.

Also check in System > Prefs > Power Management to make sure your computer isn't being put to sleep when it is idle.

---

### Post by jpoRS on 2008-09-22
I tried that already.  Sorry.  I should have said so.

It isn't going to the screensaver password screen.  When I go to the computer in the morning, it is on the main Ubuntu log in screen.  

I don't know for sure if it is logging me out or if it is restarting the computer.  I suspect it is just logging me out because my sleep hasn't been disturbed by the sound of the Ubuntu drums.  However I am a heavy sleeper so that doesn't guarantee anything.

jim

---

### Post by thomasaaron on 2008-09-22
You might want to have a look in /var/log/syslog and /var/log/messages to see if there is an indicator of what caused it to shut down.

I assume you were running on ac power, right?

---

### Post by jpoRS on 2008-09-22
Ah ha!  From /var/log/messages

```
Sep 22 08:03:21 ubuntu syslogd 1.5.0#1ubuntu1: restart.

```

Now what?

And yes, AC power.  I mean battery life on this guy is pretty good, but I need more than three hours of sleep.

---

### Post by thomasaaron on 2008-09-22
There may be several instances of "restart" in there. You want to find the one that would correspond to the restart that must have happened in the middle of the night. The look at the lines before it to see why it shut down in the first place.

If you want to email me the file created on your desktop by running this command...

cat /var/log/messages > ~/Desktop/messages.txt

...I'll help you look through them.

support(at)system76(dot)com

---

### Post by jpoRS on 2008-09-26
For those who may be having the same problem:

Tom helped me go through my /var/log/messages and after finding

```
Sep 22 14:32:32 ubuntu kernel: [  482.722424] npviewer.bin[7090]: segfault at 4 rip f6e29d54 rsp ffca2da0 error 4

```

as the last message before a restart, Tom suggested that it may be my flash plugin causing trouble.  I removed and reinstalled my plugin (see [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash#amd64andppc") for more on that) and haven't had any problems since!

Thanks Tom!

jim

---

### Post by aifei on 2008-10-01
I am thinking about buying these cigarette filters and maybe one of these cigarette water filter pipes to try. Has anyone ever tried one of these? [www.LDUcompany.com](www.LDUcompany.com) has them on thier tobacciana page. There are two or three different types of cigarette filters and I am not sure if they are right for me. [http://www.liangdianup.com/tobacciana_1.htm](http://www.liangdianup.com/tobacciana_1.htm) is the page with all the smoking things. I would like to learn a little about these before I place an order. I heard that these are the next best thing besides quiting smoking and I ain't quiting.
:guitar::popcorn:

---

