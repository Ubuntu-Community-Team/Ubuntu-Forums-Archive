---
title: "I Miss FileZilla"
date: 2006-11-28
forum: The Cafe
---

### Post by BlueSun on 2006-11-28
I've been using gFTP to upload pages to my remote webserver.  I really hate it.  It just seems clunky and slow compared to what I'm used to from my MS days: FileZilla.  Maybe I'm ignorant.  What else is out there?  There has to be a better way.  Somebody educate me, please.

---

### Post by Lord Illidan on 2006-11-28
Try getting FileZilla for Linux here : [http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

---

### Post by Bizmac on 2006-11-28
I was a user of Filezilla, if you are using Kubuntu, might be not the case, you can use Konqueror, really easy to use for your ftp transfer with the two panes.

---

### Post by aysiu on 2006-11-28
You can also install Windows' FileZilla using [Wine](http://www.psychocats.net/ubuntu/wine).

The native Linux FileZilla Beta isn't too bad, though.

---

### Post by JeffS on 2006-11-28
My work is a mostly Windows shop, and I'm the web developer (among many other things).  I use FileZilla all the time, and I love it.  One would have thought that since it has the word "zilla" in it, it would have been affiliated with Mozilla, and be fully cross platform.  But that does not seem to be the case, other than the links posted (I'll have to give that a try).

---

### Post by Rhubarb on 2006-11-28
If you're having problems with the windows version of filezilla with wine, then try Portable Filezilla with wine:-
[http://portableapps.com/apps/internet/filezilla_portable](http://portableapps.com/apps/internet/filezilla_portable)

I've tested it out in Edgy with wine, it seems to work fine here for me.

Aside, here's some *zilla info:-
Filezilla is certainly not affiliated with Mozilla.
The only *zilla project I can find by Mozilla would be Bugzilla.
There's a few other *zilla's out there in the open source world too, like Gozilla.

---

### Post by motin on 2006-12-09
I too have missed FileZilla for a very long time. Since some months ago I've been using FileZilla over WINE though which has been really buggy and unstable but still better than everything else I have tested so far! (Kftpgrabber is a decent alternative though)

The upside to the story is that FileZilla version 3 (soon to be released) is multi-platform and has a native Linux port!

Installation-instructions for Dapper Drake are found here: [http://kaisman.free.fr/dotclear/index.php?ubuntu-dapper-drake-installer-filezilla](http://kaisman.free.fr/dotclear/index.php?ubuntu-dapper-drake-installer-filezilla)

Or you can download the .deb files (filezilla and filezilla-common) from: [http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ff%2Ffilezilla%2Ffilezilla_3.0.0~beta2-2_i386.deb&md5sum=7fc605e907f1bcb117068a8c12eae470&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ff%2Ffilezilla%2Ffilezilla_3.0.0~beta2-2_i386.deb&md5sum=7fc605e907f1bcb117068a8c12eae470&arch=i386&type=main)    and [http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Ff%2Ffilezilla%2Ffilezilla-common_3.0.0~beta2-2_all.deb&md5sum=58fa26fa2108bca888dfc01dab03a9e0&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Ff%2Ffilezilla%2Ffilezilla-common_3.0.0~beta2-2_all.deb&md5sum=58fa26fa2108bca888dfc01dab03a9e0&arch=all&type=main) respectively. 

I am trying out the first alternative as I am writing. I'll be back to report in case it didn't turn out well.

---

### Post by motin on 2006-12-09
Here are my experiences:

First method "works", but you have to change the repository that the french site's instructions recommend to it's mirror: deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper 3v1n0

AND you will only install version 2.9.4 from CVS dated 2006-06-28.

Sadly, the Beta-version of FileZilla 3 found on debian.org unstable requires a later version of libc6 - a package I'd bet is best to leave as it is and not try to manually force an update via other deb-files etc. 

I guess Edgy Eft has the updated package though... But the update process to Edgy broke my computer (totally - needed to restore from barebone backup) last time so I'll have to do with an upgraded FileZilla Portable  (2.2.29 upgraded from 2.2.24) running over Wine I guess and hope it is not as buggy as the last one... 

I miss FileZilla too...

---

### Post by tbroderick on 2006-12-09
How about lftp?

---

### Post by motin on 2006-12-09
You can also download the Beta 3 .tar.bz2 archive from filezilla.com, extract it and run bin/filezilla - no installation required - and I guess it is better than the 2.9.4-version. 

Still i found some slight problems:

1. Uploading doesn't work
2. Everything else seems buggy and broken...

---

### Post by Somenoob on 2006-12-09
Why do so many users dislike gFTP? i find it to be quite comfortable and useful.

---

### Post by v8YKxgHe on 2006-12-09
While gFTP is good, sometimes - the lack of a Tree View seriously makes my fingers/wrist hurt, double clicking in and out of folders is not fun, not fun at all. 

Linux seriously is lacking in the GUI FTP department, which I think is quite strange.

---

### Post by greggh on 2006-12-09
I don't use it myself, but I think I remember my friend recommending Midnight Commander as an ftp client. Has anyone tried that?

---

### Post by DC@DR on 2006-12-09
I have no problem at all with gFTP, it seems stable for me. Ofcourse I loved FileZilla also while I was on Windoze, and I will give it a try when the FileZilla v3.0 released :)

---

### Post by zachtib on 2006-12-09
has anyone tried to build filezilla with prevu? (it's in the feisty repository)

---

### Post by zachtib on 2006-12-09
I just built filezilla on edgy with prevu. It builds, installs, and runs just fine, which would make it prime backporting material, methinks

---

### Post by BlueSun on 2007-03-28
Ah!  At long last I have found the solution: [FireFTP]("https://addons.mozilla.org/en-US/firefox/addon/684").  This is a simple Firefox extension that runs in a tab right in the browser.  It's lightning fast -- especially for an extension -- and it has all the features I missed from FileZilla.  This has become my most well-used Firefox extension *by far*.  It's worth checking out -- you may never go back!

---

### Post by Bloodfen Razormaw on 2007-03-28
There is no legitimate use of FTP that requires a devoted application (really, there's no legitimate use for FTP at all anymore, but that's another issue).  Use Konqueror or Nautilus and use the FTP location as a local folder.

---

### Post by v8YKxgHe on 2007-03-29
Bluesun, you could always just install Filezilla from the Ubuntu backport repo's?

---

### Post by frotzed on 2007-04-12
> **DC@DR said:**
> I have no problem at all with gFTP, it seems stable for me. Ofcourse I loved FileZilla also while I was on Windoze, and I will give it a try when the FileZilla v3.0 released :)

I'm pretty sure that the reason some folks don't like gftp is its interface, not the stability of the client.  It's really as solid as a rock, but filezilla has the best GUI, IMHO and I'm anxiously waiting to get home so I can try installing it.

---

### Post by fuzznight on 2007-04-12
> **BlueSun said:**
> Ah!  At long last I have found the solution: [FireFTP]("https://addons.mozilla.org/en-US/firefox/addon/684").  This is a simple Firefox extension that runs in a tab right in the browser.  It's lightning fast -- especially for an extension -- and it has all the features I missed from FileZilla.  This has become my most well-used Firefox extension *by far*.  It's worth checking out -- you may never go back!

I second this. It works like a charm, nice interface, and I can quickly access all the features I used in Filezilla.

---

### Post by Tiziano on 2007-05-30
> **Bloodfen Razormaw said:**
> There is no legitimate use of FTP that requires a devoted application (really, there's no legitimate use for FTP at all anymore, but that's another issue).  Use Konqueror or Nautilus and use the FTP location as a local folder.

Sorry to bump (hope it's not too old), but I came here via Google (looking on how to install the beta version).  

I use FileZilla on Windows because it's a great way to transfer files via SSH.  I'm used to it, so that's why I'm looking forward to using it under Ubuntu, too.

---

### Post by use a name on 2007-05-30
I like the current beta, since they included sftp. It's starting to look real good. :)

---

### Post by pommattski on 2007-06-10
This is good progress...  I was about to reboot into windows to use FileZilla, but though I'd check here in case there had been any updates...

I've now just installed the version in universe (currently V3 beta7).  Not quite up to the standard of the windows version yet - but well on the way. It's now good enough to prevent me from booting into Windows for this reason.

---

### Post by kiddo on 2007-06-10
why do you need a separate application for FTP? Your file manager does that already. See this short video demonstration I just recorded for you to show you how easy it is :)

[http://jeff.ecchi.ca/nautilus-ftp.ogg](http://jeff.ecchi.ca/nautilus-ftp.ogg) (1.5 Mib)

---

### Post by ThinkBuntu on 2007-06-10
FileZilla is available in Linux. Check the repos, I think it's there. KFTPGrabber is pretty solid. When I'm in GNOME, I just use gFTP, as I'm usually just maintaining websites with a quick transfer here or there, but I've found KFTPGrabber to be very solid, especially with its default tree menu structure.

---

### Post by pommattski on 2007-06-10
Cheers kiddo...  I didn't realize it was that easy through nautilus.  
However, I regularly have to connect to 5, or so, different servers, and filezilla with it's site manger, along with it's local and remote tree and file listing makes it all very easy.

---

### Post by kiddo on 2007-06-10
oh and just for additional info, nautilus and konqueror support just typing a ftp/sftp kind of url in their location bars (ctrl-L usually). For example,
```
sftp://user@host:port
```

---

### Post by Zootropo on 2007-06-10
And you can bookmark your connections, which is always useful for fast and easy access

---

### Post by morningboat on 2007-06-10
I currently use [CrossFTP]("http://www.crossftp.com/"), which is a java web start GUI FTP client for your desktop, and is very solid. It is worth of trying, and you may never come back again.

---

### Post by Tiziano on 2007-07-23
> **kiddo said:**
> why do you need a separate application for FTP?  I use FileZilla for SFTP.  I don't even use plain FTP anymore.

---

### Post by motin on 2007-07-23
> **Bloodfen Razormaw said:**
> There is no legitimate use of FTP that requires a devoted application (really, there's no legitimate use for FTP at all anymore, but that's another issue).  Use Konqueror or Nautilus and use the FTP location as a local folder.

> **kiddo said:**
> oh and just for additional info, nautilus and konqueror support just typing a ftp/sftp kind of url in their location bars (ctrl-L usually). For example,
```
sftp://user@host:port
```

> **Zootropo said:**
> And you can bookmark your connections, which is always useful for fast and easy access

> **pommattski said:**
> This is good progress...  I was about to reboot into windows to use FileZilla, but though I'd check here in case there had been any updates...

I've now just installed the version in universe (currently V3 beta7).  Not quite up to the standard of the windows version yet - but well on the way. It's now good enough to prevent me from booting into Windows for this reason.

> **Tiziano said:**
> I use FileZilla on Windows because it's a great way to transfer files via SSH.  I'm used to it, so that's why I'm looking forward to using it under Ubuntu, too.

To wrap it up, it seems that the time has come where there is no logic reason to miss FileZilla - at least not when using Feisty repos:
[LIST]
[*]For those who want to run the Windows version, FileZilla over WINE is very stable with the current versions of WINE.
[*]For a native version, the filezilla package includes version 3.0.0 Beta 7 native linux port of FileZilla - just install and fire up.
[*]For those that do not need the ability to queue a lot of transfers, or believes that using a separate FTP program for file transfers over SSH/SFTP/FTP is like using a separate computer screen to read ones e-mails -  use the standard file manager (Nautilus / Konqueror)
[*]For those that do not need to transfer files through SSH/SFTP, use the FireFTP Firefox extension
[*]If none of this suits you - use KFTPGrabber, gFTP, lftp, CrossFTP or any other FTP software available to the Linux platform
[/LIST]

Freedom of choice :)

---

### Post by aysiu on 2007-07-23
SFTP doesn't work for me in Nautilus. It does in FileZilla.

You're right, though--there's no point in missing something that exists. I currently run FileZilla that's available through the repositories.

I don't see what's wrong with using a separate application for FTP, though. How is that any more steps or any more trouble than firing up Nautilus? Or opening a FireFTP tab in Firefox?

---

### Post by alan_new on 2007-07-26
Does anybody know how to manage files on a server that runs OpenVMS through a FTP client like gFTP or Filezilla 3? I'm able to do so only with Filezilla 2.2. gFTP connects to the server but it doesn't show the files, while Filezilla 3 connects and shows the files, but I can't do nothing with them. They have a (I think) version number by the name of files and directories like "picture.jpg;1".

---

### Post by frodon on 2007-07-26
I'm still looking for a good FTP client which support FTPS (TLS auth/encryption) but unfortunately neither gFTP nor filezilla support it despites it is the most secure FTP transfer so till now i'm stuck with fireFTP but would really prefer a dedicated client rather than a firefox extendion.

I hope gFTP or filezilla will include FTPS support soon.

---

### Post by aysiu on 2007-07-26
> **frodon said:**
> I'm still looking for a good FTP client which support FTPS (TLS auth/encryption) but unfortunately neither gFTP nor filezilla support it despites it is the most secure FTP transfer so till now i'm stuck with fireFTP but would really prefer a dedicated client rather than a firefox extendion.

I hope gFTP or filezilla will include FTPS support soon.
When's the last time you tried Filezilla, frodon? I think it now has what you're looking for. Not 100% sure, though.

---

### Post by frodon on 2007-07-26
Will test this as soons as i'm at home, last time i checked filezilla it didn't had the FTPS support, i would be more than happy if it has now \\:D/

---

### Post by aysiu on 2007-07-26
> **frodon said:**
> Will test this as soons as i'm at home, last time i checked filezilla it didn't had the FTPS support, i would be more than happy if it has now \\:D/
It's been evolving quite quickly. It feels as if only a few months ago it didn't have any option but just plain text FTP. Now it has four options.

---

### Post by frodon on 2007-07-27
I tested it yesterday and you are right aysiu, filezilla has now all the features i need, to be exact what i needed is what filezilla call FTPES and very few FTP clients support it.

I'm a new filezilla fan now, thanks for the update about filezilla features aysiu.

---

### Post by runningwithscissors on 2007-07-27
Don't know about filezilla as an FTP client, but I did try to set up an FTP server on Windows with FileZilla and it was ****.

---

### Post by pt123 on 2007-08-21
Found a place with DEBS for RC1
[http://ftp.cica.es/guadalinex/reposi...e/f/filezilla/](http://ftp.cica.es/guadalinex/reposi...e/f/filezilla/)


This one has beta
[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)


[http://linuxappfinder.com/package/filezilla](http://linuxappfinder.com/package/filezilla)
Only has for Gutsy

---

### Post by misfitpierce on 2007-08-21
linuxappfinder has for feisty as well for beta. Filezilla is auto installed with automatix tho.

[http://getautomatix.com](http://getautomatix.com)

---

### Post by 23meg on 2007-08-22
FileZilla is in Gutsy Universe.

[http://packages.ubuntu.com/gutsy/net/filezilla](http://packages.ubuntu.com/gutsy/net/filezilla)

---

### Post by AnRkey on 2007-10-01
Thanks to the MOTU team for this! I am so happy now :D

---

### Post by techpr on 2007-10-04
just installed FileZilla 3.0.1 and imported the .xml from the windows version, thanks..!

---

### Post by xyloweb on 2007-11-04
I see that a newer version of FileZilla (3.0.2.1) is available.

[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)

How soon should I expect it to be available in the Synaptic Package Manager?

(I am a very new Ubuntu user.)

---

### Post by bruce89 on 2007-11-04
> **xyloweb said:**
> How soon should I expect it to be available in the Synaptic Package Manager?

Never until you upgrade to Hardy.

---

### Post by TeaSwigger on 2007-11-04
> **xyloweb said:**
> I see that a newer version of FileZilla (3.0.2.1) is available.

[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)

How soon should I expect it to be available in the Synaptic Package Manager?

(I am a very new Ubuntu user.)

Hello, 

Hard to say. It might wait until the next major release (Hardy Heron) or it might come through in the "backports" (if you have the backports repositories enabled in your system). There's only so many folks working on tons of apps out there, and with there being so many ftp apps already available it's hard to know if they'll have it as a high enough priority to add it soon or soonish.

---

### Post by ghandi69_ on 2007-11-05
This thread seems strange to me because just last week I did the ole..

> sudo apt-get install filezilla

and have been using it ever since....

---

### Post by yngens on 2008-03-24
I am on Hardy now and using FileZilla 3.0.7.1. This version has an option to make associations for editor programm, but unfortunately I could not make it work. Pointing to '/usr/bin/gedit' did not help. And it requires putting path to programm, it does not accept a command.

I would appreciate if anyone could advice how to make editor programm work. I am tired of switching between two windows all the time - FileZilla and Browser - to edit my files.

---

