---
title: "Trouble Opening .Exes"
date: 2007-12-18
forum: Windows
---

### Post by DUDE_2000 on 2007-12-18
I've accidentally made .exe files open with wordpad. Does anyone know how to fix this

I'm using Vista home premium at the moment.

---

### Post by lespaul_rentals on 2007-12-18
Right-click an .exe and select "Open With," from here you should be able to select cmd.

---

### Post by DUDE_2000 on 2007-12-18
it doesn't give me that option, but I can run exe files be calling them cmd files

---

### Post by LaRoza on 2007-12-18
Go to Control Panel, (use classic view) and choose "Default Programs", go to "Associate File Extension...", and you should be able to change it there.

Next time, don't do whatever you did.

---

### Post by DUDE_2000 on 2007-12-18
The default programs won't let me access exe files; they are excluded from the list

---

### Post by tgalati4 on 2007-12-18
That's Vista's way of protecting yourself from pointy scissors.  All of mine have bent tips and cut like crap.

---

### Post by Antman on 2007-12-18
> **DUDE_2000 said:**
> I've accidentally made .exe files open with wordpad. Does anyone know how to fix this

If the Vista EXE association is damaged the location in the registry most likely changed is in this key...

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.exe] 

The "OpenWithList" and "UserChoice" subkeys probably have some program listed as opening the .EXE file extension. These need to be cleared and, when cleared, the system will go back to the default and the EXE extension should then work again.

You can do this by creating a .REG file with these lines in it...

Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.exe] 
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.exe\OpenWithList] 
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.exe\OpenWithProgids] 
"exefile"=hex(0): 

Use cut/paste to copy these five lines to an editor like Notepad and then save the file with a .REG file extension. Copy the file to the misbehaving Vista machine and double click on it (or right click and select Merge). You will likely have to say OK to a number of different things (the user access control and the registry editor for certain) but afterward (and a restart to be certain) the system EXE association should come back.

[B][COLOR="Red"]Warning!
Editing the System Registry can have seriously affect your system. Make no changes to the System Registry without having a complete backup of important files and only after setting a System Restore Point.[/COLOR][/B]

---

### Post by DUDE_2000 on 2007-12-18
> **tgalati4 said:**
> That's Vista's way of protecting yourself from pointy scissors.  All of mine have bent tips and cut like crap.

but preventing you from pointy scissors means you are ever so more lured to accidentally stab yourself with a knife.

---

### Post by rickyjones on 2007-12-19
You might want to try System Restore. Unless you can't even run that executable...

---

### Post by DUDE_2000 on 2007-12-19
I did. After rebooting with Antmans registry fix I didn't get a desktop at all, only a black screen with a "My Documents" window open. As it turns out, My computer automatically made a restore point yesterday, so I restored back to that.

Thank you everyone, for helping.

---

