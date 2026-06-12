---
title: "Am I compromised?"
date: 2008-08-05
forum: Security
---

### Post by jasongreen on 2008-08-05
I've had something very unnerving happen a couple of times now.  My computer will start running very slowly. I kill X with Ctl-ALT-BKSP  and then select restart once I hit gdm.  Then I briefly see another login screen (blue w/ a sunflower in the lower left hand corner) before the shutdown proceeds.  Any idea what this could be?  I'm behind a router w/ NAT and no ports forwarded and am not using the default password on the router.  

How worried should I be?

What should I do next?

Thanks

---

### Post by Jordanwb on 2008-08-05
Do you mean by running slowly that it takes a will to respond or is there a lot of hard drive activity?

---

### Post by jasongreen on 2008-08-05
Yes

---

### Post by pedja_portugalac on 2008-08-05
My strategy is to reinstall every time I doubt my security was compromised. I store everything on external HD and that's why it gets me 30 minutes to reinstall, 45 with an encrypted LVM. Are you using kubuntu or ubuntu (KDE or GNOME)? I use GNOME and I'd never seen some blue flower in the corners nor the KDE have it, in my experience? Maybe you have installed packages from GNOME Arts or some other site to make your desktop looking nicer, login managers and staff? If that's the case, maybe it is reason why your PC is slow and conflictuous?

---

### Post by Jordanwb on 2008-08-05
> **jasongreen said:**
> Yes

OMG. Which? :)

> **pedja_portugalac said:**
> My strategy is to reinstall every time I doubt my security was compromised. I store everything on external HD and that's why it gets me 30 minutes to reinstall, 45 with an encrypted LVM. Are you using kubuntu or ubuntu (KDE or GNOME)? I use GNOME and I'd never seen some blue flower in the corners nor the KDE have it, in my experience? Maybe you have installed packages from GNOME Arts or some other site to make your desktop looking nicer, login managers and staff? If that's the case, maybe it is reason why your PC is slow and conflictuous?

Posting your computer specs is always useful.

On an unrelated note: it's 11PM here. Time to go to sleep. Good night.

---

### Post by jasongreen on 2008-08-05
Both.

---

### Post by pedja_portugalac on 2008-08-05
> **Jordanwb said:**
> OMG. Which? :)
Posting your computer specs is always useful.

 
Didn't pay attention to second address mention, it was hidden between words which were copy - pasted, and then? I just try to help solving problem. Forget...

---

### Post by jasongreen on 2008-08-05
AMD 2800+ (1,8 GHZ) running 7.10  Primarily GNOME but have other desktop environments installed.

---

### Post by SunnyRabbiera on 2008-08-05
are you sure its just your OS?
Check your actual computer, make sure she is running clean and such?

---

### Post by jasongreen on 2008-08-05
I guess I'm a bit unsure as to how to do that.  I don't see anything odd when I do a last.  Where else should I look?

---

### Post by pedja_portugalac on 2008-08-05
> **jasongreen said:**
> Primarily GNOME but have other desktop environments installed.

There's a problem, I knew that.

---

### Post by jasongreen on 2008-08-05
Looking at /var/log/messages I see out of memory errors when I had my issue.

---

### Post by pedja_portugalac on 2008-08-05
Before your problems began did you install some additional login manager, screen saver etc? 

If yes, open your synaptic package manager: >System > Administration > synaptic package manager and then in that window open History in the File tab. You'll find there history of all installed packages on your system (less those which we install from source). Browse them and completely remove all those who were installed after the date you've noticed beginning of your trouble. This could be one way to solve your problem. Else, I can see your PC is enough powerful to run the latest release of Ubuntu which is 8.04.1 and is Long Term Supported. I strongly encourage you to get one copy of it and reinstall your system.

---

### Post by Tylazene on 2008-08-05
I think one of the default login screens has a sunflower on it. Could be just logging out to that screen and then shutting down.

---

### Post by jasongreen on 2008-08-05
I don't think so.

---

### Post by 16777216 on 2008-08-05
I am not sure what is causing your slowdown problem but the flower thing is one of the default GDM themes.

Perhaps a look at your processes to familiarize yourself with is normally running then when you get the slow down issue look again to see if any thing odd is running.

If you have not already open  gnome-system-monitor  and click edit > preferences and activate all information fields.

And in the view menu check all processes.

---

### Post by jasongreen on 2008-08-06
I'll try that.  It sounds at least possible that the memory thrash caused something with the login manager.

---

### Post by pedja_portugalac on 2008-08-06
Before your problems began did you install some additional login manager, screen saver etc? 

If yes, open your synaptic package manager: >System > Administration > synaptic package manager and then in that window open History in the File tab. You'll find there history of all installed packages on your system (less those which we install from source). Browse them and completely remove all those who were installed after the date you've noticed beginning of your trouble. This could be one way to solve your problem. Else, I can see your PC is enough powerful to run the latest release of Ubuntu which is 8.04.1 and is Long Term Supported. I strongly encourage you to get one copy of it and reinstall your system.

---

### Post by Jordanwb on 2008-08-06
> **pedja_portugalac said:**
> Didn't pay attention to second address mention, it was hidden between words which were copy - pasted, and then? I just try to help solving problem. Forget...

Huh?

> **pedja_portugalac said:**
> I can see your PC is enough powerful to run the latest release of Ubuntu which is 8.04.1 and is Long Term Supported. I strongly encourage you to get one copy of it and reinstall your system.

Yeah 7.10 wouldn't boot on my Laptop most of the time, installed 8.04; worked like a charm.

How much physical memory and swap do you have?

---

### Post by jasongreen on 2008-08-06
512 MB of physical RAM and 1 GB of swap.  Yes, I know I need more :)

---

### Post by Jordanwb on 2008-08-06
No that's a good amount

---

