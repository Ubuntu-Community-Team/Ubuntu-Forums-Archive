---
title: "WoW Crashing Problems."
date: 2011-03-29
forum: Wine
---

### Post by Pat Dezmo on 2011-03-29
I went to the ubuntu howto page on how to install WoW. Followed it to the letter. Installed the game from the website (as I purchased the digital copy, not the CD's) It installed and when I double click the desktop icon, or go through the .wine file to it, this is what happens.

Firstly, when I click play from the launcher the first time, it changes the resolution, which stays

It opens up the launcher without any problem, I click play, and it either comes up with a completely white screen and than crashes a few minutes later, when it does this, the sound for the login screen is playing ( If I press any button it pops up with the crash immediately)

 Or it will "freeze" my screen, where the "World of warcraft" will come up at the bottom, but it stays showing whatever was showing before I opened up the program, and I get complete loss of mouse control until I ALT+tab, and will only close if I end process from system monitor. 

Can anyone think of a reason this might happen, and maybe try to help me?


EDIT:  When I opened the game through the terminal using 

wine "C:\Program Files\World of Warcraft\WoW.exe"

I kept getting this in the terminal window.

fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB

---

### Post by Tweak42 on 2011-03-31
> **Pat Dezmo said:**
> I went to the ubuntu howto page on how to install WoW. Followed it to the letter. Installed the game from the website (as I purchased the digital copy, not the CD's) It installed and when I double click the desktop icon, or go through the .wine file to it, this is what happens.

Firstly, when I click play from the launcher the first time, it changes the resolution, which stays

It opens up the launcher without any problem, I click play, and it either comes up with a completely white screen and than crashes a few minutes later, when it does this, the sound for the login screen is playing ( If I press any button it pops up with the crash immediately)

 Or it will "freeze" my screen, where the "World of warcraft" will come up at the bottom, but it stays showing whatever was showing before I opened up the program, and I get complete loss of mouse control until I ALT+tab, and will only close if I end process from system monitor. 

Can anyone think of a reason this might happen, and maybe try to help me?


EDIT:  When I opened the game through the terminal using 

wine "C:\Program Files\World of Warcraft\WoW.exe"

I kept getting this in the terminal window.

fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB

What wine version and video hardware are you using?

Have you tried running in opengl mode?
```
wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

---

### Post by IHeequ5i on 2011-04-01
I had a similar problem until I started using opengl.

There's a lot of good information at WineHQ on how to install and configure WoW on wine. 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

That's the guide I followed.

---

