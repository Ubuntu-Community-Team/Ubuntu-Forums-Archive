---
title: "Installing Counter Strike: Source or any other half-life Sever On Breezy."
date: 2005-10-15
forum: Tutorials
---

### Post by bjweeks on 2005-10-15
This how-to will help you install a Counter Strike: Source server.

The first step is to make a directory to put the server I will use /srcds (source dedicated server) because I find is the most convenient.

```
 sudo mkdir /srcds 
```

Move into the directory.

```
 cd /srcds 
```

Change the directory permissions.

```
 chmod 755 /srcds 
```

Download the Half-Life server update tool.

```
 sudo wget http://storefront.steampowered.com/download/hldsupdatetool.bin 
```

Make the file an executable.

```
 chmod +x hldsupdatetool.bin 
```

Run the update tool. Then except the EULA.

```
 ./hldsupdatetool.bin 
```

The bin extracted 'steam'. So you can remove it and the readme now.

```
 sudo rm hldsupdatetool.bin 
```

```
 sudo rm readme.txt 
```

Run the 'steam' file to update it.

```
 ./steam 
```

Install the server. This could take a few hours.

```
 ./steam -command update -game "Counter-Strike Source" -dir . 
```


Now go take a break it is installing all the files. It could take a over an hour.

Once that done you can start you server by.

```
 ./srcds_run -game cstrike -autoupdate +map de_dust 
```

I hope this how-to helped you post any errors, typos, suggestions or feedback.

I'm in the process of updateing the how-to, I have a few more bugs to comfirm.

---

### Post by ::DoGG:: on 2005-10-27
GREAAAATT howto
helped me a lot, ony one question - can i download with this steam server for CS 1.5 or only 1.6 is available ???

EDIT:
i would add "chmod 755 -R /srcds" , if you add just "chmod 755 /srcds" after install you wont be able to do anything without superuser privileges.

---

### Post by bjweeks on 2005-10-27
This only install the latest server so installing "cstrike" would install Counter Strike 1.6. Would you need to use -r because you set the chmod before you put  the files in the directory.

---

### Post by Plasma88 on 2005-12-23
everything went smoothly, until the second to last step....

plasma@ubuntu:/cs$ ./steam -command update -game cstrike -dir .
Checking bootstrapper version ...
Getting version 17 of Steam HLDS Update Tool
Downloading. . . . . . . . . . . .
**[COLOR="Red"]Cannot open output file 'LinuxHldsUpdateTool_17.pkg'[/COLOR]**

i get that cannot open 17 pkg....

any ideas?


p.s. im also a complete linux noob

---

### Post by bjweeks on 2005-12-26
It could be a issue with Valve's servers, try again and see if is works.

---

### Post by Brian.Hall on 2005-12-27
[QUOTE=Plasma88]everything went smoothly, until the second to last step....

plasma@ubuntu:/cs$ ./steam -command update -game cstrike -dir .
Checking bootstrapper version ...
Getting version 17 of Steam HLDS Update Tool
Downloading. . . . . . . . . . . .
**[COLOR="Red"]Cannot open output file 'LinuxHldsUpdateTool_17.pkg'[/COLOR]**

i get that cannot open 17 pkg....

any ideas?


p.s. im also a complete linux noob[/QUOTE]


Run ./steam as sudo.  That should fix it for you.

Ex: sudo ./steam -command update -game cstrike -dir .

---

### Post by jamaican on 2005-12-30
hello just wondering how do you make a directory or wer do you get one because im on windows xp and i dont no how thnx for you help 


jamaican:confused:

---

### Post by dynamicres on 2007-01-07
great howto!!

---

### Post by Dark Sarcasm on 2007-03-14
Hi, I am new to linux and I was wondering what port I should forward for this server, and also how to configure admins and such. I have another server that I am using as a web, ftp, and network server, so I don't want to put it in the DMZ and disrupt the other server.
  Thanks in advance!

-Tom

---

### Post by tehgooch on 2007-06-09
I keep getting this when trying to run hldsupdatetool.bin:

> tehgooch@gserver:/srcds# ./hldsupdatetool.bin 
bash: ./hldsupdatetool.bin: No such file or directory
tehgooch@gserver:/srcds# 

The file is there, and I followed all the directions exactly. I am running Ubuntu 7.04 Server AMD64 (Is it because I'm running AMD64?).

I'm doing this through SSH on my Windows XP Pro computer. Any help would be greatly appreciated. I tried to include any information that might be useful, but if you need more just ask :).

---

### Post by ginnsu on 2007-06-20
> **tehgooch said:**
> I keep getting this when trying to run hldsupdatetool.bin:



The file is there, and I followed all the directions exactly. I am running Ubuntu 7.04 Server AMD64 (Is it because I'm running AMD64?).

I'm doing this through SSH on my Windows XP Pro computer. Any help would be greatly appreciated. I tried to include any information that might be useful, but if you need more just ask :).

Sorry to drudge up a new thread but I found this thread looking for answers and this post gave me an idea that solved this problem for me. I'd just like it answered for the next person who's looking for answers (or more likely: me if I set up another server and forget my own solution.) From what I understand the Ubuntu Server & Desktop AMD64 do not come with the package lib32gcc1, which in most cases is not needed, but for installing the half life & source dedicated servers it is. So:
```
sudo apt-get install lib32gcc1
```
That nipped this one in the butt for myself. And I hope tehgooch had this solved a long time ago. Thank you.

---

### Post by ||Console|| on 2007-06-27
nice guid i hope it works for me that missing LIB was a pain

---

### Post by ||Console|| on 2007-06-28
I got it working . =) Vmware/ Bridged connection .

---

### Post by not_aWake on 2007-07-23
> **tehgooch said:**
> I keep getting this when trying to run hldsupdatetool.bin:



The file is there, and I followed all the directions exactly. I am running Ubuntu 7.04 Server AMD64 (Is it because I'm running AMD64?).

I'm doing this through SSH on my Windows XP Pro computer. Any help would be greatly appreciated. I tried to include any information that might be useful, but if you need more just ask :).

I think u forgot to sudo chmod +x hldsupdatetool.bin, hope this helps

---

### Post by tehgooch on 2007-09-08
Sorry to dredge an old thread as well, but I forgot to add the rest of my story. I had it set as executable, and it still wasn't working. I installed the 32-bit ubuntu server and it worked fine :mad:. Thanks for the tutorial :) .

---

### Post by firefall121 on 2007-09-16
how do i do it can u put it in a simpiler form?
like were do i even download the server?

---

### Post by golfing22 on 2007-11-24
Thanks a ton ginnsu, I thought I was crazy when bash said file not found!

---

### Post by chapman691 on 2008-08-15
ok well im not very happy.

everything went well until the last command.
i entered it and even sudo'd it this is what i got > [QUOTE]kris@kris-desktop:~$ cd /srcds
kris@kris-desktop:/srcds$ ./srcds_run -game cstrike -autoupdate +map de_dust
bash: ./srcds_run: Permission denied
kris@kris-desktop:/srcds$ sudo ./srcds_run -game cstrike -autoupdate +map de_dust
Auto detecting CPU
Using SSE2 Optimised binary.
Server will auto-restart if there is a crash.
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation

[/QUOTE] any suggestions.
im running ubuntu 7.4 and i think my graphics card is an ati.
thanks in advance

---

### Post by eenofonn on 2008-12-10
> **chapman691 said:**
> ok well im not very happy.

everything went well until the last command.
i entered it and even sudo'd it this is what i got  any suggestions.
im running ubuntu 7.4 and i think my graphics card is an ati.
thanks in advance

it seems as if you are trying to run the game... from what you posted it looks like the "server" is running fine.

---

### Post by tybasher on 2009-03-16
Newfag here at Ubuntu. I am running Ubuntu Server 8.10 on my Dell. This guide helped me loads. I thank you for your time you put into this.

---

### Post by Reyes1986 on 2009-05-06
Hey guys, I am proud to say that I've successfully installed Steam! CSS Is currently downloading :) ...For those who need help do what I do:


[SIZE=2][B][COLOR=Red][FONT=Arial Black]1. Make sure you have Wine. 
1a. Make sure you have Tahoma font.
1b. If you need it, download it [here]("http://www.dsource.org/projects/bindings/browser/trunk/freetype/examples/Tahoma.ttf?format=raw")
1c. extract font to [/FONT]cp Tahoma.ttf /home/USERNAME/.wine/drive_c/windows/fonts
1d. If you still cannot find it, search for .wine folder (make sure hidden files are not hidden.)[/COLOR]
[/B][/SIZE][COLOR=Red][FONT=Arial Black][SIZE=3][SIZE=2][B]
2. Once you have wine, type this in terminal wine --version

3. Make sure you have version 1.+ not 0.9

4. Go to [www.steamgames.com](www.steamgames.com) download file (it's .msi not exe.)

5. Open file, don't save to desktop.

6. Wine should automatically open up Steam and you should have a regular "Windows" program running (steam). 

7. Just follow the instructions and your good to go! :)

:guitar:[SIZE=1][COLOR=Black] [/COLOR][/SIZE][/B][SIZE=1][COLOR=Black]It feels good, considering the fact this is my second day with Linux, I still have a lot to learn, and need help with a few things myself, but this is for all those who were puzzled like me. I guess the other versions people were telling you to do were outdated?

PS - My O/S is Ubuntu 8.4[/COLOR][/SIZE][B][SIZE=1][COLOR=Black]
[/COLOR][/SIZE][/B][/SIZE][/SIZE][/FONT][/COLOR]

---

### Post by majormashup on 2010-04-03
@Reyes1986

running the windows version through wine may not be the most CPU efficient way of running a CS:S server, I'd recommend checking out 
[this guide:]("http://www.cstrike-planet.com/tutorial/1-Linux-Install-CS-Source/5") on installing it in linux without having to bother with those windows libraries.

---

### Post by bayou on 2010-04-20
when i use this command

./steam -command update -game "Counter-Strike Source"-dir


i have an result like this

Checking bootstrapper version ...
Updating Installation
No installation directory supplied or previously set



can anyone help me???

:) :) :)

---

### Post by Major Payne on 2010-06-07
when running ubuntu 10 desktop i attempt the ./steam command and it gives a illegal instruction

please help

---

### Post by morphication on 2010-06-08
> **Major Payne said:**
> when running ubuntu 10 desktop i attempt the ./steam command and it gives a illegal instruction

same here. after tow days of crazy search i found out that it has to do with the update from march 2010, in which the valve guys f***ed us all by making sse2 of the cpu mandatory. does anybody know a work around other then installing windows or wine?

major payne, can you confirm using an older cpu? i have a athlonxp 2400+, which supoorts sse, but not sse2. 

i am highly frustrated and feel left behind by the until now super cool valve guys :(

---

### Post by zmolix on 2011-08-17
> **bjweeks said:**
> This how-to will help you install a Counter Strike: Source server.

The first step is to make a directory to put the server I will use /srcds (source dedicated server) because I find is the most convenient.

I made all of them with some small problems but i retried and it worked. 
And after that when i run the " ```
./srcds_run -game cstrike -autoupdate +map de_dust
```i get ```
bash: ./srcds_run: No such file or directory
``` I tried with sudo and from the srcds folder and from root and all of them !!! 

[SIZE=2]WHAT IS HAPPENING ? [/SIZE]

P.S. I am kind of a noob, so if you explain what is happening please say it step-by-step. 

Thanks !!!


I resolved the problem.

Now the updater creates a folder "orangebox" and there are the server files.

If you want to config the server you may encounter a problem: the file /orangebox/cstike/cfg/server.cfg

you have to : 
```
cd orangebox/cstrike/cfg/
``````
sudo gedit server.cfg
```Reply if something goes wrong.

---

### Post by Flubbacrud on 2011-12-20
> **bayou said:**
> when i use this command

./steam -command update -game "Counter-Strike Source"-dir


i have an result like this

Checking bootstrapper version ...
Updating Installation
No installation directory supplied or previously set



can anyone help me???

:) :) :)

you are missing a space and a full stop after the -dir thats why it isnt working.

---

### Post by Flubbacrud on 2011-12-20
Also for any one running a 64 bit version before you start trying to run the hldsupdatetool.bin i suggest you run the following first otherwise nothing will happen as the 64 bit has some 32bit libraries missing. 

sudo apt-get install ia32-libs

---

### Post by dkaratsos on 2013-10-21
hi everybody. i m a total noob in linux but i usually find my way through googling things....so for the server i was trying over 3 hours typing and copy pasting the <<[COLOR=#000000][FONT=Ubuntu Mono] ./steam -command update -game "Counter-Strike Source" -dir .>>[/FONT][/COLOR] nothing happens. no files downloaded nothing....it just said that it was updated....so i checked the list of games using the ./steam -command list and there is not css in there.... now im trying the same but for game i put "orangebox" seems the most correct and yes its finally downloading game files...i hope its the correct one....if everything works fine....i ll feedback.

---

### Post by coffeecat on 2013-10-21
Oh, wow. An old Breezy thread still open?

If anyone needs help with installing Counter Strike on a current version of Ubuntu (Breezy went end-of-life in 2007) please start a new thread in a support section of the forum where you are more likely to get help. The OP has not logged in for several years.

Thread closed.

---

