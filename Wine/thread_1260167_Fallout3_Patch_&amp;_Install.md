---
title: "Fallout3 Patch &amp; Install"
date: 2009-09-07
forum: Wine
---

### Post by Bonzai11 on 2009-09-07
With fallout3 I have been having a ton of problems trying to get it to run, because the install runs flawless.
I was just wondering what method did anyone use to configure wine whether it be newest wine, custom compiled, or Playonlinux.
I've been using play on linux to just get a quick install because it works and it saves me having to setup wine again, but only version 1 ( the version on the release cd.) Seems to be the only thing working.
All other patch version 1.05, 1.06, 1.07 crash and the launcher, and only vanilla loads, but I will be unable to use the Dlc which requires patch > 1.05.

---

### Post by castlefox on 2009-09-07
What version of wine are you using?

What graphic hardware are you using?

---

### Post by Mr. Teal'c on 2009-11-08
[FONT=Verdana, sans-serif][SIZE=2]Hello, I have managed to "compile" wine, 1.1.32 on a fresh install of Ubuntu 9.10 the 32 bit version, because on my 9.04 64 bit version I was unable to compile wine correctly, due to certain build packages being only available in 32 bit form.
[http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)
Get and install a 32 bit OS, preferably Ubuntu, (most packages), unless you want to try it, then more power to you, but 32 bit build is easier.

Get the latest source code for your system "http://www.winehq.org/download/", get wine 1.1.32, save it to your desktop, extract by right clicking on the saved file, and choose "extract here"

Get the patch from "http://bugs.winehq.org/attachment.cgi?id=20312" right click and "Save Page As..." save it, then patch wine by copying and pasting the patch file into the now extracted wine sorce code folder. Now do "cd /home/{your name}/Desktop/{name of wine source code folder}/" then type "patch -p1 < patch-benv.diff" do not close the terminal yet.

Next in new terminal get all the packages needed to build and install wine (VERY IMPORTANT), sorry I forgot the command for this.

Now do "./compile" if there is an error message, install suggested packages, other wise do "[/SIZE][/FONT][SIZE=2][FONT=Verdana, sans-serif]make depend" and then "make" (these steps will take a Loooooong time, so do something like watch movies, because it took me like 2 hours for it to run through a everything, then once it is done, do "sudo make install[/FONT][/SIZE][FONT=Verdana, sans-serif][SIZE=2]" "{your password}" , and it should be installed, follor the steps for adding the string values to "regedit" on the how to part of "http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322" 

Next go to "http://wiki.winehq.org/winetricks" to learn how to install wine tricks, do
 "sh winetricks"  choose to install the package "d3dx9" it may take a while.

then install play on linux, and if you self compiled wine right you should be able to install or play fallout 3 on either play on Linux or plain wine.[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]If there is missing information or a part is unclear, ask me. Right now[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]I am trying to get my GOTY edition installed so I can access the DLC on [/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]the second disc, and patch fallout 3 correctly. but I have benable to [/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]start a new game, and get far without much trouble.[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]P.S. what type of computer are you running it on? mine is a athlon x2 64 [/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]with a NVIDIA 9800 GT.[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]Good Luck:grin:[/SIZE][/FONT]

---

