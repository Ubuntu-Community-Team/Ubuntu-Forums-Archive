---
title: "HowTo: Use your mobile phone as a remote control for your Ubuntu system"
date: 2007-01-18
forum: Tutorials
---

### Post by elektronaut on 2007-01-18
Have you ever been attending presentations envying all the time the guy in front using his mobile phone to switch the slides? Or dreamed of sitting on the sofa and controlling your music player without having to go to the computer?
At least I did and so I searched on the net for possible solutions. Most of the projects are either outdated, only work for certain phones or certain software on the computer. Finally I discovered anyremote from Mike Fedotov, which you can download from the project's site at sourceforge: 

[http://sourceforge.net/projects/anyremote/](http://sourceforge.net/projects/anyremote/)

The great thing is that it works for different connections like bluetooth, infrared or serial cable (though I only tested bluetooth) and, according to the project notes, for all kinds of phones. Several configuration files for different software, e.g. amarok, xmms, etc. are included, and it is easy to write new ones. 

[SIZE="2"]**NB:**[/SIZE] [LIST]
[*]This was tested on Ubuntu 6.10 (32bit).
[*]There is also the KDE version kAnyRemote, which provides a little panel applet to change configuration files. I also tried this flavor, as I have KDE installed. But I'll focus on anyremote, the CLI version, as it has the same functionality, and you don't need to install any KDE libraries.
[*]I only describe using bluetooth and assume you have already set up a bluetooth connection between your computer and your phone.
[*]I assume you have a java enabled phone (JSR-82), I haven't investigated yet how this works if your phone doesn't support java. 
[*][COLOR="Blue"]*This post will be edited if questions or suggestions come up.*[/COLOR]
[/LIST]
[SIZE="2"]**Steps to take:**[/SIZE]
[LIST=1]
[*]**Install dependencies**
I can't tell you exactly what you need, because I encountered only one missing package, and that was *libbluetooth-dev*. I guess you need the bluetooth libraries for compilation even if you'll use another kind of connection. So I'll simply list all the blue* packages that are installed on my system. Corrections considering unnecessary packages or missing packages are welcome! You can either use synaptic or aptitude or apt-get on the command line to install the packages, so for instance you have to enter: ```
$ sudo aptitude install checkinstall *gcc build-essential other_missing_packages*
```
[LIST]
[*]gcc
[*]build-essential
[*]bluetooth
[*]bluez-cups
[*]bluez-hcidump
[*]bluez-passkey-gnome
[*]bluez-pin
[*]bluez-utils
[*]gnome-bluetooth
[*]libbluetooth2
[*]libbluetooth2-dev
[/LIST]

[*]**Install anyremote**
In case you have already compiled from source code before, this is nothing new to you. If not: Don't be afraid, there is no dark magic involved ;-) After downloading anyremote-*.tar.gz, go to the download directory, decompress the file, change to the now extracted directory and prepare for installation:
```
$ tar xvzf anyremote-*.tar.gz
$ cd anyremote-*
$ ./configure
$ make

```
Now, I advise you to have checkinstall installed, this will allow you to easily remove anyremote later on. ```
$ sudo aptitude install checkinstall
```
We install it:
```
$ sudo checkinstall
*or, if checkinstall is not available*
$ sudo make install
```
[*]**Install the Java client**
The anyremote directory we extracted earlier contains the phone client file anyRemote.jar. Install this on your phone, either by sending it via bluetooth or by using a data cable.
[/LIST]
Now, using an existent bluetooth connection, we can start anyremote and indicate which configuration file to use:
```
$ anyremote -f  anyremote-2.6/cfg-examples/Server-style/adminExample.cfg &
```
Finally we start the java application on the phone, connect to the computer, and **[COLOR="Red"]have fun![/COLOR]**
The author is very cooperative and likes to hear from you if you used his program successfully with a phone not yet on his list on this page: [http://anyremote.sourceforge.net/doc-html/intro.html](http://anyremote.sourceforge.net/doc-html/intro.html). But let's try to keep questions concerning installation and such here in the forum.

---

### Post by BatteryCell on 2007-01-18
Nice tutorial :-)

I installed it on my phone just like you said (I did kanyremote).  I start the service on my computer and then I move to the phone and start the java.  It searches and finds my computer, then I click connect but it doesn't do anything. it just sits there and thinks.

Any suggestions?

---

### Post by elektronaut on 2007-01-19
Did you manage to have a working bluetooth connection before, e.g. for sending files? Which configuration file did you use? What says /tmp/kanyremote.log?

---

### Post by BatteryCell on 2007-01-19
I used the obex file transfer to get the java prog to my phone, so yes. I used the configuration file that you suggested, adminExample.cfg, and the log file does give a bunch of repeated errors/info along the lines of:
```

[Thu Jan 18 20:43:21 2007] - ERROR - error writing to socket
[Thu Jan 18 20:43:21 2007] - DEBUG - Fails in writeSocketConn() (Set)
[Thu Jan 18 20:47:14 2007] - DEBUG - KAnyRemote::doQuit()
[Thu Jan 18 20:47:14 2007] - DEBUG - freeCfg()
[Thu Jan 18 20:47:14 2007] - DEBUG - freeCfg() OK

```

Thats probably what is not letting it connect, but what do I do to fix it lol?

---

### Post by elektronaut on 2007-01-20
I don't have enough experience with bluetooth to suggest a solution. For me everything worked fine except some little problems in earlier versions. Hopefully somebody else has an idea, or you might try to contact the author. Sorry.

---

### Post by Rule on 2007-01-20
nice project but it doesn't work with my Nokia 6265i :(

---

### Post by elektronaut on 2007-01-21
> **Rule said:**
> nice project but it doesn't work with my Nokia 6265i :(
Strange, because [http://www.phoneslim.com/nokia-6265i-information.html](http://www.phoneslim.com/nokia-6265i-information.html) says it would support JSR-82. What's the problem?

---

### Post by elektronaut on 2007-01-21
> **BatteryCell said:**
> I used the obex file transfer to get the java prog to my phone, so yes. I used the configuration file that you suggested, adminExample.cfg, and the log file does give a bunch of repeated errors/info along the lines of:
...
Thats probably what is not letting it connect, but what do I do to fix it lol?
Did you try again after a reboot? Maybe something is still registered exclusively in some way for the bluetooth port?

---

### Post by mike_mike on 2007-01-22
Hi all !

I'm the author of kAnyRemote.
In case of questions send me e-mail with description of the problem  and attached log file (/tmp/kanyremote.log)  and cfg.file used. 
Hope i could clarify situation for You.

Mike

---

### Post by mike_mike on 2007-01-22
Please send me log and cfg files.

---

### Post by rama on 2007-01-23
Anybody got a deb they 'd like to share cause I m trying to build the application and I get this: 
```
anyremote-2.6$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
```

---

### Post by Rule on 2007-01-23
> **elektronaut said:**
> Strange, because [http://www.phoneslim.com/nokia-6265i-information.html](http://www.phoneslim.com/nokia-6265i-information.html) says it would support JSR-82. What's the problem?

on my laptop it's like I can only either have Bluetooth on and Wireless Off (or the other way around) so thats quite annoying, and ubuntu can't always find my phone. sometimes it will find it and work and other times not even notice it. 

I will try again, i'm also having the same problem as  rama.

EDIT: also when I copy the .jar file over to my phone I get "Application no supported. Delete?"

---

### Post by mike_mike on 2007-01-24
Could You please try:
automake
aclocal
autoconf
before ./configure

or copy absent files from automake package (on my FC it is /usr/share/automake-1.9/install-sh)

---

### Post by rama on 2007-01-24
I installed the automaka package and tried your suggestion but still :
```
$ automake
automake: configure.in: required file `./install-sh' not found
automake: configure.in: required file `./mkinstalldirs' not found
automake: configure.in: required file `./missing' not found
automake: configure.in: required file `./config.guess' not found
automake: configure.in: required file `./config.sub' not found
$ aclocal
$ autoconf
$ ./configure
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."

```

This is not the first time that I compile something from source (although I am far from a guru) and it does not make sense. This is the output of ls -l in the dir I'm executing the commands (in case something is wrong with the path I m in or the gz I downloaded):

CODE]$ ls -l
total 424
-rw-r--r-- 1 username username  41102 2007-01-24 22:58 aclocal.m4
-rw-r--r-- 1 username username    721 2007-01-17 19:05 anyRemote.jad
-rw-r--r-- 1 username username  64924 2007-01-17 19:05 anyRemote.jar
-rw-r--r-- 1 username username   1069 2007-01-14 16:26 anyremote.spec
-rw-r--r-- 1 username username     31 2006-12-26 13:51 AUTHORS
drwxr-xr-x 2 username username   4096 2007-01-24 22:58 autom4te.cache
drwxr-xr-x 5 username username   4096 2007-01-10 16:50 cfg-examples
-rw-r--r-- 1 username username     14 2006-12-26 13:51 ChangeLog
-rw-r--r-- 1 username username   2901 2007-01-24 22:58 config.log
-rwxr-xr-x 1 username username 182156 2007-01-24 22:58 configure
-rw-r--r-- 1 username username    823 2006-12-26 13:51 configure.in
-rw-r--r-- 1 username username  18009 2006-12-26 13:52 COPYING
lrwxrwxrwx 1 username username     31 2007-01-24 01:00 depcomp -> /usr/share/automake-1.9/depcomp
drwxr-xr-x 3 username username   4096 2007-01-14 16:04 doc-html
-rw-r--r-- 1 username username    287 2006-12-26 13:51 INSTALL
lrwxrwxrwx 1 username username     34 2007-01-24 01:00 install-sh -> /usr/share/automake-1.9/install-sh
drwxr-xr-x 2 username username   4096 2006-12-26 13:51 keymaps
-rw-r--r-- 1 username username  18489 2007-01-17 07:46 Makefile
-rw-r--r-- 1 username username     14 2006-12-26 13:51 Makefile.am
-rw-r--r-- 1 username username  10295 2007-01-24 22:58 Makefile.in
lrwxrwxrwx 1 username username     31 2007-01-24 01:00 missing -> /usr/share/automake-1.9/missing
-rw-r--r-- 1 username username   4584 2007-01-14 16:24 NEWS
-rw------- 1 username username     90 2006-12-26 13:51 nohup.out
-rw-r--r-- 1 username username   1253 2006-12-26 13:51 README
drwxr-xr-x 3 username username   4096 2007-01-17 19:05 src
-rw-r--r-- 1 username username      1 2006-12-26 13:51 TODO
-rw-r--r-- 1 username username     15 2007-01-14 16:24 VERSION
[/CODE]

I downloaded the kanyremote gz and run ./configure and it run fine (but I had some missing libs in that case which I cant install cause I 'm using some extra repos and all hell will break loose!)

PS: Thx for being so supportive!:smile:

---

### Post by deNniZ on 2007-01-24
anyremote works on my pc, but not on my symbian s60 phone it's a "nokia n-gage" NEM-4, it's stuck in installing Java Program, and quits then with unknown error.

---

### Post by mike_mike on 2007-01-25
Since anyRemote have limited suport of Bemused clients You can try Bemused symbian client
even if Java Client of anyRemote does not works ;-)

---

### Post by mike_mike on 2007-01-25
To clarify situation... 
Does configure works well for You in v2.7 ?
Does file /usr/share/automake-1.9/install-sh present on Your system ?

>automake: configure.in: required file `./config.sub' not found
Does You run automake with -a ??
automake -a

In case of failure with kAnyRemore You can try anyRemote anyway (it did not depends
on KDE at all and provide the same functionality)

---

### Post by GI-Orca on 2007-01-25
Hi to all!

First I want to thank Mike for his great work.

I am using the cli version (2.4)  on my edgy/gnome -box & 6280 nokia with some (rough) adaptions to cooperate with rhythmbox/dbus(attached). Today I wanted to upgrade to 2.7 but unfortunately the newest version of the java client crashes with 
"Null Pointer java/lang/NullPointerException"
 although the 2.6 Version client did work. 
I am not really familiar with programming so I fear the client sources. 
Help would be appreciated

Orca

---

### Post by rama on 2007-01-25
Ok. I realized that by executng "sudo apt-get install automake" I got automake-1.4 installed and the link of your install-sh file was on .../automake-1.9/install-sh. I haven't got the slightest idea why this has happend since I didn't specify a version ... 
So after installing automake version 1.9 ./configure ran fine, make ran fine but I get and error with sudo checkinstall :
```
Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/jsar/Desktop/anyremote-2.7/src'
make[2]: Entering directory `/home/jsar/Desktop/anyremote-2.7/src'
/bin/bash ../mkinstalldirs /usr/local/bin
/bin/bash: ../mkinstalldirs: No such file or directory
make[2]: *** [install-binPROGRAMS] Error 127
make[2]: Leaving directory `/home/jsar/Desktop/anyremote-2.7/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jsar/Desktop/anyremote-2.7/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
Like I said I 'm far from an expert and I dont know how make install works but I 'm guessing that when checkinstall calls make install some directory is not found and that crashes the process. It may be due to slight distribution differences in directory organization. Is there anything I can do to fix it? :confused: 

PS: I didn't execute sudo make install cause I don't know which files will be installed in which directories and if something goes wrong I don't know how to clean it up.

EDIT: I tried running the app directly from the src and it works... no sorry ... IT ROCKS! IT IS GREAT! Still I would be very interested in creating a deb file and uploading it to the forum for other people to be able to install it easily.

---

### Post by elektronaut on 2007-01-25
I don't know why you get these errors, 'cause the installation of version 2.7 just ran fine on my Edgy. I attach the debian package generated by checkinstall which you can install like this: ```
sudo dpkg -i anyremote_2.7-1_i386.deb
```

---

### Post by rama on 2007-01-25
Thank you:D

---

### Post by mike_mike on 2007-01-26
Did You run configure with --prefix option ?
./configure --prefix=.... ?
Run ./configure --help to see the help.

Anyway, You can use anyremote from the src without any problem.

By tha way, which phone (manufacturer/model) do You use ?

---

### Post by mike_mike on 2007-01-26
Did Java Client v2.7 works fine or crashes  on Your phone ?

---

### Post by mike_mike on 2007-01-26
Umm... When it crashed ?
At the load stage ? At connect stage ? After connect ? When You press some button ? (which one ?)
Could You please send to me logs (/tmp/*anyremote.log) ?

---

### Post by mike_mike on 2007-01-26
Remarks about *cfg:

* #=%Timer(id1, 20, 0, status, /home/orca/dbustest.py.py --elapsed);
% should be the _first_ symbol in line

7=ExecAndSet(/home/orca/dbustest.py --previous; sleep.2 /home/orca/dbustest.py --song)
IMHO it should be 
7=ExecAndSet(title,........)

---

### Post by mike_mike on 2007-01-26
>it's stuck in installing Java Program, and quits then with unknown error
By the way, did You try to install other Java application ? 
Did You use Nokia Suite to instal Java App ?

---

### Post by GI-Orca on 2007-01-26
Hi!

The Phone is givining the exception on loading the programm (v2.7).
I just sent the jar file over with bluetooth, did work for previous versions.
There are no errors or additional info in the anyermote.log

---

### Post by rama on 2007-01-26
> **mike_mike said:**
> Did You run configure with --prefix option ?
./configure --prefix=.... ?
Run ./configure --help to see the help.

Anyway, You can use anyremote from the src without any problem.

By tha way, which phone (manufacturer/model) do You use ?
Er no I didn't try that. Dont know what it does! Will try it!
My mobile is a Nokia 6230. Of all the cfgs I tried (not much) the one that is supposed to move the mouse did not work (I'll send you a log or something as soon as I get back from work). Amarok worked great!

---

### Post by mike_mike on 2007-01-26
Try to add Set(debug,on) to the (Connect) line. 
Then send me error message if it will be shown

---

### Post by GI-Orca on 2007-01-26
I am not sure if I was meant :o 

Adding
>Set (debug, on)
to my cfg did not bring any change

cu

---

### Post by mike_mike on 2007-01-26
Could You please, try development version v2.8-alpha ?

---

### Post by mike_mike on 2007-01-26
Updated version of v2.8-alpha here. I've corrected somesuspicious places )

---

### Post by mike_mike on 2007-01-26
One more v2.8-alpha(3) ...
Hope the last one )

---

### Post by GI-Orca on 2007-01-26
Client is working for me again thank you very much

---

### Post by mike_mike on 2007-01-27
By the way, there is  cfg.file for Rhytnmbox

---

### Post by GI-Orca on 2007-01-27
rhytmbox.cfg: After adding the other aliases working delightfully well ...

---

### Post by phormion on 2007-01-27
> **rama said:**
> Ok. I realized that by executng "sudo apt-get install automake" I got automake-1.4 installed and the link of your install-sh file was on .../automake-1.9/install-sh. I haven't got the slightest idea why this has happend since I didn't specify a version ... 
So after installing automake version 1.9 ./configure ran fine, make ran fine but I get and error with sudo checkinstall :


Rama, I haven't used anyremote, but setting up a source package built using autoconf and automake is pretty standard. If you run: 

```

$ autoreconf -fvi

```

All the auto/ac* tools that have to be run will be run (autoreconf is smart enough to figure that out), and also the relevant scripts like mkinstalldirs.sh will be **copied** (without -i, only symlinks to the location in /usr/share/... are created). So, using the following sequence: 

```

$ autoreconf -fvi
$ ./configure *list_of_options*
$ make
$ sudo checkinstall

```

should do the trick for you, I think.

Note: this works in automake 1.9, I haven't tried it in earlier versions, which might not even have autoreconf.

---

### Post by rama on 2007-01-28
That did the trick. Txh. 
Mike I was wrong about the mouse feature not working. I haven't installed the extra application that this function requires so it naturally did not work

---

### Post by bodhi.zazen on 2007-02-01
Nice How-to

This thread has been added to the UDSF wiki.

[Mobile_phone_as_a_remote_control](http://doc.gwos.org/index.php/Mobile_phone_as_a_remote_control)

---

### Post by PsychedelicReaction on 2007-02-28
i got a problem in make (kubuntu feisty):

```
michele@michele-laptop:~/Desktop/anyremote-2.8$ make
Making all in src
make[1]: Entering directory `/home/michele/Desktop/anyremote-2.8/src'
gcc -DPACKAGE_NAME=\"AnyRemote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"0.3\" -DPACKAGE_STRING=\"AnyRemote\ 0.3\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyRemote\" -DVERSION=\"0.3\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.     -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT btio.o -MD -MP -MF .deps/btio.Tpo -c -o btio.o btio.c
btio.c:37:33: error: bluetooth/bluetooth.h: No such file or directory
btio.c:38:30: error: bluetooth/rfcomm.h: No such file or directory
btio.c: In function ‘openSocketPort’:
btio.c:298: error: storage size of ‘bt_addr’ isn’t known
btio.c:318: error: ‘BTPROTO_RFCOMM’ undeclared (first use in this function)
btio.c:318: error: (Each undeclared identifier is reported only once
btio.c:318: error: for each function it appears in.)
btio.c:351: error: ‘BDADDR_ANY’ undeclared (first use in this function)
btio.c:298: warning: unused variable ‘bt_addr’
btio.c: In function ‘listenAndAcceptSocketConn’:
btio.c:397: error: storage size of ‘bt_addr’ isn’t known
btio.c:398: error: ‘bdaddr_t’ undeclared (first use in this function)
btio.c:398: error: expected ‘;’ before ‘ba’
btio.c:449: warning: implicit declaration of function ‘baswap’
btio.c:449: error: ‘ba’ undeclared (first use in this function)
btio.c:451: warning: implicit declaration of function ‘batostr’
btio.c:451: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
btio.c:397: warning: unused variable ‘bt_addr’
make[1]: *** [btio.o] Error 1
make[1]: Leaving directory `/home/michele/Desktop/anyremote-2.8/src'
make: *** [all-recursive] Error 1

```

---

### Post by elektronaut on 2007-03-01
I don't have any problems with 2.8 on Edgy. Did you check if you have the libraries installed which are mentioned in my first post?

---

### Post by georgie on 2007-03-04
This worked here on my debian etch (ppc) ibook - both the howto and the app iself.

It's great! I'm cooking whilst fast forwarding amarok :)

Using nokia 6233.

I couldn't get bemused to work, but used server-style and amarok.cfg

Hurrah, thanks to the authors of the howto and the app.

---

### Post by herbster on 2007-03-10
Anyone gotten this to work on a Treo? I have a Treo 650 and when I transfer the anyremote.jar file over, it sends to my phone but upon completion says "File received in an unknown format" and the file doesn't stay on my phone, I can't access it or anything. So I've gotten everything up to getting the dang anyremote.jar file to get onto my Treo so I can run it :( :(

---

### Post by mike_mike on 2007-03-10
But did Treo supports Java ? Do Yoy use any other Java apps on Treo ?

---

### Post by mike_mike on 2007-03-10
It needs to install development packege(s) for Blues.

---

### Post by cold_fu5ion on 2007-03-10
Hey all,
I get an error when trying to compile anyremote. 
When I ./configure I get "missing install-sh" the file is there with a picture of a padlock and a broken link icon next to it, as with two other files in the archive.

Has anyone else come across this or know how I can fix it?

Thanks.

---

### Post by herbster on 2007-03-10
> **mike_mike said:**
> It needs to install development packege(s) for Blues.

What? You mean for the Treo? If so, where can I get them from please?

---

### Post by mike_mike on 2007-03-11
No. 
The question was: does Treo supports Java ?
Do You previously upload any java apps to treo ?

---

### Post by mike_mike on 2007-03-11
This question was already discussed in this thread.
In shorts:
1.You can install automake-1.8
2.or run autoreconf

---

### Post by cold_fu5ion on 2007-03-11
Hi again,
I worked out the problem, I should have read the entire topic first! I just installed automake-1.9 as thats what the files were linking to. Oddly enough it installed to the wrong directory so I ended up copying the install-sh and other missing files into the anyremote directory.

Now that it is installed I'm haivg another problem. I cant get it to run. at all :( 
When I type this in terminal: 
```
anyremote -f  anyremote-2.9/cfg-examples/Server-style/adminExample.cfg
```
(chaning the anremote-2.6 to 2.9)

I get this.........

```
CFG: Use cfg file >anyremote-2.9/cfg-examples/Server-style/adminExample.cfg<
ERROR: Fails in init_cfg()
```

Any idea what this means or how I can get it running?

---

### Post by mike_mike on 2007-03-11
It seems anyremote just can't find cfg file.
Try to use absolute path(/..../adminExample.cfg) or try to use any other cfg file.
Then inspect /tmp/anyremote.log file for some error messages (make sure there is a line Log=true in cfg file)

---

### Post by herbster on 2007-03-11
The Treo is capable of running Java, yes!

---

### Post by mike_mike on 2007-03-11
If Treo is capable of running Java, then upload java client like any other java app
But did Treo JSR82-compatible ?

---

### Post by cold_fu5ion on 2007-03-13
For some reason that I can't figure out anyremote was compiled but is just sitting in /usr/local/bin by itself, it doesnt even have a folder to itself. I have no idea how that happened.

mike_mike , you were 100% right that it couldnt find the cfg file, I pointed it to the folder where the source (and cfg) files extraced to and it worked.
 Thanks for the help! :)  great little app.

---

### Post by Daniel15 on 2007-03-13
I compiled the application successfully, but can't seem to get my Sony Ericsson Z550i to connect. When I start the Java client, it says "Unconnected" at the top of the screen. I press the second softkey (More) and choose "Search". It says "Searching..." for a while, and then returns "Done." I'm not sure what to do after this...

It's getting here late now, so I may be doing something wrong. I'll read through the documentation again tommorow, and try to figure it out :)

---

### Post by mike_mike on 2007-03-14
Umm... a couple of questions:
Did You start anyremote on Your PC ?
Did You choose cfg.file from Server-style directory ?
Is any error reported in /tmp/*anyremote.log ?
Did You try to connect to the phone by minicom or cu ?

---

### Post by mike_mike on 2007-03-14
configure --prefix=.... ??

---

### Post by Cheizzz on 2007-03-20
You should list Automake 1.9 as a dependancy.

---

### Post by ricpersi on 2007-04-03
hi all, I'm new to this forum.. would it be hard for someone to make a deb for the latest anyremote version?
sorry if I'm asking something that cannot be done..

regards,

  riccardo

---

### Post by vilto on 2007-04-05
i was unable to install the anyremote.jar file in my n-gage qd......... any ideas???
is t5here a sis file available? for this

---

### Post by mike_mike on 2007-04-09
Sorry..There is no sis file (

---

### Post by fanoodlehey on 2007-04-14
I have installed kanyremote using ./configure, make and checkinstall

~$ sudo aptitude search kanyremote
i   kanyremote                                                             - kanyremote allows the use of many mobiles to control various apps via bluetooth

But for some reason neither kanyremote or anyremote are recognised commands.
bash: kanyremote: command not found

Any ideas what I've done wrong?

---

### Post by elektronaut on 2007-04-14
> **fanoodlehey said:**
> 
But for some reason neither kanyremote or anyremote are recognised commands.
bash: kanyremote: command not found
What do ```
locate kanyremote
``` and ```
echo $PATH
``` say? The path to the binary seems not be stored in the system's PATH environment variable.

---

### Post by fanoodlehey on 2007-04-15
OK so it looks like kanyremote is in /usr/local/kde/bin/kanyremote

And PATH does not have that location.
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

What's the best thing to do here. Add /usr/local/kde/bin to PATH or move kanyremote?

---

### Post by elektronaut on 2007-04-15
I would either add an entry in the Gnome application starter menu with the full path to the executable or add the /usr/local/kde/bin/ to the PATH. The latter is better if you are going to use other KDE applications that might be installed into that directory. This way they all will be known to the system.

---

### Post by koshari on 2007-05-12
i can paste  a checkinstall 2.11 deb compiled for feisty if you like but you will still need the config files that are in the tarball. pasted in your home directory. you will likey need all the other dependencies (listed throughout this post) as well for it to work.

initially i also had some errors, 

i renamed install to install.sh and installed checkinstall and then the deb compiled.

heres my launcher line for amarok, obviously you change the cfg file for the app you will want to contro and your home directorys name.

```
anyremote -f /home/[COLOR="Red"]<insert_your_home_directory_name_here>[/COLOR]/anyremote-2.11/cfg-examples/Server-mode/amarok.cfg &
```

and heres a tarball with the deb, source and config files to be placed in your home directory.

---

### Post by mike_mike on 2007-05-23
v2.12 is out

---

### Post by sad_iq on 2007-06-21
Works great(amarok at least) here using v2.12. ...however if you have long filenames in the playlist my phone(Motorola V6) responds a little slow...Anyway...great job done!!!
 Also the ```
anyremote -f  anyremote-2.6/cfg-examples/Server-style/adminExample.cfg &
``` should be ```
anyremote -f anyremote-2.12/cfg-examples/Server-mode/adminExample.cfg &
``` just for the ones that like to copy-paste without reading(like me :D)
 Ps: I have some spanish characters in the filenames of my songs(like ñ, í, ò...)...and the client displays something else!! Don't know if it's my fault or what...Maybe someone can test(fix) it!!!

---

### Post by mike_mike on 2007-07-10
Thank You for findings.
Hope problems with spanish characters will be solved in upcoming v3.0

---

### Post by herbster on 2007-07-10
Okay I got everything working, installed anyRemote.jar on my Treo 650 but when I went to launch it I got an error that said:

```
javax.bluetooth.DiscoveryListener
```

I then output the details to a memo and this is what it gave:

```
ava.lang.NoClassDefFoundError: javax.bluetooth.DiscoveryListener
	at java.lang.Class.forNameImpl(Native Method)
	at java.lang.Class.forName(Unknown Source)
	at javax.microedition.lcdui.AppManager.launch(Unknown Source)
	at javax.microedition.lcdui.AppManager.main(Unknown Source)
```

Damn, came so close, any ideas?

---

### Post by elektronaut on 2007-07-11
The DiscoveryListener is part of JSR 82, see [http://java.sun.com/javame/reference/apis/jsr082/javax/bluetooth/DiscoveryListener.html](http://java.sun.com/javame/reference/apis/jsr082/javax/bluetooth/DiscoveryListener.html). It seems as if the Java environment on your Treo doesn't support JSR 82. You should try to find out which JVM is installed and check out if you can install another one.

---

### Post by Daniel15 on 2007-07-17
> **Daniel15 said:**
> I compiled the application successfully, but can't seem to get my Sony Ericsson Z550i to connect. When I start the Java client, it says "Unconnected" at the top of the screen. I press the second softkey (More) and choose "Search". It says "Searching..." for a while, and then returns "Done." I'm not sure what to do after this...

It's getting here late now, so I may be doing something wrong. I'll read through the documentation again tommorow, and try to figure it out :)

Just as an update, I tried this again today (on Feisty, I was previously using Edgy), and it worked perfectly. I'm now controlling AmaroK via my phone :D

To the author: Excellent work! I absolutely love this, it's really cool :D

---

### Post by budimagelang on 2007-07-19
I'm use Sony Ericsson K510i. And it's work with Desknote ECS A535 with Ubuntu 7.04. My Bluetooth Cryptonix.

I'm reading this forum 3 hour ago, then try, and success.

But, most of cfg file is for KDE (KUBUNTU). How to make/build cfg file for UBUNTU? (like mplayer)

Last, I so sorry for my english. I'm Indonesian. I Just a teacher ITC in a High School.

---

### Post by purfier on 2007-07-19
purfier@dreamMedia:~$ CFG: Use cfg file >./anyremote-2.12/cfg-examples/Server-mode/amarok.cfg<
INFO: log file is /tmp/anyremote.log.purfier
Serial Port service registered
ERROR: Couldn't attach to DCOP server!
: cannot connect to X server
ERROR: Couldn't attach to DCOP server!
ERROR: Couldn't attach to DCOP server!
ERROR: Couldn't attach to DCOP server!


And the app does not respond to what I press on my phone, stop,play etc.

---

### Post by purfier on 2007-07-19
(rhythmbox-client:7181): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session

(rhythmbox-client:7187): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session

(rhythmbox-client:7191): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session

(rhythmbox-client:7197): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session

(rhythmbox-client:7203): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session
INFO: Wait 5 seconds to connect ...


dont know what error it is, but cant control ryhtmbox ...

---

### Post by mike_mike on 2007-07-23
Do You use KDE ? DCOP works only if You run KDE.

---

### Post by mike_mike on 2007-07-23
2 purfier: 
Which distro do You use ? 
Gnome or KDE (or some other window manager)?
Did You managed al least some cfg.files works for You ?

---

### Post by mike_mike on 2007-07-23
2 budimagelang:
>How to make/build cfg file for UBUNTU? (like mplayer)
The syntax of cfg.file is the SAME ... You have to find out the way to control You app from console. 
Then You will be able to write some script wrapper to make remote control. 
Read the FAQ page on [http://anyremote.sf.net](http://anyremote.sf.net)

---

### Post by Daniel15 on 2007-07-28
> **mike_mike said:**
> Do You use KDE ? DCOP works only if You run KDE.

This is not true... I'm using DCOP fine with GNOME ;)
Amarok is not only a KDE player... It works perfectly fine under GNOME as well :)

---

### Post by zuzuzzzip on 2007-08-08
what socket should i use?

I thought socket://bluetooth:10 but doesn't seem to work...
log:
```
CFG - [Mode] default
CFG -     61441 = ExecAndSet(title<|>,nokiafn 61441);ExecAndSet(status<|>,nokiafn title);
CFG -     241 = ExecAndSet(title<|>,nokiafn 241);ExecAndSet(status<|>,nokiafn title);
CFG -     32 = ExecAndSet(title<|>,nokiafn 32);ExecAndSet(status<|>,nokiafn title);
CFG -     231 = ExecAndSet(title<|>,nokiafn 231);ExecAndSet(status<|>,nokiafn title);
CFG -     -50 = ExecAndSet(title<|>,nokiafn -50);ExecAndSet(status<|>,nokiafn title);
CFG -     0 = ExecAndSet(title<|>,nokiafn 0);ExecAndSet(status<|>,nokiafn title);
CFG -     46 = ExecAndSet(title<|>,nokiafn 46);ExecAndSet(status<|>,nokiafn title);
CFG -     44 = ExecAndSet(title<|>,nokiafn 44);ExecAndSet(status<|>,nokiafn title);
CFG -     110 = ExecAndSet(title<|>,nokiafn 110);ExecAndSet(status<|>,nokiafn title);
CFG -     98 = ExecAndSet(title<|>,nokiafn 98);ExecAndSet(status<|>,nokiafn title);
CFG -     99 = ExecAndSet(title<|>,nokiafn 99);ExecAndSet(status<|>,nokiafn title);
CFG -     120 = ExecAndSet(title<|>,nokiafn 120);ExecAndSet(status<|>,nokiafn title);
CFG -     122 = ExecAndSet(title<|>,nokiafn 112);ExecAndSet(status<|>,nokiafn title);
CFG -     9 = ExecAndSet(title<|>,nokiafn 9);ExecAndSet(status<|>,nokiafn title);
CFG -     108 = ExecAndSet(title<|>,nokiafn 108);ExecAndSet(status<|>,nokiafn title);
CFG -     1 = ExecAndSet(title<|>,nokiafn 1);ExecAndSet(status<|>,nokiafn title);
CFG -     115 = ExecAndSet(title<|>,nokiafn 115);ExecAndSet(status<|>,nokiafn title);
CFG -     97 = ExecAndSet(title<|>,nokiafn 97);ExecAndSet(status<|>,nokiafn title);
CFG -     112 = ExecAndSet(title<|>,nokiafn 112);ExecAndSet(status<|>,nokiafn title);
CFG -     111 = ExecAndSet(title<|>,nokiafn 111);ExecAndSet(status<|>,nokiafn title);
CFG -     105 = ExecAndSet(title<|>,nokiafn 105);ExecAndSet(status<|>,nokiafn title);
CFG -     121 = ExecAndSet(title<|>,nokiafn 121);ExecAndSet(status<|>,nokiafn title);
CFG -     116 = ExecAndSet(title<|>,nokiafn 116);ExecAndSet(status<|>,nokiafn title);
CFG -     101 = ExecAndSet(title<|>,nokiafn 101);ExecAndSet(status<|>,nokiafn title);
CFG -     119 = ExecAndSet(title<|>,nokiafn 119);ExecAndSet(status<|>,nokiafn title);
CFG -     113 = Set(text,replace,TEXT,Loading ...<|>);ExecAndSet(title<|>,nokiafn 113);ExecAndSet(status<|>,nokiafn title);
CFG -     #(Connect) = Set(parameter,joystick_up,-1,joystick_down,-2,joystick_left,-3,joystick_right,-4,joystick_push,-5<|>);Set(title,Modo activo: teclado<|>);Set(icons,Keyboard,0,empty,1,empty,2,empty,3,empty,4,empty,5,empty,6,empty,7,empty,8,empty,9,empty,*,empty,0,empty,#,empty<|>);
CFG -     (Connect) = Set(parameter,debug,on<|>);Set(parameter,fix_joystick,auto<|>);Set(title,Modo activo: teclado<|>);Set(icons,Keyboard,0,empty,1,empty,2,empty,3,empty,4,empty,5,empty,6,empty,7,empty,8,empty,9,empty,*,empty,0,empty,#,empty<|>);
CFG -     Cancel = Exit<|>;
CFG -     Back = Set(text,close<|>);
CFG - [ModeEnd] default
CFG - [Aliases]
CFG -     Key 241     aliased to Cancel
CFG - [End]
CFG - [Alarms]
CFG - [End]
CFG - [Parameters]
CFG -     AutoRepeat    No
CFG -     Debug          Yes
CFG -     Device        bluetooth:10
CFG -     Log          Yes
CFG -     Max Text Size 18
CFG -     Retry Sec     5
CFG -     Screen Menu   Yes
CFG - [End]
[Wed Aug  8 20:55:25 2007] - DEBUG - mainRoutine
[Wed Aug  8 20:55:25 2007] - INFO - openPort()
[Wed Aug  8 20:55:25 2007] - DEBUG - Bluetooth Sockets Server mode. Use channel 10
[Wed Aug  8 20:55:25 2007] - INFO - registered SP for channel 10
[Wed Aug  8 20:55:25 2007] - DEBUG - findItem()
[Wed Aug  8 20:55:25 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Wed Aug  8 20:55:25 2007] - INFO - No command on init

[Wed Aug  8 20:55:25 2007] - DEBUG - initPort
[Wed Aug  8 20:55:25 2007] - INFO - Server mode: Waiting connection
[Wed Aug  8 20:55:25 2007] - INFO - listenAndAcceptSocketConn
```

if  you're wondering what config file i used, I copied the one that came with the package...
```
AutoRepeat=false
Device=bluetooth:10
Log=true
Debug=true
RetrySecs=5
Screen=true

[Aliases]
241=Cancel
[End]

[Keys]

Back=Set(text,close)

Cancel=Exit;
(Connect)=Set(parameter,debug,on);Set(parameter,fix_joystick,auto);Set(title, Modo activo: teclado);Set(icons,Keyboard,0,empty,1,empty,2,empty,3,empty,4,empty,5,empty,6,empty,7,empty,8,empty,9,empty,*,empty,0,empty,#,empty);
# If does not work try to change to 
#(Connect)=Set(parameter,joystick_up,-1,joystick_down,-2,joystick_left,-3,joystick_right,-4,joystick_push,-5);Set(title, Modo activo: teclado);Set(icons,Keyboard,0,empty,1,empty,2,empty,3,empty,4,empty,5,empty,6,empty,7,empty,8,empty,9,empty,*,empty,0,empty,#,empty);
# where -1:-5 is keykodes of joystick(possibley it needs to change them)

113 = Set(text,replace,TEXT,Loading ...);ExecAndSet(title, nokiafn 113); ExecAndSet(status, nokiafn title);
119 = ExecAndSet(title, nokiafn 119); ExecAndSet(status, nokiafn title);
101 = ExecAndSet(title, nokiafn 101); ExecAndSet(status, nokiafn title);
116 = ExecAndSet(title, nokiafn 116); ExecAndSet(status, nokiafn title);
121 = ExecAndSet(title, nokiafn 121); ExecAndSet(status, nokiafn title);
105 = ExecAndSet(title, nokiafn 105); ExecAndSet(status, nokiafn title);
111 = ExecAndSet(title, nokiafn 111); ExecAndSet(status, nokiafn title);
112 = ExecAndSet(title, nokiafn 112); ExecAndSet(status, nokiafn title);
97  = ExecAndSet(title, nokiafn 97); ExecAndSet(status, nokiafn title);
115 = ExecAndSet(title, nokiafn 115); ExecAndSet(status, nokiafn title);
1   = ExecAndSet(title, nokiafn 1); ExecAndSet(status, nokiafn title);
108 = ExecAndSet(title, nokiafn 108); ExecAndSet(status, nokiafn title);
9   = ExecAndSet(title, nokiafn 9); ExecAndSet(status, nokiafn title);
122 = ExecAndSet(title, nokiafn 112); ExecAndSet(status, nokiafn title);
120 = ExecAndSet(title, nokiafn 120); ExecAndSet(status, nokiafn title);
99  = ExecAndSet(title, nokiafn 99); ExecAndSet(status, nokiafn title);
98  = ExecAndSet(title, nokiafn 98); ExecAndSet(status, nokiafn title);
110 = ExecAndSet(title, nokiafn 110); ExecAndSet(status, nokiafn title);
44  = ExecAndSet(title, nokiafn 44); ExecAndSet(status, nokiafn title);
46  = ExecAndSet(title, nokiafn 46); ExecAndSet(status, nokiafn title);
0   = ExecAndSet(title, nokiafn 0); ExecAndSet(status, nokiafn title);
-50 = ExecAndSet(title, nokiafn -50); ExecAndSet(status, nokiafn title);
231 = ExecAndSet(title, nokiafn 231); ExecAndSet(status, nokiafn title);
32  = ExecAndSet(title, nokiafn 32); ExecAndSet(status, nokiafn title);
241 = ExecAndSet(title, nokiafn 241); ExecAndSet(status, nokiafn title);
61441 = ExecAndSet(title, nokiafn 61441); ExecAndSet(status, nokiafn title);

[End]
```

---

### Post by zuzuzzzip on 2007-08-08
nm! got a connection!

but my buttons don't work (in fact the screen is black and says keyboard as title and in white letter modo: terclavo -- which for all i know means mode: keyboard :P)
so there must be something wrong in my config file...
I have a nokia N80 and Ubuntu 7.04 (Gnome).

I'd like to make it work with rhythmbox!

---

### Post by mike_mike on 2007-08-09
2 zuzuzzzip:
Which version of anyRemote do You use ? 
Did cfg-examples/Server-mode/kdialog.cfg works for You ?

Please, send logs&and terminal output to [email]anyremote@mail.ru[/email]

---

### Post by zuzuzzzip on 2007-08-09
no (sh: kdialog: not found), I'm not running KDE
but adminExample does!
I just need the right config for a nokia n80 to control my music

which logs & terminal output should I mail?
this is the one for adminExample.cfg
```
zuzuzzzip@ZuzuPC-ubuntu:~/downloads/anyremote-3.0/cfg-examples/Server-mode$ anyremote -f adminExample.cfg 
CFG: Use cfg file >adminExample.cfg<
INFO: log file is /home/zuzuzzzip/.anyRemote/anyremote.log
Serial Port service registered
Finish events forwarding

```log file:
```
CFG - [Mode] PROCS
CFG -     Back($$) = SetMode(LIST<|>);
CFG -     Kill($$) = Exec(<|>kill `echo $(Param) | cut -d ' ' -f 1`;ExecAndSet(list,replace,SAME<|>,ps -o pid -o command -u `whoami` | tr -s ' ' | cut -d ' ' -f 1,2,3 | sed 's/$/,/' | grep -v sed | grep -v cut);
CFG -     (EnterMode) = ExecAndSet(list,replace,User Processes<|>,ps -o pid -o command -u `whoami` | tr -s ' ' | cut -d ' ' -f 1,2,3 | sed 's/$/,/' | grep -v sed | grep -v cut);Set(menu,replace,Kill<|>);
CFG - [ModeEnd] PROCS
CFG - [Mode] TXT2
CFG -     Back = Set(text,close<|>);SetMode(FILES<|>);
CFG - [ModeEnd] TXT2
CFG - [Mode] FILES
CFG -     Back($$) = SetMode(LIST<|>);Set(list,replace,Available commands,Disk free space,Run Top, Stop Top, Uptime, User Processes, File List,Dmesg output<|>);Set(menu,replace,Choose<|>);
CFG -     Choose($$) = ExecAndSet(list,replace,SAME<|>,echo 'cd `cat $HOME/.anyRemote/ar_storedir.tmp`;if [ -d $(Param) ]; then cd $(Param);fi;pwd>$HOME/.anyRemote/ar_storedir.tmp;ls -F| sed "s/$/,/"|sed "s/(/openbrace/g"|sed "s/)/closebrace/g";'|bash -f -s);Set(list,add,SAME,..<|>);
CFG -     File info($$) = ExecAndSet(text,replace,File info<|>,cd `cat $HOME/.anyRemote/ar_storedir.tmp`;file $(Param));Set(text,add,SAME,\n<|>);ExecAndSet(text,add,File info<|>,cd `cat $HOME/.anyRemote/ar_storedir.tmp`;ls -l $(Param));SetMode(TXT2<|>);
CFG -     (EnterMode) = ExecAndSet(list,replace,Files<|>,cd `cat $HOME/.anyRemote/ar_storedir.tmp`;echo `pwd`>$HOME/.anyRemote/ar_storedir.tmp;ls -F| sed 's/$/,/'|sed 's/(/openbrace/g'|sed 's/)/closebrace/g');Set(list,add,SAME,..<|>);Set(menu,replace,Choose,File info<|>);
CFG - [ModeEnd] FILES
CFG - [Mode] TXT
CFG -     Back = Set(text,close<|>);SetMode(LIST<|>);
CFG - [ModeEnd] TXT
CFG - [Mode] LIST
CFG -     Choose(Dmesg output) = ExecAndSet(text,replace,Dmesg output<|>,dmesg|tail -50);SetMode(TXT<|>);
CFG -     Choose(User Processes) = SetMode(PROCS<|>);
CFG -     Choose(File List) = SetMode(FILES<|>);
CFG -     Choose(Uptime) = Set(list,close<|>);ExecAndSet(title<|>,uptime|tr -s ' '|cut -d ' ' -f 3,4,5);SetMode(default<|>);
CFG -     Choose(Stop Top) = CancelTimer(t1<|>);
CFG -     Choose(Run Top) = Timer(t1,5,0,text,replace,top<|>,top -bn 1|head -10|tr -s ' '|cut -f 2,3,10,13 -d ' '|tail -5);SetMode(TXT<|>);
CFG -     Choose(Disk free space) = ExecAndSet(text,replace,Free Space<|>,df -kl|tr -s ' '|cut -f 1,4 -d ' ');SetMode(TXT<|>);
CFG -     Back($$) = Set(list,close<|>);SetMode(default<|>);
CFG -     (EnterMode) = Set(list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output<|>);Set(menu,replace,Choose<|>);
CFG - [ModeEnd] LIST
CFG - [Mode] default
CFG -     0 = Exit<|>;
CFG -     1 = SetMode(LIST<|>);
CFG -     Back = Set(text,close<|>);
CFG -     * * = Set(text,replace,Help,Just press buttons and inspect results<|>);
CFG -     (Connect) = ExecAndSet(status<|>,uname -n);ExecAndSet(title<|>,whoami);Set(icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default<|>);
CFG -     Cancel = Exit<|>;
CFG - [ModeEnd] default
CFG - [Aliases]
CFG -     Key 69     aliased to Cancel
CFG -     Key -8     aliased to Cancel
CFG -     Key -11     aliased to Cancel
CFG - [End]
CFG - [Alarms]
CFG - [End]
CFG - [Parameters]
CFG -     AutoRepeat    No
CFG -     Debug          Yes
CFG -     Device        bluetooth:10
CFG -     Log          Yes
CFG -     Max Text Size 18
CFG -     Retry Sec     5
CFG -     Screen Menu   Yes
CFG - [End]
[Thu Aug  9 13:40:51 2007] - DEBUG - mainRoutine
[Thu Aug  9 13:40:51 2007] - INFO - openPort()
[Thu Aug  9 13:40:51 2007] - DEBUG - Bluetooth Sockets Server mode. Use channel 10
[Thu Aug  9 13:40:51 2007] - INFO - registered SP for channel 10
[Thu Aug  9 13:40:51 2007] - DEBUG - findItem()
[Thu Aug  9 13:40:51 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:40:51 2007] - INFO - No command on init

[Thu Aug  9 13:40:51 2007] - DEBUG - initPort
[Thu Aug  9 13:40:51 2007] - INFO - Server mode: Waiting connection
[Thu Aug  9 13:40:51 2007] - INFO - listenAndAcceptSocketConn
[Thu Aug  9 13:40:58 2007] - INFO - listenAndAcceptSocketConn: accepted
[Thu Aug  9 13:40:58 2007] - DEBUG - findItem()
[Thu Aug  9 13:40:58 2007] - INFO - Exec cmd on connect
[Thu Aug  9 13:40:58 2007] - DEBUG - handleCmdByKey() >(Connect)<
[Thu Aug  9 13:40:58 2007] - DEBUG - getCommand for >(Connect)<
[Thu Aug  9 13:40:58 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:40:58 2007] - DEBUG - Process next command status
[Thu Aug  9 13:40:58 2007] - INFO - processOneCommand >status< >uname -n< >1<
[Thu Aug  9 13:40:58 2007] - INFO - Command: ExecAndSet
[Thu Aug  9 13:40:58 2007] - DEBUG - execCmdAndGetResults
[Thu Aug  9 13:40:58 2007] - INFO - substParams >uname -n<
[Thu Aug  9 13:40:58 2007] - INFO - execSimpleCmd >uname -n<
[Thu Aug  9 13:40:58 2007] - INFO - Close port in child
[Thu Aug  9 13:40:58 2007] - INFO - closeSocketPort
[Thu Aug  9 13:40:58 2007] - INFO - substParams >status<
[Thu Aug  9 13:40:58 2007] - DEBUG - readResultsFile >14<
[Thu Aug  9 13:40:58 2007] - DEBUG - after readResultsFile()
[Thu Aug  9 13:40:58 2007] - DEBUG - ID_SET
[Thu Aug  9 13:40:58 2007] - DEBUG - sendData() >27<
[Thu Aug  9 13:40:58 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:40:58 2007] - DEBUG - Set(status,ZuzuPC-ubuntu
);
[Thu Aug  9 13:40:58 2007] - INFO - writeSocketConn 27 bytes
[Thu Aug  9 13:40:58 2007] - INFO - execCmdAndGetResults finished
[Thu Aug  9 13:40:58 2007] - DEBUG - Command: ExecAndSet FINISHED
[Thu Aug  9 13:40:58 2007] - DEBUG - Process next command title
[Thu Aug  9 13:40:58 2007] - INFO - processOneCommand >title< >whoami< >1<
[Thu Aug  9 13:40:58 2007] - INFO - Command: ExecAndSet
[Thu Aug  9 13:40:58 2007] - DEBUG - execCmdAndGetResults
[Thu Aug  9 13:40:58 2007] - INFO - substParams >whoami<
[Thu Aug  9 13:40:58 2007] - INFO - execSimpleCmd >whoami<
[Thu Aug  9 13:40:58 2007] - INFO - Close port in child
[Thu Aug  9 13:40:58 2007] - INFO - closeSocketPort
[Thu Aug  9 13:40:58 2007] - INFO - substParams >title<
[Thu Aug  9 13:40:58 2007] - DEBUG - readResultsFile >10<
[Thu Aug  9 13:40:58 2007] - DEBUG - after readResultsFile()
[Thu Aug  9 13:40:58 2007] - DEBUG - ID_SET
[Thu Aug  9 13:40:58 2007] - DEBUG - sendData() >22<
[Thu Aug  9 13:40:58 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:40:58 2007] - DEBUG - Set(title,zuzuzzzip
);
[Thu Aug  9 13:40:58 2007] - INFO - writeSocketConn 22 bytes
[Thu Aug  9 13:40:58 2007] - INFO - execCmdAndGetResults finished
[Thu Aug  9 13:40:58 2007] - DEBUG - Command: ExecAndSet FINISHED
[Thu Aug  9 13:40:58 2007] - DEBUG - Process next command icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default
[Thu Aug  9 13:40:58 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:40:58 2007] - INFO - substParams >icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default<
[Thu Aug  9 13:40:58 2007] - INFO - Command: Set
[Thu Aug  9 13:40:58 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:40:58 2007] - DEBUG - Set(icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default);
[Thu Aug  9 13:40:58 2007] - INFO - writeSocketConn 131 bytes
[Thu Aug  9 13:40:58 2007] - INFO - Start event forwarding
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(status)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(status)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() ZuzuPC-ubuntu)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() ZuzuPC-ubuntu)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(title)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(title)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() zuzuzzzip)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() zuzuzzzip)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(icons)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(icons)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() ADMIN)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() ADMIN)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 1)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 1)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() plus)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() plus)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 2)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 2)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 3)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 3)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 4)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 4)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 5)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 5)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 6)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 6)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 7)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 7)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 8)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 8)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 9)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 9)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() *)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() *)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 0)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 0)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() exit)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() exit)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() #)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() #)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() default)<
[Thu Aug  9 13:41:00 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:00 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:04 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 1,1<
[Thu Aug  9 13:41:04 2007] - DEBUG - handle_command() >+CKEV: 1,1<
[Thu Aug  9 13:41:04 2007] - DEBUG - Button down event
[Thu Aug  9 13:41:04 2007] - DEBUG - handle_key_press() >1<
[Thu Aug  9 13:41:04 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:04 2007] - DEBUG - handleCmdByKey() >1<
[Thu Aug  9 13:41:04 2007] - DEBUG - getCommand for >1<
[Thu Aug  9 13:41:04 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:04 2007] - DEBUG - Process next command LIST
[Thu Aug  9 13:41:04 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:04 2007] - INFO - substParams >LIST<
[Thu Aug  9 13:41:04 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:04 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:04 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:04 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:04 2007] - DEBUG - setMode() to LIST
[Thu Aug  9 13:41:04 2007] - DEBUG - findMode() LIST = LIST
[Thu Aug  9 13:41:04 2007] - DEBUG - setMode() new mode was set to LIST
[Thu Aug  9 13:41:04 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:04 2007] - DEBUG - Exec cmd on enter to mode
[Thu Aug  9 13:41:04 2007] - DEBUG - handleCmdByKey() >(EnterMode)<
[Thu Aug  9 13:41:04 2007] - DEBUG - getCommand for >(EnterMode)<
[Thu Aug  9 13:41:04 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:04 2007] - DEBUG - Process next command list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output
[Thu Aug  9 13:41:04 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:04 2007] - INFO - substParams >list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output<
[Thu Aug  9 13:41:04 2007] - INFO - Command: Set
[Thu Aug  9 13:41:04 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:04 2007] - DEBUG - Set(list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output);
[Thu Aug  9 13:41:04 2007] - INFO - writeSocketConn 116 bytes
[Thu Aug  9 13:41:04 2007] - DEBUG - Process next command menu,replace,Choose
[Thu Aug  9 13:41:04 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:04 2007] - INFO - substParams >menu,replace,Choose<
[Thu Aug  9 13:41:04 2007] - INFO - Command: Set
[Thu Aug  9 13:41:04 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:04 2007] - DEBUG - Set(menu,replace,Choose);
[Thu Aug  9 13:41:04 2007] - INFO - writeSocketConn 25 bytes
[Thu Aug  9 13:41:04 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:04 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:05 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:05 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:09 2007] - DEBUG - -------------------- Command read -------------------- >Msg:Choose(4,Uptime)<
[Thu Aug  9 13:41:09 2007] - DEBUG - handle_command() >Msg:Choose(4,Uptime)<
[Thu Aug  9 13:41:09 2007] - DEBUG - Got event from client
[Thu Aug  9 13:41:09 2007] - DEBUG - handle_key_press() >Choose(4,Uptime)<
[Thu Aug  9 13:41:09 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:09 2007] - DEBUG - Parametrized command parsed as >Choose< >4< >Uptime< 
[Thu Aug  9 13:41:09 2007] - DEBUG - Found exact (explicitly specified by value) parametrized command
[Thu Aug  9 13:41:09 2007] - DEBUG - handleCmdByKey() >Choose(Uptime)<
[Thu Aug  9 13:41:09 2007] - DEBUG - getCommand for >Choose(Uptime)<
[Thu Aug  9 13:41:09 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:09 2007] - DEBUG - Process next command list,close
[Thu Aug  9 13:41:09 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:09 2007] - INFO - substParams >list,close<
[Thu Aug  9 13:41:09 2007] - INFO - Command: Set
[Thu Aug  9 13:41:09 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:09 2007] - DEBUG - Set(list,close);
[Thu Aug  9 13:41:09 2007] - INFO - writeSocketConn 16 bytes
[Thu Aug  9 13:41:09 2007] - DEBUG - Process next command title
[Thu Aug  9 13:41:09 2007] - INFO - processOneCommand >title< >uptime|tr -s ' '|cut -d ' ' -f 3,4,5< >1<
[Thu Aug  9 13:41:09 2007] - INFO - Command: ExecAndSet
[Thu Aug  9 13:41:09 2007] - DEBUG - execCmdAndGetResults
[Thu Aug  9 13:41:09 2007] - INFO - substParams >uptime|tr -s ' '|cut -d ' ' -f 3,4,5<
[Thu Aug  9 13:41:09 2007] - INFO - execSimpleCmd >uptime|tr -s ' '|cut -d ' ' -f 3,4,5<
[Thu Aug  9 13:41:09 2007] - INFO - Close port in child
[Thu Aug  9 13:41:09 2007] - INFO - closeSocketPort
[Thu Aug  9 13:41:09 2007] - INFO - substParams >title<
[Thu Aug  9 13:41:09 2007] - DEBUG - readResultsFile >11<
[Thu Aug  9 13:41:09 2007] - DEBUG - after readResultsFile()
[Thu Aug  9 13:41:09 2007] - DEBUG - ID_SET
[Thu Aug  9 13:41:09 2007] - DEBUG - sendData() >23<
[Thu Aug  9 13:41:09 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:09 2007] - DEBUG - Set(title,up 14 min,
);
[Thu Aug  9 13:41:09 2007] - INFO - writeSocketConn 23 bytes
[Thu Aug  9 13:41:09 2007] - INFO - execCmdAndGetResults finished
[Thu Aug  9 13:41:09 2007] - DEBUG - Command: ExecAndSet FINISHED
[Thu Aug  9 13:41:09 2007] - DEBUG - Process next command default
[Thu Aug  9 13:41:09 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:09 2007] - INFO - substParams >default<
[Thu Aug  9 13:41:09 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:09 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:09 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:09 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:09 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:09 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:09 2007] - DEBUG - setMode() to default
[Thu Aug  9 13:41:09 2007] - DEBUG - findMode() default = default
[Thu Aug  9 13:41:09 2007] - DEBUG - setMode() new mode was set to default
[Thu Aug  9 13:41:09 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:09 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:09 2007] - DEBUG - Entered to mode
[Thu Aug  9 13:41:09 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:09 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(title)<
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(title)<
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() up 14 min,)<
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() up 14 min,)<
[Thu Aug  9 13:41:10 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:10 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:14 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 1,1<
[Thu Aug  9 13:41:14 2007] - DEBUG - handle_command() >+CKEV: 1,1<
[Thu Aug  9 13:41:14 2007] - DEBUG - Button down event
[Thu Aug  9 13:41:14 2007] - DEBUG - handle_key_press() >1<
[Thu Aug  9 13:41:14 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:14 2007] - DEBUG - handleCmdByKey() >1<
[Thu Aug  9 13:41:14 2007] - DEBUG - getCommand for >1<
[Thu Aug  9 13:41:14 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:14 2007] - DEBUG - Process next command LIST
[Thu Aug  9 13:41:14 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:14 2007] - INFO - substParams >LIST<
[Thu Aug  9 13:41:14 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:14 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:14 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:14 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:14 2007] - DEBUG - setMode() to LIST
[Thu Aug  9 13:41:14 2007] - DEBUG - findMode() LIST = LIST
[Thu Aug  9 13:41:14 2007] - DEBUG - setMode() new mode was set to LIST
[Thu Aug  9 13:41:14 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:14 2007] - DEBUG - Exec cmd on enter to mode
[Thu Aug  9 13:41:14 2007] - DEBUG - handleCmdByKey() >(EnterMode)<
[Thu Aug  9 13:41:14 2007] - DEBUG - getCommand for >(EnterMode)<
[Thu Aug  9 13:41:14 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:14 2007] - DEBUG - Process next command list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output
[Thu Aug  9 13:41:14 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:14 2007] - INFO - substParams >list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output<
[Thu Aug  9 13:41:14 2007] - INFO - Command: Set
[Thu Aug  9 13:41:14 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:14 2007] - DEBUG - Set(list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output);
[Thu Aug  9 13:41:14 2007] - INFO - writeSocketConn 116 bytes
[Thu Aug  9 13:41:14 2007] - DEBUG - Process next command menu,replace,Choose
[Thu Aug  9 13:41:14 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:14 2007] - INFO - substParams >menu,replace,Choose<
[Thu Aug  9 13:41:14 2007] - INFO - Command: Set
[Thu Aug  9 13:41:14 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:14 2007] - DEBUG - Set(menu,replace,Choose);
[Thu Aug  9 13:41:14 2007] - INFO - writeSocketConn 25 bytes
[Thu Aug  9 13:41:14 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:14 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 1,0<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >+CKEV: 1,0<
[Thu Aug  9 13:41:15 2007] - DEBUG - Button up event
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:15 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:15 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:17 2007] - DEBUG - -------------------- Command read -------------------- >Msg:Choose(1,Disk free space)<
[Thu Aug  9 13:41:17 2007] - DEBUG - handle_command() >Msg:Choose(1,Disk free space)<
[Thu Aug  9 13:41:17 2007] - DEBUG - Got event from client
[Thu Aug  9 13:41:17 2007] - DEBUG - handle_key_press() >Choose(1,Disk free space)<
[Thu Aug  9 13:41:17 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:17 2007] - DEBUG - Parametrized command parsed as >Choose< >1< >Disk free space< 
[Thu Aug  9 13:41:17 2007] - DEBUG - Found exact (explicitly specified by value) parametrized command
[Thu Aug  9 13:41:17 2007] - DEBUG - handleCmdByKey() >Choose(Disk free space)<
[Thu Aug  9 13:41:17 2007] - DEBUG - getCommand for >Choose(Disk free space)<
[Thu Aug  9 13:41:17 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:17 2007] - DEBUG - Process next command text,replace,Free Space
[Thu Aug  9 13:41:17 2007] - INFO - processOneCommand >text,replace,Free Space< >df -kl|tr -s ' '|cut -f 1,4 -d ' '< >1<
[Thu Aug  9 13:41:17 2007] - INFO - Command: ExecAndSet
[Thu Aug  9 13:41:17 2007] - DEBUG - execCmdAndGetResults
[Thu Aug  9 13:41:17 2007] - INFO - substParams >df -kl|tr -s ' '|cut -f 1,4 -d ' '<
[Thu Aug  9 13:41:17 2007] - INFO - execSimpleCmd >df -kl|tr -s ' '|cut -f 1,4 -d ' '<
[Thu Aug  9 13:41:17 2007] - INFO - Close port in child
[Thu Aug  9 13:41:17 2007] - INFO - closeSocketPort
[Thu Aug  9 13:41:18 2007] - INFO - substParams >text,replace,Free Space<
[Thu Aug  9 13:41:18 2007] - DEBUG - readResultsFile >216<
[Thu Aug  9 13:41:18 2007] - DEBUG - after readResultsFile()
[Thu Aug  9 13:41:18 2007] - DEBUG - ID_SET
[Thu Aug  9 13:41:18 2007] - DEBUG - sendData() >246<
[Thu Aug  9 13:41:18 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:18 2007] - DEBUG - Set(text,replace,Free Space,Filesystem Available
/dev/sda4 32031092
varrun 1030264
varlock 1030364
procbususb 1030224
udev 1030224
devshm 1030364
lrm 991392
/dev/sda1 183257300
/dev/sdb1 6963840
/dev/sdc1 11087344
/dev/hdb1 28621760
/dev/hda 0
);
[Thu Aug  9 13:41:18 2007] - INFO - writeSocketConn 246 bytes
[Thu Aug  9 13:41:18 2007] - INFO - execCmdAndGetResults finished
[Thu Aug  9 13:41:18 2007] - DEBUG - Command: ExecAndSet FINISHED
[Thu Aug  9 13:41:18 2007] - DEBUG - Process next command TXT
[Thu Aug  9 13:41:18 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:18 2007] - INFO - substParams >TXT<
[Thu Aug  9 13:41:18 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:18 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:18 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:18 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:18 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:18 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:18 2007] - DEBUG - setMode() to TXT
[Thu Aug  9 13:41:18 2007] - DEBUG - findMode() TXT = TXT
[Thu Aug  9 13:41:18 2007] - DEBUG - setMode() new mode was set to TXT
[Thu Aug  9 13:41:18 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:18 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:18 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:18 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:18 2007] - DEBUG - Entered to mode
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Free Space)<
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Free Space)<
[Thu Aug  9 13:41:18 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:18 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:19 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Filesystem Available
/dev/sda4 32031092
varrun 1030264
varlock 1030364
procbususb 1030224
udev 1030224
devshm 1030364
lrm 991392
/dev/sda1 183257300
/dev/sdb1 6963840
/dev/sdc1 11087344
/dev/hdb1 28621760
/dev/hda 0)<
[Thu Aug  9 13:41:19 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Filesystem Available
/dev/sda4 32031092
varrun 1030264
varlock 1030364
procbususb 1030224
udev 1030224
devshm 1030364
lrm 991392
/dev/sda1 183257300
/dev/sdb1 6963840
/dev/sdc1 11087344
/dev/hdb1 28621760
/dev/hda 0)<
[Thu Aug  9 13:41:19 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:19 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:28 2007] - DEBUG - -------------------- Command read -------------------- >Msg:Back<
[Thu Aug  9 13:41:28 2007] - DEBUG - handle_command() >Msg:Back<
[Thu Aug  9 13:41:28 2007] - DEBUG - Got event from client
[Thu Aug  9 13:41:28 2007] - DEBUG - handle_key_press() >Back<
[Thu Aug  9 13:41:28 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:28 2007] - DEBUG - handleCmdByKey() >Back<
[Thu Aug  9 13:41:28 2007] - DEBUG - getCommand for >Back<
[Thu Aug  9 13:41:28 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:28 2007] - DEBUG - Process next command text,close
[Thu Aug  9 13:41:28 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:28 2007] - INFO - substParams >text,close<
[Thu Aug  9 13:41:28 2007] - INFO - Command: Set
[Thu Aug  9 13:41:28 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:28 2007] - DEBUG - Set(text,close);
[Thu Aug  9 13:41:28 2007] - INFO - writeSocketConn 16 bytes
[Thu Aug  9 13:41:28 2007] - DEBUG - Process next command LIST
[Thu Aug  9 13:41:28 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:28 2007] - INFO - substParams >LIST<
[Thu Aug  9 13:41:28 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:28 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:28 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:28 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:28 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:28 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:28 2007] - DEBUG - setMode() to LIST
[Thu Aug  9 13:41:28 2007] - DEBUG - findMode() LIST = LIST
[Thu Aug  9 13:41:28 2007] - DEBUG - setMode() new mode was set to LIST
[Thu Aug  9 13:41:28 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:28 2007] - DEBUG - Exec cmd on enter to mode
[Thu Aug  9 13:41:28 2007] - DEBUG - handleCmdByKey() >(EnterMode)<
[Thu Aug  9 13:41:28 2007] - DEBUG - getCommand for >(EnterMode)<
[Thu Aug  9 13:41:28 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:28 2007] - DEBUG - Process next command list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output
[Thu Aug  9 13:41:28 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:28 2007] - INFO - substParams >list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output<
[Thu Aug  9 13:41:28 2007] - INFO - Command: Set
[Thu Aug  9 13:41:28 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:28 2007] - DEBUG - Set(list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output);
[Thu Aug  9 13:41:28 2007] - INFO - writeSocketConn 116 bytes
[Thu Aug  9 13:41:28 2007] - DEBUG - Process next command menu,replace,Choose
[Thu Aug  9 13:41:28 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:28 2007] - INFO - substParams >menu,replace,Choose<
[Thu Aug  9 13:41:28 2007] - INFO - Command: Set
[Thu Aug  9 13:41:28 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:28 2007] - DEBUG - Set(menu,replace,Choose);
[Thu Aug  9 13:41:28 2007] - INFO - writeSocketConn 25 bytes
[Thu Aug  9 13:41:28 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:28 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:30 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:30 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:34 2007] - DEBUG - -------------------- Command read -------------------- >Msg:Choose(7,Dmesg output)<
[Thu Aug  9 13:41:34 2007] - DEBUG - handle_command() >Msg:Choose(7,Dmesg output)<
[Thu Aug  9 13:41:34 2007] - DEBUG - Got event from client
[Thu Aug  9 13:41:34 2007] - DEBUG - handle_key_press() >Choose(7,Dmesg output)<
[Thu Aug  9 13:41:34 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:34 2007] - DEBUG - Parametrized command parsed as >Choose< >7< >Dmesg output< 
[Thu Aug  9 13:41:34 2007] - DEBUG - Found exact (explicitly specified by value) parametrized command
[Thu Aug  9 13:41:34 2007] - DEBUG - handleCmdByKey() >Choose(Dmesg output)<
[Thu Aug  9 13:41:34 2007] - DEBUG - getCommand for >Choose(Dmesg output)<
[Thu Aug  9 13:41:34 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:34 2007] - DEBUG - Process next command text,replace,Dmesg output
[Thu Aug  9 13:41:34 2007] - INFO - processOneCommand >text,replace,Dmesg output< >dmesg|tail -50< >1<
[Thu Aug  9 13:41:34 2007] - INFO - Command: ExecAndSet
[Thu Aug  9 13:41:34 2007] - DEBUG - execCmdAndGetResults
[Thu Aug  9 13:41:34 2007] - INFO - substParams >dmesg|tail -50<
[Thu Aug  9 13:41:34 2007] - INFO - execSimpleCmd >dmesg|tail -50<
[Thu Aug  9 13:41:34 2007] - INFO - Close port in child
[Thu Aug  9 13:41:34 2007] - INFO - closeSocketPort
[Thu Aug  9 13:41:34 2007] - INFO - substParams >text,replace,Dmesg output<
[Thu Aug  9 13:41:34 2007] - DEBUG - readResultsFile >2865<
[Thu Aug  9 13:41:34 2007] - DEBUG - after readResultsFile()
[Thu Aug  9 13:41:34 2007] - DEBUG - ID_SET
[Thu Aug  9 13:41:34 2007] - DEBUG - sendData() >2897<
[Thu Aug  9 13:41:34 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:34 2007] - DEBUG - Set(text,replace,Dmesg output,[   54.981114] NET: Registered protocol family 17
[   55.064786] EXT3 FS on sda4, internal journal
[   58.629790] input: Power Button (FF) as /class/input/input4
[   58.630047] ACPI: Power Button (FF) [PWRF]
[   58.657789] in
[Thu Aug  9 13:41:34 2007] - INFO - writeSocketConn 2897 bytes
[Thu Aug  9 13:41:34 2007] - INFO - execCmdAndGetResults finished
[Thu Aug  9 13:41:34 2007] - DEBUG - Command: ExecAndSet FINISHED
[Thu Aug  9 13:41:34 2007] - DEBUG - Process next command TXT
[Thu Aug  9 13:41:34 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:34 2007] - INFO - substParams >TXT<
[Thu Aug  9 13:41:34 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:34 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:34 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:34 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:34 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:34 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:34 2007] - DEBUG - setMode() to TXT
[Thu Aug  9 13:41:34 2007] - DEBUG - findMode() TXT = TXT
[Thu Aug  9 13:41:34 2007] - DEBUG - setMode() new mode was set to TXT
[Thu Aug  9 13:41:34 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:34 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:34 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:34 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:34 2007] - DEBUG - Entered to mode
[Thu Aug  9 13:41:34 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:34 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() [   54.981114] NET: Registered protocol family 17
[   55.064786] EXT3 FS on sda4, internal journal
[   58.629790] input: Power Button (FF) as /class/input/input4
[   58.630047] ACPI: Power Button (FF) [PWRF]
[   58.657789] input: Power Button (CM) as /class/input/input5
[   58.657830] ACPI: Power Button (CM) [PWRB]
[   58.725711] No dock devices found.
[   58.754473] Using specific hotkey driver
[   58.799830] ibm_acpi: ec object not found
[   58.855414] pcc_acpi: loading...
[)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() [   54.981114] NET: Registered protocol family 17
[   55.064786] EXT3 FS on sda4, internal journal
[   58.629790] input: Power Button (FF) as /class/input/input4
[   58.630047] ACPI: Power Button (FF) [PWRF]
[   58.657789] input: Power Button (CM) as /class/input/input5
[   58.657830] ACPI: Power Button (CM) [PWRB]
[   58.725711] No dock devices found.
[   58.754473] Using specific hotkey driver
[   58.799830] ibm_acpi: ec object not found
[   58.855414] pcc_acpi: loading...
[)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 59.049987] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   59.050073] powernow-k8: MP systems not su)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 59.049987] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   59.050073] powernow-k8: MP systems not su)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() pported by PSB BIOS structure
[   59.050031] powernow-k8: MP systems not supported by PSB BIOS structure
[   59.585267] usb-storage: device scan complete
[   59.586511] scsi 6:0:0:0: Direct-Access     WDC WD50  WD-WCANU1617017 2E07 PQ: 0 ANSI: 2 CCS
[   59.588365] SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
[   59.589988] sdd: Write Protect is off
[   59.589992] sdd: Mode Sense: 00 38 00 00
[   59.589995] sdd: assuming drive cache: write through
[   59.596965] SCSI device sdd: 976773168 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() pported by PSB BIOS structure
[   59.050031] powernow-k8: MP systems not supported by PSB BIOS structure
[   59.585267] usb-storage: device scan complete
[   59.586511] scsi 6:0:0:0: Direct-Access     WDC WD50  WD-WCANU1617017 2E07 PQ: 0 ANSI: 2 CCS
[   59.588365] SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
[   59.589988] sdd: Write Protect is off
[   59.589992] sdd: Mode Sense: 00 38 00 00
[   59.589995] sdd: assuming drive cache: write through
[   59.596965] SCSI device sdd: 976773168 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 512-byte hdwr sectors (500108 MB)
[   59.598981] sdd: Write Protect is off
[   59.598985] sdd: Mode Sense: 00 38 00 00
[   59.598988] sdd: assuming drive cache: write through
[   59.598995]  sdd: sdd1 sdd2 < sdd5 >
[   59.615825] sd 6:0:0:0: Attached scsi disk sdd
[   59.615873] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   66.119783] ppdev: user-space parallel port driver
[   67.382684] NET: Registered protocol family 10
[   67.382801] lo: Disabled Privacy Extensions
[   67.382862] ADDRCONF(NETDEV_UP):)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 512-byte hdwr sectors (500108 MB)
[   59.598981] sdd: Write Protect is off
[   59.598985] sdd: Mode Sense: 00 38 00 00
[   59.598988] sdd: assuming drive cache: write through
[   59.598995]  sdd: sdd1 sdd2 < sdd5 >
[   59.615825] sd 6:0:0:0: Attached scsi disk sdd
[   59.615873] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   66.119783] ppdev: user-space parallel port driver
[   67.382684] NET: Registered protocol family 10
[   67.382801] lo: Disabled Privacy Extensions
[   67.382862] ADDRCONF(NETDEV_UP):)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() eth)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() eth)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 1: link is not ready
[   67.559020] Bluetooth: L2CAP ver 2.8
[   67.559025] Bluetooth: L2CAP socket layer initialized
[   67.565142] Bluetooth: RFCOMM socket layer initialized
[   67.565162] Bluetooth: RFCOMM TTY layer initialized
[   67.565165] Bluetooth: RFCOMM ver 1.8
[   68.118179] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   68.118192] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[   78.590425] ra0: no IPv6 routers present
[   81.7<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 1: link is not ready
[   67.559020] Bluetooth: L2CAP ver 2.8
[   67.559025] Bluetooth: L2CAP socket layer initialized
[   67.565142] Bluetooth: RFCOMM socket layer initialized
[   67.565162] Bluetooth: RFCOMM TTY layer initialized
[   67.565165] Bluetooth: RFCOMM ver 1.8
[   68.118179] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   68.118192] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[   78.590425] ra0: no IPv6 routers present
[   81.7<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >88623] ISO 9660 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >88623] ISO 9660 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - isBemusedCommand: >88623] ISO 9660 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - Unhandled cmd 88623] ISO 9660 )
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Extensions: Microsoft Joliet Level 1
[   81.860129] ISOFS: changing to secondary root
[   85.393343] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   85.393354] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[   95.401035] ra0: no IPv6 routers present
[  166.920493] sky2 eth1: disabling interface
[  167.077987] sky2 eth1: enabling interface
[  167.079821] sky2 eth1: ram buffer 48K
[  167.084027] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  169.472476] rt2500 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Extensions: Microsoft Joliet Level 1
[   81.860129] ISOFS: changing to secondary root
[   85.393343] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   85.393354] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[   95.401035] ra0: no IPv6 routers present
[  166.920493] sky2 eth1: disabling interface
[  167.077987] sky2 eth1: enabling interface
[  167.079821] sky2 eth1: ram buffer 48K
[  167.084027] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  169.472476] rt2500 )<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() EEPROM:)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() EEPROM:)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() 1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[  169.472484] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[  179.686341] ra0: no IPv6 routers present)<
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() 1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[  169.472484] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[  179.686341] ra0: no IPv6 routers present)<
[Thu Aug  9 13:41:36 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:36 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:45 2007] - DEBUG - -------------------- Command read -------------------- >Msg:Back<
[Thu Aug  9 13:41:45 2007] - DEBUG - handle_command() >Msg:Back<
[Thu Aug  9 13:41:45 2007] - DEBUG - Got event from client
[Thu Aug  9 13:41:45 2007] - DEBUG - handle_key_press() >Back<
[Thu Aug  9 13:41:45 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:45 2007] - DEBUG - handleCmdByKey() >Back<
[Thu Aug  9 13:41:45 2007] - DEBUG - getCommand for >Back<
[Thu Aug  9 13:41:45 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:45 2007] - DEBUG - Process next command text,close
[Thu Aug  9 13:41:45 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:45 2007] - INFO - substParams >text,close<
[Thu Aug  9 13:41:45 2007] - INFO - Command: Set
[Thu Aug  9 13:41:45 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:45 2007] - DEBUG - Set(text,close);
[Thu Aug  9 13:41:45 2007] - INFO - writeSocketConn 16 bytes
[Thu Aug  9 13:41:45 2007] - DEBUG - Process next command LIST
[Thu Aug  9 13:41:45 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:45 2007] - INFO - substParams >LIST<
[Thu Aug  9 13:41:45 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:45 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:45 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:45 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:45 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:45 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:45 2007] - DEBUG - setMode() to LIST
[Thu Aug  9 13:41:45 2007] - DEBUG - findMode() LIST = LIST
[Thu Aug  9 13:41:45 2007] - DEBUG - setMode() new mode was set to LIST
[Thu Aug  9 13:41:45 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:45 2007] - DEBUG - Exec cmd on enter to mode
[Thu Aug  9 13:41:45 2007] - DEBUG - handleCmdByKey() >(EnterMode)<
[Thu Aug  9 13:41:45 2007] - DEBUG - getCommand for >(EnterMode)<
[Thu Aug  9 13:41:45 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:45 2007] - DEBUG - Process next command list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output
[Thu Aug  9 13:41:45 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:45 2007] - INFO - substParams >list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output<
[Thu Aug  9 13:41:45 2007] - INFO - Command: Set
[Thu Aug  9 13:41:45 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:45 2007] - DEBUG - Set(list,replace,Available commands,Disk free space,Run Top,Stop Top,Uptime, User Processes,File List,Dmesg output);
[Thu Aug  9 13:41:45 2007] - INFO - writeSocketConn 116 bytes
[Thu Aug  9 13:41:45 2007] - DEBUG - Process next command menu,replace,Choose
[Thu Aug  9 13:41:45 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:45 2007] - INFO - substParams >menu,replace,Choose<
[Thu Aug  9 13:41:45 2007] - INFO - Command: Set
[Thu Aug  9 13:41:45 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:45 2007] - DEBUG - Set(menu,replace,Choose);
[Thu Aug  9 13:41:45 2007] - INFO - writeSocketConn 25 bytes
[Thu Aug  9 13:41:45 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:45 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(text)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Available commands)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Disk free space)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Run Top)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Stop Top)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Uptime)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() User Processes)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() File List)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Dmesg output)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(menu)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() replace)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Choose)<
[Thu Aug  9 13:41:47 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:47 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:52 2007] - DEBUG - -------------------- Command read -------------------- >Msg:Choose(4,Uptime)<
[Thu Aug  9 13:41:52 2007] - DEBUG - handle_command() >Msg:Choose(4,Uptime)<
[Thu Aug  9 13:41:52 2007] - DEBUG - Got event from client
[Thu Aug  9 13:41:52 2007] - DEBUG - handle_key_press() >Choose(4,Uptime)<
[Thu Aug  9 13:41:52 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:52 2007] - DEBUG - Parametrized command parsed as >Choose< >4< >Uptime< 
[Thu Aug  9 13:41:52 2007] - DEBUG - Found exact (explicitly specified by value) parametrized command
[Thu Aug  9 13:41:52 2007] - DEBUG - handleCmdByKey() >Choose(Uptime)<
[Thu Aug  9 13:41:52 2007] - DEBUG - getCommand for >Choose(Uptime)<
[Thu Aug  9 13:41:52 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:52 2007] - DEBUG - Process next command list,close
[Thu Aug  9 13:41:52 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:52 2007] - INFO - substParams >list,close<
[Thu Aug  9 13:41:52 2007] - INFO - Command: Set
[Thu Aug  9 13:41:52 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:52 2007] - DEBUG - Set(list,close);
[Thu Aug  9 13:41:52 2007] - INFO - writeSocketConn 16 bytes
[Thu Aug  9 13:41:52 2007] - DEBUG - Process next command title
[Thu Aug  9 13:41:52 2007] - INFO - processOneCommand >title< >uptime|tr -s ' '|cut -d ' ' -f 3,4,5< >1<
[Thu Aug  9 13:41:52 2007] - INFO - Command: ExecAndSet
[Thu Aug  9 13:41:52 2007] - DEBUG - execCmdAndGetResults
[Thu Aug  9 13:41:52 2007] - INFO - substParams >uptime|tr -s ' '|cut -d ' ' -f 3,4,5<
[Thu Aug  9 13:41:52 2007] - INFO - execSimpleCmd >uptime|tr -s ' '|cut -d ' ' -f 3,4,5<
[Thu Aug  9 13:41:52 2007] - INFO - Close port in child
[Thu Aug  9 13:41:52 2007] - INFO - closeSocketPort
[Thu Aug  9 13:41:52 2007] - INFO - substParams >title<
[Thu Aug  9 13:41:52 2007] - DEBUG - readResultsFile >11<
[Thu Aug  9 13:41:52 2007] - DEBUG - after readResultsFile()
[Thu Aug  9 13:41:52 2007] - DEBUG - ID_SET
[Thu Aug  9 13:41:52 2007] - DEBUG - sendData() >23<
[Thu Aug  9 13:41:52 2007] - DEBUG - writeSocketConn
[Thu Aug  9 13:41:52 2007] - DEBUG - Set(title,up 15 min,
);
[Thu Aug  9 13:41:52 2007] - INFO - writeSocketConn 23 bytes
[Thu Aug  9 13:41:52 2007] - INFO - execCmdAndGetResults finished
[Thu Aug  9 13:41:52 2007] - DEBUG - Command: ExecAndSet FINISHED
[Thu Aug  9 13:41:52 2007] - DEBUG - Process next command default
[Thu Aug  9 13:41:52 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:52 2007] - INFO - substParams >default<
[Thu Aug  9 13:41:52 2007] - INFO - Command: SetMode
[Thu Aug  9 13:41:52 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:52 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:52 2007] - DEBUG - findItem() search in default
[Thu Aug  9 13:41:52 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:52 2007] - DEBUG - Leave mode
[Thu Aug  9 13:41:52 2007] - DEBUG - setMode() to default
[Thu Aug  9 13:41:52 2007] - DEBUG - findMode() default = default
[Thu Aug  9 13:41:52 2007] - DEBUG - setMode() new mode was set to default
[Thu Aug  9 13:41:52 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:52 2007] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Thu Aug  9 13:41:52 2007] - DEBUG - Entered to mode
[Thu Aug  9 13:41:52 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:52 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(list)<
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() close)<
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() Set(title)<
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() Set(title)<
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- >Msg:_DEBUG_(getWord() up 15 min,)<
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() >Msg:_DEBUG_(getWord() up 15 min,)<
[Thu Aug  9 13:41:53 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:53 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:56 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 4,1<
[Thu Aug  9 13:41:56 2007] - DEBUG - handle_command() >+CKEV: 4,1<
[Thu Aug  9 13:41:56 2007] - DEBUG - Button down event
[Thu Aug  9 13:41:56 2007] - DEBUG - handle_key_press() >4<
[Thu Aug  9 13:41:56 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:56 2007] - DEBUG - findItemInMode: Item does not found
[Thu Aug  9 13:41:56 2007] - DEBUG - No approprite key definition was found by findItem()
[Thu Aug  9 13:41:56 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:56 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:56 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 4,0<
[Thu Aug  9 13:41:56 2007] - DEBUG - handle_command() >+CKEV: 4,0<
[Thu Aug  9 13:41:56 2007] - DEBUG - Button up event
[Thu Aug  9 13:41:56 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:56 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:57 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 5,1<
[Thu Aug  9 13:41:57 2007] - DEBUG - handle_command() >+CKEV: 5,1<
[Thu Aug  9 13:41:57 2007] - DEBUG - Button down event
[Thu Aug  9 13:41:57 2007] - DEBUG - handle_key_press() >5<
[Thu Aug  9 13:41:57 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:57 2007] - DEBUG - findItemInMode: Item does not found
[Thu Aug  9 13:41:57 2007] - DEBUG - No approprite key definition was found by findItem()
[Thu Aug  9 13:41:57 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:57 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:57 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 5,0<
[Thu Aug  9 13:41:57 2007] - DEBUG - handle_command() >+CKEV: 5,0<
[Thu Aug  9 13:41:57 2007] - DEBUG - Button up event
[Thu Aug  9 13:41:57 2007] - DEBUG - -------------------- Command read -------------------- ><
[Thu Aug  9 13:41:57 2007] - DEBUG - handle_command() ><
[Thu Aug  9 13:41:58 2007] - DEBUG - -------------------- Command read -------------------- >+CKEV: 0,1<
[Thu Aug  9 13:41:58 2007] - DEBUG - handle_command() >+CKEV: 0,1<
[Thu Aug  9 13:41:58 2007] - DEBUG - Button down event
[Thu Aug  9 13:41:58 2007] - DEBUG - handle_key_press() >0<
[Thu Aug  9 13:41:58 2007] - DEBUG - findItem()
[Thu Aug  9 13:41:58 2007] - DEBUG - handleCmdByKey() >0<
[Thu Aug  9 13:41:58 2007] - DEBUG - getCommand for >0<
[Thu Aug  9 13:41:58 2007] - DEBUG - ready to execute command
[Thu Aug  9 13:41:58 2007] - DEBUG - Process next command NULL parameters
[Thu Aug  9 13:41:58 2007] - INFO - processOneCommand>no exec params< >1<
[Thu Aug  9 13:41:58 2007] - INFO - Exit key detected
[Thu Aug  9 13:41:58 2007] - INFO - Finish events forwarding
[Thu Aug  9 13:41:58 2007] - INFO - closeSocketPort
[Thu Aug  9 13:41:58 2007] - DEBUG - Return code from processOneCommand() is 3
[Thu Aug  9 13:41:58 2007] - DEBUG - Abort or disconnect after processOneCommand()
[Thu Aug  9 13:41:58 2007] - DEBUG - handleCmdByKey() EXIT_ABORT || EXIT_DISCON
[Thu Aug  9 13:41:58 2007] - DEBUG - handle_key_press EXIT_ABORT || EXIT_DISCON
[Thu Aug  9 13:41:58 2007] - DEBUG - mainRoutine
[Thu Aug  9 13:41:58 2007] - DEBUG - freeTimers()
[Thu Aug  9 13:41:58 2007] - DEBUG - freeCfg()
[Thu Aug  9 13:41:58 2007] - DEBUG - freeCfg() OK
```

---

### Post by mike_mike on 2007-08-09
2 zuzuzzzip:
So, does adminExample.cfg works for You ?
According to logs it should works :-)
If so, just use cfg-examples/Server-mode/rhytmbox.cfg to control rhytmbox

---

### Post by zuzuzzzip on 2007-08-09
omg this is realy GREAT! 
Thanks man! Keep up the good work :D

(the problem was i looked over rhythmbox.cfg, stupid me :$)

---

### Post by mike_mike on 2007-08-27
Good news !

There is an repository for kubuntu 7.04 i386 with debian packages for kAnyRemote [http://jerrad.tuxfamily.org/repo_eng.html](http://jerrad.tuxfamily.org/repo_eng.html)

---

### Post by markp1989 on 2007-08-31
Thankyou so much, i been looking for somthing like this for a very long time


tried it on 2 phones, workes perfectly with motorola L7, but doesnt work with the L6

---

### Post by jusmurph on 2007-09-01
This is sweet...

---

### Post by koshari on 2007-10-23
ok trying to build a deb for 7.10 using the 3.04anyremote source, 

and come up with this,

```
deps/btio.Tpo -c -o btio.o btio.c
btio.c:38:33: error: bluetooth/bluetooth.h: No such file or directory
btio.c:39:30: error: bluetooth/rfcomm.h: No such file or directory
btio.c: In function &#8216;openSocketPort&#8217;:
btio.c:314: error: storage size of &#8216;bt_addr&#8217; isn&#8217;t known
btio.c:334: error: &#8216;BTPROTO_RFCOMM&#8217; undeclared (first use in this function)
btio.c:334: error: (Each undeclared identifier is reported only once
btio.c:334: error: for each function it appears in.)
btio.c:370: error: &#8216;BDADDR_ANY&#8217; undeclared (first use in this function)
btio.c:314: warning: unused variable &#8216;bt_addr&#8217;
btio.c: In function &#8216;listenAndAcceptSocketConn&#8217;:
btio.c:416: error: storage size of &#8216;bt_addr&#8217; isn&#8217;t known
btio.c:417: error: &#8216;bdaddr_t&#8217; undeclared (first use in this function)
btio.c:417: error: expected &#8216;;&#8217; before &#8216;ba&#8217;
btio.c:469: warning: implicit declaration of function &#8216;baswap&#8217;
btio.c:469: error: &#8216;ba&#8217; undeclared (first use in this function)
btio.c:471: warning: implicit declaration of function &#8216;batostr&#8217;
btio.c:471: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
btio.c:416: warning: unused variable &#8216;bt_addr&#8217;
make[1]: *** [btio.o] Error 1
make[1]: Leaving directory `/home/user/anyremote-3.4/src'
make: *** [install-recursive] Error 1

```
i just realised i got this because i dint have the libbluetoothdev installed.

---

### Post by mike_mike on 2007-11-20
Debian packages are available now  at anyremote.sf.net

---

### Post by myharshdesigner on 2007-11-21
Cool Topic Thanks :)

---

### Post by markp1989 on 2007-12-01
how do i found out which /dev/ is my bluetooth device?

---

### Post by mike_mike on 2007-12-13
See /etc/bluetooth/rfcomm.conf
There should be description of all /dev/rfcomm's

If there is no appropriate rfcomm You have to add it by Youself
(see man hciconfig, hcitool, sdptool)

Also, it is possible to create /dev/rfcommX by one command:
rfcomm bind <params>
(see man rfcomm)

---

### Post by brickZA on 2007-12-14
Hi,

I'm trying to use anyremote, but I can't figure out how to upload the app to my phone. Been bashing my head for hours, doing BT transfers and also downloading from the web. 

I have a Nokia 6230i,  how can I get the java app installed on it? I don't have windows, so is there a way to do it under Ubuntu/ 7.10 i386?

I have tried the following:

1) Upload anyRemote.jar and anyRemote.jad through obex:// in nautilus to the phone. I can see the file on the phone in the file browser, but I can't figure out how to run/install it

2) Used the "send java to phone" button in ganyremote. My phone receives a bluetooth message containing anyRemote.jar but doesn't know what to do with it

3) Download anyRemote.jar directly by entering the URL in the phone webbrowser

I may have tried other things too, none of which were successful ;P

Thanks
Neilen

---

### Post by b4d on 2007-12-16
> **markp1989 said:**
> how do i found out which /dev/ is my bluetooth device?

I put "bluetooth:10" for device and it works (without the ")

How can the look of screen on phone be changed, mine allways looks like it's for music player control...

---

### Post by b4d on 2007-12-16
Okay, I've got to the point where I understand the cfg files and I've hacked my amarok.cfg, so now it shows some volume and status info on the phone...

---

### Post by Nicke2 on 2007-12-18
The link to the "howto" on making your own config files seems to be dead. Does anyone care to share their repository of cfgs and/or give some sort of short introduction for those of us who want to learn to make our own ? :D

---

### Post by b4d on 2007-12-19
Download the source package, in there you'll find some default cfg's, you can take a look at them, and start to modify so they suit your needs. If you have any questions, just ask :)

---

### Post by Fab on 2007-12-29
Okay, I used the debs from the sourceforge site and had no problem sending the jar to my phone (a motorola krzr k1) and installing it.. now I used the following procedure to start anyremote (not sure if it's the proper way?)

make phone discoverable for one minute
start anyremote with config file on computer
start client on phone, connect to computer (works with most configs..)

and that's where the trouble starts.. with some configs, I can't do anything at all.. with some, I can press one button (ie mpd/amarok stop), but then it says disconnected in the terminal, while the phone is still believing to be connected (ie has the options disconnect and exit, and I can still navigate the control buttons, but nothing happens anymore). If I disconnect or exit, I can't connect again until I repeat the whole procedure..

Any hints? I'll try to provide logs if necessary, right now the pc in question doesn't have net access..

---

### Post by Fab on 2007-12-30
Okay, I tried again with AT-mode, all the test commands described in the documentation worked flawlessly. I tried to run anyremote with the mpd.cfg for at-mode, didn't work, then I realized it says "Status: Broken" in the cfg file and tried again, this time with mouse.cfg. Didn't work either, same error. Here is the log.

> CFG - [Mode] default
CFG - 	Hash = Exec(<|>xte 'mouseclick 1' 'usleep 1000' 'mouseclick 1');
CFG - 	0 = Exec(<|>xte 'key space');
CFG - 	9 = Exec(<|>xte 'mouseclick 5');
CFG - 	8 = Exec(<|>xte 'mousermove 0 10');
CFG - 	7 = Exec(<|>xte 'mouseclick 4');
CFG - 	6 = Exec(<|>xte 'mousermove 10 0');
CFG - 	5 = Exec(<|>xte 'mousermove 0 -10');
CFG - 	4 = Exec(<|>xte 'mousermove -10 0');
CFG - 	3 = Exec(<|>xte 'mouseclick 3');
CFG - 	2 = Exec(<|>xte 'mouseclick 2');
CFG - 	1 = Exec(<|>xte 'mouseclick 1');
CFG - 	Star Star = Exec(<|>echo 'F="$HOME/.anyRemote/anyrem.hlp";echo "1 - Left Click     2 - CenterClick  3 - RightClick" > $F;echo "4 - Move Left      5 - MoveUp       6 - MoveRight" >> $F;echo "7 - Wheel Up       8 - Move Down    9 - Wheel Down" >> $F;echo "                   0 - Space        # - Left DblClick" >> $F;kdialog -passivepopup "`cat $F`" 7' |bash -f -s);
CFG - 	Cancel = Exit<|>;
CFG - 	Answer = TempDisconnect<|>;
CFG - 	(Init) = Exec(<|>echo 'P=`which xte|grep xte|grep -v not|wc -l`; KD=`which kdialog|grep kdialog|grep -v not|wc -l`;if [ "x$KD" == "x1" ]; then M="kdialog --msgbox"; else M="xmessage"; fi; if [ "x$P" == "x1" ]; then true; else $M "ERROR: xautomation package is not installed"; fi'|bash -f -s);
CFG - [ModeEnd] default
CFG - [Aliases]
CFG - 	Key POWER 	aliased to #
CFG - 	Key TEXT 	aliased to *
CFG - 	Key 57 	aliased to 9
CFG - 	Key 56 	aliased to 8
CFG - 	Key 55 	aliased to 7
CFG - 	Key 54 	aliased to 6
CFG - 	Key 53 	aliased to 5
CFG - 	Key 52 	aliased to 4
CFG - 	Key 51 	aliased to 3
CFG - 	Key 50 	aliased to 2
CFG - 	Key 49 	aliased to 1
CFG - 	Key 48 	aliased to 0
CFG - 	Key 35 	aliased to Hash
CFG - 	Key # 	aliased to Hash
CFG - 	Key 42 	aliased to Star
CFG - 	Key * 	aliased to Star
CFG - 	Key 69 	aliased to Cancel
CFG - 	Key 83 	aliased to Answer
CFG - 	Key p 	aliased to Cancel
CFG - 	Key L 	aliased to Cancel
CFG - 	Key c 	aliased to Answer
CFG - 	Key E 	aliased to Cancel
CFG - 	Key S 	aliased to Answer
CFG - [End]
CFG - [Alarms]
CFG - [End]
CFG - [Parameters]
CFG - 	AutoConnect   No
CFG - 	AutoRepeat    Yes
CFG - 	CMER On	   Will be determined automatically
CFG - 	CMER Off	   Will be determined automatically
CFG - 	Debug	      Yes
CFG - 	Device        /dev/rfcomm0
CFG - 	Log	      Yes
CFG - 	Retry Sec     5
CFG - 	Screen Menu   No
CFG - 	To Main Menu  E  for Motorola
CFG - [End]
[Sun Dec 30 12:04:15 2007] - DEBUG - mainRoutine
[Sun Dec 30 12:04:15 2007] - INFO - openPort()
[Sun Dec 30 12:04:15 2007] - DEBUG - Serial Client mode. Use device /dev/rfcomm0
[Sun Dec 30 12:04:18 2007] - DEBUG - findItem()
[Sun Dec 30 12:04:18 2007] - DEBUG - findItemInMode >default,(Init)<
[Sun Dec 30 12:04:18 2007] - DEBUG - findItem() after findItemInMode
[Sun Dec 30 12:04:18 2007] - DEBUG - findItem() EXIT
[Sun Dec 30 12:04:18 2007] - INFO - Exec cmd on init
[Sun Dec 30 12:04:18 2007] - DEBUG - handleCmdByKey() >(Init)<
[Sun Dec 30 12:04:18 2007] - DEBUG - getCommand for >(Init)<
[Sun Dec 30 12:04:18 2007] - DEBUG - ready to execute command
[Sun Dec 30 12:04:18 2007] - DEBUG - Process next command NULL parameters
[Sun Dec 30 12:04:18 2007] - INFO - processOneCommand>no description< >1<
[Sun Dec 30 12:04:18 2007] - INFO - Command: Exec
[Sun Dec 30 12:04:18 2007] - INFO - substParams >echo 'P=`which xte|grep xte|grep -v not|wc -l`; KD=`which kdialog|grep kdialog|grep -v not|wc -l`;if [ "x$KD" == "x1" ]; then M="kdialog --msgbox"; else M="xmessage"; fi; if [ "x$P" == "x1" ]; then true; else $M "ERROR: xautomation package is not installed"; fi'|bash -f -s<
[Sun Dec 30 12:04:18 2007] - INFO - execSimpleCmd >echo 'P=`which xte|grep xte|grep -v not|wc -l`; KD=`which kdialog|grep kdialog|grep -v not|wc -l`;if [ "x$KD" == "x1" ]; then M="kdialog --msgbox"; else M="xmessage"; fi; if [ "x$P" == "x1" ]; then true; else $M "ERROR: xautomation package is not installed"; fi'|bash -f -s<
[Sun Dec 30 12:04:18 2007] - INFO - Close port in child
[Sun Dec 30 12:04:18 2007] - DEBUG - initPort
[Sun Dec 30 12:04:18 2007] - DEBUG - ATZ
[Sun Dec 30 12:04:18 2007] - DEBUG - ATZ

OK

[Sun Dec 30 12:04:18 2007] - DEBUG - ATE0
[Sun Dec 30 12:04:18 2007] - DEBUG - ATE0

OK

[Sun Dec 30 12:04:18 2007] - DEBUG - AT+CSCS="8859-1"
[Sun Dec 30 12:04:19 2007] - DEBUG - OK

[Sun Dec 30 12:04:19 2007] - DEBUG - AT+CLIP=1
[Sun Dec 30 12:04:19 2007] - DEBUG - ERROR

[Sun Dec 30 12:04:19 2007] - DEBUG - AT+CGMI
[Sun Dec 30 12:04:19 2007] - DEBUG - +CGMI: "Motorola CE, Copyright 2000"

OK

[Sun Dec 30 12:04:19 2007] - DEBUG - AT+MODE=2
[Sun Dec 30 12:04:19 2007] - DEBUG - OK

[Sun Dec 30 12:04:19 2007] - DEBUG - AT+CMER=3,1,0,0,0
[Sun Dec 30 12:04:19 2007] - DEBUG - +MBAN: Motorola CE, Copyright 2000
AT+CMER=3,1,0,0,0

OK



---

### Post by Fab on 2008-01-07
No hints at all? :(

---

### Post by mike_mike on 2008-01-08
Well, start anyremote from console with -log option:
anyremote -log -f /pathto/cfg/file
try to use it and 
then send $HOME/.anyRemote/anyremote.log to [email]anyremote@mail.ru[/email]

---

### Post by mike_mike on 2008-01-08
2 Fab:
Connect to Motorila with cu or Minicom,
then enter
ATZ
AT+CMER=3,1,0,0,0
and try to press buttons on the phone.
If You did not see "+CKEV...." responces try to enter other AT+CMER=...
variants (see docs)

But i think java client should work OK on K1 :-)

---

### Post by mike_mike on 2008-01-08
Send logs of server mode to [email]anyremote@mail.ru[/email]

---

### Post by Fab on 2008-01-16
I did some days ago, but got no reply so far. Did you receive my mail?

---

### Post by mike_mike on 2008-01-17
No. Which subject does Your letter  have ?
Anyway, please, send it again to [email]anyremote@mail.ru[/email]

---

### Post by mike_mike on 2008-01-17
By the way, i've borrowed  Motorola RIZR Z3 to test. 
So i believe v4.2 will fix Your issues.

---

### Post by Fab on 2008-01-17
Sent again :) Subject is "anyremote ubuntuforums"

---

### Post by Fab on 2008-01-23
new log using the new version:

```
CFG - [Mode] PROCS
CFG - 	Back($$) = SetMode(LIST<|>);
CFG - 	Kill($$) = Exec(<|>kill `echo $(Param) | cut -d ' ' -f 1`);ExecAndSet(list,replace,SAME<|>,ps -o pid -o command -u `whoami` | tr -s ' ' | cut -d ' ' -f 1,2,3 | sed 's/$/,/' | grep -v sed | grep -v cut);
CFG - 	(EnterMode) = ExecAndSet(list,replace,User Processes<|>,ps -o pid -o command -u `whoami` | tr -s ' ' | cut -d ' ' -f 1,2,3 | sed 's/$/,/' | grep -v sed | grep -v cut);Set(menu,replace,Kill<|>);
CFG - [ModeEnd] PROCS
CFG - [Mode] TXT2
CFG - 	Back = Set(text,close<|>);SetMode(FILES<|>);
CFG - [ModeEnd] TXT2
CFG - [Mode] FILES
CFG - 	Back($$) = SetMode(LIST<|>);Set(list,replace,Available commands,Disk free space,Run Top, Stop Top, Uptime, User Processes, File List,Dmesg output<|>);Set(menu,replace,Choose<|>);
CFG - 	Choose($$) = ExecAndSet(list,replace,SAME<|>,echo 'cd `cat $HOME/.anyRemote/ar_storedir.tmp`;if [ -d $(Param) ]; then cd $(Param);fi;pwd>$HOME/.anyRemote/ar_storedir.tmp;ls -F| sed "s/$/,/"|sed "s/(/openbrace/g"|sed "s/)/closebrace/g";'|bash -f -s);Set(list,add,SAME,..<|>);
CFG - 	File info($$) = ExecAndSet(text,replace,File info<|>,cd `cat $HOME/.anyRemote/ar_storedir.tmp`;file $(Param));Set(text,add,SAME,\n<|>);ExecAndSet(text,add,File info<|>,cd `cat $HOME/.anyRemote/ar_storedir.tmp`;ls -l $(Param));SetMode(TXT2<|>);
CFG - 	(EnterMode) = ExecAndSet(list,replace,Files<|>,cd `cat $HOME/.anyRemote/ar_storedir.tmp`;echo `pwd`>$HOME/.anyRemote/ar_storedir.tmp;ls -F| sed 's/$/,/'|sed 's/(/openbrace/g'|sed 's/)/closebrace/g');Set(list,add,SAME,..<|>);Set(menu,replace,Choose,File info<|>);
CFG - [ModeEnd] FILES
CFG - [Mode] TXT
CFG - 	Back = Set(text,close<|>);SetMode(LIST<|>);
CFG - [ModeEnd] TXT
CFG - [Mode] LIST
CFG - 	Choose(Dmesg output) = ExecAndSet(text,replace,Dmesg output<|>,dmesg|tail -50);SetMode(TXT<|>);
CFG - 	Choose(User Processes) = SetMode(PROCS<|>);
CFG - 	Choose(File List) = SetMode(FILES<|>);
CFG - 	Choose(Uptime) = Set(list,close<|>);ExecAndSet(title<|>,uptime|tr -s ' '|cut -d ' ' -f 3,4,5);SetMode(default<|>);
CFG - 	Choose(Disk free space) = ExecAndSet(text,replace,Free Space<|>,df -kl|tr -s ' '|cut -f 1,4 -d ' ');SetMode(TXT<|>);
CFG - 	Back($$) = Set(list,close<|>);SetMode(default<|>);
CFG - 	(EnterMode) = Set(list,replace,Available commands,Disk free space,Uptime, User Processes,File List,Dmesg output<|>);Set(menu,replace,Choose<|>);
CFG - [ModeEnd] LIST
CFG - [Mode] default
CFG - 	0 = Exit<|>;
CFG - 	1 = SetMode(LIST<|>);
CFG - 	Back = Set(text,close<|>);
CFG - 	* * = Set(text,replace,Help,1 - Show list of features\n0 - Exit<|>);
CFG - 	(Connect) = ExecAndSet(status<|>,uname -n);ExecAndSet(title<|>,whoami);Set(icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default<|>);
CFG - 	Cancel = Exit<|>;
CFG - [ModeEnd] default
CFG - [Aliases]
CFG - 	Key POWER 	aliased to #
CFG - 	Key TEXT 	aliased to *
CFG - 	Key 69 	aliased to Cancel
CFG - 	Key -8 	aliased to Cancel
CFG - 	Key -11 	aliased to Cancel
CFG - [End]
CFG - [Alarms]
CFG - [End]
CFG - [Parameters]
CFG - 	AutoRepeat    No
CFG - 	Device        bluetooth:19
CFG - 	Log	      Yes
CFG - 	Retry Sec     5
CFG - 	Screen Menu   Yes
CFG - [End]
[Wed Jan 23 20:20:16 2008] - INFO - openPort()
[Wed Jan 23 20:20:16 2008] - INFO - registered SP for channel 19
[Wed Jan 23 20:20:16 2008] - INFO - Server mode: Waiting connection
[Wed Jan 23 20:20:16 2008] - INFO - listenAndAcceptSocketConn
[Wed Jan 23 20:20:35 2008] - INFO - listenAndAcceptSocketConn: accepted
[Wed Jan 23 20:20:35 2008] - INFO - Exec cmd on connect
[Wed Jan 23 20:20:35 2008] - INFO - processOneCommand >status< >uname -n< >1<
[Wed Jan 23 20:20:35 2008] - INFO - Command: ExecAndSet
[Wed Jan 23 20:20:35 2008] - INFO - substParams >uname -n<
[Wed Jan 23 20:20:35 2008] - INFO - execSimpleCmd >uname -n<
[Wed Jan 23 20:20:35 2008] - INFO - Close port in child
[Wed Jan 23 20:20:35 2008] - INFO - closeSocketPort
[Wed Jan 23 20:20:35 2008] - INFO - substParams >status<
[Wed Jan 23 20:20:35 2008] - INFO - Data is new
[Wed Jan 23 20:20:35 2008] - INFO - writeSocketConn 17 bytes
[Wed Jan 23 20:20:35 2008] - INFO - execCmdAndGetResults finished
[Wed Jan 23 20:20:35 2008] - INFO - processOneCommand >title< >whoami< >1<
[Wed Jan 23 20:20:35 2008] - INFO - Command: ExecAndSet
[Wed Jan 23 20:20:35 2008] - INFO - substParams >whoami<
[Wed Jan 23 20:20:35 2008] - INFO - execSimpleCmd >whoami<
[Wed Jan 23 20:20:35 2008] - INFO - Close port in child
[Wed Jan 23 20:20:35 2008] - INFO - closeSocketPort
[Wed Jan 23 20:20:35 2008] - INFO - substParams >title<
[Wed Jan 23 20:20:35 2008] - INFO - Data is new
[Wed Jan 23 20:20:35 2008] - INFO - writeSocketConn 16 bytes
[Wed Jan 23 20:20:35 2008] - INFO - execCmdAndGetResults finished
[Wed Jan 23 20:20:35 2008] - INFO - processOneCommand>no exec params< >1<
[Wed Jan 23 20:20:35 2008] - INFO - substParams >icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default<
[Wed Jan 23 20:20:35 2008] - INFO - Command: Set
[Wed Jan 23 20:20:35 2008] - INFO - Data is new
[Wed Jan 23 20:20:35 2008] - INFO - writeSocketConn 131 bytes
[Wed Jan 23 20:20:35 2008] - INFO - Start event forwarding
[Wed Jan 23 20:20:40 2008] - INFO - processOneCommand>no exec params< >1<
[Wed Jan 23 20:20:40 2008] - INFO - substParams >LIST<
[Wed Jan 23 20:20:40 2008] - INFO - Command: SetMode
[Wed Jan 23 20:20:40 2008] - INFO - processOneCommand>no exec params< >1<
[Wed Jan 23 20:20:40 2008] - INFO - substParams >list,replace,Available commands,Disk free space,Uptime, User Processes,File List,Dmesg output<
[Wed Jan 23 20:20:40 2008] - INFO - Command: Set
[Wed Jan 23 20:20:40 2008] - INFO - Data is new
[Wed Jan 23 20:20:40 2008] - INFO - writeSocketConn 99 bytes
[Wed Jan 23 20:20:40 2008] - INFO - processOneCommand>no exec params< >1<
[Wed Jan 23 20:20:40 2008] - INFO - substParams >menu,replace,Choose<
[Wed Jan 23 20:20:40 2008] - INFO - Command: Set
[Wed Jan 23 20:20:40 2008] - INFO - Data is new
[Wed Jan 23 20:20:40 2008] - INFO - writeSocketConn 25 bytes
[Wed Jan 23 20:20:51 2008] - INFO - Got disconnected
[Wed Jan 23 20:20:51 2008] - INFO - Wait 5 seconds to connect/open server socket ...
[Wed Jan 23 20:20:56 2008] - INFO - openPort()
[Wed Jan 23 20:20:56 2008] - ERROR - socket was already opened
[Wed Jan 23 20:20:56 2008] - INFO - Server mode: Waiting connection
[Wed Jan 23 20:20:56 2008] - INFO - listenAndAcceptSocketConn
[Wed Jan 23 20:20:56 2008] - INFO - listenAndAcceptSocketConn: accepted
[Wed Jan 23 20:20:56 2008] - INFO - Exec cmd on connect
[Wed Jan 23 20:20:56 2008] - INFO - processOneCommand >status< >uname -n< >1<
[Wed Jan 23 20:20:56 2008] - INFO - Command: ExecAndSet
[Wed Jan 23 20:20:56 2008] - INFO - substParams >uname -n<
[Wed Jan 23 20:20:56 2008] - INFO - execSimpleCmd >uname -n<
[Wed Jan 23 20:20:56 2008] - INFO - Close port in child
[Wed Jan 23 20:20:56 2008] - INFO - closeSocketPort
[Wed Jan 23 20:20:56 2008] - INFO - substParams >status<
[Wed Jan 23 20:20:56 2008] - INFO - Data is new
[Wed Jan 23 20:20:56 2008] - INFO - writeSocketConn 17 bytes
[Wed Jan 23 20:20:56 2008] - INFO - execCmdAndGetResults finished
[Wed Jan 23 20:20:56 2008] - INFO - processOneCommand >title< >whoami< >1<
[Wed Jan 23 20:20:56 2008] - INFO - Command: ExecAndSet
[Wed Jan 23 20:20:56 2008] - INFO - substParams >whoami<
[Wed Jan 23 20:20:56 2008] - INFO - execSimpleCmd >whoami<
[Wed Jan 23 20:20:56 2008] - INFO - Close port in child
[Wed Jan 23 20:20:56 2008] - INFO - closeSocketPort
[Wed Jan 23 20:20:56 2008] - INFO - substParams >title<
[Wed Jan 23 20:20:56 2008] - INFO - Data is new
[Wed Jan 23 20:20:56 2008] - INFO - writeSocketConn 16 bytes
[Wed Jan 23 20:20:56 2008] - INFO - execCmdAndGetResults finished
[Wed Jan 23 20:20:56 2008] - INFO - processOneCommand>no exec params< >1<
[Wed Jan 23 20:20:56 2008] - INFO - substParams >icons,ADMIN,1,plus,2,default,3,default,4,default,5,default,6,default,7,default,8,default,9,default,*,default,0,exit,#,default<
[Wed Jan 23 20:20:56 2008] - INFO - Command: Set
[Wed Jan 23 20:20:56 2008] - INFO - Data is new
[Wed Jan 23 20:20:56 2008] - INFO - writeSocketConn 131 bytes
[Wed Jan 23 20:20:56 2008] - INFO - Start event forwarding
[Wed Jan 23 20:21:01 2008] - INFO - writeSocketConn 16 bytes
[Wed Jan 23 20:21:01 2008] - INFO - Got disconnected
[Wed Jan 23 20:21:01 2008] - INFO - Got signal, exiting
[Wed Jan 23 20:21:01 2008] - INFO - closeSocketPort
```

same problems as before :/

---

### Post by mike_mike on 2008-01-25
Fab, 
1. have You tested AT mode ?
2. have You tried JamSE ?

---

### Post by mike_mike on 2008-01-25
Fab,
thanks You for logs...
By the way, after anyRemote had connected to RIZR, did You saw
output of "uname -n" and "whoami" commands on screen of cell phone  ?

---

### Post by mike_mike on 2008-01-26
Hello Fab,

Thank You for log on ubuntuforums. Unfortunately it does not contains much info. So i still could not get information about possible reasons of this
strange behaviour. 

In common, there could be a lot of reason:
1. bugs in anyremote and java client
2. improper software configuration
3. conflict with some other software (do You have kdebluetooth running?)
4. hardware problem

I saw in the middle of the log:
>[Wed Jan 23 20:20:51 2008] - INFO - Got disconnected
>[Wed Jan 23 20:20:51 2008] - INFO - Wait 5 seconds to connect/open server socket ...
>[Wed Jan 23 20:20:56 2008] - INFO - openPort()
So, have You restarted java client or it have lost connection with another reason ?

>with some configs, I can't do anything at all.. with some, I can press one
>button (ie mpd/amarok stop), but then it says disconnected in the terminal
So, in which cases it works at least until first button is pressed ?

Well, i'm really want to help You. But in this case You need to help me
to make testing step-by-step. If You agree to spend some time in testing
contact me via e-mail (actually i visit ubuntu forums only from time to time).

---

### Post by mike_mike on 2008-01-26
Actually anyRemote v4.2 works perfect on my Kubuntu 7.10 with Motorola RIZR Z3

---

### Post by Nonno Bassotto on 2008-01-28
I like this app very much, but the cfg files look very scaring to edit. I'm looking for a config file to use MPD with bemused emulation. Does anybody have one?

---

### Post by mike_mike on 2008-01-29
2 Nonno Bassotto:
In general You can use cfg-data/Bemused-emulation/template.cfg as a starting point.
I spent about only 5 minutes )))) to wrote mpd.cfg. But I not test yet it, so i'm not sure it will work properly.
Anyway, please, try it.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%
% anyremote configuration file for MPD management. (Server-mode Bemused emulation)
% Prerequisites amixer utility, Bemused client installed on cell phone
%

% STATUS stable
% XTEST no
% SOUND app
% ENV no

% Uncomment if needed
%AutoRepeat=false
%Baudrate=19200
%Device=bluetooth:19
%Log=true
Screen=true

GuiAppName=MPD
GuiAppBinary=mpc
GuiAppRun=echo 'P=`ps -ef|grep mpd|grep -v grep|grep -v anyremote|grep -v nedit|grep -v mpd.cfg`; if [ "x$P" == "x" ]; then echo NOK; else echo OK; fi' | bash -f -s
GuiAppType=Application

[Aliases]
STRT=PLAY
LADD=PLAY
STEN=STOP
[End]

[Keys]

(Init)=Macro(CheckMPC);Macro(CheckMPD);Macro(CheckPL);

CheckMPC=Exec(echo 'P=`which mpc|grep mpc|grep -v not|wc -l`; KD=`which kdialog|grep kdialog|grep -v not|wc -l`;if [ "x$KD" == "x1" ]; then M="kdialog --msgbox"; else M="xmessage"; fi; if [ "x$P" == "x0" ]; then $M "ERROR: mpc client is not installed"; fi'|bash -f -s);
CheckMPD=Exec(echo 'P=`ps -ef|grep mpd|grep -v grep|grep -v mpd.cfg|wc -l`; KD=`which kdialog|grep kdialog|grep -v not|wc -l`;if [ "x$KD" == "x1" ]; then M="kdialog --msgbox"; else M="xmessage"; fi; if [ "x$P" == "x0" ]; then $M "ERROR: mpd is not run"; fi'|bash -f -s);
CheckPL =Exec(echo 'P=`mpc playlist |wc -l`; KD=`which kdialog|grep kdialog|grep -v not|wc -l`;if [ "x$KD" == "x1" ]; then M="kdialog --msgbox"; else M="xmessage"; fi; if [ "x$P" == "x0" ]; then $M "ERROR: mpd playlist is empty"; fi'|bash -f -s);

EXIT=Exec(mpd --kill)  
FADE=Exec(mpc volume 0) 
FFWD=Exec(mpc seek +00:00:05) 
INF2=Send(string,INF2ACK);Send(bytes,128,0,0,0,128,0,0,0,1,0,0);ExecAndSend(string,mpc|head  -1|sed "s/.*\///;s/(/-/g;s/)/-/g");Send(bytes,0,0)
INFO=Send(string,INFOACK);Send(bytes,128,0,0,0,128,0,0,0,1,0,0);ExecAndSend(string,mpc|head  -1|sed "s/.*\///;s/(/-/g;s/)/-/g")
NEXT=Exec(mpc next) 
PAUS=Exec(mpc toggle) 
PLAY=Exec(mpc play) 
PREV=Exec(mpc prev) 
RWND=Exec(mpc seek -00:00:05) 
STOP=Exec(mpc stop) 
VOLM($$)=Exec(mpc volume $(Param))
%REPT
%SHFL

% The following is ditry trick. Replays are not real, just to satisfy client.
CHCK=Send(string,Y);
DINF=Send(string,DINFACK);Send(bytes,0,0,0,244,0,0,32,0,0,0,0,2);
DLST=Send(bytes,1);Send(string,Root);Send(bytes,0,1,482,0)
DOWN=Send(bytes,0,100);Send(string,NoName)
FINF=Send(string,FINFACK);Send(bytes,0,0,0,100);
GVOL=Send(string,GVOLNAK)
LIST=Send(bytes,1);Send(string,Root);Send(bytes,0,1,482,0)
PLEN=Send(bytes,0,100)
PLST=Send(string,PLSTACK);Send(bytes,0,1,35,10);Send(string,NoName);Send(bytes,10,0)
%SEEK=
%SLCT=
VERS=Send(string,VERSACK);Send(bytes,1,73);
[End]

---

### Post by mike_mike on 2008-01-29
Beware of newlines !!!

---

### Post by Nonno Bassotto on 2008-01-29
I get some connection problems when using anything but play, but I have yet to investigate if this has to do with the config file. I'll try with other bemused applications and let you know.Thank you :)

---

### Post by mike_mike on 2008-02-01
I have tested  config file to use MPD with bemused emulation. It works well
on my Fedora8.

---

### Post by jasonmeansfriend on 2008-02-08
hi all,

just found out about this app... nice idea!

but just one problem, i researched on the internet and my phone (motorola RAZR v3t) is JSR-82 complieant.

now, everything seems fine until i go to the anyRemote app on my phone. whatever i type in that socket thing:
("comm:COM0", "socket://enter.ip.here<colon>port", "socket://bluetooth:10", "socket://bluetooth:16" (i tried all 4, i couldn't think of anything else)), i get a half-error-half-working screen.

at the top, i get a virtual "keypad" thing where i have volume controls (volume down, mute, volume up) and media controls (play/pause/next/prev/stop/etc.); at the bottom i get this error:

openConnection Exception
java.lang.SecurityException
javax.microedition.io.Connect
or.comm was denied

on the 4 lines. anyone know where i'm going wrong? i installed the deb in ubuntu gutsy and the jar file (sent to my phone thru bluetooth) in the phone.

from this screen, i can either "EXIT" or "DISCONNECT"

the "<colon>" above was ":" but to avoid a smiley face where inappropriate...

sorry if this post was too long, the prospect of having a cool remote with me was tempting... waiting for your replies... please help...


jason

---

### Post by Fab on 2008-02-09
Okay, I am back again :P Completely reinstalled anyremote 4.2, connected with phone with the gnome gui, using mpd server config. I press the play button, mpd starts to play, I press another button, the phone says

```
openConnection Exception
javax.bluetooth.BluetoothConnectionException errno=-1
```

But the computer still thinks it's connected to the phone. If I press disconnect on the phone, and reconnect again (without closing anyremote on either side), it's still displaying the same screen like before I disconnected. Even if I exit the anyremote app on the phone, ganyremote still says "Connected to phone".

Another thing I noticed is that if I try to do the AT mode test from ganyremote, it says it doesn't work, with the message "Cannot get port to connect. Are the device available?" The manual test like in the docs still works, and I can see the keys I press in my terminal.

If I try a config file for AT mode, for example Mousetest, the first key press works okay, but after that it's the same like with server mode, except it doesn't display an error message :(

Also, I am using a Motorola KRZR K1, I think that is a different model than the RAZR or RIZR you were talking about.


> Hello Fab,

Thank You for log on ubuntuforums. Unfortunately it does not contains much info. So i still could not get information about possible reasons of this
strange behaviour.

In common, there could be a lot of reason:
1. bugs in anyremote and java client
2. improper software configuration
3. conflict with some other software (do You have kdebluetooth running?)
4. hardware problem

I saw in the middle of the log:
>[Wed Jan 23 20:20:51 2008] - INFO - Got disconnected
>[Wed Jan 23 20:20:51 2008] - INFO - Wait 5 seconds to connect/open server socket ...
>[Wed Jan 23 20:20:56 2008] - INFO - openPort()
So, have You restarted java client or it have lost connection with another reason ?

>with some configs, I can't do anything at all.. with some, I can press one
>button (ie mpd/amarok stop), but then it says disconnected in the terminal
So, in which cases it works at least until first button is pressed ?

Well, i'm really want to help You. But in this case You need to help me
to make testing step-by-step. If You agree to spend some time in testing
contact me via e-mail (actually i visit ubuntu forums only from time to time).

I do not disconnect or restart anything, I get disconnected as soon as I try to press any button a second time (ie play, then pause -> pause causes phone to disconnect). Only bluetooth software I am running is the gnome bluetooth applet, might that be causing a conflict? I'll send you an email so you read this (maybe someone else has the same problem too..)

Regards,
Fab

---

### Post by mike_mike on 2008-02-10
You need not type anything in address field if You plans to connect  to anyRemote throgh bluetooth. It needs to run search instead. And then select one of items to connect to.
Anyway, in general it is possible to enter something like: btspp://00:17:E3:92:C5:33:19
(btspp://<bluetooth adddress>:19)

---

### Post by mike_mike on 2008-02-10
2 Fab:
Well, situation is strange. At this moment i have no ideas why it could be.
Anyway, i have plans to borrow K1 somethere to test.

---

### Post by Fab on 2008-02-10
> **mike_mike said:**
> 2 Fab:
Well, situation is strange. At this moment i have no ideas why it could be.
Anyway, i have plans to borrow K1 somethere to test.

thank you for your time :)

---

### Post by maxehhh on 2008-02-12
anybody tried this with a K1?

Edit: can anybody upload this to rapidshare or anywhere else? because i can't download it from sf =(

---

### Post by Fab on 2008-02-12
> **maxehhh said:**
> anybody tried this with a K1?

Edit: can anybody upload this to rapidshare or anywhere else? because i can't download it from sf =(

I tried it with a K1 without success (see above). It's not yet clear wether the problem is the phone or the computer hardware.. But try yourself, maybe you have more luck than me ;)

As far as SF is concerned, try a different mirror, they should work..

---

### Post by maxehhh on 2008-02-12
> **Fab said:**
> I tried it with a K1 without success (see above). It's not yet clear wether the problem is the phone or the computer hardware.. But try yourself, maybe you have more luck than me ;)

As far as SF is concerned, try a different mirror, they should work..

I tried but i always got redirected to SF.

btw... i have AMD64, it isn't really a problem, is it?

Edit: i finally manage to download it, but when i execute the make (after ./configure) i get this

> 
root@bl1zzard:/home/bl1zzard/Desktop/anyremote-4.2# make
Making all in src
make[1]: Entering directory `/home/bl1zzard/Desktop/anyremote-4.2/src'
gcc -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g   -o anyremote atsend.o btio.o main.o cmds.o parse.o utils.o xemulate.o conf.o -lbluetooth -lXtst 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[1]: *** [anyremote] Error 1
make[1]: Leaving directory `/home/bl1zzard/Desktop/anyremote-4.2/src'
make: *** [all-recursive] Error 1


---

### Post by mike_mike on 2008-02-13
2 maxehhh:
It needs to install libXtst (packages libxtst libxtst-dev)
Alternatively it is possible to run ./configure --disable-xtest
but in this case it will be impossible to use mouse/keyboard emulation commands.

---

### Post by maxehhh on 2008-02-13
Ok thanks, anyway i will re-install ubuntu to leave it like it were before i started with the xgl, etc. and will install this thing first.

Edit:  

> No candidate version found for bluez-passkey-gnome
No candidate version found for bluez-pin


Where can i get a repository for this? i tried downloading from debian.org the packages but i get and error when i try to install it by my self

> root@bl1zzard:/home/bl1zzard/Desktop# dpkg -i bluez-pin_0.25-1_amd64.deb 
Selecting previously deselected package bluez-pin.
(Reading database ... 89995 files and directories currently installed.)
Unpacking bluez-pin (from bluez-pin_0.25-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of bluez-pin:
 bluez-pin depends on dbus-1 (>= 0.23.4); however:
  Package dbus-1 is not installed.
 bluez-pin depends on dbus-glib-1 (>= 0.23.4); however:
  Package dbus-glib-1 is not installed.
 bluez-pin depends on libbluetooth1 (>= 2.15); however:
  Package libbluetooth1 is not installed.
dpkg: error processing bluez-pin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez-pin


And when i try to install dbus-1 it says

> root@bl1zzard:/home/bl1zzard/Desktop# apt-get install dbus-1 dbus-glib-1 libbluetooth1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dbus-1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dbus
E: Package dbus-1 has no installation candidate


---

### Post by mike_mike on 2008-02-14
2 maxehhh:
Use "adept" package manager to install *deb's.

---

### Post by maxehhh on 2008-02-17
> **mike_mike said:**
> 2 maxehhh:
Use "adept" package manager to install *deb's.

I've already installed adept manager and when i select bluez-pin to request install it doesn't select the package for installation.


Edit: i managed it to install the bluez-passkey-gnome and now the only thing left to install it's bluez-pin.

---

### Post by woferon on 2008-02-18
Hey, can you please tell me how am I supposed to connect if I wanna use usb cable ? I've installed AnyRemote from .deb, uploaded java to my K510i phone and... well, do I have to create any special cfg for usb connection? and what adress should I write on my phone to connect to ? (search function on my phone doesn't find anything). Thanks ;)

---

### Post by mike_mike on 2008-02-18
2 woferon:
There is no needs to create special files for USB connection. You should play 
with "-s" command line parameter instead.
Seems You want to use AT mode, am i right ???
 If  so,  specify "-s /dev/ttySX" option to
connect to the phone (where "dev/ttySX" is normally is /dev/ttyS0, but could vary 
depending of system configuration)

---

### Post by maxehhh on 2008-02-18
mike_mike, i read that i don't need the bluez-pin to make the bluetooth work, the only problem i have it's that my ubuntu doesn't recognize the USB, when i unplug it, it says: Device has been removed, and when i plug it in it says the opposite, but it doesn't show the device :\

---

### Post by woferon on 2008-02-18
Thanks, mike_mike, it works now :)  I just have one question, is it possible to put some kind of image on my phone's screen which would help me remember which key does what ? :) Because it looks pretty bad showing only  "Done."  and   "Connect / More" .

PS. You can add Sony Ericsson K510i    to    [http://anyremote.sourceforge.net/devices.html](http://anyremote.sourceforge.net/devices.html)    as USB connection works fine. Can't test if Bluetooth / IrDA connection works as I don't have any of those ... gonna borrow bluetooth from a friend and I'll test :)

---

### Post by mike_mike on 2008-02-19
2 woferon:
In AT-mode it is impossible to show  images on screen of cell phone. If You will manage
to borrow  bluetooth dongle somethere and if K510 supports JSR-82 .... then it will be possible
to use anyRemote in Server-mode with all eye-candys :))

---

### Post by stareez on 2008-02-19
Hi,
I'm stuck at installing anyremote. Many errors about "xemulate", how to solve this?
Please help a newbe..

```
oscar@Zepto:~/anyremote-4.3$ make
Making all in src
make[1]: Entering directory `/home/oscar/anyremote-4.3/src'
gcc -DPACKAGE_NAME=\"anyremote\" -DPACKAGE_TARNAME=\"anyremote\" -DPACKAGE_VERSION=\"4.3\" -DPACKAGE_STRING=\"anyremote\ 4.3\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"anyremote\" -DVERSION=\"4.3\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DHAVE_ISASCII=1 -DHAVE_SELECT=1 -DHAVE_STRCHR=1 -DHAVE_STRSTR=1 -I.    -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g -MT xemulate.o -MD -MP -MF .deps/xemulate.Tpo -c -o xemulate.o xemulate.c
xemulate.c:31:22: error: X11/Xlib.h: No such file or directory
xemulate.c:32:34: error: X11/extensions/XTest.h: No such file or directory
xemulate.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
xemulate.c: In function ‘freeDisplay’:
xemulate.c:47: error: ‘disp’ undeclared (first use in this function)
xemulate.c:47: error: (Each undeclared identifier is reported only once
xemulate.c:47: error: for each function it appears in.)
xemulate.c:48: warning: implicit declaration of function ‘XCloseDisplay’
xemulate.c: In function ‘mouseClick’:
xemulate.c:57: warning: implicit declaration of function ‘XTestFakeButtonEvent’
xemulate.c:57: error: ‘disp’ undeclared (first use in this function)
xemulate.c:57: error: ‘True’ undeclared (first use in this function)
xemulate.c:57: error: ‘CurrentTime’ undeclared (first use in this function)
xemulate.c:58: error: ‘False’ undeclared (first use in this function)
xemulate.c: At top level:
xemulate.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘keysymStr2keycode’
xemulate.c: In function ‘keyboardClick’:
xemulate.c:80: error: ‘KeyCode’ undeclared (first use in this function)
xemulate.c:80: error: expected ‘;’ before ‘kc’
xemulate.c:82: warning: implicit declaration of function ‘XTestFakeKeyEvent’
xemulate.c:82: error: ‘disp’ undeclared (first use in this function)
xemulate.c:82: error: ‘kc’ undeclared (first use in this function)
xemulate.c:82: error: ‘True’ undeclared (first use in this function)
xemulate.c:82: error: ‘CurrentTime’ undeclared (first use in this function)
xemulate.c:83: error: ‘False’ undeclared (first use in this function)
xemulate.c: In function ‘emulateCommands’:
xemulate.c:94: error: ‘disp’ undeclared (first use in this function)
xemulate.c:95: warning: implicit declaration of function ‘XOpenDisplay’
xemulate.c:106: warning: implicit declaration of function ‘keysymStr2keycode’
xemulate.c:106: error: ‘False’ undeclared (first use in this function)
xemulate.c:106: error: ‘CurrentTime’ undeclared (first use in this function)
xemulate.c:113: error: ‘True’ undeclared (first use in this function)
xemulate.c:130: warning: implicit declaration of function ‘XTestFakeMotionEvent’
xemulate.c:139: warning: implicit declaration of function ‘XTestFakeRelativeMotionEvent’
xemulate.c:186: warning: implicit declaration of function ‘XFlush’
make[1]: *** [xemulate.o] Error 1
make[1]: Leaving directory `/home/oscar/anyremote-4.3/src'
make: *** [all-recursive] Error 1

```

---

### Post by mike_mike on 2008-02-19
2stareez:
>error: X11/Xlib.h: No such file or directory
>error: X11/extensions/XTest.h
You have to install package with these headers ( ... and Xtst libs also). 
See [http://anyremote.sourceforge.net/pre.html](http://anyremote.sourceforge.net/pre.html) for details.

---

### Post by woferon on 2008-02-19
mike_mike:
I've bought bluetooth today, will receive it tommorow. 
BTW Can you please tell me why Server-mode can't be run by usb cable? I just don't get what's difference :)

---

### Post by mike_mike on 2008-02-20
2 woferon:
Well, in general it could - but only if java in phone have access to com port.
And did not manage to work anyRemote with this type of connection yet. 
Anyway You can try :-)))

---

### Post by stareez on 2008-02-20
Thanks Mike, Installing those packages did the trick!
Now I can connect, just need to learn to config the cfg right.

Edit: I use anyremote 4.3 and ganyremote 2.5, it works fine now with my Nokia 5310!

---

### Post by mike_mike on 2008-02-20
2 stareez:
Just to clarify... Do You use anyRemote in Server mode via bluetooth ?
(i'm going top add 5310 to list of supported models)

---

### Post by stareez on 2008-02-21
2 mike_mike:

I have run: ./configure
make 
sudo make install

I get following when trying to start anyremote:
```
oscar@Zepto:~/anyremote-4.3$ anyremote
Search configuration file /home/oscar/.anyremote.cfg
Search configuration file ./.anyremote.cfg
Can not find configuration file to use or incorrect content of configuration file detected.
Can not initialize configuration. Exiting.

```

When I start ganyremote I get following:
```
oscar@Zepto:~/anyremote-4.3$ ganyremote
Starting backgroung threads
FrontEnd init
FrontEnd thread is running
FrontEnd socket created
FrontEnd socket after listen

```
With ganyremote I can remote my computer with bluetooth.

Phone: Nokia 5310

---

### Post by mike_mike on 2008-02-21
2 stareez:
You need to run anyremore with "-f /path/to/cfg/file" option.Just to clarify... 

Do You use anyRemote in Server mode via bluetooth ?
(i'm going top add 5310 to list of supported models)

---

### Post by woferon on 2008-02-21
2 mike_mike:
I've bought bluetooth adapter, installed and ... doh, I think something's wrong here. When I connect to the computer with anyremote (java one) I can see few "buttons" which show what key's I use at the moment and there's, I guess, error under them. It says
```
openConnection
Exception
java.lang.IllegalArgumen
```
the rest is running out of screen, so can't quote it. Does it mean that my phone can't be connected via bluetooth? Tried it in Server-mode, can't check AT mode because it won't "run", I have no idea why, simply when I click "run" in ganyremote it doesn't run. Any ideas?

Edit:

Just realised ... when trying to use AT mode  it says "Disconnected from phone", anyremote  on my phone also doesn't find anything when I use search function (well, bluetooth connection works as I can enter my phone from computer and transfer files, so it's not the case for sure..)

Edit2: doh... damn typo's -.- they're following me :P

---

### Post by mike_mike on 2008-02-22
2 woferon:
Have You managed to solve issues ?
If no:
1. run anyremote from command line with "-f ...." option. Use cfg.file from Server-mode
directory.
2. Are the page amd inqury scan enabled on PC side ? (see docs about that)
3. Start java client and run search.

---

### Post by stareez on 2008-02-23
2: mike_mike

Thanks for the help! Now I run anyRemote in Server mode via bluetooth on my Nokia 5310.
It works great!

---

### Post by dogscoff on 2008-04-04
I've been playing with anyremote the last few days. Got it installed and working both on PC and phone. The two are talking to each other, I'm at the point now where I need to write some .cfg files. The ones supplied don't work on my system for some reason (I think running gnome rathr than kde might be a big part of it.)

I'm particularly interested in getting working cfgs for vlc and totem. 
From vlc's docs I see you can start it in --intf rc mode, which will allow it to accept commands from the terminal. Could I just plug some of these commands into a cfg file and control vlc that way? Am I on the right tracks here?

---

### Post by mike_mike on 2008-04-08
2 dogscoff:
Firstly, it is good idea to find out why supplied cfg files does not works.
Please, run anyRemote with -log option and send log files to [email]anyremote@mail.ru[/email]

As for vlc, please see cfg-data/Server-mode/vlc.cfg for details.

---

### Post by dogscoff on 2008-04-10
Thanks for the reply, i will do email you in a few days. 
Is anyremote designed with kde in mind rather than gnome? From memory (not at my home PC right now, so I can't check) the error message were about something called dbus, which google told me was kde only. Many of the cfg files also use "kdialog" which doesn't seem to be recognised by my system, and the name looks like a kde app.

---

### Post by mike_mike on 2008-04-10
No, anyRemote is a console application and should work with any WM. 
DCOP (not dbus) is KDE-related thing and used only to manage KDE-related apps.
kdialog used in many cfg.files, but with keepeng in mind possibility to work in non-KDE environment (in this case xmessage will be used)

---

### Post by dogscoff on 2008-04-10
Yes, Dcop, that's it. What is the gnome alternative to dcop? The VLC config I found seemed to rely on dcop, but of course I don't have it. 

Maybe I have downloaded the wrong config files somwhow?

---

### Post by mike_mike on 2008-04-11
Mmm ... VLC config should NOT rely on DCOP. It uses wget instead.
Please post suspicious :-) part of VLC config here.

---

### Post by dogscoff on 2008-04-12
Well damn... it works.. .mostly. What I did differently:

1 - I copied the vlc.cfg from server-mode to ~/.anyremote.cfg
2 - I used anyremote rather than the ganyremote gui (which I thought would make things easier)
3 - instead of opening vlc and then opening a video file from the PC, I used the file browser on the mobile (hadn't noticed it before!)

So the the file browser works, pause/ play/ back forwards seem to work. Volume doesn't work ( amixer: Unable to find simple control 'Master',0 ) and I can't figure out how to get to DVDs from the phone's file browser, but I'm most of the way there.

This is so cool... even my wife had to admit it, and she said I was being ridiculously geeky when I first explained to her what I was trying to do...

Thanks for your help mike, any more advice would be welcome but I'm pretty happy already =-) =-)

---

### Post by dogscoff on 2008-04-13
OK, got the volume control working: I changed 
1=Exec(amixer $(mixer_card) sset,master,0 5%-    -q)

to 

1=Exec(amixer $(mixer_card) sset Front,0 5%-    -q)

Volume controls now work perfectly. Anyone know how to open and play a dvd in vlc from the phone's browser?

---

### Post by mike_mike on 2008-04-14
2 dogscoff:
by the way, which phone/model do You use with anyRemote ?
Which kind of connection do You use (bluetooth/IR/HTTP interface/...  ) ?

---

### Post by mike_mike on 2008-04-14
2 dogscoff:

>Anyone know how to open and play a dvd in vlc from the phone's browser?
Not yet. I'm going to investigate this.

---

### Post by dogscoff on 2008-04-14
> **mike_mike said:**
> 2 dogscoff:
by the way, which phone/model do You use with anyRemote ?
Which kind of connection do You use (bluetooth/IR/HTTP interface/...  ) ?

Sony Ericsson k800i via bluetooth. This phone really is an all purpoose device for me now... phone, camera, video camera, mp3 & movie player, radio... and now PC remote control as well. All i need now is a way for it to fetch me beer from the fridge. 

BTW, the VLC config file I used *does* use wget and not dcop. I don't know where I go that idea from =-/

---

### Post by kwaanens on 2008-04-21
Here are 64 bit packages. I had to struggle a bit to get this going, but after getting 64 bit, everything was smooth sailing :)
Run ganyremote in terminal and you will likely figure out what depoendencies your are missing.

---

### Post by mike_mike on 2008-04-22
Could You please send me the patch to [email]anyremote@mail.ru[/email] ?

---

### Post by aaron552 on 2008-04-23
Hi. I've had anyremote working over bluetooth (in server mode) for a while now, but there has always been one thing that doesn't work. Any config that depends on imagemagick crashes my phone (nokia 6234). The screen goes white and the start video plays again, so i assume something went wrong somewhere. I have no idea how to fix this, can anyone help?

---

### Post by mike_mike on 2008-04-25
Yes, i've got the same behavoiur witn 6288. Please, read
[http://anyremote.sourceforge.net/phones.html](http://anyremote.sourceforge.net/phones.html)
Seems this could be Nokia's bug.

---

### Post by n0l4n on 2008-05-06
I get an error on my 5500 Sport:

```
openConnection Exeption java.io.IOExeption SymbianOS error=-1 : General: System error
```
The client is 4.5-2_all

This is the log file on the PC:

```
[Tue May  6 15:53:08 2008] - DEBUG - mainRoutine
[Tue May  6 15:53:08 2008] - INFO - openPort()
[Tue May  6 15:53:08 2008] - DEBUG - Bluetooth Sockets Server mode. Use channel 19
[Tue May  6 15:53:08 2008] - INFO - registered SP for channel 19
[Tue May  6 15:53:08 2008] - DEBUG - findItemInMode >default,(Init)<
[Tue May  6 15:53:08 2008] - DEBUG - findItemInMode: No parameters suspected. Item does not found.
[Tue May  6 15:53:08 2008] - DEBUG - initPort
[Tue May  6 15:53:08 2008] - INFO - Server mode: Waiting connection
[Tue May  6 15:53:08 2008] - INFO - listenAndAcceptSocketConn

```

---

### Post by mike_mike on 2008-05-07
Well, does 5500 finds PC with anyRemote ?
Does java client have permissions to connect ? (it needs to set midlet permissions)

---

### Post by n0l4n on 2008-05-07
yes. It has permissions (i`m asked about permissions every time i start the app). The phone finds anyremote. i get some services to conect to like COM0, IR0, USB0 and BT0-BT63. No mather what i choose i get the same error.

---

### Post by mike_mike on 2008-05-08
If i remembet correctly, there should be some menu like "Allow ... to untrusted midlets" or "Trust ... untrusted midlets" where is it possible to set additional permissions. Have You found that one ?

---

### Post by mike_mike on 2008-05-08
Please, read this:
[http://www.allaboutsymbian.com/forum/showthread.php?t=56071](http://www.allaboutsymbian.com/forum/showthread.php?t=56071)
Will soft-reset could helps You ?

---

### Post by n0l4n on 2008-05-09
I resetted the phone. I found the menu with permissions. Its "Suit Settings". I`ve set everything to "Always allowed". The error is still present. Are there any logs in the phone i can send you?
Apps like BluePad and Amora work fine btw.

---

### Post by mike_mike on 2008-05-12
Have You reinstalled java client after resetting the phone ?
By the way, is You phone operator-locked ?

---

### Post by saverjack on 2008-06-04
how to install the software in ubuntu 7.10

---

### Post by saverjack on 2008-06-04
> **elektronaut said:**
> Have you ever been attending presentations envying all the time the guy in front using his mobile phone to switch the slides? Or dreamed of sitting on the sofa and controlling your music player without having to go to the computer?
At least I did and so I searched on the net for possible solutions. Most of the projects are either outdated, only work for certain phones or certain software on the computer. Finally I discovered anyremote from Mike Fedotov, which you can download from the project's site at sourceforge: 

[http://sourceforge.net/projects/anyremote/](http://sourceforge.net/projects/anyremote/)

The great thing is that it works for different connections like bluetooth, infrared or serial cable (though I only tested bluetooth) and, according to the project notes, for all kinds of phones. Several configuration files for different software, e.g. amarok, xmms, etc. are included, and it is easy to write new ones. 

[SIZE="2"]**NB:**[/SIZE] [LIST]
[*]This was tested on Ubuntu 6.10 (32bit).
[*]There is also the KDE version kAnyRemote, which provides a little panel applet to change configuration files. I also tried this flavor, as I have KDE installed. But I'll focus on anyremote, the CLI version, as it has the same functionality, and you don't need to install any KDE libraries.
[*]I only describe using bluetooth and assume you have already set up a bluetooth connection between your computer and your phone.
[*]I assume you have a java enabled phone (JSR-82), I haven't investigated yet how this works if your phone doesn't support java. 
[*][COLOR="Blue"]*This post will be edited if questions or suggestions come up.*[/COLOR]
[/LIST]
[SIZE="2"]**Steps to take:**[/SIZE]
[LIST=1]
[*]**Install dependencies**
I can't tell you exactly what you need, because I encountered only one missing package, and that was *libbluetooth-dev*. I guess you need the bluetooth libraries for compilation even if you'll use another kind of connection. So I'll simply list all the blue* packages that are installed on my system. Corrections considering unnecessary packages or missing packages are welcome! You can either use synaptic or aptitude or apt-get on the command line to install the packages, so for instance you have to enter: ```
$ sudo aptitude install checkinstall *gcc build-essential other_missing_packages*
```
[LIST]
[*]gcc
[*]build-essential
[*]bluetooth
[*]bluez-cups
[*]bluez-hcidump
[*]bluez-passkey-gnome
[*]bluez-pin
[*]bluez-utils
[*]gnome-bluetooth
[*]libbluetooth2
[*]libbluetooth2-dev
[/LIST]

[*]**Install anyremote**
In case you have already compiled from source code before, this is nothing new to you. If not: Don't be afraid, there is no dark magic involved ;-) After downloading anyremote-*.tar.gz, go to the download directory, decompress the file, change to the now extracted directory and prepare for installation:
```
$ tar xvzf anyremote-*.tar.gz
$ cd anyremote-*
$ ./configure
$ make

```
Now, I advise you to have checkinstall installed, this will allow you to easily remove anyremote later on. ```
$ sudo aptitude install checkinstall
```
We install it:
```
$ sudo checkinstall
*or, if checkinstall is not available*
$ sudo make install
```
[*]**Install the Java client**
The anyremote directory we extracted earlier contains the phone client file anyRemote.jar. Install this on your phone, either by sending it via bluetooth or by using a data cable.
[/LIST]
Now, using an existent bluetooth connection, we can start anyremote and indicate which configuration file to use:
```
$ anyremote -f  anyremote-2.6/cfg-examples/Server-style/adminExample.cfg &
```
Finally we start the java application on the phone, connect to the computer, and **[COLOR="Red"]have fun![/COLOR]**
The author is very cooperative and likes to hear from you if you used his program successfully with a phone not yet on his list on this page: [http://anyremote.sourceforge.net/doc-html/intro.html](http://anyremote.sourceforge.net/doc-html/intro.html). But let's try to keep questions concerning installation and such here in the forum.

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by Darkade on 2008-06-07
Hey! great post. I just would like to add that there's available a graphic frontend for anyremote available here [http://anyremote.sourceforge.net/dload.html](http://anyremote.sourceforge.net/dload.html)

For this to work you should first have installed anyremote and then install ganyremote or kanyremote both available in .deb files from the website above.

:lolflag:

---

### Post by St Stephen on 2008-06-13
Hi,
Im trying to get gAnyremote up and running, and right now I'm working on the Java client package.  I've tried to install it with
```
$ ./configure --prefix=/usr --with-wtk=~/Documents/gAnyremote?WTK.5.2 --with-ProGuard=~/Documents/gAnyremote/proguard4.2

```
but the output is
```
checking for javac... /usr/bin/javac
checking for java... /usr/bin/java
checking for jar... /usr/bin/jar
configure: error: please specify --with-proguard <path to ProGuard>
See `config.log' for more details.

```
is there somewhere else that im supposed to point to? Is there a specific file that its looking for?

And on a side note, what is the best place to have the WTK and ProGuard installed?  I feel like my current place for them is less than stellar

Thanks

---

### Post by mike_mike on 2008-06-17
2 St Stephen:
Do You really want to compile java client from sources ? You can just
upload precompiled *jar to the phone.

---

### Post by TwoD on 2008-06-24
I'm having trouble installing anyremote v4.6 on my amd64 system.
Compilation etc works fine, but when I try "sudo checkinstall make install" I get this:
```

[SNIP]Config questions[/SNIP]
...
Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Går till katalogen "/tmp/anyremote-4.6/src"
make[2]: Går till katalogen "/tmp/anyremote-4.6/src"
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /usr/bin/install -c 'anyremote' '/usr/bin/anyremote'
make[2]: Inget behöver göras för "install-data-am".
make[2]: Lämnar katalogen "/tmp/anyremote-4.6/src"
make[1]: Lämnar katalogen "/tmp/anyremote-4.6/src"
make[1]: Går till katalogen "/tmp/anyremote-4.6"
make[2]: Går till katalogen "/tmp/anyremote-4.6"
make[2]: Inget behöver göras för "install-exec-am".
test -z /usr/share/anyremote || mkdir -p -- . /usr/share/anyremote
test -z /usr/share/doc/anyremote || mkdir -p -- . /usr/share/doc/anyremote
cp -r cfg-data /usr/share/anyremote
cp -r doc-html NEWS README COPYING VERSION AUTHORS /usr/share/doc/anyremote/
find /usr/share/anyremote /usr/share/doc/anyremote -type f -exec chmod 644 {} \;
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Utils/xmms_is_playing": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Utils/all-in-1.py": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Utils/gradient.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/amarok.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/xmms.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/juk.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/noatun.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/kdetv.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/kscd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/tvtime.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/quodlibet.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/totem.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/exaile.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/template.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/kaffeine.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/mpd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/kplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Bemused-emulation/rhythmbox.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/banshee-v2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/fileManager2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kmplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/gnomeradio.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/customizeClient5.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/keyboard.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/amarok.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kuickshow.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/adminExample.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/xfmedia.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/xmms.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/audacious.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kaboodle.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/sound.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/nokia-e61.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/juk.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/noatun.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/bmp.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/autolock.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/winManager.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/amarok-v3.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/fileManager3.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kaffeine-v2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kview.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/decibel.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/xdtv.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/xine.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kdetv.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/customizeClient.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/moc.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kscd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/customizeClient4.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/tvtime.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/quodlibet.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kmid.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/all-in-one.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/fileManager.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/gmusicbrowser.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/totem.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/ooimpress.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kaffeine_dvbt.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kopete.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/exaile.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/xmms2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kaffeine.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/vlc.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/aqualung.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/myth-tv.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/iconUpload.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/mpd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/smplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/listen.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/elisa.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/imageViewer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/mouse.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/nokia-e70.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/amarok-v2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/multimode.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kdialog.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/freevo.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/rhythmbox.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/all-in-one2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/banshee.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/mplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/rssReader.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/comix.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/customizeClient3.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/customizeClient2.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/kpdf.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Server-mode/gwenview.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/xineForDvd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kmplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/keyboard.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kdialog.siemens.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/amarok.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kuickshow.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/xfmedia.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/xmms.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/audacious.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/sound.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kdialog.se.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/juk.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kdialog.sagem.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/noatun.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/bmp.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/autolock.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kview.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kdialog.motorola.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/xdtv.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kdetv.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/moc.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kscd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/tvtime.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/quodlibet.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/all-in-one.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/gmusicbrowser.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/totem.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/exaile.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kaffeine.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/aqualung.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/mpd.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kplayer.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/listen.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/elisa.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/mouse.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/multimode.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/kdialog.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/freevo.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/rhythmbox.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/AT-mode/banshee.cfg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/VERSION": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/COPYING": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/NEWS": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/lirc.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/use.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/mode.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/getstarted.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-window.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/setup-at.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/contacts.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/web.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/pre.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/make.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-icons.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/k-shots.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyRemote16.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-xmms32.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyremote22.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/file-manager.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyremote16.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-xmms.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/spacer.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/ganyremote-tray.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/any3.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/nothing.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/kanyremote-devbr.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-default-fs.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/hash.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/launch.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/up.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/previous.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/vol_up.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/star.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/view_text.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/down.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/flag.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/pause.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/plus.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/next.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/mute.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/fileclose.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/vol_down.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/question.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/minus.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/black.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/fullscreen.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/bookmark.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/view_tree.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/save.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/no.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/anyRemote.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/file.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/click_icon.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/info.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/forward.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/fit.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/exit.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/default.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/refresh.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/minimize.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/exec.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/ok.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/empty.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/apply.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/play.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/edit.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/rewind.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/find.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/configure.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/anyRemoteClient.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/folder.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/icons/stop.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-bottomarc-fs.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyRemote.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyremote.svg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyremote32.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/default.css": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyRemote16.ico": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyremote24.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/file-manager2.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-list.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-list-menu.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/ganyremote1.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-text.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/master.css": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/any1.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/jc-menu.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/fileManager3.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/amarok.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/fileManager2.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/amarok-v2.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/banshee-v2.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/jc/banshee.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-digikam.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/header.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/kanyremote-devdet.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-test.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyRemote32.ico": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyRemote32.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/ganyremote-devdet.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/client-bottomline-fs.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/view-screen.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/kanyremote2.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar-gray.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar-yellow.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar.xcf": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-foot.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-navigation-off.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar-old.xcf": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar-red.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar-green.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bullet-blue.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-navigation-on.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/img/bg-sidebar-blue.png": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/anyRemote16.gif": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/any6.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/ganyremote3.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/ganyremote2.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/data/ganyremote-devbr.jpg": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/docs.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-text.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/conf-at-ex.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/cfg-howto.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/frontend.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-parameter.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/ir.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-menu.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/g-shots.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-list.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/bemused.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/dcop.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/thanks.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/conf-server.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/ev-reporting.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/index.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set-fm.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/devices.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/man.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/dload.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/emulate.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/set.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/conf-at.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/setup-server.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/use-jc.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/phones.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/conf-server-ex.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/faq.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/install.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/pre-setup.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/doc-html/ckpd-emulation.html": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/README": Filen eller katalogen finns inte
chmod: ändrar rättigheter på "/usr/share/doc/anyremote/AUTHORS": Filen eller katalogen finns inte
chmod -R a+x /usr/share/anyremote/cfg-data/Utils
chmod: ändrar rättigheter på "/usr/share/anyremote/cfg-data/Utils": Filen eller katalogen finns inte
chmod: kan inte läsa katalog "/usr/share/anyremote/cfg-data/Utils": Filen eller katalogen finns inte
make[2]: *** [install-data-local] Fel 1
make[2]: Lämnar katalogen "/tmp/anyremote-4.6"
make[1]: *** [install-am] Fel 2
make[1]: Lämnar katalogen "/tmp/anyremote-4.6"
make: *** [install-recursive] Fel 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
Basically, chmod tries to set permissions on all files, but fails because they don't exist.

Regular "sudo make install" works fine.

I found some indications that there might be a bug in checkinstall, although there was no reply to the mailing list thread I found so I'm not sure.

Anyone else having the same problem?

---

### Post by mike_mike on 2008-06-26
Hi All!

See [http://anyremote.sourceforge.net/contacts.html](http://anyremote.sourceforge.net/contacts.html) for the contact e-mail.

---

### Post by empty_tank on 2008-07-14
> **kwaanens said:**
> Here are 64 bit packages. I had to struggle a bit to get this going, but after getting 64 bit, everything was smooth sailing :)
Run ganyremote in terminal and you will likely figure out what depoendencies your are missing.

thank you. worked with hardy amd64

---

### Post by Umbro_domini on 2008-08-01
can anyone help me with my motorola a1200 ming?I cant figure out how to configure the server and my phone hangs everytime I bond with my machine..

help please/.:((

---

### Post by Gourgi on 2008-08-01
> **Umbro_domini said:**
> can anyone help me with my motorola a1200 ming?I cant figure out how to configure the server and my phone hangs everytime I bond with my machine..

help please/.:((

i can confirm this bug with my motorola moto ming a1200 too ..

---

### Post by mike_mike on 2008-08-04
2 Umbro_domini:
Please try to use anyRemote v3.6 (it contains java client inside). This version was tested with a1200 with success. 
After this please help me to understand the difference beetween v3.6 and \
current v4.6 :-)

---

### Post by mike_mike on 2008-08-04
By the way, which version of BlueZ do You have ?

---

### Post by Umbro_domini on 2008-08-05
> **mike_mike said:**
> By the way, which version of BlueZ do You have ?

yes sir I do have bluez...i can't figure just can't figure out how to configure the server mode in my computer cant understand how the cfg files work..could you please give me a step by step..please...:((

---

### Post by mike_mike on 2008-08-06
1. install anyremote, anyremote-data, anyremote-doc, ganyremote (or kanyremote)
2. update BlueZ to 3.35 or higher (which version do You have ?)
3. run ganyremote/kanyremote
4. upload java client to the phone 
(Setup->Device Browser->Search;
then Setup->Device Browser->Device details->Upload java)
5. choose application in GUI and click "Run"
6. run java client on the phone and start search.
7. if anyremote found connect to it and enjoy.

What exactly does not works ? 
Please, step-by-step - what i've done with which result ?

---

### Post by mike_mike on 2008-08-06
oops, typo ... last line should be:
Please, step-by-step - what you've done with which result ?

---

### Post by flytripper on 2008-08-06
> Making all in src
make[1]: Entering directory `/home/andy/Desktop/anyremote-4.7/src'
gcc -DUSE_BT=1 -DUSE_XTEST=1 -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g   -o anyremote atsend.o btio.o main.o cmds.o parse.o utils.o xemulate.o conf.o -lbluetooth -lXtst 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[1]: *** [anyremote] Error 1
make[1]: Leaving directory `/home/andy/Desktop/anyremote-4.7/src'
make: *** [all-recursive] Error 1


i am stuck on ```
make
```  any pointers? i googled lxtst and got nothing,zip,nada.

---

### Post by flytripper on 2008-08-06
Ok i finally got it installed. and all the extras gany/html etc.

i am trying to connect via my AP with an N95

now when i start the PC side up it says "connected to phone" and automatically starts up banshee (good :) )
it says "internet:server not found". also it doesnt have any functionality. the buttons are just blue circles and don't do anything...

i am using ip 192.168.0.1:5550 and :5000


when i manually got to my address via a browser it works!!
its just the java client that is confusing
can anyone help?

---

### Post by mike_mike on 2008-08-07
2 flytripper:
it needs to install Xtest library and headers first.
see [http://anyremote.sourceforge.net/pre.html](http://anyremote.sourceforge.net/pre.html) for details

---

### Post by mike_mike on 2008-08-07
2 flytripper:
Just to clarify: So, You have tried to use anyRemote through WiFi and web interface ?
(not directrly through bluetooth ?)

---

### Post by mike_mike on 2008-08-07
2 flytripper:
Just to clarify: So, You have tried to use anyRemote through WiFi and web interface ?
(not directrly through bluetooth ?)

---

### Post by flytripper on 2008-08-07
that is what i am doing.. wifi using the java client... the web interface works but the client doesnt.

---

### Post by mike_mike on 2008-08-07
This is is the problem. If You use java client, You need not use WEB interface.
Or if You want to use WEB interface, not use java client :-)
These are two different ways to get thing worked.

so,
1. run anyremote -s socket:5000 -f ..../fcfg/file on PC 
(or use GUI. it needs to set "override device parameter" as socker:5000)
Do not start WEB interface
In java client insert IP address of Your PC:5000
Then connect and use it.
2. Alternatively: start anyremote with WEB interface (port 5550).
Do not start java client.
Run WEB browser (You want to use WEB interface, right ? :-)) on You Nokia and open
in browser page http://<ip address of PC>:5550

---

### Post by flytripper on 2008-08-08
O my goodness.. thank you so much.. awesome piece of software :) bit tricky to get working though..  +8

---

### Post by mike_mike on 2008-08-08
So, does it finally works in Server mode with java client ?

---

### Post by flytripper on 2008-08-08
yes!! thanks  a mil.

---

### Post by Umbro_domini on 2008-08-09
Hi i've go anyremote and ubuntu Harday heron workd via bluetooth but I can't seem to control openoffice impress...does anyone have an idea about this?...tnx in advance:D

---

### Post by mcbean on 2008-08-09
Does anyone have any experience with the Samsung E840? I can't install the Java Client on it, each time it says "Java Error. Authorization Failed". I've tried to change security settings on my phone, but I can't see anything about letting untrusted app's run. 

E840 is not mentioned specifically on the anyRemote site, and it claims to be JSP-82 compliant. So I assume I'm doing something wrong! 

Any help greatly appreciated!

---

### Post by mike_mike on 2008-08-10
2 Umbro_domini:
So, do You manage anyRemote to work with Your a1200 ?
If not, please describe issue in details.

---

### Post by mike_mike on 2008-08-10
2 mcbean:
It is a pity, but seems this problem is typical for Samsungs.

---

### Post by mcbean on 2008-08-12
Mike_Mike, thanks for the quick response. Pity about the samsungs. I'll have to wait 'til I get a new phone!

---

### Post by majaron on 2008-10-29
Hello

I installed everything (anyremote, ganyrmote, bluez...) on my computer and it works i guess. It recognizes my Sony Ericsson w950 and there is a list of all cfg files.

On my phone i installed java client, and it works too i guess. It found my computer when i select search for device.

Than i try to connect computer and the phone:
1. I open ganyremote and click start. It says "disconnected from phone" but that's fine i think.
2. I open java client on my phone and start searching for devices
3. I click connect and a black keyboard pops up.

But here know is the problem. On the keyboard there are no keys, just locks so i can't do anything. 
And another thing, on ganyremote on my computer stil say "disconnected from phone".

So it didn't even connect.
What can i do. Please help!

---

### Post by mike_mike on 2008-11-05
If You are using 8.10 please see the following thread [http://ubuntuforums.org/showthread.php?t=964139&highlight=anyremote&page=2](http://ubuntuforums.org/showthread.php?t=964139&highlight=anyremote&page=2)

---

### Post by danf_1979 on 2008-11-20
This worked on a SE W890i. Thanks!

I did this:

```

$ sudo aptitude install anyremote

```

Then download anyremote-j2me-client from the download section from anyremote's page on sourceforge.

```

$ dpkg -i anyremote-j2me-client

```

I copied /usr/share/anyremote-J2ME-client/anyRemote.jar to my phone using apache webserver to download it, since I have problems sending files through bluetooth. Once installed, you're ready.

All configuration files are stored in /etc/anyremote. For example, to control openoffice impress, go to a console and type:

```

$ anyremote -f /etc/anyremote/Server-mode/ooimpress.cfg

```

And then execute anyremote client on your phone.

Thanks mike!

---

### Post by loopeando on 2008-12-28
Any idea on how to install the anyRemote JAVA client on a Nokia 6820 (Symbian S40 v1.0 with 64 Kb limit for JAVA apps)?

---

### Post by mike_mike on 2009-01-02
Since *jar is just a zip file it is possible to remove some icons from it and decrease size.

---

### Post by wantime on 2009-02-06
hmm .. don't see how to completely delete this message, got it working thanks.

---

### Post by Ahmedmb on 2009-05-22
Thank You

i try to use anyremote to control XBMC on ubuntu 9.04
My mobile is nokia 5320 
I get this error on mobile
openconnection Exception javax.bluetooth.blutoothconnectionException SymbionOS error = -6004 : General: System Error.

Any Help

---

### Post by Lylex11 on 2009-07-05
I am using ubuntu 9.04 amd64 on hp g60 trying to connect to a nokia 3110c. I can transfer files to/from phone and palm t|x using obex, however on startup message pop up says "bluetooth not connected". When I click on "start" in ganyremote status reports "disconnected from phone". When I open anyremote on Nokia and try to connect I get message:
openConnection Exception javax.bluetooth.BluetoothConnectionException null and also get a black background with locks.

Any help to fix this issue is appreciated.

---

### Post by lwhitmore on 2009-07-21
The version of anyRemote in the standard Jaunty repositories didn't work for me.

I managed to get the program working with Ubuntu 9.04 by installing the latest version from this repository:

[https://launchpad.net/~anyremote/+archive](https://launchpad.net/~anyremote/+archive)

----

I also installed blueman (to manage bluetooth devices) from this repo:
[https://edge.launchpad.net/~blueman/+archive/ppa](https://edge.launchpad.net/~blueman/+archive/ppa).

---

### Post by dogscoff on 2009-08-30
I've just come back to anyremote after a short absence (and OS upgrade) and I've been using the server-mode/rhythmbox.cfg to control my music via bluetooth. It's not my favourite player (I've been bugging the Jajuk ppl to add support but they don't seem interested - ah well), but it seems to have the best anyremote support. 

Anyway, I'm positive rhythmbox used to send album titles over to the phone, but now it doesn't. Am I dreaming or did this function exist in the past? Am I running an old version of the cfg file? Where can get a fully functional one?

---

### Post by theone964 on 2010-02-09
Hey i guess i'm starting the tread again since the last time it was used was over 6 months ago lol.

Ok so i just installed Ubunto for the first time ever on my system (9.10)

I was trying to use the gAnyRemote application on my HTC Tilt via Bluetooth and am running into some problems.

I've connected my phone to the pc, and uploaded the .jar file for the nojsr82. Whenever i run the app on the phone to connect it says "socket://enter.ip.here.port", no matter what i do it tries to connect through wifi or a data package and i got my carrier to disable data ( and at a location without wifi). is there anyway to make it work without wifi or data packages?

Thank you

---

### Post by userkiller on 2010-02-10
This is pretty cool.

---

### Post by airtonix on 2010-04-07
anyremote wont work with my cheap'o mobile phone (samsung c3050) since both variants of the client don't launch.

After much searching and experimenting, i managed to get Linux Bluetooth Remote Control (LBRC) to work.

First few times the client would find the server, and connect ... however the server would not show any recognition of this and reported that there were no connected clients.


But I eventually got it working, not exactly sure how but currently my setup looks like this : 

1. bluetooth properties > 
  always visible : true
  phone found and trusted : true

2. launch LBRCdbus : 
```
$ sudo LBRCdbus
```

3. launch LBRC-config >
 ```

[Configuration]
  save profile for next start : ticked
  show bluetooth controls : ticked
  require pairing : unticked
  one time pairing : unticked
 [Profile] 
  XInput

```

4. run LBRC-applet
```
$ LBRC-applet & 
```5. right click the LBRC notification icon and select : Profiles > XInput

6. send client to your phone : 
 a. ```
$ bluetooth-sendto 
```
b. file browser shows up >>> press ctrl-l
 c. replace the text in the locaton field with : 
   /usr/share/lbrc/j2me/
 d. hightlight both files there, one jad file and one jar file
 e. click "Open"
 f. Select your phone
 g. ???
 h. profit

7. run the client on your phone and search for your comptuer
   ( I assume you can already pair with your computer from your phone and vice versa).

8. If connection is successful, you should see two things :
 a. on your computer you will see a notification bubble saying that such and such mac address has connected to so and so mac address.
   (these are mac addresses of your phone and computers bluetooth devices)
 b. on the phones screen, two lines of text : 
```

Keypress : blah blah blah:
keycode : somethingsomethingsomething

```

9. using the directional pad on your phone ought to move your mouse cursor around and depending on the profile settings the numpad on your phone will send keyboard codes to the computer.

---

### Post by djcrash1981 on 2010-04-07
> **mike_mike said:**
> Fab, 
1. have You tested AT mode ?
2. have You tried JamSE ?

Hi, I've just send you an e-mail with some info.

Would you take care to see it?

Thanks in Advance.

The subject say: Anyremote karmic (PPA) with nokia n97

---

### Post by KEE on 2010-04-10
hello i get missing packages =S```
l@l-laptop:~$ sudo aptitude install gcc build-essential bluetooth bluez-cups bluez-hcidump bluez-passkey-gnome bluez-pin bluez-utils gnome-bluetooth libbluetooth2 libbluetooth2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for bluez-passkey-gnome
Couldn't find any package whose name or description matched "bluez-pin"
Couldn't find any package whose name or description matched "libbluetooth2"
Couldn't find any package whose name or description matched "libbluetooth2-dev"
No candidate version found for bluez-passkey-gnome
Couldn't find any package whose name or description matched "bluez-pin"
Couldn't find any package whose name or description matched "libbluetooth2"
Couldn't find any package whose name or description matched "libbluetooth2-dev"
The following NEW packages will be installed:
  bluez-hcidump 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 86.9kB of archives. After unpacking 291kB will be used.
Writing extended state information... Done
Get:1 http://ubuntu.mirror.iweb.ca karmic/universe bluez-hcidump 1.42-1build1 [86.9kB]
Fetched 86.9kB in 1s (60.2kB/s)         
Selecting previously deselected package bluez-hcidump.
(Reading database ... 232075 files and directories currently installed.)
Unpacking bluez-hcidump (from .../bluez-hcidump_1.42-1build1_i386.deb) ...
Processing triggers for man-db ...
Setting up bluez-hcidump (1.42-1build1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

l@l-laptop:~$ 

```

---

### Post by mealstrom on 2010-06-01
maybe this will be useful , just like some replacement to ganyremote. server edition :).
scans media for yours BT devices;
run application if found some available devices.
set password for anyremote. This is useful to protect server :D


put this file to run every 1 minute in cron.

cat bluetooth.pl 
[PHP]#!/usr/bin/perl 
########################################
# By Aleksander Mischenko aka Mealstrom #
# mail: mischenko.mm[doggy]gmail[dot]com#
# Licence: GPL v3 :D            #
# Version: 0.9 beta            #
#########################################
#
# 
#
# hcitool scan -- timeout 30 sec. Run it in console to get BT MAC
# 
# list of processes to be runned or shutdown when BT device is in range
# %processes=(process1,parameters for proc1 , proc2...)
# allowed macs:
# @mac = ("mac1","mac2");
# TODO:
# remake match pattern for BT macs.

#Globals

#delete -password to access without it
%processes=("anyremote","-fe 5050 -f /usr/share/anyremote/cfg-data/Server-mode/all-in-one2.cfg -password -s bluetooth:19 > /dev/null &");

#change this for yours real BT macs
@mac =("00:XX:XX:XX:XX:XX","00:AA:A1:A2:A3:A4");
#change yours home directory
$password_file="/home/xxxxxxxxx/.anyRemote/password";
#change password for access
$password="XXX";
#check if there any allowed mac-address
sub bt_mac_check
 {
  my @btscan = `hcitool scan`; 
    #remake match pattern for multiline input
    foreach $i(@btscan){
            if ($i =~ m/\t(.*)\t/){
#        if ($i =~ m/([0-9A-F]{2}:){5}[0-9A-F]{2}/i){
        #mach mac address format
            foreach (@_){if ($_ eq $1){return 1;}}        
        }    
    }
 return 0;
 } 

#check if password is ne
sub passcheck
{
open (PASSWD, "< $password_file") || die("Could not open file!");
    while (<PASSWD>) {
            if ($_ ne $password){
        return 1;
            }
    }
    return 0;
close(PASSWD);
}

#set password for anyremote
sub passset
{
    open (PASSWD, "> $password_file") || die("Could not open file!");
    print PASSWD $password;
    close (PASSWD);
}

if (passcheck){passset;}
$mac_check=bt_mac_check @mac;
#$mac_check=0;
print "maccheck = $mac_check\n";

while (($key, $value) = each (%processes)) {
    if ($mac_check){
         if (!`pgrep $key`) {                               
                 #print "Starting process $key ... \n";
          `$key $value`;
                 }

    }
    else {
        if (`pgrep $key`) {
        #print "Process $key is running. So lets kill it ...\n";
        `pkill $key`;
        }
    }
}[/PHP]

---

### Post by dr_smit on 2011-09-25
Great work by Mike!!

I am trying to use on Ubuntu 11.04 with Samsung Galaxy S2 Android phone, there are connected, filemanager on phone could list files, but nothing further can be done presently..
Let me try to update through ppa instead of old version from ububuntu software centre..
any recommendation / comments are welcome

---

### Post by pkg9991 on 2011-09-25
nice tutorial.. thank u

---

