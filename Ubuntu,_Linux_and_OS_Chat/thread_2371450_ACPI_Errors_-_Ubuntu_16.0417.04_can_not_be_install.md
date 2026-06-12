---
title: "ACPI Errors - Ubuntu 16.04/17.04 can not be installed"
date: 2017-09-14
forum: Ubuntu, Linux and OS Chat
---

### Post by julsy on 2017-09-14
[COLOR=#111111][FONT=Ubuntu]I have a problem with installing Ubuntu on my desktop computer.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I had Ubuntu 16.04 and Windows 10 dual boot. After one update of Windows, the Ubuntu installation disappeared. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to install it again with Ubuntu Live USB but when I clicked on 'Install Ubuntu' or 'Try Ubuntu without installing' I got the following errors:
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas][ 0.016192] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup [/FONT][/COLOR]
  failure, AE_NOT_FOUND (20150930/dswload-210)
  [ 0.016195] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog 
    (20150930/psobject-227)
  [ 0.016222] ACPI Exception: AE_NOT_FOUND, (SSDT:xh_rvp08) while loading 
  table (20150930/tbxfload-193)
  [ 0.021348] ACPI Error: 1 table load failures, 7 successful  [COLOR=#111111][FONT=Consolas]  (20150930/tbxfload-214)[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Ubuntu]This text is repeated on the whole screen and after the first time it seems blurry as if there are video card issues. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The same Ubuntu Live USB works fine on another PC.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried also with Ubuntu 17.04 - still the same errors. I deleted Windows installation as well and tried to install Ubuntu again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Without success.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then I tried Windows installation and it installed correct. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After a lot of researching in the web, I reached to the conclusion that I have to turn off ACPI in order to install Ubuntu. So I did it. It got installed but it behaved strange, the resolution could not be changed and it started to restarts repeatedly. So I deleted the installation again, considering turning ACPI off was not a good solution.[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]Has anyone ever had the same or similar problem? What are these errors displaying? How to fix them?[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]Any help would be greatly appreciated.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by murlou on 2017-09-18
I've had some similar AE_NOT_FOUND problems recently.

I noticed that in my case 16.04.3 and 17.04 ISOs couldn't be installed at all in my PC, even with ACPI off. I downloaded 16.04.1 and it installed normally.

Hope this can help you.
Cheers,
M

---

