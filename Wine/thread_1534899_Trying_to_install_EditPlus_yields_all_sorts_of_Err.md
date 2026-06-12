---
title: "Trying to install EditPlus yields all sorts of Errors, PLS HLP!"
date: 2010-07-20
forum: Wine
---

### Post by CuXe on 2010-07-20
Hi guys,

I am trying to install editplus with wine but for some reason I am getting all sorts of errors.  Here is what I did:

I installed wine 1.2 using Synaptic and things went fine.  I haven't changed any config within wine.

When I located the exe file I want to install I entered this in the terminal:

> wine ./epp301_en.exe

When I press enter this is the terminal's output:


```
err:process:start_wineboot failed to start wineboot, err 11
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:shell:SHAutoComplete stub
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:create_server class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x5
fixme:exec:SHELL_execute flags ignored: 0x00000180
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
```

Prior to trying to install editplus I wanted to get winamp going within wine and I followed the steps outlined here:

[http://www.wine-reviews.net/applications/winamp-55-on-linux-with-wine.html](http://www.wine-reviews.net/applications/winamp-55-on-linux-with-wine.html)

But when I tried launching the exe with wine:

> wine winamp55_full_emusic-7plus_en-us.exe

I got a similar output from the terminal and it always seems to start with:

```
err:process:start_wineboot failed to start wineboot, err 11
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
```

I read another tut to install winamp and it mentioned something about winetricks but I can't seem to find that tut to quote it here.

After all that I removed wine completely with synaptic and installed it again to try to get editplus running but my guess is that my wine installation is completely screwed up and I don't have the slightest idea as to how to go about fixing it...

Any ideas??

---

### Post by ronnielsen1 on 2010-07-20
I researched epp301_en.exeand came up with this page 

[http://editplus.info/wiki/Running_on_Linux](http://editplus.info/wiki/Running_on_Linux)

so I tried it:

[COLOR=Blue]sudo apt-get install wine[/COLOR] (which I didn't do since I already have it)
[COLOR=Blue]cd ~[/COLOR]                      (changes to your home directory)


[COLOR=Blue]wget [ftp://ftp.editplus.com/epp301_en.exe](ftp://ftp.editplus.com/epp301_en.exe)[/COLOR] (dl's the files)

[COLOR=Blue]wine ./epp301_en.exe[/COLOR]    (not sure why I had to put the./ in plus it didn't work)


So, I browsed home and I found epp301_en.exe so I went back to terminal and typed 

[COLOR=Blue]wine epp301_en.exe[/COLOR] and it installed and started 


It appears to install in .wine/drive_c/Program\ Files/EditPlus\ 3/ or Start Button > 
Wine > Programs >   EditPlus 3

---

### Post by CuXe on 2010-07-20
Thanks for the quick reply :)

I just tried once again with:

[COLOR="Red"]wine epp301_en.exe[/COLOR] and this is what the terminal shows


```
err:process:start_wineboot failed to start wineboot, err 11
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:shell:SHAutoComplete stub
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:create_server class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x5
```

**And then the program installation opens BUT** here is the thing, if I follow through an finish the installation I don't see the wine section within the Applications menu and EditPlus is nowhere to be found.

---

### Post by ronnielsen1 on 2010-07-20
You might consider native linux apps instead of the windows software. 

[http://editplus.info/wiki/Alternative_Editors](http://editplus.info/wiki/Alternative_Editors)
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2723](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2723)

Winamp has some config files to change as the post above says

You will probably have to install winetricks
sudo apt-get install winetricks
always google windowssoftware winehq first. It will tell you if you need to do anything special. As far as winamp, I think I'll stick with rhythmbox myself. There's tons of other ones if you don't like it

>                   HOWTO WINAMP 5.5 -  5.56   	 	   [SIZE=2]Before installing  winamp 5.5 - 5.56 you can try a 'sh winetricks comctl32 wininet ie6 allfonts divx' in the terminal for a better winamp experience in WINE[/SIZE]
  (see below for instructions)   [SIZE=2]Comctl32, ie6  & wininet for the media library to show up and for the 'send to  menu' to work, allfonts for a good display of the bento skin and divx to  watch online shoutcast movie stations and local movies. [/SIZE]
        

   [SIZE=2]There are  some annoying window issues with the modern and bento skin. Like submenus disappearing behind the main window, or even a disappearing window with a repositioning.  [/SIZE]
   [SIZE=2]To prevent  this you can enable the virtual desktop in winecfg (you can set “1280x945” for a full-screen experience on a 17inch monitor) otherwise use “pkill winamp*” to get out of trouble.[/SIZE]
   [SIZE=2]If you  use the modern skin you might need to enlarge the main window for the media library to show up, if you want to use the Bento skin, make  sure you only enable it 'after' you filled the library in classic or  modern skin style[/SIZE]
        

   [SIZE=2]If your  new to WINE this might sound a bit daunting, but really an installation  is mostly a matter of copy/paste in the terminal, so go ahead.[/SIZE]
        

        

   [SIZE=2]cd ~/  && wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) && chmod +x winetricks[/SIZE]
   [SIZE=2]env WINEPREFIX=~/.wine-winamp  sh winetricks comctl32 wininet ie6 allfonts divx[/SIZE]
   [SIZE=2]env WINEPREFIX=~/.wine-winamp  wine winecfg [/SIZE]
   [SIZE=2](optional, enable  a virtual desktop, go to graphics, check emulate) [/SIZE]
   [SIZE=2]env WINEPREFIX=~/.wine-winamp  wine '/path/to/winamp556_full_emusic-7plus_en-us.exe'[/SIZE]
   [SIZE=2]env WINEPREFIX=~/.wine-winamp  wine 'C:\Program Files\winamp\winamp.exe'[/SIZE]


---

### Post by CuXe on 2010-07-20
Yeap, I ended up using Audacious instead of winamp.  I guess I'll go with one of the alternative editors mentioned in that editplus URL.

The only thing that bugs me are those weird errors in wine.

At the moment I am learning as much as possible to later on migrate from windows however it seems I'll have to run either wine or virtualbox for certain apps I need to use.

Thanks so much for all your help m8, I really appreciate it :)

---

### Post by ronnielsen1 on 2010-07-20
You can also right click on file and open with wine (assuming there are no issues with wine running the software) or associate exe to automatically open with wine on a click

---

