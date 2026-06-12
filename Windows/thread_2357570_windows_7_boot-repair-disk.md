---
title: "windows 7 boot-repair-disk"
date: 2017-04-03
forum: Windows
---

### Post by mj74 on 2017-04-03
Hi people
Can someone pls help me with this issue, when i turn on pc i get a black screen with a blinking underscore in my left upper corner.I have used a usb boot repair disk and i got the following results. [http://paste.ubuntu.com/24308472/](http://paste.ubuntu.com/24308472/)
I have no idea how to read the result, I need help.

---

### Post by oldos2er on 2017-04-03
Are you trying to install Ubuntu?  If so which version? Is your system UEFI or MBR?

---

### Post by mj74 on 2017-04-03
Hi
Im trying to get windows 7 running again, I think its MBR.

Im sry i didint mention what i was doing, i can see that now.

is it the wrong forum i have postet in?

---

### Post by deadflowr on 2017-04-03
> is it the wrong forum i have postet in?
Not anymore.
Thread moved to **Windows **sub-forum

---

### Post by mj74 on 2017-04-03
thank you

---

### Post by oldfred on 2017-04-03
But Boot-Repair is primarily for Linux booting issues. It can only install a Windows type boot loader and very little else to fix Windows.
You generally need to use your Windows repair disk or Windows installer's repair console.

       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/) 

Is it still Windows 7 or upgraded to Windows 10?
Errors shown are most typical with Windows 10 fast startup which is always on hibernated.
If Windows 7 then did you leave it hibernated, or it may need chkdsk from the repair console.

---

### Post by mj74 on 2017-04-03
Im not sure if it has been updatet to w10, and I dont know what hibernated means.
Nothing happens when i press f8, i can only acces bios by f2.

---

### Post by yancek on 2017-04-03
If you scroll down the boot repair output about one third of the way, you will see a number of messages indicating that various partitions could not be accessed because they are hibernated.  Look in the BIOS for any options related to 'hibernate' or 'fastboot' and turn them off.  You don't have any windows code in the MBR so I don't know how you could boot uness you were using UEFI and if that were the case, you would need to have an EFI partition with EFI files which you do not have.

The best solution to your windows boot problem would be to use the Repair option on the windows installation DVD to write windows code to the MBR.  You have all the necessary boot files on your windows partitions so that should work.  If you don't have the windows installation DVD, you might be able to download something from a windows site.

---

### Post by mj74 on 2017-04-03
I am looking for an system repair disc online to download,but have only find the one i used for that analyse.Cant seem to find one.
I will be looking into the bios for that hibanet or fastboot now.

there is only these options in the bios, they are all enabled
quietboot
networkboot
f12 boot menu
d2d recovery 
sata mode

---

### Post by yancek on 2017-04-03
Those look like the different boot options.  You have to have a lot more options than that for other than booting.  Do you still have the manual for whatever type computer you have?  If not, just do an online search for the system you are using, specific brand and model as most major manufacturers have online manuals available to read or download.  I think you should be able to find some kind of windows repair tool.

---

### Post by mj74 on 2017-04-04
SOLVED
I found and used this great tool [https://toolslib.net/downloads/viewdownload/255-winpese-x64/](https://toolslib.net/downloads/viewdownload/255-winpese-x64/)

just one problem though, now windows is in english wich is not my first language

---

