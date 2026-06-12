---
title: "Re: Ezstream old version on ubuntu server on my raspberry pi ?"
date: 2021-02-20
forum: Server Platforms
---

### Post by echosmart on 2021-02-20
Hi !
I want to make my raspberry pi one little radio server, for home.
Installed icecast2, and server run ok, but i have problems with ezstream.

Ezstream it's installed (last version) and not recognize correctly my ezstream xml config files.
If i run ezstream, i have this error:

```
ezstream -c /home/ftpuser/ftp/ezstream_mp3.xmlezstream[5068]: /home/ftpuser/ftp/ezstream_mp3.xml: world readable
ezstream[5068]: stream: default: no configuration

```

I have this problem with other servers, tested this on google cloud server, and only version 0.5.6 working corectly with my configuration file.
The problem is:
how to install older version of ezstream, 0.5.6 in this case...
I'm dowload tar.gz files [from this place]("https://ftp.osuosl.org/pub/xiph/releases/ezstream/") and get [this file]("https://ftp.osuosl.org/pub/xiph/releases/ezstream/ezstream-0.5.6.tar.gz") for install oin my raspberry pi.

After download, i uncompress archieve vith:
```
tar xzf [ezstream-0.5.6.tar.gz]("https://ftp.osuosl.org/pub/xiph/releases/ezstream/ezstream-0.5.6.tar.gz")
```

and enter in ezstream-0.5.6 folder...
after this i run
```
./configure
```
and i have this in console
```
root@ubuntu:/home/ftpuser/ftp/ezstream-0.5.6# ./configurechecking for a BSD-compatible install... /usr/bin/install -c
checking for a thread-safe mkdir -p... /usr/bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for AIX... no
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc option to accept ISO C99... none needed
checking for gcc option to accept ISO Standard C... (cached) none needed
checking for fgrep... /usr/bin/grep -F
checking build system type... build-aux/config.guess: unable to guess system type


This script, last modified 2008-11-15, has failed to recognize
the operating system you are using. It is advised that you
download the most up to date version of the config scripts from


  [http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.guess;hb=HEAD](http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.guess;hb=HEAD)
and
  [http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD](http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD)


If the version you run (build-aux/config.guess) is already up to date, please
send the following data and any information you think might be
pertinent to <config-patches@gnu.org> in order to provide the needed
information to handle your system.


config.guess timestamp = 2008-11-15


uname -m = aarch64
uname -r = 5.4.0-1028-raspi
uname -s = Linux
uname -v = #31-Ubuntu SMP PREEMPT Wed Jan 20 11:30:45 UTC 2021


/usr/bin/uname -p = aarch64
/bin/uname -X     =


hostinfo               =
/bin/universe          =
/usr/bin/arch -k       =
/bin/arch              = aarch64
/usr/bin/oslevel       =
/usr/convex/getsysinfo =


UNAME_MACHINE = aarch64
UNAME_RELEASE = 5.4.0-1028-raspi
UNAME_SYSTEM  = Linux
UNAME_VERSION = #31-Ubuntu SMP PREEMPT Wed Jan 20 11:30:45 UTC 2021
configure: error: cannot guess build type; you must specify one
root@ubuntu:/home/ftpuser/ftp/ezstream-0.5.6#



```

after this i run ```
make
```
and in console i have this ....
```


root@ubuntu:/home/ftpuser/ftp/ezstream-0.5.6# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:/home/ftpuser/ftp/ezstream-0.5.6#



```

How to solve instalation of older version of ezstream on my raspberry pi ?

Sorry for my bad english.

all working ok with ezstream-0.6.1 version

i try to make ezstream to run automatically on system boot.
Trying with crontab -e
put this line in crontab
@reboot ezstream -c /home/ftpuser/ftp/ezstream_mp3.xml
and not run automatically on reboot....\

second try,
sudo nano /etc/rc.local

add this line:
sudo ezstream -c /home/ftpuser/ftp/ezstream_mp3.xml

i try to make ezstream to run automatically on system boot.
Trying with crontab -e
put this line in crontab
@reboot ezstream -c /home/ftpuser/ftp/ezstream_mp3.xml
and not run automatically on reboot....\

second try,
sudo nano /etc/rc.local

add this line:
sudo ezstream -c /home/ftpuser/ftp/ezstream_mp3.xml

but not run automatically on reboot

---

### Post by echosmart on 2021-02-20
try to run automatically with [this procedure]("https://help.skysilk.com/support/solutions/articles/9000162390--basic-how-to-start-a-program-or-script-on-linux-automatically-on-boot-with-systemd"), but not starting automatically.

---

### Post by echosmart on 2021-02-20
With [this procedure]("https://www.dexterindustries.com/howto/run-a-program-on-your-raspberry-pi-at-startup/") autostart working ok !

Thread closed, all ok !

---

