---
title: "E-Sword 10.3 and Ubuntu 14.04"
date: 2014-08-11
forum: Ubuntu Christian Edition
---

### Post by ubume2 on 2014-08-11
I have used E-Sword for several years. At about 12.04 I had to use winetricks to install several dll files to get the search function to work, and the greek modules to work (SBLGNT, WH+TVM,IGrNT+). 

I recently installed Kubuntu 14.04 with wine 1.6. I used winecfg to load oleaut32.dll. I did not install any of the dll files that were recommended earlier. I installed E-Sword 10.3 by right clicking and using wine windows program loader.  

I keep a backup of all my bible and commentary modules. I put them in ~/.wine/drive_c/Program Files (x86)/e-Sword.

E-Sword works great including the search function and those Greek modules.

Those dll files may be required for other functions in E-Sword that I do not use, but installing E-Sword has never been easier.
No doubt that this will work for all flavors of 14.04.

Your experience may vary.

---

### Post by kc1di on 2014-08-11
i've use e-swords for years on linux and find it to be very good. 
you may also want to give xiphos at try it's in the repository. 
 ;)

---

### Post by Rogermana on 2014-09-01
I am new to using wine though I know e-Sword well. What are the basic steps to the e-Sword install, which dll files are essential and can winetricks fetch them all, or should I get them from MS?

thanks, Roger Levy

---

### Post by ubume2 on 2014-09-02
Hi,

If you have wine 1.6 installed, from the terminal do 
$ winecfg 
go to libraries and add oleaut32.dll

right click on the e-Sword.exe file and choose install from wine windows program loader. 

It should install into /home/user/.wine/drive_c/ProgramFiles (x86)/e-Sword  

If you have an older version of wine, or are using 12.04, or Ubuntu CE (which I think is based on 12.04)

start winetricks from the command line and 



Edit: install msls31 msxml3 vbrun 6 vcrun6 and wsh57.  A couple of them are downloaded from download.com and you would need to place them in /home/user/.cache/winetricks/ .

see
[http://ubuntuforums.org/showthread.php?p=11673552#post11673552](http://ubuntuforums.org/showthread.php?p=11673552#post11673552)

---

### Post by peter161 on 2014-11-26
the suggestion that fireandsalt mentions over  at [http://e-sword-users...sers/node/223  ]("http://e-sword-users.org/users/node/223")

 Sun, 08/02/2009 - 16:29
 [#6]("http://e-sword-users.org/users/node/223#comment-1374") 
  
 mostly works for me. The only thing that i did differently is i did  not follow step 14. "Click on the Libraries Tab, and in the “New  override for Library” drop down box, fine Riched20, click add, apply,  and ok. Close out of Configure Wine." this did not work for me. I also noticed that I had to use Esword version 10.00 and not 10.2, 3 0r 4.

  
 I have NET Bible Premium from bible.org but the verses do not show up. (It works fine in Windows.) however,  the NET commentary works fine. Does anyone have any suggestions?

---

### Post by djh-compnet on 2014-12-10
E-sword fully works under Ubuntu 14.04 including search functions,  graphics viewer and the module downloader. There may still be quirks  here and there and one known issue is Indian languages are not rendered  properly because E-Sword does not have any configuration options for  Sanskrit languages and cannot rely on the capabilities you can get by on  a Windows box. The Bible text still can be pasted into an external word  processor though. The Code2000 font supposedly solves this kind of  problem on a different Bible programme running under Wine but it sadly  did not work with E-Sword.

You have to follow these instructions  in the right order to get it working properly. If you don't you can end up with  with E-sword not displaying any text or the module downloader not adding  modules to the download queue and neither allowing you to download any.

1.  Requirements: Ubuntu (and other flavours) 14.04, Linux Mint 17 (make  sure all the dependencies are installed as Mint sometimes fails to  install them), Wine 1.7.31 via PPA (at the time of writing 1.7.32 or  later), Windows libraries installed via Winetricks, E-Sword 10.4.0 (at  the time of writing), a terminal to run several commands

2. The first step is to install the latest version of Wine if you do not have it already installed:

[B]user@pc:~$ sudo add-apt-repository -y ppa:ubuntu-wine/ppa
user@pc:~$ sudo apt-get update && sudo apt-get install wine1.7[/B]

3.  Next you have to install some libraries with Winetricks which also  registers them. Pasting them into  /home/user/.wine/drive_c/windows/system32 might not work properly unless  you register some of the DLLs.
[B]
user@pc:~$ winetricks mfc42 [/B]<-- requires you to click on 'Yes' on a dialogue box that appears after downloading to agree with installing it[B]
user@pc:~$ winetricks msls31
user@pc:~$ winetricks msxml3 [/B]<--  automatically opens a URL to download msxml3.msi and a file manager  window for you to paste the installer in, execute the command again once  the file has been moved into that folder, at the installer wizard click  Next and accept the License Agreement and click Next again, you might  also have to enter your name and organization if you have not already  done so in the Wine configuration applet, click Next , Install and  Finish[B]
user@pc:~$ winetricks vb6run [/B]<-- requires you to click on 'Yes' on a dialogue box that appears after downloading to agree with installing it[B]user@pc:~$ winetricks vcrun6
user@pc:~$ winetricks wsh57[/B] <-- registers some DLLs

4. Now you must download and install E-Sword.

The  following link has the latest version:  [http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html) and download as you would with any  other file and make sure you know where it is saved.

Locate the  downloaded E-Sword installer for Windows with your file manager.  Right-click on it and click on Open With Wine Windows Program Loader.  Your system might already be set up to open .exe files with Wine in that  case you can just double-click. The E-Sword InstallShield wizard will  open. Click next, accept the license agreement, click next, next again  at the release notes, choose your installation directory (default one is  fine) and click next and finally Install and Finish. You will be  redirected to an informational E-Sword confirmation web page that  includes a donate button.

Your E-Sword launcher will be on the  Desktop on most distros. Xubuntu allows launching E-Sword by searching  for it or by browsing in the XFCE menu.

---

### Post by peter161 on 2014-12-11
Your instructions [**[COLOR=#000000]djh-compnet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1260569") worked! But I have NET Bible Premium from bible.org but the verses do not show up.  (It works fine in Windows.) however,  the NET commentary works fine. any suggestions?

---

### Post by ubume2 on 2014-12-12
> **djh-compnet said:**
> E-sword fully works under Ubuntu 14.04 including search functions,  graphics viewer and the module downloader. There may still be quirks  here and there. . . .




Yes, It all (mostly) works.  With 14.04 and wine 1.6 I no longer have to add anything with libraries such as oleaut32.dll or install the dll's through winetricks.

One thing that does not work in module KJV+: hovering mouse pointer over Strong's number does not reveal the Greek word information. I have also tried this with wine 1.7, and this feature does not work.

---

### Post by leunam12 on 2015-05-16
I use e-sword on Ubuntu 14.04 on a daily basis and one trick that I have not seen documented is that uninstalling and re-installing e-sword unlocks certain features that didn't work on the first install. I don't know why this is so but it works.

---

### Post by Hodevah on 2015-07-29
what kind of features?

---

