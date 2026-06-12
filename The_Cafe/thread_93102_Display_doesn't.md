---
title: "Display doesn't"
date: 2005-11-21
forum: The Cafe
---

### Post by jjroper on 2005-11-21
That is, I just installed, and everything seemed to go fine.  But, at boot, when the splash screen should start, the monitor shows lines of static.  Then, when Ubuntu splash shows up, all I see is distortion caused by horizontal lines that apparently move up and down the screen.  I don't know if I explained well, but I sure can't figure out how to fix it!  Anybody?

Thanks in advance!

Jim :(

---

### Post by xmastree on 2005-11-21
It sounds like a resolution issue.
Try pressing Ctrl-Alt-+ (that's + on the numeric keypad) to switch to a lower resolution. If that works then you will need to edit your xorg.conf file to remove the offending options.

Oh, and you would probably be better off asking in one of the tech support forums rather than this one.

---

### Post by teaker1s on 2005-11-21
sudo dpkg-reconfigure xserver-xorg
find out the spec on your screen model and when you get to screen section set to the correct settings choose advanced settings eg of mine.-
HorizSync	30-70
	VertRefresh	50-160
you also want to search forums for ati if your card is ati as there are drivers and patches needed

---

