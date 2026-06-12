---
title: "Trying to install CorelDraw 8 to run in Wine"
date: 2010-11-18
forum: Wine
---

### Post by grey1beard on 2010-11-18
I have been running Draw in windows for many years, and now that I've installed meerKat, I'd like to try running it in Wine.
I know there  are other possibilities, but this is my current bit of masochism.;)
I have the cd in the drive, and looking for an installer, I realised I have no idea how to identify the correct file.
As an alternative I tried right clicking corelDrw.exe to change the permissions to executable, but it denied this as it was a read only file. Trying to change it to read/write was also denied.

If anyone could give me a pointer towards how to find the correct file, I'd be most grateful.
John
After thought - Do I need to create a folder and copy the whole disc into that first ?

---

### Post by grey1beard on 2010-11-18
I tried copying the Program folder(which contains the coreldraw exe file) onto the desktop. This then appeared to allow me to change the .exe file permission to executable, and tell it to open with the wine installer.
However, no link has appeared in the wine folder, and if I double click on the icon in the desktop folder the timer icon appears, but nothing then happens.
I left the cd in the drive in case that was necessary, but zilch.

Perhaps I have to copy the whole disk onto the desktop first ?

John

---

### Post by grey1beard on 2010-11-19
Well, this is going to be a fairly short thread.

With the Cd in the disk drive I copied all the folders/files onto the desktop.
Then created a folder to place them all in(28 folders + some files).
Found the coreldrw.exe file in the programs folder, made it executable, and opened with wine.
It then went through the familiar installation process as in windows, and on my first test seems to be running as expected.
Hope this helps anyone else along the same path.
John

---

### Post by fcigoi on 2010-12-28
Hi John,

That's good news, thank you.
Only one question though: what version of Wine are you using ?
There seem to be two in Maverick, a stable version and a (final?) beta.

---

### Post by grey1beard on 2010-12-28
Hi fcigoi.
Wine ver 1.2.1 according to my "About".
I have had some issues with Corel however. copy/paste causes it to crash, which isn't terribly helpful !
Due to time pressure, I've carried on using it in windows for the moment, and then using a memory stick to bring files over to this system for posting.
All a bit complex here, and the whole idea to use it in Wine is to simplify life.

I'm sticking with Corel for the time being, as with >>10 years use and stored files, switching to inkscape et al would be quite a slow process for someone as long in the toth as me ;)
John

---

### Post by grey1beard on 2011-07-02
Just an update for anyone trying the same installation.
I'm now running 10.04LTS on my laptop, with Wine 1.2.2.
The installation only had minor differences from that described above. I also changed the permissions for the setup.exe file in Programs, double clicked on that and away it went.
It is possible that I did likewise the first time, and omitted that from my post.

John

---

### Post by John-B on 2011-07-02
Have you ever printed in Corel when running in wine?

---

### Post by grey1beard on 2011-07-02
Hi John-B,
Alas, no. 
But that is probably because I have the added complication of having a Ricoh Gel printer, and I never managed to get that set up in either 8.04 nor 10.10.
I might have another go in 10.04, being something of a masochist ;)

Regards
John

---

### Post by grey1beard on 2012-04-29
Just an update.
I have now installed CorelDraw 8 in Wine 1.2.2 running on 11.04.
The display of the various roll-ups in the corel window is more like I remember them on XP, but the "Copy" problem still exists, causing the prog to crash.
I now wonder if this is caused by something not set up correctly when I do the installation ? Perhaps some other files need to have permissions altered.
Goodness knows how one could find out, but if anyone has any thoughts, please let us know.

---

