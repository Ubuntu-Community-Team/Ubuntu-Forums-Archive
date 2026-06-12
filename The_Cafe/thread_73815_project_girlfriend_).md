---
title: "project girlfriend :)"
date: 2005-10-10
forum: The Cafe
---

### Post by ubuntu_demon on 2005-10-10
Hi guys,

So I have a girlfriend for two months now. Now the time is right to try to convert her to Ubuntu :-D.

I'm gonna install breezy on the pc of my girlfriend.

The target pc is a compaq with 64 mb ram. It's a pentium 1 (or higher) with 3 gb harddisk. When the pc boots up I get a compaq screen instead of some specs. The pc runs windows 2000 but we don't know the admin password so it needs to be reinstalled. 

She needs to be able to run firefox,gaim and openoffice.

I'll first try the live cd to make sure the hardware is compatible with breezy and to try  to detect any possible problems.

So what environment do you recommend ? It has to be really easy (sometimes it's hard for a nerd like me to think like a green user)

Other suggestions for stuff girls like ? (I'll install some games)

I'm gonna try xfce4 (because I use it already and I like it very much) but it probably is too heavy (it's for the pc of my girlfriend)

---

### Post by 23meg on 2005-10-10
I'd recommend you try fluxbox right away, and XFCE as well. if they both work, see which one she's more comfortable with and stick with that. Do it the linux way; give her the choice ;)

I did a quick demo of XFCE to my mother and she found it incredibly more usable than windows. Next time I go to her place, I'll initiate Project XFCE-Mother. 

For stuff girls like, you may want to take a look at the Ubuntu women project subforum.

---

### Post by graabein on 2005-10-10
I think girls are generally into stuff like card games, sudoku, tetris, frozen bubble and maybe freeciv...

---

### Post by ubuntu_demon on 2005-10-10
[QUOTE=graabein]I think girls are generally into stuff like card games, sudoku, tetris, frozen bubble and maybe freeciv...[/QUOTE]
I know for sure she'll like frozen bubble,tuxracer (planet penguin racer). tuxracer isn't possible on her machine. frozen bubble might be possible.

I don't know whether she'll like card games. 

Do you know a nice tetris clone ?

---

### Post by 23meg on 2005-10-10
gnometris should do.

---

### Post by ubuntu_demon on 2005-10-10
xfce works nice with gnome applications (they look good)

It would be nice to have the following packages installed :
gnome-app-install
update-manager
upgrade-notifier

I really hope the pc is fast enough for xfce4

---

### Post by ubuntu_demon on 2005-10-10
[QUOTE=23meg]gnometris should do.[/QUOTE]
thnx!
hey that one is installed by default :)

---

### Post by jatos on 2005-10-10
I planning to try XCFE4 on a pc with the following

32mb ram
100mhz

Could you day how well XFCE runs so I can decide whether to try it on that.

---

### Post by daschl on 2005-10-10
you can also try to use

Openbox with Fbpanel as taskmanager

lightweight and userfriendly :)

---

### Post by ubuntu_demon on 2005-10-10
[QUOTE=jatos]I planning to try XCFE4 on a pc with the following

32mb ram
100mhz

Could you day how well XFCE runs so I can decide whether to try it on that.[/QUOTE]
yeah ofcourse I'll report my findings :)

---

### Post by ubuntu_demon on 2005-10-10
[QUOTE=daschl]you can also try to use

Openbox with Fbpanel as taskmanager

lightweight and userfriendly :)[/QUOTE]
never heard of openbox. Maybe I'll check it out. thnx!

---

### Post by Wolki on 2005-10-10
Consider IceWM. It's rather lightweight and has a very familiar interface for people used to older versions of windows.

---

### Post by KingBahamut on 2005-10-10
Whatever you do Demious, 

Dont install package othergirlfriend-2.5.deb , while also averting to install mistress-4.5-1.deb as well. Whatever you do DO NOT, I REPEAT DO NOT UPGRADE TO maritalpartner-2.1.deb or wife-4.1.0-5.deb. These packages are dummy packages and ulitmately do you no good whatsoever. 

=)

---

### Post by YourSurrogateGod on 2005-10-10
Gnome. Imo, it's very n00b friendly and has a soft feel to it.

---

### Post by nkhansen on 2005-10-10
[QUOTE=jatos]I planning to try XCFE4 on a pc with the following

32mb ram
100mhz

Could you day how well XFCE runs so I can decide whether to try it on that.[/QUOTE]

I am currently using XFCE4.2 on my laptop with the following specs:

48mb ram
Pentium MMX 150 MHz.

It is running reasonably, except for the filemanager, which is too slow - but I use Midnight Commander anyways, also on my 2500+ Desktop computer.

This is on Debian Etch, mind you - I couldn't install Ubuntu, because I can't boot from the CD drive.

It seems to me, that the 2.4 kernel gives better than 2.6 - I guess because of memory-usage (I know that a kernel recompile is the way to go - but it takes time, you know)

Other ways to save memory:

- Do not install GDM/XDM, use the text-login, and continue with startxfce4, or try to use a autologin guide (I have forgotten the link, I'll get back to you on that)

- Use few panel-plugins - they all drain memory.

- Multitasking is nice, but don't overdo it.

If this post is messy and confusing, please ask me to make it clearer. The clock is ticking on this public library computer :-)

---

### Post by heimo on 2005-10-10
[quote=KingBahamut]Whatever you do DO NOT, I REPEAT DO NOT UPGRADE TO maritalpartner-2.1.deb or wife-4.1.0-5.deb. [/quote] 
```
heimo@box1:~$ sudo apt-get install wife
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  friends booze lanparty playstation motorcycle
The following NEW packages will be installed:
  wife nagging2.0 decoration expenses++
0 upgraded, 4 newly installed, 5 to remove and 0 not upgraded.
Need to get 3795kB of archives.
After unpacking 4563kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by YourSurrogateGod on 2005-10-10
[QUOTE=heimo]```
heimo@box1:~$ sudo apt-get install wife
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  friends booze lanparty playstation motorcycle
The following NEW packages will be installed:
  wife nagging2.0 decoration expenses++
0 upgraded, 4 newly installed, 5 to remove and 0 not upgraded.
Need to get 3795kB of archives.
After unpacking 4563kB of additional disk space will be used.
Do you want to continue [Y/n]?
```[/QUOTE]
:lol: :lol: :lol: :lol:

---

### Post by KingBahamut on 2005-10-10
Your version must be different from mine. I got mine from an american respository.

bahamut@bahamut:~$ sudo apt-get install wife
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  friends booze lanparty girlie-bar curfew-after-12midnight remote-control-tv
The following NEW packages will be installed:
  wife PMS fryingpan pregnancy kids marital-bondage
0 upgraded, 6 newly installed, 6 to remove and 0 not upgraded.
Need to get 15687kB of archives.
After unpacking 35784kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by kassetra on 2005-10-10
```
kassetra@geisha:~$ sudo apt-get install husband
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  friends life freetime freedom eating_out parties bars dance_clubs
The following NEW packages will be installed:
husband duty bills chores laundry cooking cleaning wiping_ass babies second_job
0 upgraded, 10 newly installed, 8 to remove and 0 not upgraded.
Need to get 2215kB of archives.
After unpacking 654312kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

N!  No way!

---

### Post by ubuntu_demon on 2005-10-11
it was more like this :-P :
> 
ubuntu_demon@blabla:~$ sudo apt-get install girlfriend
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
 fun
The following packages will be REMOVED:
 freetime 
The following NEW packages will be installed:
 long-train-rides sex love
1 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 22515kB of archives.
After unpacking 654342kB of additional disk space will be used.
Do you want to continue [Y/n]?


---

### Post by nocturn on 2005-10-11
$ sudo apt-get install wife
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lonelyness 
The following NEW packages will be installed:
  wife kids hapiness 
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 3795kB of archives.
After unpacking 4563kB of additional disk space will be used.
Do you want to continue [Y/n]

I didn't have to think for long.

---

### Post by ubuntu_demon on 2005-10-11
currently logged in to her pc (still on w2k). The upload speed is very slow (no cd-burner or admin passwd) so backing stuff up takes a long time :(

it's a x86 family 6 model 3 stepping 4 .. using google I estimate it's speed between 200 mhz and 300 mhz.

I'll install xfce4. She isn't very interested in games although she was curious about the pinguin games. I won't install very much games on it.

The harddisk is a terribly slow 3 gb drive. I'll use this partitioning :
500 mb /home
128 mb swap
aprox 2 gb /

---

### Post by Sirin on 2005-10-11
[QUOTE=ubuntu_demon]with a 3 gb harddisk. [/QUOTE] Sorry dude, I don't think that's gonna happen. The drive's too small. Ubuntu won't fit on such a tiny thing like that, as it takes up more than 6GB of data. You COULD get a 10GB drive, but a 20GB or higher is recommended for long-term use. ;)

---

### Post by Brunellus on 2005-10-11
```
luigi@funes $> man girlfriend
no reference page found for girlfriend.
luigi@funes $>
```

Drat!

---

### Post by Wolki on 2005-10-11
[QUOTE=Sirin]Sorry dude, I don't think that's gonna happen. The drive's too small. Ubuntu won't fit on such a tiny thing like that, as it takes up more than 6GB of data. [/QUOTE]

? No it doesn't, according to my cd it takes 1,8 gb for a typical install; which fits my experience. If you install additional software, the gb count goes up of course :)

---

### Post by ubuntu_demon on 2005-10-11
[QUOTE=Sirin]Sorry dude, I don't think that's gonna happen. The drive's too small. Ubuntu won't fit on such a tiny thing like that, as it takes up more than 6GB of data. You COULD get a 10GB drive, but a 20GB or higher is recommended for long-term use. ;)[/QUOTE]
it was actually a 4.3 gb harddisk (windows showed c: as being 3 gb maybe there was some recovery partition or something)

df -h gives :
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             2.8G  927M  1.8G  35% /
tmpfs                  31M     0   31M   0% /dev/shm
tmpfs                  31M   13M   18M  41% /lib/modules/2.6.12-9-686/volatile
/dev/sda2             897M   19M  831M   3% /home

so there's still a lot of space left.

It's running xfce4 currently. I prefer this above win2k. It's also a bit faster. But I think I'm also gonna try icewm.

---

### Post by YourSurrogateGod on 2005-10-11
I'll probably get flamed for saying this, but why remove Win2K? After the crap that was Win 9x, Windows 2000 was a pretty darn good OS.

---

### Post by Stormy Eyes on 2005-10-11
[QUOTE=YourSurrogateGod]Gnome. Imo, it's very n00b friendly and has a soft feel to it.[/QUOTE]

It won't seem so friendly on a Pentium I with 64MB of RAM. Trust me; I made that mistake on an old Toshiba Tecra laptop: Pentium Pro 233MHz, with 64MB of RAM. My wife saw me installing Ubuntu on it and asked me if I had been smoking catnip again.

---

### Post by ubuntu_demon on 2005-10-11
switched to icewm -> finally some speed :)
(xfce4 was as slow as win2k especially when doing a couple of things together )

---

### Post by ubuntu_demon on 2005-10-12
I tested the harddrive :

Timing buffered disk reads  ==> between  3.16 MB/sec and 3.96 MB/sec

---

### Post by ubuntu_demon on 2005-10-14
I've discovered the IceQua theme on the icewm homepage. I really like this theme.

I like icewm a lot. It's clean,easy and fast. Would be nice if there was an Ubuntu Icewm selection or something :). Right now I have to select each application by hand instead of having a workable default selection like gnome has. I'm selecting nice applications that don't require too much memory by hand and creating a nice menu for icewm. This takes a lot of time. 

This pc is a compaq deskpro with an intel pentium II (mmx) processor.

I have a lot of small things I want to improve on this installation and some minor problems I have to look at.

some problems I didn't spend time on yet :
-see if I can get the pc to powerdown instead of having to press a button. modprobing apm  or acpi doesnt work, I even get some error (acpi cannot locate RSDP) when booting the kernel if I don't pass acpi=off. I think I have to get into the bios to make this possible. I don't know how to get into the bios ( I have to try pressing some keys because f1,f10 and del don't work)

-sound doesn't work yet in the games that I tested. I hear the "ubuntu sound" when gdm shows the login screen. I also hear gaim sounds. I just have to spend a little more time on the sound guides/links.
-barrage didn't work the last time I started it 
-gaim crashes sometimes
-no usplash yet for some reason

some tweaks :
-I want to optimize swapping performance by doing some tweaking (the memory of this pc is the bottleneck)
-I want to play with hdparm to optimize hd performance

some things I have to look up  / find out :
-how I can get a graphical login screen using xdm or wdm (if possible)
-what benefits gdm above xdm/wdm brings (if using icewm) except for nice login screen
-how to get a wastebasket/trashcan (rox-filler is the filebrowser of choice)
-how to get a new session running at the same time as the current session so I can switch using ctrl-alt-f7 / ctrl-alt-f8 (just curious probably has no use on this slow machine)
-how to repair rar files (I did a backup of pictures using 17 small rar files of 3mb each but the 13th rar file is bad)
-how to start up dfm and xscreensaver automatically in a nice way
-if rox-filler can show previews of pics
-if dfm can automatically put the links of mounted floppy/cd-rom on the desktop after manually mounting
-what exactly the difference is between icewm and icewm-experimental in practice
-more info on monitor so that I might increase the resolution to at least 800x600 (currently using 640x480)

some minor things I have to do :
-make the icewm menu nice&easy for my gf
-create rox bindings for files so the open with the right application
-create a sheet of paper so my girlfriend remembers all the stuff she needs to know (for example running the update manager at least once each week)

---

### Post by Wolki on 2005-10-14
[QUOTE=ubuntu_demon]-how to get a wastebasket/trashcan (rox-filler is the filebrowser of choice)[/quote]

Try this: [http://www.skepticats.com/rox/trash.html](http://www.skepticats.com/rox/trash.html)

I tried it when i was using the complete rox DE, but I can't remember how well it worked. Not sure if it's still under active development.

> -if rox-filler can show previews of pics

Options -> Filer window -> Thumbnails

> -if dfm can automatically put the links of mounted floppy/cd-rom on the desktop after manually mounting

Not sure. Are you using rox for desktop, too? It can take care of mounting on its own, I found this quite easy to use for cds back then. The icon has a little light when it's mounted, and a dim circle if it's not. click on it, and it will open the medium, mounting if necassary. Leave the folder again (or close the window) and it will offer you to unmount it. Of course, right-click menu will work too.

> -create rox bindings for files so the open with the right application

Grab yourself a set of rox wrappers (they are on the rox homepage), they are rox program starters. With them you don't need to create bindings manually, just drop the relevant icon into a folder that comes up from the right-click menu (maybe rox will even understand .desktop files, not sure, the rox developrs are quite active with fdo).

---

### Post by ygarl on 2005-10-14
Have a look for the Xubuntu thread on here (search at the top) to install XFCE instead of Gnome. Should work on that small PC...

---

### Post by ubuntu_demon on 2005-10-14
[QUOTE=Wolki]Try this: [http://www.skepticats.com/rox/trash.html](http://www.skepticats.com/rox/trash.html)

I tried it when i was using the complete rox DE, but I can't remember how well it worked. Not sure if it's still under active development.

[/QUOTE]

thnx I'll take a look

[QUOTE=Wolki]
Options -> Filer window -> Thumbnails
[/quote]

thnx!

[QUOTE=Wolki]
Not sure. Are you using rox for desktop, too? It can take care of mounting on its own, I found this quite easy to use for cds back then. The icon has a little light when it's mounted, and a dim circle if it's not. click on it, and it will open the medium, mounting if necassary. Leave the folder again (or close the window) and it will offer you to unmount it. Of course, right-click menu will work too.
[/QUOTE]

thnx 

I don't use rox for desktop. But I'll try whether I can make this work with rox :)

[QUOTE=Wolki]
Grab yourself a set of rox wrappers (they are on the rox homepage), they are rox program starters. With them you don't need to create bindings manually, just drop the relevant icon into a folder that comes up from the right-click menu (maybe rox will even understand .desktop files, not sure, the rox developrs are quite active with fdo).[/QUOTE]

thnx!

---

### Post by ubuntu_demon on 2005-10-14
[QUOTE=ygarl]Have a look for the Xubuntu thread on here (search at the top) to install XFCE instead of Gnome. Should work on that small PC...[/QUOTE]
I tried xfce4 first. icewm is lighter.

---

### Post by Wolki on 2005-10-14
What I nearly forgot, ther is also a nice graphical application that can creat rox starters (so-called wrappers). You can find it here: [http://www.kerofin.demon.co.uk/rox/utils.html](http://www.kerofin.demon.co.uk/rox/utils.html) and the big set of premade wrappers on the rox page's ([http://rox.sf.net](http://rox.sf.net)) software list.

---

### Post by tseliot on 2005-10-14
You could try Damn Small Linux (DSL) which uses Fluxbox. I use it on my Xbox (64mb RAM) and it is fast.

---

### Post by ubuntu_demon on 2005-10-14
[QUOTE=Wolki]What I nearly forgot, ther is also a nice graphical application that can creat rox starters (so-called wrappers). You can find it here: [http://www.kerofin.demon.co.uk/rox/utils.html](http://www.kerofin.demon.co.uk/rox/utils.html) and the big set of premade wrappers on the rox page's ([http://rox.sf.net](http://rox.sf.net)) software list.[/QUOTE]
thnx!

---

### Post by ubuntu_demon on 2005-10-14
[QUOTE=tseliot]You could try Damn Small Linux (DSL) which uses Fluxbox. I use it on my Xbox (64mb RAM) and it is fast.[/QUOTE]
no I like Ubuntu with icewm very much :)
it just takes a bit of time to make everything exactly like I want (I haven't worked with icewm before and this pc is really slow compared to my P4 2.8 ghz with 1 gb ram)

---

### Post by tseliot on 2005-10-14
[QUOTE=ubuntu_demon]no I like Ubuntu with icewm very much :)[/QUOTE]
I completely understand you :) . For example I've tried SUSE recently and although I find it a good distro I can't get Ubuntu (Breezy now) out of my head. Perhaps it's magic :p

---

### Post by Sirin on 2005-10-14
[QUOTE=tseliot]You could try Damn Small Linux (DSL) which uses Fluxbox. I use it on my Xbox (64mb RAM) and it is fast.[/QUOTE]

Never knew you could do that on Microsoft's proprietary hardware... 

Make sure [IMG]http://www.longwood.edu/english/esl/GALGATES.JPG[/IMG] doesn't know that you've done this, or he will boot you from Windows and Xbox 360, and cream your face whenever you go to Brussels. :razz:

---

### Post by tseliot on 2005-10-14
[QUOTE=Sirin]Never knew you could do that on Microsoft's proprietary hardware... 

Make sure [IMG]http://www.longwood.edu/english/esl/GALGATES.JPG[/IMG] doesn't know that you've done this, or he will boot you from Windows and Xbox 360, and cream your face whenever you go to Brussels. :razz:[/QUOTE]
:p There is no fun if you don't tweak your xbox (bios, dashboard, mediaplayer, harddisk, etc.).

---

### Post by swerner on 2005-10-14
[QUOTE=ubuntu_demon]Hi guys,

So I have a girlfriend for two months now. Now the time is right to try to convert her to Ubuntu :-D.

I'm gonna install breezy on the pc of my girlfriend.

[/QUOTE]

Good luck on getting your girlfriend to use Linux.  All I can say is that unless your girlfriend is a nerd like you and I, she is only going to want to use it if it works all the time.  Small things should just work, like plugging in a USB stick, viewing a video online (ok with 64MB that may not be possible even with window), playing MP3's she shares with friends, etc.

---

### Post by ubuntu_demon on 2005-10-16
[QUOTE=swerner]Good luck on getting your girlfriend to use Linux.  All I can say is that unless your girlfriend is a nerd like you and I, she is only going to want to use it if it works all the time.  Small things should just work, like plugging in a USB stick, viewing a video online (ok with 64MB that may not be possible even with window), playing MP3's she shares with friends, etc.[/QUOTE]
she's no nerd so luckily I'm her supporting nerd :)

also on windows 2000 she was only able to : browse,view pics and use webbased manager (which crashed if she browsed at the same time). So icewm is already an improvement for her :)

---

### Post by swerner on 2005-10-16
With my Project G/F I made her desktop as Windows-like as possible.  Somethings still frustrate her, like "Why can't I install that cool screensaver?"  It's hard to explain that somethings just won't work (I try and avoid Wine, 90% of the time it's more trouble than it's worth).

---

### Post by m0biu5 on 2005-10-16
[QUOTE=swerner]With my Project G/F I made her desktop as Windows-like as possible.  Somethings still frustrate her, like "Why can't I install that cool screensaver?"  It's hard to explain that somethings just won't work (I try and avoid Wine, 90% of the time it's more trouble than it's worth).[/QUOTE]

I think we have our fair share of "cool screensavers":cool:

---

