---
title: "Flawless install of Office 2007 on ubuntu 8.10"
date: 2009-05-07
forum: Wine
---

### Post by atulkakrana on 2009-05-07
**Ubuntu** has evolved as most successful Linux distro in last few years. Its high popularity is evident from its forum.

[CENTER][FONT="Century Gothic"]**[SIZE="4"]Steps for Installing MS office 2007 on Ubuntu OS[/SIZE]**[/FONT][/CENTER]


*Requirements Ubuntu 8.04 or 8.10 (may work on 9.10 too) 
*At least 1GB RAM, for better working
*Little patience and copy-paste ability. ( Believe me this is imperative)

Here we Go;)

**Step 1. Install msttcorefonts** via synaptic/adept from System>Administration>Synaptic

Search for msttcorefonts and select for installation. Press Apply

OR

> $sudo apt-get install

**Step 2. Install wine 1.1.16** ( versions new to this i.e 1.1.17-20 does not support MS office 2007 installation )

we will download wine version 1.1.16 (links from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) and then update to latest wine.

   Intrepid: [http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)
   Hardy: [http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb)
   
   

   Once you downloaded the file (anywhere will do), just double click it, and let it install.

[NOTE: If you already have wine 1.1.17/1.1.18/1.1.19/1.1.20 installed, you will have to uninstall it first (use synaptic/adept).Also Manually delete .wine folder from HOME ]
In case you screw your wine or want to reset to original wine installation>  $rm -rf ~/.wine 

Now you should have wine 1.1.16 installed. If you want to verify this, open up a terminal and type in > $wine &#8211;version

which should report:** wine-1.1.16**

**Step 3 Install winetricks**

> $sudo apt-get install cabextract ( for smoother working of winetricks)

> $wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

> $chmod +x ./winetricks

Use wine tricks to install windows components 

> $sh ./winetricks msxml3 vcrun2003 vcrun2005sp1 vcrun2008 gdiplus riched20 riched30 msxml3 msxml4 msxml6 tahoma vb3run vb4run vb5run vb6run vcrun6 msi2 allfonts dotnet11 corefonts wsh56js



OR


> $sh ./winetricks and select above stated components.

**Step 4  Install MS office 2007**

I used Gmount to load ISO and opened Setup.exe with wine.You can either use Office 2007 cd or mount ISO with any available tool.Open Setup.exe (I dnt remember name correctly) by right click and select wine. You have to be little patient as it may get stuck for some time while installing, wait and it will get installed.

I customized and installed only three components Word, Powerpoint and Excel ( Dont untick shared components or whatever)
But you can try full install also


[B]Step 5 Upgrade Wine to latest Wine
[/B]
Open the Software Sources menu by going to System->Administration->Software Sources. Then select the Third Party Software tab and click Add Then, copy and paste one of the lines below depending on which version you are running.

For Ubuntu Jaunty (9.04): deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

For Ubuntu Intrepid (8.10): deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

For Ubuntu Hardy (8.04): deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

Download or save Scott Ritchie's key[http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg]("http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg") to your desktop (Right click and select "save as"). Then open the Authentication tab (Under software sources only) , click import key file, and select the key file you just saved (Scott Ritchie.gpg). It is safe to delete this file after doing this step. Click close to finish, and then reload the package information when prompted. If you have Wine installed, the system's update manager will now inform you of the latest Wine beta release and prompt you to upgrade. If you haven't installed Wine yet, go to Applications->Add/Remove and search for Wine or just click this link.

Go to System>Administration>synaptic and search wine

Select wine by right click and click on upgrade

**Step 6 Run office 2007** :popcorn:

&#8226;If symbols like bullets look weird; Copy symbol.ttf from Office 2007 installation from windows to **~/.wine/drive_c/windows/fonts**

---

### Post by zbeckerd on 2009-05-21
dotnet11 failed to install.  Am trying to find a fix... otherwise this seems to work better than some other things I have tried.

---

### Post by atulkakrana on 2009-05-25
> **zbeckerd said:**
> dotnet11 failed to install.  Am trying to find a fix... otherwise this seems to work better than some other things I have tried.


I think Dotnet 11 should install and problem is with Dotnet 20 and above, As they neeed new version of MSI (Microsoft installer)

Try Reinstalling wine or reset wine settings as Stated in my post. and then start Again. Try to follow as it is.

Note- To revert to original wine installation $rm -rf ~/.wine (In case you have wine and want to revert to original state)

---

### Post by Duskao on 2009-05-25
Heh, But why??? LOL. JK. nice work.

---

### Post by rvgsd on 2009-05-31
Hi,
I am trying to install MSO through wine using this tutorial. Every step works fine until I start Office 2007 setup. It continues for a little while and stops with an error (Screenshot attached). Here is what I see in the terminal:

```
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:powrprof:DllMain (0x7dfd0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33f0dc 0x33f0d0
fixme:advapi:CheckTokenMembership ((nil) 0x12c8c0 0x33f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12c8c0 0x33f0b8) stub!
fixme:powrprof:DllMain (0x7dfd0000, 0, (nil)) not fully implemented
```

Also, when I type **wine -version** in the terminal, I get this message:
```
could not load L"C:\\windows\\system32\\-version.exe"
```Any suggestions? 
Thanks for helping. 

Regards, rvgsd.

---

### Post by jhoeijao on 2009-05-31
> **rvgsd said:**
> Hi,
I am trying to install MSO through wine using this tutorial. Every step works fine until I start Office 2007 setup. It continues for a little while and stops with an error (Screenshot attached). Here is what I see in the terminal:

```
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:powrprof:DllMain (0x7dfd0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33f0dc 0x33f0d0
fixme:advapi:CheckTokenMembership ((nil) 0x12c8c0 0x33f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12c8c0 0x33f0b8) stub!
fixme:powrprof:DllMain (0x7dfd0000, 0, (nil)) not fully implemented
```Also, when I type **wine -version** in the terminal, I get this message:
```
could not load L"C:\\windows\\system32\\-version.exe"
```Any suggestions? 
Thanks for helping. 

Regards, rvgsd.

I suggest install your Wine again.

Give this a try [http://ubuntuforums.org/showthread.php?p=7375966#post7375966](http://ubuntuforums.org/showthread.php?p=7375966#post7375966).

---

### Post by tuskenraider on 2009-05-31
crossover linux from codeweavers.  
i have office 07 enterprise installed on my ubuntu 9.04 machine...    installed perfectly...  

whats this wine you speak of?? LMAO kidding kidding.. but seriously...

codeweavers look into it. goooooooooooooooooooooooood stuff man


tusken

---

### Post by jhoeijao on 2009-05-31
> **tuskenraider said:**
> crossover linux from codeweavers.  
i have office 07 enterprise installed on my ubuntu 9.04 machine...    installed perfectly...  

whats this wine you speak of?? LMAO kidding kidding.. but seriously...

codeweavers look into it. goooooooooooooooooooooooood stuff man


tusken

Yeah you're right Crossover Linux works well also the only problem is CXOffice is not an opensource software.

---

### Post by Newtothegame on 2009-05-31
Thanks for the Post. 
However I am getting an error. 

Note: command 'wine /home/mac/.winetrickscache/dotnet11/dotnetfx.exe' returned status 65.  Aborting

I have uninstalled and reinstalled wine 3 times now and it fails here everytime. 

Also, has anyone got there office to work in completion? On first install I had word working but wouldnt update, and powerpoint would not work. 

thanks, 

Newtothegame

---

### Post by NightMKoder on 2009-05-31
> **Newtothegame said:**
> Thanks for the Post. 
However I am getting an error. 

Note: command 'wine /home/mac/.winetrickscache/dotnet11/dotnetfx.exe' returned status 65.  Aborting

I have uninstalled and reinstalled wine 3 times now and it fails here everytime. 

Also, has anyone got there office to work in completion? On first install I had word working but wouldnt update, and powerpoint would not work. 

thanks, 

Newtothegame

Geez you don't need any of this stuff. Just install wine 1.1.16 and install office. Then you need to add two overrides. Service packs don't install yet so don't try. [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

---

### Post by atulkakrana on 2009-06-03
> **Newtothegame said:**
> Thanks for the Post. 
However I am getting an error. 

Note: command 'wine /home/mac/.winetrickscache/dotnet11/dotnetfx.exe' returned status 65.  Aborting

I have uninstalled and reinstalled wine 3 times now and it fails here everytime. 

Also, has anyone got there office to work in completion? On first install I had word working but wouldnt update, and powerpoint would not work. 

thanks, 

Newtothegame

I am sorry for late response. My GRE is next week, busy with it.

I suggest you to uninstall wine and delete .wine folder from home. Its hidden folder to make it appear press ctrl+H and delete permanently.

Reinstall wine (1.1.16) as explained above and to double check that wine is in default mode 
$rm -rf ~/.wine 

Check wine version 
$wine –version 

it should reply wine 1.1.16.

Only after successful completion of this step we can think of installing office 2007;)

---

### Post by atulkakrana on 2009-06-03
> **tuskenraider said:**
> crossover linux from codeweavers.  
i have office 07 enterprise installed on my ubuntu 9.04 machine...    installed perfectly...  

whats this wine you speak of?? LMAO kidding kidding.. but seriously...

codeweavers look into it. goooooooooooooooooooooooood stuff man


tusken

You may be right tuskenraider. But can you specifically tell the version of crossover you are using.

Also I would like to inform you the codeweaver is based on wine , and wine makes the core. They just extended little support for most used windows apps. 

I will also like to add that crossover is not open source software. So everybody can not have the luxury hassle free install of office like you.

---

### Post by atulkakrana on 2009-06-03
> **rvgsd said:**
> Hi,
I am trying to install MSO through wine using this tutorial. Every step works fine until I start Office 2007 setup. It continues for a little while and stops with an error (Screenshot attached). Here is what I see in the terminal:

```
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:powrprof:DllMain (0x7dfd0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33f0dc 0x33f0d0
fixme:advapi:CheckTokenMembership ((nil) 0x12c8c0 0x33f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12c8c0 0x33f0b8) stub!
fixme:powrprof:DllMain (0x7dfd0000, 0, (nil)) not fully implemented
```

Also, when I type **wine -version** in the terminal, I get this message:
```
could not load L"C:\\windows\\system32\\-version.exe"
```Any suggestions? 
Thanks for helping. 

Regards, rvgsd.

Hello rvgsd,

Dude theres problem with wine, We need to install it perfectly first.

Uninstall wine.
Delete .wine folder from HOME directory ( press ctrl+H to unhide it first)
Install wine 1.1.16 as explained before.
Just to make sure reset wine 
$rm -rf ~/.wine 

and then check wine version.

You must have played with override **** first I believe, All those customization are still extant.

please post the result.

Take care

---

### Post by atulkakrana on 2009-06-03
> **NightMKoder said:**
> Geez you don't need any of this stuff. Just install wine 1.1.16 and install office. Then you need to add two overrides. Service packs don't install yet so don't try. [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

Hi nightMkoder,

I think i they need this stuff as other guides stink of ****. Actually you only took few winetricks stuff from this guide. We both use linux and on the same stage. I dont want any mud slinging, I respect your work also. Lets concentrate on helping our brothers rather then exposing them to new guides every day.

---

### Post by atulkakrana on 2009-06-03
> **Newtothegame said:**
> Thanks for the Post. 
However I am getting an error. 

Note: command 'wine /home/mac/.winetrickscache/dotnet11/dotnetfx.exe' returned status 65.  Aborting

I have uninstalled and reinstalled wine 3 times now and it fails here everytime. 

Also, has anyone got there office to work in completion? On first install I had word working but wouldnt update, and powerpoint would not work. 

thanks, 

Newtothegame

Hi newtogame, I really cant understand whats conflicting with dotnet install. Maybe something you did in past regarding wine or crossover. It can be anything. But i will like to tell you that this is the problem with wine. Did you followed the steps completely.

---

### Post by trouserless on 2009-06-03
> **zbeckerd said:**
> dotnet11 failed to install.  Am trying to find a fix... otherwise this seems to work better than some other things I have tried.

had same problem...run winecfg and delete all overrides (library tab) and make sure Applications tab has Windows XP selected, then apply.

---

### Post by MALeh on 2009-06-05
Hello, i've the same problem that Newtothegame have. Any ideas to solve the problem? Already have installed and deleted (permanently) wine for a thousand times.

Thanks in advance.

---

### Post by taytayflyfly on 2009-06-06
I'm guessing this won't work with Jaunty 9.04 because there is no wine 1.1.16 for it, only 17-22 as of right now. 
Hopefully this will get fixed in a future Wine release?

---

### Post by NightMKoder on 2009-06-06
> **taytayflyfly said:**
> I'm guessing this won't work with Jaunty 9.04 because there is no wine 1.1.16 for it, only 17-22 as of right now. 
Hopefully this will get fixed in a future Wine release?

Install intrepid's 1.1.16. And yes it will be fixed.

---

### Post by jhoeijao on 2009-06-06
> **Newtothegame said:**
> Thanks for the Post. 
However I am getting an error. 

Note: command 'wine /home/mac/.winetrickscache/dotnet11/dotnetfx.exe' returned status 65.  Aborting

I have uninstalled and reinstalled wine 3 times now and it fails here everytime. 

Also, has anyone got there office to work in completion? On first install I had word working but wouldnt update, and powerpoint would not work. 

thanks, 

Newtothegame

> **MALeh said:**
> Hello, i've the same problem that Newtothegame have. Any ideas to solve the problem? Already have installed and deleted (permanently) wine for a thousand times.

Thanks in advance.

I manage to install dotnet11 by locating the installer itself (dotnetfx.exe) you can locate this by opening your home folder press control H to unhidden files click .winetricks cache/dotnet11 and double click dotnetfx.exe or you can "sh ./winetricks [COLOR=Red]dotnet11[/COLOR] msxml3 vcrun2003 vcrun2005sp1 vcrun2008 gdiplus riched20 riched30 msxml3 msxml4 msxml6 tahoma vb3run vb4run vb5run vb6run vcrun6 msi2 allfonts corefonts wsh56js" if you notice I inserted the code [COLOR=Red]dotnet11[/COLOR] first I don't know what's the reason but it works. 

> **taytayflyfly said:**
> I'm guessing this won't work with Jaunty 9.04 because there is no wine 1.1.16 for it, only 17-22 as of right now. 
Hopefully this will get fixed in a future Wine release?

I agree with NightMKoder's suggestion just use Intrepid's wine version 1.1.16. I'm using Jaunty right now and I had no problem installing it.

---

### Post by Fuzzy Toaster on 2009-06-08
Gmount? tsk tsk :)
You can easily mount a disk image from terminal:
sudo mount -t FILESYSTEM ISO-LOCATION MOUNT-POINT -o loop
-o loop as it's inside the same mounted hdd

eg:
sudo mount -t iso9660 /home/user/software/office2007.iso /home/user/software/newfolder -o loop

---

### Post by autra on 2009-06-08
its wine --version and not wine -version to get the version of wine ):P

---

### Post by atulkakrana on 2009-06-10
> **autra said:**
> its wine --version and not wine -version to get the version of wine ):P


Thanks Autra....

---

### Post by JustLookingToHelp on 2009-06-12
Thanks for the step-by-step. Worked great for me on 8.10 Intrepid. My friend gave me the trial version exe files that he downloaded. I had to do one extra step to get it to work though:

Go to wine settings (Applications-> Wine -> Configure Wine -> Drives "Tab"-> hit the "Autodetect..." button). I also had to add the hidden folder /home/USERNAME/.wine/ (hit "Add..." button, type in /home/USERNAME/.wine/) replacing USERNAME with your home directory.

I just did the regular install. Word seems to work great... now if I could only figure out how to update...

Thanks again!

[Thanks for the heads up as well... took forever to install]

---

### Post by jhoeijao on 2009-06-12
Kindly change the S in the "Sudo apt-get install cabextract" into small letter  although it's  a typographical error only but it will confuse newbies who wants to use your guide.

Thanks.

---

### Post by Jannes. on 2009-06-16
thx m8

With this tutorial i already can open my CD but if its installing it gives an error... but not what kind of error.

grtz

---

### Post by atulkakrana on 2009-06-18
> **jhoeijao said:**
> Kindly change the S in the "Sudo apt-get install cabextract" into small letter  although it's  a typographical error only but it will confuse newbies who wants to use your guide.

Thanks.


Thanks Jhoeijao.

---

### Post by atulkakrana on 2009-06-18
> **Jannes. said:**
> thx m8

With this tutorial i already can open my CD but if its installing it gives an error... but not what kind of error.

grtz

Please specify your error...or point at which error appears ( like installing some specific component).

---

### Post by tstduke on 2009-10-07
Followed the instructions and Work works perfectly. I cannot however get power point to open. Any suggestions?

---

### Post by tstduke on 2009-10-07
After searching the net I found this 
  (Type winecfg in a terminal, then go to the libraries tab. In the "Add new override for library" box type "riched20" (no ") and click add, then click edit and make sure it is set to "native then built in".)
Now Power point works perfectly too!.

---

