---
title: "Unable to play counter strike"
date: 2009-10-20
forum: Wine
---

### Post by subinthegladiator on 2009-10-20
Hi every body...

I installed Counter strike 1.6 using wine, installation was successful without showing any error message,but i am unable to play the game,,,, when i double click the icon , it shows "opening counter strike" for few seconds and then disappears....
Wat could be the problem.. please guide me...


Thanks


Subin

---

### Post by beastrace91 on 2009-10-20
What Wine version, what graphics card, and what driver version?

~Jeff

---

### Post by AllRadioisDead on 2009-10-20
Run it via terminal.
cd to your directory
then run:
```

wine counterstrike.exe

```
(Replace counterstrike.exe with whatever the applications name is)
Then post the output.

---

### Post by asenine on 2009-10-21
> **ihermit said:**
> Run it via terminal.
cd to your directory
then run:
```

wine counterstrike.exe

```
(Replace counterstrike.exe with whatever the applications name is)
Then post the output.
If this is the steam version, this will not work. You must run:

```
wine Steam.exe -applaunch 10
```

Software using Steam tends to use Steam DRM, launching it outside the client won't work.

---

### Post by beastrace91 on 2009-10-21
@ihermit and asenine - Most Wine cases like this are often solved by simply having to install GFX drivers or upgrading/downgrading your Wine release. Always try one of these before sending a new person to terminal to collect what could be useless information :) For now just wait for the OP to respond (and FYI there are a few version of CS out there still that do not require Steam to run)

~Jeff

---

### Post by OpenGuard on 2009-10-22
Weird .. I have been playing Counter Strike through Wine since 08 - works fine, except, it does have a weird mouse sensitivity ( due to Compiz ).

---

### Post by subinthegladiator on 2009-10-24
i opened the terminal and typed " wine counterstrike.exe " and received the following error message 
Wine :could not load L"C:\\windows\\system32\\counterstrike.exe": Module not found
:confused::confused:

---

### Post by OpenGuard on 2009-10-24
> **subinthegladiator said:**
> i opened the terminal and typed " wine counterstrike.exe " and received the following error message 
Wine :could not load L"C:\\windows\\system32\\counterstrike.exe": Module not found
:confused::confused:
 
```
 
wine "C:\\Program files\\Valve\\hl.exe -game cstrike"

```
 
** Not sure if that's the right path, so .. browse Wine's C: drive and replace it.

---

### Post by beastrace91 on 2009-10-24
> **beastrace91 said:**
> What Wine version, what graphics card, and what driver version?

Help us, help you,
~Jeff

---

### Post by Daddy1 on 2009-11-01
If you are using wine and you also but you counter strike directory in the wine program files, right click on the .exe file and choose open with wine. This should work. If you still have a problem, come back here with more information about you wine version and hardware 
info and someone should be able to help you.

---

### Post by Daddy1 on 2009-11-01
> **OpenGuard said:**
> Weird .. I have been playing Counter Strike through Wine since 08 - works fine, except, it does have a weird mouse sensitivity ( due to Compiz ).

OpenGuard, how does your system run through wine with Counter Strike, are you are serious Counter Strike gamer, is the functionality smooth???

---

