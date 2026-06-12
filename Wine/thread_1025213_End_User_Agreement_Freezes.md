---
title: "End User Agreement Freezes"
date: 2008-12-29
forum: Wine
---

### Post by Dontechjuan on 2008-12-29
I am trying to install World of warcraft wrath of the lich king and i was able to unhide the "tome" files and got the installer working. However, after I select the language it brings me to the "End User Agreement" and freezes. According to the system monitor the installer enters into "zombie" mode, which I'm guessing is not a good sign. does anyone have any suggestions on how to fix this or even know of a way around the end user agreement?

---

### Post by tuxxy on 2008-12-29
Your best looking on the wineHQ site there likely to be a solution there if anywhere.

---

### Post by Dontechjuan on 2009-01-01
SUCCESS!! I finally figured it out. For those of you who are curious in how I got it working or anyone who has the same problem in the future I will go through the steps on how I got "Lich King" working.

1.Mounting the cd-rom drive with the "unhide" option. 

As stated above you must open the terminal and enter this line...
"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/"
However this did not work for me, because I do not have "/dev/cdrom". During one of the ubuntu updates it changed the folder name from cdrom to cdrom1 so i had to enter this line....
"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom1 /media/cdrom0/"
But it did not work either with or without the cd, i did get it working by opening the cd tray placing the cd in the tray entering the line on the terminal and when i did it pulled the tray in and it worked.

2.Copy the entire contents of the cd to a folder on your drive. 

I would suggest making a new folder on your desktop to copy the cd to. Do not copy it to the WoW folder.

3.Try running the "installer.exe" file.
If it works then great. If it freezes on the "End User Agreement" like it was doing on me then proceed to step 4.

4.Getting past the "End User Agreement"

As most of you know some games require you to go to the "configure wine" and add .dll files in the libraries tab. If you don't know where that is just click on "Applications" on the top left of your desktop on the toolbar, go down to "Wine", then "Configure Wine" and click on the "Libraries" tab. In this tab you can add .dll files and change their status to a couple of different options like, native, builtin, disable, ect. The problem that I was having was that a game I installed earlier required that I add the "mshtml.dll" and set it to "native". Having this .dll file added to the list was keeping the program from getting the data from online sources. I didn't know it when I was playing the original WoW and "The Burning Crusade" that when I started the game and the news page comes up that because of the mshtml.dll file it was not able to access the data for the news page. The same thing was happening to the "End User Agreement". So just write down on a piece of paper mshtml.dll(native), so that when you go to play the other game that requires it you'll be able to remember what to add to play the other game. And then remove the mshtml.dll from the list. Now open the "installer.exe" and it should work. If it does not then you may have another .dll file causing problems, so again start writing down all the .dll files you have added to your list and start removing them one by one and after each one try the installer. One should eventually work.

---

### Post by Nikeman121 on 2009-02-17
i cant see the words in Wine ? how you fix??

---

