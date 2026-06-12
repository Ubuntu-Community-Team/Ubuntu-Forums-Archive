---
title: "Sable Performance / Intel X3100 issues"
date: 2008-07-15
forum: System76 Support
---

### Post by randizzle on 2008-07-15
I am experiencing some very long screen drawing times when using some applications, ex. Firefox or Netbeans. It is most noticeable when using the desktop switcher.

It happens regardless of the level of eye candy I have enabled via compiz or emerald window manager, though the cube effect really stutters. 

I am using whatever drivers were pre-installed by System 76 when the machine was shipped. It is a 2.4 core 2 duo with 4 gigs of ram. 

I have browsed the forums and have not found any clear evidence that others are having this issue. Compiz functions correctly for me. I ran the compiz-check script just to be sure, it passed with flying colors. Direct rendering is on. I see no mention of the vesa driver in my xorg.conf. 

I am only slightly above newb level, so any and all help in debugging this problem would be greatly appreciated. One particular question I have; how can I determine if I have the latest and/or best driver?

---

### Post by thomasaaron on 2008-07-15
You don't really have to worry about making sure you have the latest video driver. New versions will come down via Update Manager whenever they are available.

Do you have the slow re-drawing times *all* the time? After the computer has been running a while? After resuming from hibernate/suspend? After a fresh start-up? With apps running? With no apps running?

Also, open a terminal and run this command...

top

...See if you can tell if anything is hogging cpu time. It will appear close to the top of the list. Take three or four screenshots of it consecutively after a slow re-draw (as it changes the listing frequently). Post them here and we'll have a lookie-see.

---

### Post by randizzle on 2008-07-16
It only seems to be when running some applications. I hope "redraw" is the right term, I will try and take a video of what I mean and post that. Applications take a unacceptably long time to come out of hide, and swithing between virtual desktops is very stuttery and chunky, if that makes sense.

BTW I have a CPU monitoring screenlet on my desktop, and have been keeping an eye on it as I have this problem. It doesn't seem to be related to the CPU, as it does not seem to be taxed when I see this issue.

I will post that viddy tonight...

Thanks!

---

### Post by thomasaaron on 2008-07-16
[http://ubuntuforums.org/showthread.php?t=500335](http://ubuntuforums.org/showthread.php?t=500335)

See if that sounds right.

---

### Post by randizzle on 2008-07-16
After some experimentation I think I have figured out what is going on.

The whole thing stank of memory leak.. but all of the software I am running is pretty stable and established, except two, AWN and screenlets. I stumbled across a thread on the AWN message board where a number of people were complaining that screenlets "crashed their desktop". I ran some tests and sure enough, that was the culprit. 

That's what I get for loading up on eye candy the day I get a new machine.

Sorry for the hassle, and thanks so much for your help!!

PS I love my System 76 :)

---

