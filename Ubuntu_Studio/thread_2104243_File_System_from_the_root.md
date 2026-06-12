---
title: "File System from the root"
date: 2013-01-12
forum: Ubuntu Studio
---

### Post by animaguy on 2013-01-12
I used Thunar file system on Linux Mint and one of the features I got used to was the ability to open a File from the root.

In Ubuntu Studio the File Manager does not have that feature.

I tried to learn what File Manger is used in Ubuntu Studio and apparently it is Thunar.

Question:

Does anyone know how to open a File from the root using the default File Manager in Ubuntu Studio?

---

### Post by sudodus on 2013-01-12
What do you mean by root?

1. the root file system /
2. the superuser id 'root'

---

### Post by animaguy on 2013-01-12
Thank you for the reply.

When i was using Linux Mint and I wanted to file manage I would open up the default Thunar File Manager.

A lot of my files in my external storage disk are locked. 

So if I wanted to unlock a file to open, move or copy I had two choices:

1) Terminal command sudo su chmod a+rwx 

2) open up a File Manager and right click a file on the left side panel and click "open as root".

I do not know whether it was as a "root" or superuser.

I just know that I could open, move or copy files easier than using the chmod command.

---

### Post by sudodus on 2013-01-12
I see: that means to run thunar with the user id root.

You can do that with the terminal command

```
gksudo thunar
``` but it is not recommended. This way, Thunar will be very powerful, and you can easily damage your file system for example remove a lot of files or change a lot of permissions by mistake.

Instead I suggest that you check what file system is used on your external disk. If it is a windows file system, FAT32 or NTFS, the permissions will be set when the drive is mounted, not individually for each file/folder as with linux file systems. So it is an alternative to change how you mount the drive (change the permissions). If you are not sure about the file system, please post the output of the following command
```
sudo blkid
``` in a reply.

---

### Post by AstroLlama on 2013-01-13
you mean when right-clicking on a folder there is an option to open the folder as root. it prompts for password then opens it as root. Very useful, yes. 

There is a nautilus extension which will give you the same functionality 
[http://www.hecticgeek.com/2012/12/useful-nautilus-extensions-ubuntu/](http://www.hecticgeek.com/2012/12/useful-nautilus-extensions-ubuntu/)

---

### Post by Losgann Mor on 2013-01-14
By default, Ubuntu Studio uses Nautilus for the file manager, not Thunar, despite using XFCE as the desktop environment. I personally prefer Thunar, and it's easy to switch back to it: go to Menu > Settings Manager > Preferred Applications, select the Utilities tab, and under File Manager select Thunar from the drop down list. Now when you go to the menu and click on File Manager, you have Thunar instead of Nautilus.

For the open as root thing: Mint XFCE comes with several so-called "custom actions" preconfigured in Thunar, of which the "Open as root" option is one. To create the open as root custom action in Ubuntu Studio (or Xubuntu) do the following:

1. Open Thunar and go to Edit > Configure Custom Actions.

2. Click the plus icon to add a new action. A dialog box will open up entitled "Create Action".

3. Under the Basic tab, enter the following:
Name: Open as root 
Description: Open folder as root user
Command: gksu Thunar %F

4. Under the Appearance Conditions tab, do the following:
Ensure that under "File Pattern" the field contains an asterisk (in other words "File Pattern: *"). It should appear by default, but put it in if it does not.
Uncheck the "Text Files" box.
Check the "Directories" box.

5. Finally, click the OK button at the bottom and the "Open as root" custom action will be saved and you should be good to go.

---

