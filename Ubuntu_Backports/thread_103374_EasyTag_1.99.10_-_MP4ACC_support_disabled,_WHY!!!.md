---
title: "EasyTag 1.99.10 - MP4/ACC support disabled, WHY???!!!"
date: 2005-12-14
forum: Ubuntu Backports
---

### Post by theOrange on 2005-12-14
I see the new EasyTag has been backported. So i download and install it from synaptic. I'm all excited b/c i have been waiting for a tool to tag my .m4a files.
So i start it up and check the "About" and it reports...

EasyTAG 1.99.10 => check
compiled: Dec 13 2005 => check
using: GTK+ 2.8.6 and id3lib 3.83 => check
MP4/AAC file support disabled => WHAT THE FARK???

Why, why, why, why was this package compiled with the much anticipated and much needed new feature disabled???

---

### Post by jdong on 2005-12-14
I believe there are licensing issues?

Check with the developers on #ubuntu-motu/irc.freenode.org for more info.

---

### Post by noximyre on 2005-12-30
How to get Easytag with MP4/AAC support

This didn't work for me on Breezy AMD64, but it might work in a 32-bit environment, although I couldn't get it to work in my chroot. Hopefully someone will find this useful.

Okay, so we're going to compile Easytag from source. But Easytag requires mpeg4ip, which requires x264, which requires yasm. To compile anything, you need:

```
sudo apt-get install automake build-essential fakeroot libtool wget
```

Usually, when compiling, things go wrong during the ./configure and make steps. ./configure will usually terminate with a message explaining what you have to do before you can compile. make will usually terminate with pretty opaque error messages. If you get any errors, post them here!

Now, starting from the top:

1. Get yasm ([http://www.tortall.net/projects/yasm/)](http://www.tortall.net/projects/yasm/)). Check for newer versions of yasm at [http://www.tortall.net/projects/yasm/wiki/Download](http://www.tortall.net/projects/yasm/wiki/Download)

To get the latest yasm version as of 30 Dec 2005:

```

wget http://www.tortall.net/projects/yasm/releases/yasm-0.4.0.tar.gz
tar -xvvf yasm-0.4.0.tar.gz
cd yasm-0.4.0

```

Compile it:

```

./configure
make
sudo make install

```

2. Get x264 ([http://developers.videolan.org/x264.html)](http://developers.videolan.org/x264.html)). Check for newer versions of x264 at [ftp://ftp.videolan.org/pub/videolan/x264/snapshots/](ftp://ftp.videolan.org/pub/videolan/x264/snapshots/)

If you have subversion installed (sudo apt-get install subversion), this is very easy:

```

svn co svn://svn.videolan.org/x264/trunk x264
cd x264

```

Otherwise, to get the latest yasm version as of 30 Dec 2005:

```

wget ftp://ftp.videolan.org/pub/videolan/x264/snapshots/x264-snapshot-20051230-2245.tar.bz2
tar -xjvf x264-snapshot-20051230-2245.tar.bz2
cd x264-snapshot-20051230-2245

```

Compile it:

```

./configure
make
sudo make install

```

3. Get mpeg4ip ([http://www.mpeg4ip.net/)](http://www.mpeg4ip.net/)). Check for newer versions of mpeg4ip at [http://mpeg4ip.sourceforge.net/downloads/index.php](http://mpeg4ip.sourceforge.net/downloads/index.php)

To get the latest yasm version as of 30 Dec 2005:

```

wget http://prdownloads.sourceforge.net/mpeg4ip/mpeg4ip-1.4.1.tar.gz
tar -xvvf mpeg4ip-1.4.1.tar.gz
cd mpeg4ip-1.4.1

```

Before you can compile it and Easytag, you need a lot of development headers. Get those now:

```

sudo apt-get install libavcodec-dev libfaac-dev libflac-dev libid3-3.8.3-dev
liblame-dev libmp4v2-dev libogg-dev libsdl1.2-dev libvorbis-dev libxvidcore4-dev

```

You probably don't want all of mpeg4ip, especially mp4live. To learn more about mp4live and to decide whether you want it or not, visit [http://mpeg4ip.sourceforge.net/documentation/index.php?readme=mp4live](http://mpeg4ip.sourceforge.net/documentation/index.php?readme=mp4live). To get rid of it, just add the following parameter to the first line below:

```

./bootstrap --disable-mp4live

```

Compile it:

```

./bootstrap
make
sudo make install

```

I get the following error after ./bootstrap:

```

/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/libavcodec.a(utils.o): relocation R_X86_64_32 against `first_avcodec' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[5]: *** [ffmpeg_audio_plugin.la] Error 1
make[5]: Leaving directory `/home/james/mpeg4ip-1.4.1/player/plugin/audio/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/james/mpeg4ip-1.4.1/player/plugin/audio'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/james/mpeg4ip-1.4.1/player/plugin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/james/mpeg4ip-1.4.1/player'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/mpeg4ip-1.4.1'
make: *** [all] Error 2

```

4. Get Easytag ([http://easytag.sourceforge.net)](http://easytag.sourceforge.net)). Check for newer versions of Easytag at [http://sourceforge.net/project/showfiles.php?group_id=5216](http://sourceforge.net/project/showfiles.php?group_id=5216)

Download the source .bz2. As of 30 Dec 2005, that's easytag-1.99.11.tar.bz2

```

(Open a terminal)
(Browse to the directory to which you saved the source .bz2)
tar -xjvf easytag-1.99.11.tar.bz2
cd easytag-1.99.11

```

Compile it:

```

./configure
make
sudo make install

```

Done! Now you can remove all the downloaded files and the extracted directories.

---

### Post by Bazon on 2006-04-22
I tried to compile Easytag with aac/m4a/mp4 Support by myself, but I didn't suceed. :(
(Everything fine until *make* in easytag, there I get an error about mp4.h [although in *./configure* mp4 support was displayed!])

So has anyone made a .deb or could make one please? :)

---

### Post by mazirian on 2006-07-31
There really should be an easytag-aac package in the plf repository, just as there is in the debian-multimedia repository.  Has anyone succeeded in building this and its dependancies recently? A dapper package would be most useful for many people, I think.  In fact, a review of the forums seems to show that most people don't even realize easytag is capable of editing mp4 tags!

---

### Post by mlind on 2006-08-01
> **mazirian said:**
> There really should be an easytag-aac package in the plf repository, just as there is in the debian-multimedia repository.  Has anyone succeeded in building this and its dependancies recently? A dapper package would be most useful for many people, I think.  In fact, a review of the forums seems to show that most people don't even realize easytag is capable of editing mp4 tags!

You need to build easy-tag with newer libmp4 to get package build with mp4 support I guess.
Try if this works for you [http://www.freefilehoster.com/uploads/1154471563easytag-aac_1.99.12-dapper.tar.gz](http://www.freefilehoster.com/uploads/1154471563easytag-aac_1.99.12-dapper.tar.gz)

---

### Post by mazirian on 2006-08-01
Thanks, those worked well.  I was trying trying to rebuild easytag against dapper's libmp4 package.

Thanks very much.  Hopefully libmp4 will be backported for dapper so an easytag-aac can get into universe or some other repo.

Thanks again.

---

### Post by mlind on 2006-08-01
> **mazirian said:**
> Thanks, those worked well.  I was trying trying to rebuild easytag against dapper's libmp4 package.

Thanks very much.  Hopefully libmp4 will be backported for dapper so an easytag-aac can get into universe or some other repo.

Thanks again.

If you want to get easytag-aac to build, get mpeg4ip package from Marillat repository and build that first. 
Then use created libmpeg4ip-dev as build dependency for easytag-aac.

---

### Post by rrdharan on 2006-10-08
Since the above link no longer works, here's one that does:

[http://www.electricrelaxation.com/2006/10/08/easytag-with-aac-support-for-dapper](http://www.electricrelaxation.com/2006/10/08/easytag-with-aac-support-for-dapper)

I rebuilt easytag for Dapper with --enable-mp4, statically linking with the newest mp4v2 library from the MPEG4IP project, which I also built from source. 

The resulting easytag can edit .m4a tag information.

---

### Post by mazirian on 2006-11-11
@mlind: Might you have a new deb you could share for edgy?

---

### Post by mazirian on 2006-11-12
n/m, building easytag was aac support was easy enough.  There was a slight issue with a dependency conflict when satisfying the build dependencies of libmpeg4ip having to do with libglu1-mesa and libglu1-mesa-dev, but other than that, it was a snap.

For those wishing to repeat the process, grab the source package for libmpeg4ip from the marillat repositories ([www.debian-multimedia.org](www.debian-multimedia.org)) and build it with debuild.  Install all the resulting debs.  Then grab the source package for easytag from edgy, and build it with debuild and install it.  The configure script will automatically detect that you have aac/mpeg4 support and build easytag accordingly--you don't have to edit a rules file or anything.  There will probably be quite a few missing dependencies for each build, so be sure to install them all when debuild prompts you.

---

### Post by samwise on 2007-01-06
mazirian, rrdharan actually linked to a binary hosted on his blog.  So it's quite simple to install the non-m4a version of easyTAG from the ubuntu repositories and then just drop the binary over the top in /usr/bin.

I've done this in Kubuntu Edgy Eft (6.10) on my x86 puter and it seems to work a treat.

Cheers, rrdharan - totally saves the hassle of compiling everything from scratch.

I'd also agree the M4A/AAC-enabled version should be a package in the PLF repositories or equivalent.

---

### Post by simonn on 2007-02-02
Rather than rebuilding mpeg4ip, which requires recompiling a whole load of other stuff, changing the source of easytag to work with the existing version of mpeg4ip seems more sensible.

Uninstall the easytag package from the repositories and then install the latest (1.99.13 at time of writing) from source using the patch attached. Note that the patch is based on the patch here [http://permalink.gmane.org/gmane.comp.audio.easytag.general/172](http://permalink.gmane.org/gmane.comp.audio.easytag.general/172) - I only made one change to it so that it displayed the MPEG4 type correctly.

I have a lot of dev packages installed anyway so I am not sure 100% which ones you need to install, however, the following seem likely:

libgtk2.0-dev libvorbis-dev libflac-dev libid3-3.8.3-dev libmp4v2-dev

Obviously you need gcc installed as well.

```

$ tar jxf easytag-1.99.13.tar.bz2
$ cd easytag-1.99.13
$ bzip2 -c -d ../ubuntu-easytag.patch.bz2 | patch -p1
$ ./configure
$ make
$ sudo make install

```

The patch is a bit of a hack, but i have tested it against all types of m4a created using faac and iTunes (OSX), and it seems to work fine, of course the responsibility is all yours.

(To the moderators: Why the hell is .patch an invalid file extension on a Linux message board??????)

---

### Post by samwise on 2007-02-05
I gave up with EasyTag in the end.  I found it more hassle than it's worth, getting it up and running.

For example, it's mp3 tagging support is based on id3lib which hasn't been updated for over three years, so it doesn't even support ID3 v2.4 tags in mp3s.

I found it far easier to just run Mp3tag, which seems to be more mature and also has a GUI more to my liking.

Thanks muchly WINE guys ...

Sam.

---

### Post by F-3582 on 2007-03-18
Thanks for that patch. It even works on EasyTag 2.0!

By the way: The easiest way to make sure that all build dependencies are met is ```
# apt-get build-dep easytag
``` ;)

EDIT: Okay, it doesn't work. It compiles well, but the resulting app causes mass-corruption in m4a files.

---

### Post by cyb3rj on 2007-03-26
Cool.  Thanks for the patch!

Now I just need Amarok to recognize MP4/AAC tags...

Another battle for another day.

---

### Post by cyb3rj on 2007-04-13
> **cyb3rj said:**
> Cool.  Thanks for the patch!

Now I just need Amarok to recognize MP4/AAC tags...

Another battle for another day.

i'll answer myself with 'feisty fawn' takes care of this with packages from medibuntu.

happy happy joy joy

---

### Post by zorkerz on 2007-04-22
I still have not managed to get easytag to work with aac support. Currently when i install the default easytag from the repos it no longer recognizes any music files. I don't know where to go from here.

---

### Post by F-3582 on 2007-04-22
Okay, I have found a pretty easy way to solve all those problems:

0. In case you didn't do this already: Make sure that Easytag is NOT installed and enable the universe, multiverse and restricted repositories.
1. Visit [this place]("http://ftp.sh.cvut.cz/MIRRORS/debian-multimedia/pool/main/libm/libmpeg4ip/") and install the packages libmp4v2-0, libmp4v2-dev, libmpeg4ip-0 and libmpeg4ip-dev.
2. Either get the [precompiled (and outdated) Debian build]("http://ftp.sk.debian.org/debian-multimedia/pool/main/e/easytag-aac/") or compile the latest version yourself. In order to do this, visit the [Easytag Home]("http://easytag.sourceforge.net/"), grab the latest source tarball, run "sudo apt-get build-dep easytag" and "sudo apt-get install libwavpack-dev" and "make" away! Note that CheckInstall doesn't seem to work here.

I hope that this helps. And I hope that someone will update the MPEG4IP packages in the Ubuntu repositories, someday.

Edit: By the way - it looks like these packages also enable AAC tagging support in Amarok ;)

---

### Post by zorkerz on 2007-04-22
If im correct F-3582 your first link only provides 3 files not 4 (libmp4v2-0 libmpeg4ip-0 mpeg4ip-utils).

I installed these three and then used your link the the recompiled deb. However easytag still refuses to recognize any music files at all. I have been messing around with this for a long time and probably messed up some setting somewhere. I was over a year ago that i started trying to change m4a tags and i have never found a satisfactory solution.

So when i uninstall easytag how do i make sure all of its files are deleted so that i can get at least the basic functionality that it is supposed to come with in ubuntu and debian (ie without aac support)? I have already tried deleting the easytag file in my home directory.

Thanks

---

### Post by F-3582 on 2007-04-23
Sorry. I'll change my post.

The packages you need are: libmp4v2-0, libmp4v2-dev, libmpeg4ip-0 and libmpeg4ip-dev.

As I said, compiling the latest version might be the most satisfactory choice. You should also enable the universe multiverse and restricted repositories. Source packages are important, too, I think.

---

### Post by zorkerz on 2007-04-23
F-3582 oops you are right all the files are there i just ignored the devs.

Well this is a pain. I have installed all the packages specified above by F-3582 including the outdated easytag. I am not at the point were i can check aac support because easytag does not find any music files or any files at all for that matters. I can brows through all my directories where i know music is located but they all appear empty in easytag.

I get this problem no matter what version of easytag i install. I would like to eventually build the newer easytag with aac support to get around it being disabled in the repos easytag but until i cant test it properly there is no point. I guess i said this all once before.

oh bother

---

### Post by nrwilk on 2007-08-16
> **F-3582 said:**
> Okay, I have found a pretty easy way to solve all those problems:

Edit: By the way - it looks like these packages also enable AAC tagging support in Amarok ;)

Thank you so much! this worked for me!  :)

I really wanted to be able to use Amarok to do this tagging, but I don't seem to have the ability to edit my m4a tags with Amarok even after installing these packages.  Do you have any info/tips for this?  I did try restarting Amarok...

Thanks again!

---

### Post by BioTeX on 2007-08-16
Good work finding an easy workaround.

I can't write tags to m4a files in amarok either though, and that's what I was hoping for.  Luckily the command line tool mp4tags, which comes with mpeg4ip, works fine.  Try   'mp4tags -h' after installing those debian packages to see the available options.

---

### Post by logos34 on 2007-08-16
> **BioTeX said:**
> Good work finding an easy workaround.

I can't write tags to m4a files in amarok either though, and that's what I was hoping for.  Luckily the command line tool mp4tags, which comes with mpeg4ip, works fine.  Try   'mp4tags -h' after installing those debian packages to see the available options.

will it handle .m4a apple lossless (.alac) files?

---

### Post by nrwilk on 2007-08-17
OK, now I'm having a new problem which I think may be unrelated.

Many of my m4a files show up in amarok with all the tags working except the genre tag.  These files DO have genre tags set, and easytag reads and writes their genre tag correctly, but Amarok doesn't recognize it.  So, they get put into an "unknown" genre category by Amarok.  This is very annoying.

Does anyone else have this problem, or know how I can fix it?

Or, should I start a new thread?

---

### Post by F-3582 on 2007-09-11
You should probably file a bug for Amarok, if this happens on ALL m4a files. This happens to me, as well, by the way and trying to edit that tag results in an error.

EDIT: Seems like Amarok still cannot edit the tags themselves and just decides to modify the fields in its database.

---

### Post by JOWIROMA on 2007-09-13
Hi guys!

I do not know if this helps with your problem but I tested the neroAacenc to  encode my Moonspell cd but after the encoding the problem would be the tagging of the files so I downloaded a program called Quod Libet from sinaptyc and this player also installs a program called EX FALSO and this program edits the tags of the m4a files.
You can download EX FALSO alone but it does not have the plug ins to edit the tags so thats why you have to install Quod Libet too.

I edited the tags of some m4a files that Amarok did not recognice, neither the Ipod...

Anyways now Amarok, my Ipod and now my iTunes at work can read those tags..... and the only thing that I did not try to add to the tags was the artwork... will try that tonight...

---

