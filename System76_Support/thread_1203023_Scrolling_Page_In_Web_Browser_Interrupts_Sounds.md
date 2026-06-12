---
title: "Scrolling Page In Web Browser Interrupts Sounds"
date: 2009-07-02
forum: System76 Support
---

### Post by Cygnia on 2009-07-02
Greetings, firstly if I should be posting this elsewhere please feel free to correct me and I will...

I have a PanP4n that otherwise is running nicely with Jaunty and all latest updates that has developed the weird problem that about every other time I scroll a webpage in Firefox the music or other sounds will be interrupted then resume. At first I thought it was related to the use of the bluetooth mouse that I recently began using in place of USB, but then observed that it happens while scrolling with the arrow keys on the keyboard as well. Is there a particular log or process I should check? Thanks for any pointers anyone may have.

---

### Post by thomasaaron on 2009-07-03
No, this is a good place to post it since you have a System76 computer. 
However, I've not heard of this one yet. Is anyone else experiencing this?

Looks like it might be related to this bug...
[https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-April/074946.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-April/074946.html)

But that's the only mention I see of it.

You could look at /var/log/syslog to see if there are any messages when you scroll. Not the time that you scroll to make the messages easier to locate.

Did you upgrade to Jaunty or do a fresh install (or did your machine come with it)?

---

### Post by Cygnia on 2009-07-03
Hi Thomas, thanks for the reply. I got the behavior to repeat at 8:35am by scolling (this time with the mouse wheel.) Here is the part of /var/log/syslog that includes that time period, but there isn't anything I can see there:

Jul  3 08:30:01 cygniapolis /USR/SBIN/CRON[2967]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  3 08:40:01 cygniapolis /USR/SBIN/CRON[3267]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

I upgraded to Jaunty from the Update Manager the very day it was released, but I'm pretty sure this is a recently encountered problem. Thanks again.

---

### Post by matt79 on 2009-07-03
Is your computer older? If it has less processing power I believe your problem might be that the computer can only do so much at one time. It plays the music until you scroll.......then when you do scroll it might take the resources from playing the music to scrolling the page. Just a thought though. You can see your resource usage by going to Systems--Administration--System monitor. Then click the Resources tab.

---

### Post by thomasaaron on 2009-07-03
Yeah, those logs have nothing to do with it. They are for update-motd which is checking from updates on your system.

There were a ton of problems with the Intrepid > Jaunty online update, particularly early on.

I'll google around some more and see if I can find anything. Which sounds are breaking up? Completely external-to-Firefox stuff like rythm-box? Audio in DVD playback? Youtube audio?

---

### Post by Cygnia on 2009-07-04
Hi, sorry for the late response, I was out all day yesterday. Yes it happens during Rhythmbox playing songs, but I've been trying to duplicate it during other programs and youtube videos but it seems to only be Rhythmbox. Banshee seems to not cause the same behavior. Maybe I should delete the cache file for Rhythmbox, if there is one? Thanks for your time. I'll try to jigger around on my own and report back if I solve it.

---

### Post by thomasaaron on 2009-07-06
Check out this thread...

[http://ubuntuforums.org/showthread.php?t=766860](http://ubuntuforums.org/showthread.php?t=766860)

---

