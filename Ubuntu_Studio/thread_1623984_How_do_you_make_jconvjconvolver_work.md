---
title: "How do you make jconv/jconvolver work"
date: 2010-11-17
forum: Ubuntu Studio
---

### Post by marcoharder on 2010-11-17
I can't seem to make this convolution reverb work from the command line. It gives me this 'Syntax error on line 1' message every time I try to run it from the command line. 
 
Anybody who can point me to a good tutorial? I wanna use all these convolution reverbs that I used to use with SIR when I was still using WinXP.
 
Cheers
 
 
MH

---

### Post by Pablo_F on 2010-11-17
The jconv command calls a configuration file, which points to the IR file and sets several options.

You have examples. This is a suggestion:

sudo cp -av /usr/share/jack-jconv/config-files/* /home/your_user_name/jconv-config-files/

Change the owner, so you don't have problems to read and write:

sudo chown -R your_user_name.your_user_name /home/your_user_name/jconv-config-files/

Take a look at a simple one, for example:

cat /home/your_user_name/jconv-config-files/chapel.conf

```

#
#  Copyright (C) 2005-2007 Fons Adriaensen <fons@kokkinizita.net>
#  
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#
#  -----------------------------------------------------------------------------
#
#
# Jconv demo configuration
# ------------------------
#
# The file 'chapel.wav' contains the reverb impulse response only,
# not the direct sound. The correct way to use this in e.g. Ardour
# is to use a post-fader send on the channels that need this reverb.
# This way you can use a single reverb for any number of tracks,
# and adjust the amount of reverb in function of the 'depth' or
# 'distance' of each track.
# The output can be connected directly to the Master module, or via
# a stereo bus if you want to control the return gain (which should
# not normally be necessary but can be handy).
#
# The required file 'chapel.wav' can be found at
#
#  http://www.kokkinizita.net/linuxaudio/downloads/chapel.wav
#
#
# Replace by whatever required...
#
/cd /audio/reverbs
#
#
#                in  out   partition    maxsize
# -----------------------------------------------
/convolver/new    1    2         512      80000
#
#
#              num   port name     connect to 
# -----------------------------------------------
/input/name     1     Input
#
/output/name    1     Output.L
/output/name    2     Output.R
#
#
#               in out  gain  delay  offset  length  chan      file  
# -----------------------------------------------------------------------------------
/impulse/read    1   1   0.5    0       0       0     1    chapel.wav
/impulse/read    1   2   0.5    0       0       0     2    chapel.wav
```

In this example, /audio/reverbs is the directory path where your IR's are. You could change that line to:

/cd /home/your_user_name/my_IR_files

The rest is more or less self-explanatory. Of course, in this example, chapel.wav must be in /home/your_user_name/my_IR_files

Change paths and IR files names as needed. 

Now, do a:

jconv /home/your_user_name/jconv-config-files/chapel.conf

(or whatever conf file you have written)

And you are done.

This example has one input and two outputs and it is simple enough but jconvolver is very flexible and it has lots of options. See the other configuration examples and also take a look at 

cat /usr/share/doc/jack-jconv/README.CONFIG

See also: [http://www.kokkinizita.net/linuxaudio/](http://www.kokkinizita.net/linuxaudio/)


Frontends:

Now, afaik, there are two gui frontends for jconvolver. Needless to say, none of them is as flexible as the jconvolver config file.

One is called Jcgui, which is a break-out of guitarix. In fact, you can also use guitarix as a jconvolver front-end.  [http://jcgui.sourceforge.net/](http://jcgui.sourceforge.net/)

The other one is called conviction. And you can find it here: 

[http://sourceforge.net/projects/conviction/](http://sourceforge.net/projects/conviction/)


Cheers! Pablo

---

### Post by marcoharder on 2010-11-18
Hey, thanks man! Not only did you point to where I should be reading but also a front end! I think that's what I greatly need as I come from a Windows DAW background [yuck, I know, but I'm learning!] and most of the reverb tasks I need are quite simple anyway. Thanks again!
 
MH

---

### Post by marcoharder on 2010-11-20
I seem to be having a problem installing jcgui; I tried installing it in both software center and synaptic but it keeps on failing

---

### Post by Pablo_F on 2010-11-20
Hi, 

jcgui is not in the official ubuntu repos so it will not appear in the software center or synaptic. You have to download the sources and compile it. It is really easy but I will explain how to do it if you wish, step by step. 

As a general rule, read the README and INSTALL files in the sources and install the essential tools to compile or build programs (package "build-essential" in synaptic). Then you will have to install some development packages that are in the official repos aswell, so synaptic will do it, but use "sudo apt-get install package" in a terminal because it is a lot faster. Develpment packages typically end with "-dev". For example, libasound2-dev. But there are lots of them and you only need a few. That should be documented in the above said files and, if nothing else, you can always try compiling and read the error messages, then install the missing packages and try again after cleaning (make clean ./waf clean or whatever). ¿What ubuntu version are you running?

Cheers! Pablo

---

