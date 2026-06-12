---
title: "HowTo: Install and Use OGRE"
date: 2009-05-04
forum: Tutorials
---

### Post by CalderCoalson on 2009-05-04
Here's a quick guide I wrote up for installing OGRE on Ubuntu.  I hope it's useful.



[SIZE="3"]**1 Installing OGRE**[/SIZE]

**1.0 Install Dependencies**
Execute the following in a terminal window:
```
sudo apt-get install build-essential autoconf libtool libdevil-dev libfreeimage-dev libfreetype6-dev libglew1.5-dev libxaw7-dev libxrandr-dev libxt-dev libxxf86vm-dev libzzip-dev
```
In case you're curious, the dependencies are as follows:
Bootstrap: autoconf libtool
Make: build-essential
Ogre: libdevil-dev libfreeimage-dev libfreetype6-dev libglew1.5-dev libxaw7-dev libxrandr-dev libxt-dev libxxf86vm-dev libzzip-dev

**1.1 Install OIS**
Go to OIS's download's page: [http://sourceforge.net/project/showfiles.php?group_id=149835](http://sourceforge.net/project/showfiles.php?group_id=149835) and download the latest release.  Decompress the file, open a terminal window, and cd to the decompressed folder.  Then, in a rather particular order, type:
```

./bootstrap
./configure
make
sudo make install

```

**1.2 Obtain the OGRE Source**
Download the "Ogre x.x.x Source for Linux / OSX" from [http://www.ogre3d.org/download/source](http://www.ogre3d.org/download/source) where x.x.x is the current distribution number.

**1.3 Create a Permanent Location**
Unlike most source distributions, you can't simply build, install and dispose.  The OGRE directory will need to be situated in a place you won't mind having it forever.  Personally, I have everything in ~/.ogre, but you can choose your own.  If you pick something else, just remember to substitute the location of your permanent folder whenever I say ~/.ogre.

**1.4 Unpack and Relocate**
Unpack the OGRE source using whatever means you choose, and move it to your undislosed permanent location, (~/.ogre).

**1.5 Configure**
Open a terminal window and cd to the OGRE source directory, (~/.ogre/ogre).  Now execute the following in the terminal:
```
./bootstrap
```
Now enter and execute the following:
```
./configure
```
If configuration fails after telling you to get nVidia's Cg library, then see the next step.

**1.6 Install nVidia Cg libraries**
**Note:** Do not perform this step if configuration runs successfully.
Download the "Linux x86" (32-bit) or Linux x86-64" (64-bit) tar files from [http://developer.nvidia.com/object/cg_toolkit.html#downloads](http://developer.nvidia.com/object/cg_toolkit.html#downloads) .  Decompress the file to wherever you want, and copy all the files to their appropriate folders on your system.
After placing the files, you need to reconfigure Ogre:
```
./configure
```

**1.7 Make**
Once configuration has finished, run the following:
```
make
```
Note that this can take a REALLY long time.  On my dual core 2Ghz it took nearly an hour.  If you want to speed this up, you can run make in multithreaded mode using the following command:
```
make -j x
```
where x is twice the number of cores your computer has.
**WARNING:** Do not execute 'make -j', this will run make with an unlimited number of concurrent threads and will overload and freeze your OS within a couple seconds.  This is called a makebomb.

**1.8 Install**
Now that everything has (hopefully) been built correctly, you're finally ready to install OGRE.  Cross your fingers and type:
```
sudo make install
```

**1.9 Update Dynamic Linker**
Now that you've installed everything in its proper place, you need to tell the linker to update it's chaches.  Run:
```
sudo ldconfig
```



[SIZE="3"]**2 Installing CEGUI [OPTIONAL]**[/SIZE]

**2.0 Install Dependencies**
Open a terminal window and type:
```
sudo apt-get install libpcre++-dev libpng12-dev libjpeg62-dev libmng-dev libwxgtk2.8-dev
```
Again, if you're curious, here're the dependencies:
CEGUI: libpcre++-dev
SILLY: libpng12-dev libjpeg62-dev libmng-dev
Layout Editor: libwxgtk2.8-dev
Imageset Editor:

**2.1 Download and Relocate**
Download the current source release of CEGUI, SILLY Image Loading Library, CEGUI Layout Editor, and CEGUI Imageset Editor.  Unzip all the packages and move CEGUI-x.x.x, CEImagesetEditor-x.x.x and CELayoutEditor-x.x.x to your permanent location, (~/.ogre).

**2.2 Install SILLY**
Open a terminal window and cd to the SILLY directory.  No execute the following commands, one after another.
```

./configure
make
sudo make install

```
You are now free to dispose of the SILLY source directory.

**2.3 Install CEGUI**
Now cd to the CEGUI directory, (~/.ogre/CEGUI-x.x.x) and run the following commands:
```

./bootstrap
./configure
make
sudo make install
sudo ldconfig

```
This build also takes a while, so if you want to use multithreading you can replace 'make' with 'make -j x' like last time.

**2.4 Install CEGUI Layout Editor**
Open a terminal window, cd to the CEGUI Layout Editor directory, (~/.ogre/CELayoutEditor-x.x.x), and enter:
```

./configure
make
sudo make install

```
To run CEGUI Layout Editor, use 'CELayoutEditor'.  You can make a launcher for it or add it to your main menu at your leisure.
The first time you start it, CELE requires you to give it the location of the default datafiles.

**2.5 Install CEGUI Imageset Editor**
*To be done...*



[SIZE="3"]**3 Installing QuickGUI [OPTIONAL]**[/SIZE]

**3.0 Install Dependencies**
Open a terminal window and type:
```
sudo apt-get install cmake
```
This is pretty self explanatory and is only for building the library.  QuickGUI's only other dependency is Ogre.

**3.1 Download and Relocate**
Obtain QuickGUI from the latest release thread here: [http://www.ogre3d.org/addonforums/viewforum.php?f=13](http://www.ogre3d.org/addonforums/viewforum.php?f=13) .  Extract the source and move it to your Ogre folder, (~/.ogre).

**3.2 Configure**
You may either use Code::Blocks or CMake to build the QuickGUI library.  If you are using Code::Blocks, the process is rather self-explanatory.
**Note:** Code::Blocks only builds the library, but does not install it.  You will have to manually move the dynamic library file (~/.ogre/QuickGUI/bin/libQuickGUI.so) to /usr/local/lib or wherever else you want to put it.
If, however, you decided to use CMake, cd to the QuickGUI source directory, (~/.ogre/QuickGUI) and type:
```

cmake .

```
**Note:** if you want to alter the default build options, you can type 'ccmake .' rather than 'cmake .'

**3.3 Build and Install**
Now that CMake has generated the Makefiles for you, you can simply run:
```

make
sudo make install
sudo ldconfig

```



[SIZE="3"]**4 Installing Bullet**[/SIZE]

**4.0 Install Dependencies**
Use apt-get to install dependencies:
```
sudo apt-get install freeglut3-dev
```

**4.1 Obtain Source**
Download the Bullet source code from here: [http://code.google.com/p/bullet/downloads/list](http://code.google.com/p/bullet/downloads/list) .  You don't need to keep the Bullet source, so feel free to install it right from your desktop.

**4.2 Make**
Open a terminal to the Bullet source directory and type:
```

./autogen.sh
./configure
make -j 4

```

**4.3 Install**
As of the time of this writing, the install-sh script included with Bullet has incompatible line endings.  Download another version from here: [http://www.fastcgi.com/devkit/install-sh](http://www.fastcgi.com/devkit/install-sh) and replace the one in the Bullet folder.  Then you can run:
```

sudo make install
sudo ldconfig

```



[SIZE="3"]**5 Creating an OGRE Project**[/SIZE]
**Note:** I will be using Code::Blocks for these instructions, although they will probably be easily adaptable to other IDEs as well.

**5.1 Create an Empty project**
Open Code::Blocks and select File->New->Project.  Choose an Empty Project, (the Ogre Project is broken on Linux), click Go, and choose a location.  Leave all the options on the next page default and click Finish.

**5.2 Add Linked Libraries**
In Project->Build Options select the "Linker Settings" tab and add "OgreMain" and "GL" to the "Link Libraries" box.
**Note:** Also add "OIS" for OIS, "CEGUI" for CEGUI, "QuickGUI" for QuickGUI depending on which of these additional libraries you will be using.  If you are using Bullet, it is absolutely essential that you include "bulletmath", "bulletcollision", and "bulletdynamics" in exactly that order.

**5.3 Setting up your plugins.cfg File**
Create a file named "plugins.cfg" in the directory your project's executable will reside in.  At the very minimum, this should include the following:
```

PluginFolder=/usr/local/lib/OGRE
Plugin=RenderSystem_GL.so
Plugin=Plugin_OctreeSceneManager.so

```

**5.4 Using the Example Application [OPTIONAL]**
If you are doing the tutorials or otherwise basing your project on the Example Application framework included with the OGRE source, you must copy the Samples/Media, and the Samples/Common/include/* from your OGRE source directory, (~/.ogre/ogre), to your project directory and your project include directory respectively.  Finally, you should also copy Samples/Common/bin/resources.cfg file to your project's build directory and replace all '../../'s with the appropriate path to your media directory.  Also remember to add
```
#include "ExampleApplication.h"
```
to your main Ogre file, and you should hopefully be good to go.



Once you have all this done, you should finally be able to follow the generic instructions on the Wiki.  I hope somebody finds these instructions helpful.  The whole installation process was hellishly time consuming and frustrating for me, and I hope this makes that slightly better.

-Calder

---

### Post by jpeddicord on 2009-05-12
Approved and thank you for your tutorial contribution. I'm curious though, why do you choose to download & install from source instead of using the version of OGRE in the repositories? I've never personally had any problems with the packaged framework, but it's been a while since I've used it.

---

### Post by CalderCoalson on 2009-05-12
The package version is old and hasn't been updated in nearly a year.  This also allows you to compile a lot of the newer versions of plug-ins, as well as actually understand what's going on with the library.  I don't remember the specifics, but I had a rather horrible time trying to get OGRE working with a lot of the plug-ins I wanted to use with the repository version.  Also, as a matter of principle, I prefer building from source when you're going to be developing with something.  End-user packages are one thing, but for developers source builds are kinda nice.

---

### Post by city-17 on 2009-08-25
Thanks for your tutorial :). I'll give it a try tonight and give you some feedback.

---

### Post by city-17 on 2009-08-26
:guitar:

It works! At least the directions for installing Ogre3D worked as I was able to run a couple of the sample demos successfully. I haven't tried the directions to install the optional stuff. And also I still need to try compile a demo myself with CodeBlocks just be sure, but it should be ok.

I'm curious about something though. Is the default behaviour of the autotool to configure against the GLX plattform. In other words would this be redundant:
```

./configure \--with-platform=GLX
```

At the beginning, I tried the previous command with GTK but make failed at some point so I ended up just using ./configure like you said.

Thanks again man! Your post surely made my life easier.

---

### Post by CalderCoalson on 2009-08-26
That's a good question, and one I'm unfortunately ignorant of the answer to.  I can tell you that on my system with an nVidia graphics card, the --with-platform=GLX option was automatically assumed, so I didn't think to include it in the tutorial.  I'm not what situations or systems would require manual configuration of the with-platform option, but of the two systems I have installed on, both have chosen correctly.

---

### Post by city-17 on 2009-08-28
Hey Calder, 

The how-to compile part of your tutorial is very accurate. It worked for me also. Another alternative for setting up an ogre project can be found here [http://www.plasticboy.de/2009/06/22/setting-up-an-ogre3d-project-in-codeblocks-ide-on-ubuntu/comment-page-1/#comment-269]("http://www.plasticboy.de/2009/06/22/setting-up-an-ogre3d-project-in-codeblocks-ide-on-ubuntu/comment-page-1/#comment-269"). But I like yours better because you showed how to create your own plugins.cfg file. 

Now its time for me to start playing around with ogre. 
Thanks again

---

### Post by CalderCoalson on 2009-08-28
The distinction is between copying your build to the Ogre directory or copying the resources from the Ogre directory to your project.  The latter seems more versatile and shows people what's actually going on, so I chose that.

---

### Post by city-17 on 2009-08-30
Hey Calder, it's me again.

I install ogre on another computer running ubuntu 9.04 as well (using your tutorial) but this time I paid more attention to the config summary that ./configure spits out. I noticed that CEGUI demos were not going to be built.
Here take a look:

```
--------=== Configuration summary ===--------
    Target platform                 : GLX
    OpenGL Ogre support             : GLX
    GUI library to use              : Xt
    Use double precision arithmetic : no
    Support for threading           : no
    Memory allocator                : ned
    Use STLport                     : no
    Use FreeType                    : yes
    Use FreeImage                   : yes
    Use DevIL                       : no
    Build OGRE demos                : yes
    Build CEGUI demos               : false
    Build the OpenEXR plugin        : no
    Build the Cg plugin             : yes
    Build the DirectX 9 plugin      : no
--------===============================--------
```

So I decided to fix that. Below, I describe the steps I took to have those demos working.

Basically you need to build DEVIL and CEGUI from source. You can get the latest tarballs from [here]("http://openil.sourceforge.net/download.php") and [here]("http://www.cegui.org.uk/wiki/index.php/Downloads") respectively

Before you compile make sure you uninstall the following packages
libdevilc2
libdevil-dev

Now, because I wanted to make sure I had all the dependencies before trying to compile both projects I checked out the packages suggested at this [wiki]("http://www.ogre3d.org/wiki/index.php/Building_From_Source#Ubuntu_.2F_Kubuntu") and compared them with the ones you suggested. Turns out there are some packages that are not repeated but I don't know how much difference they make. At least i tried them and they didn't broke anything

```
sudo apt-get install pkg-config automake checkinstall libpcre3-dev ibopenexr-dev freeglut-dev mesa-common-dev libtiff4-dev libglademm-2.4-dev libcppunit-dev libxaw7-dev 
```

These are some I tried on my own but I'm still not really sure if they make a difference or not. Try without them first

```
pkg-config freetype2-demos zziplib-bin libmng-dev libtiff-doc libmetacity-dev

```

Then go to Synaptic and make sure you have all of the following installed (as this will enable sdl support in devil)
libsdl-1.2debian
libsdl-1.2debian-alsa
libsdl-1.2dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-mixer1.2
libsdl-mixer1.2-dev
libsdl-net1.2
libsdl-net1.2-dev

once you are in the directory where you unpacked the DEVIL source
 
```
autoreconf -i
./configure --enable-ILU --enable-ILUT --with-examples 
make
sudo make install
ldconfigq

```

This should take care of DEVIL. Now to install CEGUI go to the CEGUI where you unpacked the source and type

```
aclocal && ./bootstrap && ./configure --with-default-xml-parser=TinyXMLParser
make

```

If make doesn't complete successfully because a strange compilation error related to ILVoid try the following fix:

in CEGUI-0.6.2/ImageCodecModules/DevILImageCodec/CEGUIDevILImageCodec.cpp 
replace all instances of ILvoid with void (I found two)

after that 

```
sudo make install
```

This should take care of CEGUI

finally install ogre (again type the following in the dir where you unpacked the ogre tarball)

```
aclocal
./bootstrap
./configure
make
sudo make install
sudo ldconfig
```

After the ./configure you should have CEGUI demos enabled.

```
--------=== Configuration summary ===--------
    Target platform                 : GLX
    OpenGL Ogre support             : GLX
    GUI library to use              : Xt
    Use double precision arithmetic : no
    Support for threading           : no
    Memory allocator                : ned
    Use STLport                     : no
    Use FreeType                    : yes
    Use FreeImage                   : yes
    Use DevIL                       : no
    Build OGRE demos                : yes
    Build CEGUI demos               : true
    Build the OpenEXR plugin        : no
    Build the Cg plugin             : yes
    Build the DirectX 9 plugin      : no
--------===============================--------

```
However, there is something that still bothers me and that is the line
Use DevIL : no
I don't know how come. I was able to build DEVIL succesfully so I don't know why ogre's autoconfigure tool can't find DEVIL. For that I'm going to ask for some help here in the forum.

But I can still build ogre successfully and all the demos seem to work fine
Hope this can be helpful to someone out there.

---

### Post by CalderCoalson on 2009-08-30
Is there any specific reason you wanted to build Devil from source?  And did you try my instructions for installing CEGUI first, to compare?  If those failed, please post while and I'll try and figure it out.  Simply building and installing CEGUI and then rebuilding Ogre did the trick for me, but did you at least try it so we can be sure it didn't work before we start figuring out why?  Also, I know CEGUI is kindof the monolithic standard because it was the ONLY GUI system for Ogre for a while, but personally I find QuickGUI's API and especially skinning method infinitely clearer.

---

### Post by city-17 on 2009-09-01
The reason I wanted to build devil from source was because the config summary from the ogre compilation read: 

Use Devil  No

And since devil is listed as a dependency for ogre I just thought I could have issues later on with my projects if I didn't get it right from the beginning. 

When I built CEGUI I forgot that your post also had directions for it. But I built CEGUI without issues anyway (without SILLY and CEGUILayerEditor though) and the ogre auto config did detect CEGUI. 

Now, do you remember if your config summary (just bebore typing make) had the option "Use Devil" enabled?. Do you think that by rebuilding CEGUI, with the dependencies you mentioned, I could get Devil detected?

Yeah, I might try QuickGui later on.

---

### Post by CalderCoalson on 2009-09-01
Sorry, I don't remember if Use Devil was enabled, and the computer running the virtual machine I used to write this tutorial on has a fried motherboard.  If I recall correctly from earlier installations, Ogre would not even build without devil installed, so it might be using it in some way even if configure didn't recognize it.  You may want to try posting on the Ogre forums about this or trying the 1.7.0 trunk; they're switching to CMake so the dependency finding code will have been completely re-written and will hopefully work better.

---

### Post by city-17 on 2009-09-02
Yes, I might give it a try to the latest trunk. Although, on a second thought, I'll better start playing with Ogre first and try to build the latest trunk only if I find an issue.

Again, thanks for the post, it was very valuable to me.

---

### Post by gauravsc on 2010-01-04
I am trying to install ogre on ubuntu 9.04
I followed your tutorial but I am getting the following error
thanks for your help in advance

gaurav@gaurav-desktop:~/ogre$ make
Making all in OgreMain
make[1]: Entering directory `/home/gaurav/ogre/OgreMain'
Making all in src
make[2]: Entering directory `/home/gaurav/ogre/OgreMain/src'
/bin/bash ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../OgreMain/include  -I/usr/include/freetype2 -I../../OgreMain/include -DOGRE_NONCLIENT_BUILD -DOGRE_GUI_GLX     -fvisibility=hidden -fvisibility-inlines-hidden -DOGRE_GCC_VISIBILITY -I../../OgreMain/src/nedmalloc    -g -O2 -MT OgreBillboardParticleRenderer.lo -MD -MP -MF .deps/OgreBillboardParticleRenderer.Tpo -c -o OgreBillboardParticleRenderer.lo OgreBillboardParticleRenderer.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../../OgreMain/include -I/usr/include/freetype2 -I../../OgreMain/include -DOGRE_NONCLIENT_BUILD -DOGRE_GUI_GLX -fvisibility=hidden -fvisibility-inlines-hidden -DOGRE_GCC_VISIBILITY -I../../OgreMain/src/nedmalloc -g -O2 -MT OgreBillboardParticleRenderer.lo -MD -MP -MF .deps/OgreBillboardParticleRenderer.Tpo -c OgreBillboardParticleRenderer.cpp  -fPIC -DPIC -o .libs/OgreBillboardParticleRenderer.o
OgreBillboardParticleRenderer.cpp:489: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[2]: *** [OgreBillboardParticleRenderer.lo] Error 1
make[2]: Leaving directory `/home/gaurav/ogre/OgreMain/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gaurav/ogre/OgreMain'
make: *** [all-recursive] Error 1

---

### Post by gauravsc on 2010-01-04
I followed you advice on Ubuntu 9.04 but I am getting the error on make.If you can help.. 
thanks for your help in advance
--------=== Configuration summary ===--------
    Target platform                 : GLX
    OpenGL Ogre support             : GLX
    GUI library to use              : Xt
    Use double precision arithmetic : no
    Support for threading           : no
    Memory allocator                : ned
    Use STLport                     : no
    Use FreeType                    : yes
    Use FreeImage                   : yes
    Use DevIL                       : no
    Build OGRE demos                : yes
    Build CEGUI demos               : false
    Build the OpenEXR plugin        : no
    Build the Cg plugin             : yes
    Build the DirectX 9 plugin      : no
--------===============================--------
**make result:-**
OgreBillboardParticleRenderer.cpp:489: internal compiler error: in verify_marks_clear, at dwarf2out.c:14909
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[2]: *** [OgreBillboardParticleRenderer.lo] Error 1
make[2]: Leaving directory `/home/gaurav/ogre/OgreMain/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gaurav/ogre/OgreMain'
make: *** [all-recursive] Error 1

---

### Post by CalderCoalson on 2010-01-04
I just replied to your personal message, but in case anyone else encounters this extremely strange error, it's more likely to be a compiler error than an Ogre one, but I would still check the [Ogre forums]("http://ogre3d.org/forums/") just to make sure.

---

### Post by r.stiltskin on 2010-02-02
Ubuntu 8.04 (Hardy)

This is my first shot at OGRE.   At first, I installed it from the repos but had a hell of a time trying to run the first tutorial program.  I had problems compiling it, and even after getting it to compile, I had runtime errors -- as soon as I fixed one another popped up.  The binary packages don't include the OGRE sample programs, and even after downloading the sample programs from svn and taking the headers and .cfg files that the tutorials need, I still couldn't get the tutorial programs to run.  I figured it would be easier and quicker to build the svn source than to try to sort out the directory structures to be able to run the tutorials.  (All this occurred before I found your excellent HowTo.)

But before I had decided to build OGRE, I happened to notice [Andrew Fenn's PPA]("https://launchpad.net/~andrewfenn/+archive/ogredev") which has updated packages for cegui, cegui-layout-editor, nvidia-cg-toolkit, ois and silly, so I installed those from his archive rather than building them. (He also has an updated build of OGRE, but it seems to have the same limitations regarding the tutorials as the official Ubuntu version.  I guess it's fine for experienced users but not much help for novices.) 

I installed all the other dependencies as listed in your HowTo from my regular Synaptic sources. I'm using Synaptic rather than apt-get just to have the convenient history available as a guide if (when) I want to uninstall any or all of these packages.  The only significant difference is that I already had cegui installed before building OGRE, so when I ran OGRE's configure script, it enabled the cegui demos.

Regarding DevIL:  It doesn't seem to matter whether DevIL is built from source or installed from repos.  It's not that configure can't find DevIL; it seems that if it finds Freeimage, it uses that instead of DevIL.  I found this in configure's output:
configure: Freeimage is being built, disabling check for DevIL.

My machine is older and slower than yours, so the build has been running for over an hour and no end in sight...  I'll update this after I see how it turns out.

One question though:
You said that the build directory for OGRE has to be kept permanently, but you didn't say why.  So I'm wondering, why?

---

### Post by CalderCoalson on 2010-02-02
The reason I'd recommended keeping the build directory around is because people will often link to the sample app header or media files with a lot of their early applications, and be extremely confused about where to find those if they've deleted them.  That, and the examples are really nice to have around.  Once you've gotten to the point of a completely standalone app, though, you don't need to keep it around if you don't want to.

---

### Post by r.stiltskin on 2010-02-02
As it turned out, my build eventually bombed -- near the end, while compiling something in Samples/Common/CEGUIRenderer there was an error about a "conflicting return type specified for ‘virtual CEGUI::Texture* CEGUI::OgreCEGUIRenderer::createTexture()’" yadda yadda yadda...
so I decided I must have some sort of incompatibility between versions of programs.  I uninstalled the binary packages of SILLY and all of the CEGUI components (but retained the ois and nvidia-cg-toolkit binaries), downloaded tarballs (NOT the latest ones) of SILLY and CEGUI and built them, and then rebuilt OGRE and it completed successfully.

So, what ultimately succeeded for me was the latest source from the subversion v1-6 branch, along with the tarballs of CEGUI-0.6.2, CELayoutEditor-0.6.2 and CEImagesetEditor-0.6.2 and SILLY-0.1.0.  All other dependencies came from the official Ubuntu Hardy (8.04) repos, except for ois and nvidia-cg-toolkit which are more recent binaries from Andrew Fenn's PPA.

---

### Post by r.stiltskin on 2010-02-03
Well, after all that, although I did successfully build OGRE and CEGUI (and QuickGUI as well), exactly the same error occurred with the newly built libs as did with the Ubuntu binaries 24 hours ago.  When I tried to run the initial code in Basic Tutorial 1, it immediately exited the program with this error ...
```
An exception has occurred: OGRE EXCEPTION(6:FileNotFoundException): 'resources.cfg' file not 
found! in ConfigFile::load at OgreConfigFile.cpp (line 84)
*-*-* OGRE Shutdown
```
... and that is also exactly what happened when I ran the SampleApp code in CodeBlocks' ogre project (after fixing up the Project Properties).  The missing final step needed to successfully run the sample code is that there must be a 'resources.cfg' file in the project root directory containing the following:
```
# Resource locations to be added to the 'boostrap' path
# This assumes that the entire Samples/Media directory from the OGRE source
#  has been copied to the project root directory.
# This also contains the minimum you need to use the Ogre example framework
[Bootstrap]
Zip=Media/packs/OgreCore.zip

# Resource locations to be added to the default path
[General]
FileSystem=Media
FileSystem=Media/fonts
FileSystem=Media/materials/programs
FileSystem=Media/materials/scripts
FileSystem=Media/materials/textures
FileSystem=Media/models
FileSystem=Media/overlays
FileSystem=Media/particle
FileSystem=Media/gui
FileSystem=Media/DeferredShadingMedia
FileSystem=Media/PCZAppMedia
Zip=Media/packs/cubemap.zip
Zip=Media/packs/cubemapsJS.zip
Zip=Media/packs/dragon.zip
Zip=Media/packs/fresneldemo.zip
Zip=Media/packs/ogretestmap.zip
Zip=Media/packs/skybox.zip

```
(I just took the resources.cfg file from Samples/Common/bin and edited the paths.)
Now, the sample code actually runs!  It would probably be helpful to the next new user if you would edit your Post #1 to include this resources.cfg file in your Step 5 ("Creating an Ogre Project").

---

### Post by CalderCoalson on 2010-02-03
So sorry, you're right, I'd completely forgotten that.

*[FIXED]*

[EDIT]Fixed another inconsistency Joel pointed out.[/EDIT]

---

### Post by ebirah on 2010-05-04
Thanks for the tutorial :)

I downloaded the most recent release of Ogre, 1.7.1, but the source directory doesn't contain ./bootstrap or ./configure (step 1.5). I'll probably use 1.6.5 for now, as I'm just getting started and I'm lazy, but perhaps the lack of these files / building method in 1.7 should be noted in the OP.

Edit: I followed the instructions exactly with 1.6.5, but when I try to run the ogre/Sample binaries or my own compilation of the tutorial it fails because of various ogre exceptions and compiler errors, some relating to Cg. Any ideas? 

Cheers

---

### Post by CalderCoalson on 2010-05-04
Sorry, I hadn't gotten around to updating these instructions for 1.7 yet.  I think you can get by with replacing all the Ogre build instructions with
```

cmake .
make -j 4
sudo make install

```
from the Ogre directory.  Though you'll probably want Boost for threading support as well.  You can download that here: [http://sourceforge.net/projects/boost/files/boost/1.42.0/](http://sourceforge.net/projects/boost/files/boost/1.42.0/) and run
```

./bootstrap.sh
sudo ./bjam install

```
More instructions on their website here: [http://www.boost.org/doc/libs/1_42_0/more/getting_started/unix-variants.html](http://www.boost.org/doc/libs/1_42_0/more/getting_started/unix-variants.html)

---

### Post by Liemarzac on 2010-07-31
Thank you for the time you spent writing this very good step by step installation tutorial.

I managed to have Ogre 1.7.x compiled from source without too much pain. 

Im now trying to run the very small exampleapplication with Code::Blocks. But I run into the issue where RenderSystem_GL.so is not found. Apparently several people had the same issue and managed to get it working but no chance for me. I've added /usr/local/lib/OGRE/RenderSystem_GL.so in the Build Options-->Linker Settings of my project and checked that the lib does exist. I also have the plugins.cfg file filled with this code:

```
PluginFolder=/usr/local/lib/OGRE
Plugin=RenderSystem_GL.so
Plugin=Plugin_OctreeSceneManager.so
```

The plugin.cfg file is in the same folder as my binary. I've also tried to change the Execution working dir to the absolute path of my binary and renaming the plugins file with a uppercase P since it appared to fix that problem for someone but  I can't get rid of the error. How to make sure that this Plugins file is found? 
Im using ubuntu 10.04 64bit, could it be the problem?
Thanks is advance for any help ;)

---

### Post by CalderCoalson on 2010-08-01
Hmm...  How are you initializing the Ogre Root object?  Also, can you post your Ogre.log file as well as the console output?

---

### Post by Liemarzac on 2010-08-21
I'm sorry I didn't reply quicker; my internet connection went down for quite a while.

I took out RenderSystem_GL.so from Options-->Linker Settings and it worked. The executable was not even starting with it. I don't know why the linker couldn't find the lib because it is definitely there. Anyway Code::Blocks doesn't seem to need it at all for linking. I now have the basic tutorial running but with a black screen without any of the entities i created in my scene. But this is another problem ;)

Edit: Never mind my ambient light was set black...
Again thanks for your tutorial, i would never have gone this far without it.

---

### Post by CalderCoalson on 2010-08-21
Great, glad you figured it out!  And glad the tutorial helped someone! :D

---

### Post by shadowpt on 2011-02-02
I'm trying to run OGRE with Eclipse but I get a black screen with the basic tutorial 1 (from their tutorial page). I get FPS information and the OGRE Icon though.

Any thoughts?

---

### Post by CalderCoalson on 2011-02-02
Oh god, that's probably shitty graphics card drivers.  I had that for a year on my old laptop before Ubuntu finally updated their drivers.  I'm not sure there's much I can do for you there.

---

### Post by Irvine_himself on 2011-04-08
I am trying to install the latest Ogre from SVN 

I was using the [Ogre Build Wiki]("http://code.google.com/p/gamekit/wiki/Building") which calls CMake, but that is probably unimportant. My real problem is that apart from some problems with "Xaw widgets", everything went fine until I called "make install" it does all the makes, but fails with the final install
```
Install the project...
/usr/bin/cmake -P cmake_install.cmake
-- Install configuration: ""
-- Up-to-date: /usr/local/lib/libOgreMainStatic.a
-- Up-to-date: /usr/local/include/OGRE/asm_math.h
-- Up-to-date: /usr/local/include/OGRE/Ogre.h
-- Up-to-date: /usr/local/include/OGRE/OgreAlignedAllocator.h
-- Up-to-date: /usr/local/include/OGRE/OgreAnimable.h
-- Up-to-date: /usr/local/include/OGRE/OgreAnimation.h
-- Up-to-date: /usr/local/include/OGRE/OgreAnimationState.h
-- Up-to-date: /usr/local/include/OGRE/OgreAnimationTrack.h
-- Up-to-date: /usr/local/include/OGRE/OgreAny.h
-- Up-to-date: /usr/local/include/OGRE/OgreArchive.h
-- Up-to-date: /usr/local/include/OGRE/OgreArchiveFactory.h
-- Up-to-date: /usr/local/include/OGRE/OgreArchiveManager.h
-- Up-to-date: /usr/local/include/OGRE/OgreAtomicWrappers.h
-- Up-to-date: /usr/local/include/OGRE/OgreAutoParamDataSource.h
-- Up-to-date: /usr/local/include/OGRE/OgreAxisAlignedBox.h
-- Up-to-date: /usr/local/include/OGRE/OgreBillboard.h
-- Up-to-date: /usr/local/include/OGRE/OgreBillboardChain.h
-- Up-to-date: /usr/local/include/OGRE/OgreBillboardParticleRenderer.h
-- Up-to-date: /usr/local/include/OGRE/OgreBillboardSet.h
-- Up-to-date: /usr/local/include/OGRE/OgreBitwise.h
-- Up-to-date: /usr/local/include/OGRE/OgreBlendMode.h
-- Up-to-date: /usr/local/include/OGRE/OgreBone.h
-- Up-to-date: /usr/local/include/OGRE/OgreBorderPanelOverlayElement.h
CMake Error at Ogre-1.8/OgreMain/cmake_install.cmake:60 (FILE):
  file INSTALL cannot find
  "~/gamekit-SVN/Ogre-1.8/Settings/OgreBuildSettings.h".
Call Stack (most recent call first):
  Ogre-1.8/cmake_install.cmake:37 (INCLUDE)
  cmake_install.cmake:39 (INCLUDE)


make: *** [install] Error 1

```I must admit that I am not brilliant at installing from source and would be grateful if you could point out where I am going wrong
.

---

### Post by CalderCoalson on 2011-04-08
For starters, you're using the unstable development version, 1.8.  Try with 1.7 and see what happens! :)

---

### Post by Irvine_himself on 2011-04-09
Okay, after a little more research and a nights sleep, I think I have made a classic mistake. I am not specifically trying to install [Ogre]("http://www.ogre3d.org/"), but the Blender add-on [Game-Kit]("http://code.google.com/p/gamekit/source/checkout"), which, confusingly, is often referred to by the less technically informed as the "Ogre Game-Engine" or "Ogre-Game-Kit" or "Ogre-Kit"  or even just "Ogre"

If I am outside the scope of this tutorial, I appologise for the inconvenience and will look elsewhere for answers.

By the way, the reason I am using SVN is that the current rapid development of MakeHuman, Blender-2.5x and  Game-Kit more or less demand these three be regularly updated, (either through nightly builds or  SVN,) and that these updates be synchronous.

Sorry.
.

---

### Post by insanity werks on 2011-10-09
trying to follow the directions and at the first part installing ois it keeps telling me bash: ./bootstrap: Permission denied
 dont have any clue on what i have done wrong help is appreciated

---

### Post by ebirah on 2011-10-13
> **insanity werks said:**
> trying to follow the directions and at the first part installing ois it keeps telling me bash: ./bootstrap: Permission denied
 dont have any clue on what i have done wrong help is appreciated
It sounds like you don't have permission to run the bootstrap file. Files in GNU/Linux have 'permissions' which control who can and can't read, write to and run them, as a security feature.
Run
```
ls -l | grep bootstrap
```from the same directory. You should see something like this:
```
-rwxr--r-- 1 username:username 1024 2011-10-13 17:30 bootstrap
```(see [http://en.wikipedia.org/wiki/Ls](http://en.wikipedia.org/wiki/Ls))
If the 'x' is missing, that means the owner ('username', you) doesn't have permission to run the file. To fix this, 
```
chmod u+x bootstrap
```(Modify permissions: owner add execute permission on bootstrap)
If you have 'root' instead of your user name, then you probably decompressed it with sudo. If you decompressed the archive in your home directory, go to the folder above the one with OIS in it and do:
```
sudo chown -R username: OIS
```Where username = your user name and OIS = the OIS folder.
(Recursively change the ownership of the folder OIS to username and the group to username's login group.)
Then run ./bootstrap. Don't run ./bootstrap as root, ('sudo ./bootstrap') because then it would have permission to screw up your system if something went wrong.

---

### Post by insanity werks on 2011-10-14
it tells me when i go to do sudo chown -R geeky:ois to tell me im missing an operand after 
 im in the file ois directory when running this code

---

### Post by ebirah on 2011-10-17
> **insanity werks said:**
> it tells me when i go to do sudo chown -R geeky:ois to tell me im missing an operand after 
 im in the file ois directory when running this code

You need a space after the colon. I.e.
```
sudo chown -R geeky: ois
```Generally, if things complain at you, try reading "[command] --help" or "man [command]"
E.g.
```
chown --help
man chown
```

---

### Post by insanity werks on 2011-10-17
ok thanks to all who have helped My next problem comes in installing cegui i can make the ./bootstrap and ./configure just fine no errors but when i go to make the file i come up with an error this the error :
In file included from ../../cegui/include/CEGUIAffector.h:33:0,
                 from CEGUIAffector.cpp:30:
../../cegui/include/CEGUIString.h:65:11: error: 'ptrdiff_t' does not name a type
make[3]: *** [libCEGUIBase_la-CEGUIAffector.lo] Error 1
make[3]: Leaving directory `/usr/share/ogre/cegui_mk2-0-7/cegui/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/share/ogre/cegui_mk2-0-7/cegui/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/share/ogre/cegui_mk2-0-7/cegui'
make: *** [all-recursive] Error 1
 have no clue  on how to fix it any help would be appreciated

---

### Post by ebirah on 2011-10-18
> **insanity werks said:**
> ok thanks to all who have helped My next problem comes in installing cegui i can make the ./bootstrap and ./configure just fine no errors but when i go to make the file i come up with an error this the error :
In file included from ../../cegui/include/CEGUIAffector.h:33:0,
                 from CEGUIAffector.cpp:30:
../../cegui/include/CEGUIString.h:65:11: error: 'ptrdiff_t' does not name a type
make[3]: *** [libCEGUIBase_la-CEGUIAffector.lo] Error 1
make[3]: Leaving directory `/usr/share/ogre/cegui_mk2-0-7/cegui/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/share/ogre/cegui_mk2-0-7/cegui/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/share/ogre/cegui_mk2-0-7/cegui'
make: *** [all-recursive] Error 1
 have no clue  on how to fix it any help would be appreciated

Googling "'ptrdiff_t'" reveals that it is a type from the C standard library, defined in stddef.
Googling "'ptrdiff_t' does not name a type" gives [this page]("https://wiki.edubuntu.org/GCC4.6") which indicates that with GCC4.6 you have to include stddef to use ptrdiff_t, whereas you didn't before, although you technically should have. 
So, [grep]("http://ss64.com/bash/grep.html") the CEGUI sources for "ptrdiff_t", and in the files were it appears, add the include (#include <cstddef>)
Iff that works, you might want to check if the latest version of CEGUI now includes the header, and if it doesn't, bring it up on their IRC channel or mailing list.

---

### Post by insanity werks on 2011-10-20
ok I think i have everything install  but running into trouble setting up codeblocks to fix the file i can get a new project and i get Project->Build Options but what confuses me it when adding ogre main no files show up to add what have i done wrong help me please :sad:

---

### Post by ebirah on 2011-10-24
> **insanity werks said:**
> ok I think i have everything install  but running into trouble setting up codeblocks to fix the file i can get a new project and i get Project->Build Options but what confuses me it when adding ogre main no files show up to add what have i done wrong help me please :sad:

;_;

Not entirely sure what you mean by 'fix the file'. Assuming everything built and installed OK and you're now trying the tutorials / your own project:

You don't need to select the file: just literally put 'OgreMain' (without quotes) etc.. If you have installed Ogre, libOgreMain.so will be in the /usr/lib directory, which is one of the paths that the linker will search, and you're done.

If you didn't install, go into build options->search directories->linker [tab], and add the directory where you build Ogre, or wherever it put OgreMain. (If you need to find it, try 'find [directory] -iname ogremain' without the quotes (see 'man find'). Edit: if you haven't installed, you would also need to add the appropriate path to 'compiler' to get the headers.
The library thing confused me at first too.

---

### Post by Orpheon on 2012-02-29
Sorry to necrobump this thread, but I'm getting problems with compiling.

> **CalderCoalson said:**
> Sorry, I hadn't gotten around to updating  these instructions for 1.7 yet.  I think you can get by with replacing  all the Ogre build instructions with
```

cmake .
make -j 4
sudo make install

```from the Ogre directory.
When I tried to do this, cmake worked fine, but make crashed.
It doesn't matter whether normal make or make -j 4.

The log of the error is bigger than the console output memory, here is everything that's left:
```
/usr/local/include/boost/thread/locks.hpp: In function ‘void boost::swap(boost::unique_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:486:9: error: ‘lhs’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp:486:18: error: ‘rhs’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:490:31: error: expected unqualified-id before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:496:31: error: expected unqualified-id before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:509:30: error: expected unqualified-id before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:515:30: error: expected unqualified-id before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:629:30: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In member function ‘void boost::shared_lock<Mutex>::swap(boost::shared_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:631:25: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:732:33: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In function ‘void boost::swap(boost::shared_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:734:9: error: ‘lhs’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp:734:18: error: ‘rhs’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:780:41: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:780:49: error: invalid constructor; you probably meant ‘boost::upgrade_lock<Mutex> (const boost::upgrade_lock<Mutex>&)’
/usr/local/include/boost/thread/locks.hpp:787:40: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:798:52: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:805:51: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In constructor ‘boost::upgrade_lock<Mutex>::upgrade_lock(boost::unique_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:788:15: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: In member function ‘boost::upgrade_lock<Mutex>& boost::upgrade_lock<Mutex>::operator=(boost::upgrade_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:800:62: error: expected ‘>’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:800:62: error: expected ‘(’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:800:64: error: expected identifier before ‘>’ token
/usr/local/include/boost/thread/locks.hpp:800:66: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: In member function ‘boost::upgrade_lock<Mutex>& boost::upgrade_lock<Mutex>::operator=(boost::unique_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:807:61: error: expected ‘>’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:807:61: error: expected ‘(’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:807:63: error: expected identifier before ‘>’ token
/usr/local/include/boost/thread/locks.hpp:807:65: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:923:56: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In constructor ‘boost::unique_lock<Mutex>::unique_lock(boost::upgrade_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:924:11: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:966:61: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:966:69: error: invalid constructor; you probably meant ‘boost::upgrade_to_unique_lock<Mutex> (const boost::upgrade_to_unique_lock<Mutex>&)’
/usr/local/include/boost/thread/locks.hpp:972:72: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In member function ‘boost::upgrade_to_unique_lock<Mutex>& boost::upgrade_to_unique_lock<Mutex>::operator=(boost::upgrade_to_unique_lock<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:974:41: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:1044:46: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:1044:54: error: invalid constructor; you probably meant ‘boost::detail::try_lock_wrapper<Mutex> (const boost::detail::try_lock_wrapper<Mutex>&)’
/usr/local/include/boost/thread/locks.hpp:1048:29: error: expected unqualified-id before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:1053:64: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp:1060:39: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In member function ‘boost::detail::try_lock_wrapper<Mutex>& boost::detail::try_lock_wrapper<Mutex>::operator=(boost::detail::try_lock_wrapper<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:1055:39: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: In member function ‘void boost::detail::try_lock_wrapper<Mutex>::swap(boost::detail::try_lock_wrapper<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:1062:28: error: ‘other’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp: At global scope:
/usr/local/include/boost/thread/locks.hpp:1133:42: error: expected ‘,’ or ‘...’ before ‘&&’ token
/usr/local/include/boost/thread/locks.hpp: In function ‘void boost::detail::swap(boost::detail::try_lock_wrapper<Mutex>)’:
/usr/local/include/boost/thread/locks.hpp:1135:13: error: ‘lhs’ was not declared in this scope
/usr/local/include/boost/thread/locks.hpp:1135:22: error: ‘rhs’ was not declared in this scope
In file included from /usr/local/include/boost/thread/pthread/thread_data.hpp:16:0,
                 from /usr/local/include/boost/thread/pthread/condition_variable.hpp:10,
                 from /usr/local/include/boost/thread/condition_variable.hpp:16,
                 from /usr/local/include/boost/thread/pthread/shared_mutex.hpp:13,
                 from /usr/local/include/boost/thread/shared_mutex.hpp:16,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeadersBoost.h:33,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeaders.h:30,
                 from /home/alexander/.ogre/OgreMain/include/OgreStdHeaders.h:114,
                 from /home/alexander/.ogre/OgreMain/include/OgrePrerequisites.h:315,
                 from /home/alexander/.ogre/OgreMain/src/OgreAlignedAllocator.cpp:30:
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp: In constructor ‘boost::condition_variable::condition_variable()’:
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:40:69: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp: In destructor ‘boost::condition_variable::~condition_variable()’:
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:46:65: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:50:29: error: ‘EINTR’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp: In member function ‘bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&)’:
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:66:55: error: no matching function for call to ‘boost::posix_time::ptime::ptime(const boost::xtime&)’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:66:55: note: candidates are:
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:53:5: note: boost::posix_time::ptime::ptime()
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:53:5: note:   candidate expects 0 arguments, 1 provided
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:49:5: note: boost::posix_time::ptime::ptime(boost::date_time::special_values)
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:49:5: note:   no known conversion for argument 1 from ‘const boost::xtime’ to ‘boost::date_time::special_values’
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:45:5: note: boost::posix_time::ptime::ptime(const time_rep_type&)
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:45:5: note:   no known conversion for argument 1 from ‘const boost::xtime’ to ‘const time_rep_type& {aka const boost::date_time::counted_time_rep<boost::posix_time::millisec_posix_time_system_config>&}’
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:42:14: note: boost::posix_time::ptime::ptime(boost::gregorian::date)
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:42:14: note:   no known conversion for argument 1 from ‘const boost::xtime’ to ‘boost::gregorian::date’
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:39:5: note: boost::posix_time::ptime::ptime(boost::gregorian::date, boost::posix_time::ptime::time_duration_type)
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:39:5: note:   candidate expects 2 arguments, 1 provided
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:31:9: note: boost::posix_time::ptime::ptime(const boost::posix_time::ptime&)
/usr/include/boost-1_34/boost/date_time/posix_time/ptime.hpp:31:9: note:   no known conversion for argument 1 from ‘const boost::xtime’ to ‘const boost::posix_time::ptime&’
In file included from /usr/local/include/boost/thread/pthread/condition_variable.hpp:10:0,
                 from /usr/local/include/boost/thread/condition_variable.hpp:16,
                 from /usr/local/include/boost/thread/pthread/shared_mutex.hpp:13,
                 from /usr/local/include/boost/thread/shared_mutex.hpp:16,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeadersBoost.h:33,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeaders.h:30,
                 from /home/alexander/.ogre/OgreMain/include/OgreStdHeaders.h:114,
                 from /home/alexander/.ogre/OgreMain/include/OgrePrerequisites.h:315,
                 from /home/alexander/.ogre/OgreMain/src/OgreAlignedAllocator.cpp:30:
/usr/local/include/boost/thread/pthread/thread_data.hpp: In member function ‘void boost::detail::interruption_checker::check_for_interruption()’:
/usr/local/include/boost/thread/pthread/thread_data.hpp:89:46: error: ‘thread_interrupted’ was not declared in this scope
/usr/local/include/boost/thread/pthread/thread_data.hpp: In constructor ‘boost::detail::interruption_checker::interruption_checker(pthread_mutex_t*, pthread_cond_t*)’:
/usr/local/include/boost/thread/pthread/thread_data.hpp:105:56: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/thread_data.hpp:109:56: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/thread_data.hpp: In destructor ‘boost::detail::interruption_checker::~interruption_checker()’:
/usr/local/include/boost/thread/pthread/thread_data.hpp:116:58: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/thread_data.hpp:123:58: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/thread_data.hpp: At global scope:
/usr/local/include/boost/thread/pthread/thread_data.hpp:147:16: error: ‘BOOST_SYMBOL_VISIBLE’ does not name a type
In file included from /usr/local/include/boost/thread/condition_variable.hpp:16:0,
                 from /usr/local/include/boost/thread/pthread/shared_mutex.hpp:13,
                 from /usr/local/include/boost/thread/shared_mutex.hpp:16,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeadersBoost.h:33,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeaders.h:30,
                 from /home/alexander/.ogre/OgreMain/include/OgreStdHeaders.h:114,
                 from /home/alexander/.ogre/OgreMain/include/OgrePrerequisites.h:315,
                 from /home/alexander/.ogre/OgreMain/src/OgreAlignedAllocator.cpp:30:
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&)’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:57:29: error: ‘EINTR’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp:62:52: error: ‘condition_error’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&)’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:77:22: error: ‘ETIMEDOUT’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp:83:52: error: ‘condition_error’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘void boost::condition_variable::notify_one()’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:91:49: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘void boost::condition_variable::notify_all()’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:97:52: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In constructor ‘boost::condition_variable_any::condition_variable_any()’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:119:69: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In destructor ‘boost::condition_variable_any::~condition_variable_any()’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:125:65: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘void boost::condition_variable_any::wait(lock_type&)’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:142:56: error: there are no arguments to ‘condition_error’ that depend on a template parameter, so a declaration of ‘condition_error’ must be available [-fpermissive]
/usr/local/include/boost/thread/pthread/condition_variable.hpp:142:56: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘bool boost::condition_variable_any::timed_wait(lock_type&, const system_time&)’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:164:21: error: ‘ETIMEDOUT’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp:170:56: error: there are no arguments to ‘condition_error’ that depend on a template parameter, so a declaration of ‘condition_error’ must be available [-fpermissive]
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘void boost::condition_variable_any::notify_one()’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:212:53: error: ‘BOOST_VERIFY’ was not declared in this scope
/usr/local/include/boost/thread/pthread/condition_variable.hpp: In member function ‘void boost::condition_variable_any::notify_all()’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:218:56: error: ‘BOOST_VERIFY’ was not declared in this scope
In file included from /usr/local/include/boost/thread/shared_mutex.hpp:16:0,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeadersBoost.h:33,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeaders.h:30,
                 from /home/alexander/.ogre/OgreMain/include/OgreStdHeaders.h:114,
                 from /home/alexander/.ogre/OgreMain/include/OgrePrerequisites.h:315,
                 from /home/alexander/.ogre/OgreMain/src/OgreAlignedAllocator.cpp:30:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘void boost::shared_mutex::lock_shared()’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:64:36: error: no matching function for call to ‘boost::condition_variable::wait(boost::mutex::scoped_lock&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:64:36: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note: void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:57:14: note: template<class predicate_type> void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&, predicate_type)
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘bool boost::shared_mutex::timed_lock_shared(const system_time&)’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:91:54: error: no matching function for call to ‘boost::condition_variable::timed_wait(boost::mutex::scoped_lock&, const system_time&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:91:54: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:66:17: note: bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:66:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:64:14: note: bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:64:14: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:70:14: note: template<class duration_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const duration_type&)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:76:14: note: template<class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&, predicate_type)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:87:14: note: template<class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&, predicate_type)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:93:14: note: template<class duration_type, class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const duration_type&, predicate_type)
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘void boost::shared_mutex::lock()’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:135:39: error: no matching function for call to ‘boost::condition_variable::wait(boost::mutex::scoped_lock&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:135:39: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note: void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:57:14: note: template<class predicate_type> void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&, predicate_type)
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘bool boost::shared_mutex::timed_lock(const system_time&)’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:148:57: error: no matching function for call to ‘boost::condition_variable::timed_wait(boost::mutex::scoped_lock&, const system_time&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:148:57: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:66:17: note: bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:66:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:64:14: note: bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:64:14: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:70:14: note: template<class duration_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const duration_type&)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:76:14: note: template<class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&, predicate_type)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:87:14: note: template<class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&, predicate_type)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:93:14: note: template<class duration_type, class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const duration_type&, predicate_type)
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘void boost::shared_mutex::lock_upgrade()’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:199:36: error: no matching function for call to ‘boost::condition_variable::wait(boost::mutex::scoped_lock&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:199:36: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note: void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:57:14: note: template<class predicate_type> void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&, predicate_type)
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘bool boost::shared_mutex::timed_lock_upgrade(const system_time&)’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:211:54: error: no matching function for call to ‘boost::condition_variable::timed_wait(boost::mutex::scoped_lock&, const system_time&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:211:54: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:66:17: note: bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:66:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:64:14: note: bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:64:14: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:70:14: note: template<class duration_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const duration_type&)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:76:14: note: template<class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const system_time&, predicate_type)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:87:14: note: template<class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const boost::xtime&, predicate_type)
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:93:14: note: template<class duration_type, class predicate_type> bool boost::condition_variable::timed_wait(boost::unique_lock<boost::mutex>&, const duration_type&, predicate_type)
/usr/local/include/boost/thread/pthread/shared_mutex.hpp: In member function ‘void boost::shared_mutex::unlock_upgrade_and_lock()’:
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:266:37: error: no matching function for call to ‘boost::condition_variable::wait(boost::mutex::scoped_lock&)’
/usr/local/include/boost/thread/pthread/shared_mutex.hpp:266:37: note: candidates are:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note: void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&)
/usr/local/include/boost/thread/pthread/condition_variable.hpp:48:17: note:   no known conversion for argument 1 from ‘boost::mutex::scoped_lock {aka boost::detail::thread::scoped_lock<boost::mutex>}’ to ‘boost::unique_lock<boost::mutex>&’
/usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:57:14: note: template<class predicate_type> void boost::condition_variable::wait(boost::unique_lock<boost::mutex>&, predicate_type)
In file included from /usr/local/include/boost/thread/pthread/condition_variable_fwd.hpp:12:0,
                 from /usr/local/include/boost/thread/pthread/thread_data.hpp:16,
                 from /usr/local/include/boost/thread/pthread/condition_variable.hpp:10,
                 from /usr/local/include/boost/thread/condition_variable.hpp:16,
                 from /usr/local/include/boost/thread/pthread/shared_mutex.hpp:13,
                 from /usr/local/include/boost/thread/shared_mutex.hpp:16,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeadersBoost.h:33,
                 from /home/alexander/.ogre/OgreMain/include/Threading/OgreThreadHeaders.h:30,
                 from /home/alexander/.ogre/OgreMain/include/OgreStdHeaders.h:114,
                 from /home/alexander/.ogre/OgreMain/include/OgrePrerequisites.h:315,
                 from /home/alexander/.ogre/OgreMain/src/OgreAlignedAllocator.cpp:30:
/usr/local/include/boost/thread/locks.hpp: In constructor ‘boost::lock_guard<Mutex>::lock_guard(Mutex&) [with Mutex = boost::mutex]’:
/usr/local/include/boost/thread/pthread/thread_data.hpp:101:68:   instantiated from here
/usr/local/include/boost/thread/locks.hpp:257:13: error: ‘class boost::mutex’ has no member named ‘lock’
/usr/local/include/boost/thread/locks.hpp: In destructor ‘boost::lock_guard<Mutex>::~lock_guard() [with Mutex = boost::mutex]’:
/usr/local/include/boost/thread/pthread/thread_data.hpp:101:68:   instantiated from here
/usr/local/include/boost/thread/locks.hpp:264:13: error: ‘class boost::mutex’ has no member named ‘unlock’
/usr/local/include/boost/thread/locks.hpp: In member function ‘void boost::unique_lock<Mutex>::lock() [with Mutex = boost::mutex]’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:42:21:   instantiated from ‘boost::thread_cv_detail::lock_on_exit<MutexType>::~lock_on_exit() [with MutexType = boost::unique_lock<boost::mutex>]’
/usr/local/include/boost/thread/pthread/condition_variable.hpp:52:65:   instantiated from here
/usr/local/include/boost/thread/locks.hpp:412:13: error: ‘class boost::mutex’ has no member named ‘lock’
/usr/local/include/boost/thread/locks.hpp: In member function ‘void boost::unique_lock<Mutex>::unlock() [with Mutex = boost::mutex]’:
/usr/local/include/boost/thread/pthread/condition_variable.hpp:35:17:   instantiated from ‘void boost::thread_cv_detail::lock_on_exit<MutexType>::activate(MutexType&) [with MutexType = boost::unique_lock<boost::mutex>]’
/usr/local/include/boost/thread/pthread/condition_variable.hpp:54:29:   instantiated from here
/usr/local/include/boost/thread/locks.hpp:447:13: error: ‘class boost::mutex’ has no member named ‘unlock’
make[2]: *** [OgreMain/CMakeFiles/OgreMain.dir/src/OgreAlignedAllocator.cpp.o] Error 1
make[1]: *** [OgreMain/CMakeFiles/OgreMain.dir/all] Error 2
make: *** [all] Error 2
```Synaptic said that boost was already installed, I still took the newest source and compiled per other instructions in that same post. That worked, but it didn't change the Ogre error.

Help?

---

### Post by r.stiltskin on 2012-02-29
Which version of boost is installed?

---

### Post by Orpheon on 2012-03-01
> **r.stiltskin said:**
> Which version of boost is installed?
Huh. I have 2 Boost directories in the usr/include.
One has version 1_46_1 (the folder is named boost), and the other 1_34 (the folder is named boost_1_34, with another folder boost inside it).

---

### Post by r.stiltskin on 2012-03-01
The 1.46 is probably OK (but maybe not, as the [Ogre Wiki]("http://www.ogre3d.org/tikiwiki/Prerequisites#Boost") recommends Boost 1.44, which is very easy to get directly from boost.org and build yourself).

But your error messages, for example
```
/usr/local/include/boost/thread/locks.hpp:
```indicate that make is looking for boost in /usr/local/include and obviously not finding it because your boost is in /usr/include.  You can either change the Cmake parameter BOOST_INCLUDEDIR to direct it to /usr/include and try to build Ogre with your Boost 1.46. Or you can download Boost 1.44, build it and install it in /usr/local/include and let Cmake find it there.

---

