---
title: "HOWTO: Gspot Equivalent on Linux"
date: 2007-05-24
forum: Tutorials
---

### Post by userundefine on 2007-05-24
Finally I get to contribute a HOWTO. :)  I've seen this requested often, mainly because I was looking for an equivalent myself.  If you're familiar with Gspot, it's a Windows-only program that spits out information on an AVI you feed it: codec, bitrate, audio quality, resolution, etc.  Now, with some clever grep work of mplayer's output, you can do a decent job of getting these details, but how about a tool written specifically for the job that does it BETTER than Gspot?  That's what I finally found with [MediaInfo]("http://mediainfo.sourceforge.net/").

It's a GPL windows/linux program.  Windows version has a GUI, and on Linux we bypass that distraction and just get our goodies with a CLI version.  It supports a ton of formats.  It's so good, when you put an AVI through it that's been downloaded from Google Video, it says "Google Video / Hack of AVI".  Your information will look like this once you use the prog:

```

General #0
Complete name        : /home/userundefine/video001.avi
Format               : AVI
Format/Info          : Audio Video Interleave
Format/Family        : RIFF
File size            : 137 MiB
PlayTime             : 29mn 14s
Bit rate             : 645 Kbps

Video #0
Codec                : DivX 5
Codec/Family         : MPEG-4
Codec settings/Packe : Yes
Codec settings/BVOP  : Yes
Codec settings/QPel  : No
Codec settings/GMC   : 0
Codec settings/Matri : Default
PlayTime             : 29mn 14s
Bit rate             : 408 Kbps
Width                : 512 pixels
Height               : 384 pixels
Aspect ratio         : 4/3
Frame rate           : 25.000 fps
Resolution           : 8 bits
Chroma               : 4:2:0
Interlacement        : Progressive
Bits/(Pixel*Frame)   : 0.083
Writing library      : DivX503b2207p

Audio #0
Codec                : MPEG-1 Audio layer 2
Bit rate             : 224 Kbps
Bit rate mode        : CBR
Channel(s)           : 2 channels
Sampling rate        : 44 KHz
Resolution           : 16 bits
Title                : Audio Stream
Writing library      : Xing (new)
Coherency/PlayTime   : 2398

```

This program will compile on x64 and is officially supported (see [post 6]("http://ubuntuforums.org/showpost.php?p=2740965&postcount=6")), but we won't be getting into that here.

Now, let's do it.  The simplest way to do it is to use the pre-compiled binary for i386 because MediaInfo has a lot of dependencies.  However, if you really do want to compile from source, there is a nice script to grab all the necessary dependencies for you and compile them.  We won't cover that here, though.

Step 1: download
```
wget http://superb-west.dl.sourceforge.net/sourceforge/mediainfo/MediaInfo_0.7.4.7_CLI_Linux_i386.tar.bz2
```

Step 2: extract
```
tar xjvf MediaInfo_0.7.4.7_CLI_Linux_i386.tar.bz2
```

Step 3: put MediaInfo in your PATH
```
sudo mv MediaInfo_CLI_GNU/MediaInfo /usr/local/bin/
```

Step 4: usage
```
MediaInfo *file*
```

This is the first version released for Linux.  There aren't many options for the CLI because, according to the author, there's less interest.  So generate some interest! :)  It's a great little program.  Some issues noted for this first Linux release in the readme that aren't working properly:

[list]
[*] Filename with non-american letters (other than A-Z, a-z)
[*] Matroska, FLAC, APE, MonkeyAudio and old Sound format parsers are disabled*
[/list]

* seems to be a nonissue now according to the programmer, see  [post 6]("http://ubuntuforums.org/showpost.php?p=2740965&postcount=6").

Hope you enjoyed this short howto.

---

### Post by hornett on 2007-05-24
Excellent! I've been looking for something like this.

Working nicely here.

---

### Post by derekguy on 2007-05-25
Brilliant I was also looking for such a program. Works well for me on 2.6.20-15 on i686. Gives a lot more info than 'file'

Hope to help in generating interest ;)

---

### Post by capitalistpiglet on 2007-05-27
Thanks this is just what i was looking for

---

### Post by killkoy on 2007-05-27
Works for me on x64using the i386 binary

---

### Post by Zenitram-MediaInfo on 2007-05-29
I am the developper of MediaInfo, some comments :
- Linux CLI may have more options if Linux users are a lot (=referers on MediaInfo website are from linux websites), currently my main users are on Windows. But I try to debug it before implementing more options.
- I am working on a cross-platform GUI, released on Linux soon. But all of this requests time, and I am alone :)
- x64 version was not released for version 0.7.4.7, but you can compiled from sources without problems. I officially support it. next versions will have a x64 binary.
- Matroska, FLAC, APE, MonkeyAudio parsers are now enabled
- MediaInfo has now less dependancies : "only" libwx, libmatroska and libebml. The installation script try to download and compile them.

---

### Post by mozetti on 2007-05-29
To the **OP** and possibly the developer if Linux gets an installation script:

If you don't want to move the program into your path, you can just create a symlink in your path to the file. Assuming you extract it in your home directory to /home/<user>/MediaInfo_CLI_GNU/, just type:

```
sudo ln -s /home/<user>/MediaInfo_CLI_GNU/MediaInfo /usr/bin/MediaInfo
```

****Notes****
-The **ln** command will create the symlink file (in the example /usr/bin/MediaInfo), so don't create it yourself before running the **ln** command because it will fail if the file already exists (or add the -f switch to force an overwrite).

-The name you give the symlink file in your path (in the example /usr/bin/MediaInfo) can be anything you desire. For example, You can use "gspot" or "mediainfo" (note the lowercase letters here) to launch the file instead of "**M**edia**I**nfo" (note the bolded uppercase letters). The command would be (using the "gspot" example)

```
sudo ln -s /home/<user>/MediaInfo_CLI_GNU/MediaInfo /usr/bin/gspot
```

**EDIT** And thanks for this! I've been looking for a replacement for Gspot since I moved to Linux.

---

### Post by userundefine on 2007-05-30
Good points, mozetti.  Even if a user wants to symlink, it should still be put in /usr/local/bin, though, just to distinguish from something the package manager installs.

Zenitram, thanks for clarifying some issues and thanks for a great program!  Personally I'm not sure what other options are needed because what it currently displays on a file is exactly what I've been looking for, which isn't to say that you couldn't blow my mind with something I hadn't thought of. :)  I'm sure you'll make other users happy with a GUI, though.

---

### Post by Miguellint on 2007-06-14
Works superbly with Feisty. Many thanks for that.

Regards
Miguel

---

### Post by Virtual_Ron on 2007-12-03
> **killkoy said:**
> Works for me on x64using the i386 binary

Thanks for pointing that out....   I couldn't compile the x64 version to save my life.  
compile errors up the wazoo.

Thanks.   AWESOME app.

---

### Post by sciurus on 2007-12-03
Instead of compiling this program, you can use the program tcprobe, which is a part of the transcode package.

---

### Post by bliffle on 2007-12-07
Worked great for me on Gutsy!

---

### Post by sensimilla on 2007-12-29
Anyone know how to run and show MediaInfo from the right-click open with menu ?

I tried:

gnome-terminal -x MediaInfo

but it closes the terminal as soon as MediaInfo has finished.

---

### Post by 3ntity on 2008-01-04
Thx :)
Your instructions work on Gutsy x64 using the latest MediaInfo_0.7.5.6_CLI_Linux_x64.tar.bz2 from SourceForge. Great success!

---

### Post by timseal on 2008-02-28
Just noticed there's a .deb package for this now, on the sourceforge site.

---

### Post by Jose Catre-Vandis on 2008-02-28
> **timseal said:**
> Just noticed there's a .deb package for this now, on the sourceforge site.

here:```
http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612
```

In using the .deb file, I find the terminal command is:```
mediainfo [file]
```

---

### Post by Zenitram-MediaInfo on 2008-02-29
I am the developper of MediaInfo, some comments :
- The original post is old. Yes, the command is now "mediainfo", without uppercase.
- There is a .deb for i386
- i386 and x64 binary are available on SourceForge (.tar.bz2).
- A beta version of the GUI is avalable too (i386 and x64). It is not integrated yet in Gnome, but a "gnome-terminal -x mediainfo-gui" can be good. Any help is welcome for Gnome/KDE integration.

---

### Post by Jose Catre-Vandis on 2008-03-01
> **sensimilla said:**
> Anyone know how to run and show MediaInfo from the right-click open with menu ?

I tried:

gnome-terminal -x MediaInfo

but it closes the terminal as soon as MediaInfo has finished.

Try this:

Create a new file, and copy and enter this text:
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
gnome-terminal -x sh -c "mediainfo $*; sh"
```

Save the file as [COLOR="Blue"]mediainfo[/COLOR] (or whatever) and move it to your nautilus scripts folder, usually: [COLOR="Sienna"]/home/username/.gnome2/nautilus-scripts[/COLOR]

Make the file executable by right clicking on the file in nautilus, select properties then permissions and ticking the executable box.

restart nautilus so the changes can take effect, and you should see "mediainfo" listed as a script. 

Try it. You should get a new terminal window with the file info displayed, followed by a $. Click the x in the top right to close the terminal when finished.

I also tried doing this with nautilus actions, but it didn't work. Oh, and note that my version of mediainfo requires lowercase, your might be different.

There is probably a better way, but I am a NS newbie and there ain't much info out there about how to do this :)

---

### Post by dotdot on 2008-03-09
brilliant - magic - clap clap clap.

works a treat.

oh the wows of organising digital media.

exif for images
...mediainfo for avi's.

brilliant.

..

---

### Post by ShirishAg75 on 2008-03-16
Nice just one comment, perhaps it can be made so that it installs in /usr/local/bin rather than in /usr/bin 

doing a dpkg -i mediainfo.cli_0.7.6.1-1_i386.deb  puts it right in /usr/bin which perhaps is not the right place to put them? 

Comments, suggestions anyone?

---

### Post by timseal on 2008-03-17
/usr/local is for installs done by the user, so when building from source it should default to there.   The /usr prefix is for the packaging system, so dpkg is correct to put binaries in /usr/bin.

---

### Post by jjgomera on 2008-03-20
another alternative to gspot, [avinaptic]("http://fsinapsi.altervista.org/")

---

### Post by jojo4u on 2008-05-20
> **timseal said:**
> The /usr prefix is for the packaging system, so dpkg is correct to put binaries in /usr/bin.

The /usr hierarchy is programs which are non-essential and can be mounted read-only from external. See [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) and Notes and references of this article.

---

### Post by zuzarte on 2008-07-20
On the folder
~/.kde/share/apps/konqueror/servicemenus

Create the file mediainfo.desktop

With this..

[Desktop Entry]
Comment=Media File Informations
Encoding=UTF-8
GenericName=
GenericName[en_US]=
Name=mediainfo.desktop
Name[en_US]=mediainfo.desktop
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=
ServiceTypes=all/allfiles
Actions=MediaFileInformation

[Desktop Action MediaFileInformation]
Name=Media File Information
Icon=kaffeine
Exec=konsole -noclose -e mediainfo %U

To have an action menu "Media File Information" on right mouse click.

[]'s

---

### Post by z0mbie on 2008-07-22
They have an easy to install [debian package]("http://downloads.sourceforge.net/mediainfo/mediainfo.cli_0.7.7.4-1_i386.deb?modtime=1215898789&big_mirror=0") that works great with Ubuntu Hardy.

---

### Post by mb_webguy on 2008-08-25
> **Jose Catre-Vandis said:**
> Try this:

Create a new file, and copy and enter this text:
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
gnome-terminal -x sh -c "mediainfo $*; sh"
```

Save the file as [COLOR="Blue"]mediainfo[/COLOR] (or whatever) and move it to your nautilus scripts folder, usually: [COLOR="Sienna"]/home/username/.gnome2/nautilus-scripts[/COLOR]

Make the file executable by right clicking on the file in nautilus, select properties then permissions and ticking the executable box.

restart nautilus so the changes can take effect, and you should see "mediainfo" listed as a script. 

Try it. You should get a new terminal window with the file info displayed, followed by a $. Click the x in the top right to close the terminal when finished.

I also tried doing this with nautilus actions, but it didn't work. Oh, and note that my version of mediainfo requires lowercase, your might be different.

There is probably a better way, but I am a NS newbie and there ain't much info out there about how to do this :)

To use this with Nautilus actions, enter the following as the path:```
/usr/bin/gnome-terminal
``` And enter the following as the parameters:```
-x sh -c "mediainfo %d/%f;sh"
```

---

### Post by ubi-laptop on 2008-10-11
using grep and ffmeg I use this command saved as script "des" in my path, so I get less information but enough for most occasion:

ffmpeg -i $1 2>&1 | grep Duration 
ffmpeg -i $1 2>&1 | grep Stream

or

mplayer $1 -identify -frames 0 -vc null -vo null -ao null -nosound 2>&1 | grep ID_VIDEO_FORMAT
mplayer $1 -identify -frames 0 -vc null -vo null -ao null -nosound 2>&1 | grep ID_VIDEO_ASPECT
and on.
greetings

---

### Post by roddersg on 2010-06-02
I can confirm that mediainfo v.0.7.33 works on Ubuntu 10.04 amd64 without problems.

Besides the 4 files in the repository, you will also need to install
libwx and libgtk2.0 libraries as the dependencies

Thanks

---

### Post by babygenius55 on 2010-07-10
Wow, this isn't even close to what I was looking for.  I use gspot to figure out what is wrong with a certain file I downloaded, or more properly to see if what it is that's not working right after a download is in reality-porn that some poor sap has to hide from his wife or parents.

EX - Lenticular imaging seminar.rar will not open in a decompressor.
       Right click>send to gspot.....
       ....File is type .mpg, or .avi, or whatever, and it's someone getting a **** poor
       hummer in front of a dirty

I said all of that to ask this; Does anyone know of a program that can actually tell you what a file is when it won't run?

---

### Post by quiritius on 2010-07-11
There is an official [COLOR=Blue]_[PPA]("https://launchpad.net/%7Eshiki/+archive/mediainfo")_[/COLOR], BTW. See on the [COLOR=Blue]_[website]("http://mediainfo.sourceforge.net/en/Download/Ubuntu")_[/COLOR]. Just add-apt-repository it.

---

### Post by ozzyprv on 2010-07-14
> **babygenius55 said:**
>  Does anyone know of a program that can actually tell you what a file is when it won't run?

I haven't used it myself yet, but I think that what quiritius' post tried to say is that the package "mediainfo" can provide that information.

---

### Post by TylerD75 on 2010-10-15
THANK YOU!

I've been looking for something like this!
It compiles & runs perfectly on Gentoo x64 (0.7.34), and is also (although masked) in portage.
Probably not the right forum to mention Gentoo, but this was the first thread (and most useful) to have any info on this!

If any gentoo users want to emerge it, just unmask the following:
```
#/etc/portage/package.keywords
#----------- MediaInfo -----------------
>=media-video/mediainfo-0.7.34 ~amd64
>=media-libs/libzen-0.4.15 ~amd64
>=media-libs/libmediainfo-0.7.34 ~amd64
#---------------------------------------
```

---

### Post by JBAlaska on 2010-11-17
I'll wake this thread up by saying the Ubuntu Lucid x86_64 version of Mediainfo works fine on Maverick, Just be sure to install the dependencies and use Gdebi to install the deb file, as there are 2 other dependencies that are not listed on the website that gdebi downloads and installs. 


That being said, mediainfo does not report things like GMC or Q-Pel that are quite important if you need to know why a avi file will not play on a DivX player.

However Avidemux DOES report these advanced encoding options and also offers to unpack the bitstream (required on some older DivX players) when you load the avi file.

To get info with Avidemux, load your video file and go to File, Properties.

---

### Post by äxl on 2012-02-25
Big Thanks!

I prefer the CLI version from [mediainfo.sourceforge.net/Download]("http://mediainfo.sourceforge.net/Download").

---

