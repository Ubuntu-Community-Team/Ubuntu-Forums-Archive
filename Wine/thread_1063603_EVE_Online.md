---
title: "EVE Online"
date: 2009-02-08
forum: Wine
---

### Post by RedSingularity on 2009-02-08
This is Unbelievable!  All i want is to be able to get on EVE and play.  It always freezes up though and the only way to get out of it is to restart the whole computer!  Even Ctl+Alt+Backspace doesn't work.  As you may imagine this is VERY agrivating.  If anyone knows a solution to this problem please let me know.

---

### Post by betrunkenaffe on 2009-02-08
you'll need the arial font installed into windows/Fonts to start, I also found I ran into some issues with the scroll bars in the game. I solved the problem by loading all the Windows dlls into wine.

---

### Post by RedSingularity on 2009-02-08
Where can i get these Dll files?

---

### Post by timofthec on 2009-02-10
Shadow, as this post is in the Wine forum, am I to assume that you are trying to get eve to run through Wine?

If so, you should know that CCP do an eve linux client that (for me) has run very well under Ubuntu.

On the other hand, if you are talking about the linux eve client and have posted in this forum for convenience - please ignore this post:P

---

### Post by 0bso on 2009-02-10
> **timofthec said:**
> 
If so, you should know that CCP do an eve linux client that (for me) has run very well under Ubuntu.

I had horrible luck with CCP's "linux client" (normal client with a cedega wrapper). They have officially ended support for it anyways. Here is the how-to install eve on linux from them.

> 


Wine:

To install Wine either use your distributions package management software or download the sounrce and install it manually. Information on how to download and install Wine for a few distributions can be found here

To install EVE using Wine follow these steps.
1. Download the Windows client from our homepage
2. Right click on the EVE client installer and select "open with Wine Windows Program Loader"
3. This starts the EVE client installation process.
4. Follow the instructions here to get EVE to run fully.
4. When complete simply run the EVE online Client using the Shortcut created on your desktop.


Wine-Doors:

Wine-Doors is a frontend application for Wine and includes easy installation for a number of additional programs and games with easy installation procedures. Wine-Doors binaries and sources can be found here

To install EVE using Wine-Doors follow these steps:
1. Download the Windows client from our homepage
2. Start Wine-Doors
3. Find EVE Online in the list of available applications and press the install option behind it, then press Apply.
4. Navigate to where you saved the EVE installer and press Open.
5. This starts the EVE client installation process.
6. Install all Windows Fonts available
6. When completed simply go to Applications --> Wine --> Programs --> EVE and select EVE Online to start.


PlayOnLinux

PlayOnLinux is another frontend application for Wine which also includes easy installation for a number of programs and games. Download the binaries from here

To install EVE using PlayOnLinux follow the these steps.
1. Download the Windows client from our homepage
2. Under File select Install
3. At the bottom of the window you see a text line "Install a .pol package or an unsupported application". A new window appears.
4. Select Manual installation and press NEXT
5 A wizard is started, press Forward
6. Select "Install a program in a new prefix"
7. Name the Prefix EVE ( do not use spaces ) and press Forward
8. Browse to the location where you saved the EVE installer, select it and then press Forward.
9. Now begins the Installation process for the EVE client itself.
10. When the EVE client has completed installation untick "Run EVE-Online" then press Finish and then Forward.
11. Say yes to creating a shortcut to the Application
12. Press Browse and navigate into the Program Files\CCP\EVE folder, there select eve.exe and press open then Forward.
13. Name the shortcut ( i.e. EVE Online ) and press Forward.
14. Select where you wish the shortcut to be displayed and press Forward then press No.

Install the Microsoft Fonts

1. Under File select Install
2. Select the "Other" category
3. Here select Microsoft Fonts and press the Apply button, then Forward
4. Select EVE as the target prefix and press forward.
5. When done, press forward.

Install DirectX

1. Under File select Install
2. Select the "Other" category
3. Here select DirectX 9 : June 2008 patch and press the Apply button, then Forward
4. Select EVE as the target prefix and press forward.
5. After downloading the window closes automatically.

EVE can now be run normally

Cedega
1. Install the Cedega application
2. Download the Windows client from our homepage
3. Start the Cedega Gaming Service application
4. Press Install
5. Under GDDB Profile drop down box select EVE online and browse to the EVE client installer file under Program.
6. Press Continue and the EVE client installation is started.
7. When the client installation is completed use the Cedega Gaming server Application to launch EVE.


CodeWeaver Games

1. Install the Codeweavers games application
2. Start the CodeWeaver Games application and select EVE Online from the options list and press next.
3. The installation process takes care of all requirements so there's not much else you need to do at this point but wait for it to complete apart from pressing Yes and Ok from time to time.
4. When the installation is complete untick "Run EVE-Online" and press finish.
5. The application finalizes the installation proces, when finished press Finish.
6. Start the EVE client by double clicking on the EVE icon on your desktop. 

I haven't got a chance to personally see if any of these methods work better than the "linux client" did, but it's worth a shot.

---

### Post by RedSingularity on 2009-02-10
I have not tried the native client yet.  I guess i will after i try Wine Doors.  Thanks guys.  :)

---

### Post by betrunkenaffe on 2009-02-11
[http://winehq.com]("http://winehq.com")

Every problem I ran into with Eve is covered here with the solutions. Just type in Eve in the search box.

---

### Post by RedSingularity on 2009-02-11
Ok thanks.  I am looking into that now.

---

