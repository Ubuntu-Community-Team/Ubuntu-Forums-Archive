---
title: "Closing lid doesn't lock screen"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scaine on 2012-03-14
On my 12.04 fresh install, I have set my lock settings as :[ http://i.imgur.com/Duw7C.jpg]("http://i.imgur.com/Duw7C.jpg")

But when I close my lid, despite the screen turning off, when I open it again it's unlocked.

This behaviour was a breeze to set up in 11.04 and 11.10. Anyone suffering the same issue on 12.04?

(as an aside, I tried setting org.gnome.desktop.screensaver.lock-delay to zero, but that didn't make any difference. Also, I tried setting org.gnome.settings-daemon.plugins.power.lid-close-battery-action to "blank", but again, no dice.)

---

### Post by scaine on 2012-03-15
Nobody even willing to test this, if only to refute it? Set screen to lock in preference, close your lid for 5 seconds, open it again - still unlocked.

I'll can file a bug a bug at the weekend regardless.

---

### Post by cariboo on 2012-03-15
It works as it should on my system. There was some talk of the problem showing when using an encrypted hard drive, in another thread:

[http://ubuntuforums.org/showthread.php?t=1921621&highlight=lock](http://ubuntuforums.org/showthread.php?t=1921621&highlight=lock)

check it out to see if it applies to you.

---

### Post by bmbaker on 2012-03-15
just tried didn't lock on mine either!
when i tried to put it into sleep mode it took a long long time!
i noticed that my bluetooth light was on the whole time then it went off and my laptop went into sleep mode.

---

### Post by scaine on 2012-03-19
I've created a bug report here :
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/959184](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/959184)

Added in a note at the end about the fact that both my laptops suffering from this behaviour have encrypted home directories. I think one of my colleagues is using a non-encrypted version of 12.04. I'll give that shot.

[EDIT : Should have said - Cariboo907, none of these systems are set to auto-login, so hopefully that thread isn't relevant here. Also, bmbaker, I'm not using suspend/resume here, just "screen off" when I close the lid, so again, hopefully not relevant in this case!]

Thanks for the replies.

---

### Post by cryptotheslow on 2012-03-19
Confirmed here. It doesn't appear to be related to having an encrypted home directory as it behaves the same for my usual user with encrypted home as well as for a newly created one without.

I'll recheck later on today when the mentioned "fix" as per your bug report is released - although I note you've already replied that it's unrelated to the encrypted home on the bug.

***edit*** - Ahh I see the mention about encryption here was referring to a LUKS partition rather then ecryptfs encrypted home dirs. I can't see any mention of encryption one way or another on the gnome-settings-daemon bug and fix info on the linked Gnome and Debian bugs - so hopefully this patch should fix this.

---

### Post by cryptotheslow on 2012-03-19
The latest updates gave me gnome-settings-daemon (3.3.92-0ubuntu1) and this has fixed the problem here - screen locks as expected when the laptop lid is closed and screen goes off. :)

---

