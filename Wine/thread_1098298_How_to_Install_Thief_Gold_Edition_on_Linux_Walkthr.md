---
title: "How to Install Thief Gold Edition on Linux Walkthrough"
date: 2009-03-16
forum: Wine
---

### Post by nova47 on 2009-03-16
Like many others I have an nvidia graphics card with drivers past version 8.xx and can't play Thief in Windows XP. Well that's why god gave man Ubuntu. Here's how I got Thief Gold Edition running on Ubuntu.

                         INSTALLING THIEF ON LINUX

I'm assuming if you're wanting to get Thief working on Linux you already know this but you'll be installing Thief via Wine.

1.) I couldn't get setup running properly at first something about directx. To get past that open up a terminal and type

/media/cdrom1/setup.exe -lgntforce

Replace /media/cdrom1 with wherever you're installing Thief from.

2.) Setup should start up. The one thing that fooled me is it didn't start right away. You'll have to minimize the setup and click ok on some warning message.

3.) At the end it will say something about intel codecs. I told it to go ahead and install. However if it starts searching for something about netscape just tell it to cancel.

4.) I noticed that during the game parts of the desktop liked to pop up. I found that right clicking remedied this problem.

5.) Next go to the Wine Configuration under the applications tab. You should see a tab labeled graphics at the top. Check the box that says "Allow directx apps to stop mouse from leaving their window".
If you need any more help just send me a message. Also make sure that "Allow the Window Manager to Control Windows" is selected.

6.) Finally go to the applications tab make sure that you change the Windows Version at the bottom to Windows 98.

Note: The one problem I have had is I can't seem to get the movies working in Ubuntu even with the win32 avi codec. I've noticed they run fine in Windows on WMP but you can only get sound on VLC (in Windows or Ubuntu). If someone comes up with a fix for this feel free to post it.

---

