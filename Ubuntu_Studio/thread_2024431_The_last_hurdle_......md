---
title: "The last hurdle ....."
date: 2012-07-13
forum: Ubuntu Studio
---

### Post by Gusss on 2012-07-13
So finally got ./configure to finish but when I type make it all looks good until :

> 
./gui/qopenglplotter.h:193:5: error: ‘GLUquadricObj’ does not name a type
posixpathtools.h: In function ‘bool posixpathtools::getcwd(std::string&)’:
posixpathtools.h:141:27: warning: ignoring return value of ‘int fchdir(int)’, declared with attribute warn_unused_result [-Wunused-result]
make[2]: *** [ssr-controller.o] Error 1
make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
make: *** [all-recursive] Error 1
dew@ubuntu:~/Desktop/ssr-0.3.3$ 



anyone any ideas what needs to be done here ?

Just out of interest the end of ./configure looks like this :

> 
| Build with tracker support:
|    InterSense .............................. : no
|    Polhemus Fastrak ........................ : yes
|    Razor AHRS .............................. : yes
|
| Build with Ecasound support ................ : yes
| Build with IP interface .................... : yes
| Build with GUI ............................. : yes (floating)
| Build with new renderer base class ......... : no
|
| Enable debugging ........................... : no
| Enable optimization ........................ : yes
| Install prefix ............................. : /usr/local
|

Dont know if thats relevant Intersense is not massively impiortant though as its something Im not going to use.

---

### Post by Cheesemill on 2012-07-14
It would probably help if you told us what you were trying to install.....

---

### Post by Gusss on 2012-07-14
> **Cheesemill said:**
> It would probably help if you told us what you were trying to install.....

Sorry - this is a continuation of this thread :

[http://ubuntuforums.org/showthread.php?t=2024198](http://ubuntuforums.org/showthread.php?t=2024198)

all the details are there.

The following dependancies were installed :

JACK Audio Connection Kit [4]
- FFTW3 compiled for single precision (fftw3f) version 3.0 or higher [5]
- libsndfile [6]
- Ecasound [7]
- Trolltech’s Qt 4.2.2 or higher with OpenGL (QtCore, QtGui and QtOpenGL) [8]
- libxml2 [9]
- Boost.Asio [10], included since Boost version 1.35.

[4] Paul Davis et al. JACK Audio Connection Kit. [http://jackaudio.org](http://jackaudio.org).
[5] Matteo Frigo and Steven G. Johnson. FFTW3. [http://www.fftw.org](http://www.fftw.org).
[6] Erik de Castro Lopo. libsndfile. [http://www.mega-nerd.com/libsndfile](http://www.mega-nerd.com/libsndfile).
[7] Kai Vehmanen. Ecasound. [http://eca.cx/ecasound](http://eca.cx/ecasound).
[8] Trolltech. Qt4. [http://doc.trolltech.com/4.2](http://doc.trolltech.com/4.2).
[9] Daniel Veillard. Libxml2. [http://xmlsoft.org](http://xmlsoft.org).
[10] Boost C++ Libraries. [http://www.boost.org](http://www.boost.org).

---

### Post by CrocoDuck on 2012-07-14
After some rumination, even if configure didn't found any other unresolved dependencies, I would try to install libglu1-mesa-dev and/or libglw1-mesa-dev and/or libgl1-mesa-dev , as the definition of GLUquadricObj should be in one of those headers (I think)...

---

### Post by Gusss on 2012-07-14
> **CrocoDuck said:**
> After some rumination, even if configure didn't found any other unresolved dependencies, I would try to install libglu1-mesa-dev and/or libglw1-mesa-dev and/or libgl1-mesa-dev , as the definition of GLUquadricObj should be in one of those headers (I think)...

Roger that Croco-duck

---

### Post by Gusss on 2012-07-14
Hmmm still no joy. I did notice in the configure this though :

> configure: WARNING: Found Qt >= 4.7, forcing --enable-floating-control-panel!
checking Searching for non-default Boost include directory... none found.
checking boost/asio.hpp usability... yes
checking boost/asio.hpp presence... yes


Could this be a factor ?

---

### Post by CrocoDuck on 2012-07-14
Probably... I still feel smells of "needing for development libraries", as written at page 11 of the manual:

[I]Ensure that you really installed all libraries (lib) with devel-package (devel or
dev, where available) mentioned in section 2.3.1.
[/I]

I really hope that someone will correct me if I'm wrong. The good thing is that installing packages can't burn your system... Have a try to search for dev packages related to dependencies... Here a one that may be linked to our issue: libqt4-opengl-dev

---

### Post by Gusss on 2012-07-14
> **CrocoDuck said:**
> Probably... I still feel smells of "needing for development libraries", as written at page 11 of the manual:

[I]Ensure that you really installed all libraries (lib) with devel-package (devel or
dev, where available) mentioned in section 2.3.1.
[/I]

I really hope that someone will correct me if I'm wrong. The good thing is that installing packages can't burn your system... Have a try to search for dev packages related to dependencies... Here a one that may be linked to our issue: libqt4-opengl-dev

Well Ive tried to install every package now with the dev. The only one I had a problenm with is boost but that isnt really like the others . Im still sure the problem is to do with this line in the configure output :

> configure: WARNING: Found Qt >= 4.7, forcing --enable-floating-control-panel!
checking Searching for non-default Boost include directory... none found.

I cant help wondering what these two lines mean exactly (I know the second one has to do with setting directory paths but have no idea how to make sure the directory paths are correct)

> • Ensure that /etc/ld.so.conf or LD_LIBRARY_PATH are set properly, and run
ldconfig after changes.
• If a header is not installed in the standard paths of your system you can pass its
location to the configure script using ./configure CPPFLAGS=-Iyourpath.


---

### Post by CrocoDuck on 2012-07-15
> **Gusss said:**
> Well Ive tried to install every package now with the dev. The only one I had a problenm with is boost but that isnt really like the others . Im still sure the problem is to do with this line in the configure output :



I cant help wondering what these two lines mean exactly (I know the second one has to do with setting directory paths but have no idea how to make sure the directory paths are correct)

Ok, so we are sure that all the dependencies are ok. Use this

```
locate boost
```

and repost the output. I think that the issue is probably linked to qt and opengl related things, seeing the error while you hit make. We see a warning in the configure output, but as we not see errors I would say that configure had success enabling the floating control panel... Those issues are described here: [https://dev.qu.tu-berlin.de/projects/ssr/wiki/Known_Issues](https://dev.qu.tu-berlin.de/projects/ssr/wiki/Known_Issues)

Even if they should be solved on the current ssr release, we could try some of those (please, read that page):

```
./configure --enable-floating-control-panel
./configure LIBS=-lGL
./configure LIBS=-lpthread
./configure LIBS="-lGL -lpthread" 
```

---

### Post by Gusss on 2012-07-15
Locate boost :

> /host/Program Files (x86)/AVG/AVG2012/3rd_party/licenses/boost.txt
/host/Program Files (x86)/Image-Line/FL Studio 10/Data/Patches/Plugin presets/Effects/Fruity Multiband Compressor/Bass boost.fst
/host/Program Files (x86)/Image-Line/FL Studio 10/Data/Patches/Plugin presets/Effects/Fruity WaveShaper/Transient boost.fst
/host/Windows/SoftwareDistribution/Download/433767575943dacb697ee0558fc08c06/amd64_microsoft-windows-readyboostdriver_31bf3856ad364e35_6.1.7601.17514_none_72cb0bf60b9c95a5
/host/Windows/SoftwareDistribution/Download/433767575943dacb697ee0558fc08c06/amd64_microsoft-windows-readyboostdriver_31bf3856ad364e35_6.1.7601.17514_none_72cb0bf60b9c95a5/rdyboost.sys
/host/Windows/System32/drivers/rdyboost.sys
/host/Windows/inf/rdyboost
/host/Windows/inf/rdyboost/0000
/host/Windows/inf/rdyboost/0409
/host/Windows/inf/rdyboost/ReadyBoostPerfCounters.h
/host/Windows/inf/rdyboost/0000/ReadyBoostPerfCounters.ini
/host/Windows/inf/rdyboost/0409/ReadyBoostPerfCounters.ini
/host/Windows/winsxs/amd64_microsoft-windows-readyboostdriver_31bf3856ad364e35_6.1.7600.16385_none_7099f82e0eae120b
/host/Windows/winsxs/FileMaps/$$_inf_rdyboost_0000_50c61a1d7330c91d.cdf-ms
/host/Windows/winsxs/FileMaps/$$_inf_rdyboost_0409_50c6198d7330ca6a.cdf-ms
/host/Windows/winsxs/FileMaps/$$_inf_rdyboost_95e76b07334dd353.cdf-ms
/host/Windows/winsxs/Manifests/amd64_microsoft-windows-readyboostdriver_31bf3856ad364e35_6.1.7600.16385_none_7099f82e0eae120b.manifest
/host/Windows/winsxs/Manifests/amd64_microsoft-windows-readyboostdriver_31bf3856ad364e35_6.1.7601.17514_none_72cb0bf60b9c95a5.manifest
/host/Windows/winsxs/amd64_microsoft-windows-readyboostdriver_31bf3856ad364e35_6.1.7600.16385_none_7099f82e0eae120b/rdyboost.sys
/usr/lib/libboost_serialization.so.1.46.1
/usr/lib/libboost_wserialization.so.1.46.1
/usr/share/app-install/desktop/pianobooster:pianobooster.desktop
/usr/share/app-install/icons/pianobooster.png
/usr/share/doc/libboost-serialization1.46.1
/usr/share/doc/libboost-serialization1.46.1/NEWS.Debian.gz
/usr/share/doc/libboost-serialization1.46.1/README.Debian.gz
/usr/share/doc/libboost-serialization1.46.1/changelog.Debian.gz
/usr/share/doc/libboost-serialization1.46.1/copyright
/usr/share/lintian/overrides/libboost-serialization1.46.1
/usr/src/linux-headers-3.2.0-23/scripts/rt-tester/t4-l2-pi-deboost.tst
/usr/src/linux-headers-3.2.0-23/scripts/rt-tester/t5-l4-pi-boost-deboost-setsched.tst
/usr/src/linux-headers-3.2.0-23/scripts/rt-tester/t5-l4-pi-boost-deboost.tst
/var/lib/dpkg/info/libboost-serialization1.46.1.list
/var/lib/dpkg/info/libboost-serialization1.46.1.md5sums
/var/lib/dpkg/info/libboost-serialization1.46.1.postinst
/var/lib/dpkg/info/libboost-serialization1.46.1.postrm
/var/lib/dpkg/info/libboost-serialization1.46.1.shlibs
dew@ubuntu:~$ 


Im wondering if go into the file "qopenglplotter.h" there is a line :

>  bool _allow_displaying_text;
    /// Quadric necessary to plot spheres and disks 
    [COLOR="Red"]GLUquadricObj *_glu_quadric;[/COLOR]

    bool _plot_listener;

This is apparently where the problem is but I dont know what a type is let alone how to name one in this line.... still have " Searching for non-default Boost include directory... none found." but  ./configure --enable-floating-control-panel gets rid of the warning about the floating point though - so some progress has been made !

---

### Post by CrocoDuck on 2012-07-16
I think we should make sure that headers files are all in their natural location. If not, we have to run configure with the right options (I think). Repost the output of this:

```
ls -l /usr/include
```

---

### Post by Gusss on 2012-07-16
So I got a message from the developer :

> Thanks for trying the SSR, we are always interested in feedback!

Can you please open the file src/gui/qopenglplotter.h and add the line

#include <GL/glu.h>

somewhere around the other "include"-lines and then try to run "make" again?
This was a problem with Archlinux we found out recently, maybe it also applies to Ubuntu?

adding this line did indeed get us through the make process and to the make install :

> dew@ubuntu:~/Desktop/ssr-0.3.3$ sudo make install
[sudo] password for dew: 
Making install in src
make[1]: Entering directory `/home/dew/Desktop/ssr-0.3.3/src'
make[2]: Entering directory `/home/dew/Desktop/ssr-0.3.3/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c ssr '/usr/local/bin'
libtool: install: /usr/bin/install -c ssr /usr/local/bin/ssr
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
Making install in data
make[1]: Entering directory `/home/dew/Desktop/ssr-0.3.3/data'
make[2]: Entering directory `/home/dew/Desktop/ssr-0.3.3/data'
make[3]: Entering directory `/home/dew/Desktop/ssr-0.3.3/data'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/ssr" || /bin/mkdir -p "/usr/local/share/doc/ssr"
 /usr/bin/install -c -m 644 ssr.conf.example '/usr/local/share/doc/ssr'
test -z "" || /bin/mkdir -p ""
test -z "/usr/local/share/ssr" || /bin/mkdir -p "/usr/local/share/ssr"
/bin/mkdir -p '/usr/local/share/ssr/impulse_responses/wfs_prefilters'
 /usr/bin/install -c -m 644  impulse_responses/wfs_prefilters/wfs_prefilter_120_1500_44100.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1300_44100.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1300_48000.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1800_44100.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1800_48000.wav '/usr/local/share/ssr/impulse_responses/wfs_prefilters'
/bin/mkdir -p '/usr/local/share/ssr/impulse_responses/hrirs'
 /usr/bin/install -c -m 644  impulse_responses/hrirs/hrirs_fabian.wav impulse_responses/hrirs/hrirs_fabian_documentation.pdf '/usr/local/share/ssr/impulse_responses/hrirs'
/bin/mkdir -p '/usr/local/share/ssr/matlab_scripts'
 /usr/bin/install -c -m 644  matlab_scripts/prepare_hrirs_kemar.m matlab_scripts/make_wfs_prefilter.m '/usr/local/share/ssr/matlab_scripts'
/bin/mkdir -p '/usr/local/share/ssr/reproduction_setups'
 /usr/bin/install -c -m 644  reproduction_setups/2.0.asd reproduction_setups/2.1.asd reproduction_setups/5.1.asd reproduction_setups/rounded_rectangle.asd reproduction_setups/circle.asd reproduction_setups/loudspeaker_setup_with_nearly_all_features.asd '/usr/local/share/ssr/reproduction_setups'
test -z "/usr/local/share/ssr" || /bin/mkdir -p "/usr/local/share/ssr"
/bin/mkdir -p '/usr/local/share/ssr/images'
 /usr/bin/install -c -m 644  images/listener_background.png images/listener.png images/listener_shadow.png images/pause_button.png images/pause_button_pressed.png images/play_button.png images/play_button_pressed.png images/processing_button.png images/processing_button_pressed.png images/scene_menu_item.png images/scene_menu_item_selected.png images/skip_back_button.png images/skip_back_button_pressed.png images/source_shadow.png images/ssr_logo_large.png images/ssr_logo.png '/usr/local/share/ssr/images'
/bin/mkdir -p '/usr/local/share/ssr/impulse_responses/wfs_prefilters'
 /usr/bin/install -c -m 644  impulse_responses/wfs_prefilters/wfs_prefilter_120_1500_44100.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1300_44100.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1300_48000.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1800_44100.wav impulse_responses/wfs_prefilters/wfs_prefilter_100_1800_48000.wav '/usr/local/share/ssr/impulse_responses/wfs_prefilters'
/bin/mkdir -p '/usr/local/share/ssr/impulse_responses/hrirs'
 /usr/bin/install -c -m 644  impulse_responses/hrirs/hrirs_fabian.wav impulse_responses/hrirs/hrirs_fabian_documentation.pdf '/usr/local/share/ssr/impulse_responses/hrirs'
/bin/mkdir -p '/usr/local/share/ssr/reproduction_setups'
 /usr/bin/install -c -m 644  reproduction_setups/2.0.asd reproduction_setups/2.1.asd reproduction_setups/5.1.asd reproduction_setups/rounded_rectangle.asd reproduction_setups/circle.asd reproduction_setups/loudspeaker_setup_with_nearly_all_features.asd reproduction_setups/asdf2html.xsl '/usr/local/share/ssr/reproduction_setups'
 /usr/bin/install -c -m 644  asdf.xsd '/usr/local/share/ssr/.'
make  install-data-hook
make[4]: Entering directory `/home/dew/Desktop/ssr-0.3.3/data'
cd /usr/local/share/ssr \
	  && ln -s ` target="/usr/local/share/ssr"; common_part="/usr/local/share/ssr"; if test "x$target" = "x$common_part"; then echo .; exit; fi; back= ; while test "x${target#$common_part}" = "x$target"; do common_part="$(dirname "$common_part")"; back="../$back" ; done; echo "${back}${target#$common_part/}"`/impulse_responses/hrirs/hrirs_fabian.wav default_hrirs.wav
ln: failed to create symbolic link `default_hrirs.wav': File exists
make[4]: [install-data-hook] Error 1 (ignored)
cd /usr/local/share/ssr \
	  && ln -s ` target="/usr/local/share/ssr"; common_part="/usr/local/share/ssr"; if test "x$target" = "x$common_part"; then echo .; exit; fi; back= ; while test "x${target#$common_part}" = "x$target"; do common_part="$(dirname "$common_part")"; back="../$back" ; done; echo "${back}${target#$common_part/}"`/reproduction_setups/rounded_rectangle.asd default_setup.asd
ln: failed to create symbolic link `default_setup.asd': File exists
make[4]: [install-data-hook] Error 1 (ignored)
cd /usr/local/share/ssr \
	  && ln -s ` target="/usr/local/share/ssr"; common_part="/usr/local/share/ssr"; if test "x$target" = "x$common_part"; then echo .; exit; fi; back= ; while test "x${target#$common_part}" = "x$target"; do common_part="$(dirname "$common_part")"; back="../$back" ; done; echo "${back}${target#$common_part/}"`/impulse_responses/wfs_prefilters/wfs_prefilter_120_1500_44100.wav default_wfs_prefilter.wav
ln: failed to create symbolic link `default_wfs_prefilter.wav': File exists
make[4]: [install-data-hook] Error 1 (ignored)
make[4]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/data'
make[3]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/data'
make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/data'
make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/data'
Making install in android_ssr_remote
make[1]: Entering directory `/home/dew/Desktop/ssr-0.3.3/android_ssr_remote'
make[2]: Entering directory `/home/dew/Desktop/ssr-0.3.3/android_ssr_remote'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/android_ssr_remote'
make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/android_ssr_remote'
make[1]: Entering directory `/home/dew/Desktop/ssr-0.3.3'
Warning: doc/manual/SoundScapeRenderer.pdf is not generated by the Makefile!
make[2]: Entering directory `/home/dew/Desktop/ssr-0.3.3'
make[2]: Nothing to be done for `install-exec-am'.
Warning: doc/manual/SoundScapeRenderer.pdf is not generated by the Makefile!
test -z "/usr/local/share/doc/ssr" || /bin/mkdir -p "/usr/local/share/doc/ssr"
 /usr/bin/install -c -m 644 AUTHORS COPYING doc/SoundScapeRenderer-0.3.3-manual.pdf NEWS '/usr/local/share/doc/ssr'
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3'
make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3'


so it seems to be working - now if I can just work out how to get the gui open............. then I will post a picture of an exploding bottle of champaigne .

---

### Post by Gusss on 2012-07-16
[IMG]http://a.espncdn.com/photo/2008/1008/mlb_g_rays2_sw_580.jpg[/IMG]

---

### Post by Gusss on 2012-07-16
CrocoDuck what can I say - thanks again for all your help. At first I thought I would be alone with this problem but I was wrong - I guess people like yourself are what makes linux a strong and growing community - Im hooked !

---

### Post by CrocoDuck on 2012-07-17
> **Gusss said:**
> So I got a message from the developer :



adding this line did indeed get us through the make process and to the make install :



so it seems to be working - now if I can just work out how to get the gui open............. then I will post a picture of an exploding bottle of champaigne .

\\:D/ AWWW YEAH... I'm very happy to have been useful, in my little. If everything is ok (:biggrin:) mark the thread as solved. Best regards and have fun with the cool open source software!

---

