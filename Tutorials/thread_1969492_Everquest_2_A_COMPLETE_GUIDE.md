---
title: "Everquest 2 A COMPLETE GUIDE"
date: 2012-04-30
forum: Tutorials
---

### Post by ExSuSEusr on 2012-04-30
This is my guide to getting Everquest II to run in Linux (Ubuntu / Mint).  A lot of people out there want to know how to get it working, and this is what worked for me.  Step by step.  I will take some time to break it down in more detail for the those new users to the OS.

I feel your pain - you love your SK, your Ranger, your Assassin and you love Linux.... and you spend hours and days trying to figure out how to marry the two  - only to have people tell you "Games don't work in Linux just play Frozen Bubble and be happy."  I know, I know you want to reach through the screen and choke the hell out of them, but just remember they are not gamers, they don't "get it."  I do, so that is why I put this together - and I hope it helps at least one of you get your game on.

First, I don't run Ubuntu, I run Linux Mint (which is based off Ubuntu/Debian).  So, this walk through *should* work for you too.  

It took a while and a lot of pain and trial and error to figure it all out, but in the end it isn't as hard as you might think.

_**Steps**_

Make sure you have the correct drivers for your video card installed.  To do this:

Open a terminal and in the command line type -

> lspci | grep VGAThat will tell you what type of card you have installed.  You should get something like:

> 01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2)Go to your "Systems Settings" and click "Additional Driver" under "Hardware"

[I]I think it's the same in Ubuntu as Mint.... if not ask, someone here will correct me.

[/I]You should see something like:

[IMG]http://i808.photobucket.com/albums/zz4/cam727_2010/EQ/settings.jpg[/IMG]


Now make sure you have direct rendering working. Open the terminal if you closed it and type:

> glxinfoAbout the third line down it should say "[I]direct rendering = yes." 

[/I]Ok, now you see that your video card is properly installed with the right drivers - we can move on to the next set of steps.

You will need the following applications:

WINE
WINE TRICKS

There are a couple of ways to get these.  First, you can use Synaptic or you can use the terminal.  I use the terminal, but if you're new to the OS I would suggest using Synaptic.

Open Synaptic and select the following:

Wine 1.3
Winetricks 
Wine
gnome-exe-thumbnailer
wine 1.3 gecko

Select "Install" and wait for the applications to finish installing.

Now you notice there is a selection for **PlayonLinux** - this is a great application.  So, I will take a few moments here to talk to you about it.  IF you have a dual boot machine and you already have EQ II installed on your Windows partition you won't need it.  But, if your machine is all Ubuntu / Mint then I would suggest installing it.  It is a front end app for wine.  It is pretty sweet as it makes installing Windows app's easier.  

If you already have EQ running on another partition you can just copy and paste the contents at the end of your set up.  If you do not then I would suggest installing PlayonLinux.  Hell, just go ahead an install it in case you want to install MS Word or other apps later.  Nuff said.


Anyway....

Ok, so now you've got the video card read, you've got Wine installed.... what now?

YOU MUST HAVE ttf-mscorefonts installed.  IF YOU DON'T THE GAME WILL NOT LOAD.  The launcher need "Arial."  Follow the instruction here:

[http://ubuntuforums.org/showthread.php?t=1089577](http://ubuntuforums.org/showthread.php?t=1089577)

You must have these fonts, or the game will not load.

Ok, moving on.....

Now, you need to make some changes to your "regedit" for Wine.

Open your terminal and type:

> regeditLook for an option called "HKEY_CURRENT_USER" and expand it.  If I have to explain how to expand it, then throw your computer out the window... cause.... well....

Ok how that you have it expanded  go to "Software" and then "Wine."

You are going to need to add some strings that aren't there.  This is where a LOT of EQ'ers go wrong in trying to get the game working.  They forget to edit the registry.


Right click on "Wine" and select "New" then select "Key"  Type Direct3D and hit enter.

Now, right click on the newly made Direct3D key you just made and select "New" then select "String."

Now to the right you should see your newly created string.  Right click on it and select "Modify."  

Where it says "Value Data" type: **opengl** 

Ok, I bolded that so you'd see it... if you dare ask how to bold text......

Now, that's the first string you need.

DO THE SAME PROCESS ABOVE FOR THE FOLLOWING:

String name - OffScreenRenderingMode
Value data - fbo 


String name - PixelShaderMode
Value data - enabled

String name - RenderTargetLockMode 
Value data - texdraw

You're now finished with that step.

Now open up your Wine Configuration application.  You can find this through your Applications menu.

It will look like this:

[IMG]http://i808.photobucket.com/albums/zz4/cam727_2010/EQ/regedit.jpg[/IMG]

Go to the "Graphics" tab and uncheck the "Allow Windows manager to decorate the windows"

And close out.

So far so good... I hope.

Now if you have EQ installed on your Windows partition you can browse to the "EverQuestII.exe" and right click on it and select "wine" as your program to run it.  

It should start up and run.

You MAY have to go into your Windows partition and configure our EQ.ini to windowed screen and not full screen.  Full screen is hit or miss if it works.  I run windowed so I can browse Milfhunter.com while playing...  Kidding!  I run windowed mode because full screen has crashed on me. And, if you're running compiz for the 3D cube, full screen.... it's bad... let's just leave it at that and drive on.

Ok - so if you do NOT have a Windows partition - this is where PlayonLinux comes in handy.  Start it up and in the search box type: "Everquest II."  You see an option for the SF expansion.  Install it.  It will take a while....

Now, PlayonLinux will not store the game file in your .wine directory.  If you don't know what I am talking about.  A dot in front of folder hides it.  I use it to hide my adult videos from my GF... kidding again... seriously.  But go your "Home" directory and goto "View" and select "show hidden files" - then you'll see everything that's in your home directory.  If you goto .wine you will not find EQ  - that is if you installed it with PlayonLinux.  

Now for those of you who do have it installed on a W-partion..... just copy the "Sony Online Entertainment" folder from your Windows partition and paste in your in your "Program Files" under .wine.  

I am too lazy and tired now to explain how to create a wine launcher on your desktop.

Serious, all, I hope this helps you new Linux users / gamers.  And as I said before this worked for me with Linux Mint - but it's based off Ubuntu so I can't see how it wouldn't work for you too.

Couple of more points I forget to mention - hence the edit.

1.  I can't get voice to work.  I have tried and tried, but it seems beyond my skill level.  In fact when voice is active is makes the game slow and sluggish.  SO, at the char select of your character go to Options and turn voice chat off.  

2.  Running EverquestII.exe does NOT update (if your playing from a partition).  For this I have seen that running EQ2.exe will update.  Y'all know the game patches once a week.  If you do not have the current patch the game will not load.

This isn't perfect because for some reason the Linux God's haven't gotten it through their heads that real gaming is a serious issue for a billion computer users worldwide - but that's a rant I will save for later. World of Warcraft alone has over 20 million world wide... that's just one game... you do the math.

---

