---
title: "trying to install WotLK with wine, linux noobie needs help!"
date: 2010-05-03
forum: Wine
---

### Post by iamtheculprit on 2010-05-03
Hello all, this is my first time using any distro of linux for anything other than recovering files from windows. I am trying to get Wrath of the Lich King installed via wine, and i've gotten all the files copied successfully (or so it appears) to a folder on my desktop, but when i try to start the install through terminal with the command "wine Installer.exe" it says "wine: cannot find L"H:\\Desktop\\wotlk\\installer.exe"". Am I doing something wrong? please help! thanks

---

### Post by 5dolla on 2010-05-03
use playonlinux make your life  whole lot easier

---

### Post by elsanto80 on 2010-07-14
This thing was done on **Ubuntu 10.04 **with ALL the updates/upgrades  sorted, on a **HP Pavilion DV6000**. Also this text is more a story steep by steep.

_**Intro**_
I got hacked..Playing on windows. I got some sort of troyan, keylogger, virus... Prolly from my work, i used the usb device there on those infested computers, then bak at home. First i got banned because my comp had something wrong. Yep, hapens. **Blizz will bann you for a day telling your that something is wrong with your computer, but they wont tell you what is wrong**... Ok, i got instaled a good antivirus. After al got working, 3 days... i was grabing the flames and i got loged out, try to log again, and it did asked me for a keylogger...ouch...bump, mega hack!
that is how my search for a safe OS started. 
Before I wipe that windows vista, i did a proper research that was able to play wow on linux. And it is. this is how I got wow working on my laptop.

OK, I am not a Guru in Linux like the fellas ova here, but i think I got it sorted. There are a few ways u will manage to do this, I am gona explain 3 ways. This ways are mainly focus to run with the cd and ussing files.

 Particularly the video card. this was done easy, is was just having a look on the video preferences, and then click on an icon that said something about activated (what i belived) some "cool" stuff. ok, gave me a message saying that I need to update the NVIDIA graphic card. I did it, not when i move my windows arround the have some funny "wably" moves.

_**Wine**_
I have inserted the cd from  the original game. To start i find the wow file but it wont run, right clik and them to run it with wine, but nothing. Ok, back to the net to read about. I found a post (that i belived it was clear) at wowwikki.
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)
ok, so since the normal instalation was not gona work i opened a terminal, and copy paste:
wine /media/WoWDisc1/Installer.exe
Enter...aha It did worked, something hapened (i allready had the cd1 in the computer) and the instalation did runned smooth... Once the original game was intaled, I did runed it. It did open the launcher, and the update stedted running, after 3 mins, it came up a fancy wondows saying that i needed to download 3.7 gigs... ok... I live in south america, there is nothing like internet cap,  so i went for it!
The next morning it was there... Fully installed, i did runned, but... wasnt able to login since my my account got frozen when I got hacked (F$%^ windows virus). anyway, It was the windows of the WoLK, it said "version 3.3.5 (12340)" yerr!! One of my mates (fagget windows lover) got home and I asked him to log on his account to tray out... ok... it started. Wont work. Basic message: "you dont have installed WoLK"... mhm... I try to have a look in the cinematics..OMG, indeed, no cinematic for WoLK!! But the bloody frozing drake is flying on my desk!!! AAHHHH!!!
Looking for answers I found this post, and comments like the one of the fella above:
 "noob, you should try with PlayOnLinux" ...mhm... ok...
started having a look around, and i found the root where those files are saved. Just click on your Home folder, then again in places and click to show u hidden files. there you will find .wine , go there, and look into the folders, and aha, there is wow folder, and having look around where missing some things...or at least on in the right place..(i will be back into that).

**_PlayOnLinux_**
It was already installed 2 days ago when i started to use Ubuntu for first time. I did run it. I have to get the upgrade running, once that was done, got the program running. Click where it say "install", then i went to games (fellas, plz understand that all this stuff toked me over 1 hr to figure out), found WoW and TBC... Ok, lets run WoW.
First thing it did asked was: "4 or 5 Cd, or a DVD?" ok, since I got it downloaded yesterday, i was hoping to find a way to make it run from that source that i have downloades and that it was hidden some where in my home folder!! ...but after extensive reading (like 1 hr) I got done, so, I decided to run it from the 5 CD. Ok, insert disk 1...5, done! :p ...was hoping. Then pops up a very confusing message (awfull english!! worse the mine!), called my wife (english teacher) and she confirmed that. Ok, i just clicked "forward", and the installation windows from the wow comes up... UH? ](*,)
With a bit of rage, i decided to uninstall the wow on wine, F..k the WoW!
Time for a cigarette... 
Outside is snowing, our baby was sleeping, the house was calm.
And it comes to my mind that when Blizz launched WoLK, the did reform the folder structure!! The users had to move things around when we did installed a few years ago... So there was the problem!! That is way there are so many problems with wolk!
Ok, I have allready move things to the trash and clean the trash.. :D

_**Alternative**_
Lucky me, my wonderful and beautiful wife also plays WoW (a :-# class: Night elf, and druid...)!! she got the same computer as i do, i fed up of the instalation, and plugued the external hard drive, and compy paste her WoW folder... 20 gigs... :D
Since I have also found the wow folder in .PlayOnLinux , that folder was nearly empy, had some files that wont make over 1 meg, so, i did erraise and paste the 20gig folder that my lovely wife lended me \\:D/ !!
ok, i still havent activated my acount...but this time there is there the cinematics of WoLK!! wich hopefully mean that it should work. Since it is kinda late i am gona get a game card tomorrow and run it. Hopefully gona work.

_**Reflexion**_
I know this is more of a story  then a real instruction. We can take 2 things from all this stuff I wrote. 
1. If you don't have a lovely wife that also plays wow on her computer, DON'T FREAK OUT!! we all have some geek friend (he/she not necessarily lovely, but a good friend will do it) that can help. Bump will be if your friend is playing wow in spanish or german, but sure u gona get it working :D .  Seriously, this seems to work.

2. I like to think the world is full of good pacient ppl. Look around your wow folder in wine/playonlinux and star moving folders.. it is riski, and do that only if you have played wow long enough (my case ova 5 years) and you know how things should look... Not certain, but should work too.

I will be back with the final results. One thing is an issue already. I have noticed a slight frame drop on the cinematic. But they all look Good.

PS: I am a noob on Linux. But i know it works, so i wont give up.
PS 2: sos for the rubbish english. My spoken language is spanish.

---

### Post by hikaricore on 2010-07-14
The only think that really stuck out to be is that you spelled **Reflection** as **Reflexion**.
Otherwise I barely noticed.

---

### Post by elsanto80 on 2010-07-16
Man, why u do this, help out comment is good. we are noobs, the guru fellas could help out a bit more :S

---

### Post by apostra on 2010-07-16
Hey there,

So far i make it run in 3 ways, all worked fine for me

1)Copy from windows partition or pc the folders to .wine/drive_c/ProgramsFiles/here, left click on Launcher.exe, or wow.exe, give permission to execute and at open with tab choose wine. If the computer have dif hardware from yours delete the config.wtf file at your WTF directory

2)Install them from cds, just run them on wine.

3)Use the download installer ( wow client ) from site. Use the europe installer if you are in europe ofc. That way you will get an error at begin. Have no idea what was it, but its cool, click it and keep going. Then you may have an issue on patching, you may have an error or even crash at third patch, the last one, just restart it and after 1 or 2 attempts its fetching it. I took 2 attempts, my friends pc took 3. All fine tho. Have in mind this way you download and install the game straight away. Also blizz does some work for upcoming expa. Dont choose this option on Tuesday night as servers and site is down.


As you understand, wine installed and fully updated. Havent try it with Playonlinux and dunno if its easier or not. Just mentioned what i did. 

**Before you run anything on wine, open the wineconfig first, to creat the folders and all wine directories.

Have fun and good luck mate

---

