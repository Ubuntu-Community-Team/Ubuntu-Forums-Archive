---
title: "trusting trust: a strange result."
date: 2016-02-09
forum: Security
---

### Post by Patrick_Van_Esch on 2016-02-09
Hello,

I had some fun recently trying to apply the technique of diverse double  compiling, and the result I obtained would indicate that the gcc  compiler is corrupted.  I don't believe that as for now, but I don't  explain the result.

To set the stage, I looked at this: [ACSAC paper]("http://www.codingforums.com/redirect-to/?redirect=http%3A%2F%2Fwww.acsa-admin.org%2F2005%2Fabstracts%2F47.html") Countering Trusting Trust through Diverse Double-Compiling  which is a technique which could answer the catch-22 of a corrupted  compiler, as explained and demonstrated historically by Ken Thompson in  his seminal paper:
[https://www.ece.cmu.edu/~ganger/712....1-thompson.pdf]("http://www.codingforums.com/redirect-to/?redirect=https%3A%2F%2Fwww.ece.cmu.edu%2F%7Eganger%2F712.fall02%2Fpapers%2Fp761-thompson.pdf")

I set forth to do the opposite: not to try to recompile gcc with another  compiler, tcc, as suggested, but by recompiling tcc by tcc, as tcc is  much much simpler to compile than gcc, and is said to be self-compiling  as it should.

I first tried the thing on a recent Ubuntu install, and because I had  difficulties, I went downloading the old ubuntu server installer of  Dapper (ubuntu 6.06 LTS) [Ubuntu 6.06.2 LTS (Dapper Drake)]("http://www.codingforums.com/redirect-to/?redirect=http%3A%2F%2Fold-releases.ubuntu.com%2Freleases%2Fdapper%2F")

and installed the x86 server installer in virtualbox.

I downloaded the tcc source from [Index of /releases/tinycc]("http://www.codingforums.com/redirect-to/?redirect=http%3A%2F%2Fdownload.savannah.gnu.org%2Freleases%2Ftinycc%2F")

I installed the gcc and build-essential and texinfo packages on my virtual machine.

I built and installed tcc (version 0.9.26) exactly as described in the  README file (all standard options), using ./configure, make, make test  and sudo make install.  All this went smoothly.

Of course, now I had compiled the tcc source with gcc of the Dapper  installation, this was not tcc compiled by itself.  But as I had a  working binary tcc install now, I could re-build tcc again, but this  time using tcc itself.

This is done by cleaning out the directory with make clean, and using:
./configure --cc=tcc
followed by make, make test, and make install.

Of course, as the tcc source was now compiled with tcc and not with gcc,  it is normal that we obtained ANOTHER binary of tcc (it is the output  of a different compiler: tcc instead of gcc).  So that the binaries were  different was no surprise.

But here comes the strange part: I set apart all the *.o, *.a, the lib  and the tcc executable in another directory, and I cleaned out the  directory AGAIN, and I recompiled the tcc suite AGAIN using tcc.

Note the subtlety:  the first time, I compiled the tcc suite using tcc,  but which had been built by gcc.  The second time, I used the result of  that, tcc built with tcc, to build the tcc suite.

In principle, I was expecting identical binaries.  It turns out that the  *.o files resulting from this second tcc compilation, are indeed  identical, but the strange thing is that the executable, tcc, resulting  from this, is DIFFERENT.

Still stranger: I installed this tcc over the former tcc, and when I  rebuilt the tcc suite AGAIN, a third time, this time, the binaries are  identical.

This is, according to the DDC test, the indication of a tampered binary  of a compiler if one doesn't find any other indication.  With my tin  foiled hat on, I would say: there's a backdoor in the gcc binary since  at least 2006 (Dapper) !  Of course, I think there's something else  that's wrong, but I wouldn't know what.

Here are the byte lengths of the different versions:

tcc executable (A) from tcc suite compiled with gcc: 385632 bytes

tcc executable (B) from tcc suite compiled with (A):  489020 bytes

tcc executable (C) from tcc suite compiled with (B): 486564 bytes

tcc executable (D) from tcc suite compiled with (C): 486564 bytes

C and D are byte by byte identical.

I was expecting, if gcc didn't have any back door using the DDC test, that B, C and D should be identical.

The OBJECT files *.o from the compiled suites B C and D are, however,  identical, so it is tcc as a linker that is the cullprit apparently.  

Note that the *.a files are different, but that is normal as the *.a  files contain the file dates, and the object files are of course created  at different moments.  But as they are made by up of identical object  files, that shouldn't really matter.  They have identical lengths  between the B, C and D versions, and they differ with A, as expected:

libtcc1.a has length 40020 and libtcc.a has length 511102 in version A,  and they have length 29670 respectively 474498 in versions B, C and D.

This is pretty puzzling.  Anybody an idea what can explain the  difference between the executable between version B (tcc compiled with  tcc which had been compiled with gcc) and versions C and D ?

The reason why this shouldn't happen is the following.

Consider that you have a source code S in language L which describes a  program that, say, takes text files as input, and puts out a text file  that is the alphabetic list of words in the input file, one per line.   Normally, the source code S and the language definition L determine  perfectly the output file O.txt that one should obtain, if one gives it  an input file I.txt.   
If one compiles the source code S with a compiler C1 to obtain an  executable E1, and one compiles the source code with a compiler C2 to  obtain an executable E2, then of course, E1 and E2 will be different  executables.  Their performance can differ.  But they should be  *semantically* equivalent: executable E1 should take the text file I.txt  and produce an output O.txt, and executable E2 should take text file  I.txt and produce output O.txt, because that is what the source code S  and the language definition L specify !  If the executable does other  things than the source code indicates, then the executable is not a  correctly compiled executable of that source code and language.

Now, in my test, the source code S is the source code of tcc, and is  written in C.  It is the source code of a compiler, that is, a program  that takes source code I.txt, and produces a binary executable O.txt.
If I compile source code S with two different compilers, namely, gcc,  and tcc, I should of course obtain different binaries, but these  binaries are both executables that should do what the source code S  (here, the source code of tcc) and language L (here, C) tells it to do.
If I apply these two different executables to the same input I.txt  (here, the source code of tcc), I expect the same output (the generated  binary of tcc).  The fact that the two binaries (B) and (C) are  different responses to the two different executables E1 and E2 (in my  exercise, versions A and B of tcc executable), indicates that E1 and E2  cannot be both correct executables corresponding to the same source code  S.

So my question is: what happens ?  I have difficulties thinking this is a genuine security issue in the gcc compiler, but if not, what is it ?

Can a linker (here, tcc) which has been compiled with two different compilers, but from the same source code, generate different executables from the same object files without something fishy going on ?

PS: btw, I had posted a very similar message to codingforums.com, but it didn't get any replies, so maybe this place is more suited.

---

### Post by matt_symes on 2016-02-09
Hi

This may seem like a factious question, it's not intended to be, but have you looked at the differences ?

Did you really build it in dapper drake ?  

Kind regards

---

### Post by Patrick_Van_Esch on 2016-02-09
I didn't look at the differences.  That would be the next step, by analysing the differences in the executables, by reverse engineering them.  But that's a lot of work, and I'm just a beginner at that.  My point was that there shouldn't be any differences, but maybe I'm wrong there on the principle.  If tcc were non-deterministic, then I shouldn't have obtained identical versions in C and D, but they are byte-wise identical (looked at it with diff).

Yes, I really built it in a server version of Dapper (and I did it over in Warty and Breezy, although one should edit the Makefile there, because they have make version 3.80 and not 3.81 (which came out in 2006, and included in Dapper).  Versions 3.80 and earlier do not support the "else ifeq" construction (according to the change log on [http://ftp.gnu.org/gnu/make/](http://ftp.gnu.org/gnu/make/) ).
I installed it, that is, in VirtualBox (version 5).

I did it with a 32 bit version, and a 64 bit version (all "server" installs, to have light installations).

Of course I first did it on my current actual trusty install, but I was hesitant to use the install on my system and the install in a local directory doesn't work very well.  So I first ran it on a ubuntu 13.10 virtual machine with which I'm playing (the last install that has the shell shock bug), and I saw a difference.  So I wanted to look at old gcc versions, from the time before tcc was well-known through David A. Wheeler's work.

There are a few tricks one has to apply when installing these old ubuntu installs, because some hang as they cannot contact the repositories which are now not anymore us.archive.ubuntu.com but old-releases.ubuntu.com.  So one first has to disable networking in the virtual machine, do an install like that, edit the /etc/apt/sources.list file, restore the networking function in /etc/network/interfaces.  The reason is that although gcc and build-essential are on the .iso file, texinfo isn't (which is needed for the standard install of tcc), and has to be downloaded from the server.

Also, I had to run the installers with the noapic option, and modify the storage settings in some cases.

But I have up and running servers now of warty, breezy and dapper, both in 32 bit and 64 bit.  I re-did the exercise on several of them, and always I find different executables of tcc with a tcc compiled with gcc, and tcc made with tcc compiled with tcc.
On warty and breezy, I have difficulties running the test suite (but not the compilation and the installation).  On dapper, everything works smoothly.

It might very well be - I hope so, and I think so - that there's something I don't understand of the loader process that causes these differences.  But Wheeler didn't mention it in his article when doing the opposite (compiling gcc with tcc, which is much harder to do).  But I would like to understand.

---

### Post by matt_symes on 2016-02-09
Hi

There's no need to start reverse engineering the .text section.

Start by checking the section and elf header sizes.

Kind regards

---

### Post by Patrick_Van_Esch on 2016-02-10
> **matt_symes said:**
> Hi

There's no need to start reverse engineering the .text section.

Start by checking the section and elf header sizes.

Kind regards

I will look into it as far as I can do so.

In the mean time, I repeated the exercise more or less under Windows (8.1).  

I took the binary version of tcc from [http://download.savannah.gnu.org/releases/tinycc/](http://download.savannah.gnu.org/releases/tinycc/), which I suppose has been compiled by the gcc compiler in mingw (although I'm not sure).

I took also the source files from the same site, and I copied the binary of tcc and its dll into the win32 directory.
By modifying the .bat file to use this tcc binary as a compiler, and not the specified x86_64-pc-mingw32-gcc compiler, I succeeded in compiling tcc with the tcc-binary I downloaded.
I assume that I can take the downloaded binary as the tcc-version A in my opening post, and the newly compiled tcc from the source, with that binary, as the tcc-version B.
Next, I did this over, but with this time the newly produced tcc-version B as the compiler, to produce yet another binary (and its dll): version C.

This time, B and C are (almost) identical.  In fact, the tcc.exe (version B) and tcc.exe (version C) are identical byte by byte, and the corresponding DLL differ only by 2 bytes.  I think that this is due to the two different names that I gave them (one was libtcc_new.dll (B) and the other one was libtcc_nex.dll).  When I pick names of different lengths, a whole bunch of bytes in the second one is shifted by one or two bytes as compared to the first one, so this is why I took two names of equal length.

The binaries B and C, which are essentially identical, are totally different from A.

So in this windows environment, things happen as I supposed they had to happen.

tcc.exe versions B and C are 8704 bytes long and identical ;
libtcc_new.dll versions B and C are 228 352 bytes long (and differ on two bytes - most probably due to the name as one of the two bytes corresponds indeed to the ASCII codes of the different letter in the names)

The original tcc.exe binary (version A) which I suppose was compiled with the mingw compiler, is 17 408 bytes long, and the corresponding libtcc.dll (version A) is 133 120 bytes long.

I didn't recompile them myself I have to say.

This is just to illustrate that under windows, the postulated property of David A. Wheeler, seems to hold.

(it is true that to be entirely correct, I should have compiled the source of tcc with the mingw compiler myself, but I had some difficulties doing so).

---

### Post by Patrick_Van_Esch on 2016-02-11
Comparing the two original tcc versions by looking at the symbol tables with nm, I find the following:

everything is identical (in numerical order), until this point:

tcc version B:
[INDENT]0000000008082100 T __libc_csu_fini
0000000008082140 T __floatundisf
** 0000000008082180 T __floatundidf**
00000000080821c0 T __floatundixf
00000000080821f0 T __fixunssfdi
0000000008082260 T __fixunsdfdi
00000000080822d0 T __fixunsxfdi
0000000008082330 T __va_start
0000000008082370 T __va_arg
0000000008082400 T __va_copy
0000000008082430 T __va_end
[/INDENT]
 
and in the tcc version C I have:[INDENT]0000000008082100 T __libc_csu_fini
0000000008082140 T __floatundisf
**00000000080821af T __floatundidf**
000000000808221e T __floatundixf
0000000008082286 T __fixunssfdi
0000000008082370 T __fixunsdfdi
0000000008082464 T __fixunsxfdi
0000000008082524 T __va_start
00000000080825c6 T __va_arg
00000000080826f7 T __va_copy
000000000808275f T __va_end 
[/INDENT]

of course the list is much much longer...   This happens for the first time about 1/3 of the symbol table.

Concerning the symbols themselves, they are almost identical, but there is a difference here:

< 000000000809c880 B last_ind
< 000000000809c87c B last_line_num
< 00000000080997b0 B last_text_section
---
> 000000000809cac0 B last_ind
> 000000000809cabc B last_line_num
> 00000000080999f0 B last_text_section
844,846d846
[B]< 00000000080825d0 r .LC0
< 00000000080825d4 r .LC2
< 00000000080825d8 r .LC4[/B]
858,860c858,860
< 000000000809978c B loc
< 0000000008099818 B local_label_stack
< 00000000080997f8 B local_stack
---
> 00000000080999cc B loc
> 0000000008099a58 B local_label_stack
> 0000000008099a38 B local_stack
867,868c867,868
< 0000000008088de8 B macro_ptr
< 0000000008088e28 b macro_ptr_allocated
---
> 0000000008089028 B macro_ptr
> 0000000008089068 b macro_ptr_allocated

The LC0 2 and 4 symbols appear only in the B version.

I don't know if this is relevant...

I still don't understand, in principle, how the same program source code, compiled with two different compilers (gcc, and tcc itself) can give rise to two executables which produce different outputs when presented with the same input.

---

### Post by Patrick_Van_Esch on 2016-02-12
Ok, I found the culprit.

Out of the tcc suite come two pieces of binary code: the tcc executable, and the libtcc1.a library.  These are the two executable binaries which are installed in the system when the make install instruction is given.
Apparently, tcc, when used as a linker, COPIES parts of the installed libtcc1.a library in the executable it produces.  This is somewhat sneaky, because this library is not specified anywhere explicitly on the linker line.

As such, the compilation output of tcc is "one time behind" on this part of binaries copied from libtcc1.a, because it is binary code compiled by the grand parent, and not its FUNCTION but literally the binary code.

I checked this as follows.  For this example, I had installed an archlinux on Virtualbox (KDE Plasma 5.3.2, Qt 5.4.2, kernel 4.0.7-2-ARCH, 64 bit).  The reason for this is that archlinux has a rather remote parentship with ubuntu, so if there was any compromise of one branch of binaries, there's more diversity by using another branch.

From the (rather complex) makefile that comes with the tcc installation, I distilled 4 rather simple shell scripts:
one that produces tcc from gcc (makegcc.sh), one that produces tcc from the installed tcc (maketcc.sh) and then a funny one where the object files are produced by tcc, but I use the gcc loader (maketccgcc.sh).  There I had to include libtcc1.a or there were unresolved symbols: exactly those where the symbol tables diverged in a previous post.
This hinted me that there's something misunderstood with this libtcc1.a library.  The 4th script was a bare bones install script.  I made shell scripts instead of make, because I got hesitant about the order in which make did things, and wanted to keep full control.

So, when I did the arborescence:
tcc (A) and libtcc1.a (A) compiled with gcc, I had the following byte lengths for these: 757360 and 15668 respectively.
installing them, and compiling the source again with tcc (A), I had:
tcc (B) and libtcc1.a (B), with byte lengths 671612 and 9126 respectively.
installing them, and compiling the source again with tcc (B), I had:
tcc (C) and libtcc1.a (C) with byte lengths 666144 and 9126 respectively.
again, compiling with tcc (C) I had:
tcc (D) and libtcc1.a (D) with byte lengths 666144 and 9126 respectively.

==> as before under Dapper: the DDC test doesn't seem to work because B and C are different (although C and D are equal).

If I started all over by compiling again with gcc, and installing tcc (A) and libtcc1.a (A) again, and this time:
compiling with tcc (A) but linking with gcc and the earlier locally compiled libtcc1.a, I had:

tcc (X) and libtcc1.a (X) with length 482008 and 9126 respectively.

Installing tcc (X), and again compiling with tcc (X) but linking with gcc, I had:

tcc (Y) and libtcc1.a (Y) with lengths 482008 and 9126 respectively, IDENTICAL to X.

==> If I use the gcc linker and the locally newly compiled library libtcc1.a, the DDC test seems to work out all right.

And now comes the trick: if we compile and LINK now with the installed tcc (Y) and libtcc1.a (Y), then we obtain:

tcc (Z) and libtcc1.a (Z), with lengths 666144 and 9126 respectively, which are identical to C and D.

==> at this point, it seems that the tcc linker passes the DDC test.

If now, we compile again with gcc to obtain version A, and then we compile again with tcc A to obtain tcc (B) and libtcc1.a (B) and we ONLY install libtcc1.a (B), but we keep tcc (A) in the system, and we compile tcc again with this, we obtain directly versions C = D = Z.

This is entirely consistent with tcc, when linking, COPYING binary code from the installed libtcc1.a library.

Indeed, the version (B) is then a hybrid piece of binary code: the objects are compiled by tcc, but during the linking phase, binary code from the installed libtcc1.a (A) is copied directly into the output, and libtcc1.a was made with gcc.  As such, it shouldn't surprise us that (B) is different from (C), where during its compilation the installed libtcc1.a is now version B which is tcc output.

The hypothesis for the DDC test, that the code that is put out by the compiler is *computed* by the execution of the compiler on the source code (and this computation is defined by the source code), didn't hold, because tcc *copied* a piece of its own binary code* (namely from libtcc1.a) in the output.

So, after correcting for this "one time late", as I did in the last step, by using the newly compiled libtcc1.a before using the linker, the DDC test shows that there's nothing wrong.

---

