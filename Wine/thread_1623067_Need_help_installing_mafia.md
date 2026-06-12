---
title: "Need help installing mafia"
date: 2010-11-16
forum: Wine
---

### Post by Abdullah Saleh on 2010-11-16
hello there everyone . 1st i would like to say thanks for taking some time to read this . 

i guess i don't have a big problem . but since am using ubuntu for the 1st time in my life . also using it since 2 weeks .. so yea i need some help 

am using ubuntu 10.4 and have good hardware to play mafia 

so anyway 

- i downloaded the game in ( .bin ) files which has ( .cue ) files with them 
- then installed some app called ( acetoneISO ) in order to mount the bin files . and mounted the 1st cd

then tried to run the exe installer file which is in the bin file using terminal with this command 
wine < file place > 

but it toke alot of time before it said .. ran out of time or something like that .

so basically i really need help to install the game 

thanks alot for cutting some of ur time to read this 


Abdullah Saleh

---

### Post by Abdullah Saleh on 2010-11-19
come on guys !

---

### Post by ronnielsen1 on 2010-11-19
Do you have a link to the game that you're trying to run? Googling comes up with a few different options.

---

### Post by ronnielsen1 on 2010-11-19
If this is a linux game then you should be able to open a terminal and do the following (substituting ./file.bin for the name of the file

chmod +x file.bin
./file.bin

---

### Post by ronnielsen1 on 2010-11-20
Any Luck?

---

### Post by Abdullah Saleh on 2010-11-21
thanks for the replay ronnielsen1 .. the game is called " mafia : the city of lost heaven  " . its a windows pc not linux .. i have been trying to install it using wine .. but no luck .. now when the installer opens .. it says please insert cd 1 .. and i already did mount the 1st cd ..

---

### Post by ronnielsen1 on 2010-11-22
That game should work from the reviews I've googled but you're not the first person to be plagued by the insert cd issue

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2291](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2291)

> [www.youtube.com/watch?v=0jyEHMXpdF4  ]("http://www.youtube.com/watch?v=0jyEHMXpdF4") 

Shows that the game runs great! /[QUOTE]

You could try the following
[QUOTE]The solution to the "Can not read MafiaGame/MafiaSetup from CD 1" error  is to use the MafiaSetup.exe in the cd's root folder instead of the one  at MafiaGame. 

Apparently it gets locked and the installer can't read it.or some of the other ones on the first link I provided. Good luck and post back here or on the winehq forums

---

### Post by saggz on 2011-02-01
Hello,

I had the exact same problem but all I did was install Mafia via a virtual machine (Oracle VM Virtualbox) then I installed daemon tools on windows xp, installed mafia, then copied the installed game folder over to linux and it worked.

---

