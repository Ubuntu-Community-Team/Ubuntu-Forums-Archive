---
title: "What would happen if you ran a windows virus using Wine?"
date: 2005-10-06
forum: The Cafe
---

### Post by Mustard on 2005-10-06
This is a bit of an idle question, but I've been recieving some windows viruses through my email the last week or so, and I have them all lined up on my desktop like trophies, all decorated with emblems to make them look pretty, when it occured to me that they might actually do something if I ran them in Wine.  Would anything happen do you think?

---

### Post by Zelut on 2005-10-06
Hmm.. it might mess with your WINE config but it isn't going to do anything to your ubuntu installation.  I'm not sure what exactly it'd do to WINE (I don't bother with it)... give it a try & let us know :)

---

### Post by Mustard on 2005-10-06
Eeek...I'm not sure what was happening, but it didn't look good. :)

I was running etherape and it looked like it was making connections to a lot of different places.  I'm going to examine my wine install. :D

---

### Post by Zelut on 2005-10-06
Hmm.. how 'bout that.  I'm honestly surprised that you actually tried it lol.  Sounds like maybe it didn't change much on your side but could have made a lot of outside connections.  If you closed it you're probably fine now... I'm just guessing right now though :)

---

### Post by Mustard on 2005-10-06
```
mustard@slave:/root$ clamscan ~/.wine/fake_windows/Windows/
/home/mustard/.wine/fake_windows/Windows/win.ini: OK
/home/mustard/.wine/fake_windows/Windows/winlogon.exe: Worm.SomeFool.Gen-2 FOUND/home/mustard/.wine/fake_windows/Windows/regid.zip: Worm.SomeFool.Gen-2 FOUND

----------- SCAN SUMMARY -----------
Known viruses: 40493
Engine version: 0.87
Scanned directories: 1
Scanned files: 3
Infected files: 2
Data scanned: 0.04 MB
Time: 1.496 sec (0 m 1 s)
mustard@slave:/root$ 
```

My wine install is definitely stuffed now....heheheh...time for a reinstall. :D

---

### Post by Wolki on 2005-10-06
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by Mustard on 2005-10-06
> SomeFool

The SomeFool first-generation worm (Netsky.D according to some folks) actually installs its winlogon.exe file under Wine, and, as an added bonus, seems to get stuck in an endless loop, thus really having a negative performance impact on my Linux machine! I'll give this one 4/5 penguins for not only running and sort of doing what it was supposed to, but actually doing mildly bad things to Linux -- at least until I hit Control-C in the terminal from which I was running Wine to stop it dead.

I got lucky and got the one that actually did something. :)

---

### Post by Mustard on 2005-10-06
Hey..check this out!  Found some more additions in my home directory...

```
/home/mustard/.local/share/applications/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/defaults.list: OK
/home/mustard/.local/share/applications/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Override.xml: OK
/home/mustard/.local/share/mime/packages/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/x-extension-79RZ1x.xml: OK
/home/mustard/.local/share/mime/application/x-extension-diz.xml: OK
/home/mustard/.local/share/mime/application/x-extension-nfo.xml: OK
/home/mustard/.local/share/mime/application/x-extension-CFG.xml: OK
/home/mustard/.local/share/mime/application/x-extension-bash_aliases.xml: OK
/home/mustard/.local/share/mime/application/x-extension-8U56IR.xml: OK
/home/mustard/.local/share/mime/application/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/x-extension-gnome-smproxy-YM2Dih.xml: OK
/home/mustard/.local/share/mime/application/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/subclasses: Empty file
/home/mustard/.local/share/mime/globs: OK
/home/mustard/.local/share/mime/magic: OK
/home/mustard/.local/share/mime/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/XMLnamespaces: Empty file
/home/mustard/.local/share/mime/aliases: Empty file
/home/mustard/.local/share/mime/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND

```

---

### Post by Zelut on 2005-10-06
wow I'm really sorry I even suggested the idea now.  I didn't think it'd do anything close to that much.  I hope you don't have to completely reinstall now.. sounds like a pain.

You see the filth we get from those windows types?  I'm going to have to stop letting my kids play with them ;)

---

### Post by Mustard on 2005-10-06
I'm not that worried about it. I've moved all the infected files to one folder now and trashed them.

The files you see in that list above were all downloaded by the virus at the time of execution.  Nothing that came up infected (outside of my fake windows directory) was there prior to the virus executing.

---

### Post by dasunst3r on 2005-10-06
[QUOTE=Wolki][http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)[/QUOTE]
Dang it... you beat me to the punch...

---

### Post by Mustard on 2005-10-06
I ended up finding more viruses in my usr directory way down deep in some /cups related sub directory.  Somehow in all the sudo'ing and mucking around I have managed to trash my Evolution Inbox, so  I ended up throwing the mondo backup CD into the drive and restored the system that way. :D

---

### Post by qiezi! on 2005-10-07
Mustard you are one game muther!  I'm sorry but I just have to lol, that made my Friday! 
Were all the virii contained in your user folder?  That would speak volumes for user-restrictions in Linux, huh?

---

### Post by Mustard on 2005-10-07
It seemed to be limited to my home folder and the /usr directory.  It was interesting to watch on etherape.  As soon as I executed it, I could see all those connections starting up with unfamiliar IP's all around the world and it similtaneously started downloading different versions of itself onto the system.  I should have deleted the ones that I still had sitting in the email inbox first, before doing a 'mv' command on all the other virii that had been downloaded, as the way I went about cleaning them up didn't sit well with Evolution afterwards.  It no longer recognised my default account in the Inbox.  That's about the only damage I can say for sure was done and that is more related to my clumsy command line work than anything else.

---

### Post by ardchoille42 on 2007-01-22
> **Mustard said:**
> Hey..check this out!  Found some more additions in my home directory...

```
/home/mustard/.local/share/applications/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/defaults.list: OK
/home/mustard/.local/share/applications/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/applications/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Override.xml: OK
/home/mustard/.local/share/mime/packages/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/packages/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/x-extension-79RZ1x.xml: OK
/home/mustard/.local/share/mime/application/x-extension-diz.xml: OK
/home/mustard/.local/share/mime/application/x-extension-nfo.xml: OK
/home/mustard/.local/share/mime/application/x-extension-CFG.xml: OK
/home/mustard/.local/share/mime/application/x-extension-bash_aliases.xml: OK
/home/mustard/.local/share/mime/application/x-extension-8U56IR.xml: OK
/home/mustard/.local/share/mime/application/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/x-extension-gnome-smproxy-YM2Dih.xml: OK
/home/mustard/.local/share/mime/application/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/application/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/subclasses: Empty file
/home/mustard/.local/share/mime/globs: OK
/home/mustard/.local/share/mime/magic: OK
/home/mustard/.local/share/mime/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/XMLnamespaces: Empty file
/home/mustard/.local/share/mime/aliases: Empty file
/home/mustard/.local/share/mime/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/mime/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Microsoft WinXP Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Teen Porn 16.jpg.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Adobe Premiere 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Adobe Photoshop 9 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Best Matrix Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Porno Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Dark Angels.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/XXX hardcore pic.jpg.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Microsoft Office 2003 Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Serials.txt.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Screensaver.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Full album.mp3.pif: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Ahead Nero 7.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Virii Sourcecode.scr: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/E-Book Archive.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Doom 3 Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/How to hack.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Learn Programming.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/WinXP eBook.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Win Longhorn Beta.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Dictionary English - France.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/RFC Basics Full Edition.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/1000 Sex and more.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/3D Studio Max 3dsmax.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Keygen 4 all appz.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Windows Sourcecode.doc.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Norton Antivirus 2004.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Gimp 1.5 Full with Key.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Partitionsmagic 9.0.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Star Office 8.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Magix Video Deluxe 4.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Clone DVD 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/MS Service Pack 5.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/ACDSee 9.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Visual Studio Net Crack.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Cracks & Warez Archive.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/WinAmp 12 full.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/DivX 7.0 final.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Opera.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/IE58.1 full setup.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Smashing the stack.rtf.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Ulead Keygen.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/Lightwave SE Update.exe: Worm.SomeFool.Gen-2 FOUND
/home/mustard/.local/share/The Sims 3 crack.exe: Worm.SomeFool.Gen-2 FOUND

```

This one of the reasons I feel that using wine is a bad idea.

---

### Post by steve.horsley on 2007-01-22
Looks like wine is slowly getting more Windows compatible. There should not have been anything inteh /usr directory though - not if he ran the virus as his own account id. 

It certainly shows the folly of Wine's default behaviour of mapping Z: to /. That virus could have read anda forwarded all manner of sensitive info.

---

### Post by Zyphrexi on 2007-02-08
well perhaps the wine devs don't expect us to RUN viruses...

---

### Post by shane2peru on 2007-02-22
Wow, well I will have to say I just had a similar incident!  I have a usb stick I use to take my work to different places.  I took it to a printer here in Peru (all the windows computers here have viruses!)  and it was infected.  I didn't think nothing of it, I removed the infected files, except one that I didn't believe, because it was my program, and one I run in wine.  I ran it and it acted really funny.  The I cancelled it.  The I ran the virus scan again, and there were more viruses (worms to be exact) on my usb stick.  I ran the virus scan (clamscan) on my other partition and it too was full of viruses.  I found out that 
[SIZE="6"]**YES VIRUSES WORK ON LINUX WITH WINE!**[/SIZE]  
I have yet to find where it messed up my Ubuntu system.... full scan going on at the moment... but it put viruses many places on my system, and that is not good because I **often** take my usb stick to my wife's computer (XP) and plug it in.  I will post the scan results when it gets done, if it is worth posting.

I'm not Re-installing
I'm not Restoring
I'm Removing viruses 

  Does anyone have any good suggestions on how to do that?  Thanks


Shane

---

### Post by linux_kid on 2007-02-22
Thats scary to do that...
Some stupid Windows User may have executed the file and caused some real crap ](*,)

---

### Post by X-626 on 2007-02-22
That's very scary.  I think I'll only allow Wine to access my fake C: folder...
Although, I normally only use Wine to run *certain* programs.  I've barely used Wine since I installed it.  That is very interesting, though.  I guess Wine is getting closer to being able to run **all** Windows programs (viruses included).  Well, now we know it's especially good to have a virus scanner if you're going to be running many apps on Wine.

---

### Post by aktiwers on 2007-02-22
Interesting! Gonna try to scan mine now, just for the fun :)

---

### Post by shane2peru on 2007-02-22
Ok, here is what happened.  I ran the program maybe for about 5-10 Seconds and then killed it.  However it put programs in memory, and they continued running for maybe about 10 min untill I killed everything.  Here is what happened.  I have a 8 Gig partition that is full of all my work.  While the thing was running it managed to really expand itself.  In every folder that I have in an 8Gb partition I have a very lot of partitions, it made and exe file after the folder name.  Ex:

Folder name - htmlwork
inside that folder is an htmlwork.exe file that is a virus. 
I have literally 100's of viruses on that partition, in a matter of 10 min, and it is still scanning after 3 hours of scanning.  Does anyone have a simple way of removing these?  I can go and manually do it, but it will take me a considerable amount of time.  The folder names very extensivelly, many of them contain spaces ect.  **HELP!**  

A good peice of advice **[SIZE="5"]VIRUS SCAN EVERY .EXE, .BAT, .COM OR OTHER MISC WINDOWS FILE YOU DOWNLOAD BEFORE YOU RUN IT IN WINE!!![/SIZE]**

Shane

---

### Post by Luk0r on 2007-02-22
```
cd /
rm -rf *.exe
```
? :D

---

### Post by shane2peru on 2007-02-22
> **Luk0r said:**
> ```
cd /
rm -rf *.exe
```
? :D

If I'm not mistaken that would remove every .exe file on that partition, or direcotry recursively?  I have a lot of old downloaded Windows programs that I really don't want to get rid of.  And several that I run in Linux under wine.  I did find a way to do this with clamscan.  I'm moving them all to a separate directory for revision.  I have yet to find any of my filesystem infected, just the data partition that my user name has write permissions to.  So far it has moved 177 files there for me to review and delete.  Thanks for the help though!

Shane

Oh, the command is pretty simple ```
clamscan --move=directory/to/move/infected/files name -ri --no-mail /directory/to/scan
``` any doubts just use man clamscan and it will give you the scoop.

---

### Post by n00bWillingToLearn on 2007-02-23
Just run wine as an underprivileged user that only has read and write access to ~/.wine ( I would't even give it read access to / as it could read and transmit sensitive data ). Windows privilege escalation attacks don't work in wine ( the emulation isn't THAT good :) ) and the virus will think that it has Administrator privileges and access to the entire ( fake ) C: drive anyways, it's like a chroot jail.

---

### Post by mistab1034 on 2007-02-23
So you people that have been running an anti-virus, is that a Linux side anti-virus or a anti-virus installed and running in wine? I find it interesting if a Linux side anti-virus finds wine'd windows viruses. But I also don't funny understand how wine works so I could be missing something.

---

### Post by cearum on 2007-02-23
I wonder what would happen if someone ran a virus using wine as root, with / mounted as a drive in wine. I have a free partition.... I'm tempted to try. Of course not mounting any other drives so it doesn't spread outside too far.  :D

---

### Post by andymo on 2007-02-23
Cool, you got dugg!!

---

### Post by GoneSouth on 2007-02-23
Recursively delete all .exe files in a directoy:

```
find <dir> -name '*.exe' -exec rm {} \;
```

Recursively move all .exe files to some other directory

```
find <dir> -name '*.exe' -exec mv {} <dest dir> \;
```

---

### Post by cantormath on 2007-02-23
NOTHING!!!!!!!!!!!!!!!!

Its likegoing to Russia(Linux) and saying F-OFF(Virus), no one would understand you, except the interpreter(Wine). :KS

---

### Post by Mr Frosti on 2007-02-23
Just a heads up for those thinking that "rm -rf *.exe" is a good idea...

C# based projects (including Beagle, F-Spot, and more [here]("http://en.wikipedia.org/wiki/Mono_(software)#Software_developed_with_Mono")) are compiled to have a .exe extension. This will take out these applications as well as any virus files. Also, not all virus files have a .exe extension.

---

### Post by cantormath on 2007-02-23
> **Mr Frosti said:**
> Just a heads up for those thinking that "rm -rf *.exe" is a good idea...

C# based projects (including Beagle, F-Spot, and more [here]("http://en.wikipedia.org/wiki/Mono_(software)#Software_developed_with_Mono")) are compiled to have a .exe extension. This will take out these applications as well as any virus files. Also, not all virus files have a .exe extension.

Second that.

---

### Post by Bagboy23 on 2007-02-23
> **Mustard said:**
> This is a bit of an idle question, but I've been recieving some windows viruses through my email the last week or so, and I have them all lined up on my desktop like trophies, all decorated with emblems to make them look pretty, when it occured to me that they might actually do something if I ran them in Wine.  Would anything happen do you think?

LOL

---

### Post by FullMetlaMonkey on 2007-02-23
Man, I think I'm gonna go re-install Wine to see if it will run any of the viruses I have lying around.

BTW. This story has been Dugg :) [http://digg.com/linux_unix/What_would_happen_if_you_ran_a_Windows_virus_in_Linux_using_wine](http://digg.com/linux_unix/What_would_happen_if_you_ran_a_Windows_virus_in_Linux_using_wine)

---

### Post by Obor on 2007-02-23
I've tried this couple of months ago. Can't remember what was the name of the virus but after I ran it in wine it sat in my systray and copied itself into few places. I found it afterwards with Clamav, luckily it was restricted to my wine folder. It was fun but I wouldn't try it again  :)

---

### Post by shane2peru on 2007-02-23
> **mistab1034 said:**
> So you people that have been running an anti-virus, is that a Linux side anti-virus or a anti-virus installed and running in wine? I find it interesting if a Linux side anti-virus finds wine'd windows viruses. But I also don't funny understand how wine works so I could be missing something.
I'm running ClamAv native in Linux not under wine.  I haven't used any wine programs since I discovered the virus, and have been scanning my system to get rid of it.  If wine runs, it could potentially spread the virus again, and I would spend all this time scanning again.  


> **cearum said:**
> I wonder what would happen if someone ran a virus using wine as root, with / mounted as a drive in wine. I have a free partition.... I'm tempted to try. Of course not mounting any other drives so it doesn't spread outside too far.  :D

Try it at your own risk.  I assume that is would only be a bothersome problem and not a serious system threat.  So far mine only created a bunch of viruses in many folders.  I'm up to over 1,000 viruses that it created on my computer and still searching.  I have 2 external hdd that were attached and mounted at the time so I'm scanning them as well.  Very time consuming, but doesn't seem to be any damage.

Shane

---

### Post by FullMetlaMonkey on 2007-02-23
I don't know if this will help much, but I would recommend the linux version of Avast anti-virus for the virus cleanup.  I used it once to clean up a friends computer that wouldn't even boot!
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

---

### Post by shane2peru on 2007-02-23
> **FullMetlaMonkey said:**
> I don't know if this will help much, but I would recommend the linux version of Avast anti-virus for the virus cleanup.  I used it once to clean up a friends computer that wouldn't even boot!
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

Thanks!  I will give it a try after I finish with ClamAv.  I already have/had ClamAv.  It seems to be doing the trick, however I will give Avast a try after ClamAv is done and see if it missed anything.  Downloading it now.

Shane

---

### Post by vinmar on 2007-02-23
This just shows how great Wine is. Windows virii bust your PC, exactly as they would under Windows.

---

### Post by earobinson on 2007-02-23
you should really check that wine only has the drive c before you do it, eg not the drive z that maps to the rest of your computer!

---

### Post by rasbach on 2007-02-23
So let me get this straight, I spend hours trying to get a program to work they way that I want it to in WINE-but a virus has no problem running on it's own?


[SIZE="6"]YES- WINE REALLY IS LIKE WINDOWS!!![/SIZE]

---

### Post by stu on 2007-02-23
> **rasbach said:**
> [SIZE="5"]YES- WINE REALLY IS LIKE WINDOWS!!![/SIZE]

Please quit it with the caps.

---

### Post by linuksamiko on 2007-02-23
> **shane2peru said:**
> I'm running ClamAv native in Linux not under wine.  I haven't used any wine programs since I discovered the virus, and have been scanning my system to get rid of it.  If wine runs, it could potentially spread the virus again, and I would spend all this time scanning again.  


It is unlikely that wine can spread any of your viruses if you delet your ~/.wine folder and create a new .wine directory. This will be like a complete new windows installation. But make sure that no wine-process is running when you delet ~/.wine so you probaply have to kill some processes.




But I'm still not sure what happened to some of those guyes in this thread. Some said that they had files on drive Z: (which is usually / ) but how could the virus copy anything on / when you open wine as user? Or did somebody start wine as root?
:confused:

---

### Post by shane2peru on 2007-02-23
> **linuksamiko said:**
> It is unlikely that wine can spread any of your viruses if you delet your ~/.wine folder and create a new .wine directory. This will be like a complete new windows installation. But make sure that no wine-process is running when you delet ~/.wine so you probaply have to kill some processes.

True, but would also require I completely re-setup wine.  I had a nice wine setup, that took some work to achieve.  I'm wait for the scanning to stop and see if all was removed and still works first.



> **linuksamiko said:**
> 
But I'm still not sure what happened to some of those guyes in this thread. Some said that they had files on drive Z: (which is usually / ) but how could the virus copy anything on / when you open wine as user? Or did somebody start wine as root?
:confused:

Actually I think that drive Z: is mapped to /home/user/  Kind of like My Documents.  I could be wrong, but I think that is how it works.  I didn't start wine as root, and I did have some 700+ viruses in my /home/user directory.  Just finished that scan.  What a learning experience.

Shane

---

### Post by Old Pink on 2007-02-23
Great topic, no wonder it made top of digg. :lol:

---

### Post by linuksamiko on 2007-02-23
> **shane2peru said:**
> 

Actually I think that drive Z: is mapped to /home/user/  Kind of like My Documents.  I could be wrong, but I think that is how it works.  I didn't start wine as root, and I did have some 700+ viruses in my /home/user directory.  Just finished that scan.  What a learning experience.

Shane

AFAIK is /home/user/ drive N: (with basic settings) and Z: is / but this doesn't matter anyway. The big question is:
Could a virus write something on / if the user doesn't have write permission? I don't know how that could be possible but maybe it is a security breach in wine or something like that.
Somebody in this thread said that he had viruses in /usr/<DIRECTORY>/ but how can something like this happen if you are a regular user?

---

### Post by shironeko on 2007-02-23
Got a question. How is the virus, emulated by wine, supposed to be able to copy itself to / directories if it didn't get any SUDO privileges?

Btw. I want to restrict wine to my /.wine folder. How do I do that?
Is there a way ubuntu can warn me before opening any executable file?

---

### Post by juhanfg on 2007-02-23
> **shironeko said:**
> Got a question. How is the virus, emulated by wine, supposed to be able to copy itself to / directories if it didn't get any SUDO privileges?

Btw. I want to restrict wine to my /.wine folder. How do I do that?
Is there a way ubuntu can warn me before opening any executable file?

Hi,

Run winecfg and go to the hardrives tab. Remove the entries that you want.

That should make wine not see anything but what you leave there.

J

---

### Post by guarnibl on 2007-02-23
lawl,

this is why i love you guys... running viruses in ubuntu just to see what would happen. I lol'd.

---

### Post by badgie523 on 2007-02-23
> **vinmar said:**
> This just shows how great Wine is. Windows virii bust your PC, exactly as they would under Windows.

XD  Ha ha!  That made my day.

---

### Post by redfez on 2007-02-23
Do you relize that you have posted a a log of files on your system that appear to be not of the legal ilk if you will. :)

---

### Post by MannaPC on 2007-02-23
> **redfez said:**
> Do you relize that you have posted a a log of files on your system that appear to be not of the legal ilk if you will. :)

I do seriously hope you are joking and know those are fake files intended to make you think what you just said and open them...

If not, I laugh at your stupidity :lolflag: !

---

### Post by owenleej on 2007-02-23
> **redfez said:**
> Do you relize that you have posted a a log of files on your system that appear to be not of the legal ilk if you will. :)

YOU run a virus and lets see what stuff it decides to install for YOU and then we can blame YOU for it! Awesome!

---

### Post by jobo5432 on 2007-02-23
Wow...look at all the warez in that folder, and to think it was all infected...That sucks man.

---

### Post by trmentry on 2007-02-23
This is why I run my windows applications inside a VMWare install of XP on vmware server.  I just RDP into the machine and run what I need.  If it goes all wonky, then I just restore back to the last known good snapshot and move on.

---

### Post by faradesla on 2007-02-23
That's hilarious. I hope you got everything fixed, Mustard.

I guess this is just further testament to how well WINE works.

---

### Post by MannaPC on 2007-02-23
> **jobo5432 said:**
> Wow...look at all the warez in that folder, and to think it was all infected...That sucks man.

It's not warez at all...! It's infected files named to look like warez which will entice you to open said files..

---

### Post by shane2peru on 2007-02-23
Well, two scans still finishing up, but I don't expect them to turn anything up, they haven't so far.  I had a grand total of 1305 viruses on my computer.  All in my /home/user partition and my /mnt/data partition that stores all my work.  That is all!  Probably will have to re-install a few of my wine programs but nothing more than time lost.  If it had been windows that would not have been the case!

Shane

---

### Post by oolunchbox on 2007-02-23
Unless I've misread any of the posts nobody has actually touched on why it worked like it did.  My understanding of Wine is that it's a "compatibility layer" (WINE itself stands for WINE IS NOT an EMULATOR). Being a compatibility layer it translates commands sent from windows programs into commands Linux understands, thus allowing the program to run. The comment about being in Russia and telling someone to F off is incorrect, wine works like the translator- it receives the foreign windows commands and tells your linux system how to make it work (the russian wouldnt know what you said until the translator told them, then they would understand, and get rightfully angry). Apparently the virus sent instructions to create or download files to the users main directory thus all the files in the /home directory and /usr directory.

or maybe im wrong.

---

### Post by ardchoille42 on 2007-02-24
> **oolunchbox said:**
> Unless I've misread any of the posts nobody has actually touched on why it worked like it did.

Because **wine runs Windows programs**.. including viruses, trojans, worms, etc. I've been saying this for a while but no one listens, now we have proof. And, as you saw from an earlier post, those viruses, trojans, worms can wreak havoc in any folder in $HOME as well as system folders. If the infected user runs a virus within the sudo timeout of running a command with sudo, the virus can gain sudo privs. Think about it, if the user runs "sudo command", there is a certain amount of time that the sudo password is cached. If the user runs a virus that calls sudo within that sudo cache timeframe, then the virus can run "sudo rm -rf /" and that command will succeed because the virus is running as the sudo user with sudo privs:

> **Mustard said:**
> I ended up finding more viruses in my usr directory way down deep in some /cups related sub directory.  Somehow in all the sudo'ing and mucking around I have managed to trash my Evolution Inbox, so  I ended up throwing the mondo backup CD into the drive and restored the system that way. :D

> **Mustard said:**
> It seemed to be limited to my home folder and the /usr directory.  It was interesting to watch on etherape.  As soon as I executed it, I could see all those connections starting up with unfamiliar IP's all around the world and it similtaneously started downloading different versions of itself onto the system.  I should have deleted the ones that I still had sitting in the email inbox first, before doing a 'mv' command on all the other virii that had been downloaded, as the way I went about cleaning them up didn't sit well with Evolution afterwards.  It no longer recognised my default account in the Inbox.  That's about the only damage I can say for sure was done and that is more related to my clumsy command line work than anything else.

This is why I say wine/cedega/cxoffice/other are bad things and should not be used at all. It wouldn't be hard (probably already been done) to write a keylogger into a Windows file and capture every keystroke you make and send all your personal info to a server where it is sold to the highest bidder. Some folks think that running Windows apps in wine offers them some layer of protection against bad Windows apps, but this is simply a myth.

I don't know about others, but the files in my $HOME are more important to me than the rest of the system. I won't ever use Windows files on any of my systems.. and now you see why.

---

### Post by MrHorus on 2007-02-24
> **ardchoille42 said:**
> 
This is why I say wine/cedega/cxoffice/other are bad things and should not be used at all. 

That's like saying ATMs, debit cards and computers are bad things are people can use them to defraud you so you should stay well clear.

Wine, Cenege and Crossover Office are tools, just like a hammer.

If you do stupid things with your hammer then you will bash your finger and get hurt; if you do stupid things with Wine then your system will get hurt.

It doesn't mean I won't use them, just I will be careful and not do anything blatantly stupid like trying to run malware or virii. I wouldn't willingly do it in Windows, so why should I do it in Linux? :)

---

### Post by shareMenaPeace on 2007-02-24
While reading here and on digg many wondered about the virus files which been created.
Specialy the one with "teen porn" in the filename.

> What was Matthew Bandy accused of? Jeannie and Greg Bandy were shocked to discover that their son was charged with possession of child pornography.

One December morning two years ago, Matthew's life took a dramatic turn. In an exclusive interview with "20/20," the Bandy family reveals how the world as they knew it came crumbling down, and how Matthew's life has since changed.

....

"We faced 10 years per count, there were nine counts," said Novak. "If Matt was convicted, those sentences would have to be served consecutively. In other words, he would have been sentenced to 90 years in prison. He would have served time until he died."

Matthew was in an awful predicament, and he tried to keep his house arrest a secret. He wore longer pants to hide the ankle bracelet, but he was scared he would be discovered.
 **The shy young boy could not explain how such pictures appeared on his computer hard drive.** The stress of the situation got so bad for Matthew that he told his parents the charges hanging over his head made high school impossible.

"He said 'Mom, I'm hurting,'" said Jeannie. "'I can't sleep. I don't want to disappoint anybody, but I just can't go on anymore.'"
[http://abcnews.go.com/2020/LegalCenter/story?id=2785054&page=1](http://abcnews.go.com/2020/LegalCenter/story?id=2785054&page=1)

It wasnt the same scenario but basicly means, that using windows systems are very dangerous to use in these prospects, at least in those states/countrys.
And this means also that the law is flawed here aswell, destroying lives of innocent because the state has insufficiant information/knowledge of the technologie/user which is judged.

---

### Post by ardchoille42 on 2007-02-24
> **MrHorus said:**
> That's like saying ATMs, debit cards and computers are bad things are people can use them to defraud you so you should stay well clear.

Wine, Cenege and Crossover Office are tools, just like a hammer.

If you do stupid things with your hammer then you will bash your finger and get hurt; if you do stupid things with Wine then your system will get hurt.

It doesn't mean I won't use them, just I will be careful and not do anything blatantly stupid like trying to run malware or virii. I wouldn't willingly do it in Windows, so why should I do it in Linux? :)

How many people who have suffered a virus/trojan/worm did so intentionally? Accidents can happen, even when you're careful, but using a poorly designed operating system (and I use the term "operating system" loosely) simply increases your chances of problems.

People who use Windows apps are always going to find fault in the words and opinions of those of us who criticise the many flaws in that POS operating system.

---

### Post by shane2peru on 2007-02-24
> **ardchoille42 said:**
> Because **wine runs Windows programs**.. including viruses, trojans, worms, etc. I've been saying this for a while but no one listens, now we have proof. And, as you saw from an earlier post, those viruses, trojans, worms can wreak havoc in any folder in $HOME as well as system folders. If the infected user runs a virus within the sudo timeout of running a command with sudo, the virus can gain sudo privs. Think about it, if the user runs "sudo command", there is a certain amount of time that the sudo password is cached. If the user runs a virus that calls sudo within that sudo cache timeframe, then the virus can run "sudo rm *** /" and that command will succeed because the virus is running as the sudo user with sudo privs:

I think this is very extremely highly unlikely scenario, unless the virus was made to look for a sudo command, which would mean it was actually made for Linux, and then why would they go through the trouble of making it for windows, why not just make it for Linux.  Secondly I just got rid of over 1300 viruses on my computer, it didn't mess my system up at all!  All it did was replicate itself and set dormant waiting to be run with wine, and the worst it could do is ruin my wine installation, which isn't that big of a deal.  In all technicality, I didn't even need to remove the 1300 viruses I had, I only did because I share a lot of info with my wife's computer with XP.  It really did no damage to my linux system.




> **ardchoille42 said:**
> This is why I say wine/cedega/cxoffice/other are bad things and should not be used at all. It wouldn't be hard (probably already been done) to write a keylogger into a Windows file and capture every keystroke you make and send all your personal info to a server where it is sold to the highest bidder. Some folks think that running Windows apps in wine offers them some layer of protection against bad Windows apps, but this is simply a myth.

I don't know about others, but the files in my $HOME are more important to me than the rest of the system. I won't ever use Windows files on any of my systems.. and now you see why.

I for one can tell you if we didn't have wine/cedega/cxoffice/other I for one, would still be dual booting.  There are some really great applications out there for Windows, whether we like it or not, it is the most widely used OS on the market, and to make money, the programmers (not all) are going to be making programs for Windows.  -- That is not to say anything against our wonderfull Linux programmers that are doing a good job with Ubuntu, Linux, and the many packages that are out there.  However there isn't the comparison because of the $ involved in windows.  At least that is my thoughts on it.  I don't think that wine is a bad thing, and viruses/trojans/worms etc are made in such a way that they will run on anything.  I mean have you ever read a virus labeled, for Win XP only.  :lolflag:   So no I'm not surprised or impressed that a virus runs on wine.  If you are going to run those programs and want to protect yourself you better 1.  Know the source of where any program came from  2.  Have an antivirus that can check for these kind of things.  And you should should also realize that this could be a problem with Linux too, you better know the source of where the program came from, or you could have problems in your Linux box.  

Shane

---

### Post by PriceChild on 2007-02-25
Back on topic please.

NO more references to unsuitable material. I will however leave most of the previous posts in place as they "may" be legitimate.

---

### Post by SuSUntu on 2007-02-25
> **PriceChild said:**
> Back on topic please.

NO more references to unsuitable material. I will however leave most of the previous posts in place as they "may" be legitimate.

I just read through this thread, and I completely disagree with your decision to leave the defaming posts by cantormath and StarscreamD.

They are making harmful comments against another user based solely on their ignorance of the virus under discussion.

A simple search would have cleared up any of their assertions but they decided to attack Mustard with some pretty vile accusations instead. Even if they are joking, it is not funny.

See this article which describes the exact behavior shown in the file lists supplied by Mustard:
[http://www.symantec.com/security_response/writeup.jsp?docid=2004-032110-4938-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2004-032110-4938-99&tabid=2)

---

### Post by PriceChild on 2007-02-25
I have re-read and removed all accusations that I can find.

I'm sorry that I didn't have time earlier to read the entire thread but I have done so now.

Personally I'm not surprised the virus's run well under wine... they are very basic programs.

Great experiment though :)

Pricey

---

### Post by john_spiral on 2007-05-12
If you install wine via synaptic are the default security settings enough to protect your system from Windows viruses?

Really interesting thread!

---

### Post by Tundro Walker on 2007-05-12
If it just botches your WINE install, then you can re-install.  But, if it's re-sending itself from your computer, that's still bad.

In genetics, your computer would be what's called a "carrier"; it's personally immune to the virus(es) it's carrying, but can transmit them to others.

For a demonstration of this...go see "28 Weeks Later"

---

### Post by borris.morris on 2007-05-12
I wanted to try this out for my self... but sadly I can't find any virii in my linux install. j/k

---

### Post by bodhi.zazen on 2007-07-28
I would also like to make people aware of this thread regarding wine and running viruses :

I am not sure of the implications of this, it is something I have followed.

My comments are that if you find what you feel is a vulnerability, please report it to Launchpad :

[Launchpad](http://www.lauchpad.net)

The thread is quite old (Started in 10/05) and I am reporting the more recent activity this thread now and will post an update if one becomes available.



In the past there *HAVE* been holes in the wine code that allowed viruses to run on wine, but these have been patched. In reviewing that thread :

[list=number][*]The command to run the virus was initiated by the user, ie wine did *NOT* spontaneously run the code.
[*]It appears to my review that only the home directory was affected so unless you ran the virus as root the system does not appear to be compromised.
[*]The offending worm was "Some Fool" and from here : [http://os.newsforge.com/article.pl?sid=05/01/25/1430222](http://os.newsforge.com/article.pl?sid=05/01/25/1430222)

> **SomeFool**

The SomeFool first-generation worm (Netsky.D according to some folks) actually installs its winlogon.exe file under Wine, and, as an added bonus, seems to get stuck in an endless loop, thus really having a negative performance impact on my Linux machine! I'll give this one 4/5 penguins for not only running and sort of doing what it was supposed to, but actually doing mildly bad things to Linux -- at least until I hit Control-C in the terminal from which I was running Wine to stop it dead.
[*]The thread became "active" again with a similar report posted in 1/07.
[*]Some users on that thread discuss modifying the wine environment to allow viruses to run on wine by adding missing windows .dll IMO this is akin to saying "windows viruses run on windows code" which is very different then windows viruses running on wine code.
[*]So if you modify the code be sure you understand the security implications.[/list]

IMO this falls under social engineering and/or the caution about running code from untrusted sources ...

[indent]He he he ... including windows .dll[/indent]

---

### Post by frup on 2007-07-28
I take it the fake files like cracks found later are to spam p2p networks etc.
The comment about the jackhammer is funny because unless you're a complete idiot, you will take safety precautions.

I'm glad I'm a gpl fanatic. If I was a 60 year old single female I might take up RMS's offer. Apart from ubuntu's default install there is nothing proprietary on my install... I'm too lazy to fix that.

---

### Post by Civean on 2007-08-28
Hello,
I would like to revive this thread with a slightly different question. Today I found one of these spamvertisments that tries to present themselves as windows dialog warning you about some security error or whatnot, and asking if you would like to "correct the problem" (ie. install some trojan mal/spy/adware). Amused by the situation (not often i see XP error dialogs in ubuntu) I clicked "yes", and some highly suspect .exe file was downloaded to my home folder. Of course I promptly executed it in wine, but sadly it didn't work. (Yes, I like to break this computer in imaginative ways) 

However, it made me think. If wine provides access to system resources such as the keyboard, network, filesystems etc, then when wine is sufficiently advanced and feature-complete, will windows keyloggers, trojans etc work seamlessly? This is something I don't see much discussion about, whether wine exposes the user to the giant universe of windows exploits... thus cancelling out one major advantage of using linux.

In short, does wine make users vulnerable to windows malware? (for example online banking frauds through keyloggers sniffing your password etc). And should there be more warnings in wine/ubuntu to make users aware of this?

---

### Post by bodhi.zazen on 2007-08-28
Well, yes and no

Mainly no because you are still running Linux. 

Yes because Wine is a compatibility layer so there is the potential for malware written for windows to run in wine.

No because all the secruity features of linux are in place. So if you run a program with wine it does not have access to system files. And, as you can see, you have to run programs manually so you would have to for example open viruses or malware manually and run with wine.

So the situation is quite complex if you are writing  malware for wine, first it has to run on windows (or to be more exact wine) *as root* and then it still has to exploit a linux vulnerability.

Both the wine project and linux are aware of security issues and holes in the wine code are patched as they are discovered/reported.

So, IMO, wine is no more or less vulnerable the Ubuntu to malware. That is to say, if you run programs/scripts from unknown sources as root you are in for trouble (weather you use wine or not to run the is irrelevant).

---

### Post by Civean on 2007-08-28
Ah, I see.

But still, aren't there less safeguards when executing .exe files in wine then in windows? You don't get any "Are you sure you want to execute this binary" warning, for example. I can very well imagine some of my less wary family members clicking "yes" on one of these "you've got an electronic gift card" and then "yes" when the run-in-wine dialog comes up... thus maybe installing a keylogger, to take the same example. (Which doesn't need an exploit to function, or?)

I downloaded a keylogger for windows right now and ran it in wine.. it worked perfectly, I even got a little icon in the gnome task bar. Presumably I could set it up to send keylog data to a remote address too, I think... (Note, I'm not root)

(Of course I should protect firefox with ad-blockers, and educate the users about the dangers of running unverified code, but anyway =)

My point being, one of the major features I tell other people about is that you don't run the same risks to get infected when surfing, and that ubuntu should be safer for things like online banking. However, when wine gets sufficiently advanced, and the users remain as careless as they were when running windows xp, this might not be entirely true?

---

### Post by bodhi.zazen on 2007-08-28
I understand what you are saying, but, you example is no different then saying I downloaded a linux key logger, installed it, and it worked perfectly ...

Where is the problem? With wine or "social engineering" (ie installing untrusted code) ?

So, how is, 

> Don't run untrusted scripts/programs as root on Ubuntu

different from

> Don't run untrusted scripts/programs with wine as root on Ubuntu ?

And yes, security absolutely involves user education. Security on any system is an active process and I would call your example "social engineering" in that you chose to install the said key logger, it was not installed automatically or unknowingly by some program using wine.

---

### Post by Civean on 2007-08-28
Well, the main difference being that there are so much more windows nasties out there of course =)

But I get your point. However, I think the advice should be plainly 

"Don't run untrusted scripts/programs on Ubuntu" 

since you are as vulnerable to some of these things when running as user. Then of course the problem is whether something should exist in Gnome to make the user aware that he/she is not opening a nice animated gif-card but instead an unknown .exe, and that this could be dangerous.

And you are right that this is more a problem of social engineering. But it is also a problem of less then ideal integration between wine and gnome, I would say. Maybe if there were a gnome-launcher for exe files in the form of a warning message or something like that? Instead of the more hard to understand normal "open file with - wine" dialog.

---

### Post by asdfoo on 2007-11-28
> **GoneSouth said:**
> Recursively delete all .exe files in a directoy:

```
find <dir> -name '*.exe' -exec rm {} \;
```

Recursively move all .exe files to some other directory

```
find <dir> -name '*.exe' -exec mv {} <dest dir> \;
```


This is a bad idea, you'll either delete or move applications compiled with Mono.

Tomboy Notes is one I can think of, off the top of my head.

---

### Post by hugmenot on 2007-11-28
> **asdfoo said:**
> This is a bad idea, you'll either delete or move applications compiled with Mono.

Tomboy Notes is one I can think of, off the top of my head.

You could dpkg-query -S for *.exe, then feed this list as an exclude list to rsync, which recursively pumps all other .exe files into /dev/null with --delete. Sounds complicated but was my first off-the-cuff idea.

---

### Post by avik on 2007-11-28
Hey, is this experiment by any chance inspired by [this fine comic]("http://xkcd.com/350/")?  Seems eerily similar.

---

### Post by Jengu on 2007-11-29
> **ardchoille42 said:**
> This one of the reasons I feel that using wine is a bad idea.

This doesn't mean that using wine is a bad idea. Precautions could be taken to jail the wine installation. For example, the wine package could be changed so that it created a new user, and all wine apps were run by that user, so that your windows apps wouldn't have permission to mess with your files specifically. People have talked about this on the wine mailing list before.

ANY Linux program could be trashing your home folder the same way a virus run under wine does, it's just that people tend to develop more data trashing programs for windows ;)

Note that running the virus under wine is still more secure than windows -- it can only trash the things you as a user have permission to trash, so the most it can muck up is your home folder.

---

### Post by Glenn1337 on 2007-11-30
interesting topic... i'd like to see what the do to windows itself

---

### Post by yaknowwat on 2007-12-16
Anyway you look at it running virus's under wine isn't very dangerous.
If a main dll somehow manages to be destroyed you can reinstall wine. without any major problem.

even if a keylogger can be run on wine after a restart its basically dead as it can't place itself to run on start so, the most damage a virus can do is its first run other than that it'd be dead.

virus's targets would normaly be in the main c: drive though.

z: drive if your worried that much since its the default you can alter it.
it'd be suggested running certain things in seperate false drives for wine. important things in their own drive with a funny starting name after the fake dosdevices shortcut I.E. ( J:\1a2b3c\ ) like what virus would target that.

---

### Post by MetalheadGautham on 2008-02-05
woweeee windows viruses in wine !
I guess this means an infected game disc can cause havoc in wine...

---

### Post by Christmas on 2008-02-05
The only thing that happened to me when I ran some obscure EXEs was that they created a lot of files with names like 'BF1942CRACK.exe' in some random directory in my home directory. Whatever virus you get, it can mess you .wine directory so if you want to get rid of them just delete it and start over with winecfg and installing whatever apps you need.

---

### Post by bodhi.zazen on 2008-02-05
> **MetalheadGautham said:**
> woweeee windows viruses in wine !
I guess this means an infected game disc can cause havoc in wine...

Well, as I have pointed out many times, that is simply not true. Even though you may be running wine, you are still running Linux. Security is actively built into wine and viruses either do not run, or if they have "potential" the code has been patched.

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

Please note, in order to run viruses one has to first configure wine to allow them to try to run. Even with these configurations, they run poorly, if at all (most will not do anything at all).

So yes, it is possible to configure your system to run viruses, but you the users would need to manually configure wine to allow this.

And tell me, why would your game disk have a virus? Please tell me your are not pirating software.

---

### Post by Bungo Pony on 2008-02-05
> **bodhi.zazen said:**
> 
And tell me, why would your game disk have a virus? Please tell me your are not pirating software.

Possibly the same reason these ones had a virus:

[http://www.f-secure.com/v-descs/cih.shtml](http://www.f-secure.com/v-descs/cih.shtml)

and let's not forget about the mess Sony made.

---

### Post by borris.morris on 2008-02-05
Yeah, curse sony!

---

### Post by phrostbyte on 2008-02-05
If you only let Wine to access the fake C: drive the damage a virus can do, even a really bad one, ends at messing up your Wine installation.

apt-get --purge remove wine
apt-get install wine

Note that Wine has much more access by default. This is unfortunately needed for inter operating with Linux files.

---

### Post by jakupl on 2008-04-08
> **cearum said:**
> I wonder what would happen if someone ran a virus using wine as root, with / mounted as a drive in wine. I have a free partition.... I'm tempted to try. Of course not mounting any other drives so it doesn't spread outside too far.  :D

stop giving me ideas :) I'm actually thinking of reinstalling ubuntu... I kinda messed it up allready.
???????
Let me think for a while ;):guitar:

---

### Post by swoll1980 on 2008-04-08
the universe as we know it would be annihilated

---

### Post by shane2peru on 2008-04-08
> **jakupl said:**
> stop giving me ideas :) I'm actually thinking of reinstalling ubuntu... I kinda messed it up allready.
???????
Let me think for a while ;):guitar:

All it would do, is put a bunch of viruses all over your computer, however they are windows executables, therefore if you don't run them with wine, they will just set there, however if executed, more than likely they would only reproduce themselves.  Viruses tend to spread first, and infect (do their damage in the background)  With wine this is a little more difficult because you are not running a full blow windows system.  It could in theory erase your hdd if you have the right virus, but I don't know what virus does what.  It would be to your advantage to look up the virus on symantec's web site or something to know what it would do.  You don't want to run one that deletes or destroys things. :)  Just my 2 cents worth. :)

Shane

---

### Post by jakupl on 2008-04-08
[quote="swoll1980"]the universe as we know it would be annihilated[/quote]
:razz:
[quote="shane2peru"]You don't want to run one that deletes or destroys things.[/quote]

why? :guitar: If i'm gonna reinstall the entire system anyways :)... it would almost be an advantage:lolflag:

---

### Post by bodhi.zazen on 2008-04-08
> **shane2peru said:**
> All it would do, is put a bunch of viruses all over your computer, however they are windows executables, therefore if you don't run them with wine, they will just set there, however if executed, more than likely they would only reproduce themselves.  Viruses tend to spread first, and infect (do their damage in the background)  With wine this is a little more difficult because you are not running a full blow windows system.  It could in theory erase your hdd if you have the right virus, but I don't know what virus does what.  It would be to your advantage to look up the virus on symantec's web site or something to know what it would do.  You don't want to run one that deletes or destroys things. :)  Just my 2 cents worth. :)

Shane

That is just not true. first you typically need to configure wine to allow window viruses to run at all. second, if a virus runs at all, it does not have access to files outside of ~/.wine. third , if a virus is found to run on wine, wine is then patched.

See here : 

[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Please do not spread FUD re: wine.

---

### Post by shane2peru on 2008-04-08
> **bodhi.zazen said:**
> That is just not true. first you typically need to configure wine to allow window viruses to run at all. second, if a virus runs at all, it does not have access to files outside of ~/.wine. third , if a virus is found to run on wine, wine is then patched.

See here : 

[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Please do not spread FUD re: wine.

This is from experience, not just theory.  Read this post: [http://ubuntuforums.org/showpost.php?p=2196004&postcount=18](http://ubuntuforums.org/showpost.php?p=2196004&postcount=18)  from page 1.  I did run a virus by accident using wine, and it infected almost my entire /home/username directory.  They do run.  I certainly don't mean to slight the people working on the wine project, because I honestly believe they are doing a great job!  Just that viruses are made to run on anything.  Interesting to think, viruses can run on about any version of windows, and yet Windows can't get their programs to run on all versions.  :lol:  I know, a virus is a very simplistic program and the others are not.  But still funny to me.

Shane

---

### Post by bodhi.zazen on 2008-04-08
> **shane2peru said:**
> This is from experience, not just theory.  Read this post: [http://ubuntuforums.org/showpost.php?p=2196004&postcount=18](http://ubuntuforums.org/showpost.php?p=2196004&postcount=18)  from page 1.  I did run a virus by accident using wine, and it infected almost my entire /home/username directory.  They do run.  I certainly don't mean to slight the people working on the wine project, because I honestly believe they are doing a great job!  Just that viruses are made to run on anything.  Interesting to think, viruses can run on about any version of windows, and yet Windows can't get their programs to run on all versions.  :lol:  I know, a virus is a very simplistic program and the others are not.  But still funny to me.

Shane

your /home/user or just /home/user/.wine ?

/home/user != / or system files

The only way to "infect" system files would be to run wine as root, which is not advised or supported.

Can you provide more details about your experience ? How did you configure wine ? What version of wine was it? Has it been reported and patched ? Are you saying it "just happened" when you plugged in the usb device ? How was it you ran a virus / worm ?

You should be posting a bug report with Launchpad (Ubuntu) and/or WineHQ not spreading FUD or making sweeping generalizations about wine.

---

### Post by shane2peru on 2008-04-08
> **bodhi.zazen said:**
> your /home/user or just /home/user/.wine ?

/home/user != / or system files

Can you provide more details about your experience ? How did you configure wine ? What version of wine was it? Has it been reported and patched ? Are you saying it "just happened" when you plugged in the usb device ? How was it you ran a virus / worm ?

You should be posting a bug report with Launchpad (Ubuntu) and/or WineHQ not spreading FUD or making sweeping generalizations about wine.

Well, yes much of this was my fault for opening wine up to my entire /home/username directory, not just the .wine folder.  I had a little windows program that would take a text file and transform it to a Bible file for a Bible program, and it was on my USB stick.  I took that to a company here in Peru (almost all windows computers here in Peru have a virus of some form or another about 95% of them are using pirated software), and had them print some things for me, apparently the virus on their computer infected the .exe file on my usb stick.  I came home, unaware of the problem, and ran the .exe file a week later.  It didn't run correctly and after about 5 minutes I realized that wine was still running in the background, and I killed the process.  Out of ignorance, I ran the file again, a few times I guess (don't remember now) and it littered my computer with 1,000's  of bogus .exe files.  I had recently moved over from Windows so I had a good collection of .exe files that I still have saved to my computer.  So then I had to decipher what was an infected .exe and what was a good .exe.  After a while with the help of clamAv I got it all cleaned up.  I have no idea what version of wine it was probably back in the 0.93x days or something.  Never bothered to report it, because 1.  Didn't know I should.  2.  Figured it was my own fault for ignorance. :)  It didn't really touch my computer, just propagated itself 1000 times on my hdd.  It didn't get into my root directory (/)  just my /home/username/ .  I linked that to wine as my MyDocuments folder so that I could easily access the files I needed to get at.  And, I don't mean to spread stuff, just telling my experience.  I mean jakupl asked about running a virus.  After reading the link you posted I guess not all will run with wine, I just happened to get the winning one! :lolflag:  I just know that that virus (whatever it was) did run when I ran it.  It didn't run automatically.  

Shane

---

### Post by bodhi.zazen on 2008-04-08
Thank you for the clarification, I think that information is much more helpful then your previous post.

wine is no more or less secure then any application, you need to guard against misconfiguration. Misconfigured servers or applications are obviously a security risk. Take caution that you are not circumventing security for convenience ;) It is sooo easy to make that mistake.

In general, I advise you keep wine contained in ~/.wine and do not give it access to ~ or system files.

---

### Post by shane2peru on 2008-04-08
> **bodhi.zazen said:**
> Thank you for the clarification, I think that information is much more helpful then your previous post.

wine is no more or less secure then any application, you need to guard against misconfiguration. Misconfigured servers or applications are obviously a security risk. Take caution that you are not circumventing security for convenience ;) It is sooo easy to make that mistake.

In general, I advise you keep wine contained in ~/.wine and do not give it access to ~ or system files.

I'm either a risk taker or a slow learner or have a lot of trust in the team that develops wine, because I still give it access to about everything except the filesystem.   :lolflag:   However I'm a little more cautious in that I have a regular once a  week scan of my system with good ole clamav.  I'm far lessed concerned now that all the computers in my house are running Linux.  Before I had a desktop running Windows XP with firewall and antivirus, that is how I found the virus on my usb stick.  Since that time, I have been running wine without a problem and no viruses.  It was a rare thing, and I ran it.  I have had viruses pass through my computer but since I don't run them with wine, it is not a problem.  Sorry for any unclarity in my previous posts.

Shane

---

### Post by sanderella on 2008-04-08
You guys are really scary, you are frightening little old ladies like me. I've got Wine, but never used it. Should I remove it?:confused:

---

### Post by wakeupinflames on 2008-04-08
Ha ha, I was wondering about this the other day. It's really good to know that it wouldn't mess up Ubuntu or your computer, but only your Wine conf.

---

### Post by shane2peru on 2008-04-08
> **sanderella said:**
> You guys are really scary, you are frightening little old ladies like me. I've got Wine, but never used it. Should I remove it?:confused:

Nothing to fear!  Really if you don't use it, there isn't a need to have it on there.  Course if you don't use it, there is not a need to worry about it either.  It doesn't just pickup and run viruses all by itself, and I have modified my configuration of my wine installation.  For normal average people, there is really not a problem.  Now if you go looking to run viruses on purpose there is a minimal threat at least in my experiences.

Shane

---

### Post by jakupl on 2008-04-09
ok. I tried 1000 ways to get a virus, and I found several but _none_ would work in wine.

Eventually i did a malicious code.. just for the fun of it :)
pretty impressive to see how 6 digits can turn the entire OS into monkey

---

### Post by zazuge on 2008-05-09
i think it's better to create a new user called wine
and then run wine with this unpreviliged account
(like some daemons process)
like this
sudo -u wine wine someprog.exe
I know it will not work with some apps but if your paranoid it's better than nothing.

personaly I don't guive any access to anyone to my home directory
chmod o-rwx ~/

---

### Post by john_spiral on 2008-05-28
> **zazuge said:**
> i think it's better to create a new user called wine
and then run wine with this unpreviliged account
(like some daemons process)
like this
sudo -u wine wine someprog.exe
I know it will not work with some apps but if your paranoid it's better than nothing.

personaly I don't guive any access to anyone to my home directory
chmod o-rwx ~/

Is this the default setup for running Wine under 8.04?

seems like it should be.

---

### Post by shane2peru on 2008-05-28
> **john_spiral said:**
> Is this the default setup for running Wine under 8.04?

seems like it should be.

This is not the default setup in 8.04.  I don't  think it will ever be the default setup, it is really not necessary.  Your chances of actually getting a virus, and you running it with wine are very slim.  I mean unless you just haphazardly run every .exe that you come across this is not going to be an issue that will affect you.  Even if it does, it will not damage your system.  So don't worry about it, unless you are looking for and trying to run viruses.  Only run programs that you know are trustworthy. 

Shane

---

### Post by bodhi.zazen on 2008-05-28
I agree with shane2peru.

The biggest problem with a default wine installation is that there is a link to /

Go to ~/.wine/dosdevices and run :

```
ls -l
```

Just unlink it :

```
unlink z:
```

I also unlink the one to ~ (home)

IMO, I see no need for links from ~/.wine to any location outside of ~./wine, with the exception of a link to a CD/DVD (for installation purposes).

---

### Post by dizee on 2008-05-28
You can also do it graphically with winecfg, on the drives tab.

---

### Post by mikhsoj on 2008-06-05
so what? The main question still hasnt been answered i think,

if you run a virus in WINE under Linux, does it affect your Linux install?
if you uninstall WINE with a virus, does it remove all instances of that virus?
Can a virus move itself out of the imaginary C drive (AKA Z)?
Can a virus run without SUDO permissions?

---

### Post by sdowney717 on 2008-06-05
shane2peru

do you know Don and Christie Lata in Aeroquipa?

[http://www.wegoperu.org/](http://www.wegoperu.org/)

---

### Post by Masoris on 2008-07-02
I found a virus which get platinum rate on Wine AppDB.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11780](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11780)

---

### Post by bodhi.zazen on 2008-07-02
IMO one of the most important security feature of wine is that it is contained within ~/.wine

I have noticed, however, that recent versions of wine include links outside of .wine, specifically there is a link to $HOME and /

I advise you :

```
cd ~/.wine/dosdevices
ls -lA
```

Now unlink those links to / and /home/username

```
unlink d:
```

---

### Post by Trail on 2008-07-02
> **bodhi.zazen said:**
> The biggest problem with a default wine installation is that there is a link to /

This is quite useful though, and it would cause confusion for a non-beginner, so I believe this a sane default setting.

Imagine you have a game setup on your external hdd; you mound the drive, cd to the game directory, try to run it with wine, and you get... could not find link to $game_directory, using ~/.wine/windows, could not find module $game_executable. Bottom line, won't work. You need to change wine's settings, link the folder, copy it or whatever, but googling should be usually included for a beginner. Not good.

Or, for a more common case, you download an .exe on your Desktop, wine has no 'access' to that folder, you get the previous error message.

---

### Post by notyetroot on 2008-08-12
Wine isn't Windows. It's an implementation of the Windows API for Unix based systems*^. It isn't the Windows API that has security problems, it's Windows. In Wine, a program can only do what it could normally do in Unix. 

The only program that might work would be a keylogger, but you would probably have to be trying to get that to work.

The paranoid should remove the Z:\ (root) drive in winecfg, or remap it to some other directory.

* Hmmm, would it be possible to mix Wine and Unix system calls? What about Windows and Linux calls in coLinux? I'm too lazy to experiment. :)

^ Not really an emulator or even a compatibility layer, since AFAIK Wine doesn't translate to glibc calls, except for SEH/VEH (exceptions) and signal handling. I don't think any runs in the kernel though, so there's an additional layer of security.

---

### Post by Mr.Auer on 2008-08-13
The paranoid?
Ok, I just unlinked all other dirs but ~/.wine :)

---

### Post by original_jamingrit on 2008-08-13
> **notyetroot said:**
> Wine isn't Windows. It's an implementation of the Windows API for Unix based systems*^. It isn't the Windows API that has security problems, it's Windows. In Wine, a program can only do what it could normally do in Unix. 

The only program that might work would be a keylogger, but you would probably have to be trying to get that to work.

The paranoid should remove the Z:\ (root) drive in winecfg, or remap it to some other directory.

* Hmmm, would it be possible to mix Wine and Unix system calls? What about Windows and Linux calls in coLinux? I'm too lazy to experiment. :)

^ Not really an emulator or even a compatibility layer, since AFAIK Wine doesn't translate to glibc calls, except for SEH/VEH (exceptions) and signal handling. I don't think any runs in the kernel though, so there's an additional layer of security.

Viruses can be run under wine.  If you have read and write permissions to the executable files in .wine, then they can be infected as well.  It would be very unusual for a virus to be able to infect linux binaries, (or at least infect them in a meaningful way), especially since your user account normally shouldn't have write permission to binaries found in your $PATH.  Although a wine virus is still able to create junk files in directories you own (that are linked or listed in winecfg)

---

### Post by gina88 on 2008-08-24
> **Civean said:**
> Hello,
I would like to revive this thread with a slightly different question. Today I found one of these spamvertisments that tries to present themselves as windows dialog warning you about some security error or whatnot, and asking if you would like to "correct the problem" (ie. install some trojan mal/spy/adware). Amused by the situation (not often i see XP error dialogs in ubuntu) I clicked "yes", and some highly suspect .exe file was downloaded to my home folder. Of course I promptly executed it in wine, but sadly it didn't work. (Yes, I like to break this computer in imaginative ways) 


heeeheee... this happened to my friend, he forgot he was on ubuntu (his ubuntu theme is Lunacy, the XPish theme) and he got scared, then he remembered he was on ubuntu, made him laugh out loud :lolflag:

---

### Post by thenubsauce on 2008-12-25
So I removed my drives except my fake c drive. I should be ok right?

---

### Post by eragon100 on 2008-12-25
> **gina88 said:**
> heeeheee... this happened to my friend, he forgot he was on ubuntu (his ubuntu theme is Lunacy, the XPish theme) and he got scared, then he remembered he was on ubuntu, made him laugh out loud :lolflag:

I got one of those sites, it detected I was using linux, and said my linux system was compromised, there were malicous shell scripts in my home directory. That was a very nasty one, because it *could* have been true. (not that I believed it, but some people might have)

I forgot the link, sorry :(

---

### Post by bodhi.zazen on 2008-12-26
> **thenubsauce said:**
> So I removed my drives except my fake c drive. I should be ok right?

That is what I do personally when I run wine. If needed I can make a link elsewhere (ie to the CDROM if installing). I see no reason to directly link to my home directory or /

---

### Post by elitefox on 2010-11-17
> **ardchoille42 said:**
> Because **wine runs Windows programs**.. including viruses, trojans, worms, etc. I've been saying this for a while but no one listens, now we have proof. And, as you saw from an earlier post, those viruses, trojans, worms can wreak havoc in any folder in $HOME as well as system folders. If the infected user runs a virus within the sudo timeout of running a command with sudo, the virus can gain sudo privs. Think about it, if the user runs "sudo command", there is a certain amount of time that the sudo password is cached. If the user runs a virus that calls sudo within that sudo cache timeframe, then the virus can run "sudo rm -rf /" and that command will succeed because the virus is running as the sudo user with sudo privs:





This is why I say wine/cedega/cxoffice/other are bad things and should not be used at all. It wouldn't be hard (probably already been done) to write a keylogger into a Windows file and capture every keystroke you make and send all your personal info to a server where it is sold to the highest bidder. Some folks think that running Windows apps in wine offers them some layer of protection against bad Windows apps, but this is simply a myth.

I don't know about others, but the files in my $HOME are more important to me than the rest of the system. I won't ever use Windows files on any of my systems.. and now you see why.


I don't think a windows virus will contain *snip* since it is made for windows

but that could be if it is a cross platform virus :popcorn::guitar::lolflag:

---

### Post by s.fox on 2010-11-17
Necromancy. Thread Closed.

[IMG]http://serial-coder.co.uk/blog/wp-content/uploads/2010/11/threadNecromancy.jpg[/IMG]

---

