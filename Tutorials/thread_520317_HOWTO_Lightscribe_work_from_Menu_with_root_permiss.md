---
title: "HOWTO: Lightscribe work from Menu with root permission (SCRIPT)"
date: 2007-08-08
forum: Tutorials
---

### Post by AegisTalons on 2007-08-08
This is my first how-to. I wrote it so you can follow it step by step. Hope everyone enjoys it and finds it useful.

So you got LightScribe working. If you have not check out these threads:

[HOWTO: Install Lightscribe Software]("http://ubuntuforums.org/showthread.php?t=289922")
[How-to: Lightscribe under Feisty Fawn]("http://ubuntuforums.org/showthread.php?t=512742&highlight=lightscribe")

This has been tested with Ubuntu 7.04 Feisty Fawn x64 bit, but this should work with 32 bit version.

**Explanation:** This is a how-to to get lightscribe properly launch from the menu with root permission. I wrote this small script because I wanted the menu option and did not want to always have the terminal open while burning the label on the disc.

**Required Items:** Lightscribe drive working (Use the links above to help you get it working if you have not gotten it working.), Root Access

**Uninstalling/Undoing** Delete the created menu link and the script

1) Save the following script as lightscribe.sh:
```
#!/bin/sh

# Opens 4L-gui under sudo to print

foo=`gksudo -u root -k -m "Enter your password for 4L-gui root access (It needs it to burn the label image.)" /bin/echo "got r00t?"`

sudo 4L-gui
```

2) I placed this file in a folder called scripts in my home folder: /home/user/scripts

3) Now **Right Click** on the **Applications Menu** and select **Edit Menus**

4) Decide where you want Lightscribe listing to show. I placed it in the **Sound and Video** folder. Click **New Item** on the right. 

5) A dialog box will appear. Just fill in the following:

Type: Application
Name: Lightscribe (Or whatever you wish)
Command: sh [script location]
Comment: Label a disc (This comment appears when your mouse is hovering over the icon.

In my case:
Command: sh /home/user/scripts/lightscribe.sh

If you want to use an icon, use the following attached image.

Most icons are kept in this folder: /usr/share/pixmaps/

Now hit **close**

If you want to keep the all your icons in a localized and central place. Follow these steps:

1) Save the attached image to your desktop or somewhere you can easily access.
2) Open a terminal (Applications -> Accessories -> Terminal)
3) cd (**C**hange **D**irectory) into the folder with the downloaded image
4) Type ```
sudo cp lightscribe.png /usr/share/pixmaps/
```
5) That just copied the image to that directory, to be sure ```
cd /usr/share/pixmaps/
``` then type ```
ls
```
6) Type ```
exit
```

Go ahead and give it a test run. If you have any problems/questions/comments, please feel free to post them.

---

### Post by AegisTalons on 2007-12-17
A simpler method I found out recently instead of using a script is just calling the command within the shortcut.

Type: Application
Name: Lightscribe (Or whatever you wish)
Command: sudo 4L-gui
Comment: Label a disc (This comment appears when your mouse is hovering over the icon.

---

### Post by j_dog on 2008-04-02
Help !!!     I am not understanding this !   I have it in the menu. it opens up. but I can not use it because I can't get the root thing right.

---

### Post by AegisTalons on 2008-04-05
I don't understand what you mean by "can't get the root thing right". You have to edit the Lightscribe application from the menu. So, right click on applications and click "Edit Menus". For your Lightscribe link, under the command option, use either "sudo 4L-gui" or "gksudo 4L-gui". Either of these options, when you click on the newly created link, it will ask for your password so 4L-gui can run as root and thus fully access the Lightscribe drive and burn your label.

---

### Post by j_dog on 2008-04-05
I see...... It was not working with sudo. It works with gksudo.  Why is that , I always use sudo in the terminal ?


Thank you for your Help !!

---

### Post by AegisTalons on 2008-04-05
So sudo is designed for terminal and gksudo is the graphical sudo for use with gnome.

---

### Post by vijaym on 2009-07-09
Hey AegisTalons

Thanks for the instructions.. 

Works well.

---

### Post by fballem on 2009-07-09
I must be missing something. Why do you need to run LightScribe as root? I have used the following instructions to successfully setup the LightScribe Simple Labeler software.

LightScribe is used to label LightScribe discs.

- obtain the software from: LightScribe website. Both the System Software and the Simple Labeler software are required. These should be saved to your desktop.

32-bit Linux
- install the software. There are two components. The core software must be installed first, then the Application.

64-bit Linux (This needs to be installed using the following commands in a Terminal). The version numbers will need to be changed to match the actual download files. The first two commands will install the LightScribe software. The remaining commands will resolve issues with referencing a required library.
```

sudo dpkg -i --force architecture lightscribe-1.18.6.1-linux-2.6-intel.deb
sudo dpkg -i --force architecture lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig

```

For both 32-bit and 64-bit installations, set the label so that it will print darker:
```
 
sudo /usr/lib/lightscribe/elcu.sh

```
Once installed, then a menu option can be created to use the software.

1. Right-click on Applications and select Edit Menu from the context menu.
2. Click on Accessories, which is where the lightscribe menu item will be placed.
3. Click the New Item button, and enter the following information into the fields:
   a. Ensure that Type is set to Application.
   b. Name may be anything. I use LightScribe Labeller.
   c. Command is: /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler (the browse button may be used to locate the application, which is in the /opt/lightscribeApplciations/SimpleLabeler folder.
   d. Comment may be anything. I use Writes a label on Lightscribe-enabled discs
   e. Click on the icon and browse to /opt/lightscribeApplications/SimpleLabeler/content/images folder. Once browsed, a list of suitable icons appears. Select one.
   f.  Click on the Close button, which will complete the application.

I am attaching a screenshot showing the final setup of the Application Launcher Panel.

To use, select the launcher from Applications > Accessories > LightScribe Labeller (or whatever was put in the Name field.

Hope this helps,

---

### Post by sblmgtrmsl on 2012-12-03
Still didn't work. I installed everything as you described, but I get the message "Failed to execute child process "sh/home/james/Scripts/lightscribe.sh" (No such file or directory)"

---

