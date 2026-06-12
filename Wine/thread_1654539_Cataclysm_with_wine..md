---
title: "Cataclysm with wine."
date: 2010-12-28
forum: Wine
---

### Post by Suroh66 on 2010-12-28
I've been trying for about five-six days now to get my world of warcraft running my system is fine my graphics card is fine I have the ability to play it on my computer how ever I'm fairly new to linux and wine. When I start up wow I go through the movie and get to the login screen it's solid black and it crashes almost right away and spits out this error code 

This application has encountered a critical error 
Error #132 (0x85100084) Fatal exception program 
C:/program files/world of warcraft/Wow.exe exception 
0xC0000005 (Access_Violation at 0023:F75F2D6A 
The instruction at "0xF75F2D6A" refferenced memory at 
"0x0000000C" This memory could not be read 

About a month ago I had world of warcraft running on my computer with out any problems other then bad lag which I fixed. The game was uninstalled and I just put it back on after the new expansion came out. This is a 64 bit btw and it's wine 1.2 I've tried multiple things and gotten no where. I even upgraded to  the wine beta 1.3.10. Can any one help me or give any sugestions? Again I'm fairly new to linux please keep that in mind!

---

### Post by cwwilson721 on 2010-12-28
You have to run WoW in opengl, either thru the command switch "-opengl" or adding the line in config.wtf (Search the forum. The HOW-TO covers this point.

WOW HAS TO BE RUN IN OPENGL

---

### Post by Suroh66 on 2010-12-28
Ah yes see that's what I thought how ever I run it in -opengl every time both ways you stated :) And also ftw be it true or not on the wine forums they stated that the -opengl does nothing any more. But regardless either way i run the game with it or with out I get the same error message :) So that's not my problem some thing else is.

---

### Post by cwwilson721 on 2010-12-28
The 'opengl' switch DOES work. Prrof is my dual-boot setup. I have the same config.wtf file in both, only difference is the '-opengl' switch I use under wine, and it runs in opengl fine.

I'm assuming you DO have the proprietary drivers for your videocard/chip installed? Use the ones from Ubuntu. They have the correct setup for opengl, in both 32 and 64bit setups.

---

### Post by Suroh66 on 2010-12-28
As I said before "be it true or not" but I want to thank you I went over some things again looking at the how to post and i notice that messed up one of the words that went into the wine equivelant of the registry editor :) My frustration was getting to me though lol. Thank you :)

---

