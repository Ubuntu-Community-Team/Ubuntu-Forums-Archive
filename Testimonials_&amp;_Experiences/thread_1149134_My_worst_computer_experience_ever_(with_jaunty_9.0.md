---
title: "My worst computer experience ever (with jaunty 9.04)"
date: 2009-05-04
forum: Testimonials &amp; Experiences
---

### Post by loudog23 on 2009-05-04
Hello everyone,
I would like to share some of my fustration.
First things, i must say that most of the issues i had this week-end is not related to Ubuntu itself. It is mostly a lack of connaisance from my part, an the misfortune of installing an 'not good' driver.

I started to compute at the age of 6, we need to go back in 1983, when most people didn't even know waht a computer was.  Then in the beginning of the 90's came the AT, then the pentium and finally here we are with incredile system that can do multiple task at once.

I moved to linux about 6 months ago, At first i was switching bewteen windows and linux alot to get my work done. After couple of week and months learning ubuntu i got rid of all MS crap that was in my system.

So here i was, last friday with my ubuntu 8.10 running so smooth. I had an apache server, an ftp server, my music in the background and playing AO all at once on my little 1.25gig ram.

Then i saw Jaunty was available, so i told myself, let give this a try. So Saturady i spent the day backing up my files and making a fresh-clean install of my system. (format everything and install jaunty fresh and nice).

I encrypted my home partition, re-installed the servers, had my theme look so nice, everything worked extremely well... So i told myself, ok, enough work let's play.

So i get on AO, it was so laggy. I check around a realize the video drivers was not installed. So get into add/remove program, install the ATI drivers from there and BOOM! system freeze. All is lock up, mouse dosen't move and music is stalled on the same BURRRRRRRRRRRRRR. 

Press the reset button, reload and then right after the splash screen, all the graphics are messed up and the computer is frozen again. I did not have an live cd to play with since i installed from the alternate cd.
So i decided to re-install everything leaving my home partiton intact.
After all this, i get into my 'once-again' freshly installed Jaunty but cannot access my old home dir since it was encrypted. no way to find back the key (since it was in my / partition).

After debating about it in my head, i decided to wipe my HDD once more, leaving behind about 10000 mp3s, 50 videos and few 1000's of pictures.
Good thing i did backup the important stuff on an external HDD before my 1st wipe.

So here i am, with a newly install 8.10 Intrepid, with an empty HDD, 36 direct download and 53 torrent download (trying to recover most of the music and video i lost), making my updates on intrepid and wondering why ATI did not get there video drivers working properly on jaunty in the 1st place.

Like i said before, i know this is not about ubuntu crashing on me. It's mainly about 3rd party restricted driver that did not work properly, me wanting to play a online game and a lost encryption key. 

Anyway, there is a fw thing i've learned from this experience:
1- Always backup your stuff
2- Backup your stuff, always
3- do not ignore the warning saying this driver might not work properly
4- make myself my own key and write it down!

Anyway, with all this, Microsoft windows is still going down the drain, and i just can't wait to have my ubuntu set-up like it was before because it was priceless to see my friend's face when he saw me running an open-gl 3d Online game, while copying his USB drive onto my ftp, having music playing in the background and still be able to open an firefox session to go check out stuff on the net. :guitar:

lou

---

### Post by BIGtrouble77 on 2009-05-04
So why didn't you just boot into the terminal as root, edit your xorg.conf to use the default vga driver, then sort out the ati issue?  

Reformatting my system every time I had a driver issue would drive me to insanity, that's why I stopped using windows. ;)

---

### Post by blackened on 2009-05-04
> **BIGtrouble77 said:**
> So why didn't you just boot into the terminal as root, edit your xorg.conf to use the default vga driver, then sort out the ati issue?  

Reformatting my system every time I had a driver issue would drive me to insanity, that's why I stopped using windows. ;)

Agreed, that seems like a much more reasonable response. At the very worst, you could boot into the live cd to set things aright with the xorg gods.

---

### Post by caravel on 2009-05-05
Sounds like you have an unsupported ATI card.  The latest drivers that come with 9.04 do not support the X series cards or older.  I advise you to stick with 8.10.

> **BIGtrouble77 said:**
> So why didn't you just boot into the terminal as root, edit your xorg.conf to use the default vga driver, then sort out the ati issue?
That alone may not have worked.  The fglrx module itself locked up the system in my case, so even with the oss drivers in use you still get problems.  The solution I found was to do: "apt-get remove fglrx*" from the root terminal edit "fglrx" out of xorg.conf and then reboot.  This should bring back a working display.

---

### Post by loudog23 on 2009-05-05
> **caravel said:**
> Sounds like you have an unsupported ATI card.  The latest drivers that come with 9.04 do not support the X series cards or older.  I advise you to stick with 8.10.

That's the one i re-installed (8.10) since it was the latest "good" configuration for me.


> **caravel said:**
> That alone may not have worked.  The fglrx module itself locked up the system in my case, so even with the oss drivers in use you still get problems.  The solution I found was to do: "apt-get remove fglrx*" from the root terminal edit "fglrx" out of xorg.conf and then reboot.  This should bring back a working display.

"apt-get remove fglrx" this is what i was looking for when i spend 3 hours trying to set this back up.... ill know for next time :) thx. Like i said before, it is alos due to a lack of knowledge of my part. If i only knew this option i woul've been able to restore my music and video...

Oh well :) it's just 0's and 1's. All my personal and important stuff was backup up.

Thanks guys, i'm still learning new things!

---

### Post by Armor Nick on 2009-05-05
If you want longer support for old hardware, you'd best try MEPIS (or hardcore Debian ;) ). Though the packages are not that new, you can bet your soul on it that old hardware works perfect with it. Personally, I think they moved to Xorg 1.6 a little too soon.

---

### Post by loudog23 on 2009-05-05
I've been back to 8.10 since yesterday and i already miss the little new feature of jaunty :'(

Oh well, time to upgrade the video card i guess :)
Any suggestion? 

And ill try to bum one of those old pc at work to set the ftp on it and learn my way around with the server version :)

-> neven say never, well i don't think ill ever switch back to microsoft anyway. Im hooked to open-source, because it is free but mostly because people with open mind (you) help other people opening their mind (me).

Armor nick -> im not sure what you are talking about so i won't complicate things. As long as i can play AO, listen to my music and help my students friends with my servers i'm happy :)

Ill never say thx enough for your "moral-support" and understanding! LOL cheers again guys.

---

### Post by Alterax on 2009-05-06
> **Armor Nick said:**
> If you want longer support for old hardware, you'd best try MEPIS (or hardcore Debian ;) ). Though the packages are not that new, you can bet your soul on it that old hardware works perfect with it. Personally, I think they moved to Xorg 1.6 a little too soon.

Funny thing is hardcore Debian's not really all that hardcore...

---

### Post by loudog23 on 2009-05-07
hey guys,

i've ran an undelete on my external HDD (photorec from cgsecurity) and look what i found:
```

lou@trooper:~/000RESTORE/lou$ dir -l
total 116
drwxr-xr-x 2 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka360k-SW
drwxr-xr-x 3 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka361O1QiW8YIhulhnlb0c.eFE--
-rwxr-xr-x 1 lou root 12288 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka362fOPfEmwVk1vUICHLXbXoU--
drwxr-xr-x 2 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka366DtMIJXJ23BDu-VIXonEsE--
drwxr-xr-x 2 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka3671f.OpPx9uZgtM-59EHME---
-rwxr-xr-x 1 lou root 12288 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka369jGOXtA00u4ZPURyjN5Et---
-rwxr-xr-x 1 lou root 12288 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36AjKHISvCelxG6.WYOaszBE--
-rwxr-xr-x 1 lou root 12288 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36AmvcSlnPC9zdb7mwmH45SU--
drwxr-xr-x 4 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36cJ1.-u-yyOr9OyqPaZDdPU--
drwxr-xr-x 2 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36DcJSvuYoYEJDBPSVpYfBC---
drwxr-xr-x 2 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36DZIiZoxVq6NdXyAvaWnOYE--
drwxr-xr-x 8 lou root  4096 2009-05-04 18:30 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36EPvN4d2yzlPycpW5dA3xME--
drwxr-xr-x 4 lou root  4096 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36eYDJCWQKcPFtVp5WY4xAcU--
-rwxr-xr-x 1 lou root 12288 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36FlEZGRuYnG612WGducIXW---
drwxr-xr-x 2 lou root  4096 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36GCNyjb-VOjcI2DD5OVWqpE--
drwxr-xr-x 3 lou root  4096 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36goEoFs-x0u6eMRPcia99t---
drwxr-xr-x 3 lou root  4096 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36GVnfekIvdvtv3vcR7bmdME--
drwxr-xr-x 5 lou root  4096 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36IIIG.hhPoWP46TQIWGSfXk--
drwxr-xr-x 3 lou root  4096 2009-05-04 18:31 ECRYPTFS_FNEK_ENCRYPTED.FWYCaZGwHKGU2kTLHu5NpuNK7.fFVTLdka36Ja2MwdYUMf8sk-vyFLU8A---
lou@trooper:~/000RESTORE/lou$ 

```

these are older backup i've done with my own key (that i wrote down)
Can someone tell me if i can decrpyt those? and if so how can i do it?

thx
lou

---

### Post by jdrodrig on 2009-05-07
You write "10000 mp3s, 50 videos and few 1000's of pictures.
Good thing i did backup the important stuff on an external HDD before my 1st wipe.
So here i am, with a newly install 8.10 Intrepid, with an empty HDD, 36 direct download and 53 torrent download "

mp3s, videos...torrents? mmm....I hope we are talking about LEGALly downloaded music and videos...right?...=)

---

### Post by loudog23 on 2009-05-07
Jamendo my friends :) free opensource music.
Nine inch nails offer is 2 latest album freely on the net too ->nin.com

I'm not perfect but yes most of it is legal stuff. It's just a long process to re-rip everything in the computer...

---

### Post by ukripper on 2009-05-08
So far Jaunty is best release out of the box for me. Only problem with jaunty I had was with Update manager which kept freezing the system so i just disabled it completely, other than that everything is just perfect.:KS

---

### Post by solwic on 2009-05-09
> **jdrodrig said:**
> You write "10000 mp3s, 50 videos and few 1000's of pictures.
Good thing i did backup the important stuff on an external HDD before my 1st wipe.
So here i am, with a newly install 8.10 Intrepid, with an empty HDD, 36 direct download and 53 torrent download "

mp3s, videos...torrents? mmm....I hope we are talking about LEGALly downloaded music and videos...right?...=)

Not to hijack the thread, but I wanted to compliment you on your signature, jdrodrig.

> Philosophy doesn't get the work done...the success of Linux Community resides on its ability to listen to the people's demands and transform them into software faster/better than the alternatives

+1.  :biggrin:

---

