---
title: "glc: Can't find glc libraries"
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by zcout on 2009-11-25
Hello, I'm trying to install glc on my Ubuntu 9.10 (32 bit) and I get this error: "Can't find glc libraries". Can anyone help?

```
mk@mk-desktop:~/glc$ ./glc-build.sh 
info  : Welcome to glc install script!
        Enter path where glc will be installed.
          (leave blank to install to root directory)
      > ~/glc/glc
        Enter compiler optimizations.
          (-O2 -msse -mmmx -fomit-frame-pointer -mtune=pentium3)
      > -march=i386 -O2 -pipe -fomit-frame-pointer
        Use git (y/n)
          (git contains latest unstable development version)
      > n
info  : Fetching sources...
info  : Unpacking sources...
info  : Building elfhacks...
CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

info  : Building packetstream...
CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

info  : Building glc...
CMake Warning (dev) at src/CMakeLists.txt:28 (ADD_EXECUTABLE):
  Policy CMP0003 should be set before this line.  Add code such as

    if(COMMAND cmake_policy)
      cmake_policy(SET CMP0003 NEW)
    endif(COMMAND cmake_policy)

  as early as possible but after the most recent call to
  cmake_minimum_required or cmake_policy(VERSION).  This warning appears
  because target "play" links to some libraries for which the linker must
  search:

    GL, asound, X11, m, png

  and other libraries with known full path:

    /home/mk/glc/packetstream/build/src/libpacketstream.so

  CMake is adding directories in the second list to the linker search path in
  case they are needed to find libraries from the first list (for backwards
  compatibility with CMake 2.4).  Set policy CMP0003 to OLD or NEW to enable
  or disable this behavior explicitly.  Run "cmake --help-policy CMP0003" for
  more information.
This warning is for project developers.  Use -Wno-dev to suppress it.

/home/mk/glc/glc/src/capture.c: In function &#8216;set_opt&#8217;:
/home/mk/glc/glc/src/capture.c:338: warning: ignoring return value of &#8216;getcwd&#8217;, declared with attribute warn_unused_result
/home/mk/glc/glc/src/glc/common/state.c: In function &#8216;glc_state_time_add_diff&#8217;:
/home/mk/glc/glc/src/glc/common/state.c:157: warning: format &#8216;%ld&#8217; expects type &#8216;long int&#8217;, but argument 5 has type &#8216;glc_stime_t&#8217;
/home/mk/glc/glc/src/glc/core/file.c: In function &#8216;file_set_target&#8217;:
/home/mk/glc/glc/src/glc/core/file.c:139: warning: ignoring return value of &#8216;ftruncate&#8217;, declared with attribute warn_unused_result
/home/mk/glc/glc/src/glc/core/info.c: In function &#8216;video_frame_info&#8217;:
/home/mk/glc/glc/src/glc/core/info.c:330: warning: format &#8216;%lu&#8217; expects type &#8216;long unsigned int&#8217;, but argument 3 has type &#8216;glc_utime_t&#8217;
/home/mk/glc/glc/src/glc/core/info.c: In function &#8216;audio_data_info&#8217;:
/home/mk/glc/glc/src/glc/core/info.c:406: warning: format &#8216;%lu&#8217; expects type &#8216;long unsigned int&#8217;, but argument 3 has type &#8216;glc_utime_t&#8217;
/home/mk/glc/glc/src/glc/core/info.c:407: warning: format &#8216;%ld&#8217; expects type &#8216;long int&#8217;, but argument 3 has type &#8216;glc_size_t&#8217;
info  : Installing elfhacks...
info  : Installing packetstream...
info  : Installing glc...
info  : Done :)
info  : You may need to add following lines to your .bashrc:
export PATH="${PATH}:~/glc/glc/bin"
export LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:~/glc/glc/lib"
info  : If you want to remove glc, execute:
sudo rm \
~/glc/glc/lib/libglc-core.so* \
~/glc/glc/lib/libglc-capture.so* \
~/glc/glc/lib/libglc-play.so* \
~/glc/glc/lib/libglc-export.so* \
~/glc/glc/lib/libglc-hook.so* \
~/glc/glc/lib/libelfhacks.so* \
~/glc/glc/lib/libpacketstream.so* \
~/glc/glc/include/elfhacks.h \
~/glc/glc/include/packetstream.h \
~/glc/glc/bin/glc-capture \
~/glc/glc/bin/glc-play
mk@mk-desktop:~/glc$ export PATH="${PATH}:~/glc/glc/bin"
mk@mk-desktop:~/glc$ export LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:~/glc/glc/lib"
mk@mk-desktop:~/glc$ cd glc/bin/
mk@mk-desktop:~/glc/glc/bin$ ./glc-capture 
Can't find glc libraries
```

---

### Post by carlinuxlearner on 2009-12-27
Bump... I have the same problem.

---

### Post by AutoStatic on 2009-12-27
> mk@mk-desktop:~/glc$ ./glc-build.sh 
info  : Welcome to glc install script!
        Enter path where glc will be installed.
          (leave blank to install to root directory)
      > ~/glc/glc


Try */usr/local*
If you install it in another directory the libs will not be found because your system expects them to be in either */lib*, */usr/lib* or */usr/local/lib*

---

