---
title: "Running Killing Floor Retail Version"
date: 2009-05-14
forum: Wine
---

### Post by beastrace91 on 2009-05-14
So the UT2k4 mod "Killing Floor" went retail today via steam. It installs just fine through Wine and loads up. How ever oddly enough it has the same issue of the mouse "catching" and not working properly in game as native UT2k4 does with Compiz running. I am tried turning off compiz (no effect) I am tried running inside and outside a virtual desktop, along with toggling all the different check boxes that can affect the mouse in the 3d section of the winecfg Anyone else have any idea what else I can change to maybe get my mouse working properly? The hangs make the game un playable :(

~Jeff

---

### Post by asdfoo on 2009-05-15
> **beastrace91 said:**
> So the UT2k4 mod "Killing Floor" went retail today via steam. It installs just fine through Wine and loads up. How ever oddly enough it has the same issue of the mouse "catching" and not working properly in game as native UT2k4 does with Compiz running. I am tried turning off compiz (no effect) I am tried running inside and outside a virtual desktop, along with toggling all the different check boxes that can affect the mouse in the 3d section of the winecfg Anyone else have any idea what else I can change to maybe get my mouse working properly? The hangs make the game un playable :(

~Jeff

[http://wiki.winehq.org/KnownIssues](http://wiki.winehq.org/KnownIssues)

Bug 6971 - Mouse "escapes" window or is confined to an area in the full screen program 

There might be a patch floating around, but otherwise check the AppDB for other versions of UT which also suffer from the problem, it's probably explained there too.

---

### Post by beastrace91 on 2009-05-16
Ahh thank you, I found a fix under the Red Orchestra game (another UT2k4 Mod released under steam), now if I could just get it to stop crashing on me... lol Ahh... back to the testing

~Jeff

---

### Post by kdorf on 2009-05-16
If it's really a UT2K4 mod, perhaps there's a way to get it running in the native Linux version.

---

### Post by beastrace91 on 2009-05-17
It WAS native on Linux, and then the retail release via Steam ended that. At any rate I got it working with out dumps (at least I think played for a solid half hour or so) posted it up on winedb home I did it.

~Jeff

---

### Post by kawrea on 2009-05-17
Could someone please help me with getting the mouse issue to work, I'm totally new to ubuntu and I'm using 9.04 x64 
the menus run and stuff I can't click the ready button or any others in the waiting for players thing thanks

---

### Post by beastrace91 on 2009-05-17
Alrighty the following fixed the mousing issue for me.

1.) Download the [file](http://fxlegrand.free.fr/winehq/index.php?page=patches) from here

2.) Run the following in terminal (be sure to cd into the directory where you downloaded the file to first)

```
sudo cp -p /usr/lib32/wine/dinput.dll.so /usr/lib32/wine/dinput.dll.so.old
sudo mv dinput.dll.so /usr/lib32/wine/
```

Restart steam and then reload KF and you should be all set.

Also as a side note, I had to go into the display options in KF and toggle "motion blur" off to fix the crashing issue I was having.

Best of luck,
~Jeff

---

### Post by Gondee on 2009-10-12
Hey, sorry for bringing back a dead thread, but, for some reason i have no folder called wine in the lib 32 section, so where would i put that file?

Edit, I do however have those files in the folder lib, does that work just as well?

---

### Post by beastrace91 on 2009-10-13
I'm assuming you are using 32bit Ubuntu? If so yes - just put the file in the lib folder (the lib32 is only on 64bit installs)

Just as a heads up KF is still rather hit or miss. I run this same patch under Codeweavers & sometimes it works and sometimes it doesn't (rather fickle) Let me know if it works well for you under the latest Wine release :)

~Jeff

---

### Post by Gondee on 2009-10-13
Thanks, i appriciate the help, it seems to run fine for me a dead mouse every so often though.

---

### Post by beastrace91 on 2009-10-13
Anytime, glad to hear you got it working.

~Jeff

---

### Post by L33tN1nj4 on 2009-10-18
Ugh.. Hey im trying to get this game to work and the Fxlegrand.free.fr link has no file for me to download, so i cant do the rest of the bug fix because i dont have the file, anyway im running on 64x and i use firefox as a browser, does firefox not allow me to download the file or something?

---

### Post by beastrace91 on 2009-10-18
The site that hosts that file changed itself around a small bit so that link I had posted earlier no longer works - the updated url can be found [here](http://fxlegrand.free.fr/winehq/index.php?page=patches)

~Jeff

---

### Post by Arron Thornhill on 2009-11-16
Hi there,

erm i really hope someone can help me with this. I have been following the guide and so far i managed to download the dinput.dll.so file, but when I try to copy it into the usr/lib/wine directory, the terminal says: cp: cannot create regular file `/usr/lib/wine/dinput.dll.so': Permission denied

Does anyone have any ideas?

Thanks in advance.

---

### Post by beastrace91 on 2009-11-16
Prefix the command with **sudo** - you need to be super user to write the that part of your hard drive.

Cheers,
~Jeff

---

### Post by Arron Thornhill on 2009-11-17
Thanks for getting back to me so quickly, as you might have guessed I am still new to the whole Ubuntu thing... the mouse fix seems to be working really well.

Thank-you!

---

### Post by beastrace91 on 2009-11-17
Most excellent, glad you got it working.

~Jeff

---

### Post by Shelton2142 on 2010-02-14
Sorry to bring this old thing up, but I was wondering what beastrace meant by "cd into the directory where you downloaded the file".

Also, I am having trouble making the terminal work. Whenever it comes up asking me for my password, it won't let me type anything. I hit the keys but nothing shows up.

---

### Post by beastrace91 on 2010-02-14
I suggest you learn some basic terminal commands, then those instructions would make a lot more sense. "cd" refers to "change directory" and as for your password, the system never shows any characters you are entering. Just type the characters and then press enter.

Regards,
~Jeff

---

### Post by Loctrice on 2010-06-28
I posted what I found at wine hq:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16616](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16616)

Here's basically what I did:

I had to get it opening on virtual desktop so lucid wouldn't kill it. After doing that I muddled with the settings for a long time. You have to turn the motion blur off, and set the full screen off. Then I shut off the wine desktop and set the rendering in the ini file to opengl rendering mode. After this, I found a resolution that lucid was happy with , and was still big enough to keep the mouse inside during panic attacks killing zombies. Lucid will not let the application full screen, you have to find a resolution that works because it will not keep the mouse inside your game screen.

I played solo, and was able to join other steam buddies online. The faults I still have are joining online through the internet menu. When I can get in one (setting the filters to keep out empty and password and just clicking fast) then I can last up to the second wave before crashing, so it's only really do-able if you join from a buddy link. 

Aside from that the gameplay is fast, and the maps load so much faster then they do in windoze. I hate playing this game in windoze, it's horrid and gets worse with each new update.

Hopefully what I found can get some more , who know more then myself, to help us patch the rest of it. 

Regards,
Steve

---

### Post by Loctrice on 2010-06-29
Well, rc5 just got installed here. I can use the 3d rendering now for solo play, but I havent tested online yet. I still can't join online with the opengl rendering mode either. The only issues I have as of right now :


1 - can't get online through internet list. It's on loading the list itself that it closes with an "unusual exception" error. It's something to do with how they are connecting and gathering the list, which is quite a bit out of my area.

2 - I can't get my mic to work in game at all when I join an online game through my buddy connections.


The game plays fine, especially solo with the 3d rendering object (thanks wine). It is still fun online and works well with the opengl (providing you have the window big enough). There's a small mouse glich, but nothing that is to hard for me to work around. It is just if you go to one side to much then eventually you leave the box even though it's maxed on width with the screen. A simple enough fix, you just turn a circle in the other direction and you are centered. The mouse relocates itself to center at the shop anyway, and since I blast zombies w/the best of them I usually am fine with making it to the trader :)

Anyone know how I can lock the mouse in the box, and get the internet join to work? The topic seems dropped at winehq and all the mouse fix links are outdated (mostly broken links). Seriously, I can deal with the mouse I'd really like to find out what the exact problem is with the internet list/join so that I can find a work around.

Must...blast...zombies...(to rock music even)

---

### Post by beastrace91 on 2010-06-29
The best way to get this game to work under Linux is to just use Cedega. Works nearly 100% OOTB on there last time I used it.

~Jeff

---

### Post by Loctrice on 2010-07-05
Looked into it. With cedega, who seems to be the only one who has killing floor posted as runable, I was a bit dissapointed. It doesn't work out of the box. It's not close to out of the box. With some configuration, you can get it running. You can't get support on it (at least not before you grow a beard) , because it's not certified by them. Also, the site was not correct. It listed it as "green checkmark" and it wasn't . the engine that said it worked best with wouldn't even attempt to run. I added my feedback, and of coarse it didn't show up. Still shows as a green check , and good to go.

With no support, empty chat rooms, etc... To be fair, it was not to terrible to configure. I noticed they use a wine process as well, and gambled that adding the fix commands to the command line would work, and it did. You also need to disable motion blur, and compiz to name a few things. It only cost 45 dollars for a year, which is not to shabby at all to get support (on games they do support). I thought I was paying for support, but turns out I was paying to use a different set of forums, and something that's maybe a little easier to configure. I can't say about their app database games that they sponsor, I can only say killing floor is not one of them, and I believe their website is advertising (i.e. not correct posts).


In the end, it was not expensive and it did run with some configuring. I have fought with this game for a couple months, so it seemed pretty quick and logical to me. It was definately worth the money just to get it going in linux, heh. They say codeweavers and one other can run killing floor, but from all my google searches cedega is the one that runs it, and supports (with their "seal") many of the other steam games as well.

It doesnt seem like a bad product at all, and I got kf running. I'd thank them for making some software that worked and making it affordable if I could ever get ahold of any of them.

---

### Post by beastrace91 on 2010-07-06
> **Loctrice said:**
> Looked into it. With cedega, who seems to be the only one who has killing floor posted as runable, I was a bit dissapointed. It doesn't work out of the box. It's not close to out of the box. With some configuration, you can get it running. You can't get support on it (at least not before you grow a beard) , because it's not certified by them. Also, the site was not correct. It listed it as "green checkmark" and it wasn't . the engine that said it worked best with wouldn't even attempt to run. I added my feedback, and of coarse it didn't show up. Still shows as a green check , and good to go.

With no support, empty chat rooms, etc... To be fair, it was not to terrible to configure. I noticed they use a wine process as well, and gambled that adding the fix commands to the command line would work, and it did. You also need to disable motion blur, and compiz to name a few things. It only cost 45 dollars for a year, which is not to shabby at all to get support (on games they do support). I thought I was paying for support, but turns out I was paying to use a different set of forums, and something that's maybe a little easier to configure. I can't say about their app database games that they sponsor, I can only say killing floor is not one of them, and I believe their website is advertising (i.e. not correct posts).


In the end, it was not expensive and it did run with some configuring. I have fought with this game for a couple months, so it seemed pretty quick and logical to me. It was definately worth the money just to get it going in linux, heh. They say codeweavers and one other can run killing floor, but from all my google searches cedega is the one that runs it, and supports (with their "seal") many of the other steam games as well.

It doesnt seem like a bad product at all, and I got kf running. I'd thank them for making some software that worked and making it affordable if I could ever get ahold of any of them.

Haha yea... Cedega support BLOWS. Sorry for the misleading information - last time I played KF through Cedega it was a couple months back, I know they have done alot of updates since then to the game.

Regards,
~Jeff

---

### Post by 2Karl on 2010-07-28
regarding the mouse issue, open regedit and set HKEY_CURRENT_USER/Software/Wine/DirectInput/MouseWarpOverride to "Force"

You may need to create the "DirectInput" key and "MouseWarpOverride" string value.

---

### Post by cyvi on 2010-12-28
> **2Karl said:**
> regarding the mouse issue, open regedit and set HKEY_CURRENT_USER/Software/Wine/DirectInput/MouseWarpOverride to "Force"

You may need to create the "DirectInput" key and "MouseWarpOverride" string value.
This doesn't work for me, aend this seems to be the only bug I have. Any other workaroudns for the mouse bug? 

Edit: running Ubuntu 10.10 with Wine 1.3.10

---

