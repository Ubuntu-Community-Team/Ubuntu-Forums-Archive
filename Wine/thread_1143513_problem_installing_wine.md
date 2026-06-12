---
title: "problem installing wine"
date: 2009-04-30
forum: Wine
---

### Post by tigerwarsaw on 2009-04-30
i reinstalled wine (the first time i installed it i realized i didnt really need it at the time so i removed it) but none of the stuff thats supposed to be under applications in the menu bar is there. the program does work but i pretty much can't uninstall windows programs or anything like that. i don't know if its a newer version and it's supposed to be that way or it's really a problem or something. any help would be very much appreciated.

---

### Post by asdfoo on 2009-04-30
> **tigerwarsaw said:**
> i reinstalled wine (the first time i installed it i realized i didnt really need it at the time so i removed it) but none of the stuff thats supposed to be under applications in the menu bar is there. the program does work but i pretty much can't uninstall windows programs or anything like that. i don't know if its a newer version and it's supposed to be that way or it's really a problem or something. any help would be very much appreciated.

which stuff under Applications are you talking about?

uninstalling is not really supported or a priority at the moment, if you want to remove any apps and their data from Wine, you move or remove the .wine directory in your home directory.

mv ~/.wine ~/.wine-old

To check the wine version:

wine --version

---

### Post by cogadh on 2009-04-30
> **tigerwarsaw said:**
> i reinstalled wine (the first time i installed it i realized i didnt really need it at the time so i removed it) but none of the stuff thats supposed to be under applications in the menu bar is there. the program does work but i pretty much can't uninstall windows programs or anything like that. i don't know if its a newer version and it's supposed to be that way or it's really a problem or something. any help would be very much appreciated.
I'm assuming that you mean that Wine's Applications menu shortcuts are missing. If so, that is probably because you manually deleted the shortcuts after you uninstalled Wine the last time. If so, you can get them back by editing one of the hidden configuration files in your home directory (press CTRL+H to show hidden directories/files). Look for a Wine entry in /home/<user name>/.config/menus/applications.menu. It should look something like this:
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/<username>/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```
Remove the "<Deleted/>" from the end of it, save the file and the menu entry should come back.

> **asdfoo said:**
> uninstalling is not really supported or a priority at the moment, if you want to remove any apps and their data from Wine, you move or remove the .wine directory in your home directory.

mv ~/.wine ~/.wine-old

To check the wine version:

wine --version
That's not really true. Uninstallation of applications is definitely supported, it is only certain install configurations that have uninstall issues (usually MSI based installs). In those situations you can usally get around them by performing an old-school manual uninstall (manually deleting installed files and registry entries) without killing your whole .wine directory, though it is considerably easier to do that.

---

### Post by tigerwarsaw on 2009-04-30
thanks cogadh, i did what you said and the shortcuts came back. the only problem is that the uninstall option still doesn't show up. if you could you help me out with that, it would be cool but i guess i could live without that so its whatev

---

### Post by cogadh on 2009-05-01
Are you referring to the Wine uninstaller application that is similar to the Windows Add/Remove Programs applet? If so, you can access it by just opening a terminal and typing "uninstaller".

---

