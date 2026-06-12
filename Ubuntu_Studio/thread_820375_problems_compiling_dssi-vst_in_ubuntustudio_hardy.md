---
title: "problems compiling dssi-vst in ubuntustudio hardy"
date: 2008-06-06
forum: Ubuntu Studio
---

### Post by fistuks on 2008-06-06
Hello,

I've downloaded the latest dssi-vst version 7 (i think)
Flowed the instructions from the readme file:

> To build dssi-vst, you will need:

* The DSSI header.

* Wine 0.9.5 or newer and its development tools -- [http://www.winehq.com/](http://www.winehq.com/)

* Steve Harris's liblo "Lite OSC" library -- [http://liblo.sf.net/](http://liblo.sf.net/) -- 
  version 0.9 or newer.

* OPTIONALLY the VST SDK headers.  The URL for downloading these seems
  to change every week, but at the time of writing it is:

     [http://www.steinberg.de/331+M54a708de802.html](http://www.steinberg.de/331+M54a708de802.html)

  These are free to download, but you need to agree to Steinberg's
  licensing terms and you may not redistribute them.  Unzip the SDK
  into the current directory (creating a subdirectory called vstsdk2.4).

  If you wish to use the official VST SDK, please edit the Makefile
  as directed in its comments.

Once you have all of the above, you should be able to build and
install by running "make" then "make install".

but the compiling process failed:
> fistuks@85:~/dssi-vst-0.7$ make
wineg++ -I./vstsdk2.4/pluginterfaces/vst2.x -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
In file included from /usr/include/features.h:354,
                 from /usr/include/c++/4.2/x86_64-linux-gnu/32/bits/os_defines.h:44,
                 from /usr/include/c++/4.2/x86_64-linux-gnu/32/bits/c++config.h:41,
                 from /usr/include/c++/4.2/iostream:44,
                 from dssi-vst-server.cpp:8:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
dssi-vst-server.cpp:26:21: error: windows.h: No such file or directory
dssi-vst-server.cpp:53: error: ‘HANDLE’ does not name a type
dssi-vst-server.cpp:55: error: ‘HWND’ does not name a type
dssi-vst-server.cpp: In destructor ‘virtual RemoteVSTServer::~RemoteVSTServer()’:
dssi-vst-server.cpp:245: error: ‘hWnd’ was not declared in this scope
dssi-vst-server.cpp:245: error: ‘SW_HIDE’ was not declared in this scope
dssi-vst-server.cpp:245: error: ‘ShowWindow’ was not declared in this scope
dssi-vst-server.cpp:246: error: ‘UpdateWindow’ was not declared in this scope
dssi-vst-server.cpp: In member function ‘virtual bool RemoteVSTServer::warn(std::string)’:
dssi-vst-server.cpp:501: error: ‘hWnd’ was not declared in this scope
dssi-vst-server.cpp:501: error: ‘MessageBox’ was not declared in this scope
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::showGUI(std::string)’:
dssi-vst-server.cpp:533: error: ‘hWnd’ was not declared in this scope
dssi-vst-server.cpp:545: error: ‘SWP_NOACTIVATE’ was not declared in this scope
dssi-vst-server.cpp:545: error: ‘SWP_NOMOVE’ was not declared in this scope
dssi-vst-server.cpp:546: error: ‘SWP_NOOWNERZORDER’ was not declared in this scope
dssi-vst-server.cpp:546: error: ‘SWP_NOZORDER’ was not declared in this scope
dssi-vst-server.cpp:546: error: ‘SetWindowPos’ was not declared in this scope
dssi-vst-server.cpp:552: error: ‘SW_SHOWNORMAL’ was not declared in this scope
dssi-vst-server.cpp:552: error: ‘ShowWindow’ was not declared in this scope
dssi-vst-server.cpp:553: error: ‘UpdateWindow’ was not declared in this scope
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:
dssi-vst-server.cpp:566: warning: unused variable ‘fd’
dssi-vst-server.cpp:571: error: ‘hWnd’ was not declared in this scope
dssi-vst-server.cpp:571: error: ‘SW_HIDE’ was not declared in this scope
dssi-vst-server.cpp:571: error: ‘ShowWindow’ was not declared in this scope
dssi-vst-server.cpp:572: error: ‘UpdateWindow’ was not declared in this scope
dssi-vst-server.cpp: In function ‘VstIntPtr hostCallback(AEffect*, VstInt32, VstInt32, VstIntPtr, void*, float)’:
dssi-vst-server.cpp:808: error: ‘hWnd’ was not declared in this scope
dssi-vst-server.cpp:812: error: ‘SWP_NOACTIVATE’ was not declared in this scope
dssi-vst-server.cpp:812: error: ‘SWP_NOMOVE’ was not declared in this scope
dssi-vst-server.cpp:813: error: ‘SWP_NOOWNERZORDER’ was not declared in this scope
dssi-vst-server.cpp:813: error: ‘SWP_NOZORDER’ was not declared in this scope
dssi-vst-server.cpp:813: error: ‘SetWindowPos’ was not declared in this scope
dssi-vst-server.cpp: At global scope:
dssi-vst-server.cpp:1031: error: ‘DWORD’ does not name a type
dssi-vst-server.cpp:1066: error: ‘DWORD’ does not name a type
dssi-vst-server.cpp:1115: error: ‘LRESULT’ does not name a type
dssi-vst-server.cpp:1129: error: expected initializer before ‘WinMain’
dssi-vst-server.cpp:59: warning: ‘alive’ defined but not used
winegcc: g++ failed
make: *** [dssi-vst-server.exe.so] Error 2


Help?

---

### Post by eric71 on 2008-06-06
I've never had much success compiling anything, so I can't give advice on that. I'll try to avoid it at all costs, which leads me to this suggestion:

Try downloading Rui Nuno Capela's (of QJackctl fame)SUSE rpm and converting it to deb with alien. I'm not near my linux laptop now or i'd test if it works. I've had luck with some of his packages before, though. You can find the rpm here:

[http://www.rncbc.org/jack/](http://www.rncbc.org/jack/)

---

### Post by fistuks on 2008-06-06
Thanks man.
But there is a problem, this rpm is for 32bit linux i'm using amd64, and when i try to convert the deb to rpm using alien it complains about incompatible host architecture...

---

### Post by Stochastic on 2008-06-06
You may be able to get the rpm installed via using 32-bit libraries, but I'm not sure the process for going about that.

For your original error, try doing ```
sudo apt-get install libpthread-stubs-0-dev
```
Though the "stubs-32.h" part of that error message may suggest that you need a 32-bit version.

---

### Post by thorgal on 2008-06-06
ah, you have a 64bit system ... I heard you cannot use VSTs on such systems ... is this correct ??

---

### Post by fistuks on 2008-06-06
On their site - 
[http://www.breakfastquay.com/dssi-vst/](http://www.breakfastquay.com/dssi-vst/)

It's says it does support amd64 - wine32

---

### Post by Killes on 2008-06-12
Hi, im having a similar problem, im on ubuntu studio 8,04 32bits
When i try to compile dssi-vst as per instructed i get :

> COPYING			 Makefile~		 remotepluginserver.cpp
dssi-vst.cpp		 paths.cpp		 remotepluginserver.h
dssi-vst_gui.cpp	 paths.h		 remotepluginserver.o
dssi-vst-scanner	 paths.o		 remotevstclient.cpp
dssi-vst-scanner.cpp	 rdwrops.cpp		 remotevstclient.h
dssi-vst-scanner.exe.so  rdwrops.h		 remotevstclient.o
dssi-vst-server		 rdwrops.o		 runvst.sh
dssi-vst-server.cpp	 README			 vestige
dssi-vst-server.cpp~	 remotepluginclient.cpp  vsthost.cpp
dssi-vst-server.exe.so	 remotepluginclient.h	 vstsdk2.4
libremoteplugin.a	 remotepluginclient.o
Makefile		 remoteplugin.h
root@nzeuser:/home/nzeuser/dssi-vst-0.7# make clean
rm -f remotevstclient.o remotepluginclient.o remotepluginserver.o rdwrops.o paths.o libremoteplugin.a
root@nzeuser:/home/nzeuser/dssi-vst-0.7# make
g++ -Ivestige -Wall -fPIC remotepluginclient.cpp -c
g++ -Ivestige -Wall -fPIC remotepluginserver.cpp -c
g++ -Ivestige -Wall -fPIC   -c -o rdwrops.o rdwrops.cpp
g++ -Ivestige -Wall -fPIC   -c -o paths.o paths.cpp
ar r libremoteplugin.a remotepluginclient.o remotepluginserver.o rdwrops.o paths.o
ar: creating libremoteplugin.a
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server -lpthread -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function &#8216;virtual void RemoteVSTServer::hideGUI()&#8217;:
dssi-vst-server.cpp:566: warning: unused variable &#8216;fd&#8217;
wineg++ -Ivestige -Wall -fPIC dssi-vst-scanner.cpp -o dssi-vst-scanner -lpthread -L. -lremoteplugin -lpthread
dssi-vst-scanner.cpp: In function &#8216;int WinMain(HINSTANCE__*, HINSTANCE__*, CHAR*, int)&#8217;:
dssi-vst-scanner.cpp:252: warning: unused variable &#8216;uniqueId&#8217;
g++ -Ivestige -Wall -fPIC remotevstclient.cpp -c
g++ -shared -Wl,-Bsymbolic -g3 -Ivestige -Wall -fPIC -o dssi-vst.so dssi-vst.cpp remotevstclient.o -lpthread -L. -lremoteplugin -lasound
In file included from dssi-vst.cpp:12:
/usr/include/dssi.h:28:28: error: alsa/seq_event.h: No such file or directory
dssi-vst.cpp:14:33: error: alsa/seq_midi_event.h: No such file or directory
In file included from dssi-vst.cpp:12:
/usr/include/dssi.h:307: error: &#8216;snd_seq_event_t&#8217; has not been declared
/usr/include/dssi.h:321: error: &#8216;snd_seq_event_t&#8217; has not been declared
/usr/include/dssi.h:359: error: &#8216;snd_seq_event_t&#8217; has not been declared
/usr/include/dssi.h:375: error: &#8216;snd_seq_event_t&#8217; has not been declared
dssi-vst.cpp:50: error: &#8216;snd_seq_event_t&#8217; has not been declared
dssi-vst.cpp:76: error: ISO C++ forbids declaration of &#8216;snd_midi_event_t&#8217; with no type
dssi-vst.cpp:76: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
dssi-vst.cpp:119: error: &#8216;snd_seq_event_t&#8217; has not been declared
dssi-vst.cpp: In constructor &#8216;DSSIVSTPluginInstance::DSSIVSTPluginInstance(std::string, long unsigned int)&#8217;:
dssi-vst.cpp:178: error: &#8216;m_alsaDecoder&#8217; was not declared in this scope
dssi-vst.cpp:178: error: &#8216;snd_midi_event_new&#8217; was not declared in this scope
dssi-vst.cpp:184: error: &#8216;snd_midi_event_no_status&#8217; was not declared in this scope
dssi-vst.cpp: In destructor &#8216;virtual DSSIVSTPluginInstance::~DSSIVSTPluginInstance()&#8217;:
dssi-vst.cpp:230: error: &#8216;m_alsaDecoder&#8217; was not declared in this scope
dssi-vst.cpp:231: error: &#8216;snd_midi_event_free&#8217; was not declared in this scope
dssi-vst.cpp: At global scope:
dssi-vst.cpp:370: error: &#8216;snd_seq_event_t&#8217; has not been declared
dssi-vst.cpp: In member function &#8216;void DSSIVSTPluginInstance::runSynth(long unsigned int, int*, long unsigned int)&#8217;:
dssi-vst.cpp:375: error: &#8216;m_alsaDecoder&#8217; was not declared in this scope
dssi-vst.cpp:382: error: &#8216;snd_seq_event_t&#8217; was not declared in this scope
dssi-vst.cpp:382: error: &#8216;ev&#8217; was not declared in this scope
dssi-vst.cpp:395: error: &#8216;snd_midi_event_decode&#8217; was not declared in this scope
dssi-vst.cpp: At global scope:
dssi-vst.cpp:679: error: &#8216;snd_seq_event_t&#8217; has not been declared
make: *** [dssi-vst.so] Error 1

Anyone have an idea, im totally lost, I tried getting a rpm and converting it to deb and isntalling like that, seemed to install ok but no ne of the supported vst's worked... thanks :confused:

btw I uninstalled dssi-vst as it seemed not ot be properly installed, a proper compile would be lovely :)

---

### Post by postlude on 2008-08-24
It seems that dssi-vst also requires the wine headers and the alsa headers:

apt-get install libasound2-dev wine-dev

---

### Post by Stochastic on 2008-08-24
upon some further research, the original compile error that fistuks reported should be solvable by doing ```
sudo apt-get install libc6-dev
```

The second build error that Killes reported can be solved by the commands postlude has posted above.

---

### Post by vivichrist on 2008-09-01
I have all the above installed on hardy amd64 and get this output:
```
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:
dssi-vst-server.cpp:566: warning: unused variable ‘fd’
ld: Relocatable linking with relocations from format elf64-x86-64 (./libremoteplugin.a(remotepluginserver.o)) to format elf32-i386 (dssi-vst-server.OunTMn.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: winebuild failed
make: *** [dssi-vst-server.exe.so] Error 2
```

...?

---

### Post by Stochastic on 2008-09-01
Vivichrist, your first error (that Killes had not reported), this:

> **vivichrist said:**
> ld: Relocatable linking with relocations from format elf64-x86-64 (./libremoteplugin.a(remotepluginserver.o)) to format elf32-i386 (dssi-vst-server.OunTMn.o) is not supported

Sounds exactly like this:

> **fistuks said:**
> On their site - 
[http://www.breakfastquay.com/dssi-vst/](http://www.breakfastquay.com/dssi-vst/)

It's says it does support amd64 - wine32

---

### Post by motin on 2008-09-18
This got me through the compilation on i386 8.04:
```
sudo apt-get install wine-dev liblo0-dev dssi-dev libasound2-dev
make
sudo make install
```

Currently on 8.10, I get but:
```
$ make
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:
dssi-vst-server.cpp:566: warning: unused variable ‘fd’
dssi-vst-server.cpp: In function ‘int WinMain(HINSTANCE__*, HINSTANCE__*, CHAR*, int)’:
dssi-vst-server.cpp:1138: error: ‘getenv’ was not declared in this scope
dssi-vst-server.cpp:1166: error: ‘exit’ was not declared in this scope
winegcc: i486-linux-gnu-g++ failed
make: *** [dssi-vst-server.exe.so] Fel 2
```

---

### Post by Capoeira on 2008-10-29
i'm trying to compile dssi-vst now on 8.10.
but the steinberg sdk header now requires a login for download :-)
do i realy need it? for qhat is that, since it is not necessary required?

---

### Post by thorgal on 2008-10-29
IIRC, dssi-vst can be compiled without the original steinberg VST SDK header.

---

### Post by Capoeira on 2008-10-29
i don't get it on 8.10 too:

output:
-------------
capoeirista@Capoeira:~/vst/dssi-vst-0.7$ make                    
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:                
dssi-vst-server.cpp:566: warning: unused variable ‘fd’
dssi-vst-server.cpp: In function ‘int WinMain(HINSTANCE__*, HINSTANCE__*, CHAR*, int)’:
dssi-vst-server.cpp:1138: error: ‘getenv’ was not declared in this scope
dssi-vst-server.cpp:1166: error: ‘exit’ was not declared in this scope
winegcc: i486-linux-gnu-g++ failed
make: ** [dssi-vst-server.exe.so] Erro 2
-------------

---

### Post by thorgal on 2008-10-29
make sure you have these packages installed :

libstdc++6-4.2-dev
libc6-dev

they contained gcc's and g++'s required header file stdlib.h where the getenv and exit functions are declared

---

### Post by Capoeira on 2008-10-29
> **thorgal said:**
> make sure you have these packages installed :

libstdc++6-4.2-dev
libc6-dev

they contained gcc's and g++'s required header file stdlib.h where the getenv and exit functions are declared

they where allready installed :-o.

read on other page that liblo0-dev and libasound2-dev are necessary (think its not up to date)

g++ (wich contains the 2 packs mentioned by you/thorgal), gcc, dssi header, wine, wine header, liblo are installed

now i still get this:

~/vst/dssi-vst-0.7$ make                                                     
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:                
dssi-vst-server.cpp:566: warning: unused variable ‘fd’
dssi-vst-server.cpp: In function ‘int WinMain(HINSTANCE__*, HINSTANCE__*, CHAR*, int)’:
dssi-vst-server.cpp:1138: error: ‘getenv’ was not declared in this scope
dssi-vst-server.cpp:1166: error: ‘exit’ was not declared in this scope
winegcc: i486-linux-gnu-g++ failed
make: ** [dssi-vst-server.exe.so] Erro 2
capoeirista@Capoeira:~/vst/dssi-vst-0.7$

---

### Post by thorgal on 2008-10-29
then it could be a source bug in dssi-vst-server.cpp
make sure you have an header include around the top of the file, like

```

#include <cstdlib>

```

or

```

#include <stdlib.h>

```

although the former code is best

---

### Post by Capoeira on 2008-10-29
> **thorgal said:**
> then it could be a source bug in dssi-vst-server.cpp
make sure you have an header include around the top of the file, like

```

#include <cstdlib>

```

or

```

#include <stdlib.h>

```

although the former code is best

icluded the two lines, now i get this: ‘getenv’ was not declared in this scope
wtf

also tried redownloading the sourcecode, but same thing.

output:
--------------------
~/vst/dssi-vst-0.7$ make                                                     
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:                
dssi-vst-server.cpp:567: warning: unused variable ‘fd’                                            
wineg++ -Ivestige -Wall -fPIC dssi-vst-scanner.cpp -o dssi-vst-scanner  -L. -lremoteplugin -lpthread
dssi-vst-scanner.cpp: In function ‘int WinMain(HINSTANCE__*, HINSTANCE__*, CHAR*, int)’:
dssi-vst-scanner.cpp:166: error: ‘getenv’ was not declared in this scope
dssi-vst-scanner.cpp:252: warning: unused variable ‘uniqueId’
winegcc: i486-linux-gnu-g++ failed
make: ** [dssi-vst-scanner.exe.so] Erro 2
capoeirista@Capoeira:~/vst/dssi-vst-0.7$

-----------------

---

### Post by thorgal on 2008-10-29
could it be a problem with the versions of libstdc you have installed ?
this error looks more and more weird ...

in a terminal, what does 'man getenv' outputs on the screen ?

provided that the relevant man pages are installed, this command will give you a hint regarding which header file getenv is declared in.

---

### Post by Capoeira on 2008-10-29
> **thorgal said:**
> 

in a terminal, what does 'man getenv' outputs on the screen ?


-----------
capoeirista@Capoeira:~$ man getenv
Nenhuma entrada de manual para getenv
-----------

means: no manual-entry para getenv


can it be a problem of intrepid-packages perhaps?


anyone here allready installes dssi-vst in intrepid succesfully?

---

### Post by thorgal on 2008-10-30
the lack of entry resulting from the 'man getenv' command is not an issue at all. It just indicates that you don't have the C standard lib manpages, which are useful for programmers since they give a man page for every standard function like exit, getenv, memcpy, etc. You don't need to worry about that. 

It still does not solve your problem. Did I ask you which version of gcc and g++, libstdc, libc6 you have installed ?
I

---

### Post by Capoeira on 2008-10-30
> **thorgal said:**
> Did I ask you which version of gcc and g++, libstdc, libc6 you have installed ?
I

gcc 4:4.3.1-1ubuntu2
g++ 4:4.3.1-1ubuntu2
libstdc++6 4.3.2-1ubuntu11

---

### Post by thorgal on 2008-10-30
I have ubuntu hardy on my laptop (which I am not using for music prod at all). I could compile dssi-vst without any problem. My packages :

wine and wine-dev 0.9.59 (but 1.0.1 or more would do, as I proved with my DAW running debian sid)

gcc 4.2.4-3ubuntu2
g++ 4.2.4-3ubuntu2
libstdc++-dev 4.2.4-3ubuntu2
libc6 and libc6-dev 2.8~20080505-0ubuntu7
dssi and dssi-dev 0.9.1-2ubuntu1

I can try with yuor more recent versions

So, I tried with

gcc and g++ 4.3.2-1ubuntu11
libstdc++6-4.3.2-1ubuntu11

no problem.

---

### Post by Capoeira on 2008-10-30
well, i'll wait the intrepid-final-release-update than (it's today isn't it).
after that perhaps will/have to give another vst-host a try.

thank you verry much so far thorgal.

---

### Post by Capoeira on 2008-10-31
só, anybody on 8.10 get it working?

motin?

what about fst? a good alternative?

---

### Post by oedipuss on 2008-11-10
I got it to compile by adding 
```

#include <cstdlib>

```

at the top of dssi-vst-server.cpp and dssi-vst-scanner.cpp files.

It also needs libasound2-dev , which isn't mentioned in the README, but I guess kind of obvious.

---

### Post by vivichrist on 2008-11-17
still get this in amd64:

```
$ make
wineg++ -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin -lpthread
dssi-vst-server.cpp: In member function ‘virtual void RemoteVSTServer::hideGUI()’:
dssi-vst-server.cpp:567: warning: unused variable ‘fd’
ld: Relocatable linking with relocations from format elf64-x86-64 (./libremoteplugin.a(remotepluginserver.o)) to format elf32-i386 (dssi-vst-server.iCC1g8.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: winebuild failed
make: *** [dssi-vst-server.exe.so] Error 2

```

---

### Post by otz070 on 2008-11-18
```
dssi-vst-server.cpp:566: warning: unused variable ‘fd’

```
This seems to me what is causing the problem with my install.
Anyone know what this means or how to fix it?
I see others have the "unused variable 'fd' error 2" problem too

Thanks

---

### Post by thorgal on 2008-11-18
the warning is not an issue here. The compiler just warns that a declared variable is not used in the function scope where it has been declared, which makes the variable superfluous (no need to declare stuff you don't need). Since the compilation rule does not contain -Werror, then the warning is not treated as an error.

I tend to think this has to do with compilation on a 64bit system. I would google around that instead of focusing on problems in the source code. I compile it without any problem on my 32bit boxes so it must be a 64bit issue. Have you tried to compile it in a chroot that emulates a 32bit environment ?

---

### Post by taupter on 2008-11-29
What I did here (Kubuntu Intrepid Ibex, amd64)

I got dssi-vst-0.7.tar.gz from
[http://sourceforge.net/project/showfiles.php?group_id=104230&package_id=127571](http://sourceforge.net/project/showfiles.php?group_id=104230&package_id=127571)

, uncompressed it, added the

#include <cstdlib>

to dssi-vst-scanner.cpp and dssi-vst-server.cpp, and got rid of the relocation problem by appending

-m32 -march=i586

to the CXXFLAGS in the Makefile.
I got the i386 version of liblo0ldbl from

[https://launchpad.net/ubuntu/intrepid/i386/liblo0ldbl](https://launchpad.net/ubuntu/intrepid/i386/liblo0ldbl)

, uncompressed the .deb package, uncompressed data.tar.gz that is in it, cd'ed into data's usr/lib and copied its content to /usr/lib32, then

root@ptah:/home/taupter# cd /usr/lib32/
root@ptah:/usr/lib32# rm liblo.so.0
root@ptah:/usr/lib32# ln -s liblo.so.0.6.0 liblo.so.0.6
root@ptah:/usr/lib32# ln -s liblo.so.0.6 liblo.so
root@ptah:/usr/lib32# ln -s libstdc++.so.6 libstdc++.so
root@ptah:/usr/lib32# ln -s libasound.so.2 libasound.so
root@ptah:/usr/lib32# ln -s libjack.so.0 libjack.so
root@ptah:/usr/lib32# ldconfig
root@ptah:/usr/lib32# apt-get install ia32-libs libc6-i386 libc6-dev-i386 lib32gcc1 libstdc++6-4.3-dev wine-dev liblo0-dev dssi-dev libasound2-dev libc6-dev-i386

After that, back to the dssi-vst build dir, and

root@ptah:/home/taupter/dssi-vst-0.7# make clean
root@ptah:/home/taupter/dssi-vst-0.7# make

And the thing compiled. Wow.
I didn't try to install it, as it's too late and I'm just too tired atm. There's another point: Having it compiled doesn't mean it will run as intended,as I believe it generated 32-bit versions that may not interface very well with a 64-bit system. So more investigation must be done.

---

### Post by CheShA on 2009-01-17
I just successfully compiled on UbuntuStudio Hardy 64 in minutes with a little help from this thread and the info clearly stated in the readme to install gcc-multilib and g++-multilib packages if compiling on 64 bit, yet no one here appears to have mentioned it... Here's what I did:

```

aptitude install wine-dev liblo0-dev dssi-dev libasound2-dev libc6-dev wine-dev gcc-multilib g++-multilib
wget http://downloads.sourceforge.net/dssi/dssi-vst-0.8.tar.gz
tar -xzf dssi-vst-0.8.tar.gz
cd dssi-vst-0.8/
make 
make install

```

---

### Post by vivichrist on 2009-01-18
that worked a treat

thank you CheShA:)

---

### Post by Feareilo on 2009-08-17
> **CheShA said:**
> I just successfully compiled on UbuntuStudio Hardy 64 in minutes with a little help from this thread and the info clearly stated in the readme to install gcc-multilib and g++-multilib packages if compiling on 64 bit, yet no one here appears to have mentioned it... Here's what I did:

```

aptitude install wine-dev liblo0-dev dssi-dev libasound2-dev libc6-dev wine-dev gcc-multilib g++-multilib
wget http://downloads.sourceforge.net/dssi/dssi-vst-0.8.tar.gz
tar -xzf dssi-vst-0.8.tar.gz
cd dssi-vst-0.8/
make 
make install

```

You are awesome. Thank you, thank you, thank you!!!

---

### Post by Feareilo on 2009-08-18
If anyone is interested, I posted a small (newbie, like me) guide on how to use Addictive Drums in UbuntuStudio 8.04 here: [http://www.ultimate-guitar.com/forum/showthread.php?p=21265235#post21265235](http://www.ultimate-guitar.com/forum/showthread.php?p=21265235#post21265235)

It also tells how I managed to get dssi-vst working

---

