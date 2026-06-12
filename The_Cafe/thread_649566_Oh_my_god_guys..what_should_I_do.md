---
title: "Oh my god guys..what should I do?"
date: 2007-12-25
forum: The Cafe
---

### Post by blithen on 2007-12-25
I was looking at a video and a pop up came up and it told me I had 3 HIGH alert viruses..
Please I need help, screenshot attached..



To bad those things are fake and this confirms it 100% :D

---

### Post by LaRoza on 2007-12-25
Virus alerts are great social engineering ploys. Don't click on them, unless you are using Linux, of course.

---

### Post by Iceni on 2007-12-25
Can you run a virus in wine?

---

### Post by LaRoza on 2007-12-25
> **Iceni said:**
> Can you run a virus in wine?

The virus could delete any files that it has write access to.

The Windows exploits wouldn't work, as most viruses should exploit the registry and the Windows default admin account and file associations.

The problems with Windows viruses running in Wine are few, as the Windows holes that are exploited are not present in Linux. Also, a VBScript program wouldn't run (The "I Love You" virus was written in VBScript (I have a copy of it))

---

### Post by Nekiruhs on 2007-12-25
> **Iceni said:**
> Can you run a virus in wine?
Apparently not very well. We should file a bug so that the people coming from windows don't have to go without their viruses.
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

---

### Post by LaRoza on 2007-12-25
> **Nekiruhs said:**
> Apparently not very well. We should file a bug so that the people coming from windows don't have to go without their viruses.
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Also, Windows malware usually exploits open ports that aren't open on Linux.

Try this in Linux, it would never work. (Don't worry, it isn't a virus, just a weird fact of Windows allowing scripts to do things from the browser) It opens all your cd drives.

When embedded in a web page, it can cause interesting effects :) (Doesn't work in Vista and IE7)

Note: I edited it so it won't run, unless you already know how to write it.

```

Set oWMP = CreateObject("WMPlayer.OCX.7")
Set colCDROMs = oWMP.<script edited to preserve sanity>

if colCDROMs.Count >= 1 then
        For i = 0 to colCDROMs.Count - 1
                colCDROMs.Item(i).Eject
        Next ' cdrom
End If

```

---

### Post by Polygon on 2007-12-25
that scared the sh*t out of me when i was little, just surfing a web page and suddenly notepad opens and has a message saying if my cd drive is open, i have spyware on my computer (and sure enough it opened without me pressing the button). AFter that i researched ways to keep my windows computer safe...and eventually here i am ;)

---

### Post by vishzilla on 2007-12-25
Stare at the screen and wonder what would happen if you had Windows ;)

---

### Post by EdThaSlayer on 2007-12-25
You should shut down your pc and enjoy the holidays with a cup of hot cocoa.

---

### Post by Linuxratty on 2007-12-25
Go to trend Micro and run House Call as you drink the coco.

---

### Post by LaRoza on 2007-12-25
> **EdThaSlayer said:**
> You should shut down your pc and enjoy the holidays with a cup of hot cocoa.

And yet you are logged on.

---

### Post by Tundro Walker on 2007-12-25
LOL!

I remember running across a web-site that did a pop-up "scan" like that.  I thought "wth?"  All these .dll's and stuff were flying by, and it was detecting viruses.  Then I just started laughing.

"I'm in ur Backdoor!  Alertin ur levels!"

---

### Post by blithen on 2008-01-08
> **Tundro Walker said:**
> 
"I'm in ur Backdoor!  Alertin ur levels!"

LOL!!

---

### Post by Linuxratty on 2008-01-08
Because i was always up on how secure my system was,I ignored stuff like that. 
 I'm amazed people are still doing that,as one "company" got into a heapa' trouble for doing such things.

---

### Post by Tristam Green on 2008-01-08
Funny.  I *just* repaired one of my wife's friend's computers after she clicked one of those links.

Freaked her machine GOOD.

---

