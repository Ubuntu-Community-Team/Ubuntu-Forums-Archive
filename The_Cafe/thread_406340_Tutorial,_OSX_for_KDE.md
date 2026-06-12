---
title: "Tutorial, OSX for KDE"
date: 2007-04-10
forum: The Cafe
---

### Post by Peter1234123 on 2007-04-10
NOTE: THIS TUTORIAL COMES WITH NO WARRANTY OR EVEN THE IMPLIED IDEA OF WARRANTY, I AM NOT RESPONSIBLE FOR WHAT YOU DO WITH THIS, NOR AM I RESPONSIBLE FOR ANY LEGAL ACTION TAKEN BY APPLE.

First, get SVN, either from their website (search SVN in google) or with the APT-GET command. Once you have SVN type: 
```

cvs -d:pserver:anonymous@baghira.cvs.sf.net:/cvsroot/baghira login
cvs -d:pserver:anonymous@baghira.cvs.sf.net:/cvsroot/baghira co baghira
```

With this, you obtain a baghira directory. 
Then, type ```
svn co svn://anonsvn.kde.org/home/kde/branches/kde/(your version)/kde-common/admin

```

INSTALL ALL DEPENDENCIES, you are now ready to compile baghira.

move to Baghira's file directory (CD (DIRECTORY)
then type: make -f Makefile.cvs
                ./configure --enable-final
                ./make
YOU MUST ENABLE ROOT ACCOUNT FOR THIS PORTION (if you can work around it, post here) ```
sudo passwd
``` root enter root password, type ```
su
```, to Switch User to root, type ```
make install
``` in the terminal. 

Final step, you're gonna apply the Baghira theme you've installed so easily. Open the KDE Control Center (kcontrol) > LookNFeel and select the Baghira theme in the two following sections :

    * Windows decoration
    * KDE Style
In the KDE Control Center, go to section LookNFeel > Behavior. Check  ... (Mac OS-style)  in the Menu Bar section.
In baghira's configuration dialog (right click the bab icon in the systray), go to section  Special Widgets  : check   Replace menubar extension . This allows to have the name of the application displayed next to it's menu in the top bar.
Then, right click the menubar and  Add -> Applet -> Baghira starter . Put it on the left and right click on it to change the icons (you'll find Mac icons in baghira sources, sub-directory  starter/Themes . Make your choice!). Also set the panel size to avoid having a half panel displayed instead of the full sized one : put your custom values in "popup options" (400x600 seems a good choice).
Launch the  bab  tool from a console to easily configure baghira. As long as you don't explicitly close the program, it will start again at each KDE start (don't close the console the first time you launch bab, you'll close it next restart)
An icon in leg of panther appears in the systray. If you click with the left button, you can change the style of baghira, if you click with the right button you reach the configuration dialog of baghira.
In the KDE Control Center, go to section LookNFeel > Window decorations. In the Buttons tab, check  Use custom titlebar button positions  and configure as wanted.\
Enter the name of the icon you want for K Menu (avaible icons are visible in the 128x128/apps/ folder). Building of the set can take a long time (several minutes on my centrino 1,6 Ghz). When finished, you get a full set in a tar.bz container (OS-L.tar.bz2, in the OS-L-IconSet-Buildkit/ folder).

You can in theory select this set from kcontrol if you let it in this folder, but it failed on a Mandriva Linux 2005 (several icons are not taken in account and, worst, the folder icon is an awfull enlargement of a 22x22 size !). Therefore, the best is to move the set in the kde tree, which make it also avaible for all users. Take the tar.bz and copy it to /usr/share/icons/. Unzip it to get the full set in the /usr/share/icons/OS-L/ folder. Erase the directory ~/.kde/share/icons/ cause it can confuse you when choosing the set from kcontrol (you would get two entries for the OS-L Theme).

Now open kcontrol and go to section LookNFeel > Icons : the OS-L Theme appears in the list. Select it. Hey, hey, pretty nice, isn't it ?

The set isn't all perfect. You'll have to make changes by hand to make it fit exactly your system. Here is what I had to do to make my Mandriva find all its icons. You have to do it for each icon size (xx beeing the size):

    * System icon: create an icon xx/devices/system.png from any icon that fits you (I myself took the Computer_PowerBook for my laptop for example)
    * Network icon: rename xx/devices/Network.png to network.png
    * Locked folder icon: copy xx/filesystems/Personal 2.png to folder_locked.png
      Then customize your folders with the icons you prefer (I put 48x48 icons for the file manager).
you must get the mac fonts, and you are done.

---

### Post by mips on 2007-04-11
Will this work on Kubuntu Feisty ?

---

### Post by Peter1234123 on 2007-04-11
It should, it's designed to work with any Linux flavor with KDE Installed.

---

### Post by Sunnz on 2007-04-11
Do you have a screeny?

---

### Post by mips on 2007-04-11
First people should do:

```
sudo apt-get install subversion cvs
```

I get the following error:

```
mips@obelix:~/tmp$ svn co svn://anonsvn.kde.org/home/branches/kde/3.5/kde-common/admin/
[COLOR="Red"]**svn: URL 'svn://anonsvn.kde.org/home/branches/kde/3.5/kde-common/admin' doesn't exist**
```[/COLOR]

and if I do:

```
mips@obelix:~/tmp$ svn co svn://anonsvn.kde.org/branches/KDE/3.5/kde-common/admin
[COLOR="Red"]**svn: No repository found in 'svn://anonsvn.kde.org/branches/KDE/3.5/kde-common/admin'**[/COLOR]
```

---

### Post by Ptero-4 on 2007-04-18
May I ask. What is this OSX for KDE thing?

---

### Post by mips on 2007-04-18
> **Ptero-4 said:**
> May I ask. What is this OSX for KDE thing?

It is the Baghira theme for KDE which makes KDE look & feel like the OSX looks/interface.

[http://baghira.sourceforge.net/](http://baghira.sourceforge.net/)
[http://www.kde-look.org/content/show.php?content=8692](http://www.kde-look.org/content/show.php?content=8692)
[http://en.wikipedia.org/wiki/Baghira](http://en.wikipedia.org/wiki/Baghira)

---

### Post by tbroderick on 2007-04-18
It might be easier for people to just;
```
sudo apt-get install kwin-baghira
```

---

