---
title: "Download MySpace MP3"
date: 2007-04-04
forum: Tutorials
---

### Post by Camille Harang on 2007-04-04
Hi,

i don't have sound card at work so i usually download files to put in my MP3 player, but some MySpace's ones can't be downloaded directly so made a simple script for my own use to download it, if anyone is interested in here it is:

Install ngrep if you don't have it:
```
sudo apt-get install ngrep
```

Type this in a terminal:
```
packet=`gksudo 'ngrep -q -n 1 -W none /std_'` ; \
ip=`echo $packet | awk -F '-> ' '{ print $2 }' | cut -d ' ' -f1` ; \
path=`echo $packet | awk -F 'GET ' '{ print $2 }' | cut -d ' ' -f1` ; \
firefox http://$ip$path
```

Then just click the song you want using Firefox and you will be prompted to download it.

If you want to launch it as a desktop icon just open a terminal and type:
```
cat > Desktop/MyGrab.desktop
```

Select the code bellow:
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Exec=sh -c "packet=`gksudo 'ngrep -q -n 1 -W none /std_'` ; ip=`echo $packet | awk -F '-> ' '{ print $2 }' | cut -d ' 
' -f1` ; path=`echo $packet | awk -F 'GET ' '{ print $2 }' | cut -d ' ' -f1` ; firefox http://$ip$path"
Name=MyGrab
Icon=/usr/share/pixmaps/gnome-vumeter.png
```

Middle-click in the terminal and press Ctrl+D, then you have the MyGrab icon on your desktop, just launch it before clicking the song you want to download on MySpace.

Camille.

---

### Post by ConnectWith on 2007-09-06
Alternatively, you can use [http://www.myspacegrab.com/](http://www.myspacegrab.com/) to download myspace music.

---

### Post by dracayr on 2008-11-25
Didn't work for me, I had to adjust a bit. Here's my modified solution:

```
packet=`gksudo 'ngrep -q -n 1 -W none /std_'` ; \
ip=`echo $packet | awk -F 'Host: ' '{ print $2 }' | cut -d '.' -f1-3` ; \
path=`echo $packet | awk -F 'GET ' '{ print $2 }' | cut -d ' ' -f1` ; \
firefox http://$ip$path
```

dracayr

---

### Post by Unkuiri on 2009-07-11
Hi, I've tried your scripts but none of them works for me...:(...Can you help me?
I write what you said in the terminal and then clicked in the music i want in the site and nothing happens...:(...only passed a little time opens a firefox tab with this address> [http://www.'.com/](http://www.'.com/)
Do you know what I can do?

thanks in advance

---

### Post by timehAndGod on 2010-01-19
I have made a Python script that will download and convert MySpace music. I have attached it to this post, and remember to make it executable before using it! Here is a quick usage guide:

To install all requirements:
```
sudo ./dl_myspace_music.py -install
```

To download the music from [http://www.myspace.com/atlantafall](http://www.myspace.com/atlantafall) and [http://www.myspace.com/tokyokeys](http://www.myspace.com/tokyokeys) :
```
./dl_myspace_music.py atlantafall tokyokeys
```

Enjoy! I'm not sure how long before MySpace do things differently, but it works as of now.

EDIT: Here is a pastie.org of the code: [http://pastie.org/786253](http://pastie.org/786253)

---

### Post by Unkuiri on 2010-01-19
not working for me...:(
it detects the musics from the profile but gives an error:
> manuel@manuel-laptop:~$ ./dl-myspace-music.py jandek
Profile jandek loaded.

Loading tracks for jandek
Found track Nancy Sings (26072257)
Found track Moving Slow (26056945)
Found track Pending Doom (26056947)
Found track They Told Me I Was A Fool (26056950)

Downloading 4 tracks
Downloading Nancy Sings...
Traceback (most recent call last):
  File "./dl-myspace-music.py", line 145, in <module>
    Popen( [ "rtmpdump", "-r", "rtmpe://" + track.getRtmpUrl(), "-o", track.title + ".flv" ], stdout = PIPE ).communicate()
  File "/usr/lib/python2.6/subprocess.py", line 621, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1126, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
manuel@manuel-laptop:~$ 

Is there any way to solve this?
thnaks...:)

---

### Post by timehAndGod on 2010-01-19
> **Unkuiri said:**
> not working for me...:(
it detects the musics from the profile but gives an error:

Is there any way to solve this?
thnaks...:)

Have you tried the install flag first?
```
sudo ./dl-myspace-music.py -install
```

This will install MPlayer, and build and compile rtmpdump ( [http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/) )

---

### Post by Unkuiri on 2010-01-20
I've done as you said and shows this:
> manuel@manuel-laptop:~$ sudo ./dl-myspace-music.py -install
Installing MPlayer and Build-Essential...
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
mplayer já está na versão mais recente.
mplayer está definido para ser instalado manualmente.
build-essential já está na versão mais recente.
build-essential está definido para ser instalado manualmente.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 1 não actualizados.
Downloading rtmpdump source...
--2010-01-20 03:18:42--  [http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.1c.tar.gz](http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.1c.tar.gz)
A resolver rtmpdump.mplayerhq.hu... 213.144.138.186
A conectar rtmpdump.mplayerhq.hu|213.144.138.186|:80... conectado.
Pedido HTTP enviado, a aguardar resposta... 200 OK
Tamanho: 85132 (83K) [application/x-gzip]
A gravar em: 'rtmpdump.tar.gz'

100%[======================================>] 85.132       104K/s   em 0,8s    

2010-01-20 03:18:45 (104 KB/s) - 'rtmpdump.tar.gz' gravado [85132/85132]

make[1]: Entering directory `/home/manuel/rtmpdump'
gcc -Wall   -DRTMPDUMP_VERSION=\"v2.1c\" -O2   -c -o log.o log.c
gcc -Wall   -DRTMPDUMP_VERSION=\"v2.1c\" -O2   -c -o rtmp.o rtmp.c
rtmp.c:33:25: error: openssl/rc4.h: Ficheiro ou directoria inexistente
rtmp.c: In function &#8216;ReadN&#8217;:
rtmp.c:785: warning: implicit declaration of function &#8216;RC4&#8217;
In file included from rtmp.c:2048:
handshake.h:24:25: error: openssl/sha.h: Ficheiro ou directoria inexistente
handshake.h:25:26: error: openssl/hmac.h: Ficheiro ou directoria inexistente
In file included from handshake.h:28,
                 from rtmp.c:2048:
dh.h:28:24: error: openssl/bn.h: Ficheiro ou directoria inexistente
dh.h:29:24: error: openssl/dh.h: Ficheiro ou directoria inexistente
In file included from handshake.h:28,
                 from rtmp.c:2048:
dh.h: At top level:
dh.h:61: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dh.h:112: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
dh.h:150: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dh.h:181: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dh.h:214: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from rtmp.c:2048:
handshake.h:58: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;RC4_KEY&#8217;
handshake.h:58: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;RC4_KEY&#8217;
handshake.h: In function &#8216;InitRC4Encryption&#8217;:
handshake.h:60: error: &#8216;SHA256_DIGEST_LENGTH&#8217; undeclared (first use in this function)
handshake.h:60: error: (Each undeclared identifier is reported only once
handshake.h:60: error: for each function it appears in.)
handshake.h:63: error: &#8216;rc4keyIn&#8217; undeclared (first use in this function)
handshake.h:63: error: &#8216;RC4_KEY&#8217; undeclared (first use in this function)
handshake.h:64: error: &#8216;rc4keyOut&#8217; undeclared (first use in this function)
handshake.h:66: error: &#8216;HMAC_CTX&#8217; undeclared (first use in this function)
handshake.h:66: error: expected &#8216;;&#8217; before &#8216;ctx&#8217;
handshake.h:67: warning: implicit declaration of function &#8216;HMAC_CTX_init&#8217;
handshake.h:67: error: &#8216;ctx&#8217; undeclared (first use in this function)
handshake.h:68: warning: implicit declaration of function &#8216;HMAC_Init_ex&#8217;
handshake.h:68: warning: implicit declaration of function &#8216;EVP_sha256&#8217;
handshake.h:69: warning: implicit declaration of function &#8216;HMAC_Update&#8217;
handshake.h:70: warning: implicit declaration of function &#8216;HMAC_Final&#8217;
handshake.h:71: warning: implicit declaration of function &#8216;HMAC_CTX_cleanup&#8217;
handshake.h:76: warning: implicit declaration of function &#8216;RC4_set_key&#8217;
handshake.h:60: warning: unused variable &#8216;digest&#8217;
handshake.h: In function &#8216;HMACsha256&#8217;:
handshake.h:207: error: &#8216;HMAC_CTX&#8217; undeclared (first use in this function)
handshake.h:207: error: expected &#8216;;&#8217; before &#8216;ctx&#8217;
handshake.h:208: error: &#8216;ctx&#8217; undeclared (first use in this function)
handshake.h: In function &#8216;CalculateDigest&#8217;:
handshake.h:221: error: &#8216;SHA256_DIGEST_LENGTH&#8217; undeclared (first use in this function)
handshake.h: In function &#8216;VerifyDigest&#8217;:
handshake.h:236: error: &#8216;SHA256_DIGEST_LENGTH&#8217; undeclared (first use in this function)
handshake.h:236: warning: unused variable &#8216;calcDigest&#8217;
handshake.h: In function &#8216;HandShake&#8217;:
handshake.h:263: error: &#8216;RC4_KEY&#8217; undeclared (first use in this function)
handshake.h:263: error: &#8216;keyIn&#8217; undeclared (first use in this function)
handshake.h:264: error: &#8216;keyOut&#8217; undeclared (first use in this function)
handshake.h:318: warning: implicit declaration of function &#8216;DHInit&#8217;
handshake.h:318: warning: assignment makes pointer from integer without a cast
handshake.h:329: warning: implicit declaration of function &#8216;DHGenerateKey&#8217;
handshake.h:337: warning: implicit declaration of function &#8216;DHGetPublicKey&#8217;
handshake.h:353: error: &#8216;SHA256_DIGEST_LENGTH&#8217; undeclared (first use in this function)
In file included from rtmp.c:2048:
handshake.h:437: warning: implicit declaration of function &#8216;DHComputeSharedSecretKey&#8217;
handshake.h:452: error: too many arguments to function &#8216;InitRC4Encryption&#8217;
handshake.h:457: warning: unused variable &#8216;digestResp&#8217;
handshake.h:500: warning: unused variable &#8216;digest&#8217;
handshake.h:499: warning: unused variable &#8216;signature&#8217;
handshake.h: In function &#8216;SHandShake&#8217;:
handshake.h:579: error: &#8216;RC4_KEY&#8217; undeclared (first use in this function)
handshake.h:579: error: &#8216;keyIn&#8217; undeclared (first use in this function)
handshake.h:580: error: &#8216;keyOut&#8217; undeclared (first use in this function)
handshake.h:648: warning: assignment makes pointer from integer without a cast
handshake.h:683: error: &#8216;SHA256_DIGEST_LENGTH&#8217; undeclared (first use in this function)
handshake.h:771: error: too many arguments to function &#8216;InitRC4Encryption&#8217;
handshake.h:776: warning: unused variable &#8216;digestResp&#8217;
handshake.h:819: warning: unused variable &#8216;digest&#8217;
handshake.h:818: warning: unused variable &#8216;signature&#8217;
rtmp.c: In function &#8216;RTMP_Close&#8217;:
rtmp.c:2413: warning: implicit declaration of function &#8216;DH_free&#8217;
make[1]: *** [rtmp.o] Error 1
make[1]: Leaving directory `/home/manuel/rtmpdump'
make: *** [linux] Error 2
mv: impossível analisar `rtmpdump': Ficheiro ou directoria inexistente
Finished installation.


thanks

---

### Post by timehAndGod on 2010-01-20
Looks like a issue compiling rtmpdump. I think I missed a prerequisite. I have updated the script so re-download it and try again :)

---

### Post by Unkuiri on 2010-01-20
Works very well for me now...:)...thanks...

---

### Post by deezaztaboi on 2010-01-22
Hello I have trouble on how to configure these programs such as python and rtmpdump for enjoyment of downloading stream mp3s. I have installed python but am a little lost of direction from this point on. I am need of assistance, if you can provide please do so in terms that is very protocol!
Thanks

---

### Post by timehAndGod on 2010-01-22
> **deezaztaboi said:**
> Hello I have trouble on how to configure these programs such as python and rtmpdump for enjoyment of downloading stream mp3s. I have installed python but am a little lost of direction from this point on. I am need of assistance, if you can provide please do so in terms that is very protocol!
Thanks

Well first open a terminal, then type:
```
sudo apt-get install python
```

Download the script in my previous post, and while in the file browser rename it to "dl-myspace-music.py", then Right Click -> Properties, then click on the permissions tab and make sure "Allow executing as a program" is checked at the bottom.

Right click the file browser then click "Open in Terminal", and type:
```
sudo ./dl-myspace.music.py -install
```
This will then install everything you need to run the script.

Once complete, you can then type in the same terminal:
```
./dl-myspace-music.py tokyokeys
```
To download music from [http://www.myspace.com/tokyokeys](http://www.myspace.com/tokyokeys) profile.


As of now I am making a GUI application for this, so I will post back here when complete.

---

### Post by timehAndGod on 2010-01-22
Well I tried my hand at making a GUI. It's my first time GUI programming, so there might be bugs.

It should install the dependencies by default, except for rtmpdump, which you can either compile and install yourself, or type this into a terminal after installing the deb package:
```
sudo dlmsm -rtmpdump
```

Let me know what you think!

EDIT: Updated attachment and screenshot

[IMG]http://img130.yfrog.com/img130/7514/screenshot007j.png[/IMG]

---

### Post by deezaztaboi on 2010-01-24
> **timehAndGod said:**
> Well first open a terminal, then type:
```
sudo apt-get install python
```Download the script in my previous post, and while in the file browser rename it to "dl-myspace-music.py", then Right Click -> Properties, then click on the permissions tab and make sure "Allow executing as a program" is checked at the bottom.

Right click the file browser then click "Open in Terminal", and type:
```
sudo ./dl-myspace.music.py -install
```This will then install everything you need to run the script.

Once complete, you can then type in the same terminal:
```
./dl-myspace-music.py tokyokeys
```To download music from [http://www.myspace.com/tokyokeys](http://www.myspace.com/tokyokeys) profile.


As of now I am making a GUI application for this, so I will post back here when complete.

I have not been able to execute your directions. For the first step I open up Python2.6(command line) (I'm guessing this is what you mean by open terminal) as I type in the code "sudo apt-get install python" the outcome is "File "<stdin>", line 1 SyntaxError: invalid syntax"
As for your script I changed the name and made sure it was checked as read&execute.(there was no option "Allow execute as a program"

I rightclicked the script file and tried oepning it, the black box appears for a millisecond and it disappears. If I try opening it as Edit with IDLE, the file shows up with 2 boxes: one for to write commands and the other with lists of html commands. In the command box I type in 
sudo ./dl-myspace.music.py -install" 

but it shows as a syntax error so I dont know.

As for the GUI command, I downloaded your file and typed "sudo dlmsm rtmpdump" but it follows with as a syntax error

If I am doing anything wrong please let me know so I could fix it. Thanks

---

### Post by ContentSpooling on 2010-01-25
The code didn't also work for me.

---

### Post by glitchcamp on 2010-01-25
i got the python script to install and dl music fine.  great program.  made few changes to the setup tho.  i think it needs to be changed cause i havent configured my python path settings correctly. assuming you have python installed, from your terminal, with the python file in the working directory, run:

 **$ sudo python dl-myspace-music.py -install**

then to dl an artist page( [http://www.myspace.com/edit](http://www.myspace.com/edit) )

 **$ python dl-myspace-music.py edit**

hope this helps!

---

### Post by valy_el_rumano on 2010-02-02
> **timehAndGod said:**
> Well I tried my hand at making a GUI. It's my first time GUI programming, so there might be bugs.

It should install the dependencies by default, except for rtmpdump, which you can either compile and install yourself, or type this into a terminal after installing the deb package:
```
sudo dlmsm -rtmpdump
```

Let me know what you think!

EDIT: Updated attachment and screenshot

[IMG]http://img130.yfrog.com/img130/7514/screenshot007j.png[/IMG]


it works great for me!!thank you!!

---

### Post by crack on 2010-02-14
GUI not working here, it installs and recognise the tracks but will not download them
it just says downloading track but nothing happens

haven't tried the terminal version yet

is it possible to grab the files from /tmp/ i tried but haven't found anything, maybe i'm missing something :)

---

### Post by brustschwein on 2010-02-18
works fine. Thank you :D

---

### Post by StaticIp on 2010-02-22
You sir are amazing.

---

### Post by sinofemp on 2010-03-09
thank you, for the gui

---

### Post by jamesgthang on 2010-03-23
> **timehAndGod said:**
> I have made a Python script that will download and convert MySpace music. I have attached it to this post, and remember to make it executable before using it! Here is a quick usage guide:

To install all requirements:
```
sudo ./dl_myspace_music.py -install
```To download the music from [http://www.myspace.com/atlantafall](http://www.myspace.com/atlantafall) and [http://www.myspace.com/tokyokeys](http://www.myspace.com/tokyokeys) :
```
./dl_myspace_music.py atlantafall tokyokeys
```Enjoy! I'm not sure how long before MySpace do things differently, but it works as of now.

EDIT: Here is a pastie.org of the code: [http://pastie.org/786253](http://pastie.org/786253)



Dude, you are a GOD!!  This works like a charm.  I'll have to check out the GUI version.  Pretty soon I won't need Google any more, searching ubuntuforums will be enough.  THANKS.

---

### Post by sasagundul on 2010-03-23
thanks dude ! great program ! the GUI version works fine here after compiling rtmpdump.


could you make the progress bar moving? so i know how much the file
has been downloaded. 

anyway great program.

ps: sorry for my bad english

---

### Post by Spadefinger on 2010-03-27
> **timehAndGod said:**
> Well I tried my hand at making a GUI. It's my first time GUI programming, so there might be bugs.

It should install the dependencies by default, except for rtmpdump, which you can either compile and install yourself, or type this into a terminal after installing the deb package:
```
sudo dlmsm -rtmpdump
```

Let me know what you think!


Awesome. Thanks.

---

### Post by drduck on 2010-03-28
it works fine for me

---

### Post by corwinspyre on 2010-04-01
Great tool, thanks!  In case someone else has the problem, if you run moblock, you'll need to stop it first.

---

### Post by repllccax on 2010-04-13
Tool of **timehAndGod** works perfectly![U]

thanQ :KS
[/U]

---

### Post by Maciej Lenn on 2010-05-16
Amazing! Works fine under Ludic Lynx without any additional work than installing package provided by you, timehAndGod :) Pretty useful GUI! Sb should add it to repo and ubu soft center :popcorn:

---

### Post by archubu on 2010-05-16
**timehAndGod**'s program doesn't work?

I can't download MySpace Musics with this program:

[http://georgia.ubuntuforums.org/attachment.php?attachmentid=144605&d=1264219867](http://georgia.ubuntuforums.org/attachment.php?attachmentid=144605&d=1264219867)

---

### Post by timehAndGod on 2010-05-17
> **archubu said:**
> **timehAndGod**'s program doesn't work?

I can't download MySpace Musics with this program:

[http://georgia.ubuntuforums.org/attachment.php?attachmentid=144605&d=1264219867](http://georgia.ubuntuforums.org/attachment.php?attachmentid=144605&d=1264219867)

Did you read this? [http://ubuntuforums.org/showpost.php?p=8709562&postcount=13](http://ubuntuforums.org/showpost.php?p=8709562&postcount=13)

---

### Post by NoElemental on 2010-05-26
I can't Install the GUI , it shows :

Error: Dependency is not satisfiable : python

Any help? T_T

BTW i can use the terminal way, so no rush here

---

### Post by cluelessDoc on 2010-05-27
> **NoElemental said:**
> I can't Install the GUI , it shows :

Error: Dependency is not satisfiable : python

Any help? T_T

BTW i can use the terminal way, so no rush here
Install python, silly.
```
sudo apt-get install python
```

---

### Post by /bee/ on 2010-06-06
Just wanted to leave a quick thank you for this.  It still does the trick.

@glitchcamp: I had to do the same.

---

### Post by commodianus on 2010-06-11
> **timehAndGod said:**
> I have made a Python script that will download and convert MySpace music. I have attached it to this post, and remember to make it executable before using it! Here is a quick usage guide:

To install all requirements:
```
sudo ./dl_myspace_music.py -install
```To download the music from [http://www.myspace.com/atlantafall](http://www.myspace.com/atlantafall) and [http://www.myspace.com/tokyokeys](http://www.myspace.com/tokyokeys) :
```
./dl_myspace_music.py atlantafall tokyokeys
```Enjoy! I'm not sure how long before MySpace do things differently, but it works as of now.

EDIT: Here is a pastie.org of the code: [http://pastie.org/786253](http://pastie.org/786253)

This script is a total pimp move. Note: as of 6/11/2010 still works on myspace (Ubuntu 10.04/Lucid) here.

---

### Post by seguidor777 on 2010-06-13
dlmsm works well, but i can only get 1:30 mins (1.1 Mb) of each song, can anyone tell me why? Thank's

---

### Post by elvios on 2010-06-18
Worked for me. Easy as pie.

Thanks a bunch. ;)

---

### Post by angelotti on 2010-06-20
> **timehAndGod said:**
> Well I tried my hand at making a GUI. It's my first time GUI programming, so there might be bugs.

It should install the dependencies by default, except for rtmpdump, which you can either compile and install yourself, or type this into a terminal after installing the deb package:
```
sudo dlmsm -rtmpdump
```Let me know what you think!

EDIT: Updated attachment and screenshot

[IMG]http://img130.yfrog.com/img130/7514/screenshot007j.png[/IMG]

It works perfect at me. Although, I had to install first  rtmpdump as you say.
Thanks a lot!

---

### Post by R2D2! on 2010-06-22
It actually works, as of 2010-06-22!!

There are some minor problems:
[LIST=1]
[*]The GUI only works (for me) if run from a terminal.
[*]Converted MP3 are low quality (96kbps). But I don't know if that's related to the original songs.
[/LIST]

—Ilhu&#305;temoc

---

### Post by fooey on 2010-06-23
yep works great. thanks man [IMG]http://www.acurazine.com/forums/images/smilies/thumbsup.gif[/IMG]

---

### Post by s1mple_M4N on 2010-06-25
found this through OMG! Ubuntu - it works! Thanks.

---

### Post by oreyoyo on 2010-07-12
Thanks for this great tool.
It doesn't work for me: it founds the list of the songs on the Myspace account, says it downloads it but there are no downloaded files in the destination folder.
Konsole log:
"mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Seek failed
^CTraceback (most recent call last):
  File "/usr/bin/dlmsm", line 74, in <module>
    dlmsm.start()
  File "/usr/bin/dlmsm", line 41, in start
    self.gui.show()
  File "/usr/share/dlmsm/dlmsmgui.py", line 23, in show
    gtk.main()"
Any idea?
Thanks in advance!

---

### Post by oreyoyo on 2010-07-13
Could someone confirm that dlmsm still works today?
Thanks,
AML

---

### Post by oreyoyo on 2010-07-13
Sorry, I've just tried today again Download MySpace MP3 with a faster Internet connection and it worked perfectly! I think my normal connection was too slow for the program...

---

### Post by oreyoyo on 2010-07-13
Many thanks to TimeAndGod for this awesome tool!!!

---

### Post by zweiundzwei on 2010-07-13
That rtmpdump.mplayerhq.hu website seems to be down, does anyone know where I can get rtmpdump instead?

---

### Post by Steppdeckenwolf on 2010-08-04
timehAndGod, just wanna drop my thanks for the program, it works like charms here! merci

---

### Post by bodyinflight on 2010-08-17
I just noticed that MySpace seems to replace slashes by underscores. So if you want to download a song that has a slash in the title, you will get an error, saying the file was not found.

```
File not found: '.../....flv'
Failed to open .../....flv.
Done.
```


I added one line after line 138 to make it work (in the first given file, post #5) :
```

137    print "Downloading", track.title + "..."
138    track.title = track.title.replace('/','_')
139    Popen(...

```
(replaces all slashes by underscores in the track title)

Not very clean, but I didn't want to read the code :p


By the way, thanks a lot for this fantastic script !

---

### Post by firejdl on 2010-08-23
> **timehAndGod said:**
> Well I tried my hand at making a GUI. It's my first time GUI programming, so there might be bugs.

It should install the dependencies by default, except for rtmpdump, which you can either compile and install yourself, or type this into a terminal after installing the deb package:
```
sudo dlmsm -rtmpdump
```

Let me know what you think!

EDIT: Updated attachment and screenshot

[IMG]http://img130.yfrog.com/img130/7514/screenshot007j.png[/IMG]

First, let me say: thank you! I tried to download Myspace music with a number of programs, but none of them worked. Finally I found this thread and made an Ubuntu virtual machine just for this great little program. It works where everything else fails.

However, I had a small problem with installation:
```
$ tar zxvf dlmsm_0.1_all.deb.tar.gz 
dlmsm_0.1_all.deb

$ sudo dpkg -i dlmsm_0.1_all.deb 
Selecting previously deselected package dlmsm.
(Reading database ... 107612 files and directories currently installed.)
Unpacking dlmsm (from dlmsm_0.1_all.deb) ...
dpkg: dependency problems prevent configuration of dlmsm:
 dlmsm depends on mplayer (>= 2); however:
  Package mplayer is not installed.
dpkg: error processing dlmsm (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 dlmsm

```

After this, I tried manually installing mplayer via apt-get to get around the issue, but apt-get refused to resolve any dependencies until I removed this package - initially I thought it failed to install, but apparently it installed but was broken.

I removed dlmsm, installed mplayer with apt-get, installed dlmsm, and everything worked perfectly.

---

### Post by halurnam on 2010-09-06
I'm not into writing in forums (don't get me wrong, I help every newby I know; simply I don't like registering, even less in english, a language I speak too bad). But I registered in this one only to say:

[SIZE=5]THANKS

[SIZE=1]A python app with a gui that doesn't need fighting with it? In the 0.1 version? Man, you're great. :popcorn:[/SIZE]
[/SIZE]

---

### Post by afrodeity on 2010-09-12
Worked first time for me, but now it doesnt seem to load tracks anymore. Has myspace changed something?

---

### Post by MockY on 2010-09-18
I just installed MMD 0.1 successfully, and the app does run, but it does not fetch any songs from any account. So I wonder, as others do as well; Did Myspace change anything or does it not work on 10.04?

---

### Post by R2D2! on 2010-09-19
> **MockY said:**
> I just installed MMD 0.1 successfully, and the app does run, but it does not fetch any songs from any account. So I wonder, as others do as well; Did Myspace change anything or does it not work on 10.04?

I've confirmed that it works. I'm running Myspace Music Downloader 0.1 in Ubuntu 10.10 Beta.

So I don't know if it doesn't work on Lucid, or it's just you.

---

### Post by beew on 2010-09-22
I just downloaded and install this, looks like a great app (thanks TimeAndGod for the good work). However, it seems that the program only downloaded the begining of a song and declared that download has finished. I wonder if anyone else encounters the same problem and knows of a work around. Thanks.

---

### Post by jbrid on 2010-10-03
This doesn't work for me. It would be a great tool if it worked.

It loads the tracks, but when it starts downloading it just hangs. It never downloads anything.

This is MMD 0.1 on Xubuntu 10.04

$ uname -a
Linux ------- 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Does anyone have a fix for this problem? Or another solution?

Thanks.

---

### Post by jbrid on 2010-10-04
> **jbrid said:**
> This doesn't work for me. It would be a great tool if it worked.

It loads the tracks, but when it starts downloading it just hangs. It never downloads anything.

This is MMD 0.1 on Xubuntu 10.04

$ uname -a
Linux ------- 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Does anyone have a fix for this problem? Or another solution?

Thanks.

I just got it working on Kubuntu 10.10 beta. I am not sure exactly why it didn't work on my other machine, but I may have missed asomething. 

Anyway...it does work.

---

### Post by beew on 2010-10-21
I appears that it only works when you have an unencrypted internet connection. I haven't been testing this hypothesis very carefully though.

---

### Post by Symbioosi on 2010-10-29
> **jbrid said:**
> This doesn't work for me. ... This is MMD 0.1 on Xubuntu 10.04


Hi,

just registered in order to get this program. Why is the registering required? Anyway, nice to post here first time after six years of ubuntu-usage.

This works fine with my Ubuntu 10.04. Did you install rtmpdump also, as required?
```

sudo dlmsm -rtmpdump

```

---

### Post by flk2 on 2010-10-30
> **beew said:**
> I just downloaded and install this, looks like a great app (thanks TimeAndGod for the good work). However, it seems that the program only downloaded the begining of a song and declared that download has finished. I wonder if anyone else encounters the same problem and knows of a work around. Thanks.


I modified the original script.

When rtmpdump doesn't finish correctly, it has to resume the download. It works fine for me.

My modified file is attached.

---

### Post by Symbioosi on 2010-11-01
> **flk2 said:**
> I modified the original script.

When rtmpdump doesn't finish correctly, it has to resume the download. It works fine for me.

My modified file is attached.

I'm having similar problems, doesn't always finish tracks.

I'm using the gui version.

Is it possible to use this modified file with that? What do I have to do?

---

### Post by flk2 on 2010-11-05
> **Symbioosi said:**
> I'm having similar problems, doesn't always finish tracks.

I'm using the gui version.

Is it possible to use this modified file with that? What do I have to do?


For the GUI version:

1.  Replace the file: /usr/share/dlmsm/dlmsmapp.py with the modified file (dlmsmapp.py) that is attached.
2. Remove the file /usr/share/dlmsm/dlmsmapp.pyc

That's all.

---

### Post by n~kf)}BW% on 2010-11-06
Here is a working Linux shell script to download MySpace music, for real geeks only!
Tested in Ubuntu :popcorn:
[http://360percents.com/posts/linux-myspace-music-downloader/](http://360percents.com/posts/linux-myspace-music-downloader/)

---

### Post by mung23 on 2010-11-07
i'm using the command line version on arch linux, so i have to modify the script anyway...  
 
 with python2 it runs just fine, but with python3 you will get syntax errors :-/
 
 for those who have problem with incomplete files:
 replacing
 ```

Popen( [ RTMPDUMP_PATH, "-r", "rtmpe://" + track.getRtmpUrl(), "-o", track.title + ".flv" ], stdout = PIPE ).communicate()

``` by
 ```
Popen( [ RTMPDUMP_PATH, "-r", "rtmpe://" + track.getRtmpUrl(), "-o", track.title + ".flv", "-W", "http://lads.myspacecdn.com/videos/MSMusicPlayer.swf" ], stdout = PIPE ).communicate()
 
```helped for me :-)
 
rtmpdump –help
--swfVfy|-W url         URL to player swf file, compute hash/size automatically

---

### Post by 3esmit on 2010-11-11
Thank you for the application! 
It seems to works perfect in ubuntu 10.10 32bits, using this tutorial [http://www.omgubuntu.co.uk/2010/06/easy-myspace-music-download-application/](http://www.omgubuntu.co.uk/2010/06/easy-myspace-music-download-application/)
but it just download a part of the music.

---

### Post by 3esmit on 2010-11-11
Hello,

I tryed but couldnt not make this in python, first touch was in your app.

Can you please, do the following: 

in dlmsmapp.py
in class App_Thread_DownloadTracks( App_Thread )
	at def run( self ):

Line 143, where you open the first process... 
get the readlines of this process, and check if it returened the following: """Download complete"""
if not it would appear """Download may be incomplete"""
and then you must send the command to rtmpdump with the -e option!
This option resumes the download, so you can get full files... you need to do this until you get """Download complete"""

Your program fails downloading music due this detail.
Hope soon I learn python to do myself the contribution (:

Hey, you got github for this project?

Yours,
Ricardo Schmidt.

---

### Post by beew on 2010-11-13
Thanks flk2! I have tried your fixed version on several installations, it works brilliantly!

---

### Post by m3n3chm0 on 2010-11-15
NICE WORK !!!!! thank you so much ):P

---

### Post by afrodeity on 2010-11-21
> Here is a working Linux shell script to download MySpace music, for real geeks only!
Tested in Ubuntu
[http://360percents.com/posts/linux-m...ic-downloader/](http://360percents.com/posts/linux-m...ic-downloader/)

I get this error
```

/usr/bin/getmusic.sh: line 9: syntax error near unexpected token `;&'
/usr/bin/getmusic.sh: line 9: `type -P rtmpdump &amp;&gt;/dev/null || {'

```

---

### Post by dentaku65 on 2010-11-21
Hi,
the script works fine, but often I get this message:

```
./dl-myspace-music.py <band_name>
```

```
Profile <band_name> is not a band profile.
```

Where <band_name> is the name of the myspace profile of the band :-k

---

### Post by beew on 2010-11-24
I am using flk2's modified version of the original script, for the most part it works beautifully, but sometimes it would get stuck and python would be using 100% cpu. Closing the app doesn't stop python and I have to kill it from the terminal. I am wondering if there is a small bug in the script. 

Thanks.

---

### Post by slaminallaeraew on 2010-12-29
Hi, new forum member here (just now made my account), and new Linux user (switched from Windows last week).

I downloaded and installed this MySpace Music Downloader, and it seemed to work great. I opened it, typed in the Profile ID, and it displayed the songs that I was searching for quickly and flawlessly, exactly as they appear on the MySpace ([www.myspace.com/fffke](www.myspace.com/fffke) it is my own music, check it out if you want).

However, the problem occurred when I clicked Download to download the songs themselves. I went searching for the files and could not find them. I went to Edit>Preferences to see where the files were supposed to download to (which was my /home/user folder). I changed that to /home/user/downloads; I figured they would be easy to find since that folder is empty. I clicked Download again, but this time I had the /home/user/downloads folder open as the downloads happened.

As soon as I clicked Download, I saw the file that was named according to the first song appeared in the /home/user/downloads folder, so it seemed as if things were working fine. However, as soon as the second song began to download, the first song's file disappeared, and the file for the second song replaced it. As soon as the second song finished downloading, its file disappeared as well. Since there were only two songs to download, nothing replaced the second file; I was left with an empty /home/user/download folder. Several repetitions yielded identical results.

---

### Post by afrodeity on 2010-12-29
Same here. Big mystery. Nobody knows.

---

### Post by slaminallaeraew on 2010-12-29
Hm? So is this a common problem, then? And have people been working on solutions for it? Are there people who do not encounter this problem?

---

### Post by fjcurcio on 2011-01-01
I'm having the same problem. files are downloaded as .flv (?), overwritten and then gone.
used to work flawlessly.

---

### Post by Kreuger on 2011-01-23
I get an mplayer related error when I run it from the terminal
> 
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Seek failed


---

### Post by slaminallaeraew on 2011-01-24
> **Kreuger said:**
> I get an mplayer related error when I run it from the terminal

I get the exact same error. It occurs multiple times in sequence, once for every attempted song download.

---

### Post by k.online.now on 2011-02-01
> **slaminallaeraew said:**
> I get the exact same error. It occurs multiple times in sequence, once for every attempted song download.

 me too .. i almost gave up but then , on page 7 of this topic i found slovenia 's shell
script and it worked like charm.. i just downloaded the script made it executable , downloaded rtmpdump and flvstreamer from the synaptic.(flv streamer is probably not needed,but just in case). rebooted the computer and open the terminal and cd into the directory where i had save the script and ran /bin/bash [http://in.myspace.com/thescavengerproject](http://in.myspace.com/thescavengerproject) (the http part is the url of the artist you want to download)  and it downloaded all the songs present on that page. you may want to try it .
   thak you slovenia..:guitar:

---

### Post by hiko-seijuro on 2011-02-06
Hi,

I have modified the script. I've had the same error with mplay and I've found that it was because rtmpdump doesn't download the flv file. I modified this line:

```
    Popen( [ RTMPDUMP_PATH,  "-r", "rtmpe://" + track.getRtmpUrl(), "-o", track.title + ".flv", stdout = PIPE ).communicate()
```

with

```
    Popen( [ RTMPDUMP_PATH,  "-r", "rtmpe://" + track.getRtmpUrl(), "-o", track.title + ".flv", "--swfVfy", "http://lads.myspacecdn.com/videos/MSMusicPlayer.swf"], stdout = PIPE ).communicate()
```

and now it works

---

### Post by Symbioosi on 2011-02-06
Slovenia's script (getmusic.sh) works!

[http://360percents.com/posts/linux-myspace-music-downloader/](http://360percents.com/posts/linux-myspace-music-downloader/)

---

### Post by slaminallaeraew on 2011-02-09
> **k.online.now said:**
> me too .. i almost gave up but then , on page 7 of this topic i found slovenia 's shell
script and it worked like charm.. i just downloaded the script made it executable , downloaded rtmpdump and flvstreamer from the synaptic.(flv streamer is probably not needed,but just in case). rebooted the computer and open the terminal and cd into the directory where i had save the script and ran /bin/bash [http://in.myspace.com/thescavengerproject](http://in.myspace.com/thescavengerproject) (the http part is the url of the artist you want to download)  and it downloaded all the songs present on that page. you may want to try it .
   thak you slovenia..:guitar:

Thank you, these steps worked very well. The only difference is that, once I cd into the folder with the getmusic.sh script, I use the terminal command ./getmusic.sh {URL here} rather than /bin/bash {URL here} as you said.
Apparently, the song files are supposed to be saved as MP3 rather than .flv, or is that only with the ffmpeg package installed? It is not a big deal to me since, surprisingly, .flv works in Rhythmbox, which is good news to me.
There is only one question remaining, and it relates to Rhythmbox. After I had downloaded the song files I wanted from MySpace, I moved them into the /home/username/Music folder and into the appropriate folders corresponding to artist names and then album titles, then imported them to Rhythmbox. In Rhythmbox, the song titles are listed as the file names, and the fields for artist name, album title, etc. are listed as Unknown. If I try to change any of these, I am able to select and highlight, but the words cannot even be erased or changed in any way. Is there any fix to that? I know that it is not related to the functionality of the getmusic script that we are discussing, but I would like to know anyway, if y'all know.
Oh, and is there no hope for the MySpace Music Downloader that we were originally discussing? I liked the fact that I could preview and select/deselect the songs before I chose to download, so is there any way to incorporate those sorts of options into the getmusic script, or perhaps just figure out how to get the MySpace Music Downloader to work?

---

### Post by sivliopelvico on 2011-02-16
Hi, forme don't work? This is the output. What can i do?

Downloading 4 tracks
Downloading  r menn d mamt...
RTMPDump v2.1c
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, use --swfVfy!
ERROR: rtmp server sent error
ERROR: rtmp server requested close

Converting  r menn d mamt...
mplayer: could not open config files /home/sord/.lircrc and /etc/lirc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.
Seek failed
Done.

---

### Post by Avabuntu on 2011-03-09
):P thanks for the GUI

---

### Post by fjcurcio on 2011-03-13
Avabuntu-
which GUI are you referring to?

and has anyone figured out how to get the MySpace Music Downloader working again?

---

### Post by qopi on 2011-05-12
> **fjcurcio said:**
> Avabuntu-
which GUI are you referring to?

and has anyone figured out how to get the MySpace Music Downloader working again?

[http://360percents.com/posts/myspace-music-downloader-for-linux-with-gui/]("http://360percents.com/posts/myspace-music-downloader-for-linux-with-gui/")

---

### Post by n~kf)}BW% on 2011-11-30
Hello again,

this is the author of:

[http://360percents.com/posts/myspace-music-downloader-for-linux-with-gui/](http://360percents.com/posts/myspace-music-downloader-for-linux-with-gui/)

and

[http://360percents.com/posts/linux-myspace-music-downloader/](http://360percents.com/posts/linux-myspace-music-downloader/)

I would like to know if my scripts still work and I would be really happy to see somebody help me improve them. The projects are now on github :) Fork them!:popcorn:

[https://github.com/lukapusic](https://github.com/lukapusic)

---

### Post by kotek on 2012-03-28
None of them work... myspace-dl.sh gets the artist ID and seems to get the songs, but finally nothing happens (no error messages, but no files appear!). GUI version can't find any tracks.

---

### Post by eldafani on 2012-06-14
Hello,

I tried this [http://www.omgubuntu.co.uk/2010/06/easy-myspace-music-download-application](http://www.omgubuntu.co.uk/2010/06/easy-myspace-music-download-application)

but it did not work. I enter the ID, click on loading tracks, but it  fails and does not list any songs. I am using Linux Mint 13 Maya. What  could be happening?

---

### Post by moisesber on 2012-07-03
> **slovenia said:**
> Hello again,

this is the author of:

[http://360percents.com/posts/myspace-music-downloader-for-linux-with-gui/](http://360percents.com/posts/myspace-music-downloader-for-linux-with-gui/)

and

[http://360percents.com/posts/linux-myspace-music-downloader/](http://360percents.com/posts/linux-myspace-music-downloader/)

I would like to know if my scripts still work and I would be really happy to see somebody help me improve them. The projects are now on github :) Fork them!:popcorn:

[https://github.com/lukapusic](https://github.com/lukapusic)

Actually, the GUI version seems to work pretty well, without any error but nothing is really downloaded. The list of songs is ok and the total of songs too but nothing is really downloaded.
Using Ubuntu 12.04 LTS here.
Despite that, thanks for the great work man.

---

### Post by lovo on 2012-08-12
Yes same for me. All flv files are created but they are empty then for the mp3 convertion it fails and no mp3 created.

---

