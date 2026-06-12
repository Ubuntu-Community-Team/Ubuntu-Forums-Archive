---
title: "Installing Popcap Games on Ubuntu 10.10 - Almost Perfect"
date: 2010-10-27
forum: Wine
---

### Post by shinkaide on 2010-10-27
*Note: not really asking for help or anything, just feeling a bit giddy about the state of gaming on Ubuntu and how it's gradually catching up.*

I've been an avid Linux enthusiast since before I ever hit high school a over a decade ago, and the way things have been going on the gaming side for Linux, I'm starting to feel pretty good about it. There are already a lot of good native tux games out there, but as time goes by we're able to get access to Windows games via Wine (and some other means as well). 

One of the things I miss most when using Linux is that quick hit of casual gaming that I get from Popcap. I've usually had to resort to borrowing a family member's Windows lappy or downloading a cracked version of a Popcap game I already own just so I could run it, since if you could ever get to install any of their games on wine (by some miracle), you couldn't get past the registration dialog.

Well, today I just installed Both Bejeweled 2 and Plants Vs Zombies on 10.10 via Wine from the Ubuntu software center, and everything went well, from installation, to registration, and to finally running the games! Almost.

**Bejeweled 2** would load and run up to the menu screen after "click to play". Then the visuals would hang. The music would still be running and you could click around and load the various game modes, but you wouldn't be able to see anything. I could refresh (so to speak) the screen by doing ctrl + alt + left/right to move virtual desktops back and forth, and I'd get another screen update on bejeweled, but it would immediately hang on refocusing. TLDR, it'd run, but it's unplayable cos' you can't see anything.

**Plants vs. Zombies** was almost perfect. Installed, registered, launched, and ran the game completely. Just couldn't get 3D acceleration to run. Whenever I tried, the aspect ratio would get screwed up, and the buttons weren't exactly clickable in the places that you'd see on screen. Lack of 3D acceleration isn't really a problem, at least not until you unlock the "Survival: Endless" mode where there are a ton of things going onscreen at any given second.

Been a long time coming, but I think it won't be as long as most people would think now that we can get games from one more quality company to run smoothly and without issue on Ubuntu. We're not there yet, but I'm feeling good about it!

/rant :P

---

### Post by agemini68 on 2010-12-03
How did you do it? When I tried to install it using wine, I got the message inexecuteable file or something like that.

---

### Post by mortis1369 on 2010-12-09
the reason you got that message is because you dont have the .exe set to executable. right click>properties>permissions>allow executing file as program

---

### Post by shinkaide on 2010-12-17
> **agemini68 said:**
> How did you do it? When I tried to install it using wine, I got the message inexecuteable file or something like that.

I didn't do anything fancy: I just opened a terminal, CD'd to the download directory with the .exe file, and typed:

```
wine setup_file.exe
```

That was it. All I have is the standard wine installation from the Ubuntu Software Center.

---

