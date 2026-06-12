---
title: "[SOLVED] What DOS command line will force edject a cd in XP?"
date: 2008-05-31
forum: Windows
---

### Post by Rytron on 2008-05-31
Hi.
What DOS command line will force edject a cd in XP?
Thanks.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-31
I think you have come too soon to these forums as you can use the command "help" to list all of the commands. Anyway, I don't think there is a command to force eject it from you're computer.

---

### Post by LaRoza on 2008-05-31
> **Rytron said:**
> Hi.
What DOS command line will force edject a cd in XP?
Thanks.

DOS doesn't have such a command (unlike *nix). CD drives shipped with their own programs to control them.

You could probably find a utility for it online by searching.

---

### Post by Tomatz on 2008-05-31
> **LaRoza said:**
> DOS doesn't have such a command (unlike *nix). CD drives shipped with their own programs to control them.

You could probably find a utility for it online by searching.


I am sure there is as there is a well known exploit that some web pages use to do this?

---

### Post by Tomatz on 2008-05-31
> **Tomatz said:**
> I am sure there is as there is a well known exploit that some web pages use to do this?

Ahhh Laroz was right. I stand corrected.

I have found a visual basic script to do this though if that is any help:

```
Set oWMP = CreateObject("WMPlayer.OCX.7" )
Set colCDROMs = oWMP.cdromCollection

if colCDROMs.Count >= 1 then
For i = 0 to colCDROMs.Count - 1
colCDROMs.Item(i).Eject
Next ' cdrom
End If

```

---

### Post by LaRoza on 2008-05-31
> **Tomatz said:**
> I am sure there is as there is a well known exploit that some web pages use to do this?

Technically, it isn't an exploit, it is an oversight. VBS (and JS) can be used locally using the WSH, and it is just a poor design they can reach outside the browser. It won't work in IE7 (but can still be run from command line)

---

### Post by kerry_s on 2008-05-31
to force eject a cd, a paper clip can do it in a second.

---

