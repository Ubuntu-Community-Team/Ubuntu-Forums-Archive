---
title: "Quickverse 2007"
date: 2008-05-23
forum: Ubuntu Christian Edition
---

### Post by ethanthekiwi on 2008-05-23
I am a new Linux user and I am trying to get a few Windows Applications to work on Ubuntu Hardy Heron. I tried to install Quickverse 11 (2007) using wine and it seemed to install fine. But when I go to Applications - Wine - Programs - Quickverse 2007, it shows the wait sign and a tab appears in the task bar saying "Starting Quickverse..." but then it dissapears and nothing happens.
If you have any ideas please let me know and please don't suggest using esword/gnomesword or anything else, because this is $100 software with lots of books that I am pretty sure esword can't open.

---

### Post by tak1150 on 2008-05-23
It'll help to see what the terminal says about the error.
To do this,
1. Right click on the menu on your panel
2. Select "Edit Menu"
3. Find the icon for Quickverse that Wine created
4. Find out what the command is for QuickVerse
5. Copy + Paste that command into your terminal and execute
6. See what it says

BTW, e-Sword does open books and Bibles from Quickverse (though I don't know about newer versions). Before e-Sword came out with NKJV, I used to use the NKJV Bible file from Quickverse in e-Sword.It's the button called "STEP reader" in e-Sword and from there you can open Quickverse and other materials.
Also (not trying to meddle, but) if the books of interest are from old days, there is a good chance that e-Sword has them for free.

Tak

---

### Post by ethanthekiwi on 2008-05-31
I have been trying to get some other programs to work in addition to Quickverse, so I recently installed some different graphics drivers. I then decided to reinstall Quickverse. After I reinstalled it and ran it, it asked if I wanted to register. I did not do this last time I installed so I tried it this time. I registered and the Quickverse actually opened and came to the screen.:) My excitement quickly disappeared when I realized that all the text was messed up. Some of the letters and the end of most of the words longer than 5 letters were on top of each other. In addition most of the colors and buttons were strange looking. As I was deciphering the menus trying to find graphics options, I accidentally closed the program. And now it is doing what it did before. When you click on the shortcut a tab appears in the task bar (or whatever its called in Linux) saying "starting Quickverse..." then it disappears and nothing happens.

After all that I tried what tak1150 suggested and ran the program in terminal. It said:

linux:~$ env WINEPREFIX="/home/ethan/.wine" wine "C:\PROG~FBU\QUIC~0SK\qv11.exe" 
fixme:ole:CoResumeClassObjects stub
fixme:atl:AtlModuleInit SEMI-STUB (0x3f5178 0x3f5020 0x3f0000)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE

and when I did this, no tab appeared in the task bar.
Thanks in advance for any help. In the mean time I might investigate esword.

---

### Post by david_kt on 2008-06-01
> **ethanthekiwi said:**
> 
linux:~$ env WINEPREFIX="/home/ethan/.wine" wine "C:\PROG~FBU\QUIC~0SK\qv11.exe" 
fixme:ole:CoResumeClassObjects stub
fixme:atl:AtlModuleInit SEMI-STUB (0x3f5178 0x3f5020 0x3f0000)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE

and when I did this, no tab appeared in the task bar.
Thanks in advance for any help. In the mean time I might investigate esword.

I wanted to help but I could not find any quickverse 2007 downloadable to try. But if you want to try e-Sword, please try below instruction:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by Matthew Wiebelhaus on 2008-06-01
> **ethanthekiwi said:**
> I am a new Linux user and I am trying to get a few Windows Applications to work on Ubuntu Hardy Heron. I tried to install Quickverse 11 (2007) using wine and it seemed to install fine. But when I go to Applications - Wine - Programs - Quickverse 2007, it shows the wait sign and a tab appears in the task bar saying "Starting Quickverse..." but then it dissapears and nothing happens.
If you have any ideas please let me know and please don't suggest using esword/gnomesword or anything else, because this is $100 software with lots of books that I am pretty sure esword can't open.
I know that this is pretty expensive software and if it doesn't open it probably means that it isn't going to work. I've noticed that one each upgrade with wine more and more applications do not work, which this should be the opposite. Anyway you can try downgrading your wine version and this may fix the problem. If not you can install e-sword, which may open the books which it probably does, or you can install bible time or gnome sword < which you told us not to suggest :(

---

### Post by jonathonblake on 2008-06-15
> **tak1150 said:**
> 
BTW, e-Sword does open books and Bibles from Quickverse (though I don't know about newer versions). 

Quickverse 5.0, 6.0, and 7.0 used STEP format for resources. Assuming that they are not password protected, they can be opened using e-Sword.

Quickverse 8.0, 9.0, 10.0, and 11.0 use CROSS format.  e-Sword does not read this format.

xan

jonathon

---

