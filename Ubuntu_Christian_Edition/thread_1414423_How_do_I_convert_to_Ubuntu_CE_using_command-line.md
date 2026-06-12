---
title: "How do I convert to Ubuntu CE using command-line"
date: 2010-02-23
forum: Ubuntu Christian Edition
---

### Post by Deer Hunter on 2010-02-23
I found out about this while trying to figure out how to run e-Sword on my Ubuntu 9.10 partition (I'm dual-booting with XP).  Anyway, I found the home website, and looked at this page ([http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)) that shows how to convert from standard Ubuntu to Ubuntu CE.  So, I open a terminal, copy and paste the command displayed on above-mentioned page, and hit enter.

Here's where I can't figure out what to do next.  A little line of script comes up that says "[sudo] password for davis-goertzen: (blinking cursor)"  Now, I would have thought that my next step would be to type in my password I made when installing Ubuntu; but it won't let me type anything, or copy and paste my password in.  What am I doing wrong?

BTW, I should mention that I'm extremely new to Ubuntu, and have ZERO experience trying to run things on the command line.  I'm used to a GUI, like Windows.

Anyway, if you guys could tell me how to manage the command-line, that'd be great.  Thanks.

Deer Hunter

---

### Post by Deer Hunter on 2010-02-23
UPDATE: After some hunting around I realized that the keystrokes just aren't displayed in the terminal, so that's okay.

BUT, when I run the command, this comes up:
The following packages have unmet dependencies:
  ubuntu-ce: Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

How do I deal with that?  I thought I needed Wine to run E-Sword, as well as any other Windows-based programs I want to keep using.

Deer Hunter

---

### Post by stlsaint on 2010-02-23
will it let you continue the install or does it just error out?

---

### Post by Deer Hunter on 2010-02-23
I beg pardon, I made a mistake in the second post.  After what I said it displays, it says this:

davis-goertzen@davis-goertzen-laptop:~$ 

I have no idea whether that's important or not, but I tried typing "yes" there, as well as "install" and it didn't seem to work.  But, like I said, I know practically nothing about running CLI.  Thanks for the help.

Deer Hunter

---

### Post by stlsaint on 2010-02-23
try this in the terminal:
```
sudo apt-get install --fix-broken
```

---

### Post by david_kt on 2010-02-23
> **Deer Hunter said:**
> UPDATE: After some hunting around I realized that the keystrokes just aren't displayed in the terminal, so that's okay.

BUT, when I run the command, this comes up:
The following packages have unmet dependencies:
  ubuntu-ce: Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

How do I deal with that?  I thought I needed Wine to run E-Sword, as well as any other Windows-based programs I want to keep using.

Deer Hunter

It is due to wine-christian-repos depend on wine stable, not wine beta. I suspect you have install wine beta from wine HQ repository. What you have to do is to remove wine beta and try again the convert.

If your application could not run on wine stable, later on you could install back wine beta and remove wine-christian-repository and ubuntuce meta package.

DK

---

