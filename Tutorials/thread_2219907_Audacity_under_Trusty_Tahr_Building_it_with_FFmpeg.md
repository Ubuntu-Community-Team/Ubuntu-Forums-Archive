---
title: "Audacity under Trusty Tahr: Building it with FFmpeg"
date: 2014-04-25
forum: Tutorials
---

### Post by andrew.46 on 2014-04-25
------------------------------------------
***[COLOR="#FF0000"]A fix for this problem is available in the development version of Audacity and a patched version of Audacity will arrive in Trusty soon enough. So this guide is now of historical interest only and will close soon.....[/COLOR]***
------------------------------------------


This 'mini-guide' is aimed at giving Trusty Tahr users access to the import/export function of Audacity via FFmpeg, a functionality not available with the Repository version of Audacity. Only a couple of easy steps involved:

**Build tools...**

The following build tools are required and we also create a working area for the source code. Copy the entire code block and paste into Terminal window:

```

sudo apt-get -y install build-essential checkinstall yasm && \
mkdir -pv $HOME/audacity_build

```

**Development Files...**

The following development files will be used by both Audacity and by a special *local* installation of FFmpeg. Copy the entire code block and paste into Terminal window:

```

sudo apt-get -y install libwxgtk2.8-0 libwxgtk2.8-dev libsndfile1-dev \
libsoxr-dev libexpat1-dev libgtk2.0-dev libasound2-dev libmad0-dev \
libportaudio-dev libflac++-dev libid3tag0-dev libsbsms-dev libsoundtouch-dev \
libtwolame-dev libportaudio-dev libmp3lame-dev libid3tag0-dev libfaac-dev \
libopencore-amrnb-dev libopencore-amrwb-dev

```

**FFmpeg...**

This is the piece that is missing from Trusty and for this we will build a specially customised *local* version that will not interfere with any *system* FFmpeg libraries. (If you are building for a shared computer with multiple users another option would be to install to /opt, ask in the thread below). Copy the entire code block and paste into Terminal window:

```

cd $HOME/audacity_build && \
wget http://www.ffmpeg.org/releases/ffmpeg-0.10.12.tar.bz2 && \
tar xvf ffmpeg-0.10.12.tar.bz2 && cd ffmpeg-0.10.12 && \
./configure --prefix=$HOME/audacity_build/audacity_deps/usr \
            --enable-libfaac \
            --enable-libopencore-amrnb \
            --enable-libopencore-amrwb \
            --enable-libvorbis \
            --enable-libmp3lame \
            --enable-shared \
            --disable-static \
            --disable-doc \
            --disable-ffmpeg \
            --disable-ffplay \
            --disable-ffprobe \
            --disable-ffserver \
            --disable-filters \
            --disable-bsfs \
            --disable-protocols \
            --disable-debug \
            --disable-hwaccels \
            --disable-encoder=aac \
            --disable-encoder=vorbis \
            --enable-nonfree \
            --enable-version3 && \
make -j 2 && make install-libs install-headers && make distclean

```

After installing Audacity I will give instructions so Audacity can *find* this local installation, this will be done manually.

**Compile Audacity...**

Here we download the Audacity source code, compile it, package and install it. Copy the entire code block and paste into Terminal window:

```

cd $HOME/audacity_build && \
wget http://audacity.googlecode.com/files/audacity-minsrc-2.0.5.tar.xz && \
tar xvf audacity-minsrc-2.0.5.tar.xz && cd audacity-src-2.0.5 && \
PKG_CONFIG_PATH="$HOME/audacity_build/audacity_deps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local --with-ffmpeg && \
make -j 2 && \
mkdir -vp doc-pak && cp -v LICENSE.txt README.txt doc-pak && \
sudo checkinstall --pakdir "$HOME/audacity_build" --backup=no --deldoc=yes  \
                  --pkgname audacity --pkgversion "3.2.0.5" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

**Using the FFmpeg libraries...**

To access the FFmpeg libraries from within Audacity you must show Audacity location of the libraries. Look for Edit --> Preferences --> Libraries -> FFmpeg Libraries --> Locate --> Browse and select the file:

```

 $HOME/audacity_build/audacity_deps/usr/lib/libavformat.so

```

 Of course you will not see '$HOME' in the 'Browse' box this must be replaced with *your* $HOME details, if you are not sure what your details are run the following in a Terminal:

```

echo $HOME

```

and this will give you the information you need. You can check if you have been successful by looking in *$HOME/.audacity-data/audacity.cfg* and look for a line similar to this:

```

[FFmpeg]
Enabled=1
FFmpegLibPath=/home/andrew/audacity_build/audacity_deps/usr/lib/libavformat.so

```

And now you will have access to the Import/Export functions of Audacity through FFmpeg!

**In conclusion...**

I am hoping that this 'mini-guide' will be useful to Audacity users under Trusty, let me know if I have missed something and I will do my best to fill in the details. And in the meantime: 'Have fun!!.

---

### Post by erind on 2014-04-25
Thanks for the guide!  Coincidentally today I installed manually ffmpeg 0.10.12 and audacity from the repos, but I wasn't sure I had everything right, so I completely uninstalled audacity and followed your guide to reinstall it, (reinstalled ffmpeg too). Everything went smoothly, export to MP3 works fine, so far so good.

---

### Post by andrew.46 on 2014-04-25
Good to hear it all worked :)

---

### Post by ron998 on 2014-04-25
> **andrew.46 said:**
> ... it all worked :)
Hi
I followed the mini-guide with audacity from **svn**. It's OK. :P

(imho)
It would be an improvement if we could store the FFmpeg library
somewhere more secure than "$HOME/audacity_build/audacity_deps/usr/lib/libavformat.so".

These are the config options that I used with FFmpeg-0.10.12.
```
[SIZE=1]./configure \
--prefix=$HOME/audacity_build/audacity_deps/usr \
--enable-nonfree \
--enable-version3 \
--enable-libfaac \
--enable-libgsm \
--enable-libopencore-amrnb \
--enable-libopencore-amrwb \
--enable-libspeex \
--enable-libvo-amrwbenc \
--enable-shared \
--disable-static \
--disable-avdevice \
--disable-avfilter \
--disable-bsfs \
--disable-doc \
--disable-ffmpeg \
--disable-ffplay \
--disable-ffprobe \
--disable-ffserver \
--disable-filters \
--disable-hwaccels \
--disable-postproc \
--disable-swresample \
--disable-swscale[/SIZE]
```

EDIT
There's a folder here ---> **/usr/local/share/audacity**
I've put the **audacity_deps/usr** folder inside.

---

### Post by vasa1 on 2014-04-26
> **andrew.46 said:**
> Good to hear it all worked :)
@**andrew.46**, Worked for me too :)

But I was totally nervous because this was my first ever compile. Thank you for having everything laid out stepwise. 

BTW, this is on Lubuntu 14.04.

---

### Post by andrew.46 on 2014-04-26
> **vasa1 said:**
> But I was totally nervous because this was my first ever compile. Thank you for having everything laid out stepwise.

Good to hear that it has all worked out for you. The guide is designed so that those who have less experience with compiling will not be put off by complexity :).

---

### Post by andrew.46 on 2014-04-26
> **ron998 said:**
> 
(imho)
It would be an improvement if we could store the FFmpeg library
somewhere more secure than "$HOME/audacity_build/audacity_deps/usr/lib/libavformat.so".

Could very well be true, I have left a brief not about a possible installation in /opt but not given great details, perhaps I will flesh this out a little. I have some horror of getting the FFmpeg libraries tangled up in the complex dependency arrangements of Debian / Ubuntu :(.

> These are the config options that I used with FFmpeg-0.10.12.

Looks better than the ones I have suggested so next weekend I may very well add some of those in :). I actually also had libvo_aacenc in place which seemed to be the better aac encoder for the older FFmpeg but it produced quite terrible aac from Audacity so I quietly removed it!

---

### Post by ron998 on 2014-04-26
> **andrew.46 said:**
> ... also had libvo_aacenc in place...
Hi
The Audacity page here looks very interesting ---> [http://manual.audacityteam.org/o/man/exporting_to_an_external_program.html](http://manual.audacityteam.org/o/man/exporting_to_an_external_program.html)
Allows to export audio using command line programs... lame, FFmpeg etc.
Probably fdkaac and opusenc too.

But the FFmpeg option seems versatile. :cool:

Maybe this is the way to go...
For imports use FFmpeg-0.10.12 libary with --enable-whatever to add extra **de**coders.
(Also disable some **en**coders, as in the mini-guide --disable-encoder=whatever).
And use the system (or self-compiled) FFmpeg with bells and whistles for exports that Audacity can't handle.
(Or FFmpeg static build from [http://ffmpeg.gusari.org/static](http://ffmpeg.gusari.org/static)).


This example worked OK. :P
```
ffmpeg -i - -c:a libfdk_aac -vbr 3 -ar 44100 -ac 2 "%f"
```
And this one.
```
fdkaac -m 3 -o "%f" -
```

---

### Post by andrew.46 on 2014-04-26
> **ron998 said:**
> The Audacity page here looks very interesting ---> [http://manual.audacityteam.org/o/man/exporting_to_an_external_program.html](http://manual.audacityteam.org/o/man/exporting_to_an_external_program.html)
Allows to export audio using command line programs... lame, FFmpeg etc.

Indeed it does look very interesting! I am not sure if Audacity users are by nature commandline tinkerers so it would be interesting to know if many are using this pretty flexible part of the application. As for myself I am going to jump into some of the Audacity menus and explore some of those pretty amazing looking options :).

I am hoping that in some time the need for this guide will be gone when in a future release Audacity learns to cope with a newer FFmpeg but as a quick reading of the Audacity Forums seems to indicate this is probably not the major thrust of their work...

---

### Post by livewirebt2 on 2014-04-26
This is interesting. I haven't used Audacity with 14.04 until now. I have [reported a bug]("https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/1313211") for this issue, as I couldn't find one.

I assume it's releated to ffmpeg being dropped from the repositories and package maintainers threw out the baby with the bathwater by removing the build flag from the package, which couldn't be any more wrong, because the actual ffmpeg package was replaced by a transitional(!) package from libav sources long ago (see also: AU - [Is FFmpeg missing from the official repositories in 14.04?]("http://askubuntu.com/q/432542/40581")).

**Please hit the "affects me too" button on the page of the bugreport.**

---

### Post by andrew.46 on 2014-04-26
> **livewirebt2 said:**
> I assume it's releated to ffmpeg being dropped from the repositories and package maintainers threw out the baby with the bathwater by removing the build flag from the package, which couldn't be any more wrong, because the actual ffmpeg package was replaced by a transitional(!) package from libav sources long ago (see also: AU - [Is FFmpeg missing from the official repositories in 14.04?]("http://askubuntu.com/q/432542/40581")).

I suspect that this issue has little to do with the FFmpeg / Libav situation as *neither* modern version will work with Audacity. The situation is more that Audacity developers have not had the time to dedicate to keeping up with continuing changes from both camps. The emphasis of Audacity developers is doubtless on building and developing Audacity itself rather than trying to keep pace with the rapid changes in what is essentially a very sophisticated import and export plugin. Nice to have but not essential...

This guide attempts to give the FFmpeg functionality back to Audacity, at least for Trusty, until changes in Audacity will eventually render the guide redundant; could be a while though :).

---

### Post by ron998 on 2014-04-26
> **andrew.46 said:**
> ... The situation is more that Audacity developers have not had the time to dedicate to keeping up with continuing changes....
Hi
They had this trouble with SoX, said FFmpeg was a moving target, so they dropped it.
Now they advise to use FFmpeg to import/export to SoX through a pipe.
Not easy/convenient/possible to do this with Audacity, 'cause it's not a command line program.

Also I think this is why 'imageshack-uploader' program is difficult (or impossible) to compile now, 'twas designed to be compiled/used with an earlier FFmpeg library.
;)

---

### Post by andrew.46 on 2014-04-26
A good case for some developers to ship their source with a custom FFmpeg perhaps, although this increases workload for people who for the most part have much to do In Real Life...

---

### Post by ron998 on 2014-04-27
> **ron998 said:**
> ... Maybe this is the way to go...
For imports use FFmpeg-0.10.12 libary with --enable-whatever to add extra **de**coders.
(Also disable some **en**coders, as in the mini-guide --disable-encoder=whatever)...Hi
These are the config options that I used with FFmpeg-0.10.12 to build a library for imports only.
```
[SUB][SIZE=1]./configure \
--prefix=$HOME/audacity_build/audacity_deps/usr \
--enable-libspeex \
--enable-shared \
--disable-avdevice \
--disable-avfilter \
--disable-bsfs \
--disable-debug \
--disable-doc \
--disable-encoders \
--disable-ffmpeg \
--disable-ffplay \
--disable-ffprobe \
--disable-ffserver \
--disable-filters \
--disable-hwaccels \
--disable-indevs \
--disable-muxers \
--disable-outdevs \
--disable-postproc \
--disable-protocols \
--disable-static \
--disable-swresample \
--disable-swscale[/SIZE][/SUB]
```

---

### Post by andrew.46 on 2014-04-28
In a weekend update I have added the following options to the FFmpeg installation (thanks Ron for showing some of the possibilities!):

```

--disable-filters \
--disable-bsfs \
--disable-protocols \
--disable-debug \
--disable-hwaccels

```

All seems to be working well, just a little more fine-tuning required to the FFmpeg options at some stage, certainly libpostproc and libswscale should go...

**Edit:** Interestingly enough I also tried *--enable-libvo-amrwbenc*  for FFmpeg but this would not produce a usable exported file with Audacity.

---

### Post by ron998 on 2014-04-28
> **andrew.46 said:**
> ... tried *--enable-libvo-amrwbenc*  for FFmpeg but this would not produce a usable exported file...

Hi
Maybe vo_amrwbenc is very picky about bitrate/samplerate and mono only.;)

It tested OK with Export Audio --> (external program).
Using gusari.org static build.
```
ffmpeg -i - -c:a libvo_amrwbenc -b:a 12.65k -ar 16k -ac 1 "%f"
ffmpeg -i - -c:a libvo_amrwbenc -b:a 23.85k -ar 16k -ac 1 "%f"
```

---

### Post by andrew.46 on 2014-04-29
> **ron998 said:**
> It tested OK with Export Audio --> (external program).

OIC, I was testing from File --> Export --> Custom FFmpeg Export --> Options. Seems to be a little twitchy there...

---

### Post by vasa1 on 2014-04-29
@**andrew.46**, I successfully followed the procedure you provided in the first post but I have a question regarding "cleaning up". What can be removed from the *~/audacity_build* folder? Could you please explain?

---

### Post by ron998 on 2014-04-29
> **vasa1 said:**
> ... What can be removed from the *~/audacity_build* folder? Could you please explain?
@vasa1
Hi
When Audacity has been built and installed, it needs these [s]9[/s][SIZE=1] **[SIZE=3]6[/SIZE]**[/SIZE] files:-

[SIZE=1][s]libavcodec.so[/s]
libavcodec.so.53
libavcodec.so.53.61.100
[s]libavformat.so[/s]
libavformat.so.53
libavformat.so.53.32.100
[s]libavutil.so[/s]
libavutil.so.51
libavutil.so.51.35.100[/SIZE]

They are in the folder **~/audacity_build/usr/lib**

Here is a suggestion... ;)
Create a new folder, name it **audacity_library** or similar.
Copy those [s]9[/s][SIZE=1] **[SIZE=3]6[/SIZE]**[/SIZE] files into it.
Then put your **audacity_library** folder somewhere safe/convenient.
(I have put mine in **/usr/local/share/audacity**)

After that, tell Audacity where the new **libavformat.so** is now located.
Edit --> Preferences --> Libraries -> FFmpeg Libraries --> Locate --> Browse and select the file...

When you're sure that Audacity has found the new library and it works OK, you can delete the whole **~/audacity_build** folder.:cool:

PS
(Keep the **audacity_3.2.0.5_i386.deb** package too if you like.)

---

### Post by andrew.46 on 2014-04-30
Hey Ron, you might be interested in testing out a hacked Makefile.in that installs the FFmpeg libraries to /usr/local. This might be the way to go I suspect and if it works well enough for you I will work it into the guide. Pity I don't have my own webspace any more, this would make hosting a patch much easier ...

Just unzip it in the Audacity source and allow it to overwrite the original. I have attached a screenshot showing the FFmpeg libraries as part of the Audacious package :)

---

### Post by andrew.46 on 2014-04-30
> **vasa1 said:**
> @**andrew.46**, I successfully followed the procedure you provided in the first post but I have a question regarding "cleaning up". What can be removed from the *~/audacity_build* folder? Could you please explain?

At the moment it would perhaps be best to leave the FFmpeg libraries where they are, although Ron has suggested a great alternative. I am working on a hacked makefile that will install all of the required FFmpeg libraries in with the Audacity package and this will mean that once Audacity is installed the entire build folder can be deleted and forgotten about. This would be a method of automating Ron's great idea :).

I just need available time to work on this and get it just right, my Real Life™ is somewhat busy at the moment :(.

---

### Post by vasa1 on 2014-04-30
Thanks, andrew.46 and Ron998 :)

---

### Post by andrew.46 on 2014-04-30
One issue that I need to definitively resolve is: where is the best place to store the libraries that Audacity will use? What I would like to avoid is other media applications, particularly when being compiled, finding and attempting to use  these quite dated libraries. It is a relatively simple matter to change the destination of these files from within the patched Makefile.in so I have some options to play with. The default Trusty $PATH is:

```

andrew@hellas:~$ **[COLOR="#FF0000"]echo $PATH[/COLOR]**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

which I can see totally ignores /opt completely so this might be a great option when I finalise the makefile. Possibly I could use:

```

 # install FFmpeg libraries for a certain Ubuntu guide :)
$(INSTALL) -d /opt/$(AUDACITY_NAME)/lib/FFmpeg
$(INSTALL) -m 644 $(HOME)/audacity_build/audacity_deps/usr/lib/libavcodec* /opt/$(AUDACITY_NAME)/lib/FFmpeg
$(INSTALL) -m 644 $(HOME)/audacity_build/audacity_deps/usr/lib/libavformat* /opt/$(AUDACITY_NAME)/lib/FFmpeg
$(INSTALL) -m 644 $(HOME)/audacity_build/audacity_deps/usr/lib/libavutil* /opt/$(AUDACITY_NAME)/lib/FFmpeg

```

but this is pretty ugly as it is and would really need a separate variable for FFMPEGLIBS install path (for example) and then strictly speaking an uninstall routine even though we are using checkinstall. Perhaps I won't be all that fussy :)

---

### Post by mc4man on 2014-04-30
The path you be concerned about is the linker (ld) path, not particularly bin. 
With audacity configured with dynamic loading /opt or /opt/whatever  is fine, users have to point audacity to the lib(s) anyway.

Slightly off topic - 
 Debian/Ubuntu disables dynamic loading so the ffmpeg .so's are auto added but have to be in a default linker path or audacity will error at runtime. 
(- unless started under an export or env for LD_LIBRARY_PATH=  which works fine but is a hair slower on opening

It's likely the only real issue installing the .so's to a default path is if same name .so or .so links are also installed by system libs, ex. "libavcodec.so" which seems be a part of your current install/method.  (libavcodec.so is part of libavcodec-dev, not libavcodec54 package as far as system packages
(-  one way around that is to employ ffmpeg's --build-suffix= option though not needed for this guide, ect.

---

### Post by ron998 on 2014-04-30
> **mc4man said:**
> The path you be concerned about is the linker (ld) path, not particularly bin. 
With audacity configured with dynamic loading /opt or /opt/whatever  is fine, users have to point audacity to the lib(s) anyway.

Hi mc4man
But if those 6 files are kept in, for example
**/usr/local/share/audacity/audacity_library**
or
**/usr/local/share/audacity/lib**
or
**/usr/local/share/audacity/foo**

Is there any realistic chance that another program will try to link to them?
(unless we deliberately do something dumb like **LDFLAGS="-L/usr/local/share/audacity/audacity_library"**)

Is it possible, or are we wearing tinfoil hats? :cool:

---

### Post by mc4man on 2014-04-30
> **ron998 said:**
> Hi mc4man
But if those 9 files are kept in, for example
**/usr/local/share/audacity/audacity_library**
or
**/usr/local/share/audacity/lib**
or
**/usr/local/share/audacity/foo**

Is there any realistic chance that another program will try to link to them?
(unless we deliberately do something dumb like **LDFLAGS="-L/usr/local/share/audacity/audacity_library"**)

I**s it possible ....**

No , not at all.  If you did happen to  install  into the linker search path, which this guide & your example are  not,  then it's possible if building some other source it would use them  instead of the intended ones. As far as loader path in same scenario  maybe there is some odd app or 2 that uses the generic .so (libavcodec.so, ect.) vs. more specific like libavcodec.so.54, ect.

---

### Post by ron998 on 2014-04-30
> **mc4man said:**
> ... It's likely the only real issue installing the .so's to a default path is if same name .so or .so links are also installed by system libs, ex. "libavcodec.so" which seems be a part of your current install/method.  (libavcodec.so is part of libavcodec-dev, not libavcodec54 package)...
Hi
I've had a second thoughts, hold the front page. :P

Audacity doesn't need these 3 files:-
[SIZE=1]libavcodec.so
libavformat.so
libavutil.so[/SIZE]

It only needs these **6** files (not 9):-
[SIZE=1]libavcodec.so.53
libavcodec.so.53.61.100
libavformat.so.53
libavformat.so.53.32.100
libavutil.so.51
libavutil.so.51.35.100[/SIZE]

---

### Post by pcrolandhu on 2014-05-02
I wasn't able to compile Audacity :-(
```
checking for wx-config... /usr/local/bin/wx-config

  Warning: No config found to match: /usr/local/bin/wx-config --unicode=yes --version
           in /usr/local/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.


configure: Checking that the chosen version of wxWidgets is 2.8.x
configure: error: Unable to locate a suitable configuration of wxWidgets v2.8.x or higher.
The currently available configurations are listed below.  If necessary, either
install the package for your distribution or download the latest version of
wxWidgets
from http://wxwidgets.org.


    Default config is gtk2-ansi-release-2.8


  Default config will be used for output
```
I have tried to install wxWidgets, but still can't compile Audacity. Is there any solution?
OS: Xubuntu 14.04 LTS

---

### Post by ron998 on 2014-05-02
> **pcrolandhu said:**
> ... Is there any solution?
Hi

Run this command again:-
```
sudo apt-get -y install libwxgtk2.8-0 libwxgtk2.8-dev libsndfile1-dev \
libsoxr-dev libexpat1-dev libgtk2.0-dev libasound2-dev libmad0-dev \
libportaudio-dev libflac++-dev libid3tag0-dev libsbsms-dev libsoundtouch-dev \
libtwolame-dev libportaudio-dev libmp3lame-dev libid3tag0-dev libfaac-dev \
libopencore-amrnb-dev libopencore-amrwb-dev
```

Make sure everything is "**already the newest version**".

---

### Post by pcrolandhu on 2014-05-02
I ran it as you sad, then apt-get update and apt-get upgrade, but I still can't compile it :-(

---

### Post by ron998 on 2014-05-02
> **pcrolandhu said:**
> I ran it as you sad
Post the output from this command:-
```
sudo apt-get -y install libwxgtk2.8-0 libwxgtk2.8-dev libsndfile1-dev \
libsoxr-dev libexpat1-dev libgtk2.0-dev libasound2-dev libmad0-dev \
libportaudio-dev libflac++-dev libid3tag0-dev libsbsms-dev libsoundtouch-dev \
libtwolame-dev libportaudio-dev libmp3lame-dev libid3tag0-dev libfaac-dev \
libopencore-amrnb-dev libopencore-amrwb-dev
```

---

### Post by pcrolandhu on 2014-05-02
```
pc@roland:~$ sudo apt-get -y install libwxgtk2.8-0 libwxgtk2.8-dev libsndfile1-dev \
> libsoxr-dev libexpat1-dev libgtk2.0-dev libasound2-dev libmad0-dev \
> libportaudio-dev libflac++-dev libid3tag0-dev libsbsms-dev libsoundtouch-dev \
> libtwolame-dev libportaudio-dev libmp3lame-dev libid3tag0-dev libfaac-dev \
> libopencore-amrnb-dev libopencore-amrwb-dev
[sudo] password for pc: 
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapotinformációk olvasása... Kész
libasound2-dev már a legújabb verzió.
libexpat1-dev már a legújabb verzió.
libflac++-dev már a legújabb verzió.
libgtk2.0-dev már a legújabb verzió.
libid3tag0-dev már a legújabb verzió.
libsndfile1-dev már a legújabb verzió.
libmad0-dev már a legújabb verzió.
libmp3lame-dev már a legújabb verzió.
libopencore-amrnb-dev már a legújabb verzió.
libopencore-amrwb-dev már a legújabb verzió.
libportaudio-dev már a legújabb verzió.
libsbsms-dev már a legújabb verzió.
libsoundtouch-dev már a legújabb verzió.
libsoxr-dev már a legújabb verzió.
libtwolame-dev már a legújabb verzió.
libwxgtk2.8-0 már a legújabb verzió.
libwxgtk2.8-dev már a legújabb verzió.
libfaac-dev már a legújabb verzió.
A következ&#337; csomagok automatikusan lettek telepítve, és már nincs rájuk szükség:
  hyphen-en-us kde-l10n-engb kde-l10n-hu libkateinterfaces4 libnetpbm10
  libportsmf0 libvamp-hostsdk3 mythes-en-au netpbm openoffice.org-hyphenation
Ezeket az &#8222;apt-get autoremove&#8221; paranccsal törölheti.
0 frissített, 0 újonnan telepített, 0 eltávolítandó és 0 nem frissített.
pc@roland:~$
```
English translate:
már a legújabb verzió -> is the latest version
A következ&#337; csomagok automatikusan lettek telepítve, és már nincs rájuk szükség -> The following packages were automaticly installed...

---

### Post by ron998 on 2014-05-02
> **pcrolandhu said:**
> English translate...

Looks OK.
Run the configure command again:-
```
PKG_CONFIG_PATH="$HOME/audacity_build/audacity_deps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local --with-ffmpeg

```
If it fails look for **config.log** file, put it in an attachment or send to pastebin.

---

### Post by pcrolandhu on 2014-05-02
```
pc@roland:~/audacity_build/audacity-src-2.0.5$ PKG_CONFIG_PATH="$HOME/audacity_build/audacity_deps/usr/lib/pkgconfig" \
> ./configure --prefix=/usr/local --with-ffmpeg
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for C compiler vendor... gnu
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... yes
checking for a sed that does not truncate output... /bin/sed
checking whether the linker accepts the -rdynamic flag... yes
checking for an ANSI C-conforming const... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for size_t... yes
checking for alloca.h... yes
checking CFLAGS for strict prototypes... -Wstrict-prototypes
checking wall_flags for maximum warnings... -Wall
checking whether the C++ compiler accepts the  -Wall flag... yes
checking whether the C++ preprocessor accepts the  -Wall flag... yes
checking for simple visibility declarations... yes
checking for wx-config... /usr/local/bin/wx-config


  Warning: No config found to match: /usr/local/bin/wx-config --unicode=yes --version
           in /usr/local/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.


configure: Checking that the chosen version of wxWidgets is 2.8.x
configure: error: Unable to locate a suitable configuration of wxWidgets v2.8.x or higher.
The currently available configurations are listed below.  If necessary, either
install the package for your distribution or download the latest version of
wxWidgets
from http://wxwidgets.org.


    Default config is gtk2-ansi-release-2.8


  Default config will be used for output
```
Config.log: [http://pastebin.com/ucAVtgS9](http://pastebin.com/ucAVtgS9) :-(

---

### Post by ricardisimo on 2014-05-04
Not working. Tried importing an MOV, which never gave any problem in the past. "Does not recognize this type of file."

Also, did I just mess up my fully up-to-date install of ffmpeg which I use for commandline purposes?

---

### Post by Nickjpost on 2014-05-05
This is a great guide and worked for me! Thanks!

---

### Post by andrew.46 on 2014-05-07
> **ricardisimo said:**
> 
Also, did I just mess up my fully up-to-date install of ffmpeg which I use for commandline purposes?

No, this installations of FFmpeg does not actually install an executable and removes no system files. Can you post the troublesome file somewhere?

---

### Post by ron998 on 2014-05-09
> **pcrolandhu said:**
> 
Config.log:  :-(
Hi
Looks like you need to ask question at Audacity forum ---> [http://forum.audacityteam.org/](http://forum.audacityteam.org/)
"**Compiling Audacity**" section.
:cool:

---

### Post by HarryUP on 2014-06-03
Thank you for this helpful guide! It worked on KXStudio 14.04

---

### Post by mc4man on 2014-06-05
There is a patch now that allows audacity to work with libav 9/10 & FFmpeg >= 1.2
It should show up in 14.04 shortly, is in trusty -proposed now but even though patched they didn't enable ffmpeg (makes no sense...
The package for 14.10 was done properly

edit: the trusty package & crash has been fixed, should appear in trusty -proposed shortly (patch is altered for libav9
referring bug - [https://bugs.launchpad.net/bugs/1076928](https://bugs.launchpad.net/bugs/1076928)
The changes have been committed to audacity svn so it should work with newer FFmpeg or Libav

---

### Post by andrew.46 on 2014-06-07
Thanks mc4man, I see you have been active in the process. Looks like soon this last of my guides will be obsolete which is a little sad but it has been fun :)

---

### Post by andrew.46 on 2014-06-07
Thanks mc4man, I see you have been active in the process. Looks like soon this last of my guides will be obsolete which is a little sad but it has been fun :)

---

### Post by howefield on 2014-06-08
Thread closed at authors request.

---

### Post by coffeecat on 2014-06-08
Thread closed at request of OP. From an edit in the first post:

> A fix for this problem is available in the development version of Audacity and a patched version of Audacity will arrive in Trusty soon enough. So this guide is now of historical interest only and will close soon.....

---

