---
title: "Installed eSword and Not Getting Anywhere"
date: 2008-03-28
forum: Ubuntu Christian Edition
---

### Post by Pursuer on 2008-03-28
Hi, I am Jess. Please bear with me, as I am new to all of this, but I am determined to be a part of this and learn my way through it.
The only previous Linux experience I have is OpenOffice, so this is a whole new ballgame.
Our computer crashed and before we had it fixed, I learned of LInux as a whole, including Christian Ubuntu (I read about it in a homeschooling magazine - I'm a homeschool Mom). I knew that I could learn this, though utilizing my patience! SO, we had Ubuntu CE put on, and that's all I have now.
I love the idea of eSword, but when I finally got it installed, when I click on the icon, it doesn't open.
I also tried installing all of the add-ons that I wanted. The beginning icons are on my desktop (no idea why they are instantly going there), but when I try to click on them, it says that I need to wait, and then the little button just stays there - it has for hours now.
I would love to push through this and learn how to use this, tinker with it and contribute. 
In fact, as I said before, I am determined to. I think sharing programs rather than charging for them is a wonderful concept.
I am sorry that I made this long. If anyone willing to help me needs more information, I'm more than willing to share.

---

### Post by david_kt on 2008-03-28
Please try below instruction carefully:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

you should have a fully working e-sword.
Please let me know if you still face some problems not clear about the instruction.

DK

---

### Post by Pursuer on 2008-03-28
DK thank you SO much for your help and offer to help further.
IN just a split second you will see how new I am to this. ;)
Okay, I need to go here:
[http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)
Which is what I did. I have a little wine glass on my desktop now. :) It opens up eSword, but only has the KJV on it.
Then I am supposed to add the code:
wineprefixcreate --prefix .wine_Esword
Where do I enter that code (this is the point where you realize how new I am to this, but I promise I am a quick learner!)?
Again, thank you!
Once I know where to enter code, I have a feeling the direction on your  original thread will be much easier for me. :)

---

### Post by Catalyst2Death on 2008-03-28
you have to enter these commands in the terminal.  The terminal is somewhat analogous to the command prompt in windows (I'm assuming that's where your coming from).  

Basically, anything that you can do with the mouse, can be achieved with some sequence of commands in the console...  The result of all this is a lot more control over the operating system.  Your actually in the driver seat!  

Anyway, to answer your question, you need to open the terminal and type/paste the command in... you can do this by going to:

Applications (next to the ubuntu icon in the upper left corner of your screen) and then put the mouse over Accessories.  This will open a submenu which will allow you to select Terminal.  This is the prompt (your username@computername$) that you will type the command at. 

Hope this helps!  (jumping right into wine is difficult at times, don't let it scare you away from ubuntu!)

---

### Post by Pursuer on 2008-03-29
Catalyst - thank you so much! I think I can get it. We'll see.
On a side note, I love your handle. Thought-provoking.

---

### Post by Pursuer on 2008-03-29
Okay, I have gotten to the step of downloading the 4 dll (I actually felt a rush upon creating a "bottle" for eSword and seeing that it was successful!), but am not sure where to copy them to. The directions from the "How To Install" say th copy them to ~/.wine_Esword/drive_c/windows/system32), but when I tried to do that in the terminal, it said
> bash: syntax error near unexpected token `)'

I am sorry for going over each step in such agonizing detail. I really want to learn this, but I know NOTHING. Thank you in advance for your help.

---

### Post by david_kt on 2008-03-29
> **Pursuer said:**
> , but when I tried to do that in the terminal, it said




How exactly you tried to copy it? Please make sure the dlls are in lower case. And then, for example it is on your desktop, what you could do is open terminal, and issue below two commands one by one::

1. cd Desktop
2. mv *.dll ~/.wine_Esword/drive_c/windows/system32

Please let me know if you still face problems.

DK

---

### Post by Eutaw on 2008-03-29
> **Pursuer said:**
> Okay, I have gotten to the step of downloading the 4 dll (I actually felt a rush upon creating a "bottle" for eSword and seeing that it was successful!), but am not sure where to copy them to. The directions from the "How To Install" say th copy them to ~/.wine_Esword/drive_c/windows/system32), but when I tried to do that in the terminal, it said


I am sorry for going over each step in such agonizing detail. I really want to learn this, but I know NOTHING. Thank you in advance for your help.

You just need to delete the ')', then it will fly. If you did a copy and paste, just backspace once from the end of the line, should delete the ). If you typed the line, just don't put the ) on it.

---

### Post by Pursuer on 2008-03-29
Okay. Officially done for the night. I can't take anymore. LOL
I shut the computer down for a bit, and now that it's on, I can't even find the icon on my desktop anymore.
I am going to start over again on eSword, gcompris and my HP deskjet 3520 tomorrow or Monday. My brain is on overload!
I am not sure why it's missing or where to look for it even. I am not giving up, though. I just need to refocus.
Anyone have any ideas where I could find eSword? If I can't find it, can I get it back by downloading again?

---

### Post by david_kt on 2008-03-30
> **Pursuer said:**
> 
Anyone have any ideas where I could find eSword? If I can't find it, can I get it back by downloading again?

Please delete the .wine_Esword folder, and then follow the instruction here carefully:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Please let me know where (which step) you fail or you which step you could not understand.

DK

---

### Post by Pursuer on 2008-03-30
I deleted it from Places;Home Folder; User and Desktop. Then I deleted those from the trash can. I still see the icons "eSword" and "eSword Module Manager" under the Accessories tab, however.
Should I be all set to download a new eSword now?

---

### Post by david_kt on 2008-03-30
> **Pursuer said:**
> I deleted it from Places;Home Folder; User and Desktop. Then I deleted those from the trash can. I still see the icons "eSword" and "eSword Module Manager" under the Accessories tab, however.
Should I be all set to download a new eSword now?

Do not download using the "eSword" and "eSword Module Manager".

Just follow the instruction:

Download manually all the exe files from [http://www.e-sword.net/](http://www.e-sword.net/) as is you want to install it in microsoft windows.

After that, follow the instruction I give you on the link.

DK

---

### Post by Pursuer on 2008-03-30
I am back. Holed-up for the night. I will get at least this one issue tonight. If not, I am going back at it tomorrow first thing.
Okay, so I downloaded the e-Sword v7.9.8 application installation. Went through the setup process and it said it's installed. There is now a little diamond shaped icon with toggles in it and "setup798.exe" underneath it.
Now I create the "bottle" for WIne in the terminal, and go through each step in your "How to Install" directions thread, changing any "setup797" info for the terminal to "798," correct?

Ack. I am sorry I need baby steps, but I am a perfectionist and do not want to screw anything up on my computer. And this is literally the first time manually programming anything onto a computer for me. WIndows always did it for me. I am glad to be learning it myself though.
I can't even describe how thankful I am to you for being so patient and not snickering at me. Seriously, thank you! (I need a Linux for Dummies book.)

---

### Post by Catalyst2Death on 2008-03-30
all right, at this point, I would suggest installing esword into the default wine environment.  This is not ideal, but it will make the installation easier.  (its not ideal because the .dll files for esword, the ones you downloaded, have a slight chance of conflicting with other programs later on)

to install esword on a default wine install:

first download esword to your desktop,
then download the .dll files: 
> 
Download riched20, riched32, oleaut32.dll, and msls31.dll to your ~/.wine_Esword/drive_c/windows/system32 from here:

[http://www.dlldump.com](http://www.dlldump.com)

(Search the above 4 dll one by one and download it. After that, copy them to ~/.wine_Esword/drive_c/windows/system32)

Make sure all the above dll in lower case. If it is in upper case, rename it to lower case.

to rename files, either right click and select rename, OR type this in the terminal:
```
$ mv ~/Desktop/<name of file to be renamed> ~/Desktop/<new name>
```
this tells the computer to move the file in the path, /home/<user>/Desktop/<name of file> to /home/<user>/Desktop/<new name> which renames it

(helpful hint: if you want to speed up the process, you can use TAB completion. Just type the first few characters of the file/folder your interested and hit TAB.  It will finish typing the name for you! (this won't work if there are more than one file with similar names (ie myfile1234, and myfile4321.  If I were to type: my(TAB) it would output: myfile followed by a beep to let you know that it needs more information about the file name.  If you can't remember the full name, only the first part, keep pressing tab, and it will give you a list of all the files that match the first part of what your typing... Then you can finish typing the path.)

now we need to copy the .dll files to the wine folder:
```
$ cp ~/Desktop/*.dll ~/.wine/drive_c/windows/system32/
```
now you can run this: 

```
$ wine ~/Desktop/setup798.exe
```

now if all goes well you will be presented with the windows installer, which you should be familiar with.

after the setup finishes, you should perform this step:

> In winecfg set riched20.dll and oleaut32.dll to native.

```
$ winecfg
```

Press the Libraries tab > type riched20.dll > press add > press edit > choose Native (windows).
Do the same for oleaut32.dll.

now we remove the pesky .lnk file that the installer dropped on your desktop: 
```
rm ~/Desktop/*.lnk
```

now the setup should have created a shortcut on your desktop, which you should be able to click on like any other program. If you would like to change the icon from a wineglass to something else follow these steps:

> Change Icon on Launcher.
The launccer created uses default wine icon. If you want to use other icon, follow below step:
Right click the launcher and choose properties.
After that click on the wine icon, it will open a windows.
Navigates to the icon file you want.
If the icon you want did not appear in the navigation windows, change the extension to png.


here is a link to the .png
[http://blog.nick-brewer.com/wp-content/uploads/2008/02/icon_esword.png](http://blog.nick-brewer.com/wp-content/uploads/2008/02/icon_esword.png)
save this picture to your pictures folder by right clicking on it, and then selecting save image as... then click on the pictures folder and click save

now when it says to "naviagate to the icon you want" you want to get to your pictures folder. Initially, it won't show up, but if you click open you will get image previews of .png files in your pictures folder 

(for future use ubuntu stores all of its icons in the .icons folder in ~/.icons you will not be able to see this folder withough hitting CTRL+H when your in a folder browser (the period designates that the file is hidden) therefore you can save icons here, and not have to worry about seeing/accidentally deleting them)

---

### Post by dark_harmonics on 2008-03-30
> **Pursuer said:**
> 

Ack. I am sorry I need baby steps, but I am a perfectionist and do not want to screw anything up on my computer. And this is literally the first time manually programming anything onto a computer for me. WIndows always did it for me. I am glad to be learning it myself though.
I can't even describe how thankful I am to you for being so patient and not snickering at me. Seriously, thank you! (I need a Linux for Dummies book.)

Wow. The people who want to understand what drives people away from ubuntu should read this post... This community still amazes me with their patience and willingness to help. A thread like this one makes me proud to be part of it.

---

