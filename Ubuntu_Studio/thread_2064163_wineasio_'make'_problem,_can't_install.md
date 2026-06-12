---
title: "wineasio 'make' problem, can't install"
date: 2012-09-28
forum: Ubuntu Studio
---

### Post by kujaw on 2012-09-28
Hello guys, my newbish skills are not sufficient to deal with this problem..
When I type 'make' in terminal the problem occures:
```
kujaw@KujawLap:~/wineasio$ make
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
In file included from /usr/include/stdio.h:28:0,
                 from asio.c:33:
/usr/include/features.h:324:26: fatal error: bits/predefs.h: Nie ma takiego pliku ani katalogu
compilation terminated.
make: *** [asio.o] B&#322;&#261;d 1
kujaw@KujawLap:~/wineasio$ 

```I installed wine-dev repository and I lack any idea..
My Linux distribution:
3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by kujaw on 2012-09-28
I tried the .deb wineasio. I downloaded wineasio_0.9.0-2_all.deb, than
```
sudo dpkg -i wineasio_0.9.0-2_all.deb
```
and next
```
regsvr32 wineasio.dll
```
The response was: Failed to load DLL wineasio.dll
I'm still looking for some clues in the Inernet but I'd be very thankfull if anyone can help me here :)

---

### Post by sgx on 2012-09-29
Hi, you wouldn't want to use 'make' as part of a .deb install.
That is a step during compilation. I would delete any version, and reinstall by synaptic, or using 

sudo dpkg -i name-of.deb

My wineasio is in /usr/lib/wine and has a symbolic link to /usr/lib/

Remember to have the same user start all the audio programs.

The version of both wine, and wineasio, can vary, without losing
much function, so older versions can be tried, and wine 1.3 may be
fine. I'm using a wine 1.2, and a wineasio 7.3, trying to sort
out some other niggles. The best luck is usually had by using
synaptic, and wine repository, and only installing manually,
when left no other choice. Which usually works in the end.

[http://www.ubuntugeek.com/download-wineasio-deb-packages.html](http://www.ubuntugeek.com/download-wineasio-deb-packages.html)

[https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages](https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages)

:popcorn:

---

### Post by kujaw on 2012-09-29
I tried 'make' not for .deb installation but for 'wineasio-0.9.0.tar.gz'. After not having any success with it I removed wineasio and tried the .deb install. And so on, another problem stopped my work..

OK. I installed the .deb package not by Synaptic (I can't find it there) but by Ubuntu Software Center. Do I have to regsvr32 it?
How to know if asio works?

---

### Post by sgx on 2012-09-29
Hi, yes do the regsvr32 wineasio.dll as normal user, not sudo.
To test a windows vst,
install reaper daw, your /home/username folder is fine,
about 31 meg when installed.

[http://www.cockos.com/reaper/resources.php](http://www.cockos.com/reaper/resources.php)

wine reaper4261-install.exe

wine REAPER/reaper.exe  (default folder is usually in caps,
name it as desired.

Create the standard vst path that most installers like.

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

install or copy vst plugins to that folder

Start reaper, in its (many)preferences, select your sound card, midi keyboard, select asio as audio device, not wdm, choose wineasio as the driver, select the above vst folder for reaper to scan and accept the vsts.

Use the reaper menu option 'Insert plugin on new track' and a track
will be created, and the plugin gui displayed. Make sure the track
is armed, not muted, and hit some keys.

.wine folder can be renamed Old-wine etc if problems arise,
giving you a clean slate, just run the winecfg command again.

Another good test/use option is Festige

[http://festige.sourceforge.net/](http://festige.sourceforge.net/)

While not a daw, linux itself, is, and festige is
very useful for musicians and bands just wanting vsts in the
sonic arsenal. I'll guess that more than half of windows vsts
work in festige, 80-90% in reaper, including many fine pro
instruments. Dongles and intrusive copy protected apps will fail.
Cheers

---

