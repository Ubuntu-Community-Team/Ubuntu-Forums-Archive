---
title: "XFire Jaunty - How to get it working guide"
date: 2009-06-08
forum: Wine
---

### Post by Poyntz on 2009-06-08
Hey folks,

I'm posting this up because I know there's a hell of a lot of people who can't get the latest xfire working in Jaunty (Ubuntu 9.04) and that it's frustrating that there are a few that have but most haven't posted anything up!

Given the amount of time I've spent trying to get this to work and discovering that it was actually quite simple is also quite frustrating.

First of all I'd like to mention that XFire will NOT run perfectly (at least according to my method), in fact it will be extremely buggy and if you make a wrong move it will crash. The good news is it WILL run, it will let you chat, it will recognise your games, it will save your game status to the xfire server, etc.

Also, you will have to register an xfire account on the site. Trying to do it on the application will crash wine, if your app is anything like mine.

Anyhow, if your problem was anything like mine the first thing that popped up was a **register new user** window. Ok. [COLOR="Red"]Click NOWHERE on the pane because it will will introduce a COMCTL32 error.[/COLOR] This error, for all I know, is not solvable, even if you do install all the COMCTL32 apps, etc. via winetricks. 

Where you can click is the left hand side of the top panel (for the registration window). (Yes. You need to close the registration window to interact with xfire.)
More explicitly, the far side from where you see the "X" button which designates close. The "X" button will crash xfire btw :P
Now once you click on the icon on the left hand side of the panel it will open up a small menu which will allow you to select close from the options. Do so, and the registration window will close.

Now you have access to Xfire, but it won't let you do anything until it has scanned for games on your system. You'll have to wait for this to finished (yes, very annoying, and it will scan for games every time you start it up). Once it has failed trying to find your games it will allow you to log in. Remember: YOU CANNOT CLICK ANYWHERE IN THE PANE. So you're going to have to use the tab trick. It should hopefully place a cursor in a field for you though. 

[ATTACH]116845[/ATTACH]

So basically **enter your [B]username**[/B], press the *tab* key, **enter your [B]password**[/B], press the *tab* key, hit **ENTER**. Easy, right? and that will log you in :D

[COLOR="Red"]NOTE: Do not try to tab to Auto log in or anything similar - if you hit space to try to check the box it will also crash wine.[/COLOR] 
Inconvenient,eh?

Once you're logged in it will tell you you're **offline**. I know mine says I am online but that's because I've already logged in a few times. [COLOR="Red"]Please DO NOT attempt to click on tools to change this because like everything else, it will crash wine.[/COLOR] In order to go online you have to open up your game from Applications -> Wine -> Programs. Yes... Xfire is still running even though you probably can't see it anymore...

[ATTACH]116842[/ATTACH]

Once your game opens you will see a strange popup window in the game which will tell you Xfire is enabled but you are *offline*. I've used Jedi Academy: Multiplayer for this example

[ATTACH]116843[/ATTACH]

Unfortunately it disappears nearly as quickly as you see it, but don't worry about that. In order to chat whilst in your game you need to press **Scroll lock + X**.

Now whether this means:
Press X immediately before Scroll Lock
or, Scroll Lock immediately before X
or, both simultaneously
- you'll have to figure this out for yourself. Just try all the combinations until the chat screen pops up.

[ATTACH]116844[/ATTACH]

Now here's the really cool part. You can click on your friends in the chat screen!!! :D, and then click the Speech bubble button on down the bottom to launch a chat. Then, you can type your messages, hit the Enter key and voila, you're chatting.

Now to get rid of this screen just click anywhere in the area of your game. Oh, and yes, you'll need to be running a game in order to launch chat (at least to my knowledge). If anyone knows a way around this please reply with it.

Now in order to get your game loaded into Xfire you need to either join a server or create an online game while xfire is running. Once you spend a little time on the server, Xfire will send your information to it's server and your statistics will be uploaded.

**Additional features:**
- If you wish to know what the in game key binds are for Xfire, right click the Xfire icon in your status bar. Mouse over on **Launch** and then click on **Detect Games**. Click on the **Chat** tab once it opens the window, and voila, your key binds. 

[COLOR="Red"]NOTE: Trying to tick any of the boxes, tabbing and pressing space, or clicking anywhere will crash wine again, just like it did in all the other cases.[/COLOR]

- The buttons you can click on from the main menu are the buttons circled below.

[ATTACH]116846[/ATTACH]

That's all I can think of at any rate. Best of luck, and feel free to reply if you have any questions or think there's anything I've missed

---

