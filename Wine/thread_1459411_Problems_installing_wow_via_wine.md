---
title: "Problems installing wow via wine"
date: 2010-04-21
forum: Wine
---

### Post by OSapo on 2010-04-21
Hi everyone,

i recently installed ubuntu on my computer and have some experience with debian already. So i read that it's possible to install and play World of Warcraft on ubuntu through wine. I used to play WoW in windows before, so I tried to install it in ubuntu using the instructions found here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

The problem is when i issue the comand *wine Installer.exe* it prompts a window with no title and the following content: 
"No installer data could be found. If this problem persists, please contact Blizzard Technical Support."

In the terminal, the output is:
"Missing symbol {LanguageCode}! (SymbolTable::UnmappedSymbolSubstitution)"
"fixme:ole:OleCreateStaticFromData (not shown), stub!"

I looked everywhere trying to solve this. The only thing close that i found is a reference to some hidden content on the cd's, witch could be solved by mounting them with the unhide option. Can't use that because i'm extracting the installation files from four iso archives, using Archive Manager. I don't have the installation discs, just the iso's and they worked fine under windows.

Any help would be appreciated. Thanks!

---

### Post by OSapo on 2010-04-21
Solved the problem just by mounting the iso file, instead of extracting.
Thanks

---

### Post by den1988 on 2010-07-16
While I was trying to install wow with the [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) guide.
I encouraged a problem with the "winecfg" command.
I don't really understand what must I do in the page that pops up.
However even while pressing the OK button after doing no changes,
The following line shoes up in the Terminal page "fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet".
What shall I do next?
Sincerely yours,
Denis.

---

