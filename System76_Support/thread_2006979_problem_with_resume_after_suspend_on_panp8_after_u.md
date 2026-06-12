---
title: "problem with resume after suspend on panp8 after upgrade to 12.04"
date: 2012-06-19
forum: System76 Support
---

### Post by gdgilda on 2012-06-19
Hello,

I've enjoyed my panp8 for about a year now and have upgraded it twice, once from 11.04 to 11.10, and now from 11.10 to 12.04.  I have run into a problem, however, with suspend that I didn't have anytime before the upgrade to 12.04.

I use suspend frequently, and my typical usage is just to close the lid after I'm done with using the laptop for the day (I leave it plugged into the wall outlet).  The next day I'll come back, open the lid, wait a few seconds for resume to complete and then it's off to the races.

If I now follow the same routine, the laptop seems to wake up and turn on the backlight for the display, but all I see is a pointer for the mouse.  I haven't been able to figure out a way to bring the rest of the display back.  Eventually I end up doing a alt-ctl-F1 and a shutdown -r to restart the system.

If I try to recreate the problem by shutting the lid, waiting for the suspend to complete and then re-opening the lid, resume works fine.  It seems that the problem with resume only occurs if I leave the laptop sitting in suspend state for a while (I haven't played with this much to determine how long I have to wait for the resume problem to surface).

I did reinstall the system76 driver as part of the upgrade (it says that it's at 3.0.0 level).  I'm also attaching logs taken right after rebooting the system after a failing resume.

Any ideas on what the problem is and how to fix it would be much appreciated!

Thanks
Glenn

---

### Post by isantop on 2012-06-20
> **gdgilda said:**
> Hello,

I've enjoyed my panp8 for about a year now and have upgraded it twice, once from 11.04 to 11.10, and now from 11.10 to 12.04.  I have run into a problem, however, with suspend that I didn't have anytime before the upgrade to 12.04.

I use suspend frequently, and my typical usage is just to close the lid after I'm done with using the laptop for the day (I leave it plugged into the wall outlet).  The next day I'll come back, open the lid, wait a few seconds for resume to complete and then it's off to the races.

If I now follow the same routine, the laptop seems to wake up and turn on the backlight for the display, but all I see is a pointer for the mouse.  I haven't been able to figure out a way to bring the rest of the display back.  Eventually I end up doing a alt-ctl-F1 and a shutdown -r to restart the system.

If I try to recreate the problem by shutting the lid, waiting for the suspend to complete and then re-opening the lid, resume works fine.  It seems that the problem with resume only occurs if I leave the laptop sitting in suspend state for a while (I haven't played with this much to determine how long I have to wait for the resume problem to surface).

I did reinstall the system76 driver as part of the upgrade (it says that it's at 3.0.0 level).  I'm also attaching logs taken right after rebooting the system after a failing resume.

Any ideas on what the problem is and how to fix it would be much appreciated!

Thanks
Glenn

Do your results differ if you try to suspend while running from a LiveCD of Ubuntu? This will tell me if the problem is being caused by your system or by something going wrong with the upgrade.

---

### Post by toddpedlar on 2012-06-21
I just got this advice in another thread:  while your laptop is in a happy state, go to Keyboard Layout --> Options --> Key Sequence to Kill X-Server, and enable the Ctrl-Alt-Backspace sequence by clicking the radio button next to Ctrl-Alt-Backspace in the popup.  

Then when your computer is in this "mouse cursor only" state after a resume from the suspended state, try Ctrl-Alt-Backspace.  I haven't had to do it yet, but it's reputed to work. 

Todd

---

### Post by gdgilda on 2012-06-28
Hello,

I finally got around to burning a LiveCD and trying suspend after booting from it.  It seems that I don't see the suspend issue if I boot from the LiveCD after many tries.

So what's my next step?

Thanks,
Glenn

> **isantop said:**
> Do your results differ if you try to suspend while running from a LiveCD of Ubuntu? This will tell me if the problem is being caused by your system or by something going wrong with the upgrade.

---

### Post by gdgilda on 2012-06-28
Todd,

Thanks for the suggestion.  FYI, I tried it as a workaround, but unfortunately it wasn't very effective, at least for me.  It bounced me back to the login screen, and after logging back in, ubuntu died with an "internal error" after a couple of minutes.

Glenn

> **toddpedlar said:**
> I just got this advice in another thread:  while your laptop is in a happy state, go to Keyboard Layout --> Options --> Key Sequence to Kill X-Server, and enable the Ctrl-Alt-Backspace sequence by clicking the radio button next to Ctrl-Alt-Backspace in the popup.  

Then when your computer is in this "mouse cursor only" state after a resume from the suspended state, try Ctrl-Alt-Backspace.  I haven't had to do it yet, but it's reputed to work. 

Todd

---

### Post by isantop on 2012-06-29
> **gdgilda said:**
> Hello,

I finally got around to burning a LiveCD and trying suspend after booting from it.  It seems that I don't see the suspend issue if I boot from the LiveCD after many tries.

So what's my next step?

Thanks,
Glenn

I would go ahead and perform an upgrade from the CD. My guess is that something wasn't updated properly when you did the update, and the upgrade from the CD (Which will replace the installed copy of Ubuntu with a fresh installation) will fix that.

---

### Post by gdgilda on 2012-07-02
Hello,

I tried a complete reinstall over the weekend.  Things looked good for a day or so, but now the same symptom has returned.  Is there anything else to try, or is it time to suspect bad hardware?

Glenn

> **isantop said:**
> I would go ahead and perform an upgrade from the CD. My guess is that something wasn't updated properly when you did the update, and the upgrade from the CD (Which will replace the installed copy of Ubuntu with a fresh installation) will fix that.

---

### Post by amoxicillin on 2012-07-04
I've had this same problem with my Lemu4.  I used Todd's trick and so far it worked but I am still wondering why I keep getting this problem.  It doesn't happen all the time which just makes it that much more curious.  One of the only things I have changed recently that affected the display was installing driconf and activating S3TC texture compression.  Seems like a long shot that that has anything to do with it but I am out of ideas.

---

### Post by dixtort on 2012-07-08
I am seeing the same problem with a new Gazelle Professional out of the box yesterday.  It has happened 3 out of about 10 times I've put it into suspend.  The system still seems functional as I can see the mouse pointer change when going over where the password text field should be.  I sign in, still with the black screen, and I can clearly see the mouse pointer changing where I had gedit open.

Edit 1:
I was able to dump into command line (ctrl+alt+f2).  Tried typing init 5 to reboot x and it just hanged for a few minutes before I had to force shutdown.  I tried this the first time and haven't tried it since.

Edit 2:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/966744](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/966744)

---

### Post by amoxicillin on 2012-07-10
I reinstalled 12.04 and so far that seemed to solve the problem for me.  I don't know if it was a corrupted update or if the first install was buggy but everything seems to be running well now.  Even though the kernel I am on is 3.2.0-26 instead of 3.0.0-26 everything seems to be running just fine so I haven't downloaded the new pre-release kernel update.

(note: I am using a Lemu4)

---

### Post by isantop on 2012-07-10
> **amoxicillin said:**
> I reinstalled 12.04 and so far that seemed to solve the problem for me.  I don't know if it was a corrupted update or if the first install was buggy but everything seems to be running well now.  Even though the kernel I am on is 3.2.0-26 instead of 3.0.0-26 everything seems to be running just fine so I haven't downloaded the new pre-release kernel update.

(note: I am using a Lemu4)

If you notice any stability problems resuming from suspend or with freezing/lockups, then I'd recommend installing that pre-released kernel. Otherwise, though, you should be fine to wait until it get's pushed to the normal update repository.

---

