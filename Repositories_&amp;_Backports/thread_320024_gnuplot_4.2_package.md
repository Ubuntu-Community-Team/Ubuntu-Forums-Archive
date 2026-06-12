---
title: "gnuplot 4.2 package"
date: 2006-12-16
forum: Repositories &amp; Backports
---

### Post by knahrvorn on 2006-12-16
I hope this is the right forum for my question. If not, please direct me to the right place. Thanks.

I'm trying to install gnuplot 4.2 (which is currently in release candidate status) on my Edgy system, since the latest stable gnuplot (4.0) lacks some functions that I need (histograms).

However, I didn't succeed in finding a gnuplot 4.2 deb package for Ubuntu (or for Debian, which will install on Ubuntu). Is anyone here aware of such a package, or a repository that carries it?

I've tried to compile and install from scratch (i.e. tarball) myself, alas without luck. During "./configure" I get the following error: "checking for C compiler default output file name... configure: error: C compiler cannot create executables" -- but I guess this is definitely for another forum ;)

Thanks in advance!

---

### Post by vidak on 2006-12-29
I could compile and install gnuplot 4.2 from source using edgy, on 64bit and 32bit architectures, so there should be some mess at your place ;)
Could you manage to compile any other programs from source? Do you have everything needed for compiling this thing? (make, automake, gcc, etc...)

---

### Post by tobs.en on 2007-03-20
I had the same problem because I needed some of the new filledcurves things in gnuplot 4.2.

I compiled it myself but without x11-terminal. I also kept the 4.0 version and installed gnuplot 4.2 into another directory. 

1. download the the source 

 gnuplot-4.2.0.tar.gz

from

[http://www.gnuplot.info/download.html](http://www.gnuplot.info/download.html).

2. unpack it 

>>gunzip  gnuplot-4.2.0.tar.gz
>>tar -xf gnuplot-4.2.0

this will create a folder named gnuplot-4.2

3. change to this folder

>> cd gnuplot-4.2

and run 'configure' with the directory you want to install gnuplot4.2 (e.g. /home/tobias/programms/gnuplot4.2/)

>> ./configure --prefix=/home/tobias/programms/gnuplot4.2/

then

>> make
>> make install

4. the executable file now is  /home/tobias/programms/gnuplot4.2/gnuplot
If you want to access it from everywhere you can, for example, create a link in a folder which includes in your 'PATH' enviroment variable. 

for example:
>> cd ~/bin
>> ln -s /home/tobias/programms/gnuplot4.2/bin/gnuplot      gp4.2

I called it gp4.2 to avoid a confict with the regular gnuplot (4.0) command.

Tobias.

---

