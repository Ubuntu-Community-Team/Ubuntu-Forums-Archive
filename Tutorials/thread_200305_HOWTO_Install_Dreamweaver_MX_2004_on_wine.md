---
title: "HOWTO: Install Dreamweaver MX 2004 on wine"
date: 2006-06-20
forum: Tutorials
---

### Post by w1z4rd on 2006-06-20
I have just moved over from about 14 years of microsoft abuse, and there are simply some things I can not live without. One of them is Dreamweaver. A lot of okes out out there use it. Ive seen a lot of people out there in the forums requesting information, so I thought this might be the right place to bring it.

The content was not written by me, but by Clint Christopher from Canada who is involved with the wine application wiki.

[Latest ubuntu wine distributions at SourgeForge]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803")

[B]Here's a howto for wine versions 0.9.3, 0.9.5 and 0.9.6 (Wine 0.9.4 doesn't run Dreamweaver):
[/B]

start up with a clean install of wine:
*rm -rf ~/.wine*

It is possible to run Dreamweaver without mdac and internet explorer. Just run:

*wine "Install Dreamweaver MX.exe" *(I have a licensed version)

and ignore the "This program requires mdac 2.6" warning. It is recommended however to install the Mozilla Activex Control with flash player plugin. Please see Howto section of Internet Explorer 6.0 SP1 for more details on this.

To use internet explorer as the default browser for Dreamweaver preview mode, here's how:

[COLOR="Red"]Download[/COLOR] this file: [http://www.kievinfo.com/2/ie6_overrides.reg](http://www.kievinfo.com/2/ie6_overrides.reg)
Run* wine regedit ie6_overrides.reg*

[COLOR="Red"]Download[/COLOR] dcom98
Run *wine dcom98.exe*

Run *rm -f ~/.wine/drive_c/windows/system32/regsvr32.exe*
[COLOR="Red"]Download[/COLOR] and run *wine ie6setup.exe*

Install mdac_type.exe:
[I]
wine mdac_type.exe[/I]

Run the dreamweaver installer

Run winecfg and add msvcrt.dll to the libraries as native, builtin (to avoid dreamweaver crashing when clicking on the fireworks button to launch fireworks within dreamweaver)

0.9.3 and 0.9.5 sometimes experiences hangups on the splash screen. This is because Dreamweaver seems to scan all drives. It seems to have a "hangup" when it scans mounted windows partitions. To let dreamweaver go up fast, just remove drives (in winecfg) that inadvertently goes to those mounted windows partitions.

Update:
Wine 0.9.6 doesn't seem to run dreamweaver mx (hangs at the splash screen) without installing internet explorer first.   Please install internet explorer 6 as per instruction above.

Clint Canada
		
**How to Install Dreamweaver MX in wine 0.9.9**

By default, wine 0.9.9 doesn't run or install dreamweaver (dreamweaver requires ie to be installed to avoid the splash screen hangup issue). This is because of a bug (4708) which also breaks ie6 installs and other apps as well.

To get around this, please patch 0.9.9 with this file located here: [http://bugs.winehq.org/attachment.cgi?id=2000&action=view](http://bugs.winehq.org/attachment.cgi?id=2000&action=view)

Once patched and recompiled, ie6 and dreamweaver should run ok. Also, unreadable fonts are an issue with 0.9.9 (Dreamweaver simply looks ugly!) Please copy your fonts from /usr/share/fonts or wherever your fonts are, to ~/.wine/drive_c/windows/fonts and you should be ok - it should be working a bit better.

Clint Christopher Canada

Where I found this: [http://appdb.winehq.org/appview.php?versionId=1054](http://appdb.winehq.org/appview.php?versionId=1054)

Got this from [Franks Corner]("http://frankscorner.org/index.php?p=dreamweavermx"): 

> Tested Wine Version: 0.9.2

Type wine dreamweaver\ mx\ installer.exeM to install Dreamweaver.
Type wine dreamweaver.exe in the installation directory to run Dreamweaver MX.


I think this will be a good project to keep track of as more than a few people will leave MS, when they know they can take their GfX with them. Im a n00b so hopefully the other will help assist the Dreamweaver folk.

---

### Post by rejser on 2006-06-20
very nice howto.
just one question, where can I find mdac? The one on MS home requires validation, and I don't have an win-box anywhere.

---

### Post by w1z4rd on 2006-06-20
[QUOTE=rejser]very nice howto.
just one question, where can I find mdac? The one on MS home requires validation, and I don't have an win-box anywhere.[/QUOTE]

Have uploaded mdac28.exe to my website if anyone needs it: [DOWNLOAD FILE]("http://www.pickledbushman.com/core/mdac28.exe")

---

### Post by b0bby on 2006-06-22
goodie! i will try on Wine 0.9.9 and write and tell u in a few hours how it went =)

---

### Post by b0bby on 2006-06-23
it kinda crashes when running installer, saying that it cant fint iKernel.exe and cant complete its install

---

### Post by bucksgt on 2006-06-23
I can confirm that Dreamweaver MX works on Dapper. Here is what I did to get it to work:

in the file: /etc/apt/sources.list
add the lines:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

(you need to add the above repositories or rebuild the package from source with a patch from: [http://bugs.winehq.org/attachment.cgi?id=2000&action=view](http://bugs.winehq.org/attachment.cgi?id=2000&action=view)  )

at the terminal, run: apt-get update
now install wine with apt-get at the terminal or synaptic, etc.

copy the files: mfc42.dll  and  msvcp60.dll to ~/.wine/drive_c/windows/system

**important note: other sites with documentation on this problem will direct you to download the above dlls from dll-files.com. as of writing this, mfc42.dll from dll-files.com _does_not_ work. i had to grab the file from a windows xp box. however, there are other ways to get it. the filesize of mfc42.dll is: 1028096  if it's smaller, you have the wrong file.**

run: wine ~/.wine/drive_c/Program Files/Macromedia/Dreamweaver MX/Dreamweaver.exe

(i didn't have any problems installing dreamweaver as i installed it using a standalone .exe self-installing package. your results may vary.)

-qk.

---

### Post by rejser on 2006-06-28
bucksgt: didn't try it with mx 2004?

---

### Post by jeffreyvergara.NET on 2006-06-29
I managed to run DMX8 before but it's really that usable, it's slow and some options cannot be used...

---

### Post by wislon on 2006-07-10
> **rejser said:**
> very nice howto.
just one question, where can I find mdac? The one on MS home requires validation, and I don't have an win-box anywhere.

There's an easy way to get all the required bits and pieces in one go using winetools. Check out this forum topic:

[http://ubuntuforums.org/showthread.php?t=149585&highlight=CD+repository](http://ubuntuforums.org/showthread.php?t=149585&highlight=CD+repository)

This is actually a wine install HOWTO, but the winetools is an exceptionally useful little piece of it.

HTH :)

---

### Post by PingunZ on 2006-07-10
I cant follow that howto ... maybe I'm to noob I dont know but i don't understand where to begin ... and what to do ...

Grtz PingunZ

---

### Post by Athanasius on 2006-07-21
This guide does nothing for me.  I need something simpler - can someone add more "dummy" steps please?

---

### Post by panki on 2006-07-25
Is this for MX or for MX 2004?  Mine crashes...

---

### Post by euph0rix on 2007-03-06
I got it working in Dreamweaver MX using Wine 0.9.32.. but not sure the same steps could be applied on MX 2004.. Try at your own risk..

I have wrote the steps here [B][http://mynewbietips.blogspot.com/2007/03/install-dreamweaver-and-ie6-using-wine.html](http://mynewbietips.blogspot.com/2007/03/install-dreamweaver-and-ie6-using-wine.html)
[/B]
---

1. Install IEs4Linux from good people at [http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

When you install IEs4Linux, it will automatically install necessary libraries such as dcom98.exe, mdac_type.exe, ie6setup.exe, etc. ..and, fake windows folder under `~/.wine/drive_c/` will also created.. Just follow instructions from the site and everything should be fine..

2. run your dreamweaver setup.exe using wine

    $ wine setup.exe


Here, you should have a normal installation screen just like you run it through windows.. you will need to insert serial key and that's for sure.. :)

3. If everything's fine, after the installation, you will see the dreamweaver directory under

    ~/.wine/drive_c/Program\ Files/Macromedia/Dreamweaver\ MX/


Right now, do not run the application yet or it will stuck at the splash screen.. Many people have experienced this problem and so do i.. :D This is because, during start, dreamweaver will try to scan all the drives available..

4. You need to remove all drives that not mapping to your fake windows folder.. so run:

    $ sudo winecfg


This will open wine configuration window.. Click on Drives tab and remove other mapping except to `../drive_c` and OK to save the configuration..

5. Ok, now you are ready to run Dreamweaver.. just type command

    $ wine ~/.wine/drive_c/Program\ Files/Macromedia/Dreamweaver\ MX/Dreamweaver.exe




Notice that wine will virtually set our fake windows (`/home/userdir/.wine/drive_c/`) as the C: drive in windows.. so, `My Document` you can see in dreamweaver is actually our home folder in linux..

---

### Post by geovino on 2007-03-06
I see that the Wine in Synaptic is 0.9.3. Can you install Dreamweaver 8 with it?

---

### Post by scorpiox on 2007-07-28
Does anyone know how i could do it with DW8? I have legal licensed copies etc etc but i cant make them install ;(

---

### Post by coolmanlg on 2007-11-03
You can install dreamweaver 8 by by doing wine yourdreamweaver.exe. It worked well for me. Am using the latest version of wine..0.9.48 on ubuntu feisty.

---

### Post by 0m4r22 on 2007-11-11
Is it necessary to install the ie4Linux? I installed dreamweaver first, installation seemed fine but i did it before installing ie4linux... will i have problems? I did try starting dreamweaver but did not start.

---

### Post by myharshdesigner on 2007-11-15
Can we use Wine to install any software in linux ?

like photshop , other software line office 2007 etc ?


> **w1z4rd said:**
> I have just moved over from about 14 years of microsoft abuse, and there are simply some things I can not live without. One of them is Dreamweaver. A lot of okes out out there use it. Ive seen a lot of people out there in the forums requesting information, so I thought this might be the right place to bring it.

The content was not written by me, but by Clint Christopher from Canada who is involved with the wine application wiki.

[Latest ubuntu wine distributions at SourgeForge]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803")

[B]Here's a howto for wine versions 0.9.3, 0.9.5 and 0.9.6 (Wine 0.9.4 doesn't run Dreamweaver):
[/B]

start up with a clean install of wine:
*rm -rf ~/.wine*

It is possible to run Dreamweaver without mdac and internet explorer. Just run:

*wine "Install Dreamweaver MX.exe" *(I have a licensed version)

and ignore the "This program requires mdac 2.6" warning. It is recommended however to install the Mozilla Activex Control with flash player plugin. Please see Howto section of Internet Explorer 6.0 SP1 for more details on this.

To use internet explorer as the default browser for Dreamweaver preview mode, here's how:

[COLOR="Red"]Download[/COLOR] this file: [http://www.kievinfo.com/2/ie6_overrides.reg](http://www.kievinfo.com/2/ie6_overrides.reg)
Run* wine regedit ie6_overrides.reg*

[COLOR="Red"]Download[/COLOR] dcom98
Run *wine dcom98.exe*

Run *rm -f ~/.wine/drive_c/windows/system32/regsvr32.exe*
[COLOR="Red"]Download[/COLOR] and run *wine ie6setup.exe*

Install mdac_type.exe:
[I]
wine mdac_type.exe[/I]

Run the dreamweaver installer

Run winecfg and add msvcrt.dll to the libraries as native, builtin (to avoid dreamweaver crashing when clicking on the fireworks button to launch fireworks within dreamweaver)

0.9.3 and 0.9.5 sometimes experiences hangups on the splash screen. This is because Dreamweaver seems to scan all drives. It seems to have a "hangup" when it scans mounted windows partitions. To let dreamweaver go up fast, just remove drives (in winecfg) that inadvertently goes to those mounted windows partitions.

Update:
Wine 0.9.6 doesn't seem to run dreamweaver mx (hangs at the splash screen) without installing internet explorer first.   Please install internet explorer 6 as per instruction above.

Clint Canada
		
**How to Install Dreamweaver MX in wine 0.9.9**

By default, wine 0.9.9 doesn't run or install dreamweaver (dreamweaver requires ie to be installed to avoid the splash screen hangup issue). This is because of a bug (4708) which also breaks ie6 installs and other apps as well.

To get around this, please patch 0.9.9 with this file located here: [http://bugs.winehq.org/attachment.cgi?id=2000&action=view](http://bugs.winehq.org/attachment.cgi?id=2000&action=view)

Once patched and recompiled, ie6 and dreamweaver should run ok. Also, unreadable fonts are an issue with 0.9.9 (Dreamweaver simply looks ugly!) Please copy your fonts from /usr/share/fonts or wherever your fonts are, to ~/.wine/drive_c/windows/fonts and you should be ok - it should be working a bit better.

Clint Christopher Canada

Where I found this: [http://appdb.winehq.org/appview.php?versionId=1054](http://appdb.winehq.org/appview.php?versionId=1054)

Got this from [Franks Corner]("http://frankscorner.org/index.php?p=dreamweavermx"): 



I think this will be a good project to keep track of as more than a few people will leave MS, when they know they can take their GfX with them. Im a n00b so hopefully the other will help assist the Dreamweaver folk.

---

### Post by MetalPrincess on 2008-02-10
I'm using 0.9.4.6 of Wine, Dreamweaver MX 2004 8 & Ubuntu 7.10 and it installed perfectly and runs fine. If you guys want a guide I can post it here.

---

### Post by MetalPrincess on 2008-02-10
> **myharshdesigner said:**
> Can we use Wine to install any software in linux ?

like photshop , other software line office 2007 etc ?

Actually yes you can try many windows based programs on it and see if they work ok. As for Photoshop yes you can use it. I installed Adobe Photoshop CS2 with wine and it works perfectly.

---

### Post by mustava on 2008-03-13
Hi guys, just installed DW MX on WINE over ubuntu 7.10, and although it appears to run ok (very old PC pentium 2 350Mhz), I can't get the site manager to locate my server (local nwk) which is running IIS on xp (at the mo) trying my best to c/o to linux and ditch windies altogether.
Any help on this would be appreciated, I am also a newby.

Regards Mustava..

---

### Post by brian3 on 2008-03-13
Just read your thead ,on installing dreamweaver on wine, try VIRTUALBOX thats more stable and easy to install.

---

### Post by mustava on 2008-03-13
Hi Brian3,
Can you please explain what VIRTUALBOX is?
Is this a replacement for WINE or for DW

Thanks Mustava

---

### Post by panki on 2008-03-13
Ok, this can get tricky.

DW is a windows app, therefore it uses windows file sharing.  On Linux, such file sharing is not installed by default.  So, if you want to connect to a remote machine, and use it as a "local" filesystem, you need to install the smbfs package:

$ apt-get install smbfs

After that you need to mount the remote share drive (you have to share the folder you want to access from the windows machine).

to do this, open the /etc/fstab file ( pico /etc/fstab ) and add this at the end of the file:

\\the.name.of.my.windows.server\myWindowsShare  /media/myLinuxFolder  smbfs  workgroup=myWorkGroupName,password=MyPass,username=MyWindowsUser 0  0

then save the file (ctrl+o, <enter>, ctrl+x)

OK, now you can mount the remote share drive as a local Linux folder, with the command mount /media/myLinuxFolder

After that all you need to do is point DW to that folder, and everything you save there will be actually saved on your server.

---

### Post by panki on 2008-03-13
Virtualbox emulates a complete PC within Linux (or Windows).  The idea is to have a computer inside a computer.  

Not recommended for your case since your machine is an old PII.

---

### Post by panki on 2008-03-13
Oh, I forgot... you could use apache and ftp on your server... works very good with DW.

---

### Post by undrline on 2011-12-05
This seems quite an old thread.  But, the MDAC 2.6 is still an issue for a straight installation of DreamWeaver MX 2004 under Wine.  After installing Wine1.2 or Wine1.3 (still in beta), open WineTricks.  Select to add a new prefix.  Select to install components.  Select mdac 2.8.  After it's done, do a regular Dreamweaver setup, and you won't get the error.  As for working over a Samba share you'll have to look at a previous post (I don't do that).

As for previewing in a browser, if IE is not installed, it uses winebrowser.exe, which opens your system's default browser.
If you simply choose iexplore.exe from the fake Program Files path it will use the wine gecko browser.  If you've installed IE8 and choose iexplore.exe it starts to open IE8 then crashes (for me, anyhow).  If you've installed IE7, it'll open in IE7.

---

