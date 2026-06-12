---
title: "How do I enable the &quot;execute bit&quot; for an EXE file that's on a CD (which is read-only)"
date: 2011-01-01
forum: Wine
---

### Post by diablo75 on 2011-01-01
I am trying to test some software in Wine that I have on a CD.  Often times when I need to run something in Wine, I have to open the file permission settings and check to allow execution of an EXE file, so Wine can run it.  Unfortunately the file I want to execute is on a CD, which is read only, so it doesn't let me change the files permissions.  Is the only way around this to copy all the files from the disc to the PC and run from there?

---

### Post by Ocxic on 2011-01-01
Have you tried the command "wine /path/to/file.exe"

to my knowledge exe file do not need the executable permission to run with wine,, though i could be wrong.

---

### Post by bazzer on 2011-01-06
> **diablo75 said:**
> copy all the files from the disc to the PC and run from there?

I would do this if I were you, it's a pretty easy way around the issue. :)

---

### Post by blind2314 on 2011-01-06
To my knowledge this can't be done..but, as suggested (by you as well), just copy all the files down and run it from there?

---

### Post by mcduck on 2011-01-06
> **Ocxic said:**
> Have you tried the command "wine /path/to/file.exe"

to my knowledge exe file do not need the executable permission to run with wine,, though i could be wrong.

This should work just fine. And so should right-clicking and choosing to open the file with Wine.

It's not the .exe file you actually execute, but Wine. Just like you don't need to make a text file executable to open it in Gedit, since Gedit is the one that's executed.

(And you can't change permissions of optical media. They are read-only filesystems.)

---

### Post by finnipinni on 2011-03-16
Hi mcduck - I also got this problem tryin' to install Polar PPT5 from CD.
Also rightclick "open with wine".
I loaded CD to screenboard with same result.
Some ideas howto do this ?

Setup is not marked as executable......

And some ideas how to get the IRDA mojo to work in wine ?
Greatful for help on this.

---

### Post by YokoZar on 2011-03-16
Here is the relevant launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/mime-support/+bug/561479](https://bugs.launchpad.net/ubuntu/+source/mime-support/+bug/561479)

There's a workaround at the bottom (installing Wine from PPA is probably easier, and also works)

---

### Post by Morbius1 on 2011-03-16
To answer the original question, you don't have to enable the "execute bit" on a CD for wine to run an exe because wine is incapable of determining if a given file has a linux executable bit set.

The problem is something called "cautious-launcher". Two easy workarounds can be found here:[http://ubuntuforums.org/showpost.php?p=10548141&postcount=8](http://ubuntuforums.org/showpost.php?p=10548141&postcount=8)

---

### Post by Clessy on 2011-03-16
just terminal script it. 

wine "/media/im a cd.exe"

Works fine for me.

---

### Post by Morbius1 on 2011-03-16
> **Clessy said:**
> just terminal script it. 

wine "/media/im a cd.exe"

Works fine for me.
That actually proves my point. The link I gave in my previous post will show you how you can fix this so you can all go back to double clicking an exe file regardless of where it is and invoke the "correct" wine application.

---

### Post by finnipinni on 2011-03-16
Thanks !
My workaround was to copy the CD to the screenboard, rightclick om the .exe file, properties, and check box under "rights" "Allow running file as a program" (translated from Norwegian...."
I tried this on the same file directly on the CD, but checkermark would not stik.

Guess I will post my other issues suitable places.....

---

### Post by Clessy on 2011-03-16
> **Morbius1 said:**
> That actually proves my point. The link I gave in my previous post will show you how you can fix this so you can all go back to double clicking an exe file regardless of where it is and invoke the "correct" wine application.

Well that makes me wonder. Why is my wine instantly broken when i just installed it?

---

### Post by Morbius1 on 2011-03-17
Wine itself is not broken. This cautious-launcher thing is there to protect you from yourself. From [https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required) :
> **Execute-Permission Bit Required**

 
[LIST]
[*]Applications, including desktops and shells, must not run executable code from files when they are both:
[LIST]
[*]lacking the executable bit
[*]located in a user's home directory or temporary directory.
[/LIST]
 
[*]The GNOME or KDE MIME type handlers must not circumvent this principle.
[*]This includes *.desktop, *.jar, and *.exe files.
[LIST]
[*]Look for .desktop files with [MimeType]("https://wiki.ubuntu.com/MimeType")= and Exec= lines that do not use "cautious-launcher"
[/LIST]
 
[*]Nothing  may provide a workaround to run them anyway automatically - i. e.,  never juxtapose <long explanatory text> with <easy button that  bypasses the text>
[/LIST]
Well, there is a workaround. Execute wine directly from the terminal as you have done or remove cautious-launcher from the wine launcher at it's source.

---

### Post by Clessy on 2011-03-17
> **Morbius1 said:**
> Wine itself is not broken. This cautious-launcher thing is there to protect you from yourself. From [https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required) :
Well, there is a workaround. Execute wine directly from the terminal as you have done or remove cautious-launcher from the wine launcher at it's source.

Wine is straight sucking for me. I Just tried Ragnarök Online which is supposed to work as it was rated platinum. The thing wont even launch even when trying to launch it from terminal

---

### Post by finnipinni on 2011-03-17
Solved.
I had to load the CD to screenboard, rightclick on the exe-file and checked the box there.

---

