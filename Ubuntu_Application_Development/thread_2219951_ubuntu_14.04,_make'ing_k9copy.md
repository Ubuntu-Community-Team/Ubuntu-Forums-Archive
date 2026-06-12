---
title: "ubuntu 14.04, make'ing k9copy"
date: 2014-04-26
forum: Ubuntu Application Development
---

### Post by squakie on 2014-04-26
I was looking at a thread in the multimedia & video forum about k9copy no longer being in the repositories, and that someone had tried an old version but it apparently didn't work as they wanted.  I checked and indeed it's not in the default repos anymore.  I installed kdevelop, which in turn installed much, if not all, of kde4.  I downloaded the source from sourceforge and unpacked it.  I'm not sure exactly how I did it, because I really don't understand the occumpaning readme, but I've gotten cmake to run and then running make it kicks out one error.  It appears, if I am following things correctly, that something has changed in avformat.h, which I believe is from libavformat-dev, which in turn I *think* is installed when ffmpeg is.  At any rate, the struct (??) of  "AVFormatParameters" is no longer defined.  I checked the avformat.h on my 14.04 system and "AVFormatParameters" is not there.

Here's the output from the latest make:```
dave@davelaptop:~$ cd Downloads
dave@davelaptop:~/Downloads$ ls
cm-10.1.3.2-encore.zip        k9copy-2.3.8-Source.tar.gz
cm-10.2.1-encore.zip          openrecovery-twrp-2.3.1.0-encore-signed.zip
Downloads.kdev4               TWRP_2.3.0.2-encore-1gb-sdimg.zip
gapps-jb-20130812-signed.zip  TWRP_2.3.0.2-encore-sdimg.img
k9copy-2.3.8-Source
dave@davelaptop:~/Downloads$ cd k9copy-2.3.8-Source
dave@davelaptop:~/Downloads/k9copy-2.3.8-Source$ cd build
dave@davelaptop:~/Downloads/k9copy-2.3.8-Source/build$ make
[  0%] Built target k9copy_automoc
[  0%] Built target k9copylib_automoc
[ 43%] Built target k9copylib
[ 43%] Building CXX object CMakeFiles/k9copy.dir/k9copy_automoc.o
In file included from /home/dave/Downloads/k9copy-2.3.8-Source/build/../src/import/k9chapteredit.h:18:0,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/moc_k9chapteredit.cpp:9,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/k9copy_automoc.cpp:15:
/home/dave/Downloads/k9copy-2.3.8-Source/build/../src/import/k9avidecode.h:32:91: error: ‘AVFormatParameters’ has not been declared
 typedef int (*av_open_input_file_t)(AVFormatContext **, const char *,AVInputFormat *,int, AVFormatParameters *);
                                                                                           ^
In file included from /home/dave/Downloads/k9copy-2.3.8-Source/src/mpeg2/kdecmpeg2.h:24:0,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/src/mpeg2/k9decodethread.h:20,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/src/mpeg2/k9plaympeg2.h:24,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/../src/main/k9cropselect.h:33,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/moc_k9cropselect.cpp:9,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/k9copy_automoc.cpp:41:
/home/dave/Downloads/k9copy-2.3.8-Source/src/mplayer/k9internalplayer.h:17:7: warning: ‘class k9InternalPlayer’ has virtual functions and accessible non-virtual destructor [-Wnon-virtual-dtor]
 class k9InternalPlayer {
       ^
make[2]: *** [CMakeFiles/k9copy.dir/k9copy_automoc.o] Error 1
make[1]: *** [CMakeFiles/k9copy.dir/all] Error 2
make: *** [all] Error 2
dave@davelaptop:~/Downloads/k9copy-2.3.8-Source/build$ 


```

Can anyone guide a novice in how to get around this?  Basically I just want to build k9copy from the latest source on sourceforge using the 14.04 libs, etc..  I can then try it out and see if it works as one of the posters in that thread wants it to.

Thank you in advance!!

---

### Post by andrew.46 on 2014-04-26
Looks like k9copy has been abandoned [since 2011]("http://k9copy.sourceforge.net/web/index.php/en/nouveautes/12-theend") with no sign of anybody else picking up the code and running with it. Author sounds a little disillusioned too :(. So it might be a difficult and perhaps thankless task to get it running under a modern distro...

---

### Post by squakie on 2014-04-26
Hummm, I *thought* I downloaded source that said 2013 - but I may be confusing that with something else I was downloading at the same time.  Vis searchmonkey I found the related problem seems to be only referenced in the header and a single source in src/import and in src/vamps (dealing with ffmpeg).  Do you know where I might be able to find out what was trying to be accomplished (I *think* it's either opening or reading an input stream) and what the syntax would be with libav now?

It's something I'm familiar with at all, and my C coding skills are almost non-existent now.  I think this all ties back to using ffmpeg calls to do some of the processing.  I don't have the skills to maintain something like this by a long shot, but I'd like to see if I can get it going in 14.04.

Here's the main reason:  apparently there is no other tool to just shrink a dvd9 to a dvd5 - the output still contains the menus, extras, etc., as the dvd9.

---

### Post by squakie on 2014-04-26
Ok, further "looking" finds it the open input av stream call, and according to something I found on the net it has been deprecated and a different call is recommended and I think that was over 2 years ago!).  So, I'm assuming the libav "stuff" has changed accordingly, and hence why AVFormatParameters isn't defined now.  I'd like to change it over to the new call for av open stream, but I'll just be guessing at what to do to actually accomplish it.  At least it's only in 2 headers and 2 pieces of code out of the entire base for k9copy.

If anyone has any familiarity with programming using the ffmpeg libs (thus including libav, etc.), I could REALLY use some help here.  I really don't know what I'm doing! ;) ;)

---

### Post by squakie on 2014-04-27
Well, this gets just more interesting!  I found a copy of the definition of the AVFormatProperties structure online so I temporarily put it in my avformat.h file.  Got past those 2 errors on the compilation, but now more have started showing up - more libav/ffmpeg calls.  Adding the struct definition should not have really made any difference in terms of run-time, as all the author was doing was passing NULL on that value anyway.  It just purely needed to be defined just so it would compile.  I may take some time to look at that more yet, but I have a suspicion that the code hasn't been maintained because of some change in ffmpeg a while back (years?) that started causing all of these "old version" calls to bomb out in compilation.

BTW - I did try dvd95 myself in 14.04 since it is supposed to shrink a dvd9 to a dvd5, but I could not get it to work.  Know good dvd - both pre-testing and post-testing - yet it gives read errors.  Tell it to continue and ignore read errors and it immediately bombed out.  

So, don't know what the deal is with that, but I'll keep trying to make k9copy compile even though I don't know what the heck I'm doing.

---

### Post by squakie on 2014-04-27
Searching the net it appears that the code was written either to use old ffmpeg calls or an older version of libav, for which enough time has gone by that the deprecated items have actually been removed in the current libraries.  I have absolutely NO idea where to even start on something like that.

If someone could pick this up and let me know I'd appreciate it.

Thanks!

---

### Post by squakie on 2014-04-27
Okay,now I *think* I'm starting to see the picture.  K9copy was originally developed using ffmpeg.  The came the split where libav was born, and since Ubuntu supports libav, the long-story short version is that now I have the libav version of avformat.h instead of the ffmpeg one, and k9copy relies on the ffmpeg one.  So to be supported in Ubuntu it appears it would need to be converted to libav from ffmpeg.  But that also means the maintainer would have to "restrict" the project to Ubuntu, or maintain 2 sets of code for other distros that use ffmpeg.  No wonder it isn't supported anymore, and no wonder the developer of k9copy is disillusioned.

So, with that in mind, what all is involved to modify code from using ffmpeg to using libav?  I think that is my immediate question to solve the problem.  I temporarily got rid of the problem and was able to build against 14.04 and run ok by using a copy of avformat.h that I found on the net that was supposedly posted by MIT.  I have NO clue about any of these things, but I'm going to do the dangerous thing and assume that it is the ffmpeg avformat.h.  All I know is that it has the structures and the members to structures that k9copy needs to compile.


I have no idea how to do this myself.  My programming skills now are marginal at best.  Any help would be greatly appreciated   Hopefully there is some way to do this using ifdef's or something such that a single code base can be maintained.

---

### Post by squakie on 2014-04-28
I am closing this thread as the problem is not k9copy per se - it's the result of the conflict a few years ago in the ffmpeg community that resulted in the libav project instead, and in Debian/Ubuntu not including ffmpeg nor supporting in any way ffmpeg.

I have opened another post with a more fitting title and a more fitting request for info since k9copy is a victim, not a problem.

---

### Post by Sef on 2014-04-28
Closed by OP's request.

---

