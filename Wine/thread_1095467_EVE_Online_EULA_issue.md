---
title: "EVE Online EULA issue"
date: 2009-03-13
forum: Wine
---

### Post by Ixonal on 2009-03-13
The issue is that it doesn't appear. The box for it does, and it tells me to scroll to the bottom to move on, but there's no text in the box and it won't let me scroll, so I can never get farther. Everything else seems to look right, I just can't get past that screen to play the actual game. I'm running Ubuntu 8.10 and Wine 1.1.16.

---

### Post by kidux on 2009-03-13
It sounds like a font issue. Do you have the mstcorefonts package installed? You may also need to get the actual TTF fonts from a Windows install.

---

### Post by Ixonal on 2009-03-13
still having the same issues after trying that and rebooting.

---

### Post by kidux on 2009-03-13
I'm not at my machine right now, but I think there is a setting in WINE itself to change the font, which EVE may be set to use an official MS TTF font. You can either get those (recommended) or try to force WINE to use a different font. I had the same problem, and getting the TTF's and messing with WINE's settings solved the problem. If you look at WINE HQ AppDB, there may be some information on what fonts are needed, or problems in general.

---

### Post by Ixonal on 2009-03-13
oops, I lied. it looks like it DID work after all, after I forced the issue. apparently none of the executables to install the fonts actually installed them to the right place (who knows where they actually are). So I went out and downloaded a couple .ttf files to stick in the C:\Windows\Fonts folder (got arial and verdana) and it showed up this time.

---

### Post by penalt on 2010-08-08
Sorry to revive this old thread but I am having the same issue.  Running Ubuntu 10.04 with Wine 1.1.42.  I keep getting the EULA box with no text in it and no ability to scroll down.

I have been able to gather that this has something to do with fonts and that I need to get some MS fonts into wine.  However, I am very new to Ubuntu and the directions I have found online might as well have been written in Klingon for all I can understand them.  Please help.....

---

### Post by buddah1620 on 2011-02-03
First access your wine fonts folder by going to your home folder.  Click "View" at the top menu, then click show hidden files.  Scroll down to ".wine" and double click that.  Then double click "drive_c".  Double click "Windows" Double click "Fonts".  Leave that window open.  Open the partition that you have windows on.  Access "C", then windows, then fonts.  The font files end with *.ttf  For instance - Arial.ttf   The idea is that you want to copy and paste the fonts you need "Arial" from your windows partition to wine.   Unfortunately, this is not working for me.  I still can not see the EULA and am stuck. :(

---

### Post by buddah1620 on 2011-02-03
Oh snap, I got it!  So, do what I just explained above.  Then restart computer.  Start EVE in Wine.  I got the blank EULA again.  I right clicked the blank field and selected copy all.  I then Pasted in text editer just to see what would happen.  shortly after that the EULA poped up.  I scrolled down, accepted, and the client is updating now.  Now, I'm sure it had nothing to do with the right clicking and pasting... It probably just needed a minute to load.  Good luck penalt. LEt us know how it worked for you.

---

### Post by buddah1620 on 2011-02-03
Meh, it keeps freezing up.

---

### Post by mg.mattgonterman on 2011-03-19
Wine doesn't include the Arial font, which is what the EULA requires.  Here's the fix:

Download the Arial True Type Font.
Source: [http://www.4shared.com/get/h6VD3TRz/arial.html](http://www.4shared.com/get/h6VD3TRz/arial.html)

-Copy or move the arial.ttf file to the WINE folder.
-Navigate to your home folder.
-Click EDIT, then PREFERENCES.  Check "Show hidden and backup files".  Close the window.
- Go to .wine/drive_c/windows/Fonts and put the font file in there.
- Close the explorer.  Undo the changed in step 3bb if you like.

---

