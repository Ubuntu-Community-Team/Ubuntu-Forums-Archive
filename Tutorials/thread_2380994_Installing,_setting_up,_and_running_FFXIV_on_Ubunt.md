---
title: "Installing, setting up, and running FFXIV on Ubuntu 14.04 LTS and beyond releases"
date: 2017-12-24
forum: Tutorials
---

### Post by shadow13069 on 2017-12-24
**This tutorial is for installing, setting up, and running FFXIV   Stormblood on Ubuntu Based 14.04 LTS releases and beyond 32/64 Bit with default AMD/ATI drivers**

[B][COLOR=#ff0000]Note: I have only tested this with the default FGLRX drivers that are installed by default in the Ubuntu 14.04 LTS and later up to 16.04 LTS and the AMDGPU and RADEON default drivers that are installed by default when installing Ubuntu 16.04 LTS or later variant. I will be testing this at some point in the future with NVIDIA and INTEL drivers as well but for the time being I have only been able to confirm this works with AMD/ATI graphics. If anyone has tried this with NVIDIA Or INTEL graphics feel free to reply to this post and you are more than welcome to share a link to your guide as well. 

Note: I am particularly using currently an AMD Radeon R7 370 Desktop Graphics card with a Gigabyte 1170A motherboard. I have tested various older AMD/ATI Video cards as well varying from HD4000 series, HD5000 series, HD6000 series, etc. This appears to work on many combinations and I was also able to get this same method to work on an older Lenovo Thinkpad Laptop model X130e which has an AMD Radeon HD 6320 on board graphics and a AMD Core i3-2367M processor being the oldest system I tried this on. It does get pretty laggy but it will launch and load the game this way as well on the Lenovo Thinkpad X130e.[/COLOR][/B]

 **[COLOR=#ff0000]Note:  I have not tried this on any release before 14.04 LTS but I have no  doubt that this will work. Also do not install DirectX separately in  wine as FFXIV Stormblood will do it during the install. This same method  appears to work on some other games that are Pre DirectX 11 that I am still  currently testing[/COLOR][COLOR=#ff0000]. So far this is only known to work with games that are pre DirectX 11 so anything DirectX 9 and below works for this method.[/COLOR]**

The topics discussed here  are not sponsored by or  endorsed by the respective companies that own  the rights to the  following games mentioned. All this information is  from my own point of  view and experience and is also for educational  purposes to get the  game to work on your Ubuntu Based 14.04 LTS release and beyond 32/64 Bit operating   system. The steps below will get you up and running quickly.

**Step 1: Start off with a freshly installed Operating System or a fresh reset. **

I highly recommend this to ensure there is nothing that can interfere with the wine staging that is about to be installed. Ensure that you have installed all available safe updates available and you will quickly be able to determine this by seeing a shield symbol with a green check mark in it at the bottom right hand side of you desktop in the task bar.


**Step 2: Installing Wine Staging For Ubuntu**

Open up terminal by pressing CTRL+ALT+T and put in the following code below and hit enter. This will install the wine staging release key needed for ubuntu. 
```

wget -nc https://dl.winehq.org/wine-builds/Release.key

```

Next put in the following code and hit enter. This will add the release key to the system for wine.
```

sudo apt-key add Release.key

```

Next put in the following code and hit enter. This will add the wine build repository for wine. After its added you will see where it was added then you just hit enter again to confirm.
```

sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'

```

Next put in the following code and hit enter. This will update the changes you have made so far.
```

sudo apt-get update

```

Next put in the following code and hit enter. This will finish your install of wine-staging for Ubuntu.
```

sudo apt-get install --install-recommends winehq-staging

```

[COLOR=#008000]*I want to send Kudos to Wine HQ for making Wine Staging Possible to get alot of games working in Ubuntu*[/COLOR] :)

**Step 3: Configuring Wine To Work For You In Ubuntu Before Installing FFXIV Stormblood**

Put in the following code in terminal and hit enter. This will install Winetricks to take care of any DLL issues that can appear during install and running of the game.
```

sudo apt-get install winetricks

```

Next put in the following code and hit enter. This will open a **Wine Configuration** menu.
```

winecfg

```

[B][COLOR=#ff0000]Note: When you put that code in for the first time you will see a couple installs pop up. One will be for [/COLOR][COLOR=#000000]Wine Gecko[/COLOR][COLOR=#ff0000] and the Other will be for [/COLOR][COLOR=#000000]Wine Mono[/COLOR][COLOR=#ff0000]. Make sure to proceed with those installs as they are needed for wine to function properly.
[/COLOR][/B]
Once you are in the **Wine Configuration** menu you will go to the **Staging** tab and make sure the **Enable CSMT** is checked. This will take care of registry issues that can arise during install and running of the game. After that you to the **Applications** tab and make sure that the environment is set to **Windows 7**. Once that is done click apply and then click close.

**Step 4: Installing Final Fantasy XIV Stormblood**

Next you will go to the Final Fantasy XIV website to download the game client that will be used to play the game. The link to download this is below...

[https://www.finalfantasyxiv.com/playersdownload/na/](https://www.finalfantasyxiv.com/playersdownload/na/)

Once the download completes proceed to install. 

**[COLOR=#ff0000]Note: During the install you may see a couple installs pop up once again. One will be for [/COLOR][COLOR=#000000]Wine Gecko[/COLOR][COLOR=#ff0000] and the Other will be for [/COLOR][COLOR=#000000]Wine Mono[/COLOR][COLOR=#ff0000]. Make sure to proceed with those installs as they are needed for wine and the game to function properly.[/COLOR]**

Once that is done make sure to select the create desktop icon at the end to place an icon for the game on your desktop. After this that will complete the installation.

[B]Step 5: Configuring Final Fantasy XIV Stormblood To Launch Properly And Avoid The Black Screen Launcher

[/B]Double click on your **Home** folder or search under **Applications** search for Home and select it. This will take you to your home directory. Once you are there navigate to **Documents** --> **My Games** --> **FINAL FANTASY XIV - A Realm Reborn** and then find the file **FFXIV_BOOT.cfg** and open it. A dialogue box will pop up just select display. This will open the file in plain text. 

You will see a line near the bottom that says **"BrowserType  0"**. Change that line to "**BrowserType  2" **and then save and close the text file. This will change your game launcher to a style that your operating system will be able to load so that you will be able to play the game.

**Step 6: Launch Final Fantasy XIV Stormblood And Configure Graphics Settings Before Playing**

Next we are going to go ahead and launch FFXIV Stormblood by double clicking the icon you made on your desktop. On first start up it is going to take you through the registration portion. You will have the option to **Sign Into Current Square Enix Account** or **Create A New Account**. Select the appropriate option for you and complete it. Once that completes it will start logging you in as its doing that click the Config option near the bottom of the launcher. This will interrupt the download for a minute and make sure DirectX 11 support is turned off as the game currently does not display correctly with this on. After that save it and it will take you back to the login. Go ahead and login and it will proceed downloading. Let this complete as it can take some time. Once that completes you will see a green box to click on that says DirectX 9 be sure to click on that to start the game.

It will pull up the main game window at this point and begin to start up. You will have the main menu starting off. Select **System Configuration** from the main menu. In the **Configuration Menu** first go to the **Game Pad** tab. If you have a game pad keep enabled  if not then disable as it will not be needed. After that go to the **Mouse Tab** and ensure its enabled. Once that is done select the **Graphics Tab** and make sure to uncheck **Disable Rendering Of Objects When Not Visible (Occlusion Culling)**. This is due to a glitch that makes objects disappear in game. Also make sure that **Enable HDR Rendering** is checked as that will improve your graphics quality. Once that is done click apply and then click close.

**Step 7: You are ready to go everything has been setup**

From the main menu just finish logging in. If you have any feedback or find any other games that this method helped make work as well feel free to reply and let me know. Happy Gaming :)

---

### Post by SeijiSensei on 2017-12-25
Will this method really detect and use my NVIDIA GTX 750?  As I recall FFXIV wouldn't install on a machine with standard Intel graphics, though it's been a while since I ran the installer.  I presume the game makes the usual Windows calls to the video driver and its libraries.  Are these somehow translated into the appropriate commands for the Linux NVIDIA driver?

I got bored with FFXIV some time back and decided it wasn't worth the subscription.  Still I'm curious about how this process might work with other games that I can only play now by booting into Windows.

---

### Post by shadow13069 on 2017-12-25
I have not personally tested this on standard Intel graphics and on the NVIDIA GTX series. I apologize for that and have updated my post of what I have tested this on. What I can tell you is that I only used the wine staging that you see in the tutorial with wine tricks and I just used the default drivers that install by default with those versions of Ubuntu. I didn't have to mess with any drivers or anything like that all I did was install the Ubuntu release, ran all the safe updates after that did exactly in order like in the tutorial. After that I just went to FFXIV website and downloaded the game client file and ran it with the usual windows program loader. I am currently working on a build involving Intel and NVIDIA graphics though so once I test it and confirm that it works ill update the post. So far it has worked for me on many different AMD/ATI setups and I chose to test that first since AMD/ATI isnt really linux friendly in general. I am currently testing this with various games and it appears to only work with mostly games that are Pre DirectX 11 at the moment. Some of the games I have tested so far are World Of Warcraft Legion, Diablo III, Starcraft II, Star Wars The Old Republic which all of those worked in standard graphics settings, and Steam windows based games are kind of hit and miss some work and others do not. I know that Carmagedden, and Starbound work though when it comes to Steam so far.

---

### Post by SeijiSensei on 2017-12-25
Thanks.  I might give this a try with Nier: Automata on Steam, but not until after the first of the year.

---

### Post by shadow13069 on 2017-12-25
Awesome sauce let me know how it goes I always like hearing that it works for others and if it works on Intel with NVIDIA as well thats a huge deal. :)

---

