---
title: "Adobe Photoshop CS5 Install Problems"
date: 2011-02-03
forum: Wine
---

### Post by Tragic Pumpkin on 2011-02-03
I tried looking for solutions to this problem but found nothing so far. 

I am trying to install Photoshop CS5 on my Vaio laptop. I am a total noob to Linux and am committed to never going back to Windows or Mac. 

I have Installed the latest version of Wine and have downloaded the Photoshop CS5 trial directly from Adobe's site. 

When I launch the Photoshop.exe file I can begin the setup process. I can select trial version, language, and so on. But once the install begins. It gives me an error message saying "Your installation encountered errors. Please try restarting your system and installing again. [I did] The setup encountered an error(-1) during install. Please restart the machine and try again.

Any help will be greatly appreciated. 

ps: I understand that Ubuntu offers Gimp for free and the two are comparable. But I have used Photoshop for years and have grown very used to it.

---

### Post by sandyd on 2011-02-03
> **Tragic Pumpkin said:**
> I tried looking for solutions to this problem but found nothing so far. 

I am trying to install Photoshop CS5 on my Vaio laptop. I am a total noob to Linux and am committed to never going back to Windows or Mac. 

I have Installed the latest version of Wine and have downloaded the Photoshop CS5 trial directly from Adobe's site. 

When I launch the Photoshop.exe file I can begin the setup process. I can select trial version, language, and so on. But once the install begins. It gives me an error message saying "Your installation encountered errors. Please try restarting your system and installing again. [I did] The setup encountered an error(-1) during install. Please restart the machine and try again.

Any help will be greatly appreciated. 

ps: I understand that Ubuntu offers Gimp for free and the two are comparable. But I have used Photoshop for years and have grown very used to it.
copy instalation from windows. don't forget the registry keys.
[http://bugs.winehq.org/show_bug.cgi?id=22680](http://bugs.winehq.org/show_bug.cgi?id=22680)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)

---

### Post by Tragic Pumpkin on 2011-02-03
> copy instalation from windows. don't forget the registry keys.
[http://bugs.winehq.org/show_bug.cgi?id=22680](http://bugs.winehq.org/show_bug.cgi?id=22680)

[http://appdb.winehq.org/objectManage...sion&iId=20158](http://appdb.winehq.org/objectManage...sion&iId=20158)

Thank you. I will do what I can with this. I understand very little of these links. But I DO appreciate the help.

---

### Post by cornellg on 2011-12-21
I encountered the same problem during installation, but don't have Windows. Anyone know a solution?

---

### Post by OrangeVixen on 2012-02-11
It's a known bug in the Adobe Photoshop CS5 installer, see more info on the bug: [http://bugs.winehq.org/show_bug.cgi?id=22680](http://bugs.winehq.org/show_bug.cgi?id=22680)

There is currently no solution, does not work on wine-1.3.37.

---

