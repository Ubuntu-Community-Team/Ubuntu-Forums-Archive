---
title: "USP on Gutsy Gibbon, problems go here"
date: 2007-09-08
forum: Ubuntu System Panel
---

### Post by 4tro on 2007-09-08
USP runs quite smoothly on gutsy, but there are small problems.
maybe we can collect them here.

my first problem is going to drive malac crazy i think :P
the reminder part of calrem and remind gives an error on gutsy
```

Plugin "remind" error
invalid literal for int() with base 10: '20071005T215959Z'
```

---

### Post by Malac on 2007-09-08
> **4tro said:**
> USP runs quite smoothly on gutsy, but there are small problems.
maybe we can collect them here.

my first problem is going to drive malac crazy i think :P
the reminder part of calrem and remind gives an error on gutsy
```

Plugin "remind" error
invalid literal for int() with base 10: '20071005T215959Z'
```Hi 4tro,
Due to my moving house hassles I've still not got round to installing any of my machines with Gutsy yet so I haven't had a chance to test any of the plugins or main app yet.
Thanks for the heads up about the reminders, as soon as I've got something up and running I'll look into this one first.

---

### Post by 4tro on 2007-09-09
if i can help you with reproducing the bug, I'd be happy to ;-)
and this isn't meant to make you work faster, just to discuss problems on gutsy gibbon

---

### Post by 16777216 on 2007-09-24
Some times trying to log out does nothing form USP yet the regular menu it works fine.
Though, it seems to happen less nowadays.
That is about the only thing I have noticed.
I use the glossy theme and have attached a backup of my config.

---

### Post by 4tro on 2007-09-26
i noticed that as well, maybe the command fails...

another problem i have is that sometimes it cannot get my username or logon time...

it shows some sort of, i guess, smiley
(:0)
and --pts/ for the logon date
and logon time is the real logon date
i included a screenshot....

---

### Post by 16777216 on 2007-09-26
I have had that happen as well but, not for a while now.

---

### Post by m0eman on 2007-10-10
Does LinuxMint send you their changes for their mintMenu? Right now on gutsy mintMenu is working flawlessly but I had a lot of trouble with usp, I'll be posting those bugs soon, I have to reinstall usp again. (I was changing things in the code to fix bugs I was getting and I want to start fresh again)

---

### Post by spockrock on 2007-10-14
I am trying to run usp on gutsy and when I try to add it I get an error saying the panel encountered a problem while loading OAFIID:GNOME_USP.

I try to run USP with the usp run-in-window and nothing pops up, and terminal is not giving me anything.

---

### Post by 4tro on 2007-10-16
> **spockrock said:**
> I am trying to run usp on gutsy and when I try to add it I get an error saying the panel encountered a problem while loading OAFIID:GNOME_USP.

I try to run USP with the usp run-in-window and nothing pops up, and terminal is not giving me anything.
i guess you did an upgrade from feisty?
try reinstalling usp

---

### Post by spockrock on 2007-10-17
I did that didnt work but I fixed an issue I was having with cairo and that seemed to fixed it.

---

### Post by virtualmaster on 2007-11-03
I had a couple problems installing 0.41 fro the provided deb on gutsy gibbon. I can't get control center to open and any changes to the menus aren't reflected in USP until reboot.

---

### Post by 16777216 on 2007-11-03
Some settings require USP to be removed then added back to the panel to take effect.
or you could type ( or copy / paste )  ```
killall gnome-panel
``` in a terminal this will cause the panel/s and all active applets to restart, your new settings will have taken effect then.

---

### Post by delfick on 2007-11-04
0.4.1 is old

I suggest using svn instead :D

[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

---

### Post by Erraticorder on 2007-11-09
i can't get the preferences to open in gutsy.  When i type uspconfig in a terminal i get this error.
```

Traceback (most recent call last):
  File "/usr/bin/uspconfig", line 610, in <module>
    app=MainWindow()
  File "/usr/bin/uspconfig", line 88, in __init__
    self.lang=self.language[0:2]
TypeError: 'NoneType' object is unsubscriptable

```

---

### Post by uzi09 on 2008-08-28
> **Erraticorder said:**
> i can't get the preferences to open in gutsy.  When i type uspconfig in a terminal i get this error.
```

Traceback (most recent call last):
  File "/usr/bin/uspconfig", line 610, in <module>
    app=MainWindow()
  File "/usr/bin/uspconfig", line 88, in __init__
    self.lang=self.language[0:2]
TypeError: 'NoneType' object is unsubscriptable

```

bump...same issue

---

### Post by Malac on 2008-08-29
> **uzi09 said:**
> bump...same issue
Looks like you are using the old 0.41 version of USP.
This is now obsolete for several reasons due to changes in GNOME and XORG.
 
If so please update USP to the 2.0 Beta SVN version.
Instructions here:
[http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)
 
Hope this helps.

---

