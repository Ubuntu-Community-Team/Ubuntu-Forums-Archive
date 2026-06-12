---
title: "Getting Civilization IV installed"
date: 2009-07-29
forum: Wine
---

### Post by fomorian on 2009-07-29
So I purchased Civilization IV (just the original version) and I'm trying to install in using Wine 1.0.1 and I keeping getting an error. When I run Setup.exe and I get the following error:

> 
Setup has experienced an error.

Please do the following:
- Close any running programs
- Emply your temporary folder
- Check your Internet connection (Internet-based Setups)

Then try to run the Setup again.

Error code: -6006


Anyone come across this error before? My Internet connection is fine and nothing else is running when I try to make install (except Wine technically) and I'm not sure how to empty my temporary folder through Wine.

---

### Post by letatcest on 2009-07-29
I managed to install Civ IV with the original data disks following instructions I found here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10158)

I had some inintial problems, but don'tremember what the troubles were...

---

### Post by fomorian on 2009-07-29
I appreciate the link, letatcest, but I can't even get Civilization IV to install let alone run. The instructions there just tell me to install it and after that the guide goes over the things I need to do to get it running.

I probably should have mentioned this before but I'm using Ubuntu 9.04 also.

---

### Post by fomorian on 2009-07-29
Perhaps I'm using an outdated version of Wine?

Looking over posts and pages I noticed a lot of people using Wine version 1.1.something (usually in the twenties). My version of Wine is 1.0.1, which I would guess is older. I just used the ```
sudo apt-get install wine
``` to install it recently so I can't imagine that it's out of date. I tried ```
sudo apt-get update
``` but my version of Wine has remained the same.

Can anyone confirm that Wine version 1.0.1 is out of date and that may be a problem? If it is, can someone tell me how to install a specific (like the latest) version of Wine?

########

Just as a quick update. I installed Wine version 1.1.26 and the results are the same. I still can't install and I'm getting the same error.

---

### Post by fomorian on 2009-07-29
Bump!

Anyone have any insights on this? Surely I can't be the first person to come across an error like this?

---

### Post by pedro_orange on 2009-07-30
To update your wine:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I have CIV IV (Complete) running on my Ubuntu box. I had some issues with having to use Winetricks to install DX before I could install, I then copied alot of .dll files to the system32 folder - but all of these suggestions are on the WineHq AppDb section.


Hope this helped

---

### Post by fomorian on 2009-07-31
Thank you for the help pedro_orange. Unfortunately nothing worked. I tried updating to the latest version of Wine. I downloaded the dlls that CivIV needs and put them in the System32 folder. I used WineTricks to download DX. After all that I get the exact same error as I described in my first post.

Anyone else have any insights?

---

### Post by antientropy on 2009-08-14
I had the same problem. Got error 6006 when opened setup.exe with wine program loader. I solved this problem by copying all the files from the installation DVD to my hard drive. After that the installation ran smoothly. I am using Ubuntu 9.04 with wine 1.1.27.

---

### Post by ersatzorama on 2009-09-30
I double that solution.. Encountered the same -6006 error, copying all the files to my HD solved the problem.. Works like a charm now!

---

### Post by sabre2th on 2009-09-30
It's been a while since I had to play with it, but I don't believe it took any special doing last time I installed.  I used ISOs of the disks to install (including Beyond the Sword, which may make a difference), installed the standalone version of the latest patch, and then copied my program folder from my Windows partition.

I think copying the files was the key, though I don't remember for sure now.  I always used the latest version of Wine from the Wine repo.

---

### Post by Newbie_777 on 2009-10-28
**I need help ASAP. I have been using Ubuntu Linux for several years now. I am currently running under Ubuntu 9.04 Jaunty, GNOME 2.26.1.** I have been quite persistent with installing Civilization 4 because it is one of my favourite games. I have a solid graphic card (256 MB DDR2), 2.6 GHz processor and 1GB of RAM. Enough for CIV4s requirements. I install wine through the terminal and everything goes smoothly. Then I ran setup.exe from my game folder. I installed the game quite smoothly. ***(DirectX installation doesnt even pop up!) ***Then I update the game to version 1.61. After that I re-update it again to the newest patch version 1.74. Then I "crack" the game by pasting the NO-CD crack to my CIV4 folder in .wine. Finally, I restart my system and after that I start the game in Applications>Wine>Program>Firaxis Games>Sid Meiers Civilization 4. Game loads sucessfully and then problems begin to emerge : 1. videos arent visible(the screen is blue) 2. the game menu is messed up(cant see the words, it is like they are white muddy squares). Then I try to continue with playing,randomly guessing what needs to be pressed,I manage to do it and then before the "evolution" video start, game freezes.:( Can anyone help me?

---

### Post by pedro_orange on 2009-10-29
> **Newbie_777 said:**
> **I need help ASAP.I have been using Ubuntu Linux for several years now.I am currently running under Ubuntu 9.04 Jaunty,GNOME 2.26.1.** I have been quite persistent with installing Civilization 4 because it is one of my favourite games. I have a solid graphic card(256 MB DDR2),2.6 GHz processor and 1GB of RAM.Enough for CIV4s requirements.I install wine through the terminal and everything goes smooth.Then I run setup.exe from my game folder.I installed the game quite smoothly.***(DirectX installation doesnt even pop up!)***Then I update the game to version 1.61. After that I re-update it again to the newest patch version 1.74. Then I "crack" the game by pasting the NO-CD crack to my CIV4 folder in .wine. Finally,I restart my system and after that I start the game in Applications>Wine>Program>Firaxis Games>Sid Meiers Civilization 4. Game loads sucessfully and then problems begin to emerge : 1. videos arent visible(the screen is blue) 2. the game menu is messed up(cant see the words,it is like they are white muddy squares). Then I try to continue with playing,randomly guessing what needs to be pressed,I manage to do it and then before the "evolution" video start, game freezes.:(Can anyone help me?

You don't actually need the NO-CD crack. It works without it fine. I find it actually plays better without it.

Have you put the DLLs from the WineHQ guide into your ..\system32 and put in the necessary overrides in winecfg?

Also, this may be because of your video card. What card do you have? Which drivers are you using? I run an nVidia and it's flawless.

---

### Post by Newbie_777 on 2009-10-29
You mean this from the WineHQ : "Then, it is necessary to add following libraries to windows/system32: (download it from web) **d3dx9_26.dll d3dx9_31.dll d3dx9_32.dll d3dx9_33.dll d3dx9_34.dll msxml3.dll msxml3r.dll **Then make overrides (native) for: msxml3.dll msxml3r.dll And remove these libraries from al game folders      
Note:  **d3dx9_31.dll **is also needed even if the game does not complain that you dont have it." Without this library the game will crash during Init Engine." > I will try with adding all the DLLs today.:D
I think it is ATI Radeon,but I dont know what model(I know its a pretty new version).Do I need to install a a driver for my graphics card? I lost my CD so I need the NO-CD crack.:(

---

### Post by Newbie_777 on 2009-10-29
I installed it all over again. I added the DLLs to the windows/system32 folder. I checked the game folders for the DLLs above and they weren't there so I had nothing to remove. I made the native override for msxml3.dll but I could find **msxml3r.dll:( ? What should I do?**

---

### Post by pedro_orange on 2009-11-03
> **Newbie_777 said:**
> I installed it all over again.I added the DLLs to the windows/system32 folder. I checked the game folders for the DLLs above and they weren't there so I had nothing to remove.I made the native override for msxml3.dll but I could find [B]msxml3r.dll:( ? What should I do?

[/B]

You -could- or couldn't find msxml3r.dll? 

I'd rather not link to an external download site, but if you go to google and type in 'msxml3r.dll you will find it.
Put that in your .\system32
Terminal > winecfg > Libraries > type in 'msxml3r' in the drop down and click apply & ok.

Check the CIV IV folder in \home\<usr>\.wine\... I'm pretty sure there is an msxml.dll in the Beyond the Sword folder. But instead of deleting it, just rename the file. In case you need to roll back for any reason.

Also have you actually installed your Radeon driver? I'm not sure how you do it with ATI, but on nVidia I just go into System > Hardware Drivers (IIRC) and it tells me which driver to download with the (Recommended) tag. Then wait for about 20 minutes!

Good luck.

---

### Post by Newbie_777 on 2009-11-10
I have done everything as you said. I found the msmxl3r on the dll dump site and put it in my system32 folder. The I ran winecfg but still I couldn't find it. I decided to upgrade my Ubuntu to 9.10 Karmic Koala because I couldn't find the suiting driver for my system. I stopped trying to install Civilization 4. I hope that the possibilities with the new Ubuntu will be much greater. And that it will provide more of a gaming spirit than before. I have recently upgraded my system but when I go on System>Hardware Drivers I still cant find my suited drivers. Here is the message that shows: No proprietary drivers are in use on this system:mad:

---

