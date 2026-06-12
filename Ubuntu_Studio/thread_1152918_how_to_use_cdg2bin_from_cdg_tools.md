---
title: "how to use cdg2bin from cdg tools"
date: 2009-05-08
forum: Ubuntu Studio
---

### Post by alejobar on 2009-05-08
Hi I'm trying to create a karaoke cd from my mp3+cdg files in my ubuntu Hardy computer. I download CDG Tools [http://www.kibosh.org/cdgtools/]("http://www.kibosh.org/cdgtools/"), after reading it said that there's no need to install them, just untar and click the tools to use them, ok I can open cdgtools but when I try to use cdg2bin I choose run in terminal and terminal opens and closes by itself, I don't know what I'm doing wrong, could someone help me please?

---

### Post by alejobar on 2009-05-09
Oh C'me on! nobody? really?

---

### Post by disturbed1 on 2009-05-11
It's as simple as running the program with -h and following the directions :)

```

./cdg2bin.py -h
Usage: cdg2bin.py [options] <file1> [fileN [ ... fileN]]

After any appropriate program options, list files to be added to the CD+G disc.
They will be placed on the disc in the order provided on the command line.
Files can be any combination of tar.gz, tar.bz2, .zip, .mp3+cdg, .ogg+cdg, and
.wav+cdg. For .mp3+cdg and .ogg+cdg, specify either the CDG file or the sound
file; cdg2bin will find the matching file.

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -o NAME, --output-prefix=NAME
                        Output filename prefix to use when creating files; "-o
                        foo" produces "foo.toc" and "foo.bin" files
  -s, --split-image     Produce individual .bin images for each track instead
                        of a single .bin image for the whole disc
  -r, --raw             Produce raw data instead of cooked data (cooked data
                        is the default)
  -b, --byte-swap       Swap byte order while processing audio.
```Maybe your archive did not have the **_*README*_** file included? I'll quote it for you.

> 
CDG2BIN QUICK START

To create your own custom CD+G discs with files stored on your machine, use
cdg2bin to create a disc image and cdrdao to write it to a CD-R. cdg2bin's
command-line syntax is straightforward:

$ cdg2bin.py [options] <files>

You must pass at least one CD+G track to cdg2bin to create a disc image. To
provide a CD+G track, specify one of the track's two files (the .cdg graphic
data file or the .mp3/.ogg audio data file), or specify a .zip, .tar.gz, or
.tar.bz2 archive that contains a single pair of files for a track). Archives
are handled automatically and transparently.

Given this directory of files:

track01.cdg    track01.ogg    track02.zip    track03.tar.bz2

With track02.zip containing:

track02.cdg    track02.mp3

And track03.tar.bz2 containing:

track03.cdg    track03.mpg

You can create a three track disc with either of the following commands:

$ cdg2bin.py track01.cdg track02.zip track03.tar.bz2
$ cdg2bin.py track01.ogg track02.zip track03.tar.bz2

(note you can use the CDG or audio file to specify a track -- cdg2bin
automatically locates the appropriate matching file based on your
specification)

Wildcards can also be used to easily create a multiple-track disc from every
track stored in a directory:

$ cdg2bin.py /home/user/karaoke/dk97/*zip

The index file produced (suffixed with .txt) is a plain text file listing the
CDG filenames placed on the disc (in the order they appear on the disc). It can
be used to keep track of the disc's contents, or removed; cdrdao does not use
or need this file to record discs.

cdg2bin needs write access to the directory(ies) where your source files are
stored if they are archives. It also naturally needs write access to the output
directory (the current directory if not specified with the -o option).

---------------------------------------------------------------------------

CDG2BIN COMMAND LINE OPTIONS

With no options, cdg2bin will create an image file named cdg.bin, a cue sheet
named cdg.toc, and an index file named cdg.txt. It uses appropriate
byte-swapping for little-endian machines (x86 and AMD64) to produce big-endian
audio data as required by the redbook audio specification.

Use the -o or --output-prefix= option to specify the name of the output files:

$ cdg2bin.py -o MYDISC001 /home/user/karaoke/dk97/*zip
$ cdg2bin.py --output-prefix=MYDISC001 /home/user/karaoke/dk97/*zip

This produces MYDISC001.bin, MYDISC001.toc, and MYDISC001.txt instead of cdg.bin, cdg.toc, and cdg.txt.

Use the -s or --split-image option to write each track into its own individual
.bin file. A single .toc cue sheet will still be created that correctly
specifies each of these individual .bin files:

$ cdg2bin.py -s /home/user/karaoke/dk97/*zip
$ cdg2bin.py --split-image /home/user/karaoke/dk97/*zip

Use the -b or --byte-swap option to change how audio data is produced by the
MP3 decoder (the OGG Vorbis decoder always produces the correct, big-endian
output, regardless of platform). If your CD images show correct graphics but
play static, use this option to generate a new image and record the disc again.

Use the -r or --raw option to write raw R-W subchannel data instead of cooked
R-W subchannel data (the default). If your recorder cannot record a CD with
cooked data, use this option to produce raw output. The .toc cue sheet is
written properly to reflect which data scheme is used.

---------------------------------------------------------------------------

---

### Post by EHamp10 on 2009-08-11
Following the help file and README instructions noted by disturbed1, in addition to the following Requirements from the README file:

> 

Requirements for cdg2bin:

 * Python
 * lame (for decoding MP3 files)
 * oggdec (for decoding OGG files)


I get the following results:
```

Noob420@Linux-Desktop:~/Karaoke/cdgtools-0.3.2$ dir
cdg2bin.py   cdgcddb.py  cdggui.py    cdgrip.py    README
cdg2text.py  cdgdao.py	 cdgparse.py  cdgtools.py
Noob420@Linux-Desktop:~/Karaoke/cdgtools-0.3.2$ cdg2bin -o Name001 /home/Noob420/Karaoke/*cdg
bash: cdg2bin: command not found
```


Help. :confused:

---

### Post by kiboshed on 2009-09-21
[FONT=monospace]Hi,

You need to include the extension (.py) and add a dot slash before the program name:

[/FONT]```
./cdg2bin.py <Options Here>
```Hope that helps.

---

