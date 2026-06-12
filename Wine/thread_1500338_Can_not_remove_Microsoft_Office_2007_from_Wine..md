---
title: "Can not remove Microsoft Office 2007 from Wine."
date: 2010-06-03
forum: Wine
---

### Post by rudysuryanto on 2010-06-03
I have installed Microsoft Office 2007 in Wine. Word and Excell can run, but Power Point can not run in Wine, then I want to remove Power Point from Wine. I try to uninstall power point, but when I click remove button, power point can not been removed from Wine, also all Microsoft Office 2007 programs can not been removed from Wine. What should I do to remove Microsoft Office 2007 from Wine? Thank's.

---

### Post by cogadh on 2010-06-03
If it is the only thing you have installed in Wine, just delete the .wine directory from your home directory. Its a hidden directory, so you will have to hit CTRL+H in the file browser to show hidden files.

---

### Post by pr0t3g3 on 2010-06-03
> **cogadh said:**
> If it is the only thing you have installed in Wine, just delete the .wine directory from your home directory. Its a hidden directory, so you will have to hit CTRL+H in the file browser to show hidden files.What happens if there are more than one file installed with wine?  Isn't there a way to remove only the Microsoft Office 7 and all it's extensions, rather than just obliterating the whole directory?

---

### Post by cogadh on 2010-06-03
How are you uninstalling it; using the uninstall option installed with the software or the Wine uninstaller utility?

---

### Post by mixint27 on 2010-06-06
im having the same issue. i cant remove office 2007. I have 1.1.42. Im trying to remove office within wine.

please help

---

### Post by ronnielsen1 on 2010-06-06
> , but Power Point can not run in Wine
Runs fine on my box

> In order to run Powerpoint 2007, you must set riched20.dll to (native) in winecfg. Note that you do **not **have to copy the dll from a Windows partition or use winetricks to install it. Office 2007 installs its own version of richedit in a private directory, but Wine will not use it unless you set the override.  Do not set the override globally unless you have Office installed in a separate wineprefix.    To get the thesaurus to work, install Windows Scripting Host with winetricks wsh56js.*                                                        
*                                                          
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)

---

### Post by shmiah on 2010-06-11
I am having the same problem, I cannot get rid or delete MS Office 2007 from Ubuntu 10.04. Even if I try to get rid off wine, it still stays there lurking in the Applications menu bar.

Can anyone help?

---

### Post by cogadh on 2010-06-11
That's just a leftover shortcut, you can get rid of it with the menu editor (System > Preferences > Main Menu)

---

### Post by shmiah on 2010-06-12
thanks, much appreciated.....

---

### Post by IcaroAzul on 2010-09-17
Hello, 

I had the exact couple of problems as the first user:

[1] I could not run Power Point 2007 on WineHQ
[2] I could not uninstall MS Office programs on wine.

I still need to solve [1].

To solve [2] I followed all the instructions in item 5.1 in this link and they did remove all windows applications under wine, before you see the link, I must add that I had to type in a terminall all five rm commands:

http://wiki.winehq.org/FAQ#uninstall_app[/URL]

In case the link does not work, here is what it said:

Wine has its own built-in uninstaller - the equivalent of Windows' "Add/Remove Programs" function for running standardized uninstallers.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the wineprefix (usually the ~/.wine directory):
Please note that in the following commands there should be no spaces in the path, particularly between $HOME/ and .whatever.

rm -rf $HOME/.wine

The uninstaller should remove menu and desktop entries. If the application was installed with an old version of Wine, it may not remove them. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

---

### Post by GeoffreyBernardo on 2011-12-04
Thank you for the information, guys.

The steps provided work well, except that Adobe Reader still appears on the```
 Open With...
``` menu in Nautilus.

How does one remove it from there?

---

### Post by GeoffreyBernardo on 2011-12-04
> **GeoffreyBernardo said:**
> Thank you for the information, guys.

The steps provided work well, except that Adobe Reader still appears on the```
 Open With...
``` menu in Nautilus.

How does one remove it from there?

OK, I have solved it:

[LIST=1]
[*]Right-click the pdf file.
[*]On the right-click menu, click Properties.
[*]On the Properties dialog, click the Open With tab.
[*]In the list of applications, click Adobe Reader.
[*]Click the Remove button.
[*]Click the Close button.
[/LIST]
Problem solved.

---

