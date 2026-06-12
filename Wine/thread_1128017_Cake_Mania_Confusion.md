---
title: "Cake Mania Confusion"
date: 2009-04-17
forum: Wine
---

### Post by bluepop13 on 2009-04-17
I downloaded the free trial of Cake Mania from PopCap games from a Wine page in here and it installed just fine and works like a charm. No complaints, none. 

I've already bought the game over a year ago and I tried putting in my email and the last 4 of my debit card number to get it to work right off the bat but I have a different debit card so it wouldn't recognize it.

My problem:
I downloaded it from Yahoo! Games, where I already bought it back when. I tried running it with wine and it comes up just fine to ask me where I want to install it. I must not be installing it in the right place because a screen pops up after I finish installing it and try to run it that says the page is offline or something.

Now, it shows the icon for the game when that screen pops up. When I see the wine symbol it comes up with an error when I try and run it. I'm lost and just glad to know that the game actually works this well in Linux. I'm new to learn still... Quite a bit.

Any help would be really appreciated. Thanks!

Eric

---

### Post by zami on 2009-04-17
I've been trying to install CakeMania myself.

A couple of things... 

What you are seeing is the Yahoo! "Play with Adds / Buy now" menu attempting to load. You should be able to fix that by either getting Gecko setup properly, or installing IE6.  (More on these options in a moment.)

But!  I think regardless, you might be out of luck with the Yahoo!Games flavor of that game.  I've been trying to get it to run all morning (I'd rather watch ads than shell out $20 just now), and getting no where with it, and doing some searches for "Wine Yahoo!Games" yielded really unpromising results.  

However!  The installer from PopCap gives me a game that runs just fine!  And I've successfully installed and registered PopCap games before with no problem, after installing IE6.  (The trial runs fine as you've experienced, but to buy/register/etc you need either Gecko setup just so, or IE6.)

For what it's worth, for PopCap games I'd go with the IE setup.  Written out it looks more confusing than it is - I promise!  I swear PopCap and IE are in cahoots because I simply could not connected to the PopCap registration servers via Gecko.  But once I installed IE, it was smooth as silk.

To setup Gecko:
Good instructions here - scroll about halfway down to "Install the Wine Gecko IE engine"
[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)


To setup IE6:
This IS known to "break" already working Wine setups, so I strongly recommend you make a new wineprefix just for Cake Mania.  This is very easy, and I actually recommend a separate Wine prefix for all Windows programs.  If you want to try this...
open the terminal ( **ALT+F2** then enter **gnome-terminal** ) and enter the following commands, one at a time.  Do not close down the terminal until you are through all the commands.  If you have to shut down terminal, run the first command again (the export command), and then pickup wherever you left off.


```
export WINEPREFIX=$HOME/.wine-cakemania 
```
This tells this instance of terminal to use ".wine-cakemania" instead of ".wine"



```
wineprefixcreate
```
this will actually build your new prefix called .wine-cakemania in your home direcotry.  If you can't see it in your home directory, hit CTRL+H.  At this time it's not important to see it, but I think it helps to know what's happening.



```
wget -nv http://www.kegel.com/wine/winetricks
```
this downloads the program "WineTricks" to your home directory



```
chmod 700 ./winetricks
```
allows you to actually run winetricks.  You wont see much happen.



```
./winetricks ie6
```
this tells WineTricks to install Internet Explorer 6. This is an 11mb download so it might take a few minutes. If you get a message that you need to install "cabextract" that's fine, just run
**sudo apt-get install cabextract**
then try **./winetricks ie6** again

Now you'll need to reinstall CakeMania to the .wine-cakemania prefix, and you'll have to do it from the terminal to get it to install to .wine-cakemania instead of .wine.  (Again, make sure you are working in a terminal in which you've run that first "export" command, or run that "export" command again.) So, if you have "CakeManiaInstall.exe" on your desktop, you need to

```
cd Desktop
```
this changes your current directory from /home to /home/Desktop



```
wine CakeManiaInstall.exe
```
has wine launch the .exe file

That should about do it!

You should have a new Wine launcher.  If it's on your desktop, right click on it and select properties, just to double check it's launching the instance you just installed - the one in .wine-cakemania, not the old one in .wine.  In the box labeled "Command:" you should see something like this
**env WINEPREFIX="/home/YOURNAME/.wine-cakemania" wine "C:\Program Files\PopCap Games\Cake Mania\CakeMania_data.exe"** 
(If you didn't get a new desktop launcher, look in your menu for 
Applications>Wine>Programs>PopCap Games>Cake Mania> Play Cake Mania
right click and select "add launcher to desktop".)


That does stink if you have to re-buy the game from PopCap though.

Maybe once you get Gecko or IE going, if Yahoo! can resend your purchase info, maybe you can get it registered and it will run?  From the errors I'm getting I think the Yahoo version just isn't running because it's getting hung up on serving me ads - I think I just don't have the right setup to veiw the ads, so I don't get to play the game.

Good luck.

-zami

---

