---
title: "Archiver suggestion"
date: 2007-01-22
forum: The Cafe
---

### Post by Giorgio tani on 2007-01-22
Hi, I hope that this general discussion forum is the appropriate place for suggesting a new application to try.
I'm the author of an archiving software released under LGPL, PeaZip, hosted on SourceForge: [http://sourceforge.net/projects/peazip/](http://sourceforge.net/projects/peazip/)
It's released for Linux and for Windows and it is developed in Lazarus/FreePascal, making it quite easy to be ported to platforms supported by this IDE.
PeaZip acts as graphic frontend for:
- my Pea executable (included in the package), supporting my .PEA archive format (supports split archives, fast deflate based compression, authenticated EAX-AES encryption and redundant integrity checks) and file split/join
- Myspace's POSIX port of 7z (included in the package), supporting 7Z, BZip2, GZip, TAR, ZIP and other mainstream formats (also reads RAR, CAB, ISO, DEB, RPM etc...)
For archive types supported through POSIX 7z, PeaZip 1.2 features a browser to explore archive's content, optionally in flat mode, and an advanced filtering mechanism allowing multiple inclusion and exclusion.
Job definition can be saved, to be used later in scripts or for learning how to use 7z and Pea from command line, and the user is given a detailed job log after each archiving or extraction operation, that can be saved for further inspection.
Linux precompiled version of the software is statically compiled with GTK2 and have the only dependency of libgdk_pixbuf library, then, you just have to unpack and run it from the path you prefer (even remote, or from removable media). An alternative version, statically compiled with GTK1 is available, but the former one is recommended for most desktop users offering more modern UI look&feel and more usable system dialogs.
I hope this software may meet the interests of some Gentoo users!
Giorgio Tani

---

### Post by Giorgio tani on 2007-02-05
1.3 update:
- added create, browse and extract support for PAQ8F and PAQ8JD formats;
- added in-archive add/update and delete feature for 7z-supported archive types

---

### Post by patrick295767 on 2007-02-05
Can your program split and create SFX for rar, ace, and zip ?
If not ?? :confused: 

--
file-roller
ark
xarchive

---

### Post by Giorgio tani on 2007-02-06
Hi, for creating SFX the program's frontend uses Myspace's p7zip POSIX port of 7-Zip; it creates a self extracting Win32 executable, with associated content compressed in 7z format.
It doesn't create zip, ace or rar SFX executables, only 7z ones (ace and rar creation is also subject to commercial license issues).
7z-SFX, for the moment, doesn't allow to be split (you could however split it with split feature in PeaZip, but you will need to rejoin volumes before being able to launch the SFX).
As for regards the ability to read Win32 executables, AFAIK p7zip it can read 7z-sfx only and NSIS installers, both types can be succesfully browsed (and extracted) through PeaZip's archive browser interface.
I hope the response may have been useful!
 Giorgio Tani

---

### Post by gangalee on 2007-02-10
How do I create a zip?
I can do it on my Dapper machine at work, but not at home?
Is it a plugin?

---

### Post by Giorgio tani on 2007-02-12
"How do I create a zip?
I can do it on my Dapper machine at work, but not at home?
Is it a plugin?"
Zip format is handled using POSIX-7z (see Myspace's [http://sourceforge.net/projects/p7zip/](http://sourceforge.net/projects/p7zip/) project), which is the 7z binary in /res/p7z subdirectory in PeaZip's dir; codecs used by 7z are *.so in /res/p7z/Codecs; all needed files are embedded in the program's package.

---

### Post by disturbedite on 2007-02-14
i understand that your program acts as a frontend to p7zip.  i'm looking for a frontend to (p)7zip and would like to know: does it supports all of 7zip's options or just some?

---

### Post by Giorgio tani on 2007-02-15
PeaZip frontend supports quite much of p7zip features and, if an ever finer-grained level of control is needed, it can export the command line which it would pass to POSIX-7z as plain text, to be edited as freely as possible as basis for scripts.
Through the GUI frontend for p7zip you can:
- create or update 7z supported archives (7z, 7z sfx with Win32 sfx modules, bz2, gz, tar, zip) with optional: volume spanning, encryption (with confirmation field for password check against typos), encryption of filenames and solid archiving (7z format only), set level of compression.
- open 7z supported archives (ARJ, CAB, CHM, CPIO, DEB, ISO, Java archives (JAR, EAR, WAR), LZH, NSIS installers, Open Office file types, RAR, RPM, Z), search and browse the archives, apply multiple inclusion and exclusion filters, add/update or delete in-archive objects, test archives etc...

Version 1.3 has also create/open support for paq8f and paq8jd archives and an extra package is available with FreeDesktop's standard .desktop files and instructions to add PeaZip to KDE's start menu and Konqueror's service menus.
More information on project's page on SourceForge: [http://peazip.sourceforge.net/peazip.html](http://peazip.sourceforge.net/peazip.html)
I hope you may find something useful in this project!

---

### Post by disturbedite on 2007-02-15
thanks for that response.  i think i will give it a try.  i like the fact that since it doesn't support *all* 7zip features you do this:

[quote=Giorgio tani]if an ever finer-grained level of control is needed, it can export the command line which it would pass to POSIX-7z as plain text[/quote]

do you have a deb package for ubuntu/kubuntu?

---

### Post by drdnl on 2007-02-15
Disk spanning doesnt work, it creates a file.zip.001 / file.zip.002 but the archive manager in gnome can't handle it (non standard?) only peazip. Program does look interesting, hope you can fix it.

-D

---

### Post by Omnios on 2007-02-15
Umm might be interesting to have a terminal launch for the program that would be possible for both root and user. Also a build in sudo mv or cp might  make it very desirable for novice users.  So  sort of a  higher functioning  zip  package manager.

---

### Post by Giorgio tani on 2007-02-16
> **disturbedite said:**
> thanks for that response.  i think i will give it a try.  i like the fact that since it doesn't support *all* 7zip features you do this:
Thank you for appereciating this! This is one of the key reasons why I started to code PeaZip; I choose to develope a quite simple GUI, offering intuitive access to fine-grained options but without cluttering it too much and offering instead easy way to save command line to edit it as you want and need for maximum felxibility.
It is not just an extra like in some programs where you have an extra edit field to enter command line parameters; I meant PeaZip to somewhat bridge the gap between console and GUI apps, higlighting most used functions in the UI and then letting the user save the command line as an example, if needed, to do better than the limited "AI" of the program does in composing the command line.
Moreover, I appreciate more the approach common in many console apps wich gives a more detailed report of the job than GUI counterparts, so I also focused on including detailed job logs wich can be saved to have a permanet report on most important operations.

> **disturbedite said:**
> do you have a deb package for ubuntu/kubuntu?
The application is autocontained (apart from dependency for libgdk_pixbuf library), it is meant to be deployed on mixed operating systems and mixed desktop environments, so it need just to be unpacked to run; that mens that it's also easy to use it from a network path or on a removable media, not needing to install it.
For system integration I written standard .desktop files wich can be used to easily add the application to Freedesktop-compliant environments (KDE, Gnome); this is presently on an extra package but will be better integrated and expanded in future PeaZip releases.

---

### Post by Giorgio tani on 2007-02-16
> **drdnl said:**
> Disk spanning doesnt work, it creates a file.zip.001 / file.zip.002 but the archive manager in gnome can't handle it (non standard?) only peazip. Program does look interesting, hope you can fix it.
-D

Hi, PeaZip has two distinct way to split/join volumes. 

When you are creating archives through POSIX-7z with volume spanning option, 7z split/join function will be used, in order to accomplish the work with a single command and a single pass on the input.
This function was is not the usual byte-split of the input, so it is not compatible with other applications than 7z (pros and cons of 7z volume spanning scheme are often discussed in 7-Zip SourceForge project's forums).

If you, instead, choose to split a file (select "split" in format combobox), which of course can be a previously created archive of any type, it will use my split implementation (pea executable in /res) wich is a plain byte-split so it should be compatible with any similar application; moreover, using that option, you can also specify an optional checksum or hash on the input (Adler, CRC32/64, MD5, SHA*, Ripemd, Whirlpool) which will be saved on a separate file (which will contain a record for each volume). In this way a third part application will join volumes just ignoring the checksum file, while joining volumes with PeaZip the checksum or hash will be checked for each volume, allowing to know, in case of problem, which volume(s) is(are) in error (very useful for spanned downloads).
Split/join operation will also check for free space on destination unit and ask for user input if disk is full, or if it's necessary to provide another removable unit with the next volume, in case you have spanned the input on multiple media.

---

### Post by Giorgio tani on 2007-03-05
Hi, today I released 1.4 update of PeaZip; now FreeDesktop_integration folder contains .desktop files and brief explanation to integrate the application in FreeDesktop compliant enviromnents (like Gnome and KDE), without needing an installable package (keeping the application standalone it's suitable to be used even on machines where system libraries should stay freezed).
Other news for this version are the frontend for QUAD (compression and extraction), frontend for Strip/UPX binaries compression and "TAR before" option available with all archiving/compression formats allowing to save input objects in a TAR archive before sending it to the compressor. It's very handy to improve usability of compression only formats, like GZip, BZip and QUAD.

---

### Post by dimeotane on 2007-03-09
Peazip looks really interesting.

can you give some beginner level instructions for installing it on ubuntu?

---

### Post by Giorgio tani on 2007-03-12
> **dimeotane said:**
> Peazip looks really interesting.
can you give some beginner level instructions for installing it on ubuntu?

Thanks for the appreciation!
PeaZip is a self contained application which has no external dependency (except for libgdk_pixbuf library on some systems), so to run it it's simply needed to extract the package and run the executable.
To integrate it in FreeDesktop compliant environments (like Gnome and KDE) some very simple instructions are given in FreeDesktop_integration folder, allowing to add the application as a compression application known by the system and to add shortcuts to most used functions (archive, browse archive, extract here, extract to a new folder) in service menus.
In this way the application can be easily moved on different paths or machines with minimal configuration operations to get the most from it, and (usually, unless libgdk_pixbuf library is missing) without need to instally anything in system's libraries (which is usually apreciated when changes on the system should be avoided or minimized).

---

### Post by rafalr on 2007-03-22
Hi Giorgio,

I just tested it on both Windose (at work) and Dapper (at home) and it works nice on either of them, both GUI and command line. I actually replaced what I had before on my Windows machine with your software permanently.

Two things I am (slightly) missing are:
- progress bar could be attached to GUI (when you compress with PAQ with setting 4 or higher it really takes time and resources, so you really want to know how far to go you still have ...)
- a more detailed instruction/template files to integrate with Gnome (native for Ubuntu), like you supplied for KDE.

I like simple and powerfull things like PeaZip.

rafal

---

### Post by Giorgio tani on 2007-03-22
Hi, thank you very much for the appreciation for PeaZip!

About the lack of a progress bar, it's quite problematic since indeed what the GUI wrapper does is launching the command line executable fit for the requested command and waiting for getting the output through a pipe. 
I'll work on it in the future hoping to can create something better, however a quick solution already feasible is to set the application to use binaries in console mode (in "Default settings"): in this way when the graphic frontend invokeds a binary (i.e. paq, 7z etc) it will run in its native console interface with its native progress indicator.

About the instructions and .desktop files for Gnome, I'm working on it. 
Soon I'll have a new primary test machine to test different modern Linux distros and I'll be able to give more detaild and up to date examples and instructions.

---

### Post by Biochem on 2007-04-05
Finally a GUI that support split archive. I was really missing that. 

However I use Feisty beta 64 bit and I get very weird visual output (see attached screenshot. There is always some part of the text missing and the missing part are changing randomly depending on the file I select. It makes it very hard to use.

---

### Post by Giorgio tani on 2007-04-06
> **Biochem said:**
> Finally a GUI that support split archive. I was really missing that. 
However I use Feisty beta 64 bit and I get very weird visual output (see attached screenshot. There is always some part of the text missing and the missing part are changing randomly depending on the file I select. It makes it very hard to use.
Hallo, thank you for trying PeaZip!
Could you try the PeaZip1.5_Linux_x86_GTK1.tar.gz version? *
GTK2 support in Lazarus, the IDE I use to develop PeaZip, is still experimental and may lead to visualization problems on some Linux platforms, so I'm presently always publishing both GTK1 and GTK2 releases for Linux.
I hope in future releases of the IDE the GTK2 support may become better and more mature so this sort of problems should no longer show up.

* GTK1 libraries are statically linked in _GTK1 PeaZip's package so you should not have to install anything new to run it even if it's a GTK1 application.

--edit--
by the way, as a last resort or if you want a pure archive/split/extract application: you can also disable archive browsing (disable "use archive browser" in default options); in that way you will not see archive's content but you will still be able to launch extract, test and list jobs.

---

### Post by Biochem on 2007-04-06
I just tried the GTK1 version but for some reason it won't start. 
In the terminal I get the fowllowing message:
```

/Desktop/PeaZip1.5_Linux_x86_GTK1$ ./peazip
./peazip: error while loading shared libraries: libglib-1.2.so.0: cannot open shared object file: No such file or directory

```
I installed libglib1.2 in synaptic but I still get the same message :confused:

Is my system missing something, or one of the static link broken?

---

### Post by Biochem on 2007-04-09
FYI Giorgio tani
I tried peazip on another compute, this time running Edgy 32bit (instead of Feisty 64bit). The GTK2 version was running fine, however the GTK1 still has the same problem.

---

### Post by Giorgio tani on 2007-04-10
About libglib-1.2 problem for _GTK1 version, that's strange: I'll look further in Lazarus/FPC documentation to see if they speak about some Debian-specific issues of compiled executables since I was not able to find hints about missing or misplaced libraries in the linking of the project.
And I'm going to use a plain (=whithout my development environment installed) Ubuntu 6.10 as primary machine for testing my future releases, so I hope to be able to spot out better those problems in future.

--- edit: by the way, I just updated PeaZip project releasing 1.6 version. You can see full changelog here: [http://sourceforge.net/project/shownotes.php?group_id=178996&release_id=499978](http://sourceforge.net/project/shownotes.php?group_id=178996&release_id=499978) ---

---

### Post by Giorgio tani on 2007-06-11
This weekend PeaZip 1.8 was released; main news are:
- added read support for ACE archives;
- p7zip frontend updated to version 4.47.1 (supports AES encrypted ZIP, faster and multithreaded Deflate/Deflate64...);
- various UI fixes (i.e. checkboxes in 1.7 misbehaving in Ubuntu);
- the program is now able to open files whith associated application, open dirs and URLs in Gnome and KDE...

Full changelog and release map on: [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

---

### Post by Ti-Paul on 2008-03-09
I have been looking for an archiver that could also SPLIT files...

I tried PeaZip, looks promising... But it seems that splitted files would be joined only with the same program???

It's bad that File-Roller & XArchiver don't support this usefully little task... :(

---

### Post by Giorgio tani on 2008-03-13
> **Ti-Paul said:**
> I have been looking for an archiver that could also SPLIT files...

I tried PeaZip, looks promising... But it seems that splitted files would be joined only with the same program???

It's bad that File-Roller & XArchiver don't support this usefully little task... :(

Hi, this wa discussed earlier in thread:

> **Giorgio tani said:**
> Hi, PeaZip has two distinct way to split/join volumes. 

When you are creating archives through POSIX-7z with volume spanning option, 7z split/join function will be used, in order to accomplish the work with a single command and a single pass on the input.
This function was is not the usual byte-split of the input, so it is not compatible with other applications than 7z (pros and cons of 7z volume spanning scheme are often discussed in 7-Zip SourceForge project's forums).

If you, instead, choose to split a file (select "split" in format combobox), which of course can be a previously created archive of any type, it will use my split implementation (pea executable in /res) wich is a plain byte-split so it should be compatible with any similar application; moreover, using that option, you can also specify an optional checksum or hash on the input (Adler, CRC32/64, MD5, SHA*, Ripemd, Whirlpool) which will be saved on a separate file (which will contain a record for each volume). In this way a third part application will join volumes just ignoring the checksum file, while joining volumes with PeaZip the checksum or hash will be checked for each volume, allowing to know, in case of problem, which volume(s) is(are) in error (very useful for spanned downloads).
Split/join operation will also check for free space on destination unit and ask for user input if disk is full, or if it's necessary to provide another removable unit with the next volume, in case you have spanned the input on multiple media.

That is, basically: if you create a split archive you need to handle it with the same application that created the spanned volume, since the spannig scheme is format-specific; in this case, you will need PeaZip or any other frontend application supporting archives split in 7z's way.
Instead, if you use the raw split utility of PeaZip, you will get the original data simply "cut" in volumes of specified sizes, with no changes in content or byte order, and you can simply just "stick" pieces back to obtain the whole file (using whatever method you prefer to merge files).

---

### Post by Ti-Paul on 2008-03-13
Thank you for not "blasting" me... I should have read it before posting my previous message...!

So currently, i'm using your software since it fill a missing gap for me (archiver/spliter on GUI)...

I've found the interface a little buggy (fonts misplaced/ugly, etc...) but as long as it do the job... :)

---

### Post by breaking on 2008-03-13
you should be able to get packages like zip in the ubuntu repo - ie: synaptic search for zip, ace ,etc.. you need them to decode the particular archive file. :)

---

### Post by bone2006 on 2009-03-22
64bit release and put in the repos and I'm sure there would be more use of this software.
64bit for windows is working and you can force it to be installed on Linux, but it would be nice to have a 64bit release and put on the repos

---

