---
title: "[HOW-TO] Pidgin-Rhythmbox 2.0 plug-in"
date: 2007-11-24
forum: Tutorials
---

### Post by borisattva on 2007-11-24
This nifty little plug in will conveniently display your currently played Rhythmbox track in your AIM Profile or Away message, through use of %rb (like %n - name, %t - time, etc)

Dependencies:
[B]pidgin-dev
build-essential[/B]
(possibly others, so please report if you have any errors)

If you haven't already, get the tarball of the plug-in here:
[http://jon.oberheide.org/projects/pidgin-rhythmbox/](http://jon.oberheide.org/projects/pidgin-rhythmbox/)

you can Download it to anywhere but for simplicity of instructions,
it is necessary that you drop it on your Desktop (you can delete it afterwards)

Right-click on the file name pidgin-rhythmbox-2.0.tar.gz and select 'Extract Here'

a Folder 'pidgin-rhythmbox-2.0' will be created.

Open up your Terminal and type:```
cd ~/Desktop
cd pidgin-r*
```

verify that you are in:
username@machine:**~/Desktop/pidgin-rhythmbox-2.0$**

type: ```
./configure
```

If you see any errors, the process will stop. This means that there are still some dependencies that you need to install prior to this step

If you see something like:
** configure: error: Package requirements (*packagename* >=**

go to Synaptic and search for it with 'packagename**-dev**', install it and its dependencies.

Or come here with your error and we'll help you idnetify it.

If you do not see any errors, type: ```
**sudo** make
```

Provide your linux password if necessary.

Once completed type: ```
**sudo** make install
```

Record errors if any.

If you dont see any errors, open up Pidgin and do CTRL+P on your keyboard.
In the preferences window click on Plugins and put a checkmark next to Pidgin-Rhythmbox 2.0, and click Close.

Either in your AIM profile or your away message put ```
%rb
```

Open up Rhythmbox and play a track. Check your away/profile.
If you see the song information there, youre set.
Feel free to customize the message by adding text anywhere around %rb

---

### Post by jcbodnar on 2007-12-04
> Check your away/profile.

How do you do this? I have %rb entered for amy status message. I have rhythmbox playing. When I mouse over the pidgin icon in my tray I see:

Pidgin - %rb

---

### Post by borisattva on 2007-12-04
when you open Pidgin and go into plug ins, do you see Rhythmbox plug in there? If you do, make sure its checked. if you dont, the installation did not complete: exit both rhythmbox and pidgin and rerun the above walk through.

watch the screen for any errors and report back here.

---

### Post by jcbodnar on 2007-12-04
I installed pidgin-rhytmbox from the debian package found here: [http://www.last.fm/group/Rhythmbox/forum/8096/_/310325](http://www.last.fm/group/Rhythmbox/forum/8096/_/310325)

It shows up in the list of plugins, I have it checked and I have all the configuration options checked.

---

### Post by borisattva on 2007-12-04
no idea why its not working. i would only try to use the latest ver packages from the official links.

when you were testing this, did you try to skip through the songs? if the song is already playing when you start pidgin it will only show %rb as you describe.

---

### Post by jcbodnar on 2007-12-04
Yes, I've been listening to music all day and it's always on %rb.

I'll try installing from source.

Thanks for the help.

---

### Post by mpgarate on 2007-12-09
great guide! thanks

I had to install pidgin-dev, but that wasnt a problem

---

### Post by TreeFinger on 2007-12-15
Great guide, I was having a lot of trouble getting it to work. I thought I had installed all the related packages in synaptic but I didn't.. Installing pidgin-dev did the trick!

---

### Post by Chocwise on 2007-12-20
Naw. Didn't work for me.
I have Gutsy, pidgin-dev, I installed build-essential as well.
neither ./configure, nor make or make install are giving any Errors. I checked the Plugin in Pidgin and added %rb to Away-Message. I even restarted Pidgin and Rythmbox. I switched through some Songs, but nothing.
Nice Guide. But didn't do it for me. :/

---

### Post by midtown on 2007-12-21
Thanks, installing pidgin-dev made it work for me in Gutsy!

---

### Post by borisattva on 2007-12-21
> **Chocwise said:**
> Naw. Didn't work for me.
I have Gutsy, pidgin-dev, I installed build-essential as well.
neither ./configure, nor make or make install are giving any Errors. I checked the Plugin in Pidgin and added %rb to Away-Message. I even restarted Pidgin and Rythmbox. I switched through some Songs, but nothing.
Nice Guide. But didn't do it for me. :/

i experienced something like this when i did the install not realizing either rb or pidgin was minimized but running. id give it another go making sure both are off completely.

---

### Post by minhaaj on 2008-07-19
same for me. %rb just won't work. no erros during ./configure sudo make and make install. i restarted everything. checked the plugin checkbox in plugins. ain't working. thanks for the guide though. i learned how to compile from source now :)

---

### Post by lsp@gl on 2008-09-04
Hallo,

I have the same problems like many other. 
```
./configure
```
show no errors but
```
sudo make
Making all in src
make[1]: Betrete Verzeichnis '/home/thomas/Desktop/pidgin-rhythmbox-2.0/src'
/bin/bash ../libtool --silent --mode=link gcc -g -g3 -O2 -Wall -DVERSION=\"2.0\" -g -O2   -o pidgin-rhythmbox.la -rpath /usr/lib/pidgin -module -avoid-version -L/usr/lib/pidgin -lgtk-x11-2.0 -lpurple -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -ldbus-1   -ldbus-glib-1 -ldbus-1 -lgobject-2.0 -lglib-2.0   pidgin_rhythmbox_la-pidgin-rhythmbox.lo  
/usr/bin/ld: cannot find -lpurple
collect2: ld returned 1 exit status
make[1]: *** [pidgin-rhythmbox.la] Fehler 1
make[1]: Verlasse Verzeichnis '/home/thomas/Desktop/pidgin-rhythmbox-2.0/src'
make: *** [all-recursive] Fehler 1

```

cannot find -lpurple. 
Where is the problem and what can I do?

thx

---

### Post by CharonM72 on 2008-09-06
Just for everyone's information, I too had the problem of %rb not changing to the song name and info, but when I asked a friend, he said that he could see it in ym status even though I couldn't (yes I had the checkboxes checked to show the info in my status bar)

It's still a problem, but not as much of one.

---

### Post by cnbs on 2008-10-08
Yes, you are right. It works but you can't see your status changed. To check try to add yourself to your contact list.

---

### Post by Master_Odin on 2008-10-12
Nevermind, great tutorial! :D

---

### Post by Meijuh on 2008-11-23
Hi there,

I would like to see the title of the radio stream I'm listening to.

What do I have to change in the line: '%tile' by %artist ?

Or isn't this possible?

---

### Post by xHero on 2008-12-22
I get the following error:

```
checking for pidgin... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables pidgin_CFLAGS
and pidgin_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I'm using the pidgin that comes with 8.10.

---

### Post by prateek51 on 2008-12-25
> **xHero said:**
> I get the following error:

```
checking for pidgin... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables pidgin_CFLAGS
and pidgin_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I'm using the pidgin that comes with 8.10.

You need to install pidgin-dev
```

sudo apt-get install pidgin-dev

```

---

### Post by josaphat on 2009-01-18
This is more about Rhythmbox than about the pidgin plugin, but in my status I get '[song name]([http://jon.oberheide.org/projects/pidgin-rhythmbox/query.php?lyrics%20%lots%of%URL%STUFF%HERE%ABOUT%MY%SONG](http://jon.oberheide.org/projects/pidgin-rhythmbox/query.php?lyrics%20%lots%of%URL%STUFF%HERE%ABOUT%MY%SONG)' by Artist

I disabled the Lyrics plugin in Rhythmbox already. Should I rebuild the plugin because this was one of the settings? :confused:
Thanks for the help.


**EDIT**
Just figured out what the "problem" was. It's a link that's created in the AIM Profile, but it doesn't hide the URL when looking in the buddy list.

---

### Post by dustyg54 on 2009-01-28
> **Meijuh said:**
> Hi there,

I would like to see the title of the radio stream I'm listening to.

What do I have to change in the line: '%tile' by %artist ?

Or isn't this possible?

I listen to radio streams a lot as well.  On mine, when i type %rb in the away line (or available line, both work for me), and then start the stream in Rhythmbox, it just says what the title of the radio station is under my name in the buddy list.  

Thats cool and all, but if a radio stream provides artist/song names to Rhythmbox, can they be seen on pidgin too somehow?  i currently have 2 streams, one provides artist/song info to Rhythmbox, but the other doesnt.

---

### Post by omega13a on 2009-05-01
> **cnbs said:**
> Yes, you are right. It works but you can't see your status changed. To check try to add yourself to your contact list.

Tried that. It just shows %rb...

---

### Post by gregorej on 2009-05-04
Same here. Pidgin shows just %rb. Plugin is active, compiled without errors. Restarted both rhythmbox and pidgin - still nothing. I am using pidgin 2.5.2 and rhythmbox 0.11.6.

---

### Post by rko618 on 2009-05-27
For people currently looking for this I **strongly recommend** installing pidgin-musictracker via apt-get instead of messing with the Pidigin-Rhythmbox plugin. 

Pidgin-musictracker is a newer plugin and supports a wide variety of music players not just Rhythmbox. In addition the configuration options are much nicer.

---

### Post by loweehahn on 2009-06-10
kelvin@ubuntu:~$ cd ~/Desktop
kelvin@ubuntu:~/Desktop$ cd pidgin-r*
kelvin@ubuntu:~/Desktop/pidgin-rhythmbox-2.0$ 
kelvin@ubuntu:~/Desktop/pidgin-rhythmbox-2.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for pidgin... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables pidgin_CFLAGS
and pidgin_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

kelvin@ubuntu:~/Desktop/pidgin-rhythmbox-2.0$ sudo make
[sudo] password for kelvin: 
make: *** No targets specified and no makefile found.  Stop.
kelvin@ubuntu:~/Desktop/pidgin-rhythmbox-2.0$ sudo make install
make: *** No rule to make target `install'.  Stop.
kelvin@ubuntu:~/Desktop/pidgin-rhythmbox-2.0$ 

This is what showed in the terminal. What should I do next?

---

### Post by kevdog on 2009-06-10
Do you need the pidgin sources to compile this?

---

### Post by loweehahn on 2009-06-10
I don't know. I just want to get the plugin working that's it. Please help me.

---

### Post by gunbladeiv on 2009-06-14
There are a plugin to display current track played in rhythmbox.  It's called pidgin-musictracker which is in ubuntu repositories. just ```
apt-get install pidgin-musictracker
``` and tick to enable the plugin. it's easier and no need to compile.

---

### Post by loweehahn on 2009-06-14
I tried but can't. Here's the result:

kelvin@ubuntu:~$ apt-get install pidgin-musictracker
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I login as root and tried again but the same message appeared.

---

### Post by billynomates on 2009-09-12
> **rko618 said:**
> For people currently looking for this I **strongly recommend** installing pidgin-musictracker via apt-get instead of messing with the Pidigin-Rhythmbox plugin. 

Pidgin-musictracker is a newer plugin and supports a wide variety of music players not just Rhythmbox. In addition the configuration options are much nicer.

I second this! It's simple as hell, and has a nice GUI to edit your statuses with.

Don't bother with all that other crap :)

---

### Post by lads on 2012-09-21
> **borisattva said:**
> 
Either in your AIM profile or your away message put ```
%rb
```


I can't find neither on any of the menus (Pidgin 2.10.3). Could you be more specific on where are these settings tweaked?

Thank you.

---

