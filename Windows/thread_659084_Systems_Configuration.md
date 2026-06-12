---
title: "Systems Configuration"
date: 2008-01-05
forum: Windows
---

### Post by gary1163 on 2008-01-05
One other thing:
In Systems Config (msconfig) under BOOT.INI, I get a message that reads:
It appears that the following line in the BOOT.INI file does not refer to a valid Operating System: "C:\CMDCONS\BOOTSEC.DAT=" Microsoft Windows Recovery Console"/cmdcons"

Would yo like to remove the BOOT.INI file?

Yes or No

Should this be removed or not?

Thanks
Gary
:guitar:

---

### Post by WearZeeP on 2008-01-05
You should definitely not remove it, as it is to Windows what GRUB is to linux.
You should rather remove the broken line from the file.

---

### Post by gary1163 on 2008-01-06
Please elaborate on that procedure...


Thanks
Gary
:guitar:

---

### Post by 67GTA on 2008-01-06
Here is a snippet from Windows help webpage:

To Delete the Recovery Console

Open My Computer.
Double-click the hard drive on which you installed the Recovery Console.
On the Tools menu, click Folder Options.
Click the View tab.
Click Show hidden files and folders, clear the Hide protected operating system files check box, and then click OK.
At the root directory, delete the \Cmdcons folder.
At the root directory, delete the file Cmldr.
At the root directory, right-click the Boot.ini file and then click Properties.
Clear the Read-only check box, and then click OK.
Open Boot.ini in Notepad, and remove the entry for the Recovery Console. It will look similar to this:
C:\cmdcons\bootsect.dat="Microsoft Windows Recovery Console" /cmdcons

Save the file and close it.

Modifying the Boot.ini file incorrectly may prevent your computer from restarting. Be sure to delete only the entry for the Recovery Console.  Notes:

To open My Computer, double-click the My Computer icon on the desktop.
It is recommended that you change the attribute for the Boot.ini file back to read-only after you complete this procedure. You may also want to hide your system files again.

---

### Post by gary1163 on 2008-01-07
Ok 67GTA,
But when I go to select BOOT.INI in the root directory I see a folder named BOOT and another one named BOOT.INI2, which should I select to go into properties with? In addition once I achieved this, do I simply just open NotePad,click New and browse my computer for the BOOT.INI? And finally once I've executed this, how exactly do I remove c:\cmdcons\bootsect.dat =Microsoft Windows Recovery Console?

Thanks for all your help
Gary
:guitar:

---

### Post by 67GTA on 2008-01-07
The easiest way is:

Click Start, click Run, type "sysdm.cpl", and then click OK. On the Advanced tab, click Settings under Startup and Recovery. Under System Startup, click Edit.

Then just highlight and delete the line. Make sure to get rid of the other files in my previous post.

---

### Post by gary1163 on 2008-01-07
Great! 67GTA, But what about this part:[COLOR="Red"]But when I go to select BOOT.INI in the root directory I see a folder named BOOT and another one named BOOT.INI2, which should I select to go into properties with? In addition once I achieved this, do I simply just open NotePad,click New and browse my computer for the BOOT.INI? [/COLOR]

Thanks
:guitar:

---

### Post by 67GTA on 2008-01-07
You can do it with notepad if you are administrator. The last post was how I always edited the boot.ini file. Either way will work.

---

### Post by gary1163 on 2008-01-07
Ok ! Cmdcons folder and Cmldr file are deleted, Now I have two options in the root directory, [COLOR="Red"]should I right click on the BOOT (configurations settings or on the BOOT.INI2  file? [/COLOR] I know past that point to go into properties and clear the read only box and iopen in Notepad to delete 
c:\cmdcons\bootsect.dat="Microsoft Windows Recovery Console"\cmdcons..Thanks I'm almost there.

:guitar:

---

### Post by 67GTA on 2008-01-08
It will be named BOOT.INI. Open the start menu, click on My Computer, click on the C:\ drive. It should be right there. If you have a BOOT.INI2 file there, then the original may have been overwritten. Check the BOOT.INI2 file and see if it contains the line you want to remove.

---

### Post by gary1163 on 2008-01-08
Thanks 67GTA...The file was in the BOOT.INI2 and I deleted it in Notepad,and Saved it! Does it matter that the BOOT.INI was overwritten? Is there anything I should have to worry about? Thanks again for all your help!

Gary
:guitar:

---

### Post by 67GTA on 2008-01-08
It doesn't matter. Your boot configuration was modified at some point. Did you manually install the Recovery Console? That may have done it. It should still boot fine. Your system was already using it.

---

