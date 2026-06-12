---
title: "How to Sync your Blackberry in Linux"
date: 2006-06-06
forum: Tutorials
---

### Post by NinjitsuStylee on 2006-06-06
[B]UPDATES (Jan 2, 2007):  

I am now editing the original post to reflect changes in software and also add tips on how to sync with Google Calendar.  (ScheduleWorld now has built-in Google Calendar support, so this makes it easy to synchronize your address book and calendar between your Blackberry, Evolution, and Google Calendar).

Also, I haven't been able to check it out yet, but check out [BCharge]("http://sourceforge.net/forum/forum.php?forum_id=648040") to charge your Blackberry with Linux![/B]


Ok, I'll admit, I used the title of the post to grab your attention.  But don't worry! I'm not lying about anything here!

Just a few quick disclaimers before we get started:

0.  I'm relatively new to linux, so bear with me here if I sound like a newbie.  However, I had the balls to jump right into it and try lots of different things, so I hope you can appreciate that.  Trust me, I spent many many hours of trial and error to figure this solution out.  I think I'm going a little crazy, actually.  The fact that I started this list with the number 0 should tell you something...

1.  I didn't test this setup with anything else besides the stuff I had access to.  In other words, I only know that this setup works on the Blackberry 7100t phone (although I imagine it would work for any 4.0.2 OS-enabled BB device) and it works with Evolution 2.4.1 (default with Ubuntu 5.10 Breezy Badger).

2.  Don't expect a 100% sync.  Everyone and their mother knows that Blackberry support on Linux is barely existant.  Sure, there are a small [handful of projects in development]("http://www.ubuntuforums.org/showthread.php?t=179950") (infinite development, in most cases...sigh, vaporware).  But for the most part there's not much we can do.

_What I managed to figure out:_

**UPDATE:** I am currently syncing both my address book and my calendar with [ScheduleWorld]("http://www.scheduleworld.com").  This means that I am syncing them with my Evolution client, but thanks to ScheduleWorld's new built-in [Google Calendar]("http://calendar.google.com") sync, I am also syncing with Google Calendar! How sweet is that?

[SIZE=4]**How to Sync your Blackberry in Linux**[/SIZE]

Things you'll need:[LIST]
[*]Your Blackberry device running at least the **4.1** OS
[*]A Windows install (on your box or your grandmother's, doesn't matter) with Blackberry Desktop Software installed and the USB cable. For all you linux uber-zealots, sorry guys, I know I'm making you use Windows here...I dunno, hold your breath or something :rolleyes:
[*]Evolution 2.4.1 Note:  I'm not sure whether or not any older/newer versions will work, I would imagine they would...it mostly depends on the next piece of software, which is:
[*][SyncEvolution]("http://sourceforge.net/projects/sync4jevolution") **0.5 **(formerly known as Sync4jEvolution):  Probably the only opensource solution for integrating Evolution with SyncML.  I'm sorry, but I gotta say...that's kinda sad.  I guess it works though.  See the tutorial below.
[*]An account with [ScheduleWorld]("http://www.scheduleworld.com"):  These guys are pretty cool.  Their service is free and it actually works. They even have a nice web-based interface for you to mess with.  Anyways, if you want to set up your own Sync4j server, be my guest...I tried it but decided to go with the ScheduleWorld route instead (was having silly networking issues that I didn't feel like resolving).
[*][Funambol Blackberry Client]("http://www.funambol.com/opensource/download_form.html?file_id=funambol-blackberry-plugin-3.0.7.zip") - **UPDATE:**  The latest Funambol Blackberry client supports a lot more than the previous clients did!  I highly suggest you upgrade your Blackberry device to at least OS 4.1 (required, visit website of your phone provider) and use this client.
[*]Patience.  Seriously.  Not only does this whole process take a while, but the syncing itself is pretty slow.[/LIST]**_What to do:_**
**Step 1 - Backup:** 
Boot into Windows (or shove grandma aside) and backup all your Blackberry data.  I'm not going to go over how to do that here because I'm assuming most of you Blackberry users know how to do this (and if not, google it or check out the bb website, it's not hard).

Once you do that, get back into Ubuntu (or whatever distro you use...I guess this solution should work in all Linux distros?  Anyone wanna check for me?) and go into your Home folder. Unhide all them fancy .folders (ctrl+H in ubuntu) and look for the .evolution folder.  Make a copy of it elsewhere (or go into it and backup whatever contents you want...I'm paranoid so I just back everything up).


**Step 2 - Set up an account with [ScheduleWorld]("http://www.scheduleworld.com"):**
What you're going to need here is to change your password (by default they email you a numerical password when you sign up, I guess you could keep it the same if you wanted to) and also take note of the "account" number, which is listed on the preference page as "12345@Scheduleworld.com" (where 12345 is going to be your number).  Write this down somewhere because you are going to need it.

**Step 3 - Setup SyncEvolution:** 
UPDATE:  A lot of people were having trouble installing SyncEvolution.  The good news is, SyncEvolution now has pre-compiled binaries on their website, and better instructions on how to install it. 

Also, ScheduleWorld configuration files are included by default (you'll have to copy them over from the "etc" directory in the source package...follow these instructions)[INDENT][LIST=1]
[*]Open the extracted folder for syncevolution and find the "etc" directory.  Inside you'll find another directory called scheduleworld_1.  Copy this to your /home/.sync4j/evolution directory (so that it becomes /home/.sync4j/evolution/scheduleworld_1)
[*]Open this file. You should see a folder called spds.  Open that too.
[*]Now we have two folders, sources and syncml.  Open the syncml folder first.  Notice the config.txt file?  Open it.
[*]Edit this file as follows:  Replace line 5 with

```
syncURL = **http://sync.scheduleworld.com/funambol/ds **

username = (your scheduleworld #)
password = (your password)

```If you want, you can also change the "maxlogdirs" variable to some number, the details on that is explained in the file itself.
[*]Now save this file, and back up to the spds directory.  This time open the sources folder and open the config files in the address and calendar folders.  You can update the one in the todo folder if you want, but keep in mind that your Blackberry device won't support the todo list as of now.  For all of the files, the only change that you really need to make here is:

```
# picks one of Evolution's data sources:
# enter either the name or the full URL
evolutionsource = Personal
```Note:  "Personal" is the default name for all the databases in Evolution...at least, it was in mine.  If yours is different, replace it with whatever you call your contacts list/calendar.  Save the files once you're done editing them.
[*]Now it's time to attempt the first syncs.  Open up a terminal and type in the following command to sync your addressbook:

```
syncevolution scheduleworld_1 addressbook
```And of course, replace "addressbook" with "calendar" to sync the calendar.  Be patient, as this could take some time to sync depending on how much information you have, and sometimes it looks like it's just frozen.  Give it time.
[*]Optional:  Make a cronjob to have this done automatically at a certain time interval.  Google "crontab" and you'll figure that out.[/LIST][/INDENT]**Step 4 - Setup your Blackberry:**
**Although there are a few bugs with the new Funambol client (noted in the readmes in the client zip files), the latest beta version works way better than the last one.  However, initial sync will be very slow, so I recommend you do this overnight.  **

Plug your BB into your windows boot and install the Sync4j client using the Application loader (again, I won't explain this in detail because if you have a BB you probably know how to do this, and if not, hit up the BB website).

Once the client is installed, open it up and click your wheel in, and go to Configuration.

Fill out the information as follows:
[B]
(See ScheduleWorld Funambol Client information in the Preferences Panel of Scheduleworld for info)[/B]


Save this configuration and exit the client.  Then go back into the client  and click your wheel in and synchronize!  And maybe go grab a coffee while it happens...:whistle:


-NinjitsuStylee
[I]
UPDATE: [/I] One additional thing...if you ever get an error during sync that says something like "max connections open", just give your device a hard reboot (aka take the battery out and stick it back in).  I'm not 100% sure why this error comes up but it has something to do with the way your network provider handles data.

---

### Post by matthinckley on 2006-06-17
this is awesome.. i'm going to try this tonight.. 

Thanks for the post!

Matt

---

### Post by NinjitsuStylee on 2006-06-17
Sounds good, drop a reply if you have any problems or have any questions, I've subscribed to the thread.

---

### Post by Whoopie on 2006-06-18
Hi,

I don't own a Blackberry, but I know of OpenSync which also implements SyncML.

See [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) for Ubuntu (Dapper Drake) packages.

Best regards,
Whoopie

---

### Post by NinjitsuStylee on 2006-06-21
I actually looked into OpenSync.  I'm not sure how well it'll work with Blackberry, but it's a relatively new(ish) development.  I might look into it in the future if RIM decides to be more evil :(

---

### Post by rosh1182 on 2006-07-26
I got an error when I tried to install, during the .configure stage, here is the output:

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
configure: configuring the client library
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
configure: error: configuring client library failed
roshan@roshan-laptop:~/syncevolution-0.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
configure: configuring the client library
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
configure: error: configuring client library failed


Thanks for the help.

---

### Post by NinjitsuStylee on 2006-07-26
Can you post the detailed error from the config.log?

It looks like your gcc (the C++ compiler) isn't properly installed...and if it is, I bet it's a permissions error.

Make sure you've got proper execute permissions on your media.....

(if you're clueless, ask and I shall explain more)

---

### Post by rosh1182 on 2006-07-27
First, thanks for responding and being so helpful.  I am running everything as root, so I don't think it is a permissions thing.

The contents of config.log:  

```


This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = roshan-laptop
uname -m = i686
uname -r = 2.6.15-26-686
uname -s = Linux
uname -v = #1 SMP PREEMPT Sat Jul 22 12:10:30 WST 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1558: checking for a BSD-compatible install
configure:1613: result: /usr/bin/install -c
configure:1624: checking whether build environment is sane
configure:1667: result: yes
configure:1732: checking for gawk
configure:1761: result: no
configure:1732: checking for mawk
configure:1748: found /usr/bin/mawk
configure:1758: result: mawk
configure:1768: checking whether make sets $(MAKE)
configure:1792: result: no
configure:2007: configuring the client library 
configure:2011: error: configuring client library failed 

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_EPACKAGE_CFLAGS_set=
ac_cv_env_EPACKAGE_CFLAGS_value=
ac_cv_env_EPACKAGE_LIBS_set=
ac_cv_env_EPACKAGE_LIBS_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_make_make_set=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/roshan/syncevolution-0.3/missing --run aclocal-1.9'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/roshan/syncevolution-0.3/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/roshan/syncevolution-0.3/missing --run autoconf'
AUTOHEADER='${SHELL} /home/roshan/syncevolution-0.3/missing --run autoheader'
AUTOMAKE='${SHELL} /home/roshan/syncevolution-0.3/missing --run automake-1.9'
AWK='mawk'
CC=''
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EPACKAGE_CFLAGS=''
EPACKAGE_LIBS=''
EXEEXT=''
F77=''
FFLAGS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LN_S=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/roshan/syncevolution-0.3/missing --run makeinfo'
OBJEXT=''
PACKAGE='syncevolution'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PKG_CONFIG=''
RANLIB=''
SET_MAKE='MAKE=make'
SHELL='/bin/sh'
STRIP=''
SYNC4J=''
SYNC4JSRC=''
SYNC4J_CFLAGS='-I/home/roshan/syncevolution-0.3/src/client-api.build/include/common -I/home/roshan/syncevolution-0.3/src/client-api.build/include'
SYNC4J_LIBS='-L/home/roshan/syncevolution-0.3/src/client-api.build/src -lsync4j'
SYNC4J_SUBDIR='/home/roshan/syncevolution-0.3/src/client-api.build'
VERSION='0.3'
ac_ct_AR=''
ac_ct_CC=''
ac_ct_CXX=''
ac_ct_F77=''
ac_ct_RANLIB=''
ac_ct_STRIP=''
ac_pt_PKG_CONFIG=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build=''
build_alias=''
build_cpu=''
build_os=''
build_vendor=''
datadir='${prefix}/share'
exec_prefix='NONE'
host=''
host_alias=''
host_cpu=''
host_os=''
host_vendor=''
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/roshan/syncevolution-0.3/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
mkdir_p='mkdir -p --'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "syncevolution"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "0.3"

configure: exit 1

```

---

### Post by NinjitsuStylee on 2006-07-27
Hey, no problem, help is what this place is all about :)

Anyways, do you have the g++ package installed?  I've seen errors similar to yours and they can happen if gcc is installed without c++ support.  

Open up synaptic and search for the packaged called "g++" (without quotes of course).

Make sure it's installed (along with its dependancies which synaptic will take care of automatically) and let me know if you're still having trouble :)

---

### Post by rosh1182 on 2006-07-30
Progress made.  Now .configure complains that I have an incompatible evolution-data-server.  My currently installed evolution-data-server package is at version 1.6.1-0ubuntu5.

Thanks again.

---

### Post by NinjitsuStylee on 2006-07-30
I would recommend you rollback to Syncevolution 0.2 instead of the latest 0.3 ........I have the same evolution-data-server package as you do and my system works fine.....I haven't touched it since I first put it together (aside from updating the cron jobs that run the sync commands for me).

The limiting factor to this whole setup is actually the Blackberry client, not the syncevolution or scheduleworld setups...I do believe that Funambol's latest versions of the Blackberry client only allows you to sync your addressbook, and not your calendar.  The reason for this is that the claim the calendar has a bug.

Again, I have not yet encountered this "bug" so I couldn't tell you anything else.

---

### Post by s_p_a_r_k_y on 2006-08-17
You need to install the evolution-data-server-dev and libcurl3-dev

```

sudo apt-get install libcurl3-dev libcurl3-openssl-dev evolution-data-server-dev g++
```

then run ./configure again and make && make install

---

### Post by NinjitsuStylee on 2006-08-17
Good call.  Thanks for helpin him out!

---

### Post by speacock on 2006-08-21
Great directions. I was able to get to the point of tyring to sync with scheduleworld, and ran in to the following: 
```

15:31:20 [DEBUG] - Requesting resource /sync4j/sync  at www.scheduleworld.com:80
15:31:20 [DEBUG] - libcurl info: About to connect() to www.scheduleworld.com port 80
15:31:20 [DEBUG] - libcurl info:   Trying 64.34.210.174... 
15:31:20 [DEBUG] - libcurl info: connected
15:31:20 [DEBUG] - libcurl info: Connected to www.scheduleworld.com (64.34.210.174) port 80
15:31:20 [DEBUG] - libcurl header out:
POST /sync4j/sync  HTTP/1.1

Host: www.scheduleworld.com

Accept: */*

Content-Type: application/vnd.syncml+xml

Content-Length: 230673

Expect: 100-continue



15:31:27 [DEBUG] - libcurl header in: HTTP/1.1 505 HTTP Version Not Supported

15:31:27 [DEBUG] - libcurl header in: Server: Apache-Coyote/1.1

15:31:27 [DEBUG] - libcurl header in: Date: Sun, 20 Aug 2006 19:31:26 GMT

15:31:27 [DEBUG] - libcurl header in: Connection: close

15:31:27 [DEBUG] - libcurl info: Closing connection #0
15:31:27 [DEBUG] - 
15:31:27 [DEBUG] - Response read
15:31:27 [ERROR] - Server Failure: server returned error code -1
15:31:27 [ERROR] - Error in syncing: Server Failure: server returned error code -1
```


Any idea where to go for help with this. I posted to the sync4j-users mailing list but haven't received a response. 

Thanks, 

Steve

---

### Post by saracen on 2006-08-23
How do I get the thing to charge?! :confused:

---

### Post by NinjitsuStylee on 2006-08-24
Haven't quite figured that out yet......I've been using the wall plug charger ever since I moved to Ubuntu. :(

---

### Post by joflow on 2006-09-18
Could I get this working with a treo 650?  It listed as a compatible device on the funambol website.

---

### Post by clcoyle on 2006-09-22
Okay, my outputs are looking very similar.  I'm about to burn down my house, with this box in it.

All I really wanted was to use Syncberry to sync calendar/contact/task info from my company's OWA server, but the dang thing won't do it, and the "IT" guy isn't very helpful.

Why do IT guys assume that if you're trying to do something they don't know about that you surely are trying to subvert and overthrow their universe?

And the guy at Nexthaus (SyncJe), although helpful and friendly, wasn't familiar with OWA.  Geez.  

Is anyone familiar with OWA that isn't afraid I'm looking for a back door into Hackville?

](*,)

---

### Post by clcoyle on 2006-09-25
Hey, Stylee - 

You mentioned on the first page about permissions...  I know enough about permissions on Linux to be stupid.  How do I go check to see if that is what my problem is?  

I appear to have C++ installed as part of the G++ and GCC bases, but the ./config still tells me G++ no and GCC no...   What the..?

AArrrgh...

Thanx,

Lee

---

### Post by NinjitsuStylee on 2006-09-25
Hi clcoyle.

Unfortunately I'm not exactly sure what your setup is, but what I would do is make sure you're running everything as root while trying to install (sudo).......

Also, you say you have C++ instapped as part of the G++ bases.....there is a possibility that you don't have the most current version installed.  Try checking dependencies for the syncevolution package (google it i suppose, or check the website in the link i provided) and make sure you have all of those, and the dependencies for that (apt-get will be your best friend in doing that part).

---

### Post by dsyn on 2006-10-04
is there an easier way to install syncevolution? is there a package header I can put in the synaptic manager to make it install for me?

---

### Post by Tanath on 2006-10-04
Anyone know a good alternative to a Blackberry that works well with Linux (Ubuntu in particular)?

---

### Post by DocMSK on 2006-10-19
**SOLVED - SEE AT END FOR SOLUTION**

Hi, a total noob. Been following this thread. I have been trying to install syncevolution, but am running into problems.

I can't seem to install evolution-data-server-dev (managed to install libcurl3-dev ok through synaptic).

When I select evolution-data-server-dev in synaptic I get the following:

evolution-data-server-dev:
 Depends: libedata-book1.2-dev but it is not going to be installed
 Depends: libedata-cal1.2-dev but it is not going to be installed
 Depends: libegroupwise1.2-dev but it is not going to be installed
 Depends: libedataserverui1.2-dev but it is not going to be installed
 Depends: libcamel1.2-dev but it is not going to be installed
 Depends: libbonobo2-dev but it is not going to be installed
 Depends: libebook1.2-dev but it is not going to be installed
 Depends: libecal1.2-dev but it is not going to be installed
 Depends: libedataserver1.2-dev but it is not going to be installed
 Depends: libgconf2-dev but it is not going to be installed
 Depends: libglib2.0-dev but it is not going to be installed
 Depends: libgnome2-dev but it is not going to be installed
 Depends: libgnomevfs2-dev but it is not going to be installed
 Depends: liborbit2-dev but it is not going to be installed
 Depends: libsoup2.2-dev but it is not going to be installed

How can I correct this?

Thanks
Doc

**SOLVED**

Just shows what a total novice I am to Linux. I used the command 'aptitude' to get the required package, it took care of everything.

Regards
Doc

---

### Post by jrogers360 on 2006-10-20
Can you even sync with the error message on the blackberry about insufficient current (power) on the usb?

---

### Post by rosh1182 on 2006-10-20
Tanath, 

What are your requirements for a handheld?  Linux supports the Palm handhelds quite well; I use a Treo 650.

---

### Post by beginner_6.10 on 2006-11-09
hi, great howto! but what if you have bb firmware 4.0.0.188? e.g. my bb 7730 is not upgradeable to 4.1. is there some way i can sync though?

---

### Post by lucmult on 2006-11-27
To clcoyle.

Install build-essential, this package has the essentials tools to build (compile) c, c++ and others programs.

[]s

---

### Post by DoctorMO on 2006-12-08
Oh great all I have is a Linux machine... I'm going to have to work out how to sync it without the jar file, pah.

---

### Post by NinjitsuStylee on 2006-12-27
> **jrogers360 said:**
> Can you even sync with the error message on the blackberry about insufficient current (power) on the usb?

Sorry if this confused you but this thread is specifically for OTA (over-the-air) sync.

I think you're thinking of plug-in sync, which is unrelated.  There isn't a way to do plugin sync with the BB and Evo as far as I know, but the OTA sync does work.

In other news, sorry that I haven't been following my own thread, but it seems like most people have been able to help each other.  This is good news!

There are new versions of both syncevolution and the Funambol client out, and I will be experimenting with them soon.  However, I am in the process of moving to a fully web-based e-mail/contacts/calendar solution so I will probably be abandoning Evolution within the next few months.  

I'm hoping to be able to sync all my BB info with Google's services (particularly Google Calendar...Google already has a GMail client for the BB).

---

### Post by clee991 on 2007-01-16
GCalSync works on my BB Pearl with a few quirks (repeats) for Google Calendar 

[http://www.gcalsync.com/](http://www.gcalsync.com/)

The Gmail client is OK but I setup mymail to grab Gmail as a POP and find I prefer that and can use filters on mymail to fine tune what gets though

Thanks for the tip on US charging

---

### Post by rn655321 on 2007-01-28
I'm also a noob, so forgive such a simple question:

When I look for the .sync4j folder in my HOME directory I cannot find it. Is there a package that I am missing?

Thanks in advance!

---

### Post by DaveA2005 on 2007-01-29
I tried this with Verizon Wireless 7130e.  When I try to sync from blackberry I get 'Max Connections Open' error from Funambol.  I tried hard reset several times but it always happens.

---

### Post by DaveA2005 on 2007-01-29
> **rn655321 said:**
> I'm also a noob, so forgive such a simple question:

When I look for the .sync4j folder in my HOME directory I cannot find it. Is there a package that I am missing?

Thanks in advance!

Just make the folder and copy the appropriate files/folders into it.

---

### Post by NinjitsuStylee on 2007-01-29
> **rn655321 said:**
> I'm also a noob, so forgive such a simple question:

When I look for the .sync4j folder in my HOME directory I cannot find it. Is there a package that I am missing?

Thanks in advance!


dot-folders are hidden folders...I'm not sure if you knew this or not, so try pressing ctrl+h (when browsing via nautilus of course) and it will show it (or ls -a for shell style).

---

### Post by boo-koo on 2007-02-22
> **clee991 said:**
> GCalSync works on my BB Pearl with a few quirks (repeats) for Google Calendar 

[http://www.gcalsync.com/](http://www.gcalsync.com/)

The Gmail client is OK but I setup mymail to grab Gmail as a POP and find I prefer that and can use filters on mymail to fine tune what gets though

Thanks for the tip on US charging

I have Blackberry Pearl from T-Mobile and I got it working perfectly and here are the step-by-step instructions on how to accomplish this task.  

Credit Peter Gypps for these good instructions:

Using the browser of your blackberry phone Go to:  [http://wap.gcalsync.com](http://wap.gcalsync.com) and install the GCalSync program
 
 (It will download and install the .jad installer)

 
After install is complete, In your phone navigate to: 

Options>Advanced Options>TCP>APN set to wap.voicestream.com  

-reboot (by holding red hang-up button for 5 seconds then wait 30 seconds and turn power back on)- 

Go into gcalsync 
Options > Username/password > enter your user name (without the @gmail.com) and password 
Options > Timezone > Set your timezone offset.  I just played with my 
numbers until they matched between my Google calendar and phone.  I am in Eastern Standard Time so I changed upload to +05:00 and ticked the box on "use Gmail cal time" 

-reboot- 

all done, do a normal sync and there you have it.  Now I still run in to the bug where if I create a calendar entry on my mobile that I will have 2 duplicate entries on Google Calendar online via my Desktop PC at home but it's really not that big of a deal.  

I hate Microsoft Outlook so I am glad that I found this other method and am very happy now.  And I dont have to waste my time with evolution or other pop suites.

---

### Post by wyeknot108 on 2007-02-28
As a recent BB customer and a full-time Ubuntu user, I read this thread with curiosity as I was not wanting to be tied to occasionally booting Windows for synching.

My primary "global" email is just a free account though Yahoo.  I recently consolidated all my contact info into their contacts interface with the intention of exporting/importing into the BB.  I did do that last week to a degree, importing all names and number - couldn't get email addresses across for whatever reason.

This morning I downloaded Yahoo's GO application for mobile phones to the BB.  And now I am able to do over-the-air synching with my Yahoo contacts.  Voila!  No need for Windows, no need for the BB synch app.  200+ contacts synched in about 1 minute.

Thought others might be interested.

---

### Post by nrwilk on 2007-03-07
I would like to thank the people who posted about gcalsync SO much!!

This is awesome.  It took me a while to set it up, but I got it, and it's great!  Works like a charm.

Thanks again!

---

### Post by adarkmethod on 2007-03-20
ok, im trying to charge my moms Blackberry Pearl, but when i run bcharge, it says there are no devices to adjust, does this not work for Pearls, or am i retarded?

---

### Post by adarkmethod on 2007-03-20
ok, i found this [http://barry.cvs.sourceforge.net/barry/barry/tools/bcharge.cc?view=log](http://barry.cvs.sourceforge.net/barry/barry/tools/bcharge.cc?view=log)

but i cant get it to install/edit

---

### Post by dotnino on 2007-04-18
How about just getting your BB to show up as a removeable device?  I'm really just looking to transfer data to/from its memory card...

Any help would be greatly appreciated. 

Thanks.

---

### Post by LiterallyDude on 2007-05-12
Hi all,

I am a noob. I'v just installed barry and all of the other rpms that come along with it from sourceforge. I think that went okay, but I am not seeing a GUI anywhere. Could anyone give me some tips on how to actually use barry or point me to some documentation?

Thanks,
ed

---

### Post by theorem_hunter on 2007-05-29
[http://www.petitiononline.com/bb1d1234/petition.html](http://www.petitiononline.com/bb1d1234/petition.html)

i was number 1328 or something like that...

---

### Post by AbuAnsar on 2007-07-22
Hi. I'm a newbie in Linus and using Ubuntu 7.04. It's been few days now that I'm trying ti figure out how to charge my Blackberry 8100 (Pearl) thru the USB cable. I failed to follow the steps provided in BB forums to properly download and istall bcharge. Nevertheless, to my great surprise, I just found out that it DOES CHARGE! The yello Charging Icong on BB's screen stays on, an error message "USB power is insufficient......" appears for few seconds but it does charge to 100%. 

My concern is whether it will damage anything in my Blackberry or not. If you guys ever encountered with the same problem please enlighten me on this issue. Thanks.

AbuAnsar

---

### Post by Kasuko on 2007-08-31
I have been using Evolution and I have tried to install SyncEvolution 0.6 from sources and I get this error

```
kasuko@MAGI:~/Programs/syncevolution-0.6$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
configure: configuring the client library 
+ mkdir -p /home/kasuko/Programs/syncevolution-0.6/src/client-api.build
+ cd /home/kasuko/Programs/syncevolution-0.6/src/client-api.build
+ /home/kasuko/Programs/syncevolution-0.6/src/client-api/build/autotools/configure --build= --host= --target= --disable-shared
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for libcurl... found
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating include/Makefile
config.status: creating test/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPACKAGE... yes
checking for ECAL... checking for ECAL... checking for ECAL... checking for EBOOK... checking for EBOOK... checking for EBOOK... configure: error: no backend enabled - refusing to continue: 
Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libedataserver, libecal and libebook (the
latter two are optional).

You can check that these packages are available by running
pkg-config --list-all.

```

And I just don't know how to proceed.

I'm using Evolution v2.10.1

Any help would be greatly appreciated 

Ah man the answer WAS right there in the error, just goes to show always read 21 times cause the first 20 times i read that error meant nothing. Sorry.

If anyone else has this issue just get the libecal and libebook dev packages tee hee

Thanks
Kasuko

---

### Post by neetu on 2007-09-03
Hi. I'm a newbie in Linus and using Ubuntu 7.04. It's been few days now that I'm trying ti figure out how to charge my Blackberry 8100 (Pearl) thru the USB cable. I failed to follow the steps provided in BB forums to properly download and istall bcharge. Nevertheless, to my great surprise, I just found out that it DOES CHARGE! The yello Charging Icong on BB's screen stays on, an error message "USB power is insufficient......" appears for few seconds but it does charge to 100%.

My concern is whether it will damage anything in my Blackberry or not. If you guys ever encountered with the same problem please enlighten me on this issue. Thanks.


[home phone line](http://www.homephoneline.co.uk)

---

### Post by craigiedan on 2007-09-06
This worked great for me! The gcalsync website offers a few tips to get you up and running, so I recommend that for everyone... With that there are still a few areas that need to be addressed (editing on phone, repeating events), but are fairly minor and hopefully updated soon!

FYI, I'm using a BB 8100 for anyone that needs t/s help

---

### Post by rapha on 2007-09-06
Hi all!

After reading through this thread I thought I'd take a look at Berry first and alas, it has developed greatly, including the GUI which is small but looks very nice.

However, my problem begins much earlier: when I plug in my BlackBerry 7230 it begins to charge right away (even w/o bcharge), but dmesg output shows NOTHING. No "USB device attached" message like with mice and webcams and whatnot. *No nothing* - does this happen for anybody else, too?

I don't think it is a problem with Linux, but rather with my specific BlackBerry device, as the Desktop Manager under Windows doesn't work either :(

Regards,
Raphael

---

### Post by woodi68 on 2007-09-07
> **rapha said:**
> Hi all!

After reading through this thread I thought I'd take a look at Berry first and alas, it has developed greatly, including the GUI which is small but looks very nice.

However, my problem begins much earlier: when I plug in my BlackBerry 7230 it begins to charge right away (even w/o bcharge), but dmesg output shows NOTHING. No "USB device attached" message like with mice and webcams and whatnot. *No nothing* - does this happen for anybody else, too?

I don't think it is a problem with Linux, but rather with my specific BlackBerry device, as the Desktop Manager under Windows doesn't work either :(

Regards,
Raphael


Although i don't have a 7230, I would suspect that you are correct about it being the device.  

I have a new 8830 and can't get any of these things to work, Barry, nor syncevolution, nor barry util or ANYTHING!  IT SUCKS!

---

### Post by rapha on 2007-09-07
But you do get a message in dmesg about the Blackberry being plugged in?

---

### Post by jdailey67 on 2007-09-07
I was following the instructions on the original post which was to use scheduleworld to do a synch with Google Calendar, Evolution Calendar, and BB calendar.  

My priority was google and BB.  

I had no problem installing the funambol client on BB and set up the account on scheduleworld to use funambol. 

However, setting up the connection configuration on the BB Perl, is still problematic.  T-Mobile, like the other vendors have public info on the regular phone WAP gateway. For T-mobile, that is: 
wap.voicestream.com
216.155.165.50
port 9201 

They gave me that on the first call, which had to be set in the options: advanced: TCP: APN setting.  

The second call, they also mentioned that there was a RIM gateway:  blackberry.net.  
--

Just putting this in the TCP setting did not seem to impact the Funambol client.  

The configuration in funambol also includes an APN gateway, but also insists on an IP gateway if you enter that value (i.e. blackberry.net).  Using NSLOOKUP on that returns 216.9.245.101.  Port I am assuming to be 9201 , since that seems to be the default.

---

### Post by rapha on 2007-09-07
Wow, I have absolutely no experience with using any of the the Blackberry's over-the-air functions since I don't have a contract that would permit anything else but phone calls and text messages.

You're basically saying you're not using the USB cable at all?

---

### Post by alsuren on 2007-10-03
I find it quite funny that even when we have an open protocol like syncml, we can't even sync with *that*. I have a windows mobile device, and it manages to sync fine with funambol. Shame the same can't be said about the linux side of things

My solution was:

- Set up an account on  [http://www.scheduleworld.com/](http://www.scheduleworld.com/)
- export an ical from linux
- import ical into scheduleworld
- sync mobile device

Does anyone know any ways to get two syncml servers to sync with each other? If so, that would let me use my local syncml server rather than scheduleworld (for a significant reduction in cost, thanks to wifi) and also use opensync's "syncml-http-server" module to sync.

---

### Post by rapha on 2007-10-11
Okay, my 'new' 7730 has arrived now, and it looks like the old one didn't have any problems with its USB port, since both devices show exactly the same behaviour: when you plug them in and look at /var/log/messages, it'll go like this:

```
Oct 12 00:24:13 momo kernel: [  771.932000] usb 2-2: new full speed USB device using uhci_hcd and address 73
Oct 12 00:24:13 momo kernel: [  772.112000] usb 2-2: configuration #1 chosen from 1 choice
Oct 12 00:24:13 momo kernel: [  772.116000] usb 2-2: USB disconnect, address 73
Oct 12 00:24:13 momo kernel: [  772.728000] usb 2-2: new full speed USB device using uhci_hcd and address 74
Oct 12 00:24:14 momo kernel: [  772.908000] usb 2-2: configuration #1 chosen from 1 choice
Oct 12 00:24:14 momo kernel: [  772.952000] usb 2-2: USB disconnect, address 74
Oct 12 00:24:14 momo kernel: [  773.696000] usb 2-2: new full speed USB device using uhci_hcd and address 75
Oct 12 00:24:15 momo kernel: [  773.876000] usb 2-2: configuration #1 chosen from 1 choice
Oct 12 00:24:15 momo kernel: [  773.880000] usb 2-2: USB disconnect, address 75
Oct 12 00:24:15 momo kernel: [  774.492000] usb 2-2: new full speed USB device using uhci_hcd and address 76
Oct 12 00:24:16 momo kernel: [  774.672000] usb 2-2: configuration #1 chosen from 1 choice
Oct 12 00:24:16 momo kernel: [  774.716000] usb 2-2: USB disconnect, address 76
Oct 12 00:24:16 momo kernel: [  775.460000] usb 2-2: new full speed USB device using uhci_hcd and address 77
Oct 12 00:24:16 momo kernel: [  775.640000] usb 2-2: configuration #1 chosen from 1 choice
Oct 12 00:24:16 momo kernel: [  775.644000] usb 2-2: USB disconnect, address 77
Oct 12 00:24:17 momo kernel: [  776.260000] usb 2-2: new full speed USB device using uhci_hcd and address 78
Oct 12 00:24:17 momo kernel: [  776.440000] usb 2-2: configuration #1 chosen from 1 choice
Oct 12 00:24:17 momo kernel: [  776.480000] usb 2-2: USB disconnect, address 78

```

Anybody else experience this, with the 7730 or a different model? When I plug it into a Mac, nothing happens at all but "RIM Handheld" can be seen in the device manager. Windows correctly recognizes it as a USB device; haven't gotten around to installing Desktop Manager on a Windows box yet but I'd bet it works :-(

- Raphael

---

### Post by clayt0njknight on 2007-11-02
Ninjitsu,

open a konsole.  type *sudo apt-get -f install gcc g++* and press enter.

throw your root password in.

after a bunch of stuff scrolls down the screen, it'll ask if you want to download these packages, it'll take up x.xx MB of space, blah blah blah.  just press y and enter.

let synaptic do it's thing.

bingo.  you now have g++ installed, and you won't run into that error anymore.  that's not to say, however you are missing other dependancies for compiling from source...  just gotta poke around and see.  

hint: if it says you are missing something when you do try to compile from source, use the same line i gave you earlier, substituting *gcc g++* for whatever it says you are missing.  if synaptic comes back and says "whoa, i don't know what that is" then start googling for that error.  that not only saves you a little time in a lot of cases, but also eliminates one more issue that it could be.

---

### Post by kd7swh on 2007-11-12
scheduleworld_1 missing from etc dir

---

### Post by riskable on 2007-11-14
Just thought I'd let you all know that you don't need Windows to install the Funambol plugin on your Blackberry.  You just need to create a .jad file (and unzip the .cod files).  Then you can copy the files to your Blackberry's SD card and install the plugin using the Blackberry's Media application (just navigate to the .jad file).
[URL="http://www.blackberryforums.com/linux-users-corner/104838-funambol-3-0-7-jad-file.html"]
I posted a HOWTO in the Linux forum at BlackberryForums.com[/URL]

If you want to save time I've already created a zip archive with all the necessary changes.  Download it [here]("http://riskable.com/files/Funambol_Blackberry_Plugin_3.0.7_with_jad.zip").

---

### Post by alek01 on 2007-11-14
Hi,
I know this will look desperately basic to you, but I do not know. I know Barry is installed properly and looks OK because I can access my files on the BB Curve, it charges automatically, BTool answers with my BB Pin #  BUT I do not the command to launch the GUI and to performe a sync. As there is no graphical trace of Barry (Icons) what do I need to do make a sync? Thank you very much

---

### Post by kd7swh on 2007-11-15
barry and the opensync commandline tools don't like my blackberry. But KitchenSync (OpenSync GUI) seems to work with Evolution\ScheduleWorld and the Funambol Blackberry Client which I downloaded.

Best of Luck

[http://www.blackberryforums.com/linux-users-corner/104838-funambol-3-0-7-jad-file.html](http://www.blackberryforums.com/linux-users-corner/104838-funambol-3-0-7-jad-file.html)

---

### Post by DoctorMO on 2007-11-16
Can any of you lovely blackberry wielding linux users sign up by emailing me to test new barry+opensync+conduit intergration (making it all work together without your effort) You'll all have different models so it'll be nice to know. I may not call upon anyone that signs up for a month or two but it'd be nice to have a group of people willing to help out.

You can set up very good syncing between any opensync plugin endpoint (kde-pim/evolution/thunderbird/yadda) and a blackberry using the opensync blackberry plugin, you'll need to download the source code and compile it and set it all up though which is a pain.

---

### Post by kd7swh on 2007-11-16
Anything I can do to help. I don't mind using a compiler.

---

### Post by mookie_jones on 2007-11-26
when i configure, im coming up with this resulting error
checking for EBOOK... no
checking for SQLITE... yes
configure: error: no backend enabled - refusing to continue: 
Please install the development packages of Evolution and/or
set the PKG_CONFIG_PATH variable so that it points towards
the .pc files of libedataserver, libecal and libebook (the
latter two are optional).



can someone help me figure what im doing wrong?

---

### Post by mookie_jones on 2007-11-27
bump

---

### Post by DoctorMO on 2007-11-27
I'm not sure what your doing mookie_jones, are you using barry with opensync as recommended?

---

### Post by saltydog on 2007-12-10
I have just installed Funambol 3.07 on my BB curve 8300, enrolled an SW account... but the client doesn't work. Looking at the SW's forum it seems that there is a bug in BB's APIs...

---

### Post by kd7swh on 2007-12-12
> I have just installed Funambol 3.07 on my BB curve 8300, enrolled an SW account... but the client doesn't work. Looking at the SW's forum it seems that there is a bug in BB's APIs...

Funambol didn't like my 8703 either I don't think it is SW. Maybe its the funambol application itself. It seemed to try and sync for almost 20 hours straight and still no results. :(

---

### Post by fred87 on 2008-01-08
I'm looking for a solution to sync my BB 7290 with 
sunbird, evolution and all this under gutsy.
I will be please to try something.

---

### Post by rapha on 2008-01-08
You'll probably have to get rid of berry_charge.ko somehow (rename, blacklist, whatever) and then you could try out barry (barry.sf.net if memory serves). As for Evo synching, sorry, never tried that. Do tell if you got a solution tho :-)

---

### Post by saltydog on 2008-02-07
I sthere any progress on the issue: "how to sync blackberry with thunderbird?"

---

### Post by CoYoT_ on 2008-02-25
Hi,

i was following this thread earlier, tried this solutions, but i still wasn't fully satisfied. So i've been searching for solution every month or so. Finally i found two interesting articles lately and just thought i might share.
These articles explain how to **make backups/restores under Linux** with the project called **barry** and, what's more interesting, how to **sync your Blackberry using opensync/multisync and a barry-plugin.**
This will give you the ability to sync the Calendar and Contact List of your Blackberry (*Tasks and the rest are still under development*) with your Evolution, Thunderbird or Google Calendar for example. **Without doing the sync OTA**. Moreover, the software makes it possible to sync more than only 2 sources (which means you can sync your BB with Evolution and Google Calendar and Thunderbird and KDE Pim at once), so check it out.

Some problems i have experienced:
[LIST=2]
[*]Sometimes after the sync the syncing software just stops and doesn't end the transmission with the BB, you just exit the GUI as usual and in the console you have to type 
```
btool -X
```
to reset the transmission - without doing that and just pulling the cable out *you might have to hard reboot (battery pull) the BB to make it accept connections again*. Actually the best way would be something similar to my solution - just use something like this for your multisync launch (i assume you are using bash):
Create a file with your favourite editor with the following content.

```
#!/bin/bash
multisync-gui &
btool -X
```

Save it as (let's say) _blackberry.sh_
Now go to the directory you put it in and type

```
chmod a+x blackberry.sh
```

to make it runnable. Now you can add this file as an app activator to your menu or panel.
 

[*]I'm syncing with Evolution (don't know if it's the same for other plugins) and i noticed that the plugin doesn't pull recurring appointments from the BB calendar, so don't rely 100% on the sync :)

[/LIST]
Piece of advice regarding the installation (everything else is in the articles):
[LIST=4]
[*]First add the Opensync repositories in synaptic (example is for Feisty Fawn, no dedicated packages for Gutsy are available yet, so maybe try those):
```
deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
```

and type this in your console to add the gpg key for them:

```
gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -
```

The first command might need to be started through sudo.

For other distro releases please check the Opensync [download page]("http://opensync.gforge.punktart.de/repo/opensync-0.21/").


[*]Install opensync/multisync:

```
sudo apt-get install opensyncutils multisync-tools multisync-gui multisync0.90
```
[*]After that you can go to the [Link: Barry homepage]("http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564") and install the packages in the following order (notice that there are different packages for 7.10):  	```
libbarry_0.11-1_i386.deb, barry-util_0.11-1_i386.deb,  	barrybackup-gui_0.11-1_i386.deb, libopensync-plugin-barry_0.11-1_i386.deb
```
[*]Additionally you have to install the opensync plugin you need, in my case this was **libopensync-plugin-evolution2** (there are packages for Palm, Mozilla Sunbird, Google Calendar, etc. so you can sync them all together using this one brilliant piece of software)
[/LIST]
Links to the articles (i suggest to try with the Yahoo article first, because it shows how to do this using the gui, which is probably easier):
- [Link: Article on Yahoo Blog]("http://blog.360.yahoo.com/blog-ma.mjfMjfqJUD4zlQThXHOek1nbwzg--?cq=1&p=9")
- [Link: Linux.com Article]("http://www.linux.com/feature/123251")

If you should have any questions or need help, just repost. I'll try to answer ASAP.

EDIT: Thanks to saltydog for pointing out the missing instructions.
EDIT2: A quick'n'dirty solution for the tasks function, which i came up with, would be to place the tasks in one specific day in the calendar as a list of appointments without daytime. I know this sound ridiculous and doesn't provide all the tasks features, but it works for me for now ;) Until the next release of barry.

Best regards,

Wojtek

---

### Post by saltydog on 2008-02-25
Where did you get multisync-gui? It is not in Gutsy repositories.

---

### Post by saltydog on 2008-02-25
> **CoYoT_ said:**
> Hi,

Moreover, the software makes it possible to sync more than only 2 sources (which means you can sync your BB with Evolution and Google Calendar and Thunderbird and KDE Pim at once), so check it out.

Wojtek

You mentioned Thunderbird. Is there an opensync plugin available for Thunderbird?

---

### Post by CoYoT_ on 2008-02-25
> **saltydog said:**
> Where did you get multisync-gui? It is not in Gutsy repositories.
Thanks for pointing that out, i knew i forget something ;) I forgot to add the information about adding the repos for Opensync. Now the how-to should be ok.
Thanks for the feedback, saltydog.

---

### Post by CoYoT_ on 2008-02-25
> **saltydog said:**
> You mentioned Thunderbird. Is there an opensync plugin available for Thunderbird?
There is a Mozilla Sunbird plug-in and as far as i know they operate the same way, so that should work. If you're going to test it, please let us know :)
If it won't work, then you have still the possibility to sync it with ScheduleWorld using the SyncML plugin, which will do the same as NinjitsuStylee's method, but much faster, because over USB and your internet connection and not OTA through the BB.
Actually, i'm pretty sure there has to be a way to sync Evolution with Thunderbird, which would be also a solution. A little bit more effort, but... :)
Maybe someone knows a better way?

---

### Post by saltydog on 2008-02-25
Thank you Woitek but maybe something is still missing.

After multisync installation, I still not have any plugin available in the multisync window....

---

### Post by CoYoT_ on 2008-02-25
> **saltydog said:**
> Thank you Woitek but maybe something is still missing.

After multisync installation, I still not have any plugin available in the multisync window....

Did you set up the multisync software like the article mentions it? You can either do this by using the "Add" button in the multisync GUI or in the CLI:

```
msynctool --addgroup Blackberry
msynctool --addmember Blackberry barry-sync
msynctool --addmember Blackberry evo2-sync
msynctool --showgroup Blackberry
```

and the configure your PIN number:

```
msynctool --configure Blackberry 1
```

---

### Post by saltydog on 2008-02-25
> **CoYoT_ said:**
> Did you set up the multisync software like the article mentions it? 

Yes, I did.
But when running

msynctool  --sync blackberry

I get this error:

```
~ $ msynctool --sync blackberry
Synchronizing group "blackberry" 
Error while initializing syncengine: (null)
```

---

### Post by saltydog on 2008-02-25
More, the sunbird-plugin seems to be useful only for the calendar, but I first of all need to synchronize the contacts.

---

### Post by CoYoT_ on 2008-02-25
> **saltydog said:**
> Yes, I did.
But when running

msynctool  --sync blackberry

I get this error:

```
~ $ msynctool --sync blackberry
Synchronizing group "blackberry" 
Error while initializing syncengine: (null)
```

What's the output when you run this?

```
msynctool --showgroup Blackberry
```

---

### Post by CoYoT_ on 2008-02-25
> **saltydog said:**
> More, the sunbird-plugin seems to be useful only for the calendar, but I first of all need to synchronize the contacts.

If contact are top priority i would recommend to use the barry plugin and the SyncML plugin with multisync in order to synchronize with ScheduleWorld. Then you can use in Thunderbird for example this [plugin]("http://www.topologilinux.com/syncml/")

---

### Post by saltydog on 2008-02-26
> **CoYoT_ said:**
> What's the output when you run this?

```
msynctool --showgroup Blackberry
```

This is the output:
```

 $ msynctool --showgroup blackberry
Groupname: blackberry
Member 1: barry-sync
        Configuration : #
# This is the default configuration file for the barry-sync opensync plugin.
# Comments are preceded by a '#' mark at the beginning of a line.
# The config format is a set of lines of <keyword> <values>.
#
# Keywords available:
#
# DebugMode        - If present, verbose USB debug output will be enabled
#
# Device           - If present, it is followed by the following values:
#      PIN number    - PIN number of the device to sync with (in hex)
#      sync calendar - 1 to sync calendar, 0 to skip
#      sync contacts - 1 to sync contacts, 0 to skip
#

#DebugMode

Device xxxxxxxx 1 1


Member 2: sunbird-sync
        Configuration : <config>

</config>

```

---

### Post by saltydog on 2008-02-26
I have removed the sunbird-sync and added a SyncML on the group. 
I have also opened and account on ScheduleWorld and confiured the xml file with the correct items for this site.

When I try to synchronize I get:

```
 $ msynctool --sync blackberry
Synchronizing group "blackberry" 
Member 2 of type barry-sync just connected

```


..hanging forever, no synchro.

I gave up. Thank you Woitek!

---

### Post by Galactic Jack on 2008-02-29
Hi I'm a first time Blackberry user and I've been with Ubuntu now almost a year and a half.

I got my Blackberry 7250 signed up with Bell here in Canada and it's CDMA. So I have: 1) No SD Card slot 2) no SIM card port and 3) I don't have any e-mail service [this one's not CDMA related]

I did all of the procedures, downloaded Funambol 3.0.8, set up scheduleworld and the such, but I can't seem to sync with my USB cord. When I list my usb devices it shows "RIM Blackberry" but the computer doesn't recognize it as a separate disk.

My questions are: 

1) Is there any way to do a straight sync through the USB cable without using OTA syncing. It would make things a hell of a lot easier.

2) How do I get a CDMA Blackberry to show up as a separate disk on my laptop? I figure once I can do that I can just do a straight exchange of information.

Thank you.

GJ

---

### Post by CoYoT_ on 2008-03-02
@Galactic Jack
I tried to explain the straight sync in my post in this thread. It's quite complicated by now and @saltydog couldn't make it work :/ It works for me, but still ScheduleWorld works better (Tasks sync). You can make backups and restores for sure and browse in the BB using the barry software. Just checkout the articles i mentioned in my post.

---

### Post by Galactic Jack on 2008-03-04
Ok I got it working now. I had to add this to my /etc/fstab

sudo gedit /etc/fstab

/dev/shm /media/Blackberry tmpfs defaults 0 0

Started working for me after this. I think this is the big thing a lot of eople missi n their instructions

---

### Post by saltydog on 2008-03-04
@Galactic

Doesn't work for me. In my "Computer" window I have a device named "RIM BlackBerry SD", but can't mount it.

---

### Post by Galactic Jack on 2008-03-04
sorry I should have mentionned you have to make the directory first in the /media folder. I know you're a developer so I assume you did this but it's something I often overlook myself too.

sudo mkdir /media/Blackberry

Then gedit the fstab and do a restart

----------

It could also be a problem with the drivers. My solution was to install them all. It was only a few hundred KB

----------

Question about Sunbird - what version of the plugin are you using. Because I notice that - especially for gutsy - that the 0.22 version is the one that is necessary. If you have it is it possible to post a .deb version of it [or atleast a link for it] and I will see if it will work on mine.

---

### Post by Galactic Jack on 2008-03-04
Found one.

[http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/libo/libopensync-plugin-sunbird/libopensync-plugin-sunbird_0.22-1_i386.deb](http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/libo/libopensync-plugin-sunbird/libopensync-plugin-sunbird_0.22-1_i386.deb)

---

### Post by saltydog on 2008-03-04
> **Galactic Jack said:**
> sorry I should have mentionned you have to make the directory first in the /media folder. I know you're a developer so I assume you did this but it's something I often overlook myself too.
.

No, you didn't overlook. Of course, I first have made the folder in /media!

But when it is mounted, and the BB plugged in,  I cannot browse the BB as the folder is empty

---

### Post by saltydog on 2008-03-05
> **Galactic Jack said:**
> Found one.

[http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/libo/libopensync-plugin-sunbird/libopensync-plugin-sunbird_0.22-1_i386.deb](http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/libo/libopensync-plugin-sunbird/libopensync-plugin-sunbird_0.22-1_i386.deb)

Thank you Jack, but I don't bother about calendar. I am looking for a way to synchronize my BB contacts with Thunderbird.

---

### Post by Galactic Jack on 2008-03-05
Ahh ok. The /media/Blackberry worked for me to connect the Blackberry but not to transfer anything yet. I will post any progress I make on it here.

---

### Post by bigmack83 on 2008-03-21
I have put together a blackberry on linux google group i encourage everybody to join. There is a large community of linux and blackberry users trying to tether their blackberry with linux and i want to bring them together to figure this all out. We want to be able to package everything into a gzip file and be able to run 1 script to install all of the packages for you. but in order for it to work we need to pull everyone together and collect information about both successes and failures in connecting. please help us out. I am posting by tethering through my blackberry so i know it can be done

Sprint Blackberry 7130e
Ubuntu Gutsy 7.1

[http://groups.google.com/group/blackberryonlinux](http://groups.google.com/group/blackberryonlinux)

---

### Post by bigmack83 on 2008-03-21
Sorry, accidentally double posted...  :(

---

### Post by epitaph123 on 2008-03-25
> **NinjitsuStylee said:**
> Haven't quite figured that out yet......I've been using the wall plug charger ever since I moved to Ubuntu. :(

my blackberry charges when plugged into my laptop running ubuntu, didn't have to install anything, it just charges.

---

### Post by gfunkdave on 2008-04-01
Can someone tell me why, after installing the .deb packages from Barry, none of the command line tools is present? I installed all the packages listed at the bottom of [http://netdirect.ca/software/packages/barry/install.php](http://netdirect.ca/software/packages/barry/install.php) before downloading and installing the deb packages from Barry's Sourceforge site, but still get things like this:

> 
david@better-mousetrap:~$ btool -h
bash: btool: command not found


I'm sure it's something stupid...thanks!

---

### Post by bhorn on 2008-05-02
> **epitaph123 said:**
> my blackberry charges when plugged into my laptop running ubuntu, didn't have to install anything, it just charges.

My BB did not charge with Kubuntu 7.10, but I installed Ubuntu 8.10 last week, and I just noticed that it charges now! woohoo

---

### Post by theZoid on 2008-05-13
I take the easy way and sync my BB over the air with funambol to schedule world, then sync thunderbird with Schedule World (using SW TB extension).  Works.  Forget the cable.

---

### Post by chipbennett on 2008-05-31
I know I'm late to the party on this thread, but in case it helps anyone, I have written a [how-to on synchronizing a BlackBerry with Kubuntu Hardy]("http://www.chipbennett.net/wordpress/index.php/2008/05/synchronizing-a-blackberry-in-linux/").

Please let me know if you find it helpful, or if you have any comments, corrections, or suggestions.

Thanks

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> I know I'm late to the party on this thread, but in case it helps anyone, I have written a [how-to on synchronizing a BlackBerry with Kubuntu Hardy]("http://www.chipbennett.net/wordpress/index.php/2008/05/synchronizing-a-blackberry-in-linux/").

Please let me know if you find it helpful, or if you have any comments, corrections, or suggestions.

Thanks

Chip...good man, I'll give it a go!!  I have a Curve also, and use Kubuntu.

---

### Post by chipbennett on 2008-06-01
> **theZoid said:**
> Chip...good man, I'll give it a go!!  I have a Curve also, and use Kubuntu.

theZoid, please do report back and let me know if it was helpful! I'll be happy to add/revise based on suggestions.

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> theZoid, please do report back and let me know if it was helpful! I'll be happy to add/revise based on suggestions.

I'm doing it now....you're using Kontact for the sync right?  That's fine by me...having problems with Thunderbird.

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> theZoid, please do report back and let me know if it was helpful! I'll be happy to add/revise based on suggestions.

Chip....great guide btw, however my calendar sync'd, but my contacts aren't showing up in Kontact....did I miss something?

---

### Post by chipbennett on 2008-06-01
> **theZoid said:**
> I'm doing it now....you're using Kontact for the sync right?  That's fine by me...having problems with Thunderbird.

Yes, I sync with KDE-PIM (Kontact, Kmail, Kalendar, etc.).

I can't find an official OpenSync plugin for Thunderbird, but did find [something called blueZync]("http://bluezync.kaarposoft.dk/download.html"), which purports to act as a Mozilla/Thunderbird plugin for OpenSync. If so, then it should be what you need.

---

### Post by chipbennett on 2008-06-01
> **theZoid said:**
> Chip....great guide btw, however my calendar sync'd, but my contacts aren't showing up in Kontact....did I miss something?

Do you have a filter applied to your contacts in Kontact? In the upper-right-hand corner, ensure that "Filter" is set to "None".

Beyond that, I'm not sure. I've not gotten very far with synchronizing contacts (I need to be able to sync by category); however, I did do a trial-run sync of contacts, and everything from my BlackBerry showed up in Kontact afterward.

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> Yes, I sync with KDE-PIM (Kontact, Kmail, Kalendar, etc.).

I can't find an official OpenSync plugin for Thunderbird, but did find [something called blueZync]("http://bluezync.kaarposoft.dk/download.html"), which purports to act as a Mozilla/Thunderbird plugin for OpenSync. If so, then it should be what you need.

Chip, Kontact is fine.  My calendar events sync'd with Kontact, but not my Contacts?  All that's there is the one sample entry....the tool said everything sync'd ok....are they in a different file?

EDIT:  there is NO filter selected....I have around 700 contacts...?

---

### Post by chipbennett on 2008-06-01
> **theZoid said:**
> Chip, Kontact is fine.  My calendar events sync'd with Kontact, but not my Contacts?  All that's there is the one sample entry....the tool said everything sync'd ok....are they in a different file?

Zoid, see my previous post; I think our posting is out of sync (pun intended).

---

### Post by chipbennett on 2008-06-01
> **theZoid said:**
> Chip, Kontact is fine.  My calendar events sync'd with Kontact, but not my Contacts?  All that's there is the one sample entry....the tool said everything sync'd ok....are they in a different file?

EDIT:  there is NO filter selected....I have around 700 contacts...?

Hmm, I know that when I first started using KDE-PIM, I imported a couple thousand contacts, and then didn't see them in Kontact. I didn't realize that "Filter: Unfiled" meant un-categorized contacts. Once I selected one of the categories, I could see my contacts. :)

If the sync was successful, then you should see all of your contacts with "Filter: None". I am unsure what the issue is.

Did you get any errors during the sync? Are you using the CLI sync (msynctool) or the GUI sync (KitchenSync)?

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> Hmm, I know that when I first started using KDE-PIM, I imported a couple thousand contacts, and then didn't see them in Kontact. I didn't realize that "Filter: Unfiled" meant un-categorized contacts. Once I selected one of the categories, I could see my contacts. :)

If the sync was successful, then you should see all of your contacts with "Filter: None". I am unsure what the issue is.

Did you get any errors during the sync? Are you using the CLI sync (msynctool) or the GUI sync (KitchenSync)?

OK, right now I'm using KitchenSync....it is saying it's writing 658 entries (which is the number of my contacts), and has stalled at 99% complete....I think stalled, or does this take a while?

---

### Post by chipbennett on 2008-06-01
> **theZoid said:**
> OK, right now I'm using KitchenSync....it is saying it's writing 658 entries (which is the number of my contacts), and has stalled at 99% complete....I think stalled, or does this take a while?

It might take a while. Let it complete; it will either say "successful" or else "error" (or similar). 

If KitchenSync indicates that the sync was successful, yet you still can't see your contacts in Kontact, then I'm not sure what's going on. If, however, KitchenSync returns an error, then we'll have to track down what the error is.

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> It might take a while. Let it complete; it will either say "successful" or else "error" (or similar). 

If KitchenSync indicates that the sync was successful, yet you still can't see your contacts in Kontact, then I'm not sure what's going on. If, however, KitchenSync returns an error, then we'll have to track down what the error is.

Here's where it's at right now...for 10 minutes or so....pic attached...

---

### Post by theZoid on 2008-06-01
> **chipbennett said:**
> It might take a while. Let it complete; it will either say "successful" or else "error" (or similar). 

If KitchenSync indicates that the sync was successful, yet you still can't see your contacts in Kontact, then I'm not sure what's going on. If, however, KitchenSync returns an error, then we'll have to track down what the error is.

Now the contacts are showing up....GREAT GUIDE Chip!!  The is the first guide I've seen that gets down to the nitty gritty, 1 2 3..., in plain english....good job!  PS Chip....check msynctools installation...had to do that one on my own, no biggie, and group is misspelled :-)

---

### Post by chipbennett on 2008-06-02
> **theZoid said:**
> Now the contacts are showing up....GREAT GUIDE Chip!!  The is the first guide I've seen that gets down to the nitty gritty, 1 2 3..., in plain english....good job!  PS Chip....check msynctools installation...had to do that one on my own, no biggie, and group is misspelled :-)

Oh man! I completely forgot to include installation of MultiSync! I've fixed that now. (I also found the mis-spelling of "group" and fixed, as well.)

Thanks for the feedback. I'm glad to hear that someone else has found it useful!

Now, if only we can get the Barry packages included in the Ubuntu repositories... :)

---

### Post by theZoid on 2008-06-02
> **chipbennett said:**
> Oh man! I completely forgot to include installation of MultiSync! I've fixed that now. (I also found the mis-spelling of "group" and fixed, as well.)

Thanks for the feedback. I'm glad to hear that someone else has found it useful!

Now, if only we can get the Barry packages included in the Ubuntu repositories... :)

Chip....question, how does one use the Google Calendar plugin which I installed?  thanks

---

### Post by chipbennett on 2008-06-02
> **theZoid said:**
> Chip....question, how does one use the Google Calendar plugin which I installed?  thanks

theZoid, I have written a follow-up guide for [synchronizing KDE-PIM with Google Calendar using the OpenSync google calendar plugin]("http://www.chipbennett.net/wordpress/index.php/2008/06/how-to-synchronize-kde-pim-with-google-calendar/").

Let me know if it works/helps!

---

### Post by theZoid on 2008-06-03
> **chipbennett said:**
> theZoid, I have written a follow-up guide for [synchronizing KDE-PIM with Google Calendar using the OpenSync google calendar plugin]("http://www.chipbennett.net/wordpress/index.php/2008/06/how-to-synchronize-kde-pim-with-google-calendar/").

Let me know if it works/helps!

I shall check it out!  Nice job on a no BS guide =)  btw, I'm originally from Carbondale, IL....St. Louie is the big city.....;)

---

### Post by theZoid on 2008-06-03
Chip, this is way off topic, but being a VirtualBox freak that I am, have you ever used Parallels Workstation for Linux?  [http://www.parallels.com/en/download/workstation/](http://www.parallels.com/en/download/workstation/)

---

### Post by chipbennett on 2008-06-03
> **theZoid said:**
> I shall check it out!  Nice job on a no BS guide =)  btw, I'm originally from Carbondale, IL....St. Louie is the big city.....;)

Please let me know; I'd love to know if it works. I've noticed that the OpenSync plugins aren't terribly well-documented at times, so I have no idea if it will even work.

I'll have my follow-up post on using GCalDaemon posted sometime today (hopefully). It takes more to get set up, but is, IMHO, ultimately a better solution.

Carbondale, eh? Small world!

---

### Post by chipbennett on 2008-06-03
> **theZoid said:**
> Chip, this is way off topic, but being a VirtualBox freak that I am, have you ever used Parallels Workstation for Linux?  [http://www.parallels.com/en/download/workstation/](http://www.parallels.com/en/download/workstation/)

I haven't yet. One day, when I get the chance to build a linux box, I'm going to play around with more things - including some form of VM.

---

### Post by Mainiak Blaniak on 2008-06-03
Hey all...

I've been doing some searching here and on Google and am now stumped.  I'm attempting to sync an AT&T BB Pearl 8110 with a PC running Ubuntu 8.04 Hardy Heron in Gnome.  I have followed Chip's guide above to install Barry, etc.  However, Barry doesn't seem to detect my Blackberry when it is connected.  The PC seems to detect it all right, as I can see files on the microSD card in the device.  Here is the output of lsusb with the pearl connected.

```
daniel@DarkCoffeeTower:~$ lsusb
Bus 003 Device 003: ID 0fca:8004 Research In Motion, Ltd. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:009d Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
```

And the output of btool -t:

```
daniel@DarkCoffeeTower:~$ btool -t
Blackberry devices found:
No device selected
```

However, when I connect an older, 7100 series BB to the same PC using the same cable, I get the following:

```
daniel@DarkCoffeeTower:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 0fca:0001 Research In Motion, Ltd. Blackberry Handheld
Bus 001 Device 003: ID 045e:009d Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
```
```

daniel@DarkCoffeeTower:~$ btool -t
Blackberry devices found:
Device ID: 0x809a8f0. PIN: 20287e72, Description: RIM 7100 Series Colour GPRS Handheld
Using device (PIN): 20287e72
Database database:
    Database: 0x0 'Content Store' (records: 18)
    Database: 0x1 'Service Book' (records: 1)
    Database: 0x2 'Trusted Key Store' (records: 35)
    Database: 0x3 'AutoText' (records: 108)
    Database: 0x4 'Default Service Selector' (records: 2)
    Database: 0x5 'Handheld Key Store' (records: 35)
    Database: 0x6 'Handheld Configuration' (records: 0)
    Database: 0x7 'Handheld Agent' (records: 218)
    Database: 0x8 'KeyStoreManager' (records: 1)
    Database: 0x9 'Firewall Options' (records: 1)
    Database: 0xa 'Policy' (records: 1)
    Database: 0xb 'Device Options' (records: 0)
    Database: 0xc 'Options' (records: 9)
    Database: 0xd 'Application Permissions' (records: 6)
    Database: 0xe 'Key Store Options' (records: 1)
    Database: 0xf 'RMS Databases' (records: 6)
    Database: 0x10 'TLS Options' (records: 1)
    Database: 0x11 'Certificate Options' (records: 0)
    Database: 0x12 'Smart Card Options' (records: 1)
    Database: 0x13 'Random Pool' (records: 1)
    Database: 0x14 'WTLS Options' (records: 1)
    Database: 0x15 'Input Method Switcher Option' (records: 1)
    Database: 0x16 'MemoPad Options' (records: 1)
    Database: 0x17 'Memos' (records: 3)
    Database: 0x18 'Memory Cleaner Options' (records: 1)
    Database: 0x19 'Profiles Options' (records: 1)
    Database: 0x1a 'Profiles' (records: 7)
    Database: 0x1b 'Categories' (records: 5)
    Database: 0x1c 'Bluetooth Options' (records: 1)
    Database: 0x1d 'Message List Options' (records: 1)
    Database: 0x1e 'Browser Bookmarks' (records: 3)
    Database: 0x1f 'Browser Messages' (records: 0)
    Database: 0x20 'Browser Data Cache' (records: 0)
    Database: 0x21 'Browser Channels' (records: 0)
    Database: 0x22 'Browser Folders' (records: 2)
    Database: 0x23 'Browser Options' (records: 1)
    Database: 0x24 'WAP Push Messages' (records: 0)
    Database: 0x25 'Browser Urls' (records: 7)
    Database: 0x26 'Suretype options' (records: 1)
    Database: 0x27 'Calendar Options' (records: 1)
    Database: 0x28 'CustomWordsCollection' (records: 813)
    Database: 0x29 'Alarm Options' (records: 1)
    Database: 0x2a 'Messages' (records: 1)
    Database: 0x2b 'PIN Messages' (records: 0)
    Database: 0x2c 'Saved Email Messages' (records: 0)
    Database: 0x2d 'Folder Id' (records: 1)
    Database: 0x2e 'Folders' (records: 161)
    Database: 0x2f 'Purged Messages' (records: 83)
    Database: 0x30 'Recipient Cache' (records: 1)
    Database: 0x31 'Phone Options' (records: 1)
    Database: 0x32 'Tasks Options' (records: 1)
    Database: 0x33 'Tasks' (records: 4)
    Database: 0x34 'Ribbon Bar Positions' (records: 1)
    Database: 0x35 'Calendar' (records: 7)
    Database: 0x36 'Address Book Options' (records: 1)
    Database: 0x37 'Address Book' (records: 20)
    Database: 0x38 'SMS Messages' (records: 9)
    Database: 0x39 'Searches' (records: 4)
    Database: 0x3a 'Phone Call Logs' (records: 16)
    Database: 0x3b 'Phone Hotlist' (records: 1)
    Database: 0x3c 'Attachment Options' (records: 1)
    Database: 0x3d 'Attachment Data' (records: 0)
    Database: 0x3e 'Browser Push Options' (records: 1)
    Database: 0x3f 'Help Options' (records: 1)
    Database: 0x40 'Time Zone Patch' (records: 1)
    Database: 0x41 'PasswordKeeper' (records: 0)
    Database: 0x42 'PasswordKeeper Options' (records: 1)
    Database: 0x43 'Dope Wars High Scores' (records: 1)
    Database: 0x44 'Quick Contacts' (records: 3)
```

Based on apparent proper functionality, it appears that there is not a software problem up to this point...but I'm a relative noob at both Linux and Blackberry, so perhaps it's something very basic that I'm missing??

Thanks,

Mainiak Blaniak

---

### Post by chipbennett on 2008-06-03
> **Mainiak Blaniak said:**
> Hey all...

I've been doing some searching here and on Google and am now stumped.  I'm attempting to sync an AT&T BB Pearl 8110 with a PC running Ubuntu 8.04 Hardy Heron in Gnome.  I have followed Chip's guide above to install Barry, etc.  However, Barry doesn't seem to detect my Blackberry when it is connected.  The PC seems to detect it all right, as I can see files on the microSD card in the device.  Here is the output of lsusb with the pearl connected.

```
daniel@DarkCoffeeTower:~$ lsusb
Bus 003 Device 003: ID 0fca:8004 Research In Motion, Ltd. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:009d Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
```

[ snip ]

Based on apparent proper functionality, it appears that there is not a software problem up to this point...but I'm a relative noob at both Linux and Blackberry, so perhaps it's something very basic that I'm missing??

Thanks,

Mainiak Blaniak

I would *strongly* recommend using the [barry-devel mailing list]("http://sourceforge.net/mailarchive/forum.php?forum_name=barry-devel") for hardware-related issues. The list members have the best expertise in getting any particular hardware to work.

I did some hunting on the barry-devel email archives, and from what I found, it appears that the current build may not have support for the Pearl (8004 device ID):
[LIST]
[*][[Barry-devel] Barry doesn't detect my Blackberry pearl]("http://sourceforge.net/mailarchive/forum.php?thread_name=1207597917.11499.5.camel%40ruddha&forum_name=barry-devel")
[*][[Barry-devel] Blackberry 8120]("http://sourceforge.net/mailarchive/forum.php?thread_name=20080327191123.GA1282%40foursquare.net&forum_name=barry-devel")
[/LIST]

Unfortunately right now, it looks like your only options are to compile from CVS, or wait until the next release.

But, again, email the barry-devel list and see if anyone can offer any assistance.

---

### Post by Unix_Slayer on 2008-06-05
Not to throw a wrench in this thread, but has anyone tried Blackberry Desktop Manager in Wine? I have a feeling that the bluedtooth won't work, but sync might to some extend. I would do it, but I don't want to be the guinea pig yet. I've got too many projects on my hands.

---

### Post by theZoid on 2008-06-05
> **Unix_Slayer said:**
> Not to throw a wrench in this thread, but has anyone tried Blackberry Desktop Manager in Wine? I have a feeling that the bluedtooth won't work, but sync might to some extend. I would do it, but I don't want to be the guinea pig yet. I've got too many projects on my hands.

I tried the destop manager in an XP Virtual machine and although xp recognized the rim smartphone, desktop manager wouldn't detect the blackberry.  wine?

---

### Post by Unix_Slayer on 2008-06-05
> **theZoid said:**
> I tried the destop manager in an XP Virtual machine and although xp recognized the rim smartphone, desktop manager wouldn't detect the blackberry.  wine?

Figures....

---

### Post by theZoid on 2008-06-05
> **Unix_Slayer said:**
> Figures....

I know....I'm going to work on that though....but I have sync'd it in Kubuntu per Chip's instructions, but I've done a kernel upgrade and now I'm having problems but haven't gone back through the procedure yet...Chip?

---

### Post by Mainiak Blaniak on 2008-06-05
Thanks Guys...

Chip, thanks for the direction on the barry-devel mailing list.  I hadn't seen it, and have now taken a quick look.  I'll try emailing the list when I get some more time to actually work on getting this thing working.

as far as compiling barry myself, that's probably beyond my abilities in linux at this point, unless I had a really basic tutorial...  I guess I need to learn sometime though :)

I may give wine a try, I hadn't yet installed it since switching to Hardy...but I'm grabbing the packages now.  I haven't used wine much in the past...I'm guessing I'd need a PIM also running in wine to sync with??

thanks again for the input...

MB

Edit:  Can't get BB desktop software to install in wine...hmmmm...

---

### Post by linuxpimp on 2008-06-06
I love Linux, using it and what it stands for, however for my business needs, i will only move back to Linux when important functionality, such as synching a smart phone or BB works out of the box.

It is seemingly small things like this that is keeping Linux from the mainstream. When Linux users no longer need to (but can :-) ) use a terminal it will be mainstream.

Sorry for the rant, just frustrated that it is not there yet..

LP

---

### Post by Unix_Slayer on 2008-06-06
Its time for RIM to wake up, and put out Linux software, and drivers. This is ridiculous. The bluetooth doesn't even work in Vista, because RIM failed to release drivers for the BB Bluetooth.

---

### Post by regine's on 2008-06-08
Hi
anybody with a 8310 here ?
me on ubuntu studio gnome hardy.
me and artist and video girl:guitar:
a petite blonde:popcorn:
will try out yahoo or kde pim

---

### Post by Unix_Slayer on 2008-06-08
There's got to be an easier, and simple solution to this. I have an 8320 Blackberry. I am working on taking the windows Blackberry desktop manager code apart, so I could port a version for linux we can all appreciate.

---

### Post by chipbennett on 2008-06-08
> **theZoid said:**
> I know....I'm going to work on that though....but I have sync'd it in Kubuntu per Chip's instructions, but I've done a kernel upgrade and now I'm having problems but haven't gone back through the procedure yet...Chip?

I'm not sure why a kernel update would impact the process.

The only thing I can think of is an issue with bcharge and needing to blacklist a process in the kernel (outside my area of expertise). Again, the best place to go for that question is barry-devel.

---

### Post by chipbennett on 2008-06-08
> **Mainiak Blaniak said:**
> Thanks Guys...

Chip, thanks for the direction on the barry-devel mailing list.  I hadn't seen it, and have now taken a quick look.  I'll try emailing the list when I get some more time to actually work on getting this thing working.

as far as compiling barry myself, that's probably beyond my abilities in linux at this point, unless I had a really basic tutorial...  I guess I need to learn sometime though :)

I may give wine a try, I hadn't yet installed it since switching to Hardy...but I'm grabbing the packages now.  I haven't used wine much in the past...I'm guessing I'd need a PIM also running in wine to sync with??

thanks again for the input...

MB

Edit:  Can't get BB desktop software to install in wine...hmmmm...

Reading through the barry-devel archives, they seem to be pretty good about helping people through the difficult parts such as compiling. I know some other people have had your same problem, so you might search the archives and see if you can find a workable solution.

---

### Post by chipbennett on 2008-06-08
> **linuxpimp said:**
> I love Linux, using it and what it stands for, however for my business needs, i will only move back to Linux when important functionality, such as synching a smart phone or BB works out of the box.

It is seemingly small things like this that is keeping Linux from the mainstream. When Linux users no longer need to (but can :-) ) use a terminal it will be mainstream.

Sorry for the rant, just frustrated that it is not there yet..

LP

Funny you should say that, since synching most smart phones (including BlackBerries) in Windows doesn't work "out of the box" either.

Unless you include "running the hardware manufacturer's CD to install custom software" as working "out of the box"?

That's not the fault of Linux; it is the fault of the hardware manufacturers. Your rant is better directed toward RIM, in this case.

---

### Post by chipbennett on 2008-06-08
> **regine's said:**
> Hi
anybody with a 8310 here ?
[ snip ]

I use an 8310. Have a related question or issue we can help with?

---

### Post by linuxpimp on 2008-06-14
> **chipbennett said:**
> Funny you should say that, since synching most smart phones (including BlackBerries) in Windows doesn't work "out of the box" either.

Unless you include "running the hardware manufacturer's CD to install custom software" as working "out of the box"?

That's not the fault of Linux; it is the fault of the hardware manufacturers. Your rant is better directed toward RIM, in this case.

Fair point indeed.

However blame aside, the bottom line is if i want to use the software, i need a Windows machine - and i do not like that.

lp

---

### Post by jetpeach on 2008-08-03
> **linuxpimp said:**
> Fair point indeed.

However blame aside, the bottom line is if i want to use the software, i need a Windows machine - and i do not like that.

lp

Agreed. Thankfully the market share of linux is growing. Although it may still take years, but hardware makers are beginning to pay attention and device support is better than ever before. The community is also solving these problems faster than in the past... All I can say is please keep using linux whenever the support is there, and when RIM and the other hardware manufactures shun desktop Linux, email them as I do. Together we'll bring about change.

My email sent to [email]bbsuggestions@rim.com[/email]

To whom it may concern,

I was disappointed upon searching the Blackberry website that no support for Blackberry desktop software is available for Linux-based operating systems. There are third party projects , however RIM supported development could quickly improve support on Linux desktops and please many of you customers. As an excellent alternative to the Windows Mobile platform, the Linux community would love to embrace Blackberry devices if even limited support could be offered for Linux.
Thanks,

Joseph Peach, recent Blackberry owner
Ubuntu Linux 8.04

---

### Post by itmanvn on 2008-08-04
Great tutorial !!!. I am now syncing with Google Calendar, Todo, Memo using my Black Berry 8820 and Evolution.

---

### Post by sadohert on 2008-09-28
> **theZoid said:**
> I tried the destop manager in an XP Virtual machine and although xp recognized the rim smartphone, desktop manager wouldn't detect the blackberry.  wine?

I just stumbled across this post while treading into sorting blackberry-to-Linux sync out.  I initially tried using VirtualBox and I think I had the same problem you were having using the usb cable.  Somebody on the VirtualBox forums recommended I try a bluetooth dongle, as Desktop Manager would be able to pick up the Blackberry through that.  This worked PERFEctly.... for a while.  Then for some reason Windows update decided to go off searching for new Bluetooth drivers for my USB-BLuetooth dongle.... and found new ones... except in order to make this work I *HAD* to use the original Microsoft Bluetooth driver (not any of the manufacturer supplied ones... this is a known issue with Blackberries)... well, Windows update managed to find itself some manufacturer drivers, and now I can't figure out how to revert these drivers to get it to work again (hence, I'm back here going the Linux sync route).... Anyway, if you're curious, the link at VirtualBox is:
[http://forums.virtualbox.org/viewtopic.php?p=39856#39856](http://forums.virtualbox.org/viewtopic.php?p=39856#39856)

Damn I wish this would just work... I'm gonna have a word with Lazaridis next time I see him... how many billions did the company make last year... CAM AN... throw us Linux folk a fricken bone!!  Blackberry and Linux COULD have such a good relationship

---

### Post by rorshach on 2008-10-02
ive got an 8130 and im trying to put some movies on it...is there anyway to do this?  drag and dropping my music into the music folder worked great, but for some reason my movies never seem to play.

im a pretty big blackberry nub so maybe im missing something really simple, but if you can help me out, i would really appreciate it.

---

### Post by jasonsjunk on 2008-12-07
rorshach I play movies on my 8310 blackberry all the time.  I use WinFF to convert my movies into a format and resolution the blackberry can play.  You can find the necessary WinFF preset for the blackberry at [http://www.biggmatt.com/forums/index.php?action=dlattach;topic=171.0;attach=89](http://www.biggmatt.com/forums/index.php?action=dlattach;topic=171.0;attach=89) 

To install the preset just unzip and click on File->Inport Preset inside WinFF and direct it to where you unzipped the presets.  BTW you can install WinFF using synaptic.

---

### Post by Thantos3000 on 2008-12-12
Does anyone know where Evolution stores google calendars locally? I'd like to sync my blackberry with my google calendar via evolution.

Thanks!

---

### Post by brs19301 on 2009-01-03
I recently wrote BB and asked about syncing.  Below is my msg and their reply (read from bottom up).  Seems some polite messages to the address given might be a good thing.

======================
Hello ...,

Thank you for contacting BlackBerry Customer Support.

We would like you to know that your comments were most generous and insightful. We encourage our users to submit product enhancement suggestions. To complement this approach, Research In Motion has created a special mailing address that will allow our users to submit suggestions relating to BlackBerry development. In the future, you may submit suggestions to [email]bbsuggestions@rim.com[/email]. We have forwarded this suggestion for you.

We would like to thank you again for being a valuable BlackBerry smartphone user.  Have a nice day ...!

Sincerely,

...
BlackBerry Customer Support
Research In Motion Limited 
Tel:
...


------Original Message------ 
From: ...
To: [email]help@rim.com[/email]
Subject: linux storm

Dear RIM,

I just purchased a new 9530.  Thanks for making something for Verizon
users ....  Nice device and should be great after RIM finishes tweaking the OS.  Speaking of OS it would be really nice if you guys could come up with some software that would run in Linux.  Being specific, on my wish-list (and many others) it would be nice to have packages (.DEB format) to sync with "Evolution"
mail/calendar program.

Please forward this to the wish-granters department.

Thank you and Happy New Year!

...

---

### Post by brokentroy on 2009-03-03
Ok,  I'm completley lost here.  instructions say "Plug your BB into your windows boot and install the Sync4j client using the Application loader".  I downloaded everything from funambol, but can't figure out how to get it on my BB.  I use the app loader and it does not recognize the file types.  it wants .alx or .ali.  What am i doing wrong?  Instructions say to load sync4j onto the BB.  i go to the website and there is no such monster.  only blackberry sync and mail client and those have .cod and .jar files. The linux server thingy is a .bin.  I have not idea what to do with that.  what is this sync4j and how to I install it?  

sorry noob here.  thanks for the help!

---

### Post by brokentroy on 2009-03-04
I'm sure you all knew this, but for those who don't here is a link to instructions for acquiring and installing Funambol.

[http://www.gsmblog.net/lang-en/guides-and-howtos/34-guides-and-howtos/45-installing-funambol-and-synchronizing.html](http://www.gsmblog.net/lang-en/guides-and-howtos/34-guides-and-howtos/45-installing-funambol-and-synchronizing.html)

---

### Post by terribletrouble on 2009-04-09
The one thing that I find striking, in this day and age, if you take a look at an application like XPlane, the same media installs and runs on Windows, Unix & Mac. Why is it that major players create software for just one platform.

I have been running Ubuntu now for 18 months in a full corporate environment and it has not been easy, all mail, presentations, calendar, contacts, development, travel, etc. Things like the blackberry syncing are one of the major items that will stop large corporations from moving to Unix. I cannot ever imagine a CIO saying, "oh, you cannot sync a bb in Linux, oh not to worry who needs these devices anyway".

I really wish the likes of RIM and others, would follow whatever XPlane did and make a multi-platform application...!

---

### Post by Elludium_Q-36 on 2009-04-19
If you are booting windows, YOU ARE NOT USING LINUX!  At that point, YOUR MACHINE IS A BILL GATES BOX, PERIOD.  Wine is another story.  I'm not sure about VirtualBox.  I could imagine using a type of remote procedure call or samba to remotely run DM but that'd still be using windows...  We could have endless tutorials on using evil, closed source OSes and apps...

Then we're going to our Big Brother, GOOGLE!

Going over the air would seemingly involve service books and downloading applications directly to the BB, unless you have Desktop Manager installed under VirtualBox or somehow using Wine...

If the firmware on beginner_6.10's 7730 above is not upgradeable then I doubt it is so on my 7520...  That blows out adding more BlueTooth profiles as an OBEX transfer method so it's USB or OTA.  And AGAIN, I'd need to add service books assumably by DM...

I already tried to add DM under wine, which failed!
[http://ubuntuforums.org/showthread.php?p=7097839#post7097839](http://ubuntuforums.org/showthread.php?p=7097839#post7097839)

Barry seems promising but it's only been released to Jaunty so far and the only GUI thus far is for backup and restore.  Not ready for newbies or the intermediate without dedicated time to be glued to a terminal command prompt.

I have Hardy 8.04 and there are a slew of VirtualBox-ose packages there, but I have in a year old post here, that the OSE (open source) version does NOT support USB, WAAAARRRRRRGGGGGHHHHH!!!!!!
[http://ubuntuforums.org/showthread.php?t=769513&highlight=virtualbox#post4806626](http://ubuntuforums.org/showthread.php?t=769513&highlight=virtualbox#post4806626)

It would be nice to push vcard / vcal info and do data entry via a real keyboard but it seems as if I will have to upgrade to a WiFi BB if I ever hope to do that on *nix.  Unless someone can relate a good experience with VirtualBox.

I'd rather install VB as a data channel and can do a sudo apt get install command if it is confirmed that the current hardy virtualbox-ose packages are useless for USB.

---

### Post by javyn999 on 2009-04-26
I hear ya.  I have a Windows Partition only for Blackberry to sync with Outlook, and to use Acrobat Pro.  I'd love to be completely MS free, but business is business and I NEED those capabilities.  Scribe and PDF Edit don't cut it, and neither does not being able to sync my phone with my PIM software.

---

### Post by steveneddy on 2009-04-26
You may edit the original post to reflect the fact that the newer Linux kernels since the ones used in 8.04 on have native support for Blackberry charging.

Just plug it in and it should charge.

---

### Post by Elludium_Q-36 on 2009-04-30
I read elsewhere in the forums of a CIO not dreaming of telling his rank and file that they don't need those silly devices anyway...

RIM has told us that we don't need *nix and should pay tribute to Bill Gates, accepting conficker or whatever else is uploaded to "skynet"
en.wikipedia.org/wiki/Conficker
en.wikipedia.org/wiki/Skynet_(fictional)

Where would Microsoft and Gates be if he refused to allow windows to work with other vendor's peripherals, monitors...  His genius was in universality and licensing.  What if a Win box wouldn't exchange info with apple or *nix, say over ethernet?  RIM is not making money with DM since it was a free download...

RIM is to smartphone what Windows is to computers, but more closed source...

There are other smartphones and some are linux based:
[http://www.linuxdevices.com/articles/AT9423084269.html](http://www.linuxdevices.com/articles/AT9423084269.html)

Jaunty is out and hopefully Barry will be more frontend/GUI utilitarian soon...
At least before I divest myself of this paperweight...

---

### Post by kiridude on 2009-09-15
If blackberry doesn't make their phones compatible for linux users, then we should not be giving them our money. There are lots of phones out there that are linux-friendly. And please, what can a blackberry do that so many other phones cannot do too?? Let's not get mislead by fads and marketing like all the fools who buy an iphone thinking they're getting some kind of great phone.

---

### Post by X1R1 on 2009-11-28
Is this info still useful? I mean, its very old and poster hasnt come back to update. Is there any other/better way to sync now that karmic is out? It would be nice to have contacts synced with evolution, but this seems to much hassle and dangerous also since on the first post said I could lose data.

---

### Post by dlm8751 on 2010-02-03
Schedule World seems to want money as does funambol.

---

### Post by Loyd Gravitt on 2010-03-02
> **kiridude said:**
> If blackberry doesn't make their phones compatible for linux users, then we should not be giving them our money. There are lots of phones out there that are linux-friendly. And please, what can a blackberry do that so many other phones cannot do too?? Let's not get mislead by fads and marketing like all the fools who buy an iphone thinking they're getting some kind of great phone.

Unfortunately, some of us have BB's supplied by our employers and it would be quite the waste to not be able to use them and have to purchase another phone out of my own pocket.  FWIW

---

### Post by Elludium_Q-36 on 2010-03-17
So Loyd Gravitt, 

Your employer does not also supply a windows box?

Barry is the only reason I "downgraded" from 8.04 to 9.04 and it seems to have been a mistake as 9.04 has been pretty buggy AND thusfar I haven't been able to use Barry.

Using my old BB as a modem would have been helpful too.

I'm crossing my fingers that 10.04 is not so buggy and hope to do a fresh install and am looking for another brand of smart-phone that's open-source/linux friendly.  The BB will make a nice paperweight.

---

### Post by itbcn8 on 2010-05-25
How do we get RIM to support Linux??.... There must be a way...

---

### Post by Devillbe on 2010-05-26
Hi guys,
 
I can tell you I have been using a BB for some time now, AND I have been working on the 8.04, the 9.04, 9.10 and now the 10.04.
 
I must say since I upgraded the last time to the Last 2 versions (even if they are know to be not quiet that stable) may BB is know to the system and I can transfer Files Back and forward without installing anny software.
 
But however I do also want to use the Desktop manager to upgrade or manage software on my mobilde device. For this reason only I am still using a windows console on my linux.
 
The Sync part is even more easy, I use google sync on the mobile since my All (email, calendar and contacts) are on that platform. I chose this for 2 reasons.
Free and practial to use and configre.
 
On the linux I only have the Calendar configured so I can see my appiontment when I turn on the maschine, since all is web bassed I chose not to use evolution or other.
 
I hope this helps out for other newbies Like me, or other who have been struggeling.

---

### Post by Yehudah on 2010-06-01
I just want to plug my blackberry in and not have it reboot.  Not too much to ask.

---

### Post by dreamquartz on 2010-06-18
I have a software program under Windows, called ABCBerry. This program can read the backups made under Desktop Manager and will show all the info and even converts the data in different formats, if needed.
Apperantly it is not really difficult to read the database in a BB (mine is a Curve 8310).
I do not know if the info can be utilized that way, if the knowledge is there in how to create a backup underLlinux.
It will be a one way temporarely solution, but it might be the beginning of something beautiful.

---

### Post by birkopf on 2010-06-27
Guys - did any of you managed to use BB on linux as a modem (tether) and connect to internet ?

---

### Post by 80poncho on 2010-07-02
For those of you just looking to mount you BB, I just found the answer here:

[http://linuxappfinder.com/blog/using_a_blackberry_curve_with_linux](http://linuxappfinder.com/blog/using_a_blackberry_curve_with_linux)

"
**Setting Up the microSD Card**
 After installing the card nothing appeared to have changed. This  perplexed me at first, but it turns out the problem was in configuring  the BlackBerry. To enable Mass Storage Mode navigate to Settings ->  Options -> Media Card and make sure the following settings are  correct.
 - Media Card Support: On
- Mass Storage Mode Support: On
 There is an Auto Enable option for Mass Storage mode as well. I set  this to Yes because it's the only way I will be using my BlackBerry when  connected to a computer.
 If you have a password set up for your device, it must be entered  whenever you connect in Mass Storage Mode in order to prevent someone  stealing your files.
 Once the BlackBerry is setup properly, connect it by USB and most  current distributions will auto-detect it. Kubuntu popped up a dialog  letting me know that a new drive was available and presented me with a  few options."


Once I did just that, it auto mounts as soon as it is plugged into USB now..

---

### Post by birkopf on 2010-07-03
> **80poncho said:**
> For those of you just looking to mount you BB, I just found the answer here:
Once I did just that, it auto mounts as soon as it is plugged into USB now..

I'm afraid that is well known since long time ;-) SD card will be mounted always. trouble is BB is not being seen as device...

---

### Post by Elludium_Q-36 on 2010-07-22
Methinks the answer lies in an entirely different platform.

The Palm Pre seems like my answer in older hardware.

Many hardware porviders are jumping on with Ubuntu and RIM has even come on board with Bluetooth profiles to meet mainstream demands.

RIM startes serving government clients before mainstreaaam so it wanted to be secure wihch seems  like a catch 22 in that windows is a security nightmare.

I don't see RIM changing soon.

---

### Post by revelationman on 2010-08-12
I am in the same boat with the Blackberry, we need the sync function with our contacts etc. 

I would not have Windows on this system to be honest,but RIM must understand that developing Linux software is just good customer service. 

Having support for Linux could mean a big thing to Windows because many companies could consider moving to a Linux Distro. 

So maybe just maybe there is more to this 

Well that is my viewpoint.

---

### Post by Dragonbite on 2010-09-10
I just got a Blackberry which somebody was tossing away and am looking at trying to migrate my existing phone service (Verizon) to the Blackberry but without including the (expensive) data package plan.

Does the current Barry handle installing apps and sync of contacts and calendars?  Basically, to use it like an old-style Palm PDA with phone support (but not wireless networking)?

---

### Post by MetroPietro on 2010-09-16
Hi, just referencing most recent posts; I agree that the first post should be updated to reflect the fact that things have changed in recent years.
Just to recap the prevailing strategy: RIM is not supporting direct syncing to *nix, so it is easiest to set up a web account and sync Evolution and the BB through that account. That means using Sync on Ubu and downloading sync software for the BB from whichever web service you choose.
ScheduleWorld seems to ask for money up front. Funambol and Google provide basic services for free.
1. Funambol seems to work well, but my addr-DBs on Evo and the BB had migrated apart over time, so for the first week the Funambol sync software on my BB tried to do a lot of syncing, running down the battery. I had uploaded addrs from Evo first, and Fun seemed to erase phone #s on the BB that were not in the Evo DB by default. Alas, that may the nature of syncing for the first time. In any case I uninstalled and tried Google, because I do have a backup gmail account and I might as well have this full set of contacts available to it as well. (so much for worrying about M$!Google is Big Bro now).
2. Google contacts is still listed as beta, and Sync can't sync the Evo calendar with Google Calendar. That is a pain for now, but I expect either the Evo or Sync team will try to address that within the year. Contacts synced very well to BB; but maybe because the first attempt forced me to clean them both up in the first place.

One big problem is that I now have to add $15/mo data-transfer to my AT&T plan; up to now I had none. If BB could be synced directly to Evo by cable, I would not have to do this. On the other hand, I now have three current copies of the addrs, and the copy on gmail may be visible to the Lidless Eye Wreathed in Flame, at least that cloud-copy won't get wiped out if by physical devices do.

---

### Post by herryyan on 2010-09-17
Thanks for the post mate... I'll try this soon..

---

### Post by timfinley on 2010-09-18
I just bought an old blackberry (due to availability, price and the fact that my puppy destroyed my old phone) and I was wondering if any one has tried using wine + the Blackberry Desktop Software 6.0? Wine HQ lists it as "garbage" but it was only tested on a fedora machine. I need to sync my old contacts that I have on verizon's backup assistant to my blackberry. My blackberry is so old (os ver 4.5) that I have to use this application to sync my contacts. This is frustrating because I don't have a (or want) a windows box. Any info would be appreciated. 

On another note I feel this thread should be restarted or revamped in some way. Maybe I will make this a quest of my own....

---

### Post by djcj on 2010-09-30
Hello all,

First time Ubuntu/Linux user and first time posting here.  First off, many thanks to all the contributors to the Linux platform as I'm no computer expert, but can already see the benefits of being a Linux user (from a broke artist perspective) from the wonderful software such as Audacity, Cinerella, and Ardour and hope to contribute in the future.

Okay, now to the blackberry.  I've got one of the new Blackberry tours and there's a new software program called "Backup Assistant" where you can automatically backup your contacts online by pushing a button on the Blackberry.  But what sucks is I personally need to backup my notes and tasks as i'm always thinking of random and not so random ideas and thoughts and am worried about losing any of the hundreds of notes I've compiled over the years.  And only the Blackberry Desktop manager can save backups and/or Microsoft Outlook??

if somebody knows of a workaround, please let me know.  Otherwise, I'm thinking of just using a friend's laptop to backup data weekly or monthly.  or even just go to a kinkos to backup files.

thanks,
DJCJ

---

### Post by motolinux on 2010-11-10
Google has made it super simple to sync your Blackberry with your calendar and contacts:

1) Create a Google account from your "desktop" at: [http://www.google.com/accounts](http://www.google.com/accounts)

2) Import your "contacts" via vCard or CSV file to your Google Account at: [http://www.google.com/contacts](http://www.google.com/contacts)

3) Import your "calendar" via iCal or CSV file to your Google Account at: [http://www.google.com/calendar](http://www.google.com/calendar)

4) From your "BlackBerry"  go to: [http://m.google.com/sync](http://m.google.com/sync) and download the sync tool for BlackBerry to your handset.

5) Set your Google Sync from your "BlackBerry" handset to "Sync Now" and your done!

---

### Post by supermarchino on 2010-11-22
> **motolinux said:**
> Google has made it super simple to sync your Blackberry with your calendar and contacts:

1) Create a Google account from your "desktop" at: [http://www.google.com/accounts](http://www.google.com/accounts)

2) Import your "contacts" via vCard or CSV file to your Google Account at: [http://www.google.com/contacts](http://www.google.com/contacts)

3) Import your "calendar" via iCal or CSV file to your Google Account at: [http://www.google.com/calendar](http://www.google.com/calendar)

4) From your "BlackBerry"  go to: [http://m.google.com/sync](http://m.google.com/sync) and download the sync tool for BlackBerry to your handset.

5) Set your Google Sync from your "BlackBerry" handset to "Sync Now" and your done!

but not for tasks.... :(

---

### Post by Gadzks on 2011-03-09
Noob here, and yes I have read the posts.

Is there anything new on syncing a BB via cable with Google Contacts and Calendar running Ubuntu?

I do not have data nor wifi on the BB.

TIA

---

### Post by nathan28 on 2011-03-24
Another noobish question. But is there a way to export or capture my task list from Thunderbird, then use the OpenSycn task parser to copy it over to the crackberry?

And seriously, is there ever going to be a decent way to sync smartphones with ubuntu without using Google as a work-around? I let Google datamine enough of my personal life, I have no desire to have them see my grocery list.

---

### Post by ecr959 on 2011-03-27
I agree with an earlier poster (sorry I didn't get your name).  About lets start a new , updated version of this thread.  I think there are enough people following that this is a good idea.  

I don't know how to start a poll, like for taking votes for or against, but maybe one of the forum administrators will read this post, or will start the poll-taking.

*I love Ubuntu, I use it exclusively.
*I really like Blackberry cellphones, I just bought a Torch 9800 with OS 6
*I want to learn if the new BARRY will do this or if we need to discover some other solution.

I think there are many others like me, and we want to sync calendar and contacts (and memos too) and install apps and check and do other stuff on our Blackberries.:P

Maybe someone reading this can get the ball rolling.

---

### Post by mudguts on 2011-07-13
and.. did we get the new ball rolling?

I have a BB9800 and Ubuntu 11.04
I need to sync my calendar with Thunderbird...

so any suggestions would be appreciated.

---

### Post by nconceicao on 2011-08-04
Any luck on getting the sync software to work?

---

### Post by Automat2 on 2011-08-18
> **nconceicao said:**
> Any luck on getting the sync software to work?

I have just tried "Barry", and so far, it's backed up everything without a problem.However, I haven't tried the restore function because I'm waiting for a replacement handset. The one I have at the moment shows a blank screen.

I should find out how "Barry" works tomorrow or the day after.

---

### Post by Elvis99 on 2011-09-07
Well, this whole Barry Blackberry Linux business is awfully frustrating. I managed to back up my files from my Berry, but to import the dump file barry created into evolution ... I have no idea how to do that. There are some guides, but they are referring to obsolete packages and I am on the edge of throwing the BB out of the window, and the pc alongside with it. </rant off>

---

### Post by tnc on 2011-10-21
So, still no real sync for Ubuntu-BB.  Rim should get off the pot....

Anyway, tried barry again today (1-2 years since last), no joy.  The barrybackup webpage seems to have stalled at about a year ago.  Time for Rim to be getting emails from frustrated BB/Linux users?  Hmmmm...?

Would love to boot windows off my computer completely.

---

### Post by jpaulb on 2013-10-03
> **ecr959 said:**
> I agree with an earlier poster (sorry I didn't get your name).  About lets start a new , updated version of this thread.  I think there are enough people following that this is a good idea.  

I don't know how to start a poll, like for taking votes for or against, but maybe one of the forum administrators will read this post, or will start the poll-taking.

*I love Ubuntu, I use it exclusively.
*I really like Blackberry cellphones, I just bought a Torch 9800 with OS 6
*I want to learn if the new BARRY will do this or if we need to discover some other solution.

I think there are many others like me, and we want to sync calendar and contacts (and memos too) and install apps and check and do other stuff on our Blackberries.:P

Maybe someone reading this can get the ball rolling.

I´ll second that I am considering scraping my HTC One V Android crap and going to Blackberry. Hope they don´t go broke before I do.):P

---

### Post by uwe-bungto on 2014-09-17
I just picked up a BB Q5, tried to use Barry Desktop, which warns 

> No OpenSync libraries were found. Sync will be unavailable until you install OpenSync version 0.22 or version 0.4x on your system, along with the needed plugins.

OpenSync does not seem to be in the Ubuntu 14.04 Repositories.

Any suggestions

---

### Post by Dragonbite on 2014-09-18
> **uwe-bungto said:**
> I just picked up a BB Q5, tried to use Barry Desktop, which warns 



OpenSync does not seem to be in the Ubuntu 14.04 Repositories.

Any suggestions

Does this Launchpad page help? [https://launchpad.net/ubuntu/+source/opensync]("https://launchpad.net/ubuntu/+source/opensync")

---

