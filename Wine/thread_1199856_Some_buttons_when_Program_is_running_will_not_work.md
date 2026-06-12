---
title: "Some buttons when Program is running will not work ??"
date: 2009-06-29
forum: Wine
---

### Post by hufferd on 2009-06-29
I am not sure if anything can help me or not.


No cracks about the game please LOL But I downloaded "Plant Tycoon"
This was after I saw it in the winhq.org web sites **Platinum list** (*ie. Applications which install and run flawlessly on an out-of-the-box Wine installation*)

So I installed the game and it did install with no errors how ever the very first screen that comes up in game you must select 1 of three button options to move forward... :( This is where the issues start. All the buttons seems to push when clicked with the mouse  but **NOTHING HAPPENS** :( You can click to close the box hoever that takes you to a "timed demo" ver or the game I need to select one of the other buttons so I can input my key... For the full ver. :( 

The game works in VB but it runs slow and the sound stops working from time to time...


Any ideas as to what I might be able to do to fix this....  So I can use wine rather then running this game in VB?  

Side note and a bit of a vent:  I love ubuntu / linux.  Will never go back to windows BUT there are some other apps I would like to run in wine as well..
I have never been able to get much of anything to run right with wine.  That is why I have installed a VB. Very much disapointed in wine...  

Anyway any help would be great 

D

---

### Post by ackanao on 2009-06-30
Hi hufferd

There are some "scripting" issues - I think these functions are not yet (or not well) implemented in Wine (wine-gecko to be precise). First I tried to set some "overrides" to make buttons work but I failed.

I would really like to someone prove me wrong about this but it seems to me that the only way to make this buttons work is to install IE6.

Same issues can be expected with similar games too so I think the best way to make these games work is to make new wineprefix, install IE6 in it and then use that wineprefix for every game that needs IE.

To create new wineprefix use this command (I've named it "Stupid-Games" because of these issues):
```

WINEPREFIX=~/Desktop/Stupid-Games wineboot

```

Download winetricks:
```

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

```

Use winetricks to install ie6:
```

WINEPREFIX=~/Desktop/Stupid-Games sh winetricks wsh56 msxml3 ie6

```

Install game:
```

env WINEPREFIX=~/Desktop/Stupid-Games wine /path/to/Game/Installer/PlantTycoon_Setup.exe

```

Start the game:
```

env WINEPREFIX=~/Desktop/Stupid-Games wine "C:\Program Files\Plant Tycoon\Plant Tycoon.exe"

```

Active Scripting should be functional now so you can use "Unlock" button to enter your serial number.

---

### Post by hufferd on 2009-06-30
Ackano,,

Oh my thank you for all your work --- I am at work as I read this but I will try this.  When I get home and let you know if it all works out...  

Thank you for spending the time to look into it... 

Very much thank you  :) 

:KS

---

### Post by hufferd on 2009-07-01
Still having issues with this something happened during the ie6 install i got and error I did not save the out put but I will try again sometime today :)

---

### Post by ackanao on 2009-07-01
@hufferd

Maybe one of the servers was down so winetricks couldn't complete with download; If problem persists, delete "/.winetrickscache" folder and try again... Also if you messed up your wineprefix, delete it and create new one.

If you still have problems let me know...

---

### Post by hufferd on 2009-07-01
> **ackanao said:**
> @hufferd

Maybe one of the servers was down so winetricks couldn't complete with download; If problem persists, delete "/.winetrickscache" folder and try again... Also if you messed up your wineprefix, delete it and create new one.

If you still have problems let me know...

ie6 installed and directories are up and running but no buttons :(

---

### Post by hufferd on 2009-07-01
> **hufferd said:**
> ie6 installed and directories are up and running but no buttons :(

Question and it just hit me even though I have installed ie6 is wine still trying to use gecko???  Do I need to uninstall gecko now that I have installed ie6?

---

### Post by ackanao on 2009-07-01
I've just tested again, downloaded from Plant Tycoon homepage ([http://www.planttycoon.com/]("http://www.planttycoon.com/")) and did almost the same thing I did before (this time I choose to install only ie6 with winetricks).

I've created a new wineprefix (Tycoon) on my Desktop:
```

WINEPREFIX=~/Desktop/Tycoon wineboot

```

Choose to install ie6 with winetricks:
```

env WINEPREFIX=~/Desktop/Tycoon sh winetricks ie6

```

Then I install Plant Tycoon (Plant Tycoon installer is placed on my Desktop):
```

env WINEPREFIX=~/Desktop/Tycoon wine /home/ackanao/Desktop/PlantTycoon_Setup1_00.exe

```

Finally I started the game:
```

env WINEPREFIX=~/Desktop/Tycoon wine "C:\Program Files\Plant Tycoon\Plant Tycoon.exe"

```

When I click "Unlock" button, new window appears - I don't have serial number but "Enter Key" window accepts my inputs.

Which version of Wine do you use - I'm using the latest one (1.1.24). You don't need to uninstall wine-gecko.

It really bugs me that I can't explain things better - sorry for my bad english... I've sent you a private message but I'm not sure if it's forwarded or not.

---

