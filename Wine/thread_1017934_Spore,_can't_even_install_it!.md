---
title: "Spore, can't even install it!"
date: 2008-12-21
forum: Wine
---

### Post by Alexpants on 2008-12-21
I'm currently using an Acer 5520G laptop with Ubuntu 8.10
I'm not dual-booting, and I don't have another PC or a copy of Windows and I'm ITCHING to play spore again. 
I've got the galactic edition, but when I put the DVD-ROM in and try to use the auto run I get;
"Error starting autorun program: Permission denied"
I tried browsing the DVD-ROM for the exe install file but I can't find one :(
I've searched the forums and google'd a bunch but can't seem to find a resolution. Any help is really appreciated! 

P.S - I'm still learning with all this, so any command line stuff might need to be idiot proof *blushes*

---

### Post by compguy248 on 2008-12-21
i have the same edition.  i believe there is a setup.exe on the root of the disc.

---

### Post by Alexpants on 2008-12-21
I thought so too, but I'm unable to find it on the disk anywhere! Is there anything special I need to be doing to be able to see it?

---

### Post by thefiestysoldier on 2008-12-21
make sure permissions are correct:

Xfce:
```
gksudo thunar
```

GNOME:
```
gksudo nautilus
```

enter password

[B][U][COLOR="Red"]REMEMBER: YOU ARE NOW IN ROOT MODE: YOU CAN DAMAGE YOUR SYSTEM!!
[/COLOR][/U][/B]
navigate to the root file system(not root home directory)-> right click /media -> properties -> permissions tab -> All -> read&write


also, make sure you have wine installed:

```
sudo apt-get install wine
```

and if that still doesnt work use cedega: 

[URL="http://cedega.com"]cedega.com
[/URL]
its $4-5/month but with a lot more windows games than wine alone


also, while we're on the topic of games I must recommend [Urbanterror]("http://urbanterror.net") its a fun fps for linux, mac, and windows

---

### Post by Alexpants on 2008-12-21
I tried to change the permissions on the disk but it's telling me that the disk is read only, gargh! 
I'd heard a lot of bad things about cedega so I wanted to avoid it if possible. I gave CrossOver a try too but that wouldn't get it to work either (in fact, the only thing I could get to work in CrossOver was an old copy of "zoo tycoon" designed for win98!)

---

### Post by Grant A. on 2008-12-21
Spore comes with SecureROM which is a form a DRM that has been known to break optical drives, and stop Windows Explorer from deleting 16-bit files. It even installs itself if you hit disagree on the license agreement, which has sparked a huge anti-trust/privacy violation suit against Electronic Arts. From the looks of your signature, I don't think you want to play this game.

---

### Post by Alexpants on 2008-12-21
Sadly, I do want to play this game, and already have played it all the way through to the final stages on this very laptop before I uninstalled Vista. 
I hate the DRM they've put on the game, but I enjoy the game itself. It's a bit of a lose lose situation.

---

### Post by Alexpants on 2008-12-21
I'm still googling to try and find solutions but still can'nae find anything :( 
I can't adjust the disk from read-only at all, not even as root!

---

### Post by yoshi121212 on 2008-12-22
I believe that is because DVD's aren't writable under normal circumstances. They are stamped at a factory somewhere, never to be written to again. So I think that there must be some way of installing it without write-privileges on the drive. Have you tried something in a terminal like:
```
cd /media/cdrom0
ls
```
To find some appropriate executable for wine to go play with?

---

### Post by Alexpants on 2008-12-22
Hmmm... I can see the exe file when I do that, but I can't view it in the browser (even if I turn on the ability to see hidden files) can I run it from terminal using a command? (sorry, I'm so so useless at this!)
Would it just be by typing the exe file into terminal when I'm in the DVD's directory?

---

### Post by Alexpants on 2008-12-22
Ok, I'm all installed but now I have a brand new hell;
"The game can not start
The game needs access to the internet in order to verify ownership of
this game. Please ensure that your computer is online and try again."

Obviously I'm online, I've gone to check on the EA support site, but that only offers advice for those using windows. Argh! 
Does anyone have any idea why it's doing this?

---

### Post by yoshi121212 on 2008-12-22
Well if you find an .exe, the next step is to run it with wine. From the terminal, it should be a simple matter of:
```
wine thenameoftheexe.exe
``` and with any luck it will launch the installer without problems. I'm rather confused by how the graphical tools don't see the executable though, as they really should.

I've also had issues getting wine to work with the Internet at large, and never learned how to fix it. Perhaps you'll have better luck.

---

### Post by Changturkey on 2008-12-22
Try PlayOnLinux?

---

### Post by Alexpants on 2008-12-23
Just tried it on PlayOnLinux and STILL having the same game can not start issue :(

---

### Post by JTwigg on 2010-01-29
> **yoshi121212 said:**
> I believe that is because DVD's aren't writable under normal circumstances. They are stamped at a factory somewhere, never to be written to again. So I think that there must be some way of installing it without write-privileges on the drive. Have you tried something in a terminal like:
```
cd /media/cdrom0
ls
```To find some appropriate executable for wine to go play with?

When i insert spore disc i can only view the mac version but if i use that method i can see windows version so i
```
cd /media/cdrom0
ls
wine autorun.exe
```once installed run wine in safe mode
```
wine Sporebin/Sporebin.exe -safe
```more info here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652)
;)

---

