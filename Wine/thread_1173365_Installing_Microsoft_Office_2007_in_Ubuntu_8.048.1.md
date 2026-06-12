---
title: "Installing Microsoft Office 2007 in Ubuntu 8.04/8.10/9.04 using Wine 1.1.12 to 16"
date: 2009-05-29
forum: Wine
---

### Post by jhoeijao on 2009-05-29
[SIZE=2][B] UPDATED POST: (August 18, 2009)
[/B]
Since the day of the release of Wine version 1.1.24 the regression issue was resolved and probably future versions (1.1.24+) will do the same. 

The guide is just a summary of all the online guides that I have tried and to be honest many of those guides gave me so many headaches for the simple reason, **"I'm a newbie to UBUNTU"**. So I've decided to join in this forum last May 2009 and made a simple guide that's especially made for newbies like me.

Thanks to all the online guides that helped me formulate this simple guide all the credits must be given to all of you..
[B]
HERE ARE THE STEPS:
[/B]
**A. WINE CHECK/VERSION CHECK**[/SIZE][INDENT][SIZE=2]-to check if you have installed wine already or check the version of your wine
[/SIZE] [/INDENT][INDENT]
[LIST=1]
[*][SIZE=2]Click     Application>Accessories>Terminal[/SIZE]
[*][SIZE=2] On the Terminal     window type &#8216;wine --version&#8217;[/SIZE]
[/LIST]
[/INDENT][SIZE=2][COLOR=Blue] Note:[/COLOR][/SIZE]
[LIST=1]
[*][SIZE=2][COLOR=Blue] If you have not     installed wine yet you will receive this message[/COLOR][/SIZE][SIZE=2][COLOR=Blue][COLOR=DarkRed] The program 'wine' is currently not installed.  You can install it by typing: [/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=DarkRed]sudo apt-get install wine [/COLOR][/SIZE][SIZE=2][COLOR=DarkRed]bash: wine: command not found [/COLOR][/SIZE][SIZE=2][COLOR=Blue]then you may     proceed to **STEP D*****.*** [/COLOR][/SIZE]
[*][SIZE=2][COLOR=Black][COLOR=Blue]If your wine version is 1.1.12 to 1.1.16 or 1.1.24+ then you may proceed to [/COLOR][B][COLOR=Blue]STEP C[/COLOR]
[/B][/COLOR][/SIZE]
[/LIST]
 [SIZE=2][B]
  B. UNINSTALL WINE[/B][/SIZE][INDENT][SIZE=2]-If the version of your wine is 1.1.11 below, 1.1.17 to 1.1.23 you will not be able to install MSOffice 2007 due to regression so you have to uninstall this by following the steps:[/SIZE][/INDENT][INDENT]
[LIST=1]
[*][SIZE=2]Click         System>Administration>Synaptic Package Manager[/SIZE]
[*][SIZE=2]On the Synaptic Package Manager window type &#8216;Wine&#8221; on Search scroll down look for Wine right click on it and click Mark for Complete Removal>Apply>Reload>Close &#8220;OR&#8221;[/SIZE]
[*][SIZE=2]Type ```
sudo apt-get remove wine
``` in your terminal window. (I prefer this one because this is faster compared in using Synaptic Package Manager)[/SIZE]
[/LIST]
[/INDENT][SIZE=2][B]C. DELETE WINE FOLDER
[/B][/SIZE][INDENT][SIZE=2]- this step will delete your wine folder which means all programs you installed through wine will also be deleted. 
[/SIZE] [/INDENT][INDENT]
[LIST=1]
[*][SIZE=2]Click Places>Home Folder press CTRL+H to unhide .wine folder and press delete or type ```
rm -rf ~./wine
``` in your terminal window.[/SIZE]
[/LIST]
[/INDENT][SIZE=2][B]D. INSTALL WINE
[/B][/SIZE][INDENT][SIZE=2]**- **Wine is a translation layer (a program loader) capable of running Windows applications on Linux and other POSIX compatible operating systems.[/SIZE][/INDENT][INDENT]
[LIST=1]
[*][SIZE=2]Download wine from this site     [/SIZE][SIZE=2][COLOR=#0000ff]_[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)_[/COLOR][/SIZE][SIZE=2]     and click your desired version (1.1.12 &#8211; 1.1.16 or 1.1.24+)[/SIZE]
[*][SIZE=2]After downloading     double click the file and install it if a warning message like this[/SIZE][SIZE=2][COLOR=Black]* [COLOR=DarkRed]'A     later version is available in a "software channel"[/COLOR] *[/COLOR]will appear just click ok and install.[/SIZE]
[/LIST]
[/INDENT][SIZE=2][COLOR=Blue]Note:
[/COLOR][/SIZE][INDENT][SIZE=2][COLOR=Blue]If your operating system (OS) is a fresh or newly installed you need to click System>Administration>Synaptic Package Manager and click Reload to update the necessary files needed in installing wine.[/COLOR][/SIZE][SIZE=2]
[/SIZE] [/INDENT][SIZE=2]**E. INSTALL MICROSOFT OFFICE ****2007**[/SIZE][INDENT]
[LIST=1]
[*][SIZE=2]Insert your Microsoft Office 2007 installer on your CD-ROM look for the file named 'setup.exe' right click on it and click open with other application choose Wine Windows Program Loader.[/SIZE]
[*][SIZE=2]On the setup window type the license key click Continue and Install or you may click Customize and choose the applications you want and Install.[/SIZE]
[/LIST]
[/INDENT][SIZE=2][COLOR=Blue]Note: 
[/COLOR][/SIZE][INDENT][SIZE=2][COLOR=Blue]Please do not         proceed to **STEP F** if you failed on this step.
[/COLOR][/SIZE][/INDENT][SIZE=2][B] 
F. INSTALL WINETRICKS
[/B][/SIZE][INDENT][SIZE=2]- A useful tool for using common workarounds to current deficiencies in Wine. [/SIZE][/INDENT][INDENT]
[LIST=1]
[*][SIZE=2]Install winetricks by openning your terminal and type sudo wget[/SIZE] [SIZE=2][COLOR=#0000ff]_[www.kegel.com/wine/winetricks]("http://www.kegel.com/wine/winetricks")_[/COLOR][/SIZE]
[*][SIZE=2]Install cabextract to  extract the contents of Microsoft cabinet archives ```
sudo apt-get install cabextract
```[/SIZE]
[*][SIZE=2]Install the following:[/SIZE]
[/LIST]
[INDENT]
[LIST]
[*][SIZE=2]**corefronts**           - installs MS Arial, Courier and Times fonts;[/SIZE]
[*][SIZE=2]**tahoma**                  - installs tahoma fonts;[/SIZE]
[*][SIZE=2]**vcrun2005sp1**     - installs MS Visual C++ 2005 sp1 libraries; and[/SIZE]
[*][SIZE=2]**wsh56js**                - installs MS Windows scripting 5.6, jscript only, no script[/SIZE]
[/LIST]
[/INDENT][/INDENT][INDENT][SIZE=2] ```
sh winetricks corefonts tahoma vcrun2005sp1 wsh56js
```[/SIZE][/INDENT][SIZE=2]**G. CONFIGURE WINE**[/SIZE][INDENT][SIZE=2] - to be able to run programs properly like MS PowerPoint you need to configure wine 
[/SIZE] [/INDENT][INDENT]
[LIST=1]
[*][SIZE=2]Click     Applications>Wine>Configure Wine or type ```
winecfg
``` on your     terminal window[/SIZE]
[*][SIZE=2]On the Libraries Tab     type &#8216;riched20&#8217; click add and type &#8216;usp10&#8217; and click again.[/SIZE]
[*][SIZE=2]Highlight or click     'riched20' and click Edit change it to &#8216;Native windows&#8217; then     click Apply and Ok.[/SIZE]
[/LIST]
[/INDENT][SIZE=2]**H. TEST MICROSOFT OFFICE**[/SIZE][INDENT]
[LIST=1]
[*][SIZE=2]Open Microsoft Office Word 2007. Applications>Wine>Programs>Microsoft Office> Microsoft Office Word 2007 and your done![/SIZE]
[/LIST]
[/INDENT][B][SIZE=2]I. REBOOT COMPUTER
[/SIZE][/B][INDENT]- to be able update menus
[/INDENT][B][SIZE=2]

SOLUTIONS TO COMMON ISSUES:[/SIZE][/B][INDENT][SIZE=2]Read this first before asking for help with wine by admin [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)[/SIZE][/INDENT]
[LIST]
[*][SIZE=2]** I want to use old versions where can I download it?**[/SIZE]
[/LIST]
[INDENT][SIZE=2]-Use wine for Ubuntu 8.04 or 8.10 but I suggest that you use the latest version visit [http://www.winehq.org/](http://www.winehq.org/)
[/SIZE][/INDENT]
[LIST]
[*][SIZE=2]**I'm using an older version of Ubuntu will my MSOffice installation be affected if I will upgrade it?**[/SIZE]
[/LIST]
[INDENT][SIZE=2]- There's a big tendency but if that's the case then I suggest do the installation again.
[/SIZE][/INDENT]
[LIST]
[*][SIZE=2]** I'm working on Step E but then it suddenly stopped, what will I do?**[/SIZE]
[/LIST]
[INDENT][SIZE=2]- if the installation stopped on **Step E** make sure that you did not miss any step before it  but if you're sure that you did all the steps right then my assumption is it's a hardware related problem try to use a different installation media.
[/SIZE][/INDENT]
[LIST]
[*][SIZE=2]to be continued...[/SIZE]
[/LIST]
[SIZE=2]
to all the visitors of the guide please help me enumerate common issues in installing MSOffice 2007 and its possible solutions.

Thank you.

[/SIZE][SIZE=2]**ORIGINAL POST: (May 30, 2009)**[/SIZE][SIZE=2][B]
1st REVISION: (June 29, 2009)[/B][/SIZE]

---

### Post by hyperdude111 on 2009-05-29
Installing office 2007 in wine is quite easy and on the latest versions it is fully supported.

---

### Post by jhoeijao on 2009-05-29
> **hyperdude111 said:**
> Installing office 2007 in wine is quite easy and on the latest versions it is fully supported.

I will try upgrading wine after using the guide above. If it will work. then I'll update the guide. Thanks for the info anyway.

---

### Post by Sef on 2009-05-30
Moved to the WINE Forum.

---

### Post by NightMKoder on 2009-05-30
> **hyperdude111 said:**
> Installing office 2007 in wine is quite easy and on the latest versions it is fully supported.

There is a regression in wine 1.1.17-1.1.22 (and probably 23) that won't let you install wine on those versions. You can RUN office apps under those versions (in fact copy/paste support improved A LOT in 1.1.22), but you just can't install it.

---

### Post by jhoeijao on 2009-05-30
> **Sef said:**
> Moved to the WINE Forum.

Thanks for moving my post in Wine forum. I'm trying to find a way how to move this but I guess only moderators can do that.

---

### Post by monchedeng on 2009-05-30
How can you get the right wine version for jaunty?

---

### Post by jhoeijao on 2009-05-31
> **monchedeng said:**
> How can you get the right wine version for jaunty?

Try using Wine for Ubuntu 8.04 because Jaunty doesn't have wine version lower than 1.1.18. I'm using Jaunty right now wine version 1.1.14.

By the way thanks for reminding me about this I'll update my guide.

---

### Post by Pooven on 2009-06-08
Excellent post! I was trying for the longest time to setup Office 2007 and it finally works :)

Though I've noticed that PowerPoint acts up if I try to draw an arrow between shapes... kinda sad but I'm just really happy that Word 2007 works so well! Thank you ever so much!

I tried upgrading wine after installing Office and Office stopped working... just btw... so yeah, I'm sticking with wine 1.1.16

---

### Post by jhoeijao on 2009-06-08
> **Pooven said:**
> Excellent post! I was trying for the longest time to setup Office 2007 and it finally works :)

Though I've noticed that PowerPoint acts up if I try to draw an arrow between shapes... kinda sad but I'm just really happy that Word 2007 works so well! Thank you ever so much!

I tried upgrading wine after installing Office and Office stopped working... just btw... so yeah, I'm sticking with wine 1.1.16

You're welcome.

---

### Post by tarekeldeeb on 2009-06-09
I have ubuntu 9.04, followed your guide (with wine 1.1.14 and 16).. no luck

The installation starts, entered the key, chose components for installation, starts installing .. then ..the attached error shows.

I had successfully installed it long ago .. on 8.04. I remember copying some dll files from MS_windows, maybe you missed such step?

Please help.

Thank you

---

### Post by jhoeijao on 2009-06-09
> **tarekeldeeb said:**
> I have ubuntu 9.04, followed your guide (with wine 1.1.14 and 16).. no luck

The installation starts, entered the key, chose components for installation, starts installing .. then ..the attached error shows.

I had successfully installed it long ago .. on 8.04. I remember copying some dll files from MS_windows, maybe you missed such step?

Please help.

Thank you

Uninstall your wine again use the number 3 step. Delete your wine folder and install wine version 1.1.12 this time ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) then install MSO 2007. I'll stay for a while if you will still encounter problems.

---

### Post by tarekeldeeb on 2009-06-09
> **jhoeijao said:**
> Uninstall your wine again use the number 3 step. Delete your wine folder and install wine version 1.1.12 this time ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) then install MSO 2007. I'll stay for a while if you will still encounter problems.

Mmm.. 1.1.12 caused the setup to crash when i pasted the serial number!

Are you sure 1.1.14 does not need extra dlls or hacking?

---

### Post by NightMKoder on 2009-06-09
> **tarekeldeeb said:**
> Mmm.. 1.1.12 caused the setup to crash when i pasted the serial number!

Are you sure 1.1.14 does not need extra dlls or hacking?

Old HOWTO's suggest practically replacing half of wine. This is generally a bad idea, and is no longer needed since wine 1.1.9.

As for your error: make sure you start with a clean prefix. That does not mean reinstalling wine, that means `rm -rf ~/.wine`. Note, this will remove all of your programs, but we can't be sure that you haven't installed anything naughty that's making office cry.

---

### Post by demo1018 on 2009-06-09
I have ubuntu 9.04, followed your guide (with wine 1.1.14 and 16).. no luck

I can not fine the icon for office 2007 in application->Wine->Program

So, I try to use terminal with command "wine WINWORD.exe", and got the error message like below:
=====================================================
[email]donnie@donnie-nb:~/.wine[/email]/drive_c/Program Files/Microsoft Office/Office12$ wine WINWORD.EXE 
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
[email]donnie@donnie-nb:~/.wine[/email]/drive_c/Program Files/Microsoft Office/Office12$ 
======================================================

I have search in many forum and try many idea but still in fail, so I need help from some one ... thanks

---

### Post by tarekeldeeb on 2009-06-10
> **NightMKoder said:**
> Old HOWTO's suggest practically replacing half of wine. This is generally a bad idea, and is no longer needed since wine 1.1.9.

As for your error: make sure you start with a clean prefix. That does not mean reinstalling wine, that means `rm -rf ~/.wine`. Note, this will remove all of your programs, but we can't be sure that you haven't installed anything naughty that's making office cry.

that's what I do each step ..
this tutorial states so .. :)

---

### Post by tarekeldeeb on 2009-06-10
Sorry about the errors ..

My Office2007 installation source had a problem with wine (although worked perfect with many windows).

I got another Office2007 source, your guide worked perfectly
:popcorn:

Thank you!

---

### Post by jhoeijao on 2009-06-10
> **tarekeldeeb said:**
> Sorry about the errors ..

My Office2007 installation source had a problem with wine (although worked perfect with many windows).

I got another Office2007 source, your guide worked perfectly
:popcorn:

Thank you!

I was about to reply on your comment but knowing that you manage to install Office2007 already I don't need to give some help.

Your welcome tarekeldeeb!

---

### Post by jhoeijao on 2009-06-10
By the way what wine version did you use tarelkeldeeb? Just a survey.

---

### Post by tarekeldeeb on 2009-06-10
> **jhoeijao said:**
> By the way what wine version did you use tarelkeldeeb? Just a survey.

the one you selected 1.1.14.

By the way, how to install the office to /usr/share (or /opt) .. so any new user can have the office 2007 working.. any ideas?

---

### Post by jhoeijao on 2009-06-10
> **demo1018 said:**
> I have ubuntu 9.04, followed your guide (with wine 1.1.14 and 16).. no luck

I can not fine the icon for office 2007 in application->Wine->Program

So, I try to use terminal with command "wine WINWORD.exe", and got the error message like below:
=====================================================
[EMAIL="donnie@donnie-nb:%7E/.wine"]donnie@donnie-nb:~/.wine[/EMAIL]/drive_c/Program Files/Microsoft Office/Office12$ wine WINWORD.EXE 
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
[EMAIL="donnie@donnie-nb:%7E/.wine"]donnie@donnie-nb:~/.wine[/EMAIL]/drive_c/Program Files/Microsoft Office/Office12$ 
======================================================

I have search in many forum and try many idea but still in fail, so I need help from some one ... thanks

Try the solution that I have given to tarelkeldeeb. Uninstall your wine again use the number 3 step. Delete your wine folder (rm -rf ~/.wine) and install wine version 1.1.12 this time ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) then install MSO 2007.

---

### Post by jhoeijao on 2009-06-10
> **tarekeldeeb said:**
> the one you selected 1.1.14.

By the way, how to install the office to /usr/share (or /opt) .. so any new user can have the office 2007 working.. any ideas?

To be honest I haven't tried that. Since you have opened up that topic I'll find a way how to do it but if you figure it out first please feel free to post it.  :)

---

### Post by etserrano on 2009-06-10
Man, you're the best. Thanks a lot for this guide. You rule!!!

Erik

---

### Post by jhoeijao on 2009-06-10
> **etserrano said:**
> Man, you're the best. Thanks a lot for this guide. You rule!!!

Erik

Your welcome.:popcorn:

---

### Post by tarekeldeeb on 2009-06-10
> **jhoeijao said:**
> To be honest I haven't tried that. Since you have opened up that topic I'll find a way how to do it but if you figure it out first please feel free to post it.  :)

I did it .. :) 

although it's little dirty .. but working..

1) first install office (use your guide) .. do not open it!!
2) ```
sudo mv /home/$USER/.wine/drive_c /opt/wine_drive_c
```
3) repeat this for all users:
```
rm -fr /home/$USER/.wine/drive_c
ln -s /opt/wine_drive_c /home/$USER/.wine/drive_c
mkdir /home/$USER/.wine/myprofile
sudo ln -s /home/$USER/.wine/myprofile /opt/wine_drive_c/windows/profiles/$USER
```

That's it ..

Salam :popcorn:

---

### Post by jhoeijao on 2009-06-10
> **tarekeldeeb said:**
> I did it .. :) 

although it's little dirty .. but working..

1) first install office (use your guide) .. do not open it!!
2) ```
sudo mv /home/$USER/.wine/drive_c /opt/wine_drive_c
```3) repeat this for all users:
```
rm -fr /home/$USER/.wine/drive_c
ln -s /opt/wine_drive_c /home/$USER/.wine/drive_c
mkdir /home/$USER/.wine/myprofile
sudo ln -s /home/$USER/.wine/myprofile /opt/wine_drive_c/windows/profiles/$USER
```That's it ..

Salam :popcorn:

Great if you figure it out! I will try this later because I am using a different machine now. Thanks!

---

### Post by atulkakrana on 2009-06-10
I believe you were using codeweavers as you stated in 
[http://ubuntuforums.org/showthread.php?t=1151825](http://ubuntuforums.org/showthread.php?t=1151825)

---

### Post by NightMKoder on 2009-06-10
> **tarekeldeeb said:**
> I did it .. :) 

although it's little dirty .. but working..

1) first install office (use your guide) .. do not open it!!
2) ```
sudo mv /home/$USER/.wine/drive_c /opt/wine_drive_c
```
3) repeat this for all users:
```
rm -fr /home/$USER/.wine/drive_c
ln -s /opt/wine_drive_c /home/$USER/.wine/drive_c
mkdir /home/$USER/.wine/myprofile
sudo ln -s /home/$USER/.wine/myprofile /opt/wine_drive_c/windows/profiles/$USER
```

That's it ..

Salam :popcorn:

That's somewhat right, but it won't work. What you did is equivalent to copying the install from windows (it won't work correctly). You also need the wine registry that's in your wine folder. And lastly, you will probably need to chmod 777 everything so wine doesn't crash when writing temp files or something.

In general - not a very good idea. The simple reason - now you share your wine drive with someone else. Anything they install/break will "magically" propagate to your install. It's probably easier to just copy your .wine folder to the new account.

---

### Post by tarekeldeeb on 2009-06-11
> **NightMKoder said:**
> That's somewhat right, but it won't work. What you did is equivalent to copying the install from windows (it won't work correctly). You also need the wine registry that's in your wine folder. And lastly, you will probably need to chmod 777 everything so wine doesn't crash when writing temp files or something.

In general - not a very good idea. The simple reason - now you share your wine drive with someone else. Anything they install/break will "magically" propagate to your install. It's probably easier to just copy your .wine folder to the new account.

1_ The registry is not copied .. it's still in ~/.wine. I only copied ~/.wine/drive_c
2_ The temp and configuration files are written in the profile, which is located in ~/.wine/myprofile .. so I have a write access.
3_ No-one can break the wine, as he does not have the write access! On the other hand, no-one can install an application. Ie. this configuration will let office work properly .. only office! This is my case. More applications must be installed by whoever has the sudo access, whom is assumed to know what he's doing.
4_ copying the whole .wine folder will consume the storage very quickly .. moreover, creating a new user will be a slow command.

If you have another ideas, please share.

Thanks,
Salam:D

---

### Post by NightMKoder on 2009-06-11
> **tarekeldeeb said:**
> 1_ The registry is not copied .. it's still in ~/.wine. I only copied ~/.wine/drive_c
2_ The temp and configuration files are written in the profile, which is located in ~/.wine/myprofile .. so I have a write access.
3_ No-one can break the wine, as he does not have the write access! On the other hand, no-one can install an application. Ie. this configuration will let office work properly .. only office! This is my case. More applications must be installed by whoever has the sudo access, whom is assumed to know what he's doing.
4_ copying the whole .wine folder will consume the storage very quickly .. moreover, creating a new user will be a slow command.

If you have another ideas, please share.

Thanks,
Salam:D

1. Yes that's what I mean. You NEED to have the registry entries. Microsoft apps use the registry readily.
2. Not always. c:\windows\temp is the default for the TEMP env variable. You can change it by changing a registry entry, but...see 1.
3. Actually, noone can install anything anymore. sudo wine will give you a "you don't own the .wine directory" and just wine will give write errors.
4. Fair enough, but this isn't going to work too well. You're better off doing something like:
```

sudo -s
export WINEPREFIX=/opt/office2007/
wine /media/cdrom/Setup.exe
chmod -R 777 /opt/office2007
exit

```

Now to configure office on someone else's account:
```

mkdir .wine_office2007
cd .wine_office2007
for i in /opt/office2007/*.reg; do cp $i .; done
ln -s /opt/office2007/dosdevices
ln -s /opt/office2007/drive_c

```
Or do the more detailed profile linking you used. To start wine in the new users' profile you would use:

```

env WINEPREFIX=/home/$USER/.wine_office2007 wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.exe'

```

On the bright side, this doesn't touch the users' wine installation (they can install apps to their .wine directory) & they have all the registry that they should have.

On the bad side, they can mess with the general office directory if they so choose. I guess the only way out of this is to make it read only (755), but that has the downside of making windows temp unusable. Someone needs to test this.

Sadly, I'm still not entirely convinced either of these approaches will work if multiple users run it at the same time. But who knows.

---

### Post by jhoeijao on 2009-06-12
> **atulkakrana said:**
> I believe you were using codeweavers as you stated in 
[http://ubuntuforums.org/showthread.php?t=1151825](http://ubuntuforums.org/showthread.php?t=1151825)

Yes I did install Codeweavers' Cross Over Linux in one of my machine because for me that's the only way I can support WINE by purchasing their product ([http://www.codeweavers.com/products/support_wine/](http://www.codeweavers.com/products/support_wine/)). But if you don't want to spend money in installing MSOffice 2007 then you can use this guide and I also recommend NightMKoder's guide.

---

### Post by Debu182 on 2009-06-15
I am a regular visitor of this forum, but never bother about registering here.
But now i m registered here just to THANK YOU.

It's PERFECT and SIMPLE.

---

### Post by Jannes. on 2009-06-15
[IMG]http://i6.photobucket.com/albums/y229/ForzaKVM/Schermafdruk.png[/IMG]

I got an error... Im using wine 1.1.14
And my machine is 9.04

I use original office CD no crax, downloads...

Grtz

---

### Post by NightMKoder on 2009-06-15
Does said DLL exist? Can you copy it to, say, your desktop?

---

### Post by ddrum2000 on 2009-06-15
So I have a completely different problem.  I have intalled wine 1.1.14 on Ubuntu 9.04 and when I run the office 2007 setup I get an error that says "ERROR_INSTALL_LANGUAGE_UNSUPPORTED".  Has anyone tackled this one?

---

### Post by Jannes. on 2009-06-15
[IMG]http://i6.photobucket.com/albums/y229/ForzaKVM/Schermafdruk-1.png[/IMG]

OSETUP.DLL is on the CD

---

### Post by Jannes. on 2009-06-16
this helped me..[http://ubuntuforums.org/showthread.php?p=7465158#post7465158](http://ubuntuforums.org/showthread.php?p=7465158#post7465158)

i tought

with this tutorial i can open the isntaller but then it gives error while instaling.

grtz

---

### Post by jhoeijao on 2009-06-16
> **Debu182 said:**
> I am a regular visitor of this forum, but never bother about registering here.
But now i m registered here just to THANK YOU.

It's PERFECT and SIMPLE.


Your welcome.:)

Ninety percent of your thanks should be credited to the hundred tutorials that I have visited together with comments on each tutorial I only deserve 10% for summarizing and posting a simple guide.

Edit: Welcome to ubuntuforums by the way!

---

### Post by jhoeijao on 2009-06-16
> **Jannes. said:**
> 
I got an error... Im using wine 1.1.14
And my machine is 9.04

I use original office CD no crax, downloads...

Grtz

Try copying the entire CD installer in your desktop. If you will encounter error in copying the installer the problem is in your installer but if you will not encounter any problem try installing it again this time use the copied installer in your desktop look for the setup.exe file right click on it open with wine windows program loader.

---

### Post by jhoeijao on 2009-06-16
> **ddrum2000 said:**
> So I have a completely different problem.  I have intalled wine 1.1.14 on Ubuntu 9.04 and when I run the office 2007 setup I get an error that says "ERROR_INSTALL_LANGUAGE_UNSUPPORTED".  Has anyone tackled this one?

I haven't experience such problem so to be honest I can't help you with that. I tried googling it many have encountered that but I haven't seen a fix for it. What I can only suggest is try a different installer or visit NightKmoder's similar guide and the post the same error message. [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840) I hope you can find a fix.

---

### Post by jhoeijao on 2009-06-16
> **Jannes. said:**
> this helped me..[http://ubuntuforums.org/showthread.php?p=7465158#post7465158](http://ubuntuforums.org/showthread.php?p=7465158#post7465158)

i tought

with this tutorial i can open the isntaller but then it gives error while instaling.

grtz

I have visited the above tutorial and you are still having a problem, please post the error message so I can help.

Edit:
I don't care if you're using a different tutorial if I can help then I will help.

---

### Post by Jannes. on 2009-06-16
no error screen or something its the windows installer which sais fault and quits...

Installer bar is loading and after a bit of blue in the bar it gives fault, quit

---

### Post by jhoeijao on 2009-06-16
> **tarekeldeeb said:**
> Sorry about the errors ..

My Office2007 installation source had a problem with wine (although worked perfect with many windows).

I got another Office2007 source, your guide worked perfectly
:popcorn:

Thank you!

> **tarekeldeeb said:**
> the one you selected 1.1.14.

By the way, how to install the office to /usr/share (or /opt) .. so any new user can have the office 2007 working.. any ideas?

> **tarekeldeeb said:**
> I did it .. :) 

although it's little dirty .. but working..

1) first install office (use your guide) .. do not open it!!
2) ```
sudo mv /home/$USER/.wine/drive_c /opt/wine_drive_c
```3) repeat this for all users:
```
rm -fr /home/$USER/.wine/drive_c
ln -s /opt/wine_drive_c /home/$USER/.wine/drive_c
mkdir /home/$USER/.wine/myprofile
sudo ln -s /home/$USER/.wine/myprofile /opt/wine_drive_c/windows/profiles/$USER
```That's it ..

Salam :popcorn:

tarekeldeeb, I tried this but I encountered problem but I'm still trying to find a way.

---

### Post by Jannes. on 2009-06-16
> 1) first install office (use your guide) .. do not open it!!

i cant install office....

---

### Post by jhoeijao on 2009-06-16
> **Jannes. said:**
> no error screen or something its the windows installer which sais fault and quits...

Installer bar is loading and after a bit of blue in the bar it gives fault, quit

First I need to know what guide are you using right now? If yor using my guide have you tried copying your MSOffice installer in your desktop?

---

### Post by Jannes. on 2009-06-16
wine 1.1.16

---

### Post by jhoeijao on 2009-06-16
> **Jannes. said:**
> wine 1.1.16

Did you manage installing it?

---

### Post by napster2500 on 2009-06-17
It works!! Office 2007 Enterprise Blue Edition
Seems to stop at 2/3, but after 10-20sec. resumes install.

~Ubuntu 9.04 x64
~Wine 1.1.16 from [[COLOR="Red"]**here**[/COLOR]]("http://wine.budgetdedicated.com/archive/index.html"). Just download the x64 version for ubuntu 8.10.
Also, install Winetricks and add Wine libraries exactly how [**jhoeijao**]("http://ubuntuforums.org/showpost.php?p=7368136&postcount=1") kindly wrote.

Thanks a lot man. :D

---

### Post by yuli_capone on 2009-06-17
I have this problem.
The instalation works fine,office the same.
A few days ago when I want to start,won't start...
I tried to open in terminal and i get this error:

yuli@yuli-laptop:~$ /home/yuli/.wine/drive_c/Program\ Files/Microsoft\ Office/Office12/WINWORD.EXE
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE" failed, status c0000135


What can i do?

---

### Post by NightMKoder on 2009-06-17
Do you have a slipstreamed version of office or something? (you have to install the BASIC office, ie not pre-patched versions)

Try winetricks vcrun2005 vcrun2005sp1

If that doesn't help - I don't think there is a solution.

---

### Post by keypox on 2009-06-18
thanks works perfectly

---

### Post by jhoeijao on 2009-06-18
> **keypox said:**
> thanks works perfectly

You're welcome.:popcorn:

---

### Post by mcmike on 2009-06-19
The install went fine on 9.04!! I can use Word, Excel, PowerPoint!! Great!!:D
But when I try to configure Outlook the wizard configuration window doesn't show the options, they are all in grayout!! What can I do? Some help needed...

---

### Post by jhoeijao on 2009-06-19
> **mcmike said:**
> The install went fine on 9.04!! I can use Word, Excel, PowerPoint!! Great!!:D
But when I try to configure Outlook the wizard configuration window doesn't show the options, they are all in grayout!! What can I do? Some help needed...

Any screen shot of the problem?

---

### Post by james.brantley on 2009-06-19
[SIZE=3]Yes, this was a most excellent post! I have tried multiple times to install Office with no luck. I got it this time though!I have but one issue. The Arial font is for some reason italic. Any ideas? I'd just like to say again that this was a great post. It has ended my fight with installing Office in Wine! Thanks![/SIZE]

---

### Post by jhoeijao on 2009-06-19
> **james.brantley said:**
> [SIZE=3]Yes, this was a most excellent post! I have tried multiple times to install Office with no luck. I got it this time though!I have but one issue. The Arial font is for some reason italic. Any ideas? I'd just like to say again that this was a great post. It has ended my fight with installing Office in Wine! Thanks![/SIZE]

On the terminal type or copy and paste this "sh winetricks corefronts allfonts" or you may upgrade your wine to 1.1.23 download it from here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) (Note: Upgrading wine worked on me but for some they have no luck.)

---

### Post by ws.venkateswaran on 2009-06-20
thanks a lot. it works perfectly.

till now i tried a lot of guides and none were as clear as yours

thanks again

---

### Post by jhoeijao on 2009-06-20
> **ws.venkateswaran said:**
> thanks a lot. it works perfectly.

till now i tried a lot of guides and none were as clear as yours

thanks again

You're welcome.:popcorn:

---

### Post by NightMKoder on 2009-06-20
NOTE: office 2007 regression in wine is fixed with wine 1.1.24. You no longer need to downgrade to install office.

Please update your guide.

---

### Post by jhoeijao on 2009-06-20
> **NightMKoder said:**
> NOTE: office 2007 regression in wine is fixed with wine 1.1.24. You no longer need to downgrade to install office.

Please update your guide.

Thanks! I'll update my guide after my work..

---

### Post by Jannes. on 2009-06-21
I installed wine and Microsoft but i cant see my wine in my menu's...

how to add it there

found it by system --> preferences --> main menu but there i tick off wine but it does nothing after close...

---

### Post by jhoeijao on 2009-06-21
> **Jannes. said:**
> I installed wine and Microsoft but i cant see my wine in my menu's...

how to add it there

found it by system --> preferences --> main menu but there i tick off wine but it does nothing after close...

Try to reboot your computer.

---

### Post by Jannes. on 2009-06-21
Nah i did
delete wine (in the main menu preferences)
then i did turn back =)

works great now 

big hug and tq

---

### Post by jhoeijao on 2009-06-21
> **Jannes. said:**
> Nah i did
delete wine (in the main menu preferences)
then i did turn back =)

works great now 

big hug and tq

Finally, you've made it!:popcorn:

---

### Post by sandman3838 on 2009-06-21
Hello
Thanks for the Office setup!
So far so good, it’s nice to be using this again.

However, I do have one question or issue!

I mostly use Ms Word & Excel, and to open a MS Office file DOC or XLT (I use the older format so that I can switch into Open Office if I have to) I have open Word or Excel first.  Opening a already created Word or Excel file fails to open unless I open it to OpenOffice or open Ms Word or Excel first and then find the file.

What options I have under the Right Mouse Button Menu beside Open Office fail.  True there is also “Open with other application” but here again any listing of MS Office Word or Ms Office Excel fails.

My command lines for just opening Word and Excel by themselves are as follows:  If it helps?

env WINEPREFIX="/home/kevin/.wine" wine "C:\Program Files\Microsoft Office\Office12\EXCEL.EXE"

env WINEPREFIX="/home/kevin/.wine" wine "C:\Program Files\Microsoft Office\Office12\WINWORD.EXE"

How can I add a working Target program for MS Excel and MS Word to the Right Mouse Button Menu?

Thank you everyone for your help!

---

### Post by NightMKoder on 2009-06-21
You can create a couple of bash scripts that launch them:

Create a file called: .start_word.sh
```

#!/bin/bash
if [[ $# > 0 ]]; then
    env WINEPREFIX="/home/$USER/.wine" wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.EXE' "`winepath -w \"$@\"`"
else
    env WINEPREFIX="/home/$USER/.wine" wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.EXE'
fi

```

And similarly for excel. Then just run it with the bash script (ie open with other program, and type 'sh /home/kevin/.start_word.sh')

---

### Post by dailyacts56 on 2009-06-21
After I install wine, it asks for a password and it says " [sudo] password for David:
I never setup anything for a password for Ubuntu. What do I need to do?

---

### Post by sandman3838 on 2009-06-22
Thanks NightMKoder its working fine.
That did it!
Depending on the file Word or Excel a working option for either is now available and working in the menu.

I do have a question for you.  Perhaps it's nothing?
This is something else I noticed before I ran the script you suggested.

Take a look at the screen shot.
When I right click on a file (Excel or Word) and open a menu to select:

- OPEN WITH
- OPEN WITH ANOTHER PROGRAM

There are multiple entries (quite a lot actually) for all MS entries:

- 2007 Microsoft Office component
- Microsoft Office Access
- Microsoft Office Excel
- Microsoft Office PowerPoint
- Microsoft Office Publisher
- Microsoft Office Word
- Notepad

Is this normal?  Should I really worry about it?
Now there were some multiple entries for some Ubuntu programs but not as many as the Wine and Office stuff.

What do you think?

---

### Post by crepito on 2009-06-22
> **dailyacts56 said:**
> After I install wine, it asks for a password and it says " [sudo] password for David:
I never setup anything for a password for Ubuntu. What do I need to do?

Its your root password. Assuming your account is the root one, its your login password.

---

### Post by goog64 on 2009-06-24
Hi NightMKoder,
Thanks so much for your posts. A couple of weeks ago you wrote the following about making office available to all users:

"You're better off doing something like:
  	Code:
 	sudo -s
export WINEPREFIX=/opt/office2007/
wine /media/cdrom/Setup.exe
chmod -R 777 /opt/office2007
exit 
 Now to configure office on someone else's account:
  	Code:
 	mkdir .wine_office2007
cd .wine_office2007
for i in /opt/office2007/*.reg; do cp $i .; done
ln -s /opt/office2007/dosdevices
ln -s /opt/office2007/drive_c 
 Or do the more detailed profile linking you used. To start wine in the new users' profile you would use:
 
  	Code:
 	env WINEPREFIX=/home/$USER/.wine_office2007 wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.exe' 
 On the bright side, this doesn't touch the users' wine installation (they can install apps to their .wine directory) & they have all the registry that they should have."

If I re-install Ubuntu and Office and then use the code that you have written above, when I'm logged in to my own account, will this make Office available to all users?
Where you've written "$USER", is that where I put the actual usernames of the accounts to which I want to make Office available?
Thanks again,
John

---

### Post by jhoeijao on 2009-06-26
> **goog64 said:**
> Hi NightMKoder,
Thanks so much for your posts. A couple of weeks ago you wrote the following about making office available to all users:

"You're better off doing something like:
      Code:
     sudo -s
export WINEPREFIX=/opt/office2007/
wine /media/cdrom/Setup.exe
chmod -R 777 /opt/office2007
exit 
 Now to configure office on someone else's account:
      Code:
     mkdir .wine_office2007
cd .wine_office2007
for i in /opt/office2007/*.reg; do cp $i .; done
ln -s /opt/office2007/dosdevices
ln -s /opt/office2007/drive_c 
 Or do the more detailed profile linking you used. To start wine in the new users' profile you would use:
 
      Code:
     env WINEPREFIX=/home/$USER/.wine_office2007 wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.exe' 
 On the bright side, this doesn't touch the users' wine installation (they can install apps to their .wine directory) & they have all the registry that they should have."

If I re-install Ubuntu and Office and then use the code that you have written above, when I'm logged in to my own account, will this make Office available to all users?
Where you've written "$USER", is that where I put the actual usernames of the accounts to which I want to make Office available?
Thanks again,
John

John,

To be honest I'm still looking for a way to do "Multiple Office 2007 users". If you really want Office 2007 be available to all users. I have a suggestion why not install Office 2007 in every user? Although this suggestion needs a larger disk space left that will take approximately 1.5 Gigabytes [COLOR=Red][COLOR=Black](minimum requirement in installing Office 2007)[/COLOR][/COLOR][COLOR=Black] plus 6.8 Megabytes of winetricks for each u[/COLOR]ser.

Here are the steps if you want to try:
[SIZE=2][B]
[SIZE=1]Copy Winetricks[/SIZE][/B][/SIZE]

[LIST=1]
[*]Click Places>Home Folder then press Ctrl+H to unhidden files copy the file named "winetricks" and the folder named ".winetrickscache" this will help you to avoid downloading the same files again and again for each user account.
[*]Copy and paste the said file and folder to the Home Folder of another user.
[/LIST]
**Install         Microsoft Office 2007**
[LIST=1]
[*]Insert your Microsoft Office 2007 installer on your CD-ROM look for the file named 'setup.exe' right click on it and click open with other application choose Wine Windows Program Loader.
[*]On the setup window type the license key click Continue and Install or you may click Customize and choose the applications you want and Install.
[/LIST]
[B]Install         Winetricks
[/B]
[LIST=1]
[*]Type &#8216;sh     winetricks corefonts tahoma vcrun2005sp1 wsh56js&#8217; on your terminal
[/LIST]
**Configure         Wine**
[LIST=1]
[*]Click     Applications>Wine>Configure Wine or type &#8216;winecfg&#8217; on your     terminal window
[*]On the Libraries Tab     type &#8216;riched20&#8217; click add and type &#8216;usp10&#8217; and click again.
[*]Highlight or click     'riched20' and click Edit change it to &#8216;Native windows&#8217; then     click Apply and Ok.
[/LIST]
**Test         Microsoft Office 2007**
 
[LIST=1]
[*]Open Microsoft Office Word 2007. Applications>Wine>Programs>Microsoft Office> Microsoft Office Word 2007 and your done!
[/LIST]
That's it! Although this is not the best solution but for sure this will help solving your problem but don't worry as soon as I find a fix with (coz' I'm still studying about the different commands in ubuntu) or without the help of others I will post it here and update my guide.

---

### Post by goog64 on 2009-06-27
Thanks so much for your reply, Jhoeijao. 
I am going to have one more attempt using NightMKoder's code in post #30 of this thread. I have already re-installed Ubuntu and Wine and Office2007 four times now, so I'm getting pretty frustrated. This will be my last attempt, and if not successful, I will do as you say and install Office2007 for each user.
I will let you know what happens.
Regards
John

---

### Post by goog64 on 2009-06-27
OK, NightMKoder's code didn't work for me.
When I went to the other user's terminal to run WINWORD:

env WINEPREFIX=/home/$USER/.wine_office2007 wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.exe'
all I got in response was a ">" in the terminal.

Then I went back to my account to run it through my Applications>Wine menu and it didn't start, so I'm just going to install Office 2007 for each user. Please let me know if you find a foolproof way (for complete newbies) of installing Microsoft Office once and letting all users access it.
Thanks,
John

---

### Post by jhoeijao on 2009-06-27
> **goog64 said:**
> OK, NightMKoder's code didn't work for me.
When I went to the other user's terminal to run WINWORD:

env WINEPREFIX=/home/$USER/.wine_office2007 wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.exe'
all I got in response was a ">" in the terminal.

Then I went back to my account to run it through my Applications>Wine menu and it didn't start, so I'm just going to install Office 2007 for each user. Please let me know if you find a foolproof way (for complete newbies) of installing Microsoft Office once and letting all users access it.
Thanks,
John

Sure, as soon as I find a way I will post it right away.:)

---

### Post by delubu on 2009-07-07
hey [jhoeijao]("http://ubuntuforums.org/member.php?u=845538"),
dude i used your updated guide and installed wine 1.1.24 and MS office 2007 SP2. the office seems to be working fine and doing things.

But the problem is that the shortcut icons do not appear in 'Applications > Wine > *'  

:/

is there anyway i can manually add the shotcuts to that folder? or like create another class for MS office shortcuts in Application menu?

btw, i started using ubuntu about a week ago (total n00b) and i found your guide really helpful. 
thanks
=]




[COLOR=Red]EDIT:[/COLOR]
[COLOR=Red]whoa its all sorted out now. i had to reboot ubuntu and all the shortcuts were visible.[/COLOR]

---

### Post by jarrarist on 2009-07-12
works like a charm with 1.1.25 on jaunty!

---

### Post by Lockheed on 2009-07-21
I am using 1.1.25 on jaunty and install went just fine. Word also runs BUT there are two problems.

1. Whenever I try run doc file from nautilus, Word opens but complaints it cannot find the file and then that it has no permission to access it.
Document opens just fine if I run word and then open it from within it.

More important, however

2.The display of fonts! I have a great-looking CV written in Word2003 and when I open it with 2007 on wine, everything written in Arial Bold is cramped. It looks like words are squeezed horizontally. However, if I unbold it, everything looks fine. So words in bold are actually much narrower than without it. What is that?
Also, the bullet-squares I used before not changed into spades form the deck of cards...

Anyone knows how to fix that?

---

### Post by rlgc79 on 2009-07-24
Lockheed

Just out of curiosity. Does installing the microsoft ttf fonts help? Look for ttf-mscorefonts-installer in synaptic... 



> **Lockheed said:**
> I am using 1.1.25 on jaunty and install went just fine. Word also runs BUT there are two problems.

2.The display of fonts! I have a great-looking CV written in Word2003 and when I open it with 2007 on wine, everything written in Arial Bold is cramped. It looks like words are squeezed horizontally. However, if I unbold it, everything looks fine. So words in bold are actually much narrower than without it. What is that?
Also, the bullet-squares I used before not changed into spades form the deck of cards...

Anyone knows how to fix that?

---

### Post by lioncub on 2009-08-08
Ubuntu 9.04 64x, wine 1.1.27, Office 2007 Sp2 - not working!!!
wine setup.exe
Setup Error
ERROR_INSTALL_LANGUAGE_UNSUPORTED

Help...

---

### Post by NightMKoder on 2009-08-09
> **lioncub said:**
> Ubuntu 9.04 64x, wine 1.1.27, Office 2007 Sp2 - not working!!!
wine setup.exe
Setup Error
ERROR_INSTALL_LANGUAGE_UNSUPORTED

Help...

We know service packs don't work. you need the original (no sp) cd.

---

### Post by NightMKoder on 2009-08-09
> **goog64 said:**
> OK, NightMKoder's code didn't work for me.
When I went to the other user's terminal to run WINWORD:

env WINEPREFIX=/home/$USER/.wine_office2007 wine 'C:\Program Files\Microsoft Office\Office12\WINWORD.exe'
all I got in response was a ">" in the terminal.

Then I went back to my account to run it through my Applications>Wine menu and it didn't start, so I'm just going to install Office 2007 for each user. Please let me know if you find a foolproof way (for complete newbies) of installing Microsoft Office once and letting all users access it.
Thanks,
John

That means you forgot something - you either forgot a quote on the end or put a \ on the end of the line. That's not a program error - that's a bash thing.

---

### Post by Jesus_Valdez on 2009-08-10
I installed using Wine 1.1.14 on Jaunty Jackalope using the instructions without problems.

well, I also install Endnote, but I just disable the CWYW add-in and everything works like a charm.

---

### Post by pizza-is-good on 2009-08-10
I would honestly recommend OpenOffice.org
I'm using 3.1 and am very happy with it.
I heard that some future version is supposed to have a ribbon interface, like MS Office 2007.

---

### Post by playtimeX on 2009-08-10
is there a way to install the solver addon for excel?

---

### Post by linuxdiscipulus on 2009-08-11
> 
is there a way to install the solver addon for excel? 


I believe that Wine version 1.1.27 has support for that. 

[http://www.winehq.org/announce/1.1.27](http://www.winehq.org/announce/1.1.27)

---

### Post by linuxdiscipulus on 2009-08-11
I am trying to install office 2007 and its giving me an error. This error comes directly after I have put my activation code in and have chosen to install. (its at about 1% through the install when it says this)

Here is the error:
The program setup.exe has encountered a serious problem and needs to close.

I have gotten this error with wine versions 1.1.14, 1.1.16, 1.1.24, 1.1.26, and 1.1.27.

Each time I reinstall I make sure to remove the wine folder. 

Has anyone else run into this problem?

[COLOR="Red"]Edit:
Problem solved!

I had to delete the .winetrickscache folder as well as .wine

After I did that I installed wine and everything went perfectly!

Thanks for the tutorial!
[/COLOR]

---

### Post by Demon- on 2009-08-11
Thank you for this guide, I followed it to the letter and everythings works fine. Just one question though, whenever I open or save a file, there's also a .lnk file that gets created with the same name as my documents. Do you know how to fix this ?

---

### Post by MMestre on 2009-08-12
It works. ubuntu 9.04.

I'm testing to see if I run into bugs.

Thanks a lot, no reason for windows no more!

---

### Post by sumeshgupta on 2009-08-14
Everything went of very well. However I donot see any office program installed in Applications>Wine>programs. Where has office got installed? I used 1.1.24.:confused:

---

### Post by sumeshgupta on 2009-08-14
Reference my post. I forgot to reboot. 
Everything now works like a charm. Thanks a million Tons.:guitar:

---

### Post by Neffeno on 2009-08-14
perfect its working thanks ;)

---

### Post by Riaku on 2009-08-15
Anyone got Access working?

---

### Post by sumeshgupta on 2009-08-17
Nope.Access is not working for me too. Even the window does'nt open. Any fixes avail?

---

### Post by linuxdiscipulus on 2009-08-17
I am running into another problem.

Office 2007 will not open or save any documents. As soon as I click open or Save As, Office promptly crashes, giving me the Wine error message. I am thinking this might have something to do with Explorer, but I'm not sure.

Previous to this, I had problems opening Wine, so I set the default application to Windows XP which solved it. Did that have something to do with it?

Any help would be greatly appreciated.

---

### Post by NightMKoder on 2009-08-19
> **linuxdiscipulus said:**
> I am running into another problem.

Office 2007 will not open or save any documents. As soon as I click open or Save As, Office promptly crashes, giving me the Wine error message. I am thinking this might have something to do with Explorer, but I'm not sure.

Previous to this, I had problems opening Wine, so I set the default application to Windows XP which solved it. Did that have something to do with it?

Any help would be greatly appreciated.

Do you have any other overrides (other than usp10 & riched20)?

---

### Post by linuxdiscipulus on 2009-08-19
> Do you have any other overrides (other than usp10 & riched20)? 

I reinstalled wine and it's running OK now.

I tried to install IE 6 on it a while ago... I think that installed some other libraries (maybe MSXML3).

Are there specific libraries that conflict with Office 2007?

---

### Post by jhoeijao on 2009-08-19
> **linuxdiscipulus said:**
> I reinstalled wine and it's running OK now.

I tried to install IE 6 on it a while ago... I think that installed some other libraries (maybe MSXML3).

Are there specific libraries that conflict with Office 2007?

There are libraries that conflicts with office 2007 so the fewer the winetricks the lesser the conflicts. If you are planning to install a different application the safest way is to bottle it.

---

### Post by emrys on 2009-08-21
Using Jaunty and Wine Dev. (adding the source: 
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main) works like a charm. So far tried only word. Opening, saving, etc.

---

### Post by loadfoo on 2009-08-21
BTW thank's all for the info ...

---

### Post by russu52 on 2009-08-25
thanks for the help. i installed according to your instructions on a fresh jaunty installation, updated with latest wine version. thanks again

---

### Post by dudekaus on 2009-08-28
Suberb! Thank you for the post. Works great. Have been trying to do this for some time rather unsuccessfully

---

### Post by dudekaus on 2009-08-28
Hello, 

Everything runs smoothly but one, when I try to open the document by clicking it, it shows  an error but if I got to MS Office and use its Open option, the file opens without any problems. Help me. 

I have attached the error screen.

---

### Post by bryantw on 2009-08-28
I seem to be having a problem installing office 07 with wine. It gives me the following error message and i am using my original copy, any suggestions?

---

### Post by jhoeijao on 2009-08-29
> **bryantw said:**
> I seem to be having a problem installing office 07 with wine. It gives me the following error message and i am using my original copy, any suggestions?

Try to copy your installation CD in your hard drive then install it from there. If you encounter problems in copying then i can say that the problem is your installation CD.

---

### Post by jhoeijao on 2009-08-29
> **dudekaus said:**
> Hello, 

Everything runs smoothly but one, when I try to open the document by clicking it, it shows  an error but if I got to MS Office and use its Open option, the file opens without any problems. Help me. 

I have attached the error screen.

Do you mean double clicking your file in opening it? Try to right click on the file first and click Open With Microsoft Word 2007. by the way what version of wine are you using?

---

### Post by jhoeijao on 2009-08-29
> **dudekaus said:**
> Suberb! Thank you for the post. Works great. Have been trying to do this for some time rather unsuccessfully

Your welcome.:)

---

### Post by jhoeijao on 2009-08-29
> **Neffeno said:**
> perfect its working thanks ;)

Your welcome. It's your first post happy Ubuntuing!

---

### Post by jhoeijao on 2009-08-29
> **sumeshgupta said:**
> Nope.Access is not working for me too. Even the window does'nt open. Any fixes avail?

> **Riaku said:**
> Anyone got Access working?

Sad to say that I still have no fixes to make access working.

---

### Post by bryantw on 2009-08-29
> **jhoeijao said:**
> Try to copy your installation CD in your hard drive then install it from there. If you encounter problems in copying then i can say that the problem is your installation CD.

I am very new to ubuntu(just installed it yesterday) i have copied it to the desktop but it says the same thing?

---

### Post by dgrilli on 2009-08-29
Every time I try to verify the version I get:
:confused:
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dave@dave-desktop:~$ wine -version
wine: could not load L"C:\\windows\\system32\\-version.exe": Module not found
dave@dave-desktop:~$ 

Also have no luck at going to the links for Wine posted here says links are broken.

---

### Post by NightMKoder on 2009-08-30
> **dgrilli said:**
> Every time I try to verify the version I get:
:confused:
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dave@dave-desktop:~$ wine -version
wine: could not load L"C:\\windows\\system32\\-version.exe": Module not found
dave@dave-desktop:~$ 

Also have no luck at going to the links for Wine posted here says links are broken.

There are two dashes in version, ie wine --version.

---

### Post by jhoeijao on 2009-08-30
> **dgrilli said:**
> Every time I try to verify the version I get:
:confused:
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dave@dave-desktop:~$ wine -version
wine: could not load L"C:\\windows\\system32\\-version.exe": Module not found
dave@dave-desktop:~$ 

Also have no luck at going to the links for Wine posted here says links are broken.

I have tested all the links posted here and I can't see any problem.

---

### Post by jhoeijao on 2009-08-30
> **bryantw said:**
> I am very new to ubuntu(just installed it yesterday) i have copied it to the desktop but it says the same thing?

What wine version are you using?

Have you tried using a different installation CD?

Start with Step B and C above.

---

### Post by bryantw on 2009-08-31
> **jhoeijao said:**
> What wine version are you using?

Have you tried using a different installation CD?

Start with Step B and C above.
how do i check wich version of wine i have. i am sorry for being a n00b. but i just installed and i am still learning linux.
also i only have this 1 install disk. am i just out of luck?

---

### Post by jhoeijao on 2009-09-01
> **bryantw said:**
> how do i check wich version of wine i have. i am sorry for being a n00b. but i just installed and i am still learning linux.
also i only have this 1 install disk. am i just out of luck?

Just follow step A to check your wine version.

---

### Post by corpis on 2009-09-02
I have the latest beta version of wine. wine-1.1.28 and office loads, but for some reason i cant enter the product key. There a way to manually put it into registry?

---

### Post by drodiger on 2009-09-03
I am using Ubuntu 9.04 x86_64 with wine 1.1.28.
I have installed Ms Office 2007, in winecfg added overrides for riched20, usp10 and jscript to Native.
Word and excel are working fine, but Powerpoint doesn't start:
WINEPREFIX=~/.wine_office2007 wine .wine_office2007/drive_c/Program\ Files/Microsoft\ Office/Office12/POWERPNT.EXE
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:CheckTokenMembership ((nil) 0x13db60 0x32e62c) stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x32efc0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x149560,(nil)): stub
err:eventlog:ReportEventW L"Microsoft Office PowerPoint"
err:eventlog:ReportEventW L"PowerPoint failed to start correctly last time.  Starting PowerPoint in safe mode will help you correct or isolate a startup problem in order to successfully start the program.  Some functionality may be disabled in this mode.\n\nDo you want to start PowerPoint in safe mode?"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:msimtf:DllGetClassObject ({c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} {00000001-0000-0000-c000-000000000046} 0x328878)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} could be created for context 0x1
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32a088,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20042 0x00000000
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.0", (null), 0x00000000, 0x00000051, (nil), 0x00000000, (nil), 0x32a6ec, 0x0000001e, 0x32a6e4) stub
fixme:mscoree:GetCORVersion (0x32a6ec, 30, 0x32a6e4): semi-stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x00001b5b,(nil),0x0004,0x00000000,0x32a5cc,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:mscoree:CorExitProcess (0) stub
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d6e4 "loader.c: loader_section" wait timed out in thread 001a, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7ede1e80 "driver.c: driver_section" wait timed out in thread 0009, blocked by 001a, retrying (60 sec)


Also Outlook 2007 starts and when I try to configure mail account I see blank forms for mail setup: Auto account setup, Online search ... there is no option where I can add my server address...

---

### Post by drodiger on 2009-09-03
OK my mistake :-)
Powerpoint is working. I have checked winecfg and saw that I had riched2 without zero. I added riched20 and it is working.

But now I have to fix Outlook 2007. Anybody got it working with Exchange?

---

### Post by Enissay on 2009-09-03
Thanks dude, it works like a charm, at least for now :)
<3

---

### Post by drodiger on 2009-09-03
I have disabled autodiscovery in registry and I can manually configure accounts (wine regedit, hkcu/software/microsoft/office/12.0/Outlook/autodiscover, create DWORD: PreferLocalXML with value 1). When I test server (IP or fqdn) it says it server doesn't exist.

---

### Post by NightMKoder on 2009-09-04
Outlook won't work. Use a native e-mail client, I'm sure you can use native e-mail clients with exchange.

---

### Post by bryantw on 2009-09-05
> **jhoeijao said:**
> Just follow step A to check your wine version.
ok i followed step A and it said i was using version 1.01. I guess i somehow got like the oldest version. i uninstalled that and now i have 1.1.29. and it installed fine. i now have office apps in the "other" tab i click on the icon and the loading cursor comes up for a few seconds and then it goes away and nothing happens.

---

### Post by chris1950 on 2009-09-05
I have the same problem using Ultimate Edition 2.3 which is Jaunty based. All Office programs try to start but nothing happens. Using wine 1.1.29 with wine-doors installed.

---

### Post by jhoeijao on 2009-09-06
> **bryantw said:**
> ok i followed step A and it said i was using version 1.01. I guess i somehow got like the oldest version. i uninstalled that and now i have 1.1.29. and it installed fine. i now have office apps in the "other" tab i click on the icon and the loading cursor comes up for a few seconds and then it goes away and nothing happens.

Try to delete your wine folder by following step C then proceed to step E.

I just want to know what MSOffice 2007 version are you trying to install? If you're using the same version with chris1950 then I cannot tell what's the real problem. Unless I have that MSOffice 2007 version.

> **chris1950 said:**
> I have the same problem using Ultimate Edition 2.3 which is Jaunty based. All Office programs try to start but nothing happens. Using wine 1.1.29 with wine-doors installed.

I wanted to try this guide in all MSOffice 2007 version but sad to say I only have MSOffice 2007 Enterprise.

---

### Post by bryantw on 2009-09-06
> **jhoeijao said:**
> Try to delete your wine folder by following step C then proceed to step E.

I just want to know what MSOffice 2007 version are you trying to install? If you're using the same version with chris1950 then I cannot tell what's the real problem. Unless I have that MSOffice 2007 version.



I wanted to try this guide in all MSOffice 2007 version but sad to say I only have MSOffice 2007 Enterprise.

I have done what you said. and here is the status of each program:
...Word-Appears to work fine
...Excel-Appears to work fine
...Powerpoint- shows splashscreen then goes away and when i open again it wants to open in safe mode and does the same thing
...Outlook-Runs but email setup wizard does not work properly
...Publisher-Works until i create anything
...InfoPath-Does nothing

I am using the Pro version of office. I just thought i would give you an update on the programs status to help out. Thank you very much im glad that word and excel work! any thing for Powerpoint? if not it not a problem. :)

---

### Post by jhoeijao on 2009-09-07
> **bryantw said:**
> I have done what you said. and here is the status of each program:
...Word-Appears to work fine
...Excel-Appears to work fine
...Powerpoint- shows splashscreen then goes away and when i open again it wants to open in safe mode and does the same thing
...Outlook-Runs but email setup wizard does not work properly
...Publisher-Works until i create anything
...InfoPath-Does nothing

I am using the Pro version of office. I just thought i would give you an update on the programs status to help out. Thank you very much im glad that word and excel work! any thing for Powerpoint? if not it not a problem. :)

Thanks for the updates.

About your problem in running PowerPoint try Step G. I am assuming that you've installed winetricks already.

---

### Post by eugen_nicoara on 2009-09-07
Hi,
There is a nice MS Office Add-in called "Microsoft Save as PDF or XPS" avaialable here: [http://www.microsoft.com/downloads/details.aspx?FamilyID=4d951911-3e7e-4ae6-b059-a2e79ed87041&displayLang=en]("http://www.microsoft.com/downloads/details.aspx?FamilyID=4d951911-3e7e-4ae6-b059-a2e79ed87041&displayLang=en")

I was able to install it successfully but when I try to save a document as PDF, I get the following error: "The program WINWORD.EXE has encountered a serious problem and needs to close. We are sorry ..."

I'm using wine-1.1.29.
Thanks!

---

### Post by Dangger on 2009-09-08
I only installed Word, PP and Excel and the three seem to work well. I haven't tried them extensively but seem ok. 

Thanks for the info and the tutorial :D

---

### Post by zipperback on 2009-09-08
Why bother going through all this trouble when you could simply use Open Office which is open source, runs on multiple platforms, and can read and write .doc files if thats what you want.

Is there some specific feature that MS Office 2007 has that you absolutely must have that Open Office doesn't?

- zipperback
:popcorn:

---

### Post by bryantw on 2009-09-08
> **jhoeijao said:**
> Thanks for the updates.

About your problem in running PowerPoint try Step G. I am assuming that you've installed winetricks already.

Your welcome :)
Actually I have not installed winetricks. Should i do that before going to Step G?

---

### Post by bryantw on 2009-09-08
> **zipperback said:**
> Why bother going through all this trouble when you could simply use Open Office which is open source, runs on multiple platforms, and can read and write .doc files if thats what you want.

Is there some specific feature that MS Office 2007 has that you absolutely must have that Open Office doesn't?

- zipperback
:popcorn:

I cant speak for others but in my case i have invested a lot of time into learning the MSOffice suite. and it would be kinda counter productive for me to re-learn a whole new suite just because. Now if it wasn't possible to use MSOffice, then i wouldn't much other choice other than to learn it out of necessity, or boot back into windows. For a quick word doc OpenOffice is a fine choice for me, but i know all the ins and outs of MSOffice, it just makes things easier to use what i know best.

---

### Post by jhoeijao on 2009-09-09
> **bryantw said:**
> Your welcome :)
Actually I have not installed winetricks. Should i do that before going to Step G?

Yup, you have to remove the overrides that you have made(if there's any) before doing Step G.

---

### Post by jhoeijao on 2009-09-09
> **eugen_nicoara said:**
> Hi,
There is a nice MS Office Add-in called "Microsoft Save as PDF or XPS" avaialable here: [http://www.microsoft.com/downloads/details.aspx?FamilyID=4d951911-3e7e-4ae6-b059-a2e79ed87041&displayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=4d951911-3e7e-4ae6-b059-a2e79ed87041&displayLang=en)

I was able to install it successfully but when I try to save a document as PDF, I get the following error: "The program WINWORD.EXE has encountered a serious problem and needs to close. We are sorry ..."

I'm using wine-1.1.29.
Thanks!

I haven't tried that yet but if I find a fix I'll update you.

---

### Post by jhoeijao on 2009-09-09
> **Dangger said:**
> I only installed Word, PP and Excel and the three seem to work well. I haven't tried them extensively but seem ok. 

Thanks for the info and the tutorial :D

Let me know if there's a problem because I am trying to enumerate common problems and solutions on this guide to improve it and make a detailed guide.

---

### Post by zipperback on 2009-09-09
> **bryantw said:**
> I cant speak for others but in my case i have invested a lot of time into learning the MSOffice suite. and it would be kinda counter productive for me to re-learn a whole new suite just because. Now if it wasn't possible to use MSOffice, then i wouldn't much other choice other than to learn it out of necessity, or boot back into windows. For a quick word doc OpenOffice is a fine choice for me, but i know all the ins and outs of MSOffice, it just makes things easier to use what i know best.


If you know MS Office Word pretty well, then you would probably find the transition from MS Office to OpenOffice a pretty easy change. I used MS Office for years and years, and the change over to OpenOffice was a really smooth one for me.

Its worth taking a look at. :)

- zipperback
:popcorn:

---

### Post by nderic77 on 2009-09-11
> **zipperback said:**
> Why bother going through all this trouble when you could simply use Open Office which is open source, runs on multiple platforms, and can read and write .doc files if thats what you want.

Is there some specific feature that MS Office 2007 has that you absolutely must have that Open Office doesn't?

- zipperback
:popcorn:

Yes.
Visio.
MS Project.

There are linux-based "alternatives", but they will not open visio or project files.

---

### Post by nderic77 on 2009-09-11
I was able to go through the setup program, BUT when I tried to enter the license code, the field would not let me enter any text. Whats up with that? The programs still installed, but they will not be very useful unless I am able to enter the license code.

Ubuntu 9.04, 64-bit
Wine 1.1.29 (64-bit)
MS Office 2007

---

### Post by bryantw on 2009-09-11
> **jhoeijao said:**
> Yup, you have to remove the overrides that you have made(if there's any) before doing Step G.
thank you very much! powerpoint now opens it seems to be running acceptably.  im not sure if there is an easy solution but when i drag to make a selection window the slides go totally black. if thats just how it is, then thats fine. again thank you very much

---

### Post by Demon- on 2009-09-15
> **Demon- said:**
> Thank you for this guide, I followed it to the letter and everythings works fine. Just one question though, whenever I open or save a file, there's also a .lnk file that gets created with the same name as my documents. Do you know how to fix this ?

Any ideas ?

---

### Post by Leighman on 2009-09-15
Anyone had any luck installing SP2?

---

### Post by jhoeijao on 2009-09-16
> **Demon- said:**
> Any ideas ?

I haven't experience that yet. So I can't give a fix on that.

Uhm, what wine version are you using? What version of MSOffice 2007?   

> **Leighman said:**
> Anyone had any luck installing SP2?

I wanted to try SP2 but I don't have one.

---

### Post by Leighman on 2009-09-17
I just downloaded it from the Windows updates page or whatever.
Separate installer to update to SP2

---

### Post by freeztar on 2009-09-18
FWIW, this did not work for me in Jaunty using wine 1.1.29. Using 1.1.24 did the trick though.

Thanks for the tutorial! :)

---

### Post by rindi on 2009-09-23
Outlook is the only reason for having Office on a Linux Box, but also I haven't been able to get it to run, It starts, then I get a box saying "Cannot start Microsoft Office Outlook. Cannot open the Outlook window.". There is just an OK in that box which closes everything Outlook if you press it.

---

### Post by JV.com on 2009-09-23
Today i got MS Office 2007 working by using wine 1.1.29

by doing this:

1. totally remove wine.
2. install newest version of wine available.
3. install cabextracter and winetricks before the installation of office 2007.
4. install office 2007.
5. configure wine dll overrides.

i hope this will help someone.

Greetings

Jelte.

---

### Post by PrototypeAlex on 2009-10-10
Works perfectly with Jaunty 9.04 and Wine 1.1.29 i386. 

Thanks Heaps :P

---

### Post by Naren-Karma on 2009-10-11
Wine version 1.1.30 in Ubuntu 9.04 gives support all application of MS office 2007  except its mail client Microsoft Outlook 2007.
I configured Outlook through wizard but final window comes with pop up " Cannot start Microsoft Office Outlook. Cannot Open the Outlook window."
How can we solve this trouble. Please help on this because I want to use this mail client and I like its GUI.
thanks 
Naren

---

### Post by modus_kls on 2009-10-20
I just install office 2007 but I get this error when I trying to open excel and the others office file.


[IMG]http://img5.imageshack.us/img5/6863/screenshotcl.png[/IMG]

Anybody can help me.:(

---

### Post by jhoeijao on 2009-10-22
> **modus_kls said:**
> I just install office 2007 but I get this error when I trying to open excel and the others office file.

Anybody can help me.:(

How did you open your file?

By open icon?

By right clicking and through open with wine?

---

### Post by modus_kls on 2009-10-23
> **jhoeijao said:**
> How did you open your file?

By open icon?

By right clicking and through open with wine?


By open icon. 

But its works when i open the file by right clicking and through open with wine.

Thanks. :)

---

### Post by msit.ce on 2009-11-03
Hi, I am also trying to install ms office 2007. But whaen I want to install    	 	 	 	 	 	  **cabextract**, it shows below massage:
>    	 	 	 	 	 	  shams@shams-desktop:~$ sudo apt-get install cabextract 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 cabextract is already the newest version. 
 The following packages were automatically installed and are no longer required: 
   linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic libswfdec-0.8-0 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
 2 not fully installed or removed. 
 After this operation, 0B of additional disk space will be used. 
 Setting up ttf-mscorefonts-installer (2.6) ... 
  
 These fonts were provided by Microsoft "in the interest of cross- 
 platform compatibility".  This is no longer the case, but they are 
 still available from third parties. 
  
 You are free to download these fonts and use them for your own use, 
 but you may not redistribute them in modified form, including changes 
 to the file name or packaging format. 
  
 --2009-11-04 02:07:40--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving surfnet.dl.sourceforge.net... 130.59.138.21 
 Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following] 
 --2009-11-04 02:07:41--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:07:42--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:07:47--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving mesh.dl.sourceforge.net... 213.203.218.122 
 Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following] 
 --2009-11-04 02:07:48--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:07:49--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:07:54--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving dfn.dl.sourceforge.net... 194.95.236.6 
 Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following] 
 --2009-11-04 02:07:54--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:07:56--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:01--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving heanet.dl.sourceforge.net... 193.1.193.66 
 Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:02--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:03--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:08--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving jaist.dl.sourceforge.net... 150.65.7.130 
 Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:13--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:18--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1 
 Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:19--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:20--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:25--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving internode.dl.sourceforge.net... 150.101.135.12 
 Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:26--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:27--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:32--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving mesh.dl.sourceforge.net... 213.203.218.122 
 Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:33--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:34--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:39--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving voxel.dl.sourceforge.net... 208.122.31.3, 208.122.31.12, 208.122.31.13, ... 
 Connecting to voxel.dl.sourceforge.net|208.122.31.3|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:45--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:46--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:51--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving kent.dl.sourceforge.net... 212.219.56.167 
 Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:51--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:52--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:08:57--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving internap.dl.sourceforge.net... 64.7.222.131 
 Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected. 
 HTTP request sent, awaiting response... 302 Moved Temporarily 
 Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) [following] 
 --2009-11-04 02:08:58--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) 
 Resolving prdownloads.sourceforge.net... 216.34.181.59 
 Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:08:59--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 --2009-11-04 02:09:04--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
 Resolving switch.dl.sourceforge.net... 130.59.138.21 
 Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following] 
 --2009-11-04 02:09:05--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) 
 Resolving downloads.sourceforge.net... 216.34.181.59 
 Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
 HTTP request sent, awaiting response... 302 Found 
 Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
 --2009-11-04 02:09:06--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
 Resolving nchc.dl.sourceforge.net... 211.79.60.17 
 Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out. 
 Giving up. 
  
 andale32.exe: No such file or directory 
  
 All done, errors in processing 1 file(s) 
 dpkg: error processing ttf-mscorefonts-installer (--configure): 
  subprocess post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of msttcorefonts: 
  msttcorefonts depends on ttf-mscorefonts-installer; however: 
   Package ttf-mscorefonts-installer is not configured yet. 
 dpkg: error processing msttcorefonts (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because the error message indicates its a followup error from a previous failure. 
                                                                                                           Errors were encountered while processing: 
  ttf-mscorefonts-installer 
  msttcorefonts 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
  shams@shams-desktop:~$
So, what can I do now?

---

### Post by jamie_townsend on 2009-11-05
> **Naren-Karma said:**
> Wine version 1.1.30 in Ubuntu 9.04 gives support all application of MS office 2007  except its mail client Microsoft Outlook 2007.
I configured Outlook through wizard but final window comes with pop up " Cannot start Microsoft Office Outlook. Cannot Open the Outlook window."
How can we solve this trouble. Please help on this because I want to use this mail client and I like its GUI.
thanks 
Naren

I have exactly the same issue with Ubuntu 9.10, Wine 1.1.3.  Any help would be greatly appreciated.

--
Jamie

---

### Post by Ben_T_B on 2009-11-06
I would like to add that when trying to install Office 07 under Wine 1.1.32 it would continually hang around half way through the install.

I followed your guide on uninstalling WINE and deleting the directory, wanted to install .14 but it's no longer available on the website. So I installed .24 and the install went without a hitch.

Thank you very much.

---

### Post by dxxvi on 2009-11-06
> **Ben_T_B said:**
> So I installed .24 and the install went without a hitch.Thanks for sharing this valuable information. I'll try wine 1.1.24 and office 2007 on karmic tonight.

---

### Post by lostburner on 2009-11-10
Hello, 

great work, I installed Office 2007 and it works, BUT

I'm not able to enter the product key! The input box isn't working.

What do I have?
Ubuntu 9.1
followed the installation guide 
original Office CD
Wine 1.1.24

I would be very happy if anybody could help me, because I only have 22 program starts left

Greeting lost burner

---

### Post by jhoeijao on 2009-11-10
> **jamie_townsend said:**
> I have exactly the same issue with Ubuntu 9.10, Wine 1.1.3.  Any help would be greatly appreciated.

--
Jamie

Sad to inform you that Microsoft Outlook is not usable under wine. Check [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7533](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7533) for details.

---

### Post by jhoeijao on 2009-11-10
> **msit.ce said:**
> Hi, I am also trying to install ms office 2007. But whaen I want to install                                   **cabextract**, it shows below massage:

So, what can I do now?

I encountered this problem before, so based on my experience , I suggest that you run all upgrades in Synaptic Package Manager first (System>Administration>Synaptic Package Manager) before you start using the guide.

Hope that helps!

---

### Post by jhoeijao on 2009-11-10
> **lostburner said:**
> Hello, 

great work, I installed Office 2007 and it works, BUT

I'm not able to enter the product key! The input box isn't working.

What do I have?
Ubuntu 9.1
followed the installation guide 
original Office CD
Wine 1.1.24

I would be very happy if anybody could help me, because I only have 22 program starts left

Greeting lost burner

Try the solution from this thread [http://ubuntuforums.org/showthread.php?t=1283792&highlight=NightMKoder+product+key&page=2](http://ubuntuforums.org/showthread.php?t=1283792&highlight=NightMKoder+product+key&page=2) comment #14.

It worked on him/her so i hope it will also work on you.

---

### Post by ganeshmallyap on 2009-11-10
Hi,

I have Karmic AMD64 installation and my WINE version is 1.0.1.  I added the entry in third party software sources, reloaded the package list, then ran update manager and I could see two packages - wine & wine-gecko.  But there was a message box saying only partial update possible.  Not sure what is going on.  

I also want to know can I install Office 2007 32 bits on my system?

Thanks in advance

---

### Post by lostburner on 2009-11-10
> **jhoeijao said:**
> Try the solution from this thread [http://ubuntuforums.org/showthread.php?t=1283792&highlight=NightMKoder+product+key&page=2](http://ubuntuforums.org/showthread.php?t=1283792&highlight=NightMKoder+product+key&page=2) comment #14.

It worked on him/her so i hope it will also work on you.

Thank you very much!
Also worked for me :)

Everthing is working fine

Thanks once again for the great work you're doing here!

---

### Post by cairo2929 on 2009-11-11
fuuuhhh....so glad cause it works on my ubuntu karmic koala...
Thanks, my dear...
;););)

---

### Post by roystreet on 2009-11-23
jhoellhao: 
...I want to thank you very much for helping all of us get office installed!  It is amazing how fast it installed - In fact I'm worried everything didn't get installed because it went so fast.  It took much more time to install on windows.  I had used office on ubuntu 9.04 & it worked fine.
...I just installed 9.1.  It would always stall on install or encounter some error when trying to put office on it.  I followed your directions & got a different version of WINE & now it works.  Why doesn't the version that comes with 9.1 work?  I haven't tried office very much on my fresh install -considering I just did it a few minutes ago.  Question - Am I every going to be able to have my fonts I've used in the past?  I do have a copy of windows still, but so far the fonts in word don't look right.

Thanks,
  ~roystreet

---

### Post by Emeris on 2009-11-24
Hey everybody,

I'm actually on Karmik Koala (9.10) and I'm trying for days to install Office 2007.
I tried with almost each version of wine, following the tutorials on every forum taking care of this subject. And finally... It still doesn't work... :(

Could someone do a brief review (a kind of feedback) of every usefull comment that have been made on this forum, to install Office 2007 on Karmik Koala?

And especially answer thoses questions :

[LIST=1]
[*]What version of Wine should we use on Karmik Koala, in order to make Office 2007 work?
[*]How to remove correctly wine (before installing the new, correct version)? Because following the tutorial I removed my former version of Wine, and it now shows me (when I try to install Office 2007) :
wine client error:0: version mismatch 393/386.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
[/LIST]
A step by step procedure would be particlularly welcome.

Thank you in advance

---

### Post by haribol707 on 2009-12-18
Couple of doubts

1. In winecfg -> Applications -> windows version, which  version do I need to select? Vista or XP? What difference does it make?

2. Office Updates - Do I need to enable/download-install office updates? And if so, is that supported by wine? Is there additional tweaking required to install updates or I can totally ignore it?

3. Office installs proprietary font packages (?) with the setup. Can these fonts be used on Ubuntu? (Appearance->Fonts?). Is there a way to use these fonts or do we get them anyways with msttcorefonts?
 
4. I have already installed Office on my ubuntu box. I just read somewhere about Add-on/plugin to save Docs as PDF. Can I still install it from CD? Is there any documentation for the installation? (I read in Office installation doc that I cannot change customization once selected). Otherwise, I use this other tool on Windows called CutePDF which installs as a printer device (?) in Windows. Can I install it here? Has anyone done that? Bottomline, I would love to have a simple option to save my doc as PDF from word without having to open another application just to achieve it. :)

Any help would be greatly appreciated!

---

### Post by Pooven on 2009-12-19
I've also using Karmic Koala and I have wine 1.1.13 installed and running Office 2007. Incidentally, if you install PlayOnLinux ```
sudo apt-get install playonlinux
```it will set up a working version of Office for you rather easily: downloading and installing the various base fonts and required libraries.

Office updates have not worked for me - office updates are made possible via Windows Updates which, at least on my computer, does not come with wine (I don't think it can be installed on wine?).

The *Save as PDF* add on does not work. Unfortunately the built in option that comes with Ubuntu to print to a PDF or PS, is not available to Office.

---

### Post by fanglinyong on 2009-12-19
good ,thanks very much!!!

---

### Post by haribol707 on 2009-12-19
Thanks! That answered my questions on updates and pdf. I also happened to browse through wine portal and somewhere it was mentioned that they are still working on the update stuff. So, it is official that it does not work as yet (unless there are workarounds?). Saving as PDF is something I use heavily and would love to have it enabled somehow. Are there any tweaks known to perform this?

---

### Post by haribol707 on 2009-12-19
And I think this is an excellent article to help one through installation and troubleshooting. I had problems with MS Access and following this instruction helped!

[http://wiki.archlinux.org/index.php/Microsoft_Office_2007]("http://wiki.archlinux.org/index.php/Microsoft_Office_2007")

---

### Post by Ozitraveller on 2009-12-23
I'm using version 29 of wine, does upgrading to the latest work?

---

### Post by resisthegemony on 2010-01-04
Absolutely superb! I did have one little problem, though--I can't seem to open .doc or .docx files on my external hard drive using Word 2007 through WINE. Is there something I can do (winetricks, configuration, anything) to make this work? Thanks for all of the great work and clear directions!

---

### Post by phillychease on 2010-01-04
thanks i have office 2007 running but whenever i save a file and close ms word and open the file again, it says that the file cannot be found.

---

### Post by metalmaniac248 on 2010-02-13
just as the office installer starts i get a message saying that i need Microsoft installer 3.1

any solutions to this?

---

### Post by Jugantor on 2010-02-13
superb!! works perfect.

---

### Post by jfursathimn on 2010-02-22
> **Lockheed said:**
> I am using 1.1.25 on jaunty and install went just fine. Word also runs BUT there are two problems.

1. Whenever I try run doc file from nautilus, Word opens but complaints it cannot find the file and then that it has no permission to access it.
Document opens just fine if I run word and then open it from within it.


I just followed your instructions but used wine 1.1.38 on 9.04 with Office Small Buisness 2007. Almost everything worked beautifully! I checked functionality before step F. Everything worked fine except Power Point. After completing the rest of the steps PPT did as well. (Opening, saving, etc)

Except: I have the same problem as Lockheed, with opening files from outside Word. Any fixes on this yet?

Also: I installed ttf-mscorefonts-installer from Synaptic and they look great!

-Cheers

---

### Post by FF3266 on 2010-02-27
hi, thanks a lot for Your support,

i already followed Your steps and already did it before, and the MS Office 2007, but when trying to click on WORD or OUTLOOK, it gives me the "loading clock" then nothing opens, i rebooted many times reinstalled again and did everything but the same thing happens even after updating the software from update manager.

i use Zorin (Ubuntu)
Kernal .19 (the latest)
Wine 1.1.14

can You help me please?
Thanks.

---

### Post by gohanssjn on 2010-05-03
Yeah, I followed this, and I just get a "Program Error" when I try to start up Word.

Any ideas?

---

### Post by qwerty57 on 2010-05-04
I installed Wine & MS Office last night with partial success.  I could open and edit Docs and Spreadsheets, but not Powerpoints.  This morning I followed the steps from the first post of this thread and now Word, Excel and Powerpoint all work perfectly!):P  Thank you very much!

The only remaining problem is MS Picture Manager.  I happen to like this ap more than just about any other picture viewer/editor!  Unfortunately, it opens, but it will only display Icons, not the actual pictures.  Any ideas?

I have version 1.1.43 of Wine, Office 2007 and Jaunty.

Thanks.

---

### Post by Mafuzzer on 2010-05-05
Thanks for the guide :) Will be using this as soon as I get home xD

---

### Post by N_L on 2010-05-13
Installed office and working but I forgot to install 1 thing. Now when I run setup I cannon enter serial key, that area is white but cannot be pressed and when I press continue it offers trial and later error..
Any idea?

---

### Post by Ozitraveller on 2010-05-13
> **N_L said:**
> Installed office and working but I forgot to install 1 thing. Now when I run setup I cannon enter serial key, that area is white but cannot be pressed and when I press continue it offers trial and later error..
Any idea?

I had a similar problem and I uninstalled wine deleted .wine folder, then re-installed wine then office.

---

### Post by qwerty57 on 2010-05-14
I've installed wine/office2007 on both my desktop and my laptop.  It works perfectly on my desktop, but I can't register the office 2007 on my laptop.  I'll try uninstalling and reinstalling.

My laptop doesn't have a CD player, so I'm installing Office from a Thumb drive.  Could that be the reason that I'm having these problems?

---

### Post by Ozitraveller on 2010-05-14
> **qwerty57 said:**
> I've installed wine/office2007 on both my desktop and my laptop.  It works perfectly on my desktop, but I can't register the office 2007 on my laptop.  I'll try uninstalling and reinstalling.

My laptop doesn't have a CD player, so I'm installing Office from a Thumb drive.  Could that be the reason that I'm having these problems?

Is it a real copy of office? If it is then probably.

---

### Post by lvalen18 on 2010-05-14
So would it be a good idea to download the last Office 2007 Service Pack and install it?

---

### Post by Ozitraveller on 2010-05-16
If it's not installed properly then you won't be able to install the SP.

---

### Post by rainbowagent7 on 2010-06-01
Thanks a million, you saved me a mountain of headaches in school. Even though I feel I've tainted myself and my computer with M$ garbage. The ONLY reason I wanted Office '07 is for the grammar check, nothing more. As soon as Oo implements one I'll quickly rid my computer of Office, do a fresh install with a new hard drive, and curl up in the shower crying (I'll probably thoroughly wash my computer too, just to be sure!). Anyways, thanks for the great info, peace.

---

### Post by kinsago on 2010-06-01
Hi.

Thought I'd managed to fix publisher on 2007 by using an older version of wine for that and an up-to-date version for everything else - sadly this is not to be and it crashes trying to save files. Does anyone have a solution to this? Publisher is the only reason for office as their doesn't seem to be anything comparable. I know about Scribus but it's not as user-friendly nor does it have the range of templates that I use on a regular basis. For now I'm using VirtualBox but it's not as efficient.

Cheers

---

### Post by Petridish on 2010-06-08
:confused: I'll ask forgiveness in advance for having posted this plea for help in two threads. I wasn't sure which thread was actually being paid attention to.

Alright, I'm about wine-guided to death, after a week of various flavors of failure, I'm begging for mercy and assistance.

The current situation: Ubuntu 8.04, Wine 1..1..24 on an Inspiron mini 10v.

I previously had the trial version of Office 2007 Home and Student successfully installed via wine 1.1.16, but I could not activate with my key (yes it's valid). I'd get to the activation wizard, click "convert" and ... crickets.

So I started over as best I could, not knowing how to undo what I'd done. Not properly, anyway.

Installed wine 1.1.24 and downloaded the software from the Install MS Office website. Moved the .exe into the system32 folder, because that's where Wine insists on looking for it. Extracts files, then asks for the product key, but won't let me type anything. 

For what it's worth, before I moved "up" to .24, I managed to get past the product key entry, only to have the install fail shortly thereafter.

Am I cursed?
The DLL overrides I have are (as they appear in the cfg window):
*gdiplus (native)
*msi (native, builtin)
*msiexec.exe (native, builtin)
*msxml3 (native, builtin)
*msxml4 (native, builtin)
riched20 (native)
usp10 (native)

I deleted .wine and tried the install again, to no avail.

Please help!
If you live in the Louisville area, I'd be willing to <strike>throw</strike> hand the machine over to you to just Make It Work.

---

### Post by jhoeijao on 2010-07-06
> **Petridish said:**
> :confused: I'll ask forgiveness in advance for having posted this plea for help in two threads. I wasn't sure which thread was actually being paid attention to.

Alright, I'm about wine-guided to death, after a week of various flavors of failure, I'm begging for mercy and assistance.

The current situation: Ubuntu 8.04, Wine 1..1..24 on an Inspiron mini 10v.

I previously had the trial version of Office 2007 Home and Student successfully installed via wine 1.1.16, but I could not activate with my key (yes it's valid). I'd get to the activation wizard, click "convert" and ... crickets.

So I started over as best I could, not knowing how to undo what I'd done. Not properly, anyway.

Installed wine 1.1.24 and downloaded the software from the Install MS Office website. Moved the .exe into the system32 folder, because that's where Wine insists on looking for it. Extracts files, then asks for the product key, but won't let me type anything. 

For what it's worth, before I moved "up" to .24, I managed to get past the product key entry, only to have the install fail shortly thereafter.

Am I cursed?
The DLL overrides I have are (as they appear in the cfg window):
*gdiplus (native)
*msi (native, builtin)
*msiexec.exe (native, builtin)
*msxml3 (native, builtin)
*msxml4 (native, builtin)
riched20 (native)
usp10 (native)

I deleted .wine and tried the install again, to no avail.

Please help!
If you live in the Louisville area, I'd be willing to <strike>throw</strike> hand the machine over to you to just Make It Work.


Sorry guys for the late response.

To Petridish,

Start the installation again using Step B, C, and D (use the latest wine version 1.1.38 ). Type "winecfg" on your terminal make sure to remove all your overrides because this causes your problem (you can't type your product key) then follow steps E to I.

Note: Use "riched20" set to native windows and "usp10" overrides only.

---

### Post by goltoof on 2010-07-12
I followed the instructions exactly, (this is only for Visio 2007 Pro, not the whole Office Suite). Visio installs/opens/activates fine, but I can't get images or shapes to load.   There is no shape library.   I can only do lines and text. 

I'm using Lucid Lynx 10.04.

Please help, I'm so close!!

---

### Post by Ozitraveller on 2010-07-12
MS Visio 2007 in Wine
[http://ubuntuforums.org/showthread.php?t=1243858](http://ubuntuforums.org/showthread.php?t=1243858)

---

### Post by Another Monkey on 2010-07-20
Can't get Office to install.  I am using WINE 1.2 (latest from LaunchPad PPA) on Lucid 10.04, attempting to install MS Office 2007 Enterprise and have followed the steps in the first post.

The installer crashes after a few seconds and I see this in the terminal.
```
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0x4
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x28fc728,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x1c3670,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:NdrCorrelationInitialize (0x27fd480, 0x27fd080, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ole:NdrCorrelationFree (0x27fd480): stub
fixme:ole:NdrCorrelationInitialize (0x27fd440, 0x27fd040, 1024, 0x0): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
fixme:ole:NdrCorrelationInitialize (0x27fd3e0, 0x27fcfe0, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x27fd3c0, 0x27fcfc0, 1024, 0x0): stub
fixme:rpc:handle_bind_error unexpected status value 1765
err:rpc:RpcAssoc_BindConnection rejected bind for reason 0
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:netapi32:NetGetJoinInformation Stub (null) 0x32f024 0x32f018
```

I know WINE itself runs OK as Spotify works a treat.  Does anyone know how to get Office installed and running on Lucid?

Edit: Urf.  Just noticed that this is only for 1.1.12-16!  Idiot that I am.  Seeing as how the installer is rated as "garbage" on WineHQ, I think I just give up and assume that you cannot get Office to run under WINE.  Life is too short.

---

### Post by jhoeijao on 2010-07-21
> **Another Monkey said:**
> Can't get Office to install.  I am using WINE 1.2 (latest from LaunchPad PPA) on Lucid 10.04, attempting to install MS Office 2007 Enterprise and have followed the steps in the first post.

The installer crashes after a few seconds and I see this in the terminal.
```
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0x4
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x28fc728,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x1c3670,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:NdrCorrelationInitialize (0x27fd480, 0x27fd080, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ole:NdrCorrelationFree (0x27fd480): stub
fixme:ole:NdrCorrelationInitialize (0x27fd440, 0x27fd040, 1024, 0x0): stub
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
fixme:ole:NdrCorrelationInitialize (0x27fd3e0, 0x27fcfe0, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x27fd3c0, 0x27fcfc0, 1024, 0x0): stub
fixme:rpc:handle_bind_error unexpected status value 1765
err:rpc:RpcAssoc_BindConnection rejected bind for reason 0
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:netapi32:NetGetJoinInformation Stub (null) 0x32f024 0x32f018
```

I know WINE itself runs OK as Spotify works a treat.  Does anyone know how to get Office installed and running on Lucid?

Edit: Urf.  Just noticed that this is only for 1.1.12-16!  Idiot that I am.  Seeing as how the installer is rated as "garbage" on WineHQ, I think I just give up and assume that you cannot get Office to run under WINE.  Life is too short.


I'm using Lucid now and the the guide still works but not on WINE 1.2 but with WINE 1.1.42.

---

### Post by Another Monkey on 2010-08-06
> **jhoeijao said:**
> I'm using Lucid now and the the guide still works but not on WINE 1.2 but with WINE 1.1.42.
Ah, that's good to know.  I might downgrade, but it would be nice if the WINE team could fix the regression.

---

### Post by jhoeijao on 2010-08-06
> **Another Monkey said:**
> Ah, that's good to know.  I might downgrade, but it would be nice if the WINE team could fix the regression.

I've downloaded the latest WINE 1.2 and i'ts working fine.

What guide are you using?

---

### Post by jhoeijao on 2010-08-06
> **jhoeijao said:**
> I've downloaded the latest WINE 1.2 and i'ts working fine.

What guide are you using?

I know that my post is conflicting with my #192 comment but I did a clean installation after that and installed MSOfiice2007 through WINE 1.2 and everything works fine.

---

### Post by jerome_rajan on 2010-11-30
Wowwwy....this is an awesome tutorial man!!! Installed it within mins!!! The only thing that was holding me back from swiping out Windows was MS Office! And now , I hv Office on my Maverick!! Bye bye Windows!

---

### Post by jhoeijao on 2010-12-06
> **jerome_rajan said:**
> Wowwwy....this is an awesome tutorial man!!! Installed it within mins!!! The only thing that was holding me back from swiping out Windows was MS Office! And now , I hv Office on my Maverick!! Bye bye Windows!

I'm glad to help you. It's been a long time not visiting this thread. Too busy with my work but it's worth coming back when I know the guide is still helping others.

By the way I was able to install MS OFFICE 2007 in my LUCID Puppy Linux OS here's a screen shot:

---

### Post by amitash on 2011-01-16
In ubuntu 10.10 with Wine 1.2, I was able to install MS Office 2007 (Custom Install - Only Excel 2007). But on Clicking in the menu, I get the excel splash screen which never goes away. :confused:

Edit: I tried to leave it in the background, but the splash screen is on top of every program and it is a nuisance.

Help Required! :(

---

### Post by jhoeijao on 2011-01-16
> **amitash said:**
> In ubuntu 10.10 with Wine 1.2, I was able to install MS Office 2007 (Custom Install - Only Excel 2007). But on Clicking in the menu, I get the excel splash screen which never goes away. :confused:

Edit: I tried to leave it in the background, but the splash screen is on top of every program and it is a nuisance.

Help Required! :(

Try to reinstall MS Office but this time include MS Word, Start with step C. Now here's the trick open Microsoft word first before opening MS Excel so that you can click on the two flash windows that will appear.

---

### Post by amitash on 2011-01-16
> **jhoeijao said:**
> Try to reinstall MS Office but this time include MS Word, Start with step C. Now here's the trick open Microsoft word first before opening MS Excel so that you can click on the two flash windows that will appear.
jhoeijao, you are awesome. Thanks for that tip. It worked seamlessly. Just followed your instructions. First opened word, then excel and its working fine now. Thanks a bunch.

---

### Post by safarin on 2011-03-29
Cool... Thank you. My one week problem solved! :)

---

### Post by jhoeijao on 2011-03-31
> **safarin said:**
> Cool... Thank you. My one week problem solved! :)

You're welcome.

It's good that you took only a week to solve your problem if my memory serves me right it took me a month and a half to solve my problem before and this guide is the result of that one and a half month of researching.

---

### Post by BenTX on 2011-06-27
Hello **jhoeijao**, I followed your guide, and it worked flawlessly, thanks for posting this!

Here are a few questions I have as I compare this installation to a similar one on my Windows box:
[LIST=1]
[*]I would like to download/install Office 2007 Service Pack 2 (or the latest SP), however after researching the forums, I have not found a solution on how to do this. Let me know if you can help.
[*]I had the option of saving a document as a PDF from within the menu in Word 2007, now, in its place I see "Find add-ins for other file formats". How do I get this option back? or is this related to the lack of Office SP3?
[*]When I open a Word document originally composed in Windows, text that was originally bolded, does not "appear" bolded on my Linux box. However, when I select the text, the toolbar up top indicates it **IS** bolded. How do I fix this?
[*]Again, when I open a 15 page Word doc originally composed in Windows, the formatting of the whole document is different, i.e. placement of text, pictures, tables, etc are in different areas of the document. How do I get my Word doc to "look" the same as it did on my Windows box? or is this possible?
[/LIST]

Thanks again,
Ben

---

