---
title: "A huge security flaw in KDE/Kubuntu!"
date: 2009-11-01
forum: Security
---

### Post by viking_maniac on 2009-11-01
I got more or less shocked today while I was making an extra account for private use. This is where I'm going to work with very personal and private data about me and my work, so if I need to go away from the computer, I'll either lock the session or switch to my default account until I get back. Or _Especially_ if someone needs to access my computer for a short while.

While either locking the screen/session, or switching between the accounts, normally you should see a completely black screen with only the password prompt window in the middle. This I remember from Gnome/Ubuntu.

In KDE/Kubuntu, sometimes a bug hits the system so the screen of the session that you're about to log back into reveals the whole desktop in the background, and some corrupt graphics is shown around the login and password field. There's no problem logging back in again, but man, anyone can just give that a try, and even without a password, they'll get a perfect glance of the active desktop while the password is being prompted; this could reveal every open document on that desktop.

I'm pretty sure that this is a bug in KDE/Kubuntu, since this is related to the KDE lockout/user switch session manager only. I actually did like KDE/Kubuntu a lot; until I discovered this flaw. I can live with bugs here and there, but this is actually a major security breach in a multiuser environment; at least if you care about and need your privacy.

I've added this thread to the Kubuntu community, if anyone should be interested in what they have to say about this:
[http://kubuntuforums.net/forums/index.php?topic=3107547.0](http://kubuntuforums.net/forums/index.php?topic=3107547.0)

---

### Post by aysiu on 2009-11-01
> **viking_maniac said:**
> 
I'm pretty sure that this is a bug in KDE/Kubuntu, since this is related to the KDE lockout/user switch session manager only. I actually did like KDE/Kubuntu a lot; until I discovered this flaw. I can live with bugs here and there, but this is actually a major security breach in a multiuser environment; at least if you care about and need your privacy. How about filing a bug report, then?

---

### Post by Agent ME on 2009-11-01
I found a similar security flaw once. [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/313085](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/313085). I've had trouble repeating it usually, and kind of hoping it's just gone away, but who knows.

My advice, rely on screen lock to deny access (input) to your account. Don't rely on it to deny viewing the screen of your account.

---

### Post by cariboo on 2009-11-01
That sounds like a graphics driver problem, more than a security one. What graphics adapter and driver does your system use?

---

### Post by viking_maniac on 2009-11-02
> **cariboo907 said:**
> That sounds like a graphics driver problem, more than a security one. What graphics adapter and driver does your system use?

I've got 8800GTS and the recommended NVIDIA 185 that came with Kubuntu.

---

### Post by aysiu on 2009-11-02
Whether it's a graphics problem or a KDM login screen problem, you should file a bug report on it so it can be fixed. This thread alone will do nothing to fix the problem. A bug report is going to be a lot more helpful.

---

