---
title: "Google Gadgets for Linux released"
date: 2008-06-04
forum: The Cafe
---

### Post by Wobedraggled on 2008-06-04
[http://code.google.com/p/google-gadgets-for-linux/]("http://code.google.com/p/google-gadgets-for-linux/")

Great news.

:KS

---

### Post by klange on 2008-06-04
No, no, no!
This is why we have the Gadget -> Screenlet conversion tool!

---

### Post by Wobedraggled on 2008-06-04
> **WindowsSucks said:**
> No, no, no!
This is why we have the Gadget -> Screenlet conversion tool!

what? who? what?

Where?

---

### Post by Joeb454 on 2008-06-04
I don't see the fascination with gadgets, I never find a real use for them

---

### Post by KingTermite on 2008-06-04
> **Wobedraggled said:**
> [http://code.google.com/p/google-gadgets-for-linux/]("http://code.google.com/p/google-gadgets-for-linux/")

Great news.

:KS

kewl

---

### Post by FFighter on 2008-06-04
Oh, finally. Thanks for leting us know.

---

### Post by geoken on 2008-06-04
> **Joeb454 said:**
> I don't see the fascination with gadgets, I never find a real use for them

Same here.

Even in situations where I considered the functionality of a gadget/widget to be desirable, I never understood how running it as a gadget was better than running it as a regular app or panel applet.

---

### Post by FFighter on 2008-06-04
> Same here.

Even in situations where I considered the functionality of a gadget/widget to be desirable, I never understood how running it as a gadget was better than running it as a regular app or panel applet.


Technically yes, and it usually better to run a regular panel applet as it will probably have a better integration with the underlying system (talking about Gnome here). But gadgets are cross-platform and if the functionality you want only exists as a google gadget then, what do you do?

OT: Hey Wobedraggled, I really like you avatar :D

---

### Post by bufsabre666 on 2008-06-04
compiling as we speak, ive been waiting for this, screenlets suck

@windowssucks

you want to explain this gadget to screenlet thing then

---

### Post by NTolerance on 2008-06-04
> **WindowsSucks said:**
> No, no, no!
This is why we have the Gadget -> Screenlet conversion tool!

If this Google Gadgets Linux version works at all like the Windows version it will be far superior to Screenlets.  Screenlets is still early in development and is sluggish and buggy.  Left-clicking on screenlets rarely gives you any sort of options other than to move the screenlet.  Google Sidebar also works like a sidebar *should*, unlike the very early sidebar included with Screenlets.

---

### Post by klange on 2008-06-04
> **bufsabre666 said:**
> compiling as we speak, ive been waiting for this, screenlets suck

@windowssucks

you want to explain this gadget to screenlet thing then
It's been built in to Screenlets Manager since 0.1. Install -> Convert Web Widget.

---

### Post by srinath_man on 2008-06-04
I still miss Window Maker ...

---

### Post by Wobedraggled on 2008-06-04
> **srinath_man said:**
> I still miss Window Maker ...


and I miss workbench, but we all gotta move on ;)

---

### Post by kernelhaxor on 2008-06-04
Download link:
[http://code.google.com/p/google-gadgets-for-linux/](http://code.google.com/p/google-gadgets-for-linux/)

Google also has opened up the code base here: [http://code.google.com/p/google-gadgets-for-linux/source/browse](http://code.google.com/p/google-gadgets-for-linux/source/browse)
 if one wants to customize or create new apps ..

---

### Post by tbroderick on 2008-06-04
> **kernelhaxor said:**
> Download link:
[http://desktop.google.com/linux/](http://desktop.google.com/linux/)



That's Google Desktop. It's been out for a couple years now. They just released Google Gadgets. 

[http://code.google.com/p/google-gadgets-for-linux/](http://code.google.com/p/google-gadgets-for-linux/)

---

### Post by FuturePilot on 2008-06-04
Awesome, we've got gadgets now :guitar:

---

### Post by kernelhaxor on 2008-06-04
> **tbroderick said:**
> That's Google Desktop. It's been out for a couple years now. They just released Google Gadgets. 

[http://code.google.com/p/google-gadgets-for-linux/](http://code.google.com/p/google-gadgets-for-linux/)

Ah sorry .. 
Thanks for the link.  Corrected my post.

---

### Post by NTolerance on 2008-06-04
Here's a hacky how-to that works on my system.  Do this at your own risk.  I hope this works on a stock Hardy i386 install.  

1.  Install dependencies (I didn't test these one-by-one, some may not be necessary)
```
sudo apt-get install linux-headers-generic build-essential autoconf automake1.9 libtool spidermonkey-bin zlib1g-dev libmozjs-dev libgstreamer-plugins-base0.10-dev libcurl3-openssl-dev libdbus-1-dev libxul-dev libgtk2.0-dev 
```

2.  Change to home directory
```
cd ~
```

3.  Download Google Gadgets source code
```
wget http://google-gadgets-for-linux.googlecode.com/files/google-gadgets-for-linux-0.9.1.tar.gz
```

4.  Extract the source code
```
tar zxvf google-gadgets-for-linux-0.9.1.tar.gz
```

5.  Change to source code directory
```
cd google-gadgets-for-linux-0.9.1
```

6.  Make directories as per Google documentation
```
mkdir -p build/debug
```

7.  Change to new directories
```
cd build/debug
```

8.  Run configure
```
../../configure
```

9.  Compile
```
make
```

10.  Install
```
sudo make install
```

11.  Solve a dependency error that crops up when you try to run it (note:  you may be required to run this command every time you reboot.  Put this and step 12 in a shell script if you want automation.  If anyone knows how to make this change permanent, please let me know.)  Update:  cookieofdoom offers another solution [here](http://ubuntuforums.org/showpost.php?p=5125000&postcount=59).
```
export LD_LIBRARY_PATH=/usr/local/lib
```

12.  Run in sidebar mode (my preferred method)
```
/usr/local/bin/ggl-gtk -s -bg
```
  
Let me know if this works for anyone on Ubuntu Hardy.  I tried building a DEB via checkinstall but it failed.  Maybe that's why Google didn't provide their own.  I seem to remember that Google Desktop for Linux had a prebuilt DEB available when it came out.

---

### Post by NTolerance on 2008-06-04
> **Joeb454 said:**
> I don't see the fascination with gadgets, I never find a real use for them

> **geoken said:**
> Same here.

Even in situations where I considered the functionality of a gadget/widget to be desirable, I never understood how running it as a gadget was better than running it as a regular app or panel applet.

IMHO gadgets become useful when they're part of a sidebar on a widescreen monitor.  None of this widget-layer via F12 key business like OSX has.  Modern GUIs have yet to make good use of widescreen real estate, so why not use that extra space to put semi-realtime information about happenings on the internets and on your PC?  Not to mention tiny applications for say, connecting to remote desktop servers, displaying your XBox Gamertag, calendar, note-taking, slideshow, system monitoring, RSS etc...

Speaking of RSS, Gadgets are basically like a visual version of RSS, only more powerful because they can display virtually any kind of information.  Instead of constantly going back to weather.com to see how warm it is outside you can have the forecast always on your desktop and always being automatically updated.  Yes, there are Gnome applets that have some of this functionality, but the Gnome panels lack configuration options and there really aren't that many Gnome applets available.

---

### Post by Silpheed2K on 2008-06-04
Never trust google at all... they do lots of things that aren't trustworthy and have lots of privacy issue with their customer's information
[http://www.theglobeandmail.com/servlet/story/RTGAM.20080324.wrgoogle24/BNStory/Technology/home](http://www.theglobeandmail.com/servlet/story/RTGAM.20080324.wrgoogle24/BNStory/Technology/home)

I wouldn't let them on my computer if my life depended on it... yet i know Firefox is affiliated with google... dang them.
[http://www.theregister.co.uk/2008/05/19/firefox_data_snoop/](http://www.theregister.co.uk/2008/05/19/firefox_data_snoop/)

---

### Post by gameryoshi600 on 2008-06-04
> **bufsabre666 said:**
> compiling as we speak, ive been waiting for this, screenlets suck

@windowssucks

you want to explain this gadget to screenlet thing then
I agree screenlets do suck it lags when i log in

---

### Post by madjr on 2008-06-04
yay this so cool

[IMG]http://google-gadgets-for-linux.googlecode.com/svn/images/ggl-standalone.jpg[/IMG]

[IMG]http://google-gadgets-for-linux.googlecode.com/svn/images/ggl-sidebar.jpg[/IMG]

i've been wanting this ever since i left XP

i think i saw this working in the **google android** demonstration video

---

### Post by spupy on 2008-06-04
What are its dependencies? I hope it doesn't require compositing...

---

### Post by jrusso2 on 2008-06-04
The Windows one's really slow down my computer.  Not sure I want them on Linux.  Have to see how they turn out when they are further along.  At least google is trying.

---

### Post by Mateo on 2008-06-04
eh, never got desktop applets.  plus we already have several other programs that do the same thing.

---

### Post by klange on 2008-06-04
> **Mateo said:**
> eh, never got desktop applets.  plus we already have several other programs that do the same thing.
And as I said in the other thread on the subject, one that will load Google Gadgets into its own framework...

**e**: Which is now this thread...

---

### Post by K.Mandla on 2008-06-04
Similar threads merged.

---

### Post by fdmille on 2008-06-04
> **NTolerance said:**
> Here's a hacky how-to that works on my system.  Do this at your own risk.  I hope this works on a stock Hardy i386 install.  

1.  Install dependencies (I didn't test these one-by-one, some may not be necessary)
```
sudo apt-get install linux-headers-generic build-essential autoconf automake1.9 libtool spidermonkey-bin zlib1g-dev libmozjs-dev libgstreamer-plugins-base0.10-dev libcurl3-openssl-dev libdbus-1-dev libxul-dev libgtk2.0-dev 
```

2.  Change to home directory
```
cd ~
```

3.  Download Google Gadgets source code
```
wget http://google-gadgets-for-linux.googlecode.com/files/google-gadgets-for-linux-0.9.1.tar.gz
```

4.  Extract the source code
```
tar zxvf google-gadgets-for-linux-0.9.1.tar.gz
```

5.  Change to source code directory
```
cd google-gadgets-for-linux-0.9.1
```

6.  Make directories as per Google documentation
```
mkdir -p build/debug
```

7.  Change to new directories
```
cd build/debug
```

8.  Run configure
```
../../configure
```

9.  Compile
```
make
```

10.  Install
```
sudo make install
```

11.  Solve a dependency error that crops up when you try to run it
```
export LD_LIBRARY_PATH=/usr/local/lib
```

12.  Run in sidebar mode (my preferred method)
```
/usr/local/bin/ggl-gtk -s -bg
```
  
Let me know if this works for anyone on Ubuntu Hardy.  I tried building a DEB via checkinstall but it failed.  Maybe that's why Google didn't provide their own.  I seem to remember that Google Desktop for Linux had a prebuilt DEB available when it came out.

Worked for me on a AMD64 UBUNTU HARDY 8.04.  Followed NTolerance's procedures exactly as written.

Thanks! :)

---

### Post by NTolerance on 2008-06-04
> **fdmille said:**
> Worked for me on a AMD64 UBUNTU HARDY 8.04.  Followed NTolerance's procedures exactly as written.

Thanks! :)

I'm glad to hear it, especially considering that you're running AMD64 and the how-to is based off my i386 system.

At any rate, I have two main issues with the program itself.  If you put it into true sidebar mode (always on top), it duplicates itself across all your virtual desktops (not desired).  If you set it to regular mode it only appears on one virtual desktop but space is not reserved and any maximized window will cover it up. 

The other issue which is a bigger deal is that this version can only run a small subset of the Gadgets that you get with the Windows version.  Are some of the Gadgets Windows specific or will compatibility improve in the future?

---

### Post by AZX3RIC on 2008-06-04
Works perfectly on Hardy i386

...and I'm a noob.

Excellent tutorial, thank you.

---

### Post by victorgreen on 2008-06-04
Thanks for the stuff, but on make, it gives me this infinite loop of jumbled junk:

>  -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" 		   -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" 		   -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" 		   -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 		     -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1  -O2 -Werror -Wall -Wconversion  -MT libggadget-1.0_la-main_loop.lo -MD -MP -MF .deps/libggadget-1.0_la-main_loop.Tpo -c -o libggadget-1.0_la-main_loop.lo `test -f 'main_loop.cc' || echo '../../../ggadget/'`main_loop.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-main_loop.lo -MD -MP -MF .deps/libggadget-1.0_la-main_loop.Tpo -c ../../../ggadget/main_loop.cc  -fPIC -DPIC -o .libs/libggadget-1.0_la-main_loop.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-main_loop.lo -MD -MP -MF .deps/libggadget-1.0_la-main_loop.Tpo -c ../../../ggadget/main_loop.cc -o libggadget-1.0_la-main_loop.o >/dev/null 2>&1
mv -f .deps/libggadget-1.0_la-main_loop.Tpo .deps/libggadget-1.0_la-main_loop.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS 		   -DNDEBUG 		   -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\"    -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" 		   -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" 		   -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" 		   -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 		     -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1  -O2 -Werror -Wall -Wconversion  -MT libggadget-1.0_la-math_utils.lo -MD -MP -MF .deps/libggadget-1.0_la-math_utils.Tpo -c -o libggadget-1.0_la-math_utils.lo `test -f 'math_utils.cc' || echo '../../../ggadget/'`math_utils.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-math_utils.lo -MD -MP -MF .deps/libggadget-1.0_la-math_utils.Tpo -c ../../../ggadget/math_utils.cc  -fPIC -DPIC -o .libs/libggadget-1.0_la-math_utils.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-math_utils.lo -MD -MP -MF .deps/libggadget-1.0_la-math_utils.Tpo -c ../../../ggadget/math_utils.cc -o libggadget-1.0_la-math_utils.o >/dev/null 2>&1
mv -f .deps/libggadget-1.0_la-math_utils.Tpo .deps/libggadget-1.0_la-math_utils.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS 		   -DNDEBUG 		   -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\"    -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" 		   -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" 		   -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" 		   -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 		     -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1  -O2 -Werror -Wall -Wconversion  -MT libggadget-1.0_la-mediaplayer_element_base.lo -MD -MP -MF .deps/libggadget-1.0_la-mediaplayer_element_base.Tpo -c -o libggadget-1.0_la-mediaplayer_element_base.lo `test -f 'mediaplayer_element_base.cc' || echo '../../../ggadget/'`mediaplayer_element_base.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-mediaplayer_element_base.lo -MD -MP -MF .deps/libggadget-1.0_la-mediaplayer_element_base.Tpo -c ../../../ggadget/mediaplayer_element_base.cc  -fPIC -DPIC -o .libs/libggadget-1.0_la-mediaplayer_element_base.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-mediaplayer_element_base.lo -MD -MP -MF .deps/libggadget-1.0_la-mediaplayer_element_base.Tpo -c ../../../ggadget/mediaplayer_element_base.cc -o libggadget-1.0_la-mediaplayer_element_base.o >/dev/null 2>&1
mv -f .deps/libggadget-1.0_la-mediaplayer_element_base.Tpo .deps/libggadget-1.0_la-mediaplayer_element_base.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS 		   -DNDEBUG 		   -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\"    -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" 		   -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" 		   -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" 		   -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 		     -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1  -O2 -Werror -Wall -Wconversion  -MT libggadget-1.0_la-memory_options.lo -MD -MP -MF .deps/libggadget-1.0_la-memory_options.Tpo -c -o libggadget-1.0_la-memory_options.lo `test -f 'memory_options.cc' || echo '../../../ggadget/'`memory_options.cc
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-memory_options.lo -MD -MP -MF .deps/libggadget-1.0_la-memory_options.Tpo -c ../../../ggadget/memory_options.cc  -fPIC -DPIC -o .libs/libggadget-1.0_la-memory_options.o
 g++ -DHAVE_CONFIG_H -I. -I.. -I../../../ggadget -I.. -I../../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner\" -DHAVE_PTHREAD=1 -O2 -Werror -Wall -Wconversion -MT libggadget-1.0_la-memory_options.lo -MD -MP -MF .deps/libggadget-1.0_la-memory_options.Tpo -c ../../../ggadget/memory_options.cc -o libggadget-1.0_la-memory_options.o >/dev/null 2>&1


What can I do?

---

### Post by bufsabre666 on 2008-06-04
> **victorgreen said:**
> Thanks for the stuff, but on make, it gives me this infinite loop of jumbled junk:



What can I do?

wait cause thats what make looks like, it takes forever but gadgets rock

---

### Post by victorgreen on 2008-06-04
I was being retarded, just left it compiling for roughly a half hour and it worked fine. Thanks to the instructions on this forum Im now happily running the gadgets on Hardy64.

---

### Post by swoll1980 on 2008-06-04
> **Joeb454 said:**
> I don't see the fascination with gadgets, I never find a real use for them

You mean you've honestly never been sitting there, and had the sudden urge to suck up all your resources on some dumb crap? I think your fibbing

---

### Post by victorgreen on 2008-06-04
I must say Im underwhelmed. Its a bit clunky, the various gadgets don't let you resize them correctly to be placed around the desktop and I see no way to have them fade in and out like such things do on OSX. Im sure its possible though. 

Honestly the functionality you can get out of most the gadgets is already present through gnome panel apps- weather, clocks, system monitoring, searches, etc

---

### Post by Mazza558 on 2008-06-05
[http://news.softpedia.com/news/Google-Gadgets-on-Your-Linux-Desktop-87254.shtml]("http://news.softpedia.com/news/Google-Gadgets-on-Your-Linux-Desktop-87254.shtml")

Google have improved Google Desktop on linux to allow you to use Google Gadgets on it. Sure, we already have Screenlets, but google gadgets has a much wider variety of widgets.

---

### Post by Islington on 2008-06-05
Screenlets can already use google gadgets, cant they?

---

### Post by Mazza558 on 2008-06-05
> **Islington said:**
> Screenlets can already use google gadgets, cant they?

I don't think so.

---

### Post by Tomatz on 2008-06-05
> **Mazza558 said:**
> [http://news.softpedia.com/news/Google-Gadgets-on-Your-Linux-Desktop-87254.shtml]("http://news.softpedia.com/news/Google-Gadgets-on-Your-Linux-Desktop-87254.shtml")

Google have improved Google Desktop on linux to allow you to use Google Gadgets on it. Sure, we already have Screenlets, but google gadgets has a much wider variety of widgets.


Cheers big ears!

Thanks for the info ;)

---

### Post by Xanatos Craven on 2008-06-05
[http://www.screenlets.org/index.php/Google_gadgets_now_run_on_Screenlets_engine_](http://www.screenlets.org/index.php/Google_gadgets_now_run_on_Screenlets_engine_)...

Dunno how stable or easy to use it is currently, but the functionality is there in some form.

---

### Post by aDRENOcHROME on 2008-06-05
> **NTolerance said:**
> Let me know if this works for anyone on Ubuntu Hardy.  I tried building a DEB via checkinstall but it failed.  Maybe that's why Google didn't provide their own.  I seem to remember that Google Desktop for Linux had a prebuilt DEB available when it came out.

Checkinstall will work if you create the following directories by hand:

```
sudo mkdir /usr/local/lib/google-gadgets/
sudo mkdir /usr/local/lib/google-gadgets/modules
sudo mkdir /usr/local/share/google-gadgets/
sudo mkdir /usr/local/share/google-gadgets/google-gadget-browser/
```

So far GG runs, but i can't add new gadgets because 'Add gadgets' does nothing.

---

### Post by hanzomon4 on 2008-06-05
Gnome will never have the level of gadgetry OSX, Windows, or KDE-4 has until it provides a way for these things to be integrated into the desktop.

---

### Post by Jeztastic on 2008-06-05
Great news. I've been running Desklets, but they are so buggy. I've not found a gadgets app for Linux that wasn't buggy yet. It's the only thing I like about Vista - the widgets are rock solid. I'll try this as soon as I get the chance. Thanks for the how to.

---

### Post by Mazza558 on 2008-06-05
"Failed to update gadget data. Please try again later." :(

---

### Post by aaaantoine on 2008-06-05
> **hanzomon4 said:**
> Gnome will never have the level of gadgetry OSX, Windows, or KDE-4 has until it provides a way for these things to be integrated into the desktop.

Integrated in what way, exactly?  You mean installed by default?

---

### Post by rmstone1s on 2008-06-05
> **Mazza558 said:**
> "Failed to update gadget data. Please try again later." :(

Yes I get that too now... but man i have the coolest blank black box in my sidebar ever...

Any figures out the failed to update gadget data let me know... until then this thing is a useless box

-Randy

---

### Post by Mazza558 on 2008-06-05
> **rmstone1s said:**
> 

Any figures out the failed to update gadget data let me know... until then this thing is a useless box


Still, the box is a VERY COOL box.

---

### Post by eragon100 on 2008-06-05
YESS!!! I have wanted this ever since I left XP, especially the flower! :KS

---

### Post by MemoryDump on 2008-06-05
> **NTolerance said:**
> 
11.  Solve a dependency error that crops up when you try to run it
```
export LD_LIBRARY_PATH=/usr/local/lib
```


does this have to be done every time you restart the computer?

---

### Post by Islington on 2008-06-05
> **Mazza558 said:**
> I don't think so.

looked it up, you can convert web windgets.

---

### Post by Mazza558 on 2008-06-05
> **MemoryDump said:**
> does this have to be done every time you restart the computer?

Every time you want to run it - at least for me.

---

### Post by notwen on 2008-06-05
[http://ubuntuforums.org/showthread.php?t=818267](http://ubuntuforums.org/showthread.php?t=818267)

---

### Post by Mazza558 on 2008-06-05
> **notwen said:**
> [http://ubuntuforums.org/showthread.php?t=818267](http://ubuntuforums.org/showthread.php?t=818267)

Yeah, I noticed it almost as soon as I'd posted it.

---

### Post by Brunellus on 2008-06-05
Threads merged.

---

### Post by hanzomon4 on 2008-06-05
> **aaaantoine said:**
> Integrated in what way, exactly?  You mean installed by default?

No, I just mean like a dashboard, sidebar type thing. Something that would allow gnome to handle them as gadgets and not just another application. Like a widget class or something that defines how such objects should be handled? I don't know I just love how in osx my google gadgets know to go straight to the dashboard.

---

### Post by NTolerance on 2008-06-05
> **MemoryDump said:**
> does this have to be done every time you restart the computer?

Seems like I rebooted and didn't need to run the command again.  YMMV.  How-to updated to reflect this scenario.

---

### Post by cookieofdoom on 2008-06-05
I think you can just put ```
export LD_LIBRARY_PATH=/usr/local/lib
``` in your .bashrc but since I don't have the problem you guys are talking about, I'm not sure.

Also: to make windows stick to the desktop (IE, be on all desktops) in Compiz turn on the "window rules" plugin and put ```
class=Ggl-gtk
``` in the sticky section. Put it in Below to make them stay below. :)

As a general note to get window information (like class, title, etc.) type xprop in a terminal and then click on the the window in question. All you need  -- and far more than you ever wanted -- to know will be right there.:guitar:

---

### Post by dmrx24 on 2008-06-05
How do I make it startup with .bashrc ?

---

### Post by cookieofdoom on 2008-06-05
> **dmrx24 said:**
> How do I make it startup with .bashrc ?

To make the program start on Ubuntu startup you should put an entry in System-->Preferences-->Sessions. Create a new entry (click Add), type in a name (like google gadgets) then put ggl-gtk in the Command field. They should now launch on startup.

If you're having the above dependency issue you can put "export LD_LIBRARY_PATH=/usr/local/lib" in your /etc/environment file. This is probably better than your .bashrc as this should apply to other accounts as well and gets applied earlier in the startup process.

Open a terminal and type ```
gksu gedit /etc/environment
``` a text editor will come up. Create a new line after everything that's already there and then add ```
export LD_LIBRARY_PATH=/usr/local/lib
``` to the end of the file (on a new line).

**If you're not sure what you're doing you might be best off typing **```
sudo cp /etc/environment /etc/environment.backup
``` before you start. If you mess up you can restore the old file by typing ```
sudo cp /etc/environment.backup /etc/environment
```

Have fun!

---

### Post by rmstone1s on 2008-06-05
Anyone eles with the "failed to update gadget data please try again later" error?

---

### Post by indigoparadox on 2008-06-05
Regarding the inability to "update gadget data":

I found [this issue]("http://code.google.com/p/google-gadgets-for-linux/issues/detail?id=104") on the Google Code issue tracker which seems to be relevant.

Comment number 8 in that thread states:
> It works on Ubuntu when you install libcurl4-openssl-dev instead of
libcurl4-gnutls-dev before compilation.
Supposedly that works for other people, but not for me. 

I had libcurl4-openssl-dev installed from the beginning, but I also have libcurl3-gnutls-dev. My guess is that Google Gadgets is using libcurl3 rather than libcurl4, or something like that. I tried removing libcurl3-gnutls in favor of libcurl3-openssl, but it seems a lot of things on my system depend on it so it doesn't seem like I can (or should).

I'm running 7.10, though apparently my package management skills are weak. If anybody can see some kind of solution that I'm missing, that would be wonderful.

---

### Post by DeadSuperHero on 2008-06-06
Looks like the Plasma team's already working on integrating Google Gadgets into it.
Sweeeet....

---

### Post by GeneralZod on 2008-06-06
> **Mr. Psychopath said:**
> Looks like the Plasma team's already working on integrating Google Gadgets into it.
Sweeeet....

Link for those interested:

[http://aseigo.blogspot.com/2008/06/google-gadgets.html](http://aseigo.blogspot.com/2008/06/google-gadgets.html)

In fact, even better - one of the GGL developers might end up doing it themselves!

[http://groups.google.com/group/google-gadgets-for-linux-dev/browse_thread/thread/b695a1ade6a0d302](http://groups.google.com/group/google-gadgets-for-linux-dev/browse_thread/thread/b695a1ade6a0d302)

---

### Post by seenxu on 2008-06-06
> **cookieofdoom said:**
> To make the program start on Ubuntu startup you should put an entry in System-->Preferences-->Sessions. Create a new entry (click Add), type in a name (like google gadgets) then put ggl-gtk in the Command field. They should now launch on startup.

If you're having the above dependency issue you can put "export LD_LIBRARY_PATH=/usr/local/lib" in your /etc/environment file. This is probably better than your .bashrc as this should apply to other accounts as well and gets applied earlier in the startup process.

Open a terminal and type ```
gksu gedit /etc/environment
``` a text editor will come up. Create a new line after everything that's already there and then add ```
export LD_LIBRARY_PATH=/usr/local/lib
``` to the end of the file (on a new line).

**If you're not sure what you're doing you might be best off typing **```
sudo cp /etc/environment /etc/environment.backup
``` before you start. If you mess up you can restore the old file by typing ```
sudo cp /etc/environment.backup /etc/environment
```

Have fun!

this ain't work for me, have to add this line to .bashrc

---

### Post by cookieofdoom on 2008-06-06
> **seenxu said:**
> this ain't work for me, have to add this line to .bashrc

I forgot to mention, it would require one reboot (or possibly an ldconfig?). From that point on it should work... or I could be completely crazy.

---

### Post by DM was on fire! on 2008-06-06
Am I lucky enough that these will work with 6.06.1?
I love the whole widgets/gadgets/screenlets thing, but Screenlets, as far as I know, doesn't work on 6.06.1 (or I'm too stupid to realise how to install it).

But this is totally awesome. I love it. <3

---

### Post by spraveenitpro on 2008-06-06
Is there a shortcut to hide the google gadgets on hardy?

Praveen.

:guitar:

---

### Post by Nomis on 2008-06-06
There is a .deb file at [https://launchpad.net/~googlegadgets]("https://launchpad.net/~googlegadgets")
Works for me on Ubuntu 8.04

---

### Post by Killerah on 2008-06-06
I installed with the deb from that repo, but alas, all that happens when I start up ggl-gtk is that my cpu goes up to 100% usage and the program never starts. Bummer.

---

### Post by FyreBrand on 2008-06-06
> **GeneralZod said:**
> Link for those interested:

[http://aseigo.blogspot.com/2008/06/google-gadgets.html](http://aseigo.blogspot.com/2008/06/google-gadgets.html)

In fact, even better - one of the GGL developers might end up doing it themselves!

[http://groups.google.com/group/google-gadgets-for-linux-dev/browse_thread/thread/b695a1ade6a0d302](http://groups.google.com/group/google-gadgets-for-linux-dev/browse_thread/thread/b695a1ade6a0d302)
Now that's some interesting stuff there.  I like it when developers from different teams start thinking about integration possibilities.  It's exciting.

---

### Post by suzhe on 2008-06-07
Just want you know that Google Gadgets for Linux 0.9.2 has been released, which fixed most of the issues related to compilation. The requirement of curl+openssl is also removed.

And btw, there are two types of Google Gadgets:
iGoogle Gadgets, which are written in HTML/JavaScript and typically run on your iGoogle home page.
Google Desktop Gadgets, which are small files with .gg suffix and typically run in Google Desktop.

Google Gadgets for Linux supports both of them.

---

### Post by indigoparadox on 2008-06-07
I've downloaded, compiled, and installed 0.9.2, but I'm still having problems with Ubuntu 7.10. When I try to add a gadget now, I still get the error updating gadget data. If I then close the add window and try to add a gadget again, the "add" window simply says "Updating gadget data... Please wait," and hangs indefinitely. I let it sit for ten minutes a couple times and nothing happened.

The log in the console window reports:
> Call DBusWatchCallBack, watch id: 6
Not a regular file: /
Initialize gadget_browser_script_utils extension.
Register default_framework extension.
Register gtk_edit_element extension.
Register gst_mediaplayer_element extension.
Register gtk_system_framework extension.
Register gst_audio_framework extension.
Register linux_system_framework extension.
Register ggadget_browser_script_utils extension.
TRACE: begin loading metadata
Call DBusWatchCallBack, watch id: 6

"Call DBusWatchCallBack, watch id: 6" is repeated over and over.

The interface is looking better and better, though. When it can actually load gadgets, it seems like it'll be pretty sweet.

---

### Post by fjf on 2008-06-07
You can try this method:  [http://ubuntuforums.org/showthread.php?t=821478&highlight=google+gadgets](http://ubuntuforums.org/showthread.php?t=821478&highlight=google+gadgets)

---

### Post by indigoparadox on 2008-06-07
> **fjf said:**
> You can try this method:  [http://ubuntuforums.org/showthread.php?t=821478&highlight=google+gadgets](http://ubuntuforums.org/showthread.php?t=821478&highlight=google+gadgets)

Unfortunately, they don't seem to have a repository for 7.10 (Gutsy). Trying to use the 8.04 repository causes the system to claim I have unfillable dependencies.

:(

---

### Post by indigoparadox on 2008-06-08
If anyone else is still having problems fetching the list of gadgets on Gutsy, I managed to solve the problem (sort of) by building the QT version instead of the GTK version. The dependencies are a little different:

```
sudo apt-get install libcurl4-gnutls-dev libqt4-dev libqtwebkit-dev
```

It's also a lot buggier, with a mis-matched interface and with more graphical glitches and without the nice sidebar the GTK version seems to have. It does work, however, and quite acceptably so for the stage of development it's in.

Still, I can't wait until it's a bit more polished. :)

---

