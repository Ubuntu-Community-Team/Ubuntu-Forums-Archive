---
title: "Nothing is executable, how can I change this?"
date: 2010-08-08
forum: Wine
---

### Post by SonicFireStorm on 2010-08-08
I recently wiped my HDD and installed 10.04, I installed WINE a few days ago but I've been having trouble installing programs. I keep getting a message saying the file isn't executable, for example the message I get when I try to run the Guitar Pro 6 file is:

"The file 'home/sam/Desktop/GP6.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

Please someone tell me how to solve this problem, it's seriously getting annoying now. I never had this problem with earlier versions of Ubuntu.

---

### Post by howefield on 2010-08-08
Right click the file and select properties > permissions, and ensure that mark as executable is checked off.

---

### Post by corncob on 2010-08-08
I'm having the same problem but, sadly, I can only tell you what didn't work so far: [http://ubuntuforums.org/showthread.php?p=9695137#post9695137](http://ubuntuforums.org/showthread.php?p=9695137#post9695137)

---

### Post by cogadh on 2010-08-08
Its not actually a problem, it is a "feature". Starting with 10.04, Ubuntu changed the default permissions for Windows executables (among other things) to "no execute". It is supposed to make the system more secure (technically, it does), but in my opinion, it just makes it more annoying.

---

### Post by SonicFireStorm on 2010-08-09
> **cogadh said:**
> Its not actually a problem, it is a "feature". Starting with 10.04, Ubuntu changed the default permissions for Windows executables (among other things) to "no execute". It is supposed to make the system more secure (technically, it does), but in my opinion, it just makes it more annoying.

Is there anyway to delete this 'feature'?

---

### Post by ShadowMage on 2010-08-09
If you run it from the command-line like
```
wine MyProgram.exe
```then it doesn't matter if it's executable or not, because technically you're not running "MyProgram.exe" (at least not directly); instead, you're running "wine" with the parameter "MyProgram.exe".

Just thought I'd throw this out there, since for example CD-ROMs are read-only, and you might not be able to change the executable bit.

I imagine this is also the recommended way to run programs in wine and that they made the executable bit "off" by default in 10.04 for this reason, but this is just a guess.

Anyway, hope this helps.

---

### Post by cogadh on 2010-08-09
> **SonicFireStorm said:**
> Is there anyway to delete this 'feature'?
Not that I am aware of. The only way I know to deal with it is to modify the executable bit on a per EXE basis (right-click > Properties > Permissions > check the execute box). I'm sure there would also be a way to do it via a terminal command that would allow you to modify the bit for all the EXEs in an entire directory, something like "chmod -R +x *.exe" (I make no guarantees about the accuracy of that command).

I don't think you realize, this "change" to Ubuntu is not really a change; all "foreign" executables in Linux have always been set to "no execute", they just didn't do that with Windows executables for some reason. Now Windows executables are in line with everything else.

---

### Post by corncob on 2010-08-09
> **cogadh said:**
> Its not actually a problem, it is a "feature". Starting with 10.04, Ubuntu changed the default permissions for Windows executables (among other things) to "no execute". It is supposed to make the system more secure (technically, it does), but in my opinion, it just makes it more annoying.

Seems like its made WINE useless.  It seems like it wants to start from the command line ```
wine *.exe
``` for a couple seconds but then does nothing.

SonicFireStorm, did you ever have any luck?

---

### Post by mc4man on 2010-08-10
> Is there anyway to delete this 'feature'?
If you wish to revert this nonsense, other than the various workarounds, then 
```
gksu gedit /usr/share/applications/wine.desktop
```

Look for this line
Exec=cautious-launcher %f wine start /unix
and edit it to 
Exec=wine start /unix %f

Until this is implemented as a warning with a choice to proceed or not, it is, except for some very rare circumstance, a worthless policy.

There some other 'adjustments' that can be made but for the most part  this should suffice

---

### Post by apostra on 2010-08-10
Hey there,

what i did was, right click file-> properties-> open with-> choose the wine and then all my file.exe was on default for wine.

---

### Post by corncob on 2010-08-11
> **ShadowMage said:**
> 
Just thought I'd throw this out there, since for example CD-ROMs are read-only, and you might not be able to change the executable bit.


That's what I thought but, thinking again, I'm using this same CD that was executable in previous Ubuntu versions and now in 10.04 it isn't.  So this executable flag must be in Ubuntu and not on the CD?

---

### Post by cogadh on 2010-08-11
Not really. The default action on all executables in Ubuntu has always been "no execute", they just kind of ignored Windows executables until now.

---

### Post by corncob on 2010-08-12
I just found this page
[http://www.ubuntu-user.com/Online/News/Ubuntu-User-DVD-10.04-Lucid-Lynx-apt-package-manager-bug](http://www.ubuntu-user.com/Online/News/Ubuntu-User-DVD-10.04-Lucid-Lynx-apt-package-manager-bug)
It looks promising and I don't see that anybody else has posted it.

---

### Post by Lennon V C on 2010-10-03
BTW OP, There is a native linux version of Guitar Pro 6. So you don't have to use the EXE version.

---

### Post by Arkaine34 on 2010-10-10
i have the same issue going on on my ntfs partition.i cannot execute wow.exe and can't mark it as an executable file either.

---

### Post by freshmeatz on 2010-11-18
the posted fix "wine start /unix %f" works for me,

---

### Post by BigGreyhound on 2012-03-30
> **mc4man said:**
> If you wish to revert this nonsense, other than the various workarounds, then 
```
gksu gedit /usr/share/applications/wine.desktop
```Look for this line
Exec=cautious-launcher %f wine start /unix
and edit it to 
Exec=wine start /unix %f

Until this is implemented as a warning with a choice to proceed or not, it is, except for some very rare circumstance, a worthless policy.

There some other 'adjustments' that can be made but for the most part  this should suffice
Thank you so much, you have no idea how long I've looked for this. Now that I've disabled that annoyance, any idea how to get wine to install multiple disks? This works like a charm for first install disk but second disk is not visible.

---

