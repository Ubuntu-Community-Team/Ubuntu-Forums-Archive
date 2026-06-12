---
title: "How will ubuntu run on this computer?"
date: 2010-02-14
forum: The Cafe
---

### Post by gymophett on 2010-02-14
My friend from Canada is willing to convert, and I've given her the Linux is not Windows talk, and I've gotten it through her head.
She understands, and is tired of XP crashing on her.

I only know her basic specs:
They are 512MB Ram, and 2GHz.

That's all I know.
I need her to start out easy, and she wouldn't want anything like Crunchbang, and she didn't like XFCE.

Will Ubuntu run okay on her computer? Or should I lead her to something else?

It's a desktop, if that even matters.

---

### Post by 2hot6ft2 on 2010-02-14
Ubuntu will run fine with 512MB of RAM, it wont be super fast but it will work pretty good at 2Ghz. As for the rest of the hardware there in lies the questions like graphics card.

---

### Post by Dr. C on 2010-02-14
I do not see a problem here

---

### Post by themarker0 on 2010-02-14
I was running 8.04 for god knows how long on 512. I had no issue. I recently went to 9.04 and 1.5 bytes. I also have 2ghz still, it runs fine.

---

### Post by Psumi on 2010-02-14
What video card do you have on it?

---

### Post by gymophett on 2010-02-14
I'm not sure what video card she has. She lives far from here, so I can't go check. I'm gonna get her to run the LiveCD, and see if she has the correct resolution and such.

Or I'll just get her to look under her devices.

---

### Post by themarker0 on 2010-02-14
Get her to run Belarc Advisor or CPUZ, (I can't remember which says the video card) it will give all the stats needed. :)

---

### Post by witeshark17 on 2010-02-14
I bet it'll work fine; please keep us posted.

---

### Post by Psumi on 2010-02-14
> **gymophett said:**
> I'm not sure what video card she has. She lives far from here, so I can't go check. I'm gonna get her to run the LiveCD, and see if she has the correct resolution and such.

Or I'll just get her to look under her devices.

This is a problem. with older computers, the open-source drivers have evolved so that compiz can be enabled, thus, her computer may have compiz enabled by default (like mine) but unable to use ANY fancy effects, OR even the system itself unless you disable compiz. This will cause issues in ubuntu versions after 10.10, as GNOME 3 will surely be the default.

---

### Post by XubuRoxMySox on 2010-02-15
An older version (8.10 or 8.04) would work okay. The newer versions with Beta software (Grub2, PulseAudio, etc) are not to be trusted on a friend's computer if you still want to be friends afterwards. It *might* work out fine, but **it's never a good idea to give a newbie Beta software that their OS depends on! **This, in my opinion, could well be Ubuntu's downfall. In their mad rush to improve boot time (and who really cares about boot time anyway?) they've taken what is basically experimental software and made it the *default* in a distro that claims to be "newbie-friendly." PulseAudio was practically still Alpha when Ubuntu made it the default in place of the tried-and-true ALSA.

If still want to be friends with your friend after (s)he has taken your advice, give him or her a rock-solid, tried-and-proven, reliable, completely stable distro like Debian Lenny or Mepis (superb KDE/Debian Lenny mixture).

-Robin

---

### Post by NightwishFan on 2010-02-15
> **Psumi said:**
> This is a problem. with older computers, the open-source drivers have evolved so that compiz can be enabled, thus, her computer may have compiz enabled by default (like mine) but unable to use ANY fancy effects, OR even the system itself unless you disable compiz. This will cause issues in ubuntu versions after 10.10, as GNOME 3 will surely be the default.

I am quite sure that the system will not be "unbootable" if Gnome 3 cannot work. Gnome 3 is not even done yet. Compiz is an entirely different window manager than metacity and it falls back when it is unusable.

Read the link in my sig..

---

### Post by Psumi on 2010-02-15
> **NightwishFan said:**
> I am quite sure that the system will not be "unbootable" if Gnome 3 cannot work. Gnome 3 is not even done yet. Compiz is an entirely different window manager than metacity and it falls back when it is unusable.

Read the link in my sig..

I didn't say it was unbootable. Compiz did NOT fall back when it caused my system to slow to a stop.

---

### Post by NightwishFan on 2010-02-15
I see, perhaps something along the lines of a blacklist will be in order. I assume that it will not be as severe as this, but I suppose time will tell.

---

