---
title: "Rosetta Stone v2.0.8.1 under Wine"
date: 2009-11-22
forum: Wine
---

### Post by toddbmobile on 2009-11-22
This is what I did to get Rosetta Stone to work under Ubuntu 9.10. I hope this helps someone else. Do all in this order.

**1.** Make sure your Ubuntu installation is up-to-date.

**2.** Install Wine; the version I am using is **1.0.1**

**3.** Make a directory in you home directory and call it the name of the language you are learning. In my case it is $\home\mydir\German

**4.** Copy all folders from your language disk to the directory you created. Do not copy an image or ISO file. _***** Do this before you install the Rosetta Stone application *****_

**5.** Open winecfg. First under audio tab make sure OSS driver is selected for the audio driver.

**6.** Under the drives tab click "add" new drive button. Then click "show advanced" button. under path click the "browse" button and find your language folder you created. You can create a folder for every language you are studying, and map a drive letter to it. Under type from the drop-down select cdrom. 

**7.** Now only after you have created and mapped all your language drives install the Rosetta Stone application. My version for Rosetta Stone is **2.0.8.1**.

**8.** Right click the Rosetta Stone setup.exe file and left click "Open with Wine Windows Program loader." This will install the Rosetta Stone application under Wine. When you come to the Quicktime prompt click ok to continue. You will get a **_PATH_ error box** just click ok on it.

**9.** _Uncheck_ launch Rosetta Stone at the end of install.

**10.** Launch Rosetta Stone from Wine/Programs from the application menu.

Rosetta Stone works like a charm! I would give it a Gold Wine install. If you follow my steps in order, I feel it will work fine for you. I am using Ubuntu 9.10.
[B]
UPDATE 5/11/2010 This works with Ubuntu 10.04 LTS just fine!!![/B]

---

### Post by Hedley on 2009-12-25
Thanks for the tutorial. Installation worked just like you said!

However, the program seems a bit sluggish at times, despite my new computer. Oh well, better that booting Windows just for one app.

---

### Post by SCDude2009 on 2010-01-07
Tried to follow this guide. When I load the application CD I can't see any files. Appears like a blanc CD (I'm using the original RS CD and had it previously installed in win2000). Anybody any ideas how to fix that? Thanks in advance. RS-Version: 3.4.3A, Wine-Version: 1.0.1

---

### Post by zantos1 on 2010-01-23
Worked for me. thanks

---

### Post by verachion on 2010-02-10
Worked a treat this guide should be stickied in the Beginners section, thankyou so much.

---

### Post by mitchellthegreat on 2010-02-15
&#1071; &#1073;&#1091;&#1076;&#1091; &#1075;&#1086;&#1074;&#1086;&#1088;&#1080;&#1090;&#1100; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081; &#1074; &#1084;&#1075;&#1085;&#1086;&#1074;&#1077;&#1085;&#1080;&#1077; &#1086;&#1082;&#1072;!

In english, "I'll be speaking russian in no time!"

---

### Post by NongA_TongE on 2010-04-12
Thanks for the instructions!  So everything worked fine (Karmic Koala) RS 2.0.8.1), with one exception.  I'm doing russian and the russian text is not displaying, just gibberish in the standard alphabet.  any ideas?

---

### Post by toddbmobile on 2010-05-11
Not sure about the Russian language. If I come across anything I'll post it here.

---

### Post by davitodd on 2010-05-27
I tried to follow you're instructions, but it didn't even load the program after I had installed it. Any help would be greatly appreciated. Thanks in advance.

---

### Post by aepa97 on 2010-09-14
Have same problem as SCDude2009.  Anybody have any idea how to solve the problem

---

