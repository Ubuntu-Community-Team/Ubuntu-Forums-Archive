---
title: "Running One Note 2007 using Wine"
date: 2011-03-16
forum: Wine
---

### Post by rule4peace on 2011-03-16
Hey,
So I have a dual boot with ubuntu and windows and realized that the only reason I used windows anymore was for OneNote in order to take notes for classes.

I am running:
Ubuntu 10.10
Wine 1.2(Windows 7 settings)
Office 2007

I installed Office using wine, the installation was completed properly and at first glance there does not seem to be any missing files in the Program Files directory. However when attempting to run the file I receive an error message saying:
One Note Critical Error Recovery

prompting me with 4 options
-start normally
-clear cache
-delete setting
-Office diagnostics

I tried all the offered options none leading me to a solution. 

I tried launching it directly from the C: drive using the onenote.exe located in the microsoft directory with no success

I made a VM in which i tried to install wine and office again under which it still did not work.

Does anyone of you have an idea for me to get passed this issue? Or otherwise a good alternative for OneNote on ubuntu? I've tried evernote but I dont necessarily like the feel of it.

Thank you all

---

### Post by IHeequ5i on 2011-03-16
You could try Basket as an alternative to One Note.

---

### Post by mastablasta on 2011-03-17
there are plenty notes alterantives. have a look in software center. i realise One Note is perhaps more advanced, but linux alternatives are not bad either.
 
depends really what kind of notes you are taking. for simple ones tomboy does the job just fine.

---

### Post by rule4peace on 2011-03-20
I'll probably try using basket since i use one note for school and tomboy notes wouldnt really work for that but basket seems like it would work quite well, thank you

---

### Post by tgalati4 on 2011-03-20
I like zim.

sudo apt-get install zim

---

### Post by cogadh on 2011-03-20
[OneNote doesn't work in Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2911"), so I don't think any of us will be able to suggest a fix for that, you'd be much better off with one of the above suggestions.

One question though:
> **rule4peace said:**
> Hey,
I made a VM in which i tried to install wine and office again under which it still did not work.

What do you mean by this? Why did you install Wine and Office in a virtual machine and what OS did you install it on? If you have a VM to use, you could install Windows and Office in it then try to run it that way, but that is very cumbersome.

---

