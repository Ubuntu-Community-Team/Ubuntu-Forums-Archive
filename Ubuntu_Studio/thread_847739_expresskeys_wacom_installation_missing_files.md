---
title: "expresskeys wacom installation missing files"
date: 2008-07-02
forum: Ubuntu Studio
---

### Post by bigdee973 on 2008-07-02
i got expresskeys 0.4.2 on my pc i havent installed it because it says i need xlibs-dev...i go to terminal and sudo apt-get install xlibs-dev and i get this out put 
Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs-dev has no installation candidate

i need this file to be installed so that my buttons on my wacom pad work...please help im using the latetest version of ubuntu and i have not customize my synaptic source or any of that stuff whatsoever could someone help?

---

### Post by Stochastic on 2008-07-02
try installing xlibs-static-dev ```
sudo apt-get install xlibs-static-dev
``` according to [http://packages.ubuntu.com/hardy/xlibs-static-dev](http://packages.ubuntu.com/hardy/xlibs-static-dev) > This package depends on the individual libraries that used to be contained within the package of this name. These libraries used to be static libraries, but have since become shared libraries with their own packages and can be depended on by themselves. This package is for transitional purposes to prevent disruptions during automated package builds, and my be safely removed from your system. 

---

### Post by bigdee973 on 2008-07-02
> **Stochastic said:**
> try installing xlibs-static-dev ```
sudo apt-get install xlibs-static-dev
``` according to [http://packages.ubuntu.com/hardy/xlibs-static-dev](http://packages.ubuntu.com/hardy/xlibs-static-dev)

yeah i figured i had to do that and i did before in the package manager synaptic.  i have had it installed and rebooted my comptuer several times installed the program over again but i always get this output when i type in sudo ./configure in terminal..theres was more beofre checking libgen.h but i dont think its neccesary to share that part
checking libgen.h presence... yes
checking for libgen.h... yes
checking for X library directory... found /usr/lib
checking for X include directory... found /usr/include

Checking the X compiling environment in detail...

/usr/lib/libX11.so OK
Can not link with Xext /usr/lib/libXext.so library!
Can not link with Xi /usr/lib/libXi.so library!
Can not link with Xtst /usr/lib/libXtst.so library!
/usr/include/X11/Xlib.h OK
/usr/include/X11/Xutil.h OK
/usr/include/X11/extensions/XInput.h OK
/usr/include/X11/extensions/XIproto.h OK
Can not include /usr/include/X11/extensions/XTest.h header file!

The X compiling environment is NOT complete!
Some linux distributions omit parts of, or sometimes
the whole, X development environment. Based on the
error message(s) above you should be able to hunt down
which package(s) you need to install. For example, one
distribution call their xinput and xtest packages
libxi-dev and libxtst-dev

im not sure what the computer is trying to say about that header file what should i do?

---

### Post by Stochastic on 2008-07-03
It looks like you're missing the XTest.h file, when you get an error like that, the best command to help you fix it is ```
apt-file search XTest.h
```(it searches for the packages which contain the specified file - though you may need to install apt-file first), and according to that, you should download the x11proto-xext-dev package, then try ./configure again.

Edit: whoops I didn't read your full error output before posting, looks like you also need these packages: libxtst-dev libxi-dev libxext-dev

---

### Post by bigdee973 on 2008-07-03
> **Stochastic said:**
> It looks like you're missing the XTest.h file, when you get an error like that, the best command to help you fix it is ```
apt-file search XTest.h
```(it searches for the packages which contain the specified file - though you may need to install apt-file first), and according to that, you should download the x11proto-xext-dev package, then try ./configure again.

Edit: whoops I didn't read your full error output before posting, looks like you also need these packages: libxtst-dev libxi-dev libxext-dev

okay installing the last batch of files worked for me.  it configured it properly now theres the issue with making this thing work in hardy.  in the folder expresskeys-0.4.2 theres another folder named src-expresskeys and in there their is a file called getdevice.c.  in that file, line 462 i have to add this line of code to it...

||
     xdevice_list[i].use == IsXExtensionPointer)

as mentioned in this link here... [http://ubuntuforums.org/showthread.php?p=4774752](http://ubuntuforums.org/showthread.php?p=4774752) 
.. now compiling it with this code added to the source i get this error...

if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/include  -Wall -g -O2 -MT get_device.o -MD -MP -MF ".deps/get_device.Tpo" -c -o get_device.o get_device.c; \
	then mv -f ".deps/get_device.Tpo" ".deps/get_device.Po"; else rm -f ".deps/get_device.Tpo"; exit 1; fi
get_device.c: In function ‘get_device_info’:
get_device.c:462: error: expected expression before ‘||’ token
get_device.c:463: error: expected statement before ‘)’ token
make[2]: *** [get_device.o] Error 1
make[2]: Leaving directory `/home/blankhead/expresskeys-0.4.1/src-expresskeys'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/blankhead/expresskeys-0.4.1'
make: *** [all] Error 2

i also tried installing the file WITHOUT editing getdevice.c file.  of course it worked just fine but i continue to get the error as mentioned in that link where it says ...

expresskeys ERROR: Tablet not attached, OR (in case of Cintiq 21UX, Intuos3
and Graphire4) the 'pad' device has not been specified in xorg.conf, OR is
lacking on the command line when using "named devices".

now of course everything is installed fine my tablet works etc.  its just that i guess with this new xlib setup im going to have to edit the getdevice.c in a different manner any suggestions?

---

### Post by Stochastic on 2008-07-03
That error is a code syntax error, which likely mean your edits haven't followed the proper formatting.  Could you post lines 460 461 462 463 464 465 of that file? (do a straight copy/paste into codebraces (the # icon in the post editor), no re-typing)

---

### Post by bigdee973 on 2008-07-03
> **Stochastic said:**
> That error is a code syntax error, which likely mean your edits haven't followed the proper formatting.  Could you post lines 460 461 462 463 464 465 of that file? (do a straight copy/paste into codebraces (the # icon in the post editor), no re-typing)

these lines of codes are from my getdevice.c file which i copied and pasted right here...its from line 459 to 466...(xdevice_list= is the beginning at line 459 and .name); is the last at line 466)

xdevice_list = XListInputDevices(display, &nr_devices);

	for(i = 0; i < nr_devices; i++) {
		if (xdevice_list[i].use == IsXExtensionDevice) ||
     		    xdevice_list[i].use == IsXExtensionPointer) {
			len = strlen(xdevice_list[i].name);
			snprintf(read_buffer, MAXBUFFER, "%s", xdevice_list[i]
									.name);

---

### Post by Stochastic on 2008-07-04
> **bigdee973 said:**
> if (xdevice_list[i].use == IsXExtensionDevice) ||
     		    xdevice_list[i].use == IsXExtensionPointer) {


First, you forgot to enclose that in code tags (see [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code) for more info) as that would make it much more readable in the forums.

But the problem is now lying in the extra close bracket on line 462.  Instead of reading like: ```
if (xdevice_list[i].use == IsXExtensionDevice) ||
``` it should read like: ```
if (xdevice_list[i].use == IsXExtensionDevice ||
``` notice the difference?

---

### Post by bigdee973 on 2008-07-04
> **Stochastic said:**
> First, you forgot to enclose that in code tags (see [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code) for more info) as that would make it much more readable in the forums.

But the problem is now lying in the extra close bracket on line 462.  Instead of reading like: ```
if (xdevice_list[i].use == IsXExtensionDevice) ||
``` it should read like: ```
if (xdevice_list[i].use == IsXExtensionDevice ||
``` notice the difference?

wow how dumb of me i cant beleive i didnt even see that.  thanks i got it to work expresskeys works like a charm with all the buttons functioning.  thanks for all ur help now all i have to do is make the expresskeys work where its most important and thats in gimp. by default the expresskeys wont function without the some modification.  i read what u have to do but i lost the link hopefully i find it thank u.

---

