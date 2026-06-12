---
title: "Need help using WINE..."
date: 2007-11-07
forum: Virtualisation
---

### Post by some_los3r on 2007-11-07
I just recently downloaded Ubuntu, and I'm loving it! I've learned a lot of things so far. I was looking through the Add/Remove programs and found WINE. I thought it would be great so I downloaded it. I have no idea how to use it haha. I downloaded a Windows program to my desktop, but I don't know what to do from there. Hell, I'm not even sure if that's what I'm supposed to do. I only want a few Windows programs....a video converter, iTunes, and a video downloading client. So any help with this would be greatly appreciated. :) Thanks!

---

### Post by L815 on 2007-11-08
Download the program you want to install and save it to the Wine folder.

Navigate to the wine folder in terminal by doing 'cd /YOURUSERNAME/.wine'  ***Case sensitive***

In terminal type 'sudo wine filename.exe' and the install process should start.

---

### Post by some_los3r on 2007-11-08
Alright thanks...but what Wine folder? Do I have to make one? Or do I have to find it? I looked around a bit, but came up with nothing. Thanks for your help and patience.

---

### Post by Christopher Young on 2007-11-08
> **some_los3r said:**
> I just recently downloaded Ubuntu, and I'm loving it! I've learned a lot of things so far. I was looking through the Add/Remove programs and found WINE. I thought it would be great so I downloaded it. I have no idea how to use it haha. I downloaded a Windows program to my desktop, but I don't know what to do from there. Hell, I'm not even sure if that's what I'm supposed to do. I only want a few Windows programs....a video converter, iTunes, and a video downloading client. So any help with this would be greatly appreciated. :) Thanks!

Might I suggest looking for Linux alternatives?  In my opinion WINE should be used as a last resort.

After you install WINE: "sudo apt-get install wine" then "winecfg" <--Do not run as root.
Download the installers for the programs you want to use.  In terminal navigate to the folder where you saved them, and type: "wine installer.exe" where installer.exe if the file name.  If the install fails try looking in the wine application database ([http://appdb.winehq.org/](http://appdb.winehq.org/)) for the program and see if anyone else has had any luck. :)

Also, your "wine folder" is located at "/home/USERNAME/.wine/"

Navigate to your home folder in Nautilus and press CTRL + H to show the hidden file, .wine directory is one of them. :)

---

### Post by some_los3r on 2007-11-08
Alright thanks. What would you recommend as an alternative? This is getting confusing :confused:. I downloaded Crossover, but I couldn't figure out how to install custom programs. I wouldn't even need Wine or Crossover, but I can't find a good video converter. I could live with transferring videos and music to a Windows computer with iTunes in order to put them on my iPod, but I need a converter.

---

### Post by nobull on 2007-11-08
If your not looking to use the command line, you can navigate to the link in the menu called wine file.  This will bring up an explorer type view where you can navigate to the .exe file stored on your computer.  If the executable in on your desktop then you should be able to find it by clicking the H:\ on the top and scrolling down to Desktop.  Double click on the .exe and the program will install.  Before running the application locate the winecfg file, if it is not under system preferences or administration then it can be found under /usr/bin or searched for. Check the wine website [http://appdb.winehq.org/]("http://appdb.winehq.org/") for compatible applications list and special settings.  Run the winecfg script and set any special settings and windows version desired.


As stated above I use the wine emulation as a last resort.  There is a vast list of software for just about anything you want to do.

It might be outdated but here is some more information [http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

---

