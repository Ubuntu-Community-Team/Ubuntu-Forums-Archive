---
title: "Handbrake now with 'real' GTK GUI"
date: 2008-05-31
forum: The Cafe
---

### Post by Polygon on 2008-05-31
A guy on the handbrake forums is making a GTK GUI for HandBrake that has a good chance of being included in the official source code. Unlike the other gui (handbrakegtk) this actually works and closely mirrors the Mac and windows versions of handbrake

screenshots:

[[IMG]http://img81.imageshack.us/img81/7313/screenshothandbrakevx9.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshothandbrakevx9.png)

[[IMG]http://img225.imageshack.us/img225/3208/screenshothandbrakequeuig6.th.png[/IMG]](http://img225.imageshack.us/my.php?image=screenshothandbrakequeuig6.png)

[[IMG]http://img225.imageshack.us/img225/3986/screenshotpreviewar1.th.png[/IMG]](http://img225.imageshack.us/my.php?image=screenshotpreviewar1.png)

To try it out now, its still in beta, but the guy says you have to compile it and handbrake yourself

[B][COLOR="Red"]EDIT: This method no longer works, see this post for more information:  [http://ubuntuforums.org/showpost.php?p=5348490&postcount=26](http://ubuntuforums.org/showpost.php?p=5348490&postcount=26)

also note that some people have experienced that the recent svn build is a bit unstable. wait for the stable 0.9.3 release if you experience crashes[/COLOR][/B]

To do this, (correct me if im wrong) but first create a folder somewhere, called like handbrake source, called something like svn

then, open up a console, cd to this directory then type 

```
svn checkout svn.handbrake.fr/HandBrake/trunk
```

when its done cd to the folder HandBrake

before you can compile you need to install jam

```
sudo apt-get install jam
```

then

```
./configure
```

will make sure you have all the dependencies

then 

```
jam
```

Make sure it compiles. If it compiles successfully then you can make the GUI.

Download and extract this: [http://localhostr.com/files/d5e958/ghb.tgz](http://localhostr.com/files/d5e958/ghb.tgz)

then open up a terminal and cd to ghb

you need some dependencies. Im sure that you will need these, although i might be missing a few:

```
sudo apt-get install libgtk2.0-dev libglib2.0-dev  libhal-storage1 libhal-storage-dev libhal-dev 
```

now try running configure to see if you have all the dependencies

```
./configure
```

if that completed fine then now you need to compile the gui. This is a bit tricky, you NEED TO LINK TO THE HANDBRAKE SOURCE FOLDER

for example my handbrake source folder was in /home/mark/svn/HandBrake/

so just edit my path with yours and it should go fine. Make sure you end with /HandBrake/ though and not /svn/ .

```
./configure --with-hb=<PUT YOUR PATH HERE>
```

then

```
make
```

then

```
sudo make install
```

then after that, you can run the program using the command 

```
ghb
```

hopefully i typed up everything right, please tell me if im missing stuff and ill edit it.

its still in beta, so you can pass on any bugs and ill pass them on to the guy.  Im sure once this gets included with the main code there will be a deb made by someone and this will be a lot easier, this is just for people who are tired of typing  

HandBrakeCLI -i /media/LinuxBackup/vobcopy/VOLUME_IDENTIFIER/VIDEO_TS/ -o /media/LinuxBackup/Ripped_DVDs/cfhs_west_side_story.mkv -e x264 -b 1600 -E ac3 -f mkv -m -p -2 -T -x ref=5:mixed-refs:bframes=3:bime:weightb:b-rdo:b-pyramid:me=umh:subme=7:trellis=1:analyse=all:8x8dct:no-fast-pskip


every time they want to rip a movie =P

---

### Post by ghindo on 2008-05-31
'Bout time.  Good to see that Handbrake's finally giving Linux a GUI! :)

---

### Post by Mr. Picklesworth on 2008-05-31
Wow! Your theme and font had me laughing. I truly thought for a minute there that those pictures were mockups drawn on paper by someone with too much time on his hands.

More on topic: Many thanks for the heads up!

---

### Post by frenchn00b on 2008-05-31
> **Mr. Picklesworth said:**
> Wow! Your theme and font had me laughing. I truly thought for a minute there that those pictures were mockups drawn on paper.

More on topic: Many thanks for the heads up!

indeed, the fonts are cool. what are they ?
They are often used in linux

---

### Post by jrusso2 on 2008-05-31
Looks a bit like comic sans but its not.

---

### Post by Mr. Picklesworth on 2008-05-31
Little OT, but the closest I can think of (at least that Ubuntu has from the start) is Purisa. URW Chancery L (among many others) has that sort of dense cursive look as well. (While it's a little bit hard to read, it is a nice demo of X's power).

Sorry, looks like I derailed your thread. Topic, people! I don't want to be responsible for this :P
It's a nice topic. Handbrake is good. (So don't lose it!)

---

### Post by Polygon on 2008-05-31
yeah the fonts are indeed purisa :D

---

### Post by mostwanted on 2008-05-31
> **Polygon said:**
> yeah the fonts are indeed purisa :D

What about the icons - are they specific to Handbrake or can I get the theme somewhere?

---

### Post by Polygon on 2008-05-31
yeah, all of the icons except for the 'open' icon are specific to handbrake and are present in the mac and windows GUI's as well.

---

### Post by frenchn00b on 2008-05-31
thank you the community !!
btw would have someone a direct link to retrieve the purisa font?

---

### Post by Polygon on 2008-05-31
i believe it comes with the default ubuntu installation.

---

### Post by DasCrushinator on 2008-06-03
What would it take to get Handbrake into the Ubuntu repos (complete with GUI when it is done)?

---

### Post by Polygon on 2008-06-03
either having one of us package it and then submit it to the MOTU's or have one of the MOTU's do it for us. If we do it ourselfs and then submit it there is a much higher chance it will get included.

I dunno when the final gtk gui gets in maybe ill hop on to #motu or whatever their irc channel is and ask for help with packaging since it seems really complicated last time i tried to do it D:

---

### Post by maino82 on 2008-06-09
I am having a ridiculously hard time compiling this for some reason. I get the following errors:

```
...
libhb/decomb.c:952: error: ‘hb_filter_private_t’ has no member named ‘pic_out’
libhb/decomb.c:952: error: ‘hb_filter_private_t’ has no member named ‘buf_out’
libhb/decomb.c:953: error: ‘hb_filter_private_t’ has no member named ‘pic_out’
libhb/decomb.c:954: error: ‘hb_filter_private_t’ has no member named ‘buf_out’
libhb/decomb.c:960: error: ‘hb_filter_private_t’ has no member named ‘deinterlaced_frames’
libhb/decomb.c:966: error: ‘hb_filter_private_t’ has no member named ‘pic_out’
libhb/decomb.c:966: error: ‘hb_filter_private_t’ has no member named ‘buf_out’
libhb/decomb.c:969: error: ‘hb_filter_private_t’ has no member named ‘pic_out’
libhb/decomb.c:974: error: ‘hb_filter_private_t’ has no member named ‘pic_in’
libhb/decomb.c:974: error: ‘hb_filter_private_t’ has no member named ‘buf_out’
libhb/decomb.c:977: error: ‘hb_filter_private_t’ has no member named ‘pic_in’
libhb/decomb.c:977: error: ‘hb_filter_private_t’ has no member named ‘pic_out’
libhb/decomb.c:980: error: ‘hb_filter_private_t’ has no member named ‘buf_out’
libhb/decomb.c:985: error: ‘hb_filter_private_t’ has no member named ‘buf_settings’
libhb/decomb.c:988: error: ‘hb_filter_private_t’ has no member named ‘buf_settings’

gcc -c -o libhb/decomb.o -Wall -g -O3 -funroll-loops -I./contrib/include -DSYS_LINUX -DUSE_PTHREAD -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DHB_VERSION=\"svn1497\" -DHB_BUILD=2008060901 -D__LIBHB__ -Ilibhb libhb/decomb.c

...failed Cc libhb/decomb.o ...
Cc libhb/lang.o 
Cc libhb/enctheora.o 
...skipped libhb.a for lack of libhb.a(hb.o)...
Cc test/test.o 
test/test.c:90: warning: ‘cfr’ defined but not used
Cc test/parsecsv.o 
...skipped HandBrakeCLI for lack of libhb.a...
...failed updating 14 target(s)...
...skipped 5 target(s)...
...updated 29 target(s)...
```

I installed all the required dependencies and should have everything I need, but I'm not sure what's going wrong. After several hours of pouring over Google results which were no help I decided I better swallow my pride and ask for help. Any help you could offer would be greatly appreciated.

---

### Post by hizzk on 2008-06-18
I haven't been able to get the GUI to compile either (not dependency-related, AFAIK). It was also choking on the theora part for me, even when I tried commenting-out any mention of it in the source (I don't ever use theora so I wouldn't miss it).

For others in the same boat, you might look into gHandBrake, another GTK frontend.

It's only a CLI wrapper and not a true GUI, but it gets the job done without using Mono, for FOSS purists. I'm not the author of the program, but I submitted some new code for it to add most of the advanced x264 options and some of the other HandBrake options that were lacking (subtitles and deblocking/denoise filters). Hopefully, he'll add them to the official program soon.

For anyone interested in bundling HandBrake for the repos, here's a good and simple tutorial for rolling official-style .debs:

[http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

I'm not sure how well it will apply to a jam-based build, but maybe it'll get you started.

---

### Post by theacoustician on 2008-07-07
Ok, big error in your instructions that a n00b might not catch ... you ./configure 'd but you never issued a make.  

I'm also having issues compiling and I simply don't get it.  I think HandBrake is working correctly, but I have no real way of figuring out if its compiled 100% correctly to work with this GUI.  Here's the output after trying to compile ghb

```
  all-recursive
make[1]: Entering directory `/home/scott/ghb'
Making all in src
make[2]: Entering directory `/home/scott/ghb/src'
gcc -DHAVE_CONFIG_H -I. -I..  -DPACKAGE_LOCALE_DIR=\""/usr/local/lib/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPNG_NO_MMX_CODE -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -Wall -g -g -O2 -I/home/scott/HandBrake//libhb -MT callbacks.o -MD -MP -MF .deps/callbacks.Tpo -c -o callbacks.o callbacks.c
mv -f .deps/callbacks.Tpo .deps/callbacks.Po
gcc -DHAVE_CONFIG_H -I. -I..  -DPACKAGE_LOCALE_DIR=\""/usr/local/lib/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPNG_NO_MMX_CODE -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -Wall -g -g -O2 -I/home/scott/HandBrake//libhb -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I..  -DPACKAGE_LOCALE_DIR=\""/usr/local/lib/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPNG_NO_MMX_CODE -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -Wall -g -g -O2 -I/home/scott/HandBrake//libhb -MT settings.o -MD -MP -MF .deps/settings.Tpo -c -o settings.o settings.c
mv -f .deps/settings.Tpo .deps/settings.Po
gcc -DHAVE_CONFIG_H -I. -I..  -DPACKAGE_LOCALE_DIR=\""/usr/local/lib/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPNG_NO_MMX_CODE -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -Wall -g -g -O2 -I/home/scott/HandBrake//libhb -MT hb-backend.o -MD -MP -MF .deps/hb-backend.Tpo -c -o hb-backend.o hb-backend.c
hb-backend.c:92: error: ‘HB_VCODEC_THEORA’ undeclared here (not in a function)
hb-backend.c: In function ‘ghb_grey_combo_options’:
hb-backend.c:509: warning: passing argument 3 of ‘grey_combo_box_item’ makes integer from pointer without a cast
hb-backend.c:527: warning: passing argument 3 of ‘grey_combo_box_item’ makes integer from pointer without a cast
hb-backend.c:537: warning: passing argument 3 of ‘grey_combo_box_item’ makes integer from pointer without a cast
hb-backend.c:547: warning: passing argument 3 of ‘grey_combo_box_item’ makes integer from pointer without a cast
hb-backend.c: In function ‘audio_track_opts_set’:
hb-backend.c:917: error: ‘hb_audio_config_t’ undeclared (first use in this function)
hb-backend.c:917: error: (Each undeclared identifier is reported only once
hb-backend.c:917: error: for each function it appears in.)
hb-backend.c:917: error: ‘audio’ undeclared (first use in this function)
hb-backend.c:917: error: invalid operands to binary *
hb-backend.c:917: warning: statement with no effect
hb-backend.c:949: error: expected expression before ‘)’ token
hb-backend.c:949: error: invalid operands to binary *
hb-backend.c:949: warning: statement with no effect
hb-backend.c:952: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:952: error: request for member ‘description’ in something not a structure or union
hb-backend.c:954: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:954: error: request for member ‘description’ in something not a structure or union
hb-backend.c:956: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:956: error: request for member ‘description’ in something not a structure or union
hb-backend.c: In function ‘ghb_find_audio_track’:
hb-backend.c:1049: error: ‘hb_audio_config_t’ undeclared (first use in this function)
hb-backend.c:1049: error: ‘audio’ undeclared (first use in this function)
hb-backend.c:1049: error: invalid operands to binary *
hb-backend.c:1049: warning: statement with no effect
hb-backend.c:1067: error: expected expression before ‘)’ token
hb-backend.c:1067: error: invalid operands to binary *
hb-backend.c:1067: warning: statement with no effect
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: warning: passing argument 1 of ‘strlen’ from incompatible pointer type
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: warning: passing argument 2 of ‘__builtin_strcmp’ from incompatible pointer type
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: warning: passing argument 2 of ‘__builtin_strcmp’ from incompatible pointer type
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: warning: passing argument 1 of ‘strlen’ from incompatible pointer type
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: warning: passing argument 2 of ‘__builtin_strcmp’ from incompatible pointer type
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: error: ‘options_map_t’ has no member named ‘lang’
hb-backend.c:1068: error: request for member ‘iso639_2’ in something not a structure or union
hb-backend.c:1068: warning: passing argument 2 of ‘__builtin_strcmp’ from incompatible pointer type
hb-backend.c:1073: error: ‘options_map_t’ has no member named ‘in’
hb-backend.c:1073: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:1073: warning: comparison between pointer and integer
hb-backend.c: In function ‘ghb_get_audio_info’:
hb-backend.c:1547: error: ‘hb_audio_config_t’ undeclared (first use in this function)
hb-backend.c:1547: error: ‘audio’ undeclared (first use in this function)
hb-backend.c:1547: error: invalid operands to binary *
hb-backend.c:1547: warning: statement with no effect
hb-backend.c:1565: error: expected expression before ‘)’ token
hb-backend.c:1565: error: invalid operands to binary *
hb-backend.c:1565: warning: statement with no effect
hb-backend.c:1567: error: ‘options_map_t’ has no member named ‘in’
hb-backend.c:1567: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:1567: warning: assignment makes integer from pointer without a cast
hb-backend.c:1568: error: ‘options_map_t’ has no member named ‘in’
hb-backend.c:1568: error: request for member ‘bitrate’ in something not a structure or union
hb-backend.c:1568: warning: assignment makes integer from pointer without a cast
hb-backend.c:1569: error: ‘options_map_t’ has no member named ‘in’
hb-backend.c:1569: error: request for member ‘samplerate’ in something not a structure or union
hb-backend.c:1569: warning: assignment makes integer from pointer without a cast
hb-backend.c: In function ‘ghb_add_job’:
hb-backend.c:2027: error: ‘hb_job_t’ has no member named ‘list_audio’
hb-backend.c:2027: warning: passing argument 1 of ‘hb_list_count’ from incompatible pointer type
hb-backend.c:2031: error: ‘hb_job_t’ has no member named ‘list_audio’
hb-backend.c:2031: warning: passing argument 1 of ‘hb_list_item’ from incompatible pointer type
hb-backend.c:2032: error: ‘hb_job_t’ has no member named ‘list_audio’
hb-backend.c:2032: warning: passing argument 1 of ‘hb_list_rem’ from incompatible pointer type
hb-backend.c:2039: error: ‘hb_audio_config_t’ undeclared (first use in this function)
hb-backend.c:2039: warning: statement with no effect
hb-backend.c:2039: error: expected ‘;’ before ‘audio’
hb-backend.c:2040: error: ‘taudio’ undeclared (first use in this function)
hb-backend.c:2040: error: invalid operands to binary *
hb-backend.c:2040: warning: statement with no effect
hb-backend.c:2042: warning: implicit declaration of function ‘hb_audio_config_init’
hb-backend.c:2042: error: ‘audio’ undeclared (first use in this function)
hb-backend.c:2044: error: request for member ‘in’ in something not a structure or union
hb-backend.c:2044: error: request for member ‘track’ in something not a structure or union
hb-backend.c:2044: warning: statement with no effect
hb-backend.c:2045: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2045: error: request for member ‘track’ in something not a structure or union
hb-backend.c:2045: warning: statement with no effect
hb-backend.c:2046: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2046: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2046: warning: statement with no effect
hb-backend.c:2047: error: expected expression before ‘)’ token
hb-backend.c:2047: error: invalid operands to binary *
hb-backend.c:2047: warning: statement with no effect
hb-backend.c:2048: error: ‘options_map_t’ has no member named ‘in’
hb-backend.c:2048: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2048: warning: comparison between pointer and integer
hb-backend.c:2048: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2048: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2048: warning: comparison between pointer and integer
hb-backend.c:2053: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2053: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2053: warning: statement with no effect
hb-backend.c:2057: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2057: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2057: warning: statement with no effect
hb-backend.c:2060: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2060: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2060: warning: comparison between pointer and integer
hb-backend.c:2063: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2063: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2063: warning: statement with no effect
hb-backend.c:2065: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2065: error: request for member ‘dynamic_range_compression’ in something not a structure or union
hb-backend.c:2065: warning: statement with no effect
hb-backend.c:2067: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2067: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2067: warning: comparison between pointer and integer
hb-backend.c:2067: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2067: error: request for member ‘codec’ in something not a structure or union
hb-backend.c:2067: warning: comparison between pointer and integer
hb-backend.c:2069: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2069: error: request for member ‘mixdown’ in something not a structure or union
hb-backend.c:2069: warning: statement with no effect
hb-backend.c:2073: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2073: error: request for member ‘mixdown’ in something not a structure or union
hb-backend.c:2073: warning: statement with no effect
hb-backend.c:2074: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2074: error: request for member ‘bitrate’ in something not a structure or union
hb-backend.c:2074: warning: statement with no effect
hb-backend.c:2077: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2077: error: request for member ‘samplerate’ in something not a structure or union
hb-backend.c:2077: error: ‘options_map_t’ has no member named ‘in’
hb-backend.c:2077: error: request for member ‘samplerate’ in something not a structure or union
hb-backend.c:2077: warning: statement with no effect
hb-backend.c:2079: error: request for member ‘out’ in something not a structure or union
hb-backend.c:2079: error: request for member ‘samplerate’ in something not a structure or union
hb-backend.c:2079: warning: statement with no effect
hb-backend.c:2083: warning: implicit declaration of function ‘hb_audio_add’
make[2]: *** [hb-backend.o] Error 1
make[2]: Leaving directory `/home/scott/ghb/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/scott/ghb'
make: *** [all] Error 2

```I seem to have hit the same snag others have.  I don't get why since I'm using the same version of ghb as linked in at the start of this thread and I'm using Handbrake 0.9.2 from source.  Could it be using a 64 bit kernel vs. a 32 bit kernel that's causing issues?

---

### Post by Polygon on 2008-07-07
i dunno, it looks like the code might be at fault there, but i read the handbrake forums a while ago (i dont visit it often cause the developers are ALL complete jerks) but i read that its pretty much set that the linux gui will come with the next release, might want to wait for that

---

### Post by stmiller on 2008-07-07
I think the GUI is actually QT4 and not GTK. But very cool!

---

### Post by Polygon on 2008-07-08
> **stmiller said:**
> I think the GUI is actually QT4 and not GTK. But very cool!

no its not.

its gtk, the qt4 gui was started but never finished

---

### Post by theacoustician on 2008-07-08
> **Polygon said:**
> no its not.

its gtk, the qt4 gui was started but never finishedWell, not the one that comes packed in the source, but there's apparently a new one that's a bit more polished.

[http://forum.handbrake.fr/viewtopic.php?f=4&t=6388](http://forum.handbrake.fr/viewtopic.php?f=4&t=6388)

I'm going to risk it and beg for help from the Handbrake crew directly.  If I ever get it properly working, I'll roll a deb for everyone.

---

### Post by qazwsx on 2008-07-08
I just don't understand handbrake. Anything special compared to mencoder (ogmtools and mkvtoolnix combination)? Lots of work for something what is already done...

---

### Post by Polygon on 2008-07-08
> **qazwsx said:**
> I just don't understand handbrake. Anything special compared to mencoder (ogmtools and mkvtoolnix combination)? Lots of work for something what is already done...


 mencoder most likely doesnt have presets for a ton of devices (such as psp/ps3/xbox/iphone/ipod), doesnt have a queue (well it kinda does using that weird ; thing in teh gui) , doesnt have advanced features for reading DVD's, such as decrypting them, reading chapters, ignoring fake chapters, some fixes and workarounds for getting around the nasty stuff people put in dvds to prevent you from ripping them (zero cells), doesn't show you previews of the dvd before you start ripping it,...etc

sure mencoder could probably do what handbrake does, but handbrake makes it a lot easier, since the devs have done a lot of the work for you, you dont need to remember or jot down the required options and resolution to make your movie play on your ipod, you just select your dvd, the chapter and the ipod preset and click "go"....your free to use mencoder if you wish

---

### Post by theacoustician on 2008-07-08
> **qazwsx said:**
> I just don't understand handbrake. Anything special compared to mencoder (ogmtools and mkvtoolnix combination)? Lots of work for something what is already done...

Real time previews of encoding is key.  Any command line encoding of video just seems assine because there are too many variables in H.264 to stick to a single preset, unlike MP3.  I suppose if you just don't care or are only concerned about target size, its peachy.  If you're working in a pro environment or are a videophile, you need the visual feedback.  Although back to the number of options on H.264, unless you have a chart sitting next to you, I'm not sure how you can keep track of all the variables available.  I know most people don't know or care, but some do.  Handbrake is also one of the few programs out there that combines ripping with encoding, so that's a boon.

As for what's wrong with other programs?  Well, Avidemux doesn't rip, nor does it provide a full array of H.264 options, dvd::rip is downright pathetic when it comes H.264 options, and I have yet to find a decent MEncoder front end worth a hoot.

Don't get me wrong, I love the command line.  Its a beautiful thing.  But CLI on video is like trying to drive with your eyes closed; you're basically praying everything turns out ok.

---

### Post by Polygon on 2008-07-08
you can use the cli version of handbrake if you want xD

---

### Post by theacoustician on 2008-07-08
> **Polygon said:**
> you can use the cli version of handbrake if you want xD

I can also just keep video in uncompressed 4:2:2 HD.

---

### Post by theacoustician on 2008-07-08
Ladies and Gentlemen, we have a successful compile!  The problem we have been having is because development of GHB has been following Handbrake.  The version of GHB that's linked is old and doesn't work anymore with the latest svn checkouts.  Here are the instructions directly from GHB's dev, JohnAStebbins.  If this helps you, please send him a nice note and tell him how much you appreciate him.

> svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake
[I]
My gui is checked in now under the gtk subdir.[/I]
cd HandBrake
./configure
make
cd gtk
./autogen.sh
make
sudo make install

You will have to compile yasm from source if you're using a 64 bit system as already mentioned.  One more gotcha I ran into was some error screaming about lbz missing.  I fixed this by installing lib64bz2-1.0, libbz2-1.0, and libbz2-dev.

After all that, you'll see the pineapple and tropical drink under Sound & Video in your App bar :)

Now to see if I can make a deb that works...

---

### Post by reacocard on 2008-07-09
> **theacoustician said:**
> Ladies and Gentlemen, we have a successful compile!  The problem we have been having is because development of GHB has been following Handbrake.  The version of GHB that's linked is old and doesn't work anymore with the latest svn checkouts.  Here are the instructions directly from GHB's dev, JohnAStebbins.  If this helps you, please send him a nice note and tell him how much you appreciate him.



You will have to compile yasm from source if you're using a 64 bit system as already mentioned.  One more gotcha I ran into was some error screaming about lbz missing.  I fixed this by installing lib64bz2-1.0, libbz2-1.0, and libbz2-dev.

After all that, you'll see the pineapple and tropical drink under Sound & Video in your App bar :)

Now to see if I can make a deb that works...

thanks for the tip! worked like a charm on my 64bit hardy install.

---

### Post by qazwsx on 2008-07-11
> **Polygon said:**
> you can use the cli version of handbrake if you want xD

Well for video encoding cli is very good choice.

PS Mencoder is extremely advanced tool for dvd/file encoding if you read the huge manual(it is huge). Maybe even more advanced than handbrake (I have tried the cli version and missed mencoder's configurability). For example you can play with audio/video filtering all day :lolflag: Remember if MPlayer can do it it is very likely Mencoder can do it as well.One command can be several kilobytes long;). Muxing in other containers than avi is problematic but there are tools like MP4Box and mkvtoolnix for it. I guess I am too much videophile for Handbrake :). 

Handbrake GUI looks better than any other I have tried so far.

---

### Post by Polygon on 2008-07-11
> **theacoustician said:**
> I can also just keep video in uncompressed 4:2:2 HD.

you can also have a file that is many times bigger then what it needs to be if it resides on your computer ;) Most people dont have infinite drive space so they cant just rip the dvd or bluray straight to their hard drive for each movie.


and im glad you got it to compile, ill edit my post to link to yours

---

### Post by theacoustician on 2008-07-11
> **qazwsx said:**
> Well for video encoding cli is very good choice
No, no its really not.  Let me put this bug in your ear and you can consider it for a while.  No content provider uses CLI in their production path.  There are several steps in the process in which video is checked and rechecked visually along side ancillary data like waveforms, color levels, MV, phase constellations, etc.  before its allowed to move on.  Countless thousands of dollars are spend on monitors with HD-SDI in for such purposes.  Now, if no one you're receiving your content from considers that an acceptable method for compression, how is CLI somehow more videophile?  Now, if you just like it better, that's awesome and there's really nothing to say after that :)

> **Polygon said:**
> you can also have a file that is many times bigger then what it needs to be if it resides on your computer ...

and im glad you got it to compile, ill edit my post to link to yoursYour first statement is quite true ... I only keep a few such files on my machine for testing purposes.  Consumers don't generally have access to 4:2:2 video and absolutely no access to 4:4:4.  You'd be amazed at the difference.  Highly worth it if you can snag it.  Then again, you'd need something to display it on :/

Just a warning for your first post.  I've found that the most recent build isn't what I'd call 100% stable.  Doing rapid A/B comparisons will most certainly crash it out.  However, if you just go slow with it and don't try to do much else with your machine while you're encoding, it should be right as rain.

---

### Post by Polygon on 2008-07-11
well of course compiling anything from svn is a tad bit risky, since its in production and not reached a stable milestone, ill edit the first post to say that it might not be stable until 0.9.3 comes out

also, theacoustician, about your earlier post saying that i forgot "make" in my original post, that is not a mistake. I guess the handbrake devs use jam to build the program instead of make, although they do support both, the developers suggest to use jam as they dont update the makefile as religiously as they do jam. Just running jam downloads all the dependencies (the codec files), compiles them and produced HandBrakeCLI :D

---

### Post by theacoustician on 2008-07-12
> **Polygon said:**
> well of course compiling anything from svn is a tad bit risky, since its in production and not reached a stable milestone, ill edit the first post to say that it might not be stable until 0.9.3 comes out

also, theacoustician, about your earlier post saying that i forgot "make" in my original post, that is not a mistake. I guess the handbrake devs use jam to build the program instead of make, although they do support both, the developers suggest to use jam as they dont update the makefile as religiously as they do jam. Just running jam downloads all the dependencies (the codec files), compiles them and produced HandBrakeCLI :D
Just wanted to share real life feedback so people kinda knew what to expect.

You did forget to issue any build command for the GUI.  > 
Code:

./configure --with-hb=<PUT YOUR PATH HERE>

then after that, you can run the program using the command

Code:

ghb


You went from configuration straight into launching without building the GUI.  Although you bring up an interesting point which I don't understand fully.  The official docs say to use jam.  The instructions included the new svn (read the BUILD file) and the directions given to me both seem to favor using make as the preferred method.  That seems a bit confusing.  I'm not aware of the benefits of one over the other.  Why do you think they changed?  What are the real differences between jam and make?

---

### Post by Polygon on 2008-07-12
oh, that. i thought you were talking about the other part of the post =P

and ive heard from the devs them selfs to use jam to compile handbrake at least, im not sure whats best to compile the gui, if it only has a makefile then i guess use make. I used jam to compile HB and make to compile the GUI and it works fine on my machine

and here is the wiki page on jam if your interested: [http://en.wikipedia.org/wiki/Perforce_Jam](http://en.wikipedia.org/wiki/Perforce_Jam)

also, waht depenencies did you install in order to compile? im trying to compile the newest version and it keeps failing:

> 
...failed Cc libhb/decomb.o ...
Cc libhb/lang.o 
Cc libhb/enctheora.o 
...skipped libhb.a for lack of libhb.a(hb.o)...
Cc test/test.o 
test/test.c:91: warning: &#8216;cfr&#8217; defined but not used
Cc test/parsecsv.o 
...skipped HandBrakeCLI for lack of libhb.a...
...failed updating 16 target(s)...
...skipped 5 target(s)...
...updated 28 target(s)...
mark@Australis:~/svn/HandBrake$ 


---

### Post by Mic_Droz on 2008-07-13
Hey guys, i'm having a bit of difficulty compiling using the instructions theacoustician gave. 

When i'm trying to compile (i've typed jam instead of make this time, but have tried with make also) i've run into a few errors about not being able to find some things...

```
...skipped libhb.a for lack of libhb.a(encx264.o)...
Cc test/test.o 
test/test.c:91: warning: ‘cfr’ defined but not used
Cc test/parsecsv.o 
...skipped HandBrakeCLI for lack of libhb.a...
...failed updating 2 target(s)...
...skipped 2 target(s)...
...updated 75 target(s)...
```

After this, when cd into gtk, then follow the rest of the instructions, i get errors about not having packages hal, hal-storage and gtk2.0 (which i clearly have... I think!)

Can anyone point me in the right direction? happy to give more information as someone needs it... i'm running Hardy

---

### Post by qazwsx on 2008-07-13
> **theacoustician said:**
> No, no its really not.  Let me put this bug in your ear and you can consider it for a while.  No content provider uses CLI in their production path.  There are several steps in the process in which video is checked and rechecked visually along side ancillary data like waveforms, color levels, MV, phase constellations, etc.  before its allowed to move on.  Countless thousands of dollars are spend on monitors with HD-SDI in for such purposes.  Now, if no one you're receiving your content from considers that an acceptable method for compression, how is CLI somehow more videophile?  Now, if you just like it better, that's awesome and there's really nothing to say after that :)

Well you can check your results while encoding. Überpro stuff is not where MEncoder and Hanbrake are.

Besides think encoding as series of commands you put together and so on. Cli does not restrict you  visualizing encoding process. Maybe it is not handy for stuff you analyze every image you get @25 fps material  (I have better things to do) :lolflag:... And for streaming well it is practically impossible to investigate whole process... Just think of DVB stream and several channels in same package.

---

### Post by Polygon on 2008-07-13
you seem to have the same problem as me, libhb.a is not compiling cuase we are missing something, and as for you missing hal and all that, you need these packages:

```

sudo apt-get install libgtk2.0-dev libglib2.0-dev  libhal-storage1 libhal-storage-dev libhal-dev
```

---

### Post by sr55 on 2008-07-13
@Polygon - Make under Linux will call on Jam. So really, when your using make, it's simply calling on jam to build all the contribs.

Regards,
Scott

---

### Post by lingenfr on 2008-07-13
good for you theacoustician, other than being hard to compile, arcane to learn and extremely difficult to troubleshoot, handbrake is great. How about we keep this thread focused on the gtk gui, and skip the fanboys/girls telling us how great CLI is. If CLI were so great, this thread would be a black and white bbs post about a dos or unix program.

---

### Post by Polygon on 2008-07-13
> **lingenfr said:**
> good for you theacoustician, other than being hard to compile, arcane to learn and extremely difficult to troubleshoot, handbrake is great. How about we keep this thread focused on the gtk gui, and skip the fanboys/girls telling us how great CLI is. If CLI were so great, this thread would be a black and white bbs post about a dos or unix program.

the dependencies are missing, as soon as we install those, the program will compile.

troubleshooting the compile.....install teh correct dependencies...which i don't know what they are yet

and if you just have the paticence to read the man file, handbrake isnt that hard to learn, instead of clicking a checkbox you just add a -m or something.

and we are TRYING to get the cli binary compiled so we can actually use teh gui, so if you dont have anything to contribute to that, dont post here =P

---

### Post by Mic_Droz on 2008-07-13
Thanks Polygon, that did solve the three dependencies i had missing, but I still can't compile HandbrakeCLI. what is libhb.a?

I get this when I try to ./autogen.sh the gui after the dependcies you mentioned were installed

```

make[2]: *** No rule to make target `../../HandBrakeCLI', needed by `HandBrakeCLI'.  Stop.
make[2]: Leaving directory `/home/droz/hb-dev/gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/droz/hb-dev/gtk'
make: *** [all] Error 2

```

It seems that a lot of people have this issue around the internet - surely there is an easy way?

---

### Post by Polygon on 2008-07-14
*sigh* ill go ask on the handbrake forums tommrow... i hate going there =P

---

### Post by Mic_Droz on 2008-07-14
Hmmm... after more diging for random dependecies, i've managed to get only this error..

```
 skipped HandBrakeCLI for lack of contrib/lib/libx264.a 
```

Googling and reading the Handbrake Forums isn't much help - man, those guys are quite condescending and short to a lot of people no?

---

### Post by Mic_Droz on 2008-07-14
OK, so I compiled yasm from source, even though I'm not running 64-bit, then i tried compiling the latest x264 form source, got some errors, but hb compiled! so did the gtk... but it just exits when i try and start the actualy ripping process from a dvd. 

back to the drawing board eh? 

Thanks for your help guys, I'll just try to keep digging...

---

### Post by Polygon on 2008-07-14
> **Mic_Droz said:**
> OK, so I compiled yasm from source, even though I'm not running 64-bit, then i tried compiling the latest x264 form source, got some errors, but hb compiled! so did the gtk... but it just exits when i try and start the actualy ripping process from a dvd. 

back to the drawing board eh? 

Thanks for your help guys, I'll just try to keep digging...

theacoustian said that the latest svn version sometimes crashes when you try and rip a dvd...maybe the latest svn version is just unstable =P

---

### Post by Polygon on 2008-07-14
and i finally posted on their forums and asked: 

[http://forum.handbrake.fr/viewtopic.php?f=13&t=6608&p=37584#p37584](http://forum.handbrake.fr/viewtopic.php?f=13&t=6608&p=37584#p37584)

---

### Post by Mic_Droz on 2008-07-15
hah, it'll be interesting to see just how they decide to insult you on the forums for even taking up a smidgen of their precious time. 

Did you manage to get it to compile? I went to the  "HOWTO: Compile the latest ffmpeg and x264 from source" in the ubuntu forums [http://ge.ubuntuforums.com/showthread.php?t=786095](http://ge.ubuntuforums.com/showthread.php?t=786095) and followed the instructions for yasm *and* x264, just incase. Following that, hb compiled, i didn't get the lib error anymore, and the gtk compiled without any problems.

for anyone else with issues, try the above forum, and also all the dependencies listed in this thread: [http://ge.ubuntuforums.com/showthread.php?t=835825&highlight=HandBrake](http://ge.ubuntuforums.com/showthread.php?t=835825&highlight=HandBrake) 
its a quick HandbrakeCLI how to compile and how to use - highly recommended

Cheers

Oh yeah, can anyone tell me why it says I don't have any posts? just interested...

---

### Post by theacoustician on 2008-07-15
Oh wow, this is not good.  I'll try compiling again tonight.  There might have been an update to the SVN that borked everything and that's why you guys are having a problem compiling.  Here's my list of deps.

> 
libgtk2.0-dev
libglib2.0-dev
libhal-storage1
libhal-storage-dev
libhal-dev
automake
build-essential
jam
libtool
subversion
yasm (ver 0.7.1 or later)
zlib1g-dev
libbz2-dev
lib64bz2-1.0
libbz2-1.0
xmlto
texinfo
g77
gfortran
nasm
doxygen
libsdl1.2-dev
gfortran-multilib
gcc-multilib
g++-multilib
libesd0-dev
libgtk1.2-dev
libfftw3-dev
electric-fence
inux-kernel-devel

That's based on a lot of posts and should cover everything you need for the CLI and GTK frontend.

Could we also do one thing here possibly?  Start posting your SVN checkout number.  That way we can start to get a feel for good builds and bad builds.  You can usually call a previous SVN snapshot if the current one sucks.

If someone can link me to a good guide for building debs, I'll see if I can based on my current install.

---

### Post by Mic_Droz on 2008-07-15
I'm on svn1568, which has actually managed to code a movie that i had on hard disk, after the 7th attempt. 

*sigh*

Great potential in this program though!

Any word on when the 'real deal' 0.9.3 is going to land?

---

### Post by sr55 on 2008-07-16
@Mic_Droz - It's a considerable way off yet.

We still have plans for an additional 1 or more snapshots for testing to do + [http://trac.handbrake.fr/query?status=new&status=assigned&status=reopened&milestone=HandBrake+0.9.3](http://trac.handbrake.fr/query?status=new&status=assigned&status=reopened&milestone=HandBrake+0.9.3)   all that to sort out.

Months would be my estimate.

---

### Post by theacoustician on 2008-07-16
> **sr55 said:**
> @Mic_Droz - It's a considerable way off yet.

We still have plans for an additional 1 or more snapshots for testing to do + [http://trac.handbrake.fr/query?status=new&status=assigned&status=reopened&milestone=HandBrake+0.9.3](http://trac.handbrake.fr/query?status=new&status=assigned&status=reopened&milestone=HandBrake+0.9.3)   all that to sort out.

Months would be my estimate.

Would it be at all possible for final point releases like that to coordinate with a MOTU here and get them in the repositories?  I would think that if you could install the CLI and the GTK or QT4 frontend from Synaptic, that would greatly reduce Linux support questions on your forum and free up more time for development.

Even if its outside the realm of what you can/want to do, thanks so much to you and the HB team for your work.

---

### Post by Polygon on 2008-07-16
we don't really need their help, we just need someone who can create good quality debs that we just submit to the MOTU and they will include it, im thinking of doing it once i learn how to package debs

---

### Post by Polygon on 2008-07-16
and yay, i figured it out. i will try and figure out a proper list of dependencies later today using a live cd, but what my problem was at least was that the version of yasm that is in the ubuntu repos is too old, once i compiled the newer version from their website, it all went fine

i will write up a guide once i get everything sorted out and maybe compile a deb if i can figure it out =P

---

### Post by o.besner on 2008-07-18
Just did it. It was pretty hard, but I now have the CLI and the GUI.

for the CLI : ```
sudo apt-get purge yasm nasm
```

then complile yasm from source (get the source from their website : ([http://www.tortall.net/projects/yasm/](http://www.tortall.net/projects/yasm/))
it's simply a matter of ./configure, make and sudo make install.

If you can make it up to "can't find libha, 2 skipped targets", that means all you need is to compile yasm yourself. Once it's done, the GUI is a piece of cake with Polygon's list of dependencies.

PM me if you need some help in building Handbrake, but Polygon has nailed it IMHO.

I have no idea what are the exact HandbrakeCLI dependencies, I've probably installed waaay too many packages.

---

### Post by hizzk on 2008-07-18
In my experience, these are the dependencies for HandBrakeCLI:
autoconf
automake
g++
g++-multilib
gcc
gcc-multilib
jam
libgcc
libtool
make
makedev
yasm (or nasm if you don't care about cpu extensions)
zlib1g-dev
build-essential (if you're on Ubuntu or a derivative)
dpkg-dev
libdvdcss2

[_Here_]("http://filthypants.blogspot.com/2008/05/debian-or-ubuntu-handbrakecli-092.html")'s a 64-bit deb for yasm, as well as a precompiled 64-bit HandBrakeCLI binary (not trying to blogspam, I just already have them there)

I also have a screenshot and benchmark comparison of advanced x264 options [_here_]("http://filthypants.blogspot.com/2008/07/comparison-of-x264h264-advanced-options.html")

I use HandBrake quite a bit, so I try to keep updated 64-bit builds available at the aforementioned link (stable releases only, not SVN) and will also keep 32-bit builds available once I get my build environment VM up and running.

As I mentioned in my previous post, I've never had luck compiling GHB, but I'll give it another shot now that Polygon has his dependency list up. If it succeeds, I'll post a link to a deb binary. (Edit: it failed again, but I'm on Gutsy, so that could have something to do with it)

I visited the thread that acoustician linked to about an updated qt4 GUI and had much better luck compiling it.

Edit: the deb didn't work, so I removed it to prevent confusion. Oh well.

@Polygon: See my earlier post in this thread for a link to a good guide for packaging your own deb binary.

---

### Post by stmiller on 2008-07-20
> **qazwsx said:**
> I just don't understand handbrake. Anything special compared to mencoder (ogmtools and mkvtoolnix combination)? Lots of work for something what is already done...

Handbrake is smp aware so it can use multiple cores. All other encoders only use one cpu. Also the quality with Handbrake's H.264 is very nice.

---

### Post by toneman77 on 2008-07-20
Hi there
After some compiling i got a handbrake-gtk (first name that came to my mind) deb file on my hardy machine. I had to compile yasm 0.7.1 and install some file from the repositories that i cannot remember, but I'll check my history, if anyone is interested. I created the debs of yasm and handbrake-gtk with checkinstall.

If anyone is interested, drop me a line.

Greets Tone

---

### Post by hizzk on 2008-07-20
> I created the debs of yasm and handbrake-gtk with checkinstall.
If anyone is interested, drop me a line.

I'd be interested in giving them a try, if you want to post them somewhere for download. :)

---

### Post by Mic_Droz on 2008-07-22
I'm interested as well - I think everyone in this thread is quite interested - you've found the Holy Grail of video encoding for ubuntu! can you post it on getdeb.net? Or is that out of line with the Handbrake people?

---

### Post by Polygon on 2008-07-22
why would it be out of line? handbrake is open source, you can pretty much post it anywhere =P

---

### Post by poofyhairguy on 2008-07-22
I can't wait for this project to stabilize. With a GUI to handbrake, I could finally kick my OSX habit...

---

### Post by Mic_Droz on 2008-07-23
Oh, has anyone had any sucess compiling the qt4 gui that is in the handbrake directory?

Can anyone tell me what the diff between the gtk gui and the qt4 gui would be? ie, performance-wise, stability-wise, other-wise (heh) etc. 

@polygon - thought they might get upset if you roll your own deb and spread it, especially if you rolled it wrong... (i am a n00b - can that even happen?)

I love this "svn update" business aswell, great way to update Handbrake's build...

---

### Post by Polygon on 2008-07-23
they cant get upset if you make your own deb and spread it around, the program is under the GPL

anyway, the qt4 gui is incomplete and buggy and most likely doesnt even work. on the forums there is another guy who is actually making a functional qt4 gui but i do not think it is checked in to the handbrake svn yet

so now the gtk gui is the only one, but im sure soon you will be able to choose between gtk and qt4 =P

---

### Post by hizzk on 2008-07-23
The qt4 GUI is the one I posted the 64-bit deb to a few posts up. As Polygon mentioned, though, it's not officially in the svn yet (they're waiting to see if the author is going to stay around and support/update it; the version that's currently in svn is unusable). If you visit that thread on the HandBrake forums, you can download the author's patch for the qt4 source that will add his new features, putting it nearly on par with the OSX version.

If anyone wants to try compiling it, I got it to work just fine with a little fiddling, so I'm happy to help with any problems.

However, the program's still a little buggy (I had problems with the queue when I tested it, and video previews aren't implemented yet, apparently) so I would wait for them to officially check it into the svn before using it extensively.

In the meantime, the CLI is fine for nonprofessional use. I'll probably even keep using it once the GUI situation is worked out, just because it's quicker to copy/paste my string of settings from a text file into a terminal than it is to click on a bunch of checkboxes/pull-down menus/etc.

---

### Post by toneman77 on 2008-07-24
> **Mic_Droz said:**
> I'm interested as well - I think everyone in this thread is quite interested - you've found the Holy Grail of video encoding for ubuntu! can you post it on getdeb.net? Or is that out of line with the Handbrake people?

Sadly I am currently in another city, but I'll ask my brother to turn on the machine this evening so I can download the debs and upload them somewhere. I'll keep you updated.

Toni

---

### Post by hizzk on 2008-07-24
sounds good, Toneman. In the meantime, if anyone wants to try compiling the updated qt4 GUI, here are the directions for that:

install git if you don't already have it ([FONT="Courier New"]sudo aptitude install git[/FONT]), then type
```

git clone git://repo.or.cz/HandBrake.git
```

navigate to the newly created HandBrake directory:

```
cd HandBrake
```

and add the bonne/qhandbrake branch:

```
git checkout --track -b bonne/qhandbrake origin/bonne/qhandbrake
```

You might need to type [FONT="Courier New"]git pull[/FONT] just to make sure you're up to date. Then,  compile HandBrakeCLI as normal:

```
./configure && jam
```

navigate to the qt4 directory:

```
cd qt4
```

and then compile the GUI (dependencies include qt4-core and qt4-dev-tools, I think):
```

qmake && make
```

You should be left with a binary named qtHB. This GUI is feature-complete (as far as I can tell), including video previews, a working queue, advanced x264 options, presets, and so on. You can run it by typing ./qtHB into a terminal, or you can copy it into your /usr/bin file like any other program.

---

### Post by toneman77 on 2008-07-24
Ok, have the debs for yasm and handbrake-gtk... where shall i put them ?

---

### Post by hizzk on 2008-07-24
> where shall i put them ?

Any ol' upload site should be fine for the short term. I recommend mediafire.com or rapidshare.com (just post the download link here once it's finished uploading). If you want a more long-term solution, you could try submitting them to getdeb.net or something similar, but you might want to wait and make sure they work for people first.

---

### Post by toneman77 on 2008-07-25
> **hizzk said:**
> Any ol' upload site should be fine for the short term. I recommend mediafire.com or rapidshare.com (just post the download link here once it's finished uploading). If you want a more long-term solution, you could try submitting them to getdeb.net or something similar, but you might want to wait and make sure they work for people first.

So here they are, hope they work for someone :D

[handbrake-gtk deb](http://www.mediafire.com/?tck2vmzuscd) 
[yasm deb file](http://www.mediafire.com/?mdylbeywrdm)

launch handbrake with "ghb" iirc

Toni

---

### Post by Mic_Droz on 2008-07-25
right...

Two questions before I do this again.. is there something I need to do, other than delete my directory of the Handbrake gui that I compiled myself inorder to try the deb out?

And secondly... @toneman77, do you think perhaps you could call the deb something else? like adding which svn checkout of Handbrake it is, which version, etc... ie handbrake-gtk_0.1-1_i386.deb isn't really descriptive of what it is, is it? Or is there something I'm missing?

Oh yeah, and do you guys think we should try to get this thread moved somewhere else? I think we've covered a lot of ground, and this should be extremely useful for a lot of people...

Cheers, 
Droz

---

### Post by toneman77 on 2008-07-26
> **Mic_Droz said:**
> right...

Two questions before I do this again.. is there something I need to do, other than delete my directory of the Handbrake gui that I compiled myself inorder to try the deb out?
Well i think the deb installs itself in the correct directories. I dont think it conflicts with your self compiled version.

> **Mic_Droz said:**
> And secondly... @toneman77, do you think perhaps you could call the deb something else? like adding which svn checkout of Handbrake it is, which version, etc... ie handbrake-gtk_0.1-1_i386.deb isn't really descriptive of what it is, is it? Or is there something I'm missing?
Well, that's what I do normally indeed. I was very frustrated after hand-compiling yasm and instaling other dependencies and stuff. So I was happy when checkinstall generated a deb at all. Sadly, I am not at my "compiling computer" for another 5 days, but the next time I'm home I'll keep an eye on the versioning and nameing.

Greetings
Toni

---

### Post by bobbocanfly on 2008-07-26
> **toneman77 said:**
> So here they are, hope they work for someone :D

[handbrake-gtk deb](http://www.mediafire.com/?tck2vmzuscd) 
[yasm deb file](http://www.mediafire.com/?mdylbeywrdm)

launch handbrake with "ghb" iirc

Toni

C0uld you upload a tar.gz of these debs in source form? (.dsc, .orig.tar.gz, .diff.gz)

Thanks

---

### Post by toneman77 on 2008-07-26
> **bobbocanfly said:**
> C0uld you upload a tar.gz of these debs in source form? (.dsc, .orig.tar.gz, .diff.gz)

Thanks

Sorry, but I don't know how to even do that. :(

---

### Post by hizzk on 2008-07-26
> C0uld you upload a tar.gz of these debs in source form?

The binary packaging method he used (checkinstall) doesn't appear to make those files automatically. He would have to repackage the binaries using dh_make and debuild to get those, I think.

However, if you just need the source code, it's all readily available (the GTK GUI is linked at the beginning of this thread, and the HandBrake code is all available from their site). I think the dependencies are all pretty much covered in other posts, as well.

---

### Post by zagor on 2008-07-29
> **hizzk said:**
> In my experience, these are the I visited the thread that acoustician linked to about an updated qt4 GUI and had much better luck compiling it. [Here's a link]("http://rapidshare.com/files/130694430/qtHB_amd64.deb") to a 64-bit deb of it if anyone wants to try it against the latest SVN (compile from SVN, then install the deb).


@Hizzk: I've downloaded your HandbrakeCLI and it works like a charm on the fresh Hardy 64 install I have.
Thanks, for at least this time I haven't got to go through all the dependencies stuff.
Unfortunately, instead, it seems the qt4 GUI deb does not work: it installs, but no binary is present.

Think you can post a new working deb?
I've also tried Toneman77's deb, but that's for i386...

Thanks

---

### Post by hizzk on 2008-07-29
> it seems the qt4 GUI deb does not work: it installs, but no binary is present.

:mad:I was afraid that might happen. Unfortunately, I'm not really sure how to go about packaging a proper binary of HandBrake that includes a GUI. I've seen examples of it online but have no clue how to go about it.:confused: If anyone wants to try and explain it to me, I'd be happy to give it a shot, though.

In the meantime, your best bet is to build it yourself, which really isn't that hard. Just apt-get all of the dependencies for HandBrake, as well as the ones for the qt4 GUI (basically just the qt4 and qt4-dev libs) then compile.

If you run into any problems with it, I'm happy to help you work through them.

---

### Post by zagor on 2008-07-29
> **hizzk said:**
>   Just apt-get all of the dependencies for HandBrake, as well as the ones for the qt4 GUI (basically just the qt4 and qt4-dev libs)

yeah, that's exactly what I didn't want to do... I've a fresh install and didn't want to load it with deps that I'm probably not going to use for any other program....

do you use checkinstall for your packages?
why the qt4 GUI should need the full HandBrackeCLI packaged together? 

Thanks

---

### Post by Polygon on 2008-07-29
i know with teh gtk gui you have to compile the gui with the path that the hand brake binary is in...so maybe you have to put the binary in like /usr/bin, compile the gui pointing the binary to that path, and then make a package out of it

---

### Post by hizzk on 2008-07-29
> why the qt4 GUI should need the full HandBrackeCLI packaged together?

Unfortunately, the GUI is inextricably linked to HandBrakeCLI, which is why the deb I packaged previously was only 4k. At the moment, there just isn't any easy way to get a working, feature-complete GUI for HandBrake without doing a little compiling (and even then you're using an SVN version of the code, which hasn't worked well for me [lots of weird errors and crashes in 2-pass encoding and no cpu extensions past SSE2 :(])

If you're dead-set on avoiding installing dependencies, you can try gHandBrake (which is a CLI wrapper, rather than a 'true' GUI; available [here]("http://filthypants.blogspot.com/2008/05/cpu-optimized-backend-for-ghandbrake.html")). The version that is available in a 64-bit deb binary doesn't have advanced x264 options, though, which is a deal-breaker in my opinion (there's a newer version that includes most of those options, but it's source-only...).

If none of these options is acceptable for you (as is the case with me), you can just keep using the regular ol' CLI version for another couple of months until the stable 0.9.3 version is finished, presumably with at least *one* of the GUIs in a usable state.

If you want, I can try just zipping up a prebuilt copy of HandBrakeCLI with its accompanying qt4 GUI and you can try running it like that (I have no idea if it will work, though). Even then, you'd probably have to at least install the non-dev qt4 libs so it would be able to draw the window/widgets. _Edit_:try it out [here]("http://rapidshare.com/files/133431591/qtHB_AMD64.zip").

---

### Post by Polygon on 2008-07-30
gHandbrake [SIZE="3"]**DOES NOT WORK**[/SIZE]

the majority of presets use advanced x264 options and ghandbrake has a nice little bug where it doesn't pass the advanced x264 options to the binary....

and the author of ghandbrake has abandoned the project so no updates are ever going to come to fix it

---

### Post by hizzk on 2008-07-30
> ghandbrake has a nice little bug where it doesn't pass the advanced x264 options to the binary....

Full Disclosure: I wrote (poorly) the code to implement the x264 options in gHandBrake but I'm not the original author.

I know this bug exists in HandBrakeGTK (aka RippedWire), the frontend that required mono-devel to run, but I haven't had any problems with gHandBrake (which doesn't even support presets, to my knowledge) not passing the options once they were added.

I quit using HandBrakeGTK because of this problem, but never ran into it with gHandBrake when I was working on it. Is there a chance you confused the two (which would be totally understandable based on the oh-so-similar names)?

---

### Post by Polygon on 2008-07-30
ghandbrake (which teh guy renamed ripped wire) is the one with the bug

the newest and better and supported GUI is just 'handbrake'. its an offical GUI that comes in the SVN trunk of handbrake, along with the windows and mac GUI's.

point im trying to make is, use the offical handbrake gui. Its actually supported and if you find and bugs there, fixing it there will benefit a lot of linux users that will be using the GUI, instead of just making a personal fix that benefits one person

---

### Post by hizzk on 2008-07-30
> use the offical handbrake gui. Its actually supported and if you find and bugs there, fixing it there will benefit a lot of linux users that will be using the GUI, instead of just making a personal fix that benefits one person

That's a good point about bugtesting with the official GUI, but some people have different requirements and/or limitations. For instance, I've never been able to successfully compile the 'official' GTK GUI, which forces me to use alternatives. Luckily, HandBrake has a lot of different options to choose from.:)

just to get it all in one place:

GHB is the GTK GUI that started this thread and is included with the HandBrake source code. It was written by a swell guy known as JohnAStebbins from the HandBrake forums and it's nearly on par with the OS X GUI in features. However, some people have trouble getting it to compile. (you can download a 32-bit deb binary from [here]("http://www.mediafire.com/?tck2vmzuscd") (courtesy of Toneman77), or get the source code from SVN).

qtHB (aka qHandBrake) is an early, yet promising GUI based on the official QT4 HandBrake code that languished in SVN until a HandBrake forums user known as gonza updated it recently. It is still in early development and not yet included in the official SVN code, but it is nearly as complete as GHB and significantly easier to compile (fewer dependencies). You can read about it [here]("http://forum.handbrake.fr/viewtopic.php?f=4&t=6388&p=38165#p36348") or download and compile it using my instructions [here]("http://ubuntuforums.org/showpost.php?p=5451481&postcount=65")).

HandBrakeGTK (aka RippedWire) is a port of a Windows CLI wrapper that requires mono-devel to run and doesn't pass x264 options (read about its history [here]("http://forum.handbrake.fr/viewtopic.php?f=13&t=4779#p26678") or download it [here]("http://rippedwire.sourceforge.net/downloads.html"))

gHandBrake is a GTK CLI wrapper written from scratch by a guy named Darren Wright. I later added x264 options to it, but I'm a terrible programmer and it ended up really unstable. Darren seems to have dropped the project because his site for it is gone (read about it [here]("http://ohioloco.ubuntuforums.org/showthread.php?p=3882022") or download it [here]("http://filthypants.blogspot.com/2008/05/cpu-optimized-backend-for-ghandbrake.html")).

---

### Post by toneman77 on 2008-07-31
> **toneman77 said:**
> Well i think the deb installs itself in the correct directories. I dont think it conflicts with your self compiled version.


Well, that's what I do normally indeed. I was very frustrated after hand-compiling yasm and instaling other dependencies and stuff. So I was happy when checkinstall generated a deb at all. Sadly, I am not at my "compiling computer" for another 5 days, but the next time I'm home I'll keep an eye on the versioning and nameing.

Greetings
Toni

1 hour ago I returned to my desktop machine and checked out the latest svn version 1598. I re-checkinstall-ed the file and called it "ghb" like the name of the binary, i hope this fits better.
so here it is:

[ghb_svn1598-1_i386.deb](http://www.mediafire.com/?bsbdgtgmsig)

(make sure you uninstall my previous handbrake-gtk deb)
Values i used for checkinstall:
> 
0 -  Maintainer: [ root@tones ]
1 -  Summary: [ gtk gui for handbrake. svn version ]
2 -  Name:    [ ghb ]
3 -  Version: [ svn1598 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gtk ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]


---

### Post by Mic_Droz on 2008-08-01
Hey guys, 

I've tried the old svn update install way (for the second time, the first time was quite successful), and even though handbrake itself is 1598, my gtk handbrake is still 1573... any ideas? or hasn't the gtk been updated?

---

### Post by hizzk on 2008-08-01
> even though handbrake itself is 1598, my gtk handbrake is still 1573... any ideas? or hasn't the gtk been updated?

I would guess that's what happened. HandBrake's code had been updated, making its version go up, while the GUI is still the same as the last one you tried.

Since you're using the SVN, have you had any issues with it not recognizing your cpu extensions? When I try to run the SVN version in a terminal, it says "MMX2 SSE2Slow", suggesting that it's not using any of the other extensions (SSE3, etc) :confused:

Are you having the same issue?

---

### Post by Polygon on 2008-08-01
if the maintainer had yasm installed then it should use whatever extensions that you have on your cpu. maybe it just doesn't use SSE3

---

### Post by toneman77 on 2008-08-09
it's weekend and i got the chance to built another svn of ghb

so here it is: svn 1620

[http://www.mediafire.com/?04z4ukj0pmu](http://www.mediafire.com/?04z4ukj0pmu)

any feedback if it works for someone else but me is welcome.

Tone

---

### Post by Dave_G on 2008-08-13
Hi,

I have followed the instructions in [http://ubuntuforums.org/showpost.php?p=5348490&postcount=26](http://ubuntuforums.org/showpost.php?p=5348490&postcount=26) and have installed the .deb in the above post; i have the HandBrake icon via Applications > Sound & Video, but when i click on the icon nothing happens.

Can someone please advise how i lauch the GUI HandBrake?

Many Thanks

PS. I also got following when i did ./autogen.sh in the gtk:

make[2]: *** No rule to make target `../../HandBrakeCLI', needed by `HandBrakeCLI'.  Stop.
make[2]: Leaving directory `/home/droz/hb-dev/gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/droz/hb-dev/gtk'
make: *** [all] Error 2

---

### Post by toneman77 on 2008-08-13
If you installed my deb file try launching the gui in a terminal window with
```
ghb
```
and tell us, what is displayed then.

---

### Post by Dave_G on 2008-08-14
I entered ghb in the terminal and got the following error:

dave@dave-desktop:~$ ghb
ghb: error while loading shared libraries: libdca.so.0: cannot open shared object file: No such file or directory
dave@dave-desktop:~$

---

### Post by Dave_G on 2008-08-15
*Bump*

---

### Post by hizzk on 2008-08-15
@Dave_G:

It looks like it's having trouble finding your HandBrakeCLI binary. Did you compile it without any errors before attempting to compile the GUI?

---

### Post by Dave_G on 2008-08-15
I installed Toneman's .deb first thinking that it would install everything and set it all up, but when i clicked on the HandBrake icon via the application > Video and Sound menu - nothing happened.  So i then carried out the instructions in [http://ubuntuforums.org/showpost.php?p=5348490&postcount=26](http://ubuntuforums.org/showpost.php?p=5348490&postcount=26), but i did get the below error when trying to do ./autogen.sh in the gtk:

make[2]: *** No rule to make target `../../HandBrakeCLI', needed by `HandBrakeCLI'. Stop.
make[2]: Leaving directory `/home/droz/hb-dev/gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/droz/hb-dev/gtk'
make: *** [all] Error 2

Will i need to do it all again - but in the right order?

---

### Post by hizzk on 2008-08-16
> I installed Toneman's .deb first thinking that it would install everything and set it all up

He made his binaries using checkinstall, which I've heard sometimes makes less-than-optimum debs that don't always fetch all dependencies, etc. I believe the debs it makes are intended more for personal use than for distribution because of this (no offense to Toneman, of course; I/we certainly appreciate him taking the time to supply these binaries :)).

If you're compiling from source anyway, I don't think there's any reason for you to even be messing with anyone's binaries.

Anyhow, back to your problem: did you get any errors during the first couple of steps? i.e., [FONT="Courier New"]./configure && make[/FONT] went okay? Those are the steps where HandBrakeCLI is actually being built, so they should take a long time (like a half-hour, depending on how fast your machine is) with lots of downloading happening.

After that, GHB is compiled separately (with its own set of dependencies), with your freshly compiled HandBrakeCLI binary used as a reference target.

Your errors suggest that the autogen script can't find the HandBrakeCLI binary, which is probably due to a failed compile of it. It also appears to be the same (albeit vague) error that Mic_Droz was getting earlier in this thread. His posts suggest that it was a dependency problem.

Did you download all of the dependencies listed in [this post]("http://ubuntuforums.org/showpost.php?p=5393573&postcount=47")? You should be able to apt-get everything but yasm v &#8805;0.7.1 (read elsewhere in  this thread about dependencies for further info; I think most of the angles have been covered).

---

### Post by toneman77 on 2008-08-16
What i did was
- i followed exactly these steps: [http://ubuntuforums.org/showpost.php?p=5348490&postcount=26](http://ubuntuforums.org/showpost.php?p=5348490&postcount=26)
at compile time i got lots of errors. i then installed everything that sounded like the thing the compiler complained about. the only thing i had to compile myself for the dependencies was yasm. the deb for yasm is linked in one of my previous posts.

I'm actually looking for tutorials to make "correct" deb files coz I start from zero here.

---

### Post by Dave_G on 2008-08-16
Thanks for the replies guys.  I think i definitley might be a mistake somewhere on my behalf so i will have another go at installing it.

Just one more thing; do i follow the very first post or this [http://ubuntuforums.org/showpost.php?p=5348490&postcount=26](http://ubuntuforums.org/showpost.php?p=5348490&postcount=26)

---

### Post by hizzk on 2008-08-17
From the beginning:

download these dependencies (sudo aptitude install):

> automake build-essential jam libdvdcss2-dev libtool subversion zlib1g-dev libbz2-dev dvdbackup xmlto texinfo g77 gfortran libgtk2.0-dev nasm doxygen libsdl1.2-dev gfortran-multilib gcc-multilib g++-multilib libesd0-dev libgtk1.2-dev libfftw3-dev electric-fence libx264-dev libx264-57 x264 libtheora-dev intltool gettext

Then, type this into a terminal:

```
svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake
```

once it finishes,

```
cd HandBrake
```

Then,

```
./configure && jam
```

That step will take a long time with lots of downloading while it fetches and compiles the various codecs.

Next,

```
cd gtk
```

then,

```
./autogen.sh
```

and finally,

```
make && sudo make install
```


> 
I'm actually looking for tutorials to make "correct" deb files coz I start from zero here.

I posted [this good one]("http://www.debian-administration.org/articles/337") earlier in the thread, but I've been having trouble making it work with any of the GUIs for HandBrake, for some reason. Let me know if you have any success with it or any other method.

---

### Post by Dave_G on 2008-08-18
Hizzk

I have followed your instructions but get a problem on the very last part (make && sudo make install); i am getting the below error:

dave@dave-desktop:~/HandBrake/gtk$ make && sudo make install
make  all-recursive
make[1]: Entering directory `/home/dave/HandBrake/gtk'
Making all in src
make[2]: Entering directory `/home/dave/HandBrake/gtk/src'
make[2]: *** No rule to make target `../../HandBrakeCLI', needed by `HandBrakeCLI'. Stop.
make[2]: Leaving directory `/home/dave/HandBrake/gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dave/HandBrake/gtk'
make: *** [all] Error 2
dave@dave-desktop:~/HandBrake/gtk$

---

### Post by hizzk on 2008-08-18
Hmmm. I'm stumped, Dave_G. I believe that error is implying that you don't have a Makefile, but one should have been created from the autogen.sh script. Did the autogen script run through without any errors? did it end with something like "Now type `make' to compile"? Does your 'gtk' directory have a Makefile in it?

---

### Post by FlintyVamp on 2008-08-20
Thought I would just chime in. I too am having the same problems as Dave_G

---

### Post by hizzk on 2008-08-20
@Dave_G or FlintyVamp:

does your autogen.sh script end with this?

```
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing intltool commands
config.status: executing po/stamp-it commands
Now type `make' to compile.
```

---

### Post by sefs on 2008-08-21
So my ubu brothers, where are the debs. :)

---

### Post by hizzk on 2008-08-22
> **sefs said:**
> So my ubu brothers, where are the debs. :)

Unfortunately, HandBrake (CLI or GUI) is a big PIA to package in my experience. I've tried a couple of different packaging methods (debuild and dpkg-deb, which I guess are essentially the same thing :confused:) and I can't get any of them to bundle properly. I keep ending up with super-small (~4k) debs that don't actually produce an executable when you install them. :(

If you want to try the qt4 GUI, you can download [this 64-bit binary]("http://rapidshare.com/files/133431591/qtHB_AMD64.zip") I compiled, but you'll have to download the dependencies manually (I think it's just the regular qt4 libs and maybe the dev tools; the regular HandBrakeCLI dependencies may also be needed, but I doubt it).

I know it's worked for at least 1 guy, but YMMV.

I'm sure it's possible to make a deb package of these GUIs, so please post directions if you have any idea on how to make it work.

---

### Post by sefs on 2008-08-22
Let me ask some other question....

1/
Can I install ubuntu 8.04 in a VMWare environment do all my compiling & experiment there (so i dont have to mess with my machine) and transfer the results over to the real machine.

2/
Also I downloaded the HandBrakeCLI binary from their website, would I then have to still compile that or can I just compile the gui and pair their binary with it?

3/
At the end of the compilation of the gui, can I install it manually so I know where and what is going unto the machine, instead of make install which can install anything anywhere?  

4/
Does the compilation of the GUI result in one binary file or does it have many files to go here and there.

5/
Can someone post a screen shot so and make my mouth water?

Thanks.

---

### Post by hizzk on 2008-08-22
> **sefs said:**
> 1. Can I install ubuntu 8.04 in a VMWare environment do all my compiling & experiment there (so i dont have to mess with my machine) and transfer the results over to the real machine.

For the most part, yes (esp. with respect to HandBrakeCLI). However, the GUIs may require libs to draw the widgets and so forth that wouldn't be available without installing them. You can give it a shot, but there's no guarantee. I recommend just using your main machine because none of the dependencies are particularly onerous.

> **sefs said:**
> 2. Also I downloaded the HandBrakeCLI binary from their website, would I then have to still compile that or can I just compile the gui and pair their binary with it?

Yes, you'll have to compile it from scratch. The GUIs are very tightly tied to the version of HandBrakeCLI/libhb that they are intended to be compiled against. Your compile will fail if you try to use any ol' version.

> **sefs said:**
> 3. At the end of the compilation of the gui, can I install it manually so I know where and what is going unto the machine, instead of make install which can install anything anywhere?

Generally, the 'make' step builds everything and 'make install' moves it around, so just look in your build directory for a newly created binary after the 'make' step and you should be able to put it wherever you please.

> **sefs said:**
> 4. Does the compilation of the GUI result in one binary file or does it have many files to go here and there.

Just 1 file, in my experience.

> **sefs said:**
> 5. Can someone post a screen shot so and make my mouth water?

Sure. Here's the [qt4 GUI]("http://www.flickr.com/photos/60069716@N00/2788061782/sizes/o/") running on my machine (not the whole window; you get the idea) :)

---

### Post by JimsArcade on 2008-08-22
[edit] never mind, I missed one step at the beginning.  Thanks for this great GUI!

---

### Post by toneman77 on 2008-08-22
> **sefs said:**
> Let me ask some other question....
...
5/
Can someone post a screen shot so and make my mouth water?

Thanks.

screenshots of my compile of the gtk gui ghb:
[[IMG]http://img106.imageshack.us/img106/1247/ghbpk6.th.jpg[/IMG]](http://img106.imageshack.us/my.php?image=ghbpk6.jpg)[[IMG]http://img122.imageshack.us/img122/7740/ghb2ni5.th.png[/IMG]](http://img122.imageshack.us/my.php?image=ghb2ni5.png)

sadly, ghb produces unplayable sound for me... but that's another story :)

---

### Post by Dave_G on 2008-08-24
Hizzk, sorry for the delay as i have been on holiday.

I can confirm that i do have a makefile in the 'gtk' folder and i have typed 'make' again in the terminal, but i got the below error again:

dave@dave-desktop:~/HandBrake/gtk$ make
make  all-recursive
make[1]: Entering directory `/home/dave/HandBrake/gtk'
Making all in src
make[2]: Entering directory `/home/dave/HandBrake/gtk/src'
make[2]: *** No rule to make target `../../HandBrakeCLI', needed by `HandBrakeCLI'. Stop.
make[2]: Leaving directory `/home/dave/HandBrake/gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dave/HandBrake/gtk'
make: *** [all] Error 2
dave@dave-desktop:~/HandBrake/gtk$

I'm stumped as what to do now?

> **hizzk said:**
> Hmmm. I'm stumped, Dave_G. I believe that error is implying that you don't have a Makefile, but one should have been created from the autogen.sh script. Did the autogen script run through without any errors? did it end with something like "Now type `make' to compile"? Does your 'gtk' directory have a Makefile in it?

---

### Post by Dave_G on 2008-08-24
I do remember the last part stating to type 'make'.

> **hizzk said:**
> @Dave_G or FlintyVamp:

does your autogen.sh script end with this?

```
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing intltool commands
config.status: executing po/stamp-it commands
Now type `make' to compile.
```

---

### Post by Dave_G on 2008-08-29
*bump*

---

### Post by hizzk on 2008-08-29
Hey Dave_G, sorry I haven't replied earlier. I just haven't been able to come up with anything that could help :confused:

Could you try posting your entire output from autogen.sh? I'm not sure what else to try other than making sure your dependencies are all filled.

---

### Post by Dave_G on 2008-08-30
hizzk

Thanks for the reply; below is a copy of the autogen.sh output.

> dave@dave-desktop:~/HandBrake/gtk$ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running intltoolize...
Running libtoolize...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
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
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GHB... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing intltool commands
config.status: executing po/stamp-it commands
Now type `make' to compile.

---

### Post by hizzk on 2008-08-30
Dave_G,
that output looks good to me. I have no idea why 'make' would be failing for you like it is :confused:

I'm sorry I can't come up with any suggestions. If you manage to get it working, be sure to post your solution here, though. I'm very curious to see what could be the problem... :(

---

### Post by Dave_G on 2008-08-30
hizzk, i have done a search for HandBrakeCLI but no files are found! Have i done something wrong somewhere?  Should the HandBrakeCLI already be installed?

If i have to install HandBrakeCLI then what post/thread do i follow as i'm getting in a bit of a muddle #-o](*,)

---

### Post by hizzk on 2008-08-30
oh, I assume that means the compile for HandBrakeCLI failed, then. When following the steps, did you get any errors after the third step ([FONT="Courier New"]./configure && jam[/FONT])?

This is the step where HandBrakeCLI is compiled and then the next steps compile the GUI against that CLI binary. This step should take a long time and lots of text should scroll by as it compiles all of the codecs into the binary.

If it's successful, you should end up with a binary called HandBrakeCLI sitting in your HandBrake folder. If it fails, post your error here and I'll try to help.

---

### Post by Dave_G on 2008-08-31
hizzk, i did what you said above and got the below errors; i swear that i never had this problem before when i did ./configure && jam.  What should i do now?

> dave@dave-desktop:~/HandBrake$ ./configure && jam
System: Linux
Endian: little

To build HandBrake, run:
 './jam' on a Mac (or 'make' to try the UB build method),
 'jam' on Linux or Windows.
...found 329 target(s)...
...updating 41 target(s)...
LibX264 contrib/lib/libx264.a 
patching file encoder/slicetype.c
Hunk #1 succeeded at 370 (offset -9 lines).
No suitable assembler found.  Install 'yasm' to get MMX/SSE optimized code.
If you really want to compile without asm, configure with --disable-asm.

    cd `dirname contrib/x264.tar.gz` && CONTRIB=`pwd` &&
    rm -rf x264 && (gzip -dc x264.tar.gz | tar xf - ) && 
    cd x264 &&  patch -p0 < ../patch-x264-idr.patch && 
    bash ./configure --prefix=$CONTRIB --enable-pthread &&
    make libx264.a && cp libx264.a $CONTRIB/lib/ && cp x264.h $CONTRIB/include/ && strip -S $CONTRIB/lib/libx264.a

...failed LibX264 contrib/lib/libx264.a ...
Cc libhb/common.o 
Cc libhb/hb.o 
libhb/hb.c: In function &#8216;hb_detect_comb&#8217;:
libhb/hb.c:454: warning: unused variable &#8216;flag&#8217;
Cc libhb/ports.o 
Cc libhb/scan.o 
Cc libhb/work.o 
libhb/work.c:117: warning: return type defaults to &#8216;int&#8217;
libhb/work.c: In function &#8216;hb_display_job_info&#8217;:
libhb/work.c:324: warning: control reaches end of non-void function
Cc libhb/decmpeg2.o 
Cc libhb/encavcodec.o 
Cc libhb/update.o 
Cc libhb/demuxmpeg.o 
Cc libhb/fifo.o 
Cc libhb/render.o 
Cc libhb/reader.o 
Cc libhb/muxcommon.o 
Cc libhb/muxmp4.o 
Cc libhb/sync.o 
Cc libhb/stream.o 
Cc libhb/decsub.o 
Cc libhb/deca52.o 
Cc libhb/decdca.o 
Cc libhb/encfaac.o 
Cc libhb/declpcm.o 
Cc libhb/encx264.o 
Cc libhb/decavcodec.o 
Cc libhb/encxvid.o 
Cc libhb/muxavi.o 
Cc libhb/enclame.o 
Cc libhb/muxogm.o 
Cc libhb/encvorbis.o 
Cc libhb/dvd.o 
Cc libhb/muxmkv.o 
Cc libhb/deblock.o 
Cc libhb/deinterlace.o 
libhb/deinterlace.c:97: warning: initialisation from incompatible pointer type
Cc libhb/denoise.o 
Cc libhb/detelecine.o 
Cc libhb/decomb.o 
libhb/decomb.c: In function &#8216;store_ref&#8217;:
libhb/decomb.c:127: warning: unused variable &#8216;h&#8217;
libhb/decomb.c: In function &#8216;yadif_filter&#8217;:
libhb/decomb.c:637: warning: unused variable &#8216;next&#8217;
libhb/decomb.c:635: warning: unused variable &#8216;prev&#8217;
libhb/decomb.c: At top level:
libhb/decomb.c:141: warning: &#8216;get_ref&#8217; defined but not used
Cc libhb/enctheora.o 
Archive libhb/libhb.a 
Ranlib libhb/libhb.a 
Cc test/test.o 
test/test.c:91: warning: &#8216;cfr&#8217; defined but not used
Cc test/parsecsv.o 
...skipped HandBrakeCLI for lack of contrib/lib/libx264.a...
...failed updating 1 target(s)...
...skipped 1 target(s)...
...updated 39 target(s)...
dave@dave-desktop:~/HandBrake$

---

### Post by amauk on 2008-08-31
> **Dave_G said:**
> hizzk, i did what you said above and got the below errors; i swear that i never had this problem before when i did ./configure && jam.  What should i do now?
Dave_G,

You don't appear to have Yasm installed
(it's an assembler needed by handbrake)

Unfortunately, the Ubuntu repos have an old version that won't work properly
so you have to compile from source

go here
[http://www.tortall.net/projects/yasm/wiki/Download]("http://www.tortall.net/projects/yasm/wiki/Download")
and download the source tarball

bung it in a directory in your home folder
Eg. ~/src/yasm/

Then
cd ~/src/yasm
./configure && make
sudo make install

now, try compiling handbrake

---

### Post by Dave_G on 2008-08-31
Amauk, downloading Yasm and installing it did the job - woohoo!!!:guitar:

I did already have Yasm installed, but like you said it wasn't doing the trick!

I have done a screenshot of the GUI Handbrake, can you confirm if everything is how it should look?

Many thanks, i knew i would get there in the end!:)

Also many thanks Hizzk for your persistence with helping me!

[IMG]http://ubuntuforums.org/picture.php?albumid=506&pictureid=1727[/IMG]

---

### Post by toneman77 on 2008-08-31
Congratulations!
Did u maybe try to encode a xvid with ac3 pass-through ? (DVD source)
My tries with 8 svn builds all failed and i would be interested in another one's results.

Greetings
Tone

---

### Post by Dave_G on 2008-08-31
Toneman

You might have to instruct me how to do the below as I haven't messed about with it yet.  I have got a movie as an .ISO to use as a source in Handbrake; can i use the ISO for the below?

Could you give me instructions to try out your test below?

Cheers.

> **toneman77 said:**
> Congratulations!
Did u maybe try to encode a xvid with ac3 pass-through ? (DVD source)
My tries with 8 svn builds all failed and i would be interested in another one's results.

Greetings
Tone

---

### Post by Dave_G on 2008-08-31
Ok, i'm having a go at encoding the .ISO file to MPEG-4 (xViD) with the ac3 pass-through; it is currently on 'Encoding task 1 of 2 89%.

If will update when it finishes and if it works.

Edit: Now on Task 2 of 2; 3% complete

---

### Post by toneman77 on 2008-08-31
Sure. 
I used the following settings:
-Container: avi

-Picture: nothing changed

-Video:
 -Video Codec: MPEG-4 (XviD)
 -Framerate: Same as source
 -2-Pass Encoding and Turbo First Pass enabled
 -Target Size: as u wish

-Audio/Subtitles:
 -2 Audio Trackes with Codec: AC3 (pass-thru)
 -Subtitles: none
 -Allow only forced subtitles

---

### Post by Dave_G on 2008-08-31
Toneman, the film .ISO i used ripped to MPEG-4 (XviD), and also chose the AC3 (pass-thru)........but the only problem is that the sound doesn't come on.

---

### Post by toneman77 on 2008-08-31
> **Dave_G said:**
> Toneman, the film .ISO i used ripped to MPEG-4 (XviD), and also chose the AC3 (pass-thru)........but the only problem is that the sound doesn't come on.

ok, then thats the same problem that i have. thanks for the time for testing this.

---

### Post by Mic_Droz on 2008-09-01
Hey, just still checking what everyone's versions of GHB are...

is it this?

[IMG]http://i217.photobucket.com/albums/cc7/M_Droz/Screenshot-AboutHandBrake.png[/IMG]

And I finally managed to create a video on my laptop that could finally be read by something other than the laptop - my iPhone now likes to play futurama. Its been such a long time...

oh yeah, and seeing as my laptop is horrible at this encoding game, what does everyone think of getting a "mini" pc (you know, just a tiny box with some usb ports, a multi-core processor, and some ram) ? I'm looking for the cheapest possible way to encode video faster than my faulty 1.73 ghz pentium m that only runs at 1.3...(hah! came out just before all this was being rebranded centrino!)

---

### Post by toneman77 on 2008-09-01
I'm using svn1659 right now.

---

### Post by Dave_G on 2008-09-01
Does anyone know if Handbrake can shrink a DVD down to a 256MB 3gp/MP4 file to play on a mobile phone, as i know Nero Recode is able to do it.

---

### Post by hizzk on 2008-09-01
> **Mic_Droz said:**
> what does everyone think of getting a "mini" pc (you know, just a tiny box with some usb ports, a multi-core processor, and some ram) ?

If you're familiar with building computers from parts, you could assemble something simple with a micro-ATX motherboard and a cheap AMD X2 or Core2Duo/Quad CPU for around $250-400. Beyond just an improvement in clockspeed, moving to a modern CPU will also give you a huge speed improvement from the addition of newer SSE extensions. It'll certainly save you some time and free up your laptop for other things.

> Does anyone know if Handbrake can shrink a DVD down to a 256MB 3gp/MP4 file to play on a mobile phone, as i know Nero Recode is able to do it.

HandBrake should be capable, it's just a matter of knowing exactly what the phone requires for playback. If it's just a matter of filesize, you can set the maximum through the GUIs or using the -S [size in MB] option on the CLI (see more [here at the HandBrake wiki]("http://trac.handbrake.fr/wiki/CLIGuide")). You may also have to use a specific resolution and/or codec, so be sure to check your phone's documentation to know for sure.

> Hey, just still checking what everyone's versions of GHB are...

svn1661 for me. HandBrake development moves fast! :)

If anyone's interested, [here's a link]("http://rapidshare.com/files/141828793/GHB.tar.gz") to a proper 32-bit deb binary of GHB--the GTK GUI--that I just built from the latest SVN (it's compressed into a tarball, but the deb binary is inside). Let me know if it works.

---

### Post by Dave_G on 2008-09-02
hizzk, if i wanted to put the movie on my Sony Ericsson W810i (I know Sony uses the 3gp), would i need to choose the XviD or FFMPEG option?

---

### Post by hizzk on 2008-09-02
> if i wanted to put the movie on my Sony Ericsson W810i (I know Sony uses the 3gp), would i need to choose the XviD or FFMPEG option?

AFAIK, HandBrake doesn't support 3gp output, but 3gp is a subset of the mp4 standard, so your phone can probably play regular mp4 files too. I would stick with the ffmpeg mp4 encoder.

According to [this forum]("http://www.expansys.com/ft.aspx?k=70865"), you'll need to set the resolution to 176x144 with AAC or MP3 audio (set the bitrate to ~96kbps). The overall bitrate should probably be somewhere around 250-300kbps.

The guys at that forum can probably help you more than I can if you run into any phone-specific problems.

---

### Post by Dave_G on 2008-09-02
Hizzk, thanks for the help!  I will give your suggestion a try when i get home from work.

---

### Post by Mic_Droz on 2008-09-03
How frustrating - only after deleting the hb directory and redownloading everything again, does handbrake gtk show me svn1663.

i've been doing the svn updates for ages! and it never updated!

and now i have a problem where it says

** (ghb:24533): WARNING **: Plist parse error: Error on line 1 char 2: Document must begin with an element (e.g. <book>)

(ghb:24533): GLib-CRITICAL **: g_markup_parse_context_end_parse: assertion `context->state != STATE_ERROR' failed
 but it still starts up fine...

sigh. 

and Handbrake doesn't appear in my sound & video menu anymore...

grrr

---

### Post by hizzk on 2008-09-03
> **Mic_Droz said:**
> How frustrating - only after deleting the hb directory and redownloading everything again, does handbrake gtk show me svn1663.

I was perusing the HandBrake forums and coincidentally came across [this post from JohnAStebbins]("http://forum.handbrake.fr/viewtopic.php?f=13&t=6893#p39071"), which indicates that just using [FONT="Courier New"]svn update[/FONT] *was* in fact updating your source, but the version number displayed won't update if you compile using [FONT="Courier New"]jam[/FONT]. Instead, you'll need to use [FONT="Courier New"]make[/FONT], which is the same but adds the additional version-tracking step. Go figure... :/

I don't know what to tell you about the errors or lack of menu entries, though.

---

### Post by JohnAStebbins on 2008-09-03
To be sure that you have the proper version number compiled in, it is recommended that you use make instead of jam when building HandBrake.  This will always regenerate the version.h file.  Jam will not.  If you insist on using jam. You must ./configure; jam clean; jam to get the version updated.

Regarding the "Plist parse error". You should only see this the first time you start the latest svn version.  I've changed the format presets and preferences are stored in.  This is the parser complaining about the old format.  It should write new data out and not complain again.  If you had any custom presets, they will be lost.

I can't reproduce the problem with the menu item in sound & video. sudo make install seems to be working fine here.

My last commit was one scary big change. Expect bugs.

---

### Post by hizzk on 2008-09-03
JohnAStebbins, I just wanted to extend a big 'Thanks!' from all of us for your hard work on giving HandBrake a 1st class GUI in linux. You've made a lot of terminal-shy folks very happy. :)

---

### Post by Mic_Droz on 2008-09-03
Yep, I have to admit, this program has almost completed the circle of things I can do in Linux that I no longer have to do in windows... *almost*

Well done to J!

---

### Post by hugmenot on 2008-09-06
Hmm, compiled ok, but crashes on startup.

```
$ ghb
*** glibc detected *** ghb: free(): invalid pointer: 0x0ae936d0 ***
```


long output:
[http://en.pastebin.ca/1195902](http://en.pastebin.ca/1195902)

---

### Post by JohnAStebbins on 2008-09-06
I can't tell very much from that message.  when you got the latest, did you re-run autogen.sh and make clean?  there were several files added.

If your still having problems, you could help me narrow it down with gdb.

# gdb ./ghb
(gdb) run
<after it crashes>
(gdb) bt

That should show me more about where it's crashing.

---

### Post by hugmenot on 2008-09-07
> **JohnAStebbins said:**
> I can't tell very much from that message.  when you got the latest, did you re-run autogen.sh and make clean?  there were several files added.

Yes, I made clean and re-ran autogen.sh. But I'm trying to compile this on the Intrepid development series, mind you.

> 
If your still having problems, you could help me narrow it down with gdb.

# gdb ./ghb
(gdb) run
<after it crashes>
(gdb) bt

That should show me more about where it's crashing.

attached. If you need something else, go ahead.

---

### Post by JohnAStebbins on 2008-09-07
Well, that wasn't exactly smoking gun information. But it helped. I think I located it.  An improper g_free of a GtkTreePath instead of gtk_tree_path_free.

---

### Post by hugmenot on 2008-09-07
Spot on. Works now!

---

### Post by hugmenot on 2008-09-07
Me again. I got a new crash on startup. 

```
$ ghb
*** glibc detected *** ghb: free(): invalid next size (normal): 0x09370110 ***
```

I couldn&#8217;t believe it and toyed around with recompilation again. But then I figured it must&#8217;ve been something else, so I looked around where ghb stores it&#8217;s config, found it in ~/.config/ghb and deleted this folder. Now it doesn&#8217;t crash anymore. Still, once I can replicate I will post a backtrace. Do you prefer this at trac.handbrake.fr?

---

### Post by JohnAStebbins on 2008-09-07
Trac isn't open to the unwashed masses.  We prefer bugs to be reported in the bugs forum for *released* versions only.  We triage them from there. Ghb bugs should *not* be reported in the bugs forum yet. The other dev's would get a little bent over my bugs cluttering that forum. Normally, hb policy is not to accept bug reports for unreleased code, but i'm kind of a special case right now since there's been no releases since ghb's become usable.  So please post any ghb bug reports to the unix forum.

[http://forum.handbrake.fr/](http://forum.handbrake.fr/)

Regarding this particular problem. If you can reproduce it, please pastebin preferences, presets, and queue (if present) from your config dir.

[http://handbrake.fr/pastebin/](http://handbrake.fr/pastebin/)

---

### Post by JohnAStebbins on 2008-10-01
For those brave enough to try work-in-progress code, but not brave enough to build your own from svn.  There is now a binary snapshot release of the gtk gui for Ubuntu 8.04.

See the announcement here:
[http://forum.handbrake.fr/viewtopic.php?f=13&t=7230](http://forum.handbrake.fr/viewtopic.php?f=13&t=7230)

---

### Post by toneman77 on 2008-10-01
/me will definitely try this 
(and keep on trying the svn ;) )

---

### Post by bishoptf on 2008-10-03
Wanted to Chime in, running Hardy x64 bit, using svn 1799, all seems well, used the combination of a couple of posts I should proabably write up exactly what I did but always just go and do it...Great work:D, I have one question though...I encoded a movie for my 5g ipod in high rez format, and for some reason it didn't want to play I think I have the latest firmware but to no avail, it appears to play fine in the low rez mode....If somone needs someone to test .debs let me know...

---

### Post by Yaka on 2008-10-05
> **JohnAStebbins said:**
> For those brave enough to try work-in-progress code, but not brave enough to build your own from svn.  There is now a binary snapshot release of the gtk gui for Ubuntu 8.04.

See the announcement here:
[http://forum.handbrake.fr/viewtopic.php?f=13&t=7230](http://forum.handbrake.fr/viewtopic.php?f=13&t=7230)



thanks a million fella, i love the work youve done

---

### Post by Polygon on 2008-10-06
compiling question

after i compile everything once, how do i make it ACTUALLY recompiles everything again, cause after i run a svn update, it updates the files, but then i do "jam clean" and all that does is clear the handbrake binary, and if i try to compile it again, it just links all of the previously compiled files without actually recompiling it again.

The only solution ive found so far is deleting everything in the handbrake svn folder and then redownloading everything then recompiling, but surely there must be some command for this?

---

### Post by hugmenot on 2008-10-09
The bulk of the compilation time goes into compiling all the library dependencies that are copied into the tree. You really don&#8217;t need to recompile those each time. When the Handbrake team chooses to include a newer version of libx264, say, then it will be rebuilt automatically.


JohnAStebbins, I&#8217;m looking for a "debian" packaging directory that works for making personal snapshot debs of Handbrake. Do you have something like this?

---

### Post by Polygon on 2008-10-09
but for me at least, when any of the libraries are updated and i run jam again, it doesnt recompile the library that changed. also after thats all said and done, the svn number in help > about does not change.

---

### Post by hugmenot on 2008-10-10
How about running make?

---

### Post by Polygon on 2008-10-19
it seems that until recently jam was the preferred method of compiling it. but now it seems they want you to use make

---

### Post by Bou on 2008-11-24
Handbrake 0.9.3 has just been released and is available as a .deb file.

[http://forum.handbrake.fr/viewtopic.php?f=13&t=7771](http://forum.handbrake.fr/viewtopic.php?f=13&t=7771)

Do you guys happen to know where some interface suggestions could be sent to? I love the app, but the interface is madness.

---

### Post by toneman77 on 2008-11-24
awesome. i'm gonna check that out as soon as i'm back home (sadly, that means friday)

thumbs up

---

### Post by Polygon on 2008-11-24
> **Bou said:**
> Handbrake 0.9.3 has just been released and is available as a .deb file.

[http://forum.handbrake.fr/viewtopic.php?f=13&t=7771](http://forum.handbrake.fr/viewtopic.php?f=13&t=7771)

Do you guys happen to know where some interface suggestions could be sent to? I love the app, but the interface is madness.

the gtk gui i think is a lot better then the windows version, and i dunno what you could do to the interface, since its designed towards power users who want to have access to advanced features.  Really all the standard user has to deal with is the presets (right side), preview (the bottom right) and the top where you tell it where to save it

you can post suggestions on their forums, but beware, most of the devs are jerks.. example here:

[http://forum.handbrake.fr/viewtopic.php?f=13&t=7771#p43493](http://forum.handbrake.fr/viewtopic.php?f=13&t=7771#p43493)

"why did you take out dvd decrypyting?"

BECAUSE WE SAID SO. IF YOU DON'T LIKE IT, LEAVE, RAWRRR

---

### Post by lingenfr on 2008-11-24
That was my experience. For the headaches of setting it up and using, it just wasn't worth it. The people who knew the answers were asses. I am unsubscribing from this thread as each time I see an update in my inbox, it is too disappointing to see no progress. There are just too many good, finished alternatives available to deal with this silliness. Thanks to those of you who continue to keep the hope alive.

---

### Post by hugmenot on 2008-11-25
> **Polygon said:**
> 
you can post suggestions on their forums, but beware, most of the devs are jerks.. example here:

[http://forum.handbrake.fr/viewtopic.php?f=13&t=7771#p43493](http://forum.handbrake.fr/viewtopic.php?f=13&t=7771#p43493)

"why did you take out dvd decrypyting?"

BECAUSE WE SAID SO. IF YOU DON'T LIKE IT, LEAVE, RAWRRR

Well, don&#8217;t post if you yourself are a jerk. Right, Poly? I&#8217;m totally on the side of the devs here. Open source associated users can be a pain in the ***.

I mean, it&#8217;s so obvious why they don&#8217;t ship dvdcss. Why even bother to demand a reason? Tell me. They want their program to live and shipping illegal software is the best way to spoil it for everyone.

---

### Post by Bou on 2008-11-25
> **Polygon said:**
> the gtk gui i think is a lot better then the windows version, and i dunno what you could do to the interface, since its designed towards power users who want to have access to advanced features.

Well, I made a quick mockup based on Oggconvert. Please give it a look:

[IMG]http://img518.imageshack.us/img518/1415/screenshotql5.png[/IMG]

Some options don't appear, mostly the ones I didn't know what they were for, but most of the stuff is already there and it's a lot more HIG compliant.

What do you think?

---

### Post by Moustacha on 2008-11-25
I find the interface easy enough to use for a novice at video encoding. The new release is brilliant though. Flies though movies at 200fps on my mediocre settings.
handbrake still has dvdcss support through libdvdcss though doesn't it? I just don't think there's any solution for windows, unless it looks for a dll in it's directory which I don't know.

---

### Post by Bou on 2008-11-25
> **Polygon said:**
> you can post suggestions on their forums

Thanks, just did: [http://forum.handbrake.fr/viewtopic.php?f=26&t=7842](http://forum.handbrake.fr/viewtopic.php?f=26&t=7842)

---

### Post by Polygon on 2008-11-26
your missing two very important things: preview window and preset window

---

### Post by 50words on 2008-11-26
Will Handbrake let me convert DVD .iso files to an .avi I can play from iTunes?

---

### Post by Polygon on 2008-11-26
it should with the correct presets.

---

### Post by michaelzap on 2008-11-26
I was all excited to install Handbrake 0.9.3 since I'd always heard how awesome it was. The GUI is fine as far as I'm concerned, but I'm not really sure what all the fuss is about. I seem to get better quality files from Avidemux, and it has a whole lot more options and features as well.

Am I missing something? Does Handbrake have anything that Avidemux doesn't? Or is something that they both have superior in Handbrake for some reason that I haven't noticed?

I really want a decent native Linux app to rip DVD subtitles to .srt files, and I was kind of bummed to see that Handbrake doesn't do that at all...

---

### Post by Polygon on 2008-11-26
its mainly for converting a dvd like source to a file. It used to be able to decode dvds too but they took it out and the developers are being childish and not telling us WHY they took it out, so you have to install libdecss or whatever.

It also has a bunch of presets so if you want to rip a movie to an ipod, or a psp, you stick your dvd in and go. with avidemux you have to know exactly what settings and resolution and all that to make it work...and even then it might not work for stuff like ipods cause it needs a special bit in there for it to work.

---

### Post by michaelzap on 2008-11-26
> **Polygon said:**
> its mainly for converting a dvd like source to a file...It also has a bunch of presets so if you want to rip a movie to an ipod, or a psp, you stick your dvd in and go. with avidemux you have to know exactly what settings and resolution and all that to make it work...and even then it might not work for stuff like ipods cause it needs a special bit in there for it to work.

I rip DVDs using Avidemux all the time (just select the first VOB file and it will ask you if you want to index and join them all). And Avidemux actually has quite a few presets, including iPod and PSP (you'll find them in the Auto menu). And of course Avidemux is capable of reading and writing bazillions more formats than Handbrake and adding all manner of filters to the process.

Handbrake just seems like an Apple-centered version of Avidemux with far fewer options and features as far as I can tell.

---

### Post by Bou on 2008-11-27
> **Polygon said:**
> your missing two very important things: preview window and preset window

Yeah, I made some new mockups with those. What do you think?

---

### Post by Polygon on 2008-11-28
> **michaelzap said:**
> I rip DVDs using Avidemux all the time (just select the first VOB file and it will ask you if you want to index and join them all). And Avidemux actually has quite a few presets, including iPod and PSP (you'll find them in the Auto menu). And of course Avidemux is capable of reading and writing bazillions more formats than Handbrake and adding all manner of filters to the process.

Handbrake just seems like an Apple-centered version of Avidemux with far fewer options and features as far as I can tell.

im sure there is some advantage to using handbrake, go ask on their forums if you really wnat to know.

and bou, those look better

---

### Post by Bou on 2008-11-28
> **lingenfr said:**
> That was my experience. For the headaches of setting it up and using, it just wasn't worth it. The people who knew the answers were asses.

By the way, from my short experience discussing my suggestions with the developers they were the exact opposite of "asses". They were receptive and collaborative.

Just for the record.

---

### Post by bruce89 on 2008-11-28
> **Bou said:**
> By the way, from my short experience discussing my suggestions with the developers they were the exact opposite of "asses". They were receptive and collaborative.


Get them to use a proper build system - [http://ubuntuforums.org/showthread.php?t=992997](http://ubuntuforums.org/showthread.php?t=992997)

---

### Post by 50words on 2008-11-29
I downloaded the .deb from the Handbrake website, but when I try to run it (via terminal), I get the following error:

ghb: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

I am using 8.04, and I cannot find that package anywhere.

---

### Post by JohnAStebbins on 2008-11-29
If you read the download page carefully, you'll see that those packages were built for Intrepid (8.10).  You'll have to upgrade ubuntu, or build from source.

---

### Post by natrik on 2008-11-30
> **50words said:**
> ghb: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

I am using 8.04, and I cannot find that package anywhere.

> **JohnAStebbins said:**
> You'll have to upgrade ubuntu, or build from source.

Alternatively, if you're careful, you can get around this like I did, and not have to upgrade to a new distribution, and not have to compile anything from sources:

Add the apt line for intrepid packages (I use synaptic, in which case it's listed under "Settings > Repositories > Third party software").  Here is one possible sources line to add:
```
deb http://mirrors.kernel.org/ubuntu intrepid main
```
Then reload the package information, select the libxcb items of importance, download, install, make sure handbrake is not missing anything else... 

**And then REMOVE THE INTREPID SOURCES to stay otherwise in 8.04. ** This is important for me because the 'nvidia' driver currently available for my GeForce4 MX 440 IS INCOMPATIBLE with the new xorg in 8.10.   I figure I'll just wait for nvidia to catch up, but I want handbrake NOW!  :o)

Of course, you could just download the .deb files independently and install them manually with dpkg or something.

For other mirrors, check out the download page for libxcb-render-util0 ... [http://packages.ubuntu.com/intrepid/i386/libxcb-render-util0/download](http://packages.ubuntu.com/intrepid/i386/libxcb-render-util0/download)

-- Nate

---

