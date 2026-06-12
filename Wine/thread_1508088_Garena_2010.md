---
title: "Garena 2010"
date: 2010-06-12
forum: Wine
---

### Post by H0lyGanGs7eR on 2010-06-12
Hello friends! Left only one Windows' program to run under Linux - Garena. In the beggining i had problems installing, but I read some threats and I got it correctly installed, I installed Warcraft 3 TFT too, so now it lasted to combine them. I enter in rooms, when I click on the start button, Garena minimizes, but Warcraft doesn't start. I think the problem is in the internet - Wine can't change the the server in "Local game" into the server of Garena. Please guys help, there are many people who really want to play in Garena!!!

---

### Post by asdfoo on 2010-06-13
you didn't tell us which version of Wine you are using.

wine-1.2-rc3 is the most recent.

---

### Post by H0lyGanGs7eR on 2010-06-13
I run Garena in Playonlinux with Wine 1.11, i saw this in some forum. Is there any better version of Wine for Garena2010?

---

### Post by asdfoo on 2010-06-14
There is no Wine 1.11.

---

### Post by H0lyGanGs7eR on 2010-06-15
Wine 1.1.11

---

### Post by asdfoo on 2010-06-16
ok, wine-1.2-rc3 is the most recent, there has been probably over 1000 bugs fixed since the version you are using, it could be worth testing

---

### Post by H0lyGanGs7eR on 2010-06-16
No it's not working...

---

### Post by asdfoo on 2010-06-17
> **H0lyGanGs7eR said:**
> No it's not working...


"not working" very descriptive.

what happens? the same as 1.1.11 or something different?

---

### Post by H0lyGanGs7eR on 2010-06-26
Help guys please! I really want to run Garena. asdfoo, I see you want to help, but it DOESN'T MATTERS which version of Wine I use it just doesn't work!

---

### Post by borogoves on 2010-06-30
garena wont work in wine 1.2-rc5. you can install garena but after running the program the pointer turns into the circle thing(loads) and does nothing.

---

### Post by H0lyGanGs7eR on 2010-07-18
Well, I started garena, but I when I enter in room and click "Start game" nothing happens... May be there is some problem in the networking part - to replace the local server with the garena's one.

---

### Post by asdfoo on 2010-07-18
> **H0lyGanGs7eR said:**
> Well, I started garena, but I when I enter in room and click "Start game" nothing happens... May be there is some problem in the networking part - to replace the local server with the garena's one.

There are some people working on this problem, hopefully it will be fixed in next version of Wine.  Stay tuned.

---

### Post by H0lyGanGs7eR on 2010-07-20
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19336]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19336")

See in the comment, there is a way to run it. I tryed, but I still can't patch wine with AcceptEx

---

### Post by ronnielsen1 on 2010-07-20
> [http://appdb.winehq.org/objectManage...sion&iId=19336]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19336")

See in the comment, there is a way to run it.

Look closer, it installs but is rated garbage because it won't run

> *I believe Garena's engine is the reason it doesn't work. Wine can handle
 the GUI no problem because when opening it through the terminal and
 pressing Ctrl+C, the engine stops working but an error message 
comes out from Garena in its on GUI (with proper text and fonts
 and clickable buttons). Possible related to the networking part 
of the engine, since Garena is stuck at trying to send and receive 
something over the network at the beginning.


According to this guy, he got it to work but you have to jump through hoops

> HOWTO: Run GG-Client on Linux

Hi people, finally I have been  able to get GG-Client to run on _**[COLOR=#ff0000]Linux[/COLOR]**_.  This is what I did:

[I]Please note that this is experimental and GG-Game has no  support/affiliation for this process. You are entirely on your own here.  This is just an experiment that I did and succeeded.


[/I]1) Visit [www.winehq.org]("http://www.winehq.org/")  and follow the instructions there to get Wine to run on your favourite _**[COLOR=#ff0000]Linux[/COLOR]**_ flavour.
2) After Wine is set up, you need to install VC++ Framework. For this  you'd need to just double click on the installation *.exe file and Wine  will start it up for you.

3) Now you need to get Microsoft Internet Explorer 6 to run because  GG-Client does make use of IE in its working. Install it the same way  you installed VC++ Framework.

4) Download the zip version of GG-Client and install it, again through  Wine or just copy the GG-Client that you have on Windows to a _**[COLOR=#ff0000]Linux[/COLOR]**_ Partition.

5) Go to the GG-Client directory and bring up the console in it. Now  type the following command:

wine GGClient.exe


this will show many messages in the console and GG-Client window will  finally be displayed.. :)

Login to the client.

[http://www.garena.com/forum/viewthread.php?tid=47183&highlight=linux](http://www.garena.com/forum/viewthread.php?tid=47183&highlight=linux)

---

### Post by H0lyGanGs7eR on 2010-07-20
Take a look at the 3rd comment on the link i posted. There is a guy who said that he ran Garena 2010 on 15th june 2010 :)

---

### Post by Dalinor on 2010-07-23
Hi people. Im try to play war in Linux a 2 days ago.
I install the Game... install Garena. Kill winedevice.exe, but in the time do run the game... a error occur.

But... now, i run the Warcraft III, and i cant see the other games.

I just... indicate "C:\Program Files\Warcraft III\Frozen Throne.exe" with parameter -opengl **instead** C:\Program Files\Warcraft III\War3.exe".

This work for me.
Oh sorry, i use Slackware, 13.1, and install the binary package (txz).

Try this trick in Ubuntu.

Bye

---

### Post by asdfoo on 2010-07-30
> **H0lyGanGs7eR said:**
> Take a look at the 3rd comment on the link i posted. There is a guy who said that he ran Garena 2010 on 15th june 2010 :)

Install wine-1.3.0 and it should work now.

---

### Post by H0lyGanGs7eR on 2010-08-07
This is the way how to do it, but please tell me exactly how to patch my wine with AcceptEx. I have never worked with git.
> Hi, 


As of 2010-07-15, with a few tricks, Wine + Garena + Warcraft III seems to work ok together. 


I have just started from scratch to make sure it works. And I'm trying to recap what I've done. 


Wine used: [ repo.or.cz/wine/hacks.git ]("git://repo.or.cz/wine/hacks.git") 
I used this version only because it already has the AcceptEx patch  in it. As far as I know, git wine will also work if you apply the  AcceptEx patch yourself. 


1. Starting with a fresh WINEPREFIX, for example: 
   $ mkdir /home/pigeon/tmp/wc3 
   $ export WINEPREFIX=/home/pigeon/tmp/wc3 


2. I first run winecfg to configure a virtual desktop of 1024x768, a personal preference really. 


3. Install Warcraft III, then Frozen Throne, then update with the  latest patch. You can download patches from Blizzard's ftp. I upgraded  mine via battle.net. 

   If you have an already installed Warcraft III, you can use it by  copying the whole installed directory into the new WINEPREFIX. You may  also want to import some old registry too. 


4. I used winetricks to install ie6. This makes certain GUI part of  Garena work. I also tried gecko and it doesn't work as well as ie6  within Garena. But I believe this does not affect the actual game play. 


5. Install Garena. Don't let the installation run Garena yet. 


6. Run Garena with WINEDEBUG=+relay. For example: 
   $ WINEDEBUG=+relay wine "c:\Program Files\Garena\Garena.exe" 2>/dev/null 

   Note that the +relay slows everything down quite a bit. But it's  still quite playable, at least on my 3+ years old laptop. Without the  +relay, Garena's war3hook.dll will crash when you try to join a game (or  when someone else joins your game) in Warcraft3. 


7. Run 'ps axw | grep winedevice' from another terminal until you see processes like this: 

20742 ?        Sl     0:00  C:\windows\system32\winedevice.exe MountMgr                                                          
20764 ?        Sl     0:00  C:\windows\system32\winedevice.exe GarenaPEngine 


8. Kill the process with GarenaPEngine, e.g. kill 20764 

   If you are really lazy, you can also just keep typing 'killall  winedevice.exe' until Garena's GUI comes up. It will kill that MountMgr  in this case, but it doesn't seem to affect Garena and Warcraft3. 


9. Garena's GUI should come up. From this point onwards, you should  be fine. You can join a room, start Warcraft3, see other's games, join  games, and play games. Remember to setup the path to Warcraft 3 to run  war3.exe. 


10. Goto Oceania, one of the Australia DotA Rooms, look for me, say hi, and maybe we can play a game ;)

---

### Post by thenellt on 2010-08-07
Sorry garena 2010 seams to have completely broken compatibility. Check it [[COLOR="Blue"]here[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19336") in appdb. According to appdb, wine version 1.2 stable doesn't work either.

---

### Post by thenellt on 2010-08-07
Here is a step by step updated for 1.2 stable: (taken from [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1084985"))
just replace 1.1.24 with 1.2 or 1.3 depending on which source you use.

For compiling wine 1.1.24 on ubuntu jaunty.

Steps I have taken to compile wine with the patch are as follows (although all steps may not be needed):

DEPENDENCIES:

Make sure you remove any existing wine installations or configurations.

I donk know id it matters but if you have had a previous installation of wine the configuration directory is in you home directory. Delete (after backup?) all the contents of ".wine"

Code:
sudo apt-get install build-essentials
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get build-dep wine
Copy information for patch from the following link [http://bugs.winehq.org/attachment.cgi?id=8368](http://bugs.winehq.org/attachment.cgi?id=8368) into a file named "acceptex.patch".

Download the latest (another if you like but I'm doing latest) from [http://sourceforge.net/project/showf...ckage_id=77449](http://sourceforge.net/project/showf...ckage_id=77449).

Extract the wine source code into its own directory EG. "wine-1.1.24-source"

Copy the patch file created earlier into the folder the wine source was extracted.

Code:
cd ./wine-1.1.24-source
Code:
patch -p1 < acceptex.patch
COMPILING:

Code:
./configure
Output ening in "configure: Finished. Do 'make depend && make' to compile Wine." means this has completed successfully.

At this point it is time to make a cup of coffie / pot of soup / walk the dog. You may have enough time to do all of these things ZZzZzzzZzzzz....

Code:
make depend && make
INSTALL:

The install command must be run with sudo as the installer needs permissions to modify copy etcc to /usr ++ more
Code:
sudo make install

---

### Post by H0lyGanGs7eR on 2010-08-07
Dude, this quote is from the same link you gave me, just read below. I tried like it is said in the link, I compiled, but Linux didn't detected the new version. In the quote is said to try with GIT. Does anybody know how works this thing "GIT" ? :p

---

### Post by asdfoo on 2010-08-07
It's "Git", not "GIT".

It shouldn't be necessary, the latest fix is in 1.3.0.

---

### Post by H0lyGanGs7eR on 2010-08-08
Are you sure that Wine 1.3 has AcceptEx patch? You said the same for version 1.2..... Do you know where can I see the changelog of the new Wine?

---

### Post by H0lyGanGs7eR on 2010-09-02
Great news!!! Garena 2010 works perfect with wine 1.3.1, the last problem is that i can't see games in War3, so I need AcceptEx patch for Wine, to do it. Please write a small manual how to do it! Thanks a lot!

---

