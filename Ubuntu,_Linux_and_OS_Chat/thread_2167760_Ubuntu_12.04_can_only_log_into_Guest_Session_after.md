---
title: "Ubuntu 12.04 can only log into Guest Session after &quot;sudo reboot&quot;"
date: 2013-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Petro Dawg on 2013-08-14
I am posting this so that others will be able to fix this problem if it occurs to them (and to rant a bit).


When shutting down Ubuntu 12.04, I was warned that I had an open (unsaved) program running.  I hit CANCEL to stop the shutdown process.  At that point my "taskbar" and program launcher had already been killed.  I proceeded to save the open program and then called up terminal to **sudo reboot** to resume shutting down the computer. Apparently that was a mistake....


After restarting my computer and when trying to log back into Ubuntu, I kept getting spat back out to the log-in screen.  I was only able to log in as Guest.  After a Google search in the Guest session I learned this was a "common issue" which requires booting up a live session (I used Puppy) and deleting the hidden "**.Xauthority**" file in the home folder of the affected account.  After that, I rebooted and logged in as normal.


So my (somewhat rhetorical) questions are...

Why does Ubuntu always kill the taskbar and launcher **before** asking if you want to cancel the shutdown process?  It's just my humble opinion, but the "open window / unsaved work" check should occur before anything is killed.

Has this issue been fixed on later versions of Ubuntu?  If so, why is it still a problem on the LTS version?  I mean, I use an LTS version thinking that all the little bugs will be ironed out during its lifespan.  Does it only receive security updates without addressing major known bugs for the rest of it's life span?
 
Is Ubuntu's goal to drive people away from terminal commands?  I typically flow back and forth, using terminal about as seamlessly as GUI and I like having the option to do either.

Finally, is there a correct way to shut down after pressing the CANCEL shut down button; when the GUI options are gone?


Don't get me wrong, I like Ubuntu a lot (it's still my favorite OS), but I understand why stuff like this would drive people away from using it.

---

### Post by cariboo on 2013-08-15
> **Petro Dawg said:**
> I am posting this so that others will be able to fix this problem if it occurs to them (and to rant a bit).


When shutting down Ubuntu 12.04, I was warned that I had an open (unsaved) program running.  I hit CANCEL to stop the shutdown process.  At that point my "taskbar" and program launcher had already been killed.  I proceeded to save the open program and then called up terminal to **sudo reboot** to resume shutting down the computer. Apparently that was a mistake....


After restarting my computer and when trying to log back into Ubuntu, I kept getting spat back out to the log-in screen.  I was only able to log in as Guest.  After a Google search in the Guest session I learned this was a "common issue" which requires booting up a live session (I used Puppy) and deleting the hidden "**.Xauthority**" file in the home folder of the affected account.  After that, I rebooted and logged in as normal.


So my (somewhat rhetorical) questions are...

Why does Ubuntu always kill the taskbar and launcher **before** asking if you want to cancel the shutdown process?  It's just my humble opinion, but the "open window / unsaved work" check should occur before anything is killed.

In my experience, when you click the cancel button, the desktop comes back the way it should

> Has this issue been fixed on later versions of Ubuntu?  If so, why is it still a problem on the LTS version?  I mean, I use an LTS version thinking that all the little bugs will be ironed out during its lifespan.  Does it only receive security updates without addressing major known bugs for the rest of it's life span?

You are assuming this may be a problem for many others. Have you checked bug reports to see if it is really a problem for many other users?
 
> Is Ubuntu's goal to drive people away from terminal commands?  I typically flow back and forth, using terminal about as seamlessly as GUI and I like having the option to do either.

Nobody is trying to drive anyone away from the terminal, the terminal is here to stay.

> Finally, is there a correct way to shut down after pressing the CANCEL shut down button; when the GUI options are gone?

there are so many different ways to shut the system down, just find the one that works best for you. I have several systems running Ubuntu, one system uses the standard:

```
sudo halt -p
```

another system uses a custom shutdown script because I use WOL, and on my main system running Saucy, I use the standard GUI shutdown mechanism.

> Don't get me wrong, I like Ubuntu a lot (it's still my favorite OS), but I understand why stuff like this would drive people away from using it.

If you can reliably duplicate the problem, it may be time to create a bug report

---

### Post by Yougo on 2013-08-19
The .xautority problem usually happens when the x session is broken off in an improper way, such as a crash or a sudden power cut. My guess is 'sudo reboot' is such a blunt tool it cuts off Xorg before it can clear .xauthority.

Instead I use
```
sudo shutdown -r now
```( -r is for reboot, use others if desired, 'now' can be replaced by a number to delay if desired)

It plays nicer with stopping processes.

Also, when in a terminal, you could also start a panel and use the menu on that panel/dock/w.e. to shut down.

That said, the panels disappearing is odd. I can't recall that happening to me without some other crash or malfunction already present (usually due to my own tinkering and prodding :P )

---

