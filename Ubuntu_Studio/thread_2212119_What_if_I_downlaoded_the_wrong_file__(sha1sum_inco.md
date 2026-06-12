---
title: "What if I downlaoded the wrong file ? (sha1sum incorrect)"
date: 2014-03-19
forum: Ubuntu Studio
---

### Post by Ardeshir on 2014-03-19
HI !
I recently downlaoded UbuntuStudio13.10dvdAMD64.iso from its official site with direct link .
After the downlaod was complete I tried to run it on VirtualBox .
First I chose to try it without installing .
Nothing happened .
There is just a gray screen showing . (Plus there was an error while starting up , which you can see its picture :)

[IMG]http://ubuntuone.com/3Mn11iCuR83xcMpjCbRzmU[/IMG]

Then I tried installing it first , but the same thing happened .
I checked its sha1sum in terminal and it was different from the sha1 provided on its official site .

I had two questions :
1 - Why my sha1 is different ?
Is it the fault of my download manager or the file was corrupted . (read below , because I did something dangerous with my Downlaod manager)
Is it possible that the file on official site is corrupted ? ([http://ubuntustudio.org/download/](http://ubuntustudio.org/download/))

2 - What now ?
Should I redownload the whole file or is there any way that can fix it without redownloading the whole 2.5 gig ?

NOTE :
I downloaded it using FreeDownloadManager on windows 7 .
BUT I didn't download the whole file in one session and on one PC ;
I downloaded about 75% on a PC and copied its Data and file on another PC and resumed it there .
There wasn't any error during download .
FDM is supposed to be capable of doing such  a thing .
BTW if there is a corruption in file I think that may be the cause .
And this is the forum question I made if it helps : [http://www.freedownloadmanager.org/board/viewtopic.php?f=1&t=16766](http://www.freedownloadmanager.org/board/viewtopic.php?f=1&t=16766)

Thanks !
(And sorry if I created the topic in wrong place , I'm, not sure)

---

### Post by westie457 on 2014-03-19
The error in the picture is nothing to worry about, I get it all the time with VirtualBox.

As for 'free download manager' I have never used it. Either re-download w/out a download manager or get with a bit-torrent client.

---

### Post by su:bhatta on 2014-03-19
Yes, if the checksum is incorrect you have to download a fresh iso image. As of corrupt image in the Download site, chances are bleak, I guess they reverify after  hosting the image and we have all( at least I have) used that link get a copy of Ubuntu Studio 13,10 and it worked perfectly.

Never used FDM, so cannot comment, but if it failed once, it is suggested you go for a clean download in a single machine at one go, or you can follow westie457 and get it with bit torrent client.
Debian suggests using download managers while getting iso's and I follow that instead of just using the browser to get a iso. 

So, get  a fresh iso using bit torrent client or download manager and burn image to a dvd, sorry but there doesn't seem to be any other way to it.

---

### Post by Ardeshir on 2014-03-20
Thank you !
I just redownloaded it  using transmission client .

---

### Post by su:bhatta on 2014-03-20
You can mark this thread as 'Solved' using the 'Thread Tools' at the top right of the page, if the new iso works out for you.
Welcome to the world of Linux for creative humans & Best of luck.

---

