---
title: "how to install dreamweaver cs5 in ubuntu 10.4"
date: 2010-08-30
forum: Wine
---

### Post by justniik on 2010-08-30
hi!! frnds this is justniik, today i try to install dreamweaver CS5 with wine in ubuntu 10.4 ........i'm using some steps.....
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=verdana]1) Open up File Manager and navigate to *C:\Program Files*. Copy the whole ‘*Adobe*‘ folder to Ubuntu */home/username/.wine/drive_c/Program Files* folder.
2) Still in the Windows File manager, navigate to *C:\Documents and Settings\your-windows-user-name\Application Data* (if you can’t find the *Application Data* folder, go to *Tools->Folder Option->View* and select ‘*show hidden files and folders*‘) and copy the whole ‘*Adobe*‘ folder to Ubuntu */home/username/.wine/drive_c/windows/profiles/All Users/Application Data/*
3) In the Windows File manager, go to *C:\Program Files\Common Files* and copy the whole ‘*Adobe*‘ folder to Ubuntu */home/username/.wine/drive_c/Program Files/Common Files*
4) In the Windows file manager, go to *C:\WINDOWS\system32* and copy the whole ‘*marcomed*‘ folder to Ubuntu */home/username/.wine/drive_c/windows/system32*
5) In the Windows file manager, go to *C:\WINDOWS* and copy the whole ‘*WinSxS*‘ folder to Ubuntu */home/username/.wine/drive_c/win*


[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=verdana]Next, we need to import the Dreamweaver registry to WINE.
In  your Windows, go to *Start->Run*. Type in ‘*regedit*‘ and press Enter.
In the window that pop up, on the left pane, navigate to *HKEY_LOCAL_MACHINE-> SOFTWARE->Adobe->Dreamweaver*. Right click on the ‘*Dreamweaver*‘ folder and select ‘*Export’*. Save the file as *dreamweaver.reg*
Copy this *dreamweaver.reg* to your Ubuntu home folder.
[/FONT][/COLOR][/FONT][/COLOR]
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][COLOR=#110000][FONT=verdana]#sudo apt-get install recode
#recode ucs-2..ascii dreamweaver.reg ..when i try this command showing [SIZE=3][COLOR=SeaGreen]some error.........[/COLOR][/SIZE]
[/FONT][/COLOR][/FONT][/COLOR][FONT=Arial Black][SIZE=3][COLOR=SeaGreen]**recode: dreamweaver.reg failed: Untranslatable input in step `ISO-10646-UCS-2..ANSI_X3.4-1968'**[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Times New Roman][COLOR=#110000][FONT=verdana]
please help me...............

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by robbiemacg on 2010-08-30
So far, I have only succeeded in runnign CS5 apps is via a virtual machine.
Dreamweaver CS5 doesn't have as terrible a rating as some of the other apps ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=183](http://appdb.winehq.org/objectManager.php?sClass=application&iId=183)), but it still ain't great.
I use CS5 apps for print design, because my work requires me to be able to access/work on files in proprietary formats.
Do you use Dreamweaver for similar reasons? Are you interested in running it because it's tools are familiar? Perhaps someone could suggest an alternative application for the time being.

*I'll watch this thread with interest to see if anyone has a good solution for you. If you want advice about running CS5 applications via VirtualBox OSE, I'm down to chat.

---

### Post by justniik on 2010-08-30
hay plz tell me how to install dreamweaver cs5 with VirtualBox OSE.....

---

### Post by justniik on 2010-08-30
well i'm also install virtualbox ......& success fully run with redhat & backtrack.......
but i can't able to install dreamweaver in these os.....

---

### Post by robbiemacg on 2010-08-30
All right, I'm going to assume that when you were trying to figure out how to run Dreamweaver via Wine you investigated some of the native applications suggested by the WineHQ folks&#8212;applications like Nvu, Quanta, SeaMonkey. 
I don't do much web development, maybe those applications/suites are wanting in some way.

If you really want to run Dreamweaver today, I'd say the best thing to do is set up a virtual machine (my preference is to do this using VirtualBox OSE, which is available via the Software Centre). You'll have to install a desktop virtualization application, build a virtual machine (do you have access to a Windows ISO/disc?), install the application as the guest OS.

If I were in your position, I'd visit [http://www.virtualbox.org](http://www.virtualbox.org), look around the forums, watch some YouTube tutorials, and otherwise get comfortable with the idea of using the virtualization tools. There are lots of good ways to learn about these applications, so I'm not going to go into great detail.

Assuming you follow the correct steps in building your virtual machine, provide the guest OS with the appropriate access to optical drives and share the right folders, you should be able to install just about anything.

To get InDesign CS5 up and running, I built a virtual machine using VirtualBox OSE. I set up a machine that was running Windows 7 Home Premium, had 1gb RAM, a 20 gb hard drive, and had access to my optical drive and Desktop. The guest OS had the minimum resources to run the application, and I could install from DVD or ISO. 
Figure out what kind of resources Dreamweaver requires (and think about what resources you can reasonably spare when a virtual PC is running), then build accordingly. The videos on the VirtualBox site will probably be enough to get you there.

*I'm also assuming that you have some working product codes and serials.

---

### Post by justniik on 2010-08-31
hay i got it.......but first thing i want to install dreamwaver CS5 in ubuntu..........& i'm already use dreamweaver CS5 in my pc's with window 7 ultimate................hay does't matter where can i run dreamwaver.............A manly things how can i run Dreamwaver CS5 in ubuntu with help of wine......
hay lot of thanxxx for your reply......!

---

