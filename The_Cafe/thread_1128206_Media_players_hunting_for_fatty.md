---
title: "Media players: hunting for fatty"
date: 2009-04-17
forum: The Cafe
---

### Post by directhex on 2009-04-17
The choice of media player is mentioned fairly frequently on this forum. For your viewing pleasure, here are some numbers to occupy you to help spot the most heavyweight option. Bear in mind that whilst hard disk space is cheap, space on the LiveCD is at a major premium - every fraction of a megabyte needs to be argued for. I'm trying to include all the options here that I've noticed people on the forum suggesting

Remember, Rhythmbox is the baseline. Numbers for AMD64 Jaunty.

And I'm not discussing features or usability here - only size. Obviously a featureless player is a poor choice for default, even if it were tiny.

```

Player     | Version                     | Disk space incl unique deps | Resident memory - playback, 19-track test library
-----------+-----------------------------+-----------------------------+---------------------------------------------------
Amarok     | 2:2.0.2mysql5.1.30-0ubuntu2 | [COLOR="Red"]221 MiB[/COLOR]                     | [color="red"]145.5 MiB[/color]
Banshee    | 1.4.3-4                     | 12.3 MiB                    | 61.8 MiB
Exaile     | 0.2.14-0ubuntu2             | 78.2 MiB                    | 68 MiB
Quod Libet | 2.0-1ubuntu2                | [COLOR="Lime"]9327 KiB[/COLOR]                    | 56.6 MiB
**Rhythmbox  | 0.12.0-0ubuntu4             | 18.4 MiB                    | [COLOR="Lime"]50.1 MiB[/color]**
Songbird   | 1.1.1-0ubuntu1~fta4         | 42.6 MiB                    | 98.5 MiB

```

So now you know!

---

### Post by Mehall on 2009-04-17
Given how featureful and complete Rhythmbox is, and that it has the lowest memory footprint, (and that it's dependencies are maybe more shared than some of the others, though i don't know for sure) I think it's the perfect choice. (Quod Libet, I admit, is a not bad second based on these stats, but not a player I have tested)

---

### Post by Tibuda on 2009-04-17
I prefer Quod Libet because of the tagging features and the clean interface. The only thing I miss from Banshee/Rhythmbox is Last.fm, but I can use the web interface for that.

---

### Post by gnomeuser on 2009-04-17
It may be interesting to examine how the different players scale in memory use and responsiveness as collections grow.

---

### Post by directhex on 2009-04-17
> **gnomeuser said:**
> It may be interesting to examine how the different players scale in memory use and responsiveness as collections grow.

I'm at the office, so don't have access to my music. hence 19-track collection (from archive.org)

---

### Post by directhex on 2009-04-17
> **Mehall said:**
> Given how featureful and complete Rhythmbox is, and that it has the lowest memory footprint, (and that it's dependencies are maybe more shared than some of the others, though i don't know for sure) I think it's the perfect choice. (Quod Libet, I admit, is a not bad second based on these stats, but not a player I have tested)

That's what "unique deps" means - excluding dependencies shared by all other apps on a Jaunty install, RB and its RB-only dependencies came out in third place. QL was smallest, Banshee second.

---

### Post by Skripka on 2009-04-17
> **directhex said:**
> That's what "unique deps" means - excluding dependencies shared by all other apps on a Jaunty install, RB and its RB-only dependencies came out in third place. QL was smallest, Banshee second.

OTOH, Banshee has the highest number of dependencies of any audio player I know of.

---

### Post by Mehall on 2009-04-17
woops, missed the "unique" bit =[

---

### Post by gnomeuser on 2009-04-17
> **directhex said:**
> I'm at the office, so don't have access to my music. hence 19-track collection (from archive.org)

For what it's worth. 1 video, 941 podcasts and 7648 songs as well as mirage loaded in banshee leads to 78megs of memory used. I am very pleased, and it remains responsive

---

### Post by castrojo on 2009-04-17
> **Skripka said:**
> OTOH, Banshee has the highest number of dependencies of any audio player I know of.

PURE AWESOMENESS comes at a (small) cost.

---

### Post by Skripka on 2009-04-17
> **gnomeuser said:**
> For what it's worth. 1 video, 941 podcasts and 7648 songs as well as mirage loaded in banshee leads to 78megs of memory used. I am very pleased, and it remains responsive

I duon't know how poorly Ubuntu builds Amarok2...but I have it running here on Arch KDEmod with 94MB, and a library of ~6000 songs....Amarok also can use my G15 keyboard media keys-which is something I have yet to find any other media player support.

---

### Post by Skripka on 2009-04-17
> **whiprush said:**
> PURE AWESOMENESS comes at a (small) cost.

Small?

depends:

gstreamer0.10-cdparanoia gstreamer0.10-faac gstreamer0.10-faad gstreamer0.10-gconf gstreamer0.10-gnomevfs gstreamer0.10-lame gstreamer0.10-mad gstreamer0.10-ogg gstreamer0.10-vorbis gtk-sharp-2>=2.8 hal ipod-sharp-svn mono-addins>=0.3.1 musicbrainz nautilus-cd-burner ndesk-dbus>=0.5 ndesk-dbus-glib>=0.3.1 sqlite3>=3.4 taglib-sharp>=2.0

versus

Amarok: kdebase-runtime>=4.1 libmp4v2 phonon qt>=4.4 qtscriptgenerator>=0.1 taglib>=1.5 xine-lib>=1.1.2

---

### Post by directhex on 2009-04-17
> **Skripka said:**
> OTOH, Banshee has the highest number of dependencies of any audio player I know of.

There are 2 types of Banshee dependency.

The package version I've used here is a snapshot for what'll appear in Karmic pretty much the day it opens, which eliminates one class (gstreamer plugin packages with enormous dep chains, i.e. gstreamer0.10-plugins-ugly and gstreamer0.10-ffmpeg)

The other class is teeny tiny library dependencies - there are a large number of them, but they're very small. Hence on a Jaunty system, it comes out better than the major competition

---

### Post by directhex on 2009-04-17
> **Skripka said:**
> I duon't know how poorly Ubuntu builds Amarok2...but I have it running here on Arch KDEmod with 94MB, and a library of ~6000 songs....Amarok also can use my G15 keyboard media keys-which is something I have yet to find any other media player support.

You're running KDE. So the kded and kdeinit processes are "shared". For Ubuntu users on GNOME, they're NOT shared, and therefore have been added to the memory use total.

Oh, and if you're on i386, then you use less RAM than my AMD64 numbers.

---

### Post by Skripka on 2009-04-17
> **directhex said:**
> You're running KDE. So the kded and kdeinit processes are "shared". For Ubuntu users on GNOME, they're NOT shared, and therefore have been added to the memory use total.

I still don't see how that gets Amarok up to 200+ MB...Even adding kded and kdeinit along with Amarok I barely go over 100MB.


And I'm on 64bit.

---

### Post by directhex on 2009-04-17
> **Skripka said:**
> I still don't see how that gets Amarok up to 200+ MB...Even adding kded and kdeinit along with Amarok I barely go over 100MB.


And I'm on 64bit.

you're reading the disk space column. 200 meg for enough of qt and kde to run amarok? sounds right to me

---

### Post by Tibuda on 2009-04-17
I think Banshee would be a good choice because it is also a Video player.


> **Skripka said:**
> I still don't see how that gets Amarok up to 200+ MB...Even adding kded and kdeinit along with Amarok I barely go over 100MB.


And I'm on 64bit.
I already got Qt installed for Skype, and installing Amarok+deps in my x86 Jaunty will need 176MB of disk space:
```
$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amarok-common exiv2 kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins khelpcenter4
  libclucene0ldbl libexiv2-5 libkcddb4 libloudmouth1-0 libmtp8 libphonon4
  libqt4-opengl libqt4-svg libqt4-test libqt4-webkit librasqal1 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x phonon phonon-backend-xine redland-utils soprano-daemon
  ttf-dejavu ttf-dejavu-extra
Suggested packages:
  libqt4-sql-sqlite libqt4-sql-psql kdebase lame gxine xine-ui libxine1-doc
  libxine-doc libxine1-ffmpeg phonon-backend-vlc phonon-backend-mplayer
The following NEW packages will be installed:
  amarok amarok-common exiv2 kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins khelpcenter4
  libclucene0ldbl libexiv2-5 libkcddb4 libloudmouth1-0 libmtp8 libphonon4
  libqt4-opengl libqt4-svg libqt4-test libqt4-webkit librasqal1 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x phonon phonon-backend-xine redland-utils soprano-daemon
  ttf-dejavu ttf-dejavu-extra
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.7MB of archives.
After this operation, 176MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by Skripka on 2009-04-17
> **directhex said:**
> you're reading the disk space column. 200 meg for enough of qt and kde to run amarok? sounds right to me

No I was reading RAM straight off top.  Haven't checked disk space needs....

---

### Post by Polygon on 2009-04-17
> **Skripka said:**
> Small?

depends:

gstreamer0.10-cdparanoia gstreamer0.10-faac gstreamer0.10-faad gstreamer0.10-gconf gstreamer0.10-gnomevfs gstreamer0.10-lame gstreamer0.10-mad gstreamer0.10-ogg gstreamer0.10-vorbis gtk-sharp-2>=2.8 hal ipod-sharp-svn mono-addins>=0.3.1 musicbrainz nautilus-cd-burner ndesk-dbus>=0.5 ndesk-dbus-glib>=0.3.1 sqlite3>=3.4 taglib-sharp>=2.0

versus

Amarok: kdebase-runtime>=4.1 libmp4v2 phonon qt>=4.4 qtscriptgenerator>=0.1 taglib>=1.5 xine-lib>=1.1.2

you are USING kde. all the dependencies for the program are already built in. its like comparing the memory usage of internet explorer vs firefox, internet explorer is a integrated portion of windows, so therefore, it needs less stuff because everything it needs is already loaded by windows.

and like the person above said, if you arn't using kde or kubuntu, then installing amarok is quite a hefty download, as it requires kde.

---

