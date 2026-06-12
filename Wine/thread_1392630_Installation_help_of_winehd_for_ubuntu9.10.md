---
title: "Installation help of winehd for ubuntu9.10"
date: 2010-01-28
forum: Wine
---

### Post by ershibbu on 2010-01-28
I want to run .Exe file in ubuntu9.10..
I am download winehq1.1.36 n37.. Both are not install..Plz give me tut.
Thanks.

---

### Post by skymera on 2010-01-28
```
sudo apt-get update
sudo apt-get install wine 
```

What .EXE file is it?
Wine should be a last resort.

---

### Post by Sef on 2010-01-28
Moved to the WINE subforum.

---

### Post by ershibbu on 2010-01-28
> **skymera said:**
> ```
sudo apt-get update
sudo apt-get install wine 
```

What .EXE file is it?
Wine should be a last resort.

.Exe is file extension of windows...

---

### Post by Duskao on 2010-01-28
I'm quite sure he meant what program is the .exe for? Like a game or windows office etc. Either way, if you have added the repos for wine, or grabbed a .deb file in order to open a windows file with wine be sure to set up the default file extensions for .exe's and such to open with "Wine Windows Program Loader". Use "open with" if needed then choose it as the default.

---

### Post by ershibbu on 2010-01-28
guys plz suggest me which winehq.deb file is suits in ubuntu  9.10

---

### Post by ershibbu on 2010-01-28
guys plz suggest me which winehq.deb file suits in ubuntu9.10...

---

### Post by Puppyite on 2010-01-28
I realise this is not what you asked for but if all else fails [WINE](http://www.puppylinuxfaq.org/category/13/run-windows-software-in-puppy.html) is very easy to use in Puppy Linux.

---

### Post by Daddyo-613 on 2010-01-28
If I understand your question, you want to know how to install Wine in Ubuntu Karmic 9.10.

The simplest way is to follow these steps: 
 
**1. Add WineHQ to Software Sources:**  either click on this link or open a new tab in your browser and copy this address into your browser  [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb).   
Follow the instructions there to add WineHQ Apt Repository to your software sources, when you have done that;

**2. Open Synaptic Package Manager:** using your mouse go to the menus at the top of your desktop screen and click on System->Administration->Synaptic Package Manager;

**3.  Enter Password:** enter your password in the dialogue box that will appear;

**4. Update Lists:** at top left side you will see the word "reload" and an arrow shaped like a circle, click on that to update your list;

**5. Search for Wine:  **type in the word wine into box marked Quick Search and push enter;
[B]
6.  Mark Wine for Installation:[/B] a list of packages should appear, select wine1.2 by right clicking on it and choosing mark for installation, then click apply at the top of the screen and wine will automatically install.

I hope that's what you wanted to know. Good luck!

---

### Post by ershibbu on 2010-01-29
Bro i download three different type of packages 2 of 36 n 1 is 37.. But they all gives different2 error..
So i want to know how to over come these errors because i don't under stand what the means of error..

---

### Post by AllRadioisDead on 2010-01-29
Why don't you tell us what you've done so far, what you're trying to run, (ie: Name of program!), and what errors you're getting.

---

### Post by ershibbu on 2010-01-29
i want to run dotproxy.exe n yourfreedom.exe  n dot not framework3.5.exe...n java6.exe..
n i have downloaded these three files...: 1. wine_1.1.37~winehq0~ubuntu~9.04-0ubuntu1_i386.deb
                                                           2.wine_1.1.37~winehq0~ubuntu~9.04-0ubuntu1_lpia.deb
                                                           3.wine_1.1.36~winehq0~ubuntu~9.04-0ubuntu1_i386_2.deb
but all gives diffrent error ...
i am use ubuntu 9.10..

---

### Post by Daddyo-613 on 2010-01-29
My friend...we are having some difficulty understanding what you are trying to ask, so if we give you an answer that isn't the solution you're looking for, please forgive us. We are trying to help.

If your problem is that you don't have a working copy of Wine on your system and you're running Ubuntu Karmic Koala 9.10 then you may not have followed the special instructions on the WineHQ web page [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) for 9.10.

If you are using 9.10 then you don't have to download three different packages. It's quite easy. All you have to do is:

1.  **Open Software Sources:** Use your mouse and click on System->Administration->Software Sources;
2.  **Enter Password:** Enter your password in the box that will appear and press enter;
3.  **Open Other Software:** Click on the second tab that says "Other Software" and at the bottom of that box you should see "Add" with a green plus sign beside it. Click on "Add";
4.  **Add Apt:** just copy the line below and past it into the box that appears in the space marked "APT line"```
*ppa:ubuntu-wine/ppa*
``` and then click on "Add source" then "Close" and then "Reload";

Now you've added the Wine repository for Karmic Koala 9.10 and the version of Wine for your system will already be listed in your Synaptic Package Manager and can be downloaded from there. Please go back to my earlier post for detailed instructions how to do that.

Of course you can get copies of Wine from other sources and you can use terminal commands to do everything I've described above, but, it seems you may have been trying to install software sources for Wine that are for other versions of Ubuntu and are not the right ones for Karmic Koala 9.10. Those other sources should be removed.

I hope this helps you. If your question is something else, try to ask the question again using different words and maybe a little more explanation. Keep trying...your friends want to help.

Good luck!

---

