---
title: "how to install microsoft office 2007 in ubuntu 10.01"
date: 2010-07-24
forum: Wine
---

### Post by BAB SWAIN on 2010-07-24
Hi,
i am new to ubuntu ,i just want to install Microsoft office 2007 in Ubuntu lucid lynx through wine. can any one help me the installation steps.
thank you.:)

---

### Post by enebre on 2010-07-24
just don't do that.  mr frankenstein [-X

---

### Post by ronnielsen1 on 2010-07-24
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)
> [SIZE=4]_**How To Install Microsoft Office 2007**_[/SIZE]     

   In current Wine, simply install as you would in Windows:  
   Make sure your version of wine is set to ***Windows XP***.                                                                 

   Insert the disk.
   Open the disk and right click on ***setup.exe***  and select "*Open with wine windows program loader*." Or open a  terminal, navigate to the disk, and run the installer with:           

   wine setup.exe                                        

   The progress bar in the installer window may stop when it reaches  about 2/3 of the way. The installation is continuing, even though the  the progress bar is not moving. Wait for it to finish.
   **Note :** No overrides are  needed to install Microsoft Office 2007.  However to get Microsoft Office 2007 to run correctly once it has been  installed some overrides may be necessary. See below for instructions.


Will work but there are some things you have to manually edit. If you follow the directions at winehq, it should work

---

### Post by BAB SWAIN on 2010-07-25
Thanks a lot  ronnielsen for the tip, i got it.

---

### Post by finny388 on 2010-07-25
Hello Bab,

I see you are new to the forums so I want to give you this tip:

If that solution worked for you it is a courtesy in these forums to mark your thread as SOLVED.

To do this, open the thread's page and at the top click on Thread Tools, then "Mark this thread as solved"

Thanks
:p

---

