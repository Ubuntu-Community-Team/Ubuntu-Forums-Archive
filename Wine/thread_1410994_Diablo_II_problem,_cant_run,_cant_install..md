---
title: "Diablo II problem, cant run, cant install."
date: 2010-02-19
forum: Wine
---

### Post by Locaj on 2010-02-19
Hi

I have Ubuntu 9.10, Radeon x800xl and using open drivers due to no support from ati drivers on 9.10. I cant install or run Diablo II.
I checked AppDB on WineHQ and found Diablo II but none of that worked! Still no success not even one step further.

I tried all variants.
I tried all next possibilities on both Wine and Wine Beta (both installed today so fresh). Both tried with graphics set to hardware and without. Results are bit different. All settings apart of graphics are default.

I tried to run game installed on windows copied to Ubuntu and run by both Wine (result:Wine normal asks for CD. Wine Beta does nothing).I was using burned cd that i made image before from my own original cd. The same burned cd works in windows.

I tried to install from blizzard page using installer and i got error message (include screen later). Tried to choose all different patches all were the same effect.

I tried to install form images (my cds are very old and dont work anymore, ISO images done by myself) When i mount Install disc and tun setup.exe i get error message "Please insert Install Disc".

All what i said was tried before and after i applied guides from AppDB WineHQ.

Im new to Ubuntu and Linux. Please help.

[IMG]http://img638.imageshack.us/img638/3541/screenshot2lg.png[/IMG]
```
locaj@locaj-desktop:~/Games/Diablo II1$ wine game.exe
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:advapi:SetSecurityInfo stub
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  26343
  Current serial number in output stream:  26343
locaj@locaj-desktop:~/Games/Diablo II1$ 

```

Next will be when i set graphics with no hardware support.```
locaj@locaj-desktop:~/Games/Diablo II1$ wine game.exe
fixme:advapi:SetSecurityInfo stub
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  26343
  Current serial number in output stream:  26343
locaj@locaj-desktop:~/Games/Diablo II1$ 

```

---

### Post by castlefox on 2010-02-20
Im gonna say your mounting the wrong disk.  OR some problem selecting what disk you need.

I have a crappy Intel in my machine and using 1.0.1 wine and I have no problems.

---

### Post by Locaj on 2010-02-20
I have the disk burned onto cd. It works fine in windows but not in Ubuntu. I tried with iso mount ... same problem.

In WineHQ AppDB they said that version 1.12 does NOT need cd to run (mine is 1.12). They said problem is probably somewhere else.

thanks

---

### Post by gromipakao on 2010-03-08
Same here, I was hoping this is possible but I just cannot go past the "Insert the correct disk" thing... I also have image files, I first thought it is because they were .cue files, but after conversion to .iso it is the same, the system does not recognize them as actual images.
Managed to start the installation over PlayOnLinux but as soon as it starts installing (after recognizing the virtual cd I created with Gmount) it says the same thing and cannot continue because the system does not see the mounted drive.
I think that it might be because all the virtual cd programs I tried do not import the actual cd label, they just name them 1,2,3 or something else...I really want to play Diablo on my ubuntu 9.10! hope it's possible...help! :)

---

### Post by beastrace91 on 2010-03-08
What Wine version are you all using? To use the download installer I believe you need newer than 1.0.1

~Jeff

---

### Post by Ferrat on 2010-03-08
Have you checked that your drive is listed in the drive list in winecfg?

---

### Post by AbstRakTFiloSofY on 2010-03-19
i recently downloaded a torrent for d2+lod+v1.12 and everything went smooth the download the mounting the installation the only problem i have is tht it says diablo 2 is not compatbile wit windows 7...there are a number of "solutions" out there but none of them seem to work....people keep telling me to change the compatability settings but it doesnt do ne good....when i change the compatability setting it wont let me save until i try it first but wen i try it says the game doesnt work cuz im using a virtual disk not an actual so the only way to open the game is to clik ope the program used to mount so wen i change it tries to open from the shortcut and doesnt work....NE SOLUTIONS WULD BE GREATLY APPRECIATED...here or yahoo works to The_tuna_man_182YAHOO.COM OR MSN AS WELL [EMAIL="aBSTrAKtfILOsOFy@HOTMAIL.COM"]aBSTrAKtfILOsOFy@HOTMAIL.COM[/EMAIL]

---

### Post by AbstRakTFiloSofY on 2010-03-19
NOT SURE IF ITS ANY HELP BUT I HEAR ALOT OF COMPLAINTS ABOUT NOT BEING ABLE TO RUN OR INSTALL....
 
I dwnlaoded the torrent... d2+lod+v1.12 from kickasstorrents.com and used utorrent to download it... 
 
once tht was finished go to downloads.com and search for magic disk virtual mounter....
 
its free easy to use and qucik...
simply right click the program and go to virtual cd/dvd rom and then slide the mouse over to e:/ and then click mount and find ur file whereever u have it then the game will pop open and the install will be finished in 5 to ten min on any decent connection seeing as how the files r already there...
 
the installation will ask u to switch disks simply mount whatever disk it ask you to and continue on but when the message window from ur pcpops up ignore and click ok in the d2 window...
 
when finished the torrent file contains patch 1.12 so go ahead and mount the lod disk and upgrade....once u finish tht u find ur self where i am right now if ur running windws 7 the compatibility isue 
 
hopefully ive helped and mayb u can find a solution and share with me thanks!

---

### Post by Toffeeapple on 2010-03-19
The solution to your problem is to purchase a legitimate copy of the game you would then be able to use the Blizards [Battle.net]("www.battle.net/"). Where in you would be able to register your legitimately purchased key for your game thus enabling you to download it to your PC via Blizzards handy little downloading application thing, install it and happily play it without the need for the CD's. Alternatively you could just use the CD's though you may need a nocd crack to do that but seeing as you already have that I'm sure, no problem there.

At least [that's what I did]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=315") after getting the game and it's expansion for not very much on ebay.

Speaking as a recovering software pirate some companies have just made it too easy and convenient to actually get their stuff legally.. the buggers. Mind you some of them haven't, I'm talking to you Ubisoft.

---

