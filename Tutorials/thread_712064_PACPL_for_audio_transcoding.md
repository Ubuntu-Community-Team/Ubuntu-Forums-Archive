---
title: "PACPL for audio transcoding"
date: 2008-03-01
forum: Tutorials
---

### Post by cozmicharlie on 2008-03-01
Installing PACPL in Ubuntu 

PACPL is a Perl based script for converting audio files in Linux ([http://pacpl.sourceforge.net//](http://pacpl.sourceforge.net//)). It is extremely powerful and is capable of encoding/decoding a large array of formats (aac, ac3, avi, divx, flac, m4a, mp3, mp4, mpeg, ogg, raw, shn, vcd, vob, wav, wma, wmv and many more).  Installing the program itself is fairly easy but it does require a number of dependencies &#8211; this is what causes most people problems. This tutorial will show how to install PACPL, the dependencies, codecs, how to use PACPL from the command line and how to integrate it into Amarok and Konqueror.

To start, make sure that you have all the repositories and codecs installed.

**1.0  Install the Medibuntu repository**
Open a terminal (Alt + f2) and type or copy/paste the following command for your Ubuntu-release
(if you use a older release please go to [Medibuntu Repository Howto]("https://help.ubuntu.com/community/Medibuntu"))

Ubuntu 8.04 "**Hardy** Heron":
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 8.10 "**Intrepid** Ibex":
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 9.04 "**Jaunty** Jackalope":
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Then, add the **GPG** Key:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

**1.2  Install Ubuntu Restricted Extras and build-essential**
Note that there is also **xubuntu-restricted-extras** (for Xubuntu) and **kubuntu-restricted-extras** (for Kubuntu.)
```
sudo apt-get install ubuntu-restricted-extras build-essential
```

** Note: PACPL does have a very simple GUI that can be used in gnome or kde.  It requires you have Kommander installed so if you want to use the simple GUI then install Kommander prior to installing PACPL.  Kommander is a kde package, so if you are in Gnome installing Kommander will also install a full kde desktop.  If you don't want that, then do not install Kommander and either use PACPL with Amarok or from the command line.

**1.3  Now you are ready to install PACPL**
Download PACPL sources
```
wget http://dfn.dl.sourceforge.net/sourceforge/pacpl/pacpl-4.0.4.tar.bz2

```
Unpack it:
```
tar xvf pacpl-4.0.4.tar.bz2
```
Change the working directory to the source directory:
```
cd pacpl-4.0.4/extra
```
Next run the script that will install all the dependencies.
```
./mod-install-kubuntu.sh
```
Once that is finished change directories again to /pacpl-4.0.4:
```
cd ..
```
Compiling it: This generates the necessary files, and checks your system:
```
./configure
```
Then compile:
```
make
```
Install it:
```
sudo make install
```
**That's it.**

Now you have a few options, 1. start using pacpl from the command line, or 2. if you are using kde, you can run pacpl via a GUI or integrated into Amarok, Konqueror, Dolphin or d3lphin.  For all other desktop systems (gnome, xfce etc) the only option is to run pacpl from the command line.

**1.4 Using the Kommander GUI:**
To use the simple GUI that comes in the pacpl package, you first install Kommander from Synaptic (see note above). 
Launch the gui using this command in a terminal.
```
pacpl-gui-kmdr
```

**1.5 To integrate pacpl into Amarok:**
Create the directory &#65279;/usr/share/apps/amarok/scripts/pacx/
```
mkdir /usr/share/apps/amarok/scripts/pacx/
```
Move the script pacx from /pacpl4.0.4/plugins/amarok/pacx to /usr/share/apps/amarok/scripts/pacx/
```
cp pacpl4.0.4/plugins/amarok/pacx /usr/share/apps/amarok/scripts/pacx/
```
Now when you have a file loaded into Amarok simply right click and the option to convert with pacpl should be available.

**1.6 To integrate into Konqueror/d3lphin/dolphin:**
pacpl.desktop (~/pacpl-4.0.4/plugins/konqueror) can be placed in either /usr/share/apps/konqueror/servicemenus or in your home directory (~/.kde/share/apps/konqueror/servicemenus).
```
cp pacpl-4.0.4/plugins/konqueror/pacpl.desktop /usr/share/apps/[COLOR="Blue"]konqueror[/COLOR]/servicemenus
```
```
cp pacpl-4.0.4/plugins/konqueror/pacpl.desktop .kde/share/apps/[COLOR="Blue"]konqueror[/COLOR]/servicemenus
```
pacpl.desktop can be used for d3lphin or dolphin the same as konqueror by using the same directory as above. Just replace the blue marked konqueror with d3lphin/dolphin...the rest is the same.

**2.0 How to use pacpl in command line:**
This command will display the list of commands available and instructions for using PACPL.
```

pacpl -l
```
Display the list of available codecs for encoder and decoder
```
pacpl -f 
```
Some explanations, as usual
```
man pacpl
```
In general, the commands are written in the following structure
```
pacpl --to <format> <options> directories/files
```

**Some examples**
Replace "*[COLOR="Blue"]musig[/COLOR]*" with your name and change the location.

**2.1  Simple convert**
Open a terminal and go to the directory containing the files you want to convert. In the following example a  folder named "flacMusic" in the home directory of the user"*[COLOR="Blue"]musig[/COLOR]*" .This will put the converted files into the same folder. If there are other files in the folder than the supported formats you have to specify the "from" file type. with [COLOR="Red"]*.mp3[/COLOR], for example, or use the --only option (see 2.5)
```
cd /home/*[COLOR="Blue"]musig[/COLOR]*/flacMusic
pacpl -t mp3 *.flac
```
Instead of using a wildcard (*) you can specify one or more files
```
cd /home/*[COLOR="Blue"]musig[/COLOR]*/flacMusic
pacpl -t mp3 fortunate_son.flac bad_moon_rising.flac
```
To convert files in subdirectories, use the option --recursive.
```
cd /home/*[COLOR="Blue"]musig[/COLOR]*/flacMusic
pacpl -t mp3 -r *.flac
```
If you don't want to keep the original (or if you only want to change the bitrate), use --overwrite
```
cd /home/*[COLOR="Blue"]musig[/COLOR]*/flacMusic
pacpl -t mp3 --overwrite *.flac
```

**2.2  Output from and to a specified directory**
In this case from the folder aacMusic to the folder mp3Music, both in the home directory of "*[COLOR="Blue"]user musig[/COLOR]*"
```
pacpl -t mp3 --outdir /home/[COLOR="Blue"]*musig*[/COLOR]/mp3Music /home/[COLOR="Blue"]*musig*[/COLOR]/aacMusic
```
You have to create the output folder first, PACPL will tell you
```
mkdir /home/*[COLOR="Blue"]musig[/COLOR]*/mp3Music
```
If you use --recursive and want to keep the directories structure, add --preserve
```
pacpl -t mp3 -r -p --outdir /home/[COLOR="Blue"]*musig*[/COLOR]/mp3Music /home/[COLOR="Blue"]*musig*[/COLOR]/aacMusic
```
To keep files already matching the destination extension and copy to the output directory, use --keep
```
pacpl -t mp3 -k --outdir /home/[COLOR="Blue"]*musig*[/COLOR]/mp3Music /home/[COLOR="Blue"]*musig*[/COLOR]/aacMusic
```

**2.3  Set bitrate with option --bitrate (default 128 )**
[COLOR="Red"]-Have not found out yet if this option makes a CBR or VBR (default). There are other options like --mpcqual described in the --longhelp which obviously make a VBR...[/COLOR]
```
pacpl -t mp3 --bitrate 320 --outdir /home/[COLOR="Blue"]*musig*[/COLOR]/Desktop/auflegen2 /home/[COLOR="Blue"]*musig*[/COLOR]/Desktop/auflegen
```

**2.4  Set Frequency with option --freq (default 44100)**
Here with bitrate option, makes not much sense without...
```
pacpl -t mp3 --bitrate 320 --freq 48000 --outdir /home/*[COLOR="Blue"]musig[/COLOR]*/Desktop/auflegen2 /home/[COLOR="Blue"]*musig*[/COLOR]/Desktop/auflegen
```

**2.5  Specify "from" file type**
With the option --only, all other file types are excluded
```
pacpl -t mp3 -o aac --outdir /home/*[COLOR="Blue"]musig[/COLOR]*/mp3Music /home/[COLOR="Blue"]*musig*[/COLOR]/aacMusic
```

This is an update from the previous tutorial.  All the credit for this goes to my friend from Zurich ti-mo.  if you find this tutorial helpful please thank ti-mo (see post 53) also.

Enjoy!

---

### Post by pemur1 on 2008-03-21
I'm trying to re-install PACPL following this, but I'm still getting this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

Help!

---

### Post by cozmicharlie on 2008-03-21
At what step were you at when this happens?  When you state 'reinstall" - did you have it installed and working at one time?  Also, you may want to go back to your original post - Lord Illidan posted a response and I think he may know more about your particular problem than I do.  Once you get that fixed then come back here and try to install using this method..

---

### Post by pemur1 on 2008-03-21
Right after adding the GPG Key

No. I've never had it installed. At least correctly.

I'm still running sudo dpkg --confgure -a

It seems to be taking quite a long time. As soon as it's done, I'll post everything in the other thread.

---

### Post by cozmicharlie on 2008-03-21
Ok - what version of Ubuntu are you running?  Is it 32 or 64 bit?

---

### Post by pemur1 on 2008-03-21
> **cozmicharlie said:**
> Ok - what version of Ubuntu are you running?  Is it 32 or 64 bit?

7.10 32 bit

---

### Post by cozmicharlie on 2008-03-21
What is the output when you run this:
```
sudo dpkg --configure -a
```

---

### Post by pemur1 on 2008-03-21
> **cozmicharlie said:**
> What is the output when you run this:
```
sudo dpkg --configure -a
```

it's still running.

Right now, it looks like a foreign language to me. :)

Setting up pacpl (4.0.0beta3-1) ...
CPAN: Storable loaded ok
Going to read /root/.cpan/sources/authors/01mailrc.txt.gz
CPAN: Compress::Zlib loaded ok
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/02packages.details.txt.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/modules/02packages.details.txt.gz](ftp://carroll.cac.psu.edu/pub/CPAN/modules/02packages.details.txt.gz)
Going to read /root/.cpan/sources/modules/02packages.details.txt.gz
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT

  There's a new CPAN.pm version (v1.9205) available!
  [Current version is v1.7602]
  You might want to try
    install Bundle::CPAN
    reload cpan
  without quitting the current session. It should be a seamless upgrade
  while we are running...

Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/modules/03modlist.data.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/modules/03modlist.data.gz](ftp://carroll.cac.psu.edu/pub/CPAN/modules/03modlist.data.gz)
Going to read /root/.cpan/sources/modules/03modlist.data.gz
Going to write /root/.cpan/Metadata
Parse::RecDescent is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Inline is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Inline::C is up to date.
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Devel::Symdump
Running make for A/AN/ANDK/Devel-Symdump-2.08.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz)
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz)
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/A/AN/ANDK/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/A/AN/ANDK/Devel-Symdump-2.08.tar.gz ok
Scanning cache /root/.cpan/build for sizes
Devel-Symdump-2.08/
Devel-Symdump-2.08/t/
Devel-Symdump-2.08/t/recur.t
Devel-Symdump-2.08/t/export.t
Devel-Symdump-2.08/t/tree.t
Devel-Symdump-2.08/t/symdump.t
Devel-Symdump-2.08/t/pod.t
Devel-Symdump-2.08/t/autogen.t
Devel-Symdump-2.08/t/diff.t
Devel-Symdump-2.08/t/podcover.t
Devel-Symdump-2.08/ChangeLog.svn
Devel-Symdump-2.08/MANIFEST
Devel-Symdump-2.08/ChangeLog
Devel-Symdump-2.08/lib/
Devel-Symdump-2.08/lib/Devel/
Devel-Symdump-2.08/lib/Devel/Symdump.pm
Devel-Symdump-2.08/lib/Devel/Symdump/
Devel-Symdump-2.08/lib/Devel/Symdump/Export.pm
Devel-Symdump-2.08/Makefile.PL
Devel-Symdump-2.08/README
Devel-Symdump-2.08/META.yml
Devel-Symdump-2.08/SIGNATURE

  CPAN.pm: Going to build A/AN/ANDK/Devel-Symdump-2.08.tar.gz

WARNING: LICENSE is not a known parameter.
Checking if your kit is complete...
Looks good
'LICENSE' is not a known MakeMaker parameter name.
Writing Makefile for Devel::Symdump
cp lib/Devel/Symdump.pm blib/lib/Devel/Symdump.pm
cp lib/Devel/Symdump/Export.pm blib/lib/Devel/Symdump/Export.pm
Manifying blib/man3/Devel::Symdump.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/autogen.....ok                                                             
t/diff........ok                                                             
t/export......ok                                                             
t/pod.........skipped
        all skipped: Test::Pod 1.00 required for testing POD
t/podcover....skipped
        all skipped: Test::Pod::Coverage required for testing pod coverage
t/recur.......ok                                                             
t/symdump.....ok                                                             
t/tree........ok                                                             
All tests successful, 2 tests skipped.
Files=8, Tests=29,  1 wallclock secs ( 0.31 cusr +  0.07 csys =  0.38 CPU)
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.8.8/Devel/Symdump.pm
Installing /usr/local/share/perl/5.8.8/Devel/Symdump/Export.pm
Installing /usr/local/man/man3/Devel::Symdump.3pm
Writing /usr/local/lib/perl/5.8.8/auto/Devel/Symdump/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
  /usr/bin/make install  -- OK
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Fri, 21 Mar 2008 14:31:21 GMT
Running install for module Switch
Running make for R/RG/RGARCIA/Switch-2.13.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
  [ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz](ftp://bc1.hpc.lsu.edu/pub/mirrors/CPAN/authors/id/R/RG/RGARCIA/Switch-2.13.tar.gz)


There's more to come apparently.

---

### Post by cozmicharlie on 2008-03-21
Did it work?  What you have sent so far looks OK.

---

### Post by pemur1 on 2008-03-21
> **cozmicharlie said:**
> Did it work?  What you have sent so far looks OK.

Still waiting for it to finish.

---

### Post by pemur1 on 2008-03-21
Okay. It finished. I posted everything in the other thread.

---

### Post by peter_babeone on 2008-07-16
The installation was fine, but I have a problem with the formats .wma and .ra.

Does anybody know, how to solve it.

Thanks lots

---

### Post by cozmicharlie on 2008-07-17
What do you mean you "have a problem"?

---

### Post by peter_babeone on 2008-07-17
I followed your tutorial and installed without any problems. But I got an error, when I converted from .wma to .mp3. I'm using the last version 4.02 and Ubuntu Hardy

> duc@vn:~/Desktop/esl-lab/easy$ pacpl -t mp3 A\ Fun\ Day.wma 
Perl Audio Converter - 4.0.2

Converting:  [A Fun Day.wma] -> [mp3] decode failed with exit status: 256


Total files converted: 0, failed: 1


It seems to be okay with other extensions, for example

> duc@vn:~/Desktop/Entertainment/music/2_mp3$ pacpl -t aac Maria.mp3 
Perl Audio Converter - 4.0.2

Converting:  [Maria.mp3] -> [aac] ..done. 

Total files converted: 1, failed: 0
duc@vn:~/Desktop/Entertainment/music/2_mp3$ ls -al
-rwxrwx--- 1 root plugdev 2970980 2008-07-17 12:09 Maria.aac
-rwxrwx--- 1 root plugdev 1506160 2008-02-21 14:43 Maria.mp3


---

### Post by peter_babeone on 2008-07-17
After working around, I know now, this isn't the problem of pacpl.
My wma music files are copyrighted, therefor it didn't work

---

### Post by cozmicharlie on 2008-07-17
> **peter_babeone said:**
> After working around, I know now, this isn't the problem from pacpl.
My wma music files are copyrighted, therefor it didn't work

That is a problem.  You have to be careful when you purchase music from the on-line stores like itunes.  You are actually not buying the music but buying a license to play the music and that license restricts you.  

Glad you got pacpl up working though.

Enjoy!

---

### Post by eldeingles on 2008-08-29
Hi, there...seeing the app most promising I have just given it a go.
Done everything posted above.
I get the message:

aa@aa-desktop ~/pacpl-4.0.2 $ pacpl --to mp3 01.flac
Perl Audio Converter - 4.0.2

error: could not find suitable application to encode: mp3

and so?

I'm on Mint Elyssa

---

### Post by cozmicharlie on 2008-08-31
> **eldeingles said:**
> Hi, there...seeing the app most promising I have just given it a go.
Done everything posted above.
I get the message:

aa@aa-desktop ~/pacpl-4.0.2 $ pacpl --to mp3 01.flac
Perl Audio Converter - 4.0.2

error: could not find suitable application to encode: mp3

and so?

I'm on Mint Elyssa

make sure you have the codecs installed.  You should install all the gstreamer codecs (good, bad, ugly, base) and also install the flac code.  I also install the lame mp3 codec.  These should all be available in the Mint repository since Mint is based on Ubuntu.  If you can't find I am sure the Mint forums or wiki has instructions for installing all the codecs.  Post back though if you are still having problems.

---

### Post by dan73 on 2008-09-14
Hi Cozmicharlie, thanks for your useful advice about installing PACPL

I'm new to Ubuntu, but have been enjoying using it for the past few days since my Windows died (again) this time due to a virus. T

I am enjoying Amarok as a music player and finding it far superior to the bloated winamp in windows. Most of my files are burnt from CD using AAC. I'm trying to use K3B to burn some CDs which is integrated with Amarok as CD burner, but it doesn't like the AAC files. Also Amarok refuses to FF or Rewind AAC files.


What I want to do is convert all my AAC files to MP3, and place them in a new folder , leaving the original files intact.


I looked at the long help for PACPL but couldn't really figure it out, I'm not to bright with regards to using terminal and commands unless things are spelt out for me clearly. Also there doesn't seem to be any tutorials for PACPL anywhere, their website is a bit sparse.

---

### Post by cozmicharlie on 2008-09-15
dan73 - Glad you are enjoying Ubuntu.

Yes - I agree that you won't find much help on the PACPL website.  PACPL is developed by an individual and he just doesn't have time to write exhaustive manuals.  He is very good about answering any questions though and you can always ask on this thread.  If I can't help you I will ask the developer and he will always respond.

To convert from aac to mp3 is simple.  The command is:

```
pacpl --to mp3 --only aac --outdir yournewdirectory yourfile.aac

```
so say I have a folder with my aac files named aacMusic in my home directory and in them I have music1.aac music2.aac etc.  I want to convert them to mp3 and place them in a new folder in my home directory called mp3Music.  The exact command is:

```
pacpl --to mp3 --only aac --outdir /home/cozmicharlie/mp3Music Home/cozmicharlie/aacMusic

```
Note this converts all the music1.aac files in the folder (but by using the --only it only converts aac files so if you have other files such as a text or jpeg it ignores them).  If you want to convert individual files then use those instead of the whole directory so it would be:

```
pacpl --to mp3 --only aac --outdir /home/cozmicharlie/mp3Music Home/cozmicharlie/aacMusic/music1.aac Home/cozmicharlie/aacMusic/music2.aac
``` 

That should convert them to mp3 and move them to the new directory.  A couple things to remember - if you have file name with spaces use quotation marks (or change the file names).  So if my music files were named music 2.aac I would have to list them as "/Home/cozmicharlie/aacMusic/music 2.aac".  Linux does not like spaces.  Also if you want to tag then add the tag you want to the command such as --artist "Eric Clapton" etc.

Enjoy

Post back if you have any further questions.  

and of course add any other parameters you like such as tags, place in a different folder ect.

---

### Post by 3rdalbum on 2008-09-15
Thanks for the HOWTO, but PAACPL seems to do less than what I can do with sox and lame just as easily.

---

### Post by cozmicharlie on 2008-09-16
dan73 - also, if you are using Amarok it is easier to use PACPL as a plug in for Amarok.  If you open Amarok and go to the menu>tools>script manager and open it.  You should see a category called general and under general pacx.  Click on pacx to highlight it and then on the right side of the dialog window hit run.  That should start the script so any time you have a music file loaded in Amarok you right click on the file and a menu comes up and you should have an option to convert in PACPL.

---

### Post by IGITIHI on 2008-09-28
Pacx seems to be very useful but how can I choose the bitrate? For example, when converting from flac to mp3?

---

### Post by cozmicharlie on 2008-09-30
> **IGITIHI said:**
> Pacx seems to be very useful but how can I choose the bitrate? For example, when converting from flac to mp3?

Glad to hear you found it useful.  It is simple just use --bitrate as part of the command.  If you type the following at the prompt you will get a list of all the options.

```
pacpl --longhelp

```
the bitrate is --bitrate then whatever value you want.  

Enjoy

---

### Post by IGITIHI on 2008-09-30
So, as I understand, I can get only cbr with pacx. Is there a way to get vbr?

---

### Post by cozmicharlie on 2008-09-30
> **IGITIHI said:**
> So, as I understand, I can get only cbr with pacx. Is there a way to get vbr?

Not sure - let me ask the developer and I will get back to you.

---

### Post by cozmicharlie on 2008-10-01
> **IGITIHI said:**
> So, as I understand, I can get only cbr with pacx. Is there a way to get vbr?

The developer provided this answer to your question:

"As of 4.0.3, you can turn off all default encoder options via --defopts (see the man page) from there, you can specify whatever options (from the actual encoder) you want by using --eopts.  The default however, is VBR."

I hope this helps - if you still have questions, post back.

---

### Post by dutler on 2008-11-19
Thank you for the thread. Im having troubles with PACPL and hopping for some pointers:
Im using kubuntu hardy and have install PACPL from source.
I first run the kubuntu to script as instructed and then compiled and installed. All looked well, BUT there is no KDE integration. Amarok and konqueror action menu is not present.

PACPL runs fine from bash.

brilliant insights?
-tom

---

### Post by cozmicharlie on 2008-11-19
I should add this to the tutorial and I will eventually.  To add them do the following:

Amarok:  You need to add PACPL as a script.  If you don't still have the source file for PACPL go ahead and download it again.  Extract the file.  Open the file and go to >plugins>Amarok and you will see a script labeled pacx.  Copy this script to home>yourname>.kde>share>apps>amarok (note you have to do "show hidden files" from the view menu to see the .kde folder).  Now paste the script into the folder.  Open Amarok and go to menu>tools>script manager and you should see pacx listed.  Hit run and close out.  Restart Amarok.  Load a song into the play list, right click on the song and the option to convert with pacpl should be in the menu.  

Repeat the same process for konqueror but add it to .kde/share/apps/konqueror folder.

That should work for you but if not post back.

Enjoy

---

### Post by dutler on 2008-11-19
Thank you, it appears that the install of PACPL is meant to install the plugins, but in /usr space:
[LIST]
[*]/usr/share/apps/amarok/scripts/pacx
[/LIST]

But I did search around for adding extensions to konqueror and amarok resulting in the plugins also being placed in:
[LIST]
[*]/share/apps/konqueror/servicemenus
[*]~/.kde/share/apps/amarok
[/LIST]
but still no service menu.

---

### Post by cozmicharlie on 2008-11-19
> **dutler said:**
> Thank you, it appears that the install of PACPL is meant to install the plugins, but in /usr space:
[LIST]
[*]/usr/share/apps/amarok/scripts/pacx
[/LIST]

But I did search around for adding extensions to konqueror and amarok resulting in the plugins also being placed in:
[LIST]
[*]/share/apps/konqueror/servicemenus
[*]~/.kde/share/apps/amarok
[/LIST]
but still no service menu.

Humm  - not sure why.  Give me some info on the version of Linux (or Ubutnu) your are using.  Also, are you using gnome or kde.  I may have to go back to the developer.  He is very good about helping.

---

### Post by dutler on 2008-11-19
Kubuntu 8.04 2.6.24-16-generic
I the universe and multiverse repo's enabled but not back ports.

I will post the issue at sf and report developments here as well.

thanks, tom

[https://sourceforge.net/forum/message.php?msg_id=5677326](https://sourceforge.net/forum/message.php?msg_id=5677326)

---

### Post by cozmicharlie on 2008-11-19
> **dutler said:**
> Kubuntu 8.04 2.6.24-16-generic
I the universe and multiverse repo's enabled but not back ports.

I will post the issue at sf and report developments here as well.

thanks, tom

[https://sourceforge.net/forum/message.php?msg_id=5677326](https://sourceforge.net/forum/message.php?msg_id=5677326)

Just to be clear.  Did the script show up in Amarok?  Were you able to use it in Amarok?  By service menu do you mean in Konqueror?

Good idea to post there also.  I will also email the developer.

---

### Post by dutler on 2008-11-19
> By service menu
I was meaning > right click > actions > PACPL in both amarok and konqueror - but the terminology is just a konqueror thing?

/usr/share/apps/amarok/scripts/pacx/pacx
and
/usr/share/apps/konqueror/servicemenus/pacpl.desktop

are both present in the file system but the options do not "show up" in amarok nor konqueror.

-tom

---

### Post by cozmicharlie on 2008-11-20
> **dutler said:**
> I was meaning > right click > actions > PACPL in both amarok and konqueror - but the terminology is just a konqueror thing?

/usr/share/apps/amarok/scripts/pacx/pacx
and
/usr/share/apps/konqueror/servicemenus/pacpl.desktop

are both present in the file system but the options do not "show up" in amarok nor konqueror.

-tom

I tried it on another of my computers. I first tried to install the source package as per the tutorial, but I ran into the same problem you are having.  What I did to get it to work is install the debian package (I did not uninstall the pacpl installed from source).  Go to the pacpl web site>debian download>pacpl_4.0.0beta3-1_i386.deb.  Double click on the downloaded deb package (make sure you show details) and follow all the prompts (type yes at all the prompts asking for internet access). 

Once installed, open Amarok>menu>tools>script manager and pacx should be listed.  Click on run, close, give it a few seconds and you should be able to right click and pacpl should show up. 

This worked for me.

---

### Post by dutler on 2008-11-20
grrr... install the deb and now right click in empty konqueror space shows the PACPL menu (r. click on file does not show the menu), but when I select the output format and location, no files are created.

Nothing shows in Dolphin of Amarok.

thanks for your help! tom

---

### Post by cozmicharlie on 2008-11-21
> **dutler said:**
> grrr... install the deb and now right click in empty konqueror space shows the PACPL menu (r. click on file does not show the menu), but when I select the output format and location, no files are created.

Nothing shows in Dolphin of Amarok.

thanks for your help! tom

OK - let me contact the developer.  Does the script show up in the Amarok script manager (menu>tools>script manager).  Just to be sure, you are able to transcode using the command line - is that correct?

Hang in there, we will figure it out.

---

### Post by dutler on 2008-11-21
> Does the script show up in the Amarok script manager (menu>tools>script manager).
Yep, Clicked on run and now Amarok and PACPL work great. Thanks.

Still have zero success withe Dolphin - menu does not show at all.

In Konqueror, the menu is there and acts like everything works, but the out put is no where to be found.

Still no response at SF... the developer (Philip Lyons ?) must have a life or something :)

So Im trying to install soundKonverter to check it out as well, but
> dpkg: error processing /var/cache/apt/archives/soundkonverter_0.3.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/audio/x-ape.desktop', which is also in package pacpl
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I mv'd x-ape.desktop to x-ape.desktop.backup4soundKonverter...... but still got the same error. Holding my breath for the PACPL konqueror integration - wish I could do more :)

thank you for your help

---

### Post by cozmicharlie on 2008-11-21
OK - I'll check with the developer and see if he can help.

---

### Post by dutler on 2008-11-22
Thanks again for your help cozmicharlie, I am in contact with Philip. 
-tom

---

### Post by 666porcondissaum on 2008-11-23
CozmicHarli... I've been looking for the solution but no good-time. 

pacpl --to flac 101.shn
Perl Audio Converter - 4.0.3

Converting:  [101.shn] -> [flac] decode failed with exit status: 256


Total files converted: 0, failed:

Same happenned to wav.

Help me.

---

### Post by cozmicharlie on 2008-11-24
> **666porcondissaum said:**
> CozmicHarli... I've been looking for the solution but no good-time. 

pacpl --to flac 101.shn
Perl Audio Converter - 4.0.3

Converting:  [101.shn] -> [flac] decode failed with exit status: 256


Total files converted: 0, failed:

Same happenned to wav.

Help me.

Do you have the flac and wav codecs installed?

---

### Post by cozmicharlie on 2008-11-26
> **dutler said:**
> Thanks again for your help cozmicharlie, I am in contact with Philip. 
-tom

Great- he is very helpful. I did get a response from him.  This may also help. 

1st, pacpl.desktop should be in the correct location for konqueror AND dolphin to get the PACPL menu to show up in their respective locations.  Since both of these appear to be correct, I would check the permissions of the file.  You could also try placing this file in the usrers local directory to see if that works (~/.kde/share/apps/konqerour/servicemenus) & (~/.kde/share/apps/dolphin/servicemenus).  Let me know if any of this works

Post back when you get it figured out so others can see how you fixed it.

---

### Post by I_love_Life on 2008-12-09
Hello, I followed the instructions for installing pacpl, when execute ```
pacpl -f
``` I get 

[HTML]EXT       E   D   ENCODER         DECODER         TAG-READ   TAG-WRITE
----------------------------------------------------------------------
aac       Y   Y   faac            faad               N          N
ac3       Y   Y   ffmpeg          mplayer            N          N
aif       Y   Y   sox             sox                N          N
aiff      Y   Y   sox             sox                N          N
ape       Y   Y   mac             mac                N          N
asf       N   Y                   mplayer            N          N
au        Y   Y   sox             sox                N          N
avi       N   Y                   mplayer            N          N
avr       Y   Y   sox             sox                N          N
bonk      Y   Y   bonk            bonk               N          N
caf       Y   Y   sndfile-convert sndfile-convert    N          N
cdr       Y   Y   sox             sox                N          N
divx      N   Y                   mplayer            N          N
fap       Y   Y   sndfile-convert sndfile-convert    N          N
fla       Y   Y   flac            flac               Y          Y
flac      Y   Y   flac            flac               Y          Y
flv       N   Y                   mplayer            N          N
ircam     Y   Y   sndfile-convert sndfile-convert    N          N
la        Y   Y   la              la                 N          N
lpac      Y   Y   lpac            lpac               N          N
m4a       Y   Y   faac            faad               Y          Y
m4v       N   Y                   mplayer            N          N
mat       Y   Y   sndfile-convert sndfile-convert    N          N
mat4      Y   Y   sndfile-convert sndfile-convert    N          N
mat5      Y   Y   sndfile-convert sndfile-convert    N          N
mkv       N   Y                   mplayer            N          N
mmf       Y   Y   ffmpeg          ffmpeg             N          N
mov       N   Y                   mplayer            N          N
mp2       Y   Y   ffmpeg          ffmpeg             N          N
mp3       Y   Y   lame            lame               Y          Y
mp4       Y   Y   faac            faad               Y          Y
mpc       Y   Y   mppenc          mppdec             Y          Y
mpeg      N   Y                   mplayer            N          N
mpg       N   Y                   mplayer            N          N
mpp       Y   Y   mppenc          mppdec             Y          Y
nist      Y   Y   sndfile-convert sndfile-convert    N          N
nsv       N   Y                   mplayer            N          N
nuv       N   Y                   mplayer            N          N
ofr       Y   Y   ofr             ofr                N          N
ofs       Y   Y   ofs             ofs                N          N
ogg       Y   Y   oggenc          oggdec             Y          Y
ogm       N   Y                   mplayer            N          N
pac       Y   Y   lpac            lpac               N          N
paf       Y   Y   sndfile-convert sndfile-convert    N          N
psp       N   Y                   mplayer            N          N
pvf       Y   Y   sndfile-convert sndfile-convert    N          N
qt        N   Y                   mplayer            N          N
ra        Y   Y   ffmpeg          ffmpeg             N          N
ram       N   Y                   ffmpeg             N          N
raw       Y   Y   sox             sox                N          N
rm        N   Y                   mplayer            N          N
rv        N   Y                   mplayer            N          N
sd2       Y   Y   sndfile-convert sndfile-convert    N          N
sf        Y   Y   sndfile-convert sndfile-convert    N          N
shn       Y   Y   shorten         shorten            N          N
smk       N   Y                   mplayer            N          N
smp       Y   Y   sox             sox                N          N
snd       Y   Y   sox             sox                N          N
spx       Y   Y   speexenc        speexdec           Y          Y
svcd      N   Y                   mplayer            N          N
tta       Y   Y   ttaenc          ttaenc             N          N
vcd       N   Y                   mplayer            N          N
vob       N   Y                   mplayer            N          N
voc       Y   Y   sox             sox                N          N
w64       Y   Y   sndfile-convert sndfile-convert    N          N
wav       Y   Y   mv              cp                 N          N
wma       Y   Y   ffmpeg          ffmpeg             N          N
wmv       N   Y                   mplayer            N          N
wv        Y   Y   wavpack         wvunpack           Y          Y
[/HTML]
encode formats: 47 --- decode formats: 69

So, even though I have mp3 and flac encoder/decoder and decoder I still get the error

pacpl -t flac Music/B.E.S.T/moby\ -\ 18.mp3 
Perl Audio Converter - 4.0.1

error: could not find suitable application to encode: flac

see 'pacpl --help' or 'pacpl --longhelp' for a list of options.

---

### Post by mrneil on 2009-01-03
Here is a fix for the "encode failed with exit status: 256" error message.

I was getting the "encode failed with exit status: 256" error message when trying to convert flac to m4a to use on my ipod. The problem was that pacpl is passing the wrong command line options to ffmpeg, as the --verbose option reveals (see output below). The fix is to edit line 2036 of /usr/bin/pacpl to read

case /mp4|m4a|m4b/ { return "-title \"$tag_name{title}\" -track \"$tag_name{track}\" -author \"$tag_name{artist}\" -album \"$tag_name{album}\" \"$tag_name{comment}\" -year \"$tag_name{year}\""; }

(all one line). ffmpeg is expecting single dashes for options, "author" instead of "artist", and has no genre field. I've filed a bug report.

Here are some words for Google to pick up: If you are trying to batch convert flac files to mp4 or m4a then pacpl will do the job and preserve tag information.


Example of pacpl failing with "encode failed with exit status: 256" error message.

$ pacpl --verbose --encoder faac --to m4a "01. Rock n Roll Train.flac"
Use of uninitialized value in concatenation (.) or string at /usr/bin/pacpl
line 206, <DATA> line 1.
Perl Audio Converter - 4.0.3

Converting:  [01. Rock n Roll Train.flac] -> [m4a]


flac 1.2.1, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh
Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type Flac' for
details.

01. Rock n Roll Train.flac: done
FFmpeg version SVN-r13582, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=${prefix}/lib
--shlibdir=${prefix}/lib --bindir=${prefix}/bin
--incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame
--enable-gpl --enable-libfaad --mandir=${prefix}/share/man
--enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid
--enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-x11grab
--enable-libgsm --enable-libx264 --enable-liba52 --enable-libtheora
--extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --enable-swscale
--enable-libdc1394 --enable-nonfree --disable-mmx --disable-stripping
--enable-avfilter --enable-libdirac --disable-decoder=libdirac
--enable-libschroedinger --disable-encoder=libschroedinger --disable-altivec
--disable-armv5te --disable-armv6 --disable-vis
  libavutil version: 49.7.0
  libavcodec version: 51.58.0
  libavformat version: 52.16.0
  libavdevice version: 52.0.0
  libavfilter version: 0.0.0
  built on Oct 22 2008 13:31:17, gcc: 4.3.2
ffmpeg: unrecognized option '--title'
encode failed with exit status: 256


Total files converted: 0, failed: 1

---

### Post by cozmicharlie on 2009-01-03
Thanks mrneil - I will pass this on to the developer.

*update 05-08-09 - I did pass this on to the developer and he will look into it - look for a fix in the next version of PACPL.  Thanks again mrneil for bringing this to our attention.*

---

### Post by Progressive on 2009-01-07
I just got this installed in Jaunty through the universe repos and it works with Amarok after I enabled the script (wish the installer would do this for me)

Yet, I can't seem to get it to run in Konqueror or Dolphin. My Amarok is version 1.4 while Konqueror and Dolphin are version 4. Perhaps this is the reason?

I plan to upgrade to Amarok2 whenever it hits to the repos, so hopefully this isn't a KDE4 problem. It could be a Jaunty problem.

soundKonverter didn't work for me, but I am very happy with this wonderful program. It works great in Amarok!!!! It should come standard in Amarok!

---

### Post by Progressive on 2009-01-07
Also, in Amarok it doesn't seem to work if there are parentheses in the filename

---

### Post by cozmicharlie on 2009-01-08
> **Progressive said:**
> I just got this installed in Jaunty through the universe repos and it works with Amarok after I enabled the script (wish the installer would do this for me)

Yet, I can't seem to get it to run in Konqueror or Dolphin. My Amarok is version 1.4 while Konqueror and Dolphin are version 4. Perhaps this is the reason?

I plan to upgrade to Amarok2 whenever it hits to the repos, so hopefully this isn't a KDE4 problem. It could be a Jaunty problem.

soundKonverter didn't work for me, but I am very happy with this wonderful program. It works great in Amarok!!!! It should come standard in Amarok!

Thanks for pointing this out.  Turns out my directions were slightly off - luckily the developer of PACPL is very responsive to help requests.  These are the corrected instructions:

**for amarok:**
pacx -> /usr/share/apps/amarok/scripts/pacx/pacx (yes...you have to create a pacx directory and place the pacx binary in it)

**for konqueror/d3lphin/dolphin:**
pacpl.desktop can be placed in either /usr/share/apps/konquerer/servicemenus or in your home directory (as stated in post# 43) (~/.kde/share/apps/konqueror/servicemenus).  pacpl.desktop can be used for d3lphin or dolphin the same as konqueror by using the same directory as above.  Just replace konqueror with d3lphin/dolphin...the rest is the same.

This should work for you.

---

### Post by Progressive on 2009-01-12
Are those directions for the new Amarok2 which just hit the repos?

---

### Post by cozmicharlie on 2009-01-12
> **Progressive said:**
> Are those directions for the new Amarok2 which just hit the repos?

I believe so but let me try it out and I will report back.

---

### Post by cozmicharlie on 2009-01-12
> **Progressive said:**
> Are those directions for the new Amarok2 which just hit the repos?

Yes - they will work for Amarok 2.

---

### Post by t-mo_ on 2009-01-29
pacpl was one of the apps who forced me to work with the terminal when i started with ubuntu (i was perfectly supported by friends...). I couldn't discover a tutorial for a long time wherein i don't had to read the whole discussion to find answers (thanks to cozmicharlie, you saved my day last summer)

i write tutorials quite often for a friend (and she forgets from time to time how to drag and drop, no joke), usually with screenshots and optical helps... and i collect useful commands on tomboy-notes because my memory acts funny too :)

i am not really able to code, but willing to help. So i started to write some copy/paste examples with short explanations, understandable for absolute beginners like i was once. hope it helps?

cozmicharlie, maybe you can use this to complete your treat in the first page that people like my friend don't have to scroll so many pages anymore :) i started right were you stopped. it is not much, but... if more people are interested in a tidy tut, i'd like to help building it up.


complete list of options
```

pacpl -l
```
list all available codecs for encoder and decoder
```
pacpl -f 
```
some explanations, as usual
```
man pacpl
```



**1.1	Simple convert**

Open a terminal and go to the directory containing the files you want to convert. In the following example a  folder named "flacMusic" in the home directory of "*[COLOR="Blue"]user musig[/COLOR]*" (replace "*[COLOR="Blue"]musig[/COLOR]*" with your name and the location with the one you need)


```
	cd /home/*[COLOR="Blue"]musig[/COLOR]*/flacMusic
	pacpl --to mp3 Home/music/*.flac
```
 You don't need to specify the file type like in the example above.
*.flac affects .flac-files only (replaces option --only, see 1.5 ).


**1.2	Output to a specified directory**
	In this case from the folder aacMusic to the folder mp3Music, both in the home directory of "*[COLOR="Blue"]user musig[/COLOR]*"

```
	pacpl --to mp3 --outdir /home/[COLOR="Blue"]*musig*[/COLOR]/mp3Music /home/[COLOR="Blue"]*musig*[/COLOR]/aacMusic
```
you have to create the output folder first, [COLOR="Red"]**PACPL**[/COLOR] will tell you
```
mkdir /home/*[COLOR="Blue"]musig[/COLOR]*/mp3Music
```

[B]
1.3	Set bitrate with option --bitrate (default 128 )[/B]
	[COLOR="Red"]-Have not checked yet if this option makes a CBR or VBR (default). There are other options like --mpcqual described in the --longhelp who obviously make a VBR...[/COLOR]

	```
pacpl --to mp3 --bitrate 320 --outdir /home/[COLOR="Blue"]*musig*[/COLOR]/Desktop/auflegen2 /home/[COLOR="Blue"]*musig*[/COLOR]/Desktop/auflegen
```


**1.4	Set Frequency with option --freq (default 44100)**
here with bitrate option. makes not so much sense without...

	```
pacpl --to mp3 --bitrate 320 --freq 48000 --outdir /home/*[COLOR="Blue"]musig[/COLOR]*/Desktop/auflegen2 /home/[COLOR="Blue"]*musig*[/COLOR]/Desktop/auflegen
```


**1.5	Specify "from" file type**
with the option --only, all other file types are excluded

	```
pacpl --to mp3 --only aac --outdir /home/*[COLOR="Blue"]musig[/COLOR]*/mp3Music /home/[COLOR="Blue"]*musig*[/COLOR]/aacMusic
```

---

### Post by cozmicharlie on 2009-01-29
t-mo , this is great.  thanks so much.  I just have not had time to go through and consolidate this so your help is much appreciated.  I think what we really need to do is rewrite this and start a new thread but I hate to have too many threads scattered in the forums (it makes it too hard for newbies to figure out which to use).  I will try and modify and update the tutorial with your suggestions.

Again, thanks so much for taking the time to do this.

---

### Post by t-mo_ on 2009-01-29
I wouldn't care to invest some more time into this.(broke my spine some months ago, so i have lots of time... but easy, no palsy :)  )
I receive competent help so often from just "someone" who spent time for howtos, fixes and stuff, so if i can do something for this, just tell me.

i would rewrite the whole thing, and complete it with some more options like

--keep
--preserve
--defopts/--encoder/--decoder (i want to know how to make CBR, means which codec to use, so if you can give me a hint..)

and a section with fixes and workarounds, maybe.(think i should check first when the new release comes out and what changes it comes with). i would post it here or send it to you, however, so you could revise the whole thing. since i live in switzerland, i could translate it to german too, but i never used german forums. do you think this would be appreciated?

i'm not so used to work with forums and stuff, what would be the best way? attach it to the post?

---

### Post by ali-zi-zeperto on 2009-02-08
i want to convert a flv file to mpg or avi but i can`t.can you help me.i can`t understand these two lines with red color
pacpl [COLOR="Red"]--[/COLOR]to mp3 Home/music/*.flac

thanks

---

### Post by cozmicharlie on 2009-02-08
> **ali-zi-zeperto said:**
> i want to convert a flv file to mpg or avi but i can`t.can you help me.i can`t understand these two lines with red color
pacpl [COLOR="Red"]--[/COLOR]to mp3 Home/music/*.flac

thanks

No problem.  maybe once I explain the code you will have a better understanding.

In the example I am converting a flac file to an mp3.
"--to" means you want to convert your file to that format.  In my example it would be mp3.  
"Home/music/*.flac" is the location of the file I want to convert.  So I am converting the *.flac file located in the folder Home/music from flac to mp3.

So for your files the command would be:
```
$ pacpl --to mpeg Home/video/yourfile.flv 
```
Where Home/video/yourfile.flv is the location of your file (this is just an example - your file may be in another folder.  Use the actual location of your file). 

For avi it is
```
$ pacpl --to avi /Home/video/yourfile.flv
```

You may want to change the default settings in pacpl.  So before you start open a terminal and type:
```
$ pacpl --longhelp
``` 
This shows all the options available when you run pacpl.  The commands are always in the form --some command
So for example if you want to change the bitrate you would use the following (note: this is an example it is completely made up):
```
$ pacpl --to mpeg --bitrate 128 Home/video/yourfile.flv
```

As much as I love PACPL, if you are not comfortable with command line (though I think everyone that uses Linux should learn the basics), you may want to try Winff (winff.org).  It's really just a front end for ffmpeg but it is GUI so it is very easy to use.

Post back if you have any problems.

---

### Post by ali-zi-zeperto on 2009-02-08
thank you so much but there is an error 

ali-zi-zeperto@mY-Pc:~/Desktop$ pacpl --to avi /home/ali-zi-zeperto/Desktop/get_video.flv
Perl Audio Converter - 4.0.3

error: encoding 'to' the following is not supported: avi

see 'pacpl --help' or 'pacpl --longhelp' for a list of options.

what can i do?have i to do anything else

---

### Post by cozmicharlie on 2009-02-09
> **ali-zi-zeperto said:**
> thank you so much but there is an error 

ali-zi-zeperto@mY-Pc:~/Desktop$ pacpl --to avi /home/ali-zi-zeperto/Desktop/get_video.flv
Perl Audio Converter - 4.0.3

error: encoding 'to' the following is not supported: avi

see 'pacpl --help' or 'pacpl --longhelp' for a list of options.

what can i do?have i to do anything else

You probably do not have the correct codec installed.  PACPL (like most converters in Linux or windows) is simply a front end for various codecs used to convert files.  The codec for converting video is ffmpeg so in order to use PACPL you must have the codecs installed.  Most likely you do not have ffmpeg (or some other codec) installed that PACPL needs.  The easiest way to get the codecs is to add the medibuntu repository to your sources.list then install the "Ubuntu Restricted Extras".  

To add the medibuntu repository (://help.ubuntu.com/community/Medibuntu)
Open a terminal and write or copy/paste the following at the prompt:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```
Add the GPG key by writing or copy/paste the following at the prompt:
```
sudo apt-get update && sudo apt-get -y install medibuntu-keyring && sudo apt-get update

```
Close the terminal.
Open Synpatic (menu>system>administration>Synaptic, search for the "ubuntu restricted extras" (URE) and install.  The URE does contain nonfree (as in they do not release the code not as in free beer) codecs so you will be required to accept the license - go ahead and accept (unless you are opposed).

Once the URE are installed try PACPL again.

Let me know if that works.

---

### Post by ali-zi-zeperto on 2009-02-09
i do everything you say step by step and try again to convert this file after installation but it doesn`t work and reply result above.i enter pacpl -f in terminal and put result in this file.i think this can help you and me more.
[http://www.4shared.com/file/85254216/29914f51/pacpl.html]("http://www.4shared.com/file/85254216/29914f51/pacpl.html")
thank you for your attention

---

### Post by cozmicharlie on 2009-02-09
> **ali-zi-zeperto said:**
> i do everything you say step by step and try again to convert this file after installation but it doesn`t work and reply result above.i enter pacpl -f in terminal and put result in this file.i think this can help you and me more.
[http://www.4shared.com/file/85254216/29914f51/pacpl.html]("http://www.4shared.com/file/85254216/29914f51/pacpl.html")
thank you for your attention

OK - I see the problem.  I don't use PACPL for encoding to avi so I was not familiar with it's capabilities when it comes to avi.  It appears avi is supported for decoding but not encoding.  So you will not be able to use pacpl to encode to avi.  You have a couple options though.  One is the program I mentioned winff.  Two other programs that will work are Handbrake and devede.  I am not sure if Handbrake is available via Synaptic but devede is.  If you search the forums you will find a how-to for installing Handbrake. 

I hope this helps

---

### Post by pmontini on 2009-02-10
Hello everyone, great guide, but I am having a problem converting wma to ogg.

This is the error message I get:

Can't locate object method "tags" via package "Audio::WMA" at /usr/bin/pacpl line 2180

any ideas?

I installed the .deb file from sourceforge...

I installed all the codecs I could find in Synaptic as well as ID3 taggers.

thanks in advance.

---

### Post by cozmicharlie on 2009-02-10
> **pmontini said:**
> Hello everyone, great guide, but I am having a problem converting wma to ogg.

This is the error message I get:

Can't locate object method "tags" via package "Audio::WMA" at /usr/bin/pacpl line 2180

any ideas?

I installed the .deb file from sourceforge...

I installed all the codecs I could find in Synaptic as well as ID3 taggers.

thanks in advance.

Thank you for the kind words.

Are you trying to write tags into wma files?  Check and see if you have libaudio-wma-perl installed.  You can check via synaptic or look in /usr/share/perl5/Audio/wma.pm.  If it is not installed, install it from Synaptic.

---

### Post by chosenhandle on 2009-02-17
I am having a strange little problem doing a mass convert of my flac files. All of my flac files are in /media/music/flac. I want to convert all of them to 320 mp3 located in /media/music/mp3. I have tried a variety of variations on the following command:

pacpl --to mp3 --bitrate 320 -r -p /media/music/flac/* --outdir /media/music/mp3

The program converts the files, but does not create new subdirectories in mp3 folder. Rather, it drops them directly into mp3 folder.Attempts to convert one folder at a time (replace * with folder name) also returns the same result.

I have tried variations on pathing (no * etc) but with little luck. Here is the strange part. i know it will do it. I did it on another occasion with another folder full of music. Once again, I played with the format and it worked one time. Maybe I should have paid attention to what I did to get it to work, huh?

Any advice is appreciated.

---

### Post by cozmicharlie on 2009-02-20
> **chosenhandle said:**
> I am having a strange little problem doing a mass convert of my flac files. All of my flac files are in /media/music/flac. I want to convert all of them to 320 mp3 located in /media/music/mp3. I have tried a variety of variations on the following command:

pacpl --to mp3 --bitrate 320 -r -p /media/music/flac/* --outdir /media/music/mp3

The program converts the files, but does not create new subdirectories in mp3 folder. Rather, it drops them directly into mp3 folder.Attempts to convert one folder at a time (replace * with folder name) also returns the same result.

I have tried variations on pathing (no * etc) but with little luck. Here is the strange part. i know it will do it. I did it on another occasion with another folder full of music. Once again, I played with the format and it worked one time. Maybe I should have paid attention to what I did to get it to work, huh?

Any advice is appreciated.

First you must create the directory.  PACPl should tell you:
mkdir /media/music/mp3

You also do not need the * in the comand.
This should work for you:
pacpl --to mp3 --bitrate 320 -r -p /media/music/flac --outdir /media/music/mp3

---

### Post by chosenhandle on 2009-02-21
thanks for the help! What I now realize from your post is that the pacpl -r -p will work fine for a mass convert...that is I only need to create the "mp3" directory and it will create all subdirectories. I suppose that is why I was to make it work earlier...I was doing the intial mass conversion.

Now I only want to convert one subdirectory at a time (as I add new CD's). It sounds as if I will have to manually create the directory in the mp3 directory first.

Thanks again.

---

### Post by cozmicharlie on 2009-02-21
> **chosenhandle said:**
> thanks for the help! What I now realize from your post is that the pacpl -r -p will work fine for a mass convert...that is I only need to create the "mp3" directory and it will create all subdirectories. I suppose that is why I was to make it work earlier...I was doing the intial mass conversion.

Now I only want to convert one subdirectory at a time (as I add new CD's). It sounds as if I will have to manually create the directory in the mp3 directory first.

Thanks again.

Yes - you will have to create them.

---

### Post by borisz264 on 2009-02-27
I have a problem like the one mentioned above when converting my WMAs to MP3s. Here's the output:

```
Total files converted: 0, failed: 0

Total files converted: 0, failed: 0

Total files converted: 0, failed: 0
Perl Audio Converter - 4.0.4

Converting:  [Slide (dc1761897).wma] -> [mp3] Can't locate object method "tags" via package "Audio::WMA" at /usr/bin/pacpl line 2205.


```
I checked, and the library suggested above is already installed

---

### Post by cozmicharlie on 2009-03-01
> **borisz264 said:**
> I have a problem like the one mentioned above when converting my WMAs to MP3s. Here's the output:

```
Total files converted: 0, failed: 0

Total files converted: 0, failed: 0

Total files converted: 0, failed: 0
Perl Audio Converter - 4.0.4

Converting:  [Slide (dc1761897).wma] -> [mp3] Can't locate object method "tags" via package "Audio::WMA" at /usr/bin/pacpl line 2205.


```
I checked, and the library suggested above is already installed

Can you please post one of the files you are having the problems with?

Thanks

---

### Post by wickedsten on 2009-04-10
> **borisz264 said:**
> I have a problem like the one mentioned above when converting my WMAs to MP3s. Here's the output:

```
Total files converted: 0, failed: 0

Total files converted: 0, failed: 0

Total files converted: 0, failed: 0
Perl Audio Converter - 4.0.4

Converting:  [Slide (dc1761897).wma] -> [mp3] Can't locate object method "tags" via package "Audio::WMA" at /usr/bin/pacpl line 2205.


```
I checked, and the library suggested above is already installed

Try the following: in cosole, type

```
sudo perl -MCPAN -e "install Audio::WMA"
```

This was helpful for me.

---

### Post by logos34 on 2009-05-06
I'm trying to use it in Amarok.

How do you specify variable bitrate (VBR) mp3 output?  The only popup dialog boxes I get are bitrate and sampling freq, and output dir.

oggs -> mp3 are coming out CBR

---

### Post by cozmicharlie on 2009-05-07
> **logos34 said:**
> I'm trying to use it in Amarok.

How do you specify variable bitrate (VBR) mp3 output?  The only popup dialog boxes I get are bitrate and sampling freq, and output dir.

oggs -> mp3 are coming out CBR

Unfortunately you can't - there is no popup to set -eopts etc

---

### Post by logos34 on 2009-05-07
> **cozmicharlie said:**
> Unfortunately you can't - there is no popup to set -eopts etc

can I edit a .conf file somewhere?  Or maybe the /usr/share/pacpl script file?

---

### Post by cozmicharlie on 2009-05-08
> **logos34 said:**
> can I edit a .conf file somewhere?  Or maybe the /usr/share/pacpl script file?

There is no conf file but you can edit the script itself.

---

### Post by logos34 on 2009-06-03
I just ripped out 4.0.4 and installed 4.0.5...The amarok script works ok (sluggish to start, but I'm using gnome), but there's no response to pacpl on command line...'man pacpl' pulls up man page though

??

running 64-bit

---

### Post by cozmicharlie on 2009-06-03
> **logos34 said:**
> I just ripped out 4.0.4 and installed 4.0.5...The amarok script works ok (sluggish to start, but I'm using gnome), but there's no response to pacpl on command line...'man pacpl' pulls up man page though

??

running 64-bit

I take it the 4.0.4 was working OK on your system?  I just upgraded mine to 4.0.6 and it worked fine.  You could try reinstalling then upgrading.  PACPL is now in the Juanty Universe repository - I installed it from there (it installs the older 4.0.3 version) then downloaded 4.0.6, untar the folder, open a terminal, change directories to the untarred pacpl folder, run ./configure, make , sudo make install in the terminal.  I did not remove the old version prior to upgrading.

I hope this helps.

---

### Post by logos34 on 2009-06-03
> **cozmicharlie said:**
> I take it the 4.0.4 was working OK on your system?  I just upgraded mine to 4.0.6 and it worked fine.  You could try reinstalling then upgrading.  PACPL is now in the Juanty Universe repository - I installed it from there (it installs the older 4.0.3 version) then downloaded 4.0.6, untar the folder, open a terminal, change directories to the untarred pacpl folder, run ./configure, make , sudo make install in the terminal.  I did not remove the old version prior to upgrading.

I hope this helps.

I tried the 4.0.5...I got it to respond at the command line, but it's *really sluggish*...I'll do 'pacpl -l' or 'pacpl -r' and I can see my cpu go to 100% as it starts up...takes about 10 secs to output...Same for older versions...followed the INSTALL.  Even tried the 4.0.5.all.deb...no diff...And then it fails almost every attempt to transcode to ogg...although it succeeded for the most part with aac->mp3, wav>mp3, mp3>aac, etc.  Checked the codecs.conf and pacpl.conf...hmm

Maybe it just doesnt run well on 64-bit environment

---

### Post by SuperSonic4 on 2009-06-03
> **logos34 said:**
> I tried the 4.0.5...I got it to respond at the command line, but it's *really sluggish*...I'll do 'pacpl -l' or 'pacpl -r' and I can see my cpu go to 100% as it starts up...takes about 10 secs to output...Same for older versions...followed the INSTALL.  Even tried the 4.0.5.all.deb...no diff...And then it fails almost every attempt to transcode to ogg...although it succeeded for the most part with aac->mp3, wav>mp3, mp3>aac, etc.  Checked the codecs.conf and pacpl.conf...hmm

Maybe it just doesnt run well on 64-bit environment

It works OK for me although it uses a lot of CPU 2, have you specified a encoder to use and/or ran the mod-install-kubuntu script? Dolphin integration works without any problems.

Encoding from mp3 to ogg works well on my pc. I converted a bon jovi song with ```
pacpl -t ogg --channels 2 --oggqual 4 Life.mp3
```

I did have to fetch all the dependencies from the AUR when installing it on arch and then compiling it myself

---

### Post by logos34 on 2009-06-03
> **SuperSonic4 said:**
> It works OK for me although it uses a lot of CPU 2, have you specified a encoder to use and/**or ran the mod-install-kubuntu script**?

yep.  and for ./configure used --without--konq --without-dolphin

(i'm using gnome ddesktop)

---

### Post by cozmicharlie on 2009-06-03
> **logos34 said:**
> I tried the 4.0.5...I got it to respond at the command line, but it's *really sluggish*...I'll do 'pacpl -l' or 'pacpl -r' and I can see my cpu go to 100% as it starts up...takes about 10 secs to output...Same for older versions...followed the INSTALL.  Even tried the 4.0.5.all.deb...no diff...And then it fails almost every attempt to transcode to ogg...although it succeeded for the most part with aac->mp3, wav>mp3, mp3>aac, etc.  Checked the codecs.conf and pacpl.conf...hmm

Maybe it just doesn't run well on 64-bit environment

so just to be sure - your other post states you did use the script (mos-install-kubuntu) and installed all the dependencies?  Audio decoding does take cpu but it should not require that much.  I will email the developer and see if he has any suggestions.

---

### Post by logos34 on 2009-06-03
> **cozmicharlie said:**
> so just to be sure - your other post states you did use the script (mos-install-kubuntu) and installed all the dependencies?  Audio decoding does take cpu but it should not require that much.  I will email the developer and see if he has any suggestions.

yes, mod-install-kubuntu.sh in the extras dir (can't remember if any were need though...Nothing in history...I'm doing a lot of compiling recently so its all blurred)

---

### Post by cozmicharlie on 2009-06-04
> **logos34 said:**
> yes, mod-install-kubuntu.sh in the extras dir (can't remember if any were need though...Nothing in history...I'm doing a lot of compiling recently so its all blurred)

Can you provide the output of 'time pacpl -l' or 'time pacpl -h' just actually see how fast it's starting up.

---

### Post by logos34 on 2009-06-04
sorry, too late, I uninstalled it already...but i'd guestimate ~10 secs

---

### Post by r00tDemon on 2009-06-13
when converting from m4a to mp3 I get the following errors
```
pacpl -v --to mp3 /media/Music -r -k -o m4a -p --outdir /media/Music
``````

Converting:  [04 Hand In My Pocket.m4a] -> [mp3] 

 *********** Ahead Software MPEG-4 AAC Decoder V2.6 ******************

 Build: Oct  8 2008
 Copyright 2002-2004: Ahead Software AG
 http://www.audiocoding.com            
 Floating point version                

 This program is free software; you can redistribute it and/or modify
 it under the terms of the GNU General Public License.               

 **************************************************************************

/media/Music/Alanis Morissette/Jagged Little Pill/04 Hand In My Pocket.m4a file info:

LC AAC  221.511 secs, 2 ch, 44100 Hz

title: Hand In My Pocket
artist: Alanis Morissette
writer: Music by Alanis Morissette and Glen Ballard. Lyrics by Alanis Morissette.
album: Jagged Little Pill                                                        
genre: Rock                                                                      
track: 4                                                                         
totaltracks: 13                                                                  
date: 1995                                                                       
compilation:                                                                     
tempo: 00000 BPM                                                                 
tool: iTunes v4.6.0.15, QuickTime 6.5.1                                          
iTunNORM:  000005EA 00000628 00003004 0000327A 000296DE 0002D71B 00007BF3 00007A85 000189E0 000193D9
iTunes_CDDB_IDs: 13+F1AD9A1C1C6423A027F939E7F0B9F94E+671303                                         

  ---------------------
 | Config:  2 Ch       |
  --------------------- 
 | Ch |    Position    |
  --------------------- 
 | 00 | Left front     |
 | 01 | Right front    |
  --------------------- 

Decoding /media/Music/Alanis Morissette/Jagged Little Pill/04 Hand In My Pocket.m4a took:  0.00 sec.   infx real-time.                                                                                        
INFILE: /media/Music/Alanis Morissette/Jagged Little Pill/04 Hand In My Pocket.m4a                     
Could not find "/media/Music/Alanis Morissette/Jagged Little Pill/04 Hand In My Pocket.24523.wav".     
encode failed with exit status: 256

```

Im running kubuntu 9.04

---

### Post by r00tDemon on 2009-07-18
Fixed my problem, realized I needed root privileges to edit that drive even though I have user set in fstab

---

### Post by pooja on 2009-09-03
I can't convert an mp3 to m4a. I'm attaching a picture of the error I'm getting in my Terminal (Ubuntu 9.04 Gnome DE).
Please help if you can.

---

### Post by r00tDemon on 2009-09-03
You need to install the lame mp3 encoder in order to convert to/from mp3 format

---

### Post by pooja on 2009-09-03
Thank you! I installed the "lame" package via Synaptic. Then I tried converting and everything went smooth. However I expected it to shrink much more than what it actually did - initial mp3 was 4.7 MB, the converted m4a is 4.5 MB. It's not bad, mind me, however in Vista, with a proprietary software, it would have come down to approximately 1.5-2.5 MB. 
Any suggestion on how I may improve the compression of the mp3?

---

### Post by r00tDemon on 2009-10-09
look under the man files for pacpl there are a number of options that can decrease the output file size. Many of these options will also increase the time it takes to encode the files.

---

### Post by nadian on 2009-11-04
Brand new baby Ubuntu user: this may be a simple question but could you have a look at my post at [http://ubuntuforums.org/showthread.php?t=1313338](http://ubuntuforums.org/showthread.php?t=1313338) and tell me what I'm doing wrong. Trying to convert all files in 160gb folder (created in windows originally) that are wma into mp3 .  fixed issue by using a different media plaer that recognises filetype

---

### Post by aashutosh on 2009-11-23
I am facing the same problem of error 256 for caf/wav conversion. I have checked all the sndfile programs are installed properly [They show encode/decode 'y' with pacpl -f command]. Can anyone pls help me? Its urgent.

---

### Post by r00tDemon on 2009-11-23
Try running pacpl with the sudo command. I got that message on a partition where i did not have write permissions and needed to be root.

---

### Post by aashutosh on 2009-11-24
> **r00tDemon said:**
> Try running pacpl with the sudo command. I got that message on a partition where i did not have write permissions and needed to be root.

Thanks for your quick response. I have all the permission, I had logged in as a root. Here are few more details 
[COLOR=Lime]
[COLOR=SeaGreen]root@ip-XX-XX-XX-XX:~# pacpl --verbose
Perl Audio Converter - 4.0.5[/COLOR][/COLOR]

AND

[COLOR=SeaGreen]root@ip-XX-XX-XX-XX:~# pacpl -f

Perl Audio Converter - 4.0.5

EXT       E   D   ENCODER         DECODER         TAG-READ   TAG-WRITE
----------------------------------------------------------------------
aac       Y   Y   faac            faad               N          N
ac3       Y   Y   ffmpeg          mplayer            N          N
aif         Y   Y   sox             sox                N          N
aiff        Y   Y   sox             sox                N          N
ape       Y   Y   mac             mac                N          N
asf        N   Y                   mplayer            N          N
au         Y   Y   sox             sox                N          N
avi        N   Y                   mplayer            N          N
avr        Y   Y   sox             sox                N          N
bonk      Y   Y   bonk            bonk               N          N
caf         Y   Y   sndfile-convert sndfile-convert    N          N
cdr        Y   Y   sox             sox                N          N
divx      N   Y                   mplayer            N          N
fap        Y   Y   sndfile-convert sndfile-convert    N          N
fla         Y   Y   flac            flac               Y          Y
flac        Y   Y   flac            flac               Y          Y
flv         N   Y                   mplayer            N          N
ircam     Y   Y   sndfile-convert sndfile-convert    N          N
la           Y   Y   la              la                 N          N
lpac       Y   Y   lpac            lpac               N          N
m4a       Y   Y   faac            faad               Y          Y
m4b       Y   Y   faac            faad               N          Y
m4v       N   Y                   mplayer            N          N
mat        Y   Y   sndfile-convert sndfile-convert    N          N
mat4      Y   Y   sndfile-convert sndfile-convert    N          N
mat5      Y   Y   sndfile-convert sndfile-convert    N          N
mkv       N   Y                   mplayer            N          N
mmf       Y   Y   ffmpeg          ffmpeg             N          N
mov       N   Y                   mplayer            N          N
mp2       Y   Y   ffmpeg          ffmpeg             N          N
mp3       Y   Y   lame            lame               Y          Y
mp4       Y   Y   faac            faad               Y          Y
mpc       Y   Y   mppenc          mppdec             Y          Y
mpeg     N   Y                   mplayer            N          N
mpg       N   Y                   mplayer            N          N
mpp       Y   Y   mppenc          mppdec             Y          Y
nist        Y   Y   sndfile-convert sndfile-convert    N          N
nsv        N   Y                   mplayer            N          N
nuv       N   Y                   mplayer            N          N
ofr        Y   Y   ofr             ofr                N          N
ofs       Y   Y   ofs             ofs                N          N
ogg      Y   Y   oggenc          oggdec             Y          Y
ogm     N   Y                   mplayer            N          N
pac      Y   Y   lpac            lpac               N          N
paf       Y   Y   sndfile-convert sndfile-convert    N          N
psp       N   Y                   mplayer            N          N
pvf       Y   Y   sndfile-convert sndfile-convert    N          N
qt        N   Y                   mplayer            N          N
ra        Y   Y   ffmpeg          ffmpeg             N          N
ram       N   Y                   ffmpeg             N          N
raw       Y   Y   sox             sox                N          N
rm        Y   Y   ffmpeg          mplayer            N          N
rv        N   Y                   mplayer            N          N
sd2       Y   Y   sndfile-convert sndfile-convert    N          N
sf        Y   Y   sndfile-convert sndfile-convert    N          N
shn       Y   Y   shorten         shorten            N          N
smk       N   Y                   mplayer            N          N
smp       Y   Y   sox             sox                N          N
snd       Y   Y   sox             sox                N          N
spx       Y   Y   speexenc        speexdec           Y          Y
svcd      N   Y                   mplayer            N          N
tta       Y   Y   ttaenc          ttaenc             N          N
vcd       N   Y                   mplayer            N          N
vob       N   Y                   mplayer            N          N
voc       Y   Y   sox             sox                N          N
w64       Y   Y   sndfile-convert sndfile-convert    N          N
wav       Y   Y   mv              cp                 N          N
wma       Y   Y   ffmpeg          ffmpeg             Y          N
wmv       N   Y                   mplayer            N          N
wv        Y   Y   wavpack         wvunpack           Y          Y

encode formats: 49 --- decode formats: 70[/COLOR]



Please help, I am not understanding what am I doing wrong.

Thanks Again.

---

### Post by r00tDemon on 2009-11-24
what command are you using to give the error? what other information does it print out with the error and the -v switch?

---

### Post by aashutosh on 2009-11-24
> **r00tDemon said:**
> what command are you using to give the error? what other information does it print out with the error and the -v switch?


I am using the following command 

[COLOR="Green"]root@X.X.XX.X~#pacpl -t wav record.caf [/COLOR]

Perl Audio Converter - 4.0.5

Converting:  [record.caf] -> [wav] decode failed with exit status: 256


Total files converted: 0, failed: 1


Thanks a lot

---

### Post by r00tDemon on 2009-11-24
can your try the following command and copy/paste the resulting error to give me more detail to the problem. thank you.
```
[COLOR=Green]pacpl -v -t wav record.caf[/COLOR]
```

---

### Post by aashutosh on 2009-11-24
[B]Hi r00tDemon, 

Can you please help on this? It's very urgent. 

I tried using sndfile-convert directly to convert caf file to wav file but this also didn't work. I tried using sndfile-convert in the following manner

[email]root@xx.xx.xx.xx[/email]~#sndfile-convert <encoding> record.caf record.wav

I tried this with all possible <encoding>(and of course with empty) but nothing worked.

Thanks in advance.




[/B]

---

### Post by aashutosh on 2009-11-25
Your code part didn't appeared in the first load of the page.

Below was the response for the mentioned command

[email]root@ip-XX.XX.XX.XX[/email]:~/pacpltesting# pacpl -v -t wav record.caf
Perl Audio Converter - 4.0.5

Converting:  [record.caf] -> [wav]

Not able to open input file /root/pacpltesting/record.caf.
Supported file format but unsupported encoding.
decode failed with exit status: 256


Total files converted: 0, failed: 1

---

### Post by aashutosh on 2009-11-26
Please help, I am still struggling.

---

### Post by discord on 2010-02-27
I'm facing the issue also going flac -> aac



> I'm having trouble encoding aac's from my flac files. I believe there is a bug.

I've tried the following:

$ pacpl --to aac  -r -o flac --outdir /tmp /home/discord/Music/flac/

Converting:  [01 - Air - Do The Joy.flac] -> [aac] encode failed with exit status: 256


> Also note that the aacqual option does not seem to work:

$ pacpl --to aac --aacqual 196 -r -V -o flac --outdir /tmp --dryrun /home/discord/Music/flac/

debug: ffmpeg   -y -i "/tmp/Björk-Debut-12-Play_Dead.9261.wav" -ab 128.k -ar 44100 -ac 2 "/tmp/Björk-Debut-12-Play_Dead.aac"

removed temporary file: /tmp/Björk-Debut-12-Play_Dead.9261.wav


Converting:  [07 Moon 83.flac] -> [aac] 

debug: flac  -f -d "/home/discord/Music/flac/B52's/07 Moon 83.flac" -o "/tmp/07 Moon 83.24947.wav"

debug: ffmpeg   -y -i "/tmp/07 Moon 83.24947.wav" -ab 128.k -ar 44100 -ac 2 "/tmp/07 Moon 83.aac"

removed temporary file: /tmp/07 Moon 83.24947.wav

$ pacpl --to aac --aacqual 450 -r -V -o flac --outdir /tmp --dryrun /home/discord/Music/flac/

>I don't know why the manual for pacpl states the default value is 300 when it seems to be 128K. As you probably already know, the -ab option in ffmpeg specifies the bitrate.

>I found and tried a fix mentioned on the ubuntu forums, but it didn't work for me:


>Here is a fix for the "encode failed with exit status: 256" error message.
>
>I was getting the "encode failed with exit status: 256" error message when trying to convert flac to m4a to use on my >ipod. The problem was that pacpl is passing the wrong command line options to ffmpeg, as the --verbose option >reveals (see output below). The fix is to edit line 2036 of /usr/bin/pacpl to read
>
>case /mp4|m4a|m4b/ { return "-title \"$tag_name{title}\" -track \"$tag_name{track}\" -author \"$tag_name{artist}\" ->album \"$tag_name{album}\" \"$tag_name{comment}\" -year \"$tag_name{year}\""; }
>
>(all one line). ffmpeg is expecting single dashes for options, "author" instead of "artist", and has no genre field. 


 Bug report here: [https://bugs.launchpad.net/ubuntu/+source/pacpl/+bug/533111?comments=all](https://bugs.launchpad.net/ubuntu/+source/pacpl/+bug/533111?comments=all)

---

### Post by pooja on 2010-02-28
Hi everybody,
I solved all my problems by installing Sound Converter. It's in the Ubuntu Software Center (*Applications > Ubuntu Software Center > Sound & Video*). You drag any YouTube video in it, choose the appropriate format (.ogg, .mp3, .flac, .m4a, .wav) and click *Convert*. That's it!
Hope this helps.

---

### Post by nosh276 on 2010-11-20
I'm also having trouble. :(

I've read the entire thread and I still can't seem to get my audio conversion to work.

mp3 -> mp4 

I've tried both using the command line and using the Konqueror plugin. I tried to use Amarok, but it doesn't play well with Ubuntu Netbook--or at least not with mine.

Any help?:confused:


EDIT: I can't use Sound Converter because it doesn't convert to mp4

---

### Post by TheArchedOne on 2012-03-04
I'm having problems using using pacpl. I'm trying to convert various file fromats to mp3, e.g. m4a to mp3 as follows:

```
pacpl -t mp3 -r -o m4a -v /data/music/
```

But I get the following error message:

```
Perl Audio Converter - 4.0.5

error: could not find suitable application to encode: mp3
```

pacpl -f shows the following:

```
Perl Audio Converter - 4.0.5

EXT       E   D   ENCODER         DECODER         TAG-READ   TAG-WRITE
----------------------------------------------------------------------
aac       Y   Y   faac            faad               N          N
ac3       Y   Y   ffmpeg          mplayer            N          N
aif       Y   Y   sox             sox                N          N
aiff      Y   Y   sox             sox                N          N
ape       Y   Y   mac             mac                N          N
asf       N   Y                   mplayer            N          N
au        Y   Y   sox             sox                N          N
avi       N   Y                   mplayer            N          N
avr       Y   Y   sox             sox                N          N
bonk      Y   Y   bonk            bonk               N          N
caf       Y   Y   sndfile-convert sndfile-convert    N          N
cdr       Y   Y   sox             sox                N          N
divx      N   Y                   mplayer            N          N
fap       Y   Y   sndfile-convert sndfile-convert    N          N
fla       Y   Y   flac            flac               Y          Y
flac      Y   Y   flac            flac               Y          Y
flv       N   Y                   mplayer            N          N
ircam     Y   Y   sndfile-convert sndfile-convert    N          N
la        Y   Y   la              la                 N          N
lpac      Y   Y   lpac            lpac               N          N
m4a       Y   Y   faac            faad               Y          Y
m4b       Y   Y   faac            faad               N          Y
m4v       N   Y                   mplayer            N          N
mat       Y   Y   sndfile-convert sndfile-convert    N          N
mat4      Y   Y   sndfile-convert sndfile-convert    N          N
mat5      Y   Y   sndfile-convert sndfile-convert    N          N
mkv       N   Y                   mplayer            N          N
mmf       Y   Y   ffmpeg          ffmpeg             N          N
mov       N   Y                   mplayer            N          N
mp2       Y   Y   ffmpeg          ffmpeg             N          N
mp3       Y   Y   lame            lame               Y          Y
mp4       Y   Y   faac            faad               Y          Y
mpc       Y   Y   mppenc          mppdec             Y          Y
mpeg      N   Y                   mplayer            N          N
mpg       N   Y                   mplayer            N          N
mpp       Y   Y   mppenc          mppdec             Y          Y
nist      Y   Y   sndfile-convert sndfile-convert    N          N
nsv       N   Y                   mplayer            N          N
nuv       N   Y                   mplayer            N          N
ofr       Y   Y   ofr             ofr                N          N
ofs       Y   Y   ofs             ofs                N          N
ogg       Y   Y   oggenc          oggdec             Y          Y
ogm       N   Y                   mplayer            N          N
pac       Y   Y   lpac            lpac               N          N
paf       Y   Y   sndfile-convert sndfile-convert    N          N
psp       N   Y                   mplayer            N          N
pvf       Y   Y   sndfile-convert sndfile-convert    N          N
qt        N   Y                   mplayer            N          N
ra        Y   Y   ffmpeg          ffmpeg             N          N
ram       N   Y                   ffmpeg             N          N
raw       Y   Y   sox             sox                N          N
rm        Y   Y   ffmpeg          mplayer            N          N
rv        N   Y                   mplayer            N          N
sd2       Y   Y   sndfile-convert sndfile-convert    N          N
sf        Y   Y   sndfile-convert sndfile-convert    N          N
shn       Y   Y   shorten         shorten            N          N
smk       N   Y                   mplayer            N          N
smp       Y   Y   sox             sox                N          N
snd       Y   Y   sox             sox                N          N
spx       Y   Y   speexenc        speexdec           Y          Y
svcd      N   Y                   mplayer            N          N
tta       Y   Y   ttaenc          ttaenc             N          N
vcd       N   Y                   mplayer            N          N
vob       N   Y                   mplayer            N          N
voc       Y   Y   sox             sox                N          N
w64       Y   Y   sndfile-convert sndfile-convert    N          N
wav       Y   Y   mv              cp                 N          N
wma       Y   Y   ffmpeg          ffmpeg             Y          N
wmv       N   Y                   mplayer            N          N
wv        Y   Y   wavpack         wvunpack           Y          Y

encode formats: 49 --- decode formats: 70
```

Does anyone know how I can fix the issue.

---

