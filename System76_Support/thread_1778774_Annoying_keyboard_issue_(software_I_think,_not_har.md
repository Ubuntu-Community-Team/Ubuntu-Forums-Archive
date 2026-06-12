---
title: "Annoying keyboard issue (software I think, not hardware)"
date: 2011-06-09
forum: System76 Support
---

### Post by smarmytime on 2011-06-09
I'm having an odd, and quite annoying issue from time to time, with keyboard input. I have a PanP7, and I'm running 11.04 and Gnome 3. Every now and then, for no apparent reason, the keyboard will start acting as though I'm trying to enter text somewhere I can't, when I'm trying to enter it in a text field (or anywhere else text can be inputted, like the URL bar on the browser). What will happen is I'll type any key, no letter or symbol will be inputted, the cursor will not move, and it will make that sound that it makes when you are at the very beginning of a text field, and you hit backspace. 

I am absolutely positive that I am in a proper text field when it happens, and I can't click into any other text field once it does...the only thing I can do is log out and log back in. 

Any ideas as to how I can correct the problem? And feel free to let me know if I should have posted this in the General forum.

---

### Post by isantop on 2011-06-09
What version of Ubuntu are you running? Also, can you try it with a different keyboard, just to rule it out as a software problem?

---

### Post by smarmytime on 2011-06-09
> **isantop said:**
> What version of Ubuntu are you running? Also, can you try it with a different keyboard, just to rule it out as a software problem?

As I said, I'm running 11.04 with Gnome 3. How can I use a different keyboard with my laptop? Plug in a USB keyboard?

---

### Post by isantop on 2011-06-09
Yep, a USB keyboard would be a great troubleshooting implement right now.

You might also try running in the classic Gnome environment instead of Gnome Shell.

---

### Post by smarmytime on 2011-06-09
Hmmm...problem is, it's not repeatable, at least not from anything I notice that I'm doing. it just happens from time to time...so the USB keyboard not doing it wouldn't be hard and fast proof of anything. 

Is there a way to lock the keyboard? Maybe I'm doing that somehow.

---

### Post by isantop on 2011-06-10
There aren't any ways to lock the keyboard, so I don't think you're doing that. 

How frequently does this typically occur?

---

### Post by smarmytime on 2011-06-10
Once a day, once every other day, maybe...

---

### Post by isantop on 2011-06-10
Does it happen in any application, or does it only tend to happen in one of them?

---

### Post by smarmytime on 2011-06-11
It's happened in Chrome, Gwibber, and Empathy so far. It just happened again, just this minute, after not having happened for a day or so, and this time in Classic Gnome. Frustrating.

The one thing that I have noticed it happening after, is sometimes I'll hold down the shift key for a few seconds, and once or twice it was the Ctrl key (usually when I'm trying to think of how to word something). When I think of what I want to say, I go to type, and I just get that "glug" system sound that you get when you try to backspace in a text field when you're already at the first point that you're able to type at. I don't know if that's triggering it; I still have not been able to reproduce it intentionally, and it has happened when I wasn't holding a key down.

---

### Post by isantop on 2011-06-13
Did you upgrade to 11.04, or was it a fresh install? Also, which ppa did you use to install Gnome3. The official Gnome3-Team, or the UGR ppa?

---

### Post by smarmytime on 2011-06-14
> **isantop said:**
> Did you upgrade to 11.04, or was it a fresh install? Also, which ppa did you use to install Gnome3. The official Gnome3-Team, or the UGR ppa?

It was a fresh install, and it was the official Gnome3-Team ppa.

---

### Post by isantop on 2011-06-16
Did you test the keyboard in Unity at all before installing Gnome 3? If so, did you have the same issue? This looks like software corruption on one of the Gnome 3 packages, since I'm also testing Gnome 3 on a PanP7, and I don't get this issue.

---

### Post by smarmytime on 2011-06-17
> **isantop said:**
> Did you test the keyboard in Unity at all before installing Gnome 3? If so, did you have the same issue? This looks like software corruption on one of the Gnome 3 packages, since I'm also testing Gnome 3 on a PanP7, and I don't get this issue.

Not really; it didn't take me long to figure out that the current version of Unity wasn't for me. But I'm going to reinstall, so hopefully that will take care of the problem.

---

### Post by stevepowell99 on 2011-07-03
hi, exactly the same issue here. 11.04, gnome-shell from the ppa. Happens very roughly once a day. I have to log out and in again. Pretty sure it isn't hardware.

---

### Post by smarmytime on 2011-07-03
Do you tend to hold a finger down on the shift key from time to time? Because I've finally been able to reproduce the problem, just in the last couple of days...I find if I hold the left shift key down for 10 full seconds (I haven't tried with the right shift key, or any other key) it makes the problem happen. But it also stops it - if I hold the shift key down for 10 full seconds, it seems to unlock whatever is being locked. I haven't tried this with a USB keyboard, but I will shortly - hopefully, the solution works for you as well, Steve, and hopefully I'll be able to change this thread to "Solved".

---

### Post by chuckyanutsup on 2011-07-16
I've been having the same issue. I'm a fair n00b and only started using ubuntu 11.04 a month or 2 ago. I did  a fresh install, but then messed up and had to do an upgrade/reinstall (11.04 to 11.04) I'm dual booting with windows 7. Gnome is 2.32.1

Please advise if further information would be of use.

---

### Post by isantop on 2011-07-18
Did smarmytime's solution above help you out at all? That would be worth a try.

---

