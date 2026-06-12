---
title: "XP boot problem"
date: 2008-02-19
forum: Windows
---

### Post by xieu90 on 2008-02-19
hi I'm using a 64 bit computer so I use Xp 64 bit and Gutsy also 64 bit
so far I always used ghost to restore my XP and if I remember well it never had boot.ini file or ntldr, ntdetect there

and it still runs
then I installed gutsy 
they runs together well with eachother and I have reinstalled gutsy and restored xp a lot of time

recently I tried Vista but then I didn't like it and went back to xp and I also reinstalled gutsy 
I was so bored
and now I got a great trouble here

I can boot into gutsy
when I ghost XP back and boot into it I always get a message says that ntldr file is missing
when I copy it from Xp install Cd to my hard disk then another message pop up

Windows couldn't start because the following file is missing or corrupt
<Windows root>\System32\ntoskrnl.exe
Please reinstall a copy of the above file

I found a file name "ntoskrnl.ex_" in folder AMD64 in x64 Cd and I copied it there but it doesn't work and I can see a file name ntoskrnl.exe in system32 on my hard disk too

tired of ghosting, I was forced to really reinstall Xp64
but on the half way after formating and reinstalling I got that message when Xp boot to continue installing

what should I do now ?

(I need Xp to play hehehe)
Vista eat a lot of place, and with xp64 I already installed a bunch of programs, so I'd rather stick with it

---

### Post by PmDematagoda on 2008-02-19
This thread has been moved to the Windows Discussions section.

---

### Post by mimada on 2008-02-19
I have a separate computer with XP just for games. Most Windows utilities and applications seem to work okay in Ubuntu under Wine.

For your current problem, I suggest that you delete the old "ntoskrnl.exe" (or just change the file name to "ntoskrnlOLD.exe". Rename the "ntoskrnl.ex_" to "ntoskrnl.exe" and see if that fixes your problem.

Also, have you considered a hard drive switcher (just Google it). It might save you some time and aggravation if you can't afford or don't have the space for another computer.

---

### Post by Golem XIV on 2008-02-19
> **mimada said:**
> I have a separate computer with XP just for games. Most Windows utilities and applications seem to work okay in Ubuntu under Wine.

For your current problem, I suggest that you delete the old "ntoskrnl.exe" (or just change the file name to "ntoskrnlOLD.exe". Rename the "ntoskrnl.ex_" to "ntoskrnl.exe" and see if that fixes your problem.

Also, have you considered a hard drive switcher (just Google it). It might save you some time and aggravation if you can't afford or don't have the space for another computer.

Usually in Windows the .ex_ extension means that the file is compressed.  Try to extract ntoskrnl.exe from ntoskrnl.ex_ using some decompression utility (I would try with cabextract, **sudo apt-get instrall cabextract **if you don't have it installed).  I don't know if file-roller or ark support the Windows CAB format.

---

### Post by xieu90 on 2008-02-19
thank you guys
after all I I didn't have boot.ini and then I have one but it pointed to wrong partition
I'm revived, thank you

---

