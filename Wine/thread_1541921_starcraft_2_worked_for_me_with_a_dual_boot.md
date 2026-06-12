---
title: "starcraft 2 worked for me with a dual boot"
date: 2010-07-29
forum: Wine
---

### Post by ChrisEiffel on 2010-07-29
Hi

Unfortunately I couldn't install SC2 using linux. However I was able to install Starcraft 2 on windows and then run the executable in linux with wine.

for me it was 

wine /media/16C8CFA5C8CF820B/Program Files (x86)/StarCraft II/Starcraft II.exe

It took a while to load but it worked.

Make sure you have wine version 1.2 
wine --version 
should tell you

The game did run slower using linux rather than windows (duh), but that's why I have an i7.

---

### Post by tylersontag on 2010-07-30
Interesting idea, after failing at getting SC2 to run on my XP VM or through wine, partitioning was going to be my next option.   I havent had a dual partition box since my old college laptop, as i recall i couldn't get write access to my XP box from within ubuntu.  Do you have any information on how you're mounting your windows partition?

---

### Post by Mas0ne on 2010-08-01
> **ChrisEiffel said:**
> Hi

Unfortunately I couldn't install SC2 using linux. However I was able to install Starcraft 2 on windows and then run the executable in linux with wine.

for me it was 

wine /media/16C8CFA5C8CF820B/Program Files (x86)/StarCraft II/Starcraft II.exe

It took a while to load but it worked.

Make sure you have wine version 1.2 
wine --version 
should tell you

The game did run slower using linux rather than windows (duh), but that's why I have an i7.

See this howto on how to update your video drivers if you are on a nvidia chip:
[http://www.zealouscraft.com/index.php/linux/35-gaming/48-starcraft-2-on-linux](http://www.zealouscraft.com/index.php/linux/35-gaming/48-starcraft-2-on-linux)

---

### Post by tylersontag on 2010-08-03
i will note, i tried this method to run SC2 and it work for me.  I too had previously not been able to install SC2 (or play it on a VM, but i digress)

---

### Post by Mas0ne on 2010-08-06
> **tylersontag said:**
> i will note, i tried this method to run SC2 and it work for me.  I too had previously not been able to install SC2 (or play it on a VM, but i digress)

So you are saying the guide helped you? =) If so please leave a comment at the bottom of the article and tell us that it worked =)

---

### Post by anaconda on 2010-08-06
hmm..
If I understand corretly you are running the game from your windows partition.

Have you tried copying the came to your linux partition (from windows partition), and running it from there? 

That is how I used to run games that didn't want to install with wine. And I also made a (linux installer) DVDs with the installed version of the game and registry settings. So that I could get rid of the temporary windows installation..

---

### Post by tylersontag on 2010-08-12
while some of the winetricks stuff im sure improved my game performance, and just tweeking the audio settings solved a bug i had with the game (i kept getting artifacts while playing with the sound configured on 'hardware', changing it to 'emulate')  but at the end of the guide i still had the installer crash at 52% when trying a WINE install.

However, as i was saying, mounting my windows partition was still allowing me to play the game with wine.  Good write-up though!

---

### Post by killabee44 on 2011-06-30
> **ChrisEiffel said:**
> Hi

Unfortunately I couldn't install SC2 using linux. However I was able to install Starcraft 2 on windows and then run the executable in linux with wine.

for me it was 

wine /media/16C8CFA5C8CF820B/Program Files (x86)/StarCraft II/Starcraft II.exe

It took a while to load but it worked.

Make sure you have wine version 1.2 
wine --version 
should tell you

The game did run slower using linux rather than windows (duh), but that's why I have an i7.

Guys, can someone give me a hand in getting this working? 

I already installed the game from windows. Then went to wine configuration and under "application settings" selected "add application", then browsed to the exe in the widows partition (not sure if that's how this is done). 

After this I selected ok but don't see the shortcut from any Wine menus. What am I missing? Am I going about this all wrong? Thanks.


Edit: Solved. Just had to browse to the .exe on the windows partition and right click it, then select open with wine.

---

