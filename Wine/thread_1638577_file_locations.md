---
title: "file locations"
date: 2010-12-05
forum: Wine
---

### Post by etsah57 on 2010-12-05
I am new to Ubuntu and don't understand the file location system. The program that I have loaded through wine would normally have it's completed files downloaded to c:/program files/graboid/completed but, this doesn't work and I get the error message "please make sure that your completed download folder exists on your computer".
I have tried:
/media/graboid/completed
/colin/downloads/graboid/completed
/home/colin/desktop/graboid/completed
plus a few variations, but I always get the same error message and I can't download.
I don't know what I am doing wrong and would appreciate help
Colin

---

### Post by init1 on 2010-12-05
> **etsah57 said:**
> I am new to Ubuntu and don't understand the file location system. The program that I have loaded through wine would normally have it's completed files downloaded to c:/program files/graboid/completed but, this doesn't work and I get the error message "please make sure that your completed download folder exists on your computer".
I have tried:
/media/graboid/completed
/colin/downloads/graboid/completed
/home/colin/desktop/graboid/completed
plus a few variations, but I always get the same error message and I can't download.
I don't know what I am doing wrong and would appreciate help
Colin
Wine has it's own file directory system. You should find the files in "/home/colin/.wine/drive_c/program files/graboid/completed" or somewhere else in "~/.wine/drive_c". Note that ".wine" is a hidden directory, so you'll have to have hidden directories enabled to see it in Nautilus.

---

### Post by handy on 2010-12-06
You'll need to enclose your path in double quotes "" because of the space in Program Files too.

---

### Post by etsah57 on 2010-12-06
> **handy said:**
> You'll need to enclose your path in double quotes "" because of the space in Program Files too.

Still frustrated, 
I set up the folders in .wine/drive_c
In the Graboid program preferences I set the directory as      
/home/colin/.wine/drive_c/program files/graboid/completed
but this didn't work, then as per your suggestion I redid it as
""/home/colin/.wine/drive_c/program files/graboid/completed""
but this still doesn't work. What am I misunderstanding about the process?
Thanks
Colin

---

### Post by init1 on 2010-12-06
> **etsah57 said:**
> Still frustrated, 
I set up the folders in .wine/drive_c
In the Graboid program preferences I set the directory as      
/home/colin/.wine/drive_c/program files/graboid/completed
but this didn't work, then as per your suggestion I redid it as
""/home/colin/.wine/drive_c/program files/graboid/completed""
but this still doesn't work. What am I misunderstanding about the process?
Thanks
Colin
It should be 
"/home/colin/.wine/drive_c/program files/graboid/completed"
not
""/home/colin/.wine/drive_c/program files/graboid/completed""

Hope this helps

---

### Post by etsah57 on 2010-12-06
> **init1 said:**
> It should be 
"/home/colin/.wine/drive_c/program files/graboid/completed"
not
""/home/colin/.wine/drive_c/program files/graboid/completed""

Hope this helps


This is getting silly! I have now noticed that whenever I open the program it asks me for my password, even though I tell it to save, it doesn't.
Then, I have found that when I add the file location in preferences as
/home/colin/.wine/drive_c/program files/graboid/completed
it stays there, if I click back on preferences it is still there. But, if I add the quotation marks,                 "/home/colin/.wine/drive_c/program files/graboid/completed"
and click save, when I click back on preferences the box is empty
Should I delete it and start again
Thanks
Colin

---

### Post by init1 on 2010-12-06
> **etsah57 said:**
> This is getting silly! I have now noticed that whenever I open the program it asks me for my password, even though I tell it to save, it doesn't.
Then, I have found that when I add the file location in preferences as
/home/colin/.wine/drive_c/program files/graboid/completed
it stays there, if I click back on preferences it is still there. But, if I add the quotation marks,                 "/home/colin/.wine/drive_c/program files/graboid/completed"
and click save, when I click back on preferences the box is empty
Should I delete it and start again
Thanks
Colin
Try
/home/colin/.wine/drive_c/program\ files/graboid/completed

---

### Post by etsah57 on 2010-12-07
> **init1 said:**
> Try
/home/colin/.wine/drive_c/program\ files/graboid/completed

Still can't get the program to recognise where to download to. I tried to put a folder on the desktop, thinking perhaps a shorter list to go through might be the answer, but this to has failed.

My other windows based program, e-sword, has seemed to open, it has made an icon on the desktop and I can see it in Applications, wine, programs, e-sword, but when I click on it I get the small round timer icon, and then nothing, not even an error message

Graboid and e-sword are the only 2 things keeping me in windows and I would love to have them both working in Ubuntu, but I just can't deem to get them to happen

Please help!

---

