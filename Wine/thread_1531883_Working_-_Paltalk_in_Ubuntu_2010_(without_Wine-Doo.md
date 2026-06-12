---
title: "Working - Paltalk in Ubuntu 2010 (without Wine-Doors)"
date: 2010-07-15
forum: Wine
---

### Post by gothsm on 2010-07-15
Welcome to my tut, this is updated to work without the use of Wine-Doors because its now offline, Thanks to everyone who has worked on getting paltalk in linux. This tutorial was tested several times using Karmic (9.10) please make sure your Ubuntu install is up to date before following this tutorial.

Things that you need to download

[wine_0.9.61~winehq0~ubuntu~8.04-1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_0.9.61%7Ewinehq0%7Eubuntu%7E8.04-1_i386.deb")
[IEs4Linux 2.99.0.1]("http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.99.0.1.tar.gz") (extract to desktop)
[MSN Messenger 7]("http://www.microsoft.com/downloads/details.aspx?familyid=cf49c56c-8b3e-4eae-9904-9505f47bed45&displaylang=en")
[Paltalk Messenger]("http://www.paltalk.com/download_auto.shtml")


Doubble Click wine_0.9.61~winehq0~ubuntu~8.04-1_i386.deb then click 'Install Package'

then enter your terminal and copy and paste each line and do as it ask

sudo aptitude install cabextract
cd Desktop
cd ies4linux-2.99.0.1
./ies4linux --no-gui
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
winetricks riched30 richtx32 vb6run wsh56

Close Terminal

Right Click Install_MSN_Messenger.exe 'Open with Wine Windows Program Loader'
Right Click pal_install_r17742.exe 'Open with Wine Windows Program Loader'
*note if you cannot speak on mic but you are able to hear, unmute your mic

:popcorn: Paltalk is now installed and working, enjoy 

Questions? Message SDF-Monoxide on paltalk.

---

### Post by cogadh on 2010-07-15
People were still using Wine-Doors? I thought that had gone defunct years ago.

---

### Post by headcase2 on 2010-07-26
whats up gothsm... fist off, just wanted thank you for that awesome tut... second of all, i did everything u said to do by installing pal talk... i was impressed for a minute when it was working, but then it crashed... now im using ubuntu 10.04 lucid... does that have anything to with pal talk not working... thanks in advance for the response

-DaviD-

---

### Post by gothsm on 2010-07-31
Yes last tutorial used wine-doors, I updated it a bit excluding a few runtimes from the last tutorial that caused pal to glitch a bit more then it already does using winetricks. Its still a work in progress I have not tested on 10.04 because it runs vary bad on this system I will try to test in 10.04 soon.

The runtimes excluded from the last tutorial are
Visual C++ runtime libraries
Visual Basic 5 Runtime

Note* File sends do work if you download msls31.dll and place it in your wine paltalk folder

---

### Post by bou3lam on 2011-01-14
same here as headcase2 , paltalk worked fine for some 3 or 4 minutes then crash , have you please found any solution for this ?
thanks

---

### Post by balvasar on 2011-04-17
> **gothsm said:**
> Welcome to my tut, this is updated to work without the use of Wine-Doors because its now offline, Thanks to everyone who has worked on getting paltalk in linux. This tutorial was tested several times using Karmic (9.10) please make sure your Ubuntu install is up to date before following this tutorial.

Things that you need to download

[wine_0.9.61~winehq0~ubuntu~8.04-1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_0.9.61%7Ewinehq0%7Eubuntu%7E8.04-1_i386.deb")
[IEs4Linux 2.99.0.1]("http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.99.0.1.tar.gz") (extract to desktop)
[MSN Messenger 7]("http://www.microsoft.com/downloads/details.aspx?familyid=cf49c56c-8b3e-4eae-9904-9505f47bed45&displaylang=en")
[Paltalk Messenger]("http://www.paltalk.com/download_auto.shtml")


Doubble Click wine_0.9.61~winehq0~ubuntu~8.04-1_i386.deb then click 'Install Package'

then enter your terminal and copy and paste each line and do as it ask

sudo aptitude install cabextract
cd Desktop
cd ies4linux-2.99.0.1
./ies4linux --no-gui
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
winetricks riched30 richtx32 vb6run wsh56

Close Terminal

Right Click Install_MSN_Messenger.exe 'Open with Wine Windows Program Loader'
Right Click pal_install_r17742.exe 'Open with Wine Windows Program Loader'
*note if you cannot speak on mic but you are able to hear, unmute your mic

:popcorn: Paltalk is now installed and working, enjoy 

Questions? Message SDF-Monoxide on paltalk.

Thankyou so much for that, although I keep getting cut off from chat , it has installed.

---

### Post by gothsm on 2011-05-14
Paltalk will crash when using black nicknames due to the banner refresh. I've not keept up on using paltalk in linux so I've not improved it if you have questions or would like to continue the fight to run paltalk in linux you can find me on paltalk nickname 'Mr Mobile'

---

