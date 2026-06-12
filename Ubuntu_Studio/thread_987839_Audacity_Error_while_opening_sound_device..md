---
title: "Audacity Error while opening sound device."
date: 2008-11-19
forum: Ubuntu Studio
---

### Post by coolethan on 2008-11-19
So i have a Zoom H4 recording device and it works well with audacity however when i go to playback what i have recorded i get

:Error while opening sound device. Please check the output device settings and the project sample rate.

and if i don't get that error then it plays but no sound comes out.

---

### Post by wanichan on 2008-11-20
Edit -> Preferences -> Playback, what are your options? Make sure the selected entry is different from your input device.

Also make sure you've got the newest version (1.3.5-something) from the repository that seemed to have cleaned up a lot of  rubbish that plagued earlier versions.

---

### Post by mateuszbaranski on 2008-11-20
in KDE it is very often conected with notification sounds that generates KDE - so when you start Audacity, KDE generates some sound (while opening program), and the audacity tries to get control over sound device. Thus it cannot while device is still busy. In KDE I change time after which KDE is giving out control over sound device to 2 sec (default is 60s).

To get help write down what sound devices you use for AUDIO I/O (look into preferences)

---

### Post by d_in_Conduct on 2008-11-20
I've been having the same problem.  Audacity seems to be changing the selected playback device arbitrarily.  I go through a hundred or so short .wav clips each day and sometimes I will close a clip and delete it and when I open the next clip,  it will be attempting to use the wrong output device for playback.  Moreover,  the correct device isn't even one of the choices under Edit > Preference > Audio IO.

Now,  I can go through and use mouseover preview the first time around and delete the ones that don't have what I want,  but that still leave 30-40 clips where I need to see the waveforms.  So an ordinary audio player won't work for me.

What I had been doing is clicking the chooser for playback device and just re-clicking the one that had bee chosen for me.  The I would restart Audacity and go back to Preferences and click the chooser and the correct device would be available to choose and all would be well... for awhile.  This method may work for some people experiencing this problem.

Today I can't even get the correct device to show so that I can choose it.

I hard-coded audacity.cfg in my home directory .audacity-data folder and it still came up wrong and when I shut down audacity,  it overwrote the audacity.cfg,  changing it back to the wrong data.  When I made audacity.cfg readonly,  it was STILL overwritten.  

So I am stumped... and annoyed.  I hope the troubleshooting I have done here can point someone more knowledgeable than me to a solution.

Intrepid amd-64
Correct PlaybackDevice=NVidia CK8S: NVidia CK8S (hw:0,0)

---

### Post by Ng Oon-Ee on 2008-11-20
Hi. I don't have any experience with KDE, but I'm assuming that you're not using arts?

Anyway, for myself the most stable method of getting audacity to work is to use a sound server (arts and ESD being the older ones, Pulse being the latest one). By default the Ubuntu installation is buggy though, so this is going to take some effort. For me, the results are worth it though. So be warned.

Firstly, the long long long guide is [markbuntu's guide to multiple surround sound]("http://ubuntuforums.org/showthread.php?t=843012"), which I've found invaluable to properly setting up my computer. It'll take a while though, so just go through it. Remember the section at the end about pulseaudio through jack, that's needed as well.

After that, you can compile Audacity with JACK support, I've posted [a guide to that here]("http://ubuntuforums.org/showthread.php?t=843012"). The reason I've done this is because Audacity seems to support JACK much better than Pulse/arts/ESD (though I never did try for arts), and otherwise it would have to hog your sound devices, which I can't stand.

As a side-benefit, if you've followed everything so far, since your Audacity isn't directly accessing your sound card but going through JACK (very low latencies if you set that up properly, so no performance hit) you can take advantage of the whole plethora of JACK-capable synthesizers, filtes, and the like. Knock yourself  out.

---

### Post by coolethan on 2008-11-22
the version i had installed from the add/remove pragram thing was 2.3.4 beta, i got the very latest version from getdeb and it's working fine except that no sound plays, there are no more errors with the playback device but there is no sound coming out. it doesn't have anything to do with my computer that i'm aware of because i play cd's and stuff all the time.

---

### Post by Ng Oon-Ee on 2008-11-23
> **coolethan said:**
> the version i had installed from the add/remove pragram thing was 2.3.4 beta, i got the very latest version from getdeb and it's working fine except that no sound plays, there are no more errors with the playback device but there is no sound coming out. it doesn't have anything to do with my computer that i'm aware of because i play cd's and stuff all the time.

Are you comfortable with compiling from source? If so, there's good ways to solve your problem.

Otherwise, please go to Edit -> Preferences -> Audio I/O and tell me what devices are listed under Playback and Recording.

---

### Post by coolethan on 2008-11-23
i can give compiling it from source a shot but i have so far never been successful at doing that, you would have to give me step by step instructions for that to work. 

**playback devices:**
OSS:/dev/dsp1
ALSA:C-media CM18738:C-Media PCI 2nd DAC (hw:0,1)
ALSA:H4:USB Audio (hw:1,0)
ALSA:rear

**Recording devices:**
OSS:/dev/dsp
OSS:/dev/dsp1
ALSA:C-Media C-M18738:C-Media PCI DAC/ADC (hw:0,0)
ALSA:C-Media CM18738:C-Media PCI IEC 958 (hw:0,2)
ALSA:H4:USB Audio (hw:1,0)
ALSA:spdif
ALSA:default

---

### Post by Ng Oon-Ee on 2008-11-23
> **coolethan said:**
> i can give compiling it from source a shot but i have so far never been successful at doing that, you would have to give me step by step instructions for that to work.

Okay, scroll back up to my first reply. There's a link to a guide I made for that. Post questions about that guide in its thread, please. But before you do that... read my response below.

> **coolethan said:**
> **playback devices:**
OSS:/dev/dsp1
ALSA:C-media CM18738:C-Media PCI 2nd DAC (hw:0,1)
ALSA:H4:USB Audio (hw:1,0)
ALSA:rear

**Recording devices:**
OSS:/dev/dsp
OSS:/dev/dsp1
ALSA:C-Media C-M18738:C-Media PCI DAC/ADC (hw:0,0)
ALSA:C-Media CM18738:C-Media PCI IEC 958 (hw:0,2)
ALSA:H4:USB Audio (hw:1,0)
ALSA:spdif
ALSA:default

Okay, what you need to do now is stop Pulseaudio/ARTS totally BEFORE starting up your Audacity. In Ubuntu (Gnome) I just type:

```
killall pulseaudio
```

In Kubuntu I guess you would have to kill something else. Just make sure whatever sound server you're running is dead. Then run Audacity. You should have an additional Playback devices saying (hw:0,0). Try playing through that, it should work.

What you've just done is take total control of your sound device from Audacity. That's not very useful, however, as then no1 else can play any sounds or otherwise use the sound card. So you can either try to get Audacity to run with Arts/Pulseaudio (good luck, I never figured that out, I think its not possible as of now for pulse) or you can follow the guide above.

Of course, is you're happy with Audacity taking your entire sound system, and are ONLY using it without any other sound apps, this is your simplest path, just kill all sound servers, run, and then start them again when you want sound in another app (after closing Audacity).

---

### Post by coolethan on 2008-11-23
hey great! it worked, except i'm not sure it killed all other audio from the sound card because my pidgin messenger just made it's little notification bell that rings when someone comes online. oh well it works.

---

### Post by Ng Oon-Ee on 2008-11-23
> **coolethan said:**
> hey great! it worked, except i'm not sure it killed all other audio from the sound card because my pidgin messenger just made it's little notification bell that rings when someone comes online. oh well it works.

Ah, that probably means you have hardware-level mixing. Alsa dmix is supposed to do that (I've never used it before though).

Glad its working for you. Perhaps you'd like to try your other apps as well, Rhythmbox, Amarok, whatever you use for audio, as well as flash youtubes.

---

### Post by coolethan on 2008-11-23
ok so i gave rhythm box a whirl and it played the cd i had in there and then i checked out youtube and no sound, so i went back to audacity and it gave me the sound device error. i opened up the terminal and typed killall pulseaudio again and it told me no process killed and now audacity doesn't work.

---

### Post by Ng Oon-Ee on 2008-11-23
> **coolethan said:**
> ok so i gave rhythm box a whirl and it played the cd i had in there and then i checked out youtube and no sound, so i went back to audacity and it gave me the sound device error. i opened up the terminal and typed killall pulseaudio again and it told me no process killed and now audacity doesn't work.

Okay, what happens is that if you have no sound server up, the likely result is that some app will grab your sound. The app which can play but causes everything after it to stop playing is probably the culprit.

One possible thing you can do is try to set Rhythm Box to play through another device (Alsa mixer instead of OSS, maybe?).

My preferred solution would be to setup Pulseaudio properly (but Audacity won't work), then setup Jack and run Pulseaudio through that (so right now, Jack controls your sound card, Pulseaudio connects to JACK), and then recompile Audacity to use Jack. Everything works, at the same time.

Again, my first post in page one of this thread has the necessary links to do all this.

---

### Post by coolethan on 2008-11-23
ok i have found no way of changing rhythm box to play through ALSA. there are a trillion Jack things out there, jack mixer, jack rack and a slew of others, which is the actual Jack program that everyone talks about thats supposed to do all these things?

---

### Post by coolethan on 2008-11-23
ok so i looked through those tutorials and everything should be good. i'm compiling audacity from source and when i put in ./configure i get this.

ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

this basically happens every single time i try compile something, this may be because i don't have a C compiler but how do i know?

---

### Post by Ng Oon-Ee on 2008-11-24
Try installing the package 'build-essential', you need this every time you want to compile anything from source.

---

### Post by coolethan on 2008-11-24
i got it working, thank you so much for all of your help. can i pm you if i have any more questions?

---

### Post by coolethan on 2008-11-24
checking for wx-config... no
configure: error: "Could not find wx-config: is wxWidgets installed? is wx-config in your path?"


what?

---

### Post by Ng Oon-Ee on 2008-11-24
> **coolethan said:**
> i got it working, thank you so much for all of your help. can i pm you if i have any more questions?

Sorry, pm is only for private communications. You should always post questions in the forum at large for 2 reasons:-
1. Other people can jump in and help you if I haven't answered.
2. Other people can read the solutions given and will not have to ask the same questions again.

Number 2 is especially important, I've solved 10 times the number of problems compared to the questions I've asked here, simply because someone else asked about it before and the solution has been found. Saves everyone's time.

> **coolethan said:**
> checking for wx-config... no
configure: error: "Could not find wx-config: is wxWidgets installed? is wx-config in your path?"


what?

This error means that the development files for wxWidgets are not installed. Have you installed the following packages:-

libwxgtk2.8-dev
libwxbase2.8-dev

These are both installed on my system. Try to install them via Synaptic and rerun the compile. If it works please let me know, I'll update my guide.

---

### Post by coolethan on 2008-11-24
ok i downloaded those lib's and there was something else that it needed but i can't remember but i got those and now it tells me it needs expat to be enabled to work so i'm downloading that now

---

### Post by coolethan on 2008-11-24
downloaded xpat, still didn't work, downloaded libxpat-dev, worked. i'm reading your guide and you say there should be some lines that say

```
configure: ---------------------------------------
configure: Including support for OSS
configure: Including support for ALSA
configure: ---------------------------------------
```

i only get

```
configure: ---------------------------------------
configure: Including support for OSS
configure: ---------------------------------------
configure: creating ./config.status
config.status: creating Makefile
```

---

### Post by Ng Oon-Ee on 2008-11-25
> **coolethan said:**
> downloaded xpat, still didn't work, downloaded libxpat-dev, worked. i'm reading your guide and you say there should be some lines that say

```
configure: ---------------------------------------
configure: Including support for OSS
configure: Including support for ALSA
configure: ---------------------------------------
```

i only get

```
configure: ---------------------------------------
configure: Including support for OSS
configure: ---------------------------------------
configure: creating ./config.status
config.status: creating Makefile
```

Okay, I'd think ALSA support isn't really a big deal. You could search for 'alsa' in Synaptic and select any likely-sounding -dev packages. Don't select any of the players, of course (there's tons when you search 'alsa'). Sorry I can't check for you, but am currently updating my OpenOffice so my Synaptic is unaccessible for a while.

---

### Post by coolethan on 2008-11-25
ok i downloaded one of the severl alsa things and that didn't help but the most important thing is that there's jack support right?  because everything will be going through jack anyways.

---

### Post by coolethan on 2008-11-25
don't know whats wrong here but there are a LOT or errors

```
ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ make
make -C lib-src
make[1]: Entering directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src'
make -C FileDialog
make[2]: Entering directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src/FileDialog'
g++ -c -g -O2 -I.  -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  generic/FileDialogPrivate.cpp -o generic/FileDialogPrivate.o
generic/FileDialogPrivate.cpp: In function ‘int FileDataNameCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:88: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:88: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:88: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:88: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:89: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:89: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:89: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: In function ‘int FileDataSizeCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:100: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:100: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:100: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:100: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:101: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:101: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:101: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: In function ‘int FileDataTypeCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:114: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:114: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:114: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:114: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:115: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:115: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:115: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: In function ‘int FileDataTimeCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:128: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:128: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:128: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:128: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:129: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:129: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:129: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:153: error: ‘FileData’ has not been declared
generic/FileDialogPrivate.cpp:153: error: ‘fileType’ has not been declared
generic/FileDialogPrivate.cpp:153: error: ISO C++ forbids declaration of ‘FileData’ with no type
generic/FileDialogPrivate.cpp: In function ‘int FileData(const wxString&, const wxString&, int, int)’:
generic/FileDialogPrivate.cpp:155: error: ‘Init’ was not declared in this scope
generic/FileDialogPrivate.cpp:156: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp:157: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:158: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:159: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp:161: error: ‘ReadData’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:164: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp: In function ‘void Init()’:
generic/FileDialogPrivate.cpp:166: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:167: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:167: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:168: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:171: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:171: error: expected ‘,’ or ‘...’ before ‘&’ token
generic/FileDialogPrivate.cpp:171: error: ISO C++ forbids declaration of ‘FileData’ with no type
generic/FileDialogPrivate.cpp: In function ‘void Copy(int)’:
generic/FileDialogPrivate.cpp:173: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp:173: error: ‘fileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:174: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:175: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:176: error: ‘m_dateTime’ was not declared in this scope
generic/FileDialogPrivate.cpp:177: error: ‘m_permissions’ was not declared in this scope
generic/FileDialogPrivate.cpp:178: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:179: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:182: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp: In function ‘void ReadData()’:
generic/FileDialogPrivate.cpp:184: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:186: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:237: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:238: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:238: error: ‘is_link’ was not declared in this scope
generic/FileDialogPrivate.cpp:249: error: ‘is_dir’ was not declared in this scope
generic/FileDialogPrivate.cpp:250: error: ‘is_exe’ was not declared in this scope
generic/FileDialogPrivate.cpp:251: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:253: error: ‘m_dateTime’ was not declared in this scope
generic/FileDialogPrivate.cpp:258: error: ‘m_permissions’ was not declared in this scope
generic/FileDialogPrivate.cpp:281: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp:283: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp:286: error: ‘IsExe’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:293: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:293: error: non-member function ‘wxString GetFileType()’ cannot have cv-qualifier
generic/FileDialogPrivate.cpp: In function ‘wxString GetFileType()’:
generic/FileDialogPrivate.cpp:295: error: ‘IsDir’ was not declared in this scope
generic/FileDialogPrivate.cpp:297: error: ‘IsLink’ was not declared in this scope
generic/FileDialogPrivate.cpp:299: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:301: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:307: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:307: error: non-member function ‘wxString GetModificationTime()’ cannot have cv-qualifier
generic/FileDialogPrivate.cpp: In function ‘wxString GetModificationTime()’:
generic/FileDialogPrivate.cpp:310: error: ‘m_dateTime’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:313: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:313: error: non-member function ‘wxString GetHint()’ cannot have cv-qualifier
generic/FileDialogPrivate.cpp: In function ‘wxString GetHint()’:
generic/FileDialogPrivate.cpp:315: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:318: error: ‘IsDir’ was not declared in this scope
generic/FileDialogPrivate.cpp:320: error: ‘IsLink’ was not declared in this scope
generic/FileDialogPrivate.cpp:322: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:325: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:329: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:333: error: ‘m_permissions’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:339: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:339: error: ‘fileListFieldType’ was not declared in this scope
generic/FileDialogPrivate.cpp:339: error: expected ‘,’ or ‘;’ before ‘const’
make[2]: *** [generic/FileDialogPrivate.o] Error 1
make[2]: Leaving directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src/FileDialog'
make[1]: *** [FileDialog-recursive] Error 2
make[1]: Leaving directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src'
make: *** [audacity] Error 2
ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ 

```

---

### Post by Ng Oon-Ee on 2008-11-25
> **coolethan said:**
> don't know whats wrong here but there are a LOT or errors

```
ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ make
make -C lib-src
make[1]: Entering directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src'
make -C FileDialog
make[2]: Entering directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src/FileDialog'
g++ -c -g -O2 -I.  -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  generic/FileDialogPrivate.cpp -o generic/FileDialogPrivate.o
generic/FileDialogPrivate.cpp: In function ‘int FileDataNameCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:88: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:88: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:88: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:88: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:89: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:89: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:89: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: In function ‘int FileDataSizeCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:100: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:100: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:100: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:100: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:101: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:101: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:101: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: In function ‘int FileDataTypeCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:114: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:114: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:114: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:114: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:115: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:115: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:115: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: In function ‘int FileDataTimeCompare(long int, long int, long int)’:
generic/FileDialogPrivate.cpp:128: error: ‘FileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:128: error: ‘fd1’ was not declared in this scope
generic/FileDialogPrivate.cpp:128: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:128: error: expected `;' before ‘data1’
generic/FileDialogPrivate.cpp:129: error: ‘fd2’ was not declared in this scope
generic/FileDialogPrivate.cpp:129: error: expected primary-expression before ‘)’ token
generic/FileDialogPrivate.cpp:129: error: expected `;' before ‘data2’
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:153: error: ‘FileData’ has not been declared
generic/FileDialogPrivate.cpp:153: error: ‘fileType’ has not been declared
generic/FileDialogPrivate.cpp:153: error: ISO C++ forbids declaration of ‘FileData’ with no type
generic/FileDialogPrivate.cpp: In function ‘int FileData(const wxString&, const wxString&, int, int)’:
generic/FileDialogPrivate.cpp:155: error: ‘Init’ was not declared in this scope
generic/FileDialogPrivate.cpp:156: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp:157: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:158: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:159: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp:161: error: ‘ReadData’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:164: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp: In function ‘void Init()’:
generic/FileDialogPrivate.cpp:166: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:167: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:167: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:168: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:171: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:171: error: expected ‘,’ or ‘...’ before ‘&’ token
generic/FileDialogPrivate.cpp:171: error: ISO C++ forbids declaration of ‘FileData’ with no type
generic/FileDialogPrivate.cpp: In function ‘void Copy(int)’:
generic/FileDialogPrivate.cpp:173: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp:173: error: ‘fileData’ was not declared in this scope
generic/FileDialogPrivate.cpp:174: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:175: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:176: error: ‘m_dateTime’ was not declared in this scope
generic/FileDialogPrivate.cpp:177: error: ‘m_permissions’ was not declared in this scope
generic/FileDialogPrivate.cpp:178: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:179: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:182: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp: In function ‘void ReadData()’:
generic/FileDialogPrivate.cpp:184: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:186: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:237: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:238: error: ‘m_type’ was not declared in this scope
generic/FileDialogPrivate.cpp:238: error: ‘is_link’ was not declared in this scope
generic/FileDialogPrivate.cpp:249: error: ‘is_dir’ was not declared in this scope
generic/FileDialogPrivate.cpp:250: error: ‘is_exe’ was not declared in this scope
generic/FileDialogPrivate.cpp:251: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:253: error: ‘m_dateTime’ was not declared in this scope
generic/FileDialogPrivate.cpp:258: error: ‘m_permissions’ was not declared in this scope
generic/FileDialogPrivate.cpp:281: error: ‘m_image’ was not declared in this scope
generic/FileDialogPrivate.cpp:283: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp:286: error: ‘IsExe’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:293: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:293: error: non-member function ‘wxString GetFileType()’ cannot have cv-qualifier
generic/FileDialogPrivate.cpp: In function ‘wxString GetFileType()’:
generic/FileDialogPrivate.cpp:295: error: ‘IsDir’ was not declared in this scope
generic/FileDialogPrivate.cpp:297: error: ‘IsLink’ was not declared in this scope
generic/FileDialogPrivate.cpp:299: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:301: error: ‘m_fileName’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:307: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:307: error: non-member function ‘wxString GetModificationTime()’ cannot have cv-qualifier
generic/FileDialogPrivate.cpp: In function ‘wxString GetModificationTime()’:
generic/FileDialogPrivate.cpp:310: error: ‘m_dateTime’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:313: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:313: error: non-member function ‘wxString GetHint()’ cannot have cv-qualifier
generic/FileDialogPrivate.cpp: In function ‘wxString GetHint()’:
generic/FileDialogPrivate.cpp:315: error: ‘m_filePath’ was not declared in this scope
generic/FileDialogPrivate.cpp:318: error: ‘IsDir’ was not declared in this scope
generic/FileDialogPrivate.cpp:320: error: ‘IsLink’ was not declared in this scope
generic/FileDialogPrivate.cpp:322: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:325: error: ‘m_size’ was not declared in this scope
generic/FileDialogPrivate.cpp:329: error: ‘IsDrive’ was not declared in this scope
generic/FileDialogPrivate.cpp:333: error: ‘m_permissions’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:339: error: ‘FileData’ is not a class or namespace
generic/FileDialogPrivate.cpp:339: error: ‘fileListFieldType’ was not declared in this scope
generic/FileDialogPrivate.cpp:339: error: expected ‘,’ or ‘;’ before ‘const’
make[2]: *** [generic/FileDialogPrivate.o] Error 1
make[2]: Leaving directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src/FileDialog'
make[1]: *** [FileDialog-recursive] Error 2
make[1]: Leaving directory `/home/ethan/Desktop/audacity-src-1.3.6/lib-src'
make: *** [audacity] Error 2
ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ 

```

Hello, I suggest if you get such errors to google them first. It gets you results faster than anything else :). I've never seen these errors before, but a quick google on the phrase "error: ‘FileData’ was not declared in this scope" led me to some sites that suggest you do not have libgtk2.0-dev. Try installing that as well.

---

### Post by superoptimo on 2008-11-25
Please read this topic.
[http://ubuntuforums.org/showthread.php?t=993157](http://ubuntuforums.org/showthread.php?t=993157)

For using audacity, you have to configure Jack.

---

### Post by Ng Oon-Ee on 2008-11-25
> **superoptimo said:**
> Please read this topic.
[http://ubuntuforums.org/showthread.php?t=993157](http://ubuntuforums.org/showthread.php?t=993157)

For using audacity, you have to configure Jack.

That's true, but for now he still has to compile Audacity, after which he can start worrying about how to use Jack itself :)

---

### Post by coolethan on 2008-11-25
it is done, i had to install some gettext thing so i did that and no more hiccups. inside audacity now i can't select the jack program thing in any of the playback or input menus.

---

### Post by Ng Oon-Ee on 2008-11-25
> **coolethan said:**
> it is done, i had to install some gettext thing so i did that and no more hiccups. inside audacity now i can't select the jack program thing in any of the playback or input menus.

Install qjackctl and run it, click the green 'Start' button to start Jack. Start Audacity after that.

Jack might not be able to start up if Pulseaudio is already running, so 'killall pulseaudio' first if that's the case.

If this works, then you need to follow the tutorials posted earlier on how to setup Pulseaudio in a Surround system to pipe through Jack.

---

### Post by coolethan on 2008-11-25
ya i've set up the pulseaudio thing, i clicked on start and i got this friendly little message 

sh: artsshell: not found

---

### Post by Ng Oon-Ee on 2008-11-25
> **coolethan said:**
> ya i've set up the pulseaudio thing, i clicked on start and i got this friendly little message 

sh: artsshell: not found

Pulseaudio does not have a start. You probably mean qjackctl.

Is that the only message you get? Does the start button then gray out and the stop button become red? This means Jack has already started.

---

### Post by coolethan on 2008-11-25
ya thats the only error i got and i quit out of that and went killall pulseaudio and then i was able to run it fine, for some reason it isn't recording in audacity. i went through that set up in the tutorials you showed me earlier but it's not working anymore. :confused:

---

### Post by Ng Oon-Ee on 2008-11-25
> **coolethan said:**
> ya thats the only error i got and i quit out of that and went killall pulseaudio and then i was able to run it fine, for some reason it isn't recording in audacity. i went through that set up in the tutorials you showed me earlier but it's not working anymore. :confused:

Okay, it runs fine, now click on the 'connect' button on the main qjackctl window. Then start Audacity and start recording. Do you see a Portaudio appear somewhere there? It should appear on the right-hand side, connected by a line with 'system' on the left-hand side.

Remember to set JACK as your playback/recording in Audacity first.

Also, under the qjackctl Setup, make sure the correct input/output devices are chosen (normally hw:0)

---

### Post by coolethan on 2008-11-25
ok that was working and now i get this thing everytime i open it and try to start it that says error can not connect to jack server as client. it was working and then i tried to see how low i could get the latency to go and so those don't take effect until you restart jack, which i did and now this is happening.

---

### Post by Ng Oon-Ee on 2008-11-26
> **coolethan said:**
> ok that was working and now i get this thing everytime i open it and try to start it that says error can not connect to jack server as client. it was working and then i tried to see how low i could get the latency to go and so those don't take effect until you restart jack, which i did and now this is happening.

When you cannot connect to Jack server as client this is normally cos some other app has control of the sound system. I'd check on the normal suspects, arts, Pulseaudio, etc., and make sure they're all switched off before I start Jack.

---

### Post by coolethan on 2008-11-26
ok i closed all of the programs that could possible be using the sound card and it's still not working man. i also installed ardour because it's quite a bit more in depth and its and actual DAW. i did have this program before and up untill about 2 hours ago i didn't have a working resolution that i could actually see the whole program in whereas audacity was able to fit in the window so now i'm using ardour which uses the JACK thing as well and is not working. what if i reinstalled jack?

---

### Post by Ng Oon-Ee on 2008-11-26
> **coolethan said:**
> ok i closed all of the programs that could possible be using the sound card and it's still not working man. i also installed ardour because it's quite a bit more in depth and its and actual DAW. i did have this program before and up untill about 2 hours ago i didn't have a working resolution that i could actually see the whole program in whereas audacity was able to fit in the window so now i'm using ardour which uses the JACK thing as well and is not working. what if i reinstalled jack?

Have you tried checking your qjackctl setup to see whether the correct hardware device is selected? What do you mean by 'not working', is not it starting up properly or is Audacity/Ardour recording silence?

More details would help very much.

EDIT: Forgot to mention, reinstalling Jack would not help unless you're changing versions. If the problem is with your configuration, this does not get reset on a reinstall, and you can change those without reinstalling.

---

### Post by andr100 on 2008-11-27
> **wanichan said:**
> Edit -> Preferences -> Playback, what are your options? Make sure the selected entry is different from your input device.

Also make sure you've got the newest version (1.3.5-something) from the repository that seemed to have cleaned up a lot of  rubbish that plagued earlier versions.


Thenks a lot. I had the same problem.

---

### Post by coolethan on 2008-11-28
> **Ng Oon-Ee said:**
> Have you tried checking your qjackctl setup to see whether the correct hardware device is selected? What do you mean by 'not working', is not it starting up properly or is Audacity/Ardour recording silence?

More details would help very much.

EDIT: Forgot to mention, reinstalling Jack would not help unless you're changing versions. If the problem is with your configuration, this does not get reset on a reinstall, and you can change those without reinstalling.

ok i fixed my problems with JACK and it now runs but Ardour is not recording sound from the device that i have hooked up. i don't know if theirs an input device and playback device options thing like in audacity.

---

### Post by Ng Oon-Ee on 2008-11-28
> **coolethan said:**
> ok i fixed my problems with JACK and it now runs but Ardour is not recording sound from the device that i have hooked up. i don't know if theirs an input device and playback device options thing like in audacity.

In Edit->Preferences->Audio I/O you must select JACK Audio Connection Kit: system for both Playback and Recording.

Then, in qjackctl, click on the 'Connect' button. This is where you control which clients are connected to which clients.

---

### Post by coolethan on 2008-11-29
my ardour is no longer working when i go to create a new session i get a

programming error:true hardware name for ID missing

---

### Post by coolethan on 2008-11-30
now that i have ardour how do i uninstall audacity after compiling it from source because it doesn't show up in the installed programs list or in synaptic package manager that i can tell.

---

### Post by Ng Oon-Ee on 2008-11-30
> **coolethan said:**
> now that i have ardour how do i uninstall audacity after compiling it from source because it doesn't show up in the installed programs list or in synaptic package manager that i can tell.

Go to the directory where you ran 'make' and 'configure' previously and run:

```
make uninstall
```

---

### Post by coolethan on 2008-11-30
> **Ng Oon-Ee said:**
> Go to the directory where you ran 'make' and 'configure' previously and run:

```
make uninstall
```

should be 

```
sudo make uninstall
```

ok ardour is recording nothing but silence i checked on the website in the manual and i did what it said for setting up the recording device which i hardly understood and theres no sound being recorded

---

### Post by Ng Oon-Ee on 2008-11-30
> **coolethan said:**
> should be 

```
sudo make uninstall
```

ok ardour is recording nothing but silence i checked on the website in the manual and i did what it said for setting up the recording device which i hardly understood and theres no sound being recorded
Sorry about that.

Anyway, in qjackctl, under 'Connections', what do you see?

---

### Post by coolethan on 2008-11-30
on the left hand side i see                        

Ardour:
-audio1/out1
-audio1/out2
-auditioner/out1
-auditioner/out2
-click/out1
-master/out1
-master/out2
System:
-capture_1
-capture_2

and the right hand side

Ardour:
-audio1/in1
-master/in1
-master/in2
System:
-playback_1
-playback_2


oh and all of a sudden my pulse audio stopped working. when i click on volume control it says "connection failed:connection refused" fixed problem by typing pulseaudio -D in terminal. why would it stop in the first place.

---

### Post by Ng Oon-Ee on 2008-11-30
> **coolethan said:**
> on the left hand side i see                        

Ardour:
-audio1/out1
-audio1/out2
-auditioner/out1
-auditioner/out2
-click/out1
-master/out1
-master/out2
System:
-capture_1
-capture_2

and the right hand side

Ardour:
-audio1/in1
-master/in1
-master/in2
System:
-playback_1
-playback_2


oh and all of a sudden my pulse audio stopped working. when i click on volume control it says "connection failed:connection refused"

Okay, unless you followed the the guides I linked to about getting Pulse to work with JACK, it won't. By default, using the Ubuntu repos, its not possible, you have to download a separate deb to get that working. If you want to do that, we can handle that later.

However, more importantly is getting your recording working. In this Connections box, the left side shows all your sound sources (readable/output ports, meaning they output sound), the right side the targets (writeable/input ports, meaning sound is input to them, pulseaudio calls them sinks). What you need to do is ensure that your 'system' source is connected to your 'ardour' target. So, select 'system' on the left-side and 'ardour' on the right-side and click 'Connect'. You should see a line connecting them, and individual lines connecting capture_1 to master/in1 and capture_2 to master/in2 or something like that. You can manually connect them differently, for example capture_1 and capture_2 may be 2 mics in your computer or the two sides of a stereo input.

Once you're sure they're connected, try to record. If no sound is being recorded, it could be that your mic is totally muted. To check, make sure you have the Volume Control applet in your task bar. Right-click on it and select the 2nd option, Open Volume Control. Under Device, select your hardware device (probably HDA Intel (Alsa mixer) if you're using ALSA for the primary connection to your mic. Then, click 'Preferences' and make sure everything is selected. You should now have a whole bunch of sliders to play with, everything which says Mic should be turned up a bit till you get some signal, after which you can adjust for volume.

---

### Post by coolethan on 2008-11-30
ok i checked everybox that there was in the volume thing and then i went to switches where i noticed that when i checked the box labeled line in the volume bars beside the tracks in ardour went up. this was, i presumed a good sign, however they don't fluctuate with the sound coming into the mic they stay at a constant spot and ardour is still recording silence. all the connections are as they should be in JACK. when i open up the recording volume meter in the pulseaudio applet it shows that there is definately sound going into the mic so it's not like theres a problem there. the problem lies somewhere between pulseaudio and JACK/ardour.

---

### Post by Ng Oon-Ee on 2008-11-30
> **coolethan said:**
> ok i checked everybox that there was in the volume thing and then i went to switches where i noticed that when i checked the box labeled line in the volume bars beside the tracks in ardour went up. this was, i presumed a good sign, however they don't fluctuate with the sound coming into the mic they stay at a constant spot and ardour is still recording silence. all the connections are as they should be in JACK. when i open up the recording volume meter in the pulseaudio applet it shows that there is definately sound going into the mic so it's not like theres a problem there. the problem lies somewhere between pulseaudio and JACK/ardour.

Wait, Pulseaudio applet? Is your Pulseaudio grabbing control of your mic? Because that means it wouldn't be available to JACK, thus not to Ardour.

---

### Post by coolethan on 2008-11-30
i was using the pulse audio applet to determine whether or not the mic was working as JACK runs through pulseaudio if it works for pulse it should work for JACK. quiting the PA applet does not help my cause, there are now volume level bars beside the tracks but they must not be indicating the content coming in through my mic because whether i am playing or not they stay in exactly the same place.

---

### Post by Ng Oon-Ee on 2008-11-30
> **coolethan said:**
> i was using the pulse audio applet to determine whether or not the mic was working as JACK runs through pulseaudio if it works for pulse it should work for JACK. quiting the PA applet does not help my cause, there are now volume level bars beside the tracks but they must not be indicating the content coming in through my mic because whether i am playing or not they stay in exactly the same place.

AFAIK there's no way to get JACK running through Pulse, rather its that Pulse sends and receives from JACK, which connects to the base sound system through ALSA. Which guide did you follow on this? The HOWTOs on this forum which refer to the matter do things as I've just described.

For Pulse, the pulseaudio daemon is always running, even if you quit the applet (the applet is just a control/management entity, not the actual program). To totally quit Pulse its necessary to 'killall pulseaudio' in the terminal.

Try killing Pulse, restarting JACK, and doing your recordings. Make sure the connections are all at the right place.

---

### Post by coolethan on 2008-11-30
i followed the guides that you posted earlier in this thread, just disregard my last post, i am a noob. the system automatically makes all the connections for me and suddenly my computer is lagging inside and outside the program. it's still not recording anyting from the mic but it must be getting input from somewhere because the input meters are going at fullblast volume all the time.

---

### Post by Ng Oon-Ee on 2008-11-30
> **coolethan said:**
> i followed the guides that you posted earlier in this thread, just disregard my last post, i am a noob. the system automatically makes all the connections for me and suddenly my computer is lagging inside and outside the program. it's still not recording anyting from the mic but it must be getting input from somewhere because the input meters are going at fullblast volume all the time.

Okay, I must admit I'm pretty stumped now. If pulseaudio can see and hear your mic (use soundrecorder to check) and its set up according to the guides that means JACK must be working and sending the mic inputs to Pulseaudio. Please check your Pulseaudio sources, your only input device should be Jack Source (PulseAudio JACK Source).

After that, assuming that's working, then in Ardour's settings you have to check what sources are linked, I'm not too sure on that.

Normally when a system lags badly while doing sound-related stuff, it seems to be that some sources of sound are tryingn to write to non-existent sinks (for example, if Rhythmbox is trying to play to Pulse after it has been killed).

---

### Post by coolethan on 2008-12-11
i'm running 8.1 now and i just love how pulse is already set up ready to go, i have jack and ardour, i made a few adjustments in jack and i was able to record stuff! ya, the only problem is that the sounds are horribly garbled beyond recognition. what the heck is going on.

---

### Post by Ng Oon-Ee on 2008-12-11
> **coolethan said:**
> i'm running 8.1 now and i just love how pulse is already set up ready to go, i have jack and ardour, i made a few adjustments in jack and i was able to record stuff! ya, the only problem is that the sounds are horribly garbled beyond recognition. what the heck is going on.

As a general rule, when asking for help with a problem (or describing a solution) please be as verbose as possible. 'Horribly garbled beyond recognition' is good English lit., but not very helpful for diagnosis.

I would assume that you actually mean 'sounds like its being played way too loud on crappy speakers' or something to that effect. If that's the case, I'd suggest reducing the recording volume level. AFAIK JACK cannot do this, and you must adjust the volume level from alsamixer (try running gnome-alsamixer).

Oh, and a small point to note, you're actually running 8.10 (Intrepid Ibex). Meaning the release on 2008, month 10. Not 8.1, which would indicate a January release. Small matter, but I get annoyed seeing plenty of people assuming standard mathematical rules apply to software names (Windows three hundred and eleven being newer than windows 98 was such a crapshoot).

---

### Post by coolethan on 2008-12-11
yes i suppose that is what i meant, playing too loud over crappy speakers, i adjusted the sensetivity directly on my mic but that did nothing and i forgot all about the alsa mixer thing. 

i was unawares that 8.10 meant 2008 tenth month and i didn't think the 0 was very significant. wouldn't a january release be 8.01?

---

### Post by Ng Oon-Ee on 2008-12-11
So did the alsa mixer help?

And yes, its not stated openly anywhere, I had to deduce it by hearing people talk about "maybe that'll come out in 10.10" and "wait 2 years for THAT?" kind of talk. I suppose 8.01 would be the case, since they used 8.04 for April release.

---

### Post by coolethan on 2008-12-11
i downloaded alsa mixer and i don't see any recording volume slider. here's the setup

Master
PCM (whatever that is)
Synth
Line (mute)
CD
Mic (mute)
Phone (mute)
PC speak
Aux (mute)

---

### Post by Ng Oon-Ee on 2008-12-11
Okay, what you're looking at is playback volumes, there should be a way to adjust recording volumes.

Oh wait, hang that, there's a much easier way. If you're using Gnome, just add the Volume Control applet to your panel, right-click it and 'open volume control'. I'm sure there's a command you can input to your terminal to get there directly but I haven't found it yet =p

---

### Post by coolethan on 2008-12-11
i went through all of the devices in the volume control and moved any of the sliders having anything to do with recording down to 50% volume and tried each one out. its still really bad quality, its really buzzy and fuzzy sounding.

---

### Post by Ng Oon-Ee on 2008-12-11
Okay, first try turning all of the sliders to 0% and see if anything gets recorded. If something does, that means you're using an input that somehow does not appear there. Under 'preferences' you should be able to select which inputs appear to be modified.

---

### Post by coolethan on 2008-12-11
ok so all the sliders are at 0 and nothing is getting recorded, the thing is that none of the sliders were at any sort of excessive volume to begin with.

---

### Post by Ng Oon-Ee on 2008-12-11
'Excessive' is relative. 50% is excessive on my system, especially if both mic and mic boost are at 50%. Try raising mic to 50% and then recording. if there's still no sound, raise mic boost just a bit (if you're familiar with music, its sort of like the gain on your guitar amp, too much and you're gonna squeal). I doubt mic boost is needed at all except for really quiet surroundings.

---

### Post by coolethan on 2008-12-11
i am familiar with music, i'm actually getting a new guitar amp in hopefully a week. right so now my H4 doesn't want to connect to my computer for whatever reason. but i'll get it working and implement those changes.

---

### Post by coolethan on 2008-12-12
i've reduced every slider that has anything to do with recording down to just about nothing and it's not making any difference, it could possibly be something within the program that i'm not awares of.

---

### Post by Ng Oon-Ee on 2008-12-12
> **coolethan said:**
> i've reduced every slider that has anything to do with recording down to just about nothing and it's not making any difference, it could possibly be something within the program that i'm not awares of.
So to recap, when you turn all the sliders down, you do not record anything, but increasing the sliders by just a bit gives you the distortion?

I'm not sure how you'd check for hardware problems. Does soundrecorder give the same?

---

### Post by toybay on 2008-12-13
i have audacity (don't know which version) and the sound don't work but the sound works fine on my computer

---

### Post by Ng Oon-Ee on 2008-12-13
> **toybay said:**
> i have audacity (don't know which version) and the sound don't work but the sound works fine on my computer
Its not possible to help you without more information.

Please detail what the error messages (if any) are. Then what steps you have tried. Try googling the error message. Run Audacity from terminal if needed, many programs dump debug info to the terminal. Read some HOWTOs, such as those I've posted earlier in this thread. Audacity WILL NOT WORK by default on an Ubuntu install, but getting it working is just a matter of following instructions already posted, unless you have a hardware problem/out-of-the-normal software setup.

---

### Post by toybay on 2008-12-14
no error messeges come up

---

### Post by Ng Oon-Ee on 2008-12-14
> **toybay said:**
> no error messeges come up
Well, you'll have to try something, noone can help you otherwise.

Did you try running audacity from the terminal? Have you checked out any of the Pulseaudio HOWTOs?

---

