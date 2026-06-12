---
title: "Installing games"
date: 2010-07-17
forum: Wine
---

### Post by vvil2 on 2010-07-17
I'm new to Ubuntu and cannot figure out how to install Sims 2 or any other computer games I have. I've tried Wine but nothing it's not working. Can someone please help? I have no idea what I'm doing

---

### Post by Nick_Jinn on 2010-07-18
Have you tried Playonlinux or Wine Doors?

Enable third party repositories and download from Synaptic.

Its hit or miss, but try them both.....otherwise there is always Cedega.

---

### Post by vvil2 on 2010-07-18
Thanks
That got it installed (Sims 2), but now i cant get it to play on my computer, what am I doing wrong?

---

### Post by Nick_Jinn on 2010-07-18
Which one did you use?

When you use the command line there are all kinds of information and clues given. Why dont you tell us what you got? Try copying and pasting.

---

### Post by vvil2 on 2010-07-18
I opened it through wine, the Sims 2 launcher pops up so I click Play. Then a message comes up that says "Direct3D returned an error: D3DERR_INVALIDCALL! The application will now terminate"

I also installed Hospital Tycoon. I can get it to start with wine (like the intro to the game starts) but then "The program HospitalTycoon.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience."

---

### Post by Nick_Jinn on 2010-07-18
Have you installed your video card drivers?

There should be some step by step instructions, or you could try PlayonLinux or Wine Doors for an alternative installation.

---

### Post by vvil2 on 2010-07-18
I tried playonlinux, thats how I installed them. They wont run through that for me though...or maybe I just don't know how.
How do I install video card drivers? and I can't find wine doors to even install it

---

### Post by cogadh on 2010-07-18
Don't even bother looking for Wine Doors, it has [gone defunct]("http://www.wine-doors.org/") and has been mostly replaced by other Wine front ends like PlayOnLinux.

It would probably help if you could give us some details, like hardware specs, Wine version and Wine's error output. There is a sticky at the top of the forums that explains the kind of info we need to be able to help you.

---

### Post by Nick_Jinn on 2010-07-18
Playonlinux hasnt really been working out for me lately. It played Morrowind, but no sound in Oblivion (now it wont even load), and no luck whatsoever with fallout 3.

Neither Sedega nor CX games seem to support it either.

---

### Post by MattBD on 2010-07-18
> **vvil2 said:**
> I'm new to Ubuntu and cannot figure out how to install Sims 2 or any other computer games I have. I've tried Wine but nothing it's not working. Can someone please help? I have no idea what I'm doing

Sadly, The Sims 2 doesn't work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633)
Wine isn't perfect and many games just don't work with it.

However, apparently The Sims 3 does work with Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732)
So you could make the jump to that and run it on Ubuntu.

Older games often tend to work better - I've successfully run Homeworld on Wine, albeit somewhat shakily. If you have some older games that will run in DOS, you can use DOSBox to run them - I love UFO Enemy Unknown and that's a great way to play that.

---

