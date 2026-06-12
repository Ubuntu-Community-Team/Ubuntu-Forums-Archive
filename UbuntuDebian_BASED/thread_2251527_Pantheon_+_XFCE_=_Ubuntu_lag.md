---
title: "Pantheon + XFCE = Ubuntu lag"
date: 2014-11-04
forum: Ubuntu/Debian BASED
---

### Post by bio2 on 2014-11-04
i installed pantheon and kubuntu environments. when i tried kubuntu i didnt like it so i tried pantheon. only the background showed but i dont remeber which desktop environment showed tht background. it stopped loading and i wanted to switch back to ubuntu 14.04 (unity environment) because pantheon had frozen. now when i log into any environment i get the same blue background with a dog on it, it is very laggy and my folders and files do not appear on my desktot on the file manager it sayst tham my files are ther.
Pls HELP ASAP!!!

---

### Post by Frogs Hair on 2014-11-04
Is this Ubuntu with the Kubuntu desktop , XFCE , and Pantheon installed at the same time ?

---

### Post by bio2 on 2014-11-05
Yes it is have u got a solution???

---

### Post by Elfy on 2014-11-05
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Rob Sayer on 2014-11-05
Yes, I have a solution.  It may not be the one you want to hear but it'd probably be easiest and quickest to just pick the DE version you want to use and do a clean reinstall.

There's a lot of bad advice out there, and telling you it's fine to install multiple desktops is bad.  You can easily end up with problems caused by different DEs using different versions of the same library program, for example.  The only way I'd do it anymore is if one were a GTK based desktop and one was Qt like LDE.  Then there's much less chance because the DE libraries are different.

I wouldn't install multiiple Ubuntu DEs, and using an external untested ppa to install another just complicates things more.

If you reinstall try setting it up with a separate partition for the /home folder.  Then you can upgrade or reinstall in the future and keep your user settings and data.  Just remember to not format the /home partition when you upgrade and back up data anyway.  I wish a separate /home partition was the ubuntu default.

---

### Post by bio2 on 2014-11-05
i guess it has to be done thnx

---

### Post by keturidu2 on 2015-04-16
actually you won't have (or anyone else, who'll be brave enough to do thing like that) to reinstall everything. After installing elementary-desktop on my Xubuntu 15.04 i got the same blank background on Pantheon and very slugish desktop movements when i loaded back to Xubuntu. All i had to do is CTRL+ALT+F1 to get to console, there write sudo apt-get remove pantheon*. After that i could log in to Xubuntu and delete all files that was installed from elementary/daily.

---

