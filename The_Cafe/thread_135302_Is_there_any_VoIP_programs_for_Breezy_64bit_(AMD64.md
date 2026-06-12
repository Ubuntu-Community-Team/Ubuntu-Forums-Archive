---
title: "Is there any VoIP programs for Breezy 64bit (AMD64) out there like Skype??"
date: 2006-02-23
forum: The Cafe
---

### Post by Bandit on 2006-02-23
Hello Everyone,
Is there any VoIP programs for Breezy 64bit (AMD64) out there like Skype??
Thanks,
Joey

---

### Post by Jason_25 on 2006-02-23
Well Skype works.  In dapper, there is ekiga which has some voip support too.

---

### Post by Bandit on 2006-02-23
[QUOTE=Jason_25]Well Skype works.  In dapper, there is ekiga which has some voip support too.[/QUOTE]
I went home for lunch and downloaded the Skype binary tarball and it wouldnt work. It keeps giving me libxcurses*** missing.
I have libxcurses installed, so I assumed it was becuase I was running 64bit and the binary was more likely compiled for 32bit.

Isnt Ekiga the new Gnome Meeting?

Thanks,
Joey

---

### Post by kaamos on 2006-02-23
Ekiga. :KS 

Yes it is. I'm not shure about 64bit, but other programs you could try are openwengo and gizmo.

---

### Post by ssam on 2006-02-23
[QUOTE=Bandit]Isnt Ekiga the new Gnome Meeting?
[/QUOTE]

yes. it looks quite good.

[http://www.ekiga.org/](http://www.ekiga.org/)

---

### Post by Jason_25 on 2006-02-23
You have to play with skype to get it working usually.  Did you try the static tarball?  That's the one I use on kubuntu dapper with no problems and on ubuntu dapper with some mic problems.

---

### Post by henriquemaia on 2006-03-28
[QUOTE=Jason_25]You have to play with skype to get it working usually.  Did you try the static tarball?  That's the one I use on kubuntu dapper with no problems and on ubuntu dapper with some mic problems.[/QUOTE]

Good tip. Got it to work just like that on Ubuntu Dapper flight5 amd64.

---

### Post by henriquemaia on 2006-04-07
[QUOTE=henriquemaia]Good tip. Got it to work just like that on Ubuntu Dapper flight5 amd64.[/QUOTE]

Got it to work and mic is functioning perfectly.

---

### Post by spirilis on 2006-05-08
FYI I just got openwengo working in Ubuntu 5.10 breezy badger amd64/x86_64

It's an i386 binary so I had to use "dpkg --force-architecture -i wengophone-0.958m-1.i386.deb"

then it needed some libraries... note that /usr/bin/wengophone just goes into /usr/lib/wengophone, does LD_LIBRARY_PATH="." and runs the real binary, so any extraneous libraries you can just toss into /usr/lib/wengophone

I d/l'ed libqt3-mt i386, libssl0.9.7 i386 and libasound2 i386 -- took the .deb's, used "alien -t" to convert them into .tgz files, untarred those, then took the libraries in usr/lib/ and copied them into /usr/lib/wengophone

root@scitus:/usr/lib/wengophone# ls -l
total 16638
-rw-r--r--  1 root root   18356 Dec 16 11:50 COPYING
-rw-r--r--  1 root root    4776 Dec 16 11:50 changelog-fr.txt
drwxr-xr-x  3 root root      72 May  8 00:03 emoticons
drwxr-xr-x  2 root root      80 May  8 00:03 icons
-rw-r--r--  1 root root     124 Dec 16 11:49 index-fr.html
drwxr-xr-x  2 root root     464 May  8 00:03 lang
lrwxrwxrwx  1 root root      18 May  8 00:26 **libasound.so.2 -> libasound.so.2.0.0**
-rw-r--r--  1 root root  737024 May  6 21:37 **libasound.so.2.0.0**
-rwxr-xr-x  1 root root 2375912 Dec 23 09:27 libavcodec.so
-rw-r--r--  1 root root 1022224 Aug 24  2005 **libcrypto.so.0.9.7**
-rwxr-xr-x  1 root root 1483396 Dec 23 09:28 libphapi.so
-rwxr-xr-x  1 root root  160091 Dec 23 09:27 libportaudio.so
lrwxrwxrwx  1 root root      17 May  8 00:25 **libqt-mt.so.3 -> libqt-mt.so.3.3.6**
lrwxrwxrwx  1 root root      17 May  8 00:25 **libqt-mt.so.3.3 -> libqt-mt.so.3.3.6**
-rw-r--r--  1 root root 8273808 Apr  6 01:26 **libqt-mt.so.3.3.6**
lrwxrwxrwx  1 root root      15 May  8 00:25 **libqui.so.1 -> libqui.so.1.0.0**
lrwxrwxrwx  1 root root      15 May  8 00:25 **libqui.so.1.0 -> libqui.so.1.0.0**
-rw-r--r--  1 root root  236264 Apr  6 01:26 **libqui.so.1.0.0**
-rw-r--r--  1 root root  191744 Aug 24  2005 **libssl.so.0.9.7**
-rwxr-xr-x  1 root root   20670 Dec 23 09:27 libwebcam.so
-rwxr-xr-x  1 root root  217070 Dec 23 09:28 libwengocurl.so
-rw-r--r--  1 root root   20641 Dec 16 11:50 licence-fr.txt
-rw-r--r--  1 root root     557 Dec 16 11:50 readme-fr.txt
drwxr-xr-x  3 root root     136 May  8 00:03 sounds
-rwxr-xr-x  1 root root 2222956 Dec 23 09:29 wengophone

note the libssl, libqui, libqt-mt, libasound2

once I had those in place, I was able to run 'wengophone' and have it pop up a window.  I haven't actually tried using it (don't know anyone else with wengo yet, but I know someone who's gonna try it soon).
It did detect my soundcard and all.

---

### Post by osca1 on 2006-05-08
I'm currently trying out [Gizmo]("http://www.gizmoproject.com") on a 5-station LTSP setup. Everything seems fine but I have some mic problems at present. Otherwise, nice product.

---

### Post by dolny on 2006-05-08
Well I just did apt-get on skype and that's all. (With some extra repos enabled)

Works like a charm. I hope they'll get the video streaming version for Linux working finally :/

---

### Post by CyberAngel on 2006-06-09
[QUOTE=dolny]Well I just did apt-get on skype and that's all. (With some extra repos enabled)

Works like a charm. I hope they'll get the video streaming version for Linux working finally :/[/QUOTE]


You did apt-get the skype on amd64????
Where are those extra repos?? :)

---

### Post by Jason_25 on 2006-06-09
[QUOTE=CyberAngel]You did apt-get the skype on amd64????
Where are those extra repos?? :)[/QUOTE]

The PLF repo has skype.

---

### Post by CyberAngel on 2006-06-09
[QUOTE=Jason_25]The PLF repo has skype.[/QUOTE]


Yeah, but it is for 32bits. Anyway Skype is easy enough to make it work under amd64 ;)

If you download [this]("http://www.skype.com/go/getskype-linux-static") file and extract three (libXcursor1, libXft2 and libXfixes3) 32bit libraries into /usr/lib32 it works :)

---

### Post by Jason_25 on 2006-06-09
Your right on the repos.  The missing .so thing is a fairly recent development.  It used to work on AMD64 with no additional 32-bit libraries.

---

### Post by Anything Generic on 2006-06-14
> **CyberAngel]Yeah, but it is for 32bits. Anyway Skype is easy enough to make it work under amd64  said:**
> this[/URL] file and extract three (libXcursor1, libXft2 and libXfixes3) 32bit libraries into /usr/lib32 it works :)

I downloaded that file, extracted to the Desktop, extracted those 3 libs to /usr/lib32.  I also installed linux32.

I type ./skype or linux32 ./skype in the terminal, yet I'm told skype doesn't exist, when it clearly does??  What am I doing wrong?

> eric@ubuntu:~/Desktop/skype-1.2.0.18$ ls
LICENSE  icons  skype                 skype.conf     skype.desktop.old
README   lang   skype-callto-handler  skype.desktop  sound
eric@ubuntu:~/Desktop/skype-1.2.0.18$ ./skype
bash: ./skype: No such file or directory
eric@ubuntu:~/Desktop/skype-1.2.0.18$ linux32 ./skype
Cannot execute ./skype: No such file or directory


---

### Post by Johnsie on 2006-06-14
You might wanna try the Wengophone Beta........ [http://wengo.com](http://wengo.com)

Make sure you download version 2 becauseUbuntu has version 0.99 in the repositories and version 2 is a lot different (supports all the major IM networks and looks a lot better)


I actually prefer wengophone 2 beta to Gaim.

---

### Post by CyberAngel on 2006-06-14
[QUOTE=eric.ws.anderson]I downloaded that file, extracted to the Desktop, extracted those 3 libs to /usr/lib32.  I also installed linux32.

I type ./skype or linux32 ./skype in the terminal, yet I'm told skype doesn't exist, when it clearly does??  What am I doing wrong?[/QUOTE]

Is skype executable??
Try to make it executable by typing the following command into the skype folder:

```
chmod 755 skype
```

---

### Post by Anything Generic on 2006-06-14
[QUOTE=CyberAngel]Is skype executable??
Try to make it executable by typing the following command into the skype folder:

```
chmod 755 skype
```[/QUOTE]

Thanks for the response!  -No dice :(
I'm still being told that there's no such file or directory...

> eric@ubuntu:~/Desktop/skype-1.2.0.18$ ls
LICENSE  icons  skype                 skype.conf     skype.desktop.old
README   lang   skype-callto-handler  skype.desktop  sound
eric@ubuntu:~/Desktop/skype-1.2.0.18$ sudo chmod 755 skype
eric@ubuntu:~/Desktop/skype-1.2.0.18$ ./skype
bash: ./skype: No such file or directory
eric@ubuntu:~/Desktop/skype-1.2.0.18$ linux32 ./skype
Cannot execute ./skype: No such file or directory


---

### Post by CyberAngel on 2006-06-14
[QUOTE=eric.ws.anderson]Thanks for the response!  -No dice :(
I'm still being told that there's no such file or directory...[/QUOTE]


Very weird :-k 

I don`t know what to mention... Just I will tell you what I would try myself...

[LIST]
[*] Try to download the file again
[*] Extract it somewhere and rename the folder name to skype (remove the "-", "." and numbers)
[*] Move it in my home dir and run it from there.
[*] Move it as root to /opt and try to run it from there.
[*] Try to run it using kdesu (or gksudo for gnome. I am using Kubuntu)
[*] Try to run it using full path (e.g. if the executable is on ~/skype/skype i would run it as is. Not cd ~/skype && ./skype but ~/skype/skype)
[/LIST]
I can`t imagine something else :confused:

---

### Post by Anything Generic on 2006-06-14
Tried every one of your suggestions except desu (or gksudo for gnome.  I used the "Run Program..." tool from Applications, but that just brought up a black terminal that appeared and dissapeared within a second.

I also tried executing from Thundar File Manager, which gave me the error:
Failed to execute child process "/home/eric/skype/skype" (no such file or directory)

I can execute Firefox, Abiword, etc.. 
I just don't get it :(

I also noticed that when I try to double click my flash drive on the desktop, it tells  me that it "could not execute pmount"

Does my user account 'eric' not have execute permissions or something in some cases?  I've been using sudo and it doesn't make a difference.

aaaah!

---

