---
title: "help"
date: 2008-08-08
forum: Windows
---

### Post by johnling on 2008-08-08
hi can any one help me before I kick this thing .since my 17 year old has been on my computer I have lost my flash player I have tried to reinstall it but firefox wont let me it says disable firefox "WELL" if the dam thing told me how I would . I am on vista home . if I open firefox it just gives me a thing like a google serch engine :confused:

---

### Post by Skorzen on 2008-08-08
Let me see if I understood: you're currently using Vista and looking for support here?

So, if you're on Ubuntu, just try the following:
```
sudo apt-get remove flashplugin-nonfree
```

and then:
```
sudo apt-get install flashplugin-nonfree
```

It would reinstall flash plugin.

If your problem is with firefox, try the above explanation but replacing 'flashplugin-nonfree' with 'firefox-3.0'.

By the way, try a better writing, so you'll get a better support.

---

### Post by tjwoosta on 2008-08-08
???
you say you are using vista home so why are you posting this on the ubuntu forums?

> I have tried to reinstall it but firefox wont let me it says disable firefox "WELL" if the dam thing told me how I would . I am on vista home

ive never heard of such a thing  (could you post a screenshot of what is happening?)

> if I open firefox it just gives me a thing like a google serch engine

again, is there any way you can post a screenshot of this?

---

### Post by tamoneya on 2008-08-08
download this file here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Win32&P3_Browser=Netscape](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Win32&P3_Browser=Netscape)
Its best if you save it to your desktop so it is easy to access.

Then close firefox by hitting the "x" in the upper right and then run the file.  After following the prompts from the file and finishing the install just open up firefox and you should be set.

Just FYI.  This is a linux forum primarily and while we are glad to help you with your windows computers it is best if you keep it in the windows discussions sub forum.  Thanks: [http://ubuntuforums.org/forumdisplay.php?f=170](http://ubuntuforums.org/forumdisplay.php?f=170)

EDIT(addition): Skorzen gave commands to fix it as if you were running ubuntu/linux.  That is why you should try to keep it in the windows sub forum.

---

### Post by Oldsoldier2003 on 2008-08-08
moved from ABT to Windows Discussions.

---

### Post by johnling on 2008-08-08
> **Oldsoldier2003 said:**
> moved from ABT to Windows Discussions.

sorry I thought this was a forum to help beginers with there computers 
           regards
                     John

---

### Post by tamoneya on 2008-08-08
> **johnling said:**
> sorry I thought this was a forum to help beginers with there computers 
           regards
                     John

You were close and now you are in the correct forum because oldsoldier moved you.  Did you try the link i gave you?

---

### Post by johnling on 2008-08-08
> **johnling said:**
> sorry I thought this was a forum to help beginers with there computers 
           regards
                     John

thanks for your help

---

### Post by johnling on 2008-08-10
tried that before tried again and still will not load .it says that I need to "disable firefox" before it can be loaded I am very new to all this finding it dam hard not to lose my temper with it what I cant understand it was working fine then my lad went on it NOW it keeps saying I need to down load fashplayer all so says I need plug ins what ever they are think I might have to go back to pen and paper 
            thanks for your help and sorry for being on the wrong part of your site 
           regards 
                    John

---

### Post by fiddledd on 2008-08-10
It sounds like Flash is messed up. Often you can't just reinstall it, you need to download the uninstaller and then reinstall. The following from Adobe might help:

TechNote Update
Last Update: 05-28-2008
How to uninstall the Adobe Flash Player plug-in and ActiveX control

Due to recent enhancements to the Adobe Flash Player installers, you can now remove the player only by using the Adobe Flash Player uninstaller. To remove Flash Player, simply download and run the appropriate uninstaller for your system using the steps below.

1. Download the Adobe Flash Player uninstaller:
[uninstall_flash_player.exe](http://download.macromedia.com/pub/flashplayer/current/uninstall_flash_player.exe)
Note: If you have a Windows Flash Player uninstaller downloaded prior to April 4, 2008 on your desktop, then please delete it and download the latest version.
2. Save the file to your system, choosing a location where you can find it (for example, your desktop). Macintosh users may need to open or unstuff the .hqx file.
3. Quit ALL running applications, including all Internet Explorer or other browser windows, AOL Instant Messenger, Yahoo Messenger, MSN Messenger, or other Messengers. Check the Windows system tray carefully to make certain no applications are still in memory which might possibly use Flash Player.
4. Run the uninstaller. This will remove Adobe Flash Player from all browsers on the system.

Note: The uninstaller cannot remove files currently in use.

If you have any instances of the player open in your web browsers, instant messaging clients, stand-alone SWFs, or projectors, then the uninstaller will complete but some files may not be deleted. If this occurs, then close all of your applications and run the uninstaller again to ensure that all files are removed.

Note: Internet Explorer users may have to reboot to clear all uninstalled Flash Player ActiveX control files. If you're not certain, select the "Show Details" button in the Flash Player uninstaller. If there are any log lines that begin with "Delete on Reboot..." then you'll need to reboot BEFORE running the Flash Player installer again.
Platform.

---

### Post by johnling on 2008-08-13
> **fiddledd said:**
> It sounds like Flash is messed up. Often you can't just reinstall it, you need to download the uninstaller and then reinstall. The following from Adobe might help:

TechNote Update
Last Update: 05-28-2008
How to uninstall the Adobe Flash Player plug-in and ActiveX control

Due to recent enhancements to the Adobe Flash Player installers, you can now remove the player only by using the Adobe Flash Player uninstaller. To remove Flash Player, simply download and run the appropriate uninstaller for your system using the steps below.

1. Download the Adobe Flash Player uninstaller:
[uninstall_flash_player.exe](http://download.macromedia.com/pub/flashplayer/current/uninstall_flash_player.exe)
Note: If you have a Windows Flash Player uninstaller downloaded prior to April 4, 2008 on your desktop, then please delete it and download the latest version.
2. Save the file to your system, choosing a location where you can find it (for example, your desktop). Macintosh users may need to open or unstuff the .hqx file.
3. Quit ALL running applications, including all Internet Explorer or other browser windows, AOL Instant Messenger, Yahoo Messenger, MSN Messenger, or other Messengers. Check the Windows system tray carefully to make certain no applications are still in memory which might possibly use Flash Player.
4. Run the uninstaller. This will remove Adobe Flash Player from all browsers on the system.

Note: The uninstaller cannot remove files currently in use.

If you have any instances of the player open in your web browsers, instant messaging clients, stand-alone SWFs, or projectors, then the uninstaller will complete but some files may not be deleted. If this occurs, then close all of your applications and run the uninstaller again to ensure that all files are removed.

Note: Internet Explorer users may have to reboot to clear all uninstalled Flash Player ActiveX control files. If you're not certain, select the "Show Details" button in the Flash Player uninstaller. If there are any log lines that begin with "Delete on Reboot..." then you'll need to reboot BEFORE running the Flash Player installer again.
Platform.



hi thanks all. got it at last had to take firefox out completely, 
It would not let even down load the uninstaller once it was gone every thing went as you all said .then I just reinstalled firefox so all now fine 
    THANKS AGAIN 
                JOHN  :lolflag:

---

