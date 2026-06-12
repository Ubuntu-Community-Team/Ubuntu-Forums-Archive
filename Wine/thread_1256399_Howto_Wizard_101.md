---
title: "Howto Wizard 101"
date: 2009-09-02
forum: Wine
---

### Post by regor210 on 2009-09-02
**Wizard 101** is a property game that allows limited access for free.  

Wizard101 turned 1 year old today so I thought I might revisit how to install the game using Wine.

**Note. Ubuntu Administrators do not recommend installing software not in the Ubuntu repositories.**  

[https://www.wizard101.com/home2/game/page_8ad6a4041b790501011b953e28160430](https://www.wizard101.com/home2/game/page_8ad6a4041b790501011b953e28160430)

**Update May 5,2011** Wine 1.2.2 & Wine 1.3.19 worked fine without any modification.

Assuming your computer has 3D drivers and Wine installed. 

**You  will  need the adobe flashplayer for  windows** to install the game. The easiest way I know to get it is to install Firefox for Windows.  Adobe will only allow Ubuntu Firefox to download the GNU/Linux version. Go to
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

Install Firefox for Windows. Start Firefox for Windows then ckick on this link 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

uncheck the Free McAfee scan box then click on the Agree and install now bar.
Its likely you will have to use the "Your download will start automatically.
If it does not start, _click here to download_"
Save the file. Now back in Ubuntu goto Places>Home Folder>Downloads and click on the  install_flash_player.exe icon to install it using wine.

After getting an account and downloading the game, the game sould install by simply clicking the icon downloaded to your desk top.
Note. The 1st time you start the game its best to let the game finish patching (The little arrow going around in a circle in the upper left hand corner).  Or the patcher could get bugged and you will need to reinstall the game. 

After  installing the game try playing and if there is a problem? Here's the solution.

Note. The links on the login page will not work but all these links can be found at
[https://www.wizard101.com/game](https://www.wizard101.com/game)

**False starts **
Sometime when I start the game It hangs or freezes. This happens mostly when downloading or patching the game. Just restart wine as needed and you will get on. This may sound bad but with GNU/Linux Ubuntu I have never gone link dead in a match/battle like the Windows guys are always complaining about. They say things like "My stinking computer crashed again!" Well boys its not your computer thats crashing its your operating system. 
Note. You must restart Wine, not just the game in Wine as just restarting the game is not likely to help.

Update Oct 17, 2009
**If you can't see numbers in the SHOP icon.**
Yesterday Wizard 101 received a huge patch! There is now a SHOP icon in the upper left hand corner. I could not see the numbers so I used this HowTo to fix it.
Note. as of yet I have not found a way to use any wine version over 1.1.28 to run Wizard 101.  Winetricks recommends updating to the latest version of wine, I do not as it is likely that it will not work.  
Goto   
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
and right click on &#65279; [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks). link and click on "save link as..." and save it to your desktop. 
Right click on the winetricks icon on your desktop and click properties>Permissions and check the Allow executing file as program box.
Now left click on the winetricks icon and scroll down to allfonts and check the box. click ok and wait a good minuet or two.
Note. installing stuff from winetricks willy nilly is not a good idea.
You should be good to go.

**If your avatar or person is invisible.**
In Ubuntu goto Wine> Wine Configure> Graphics> (uncheck) Allow Pixel Shader.
Note. With the introduction grizzleheim there are a few items that Wine can not render properly without the pixel shader. IF you encounter one just click on another item and all will return to normal.   This has not been a big problem for me.

**If the game will not install or start.**
 Note on one of my computers with Play On Linux or POL for short conflicted with my wizard 101 installation. I removed POL and reinstalled Wine and all was fine.

If you get an error message like (improper use of a c library ) try.

In Ubuntu go to Wine> Wine Configure> and for Windows Version select (Windows 98 )
Install the game. Then after you have installed the game return your Windows Version to XP.

**If you get a blank a screen.**
I had this issue with my wide screen  
 Go to Wine configuration Graphics> (check) Emulate a virtual desktop Desktop size 800x600.
log into the game using your password, When you see your avatar click Options and select the screen resolution that fits your computer monitor. Next log out of the game. Then Goto Wine configuration Graphics> (uncheck) Emulate a virtual desktop.

**If you can not see your mouse pointer. **
Wait for the game to start then go to
options>click on the red gear(upper left)>Hardware Cursor {OFF} this can be a bit difficult if you can not see your pointer but doable. Now restart the game.

Note. My &#65279;Pentium 4 using an old ATI 256mb Radeon card played laggy. I placed an old Nvidia 128mb card in it and played much better. My newer computers running &#65279;64-bit processors do not lag. Running the same screen resolution as my Ubuntu desktop seem to give me the best performance.  
---------------------------------------------------------------------------------
**Update Mon Sep 7, 2009 Wine update 1.1.29 from **
[http://www.winehq.org/](http://www.winehq.org/)
has issues and causes the log in screen to blink on and off. 

**Update Thu oct 1,  2009** Wine 1.1.30 is out and is not working. 

**Update Thu oct 13,  2009** Wine 1.1.31 is out and is not working. 

**Update Oct 19, 2009**
Wine 1.1.31 can run Wizard 101 if you use WineTricks to install &#65279;Internet Explorer 6
1st. IE6 Is not secure and should not be used so I can't recommend this solution. Plus there is no performance boost in any way that I could see.  Best to use Wine 1.0.1 for now.

**Wine 1.0.1** in the Ubuntu repository's works just fine.

**Update oct 16, 2009 **
Big patch today lots of false starts. I had to restart Wine/Wizard 101 many times to get the patch. One of my computers seemed to be fished and kept taking me to an error page saying "Your parents may need to make changes to your system." I waited 10 minutes and tried again and got the rest of the patch.  All is up and working here.

If you get stuck and just can't get it you might try JabberwockX work around.

---

### Post by ChrisMoose on 2009-10-07
Ahhh... thanks for the fix! I had Wizard 101 working for a few months, but then a patch (either to Wine or W101, not sure which) killed it. Checking the "Emulate Virtual Desktop" option fixed it for me. 

Thanks!

---

### Post by JabberwockX on 2009-10-15
If anyone is having a problem with the patches downloading here is the fix I've had work: 


Navigate:     
Wine > Browse C:\ Drive > Program Files > Kingsisle Entertainment > PatchClient>BankA

Once there open the file named ' WizardLauncher.Log.txt '

Scroll to the bottom and read through for where the error occurs. It should say something like 

Unable to sendHTTP request (_ ...some randome URL...._)

From there just copy the URL and plug it into your favorite browser, download the file to your desktop and then drag and drop the file into:

C:\ Drive > Program Files > Kingsisle Entertainment > Data > GameData

...and there's your patch. 

Not the best, but it's a quick fix. 

Cheers.

---

### Post by solitaryr on 2009-12-14
I'd like to build on Jabberwock's comment.  Waiting 10 minutes between each update was driving me insane so, what I did was:

 tail -15 "!winepath/drive_c/Program Files/KingsIsle Entertainment/Wizard101/PatchClient/BankA/WizardLauncher.Log.txt" | grep versionllnw

This should return a single line like the following:

12/14/09 18:54:15 [ERRO] CORE_HTTP_FILE  KIHttpFileSession.cpp 0934 Inet recv failed ([http://versionllnw.us.wizard101.com/WizPatcher/LatestBuild/Data/GameData/Sound_Dialogue-WorldData.wad?v=F79E44A9](http://versionllnw.us.wizard101.com/WizPatcher/LatestBuild/Data/GameData/Sound_Dialogue-WorldData.wad?v=F79E44A9)).

Just copy the url between the parenthesis and paste it into your browser and save to the game data location.  Do this for each failed package...unfortunately, I had to keep retrying since it would only try one at a time.  Basically, lather, rinse, repeat for each one.

Note, I tried using wget but it didn't work for some reason.  I was going to try curl but haven't tried it yet.

---

### Post by solitaryr on 2009-12-16
OK...wget did work it just appended the version it was downloading as well.  Since I had to go through this so many times for the xmas update, I hacked a little script to make my life easier.  Adjust the paths to reflect your setup.

#!/bin/sh
debug=0

cdrive=~/.wine/drive_c

wlogpath="$cdrive/Program Files/KingsIsle Entertainment/Wizard101/PatchClient/BankA/WizardLauncher.Log.txt"
gpath="$cdrive/Program Files/KingsIsle Entertainment/Wizard101/Data/GameData"

urlstr=`tail -15 $wlogpath | grep versionllnw | cut -d \( -f2 | cut -d \) -f1`
fvname=`echo $urlstr | rev | cut -d / -f1 | rev`
fname=`echo $fvname | cut -d\? -f1`

if [ $debug -eq 1 ]; then
    echo "cd $gpath"
    echo "wget $urlstr"
    echo "mv $fvname $fname"
    exit 0
fi

cd $gpath
wget $urlstr
mv $fvname $fname

One last quick note:  The download tool seems to only hang on the .wad files for some reason.  The dlls and other files appear to come through just fine.

---

### Post by bullfrog55 on 2011-02-03
I failed at the 2nd hurdle. I downloaded firefox for  windows installer but when I try to install I get the error message: wine could not find L"C:\\windows\\system32\\Firefox.exe

---

### Post by cogadh on 2011-02-03
You're not running it from the correct location. Change directories to wherever you downloaded the installer, the "wine" the installer executable.

---

### Post by bullfrog55 on 2011-02-04
> **cogadh said:**
> You're not running it from the correct location. Change directories to wherever you downloaded the installer, the "wine" the installer executable.
Thanks Cogadh,
I did it on a terminal in the downloads directory and got the same message. Do you think that maybe wine is not correctly installed?

---

### Post by bullfrog55 on 2011-02-04
Hold the bus!! The executable had the name Firefox Setup 3.6.13.exe
So I eliminated the spaces in the file name and ran the wine ...etc and it seems to have worked.

---

### Post by bullfrog55 on 2011-02-20
I finally have wizard101 working but the sound disappears after a short time - about a minute or so. Are there any settings or anything that I need to adjust?

---

### Post by regor210 on 2011-02-26
You could try using the Wine OSS driver. 
Goto Applications >Wine >Configure Wine >click the Audio tab >click the OSS Driver box
Now click Test Sound. If you hear sound try playing Wizard 101 and see if it helps.

If that dose not help you could try lowing the Default Sample Rate from 44100 to 22050 in Wine’s Audio tab.

Some times you need to experiment a bit to get things to work on your hardware.

---

### Post by WinterHico on 2011-03-02
Thanks for the sound tip.  I configured wine to use OSS and now the sound works great.  I did not have to change the sample rate.

When starting up the game, some times it crashes early on, before getting in to Play.  If we past character selection into playing, we have had no further issues so far.

---

### Post by bullfrog55 on 2011-05-03
Wizard101 was crashing about 5 times each time I started it, so I uninstalled it via wine. Now I can't get it to install properly - it goes through the install process very quickly and then I get an error message and a crash almost immediately it begins. I upgraded to Maverick Meerkat but still have the same behaviour. Just can't get it going at all!! Can anyone help?

---

### Post by regor210 on 2011-05-03
You could try.

I am now using  Wine 1.2.2 from
[http://www.winehq.org/](http://www.winehq.org/)


Goto 
Applications> Wine> Browse C Dirve> Program Files> 
then rename the &#8220;Kingsisile Entertainment&#8221; folder.

In 
Wine> Configure Wine> Graphics 
I am using
Vertex Shader Support (None)
(mark) to  Allow Pixel Shader

Wine> Configure Wine>Audio
(mark) OSS
Test sound. If good- 
Apply



Reinstall the game

In Wizard101
Video Advanced tab 

Bloom Active   off
Smoothing      off
Shadows        off

I am using a Nvidia GeForce 8400 GS.

---

### Post by bullfrog55 on 2011-05-04
thanks for the reply regor210. 
I am using Wine 1.3.17
I tried as you said above but at the end of the install which is supposed to start the game I get the error message "The program Wizard101.exe has encountered a serious problem and needs to close. etc etc "
From my terminal, the end of the installation process said this:

"wine: Call from 0x7b83ab72 to unimplemented function msvcp80.dll.?find_last_of@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIPBDI@Z, aborting
wine: Call from 0x7b83ab72 to unimplemented function msvcp80.dll.?find_last_of@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIPBDI@Z, aborting    "

So I can't make out what is happening. It seems that the installation has failed. Something wrong with the msvcp80.dll - it is present in the system32 folder.

BTW I am using NForce-NVidia CK8S according to my system testing utility.

---

### Post by regor210 on 2011-05-04
I just Installed Wizard101 on one of my kids computer Using Wine 1.3.19 in Ubuntu 10.10.

Everything worked without any modification.

We do not have &#65279;msvcp80.dll in are system 32 folders. 

Do you have your video drivers installed?  Check in

System> Administration> Additional Drivers

---

### Post by bullfrog55 on 2011-05-09
I tried updating to 11.something and the whole system was unusable so I have now reinstalled 10.04 and still cannot install Wizard101. I am now using wine 1.2.2 The error messages are different now though, the last 2 lines being:

err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\users\\Public\\Application Data\\KingsIsle Entertainment\\Wizard101\\Wizard101.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\users\\Public\\Application Data\\KingsIsle Entertainment\\Wizard101\\Wizard101.exe" failed, status c0000135

I looked at the video drivers and one was installed:
NVIDIA accelerated graphics driver (version 173)    so I changed it to version 96 but still no change in the behaviour of the install.

Going back to your advice on renaming the KingIsle folder - it doesn't exist as the install failed.
So frustrating.

---

### Post by regor210 on 2011-05-09
You could try &#65279;Wine*1.3.19  from

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)
---------------------------------------------------------
Or you could try setting 
Applications> Wine> Configure Wine> Applications

Windows Version  (Windows 98 )

for the install
---------------------------------------------------------
Wizard 101 system requirements are

Operating System: Windows 98SE or later versions
Processor: 1GHz Intel Processor
RAM Space: 512 Megabytes
Video Card: Best results with GeForce 2 or equivalent
                     (standard in most PCs)
Disk Space: 5 Gigabytes
[https://www.wizard101.com/game/sysreq](https://www.wizard101.com/game/sysreq)
----------------------------------------------------------
Another option may be that your video card has gone bad.  Have you tried playing other games that use 3D drivers?

We have 3 computers here and have had Wizard 101 up on all 3 since beta testing, It should work.

---

### Post by bullfrog55 on 2011-05-11
Regor, thanks for your patience.
Installed Wine  1.3.19 - then tried reinstalling wiz - same result -  though at least the install does actually install the folder of 101  files in the "c drive" - they just don't work.
Tried every version of windows from 98 upwards - same result
Installed torcs - 3d car racing game and it worked fine (Though I played Very Badly)
It Should work as I previously had it working (not perfectly) on lucid before reinstall.
Can't think of anything else to do......

---

### Post by regor210 on 2011-05-12
Ok, you could try.

&#65279;Go to Wine configuration Graphics> (check) Emulate a virtual desktop Desktop size 800x600.

&#65279;Go to 
Applications> Wine> Browse C Dirve> Program Files> 
then rename the “Kingsisile Entertainment” folder.

Reinstall the game. Remember to let it fully update. If it gets interrupted, its likely that the installer will get bugged and you will have to start all over with a new clean install.

---

### Post by bullfrog55 on 2011-05-17
Already had the configuration of 800 x 600.
Renamed the folder but when I tried the install I got a message that  said that I needed to uninstall Wiz and then try the install again which  I did.
From the terminal the first line I get is this:
"fixme:storage:create_storagefile Storage share mode not implemented."

Lots of error stuff after that but still does not work. 
Thought it might have something to do with permissions so I gave all rwx  permissions to the install file but it did no different.
Now the Install produces the KingsIsle Folder with the executable but clearly the install has failed.

---

### Post by regor210 on 2011-05-17
Did you get the installer from here? If not use this one.

[https://www.wizard101.com/game/downloadinstructions](https://www.wizard101.com/game/downloadinstructions)

They upgraded the installer some time ago and the old installer dose not work any more.

---

### Post by bullfrog55 on 2011-05-18
Downloaded from the site you suggested but same result.
The first line from the terminal when I start the intsall is:
fixme:storage:create_storagefile Storage share mode not implemented.
does this mean I do not have permissions to do this? I tried running the install as... sudo wine ...etc but I got an error message " /home/paul/.wine is not owned by you"

---

### Post by bullfrog55 on 2011-05-18
I changed the permissions for the .wine folder but no different I am afraid.

---

### Post by regor210 on 2011-05-18
You could try
[http://wiki.winehq.org/FAQ#head-8b89c928ce782c014b8b312469223296093e1484](http://wiki.winehq.org/FAQ#head-8b89c928ce782c014b8b312469223296093e1484)

7.12. I ran wine with sudo or as root. How do I fix my permission errors?
You need to fix the permissions on your ~/.wine directory, this is where all Wine state, configuration and any important data you might have such as installed programs, saved data within Wine programs, etc. are stored. Once you delete or fix the permssions on this directory, rerun Wine as a regular user always! Run the following to fix the permissions on your ~/.wine directory if it now has root permissions.

cd ~
**sudo chown -R $USER:$USER .wine**

----------------------------------------------------------
If that is not helping and Wine is unusable there is

reinstalled the Wine application.>>> 

$sudo apt-get --purge wine

after the purge go to your home folder and click View > Show Hidden Files 

If you see .wine rename it

Restart your computer. Reinstall wine and try again.

---

### Post by bullfrog55 on 2011-05-28
I tried the same method with an old desktop and guess what? It installed fine though the graphics are a bit jumpy- actually there is a slight delay between pressing a button and getting some movement.

So I  thought the problem with the original desktop might lie with the video card, so I removed the nVidia quadro fx and put in a geforce 5200. Unfortunately the same lame result when I tried the install.
Maybe I should try to reinstall this version of ubuntu???

---

