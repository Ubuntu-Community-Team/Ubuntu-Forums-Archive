---
title: "Microsoft Office 2007 not working properly"
date: 2011-01-23
forum: Wine
---

### Post by slashwannabe94 on 2011-01-23
Good morning all,

I have recently downloaded a copy of Microsoft Office 2007 Enterprise with keys. My machine dual boots with Windows 7 Ultimate and Ubuntu 10.4. If i install office in windows all applications will work flawlessly. But when i try to emulate Office 2007 with Wine, all programs work besides OneNote, Powerpoint, Infopath, Groove and Access. 

When i open any of the above they either appear on the task bar but then disappear or come up with an error saying -  e.g. "Powerpoint failed to launch in safe mode. Do you want to start detect and repair" i click yes and nothing happens. I have checked the processes via the 'top' command and there is no sign of Office running.

I was wondering is there something that could be going on in the background? The program works fine in windows 7 but is very buggy in Wine. 

Any help will be greatly appreciated :) 

Thanks, 

SlashWannabe94

---

### Post by ronnielsen1 on 2011-01-23
> In order to run Powerpoint 2007, you must set riched20.dll to (native) in winecfg. Note that you do **not **have  to copy the dll from a Windows partition or use winetricks to install  it. Office 2007 installs its own version of richedit in a private  directory, but Wine will not use it unless you set the override.  Do not  set the override globally unless you have Office installed in a  separate wineprefix.          To get the thesaurus to work, install Windows Scripting Host with winetricks wsh56js.*                                                        

There's some tweaks to get access working too. Follow the links and directions at winehq

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

Be sure to scroll down and read it all and click on the individual entries

---

### Post by slashwannabe94 on 2011-01-23
Thanks man, so how do i go about doing this task. It seems very complex.

---

### Post by slashwannabe94 on 2011-01-23
Hey man, i have managed to get all applications running besides groove and access. I followed the commands listed at the bottom of the page you sent me. added the riched20(native) windows to the libraries. 

All apps work besides groove and access now. 

Any ideas buddy?

---

### Post by slashwannabe94 on 2011-01-23
Oh its alright dude :D 

I done it, 

Just downloaded the MSVCP80.dll file and placed it in ~/.wine/drive_c/windows/system32/
i then added the MSVCP80.dll file to the libraries and changed it to (native) windows.

---

### Post by ronnielsen1 on 2011-01-23
> Thanks man, so how do i go about doing this task. It seems very complex.

Take it one step at a time.

First I would add the wine repository so you always have the newest wine

> Open the Software Sources menu by going to **Applications->Ubuntu Software  Center**, then selecting **Edit->Software Sources**. Choose the **Other  Software** tab and click **Add**.
> Then, **copy and paste the line below**.
  *ppa:ubuntu-wine/ppa*

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Then, go to the site of Office 2007 winehq, and on that site (If you scroll down) it will say the following:

> [SIZE=4]_**Post Installation Instructions***_[/SIZE]
   Once installed, one override is necessary. Without it, Powerpoint  and Infopath with not start, and some dialog boxes in other Office apps  will not display correctly. Follow the steps below:                                                             

   Open ***winecfg*** by going to ***Applications > Wine > Configure Wine***. Or open a terminal and type:                                                                  

   winecfg                                                                      

   In the ***Libraries*** tab in the area labeled "*New override for library*" type in **riched20.dll** and click on ***Add***.
   You will see it appear in the list below. Now select the **riched20** in the list that we just added and click on the **Edit** button.
    Set it to **Native (Windows)** and click OK.
   This will allow Powerpoint and the other applications to run correctly.
   **Note :**Do not install riched20 with winetricks. Office 2007 installs its own  version of riched20. 
   If Office is installed in a separate wineprefix, you can safely set  the override globally. If not, set the overrides separately for each  Office application.                                                                                               

Try to follow these directions. If you get lost, I'll try to post some screenshots.

Some other tweaks you might have to do for certain office 2007 programs:


Excel:
> To use the thesaurus, install winetricks wsh56js.                 

Open up a terminal and copy and paste (one at a time)

 wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks) 


sh winetricks wsh56js


Access:

> Currently, Access will install but not start up (bugs 18889 & 1*9297). There are two known workarounds (tested in 1.1.33): 
   **Workaround 1:**(preferred method, as it does not remove any dependencies)     

   
[LIST=1]
[*]Use a resource editor to extract the manifest from ACEDAO.DLL  (you will find it in the same directory as msaccess.exe). (I used  Resource Tuner; it has a free trial and runs well under Wine.)
[*]Save the extracted manifest as acedao.manifest in the same directory as msaccess.exe.
[*]Delete or rename the ACEDAO.DLL located in that directory.  (There is another copy in another directory--no need to change it.)
[/LIST]


This one might require some thought but it does work. You will have to download a free trial of Resource Tuner:

[http://restuner.com/download.htm](http://restuner.com/download.htm)

If you do the tweaks above, it should install fine. Let me know if you have any trouble

---

### Post by vigneshncc on 2011-05-10
Thanks guys... Its working fine now... But one problem.. Now i am using ubuntu 11.04 and if i open an ppt file it directly goes to slide show... cannot edit the ppt file... Any solution Pls... I am new to ubuntu.. so pls give solution in detail...

---

### Post by slashwannabe94 on 2011-05-10
> **vigneshncc said:**
> Thanks guys... Its working fine now... But one problem.. Now i am using ubuntu 11.04 and if i open an ppt file it directly goes to slide show... cannot edit the ppt file... Any solution Pls... I am new to ubuntu.. so pls give solution in detail...

what Microsoft office are you using? That happens when you use a Trial version of office. 
Can you open and edit files in other Office programs, such as Word, Excel and publisher?

---

