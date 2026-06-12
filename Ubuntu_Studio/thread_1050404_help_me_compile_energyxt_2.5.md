---
title: "help me compile energyxt 2.5"
date: 2009-01-25
forum: Ubuntu Studio
---

### Post by neu2buntu on 2009-01-25
i am trying to install the demo of energyXT 2.5 from here [http://www.energy-xt.com/index.php?id=0200 ]("http://www.energy-xt.com/index.php?id=0200")
it needs jack to run and i have jack installed fully(working with all my other apps) 

there is a file that needs compiling for it jack.cpp and that is where i am having the problem. here are the instructions in the jack.cpp file ```
// compile: g++ -shared -lasound -ljack jack.cpp -o /_path_to_energyXT2_/libaam.so
```i have all the files unpacked to /opt including jack.cpp , heres what i have tried

```
ubu@ntu:~$ cd /opt
ubu@ntu:/opt$ ls
energyxt
ubu@ntu:/opt$ cd energyxt
ubu@ntu:/opt/energyxt$ ls
clips  energyXT2  eula.txt  jack.cpp  libaam.so  presets  projects
ubu@ntu:/opt/energyxt$ sudo g++ -shared -lasound -ljack jack.cpp -o /opt/energyxt/libaam.so
[sudo] password for ubu: 
ubu@ntu:/opt/energyxt$ energyXT2
bash: energyXT2: command not found
ubu@ntu:/opt/energyxt$ ./energyXT2
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  380
  Current serial number in output stream:  382
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x3c000a4
  Serial number of failed request:  381
  Current serial number in output stream:  382
ubu@ntu:/opt/energyxt$ 


```       can anyone tell me where i am going wrong,am i installing in wrong directory or does jack.cpp have to be placed elsewhere ,or am i running the wrong command to start program?     sorry about long post and thanks for looking:(

---

### Post by neu2buntu on 2009-01-25
```
bump
```   1st ever bump..lol.... surely someone out there can help me?:D

---

### Post by neu2buntu on 2009-01-25
i have no patience...lol...

---

### Post by Stochastic on 2009-01-25
Bumps deleted.  Please don't bump so often in this section of the forums, there isn't that much traffic here.  Only after a post has left the front page of the forum should a bump be needed.

---

### Post by neu2buntu on 2009-01-27
(SOLVED) by extracting all files to my home directory instead of /opt and the path i used was sudo g++ -shared -lasound -ljack jack.cpp -o /usr/local/bin/libaam.so  to compile the libaam.so file.    so now it works under jack!!! happy days... oh and also edit my /etc/X11/xorg.conf file and added code
```
Section "Extensions"
        Option "MIT-SHM" "no" 
EndSection
```    rebooted and did the g++ code above      !!!

---

### Post by bebox on 2009-06-11
when i whant to compile i get this error:

> bebox@bebox-laptop:~/Desktop/energyXT$ sudo g++ -shared -lasound -ljack jack.cpp -o /home/bebox/Desktop/energyXT/libaam.so
[sudo] password for bebox: 
jack.cpp:5:28: error: alsa/asoundlib.h: No such file or directory
jack.cpp:6:23: error: jack/jack.h: No such file or directory
jack.cpp:46: error: ‘pthread_t’ does not name a type
jack.cpp: In destructor ‘CThread::~CThread()’:
jack.cpp:62: error: ‘handle’ was not declared in this scope
jack.cpp:62: error: ‘pthread_join’ was not declared in this scope
jack.cpp: In member function ‘void CThread::start()’:
jack.cpp:74: error: ‘handle’ was not declared in this scope
jack.cpp:74: error: ‘pthread_create’ was not declared in this scope
jack.cpp: At global scope:
jack.cpp:88: error: ISO C++ forbids declaration of ‘snd_rawmidi_t’ with no type
jack.cpp:88: error: expected ‘;’ before ‘*’ token
jack.cpp:105: error: ISO C++ forbids declaration of ‘jack_port_t’ with no type
jack.cpp:105: error: expected ‘;’ before ‘*’ token
jack.cpp:109: error: expected constructor, destructor, or type conversion before ‘*’ token
jack.cpp:119: error: ISO C++ forbids declaration of ‘snd_rawmidi_t’ with no type
jack.cpp:119: error: expected ‘;’ before ‘*’ token
jack.cpp:138: error: expected constructor, destructor, or type conversion before ‘*’ token
jack.cpp:141: error: ‘jack_nframes_t’ was not declared in this scope
jack.cpp:141: error: expected primary-expression before ‘void’
jack.cpp:141: error: initializer expression list treated as compound expression
jack.cpp:142: error: expected ‘,’ or ‘;’ before ‘{’ token

---

### Post by bebox on 2009-06-11
when i whant to compile i get this error:

```
bebox@bebox-laptop:~/Desktop/energyXT$ sudo g++ -shared -lasound -ljack jack.cpp -o /home/bebox/Desktop/energyXT/libaam.so
[sudo] password for bebox: 
jack.cpp:5:28: error: alsa/asoundlib.h: No such file or directory
jack.cpp:6:23: error: jack/jack.h: No such file or directory
jack.cpp:46: error: ‘pthread_t’ does not name a type
jack.cpp: In destructor ‘CThread::~CThread()’:
jack.cpp:62: error: ‘handle’ was not declared in this scope
jack.cpp:62: error: ‘pthread_join’ was not declared in this scope
jack.cpp: In member function ‘void CThread::start()’:
jack.cpp:74: error: ‘handle’ was not declared in this scope
jack.cpp:74: error: ‘pthread_create’ was not declared in this scope
jack.cpp: At global scope:
jack.cpp:88: error: ISO C++ forbids declaration of ‘snd_rawmidi_t’ with no type
jack.cpp:88: error: expected ‘;’ before ‘*’ token
jack.cpp:105: error: ISO C++ forbids declaration of ‘jack_port_t’ with no type
jack.cpp:105: error: expected ‘;’ before ‘*’ token
jack.cpp:109: error: expected constructor, destructor, or type conversion before ‘*’ token
jack.cpp:119: error: ISO C++ forbids declaration of ‘snd_rawmidi_t’ with no type
jack.cpp:119: error: expected ‘;’ before ‘*’ token
jack.cpp:138: error: expected constructor, destructor, or type conversion before ‘*’ token
jack.cpp:141: error: ‘jack_nframes_t’ was not declared in this scope
jack.cpp:141: error: expected primary-expression before ‘void’
jack.cpp:141: error: initializer expression list treated as compound expression
jack.cpp:142: error: expected ‘,’ or ‘;’ before ‘{’ token
```

---

### Post by bebox on 2009-06-11
can anybody help?

---

### Post by thorgal on 2009-06-11
```

sudo apt-get install libjack-dev

```

then you can try to compile your stuff.

---

### Post by bebox on 2009-06-11
thorgal thank you for the reply...

now i get even more errors:

```
bebox@bebox-laptop:~/Desktop/energyXT$ sudo g++ -shared -lasound -ljack jack.cpp -o /home/bebox/Desktop/energyXT/libaam.so
jack.cpp:5:28: error: alsa/asoundlib.h: No such file or directory
jack.cpp:88: error: ISO C++ forbids declaration of ‘snd_rawmidi_t’ with no type
jack.cpp:88: error: expected ‘;’ before ‘*’ token
jack.cpp:119: error: ISO C++ forbids declaration of ‘snd_rawmidi_t’ with no type
jack.cpp:119: error: expected ‘;’ before ‘*’ token
jack.cpp: In function ‘void openJack()’:
jack.cpp:234: error: ‘printf’ was not declared in this scope
jack.cpp:250: error: ‘strcpy’ was not declared in this scope
jack.cpp:258: error: ‘sprintf’ was not declared in this scope
jack.cpp:272: error: ‘free’ was not declared in this scope
jack.cpp:281: error: ‘strcpy’ was not declared in this scope
jack.cpp:289: error: ‘sprintf’ was not declared in this scope
jack.cpp: In function ‘void init()’:
jack.cpp:348: error: ‘snd_ctl_t’ was not declared in this scope
jack.cpp:348: error: ‘ctl’ was not declared in this scope
jack.cpp:349: error: ‘snd_ctl_card_info_t’ was not declared in this scope
jack.cpp:349: error: ‘cardInfo’ was not declared in this scope
jack.cpp:350: error: ‘snd_rawmidi_info_t’ was not declared in this scope
jack.cpp:350: error: ‘rawmidiInfo’ was not declared in this scope
jack.cpp:352: error: ‘snd_ctl_card_info_alloca’ was not declared in this scope
jack.cpp:353: error: ‘snd_rawmidi_info_alloca’ was not declared in this scope
jack.cpp:356: error: ‘snd_card_next’ was not declared in this scope
jack.cpp:360: error: ‘sprintf’ was not declared in this scope
jack.cpp:362: error: ‘snd_ctl_open’ was not declared in this scope
jack.cpp:366: error: ‘snd_ctl_card_info’ was not declared in this scope
jack.cpp:372: error: ‘snd_ctl_rawmidi_next_device’ was not declared in this scope
jack.cpp:375: error: ‘snd_rawmidi_info_set_device’ was not declared in this scope
jack.cpp:376: error: ‘snd_rawmidi_info_set_subdevice’ was not declared in this scope
jack.cpp:379: error: ‘SND_RAWMIDI_STREAM_INPUT’ was not declared in this scope
jack.cpp:379: error: ‘snd_rawmidi_info_set_stream’ was not declared in this scope
jack.cpp:380: error: ‘snd_ctl_rawmidi_info’ was not declared in this scope
jack.cpp:392: error: ‘strcpy’ was not declared in this scope
jack.cpp:393: error: ‘snd_ctl_card_info_get_name’ was not declared in this scope
jack.cpp:397: error: ‘snd_ctl_close’ was not declared in this scope
jack.cpp: In function ‘int libaam(int, int, int)’:
jack.cpp:443: error: ‘strcpy’ was not declared in this scope
jack.cpp: In constructor ‘CMIDIDev::CMIDIDev()’:
jack.cpp:553: error: ‘handle’ was not declared in this scope
jack.cpp: In member function ‘void CMIDIDev::enable(int)’:
jack.cpp:576: error: ‘handle’ was not declared in this scope
jack.cpp:576: error: ‘SND_RAWMIDI_NONBLOCK’ was not declared in this scope
jack.cpp:576: error: ‘snd_rawmidi_open’ was not declared in this scope
jack.cpp:577: error: ‘printf’ was not declared in this scope
jack.cpp:593: error: ‘handle’ was not declared in this scope
jack.cpp:595: error: ‘snd_rawmidi_close’ was not declared in this scope
jack.cpp: In constructor ‘CMIDIThread::CMIDIThread(int, int)’:
jack.cpp:608: error: ‘snd_rawmidi_t’ was not declared in this scope
jack.cpp:608: error: expected primary-expression before ‘)’ token
jack.cpp:608: error: expected `;' before ‘f’
jack.cpp: In member function ‘virtual void CMIDIThread::execute()’:
jack.cpp:663: error: ‘snd_rawmidi_read’ was not declared in this scope
jack.cpp:665: error: ‘usleep’ was not declared in this scope
```

---

### Post by bebox on 2009-06-11
o...i had to install libasound2-dev...

i only get those now:
```

bebox@bebox-laptop:~/Desktop/energyXT$ sudo g++ -shared -lasound -ljack jack.cpp -o /home/bebox/Desktop/energyXT/libaam.so
jack.cpp: In member function ‘void CMIDIDev::enable(int)’:
jack.cpp:578: error: cast from ‘snd_rawmidi_t*’ to ‘int’ loses precision
```

---

### Post by thorgal on 2009-06-11
what is the ALSA version you are compiling against ?
when was the energyXT jack extension coded ?

looks like some version incompatibility.

By the way, it's not a good idea to compile something as root in your home directory or subdirectory.
sudo should only be used when installing to or modifying from a system location.

---

### Post by thorgal on 2009-06-11
I looked at the code in jack.cpp

There's a type cast that is potentially dangerous due to precision loss. If you are not into programming, it is a bit tough to explain but you can have nasty effect from blindly casting a pointer to "int" and back to pointer.  Are you on 32 or 64bit (but the nasty side effect could be in both) ?

The compiler is right to fail the compilation. The code needs some cleaning.

---

### Post by bebox on 2009-06-11
thanks thorgal...

i read on a forum ([http://www.kvraudio.com/forum/printview.php?t=220651&start=0](http://www.kvraudio.com/forum/printview.php?t=220651&start=0)) that i have to inlude this otion "-m32" because my system is 64 bit.

this is what i get now:

```

bebox@bebox-laptop:~/Desktop/energyXT$ g++ -shared -lasound -ljack -m32 jack.cpp -o /home/bebox/Desktop/energyXT/libaam.so
In file included from /usr/include/features.h:354,
                 from /usr/include/unistd.h:26,
                 from /usr/include/alsa/asoundlib.h:31,
                 from jack.cpp:5:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
```

---

### Post by bebox on 2009-06-11
i had to install libc6-dev-i386...
and now i get this:

```
bebox@bebox-laptop:~/Desktop/energyXT$ g++ -shared -lasound -ljack -m32 jack.cpp -o /home/bebox/Desktop/energyXT/libaam.so
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
```

---

### Post by thorgal on 2009-06-11
... you need someone knowledgeable in compiling 32bit stuff in 64bit systems. I only work with 32bits. You probably need some other 32bit lib (standard C++ lib).

---

### Post by bebox on 2009-06-11
i found it!!!!i finnaly found it!!!

i had to install "g++-multilib"!

---

### Post by liquidalien on 2009-07-06
I've a same looking problem, but no clue...

```
fabien@Athena:~/Bureau/energyXT$ g++ -shared -lasound -ljack jack.cpp -o libaam.so -m32
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libasound.so when searching for -lasound
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libasound.a when searching for -lasound
/usr/bin/ld: skipping incompatible /usr/lib/libasound.so when searching for -lasound
/usr/bin/ld: skipping incompatible /usr/lib/libasound.a when searching for -lasound
/usr/bin/ld: cannot find -lasound
collect2: ld a retourné 1 code d'état d'exécution
``` 

Does someone have an advice ?

Thanx

/Fabien

---

### Post by liquidalien on 2009-07-06
Ok, I've found the missing lib, and jack.cpp is compiled... But it doesn't work for audio, only for midi. Is this an issue with my 64 bits environment ?

---

### Post by neu2buntu on 2009-07-06
> **liquidalien said:**
> Ok, I've found the missing lib, and jack.cpp is compiled... But it doesn't work for audio, only for midi. Is this an issue with my 64 bits environment ?

im not sure about your "64 bit environment"  have you "jack" (qjackctl) up and running before starting energyXT2? and also look in >file >setup >audio >device and choose "jack audio" and also look at the "connections" in qjackctl to make sure energyXT is connected to system.

---

### Post by liquidalien on 2009-07-07
Yes, qjackctl/jackd (1.9.3) is started before. In File/Setup, Jack is the audio driver but no input or output appears. It seems it's a 32/64 bits incompatibility problem.

---

### Post by liquidalien on 2009-07-21
Just configure with the -mixed option before compiling jackd 1.9.3.

/Fabien

---

### Post by guhya on 2012-09-05
-----

---

