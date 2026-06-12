---
title: "Cannot accept WOW Terms of Agreement"
date: 2009-05-03
forum: Wine
---

### Post by PHPCody on 2009-05-03
Hi,

I am running Ubuntu Jaunty and installed WOW tonight. My install went fine and I was able to log in, but then I get the message that I need to download a patch. No problem, until I tried to accept the Terms of Use. When I get to the bottom of the Terms of Use, the Agree button never activates. Has anyone has an issue with this and is there a workaround or fix?

Thanks.

---

### Post by garythegoth on 2009-05-03
> **PHPCody said:**
> Hi,

I am running Ubuntu Jaunty and installed WOW tonight. My install went fine and I was able to log in, but then I get the message that I need to download a patch. No problem, until I tried to accept the Terms of Use. When I get to the bottom of the Terms of Use, the Agree button never activates. Has anyone has an issue with this and is there a workaround or fix?

Thanks.

I guess your using WINE 1.01. Update to the latest version (1.1.20).....

Download either of these determined by your system type ....

32Bit - [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20~winehq0~ubuntu~9.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20~winehq0~ubuntu~9.04-0ubuntu1_i386.deb)

64Bit - [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb)

That should fix it....

---

### Post by PHPCody on 2009-05-03
> **garythegoth said:**
> I guess your using WINE 1.01. Update to the latest version (1.1.20).....

Download either of these determined by your system type ....

32Bit - [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20~winehq0~ubuntu~9.04-0ubuntu1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20%7Ewinehq0%7Eubuntu%7E9.04-0ubuntu1_i386.deb")

64Bit - [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb]("http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.20%7Ewinehq0%7Eubuntu%7E9.04-0ubuntu1_amd64.deb")

That should fix it....


Although I already had 1.1.20 installed, I uninstalled it and reinstalled it back. It worked the second time, giving me the impression that it may have been my Gecko install. Thanks for the fast feedback.

---

### Post by Silvercloaks on 2009-05-07
> **PHPCody said:**
> Although I already had 1.1.20 installed, I uninstalled it and reinstalled it back. It worked the second time, giving me the impression that it may have been my Gecko install. Thanks for the fast feedback.


I'm having a similar problem... I couldn't get Ubuntu to read the WoW disc (For some reason it's reading it as a Mac version of the disc) so I downloaded WoW Lich King and tried to run setup just by right clicking on the download and running in Wine.

Opens up the program fine, but when it comes to reading the Terms - I get to the bottom and it won't highlight "Agree" so I can click on it.

Should I just reinstall Wine?  I just installed it a few weeks ago from the "Add/Remove Programs".  If I reinstall it, will I have to reinstall all programs that I've installed already for it?

Sorry I'm a REAL noob to Ubuntu and have alot to learn.

---

### Post by adromidon on 2009-05-07
> **Silvercloaks said:**
> I'm having a similar problem... I couldn't get Ubuntu to read the WoW disc (For some reason it's reading it as a Mac version of the disc) so I downloaded WoW Lich King and tried to run setup just by right clicking on the download and running in Wine.

Opens up the program fine, but when it comes to reading the Terms - I get to the bottom and it won't highlight "Agree" so I can click on it.

Should I just reinstall Wine?  I just installed it a few weeks ago from the "Add/Remove Programs".  If I reinstall it, will I have to reinstall all programs that I've installed already for it?

Sorry I'm a REAL noob to Ubuntu and have alot to learn.

This can be temporarily circumvented if you have a valid windows installation copy the .dll files mshtml.dll and wininet.dll from your windows install and add them to your wine bottle in the windows/system32 folder. then in the wine configuration change the settings to the wininet.dll to native first and save.

This will allow you to be able to click the agree button but you may or may not be able to read the text. If you do this make sure you backup the wine versions of those two files and replace them after install and rever the settings in the configuration panel from native first to what it was on before

this is a work around and should by no means be considered an official fix just a way to get by with the current version

---

