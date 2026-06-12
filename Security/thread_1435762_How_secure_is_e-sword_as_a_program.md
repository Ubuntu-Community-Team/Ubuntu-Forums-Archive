---
title: "How secure is e-sword as a program"
date: 2010-03-21
forum: Security
---

### Post by Synoc on 2010-03-21
I've been considering downloading e-sword (bible study program) I'd have to use WINE to do it I understand, but I also understand using WINE can allow viruses to operate within the  programs that use them. so my question is this... does anyone know how secure E-sword is as a program? anything that can be exploited? I've been hearing it's been targeted by malware, other people are saying no...

---

### Post by blueridgedog on 2010-03-21
There has been some discussion about virus and wine and the general consensus has been that it is easy enough to clean up from in the event of an outbreak while running wine as a normal user.

Take a look:

[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

(read the entire thread for some good information).

Statistically, you are probably safe using the program you have in mind.

How about a Linux bible study tool?

[http://linuxappfinder.com/package/xiphos/](http://linuxappfinder.com/package/xiphos/)

or

[http://linuxappfinder.com/package/bibletime](http://linuxappfinder.com/package/bibletime)

---

### Post by Synoc on 2010-03-21
I was using xiphos, but to get a lot of the functionality, you need to pay for the items, which I would have no problem doing... if I weren't broke. e-sword seems to be the most functional-for-free bible study program.

---

### Post by a.walker on 2010-03-22
I wouldn't worry too much about running e-sword in wine. Most of the security problems people seem to have in ubuntu are related to having remote Desktop and remote logins enabled. Just follow the no 1 rule of Wine security: don't run Wine as root.

You can also run the following command in terminal to unlink wine from /. 

```
unlink ~/.wine/dosdevices/z:
```

for more information about wine security read the security sticky at the top of this forum.

---

### Post by Synoc on 2010-03-23
deal

---

### Post by Rubicon_82 on 2010-03-24
[quote="a.walker"]
You can also run the following command in terminal to unlink wine from /. [/quote]

You should also be aware that the default wine configuration includes additional links outside of ~/.wine/, which are **not** explicitly mentioned in the security sticky.  Specifically, wine includes symlinks directly into $HOME in the form of the Windows 'My Documents' folder etc.  If you are concerned about what wine links to, you can try:
```

find ~/.wine/ -type l

```

In my case, with a freshly configured wine (Version 1.1.41, Lucid Beta 1), the following symlinks exist:
```

$HOME/.wine/drive_c/users/$USER/My Documents -> $HOME
$HOME/.wine/drive_c/users/$USER/My Music -> $HOME
$HOME/.wine/drive_c/users/$USER/My Pictures -> $HOME
$HOME/.wine/drive_c/users/$USER/My Videos -> $HOME
$HOME/.wine/drive_c/users/$USER/Desktop -> $HOME/Desktop
$HOME/.wine/dosdevices/z: -> /
$HOME/.wine/dosdevices/c: -> ../drive_c

```

The presence of symlinks directly into $HOME will allow programs access to your data with your normal (full) permissions.  If you plan on running an untrustworthy Windows program, you should consider the following:

**A)** Redirect those symlinks such that they don't point outside of the ~/.wine directory, or replace the symlinks with directories.  I wouldn't remove the links completely, as your program may behave inconsistently if it can't find a 'My Documents' folder.

**B)** Write an AppArmour profile to confine wine to the ~/.wine directory.

**C)** Create a non-privileged user without read access to your regular home directory.  Switch to this low privileged account to install and run your untrustworthy program.

---

### Post by jonathonblake on 2010-03-28
> **Synoc said:**
> does anyone know how secure E-sword is as a program?

I'm not aware of any exploits. OTOH, my focus is on trying to crash e-Sword, not exploit it.(OK, I also try to break the encryption it uses.)

e-Sword 9.x uses SQLite as the database engine. It does not validate data.  

> I've been hearing it's been targeted by malware, other people are saying no...

The malware has been with _resources_ for it, not the actual program. 
For example, a file purporting to be the NIV Family Bible Collection, actually was a command/control program for a botnet, a keylogger, and a something else. (All designed for Windows.)

If the only resources you use are from one of the following, you will be ok:
* e-Sword.net;
* eStudySource.com;
* Bible.org;
* e-Sword-users.org;

The Spanish Language e-Sword Resource Creators group also release resources that are "clean".  I've forgotten the URL they use for announcing new resources.   :(
[Read [email]e-sword-espanol@yahoogrupos.com.mx[/email] for Spanish language e-Sword support, and resource announcements.]

I'd also suggest to:
a) Use the e-Sword installer at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) for both the executable, and resources;

b) Put your e-Sword resources in a location other than the program executable. (IOW, not c:\Program Files\e-Sword.)

c) Periodically archive your resource collection, delete the entire WINE directory, then reinstall WINE, and your Windows programs;

jonathon

---

