---
title: "Problem with wine please help!"
date: 2010-12-24
forum: Wine
---

### Post by Suroh66 on 2010-12-24
I've been trying for a full day to get some of my games and a few other programs to run with wine. When I run winecfg in the terminal I get the message displayed below. And I get the same thing when I try to launch the game in the terminal through wine oblivion.exe, and again when i try sudo wine oblivion.exe it tells me I don't own wine.

fixme:advapi:SetEntriesInAclA 1 0x33f7d0 (nil) 0x33f818
fixme:advapi:SetSecurityInfo stub
fixme:dpnhpast:DllRegisterServer :stub
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33f120
fixme:iphlpapi:NotifyAddrChange (Handle 0xd6e8d8, overlapped 0xd6e8e0): stub 
 
this is a 64 bit btw. I've installed a few games such as Oblivion,The witcher, and world of warcraft. I have played world of warcraft on other laptops with linux in the past and never had a problem. The witcher has it's own problems but I should be able to at least play oblivion. I have to go to my .wine folder and then into my drive_c folder into the game folders and then start the launchers to get them up. As soon as I launch the games They either don't load at all or they crash. I've tried all the fixes for each game and nothing.I've uninstalled and reinstalled the games and again still nothing I'm still new to all this can any one help?

---

### Post by Suroh66 on 2010-12-24
I was able to get rid of the wine error message and finally got one of my games to load and play with out problems now to get the rest of em!:D

---

### Post by howefield on 2010-12-24
Thread moved to the Wine forum.

---

### Post by cogadh on 2010-12-24
I'd like to know what error message you got to go away, since none of that is actually an error message. The "fixme" messages are developer notes about things that still need to be worked on in Wine and, generally speaking, there is nothing an end user can do about them.

BTW - Never, ever run Wine with sudo or a root account. Doing that breaks the user permissions on your .wine directory and gives Wine, along with any potentially harmful Windows software (viruses, other malware) complete access to your system.

---

### Post by Suroh66 on 2010-12-24
Thanks for the advice I wont wine like that any more :) And as I said cogadh I'm still new to this so I considered that an error message forgive my ignorance of the linux systems. What can I say :D

---

