---
title: "How to install Hugin, Panoramic Tools and Enblend"
date: 2006-09-24
forum: Tutorials
---

### Post by DoorGunner on 2006-09-24
Hi

This is something of a "How to" to for a panoramic stitcher program.

Have collected this from several sourses of materiels mainly from ubuntu and SuSE sources with a bit of Gentoo know how. 

This should be handy to make some Skydome pics for your xgl and compiz setups.

---------------------------------------------------------------------------
PART I
DownLoad the latest "tar.gz" to Desktop the latest Source files from:

libpano
[http://sourceforge.net/projects/panotools](http://sourceforge.net/projects/panotools)

Hugin
[http://sourceforge.net/projects/hugin](http://sourceforge.net/projects/hugin)

Enblend
[http://sourceforge.net/projects/enblend](http://sourceforge.net/projects/enblend)

------------------------------------------------------------------------
PART II
Preparation of Ubuntu

These will satisfy the dependancies required for the programs being installed.

for pano dependancies
$sudo apt-get install mono libicu34 libglade-cil libgtk-cil libglib-cil libgdiplus libglut3-dev libglew-dev liplot2c2 libplot-dev libplot-perl


[http://mirrors.usc.edu/pub/gnu/libxmi/](http://mirrors.usc.edu/pub/gnu/libxmi/) and download libxmi-1.2 extract this package to your desktop the enter the following codes
file.pngCode:

$cd ~/libxmi-1.2 
$sudo ./configure 
$sudo make 
$sudo make install


for JPEG dependancies
$ sudo apt-get install libjpeg62-dev
$ sudo apt-get install libpng-dev
$ sudo apt-get install libtiff4-dev

for compiling
$ sudo apt-get install libtool autoconf automake1.7

wxGTK stuff and boost tools
$ sudo apt-get install libwxgtk2.6-dev wx-common libboost-{graph,thread}-dev libgtk2.0-dev g++

-----------------------------------------------------------------------
PART III
Compiling the source code

Open the 3 files main folders that were downloaded in PART I to your desktop. I personally just click on the "tar.gz" files and use extract. you can choose any method that works for you.

Install libpano first 

$ cd /home/Your_Name/Desktop/libpano12-2.8.4
 the version i got was libpano12-2.8.4 you put what ever you need there

libpano12-2.8-4$ sudo ./configure
libpano12-2.8-4$ sudo make
libpano12-2.8-4$ sudo make install

Install Hugin second (this one takes a while)
 
cd /home/john/Desktop/hugin-0.7_3beta 
sudo ./configure 
sudo make sudo make install

Install Enblend next

$ cd /home/john/Desktop/enblend-3.0
enblend-2.5$ sudo ./configure
enblend-2.5$ sudo make
enblend-2.5$ sudo make install

---------------------------------------------------------------------------

Congratulations everything should have installed for you.

you just need to Control+Alt+BackSpace and log back in

I use KDE and found the Icon under graphics>Hugin Panorama Creator (Panorama Stitcher)

Enjoy

---

### Post by tjansson on 2006-10-02
Thanks for the guide - it was short and concise. A shame though that hugin isn't a part of multi- or uni-verse. My small laptop (1200MHz scaled to 800MHz) isn't really made for compiling grafical programs. :D

---

### Post by CeeDub on 2006-10-13
When I run the
"sudo make" on the hugin part it runs for a bit and then I get this error:

> checking for boostlib >= 1.31... no (0)
configure: error:
        the boost headers must be installed on your system
        but configure could not find it. Use --with-boost to
        specify the location of the boost library and
        --with-boost-version to specify your version

---

### Post by DoorGunner on 2006-10-13
redo the instructions from part II for wxGTK stuff and boost tools

$ sudo apt-get install libwxgtk2.6-dev wx-common libboost-{graph,thread}-dev libgtk2.0-dev g++

---

### Post by DoorGunner on 2006-10-13
oops

---

### Post by pitrowech on 2006-10-31
Hello, DoorGunner

fisrt of all - thanks for the guide

i have a problem: ./configure hugin returns:

```
checking pano12/queryfeature.h presence... yes
checking for pano12/queryfeature.h... yes
panotools query functions enabled
checking for fcnPano in -lpano12... yes
checking for execute_stack_new in -lpano12... no
checking if Panotools package is complete... no -- libpano12 version 2.8.1 or later is required
configure: error:
        the panorama tools library must be installed on your system
        but configure could not find it. Use --with-pano to
        specify the location of the panotools library
```

do you know how to fix this?

---

### Post by DoorGunner on 2006-10-31
Im looking at this line of your error

> configure: error:
        the panorama tools library must be installed on your system
        but configure could not find it. Use --with-pano to
        specify the location of the panotools library

check to see if you have /usr/local/lib/libpano12.so 

You may have to re-download the lib and reinstall it. Then try hugin again. 

It is kind of strange for the rest of the ./configure it seems to see it.

---

### Post by midorigin on 2006-11-06
> **tjansson said:**
> Thanks for the guide - it was short and concise. A shame though that hugin isn't a part of multi- or uni-verse. My small laptop (1200MHz scaled to 800MHz) isn't really made for compiling grafical programs. :D

I can definitely sympathize with you on the laptop. Edgy on an old Latitude and it's **really** taking its time compiling.

What's the reason this isn't in a repository? Is there an actual barrier or is it simply that has no one gotten around to adding it?

---

### Post by Alexander Kirillov on 2006-11-30
Two comments:
 - to those who are asking why  hugin is not in the repositories - it has license problems. See this blog:
[http://www.figuiere.net/hub/blog/?2006/02/24/378-recent-ubuntu-uploads](http://www.figuiere.net/hub/blog/?2006/02/24/378-recent-ubuntu-uploads)

 - another set of instructions - almost identical to these ones - and a very nice tutorial on using hugin are available here: 
 [http://exolucere.ca/articles/compile-hugin-ubuntu](http://exolucere.ca/articles/compile-hugin-ubuntu)

---

### Post by bodhi.zazen on 2006-12-03
Nice How-to

This thread has been added to the UDSF wiki.

[Install_Hugin_Panoramic_Tools_and_Enblend](http://doc.gwos.org/index.php/Install_Hugin_Panoramic_Tools_and_Enblend)

If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by thalis on 2007-01-21
Hello All:)
I am new tou Ubuntu. I try to follow the direction of DoorGuner but when i am going to install libpano and give "sudo make" then i have a message command not found. Can anybody tell me why?

---

### Post by midorigin on 2007-01-21
> **thalis said:**
> Hello All:)
I am new tou Ubuntu. I try to follow the direction of DoorGuner but when i am going to install libpano and give "sudo make" then i have a message command not found. Can anybody tell me why?

By default, Ubuntu doesn't come with everything required to compile programs from source like this.
Here's what you need: [*How to install Basic Compilers (build-essential)*]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29")

---

### Post by DoorGunner on 2007-02-03
Hi guys

Please note that this site and the wiki has been updated.
[http://doc.gwos.org/index.php/Install_Hugin_Panoramic_Tools_and_Enblend](http://doc.gwos.org/index.php/Install_Hugin_Panoramic_Tools_and_Enblend)

I made changes to a particutlar section.

Jpeg dependancies. 

sudo apt-get install libjpeg62-dev 
sudo apt-get install lib-dev 
sudo apt-get install libpng-dev 
sudo apt-get install libtiff4-dev

If you tried to use the previous coding it didnt work..... :( 

If you are having or had problems with this go back and try reintalling the jpeg dependancies and everything there after should work nicely for you.

again .... sorry for the inconveniencs... :(

---

### Post by Andy17MB on 2007-02-05
Hi,

I've been struggling to get Enblend up and running.  Hugin installed fine from Synaptic and I can stitch with the Nona engine.  I am running 32bit Edgy 

I've been struggling to get the libs installed to install so I can compile enblend.  Just seen your most recent post and tried reinstalling the jpeg libs, however when i get to lib-dev i get a message "E: Couldn't Find Package li-dev".  Libjpeg62-dev installed ok.

I am also having a problem with the GTK libs in that when I run:
$ sudo apt-get install libwxgtk2.6-dev wx-common libboost-{graph,thread}-dev libgtk2.0-dev g++
I get a couldn't find package error on Libwxgtk2.6-dev

I have Universe and Multiverse repositories configured.  Any Idea where I am going wrong?

Andy Coulson

---

### Post by DoorGunner on 2007-02-05
do you have the build-essentials installed?
make sure it is installed as well.

also instead of running 
sudo apt-get install libwxgtk2.6-dev wx-common libboost-{graph,thread}-dev libgtk2.0-dev g++

try 

sudo apt-get install libwxgtk2.6-dev
sudo apt-get install wx-common
sudo apt-get install libboost-graph-dev
sudo apt-get install libboost-graph-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install g++

Let me know if this works for you....

---

### Post by Andy17MB on 2007-02-06
Thanks for the quick reply..

Well there's progress but not fixed yet.  I checked and re-installed build essentials, which reports that it's all up to date.  Re- running the Jpeg Dependences - libjpeg62-dev installed ok; lib-dev could not be found; libpng-dev returned 
"Package libpng-dev is a virtual package provided by:
 libpng12-dev 1.2.8rel-5.1ubuntu0.1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate
Libtiff4-dev was already installed

All of the GTK, WX and Boost stuff in your last reply installed ok.  I thik you may have had a typo in there - libboost-graph-dev is listed twice.  In the previous post you called libboost-thread-dev.  I have installed this too

When I run the Enblend ./configure i get warnings that the following are missing: liblcms; liblxmi, GLUT; libGLU; libGL, GLEW, and further on missing header file warnings that relate back to these. I am Assuming that this relates to the problems loading jpeg dependencies

Any suggestions

Thanks again for the help

Andy

---

### Post by DoorGunner on 2007-02-07
give this a try...

 sudo apt-get install libpng12-dev

did the tiff go in oK?


Just out of interest mine told me that i needed to choose this one or another package.

I didnt see the errors or  omissions on associated with ./enblend. However, lets try the other first and you might be right about it being a dependency.

---

### Post by Andy17MB on 2007-02-07
Ok, 

I've tried that and to summarize what has worked..
[INDENT]build essentials - installed OK[/INDENT]
[INDENT]libjpeg62-dev - installed OK[/INDENT]
[INDENT]libpng12-dev  - installed OK[/INDENT]
[INDENT]libtiff4-dev  - installed OK[/INDENT]
[INDENT]All the Libs relating to GTK, WX and Boost all Installed OK[/INDENT]

lib-dev that you listed under the jpeg dependencies earlier could not be found. 

When I run ./configure the same errors come up as before.  

I've trawled all the libraries and development libraries in synaptic and Ubuntu 6.10 doesn't seem to have the missing lib-dev.  What do you suggest?  

Thanks again for your (on-going) help

Andy

---

### Post by Falcorian on 2007-02-07
> **Andy17MB said:**
> 
When I run the Enblend ./configure i get warnings that the following are missing: liblcms; liblxmi, GLUT; libGLU; libGL, GLEW, and further on missing header file warnings that relate back to these. 

I get those missing too, but I have the JPEG dependencies... Any help would be great. Here's what comes out wrong for me:

```


configure: WARNING: liblcms is required to compile enblend.
configure: WARNING: libxmi is required to compile enblend.
configure: WARNING: GLUT is required to compile enblend.
configure: WARNING: libGLU is required to compile enblend.
configure: WARNING: GLEW is required to compile enblend.
checking for library containing opendir... none required
configure: WARNING: lcms header files are required to compile enblend.
configure: WARNING: xmi header files are required to compile enblend.
configure: WARNING: glew header files are required to compile enblend.
configure: WARNING: glut header files are required to compile enblend.


```

I went -dev hunting, and now I get only the following:

```

configure: WARNING: libxmi is required to compile enblend.
checking for library containing opendir... none required
configure: WARNING: xmi header files are required to compile enblend.

```

Everything else I was able to find with a sudo apt-get install lib{name_of_it}...

EDIT: And found libxmi is part of libplot-dev. Making now. :)

---

### Post by Andy17MB on 2007-02-07
I managed to find all of the headers and libraries except libxmi with Synaptic.  the relevant dev-libraries are:

[INDENT]libglew-dev[/INDENT]
[INDENT]liblcms-dev[/INDENT]
[INDENT]freeglut3-dev[/INDENT]

Thanks to Falcorian's pointer I found libplot-dev, but in Ubuntu 6.10 libplot2 is installed by default.  This needs to be uninstalled and replaced with liplot2c2 and libplot-dev (and libplot-perl?).  If you go through synaptic you are helped through this

Falcorian and DoorGunner - Thanks for the help

---

### Post by Andy17MB on 2007-02-07
Just when you think things are finally going ok..  

./configure runs cleanly, but when I run sudo make it gets so far and hangs here:

make[3]: Entering directory `/home/atc/enblend-3.0/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -g -O3 -ffast-math -Wall -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DENBLEND_CACHE_IMAGES -DNDEBUG -I../include -g -O2 -MT enblend-enblend.o -MD -MP -MF ".deps/enblend-enblend.Tpo" -c -o enblend-enblend.o `test -f 'enblend.cc' || echo './'`enblend.cc; \
        then mv -f ".deps/enblend-enblend.Tpo" ".deps/enblend-enblend.Po"; else rm -f ".deps/enblend-enblend.Tpo"; exit 1; fi

Any Suggestions?

---

### Post by DoorGunner on 2007-02-07
That good work

Don't let the appearance of a hang discourage you..... Just wait it out till it fails or errors out..... sometimes the compiling can take hours for programs. If you ever tried gentoo you will know what i mean. (days to compile gentoo)

I found an apt-get package for libglut3-dev and libglew-dev 
As well i goggled libxmi and found version libxmi-1.2 downloaded and installed it from there.
[http://mirrors.usc.edu/pub/gnu/libxmi/](http://mirrors.usc.edu/pub/gnu/libxmi/)


I had an error for Enblend 3 that said something to the effect that malloc was not in std and error's out at that point. However enblend 2.5 did load up. So for now im going to use enblend 2.5 until this can be worked out. 

Hugin actually works quite well. Here is a pic of my latest Hubin compilation. It is a composite of 5 photos.... not a contest winner but good to show it works. Enblend smooths out the hard join lines nicely. The photo was taken at a river near Eba in the Philippines. Went there at Christmas this year.
[IMG]http://members.shaw.ca/Doorgunner/Images/EbaRiver45.jpg[/IMG]

---

### Post by Andy17MB on 2007-02-08
DoorGunner

Thanks - I've finally got everything working.  You're right about the compilation - it hadn't hung but was just very slow. I'm getting the same results as the prebuilt windows package now.  Nicely knitted panoramas with the joins blended out.  for example this is a smaller version of a 4 image stitcher
[IMG]http://farm1.static.flickr.com/163/383552681_79f040ea2f_o.jpg[/IMG]

Time to stop playing with the computer and go and get the camera out..

Thanks again for the help

Andy

---

### Post by DoorGunner on 2007-02-08
Thanks for your help with the new updates guys. 

I amended the Wiki and Installation portion of this thread. Have a look through to see if anything was missed.

Andy have you looked into a 3d viewer yet?

---

### Post by Andy17MB on 2007-02-15
Doorgunner,

The changes look OK - I'm pretty sure you've got all of the libraries now

Not looked into 3D Viewers yet - What had you got in mind?

Andy

---

### Post by Icarosaurus on 2007-04-12
I'm using Feisty and I had to sligtly modify the Makefile for libpano12-2.8.4
I had to change the line:
```

prefix = /usr/local

```
into:
```

prefix = /usr/

```

This worked fine for me.
Without this hack hugin didn't start, looking for missing libraries...
Hope this helps someone :)

---

### Post by Andy17MB on 2008-04-20
I'm running Gutsy and Hugin updated in the Ubuntu Repositories recently to 0.7 beta 4. I'm also running Enblend 3.0.dfsg.1-0ubuntu3.  Hugin runs fine and creates the appropriately aligned TIFFs.  

I needed to change Enblend options in the enblend tab in Hugin preferences to point at enblend in /usr/local/bin, but hugin now tries to use enblend.  Enblend is stopping with the following error:
```
enblend: error while loading shared libraries: libGLEW.so.1.3: cannot open shared object file: No such file or directory
```

The version of libGLEW on my machine is 1.4.  Do I need to revert to an earlier version and if so how do I go about that?  Alternatively do I nee to rebuild enblend 
from source?

Any suggestions would be welcomed

Andy

---

### Post by Icarosaurus on 2008-04-20
As I can understand, you're trying to use an enblend version different from the default enblend installed from repositories and located in **/usr/bin**
Maybe the enblend you're trying to use is an older version, compiled for libbGLEW 1.3
The straightforward solution is to re-compile the enblend you're trying to use, so it will use the 1.4 version.
A "dirty" solution could be creating a symbolic link named 1.3 and targeting 1.4. But I'm not sure it will work..

regards

---

### Post by Andy17MB on 2008-04-28
Icarosaurus, 

Thanks for confirming my suspicions.  I did have a couple of versions of Enblend on the machine, but neither work.  I've cleared them off and reinstalled both hugin and enblend from the repositories.  Now iff I run enblend from the command line it seems happy with libGLEW but throws up the following:
```
/usr/bin/enblend: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```
If I do "whereis libGL" it returns /usr/lib/liGL.so.  So what do I need to do next - do I need to recompile and if so do i need to change something so it looks for libGL.so instead of libGL.so.1?

Thanks

Andy

---

### Post by Icarosaurus on 2008-04-28
I think libGl.so.1 should be there if you have correctly installed your video drivers.
Sometimes libGL.so is only an alias for libGL.so.1 

Check the output of 
```

ls -l /usr/lib/libGL.*

```

Mine looks like:
```

rwxrwxrwx 1 root root     10 2008-04-06 11:07 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     21 2008-04-25 17:00 /usr/lib/libGL.so.1 -> /usr/lib/libGL.so.1.2
-rw-r--r-- 1 root root 478112 2008-04-25 16:17 /usr/lib/libGL.so.1.2

```

Regards.

P.S.: You should better use "locate" instead of "whereis"

---

### Post by Andy17MB on 2008-05-12
Icarosaurus,

I've run ls and that produces:
```
lrwxrwxrwx 1 root root 10 2007-12-11 21:15 /usr/lib/libGL.so -> libGL.so.1
```
I notice that the last modified date is quite a bit older than yours.  I am running Gutsy and have kept up with all the updates. What does the "->" output mean?

Thanks Again Andy

---

### Post by Icarosaurus on 2008-05-12
The date is not a problem... I just installed my video drivers recently and I'm using Hardy.
The "->" in the output of ls means that libGL.so is in fact a symbolic link to libGL.so.1
But you don't have libGL.so.1, so the link is broken and points to nothing.
I think you messed up something in your video driver installation (libGL.* are the OpenGL libraries).
So, I think you have to check if your video drivers are well installed.

---

### Post by Andy17MB on 2008-05-13
Thanks again...

I have had problems with the Nvidia driver so have defaulted back to the NV driver which has not give me any problems until now.  I think It may be time for a clean install - looks like I'm going to be upgrading to Hardy then..  I will report back if I fix this just to close off the query

---

### Post by Andy17MB on 2008-06-02
I've done a clean install of Hardy with the closed NVidia Driver.  This has fixed the Enblend problem I was having.  Thanks again Icarosaurus for your patience and help

Andy

---

### Post by Calimo on 2009-06-21
Hi there,

I'm having some difficulties installing libxmi (intrepid 64bits).

I downloaded version 1.2 from GNU website.
tar -xvzf libxmi-1.2.tar.gz
cd libxmi-1.2/
./configure

And it ends with an error: 
```

[...]
checking for working makeinfo... missing
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
[...]
checking whether ln -s works... yes
updating cache ./config.cache
loading cache ./config.cache within ltconfig
ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed
```
I tried adding a --host argument to ./configure
```

./configure amd64
./configure host=x86_64-linux-gnu
./configure --host=x86_64
```but each time a get an error like:
```
checking host system type... Invalid configuration `amd64': machine `amd64' not recognized
```Where can I find the correct line for my machine?

What should I do to get it working?

Thanks!

---

### Post by Calimo on 2009-08-29
Libxmi doesn't compile under x64 Intrepid
It took me ages to understand, but libxmi is included in libplot, so installing libplot-dev is enough to get enblend-enfuse to compile!

---

### Post by mikecalder on 2009-09-24
I want to install hugin without mono; I'm running Jaunty AMD64.  I've been told that the only mono dependency is autopano-sift, and I've found and installed autopano-sift-c, which is the C port.

Unfortunately, when I then try to install hugin, synaptic and apt both indicate that to continue would uninstall autopano-sift-c and install the C# version, and then of course go on to pull in all the mono stuff.

Has anyone managed to get round this, or can give me some indication of how to go about it?  I don't want to start any discussion about mono or why I don't want it, and won't reply to any trolling posts.

---

### Post by gerryl on 2009-11-05
After spending several hours in an unsuccessful attempt to install Hugin, I gave up and looked for other tools.  I found fotoxx - installed in about ten minutes, is trivially easy to use, and gives very creditable results.

[http://kornelix.squarespace.com/fotoxx/](http://kornelix.squarespace.com/fotoxx/)

---

### Post by mikecalder on 2009-11-06
Fotoxx looks OK, but is not as full featured as Hugin - not being able to do more than two pictures at a time, for example, kills it for me.  Hugin is far more sophisticated and gives you better control over the process (or lets you run it automatically - there's even a batch option).

I've discovered that the way to install Hugin without Mono is to go to the Hugin Website and the page there to compile from source.  

There is a specific set of instructions for Ubuntu; all you have to do is open a terminal and cut and paste the commands given on the webpage - it does take a little time, but it's worth it.  Mono is not needed or even discussed. The Hugin package developers work with a C version of Autopano-sift which works perfectly without pulling in the overhead or potential exposures of Mono.

I have done this now for both Jaunty and Karmic.  It works fine.

I don't know why the Ubuntu distributors have added the requirement for Mono to this package when it is not needed, and when it is not recommended or even talked about by the application developers - it makes one suspect that there is some other agenda at work here.

---

### Post by kornelix on 2009-12-24
You CAN make panoramas with more than two images with fotoxx. After each join, use the output image as the first image in the next join.

---

### Post by OgreProgrammer on 2009-12-24
Hugin and the others are in the repos for 9.04 and 9.10. I just installed them in 9.10.

---

### Post by Jim_in_Omaha on 2010-02-07
> **gerryl said:**
> After spending several hours in an unsuccessful attempt to install Hugin, I gave up and looked for other tools.  I found fotoxx - installed in about ten minutes, is trivially easy to use, and gives very creditable results.

[http://kornelix.squarespace.com/fotoxx/](http://kornelix.squarespace.com/fotoxx/)

I use Fotoxx and am now experimenting with Hugin from the package manager. I can say this much with the latest Fotoxx it does do some fantastic things and is very easy to use. I'm working with Hugin because I was at the Air Force Museum in Dayton and took several spread shots in the R&D hanger of the XB70. I found that Fotoxx is having a hard time with the beams in the hanger. I took several shots from the balcany overlooking B36 and B2, Fotoxx stiched that with incredible results. 

With the manual control of points in Hugin I am able to line up the hanger's beams with precision. Both programs I find valuable. I believe that Fotoxx is more focused as a overall photo editing/correction program because it has for example a great red-eye correction.

As far as I can see, just more great stuff for the Linux world...:P

---

### Post by samthethe on 2012-04-29
Thanks for the tutorial, but IME it's not worth trying to install anything that can't be done in just a couple of lines.  Chances are something will say "Error: Incompressible nonsense".  So please could you write a script to do this?  I know it's a lot to ask but it should be possible using wget, apt-get, dpkg, etc.

That way if something does error I would have only typed in one command!

---

