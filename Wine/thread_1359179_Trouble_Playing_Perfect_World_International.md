---
title: "Trouble Playing Perfect World International"
date: 2009-12-19
forum: Wine
---

### Post by seventhreason on 2009-12-19
So I've been dual booting between Ubuntu and Winxp for a while now. I do all my school work, essays, projects, research (amazed by the research tools available) on Ubuntu, while the only reason I have kept Winxp is because I want to play my lovely game Perfect World International from time to time. Now I have finally decided to just get rid of Winxp. 

So I backed up all my important files, downloaded the latest Ubuntu version 9.10 and performed a fresh install. 

This is the basics of my laptop:

Intel IBM T43 Laptop
1Gig of Memory
1.73 Ghz
Intel 915GM northbridge with Intel Graphics Media Accelerator 900

Now I have tried just about every single guide on the web that I can find, I've tried using the latest WineHQ which is 1.0.1, and PlayonLinux. Neither of them works.

With WineHQ I have tried the registry edits, didn't work
Couldn't even install Directx9 :confused:

Then I got an idea :idea:
Lets try PlayonLinux!
But when i searched for a guide on doing that I got bombarded with scripts that were to confusing for me!

The thing that really upsets me is that other people have reported and showed themselves play this game on Linux without any flaws or errors, and it runs smoothly, some haven't even needed to install DirectX9. :mad: :mad: :mad:

So should I just donate a small bit of my hard drive to Winxp again and just accept PWI isn't gonna play on Linux? Or is there some vital key to getting this to work that I'm missing?

Thanks for the help in advance!!!!

---

### Post by del_diablo on 2009-12-19
I would start by asking WHAT GUIDES?!
And why do you want to install DX9?
What is your computer(hardware)?
What version of Wine are you using? 1.0.1 is NOT the newest, it is the newest "stable" version. Download [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) 1.1.33 here.
What other mess have you done? Tell us?
What other games?
What does happen you attempt to run it outofthebox without any guides?

---

### Post by AllRadioisDead on 2009-12-19
You need to post what kind of errors you're getting.

---

### Post by beastrace91 on 2009-12-19
Upgrading your Wine version is the first step in the right direction.

That being said I would not expect great performance for this game under Linux/Wine with your Intel graphics card (they have poor 3D drivers on Linux) if you do get it running.

Regards,
~Jeff

---

### Post by googeek on 2010-01-19
Here's how I got mine working under Karmic

1.Download wine. Do this by going to winehq.com and clicking on download. This will take you to a screen with many options, click on Ubuntu. Follow the very simple instructions for adding a new repository to your list.
If you are running Karmic, you do not need to worry about adding authentication at all, simply add the line and click the close button and allow it to reload.

2. Now open your Synaptic Package Manager, and click on Origin at the bottom left hand side of the screen. If you can't easily tell which source to click on, click on them one at a time until you see the wine files.

3.Select the wine1.2 file version 1.1.36 and click Apply up at the top. This will remove any wine you have and install one we know works with Perfect World.

4. At this point, or whilst you do all of the above, download the Vista/Windows 7 client from pwi.perfectworld.com. I don't know for sure that any other ones work. Once you have it downloaded, simply extract the file and double click the setup exe.


The game should run flawlessly, including cursor without any changes to wine or other downloads.If the game doesn't display correctly, make sure you have the best drivers possible for your system. Ubuntu Recommends the 185 Nvidia driver to me, but it doesn't work for games, so I added the repositories just like wine and installed a newer, Beta copy, 190 which runs great!

Hope this helps :)

---

### Post by KiDroboto on 2010-02-15
> **googeek said:**
> Here's how I got mine working under Karmic

1.Download wine. Do this by going to winehq.com and clicking on download. This will take you to a screen with many options, click on Ubuntu. Follow the very simple instructions for adding a new repository to your list.
If you are running Karmic, you do not need to worry about adding authentication at all, simply add the line and click the close button and allow it to reload.

2. Now open your Synaptic Package Manager, and click on Origin at the bottom left hand side of the screen. If you can't easily tell which source to click on, click on them one at a time until you see the wine files.

3.Select the wine1.2 file version 1.1.36 and click Apply up at the top. This will remove any wine you have and install one we know works with Perfect World.

4. At this point, or whilst you do all of the above, download the Vista/Windows 7 client from pwi.perfectworld.com. I don't know for sure that any other ones work. Once you have it downloaded, simply extract the file and double click the setup exe.


The game should run flawlessly, including cursor without any changes to wine or other downloads.If the game doesn't display correctly, make sure you have the best drivers possible for your system. Ubuntu Recommends the 185 Nvidia driver to me, but it doesn't work for games, so I added the repositories just like wine and installed a newer, Beta copy, 190 which runs great!

Hope this helps :)

Here's a [tutorial]("http://pwi-forum.perfectworld.com/showthread.php?t=579982") that shows (with VERY little tweaking) how to get PWI to run on Ubuntu. I followed the directions and got it to work on Jaunty using the Win XP build/installation. I think the memory tweak in regedit does make a difference in the game running or not because I did attempt running it without tweaking the memory setting and the game would crash when entering PWI (after selecting your character).

---

### Post by AllRadioisDead on 2010-02-15
> **KiDroboto said:**
> Here's a [tutorial]("http://pwi-forum.perfectworld.com/showthread.php?t=579982") that shows (with VERY little tweaking) how to get PWI to run on Ubuntu. I followed the directions and got it to work on Jaunty using the Win XP build/installation. I think the memory tweak in regedit does make a difference in the game running or not because I did attempt running it without tweaking the memory setting and the game would crash when entering PWI (after selecting your character).
The OP hasn't posted in over 2 months, why are you bumping this thread?

---

### Post by KiDroboto on 2010-02-15
> **ihermit said:**
> The OP hasn't posted in over 2 months, why are you bumping this thread?

In what I thought to be the spirit of Linux, helping those with issues with out running them under the train for it. In short the tutorial given in the thread previous to mine left out the regedit instructions that I believe make the game actually run. That post was made 3 weeks ago, which in most cases I would not have posted on. 

However, I found this thread by running a google search on this exact issue, so I thought I would leave a link to a tutorial that DOES make the game run. This way if someone else searches for help on this issue they may run across this thread as I did and may run across the correct solution right away, along with a little additional information.

---

### Post by kaliuso on 2010-03-23
Hi there, I'm totally NEW at Ubuntu. Well, I've tried your guide, kidroboto, on the pwi forum but it's still not running on my 9.10 Ubuntu.:sad: All there is, is a "%mydocs%" folder on my desktop that when I click has "downloads", click has Perfect World International back round pictures, an icon picture, auto run and set up. I tried clicking the paper icon "auto run", the "set up" paper and everything else to see if I can get it started but then all I get is a blue "default - wine desktop" window pops up and that's it, nothing else happens... I'm currently starting over and am downloading pwi again to try your steps again. 

I had a dual install but my xp was annoying me with a security update that just wouldn't install.:mad: I then foolishly thought I can just play pwi on Ubuntu, formatted my hard drive and now it's Ubuntu or NOTHING now, lol. I tried reinstalling my windows but now my comp shuts off in the middle of installation, I'm SICK of windows!! Ubuntu is the only OS I can use now.:frown: Please advise, thanks in advance.

---

