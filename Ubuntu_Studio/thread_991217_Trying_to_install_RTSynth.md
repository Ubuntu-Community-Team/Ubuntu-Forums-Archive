---
title: "Trying to install RTSynth"
date: 2008-11-23
forum: Ubuntu Studio
---

### Post by mysticofjesus on 2008-11-23
Hello, I am a linux noob trying to set up my computer as a synthesizer. I have Ubuntu Studio, amSynth, AMS, and a few other softsynth programs.

Overall, Linux so far has been great at making sounds that don't really sound "real".

I heard some sound samples from RTSynth <http://www.linux-sound.org/rtsynth/> and I am very impressed. However, I can't seem to figure out how to install it properly. I've got the tarball extracted, but I can't quite figure out where to go from there.

A little help?

---

### Post by Stochastic on 2008-11-23
Simply download from the website, extract the archive to your preferred location, then double click on the rtsynth program.  If you want to be able to execute the program from the command line, create a symbolic link into /usr/bin/ like this (first navigate to the rtsynth folder) ```
sudo ln -s rtsynth /usr/bin/
``` (this is for the alsa version, just replace rtsynth with rtsynth-jack for the jack version) Then, if you want a launcher on your desktop or gnome panel, follow these instructions [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

---

### Post by mysticofjesus on 2008-11-23
Right, the alsa version works that way, bhut the Jack version (which is what I need) gives an error message:

> Can't load the jack driver module.
Reason: /opt/rtsynth/libRTSjack.so: cannot open 
shared object file: No such file or directory

Please set the environment variable
RTSYNTH_DLL_PATH

Thanks for the quick response, by the way.

---

### Post by Stochastic on 2008-11-23
do you have jack running when this error is displayed?

Edit: (read edit#2 before doing this) ahh, after a little more reading I noticed that you need to do the following to get jack working:

-open a terminal
-navigate to the rtsynth/JackDriver folder
-do ```
make
```

If you get any errors from the compiler please post the first error printed.

It should work after that.

EDIT #2 (maybe I should try my advice before posting): Hmm, I still got the could not find error.  So, i did: ```
sudo mkdir /opt/rtsynth/
sudo mv libRTSjack.so /opt/rtsynth/
``` and that fixed it.  I actually think the libRTSjack.so is already built for you so you don't need to go through my Edit #1 process.

---

### Post by mysticofjesus on 2008-11-23
Thanks for the advice. However, it doesn't seem to be working on my system.

On edit #1:

```
andy@R2-D2:~/rtsynth-1.9.5-alsa+jack/JackDriver$ make
g++  -DGCC3 -Wall -D_REENTRANT -Wno-deprecated -O6 -fomit-frame-pointer  -fstrength-reduce -funroll-loops -ffast-math -fno-exceptions -march=pentium -fno-rtti -c jack_driver.cc
make: g++: Command not found
make: *** [jack_driver.o] Error 127

```


And #2:

```
andy@R2-D2:~$ sudo mv libRTSjack.so /opt/rtsynth/
mv: cannot stat `libRTSjack.so': No such file or directory
```

Thanks again for your help.

---

### Post by Stochastic on 2008-11-23
Okay, edit #2 should be executed from within the rtsynth-1.9.5-alsa+jack folder, not the JackDriver subfolder (unless edit #1 succeeded).  To get edit #1 to work, install g++ (sudo apt-get install g++).

---

### Post by mysticofjesus on 2008-11-23
Alright, now I've got it to open. However, now it won't show up in Jack's audio connections. Its midi input comes up, but not its audio output.

Also, this happened:

```
andy@R2-D2:~/rtsynth-1.9.5-alsa+jack/JackDriver$ make
g++  -DGCC3 -Wall -D_REENTRANT -Wno-deprecated -O6 -fomit-frame-pointer  -fstrength-reduce -funroll-loops -ffast-math -fno-exceptions -march=pentium -fno-rtti -c jack_driver.cc
make: g++: Command not found
make: *** [jack_driver.o] Error 127
andy@R2-D2:~/rtsynth-1.9.5-alsa+jack/JackDriver$ make
g++  -DGCC3 -Wall -D_REENTRANT -Wno-deprecated -O6 -fomit-frame-pointer  -fstrength-reduce -funroll-loops -ffast-math -fno-exceptions -march=pentium -fno-rtti -c jack_driver.cc
In file included from jack_driver.cc:13:
jack_driver.h:26:23: error: jack/jack.h: No such file or directory
In file included from jack_driver.cc:13:
jack_driver.h:54: error: ‘jack_nframes_t’ has not been declared
jack_driver.h:55: error: ‘jack_nframes_t’ has not been declared
jack_driver.h:66: error: ISO C++ forbids declaration of ‘jack_port_t’ with no type
jack_driver.h:66: error: expected ‘;’ before ‘*’ token
jack_driver.h:67: error: ISO C++ forbids declaration of ‘jack_port_t’ with no type
jack_driver.h:67: error: expected ‘;’ before ‘*’ token
jack_driver.h:68: error: ISO C++ forbids declaration of ‘jack_client_t’ with no type
jack_driver.h:68: error: expected ‘;’ before ‘*’ token
jack_driver.h:71: error: ‘jack_nframes_t’ does not name a type
jack_driver.h: In member function ‘virtual bool CJack::ServerActive()’:
jack_driver.h:49: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc: At global scope:
jack_driver.cc:35: error: ‘jack_nframes_t’ does not name a type
jack_driver.cc: In constructor ‘CJack::CJack()’:
jack_driver.cc:39: error: ‘m_pOutputPortLeft’ was not declared in this scope
jack_driver.cc:40: error: ‘m_pOutputPortRight’ was not declared in this scope
jack_driver.cc:41: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:47: error: ‘m_bufferIndex’ was not declared in this scope
jack_driver.cc: In destructor ‘virtual CJack::~CJack()’:
jack_driver.cc:55: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc: In member function ‘virtual const bool CJack::ConnectPorts(const std::string&, const std::string&)’:
jack_driver.cc:74: error: ‘jack_port_t’ was not declared in this scope
jack_driver.cc:74: error: ‘jport’ was not declared in this scope
jack_driver.cc:76: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:81: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:81: error: ‘jack_port_by_name’ was not declared in this scope
jack_driver.cc:85: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:85: error: ‘m_pOutputPortLeft’ was not declared in this scope
jack_driver.cc:85: error: ‘jack_port_name’ was not declared in this scope
jack_driver.cc:85: error: ‘jack_disconnect’ was not declared in this scope
jack_driver.cc:88: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:88: error: ‘jack_port_by_name’ was not declared in this scope
jack_driver.cc:92: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:92: error: ‘m_pOutputPortLeft’ was not declared in this scope
jack_driver.cc:92: error: ‘jack_port_name’ was not declared in this scope
jack_driver.cc:92: error: ‘jack_connect’ was not declared in this scope
jack_driver.cc:99: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:99: error: ‘jack_port_by_name’ was not declared in this scope
jack_driver.cc:103: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:103: error: ‘m_pOutputPortRight’ was not declared in this scope
jack_driver.cc:103: error: ‘jack_port_name’ was not declared in this scope
jack_driver.cc:103: error: ‘jack_disconnect’ was not declared in this scope
jack_driver.cc:106: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:106: error: ‘jack_port_by_name’ was not declared in this scope
jack_driver.cc:110: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:110: error: ‘m_pOutputPortRight’ was not declared in this scope
jack_driver.cc:110: error: ‘jack_port_name’ was not declared in this scope
jack_driver.cc:110: error: ‘jack_connect’ was not declared in this scope
jack_driver.cc: In member function ‘virtual bool CJack::Start()’:
jack_driver.cc:134: error: ‘m_bufferIndex’ was not declared in this scope
jack_driver.cc: In member function ‘virtual void CJack::Disconnect()’:
jack_driver.cc:149: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:150: error: ‘jack_deactivate’ was not declared in this scope
jack_driver.cc:151: error: ‘jack_client_close’ was not declared in this scope
jack_driver.cc: In member function ‘virtual const bool CJack::Connect()’:
jack_driver.cc:165: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:166: error: ‘jack_set_error_function’ was not declared in this scope
jack_driver.cc:167: error: ‘jack_client_new’ was not declared in this scope
jack_driver.cc:174: error: ‘m_pClient’ was not declared in this scope
jack_driver.cc:174: error: ‘JackProcessCallback’ was not declared in this scope
jack_driver.cc:174: error: ‘jack_set_process_callback’ was not declared in this scope
jack_driver.cc:176: error: expected `)' before ‘CJack’
jack_driver.cc:176: error: ‘jack_set_sample_rate_callback’ was not declared in this scope
jack_driver.cc:178: error: ‘jack_on_shutdown’ was not declared in this scope
jack_driver.cc:180: error: ‘m_pOutputPortLeft’ was not declared in this scope
jack_driver.cc:181: error: ‘JACK_DEFAULT_AUDIO_TYPE’ was not declared in this scope
jack_driver.cc:182: error: ‘JackPortIsOutput’ was not declared in this scope
jack_driver.cc:182: error: ‘JackPortIsTerminal’ was not declared in this scope
jack_driver.cc:182: error: ‘jack_port_register’ was not declared in this scope
jack_driver.cc:184: error: ‘m_pOutputPortRight’ was not declared in this scope
jack_driver.cc:189: error: ‘jack_activate’ was not declared in this scope
jack_driver.cc: At global scope:
jack_driver.cc:207: error: ‘int CJack::cb_srate’ is not a static member of ‘class CJack’
jack_driver.cc:207: error: ‘jack_nframes_t’ was not declared in this scope
jack_driver.cc:207: error: expected primary-expression before ‘void’
jack_driver.cc:207: error: initializer expression list treated as compound expression
jack_driver.cc:208: error: expected ‘,’ or ‘;’ before ‘{’ token
make: *** [jack_driver.o] Error 1

```

Thanks again. You're awesome.

---

### Post by Stochastic on 2008-11-23
> **mysticofjesus said:**
> Alright, now I've got it to open. However, now it won't show up in Jack's audio connections. Its midi input comes up, but not its audio output.

Also, this happened:

On the top right-hand corner of the RTSynth, you need to turn it on for it to show up in the Jack patchbay.

Now that you have it working, there's no need to rebuild the libRTSjack.so file (what I was describing in edit#1) but if you really wanted to, you'd need to install libjack-dev.

---

### Post by jazzman on 2008-11-25
Here's how I got it to work:

I downloaded the file and extracted it (see above for link) to my desktop

Placed the   rtsynth-1.9.5-alsa+jack   folder in my Home Directory with Nautilus

Open a terminal ==> Applications->Accessories->Terminal
at the prompt type: 

sudo mkdir /opt/rtsynth/

sudo cp ./rtsynth-1.9.5-alsa+jack/libRTSjack.so /opt/rtsynth/

You could launch it by typing either RTSynth or RTSynth-jack (after running Qjackctl)

To make it easier I then added an application launcher in the menu: System->Preferences->Main Menu

I am assuming that you know what to do from there.

This was all that I needed to do, No compiling. 

Hope this helps!

Jazz

---

