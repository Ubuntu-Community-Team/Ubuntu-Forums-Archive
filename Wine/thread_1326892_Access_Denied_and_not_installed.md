---
title: "Access Denied and not installed"
date: 2009-11-14
forum: Wine
---

### Post by webbdawg on 2009-11-14
When I try to use wine to run an install exe on a cd  I get access denied.

Then I go to the wine application menu and and click on Browse C: and I get the error message that the C: is not installed.

I go to the file manager and I can see that there is the home/wine/c:

What give with this?

I have looked at the Wine Configuration but I am not sure what needs to be what.

Thanks
Dave

---

### Post by beastrace91 on 2009-11-15
What program are you trying to install and with what Wine version?

~Jeff

---

### Post by webbdawg on 2009-11-15
Thanks for the response B.

I was trying to install my MM Studio 8 and have found that there are some probmels with it.

[B]I solved the issue by 
- going back to windows and coping the install CD to my flash drive
- Switching back to Kbuntu and copying the files/folders the hard drive
- Running the Wine install for each individual program I wanted, not the suite install which I read had issues.

Needless to say it worked.[/B]

What I am not sure I understand is **Why I could not copy the Studio 8 CD to the hard drive while in Kbuntu.** Several of the files and folders would copy but many would not. It must have had something to do with permissions on the CD and I could not get around them. HOw would I have gotten around this if all I had was Kbuntu?? **Any thoughts on that??**

---

### Post by beastrace91 on 2009-11-15
There *shouldn't* be any special permissions on the CD you are trying to copy from (as far as I know). Where were you trying to copy files to on your hard disc? Also did you try copying the files as root? This should solve ANY permissions problems you have when writing files as the super user can do as they please. To access the a super user folder view under KDE I believe either of the following two commands should work: ```
sudo dolphin
sudo konqueror
```

Regards,
~Jeff

---

### Post by webbdawg on 2009-11-15
Thanks B, I just login like always, open Dolphin file manager. 

I use the split view because it is very much like the old DOS XTree program (now you know I am an old fart LOL). I have my home folder on window and the CD in the other. I highlight, copy and paste. Then I get the message that this file and that file cannot be read.

I remember seeing once where I had the option of logging on a disk or file as root. I think there was a check box in the right side of dolphin. But that was not in split view. I might have to go back and see.

---

