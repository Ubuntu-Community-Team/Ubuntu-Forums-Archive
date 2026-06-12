---
title: "Unable to play DVD"
date: 2014-10-07
forum: Ubuntu Development Version
---

### Post by watsbe on 2014-10-07
I have just installed utopic into a new partition (keeping my old trusty /home directory). Just about everything is working beautifully, but I cannot mount or play DVDs.
Unencrypted DVDs are reading OK
I have done libdvdread4 and install-css.sh but I am still getting "Add. Sense: Read of scrambled sector without authentication" in syslog.
I have the same problem for both my built-in DVD and an external USB DVD drive, and different DVDs
```

3.16.0-20-generic #27-Ubuntu SMP Wed Oct 1 17:35:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

dpkg -l libdvdread4 libdvdnav4 libdvdcss2
ii  libdvdcss2                         1.2.13-0               amd64                  library designed for accessing DVDs
ii  libdvdnav4:amd64                   5.0.1-1                amd64                  DVD navigation library
ii  libdvdread4:amd64                  5.0.0-1ubuntu1         amd64                  library for reading DVDs

```

Any suggestions?

---

### Post by David D. on 2014-10-07
Have you installed Ubuntu restricted extras from the repositories?

---

### Post by watsbe on 2014-10-07
Yep, forgot to mention that one. I've also rebooted.
```

ii  ubuntu-restricted-extras    61                 amd64              Commonly used media codecs and fonts for Ubuntu

```

---

### Post by Cavsfan on 2014-10-07
Try this:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I know you already have libdvdread4 installed and so did I but I couldn't play a DVD until I entered that command in terminal.
That *should* be all you need to do.

[http://ubuntuhandbook.org/index.php/2014/04/enable-dvd-playback-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-dvd-playback-ubuntu-14-04/)

---

### Post by fooman on 2014-10-07
> **Cavsfan said:**
> Try this:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I know you already have libdvdread4 installed and so did I but I couldn't play a DVD until I entered that command in terminal.
That *should* be all you need to do.

[http://ubuntuhandbook.org/index.php/2014/04/enable-dvd-playback-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-dvd-playback-ubuntu-14-04/)

lol, ya know my dvd player hasn't played cds or dvds for ages  now...can't remember when exactly it started,  but i never really use it  so never thought about it much.  i thought it was possibly hardware  related,  until i started the machine in windows one day and discovered  that the drive itself was in fact working.

anyways saw this  thread today and read Cavsfan's suggested command, ran it and to my  amazement...i once again have a functioning optical drive!!  

thank you brother!  :D

---

### Post by watsbe on 2014-10-08
Sadly, still no joy
```

sudo /usr/share/doc/libdvdread4/install-css.sh
--2014-10-08 18:34:37--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [text/plain]
Saving to: '/tmp/dvdcss-S5MJeW/Packages&#8217;

100%[======================================>] 3,520       10.1KB/s   in 0.3s   

2014-10-08 18:34:39 (10.1 KB/s) - '/tmp/dvdcss-S5MJeW/Packages&#8217; saved [3520/3520]

--2014-10-08 18:34:39--  http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44462 (43K) [application/octet-stream]
Saving to: '/tmp/dvdcss-S5MJeW/libdvdcss.deb&#8217;

100%[======================================>] 44,462      31.5KB/s   in 1.4s   

2014-10-08 18:34:41 (31.5 KB/s) - '/tmp/dvdcss-S5MJeW/libdvdcss.deb&#8217; saved [44462/44462]

(Reading database ... 177655 files and directories currently installed.)
Preparing to unpack .../dvdcss-S5MJeW/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...

```
Is there any way to race what's being called when a DVD is inserted?

---

### Post by zika on 2014-10-08
Did You install libdvdcss2 manually as suggested?

---

### Post by watsbe on 2014-10-08
Yep.
```

sudo dpkg -l libdvdcss2
ii  libdvdcss2                         1.2.13-0               amd64                  library designed for accessing DVDs

```
 Tried that. I used to have udev persistence rules. I can't see that that would make any difference.

---

### Post by Cavsfan on 2014-10-08
> **fooman said:**
> thank you brother!  :D

Just glad to help out! :) I was in Trusty and tried to play Fast and Furious (1st one) and it would not play then I found the above link and while I did have that file installed.
It did not work until I entered that command. Then it worked just like my DVD player by my TV.

---

### Post by cariboo on 2014-10-08
> **Cavsfan said:**
> Just glad to help out! :) I was in Trusty and tried to play Fast and Furious (1st one) and it would not play then I found the above link and while I did have that file installed.
It did not work until I entered that command. Then it worked just like my DVD player by my TV.

Now if there was only a way to play Blu-ray DVDs, I'd be happy. I've tried several different methods, and all I get is:

> Key is disabled

---

### Post by zika on 2014-10-08
> **cariboo907 said:**
> Now if there was only a way to play Blu-ray DVDs, I'd be happy. I've tried several different methods, and all I get is:Did You try:
[http://makemkv.com/](http://makemkv.com/)
[http://themediaviking.com/software/bluray-linux/](http://themediaviking.com/software/bluray-linux/)
Disclaimer: I do not have BR disk(s) and do not have player, I know only that once, some (I think long) time ago, I've managed to make my friend very happy. I'm not sure if [COLOR=#333333][FONT=Ubuntu]decryption key that has not been revoked since.
Update: That friend just told me that: [/FONT][/COLOR]http://ubuntuhandbook.org/index.php/2014/04/smplayer-play-blu-ray-discs/
NO: (Experimental)Possibility to play (**non-protected**) bly-ray discs. So, disregard my second suggestion. Sorry.

---

### Post by Cavsfan on 2014-10-08
Sorry **cariboo907** I don't have a clue. I don't even own a Blu-ray DVD or a player. Still behind the times.

---

### Post by zika on 2014-10-08
> **Cavsfan said:**
> Sorry **cariboo907** I don't have a clue. I don't even own a Blu-ray DVD or a player. Still behind the times.At least **two** of us. ;)

---

### Post by Cavsfan on 2014-10-08
> **zika said:**
> At least **two** of us. ;)

LoL! :lol: My son had a PS2 or 3 I forget and it played Blu-rays but he's in the Army in Europe now and got rid of the player and Blu-rays he had.

I know they are much better than regular DVDs but just haven't ventured in that direction.

---

### Post by cariboo on 2014-10-08
> **zika said:**
> Did You try:
[http://makemkv.com/](http://makemkv.com/)
[http://themediaviking.com/software/bluray-linux/](http://themediaviking.com/software/bluray-linux/)
Disclaimer: I do not have BR disk(s) and do not have player, I know only that once, some (I think long) time ago, I've managed to make my friend very happy. I'm not sure if [COLOR=#333333][FONT=Ubuntu]decryption key that has not been revoked since.
Update: That friend just told me that: [/FONT][/COLOR]http://ubuntuhandbook.org/index.php/2014/04/smplayer-play-blu-ray-discs/
NO: (Experimental)Possibility to play (**non-protected**) bly-ray discs. So, disregard my second suggestion. Sorry.

Thanks for the links, I installed makemkv, and after having a look at their forums, I can now play at least X-Men Origins Wolverine in VLC. :)

**Edit:**  I did a backup of the disk, and it used up 42GiB of hard drive space. :(

---

### Post by watsbe on 2014-10-09
DVDs are now working.
I went back and reinstalled each of the components, re-ran each of the scripts, rebooted again, applied a bunch of updates and it has started working.
Can't explain it, but I'm happy.

---

