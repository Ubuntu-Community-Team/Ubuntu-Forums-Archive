---
title: "Viruses In WINE"
date: 2009-01-27
forum: The Cafe
---

### Post by andras artois on 2009-01-27
What happens if you were to accidently install something with a virus or trojan in WINE? Would only effect WINE components? Would it only start working once you started something in WINE?

It was just a thought.

---

### Post by MaxIBoy on 2009-01-27
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Don't browse the web with WINE, and you're probably okay. If you want to be sure, try disabling any drives that go to places you're worried about. By default, there will be a Z:\ drive that goes to your root directory (see attached picture.) I have that disabled because I'm paranoid. However, WINE is a fairly low-risk program, because it only runs on things you specifically start yourself.

---

### Post by waxBall on 2009-01-27
Interesting post!

What if I launched, say, a keygen or something and it actually had a trojan attached.  Could that trojan then infect a DLL?  What would be the result?

Signed
-Youboontoo Nuebee

---

### Post by sowelie on 2009-01-27
Fortunately, wine does not startup programs automatically.  You'd have to start up the infected program yourself.  If it does get started, it can easily be killed (and won't start back up when you restart).  Also, the infected program won't have access to damage any of your system files because of linux security.  I wouldn't worry about it.

---

### Post by Dev'olution on 2009-01-27
> **waxBall said:**
> Interesting post!

What if I launched, say, a keygen or something and it actually had a trojan attached.  Could that trojan then infect a DLL?  What would be the result?

Signed
-Youboontoo Nuebee

Effectively, its an emulation of windows, so yes it would infect a file, but only within the drive_c folder or the /home/username directory. However, it would not cause a problem with Ubuntu, as its emulated via windows.

---

### Post by Grant A. on 2009-01-27
It's highly susceptible to Trojans, as those usually are activated with user consent, so always download from trustworthy sources.

---

### Post by Skripka on 2009-01-27
> **WestAussieUbu said:**
> Effectively, its an emulation of windows, so yes it would infect a file, but only within the drive_c folder or the /home/username directory. However, it would not cause a problem with Ubuntu, as its emulated via windows.

_This presumes the bug even runs like it would under Win._


I've run HIGHLY infected executables in Wine...and only found out they were carriers when I ran them on my Win drive--which summarily was bluescreening in less than 5 minutes....with no harm done to my virtual C:\ drive

---

### Post by MaxIBoy on 2009-01-28
Almost all of these things depend on security vulnerabilities that haven't been duplicated in WINE.

---

### Post by mihai.ile on 2009-01-28
> **MaxIBoy said:**
> Almost all of these things depend on security vulnerabilities that haven't been duplicated in WINE.

Oh... so it seems that Wine still has compatibility issues in perfect emulation of Windows...:p

---

### Post by MaxIBoy on 2009-01-28
**W**ine **I**s **N**ot an **E**mulator.

But yeah, pretty much.

---

### Post by 3rdalbum on 2009-01-28
Viruses prefer to access the real running internals of Windows, but it's possible for a virus run in Wine to stay resident while Wine runs (and run itself again each time you run Wine). I guess it might be possible for it to keep running even after you think you've quit Wine.

If you want to try it out, make a new user account and try it (but disconnect yourself from the internet). I did try it once, and my chosen malware just immediately quit.

---

### Post by Johnsie on 2009-01-28
I'd be more concerned about accidently installing a bad deb than getting a wine virus. Seriously, if the repositories got compromised... Well, I'd rather not think about it.

---

