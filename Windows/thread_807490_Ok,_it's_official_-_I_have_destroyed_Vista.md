---
title: "Ok, it's official - I have destroyed Vista"
date: 2008-05-25
forum: Windows
---

### Post by Playa1313 on 2008-05-25
I have been working on my tri/quad boots lately and was attempting to install Win XP alongside Vista, Hardy, Fedora, and OpenGEU.  Well, installing/formatting for XP messed up my partitions and I had to use Partition Image (Great program) to backup/restore my partitions.

Unfortunately, I accidentally restored my Hardy install onto my Vista partition (which I had not made a backup of).  Now my vista partition is toast... fdisk reports it as ntfs but gparted reports it as ext3.. etc.

My question is: What should I do with Windows?  I need to use Microsoft Office because I do not quite like the formatting of OpenOffice (may improve though).

I could either reinstall Vista(or XP) to its partition, use Vista/XP on a virtual Machine, or somehow find a way to get Wine to run Office 2003.

Any Suggestions?

Thanks,
Brian

---

### Post by nick09 on 2008-05-25
I would use the virtual Machine method because if Office is all you are really using Vista/XP for its better than muti-booting an OS.

---

### Post by Playa1313 on 2008-05-25
> **nick09 said:**
> I would use the virtual Machine method because if Office is all you are really using Vista/XP for its better than muti-booting an OS.

Thanks for the suggestion.

I was just thinking about this though - How much ram would it (Vista) require? (thinking about all of the systems being sold with 1gb+ ram for Vista)  I have 2gb of ram but an integrated graphics card so more like 1750mb

:\

Thanks,
Brian

---

### Post by cardinals_fan on 2008-05-25
If you have enough RAM, use VirtualBox.  If you don't have enough RAM... buy more RAM!  **Be sure to run Vista in classic mode / safe mode / whatever makes it look like Windows 98** - it saves memory.

---

### Post by Playa1313 on 2008-05-25
> **cardinals_fan said:**
> If you have enough RAM, use VirtualBox.  If you don't have enough RAM... buy more RAM!  

Or better yet: buy a desktop and not a laptop that doesn't support more than 2gb of ram :\.  

> **cardinals_fan said:**
> **Be sure to run Vista in classic mode / safe mode / whatever makes it look like Windows 98** - it saves memory.

That's a great suggestion, a very simple one.  I would just have to slim down vista by at least these things:
Disable Sidebar
Old XP login screen
Windows 98 theme
No screensaver
Firefox and not IE

Thanks,
Brian

---

### Post by wolfen69 on 2008-05-26
i have heard of people having problems running vista in vm. personally, i would install xp in vm. xp runs like a dream in virtualbox.

---

### Post by Balazs_noob on 2008-05-26
if you want to try Vista in VirtualBox
then i recommend this [http://www.vlite.net/](http://www.vlite.net/)
haven't tried it yet but it can make vista a lot slimmer :D

---

### Post by MaxIBoy on 2008-05-26
If the only thing you need it for is office, just use XP. Better yet, try running the installer for office under wine (probably won't work, but worth a shot.)

---

### Post by tbroderick on 2008-05-26
> **Playa1313 said:**
> 
I could either reinstall Vista(or XP) to its partition, use Vista/XP on a virtual Machine, or somehow find a way to get Wine to run Office 2003.

Any Suggestions?

Thanks,
Brian

I'd try wine first. It worked here:

[http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2008/01/running-ms-office-2003-under-linux-with.html)

---

### Post by smoker on 2008-05-26
have you tried the beta of OOo 3? info here:
[http://www.openoffice.org/news/index.html](http://www.openoffice.org/news/index.html)

you never know, the formatting might have improved so you no longer require ms office, or windows!

---

### Post by MaxIBoy on 2008-05-26
I've heard that so far, docx support in OpenOffice is severely crippled. They're still working on it.

---

### Post by gameryoshi600 on 2008-05-26
Use virtualbox with windows xp. give it 384 mb of ram to 512 mb

---

### Post by K.Mandla on 2008-05-26
Moved to Windows Discussions.

---

### Post by karellen on 2008-05-27
if you only need office why not simply install XP in a VM?

---

### Post by Playa1313 on 2008-05-28
Thank you for all of the suggestions and replies.

The program Balazs_noob recommended, Vlite, is so awesome!  I was able to remove so many unnecessary items from the dvd and recreate my own iso.  I now have two different isos which I am testing in the virtual machine to see which is lighter - both run around 280mb of ram and are only 5.5GB installed!!! WOW!

If one of these isos turns out to work for me, I will probably allocate about 20gb to Vista and go ahead and install it on its own partition.

Thanks,
Brian

P.S. Nlite is a great program to do the same thing for XP, but it doesn't work too well with my XP-upgrade CD (supposed to have windows <XP installed before using it).

---

### Post by smoker on 2008-05-28
> **Playa1313 said:**
>  ...Vlite, is so awesome!  I was able to remove so many unnecessary items from the dvd and recreate my own iso.  I now have two different isos which I am testing in the virtual machine to see which is lighter - both run around 280mb of ram and are only 5.5GB installed!!! WOW!...

shows what a bloat-hog vista is!
if only you could get rid of all the DRM crud with that app, it might make vista almost bearable...:lolflag:

---

### Post by Stefanie on 2008-05-31
> **Playa1313 said:**
> 

I could either reinstall Vista(or XP) to its partition, use Vista/XP on a virtual Machine, or somehow find a way to get Wine to run Office 2003.

Any Suggestions?

Thanks,
Brian

running office 2003 with wine is really easy. i was amazed how smooth the install was - just pop in the cd, "cd /media/cdrom" (or cdrom0 or whatever), and run "wine SETUP.EXE" , which opens the windows installer. 

the only problem is that wine doesn't install menu shortcuts, so you have to click the option "browse c-drive" in the wine menu and then browse to the folder office 11 or something like that.there you can find excel.exe, winword.exe, powerpnt.exe , ... :-)

---

