---
title: "What happened to my WINE?"
date: 2010-09-07
forum: Wine
---

### Post by Arthur Yarbrough on 2010-09-07
I will not lie, I am very new to Ubuntu so I do not have the knowledge or experience that others have. Im 17 years old and I know how to do very few things via. terminal, and to be honest installing Ubuntu was a last resort for me. (Our computer became unstable and it seemed to be the only thing that would get it to work again.) Regardless I am slowly learning, so please bear this in mind. (:

Now to my problem. I have been using WINE since I got Ubuntu to run all my native Window programs and at first it worked great. For a long time I used Game Maker ([www.yoyogames.com](www.yoyogames.com)) even though I had to use the old version of 5.3 as opposed to the newest version 8. It worked great! Eventually I even got "The Elder Scrolls III: Morrowind" installed onto my system and, like Game Maker, it worked perfectly for me in WINE. (Installing Morrowind taught me a lot about Ubuntu functions, maybe more so than anything else to date. Through the long time it took me to figure out how to install it I figured out cd, loop mount, and alot more.) 

But now something weird has happened... out of seemingly nowhere, WINE has been completely backfiring on me! Some programs still work for me, smaller programs, but the two I mentioned above (and my two primary reasons for WINE in the first place) have gone crazy. When I tried to run Morrowind after a long time, I got a weird error message stating the renderer or something would not work. (I will give an exact error message later, as I have to reinstall Morrowind and its become an issue too. Ill describe why below.) So, desperate to play the game again, I decided to see if there were any updates for Ubuntu.

Doing this I figured out there was a whole new version of Ubuntu so I installed it! Also, before doing so I backed up all my old files onto a flash drive and created a new User with the same admin privileges as my old one because my old User folder had become so crowded I wanted to begin anew. This worked fine and I hoped after the update, and reinstalling WINE, the problems would be fixed. Alas, I did both, and neither problem had been fixed.

I tried to run Game Maker after reinstalling it, and it ran fine. Version 5.3 like I had always run before. This time though, when I attempted to run or test my games I would get two errors. One stated "Failed To Initialize DirectDraw" and the other which popped up immediately afterwards said, "Failed To Initialize DirectX." I searched everywhere but could not find a solution. I tried manually installing DirectX in WINE but, even afterwards I could not open the "dxdiag.exe" which my instructions told me if I could run, meant DirectX was running fine in WINE. The catch was most the steps in installing DirectX I was able to skip, because in reality the more I looked at it the more I believe DirectX was already installed, I just reinstalled it and it still didn't fix the errors. 

Looking at the Wine Apps site it told me that Game Maker 7 would now be able to be run with the latest WINE. (And yes I know I have the lastest version.) so I tested it. It gave me an error when I tried to run my games stating, "Failed to initialize D3D. Old graphics cards do not support this." and something about DirectX 8 at least. I know my gfx card is good enough, because I ran it perfectly when I had Windows. (And even GM6 on WINE a few times before, which is the version when the error first begins to pop up so I know its possible in WINE because the error just started showing.) I tried updating my gfx drivers through Synaptic... or at least I think I did. I may relook through them but im sure I did. o.O Anyways yeah, this error has been really bugging me because no matter what I do I cant fix either one, the Morrowind Rendering Error or the Game Maker DirectX Error.

Oh, and to top things off (Im not sure if WINE is causing this or not, but ill go ahead and put it here.) when I use the "mount -o loop morrowind.iso /CDROM" which ive used litterally hundreds of times to mount my Morrowind disk image, and even reinstall quite a few times (curse you game-breaking mods!) it always worked fine. Now its giving me the same error as if I had tried to run the installation without mounting the disk first, "Failed To Initialize IKernal" or something. This was my biggest error and what took me the longest to figure out how to install Morrowind but ever since ive learned to mount to my CD-Drive it hasn't happened once since... so why has it started again now?

The final thing, which might or might not be related to the above paragraph, is ever since I upgraded my Ubuntu and reinstalled WINE, I had to go to an .exe files properties and set the "Allow Executing File As Program" to yes (or checkmarked) otherwise WINE couldnt open it and gave a "blocked Wine/Unix" type of error. Before this happened by default, but now its not and it got annoying to the point of going in and taking out the portion of the command line which checked for it in the wine.desktop file where it said

```
Exec=cautious-launcher %f wine start /unix
```

I changed it to

```
Exec=wine start /unix %f
```

And it solved THAT problem, but none of the others. Does anyone have any clue if this has anything to do with the errors possibly?

I know this was long, and I have a lot to learn, but any help would be appreciated. Once I can get my Morrowind properly installed again i'll give an exact error message but my guess is the problem must be similar to the one from Game Maker as it relates to not being able to Render and that relates to DirectX if I am correct. So yes any help will be very much appreciated!

---

### Post by dino99 on 2010-09-08
wow, for a first post, its a long one :o

you might need to install all (or some of) the directx file from winetricks

into a console: sh winetricks

---

### Post by dirghrabadia on 2010-09-08
Apart from the directx installation, I would check on [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if the application/game has a good enough rating to run it under Wine. Platinum list is your best bet. Good luck with the learning process, its sure worth the toil and fun :)

---

### Post by Hairy_Palms on 2010-09-08
> **I tried manually installing DirectX in WINE**
this is guaranteed to mess up wine, my suggestion after doing that is to nuke your /home/username/.wine and start again

---

