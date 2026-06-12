---
title: "How-To : PopCap Games"
date: 2009-12-20
forum: Wine
---

### Post by zami on 2009-12-20
I've done it a few times now, so I guess the method is good!  I have Insaniqaurium, Plants vs. Zombies, and Peggle running smoothly under Wine.

I'll walk through installing Peggle for this How-To.

This method involves making a wine prefix or "bottle" for a specific game, and installing Internet Explorer 6 using the program Winetricks. (PopCap games install under vanilla Wine just fine, but registering them can be a trick, and I fully beleive all games/programs should be given their own Wine prefixes.)

**[SIZE="5"]::Preliminaries::[/SIZE]**
**1) Install Wine**
At this point I suggest using the WINE package "wine" (version 1.0.1) available by default in the Ubuntu repositories, not the more recent available version package "wine1.2" or any packages directly from WineHQ (more on why later)
Go into
System > Administration > Synaptic Package Manager
search for "wine", and select and install the package "wine" (it will also auto-select wine-gecko and that's fine)
Already have a more recent version of Wine?  Continue on, but know that there may be problems with registering your PopCap game - this is addressed under "High Weirdness" near the end of the How-To.

**2) Install Winetricks**
hit ALT+F2 and type in
```
gnome-terminal
```
then in the terminal, type in
```
wget -nv [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
```
then
```
chmod 700 ./winetricks
``` 

[B]
[SIZE="5"]::Install, Register, and Play Peggle::[/B][/SIZE]
**Download Peggle Installer from PopCap**
Download the game, and save it to your Desktop
[http://www.popcap.com/games/peggle/?mid=peggle_pc_en_full](http://www.popcap.com/games/peggle/?mid=peggle_pc_en_full)

**1)Open a Terminal**
hit ALT+F2 and type in 
```
gnome-terminal
```

**2)Create a Peggle "Bottle"**
in your terminal, type in
```
export WINEPREFIX=$HOME/.wine-peggle
```
I've named my bottle "wine-peggle" for the sake of the walkthrough, but the point is the bottle name reflects the program I'm going to install into that bottle.  Zuma is in wine-zuma, Lord of the Rings Online is in wine-lotro, and so forth.
Next type in
```
wineprefixcreate
```
[COLOR="Magenta"]DO NOT CLOSE THIS TERMINAL UNTILL FINISHED WITH HOW-TO[/COLOR]
(well you *can* close the terminal, but you'll need to run the "export WINEPREFIX...." command before any other wine-related commands every time you close/open a new terminal, or you'll be affecting your .wine directory and settings rather than your .wine-peggle directory and settings.  Clear as mud?  It's just easier to leave the terminal open.)
[B]
3)Configure The Peggle Bottle[/B]
in your still open terminal, type in
```
winecfg
```
Under the "Applications" tab, for Windows Version select XP
Under the "Graphics" tab, select "Emulate a Virtual Desktop" and set the Desktop size to 1024x768
Click "Apply", click "Okay"

**4)Install IE6**
in your still open terminal, type in
```
./winetricks ie6
```
and follow the install prompts.  Near the end, it might hang for a minute, with a blank WINE screen in blue and your terminal full of mumbo jumbo - give it a few minutes (I've waited up to three minutes at this screen).
[B]
4.5)Did you get CabExtract Errors?[/B]
If not, great! Just move along.  :)
If so, in your still open terminal, type in
```
sudo apt-get install cabextract
```
then try 
```
./winetricks ie6 again
```

**5)Install Peggle**
in your still open terminal, type in
```
cd Desktop
```
then
```
wine PeggleSetup.exe
```
(It's probably actually named Peggle_1_8_Really_Long_Name.exe, so change accordingly.)
Follow installation prompts, and chose "Launch game now" when installation is complete.

**6)Register Peggle**
Click "Already purchased this game?", enter in your purchase info, and hit "Register"

**6.5)Did you Register?**
Great!  Skip to step 7, "Reconfigure the Peggle Bottle".
Did you have "can't connect" problems when registering?  Oooooh boy - skip down to "High Weirdness".  And cross your fingers.

**7)Reconfigure the Peggle Bottle**
Close down any PopCap screens, then
in your still open terminal, type
```
winecfg
```
Under the Graphics tab, DEselect "Emulate a virtual desktop".

**8)Make a Peggle Launcher**
With luck a launcher shows up on your desktop, and it probably looks like
PeggleDeluxe.desktop
The first time you double click it, select "Mark as Trusted", and it should stop saying .desktop and transform to the Peggle icon.

But maybe you want to make your own launcher somewhere, sometime.  The key is to launch the game within it's own Wine prefix (the "Peggle Bottle"). 
To make a launcher in your panel:
Right click on your panel, and select "Add to Panel"
Double click on "Custom Application Launcher"
Type= Application.  
Name= Peggle
Command (this is key)= 
> env WINEPREFIX="/home/NAME/.wine-peggle" wine "C:\Program Files\PopCap Games\Peggle Nights Deluxe\PeggleNights.exe" 
Include the quotation marks. 
Where it says NAME put in the name of your home directory.  For example, mine is env WINEPREFIX="/home/laura/.wine-peggle".
Click "okay".  Now you should have a launcher on your panel.


[SIZE="5"]**::High Weirdness::**[/SIZE]
Did you get the message from PopCap
"Registration cannot proceed
An error occurred while connecting to the PopCap web site
blablabla about firewalls and such" ?
Go ahead and close the PopCap windows, and read on.

As of this writing (December 20th, 2009), I get the following results from the following Wine versions -

Synaptic package "wine" (1.0.1) registers, but sound blows.

Synaptic package "wine1.2" (1.1.31) wont register, but plays beautifully.

WineHQ directions [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) (1.1.35) wont register, but plays beautifully.

MY fix, has been to downgrade Wine, register my PopCap game, then upgrade Wine again.  Then I have a registered game WITH sound.

I suspect with the countless configurations of PCs, and sound and video drivers and frequent Wine updates, quirks like this will be all over the place.  Remembering your mileage may vary, here is my "fix" of downgrading Wine.

To downgrade Wine:
**Remove Wine extra repositories**
Go into System > Administration > Software Sources
under the "Other Software" tab uncheck or remove any entries relating to Wine.  Mine is
"http://ppa.launchpad.net/ubuntu-wine/ppa......", previous versions start with "WineHQ".
Close Software sources, and "Reload" if prompted, then "Close" Software Sources.

**Remove Wine**
Go into System > Administration > Synaptic Package Manager
Search for Wine, and remove any Wine and Wine-Gecko packages you have installed.  They should look like "wine" or "wine1.2" (Don't worry about any Wine font or icon related packs.)

**Reinstall Wine**
Go into System > Administration > Synaptic Package Manager
Search for Wine, and select and install the package "wine" - this is version 1.0.1.

NOW, try registering again.

Upgrading Wine is a common enough task that I wont cover that here.


**[SIZE="5"]::Misc. Tips::[/SIZE]**
**3D Acceleration and "Nothing happens when I launch"**
In a Wine virtual desktop environment, PopCap games seem to be unaffected by "3D Acceleration" being enabled - that is, they look the same, and the gameplay doesn't suffer.
Outside of the virtual desktop environment, they crash, go blue, go black, or "do nothing" when you try to launch the games.

to UNenable 3D Acceleration:
Start a terminal, by hitting ALT+F2 and typing
```
gnome-terminal
```
Then export to your game "bottle"
```
export WINEPREFIX=$HOME/.wine-peggle
```
(of course replace "wine-peggle" with whatever your bottle is named, but in this walkthrough we're sticking with peggle)
Start Wine Configuration
```
winecfg
```
Under Graphics, select "Emulate a virtual desktop" and set it to 1024x768, apply, click "okay".
Restart your game (you can use the launcher you made previously) and now, in the smaller virtual desktop environment, you should be able to work your way to the options menu and DEselect "3D Graphics Acceleration".  I also disable the "Custom Cursor".  Because it's a punk.

Now exit the game, and in your hopefully still open terminal, again go into
```
winecfg
```
again into the Graphics tab, and UNselect "Emulate a virtual desktop", click apply, then okay.  Now it should be safe to close your terminal, and start your game as normal (double clicking your launcher).  Hopefully it will open right up, full screen, running beautifully with troublesome 3D NOT enabled.

**Quick Desktop Toggle**
If in the middle of a game you need to pause, and check email or some such,
CTRL+ALT+right arrow
is a great screen toggle!  Oh sure, your desktop is a horrible resolution, but it's accesible, and it's much quicker than shutting the game down.  And more reliable than ALT+TABbing your way to another window.  This is a handy tip for any full-screen Wine program.

**[SIZE="5"]::Help Improve::[/SIZE]**
Was this how-to useful? Dreadful?
How can I improve it?  Was it clear?  Do you have any questions?  Suggestions?
I'm open to feedback and would appreciate help in making this a better How-To!

I spent about two hours wracking my brains over the wine version/registration issues, so if anyone has insights as to what's going on there, or a better workaround or fix, please share!

Thanks!  Hope someone can find this helpful.

-zami

---

### Post by mivo on 2009-12-20
Beautifully done. Thank you. :) (Wish we still had the "thanks" button.)

---

### Post by zami on 2009-12-20
> **mivo said:**
> Beautifully done. Thank you. :) (Wish we still had the "thanks" button.)
Thanks!

I see PopCap questions come up a lot, so hopefully this will help some fellow casual gamers out there.  :)

-zami

---

### Post by shinkaide on 2010-02-12
Hello, I've tried following your howto, but when it comes to installation, I can't complete it.

I tried installing Plants Vs. Zombies, but when it comes to the progress bar as it installs the game, it suddenly aborts (shows the "Aborted!" error dialog box).

Refuses to install!

I have the same version of wine you used for this howto, BTW.

---

### Post by drhabber on 2010-02-25
Thanks for the tip ! I've had an error **err:wininet:NETCON_secure_connect SSL_connect failed: 12157** and downgrade / register with Wine 1.0.1 / upgrade did the trick.

---

### Post by fbicknel on 2010-02-27
I tried your instructions, but wound up with the following disappointment:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148405&stc=1&d=1267287754[/IMG]

I note that they say 'deluxe'; but nowhere on their download page do they mention that.  Have they changed the game?

I'm off to try some other games... my original intent was to install Bookworm, so I'll try that one.

Thanks for the starting points!

---

### Post by fbicknel on 2010-02-27
I thought I'd try wine 1.2, but that's even worse: the install looks like this:

sbicknel@bick-ubtu1:~/Desktop$ wine ../Downloads/BookwormSetup.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32e6ac,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1345
  Current serial number in output stream:  1345
sbicknel@bick-ubtu1:~/Desktop$ 

The graphics portion never starts. 

I removed the previous bottle before starting again with 'winecfg'.

---

### Post by mikefreeman on 2010-03-09
Trying to install Plants vs. Zombies. I followed your instructions to the letter, but when I get into the actual installation of the program, an error pops up before the progress bar goes anywhere:

Cannot read access control list.
Error code: 1400

After closing the error message, it appears to install, but at the end says:

The game is not properly installed. Please reinstall.

Any attempts to actually run the program gives me this same last error message.

My specs: Running Linux Mint 8 (essentially Ubuntu 9.10), WINE 1.01 (downgraded from 1.1.40 for the install).

Any help would be great, thanks!

---

### Post by mattshow on 2010-05-11
Plants vs Zombies wouldn't install properly for me until I used winetricks (Google it) to install the vcrun2008 library.

---

### Post by mattshow on 2010-05-11
> **mattshow said:**
> Plants vs Zombies wouldn't install properly for me until I used winetricks (Google it) to install the vcrun2008 library.

Err ignore my comment about Googling it, since winetricks was already explain by the original poster. My bad.

---

### Post by themoddingden on 2010-07-05
> **zami said:**
> I've done it a few times now, so I guess the method is good!  I have Insaniqaurium, Plants vs. Zombies, and Peggle running smoothly under Wine.

I'll walk through installing Peggle for this How-To.

This method involves making a wine prefix or "bottle" for a specific game, and installing Internet Explorer 6 using the program Winetricks. (PopCap games install under vanilla Wine just fine, but registering them can be a trick, and I fully beleive all games/programs should be given their own Wine prefixes.)

**[SIZE="5"]::Preliminaries::[/SIZE]**
**1) Install Wine**
At this point I suggest using the WINE package "wine" (version 1.0.1) available by default in the Ubuntu repositories, not the more recent available version package "wine1.2" or any packages directly from WineHQ (more on why later)
Go into
System > Administration > Synaptic Package Manager
search for "wine", and select and install the package "wine" (it will also auto-select wine-gecko and that's fine)
Already have a more recent version of Wine?  Continue on, but know that there may be problems with registering your PopCap game - this is addressed under "High Weirdness" near the end of the How-To.

**2) Install Winetricks**
hit ALT+F2 and type in
```
gnome-terminal
```
then in the terminal, type in
```
wget -nv [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
```
then
```
chmod 700 ./winetricks
``` 

[B]
[SIZE="5"]::Install, Register, and Play Peggle::[/B][/SIZE]
**Download Peggle Installer from PopCap**
Download the game, and save it to your Desktop
[http://www.popcap.com/games/peggle/?mid=peggle_pc_en_full](http://www.popcap.com/games/peggle/?mid=peggle_pc_en_full)

**1)Open a Terminal**
hit ALT+F2 and type in 
```
gnome-terminal
```

**2)Create a Peggle "Bottle"**
in your terminal, type in
```
export WINEPREFIX=$HOME/.wine-peggle
```
I've named my bottle "wine-peggle" for the sake of the walkthrough, but the point is the bottle name reflects the program I'm going to install into that bottle.  Zuma is in wine-zuma, Lord of the Rings Online is in wine-lotro, and so forth.
Next type in
```
wineprefixcreate
```
[COLOR="Magenta"]DO NOT CLOSE THIS TERMINAL UNTILL FINISHED WITH HOW-TO[/COLOR]
(well you *can* close the terminal, but you'll need to run the "export WINEPREFIX...." command before any other wine-related commands every time you close/open a new terminal, or you'll be affecting your .wine directory and settings rather than your .wine-peggle directory and settings.  Clear as mud?  It's just easier to leave the terminal open.)
[B]
3)Configure The Peggle Bottle[/B]
in your still open terminal, type in
```
winecfg
```
Under the "Applications" tab, for Windows Version select XP
Under the "Graphics" tab, select "Emulate a Virtual Desktop" and set the Desktop size to 1024x768
Click "Apply", click "Okay"

**4)Install IE6**
in your still open terminal, type in
```
./winetricks ie6
```
and follow the install prompts.  Near the end, it might hang for a minute, with a blank WINE screen in blue and your terminal full of mumbo jumbo - give it a few minutes (I've waited up to three minutes at this screen).
[B]
4.5)Did you get CabExtract Errors?[/B]
If not, great! Just move along.  :)
If so, in your still open terminal, type in
```
sudo apt-get install cabextract
```
then try 
```
./winetricks ie6 again
```

**5)Install Peggle**
in your still open terminal, type in
```
cd Desktop
```
then
```
wine PeggleSetup.exe
```
(It's probably actually named Peggle_1_8_Really_Long_Name.exe, so change accordingly.)
Follow installation prompts, and chose "Launch game now" when installation is complete.

**6)Register Peggle**
Click "Already purchased this game?", enter in your purchase info, and hit "Register"

**6.5)Did you Register?**
Great!  Skip to step 7, "Reconfigure the Peggle Bottle".
Did you have "can't connect" problems when registering?  Oooooh boy - skip down to "High Weirdness".  And cross your fingers.

**7)Reconfigure the Peggle Bottle**
Close down any PopCap screens, then
in your still open terminal, type
```
winecfg
```
Under the Graphics tab, DEselect "Emulate a virtual desktop".

**8)Make a Peggle Launcher**
With luck a launcher shows up on your desktop, and it probably looks like
PeggleDeluxe.desktop
The first time you double click it, select "Mark as Trusted", and it should stop saying .desktop and transform to the Peggle icon.

But maybe you want to make your own launcher somewhere, sometime.  The key is to launch the game within it's own Wine prefix (the "Peggle Bottle"). 
To make a launcher in your panel:
Right click on your panel, and select "Add to Panel"
Double click on "Custom Application Launcher"
Type= Application.  
Name= Peggle
Command (this is key)= 
 
Include the quotation marks. 
Where it says NAME put in the name of your home directory.  For example, mine is env WINEPREFIX="/home/laura/.wine-peggle".
Click "okay".  Now you should have a launcher on your panel.


[SIZE="5"]**::High Weirdness::**[/SIZE]
Did you get the message from PopCap
"Registration cannot proceed
An error occurred while connecting to the PopCap web site
blablabla about firewalls and such" ?
Go ahead and close the PopCap windows, and read on.

As of this writing (December 20th, 2009), I get the following results from the following Wine versions -

Synaptic package "wine" (1.0.1) registers, but sound blows.

Synaptic package "wine1.2" (1.1.31) wont register, but plays beautifully.

WineHQ directions [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) (1.1.35) wont register, but plays beautifully.

MY fix, has been to downgrade Wine, register my PopCap game, then upgrade Wine again.  Then I have a registered game WITH sound.

I suspect with the countless configurations of PCs, and sound and video drivers and frequent Wine updates, quirks like this will be all over the place.  Remembering your mileage may vary, here is my "fix" of downgrading Wine.

To downgrade Wine:
**Remove Wine extra repositories**
Go into System > Administration > Software Sources
under the "Other Software" tab uncheck or remove any entries relating to Wine.  Mine is
"http://ppa.launchpad.net/ubuntu-wine/ppa......", previous versions start with "WineHQ".
Close Software sources, and "Reload" if prompted, then "Close" Software Sources.

**Remove Wine**
Go into System > Administration > Synaptic Package Manager
Search for Wine, and remove any Wine and Wine-Gecko packages you have installed.  They should look like "wine" or "wine1.2" (Don't worry about any Wine font or icon related packs.)

**Reinstall Wine**
Go into System > Administration > Synaptic Package Manager
Search for Wine, and select and install the package "wine" - this is version 1.0.1.

NOW, try registering again.

Upgrading Wine is a common enough task that I wont cover that here.


**[SIZE="5"]::Misc. Tips::[/SIZE]**
**3D Acceleration and "Nothing happens when I launch"**
In a Wine virtual desktop environment, PopCap games seem to be unaffected by "3D Acceleration" being enabled - that is, they look the same, and the gameplay doesn't suffer.
Outside of the virtual desktop environment, they crash, go blue, go black, or "do nothing" when you try to launch the games.

to UNenable 3D Acceleration:
Start a terminal, by hitting ALT+F2 and typing
```
gnome-terminal
```
Then export to your game "bottle"
```
export WINEPREFIX=$HOME/.wine-peggle
```
(of course replace "wine-peggle" with whatever your bottle is named, but in this walkthrough we're sticking with peggle)
Start Wine Configuration
```
winecfg
```
Under Graphics, select "Emulate a virtual desktop" and set it to 1024x768, apply, click "okay".
Restart your game (you can use the launcher you made previously) and now, in the smaller virtual desktop environment, you should be able to work your way to the options menu and DEselect "3D Graphics Acceleration".  I also disable the "Custom Cursor".  Because it's a punk.

Now exit the game, and in your hopefully still open terminal, again go into
```
winecfg
```
again into the Graphics tab, and UNselect "Emulate a virtual desktop", click apply, then okay.  Now it should be safe to close your terminal, and start your game as normal (double clicking your launcher).  Hopefully it will open right up, full screen, running beautifully with troublesome 3D NOT enabled.

**Quick Desktop Toggle**
If in the middle of a game you need to pause, and check email or some such,
CTRL+ALT+right arrow
is a great screen toggle!  Oh sure, your desktop is a horrible resolution, but it's accesible, and it's much quicker than shutting the game down.  And more reliable than ALT+TABbing your way to another window.  This is a handy tip for any full-screen Wine program.

**[SIZE="5"]::Help Improve::[/SIZE]**
Was this how-to useful? Dreadful?
How can I improve it?  Was it clear?  Do you have any questions?  Suggestions?
I'm open to feedback and would appreciate help in making this a better How-To!

I spent about two hours wracking my brains over the wine version/registration issues, so if anyone has insights as to what's going on there, or a better workaround or fix, please share!

Thanks!  Hope someone can find this helpful.

-zami

hi;
Will this work with the multi game cd?
It's two cd's over 150 I think.
And how about coping saved win games I would like to move two or at least one user over to nix an let him play his games .
I'll have to try this in a vm to see if his games work.

---

### Post by mahaganapati on 2010-07-16
What a great thread. I wish I had found it before buying Peggle from shockwave in stead of popcap games (it was cheaper). I tried your recipe anyway, but unfortunately it doesn't work - I can't register the game even if I downgrade wine (then the game doesn't even open anymore). I use wine 1.2rc7 (again) and when I enter my registration key I get the following message:

> ERROR
We're sorry -- the server has encountered an internal error (12) while processing your request. Please try again later. If the problem persists, contact Customer Support.

Any ideas?

---

### Post by goggins on 2011-06-24
This generally works as of 6/24/2011 except that the command wineprefixcreate doesn't work and isn't needed, the method works fine without it.

---

