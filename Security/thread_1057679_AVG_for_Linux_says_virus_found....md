---
title: "AVG for Linux says virus found..."
date: 2009-02-02
forum: Security
---

### Post by RaiCoss on 2009-02-02
Any ideas what exactly this might be??

[IMG]http://i208.photobucket.com/albums/bb43/akinginmyownmind/Screenshot-20.png[/IMG]

---

### Post by ratmandall on 2009-02-02
Do you have a seperate partition with windows on it? Or do you have any windows executables on your linux install.

---

### Post by RaiCoss on 2009-02-02
> **ratmandall said:**
> Do you have a seperate partition with windows on it? Or do you have any windows executables on your linux install.

Yeah I have the latest version of WINE (1.1.14), but the only things installed are World of Warcraft and WinRAR.

The other odd thing is that I have set AVG to do automated scans, but the logfile for last nights' scan dosen't exist (theres a red cross next to it in the test results column), is it maybe a glitch in AVG?

---

### Post by Neural oD on 2009-02-02
could be winrar - depends where u picked it up from - wouldn't worry too much - as shouldn't effect your linux os

---

### Post by mozgito on 2009-02-02
I have had the same problem and it was winrar

---

### Post by RaiCoss on 2009-02-02
> **Neural oD said:**
> could be winrar - depends where u picked it up from - wouldn't worry too much - as shouldn't effect your linux os

Hmmmm i doubt it's WinRAR, I downloaded it from the offficial site, but I'll Uninstall just to be safe.;)

---

### Post by RaiCoss on 2009-02-02
> **mozgito said:**
> I have had the same problem and it was winrar

Ohhhhhhhhhhhhh ok, thanks man!

---

### Post by RaiCoss on 2009-02-02
Seems it was WINRAR, i uninstalled it and scanned again, and it says all clean :D, thanks for the help!

---

### Post by Tubes6al4v on 2009-02-02
Just out of curiousity, why are you using WinRAR? You can install the "rar" and "unrar" packages from the repos to access rar files.

---

### Post by RaiCoss on 2009-02-02
> **Tubes6al4v said:**
> Just out of curiousity, why are you using WinRAR? You can install the "rar" and "unrar" packages from the repos to access rar files.

Because when I tried to extract a file with the Archive Manager, it kept prompting me for a password, but the file isn't password protected. So I tried WINRAR under WINE, and the file is corruped under the third RAR, and after a little research I learned that sometimes WinRAR can't distinguish between a corrupted, or password protected file, so I was wasting my time anyway.

---

### Post by RaiCoss on 2009-02-02
Ok, AVG must have some major glitch if you set it to autoscan because its saying the same thing again......

[IMG]http://i208.photobucket.com/albums/bb43/akinginmyownmind/Screenshot-32.png[/IMG]

---

### Post by PocketDog on 2009-02-03
That'll be AVG using 'heuristic detection' (security industry term for guesswork) and flagging a Windows executable just because it's small. Get rid of AVG and relax

---

### Post by RaiCoss on 2009-02-03
> **PocketDog said:**
> That'll be AVG using 'heuristic detection' (security industry term for guesswork) and flagging a Windows executable just because it's small. Get rid of AVG and relax

I don't think it's that because when you do a manual scan, it says all is fine, it only seems to "detect" the virus when it autoscans/scheduled scan.

---

### Post by ikt on 2009-02-03
> **PocketDog said:**
> Get rid of AVG and relax

and maybe do a scan with clamav instead?

---

### Post by cariboo on 2009-02-03
It seems the OP has gone back to Windows, so all of this is moot. See [this]("http://ubuntuforums.org/showthread.php?t=1058779").

Jim

---

