---
title: "Virtualbox - shared folders AND usb access - it doesn't work"
date: 2008-10-27
forum: Virtualisation
---

### Post by DeepSandwich on 2008-10-27
I can't find any set of instructions that work. Anywhere.

Ubuntu Hardy 8.10 AMD64 running Virtualbox 2.0.4_ose

with a virual windowsXP machine.


I can create the shared folders through the virtualbox control window with no errors.

Launch my winXP VM.

I installed "Guest Additions".

Open up the command prompt and type "net use x: \\vboxsvr\sharefolder". I always get this error:

"System error 53 has occured. The network path was not found"

What the hell?

--------------------------

Also:

When i open up the setting window through the virtualbox controls and look at the mounted hardware available... the USB otpion isnt even there. I want to be able to access my ipod through my VM. 

What the hell?

---------

I'm sorry for posting a redundant question, but every other thread i look at about these issues has instructions that i follow to the letter and nothing changes.

](*,)

---

### Post by basilwatson on 2008-10-27
&#12488;&#12521;&#12473;&#12473;&#12531; &#12491; &#12463;&#12481;&#12498;&#12452; &#12459;&#12463;&#12452; &#12488;&#12481;&#12514;&#12452; &#12475;&#12473;&#12521;&#12467;&#12522;&#12452;&#12514;

---

### Post by basilwatson on 2008-10-27
Sorry cant help you as I have the same problem , I do know that the software in the repository ( ose) by default does not allow you to enable usb , etc .. I am going to reload my VB system and see what happens 

Stephen

---

### Post by kevinality on 2008-10-28
The OSE (open-source edition) does not support USB or a few other functions that uses proprietary code.

The closed-source version is only available for Hardy (8.04) and older variants of Ubuntu, so I assume they'll eventually release a version setup for 8.10. If USB access still doesn't work with that release, then there's some other issue going on.

---

### Post by DeepSandwich on 2008-10-28
Thanks. I'll just wait and see.

---

