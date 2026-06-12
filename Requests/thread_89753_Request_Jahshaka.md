---
title: "Request: Jahshaka"
date: 2005-11-13
forum: Requests
---

### Post by reuben on 2005-11-13
It would be great if ubuntu supported this directly, since it would be a powerful part of the multimedia resources (also cinelerra and transcode).

It can install & work via dpkg, but it has an invalid dependency.

---

### Post by giacomolg on 2006-05-04
I agree. **My vote for Jahshaka **being in the supported repos

---

### Post by lewmnik on 2006-05-20
Yes! this is a good one:D  It feels, looks and makes professional quality all around video editing. So yes we need it!

---

### Post by lithorus on 2006-06-01
Would be great with this app in the backports repository.

Edit:

Found that they have already built it for Dapper :
[http://repo.jahshaka.org/ubuntu/dapper/binary-i386/](http://repo.jahshaka.org/ubuntu/dapper/binary-i386/)

---

### Post by adibudeen on 2006-06-02
Huzzah!!!  I'll let you know if I get it working.

---

### Post by adibudeen on 2006-06-04
I got it working, and most of it works just fine.  There is, however, one setback I've encountered.  I was curious if any of you had the same problem.  When I playback effects alone, they are fine.  When I add any of them to my editing timeline and playback the entire thing, it is slow and choppy.

I even tested exporting a finished video to see if it would still be slow and choppy, but it was smooth and fluid in the exported mpeg.

Have any of you encountered this problem.  The Jahshaka forums indicate that they've had problems with the AMD Athlon XP processor, which is exactly what I have.

Thanks

---

### Post by dangermouse28 on 2006-06-06
Hi

This might be a stupid question but I'll ask it anyway - do you install all the .deb files in the repository?

Thanks

Edit: It's ok - found the answer in the "Jahshaka repo" thread :)

---

### Post by myst3rious on 2006-11-10
what about Jahshaka Binary for Edgy and i686 optimzed... :D 
Since it have realtime rendering and preview, the i686 version
with a lot safe optimization would be a great gift.

---

### Post by Adler on 2008-01-14
Hi All,

Are there repos for Gutsy?

I think that I've outgrown recordMyDesktop.

There is a real need for an open source video editor.

Adler

---

### Post by ealott on 2008-01-24
It would be great if there was a repo for Gutsy!  I have not found one yet though.

I tried compiling Jahshaka 2, only to get the following errors when compiling the opengpulib stuff.

I'm running AMD 64 x2 with Gutsy 64 bit edition.
Looks like the dapper repo has version 2 of Jahshaka in a .deb.
Not for x64 though :(

```
evan@evan-desktop:~/Desktop/jahshaka$ ./configure
>>Configuring build type for jahshaka

Project MESSAGE: Jahshaka 2.0 build system
Project MESSAGE: -----------------------------
Project MESSAGE: 
Project MESSAGE: Checking operating system and paths
Project MESSAGE: 
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Project MESSAGE: 
Project MESSAGE: JAHPREFIX=\"/usr/local\" _THREAD_SAFE=true JAHTHEMES JAHGIFT NVIDIA_GPU JAHSCRIPT JAHLINUX
Project MESSAGE: /usr/include/freetype2 /usr/local/include /usr/include
Project MESSAGE: 
Project MESSAGE: Building Jahshaka 2.0
Project MESSAGE: ---------------------
Project MESSAGE: 
Project MESSAGE: Configuring Subsystems
Project MESSAGE: ----------------------
Project MESSAGE: 
Project MESSAGE: >> Configuring Auxillary Libraries
Project MESSAGE: 
Project MESSAGE: >> Configuring OpenLibraries
Project MESSAGE: Configuring Jahshaka
Project MESSAGE: --------------------
Project MESSAGE: 
Project MESSAGE: Configuring JahCore
Project MESSAGE: Configuring JahDesktop
Project MESSAGE: Configuring JahLibraries
Project MESSAGE: Configuring JahModules
Project MESSAGE: Configuring JahSource
Project MESSAGE: Configuring JahWidgets
Project MESSAGE: Configuring Jahshaka Linker
Project MESSAGE: 
Project MESSAGE: Finished Configuring Subsystems
Project MESSAGE: -------------------------------
Project MESSAGE: 
Project MESSAGE: Configuring Plugin Support
Project MESSAGE:  
Project MESSAGE: Make files have been configured
Project MESSAGE: type make to build
Project MESSAGE: 
Project MESSAGE: please file all bugs at http://bugs.jahshaka.org
Project MESSAGE: 

SUMMARY

     Configuration complete.

     Building         = jahshaka
     Install prefix   = /usr/local
     Debug            = true
     Static libs      = false
     Building plugins = true
     OpenAL framework = false

BUILD AND INSTALL

     To build the application and plugins, run:

     $ make

     To install, run this as your superuser:

     # make install

evan@evan-desktop:~/Desktop/jahshaka$ make
cd source/AuxiliaryLibraries && make -f Makefile
make[1]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries'
qmake -o Makefile AuxiliaryLibraries.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Project MESSAGE: Configuring AuxilliaryLibraries
Project MESSAGE: -------------------------------
make[1]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries'
make[1]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries'
cd blur && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
qmake -o Makefile blur.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
qmake -o Makefile FTGL.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
qmake -o Makefile particle.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
qmake -o Makefile apollon.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
cd gift && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
qmake -o Makefile gift.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
cd spaceball && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
qmake -o Makefile spaceball.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
cd glew && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
qmake -o Makefile glew.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[1]: Leaving directory `/home/evan/Desktop/jahshaka/source/AuxiliaryLibraries'
cd source/OpenLibraries && make -f Makefile
make[1]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries'
qmake -o Makefile OpenLibraries.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Project MESSAGE: Configuring OpenLibraries
Project MESSAGE: -------------------------
make[1]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries'
make[1]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries'
cd opencore && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opencore'
qmake -o Makefile opencore.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opencore'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opencore'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opencore'
cd openassetlib/v2_openassetlib/sqlite3 && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib/sqlite3'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib/sqlite3'
cd openassetlib/v2_openassetlib && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib/v2_openassetlib'
cd openassetlib && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib'
qmake -o Makefile openassetlib.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/openassetlib'
cd opengpulib && make -f Makefile
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opengpulib'
qmake -o Makefile opengpulib.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opengpulib'
make[2]: Entering directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opengpulib'
g++ -c -pipe -Wall -W -g -D_REENTRANT -fPIC  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DOPENGPULIB_EXPORTS -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o gpumathlib.o gpumathlib.cpp
In file included from gpumathlib.cpp:10:
gpumathlib.h:17:21: error: GL/glew.h: No such file or directory
glsl_objects.h:22: error: ‘GLhandleARB’ does not name a type
glsl_objects.h:26: error: ‘GLenum’ has not been declared
glsl_objects.h:27: error: expected `)' before ‘type’
glsl_objects.h:30: error: ISO C++ forbids declaration of ‘GLhandleARB’ with no type
glsl_objects.h:30: error: expected ‘;’ before ‘*’ token
glsl_objects.h:31: error: expected `;' before ‘char’
glsl_objects.h:38: error: ‘GLhandleARB’ does not name a type
glsl_objects.h:42: error: ISO C++ forbids declaration of ‘GLhandleARB’ with no type
glsl_objects.h:42: error: expected ‘;’ before ‘*’ token
glsl_objects.h:43: error: expected `;' before ‘bool’
gpumathlib.h:546: error: ‘GLuint’ has not been declared
gpumathlib.h:547: error: ‘GLuint’ has not been declared
gpumathlib.h:555: error: variable or field ‘readTextureSubImageUchar’ declared void
gpumathlib.h:555: error: ‘GLuint’ was not declared in this scope
gpumathlib.h:555: error: expected primary-expression before ‘int’
gpumathlib.h:555: error: expected primary-expression before ‘int’
gpumathlib.h:556: error: expected primary-expression before ‘int’
gpumathlib.h:556: error: expected primary-expression before ‘int’
gpumathlib.h:557: error: expected primary-expression before ‘unsigned’
gpumathlib.h:557: error: expected primary-expression before ‘int’
gpumathlib.h:557: error: expected primary-expression before ‘int’
gpumathlib.h:557: error: initializer expression list treated as compound expression
gpumathlib.h:559: error: variable or field ‘createEmpty2DTexture’ declared void
gpumathlib.h:559: error: ‘GLuint’ was not declared in this scope
gpumathlib.h:559: error: ‘texture_id_ptr’ was not declared in this scope
gpumathlib.h:559: error: ‘GLenum’ was not declared in this scope
gpumathlib.h:559: error: expected primary-expression before ‘int’
gpumathlib.h:559: error: expected primary-expression before ‘int’
gpumathlib.h:559: error: initializer expression list treated as compound expression
gpumathlib.h:578: error: variable or field ‘loadJahshakaBasicArb’ declared void
gpumathlib.h:578: error: ‘GLint’ was not declared in this scope
gpumathlib.h:578: error: ‘GLint’ was not declared in this scope
gpumathlib.h:578: error: expected primary-expression before ‘float’
gpumathlib.h:579: error: expected primary-expression before ‘unsigned’
gpumathlib.h:580: error: ‘GLuint’ was not declared in this scope
gpumathlib.h:580: error: ‘vertex_program_handle’ was not declared in this scope
gpumathlib.h:580: error: initializer expression list treated as compound expression
gpumathlib.h:582: error: ‘GLubyte’ was not declared in this scope
gpumathlib.h:582: error: ‘fragment_program’ was not declared in this scope
gpumathlib.h:583: error: ‘GLubyte’ was not declared in this scope
gpumathlib.h:583: error: ‘string’ was not declared in this scope
gpumathlib.cpp: In function ‘bool jahstd::glslSupport()’:
gpumathlib.cpp:59: error: ‘GLEW_VERSION_2_0’ was not declared in this scope
gpumathlib.cpp:60: error: ‘GLEW_ARB_fragment_shader’ was not declared in this scope
gpumathlib.cpp:61: error: ‘GLEW_ARB_vertex_shader’ was not declared in this scope
gpumathlib.cpp:61: error: ‘GLEW_ARB_shader_objects’ was not declared in this scope
gpumathlib.cpp:62: error: ‘GLEW_ARB_shading_language_100’ was not declared in this scope
gpumathlib.cpp: At global scope:
gpumathlib.cpp:149: error: variable or field ‘readTextureSubImageUchar’ declared void
gpumathlib.cpp:149: error: redefinition of ‘int readTextureSubImageUchar’
gpumathlib.h:555: error: ‘int readTextureSubImageUchar’ previously defined here
gpumathlib.cpp:149: error: ‘GLuint’ was not declared in this scope
gpumathlib.cpp:149: error: expected primary-expression before ‘int’
gpumathlib.cpp:149: error: expected primary-expression before ‘int’
gpumathlib.cpp:150: error: expected primary-expression before ‘int’
gpumathlib.cpp:150: error: expected primary-expression before ‘int’
gpumathlib.cpp:151: error: expected primary-expression before ‘unsigned’
gpumathlib.cpp:151: error: expected primary-expression before ‘int’
gpumathlib.cpp:151: error: expected primary-expression before ‘int’
gpumathlib.cpp: In function ‘void check_gl()’:
gpumathlib.cpp:862: error: ‘GLenum’ was not declared in this scope
gpumathlib.cpp:862: error: expected `;' before ‘error’
gpumathlib.cpp:863: error: ‘error’ was not declared in this scope
gpumathlib.cpp:863: error: ‘glGetError’ was not declared in this scope
gpumathlib.cpp:863: error: ‘GL_NO_ERROR’ was not declared in this scope
gpumathlib.cpp:864: error: ‘gluErrorString’ was not declared in this scope
gpumathlib.cpp: In function ‘void find_shader_program_error(unsigned char*, char*)’:
gpumathlib.cpp:901: error: ‘GLint’ was not declared in this scope
gpumathlib.cpp:901: error: expected `;' before ‘pos’
gpumathlib.cpp:914: error: ‘GL_PROGRAM_ERROR_POSITION_NV’ was not declared in this scope
gpumathlib.cpp:914: error: ‘pos’ was not declared in this scope
gpumathlib.cpp:914: error: ‘glGetIntegerv’ was not declared in this scope
gpumathlib.cpp:954: error: ‘GL_PROGRAM_ERROR_STRING_ARB’ was not declared in this scope
gpumathlib.cpp:954: error: ‘glGetString’ was not declared in this scope
gpumathlib.cpp: In function ‘void getMVPMatrices(float*, float*, float*, float*, float*)’:
gpumathlib.cpp:1026: error: ‘GL_MODELVIEW_MATRIX’ was not declared in this scope
gpumathlib.cpp:1026: error: ‘glGetFloatv’ was not declared in this scope
gpumathlib.cpp:1027: error: ‘GL_PROJECTION_MATRIX’ was not declared in this scope
gpumathlib.cpp:1028: error: ‘GL_TEXTURE_MATRIX’ was not declared in this scope
gpumathlib.cpp: At global scope:
gpumathlib.cpp:1308: error: variable or field ‘loadJahshakaBasicArb’ declared void
gpumathlib.cpp:1308: error: redefinition of ‘int loadJahshakaBasicArb’
gpumathlib.h:578: error: ‘int loadJahshakaBasicArb’ previously defined here
gpumathlib.cpp:1308: error: ‘GLint’ was not declared in this scope
gpumathlib.cpp:1308: error: ‘GLint’ was not declared in this scope
gpumathlib.cpp:1308: error: expected primary-expression before ‘float’
gpumathlib.cpp:1309: error: expected primary-expression before ‘unsigned’
gpumathlib.cpp:1310: error: ‘GLuint’ was not declared in this scope
gpumathlib.cpp:1310: error: ‘vertex_program_handle’ was not declared in this scope
gpumathlib.cpp: In function ‘void debug_arbdata()’:
gpumathlib.cpp:1332: error: ‘GLint’ was not declared in this scope
gpumathlib.cpp:1332: error: expected `;' before ‘max_fragment_instructions’
gpumathlib.cpp:1333: error: expected `;' before ‘max_vertex_instructions’
gpumathlib.cpp:1336: error: ‘GL_FRAGMENT_PROGRAM_ARB’ was not declared in this scope
gpumathlib.cpp:1337: error: ‘GL_MAX_PROGRAM_INSTRUCTIONS_ARB’ was not declared in this scope
gpumathlib.cpp:1338: error: ‘max_fragment_instructions’ was not declared in this scope
gpumathlib.cpp:1338: error: ‘glGetProgramivARB’ was not declared in this scope
gpumathlib.cpp:1343: error: ‘GL_VERTEX_PROGRAM_ARB’ was not declared in this scope
gpumathlib.cpp:1345: error: ‘max_vertex_instructions’ was not declared in this scope
gpumathlib.cpp: At global scope:
gpumathlib.cpp:1351: error: redefinition of ‘bool isAnARBFPInstruction’
gpumathlib.h:583: error: ‘bool isAnARBFPInstruction’ previously defined here
gpumathlib.cpp:1351: error: ‘GLubyte’ was not declared in this scope
gpumathlib.cpp:1351: error: ‘string’ was not declared in this scope
gpumathlib.cpp:1374: error: redefinition of ‘int countARBFPInstructions’
gpumathlib.h:582: error: ‘int countARBFPInstructions’ previously defined here
gpumathlib.cpp:1374: error: ‘GLubyte’ was not declared in this scope
gpumathlib.cpp:1374: error: ‘fragment_program’ was not declared in this scope
gpumathlib.cpp: In function ‘bool checkComplexArbSupport(QString, int, int)’:
gpumathlib.cpp:1412: error: ‘countARBFPInstructions’ cannot be used as a function
make[2]: *** [gpumathlib.o] Error 1
make[2]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries/opengpulib'
make[1]: *** [sub-opengpulib] Error 2
make[1]: Leaving directory `/home/evan/Desktop/jahshaka/source/OpenLibraries'
make: *** [sub-source-OpenLibraries] Error 2

```

---

### Post by Adler on 2008-01-24
> Looks like the dapper repo has version 2 of Jahshaka in a .deb.

ealott,

Do you have the .deb URL for the Gutsy repository? I'm running Linux Mint Daryna, and could dial that repository into my list of application sources.

Thanks in advance for your reply.

Adler

---

### Post by anv on 2008-01-25
Here too... vote for Jahshaka ...

---

### Post by Adler on 2008-01-26
anv,

Do you have a Gutsy repository?

Adler

---

### Post by Squish on 2008-02-16
Votes for jahshaka!

---

### Post by diablo75 on 2008-04-20
Has anyone installed Jahshaka on 8.04 yet?  Anybody know how to install it?

---

### Post by sepius on 2008-10-04
My vote as well.  I use Jahshaka on my Laptop running Mandriva.  It is in the Mandriva base repo for 2008, but no support in 2008.1, you can see it, but cannot get it, which is o.k, Mandriva 2008.1 is between KDE 3.5 and 4.0 and is a bit dodge.

I'd rather use it on this system as it is the one I mainly use for Video editing, this one being the one running Ubuntu.

---

