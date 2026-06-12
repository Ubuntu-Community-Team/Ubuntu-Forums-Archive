---
title: "JACK and wineASIO problems"
date: 2013-06-05
forum: Ubuntu Studio
---

### Post by kjell159 on 2013-06-05
Hello,
I am still pretty new to Linux but I already really love it.
It's a little faster than windows, prettier, safer, free, a lot of distros, ...
But I also want to work with audio on my computer. (Like I did on windows.)
I would like to use REAPER (I have a license so I really want this to work, otherwise the money was for nothing because I bought it when I still worked with windows.)
and also utilise Ardour and several other studio-ish apllications and VST-plugins (if this is possible).
I use a Line6 POD Studio GX as my audio interface/soundcard and my computer is 64bit.

First I cannot start JACK to begin with.
When I click start within QjackCtl I get this message: 
[COLOR=#990099]
22:10:50.704 /usr/bin/jackd -P89 -p1024 -t2000 -dalsa -dhw:0 -r44100 -p256 -n2 -s -H -M[/COLOR]Cannot connect to server socket err = Bestand of map bestaat niet
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#ff0000]22:10:50.724 JACK kon niet opstarten. Sorry.[/COLOR]
[COLOR=#999999]22:10:51.834 JACK is gestopt met exit status=255.
[/COLOR]
(Sorry, I am a Belgian who speaks Dutch, it says:[COLOR=#0000ff]Bestand of map bestaat niet = File or map doesn't exist.[/COLOR] , [COLOR=#FF0000]JACK kon niet opstarten. = JACK could not start up. [/COLOR]and[COLOR=#999999] JACK is gestopt met exit status=255. = JACK has stopped with exit status=255.
 

    [/COLOR][COLOR=#000000]My other problem is the fact that I cannot compile my wineasio driver.
    I downloaded the wineasio ZIP file, extracted it and put it on my desktop.
Then I got the ASIOSDK from Steinberger and put the asio.h file in the wineasio folder.
But when I then go to my terminal: cd Bureaublad (=Desktop in Dutch)/wineasio and then type: make,
it gives me this message:
[/COLOR][COLOR=#999999]
[/COLOR]gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
In file included from /usr/include/fcntl.h:27:0,
                 from port.h:30,
                 from asio.c:22:
/usr/include/features.h:324:26: fatale fout: bits/predefs.h: Bestand of map bestaat niet
compilation terminated.
make: *** [asio.o] Fout 1
[COLOR=#000000]
fout=mistake/error

[/COLOR]
    [COLOR=#000000]If someone could help me out/further I would really, really appreciate it! ;)
And this my sound cliché but I really already have tried a lot,
I am already trying to make Linux work for audio production for about 2-3 weeks or so? (I had to install Ubuntu 4 times :) before it worked to my beliefs, at first I installed Wubi but that was really slow and doesn't has the security of Linux as a 'real' operating system + only a several GB, now I have my whole hard drive.)[/COLOR]

---

### Post by jejeman on 2013-06-05
First find out if the sound card is supported. Is this an USB card?
Give
```
aplay -l
```

---

### Post by kjell159 on 2013-06-06
I suppose it is supported. (It is USB.)

kaart 0: PCH [HDA Intel PCH], apparaat 0: ALC269VB Analog [ALC269VB Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: PCH [HDA Intel PCH], apparaat 3: HDMI 0 [HDMI 0]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
[COLOR=#ff0000]kaart 1: PODStudioGX [POD Studio GX], apparaat 0: POD Studio GX [POD Studio GX][/COLOR]
[COLOR=#ff0000]  Sub-apparaten: 1/1[/COLOR]
[COLOR=#ff0000]  Sub-apparaat #0: subdevice #0[/COLOR]

kaart=card
apparaat=device

---

### Post by kjell159 on 2013-06-08
Say my interface/sound card is supported,
does someone know what to do next?

---

### Post by jejeman on 2013-06-08
Try to simplify your JACK command. 
Close  all applications with audio and kill pulseaudio
```
pulseaudio -k
```
Start it from terminal.
```
jackd -dalsa -dhw:0 -r44100 -p512 -n2
```Do notice that the USB card is hw:1.

---

### Post by kjell159 on 2013-06-08
I did this and rebooted my computer.
Ardour (I still want to use Reaper also, though.) and QjackCtl start up again but now I have got another problem: I don't hear any sound. (I choose JACK in Ardour and when I press play or pause in QjackCtl it also happens in Ardour.)

---

### Post by jejeman on 2013-06-08
Did you made all necesery audio connections in JACK?

---

### Post by kjell159 on 2013-06-09
It seems like it works with Ardour now,
at first I only got sound from my computer's sound card but now it works with my interface as well. (By configuring the options and stuff in QjackCtl.)
Thanks for the help so far!
Now, when I try to compile wineasio I get this message:

gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
In file included from /usr/include/fcntl.h:27:0,
                 from port.h:30,
                 from asio.c:22:
/usr/include/features.h:324:26: fatale fout: bits/predefs.h: Bestand of map bestaat niet
compilation terminated.
make: *** [asio.o] Fout 1

Bestand of map bestaat niet=File or map doesn't exist

And also when I connect my guitar to my interface,
I only hear distorted/clipped sounds coming out of my monitors/speakers even when I don't use any effect/amp but when I record it (in Audacity) and then play back the recorded sound it sounds 'normal' like it would need to sound.

---

