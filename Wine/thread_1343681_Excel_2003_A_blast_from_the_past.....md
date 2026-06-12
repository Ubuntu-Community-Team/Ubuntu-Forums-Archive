---
title: "Excel 2003 A blast from the past...."
date: 2009-12-02
forum: Wine
---

### Post by FreyGrimrod on 2009-12-02
Ok folks I am at a loss and clearly beyond my level of understanding and any help would be greatly appreciated.

I am running 8.04 Hardy Heron amd 64
at the start of this endeavor I had wine 1.0 installed
My current wine 1.1.32 I believe is configured as windows xp (had set this how can I check it now? forgotten the location) Overrides: gdiplus (native), msxml3(native, builtin), qdiplus (native,builtin), riched20(native,builtin), riched 32(native,builtin) sound all default graphics all default; one registry edit did occur

HKLocalMachine\Software\Microsoft\Office\11.0\Common\FilesPaths

was changed from C:\PROG~FBU\COMM~CP1\MICR~NEI\OFFICE11\MSO.DLL

to C:\Program Files\Common Files\Microsoft Shared\OFFICE11\MSO.DLL

However has altered back to default under the new version.




So the story of a humble newb following google howto's

I followed [http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/]("http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/") to get winetricks installed including grabbing cabextract and winetricks as noted in comments.

then followed [http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html]("http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html") to get all the MS Core fonts installed and some pretty icons in my applications gui launcher all but actually associating file types to the programs.

So Word and Power point were and still are running fine but excel was locking up on the load screen and it would be necessary to kill-9 the process no interaction with excel.

So I poked around [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2736&iTestingId=46351]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2736&iTestingId=46351") and eventually decided to give Jake's comment a go 
uninstalled wine version 1.0 via synaptic
rebooted
wget new sources "sudo wget  wine.budgetdedicated.com/apt/sources.list.d/hardy.list  -O /etc/apt/sources.list.d/winehq.list"
Then reinstalled wine 1.1.32 via synaptic

And Excel worked gorgeously I danced happily made a few graphs and got greedy overconfident and over tired..... decided to have a go at attempting to install some of the excel additional packages and broke my install back to where it loads the splash screen and locks up needs to be killed. 

In an attempt to repair this I've tried reverting wine to 1.0 repairing? I guess attempted to uninstall but errors so repaired office to no longer have excel then reinstalled excel and followed the same little blind uninstall reboot (hell I even updated my sources again just for good measure of trying to replicate what had worked before) then reinstalled wine 1.1.32 via synaptic continues to halt on the splash screen...



If you made it this far through my story thank you for taking the time. Suggestions Thoughts? Comments reminding me how greedy I was with little knowledge?


In writing and editing this I've realized when I reverted to 1.0 I forgot to regedit before changing to the new version so it wasn't a proper replication. Would regediting the reversion then installation and upgrade be the proper next step? Or is it going to proove necessary to get a full clean uninstall of office somehow also?

---

### Post by bazzer on 2010-12-07
Just wondering if you solved your issue, if not, I'll point you at something that solved the Excel splash screen lockup problem for me:

[this]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8952406&postcount=18") and [this]("http://ubuntuforums.org/showthread.php?t=1633985")

---

