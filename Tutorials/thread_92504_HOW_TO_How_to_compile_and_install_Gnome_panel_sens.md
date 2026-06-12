---
title: "HOW TO: How to compile and install Gnome panel sensors-applet"
date: 2005-11-19
forum: Tutorials
---

### Post by Zed on 2005-11-19
I wanted a persistent display of my CPU and hard drive temperatures on my Gnome panel (I tend to work with one maximized window at a time, so I'm not into gdesklets.) The Breezy universe repository offers the xfce4-sensors-plugin, but, for whatever reason, Breezy doesn't include sensors-applet for Gnome. Here's what I did to install it.

First, get [sensors](http://ubuntuforums.org/showthread.php?t=2780) working. Don't proceed without this step. Be warned that it's possible to render your machine [unbootable](http://ubuntuforums.org/showthread.php?t=41041) if you configure things incorrectly.

There are [Debian packages](http://sensors-applet.sourceforge.net/index.php?content=packages) available. I didn't use them. Maybe one or the other would work in Ubuntu; I don't know. This how-to calls for installing the build-essential package, which is a bunch of stuff you only need to compile things yourself. If disk space is tight or you otherwise don't like the idea of installing that much stuff to get one little applet, don't do it.

```

sudo apt-get install build-essential
sudo apt-get install libpanel-applet2-dev
sudo apt-get install libxml-parser-perl

```

If your hard drive supports SMART monitoring (which it probably does unless it's really old) and you want to use the sensors-applet to display its temperature, then:

```

sudo apt-get install hddtemp

```

When it asks you if you want it to run as a server, say yes. You can

```

sudo dpkg-reconfigure hddtemp

```

if you want to change it later.

Then download sensors-applet-1.5.2.tar.gz from [Sourceforge](http://prdownloads.sourceforge.net/sensors-applet/sensors-applet-1.5.2.tar.gz?download). (This is the current unstable version; the release version is [1.4](http://sensors-applet.sourceforge.net/index.php?content=source).)

```
cd ~/Desktop # or wherever you downloaded it to
tar xvzf sensors-applet-1.5.2.tar.gz
cd sensors-applet-1.5.2
./configure --prefix=/usr
make
sudo make install

```

You should now be able to right-click on your panel, select 'Add to Panel', and the add to panel window will include 'Hardware Sensors Monitor' with a computer chip icon, under Accessories. Click and drag it to the panel. Right-click on it and select properties to configure it. Here's a picture of mine, on a left-hand-side vertical panel.

---

### Post by majikstreet on 2005-11-19
[QUOTE=Zed]
tar xvzf sensors-applet-1.5.2.tar
[/QUOTE]

should be "tar xvzf sensors-applet-1.5.2.tar.gz"

---

### Post by Zed on 2005-11-19
Fixed; thanks.

---

### Post by j813 on 2005-12-01
Tootal Linux newB here:confused: 
I get this error all the time I try to install anything. What do I lack? I tried installing gawk(what is this?). Anyways please help me on what I need to install to be able to compile? Thanks:smile: 

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

---

### Post by Sutekh on 2005-12-01
That error is basically saying you don't have some packages that are required to make, compile and build.

I assume that you did a 
```

sudo apt-get install build-essential

```
as per the guide.  You may also need to
```

sudo apt-get install gcc-3.4

```

To install the GNU C compiler

---

### Post by j813 on 2005-12-01
Thanks for the quick reply
I already installed the GCC 4.0 also installed GCC 3.4 thru Synaptic.

---

### Post by Sutekh on 2005-12-01
Try re-installing build-essential, that should be it.
I've read alot of posts about "C compiler cannot create executables", they all seem to be resolved using build-essential.

---

### Post by j813 on 2005-12-01
Thanks again Sutekh 
Made some changes
Although after trying to apt-get some missing files there is still some? Please help:smile: 
Here's the log

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
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
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

---

### Post by artnay on 2005-12-01
Don't do "sudo make install", instead install checkinstall (sudo apt-get install checkinstall) and create a Debian package (.deb) with it by replacing "sudo make install" with "sudo checkinstall". That way you don't need "make clean" in order to remove an installation, "sudo dpkg -r package" is an easier and probably more favoured way. Isn't there checkinstall HOWTO somewhere?

---

### Post by Sutekh on 2005-12-01
[QUOTE=SGC]
To install the XML parser, run the following command:
```

sudo perl -MCPAN -e shell

```
When asked to do a manual configuration, type no

At thecpan> prompt type:
```

install XML::Parser

```
[/QUOTE]

Try this.

---

### Post by j813 on 2005-12-01
OK, will try.:D 
I'll update later

---

### Post by j813 on 2005-12-01
Sutekh
After trying to install the XML parser, got this errors
Here's the last part of the log, too long to paste here

Expat.xs:2194: error: syntax error before ‘)’ token
Expat.xs:2197: error: ‘parser’ undeclared (first use in this function)
make[1]: *** [Expat.o] Error 1
make[1]: Leaving directory `/home/...../.cpan/build/XML-Parser-2.34/Expat'
make: *** [subdirs] Error 2
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

cpan>

---

### Post by Sutekh on 2005-12-01
[QUOTE=j813]
  make had returned bad status, install seems impossible
[/QUOTE]
That doesn't sound encouraging does it?  What exactly are you trying to install?  For the most part its alot easier to install via Synaptic or a .deb rather than from source.

---

### Post by makisupa123 on 2005-12-01
Everything worked well but I have 2 questions:

1.  For some reason my main drive /dev/sda is not listed in the HD tempoptions...just an ide drive that i have in the machine.  The sata drive is new and i'm quite sute its SMART enabled.

2.  Is there anyway to change the labels that that the panel applet uses?  Tem3 is my mobo sensor and i'd like to display that instead of "temp3".

Thanks,

mak

PS:  Good how to!

---

### Post by RSX311 on 2005-12-04
awesome How-To, works for me on my amd64 machine :p

---

### Post by Zed on 2005-12-04
> checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Did you miss this step?

```
sudo apt-get install libxml-parser-perl
```

> 1. For some reason my main drive /dev/sda is not listed in the HD tempoptions...just an ide drive that i have in the machine. The sata drive is new and i'm quite sute its SMART enabled.

No clue, sorry. What does

```
sudo hddtemp /dev/sda
```

do?

> 2. Is there anyway to change the labels that that the panel applet uses? Tem3 is my mobo sensor and i'd like to display that instead of "temp3".

That one I know. Right-click on the sensors applet in your panel, select the 'Sensors' tab, select right-arrow next to the sensor corresponding to your mobo (it's i2c-sys for me, but this will vary) to drop down its submenu. Then select the Tem3 line, and, then select the label and it'll become an edit box and you can change it. (Don't double-click quickly -- it's like renaming a file in Windows.)

---

### Post by j813 on 2005-12-04
How blind can I be. Too much excited.:razz: 
Will update you Zed.:) 

BTW I installed from Synaptic the SMART sensors, X-sensor(which is running fine but too large Graphics). Is it just OK?

---

### Post by j813 on 2005-12-04
Great now it is working:) 
Although on the "make" command it gave me this errors 

main.c:40: fatal error: opening dependency file .deps/main.Tpo: Permission denied
compilation terminated.
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/j813/Desktop/Downloads/sensors-applet-1.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/j813/Desktop/Downloads/sensors-applet-1.5.2/src'
make: *** [all-recursive] Error 1


(which I just ignored & did the "sudo make install" command) & seem to be working

---

### Post by appdx on 2005-12-30
When i did this it says no sensors found...help?

---

### Post by henriquemaia on 2006-03-06
Nice howto. Everything went ok. Thanks a lot for this.

:-D

---

### Post by chapterthree on 2006-03-11
I just followed these steps and it worked for sensors-applet-1.6.tar.gz, so the original thread may want to be updated with this information.

---

### Post by briancrutin on 2006-03-11
big help! thanks!:)

---

### Post by escape on 2006-03-14
Are there any sensors besides the temp sensor that comes by default? Where can we get them?

---

### Post by Polygon on 2006-08-08
i did everything, but i have a couple problems

one, i have two cpu's that i can choose from (the sensor), cpu (intel) and cpu (amd). The weird thing is, i have an AMD processor , but the cpu (amd) sensor does not seem to work. it just sits at 25 degrees celsius (which i know is not right)

but when i use the cpu(intel) sensor the temperature works actually. Is this normal?

and second, i think that the cpu sensor is off. Right now its showing 40 degrees celsius which i KNOW cant be right. and the motherboard is showing 57 degrees celsius. But according to a different program in windows, it shows that:

Temperatures:
			Motherboard  	39 °C (102 °F)
			CPU  	57 °C (135 °F)
			CPU Diode  	67 °C (153 °F)

how come the cpu/motherboard sensors are wayyyy off?

---

### Post by SebMKd on 2007-02-21
For some reason I was missing the follwoing dependence: libpanel-applet2-dev
I've looked for it in Synaptic and installed it. 

I'm using Dapper and once I've finished the install as suggested, I went to install Panel-sensor on my top panel. But I didn't find it under "Accessories". However, there was a "Hardware monitor" System... Is this the same program??

Either way, I have what I need now! :)

---

### Post by Mahelita on 2011-11-08
Wow, still works perfectly after 7 years!!!! (with version 3.0, some more dependencies to solve but very easy, just do what the configure step tells you)
Installing and using GNOME instead of Unity and following this guide allows you to use sensors-applet with ubuntu 11.10! (sensors-applet was removed from the 11.10 repo!!!)

---

