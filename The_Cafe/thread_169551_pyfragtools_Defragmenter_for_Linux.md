---
title: "pyfragtools: Defragmenter for Linux"
date: 2006-05-02
forum: The Cafe
---

### Post by jdong on 2006-05-02
Hey, guess who got bored last weekend on a robotics trip and decided to write a Linux defragger? ;-)

A quote from the README:
```

defrag
==========

INTRO:

    Defrag is a set of scripts designed to measure and cope with filesystem fragmentation. Currently, it only consists of "defrag".
    
USAGE:
    
    Fragtool's syntax is:
    
    /usr/sbin/defrag [-h] [-n passes] [--passes n] [-t threshold] [--threshold n] [-a] [--analyze] [--help] path
    
    When invoked, defrag will analyze the given path recursively for file fragmentation and print out a summary of its findings. Next, it will ask you if you'd like to run any defragmentation passes.
    Fragtool also takes an optional passes argument, which makes it perform fully non-interactively. Positive number of passes will perform that many passes and exit, while zero passes will just print out the summary and exit.
    
==========
FAQ
==========

Q: A defragger? For Linux? Are you crazy?
A: No, I certainly am not. Under certain circumstances, even the most fragmentation-resistant filesystems get fragmented. Don't believe me? Look around with defrag. Whether or not filesystem performance is affected can be debatable at times, though I personally have to say that when a 300MB torrent is split into 5000 fragments, read speed is drastically affected.

Q: What filesystems is it compatible with?
A: Any filesystem that Linux can write to. The tool is pretty filesystem agnostic, but does require that filefrags be able to understand the layout of files.

Q: Is it safe to use?
A: Defrag works great in the author's extensive testing with all kinds of files. However, I cannot be certain that it does not damage your setup, so use with caution like any other fragmentation tool. As long as you use a journaling filesystem, the process is atomic. Before defragging a file, we make sure that it is not open for write access. Also, before doing the in-place replacement at the end of a defrag, we make sure again that the file has not changed. These are the same precautions that the tried-and-true xfs_fsr XFS defragger uses.

Q: Is it safe to interrupt?
A: Yes, defrag will safely clean up after itself. In the case of abrupt termination (SIGKILL, power off, etc), fragtools will leave behind ".defrag" temporary folders on the filesystem. They are owned by root with a mode of 000, and can be easily located and cleaned up using "find".

Q: Does it resume where it left off after an interrupt?
A: No. It doesn't. It sounds cool though.

Q: Is it effective?
A: Depends on the particular filesystem it is being used on. The defragmentation algorithm either fully defragments a file on the first try, get progressively better in subsequent passes, or is unable to make any improvement for infinite numbers of passes. Usually, if the file is not defragmented by the 10th pass, it's a lost cause. But in general, you will see improvements on fragmented filesystems. You will not see great improvements if you obsessive-compulsively run the defragger on the same set of files. Get a life.

Q: How many passes should I run?
A: Generally, anything from 5-10 passes is good. If it's not defragmented by then, chances are that your filesystem does not have enough contiguous free space to defragment the file. Go by what you feel is good after running the 5-10 passes.

Q: I run XFS. Should I use this, or xfs_fsr?
A: If you are interested in defragmenting, use xfs_fsr. It is faster by orders of magnitude, not to mention that it is production-tested. If you would like to get fragmentation statistics, defrag is the perfect tool to get that.

Q: If you think this is so great, why hasn't anyone else written a defragmenter for Linux?
A: Others indeed have. A user at forums.gentoo.org wrote a perl fragmentation checker, and Con Kolivas wrote a bash script defragger. Fragtool was inspired by both of these efforts, and aims to intelligently combine the two to perform the task more intelligently (i.e. do not try defragmenting defragmented files, do not make fragmentation worse than before, etc).

```



Sample output:

```

jdong@jdong-laptop:~$ sudo defrag /usr/sbin
Building list of files to analyze... done!

Analyze finished. 1.0 % fragmentation (2 files), 13.3 average frags/MB
Fragmented files:
13.92   /usr/sbin/sshd
12.74   /usr/sbin/gdm
How many passes to run? [10]

111111111111111111111111111111111111111111111111111111111111
===> Pass 1 of 10 <===    Remaining Fragmentation 26/26 (100%)
111111111111111111111111111111111111111111111111111111111111


  Pass 1 of 10, 1/2 (50%): 13.9 frags/MB /usr/sbin/sshd
           301372 100%   23.29MB/s    0:00:00  (1, 100.0% of 1)                      Fully defragmented!

  Pass 1 of 10, 2/2 (100%): 12.7 frags/MB /usr/sbin/gdm
           246864 100%   51.04MB/s    0:00:00  (1, 100.0% of 1)                      Improved: (12.7 --> 8.5)

222222222222222222222222222222222222222222222222222222222222
===> Pass 2 of 10 <===    Remaining Fragmentation 8/26 (31%)
222222222222222222222222222222222222222222222222222222222222


  Pass 2 of 10, 1/1 (100%): 8.5 frags/MB /usr/sbin/gdm
           246864 100%   68.06MB/s    0:00:00  (1, 100.0% of 1)                      Fully defragmented!

333333333333333333333333333333333333333333333333333333333333
===> Pass 3 of 10 <===    Remaining Fragmentation 0/26 (0%)
333333333333333333333333333333333333333333333333333333333333


444444444444444444444444444444444444444444444444444444444444
===> Pass 4 of 10 <===    Remaining Fragmentation 0/26 (0%)
444444444444444444444444444444444444444444444444444444444444


555555555555555555555555555555555555555555555555555555555555
===> Pass 5 of 10 <===    Remaining Fragmentation 0/26 (0%)
555555555555555555555555555555555555555555555555555555555555


666666666666666666666666666666666666666666666666666666666666
===> Pass 6 of 10 <===    Remaining Fragmentation 0/26 (0%)
666666666666666666666666666666666666666666666666666666666666


777777777777777777777777777777777777777777777777777777777777
===> Pass 7 of 10 <===    Remaining Fragmentation 0/26 (0%)
777777777777777777777777777777777777777777777777777777777777


888888888888888888888888888888888888888888888888888888888888
===> Pass 8 of 10 <===    Remaining Fragmentation 0/26 (0%)
888888888888888888888888888888888888888888888888888888888888


999999999999999999999999999999999999999999999999999999999999
===> Pass 9 of 10 <===    Remaining Fragmentation 0/26 (0%)
999999999999999999999999999999999999999999999999999999999999


101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010
===> Pass 10 of 10 <===    Remaining Fragmentation 0/26 (0%)
101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010

========= COMPLETE ===========
Remaining Fragmented Files:
Frags/MB Before:         26.66
Frags/MB After:          0.00
Improvement:             100.0 %
===============================
jdong@jdong-laptop:~$ 

```


Attached is a tarball containing both debianized source code (written in Python) and a .deb package for simpler installation. There is only one file (defrag) that needs to be installed. It should be very safe to use (follows the trusted XFS defragger algorithm) on any filesystem, but I don't guarantee that it'll be flawless on every setup. Don't run passes over crucial data unless you have backups, I guess :)


The fragmentation numbers printed are in Frags/MB. I think that makes more sense than just counting fragments, so you don't spend time defragging huge files that will naturally be slightly fragmented.


Enjoy!


**Small Note**
Do _not_ obsessive-compulsively run passes trying to achieve perfection. By default, the defragger counts files with less than .5frags/MB as unfragmented. This can be overridden with the -t parameter. Do it wisely... If you try too hard to defrag, what will happen is that while files may defragment, free space will become fragmented in the process, which will ultimately lower write performance.

This is not a full defragmenter (i.e. free space consolidation, directory reorganization), but just a file defragger.



The source code is under the GPL, and you are welcome to play around with it. I'm open to suggestions and contributions. The working directory of the source archive is already a bzr 0.8 knits repository, so it's ready for decentralized commits.

I will be publishing the head branch as soon as I find a place to host it, as my system will not take the bandwidth hit and Launchpad supermirror does not support Knits yet.

---

### Post by TheCaptain on 2006-05-02
O&O has had a defragmenter for Linux for years, i tried it on servers, the database efficiancy went up by... 0%, not measurable.

You can try this out if you have a recent backup and a lot of time on your hands but the real reason one is not provided in ANY distro is that it's not needed, the improvements aren't measurable.

---

### Post by htinn on 2006-05-02
Hmm. Anything I need to install first?

```
ImportError: No module named bzrlib.osutils
```

---

### Post by TheCaptain on 2006-05-02
Oh, and XFS is in no way safe to run on PC hardware without a good UPS that will gently shut down your system, that goes for most other filesystems like it.

---

### Post by jdong on 2006-05-02
Well, on some mythtv setups, I have seen 100MB files with 7000+ fragments (ext3 & reiser), and at that point read performance degrades to the point that it can't keep up with burning to a 48x CD (approx 5MB/s, on a 40MB/s drive). A simple copy turned it down to 50 or so fragments, and read performance drastically improved.

That's why there's the built-in limit of 0.5frags/MB, which IMO should be even higher than that.

As far as system performance, unless you do something special that fragments up the disk (torrenting, mythtv, large downloads), you probably won't realize much, but it's always good to know you're ready for something like this, or if you're curious about fragmentation the analyze mode is great.

---

### Post by jdong on 2006-05-02
[QUOTE=htinn]Hmm. Anything I need to install first?

```
ImportError: No module named bzrlib.osutils
```[/QUOTE]

You may need to install bzr. I will try to remove that dependency... The progress bar was stolen from bzrlib :)

---

### Post by TheCaptain on 2006-05-02
[QUOTE=jdong]Well, on some mythtv setups, I have seen 100MB files with 7000+ fragments (ext3 & reiser), and at that point read performance degrades to the point that it can't keep up with burning to a 48x CD (approx 5MB/s, on a 40MB/s drive). A simple copy turned it down to 50 or so fragments, and read performance drastically improved.

That's why there's the built-in limit of 0.5frags/MB, which IMO should be even higher than that.

As far as system performance, unless you do something special that fragments up the disk (torrenting, mythtv, large downloads), you probably won't realize much, but it's always good to know you're ready for something like this, or if you're curious about fragmentation the analyze mode is great.[/QUOTE]

You're saying that simultaneous read/write from multiple users on a database server will not fragment like torrenting, mythtv, large downloads?

We had extreme fragmentation, the real world results of an O&O defragment were not measurable, thus we opted not to implement the function in the nightly runs.

Provide me with real world benchmarks and i'll trust that it will improve anything, for now it's just another way to potentially screw up my system with no real benefit to be had.

---

### Post by TheCaptain on 2006-05-02
If you are curious about fragmentation run fsck, if you are worried that it may affect your performance, install more memory, afaik the cache subsystem of Linux is second to none and VERY able to keep up with the demand of burning a cd or dvd, i'd say that burning a cd has more to do with the interface than the ability to deliver when it comes to write speed.

In 110% of the cases when a burn has to slow down it's because of the writer, the media or the interface, it's never ever because the HDD cannot read (while fully cached) as fast as the burner can write.

It's not generally known but a fast read doesn't flow to a fast write, both adds to the PCI bus by requests and usually blams the inferface with crap, this happens regardless of fragmentation and is why the QOS of SCSI interfaces is so much smoother, even though it has to be translated.

---

### Post by A-star on 2006-05-03
never mind my original question.
Nice tool, just what I needed to defrag my disk full of video files.

---

### Post by A-star on 2006-05-03
when I try to run the defrag I get following error message:
```
fruymen@star1:~$ sudo defrag /media/multimedia/
Building list of files to analyze... done!
Traceback (most recent call last):
  File "/usr/sbin/defrag", line 646, in ?
    run(opts[1][0], threshold, passes)
  File "/usr/sbin/defrag", line 549, in run
    pb = ProgressBar(show_pct=True, show_bar=True, show_spinner=True, show_eta=False)
  File "/usr/sbin/defrag", line 31, in ProgressBar
    return TTYProgressBar(to_file=to_file, **kwargs)
  File "/usr/sbin/defrag", line 214, in __init__
    from bzrlib.osutils import terminal_width
ImportError: cannot import name terminal_width

```

any idea how to solve this?
I already install bzr

---

### Post by jdong on 2006-05-03
I will be posting a newer version that does not have a bzrlib dependency soon.

---

### Post by asimon on 2006-05-03
Interesting, has anyone done some benchmarking before/after?

---

### Post by Engnome on 2006-05-03
Does it work in dapper?

---

### Post by asimon on 2006-05-03
[QUOTE=Engnome]Does it work in dapper?[/QUOTE]
Yes.

---

### Post by jdong on 2006-05-03
It works fine in Dapper; as I said before, I'll upload a non-bzrlib dependent version when I get home from school.

As far as benching, if someone would like to play with that, that'd be great. I don't currently have the time to.

Note that 90%+ of Linux users will never ever need a defragmenter. The rest, 99% of them will only need it after 1+ year of heavy use. Most people will never need to defragment; Linux does a superb job of maintaining great filesystem performance.

---

### Post by asimon on 2006-05-03
[QUOTE=jdong]It works fine in Dapper; as I said before, I'll upload a non-bzrlib dependent version when I get home from school.
[/quote]
BTW, under Dapper there is no bzrlib package at all, only bzr, which is enough to run pyfragtools.

---

### Post by jdong on 2006-05-03
Alright, the new tarball now does not require any bzr.

---

### Post by John.Michael.Kane on 2006-05-03
jdong is it possable to to have this for those who run 64bit?

Thanks.

---

### Post by jdong on 2006-05-03
Unpack the tarball and run sudo make install. The python script should work fine in 64-bit mode.

---

### Post by xXx 0wn3d xXx on 2006-05-03
This works great :) Is there a way I can keep apt-get from upgrading to the new version, since the new one doesn't work

---

### Post by Lovechild on 2006-05-03
causes a traceback on Fedora for me.. but you get an A for effort.

---

### Post by dmb on 2006-05-03
Wierd, apt wants to upgrade defrag. I think the program it wants to upgrade it to is not the same one here, its a completely diferent program, just with the same name. Maybe you should come up with a diferent name for it, or just call it pydefrag or something so it doesn't conflict with other packages.

---

### Post by NeghVar on 2006-05-03
Just go into synaptic and search for the program it wants to update to and lock the version on that so it won't ask for an update.

---

### Post by jdong on 2006-05-03
crap, didn't occur to me that there's already a defrag program. I'll revert the name back to 'pyfragtools' again.

For all of you that report this program doesn't work, can you post tracebacks or other error messages so I can take a look?

---

### Post by dmb on 2006-05-03
is 500 mb a bad number for fragmentation?  I keep running it, and it keeps going about 15 percent lower each time, right now its at 300 mb. Should i keep running it?

---

### Post by jdong on 2006-05-03
That number means that for every 1MB of the file, there are 500 fragments. That's fairly severe fragmentation which will show up as adverse read performance. Is it a large file?

---

### Post by dmb on 2006-05-03
Not, its total at the end. I decided to run the program in /usr.

---

### Post by bionnaki on 2006-05-04
I have an iriver h340 - basically an external harddrive media player that is formatted with fat32. it is a good idea to defrag the player every once in awhile, but since im using linux I havent been able to do so. will pyfragtools be able to drag this volume when it is mounted?

thanks

---

### Post by jdong on 2006-05-04
Yes; this tool is capable of defragging FAT32 volumes.

---

### Post by Lovechild on 2006-05-04
Building list of files to analyze... done!
/ /usr/sbin/ntpd            [                                        ]    0/284Traceback (most recent call last):
  File "/usr/sbin/defrag", line 647, in ?
    run(opts[1][0], threshold, passes)
  File "/usr/sbin/defrag", line 554, in run
    f=numfrags(file)
  File "/usr/sbin/defrag", line 532, in numfrags
    fragresult=subprocess.Popen(["filefrag",file],stdout=subprocess.PIPE).communicate()[0]
  File "/usr/lib64/python2.4/subprocess.py", line 542, in __init__
    errread, errwrite)
  File "/usr/lib64/python2.4/subprocess.py", line 975, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

---

### Post by jdong on 2006-05-04
Do you have filefrag, of e2fsprogs?

---

### Post by Lovechild on 2006-05-04
[QUOTE=jdong]Do you have filefrag, of e2fsprogs?[/QUOTE]

Ah.. I found the issue, they were present just not in path.

---

### Post by OffHand on 2006-05-05
I just tried to install the .deb from the package in your 1st post.
Right click > Open with GDebi Package Installer

```
A later version is available in a software channel

You are strongly advised to install the version from the software channel, since it is usually better supported.
```

I want to give this a try if you have fixed this. Thumbs up for your project though. =D>

---

### Post by jdong on 2006-05-05
Use the manual installer at this moment; I still haven't gotten around to renaming the package yet... :-/

---

### Post by kinematic on 2006-07-23
and just a tip if you do a lot of torrenting...enable "pre-allocate".
that will heavily prevent fragmentation.

---

### Post by yopnono on 2006-07-24
I just tried this script, and all i get is.
```
" Error defragmenting. Did the file disappear? "
```
Have even tried on a usb disk (vfat).

---

### Post by kopilo on 2006-10-17
Just wanted to say that it is working perfectly fine under Ubuntu 6.06 AMD 64, to install it all I did was extract the deb file and type into a terminal window
```
sudo dpkg -i --force-architecture defrag*.deb
```
*note this installs it as a 32 bit program thus effecientcy is lost to some degree.

EDIT: Just wanted to say this program is awesome! I love being able to point a specific files and directories as well as it's output, such as "/lib32/ is not fragmented. Go home.". :mrgreen:

---

### Post by yopnono on 2006-10-17
Humm thats odd... I just download it again, and this time it does work. I don't get any errors. Has the script file been changed?

---

### Post by jdong on 2006-10-17
> **kopilo said:**
> Just wanted to say that it is working perfectly fine under Ubuntu 6.06 AMD 64, to install it all I did was extract the deb file and type into a terminal window
```
sudo dpkg -i --force-architecture defrag*.deb
```
*note this installs it as a 32 bit program thus effecientcy is lost to some degree.

EDIT: Just wanted to say this program is awesome! I love being able to point a specific files and directories as well as it's output, such as "/lib32/ is not fragmented. Go home.". :mrgreen:

It's a python script, so it actually is architecture independent. The program itself is a textfile... technically it's a packaging error on my part (should be architecture all instead of i386) and I should eventually fix that.

So, no efficiency is lost, but it's not a very efficient program to begin with. It was just made to work and work safely.

---

### Post by kopilo on 2006-10-17
> **jdong said:**
> It's a python script, so it actually is architecture independent. The program itself is a textfile... technically it's a packaging error on my part (should be architecture all instead of i386) and I should eventually fix that.

So, no efficiency is lost, but it's not a very efficient program to begin with. It was just made to work and work safely.
Cool that's what I hoped py was standing for. *opens it up in gedit* Nice coding style, the internal documentation is good as well. 8) 

Effecientcy would be nice (eventually), it's still faster then the XP windows defrag on my computer.

Also thanks for the explanation.

---

### Post by jdong on 2006-10-17
Right now, the major bottleneck is building a list of fragmented files. Specifically,

(1) It must first get a list of ALL the files (via **find /path**). This operation alone is pretty time-consuming, especially if you have a lot of files. (the current implementation also directly loads into RAM this list in the form of a Python list, which means it'll occupy an amount of RAM roughly equal to how big "file" would be if you did find /path > file)
(2) For each file, it must execute "filefrags $filename". This has two problems of its own. First, if you have 10,000 files, you're spawning 10,000 copies of filefrags in succession (fork overhead). Second of all, filefrags itself takes some time to determine the fragmentation (it sequentially seeks through a file and counts the number of discontinuities in the position-by-block of the filesystem obtained via VFS/kernel versus the position in the file).


By far the majority of the bottleneck is in the sheer time it takes for filefrags to figure out the fragmentation level of each file, and unfortunately, that's completely out of my control.



So far, I've experimented with a few ways to make things go faster, but had very little success.

(1) "Stream" the filelist into filefrags. In other words, read output of "find /path" line-by-line, and start a filefrags $filename job after each line of output. Timing how long it took to analyze my /usr tree, the time saved was very negligible, and this method added a fair deal of complexity (threading and more involved management of the fragmatrix) to the code that simply wasn't worth it.

(2) Parallelize filefrags calls respective to # of CPU's. I got a dual-core laptop this summer, and proceeded to see if filefrags takes advantage of multiple CPU's well. Unfortunately, though doing 2 or 3 filefrags jobs simultaneously pushed CPU usage up pretty well, it was only doing the job like 10-15% faster. I think there is a kernel or IO bottleneck rather than a CPU one. Furthermore, it introduced a similar level of complicity as #1.




So, for now I'm out of ideas as far as how to make it faster. I've modeled most of this work after the behavior of tried-and-production-trusted xfs_fsr for the XFS filesystem. XFS magically knows its level of fragmentation with some magical xfs_db calls that work like 100x faster than generic filefrags, so that's an XFS-specific feature.


My last idea is to write my own version of filefrags that would be specifically geared towards the defragmenter. It'd probably take care of the whole "find / | filefrags" shebang by itself and report back fragmentation levels. Also, I'd like to change fragmentation calculation from just a fragment count to a "radius of file:filesize" ratio. After all, seek distance is what ultimately matters. Consider the scenarios:

(A) A 100MB file is written on every other contiguous block

(B) A 100MB file is split into two fragments, one at the beginning of a 60GB disk, the other at the other end.

Intuitively, I'd expect (A) to be slurped up from the disk almost as fast as if it wasn't fragmented (we're reading over a 200MB area sequentially rather than a 100MB area. At 50MB/s, no big deal). I'd expect B to be a worse scenario, especially if it was more than two fragments. The disk seek is what's killer.

Now, the current calculation method would yield roughly 512 frags/MB for file A and next to no fragmentation for file B, thus unfairly prioritizing A over B. Even worse, while trying to defragment A, it could turn A into B, making things worse instead of better!

A radius ratio calculation would yield 2.00 for A, and somewhere around 60,000 for B, correctly recognizing that situation B is worse than A.


Anyway, that's enough out of me for now. I'm gonna do some bootfile defragmentation testing to see if defragmenting /etc/readahead/boot speeds up bootup in any appreciable way.

---

### Post by jdong on 2006-10-17
Ok, does not make any significant impact in bootup speeds. After 10 runs with bootchart before and after defragging, it shows around half a second being shaved off S01readahead (which takes around 7 seconds on my laptop HD), so not really a noticeable impact.

Here's a bzr bundle of what it takes to turn defrag into bootdefrag. 


If you want to try boot defragging, use bzr to branch [https://launchpad.net/people/jdong/+branch/pyfragtools/trunk](https://launchpad.net/people/jdong/+branch/pyfragtools/trunk). Next, save the following snippet into bundle.txt,then do a "bzr merge bundle.txt"

```

# Bazaar revision bundle v0.8
#
# message:
#   Modify to bootstrap filenames from /etc/readahead/boot
#   
# committer: John Dong <john.dong@gmail.com>
# date: Tue 2006-10-17 13:22:26.329999924 -0400

=== modified file defrag
--- defrag
+++ defrag
@@ -523,9 +523,9 @@
             print "     Aborted: file changed during defrag."
             return numfrags(file)
 
-def build_filelist(fs):
+def build_filelist():
     #Uses find to get list of files on desired filesystem
-    list=subprocess.Popen(["/usr/bin/find",fs,'-xdev','-type','f', '-print0'],stdout=subprocess.PIPE).communicate()[0].split('\0')
+    list=open("/etc/readahead/boot").read().split('\n')
     return list[:-1]
 def numfrags(file):
     #Uses filefrag to determine # of fragments.
@@ -539,11 +539,11 @@
         if frags == 1:
             return 0
     return frags/(os.path.getsize(file)/1024.0/1024.0)
-def run(path,threshold=0.5,passes=-1,list=None, fragmatrix=None):
+def run(threshold=0.5,passes=-1,list=None, fragmatrix=None):
     if not fragmatrix:
         print "Building list of files to analyze...",
         sys.stdout.flush()
-        list=build_filelist(path)
+        list=build_filelist()
         print "done!"
         fragmatrix={}
         n=0
@@ -556,7 +556,7 @@
         pb.clear()
         print "\nAnalyze finished.",
         if len(fragmatrix) == 0:
-            print "\n%s is not fragmented. Go home." % path
+            print "\nBootup files are not fragmented. Go home."
             sys.exit(0)
     most_fragmented_files=sort_by_value(fragmatrix)
     frags=sum(fragmatrix.values())
@@ -591,7 +591,7 @@
                 n+=1
                 print "\n  Pass %d of %d, %d/%d (%d%%):" % (k+1,abs(passes),n,len(most_fragmented_files),100*n/len(most_fragmented_files)), "%.1f frags/MB" % fragmatrix[i], i
                 try:
-                    fragmatrix[i]=defrag(i,path,fragmatrix[i],threshold)
+                    fragmatrix[i]=defrag(i,os.path.dirname(i),fragmatrix[i],threshold)
                 except OSError:
                     print "     Error defragmenting. Did the file disappear?"
             tmp=most_fragmented_files[:]
@@ -620,7 +620,7 @@
             while not response in ('Y','y','N','n',''):
                 response=raw_input("\nThere is still fragmentation. Run another set of passes? [Y/n]")
             if response in ('Y','y',''):
-                run(path,threshold,passes,list,fragmatrix)
+                run(threshold,passes,list,fragmatrix)
 
 
 try:
@@ -642,14 +642,12 @@
                 passes=0
                 threshold=0
         try:
-            if os.path.isdir(opts[1][0]) and opts[1][0][-1] != '/':
-                opts[1][0]+="/"
-            run(opts[1][0], threshold, passes)
+            run(threshold, passes)
         except IndexError:
             raise getopt.GetoptError("No path specified")
     except getopt.GetoptError, info:
         print info
-        print "%s [-h] [-n passes] [--passes n] [-t threshold] [--threshold n] [-a] [--analyze] [--help] path"% sys.argv[0]
+        print "%s [-h] [-n passes] [--passes n] [-t threshold] [--threshold n] [-a] [--analyze] [--help]"% sys.argv[0]
 finally:
     if opts and len(opts[1]) and os.path.isdir(os.path.dirname(opts[1][0])+"/.defrag"):
         subprocess.Popen(['rm','-f','-r',os.path.dirname(opts[1][0])+"/.defrag"], stdout=subprocess.PIPE).communicate()[0]

# revision id: john.dong@gmail.com-20061017172226-48254a7a769a18ef
# sha1: ee532c44efbc97b8337407c7333ec0ec760b0a36
# inventory sha1: f210a867ea8ed31fe3ac6f1dc24bb2d8d1daccf6
# parent ids:
#   jdong@jdong-laptop-20060503014309-b8b22cb26fef9a25
# base id: jdong@jdong-laptop-20060503014309-b8b22cb26fef9a25
# properties:
#   branch-nick: bootdefrag


```

---

### Post by John.Michael.Kane on 2006-10-17
jdong is it safe to say this tool is best used for just dfraging drives,and not boot space?

---

### Post by jdong on 2006-10-17
> **SD-Plissken said:**
> jdong is it safe to say this tool is best used for just dfraging drives,and not boot space?

Well, I'd say that this tool is best used for defragging things you KNOW need defragging (i.e. you just captured 10GB of DV, and it's reading back at 1MB/s, too slow for rendering, but you know your disk should be capable of 50MB/s, so fragmentation might be slowing it down).

In other words, it probably won't give you any benefits if you just arbitrarily ran it on the entire system.


In other, other words: Linux really doesn't need defragging like Windows.

In other, other, other words: Just because pyfragtools claims files are fragmented, then spends 10 minutes defragging 1000 files doesn't mean any programs will run faster or boot faster.

---

### Post by yopnono on 2006-10-17
I don't get it. On one of my machines it works just fine, but on the other it fails " Error defragmenting. Did the file disappear? " really don't know what I need on the other machine. Have e2fsprogs. Is it some python stuff i need.

---

### Post by jdong on 2006-10-17
You get that error when an OSError is generated during defrag() (line 595)

I don't know what would be causing it though...

---

### Post by yopnono on 2006-10-17
I did find it, after reading the py script I did find rsync = I did not have it installed. :)

---

### Post by jdong on 2006-10-17
Ah, yes, missing rsync would generate an OSError with the os.system() call -- I didn't originally anticipate it since rsync is on default Ubuntu installs.

---

### Post by EdThaSlayer on 2006-10-17
hmmmm...nice idea! I always thought that the linux filesystem never needed a thing like this! But if it can boost performance its awesome! Thanks for making this!

---

### Post by jdong on 2006-10-17
> **EdThaSlayer said:**
> hmmmm...nice idea! I always thought that the linux filesystem never needed a thing like this! But if it can boost performance its awesome! Thanks for making this!

You're right, Linux really doesn't need a defragger... except for the special circumstances noted.


Everyone, please don't tell people to run pyfragtools for fun like Windows users seem to treat defraggers.... :)

---

### Post by maniacmusician on 2006-10-17
aw darn i was just going to try pyfragtools for fun!

lol no just kidding.  I might need it though; i DO torrent a lot. do you recommend running it on all downloaded torrents or only certain types of files?

---

### Post by jdong on 2006-10-17
> **maniacmusician said:**
> aw darn i was just going to try pyfragtools for fun!

lol no just kidding.  I might need it though; i DO torrent a lot. do you recommend running it on all downloaded torrents or only certain types of files?

I'd say use it only if you feel a particular file is slow and it's likely due to fragmentation.

---

### Post by ba5e on 2006-12-01
Jdong.....another amazing thread from your humble self...respect!

this is a godsend, and I have noticed an improvement defragging /usr /home and my 'games' directories.

I don't see how it can affect torrented files speed (depending on the content) video dloaded or ISO's will never really need full whack from your HDD, no mater what you do with it (except converting, as you stated).

I suppose at the end of the day, you see disk thrashing (or hear more to the point) when accessing certain files etc. think, 'oh pyfragtools' and bobs-ur-uncle no more thrashing! :)

---

### Post by jdong on 2006-12-01
> **ba5e said:**
> 
I don't see how it can affect torrented files speed (depending on the content) video dloaded or ISO's will never really need full whack from your HDD, no mater what you do with it (except converting, as you stated).

If you're burning the ISO's or on-the-fly burning the videos, you do need to keep up with the burner. And nowadays for DVD's, your burner could easily demand data at 10-20MB/s. If you can't keep up with that, you're using buffer underrun technology, which has the side effect of degrading record quality.

---

### Post by Johan! on 2006-12-01
How do I install the latest version?

I'd like to try this:)

---

### Post by jdong on 2006-12-01
> **Johan! said:**
> How do I install the latest version?

I'd like to try this:)

The tar.gz attached to the initial post is basically the latest version. I haven't found the need to make any major fixes to it yet because I'm a perfect programmer (kidding, kidding)

The absolute latest can be checked out using bzr at [https://launchpad.net/people/jdong/+branch/pyfragtools/trunk](https://launchpad.net/people/jdong/+branch/pyfragtools/trunk)

---

### Post by ago on 2006-12-01
IMO a linearization utility would be far more useful than a defragmenter. There is no point to have a disk well defragmented if files that have to be accessed in sequence are scattered all over the disk surface. Currently the disk is pretty well maintained as far as defragmentation goes, but the linearization is lacking. The head travel is one of the greatest performance sinks particularly if you have to open hundreds of files scattered around the place. The way to address that is to run a utility to sample typical use, and "defragment" the system so that files frequently accessed in sequence are close together on the disk.

---

### Post by jdong on 2006-12-01
That would require a tool to be able to physically change the location of files on the disk, which would require the filesystem to have defragging hooks for the userland. this isn't the case yet. As soon as it happens though I'd expect such tools to start coming out :)

---

### Post by fokuslee on 2006-12-16
jdong superb job 
2 thumbs wayyyy up.  about time someone rolled out with a defrag program.  for the future can u include a .deb for amd 64? 
yeah and work on those free space consolidation hehe 
once again thx im very happy with the prog.

---

### Post by jdong on 2006-12-16
It's a Python app, it doesn't distinguish between amd64 or i386... if you have python and access to the filefrags and rsync programs, it works. It doesn't need to be installed, just run it from where you unpacked it.

---

### Post by Daemon Mort on 2006-12-17
Nice defrag. I'm running a dual boot of Ubuntu and XP.  I D/L this for defrag XP partition since unmovable files is a pain.  I discoverd that this defrag cannot scan into folders with spaces. Leading to inability to defrag those files.  Unless of course I'm doing something wrong.
I am a Linux newb so very possible.

---

### Post by yopnono on 2006-12-17
> **Daemon Mort said:**
> Nice defrag. I'm running a dual boot of Ubuntu and XP.  I D/L this for defrag XP partition since unmovable files is a pain.  I discoverd that this defrag cannot scan into folders with spaces. Leading to inability to defrag those files.  Unless of course I'm doing something wrong.
I am a Linux newb so very possible.

Do you have read and write enabled on the NTFS drive? If not then you will not be able to defrag it.

---

### Post by Daemon Mort on 2006-12-17
Its actually a FAT32 so to be more reliable as i have read Ubnuntu and NTFS are not completely compatible.  I have the partion by default as read only as i have discoverd that if i access a file (not alter just read) and have write ability to the partion; that the files attributes will change. I have had problems trying to use programs due to this, in windows.

I scan my drive for fragments both with this prog.  and another under windows.  There are files windows finds (under Program Files) that are LARGE and fragmented badly. (WoW and GW dat files) Yet this prog does not even show them as being fragmented after the anaylsis.  

Would making the mounted partion writeable fix the discovering issue?

Being read only this prog was still able to defrag other files on the drive just fine.
Again Linux Newb.. so please be gentle.

---

### Post by jdong on 2006-12-17
> **Daemon Mort said:**
> Nice defrag. I'm running a dual boot of Ubuntu and XP.  I D/L this for defrag XP partition since unmovable files is a pain.  I discoverd that this defrag cannot scan into folders with spaces. Leading to inability to defrag those files.  Unless of course I'm doing something wrong.
I am a Linux newb so very possible.

Hmm, it's certainly possible that there are some bugs in the program dealing with weird file or folder names... though I thought I already caught them all during my testing.


If this is still a problem, please attach the output of the program including any error messages and enclose the program's output in [ code ] tags (or e-mail them to me) and I'll see what I can do.

---

### Post by steevcoco on 2006-12-17
Hi. I just wanted to add more food for thought that I didn't see mentioned in the thread.

Looks like a nice program; and folks will benefit.

Another good reason not to defrag as a kind of overly-regular maintenance is the toll it takes on disk usage. One defrag might put more hours on the disk than a whole week of your typical usage depending on what you do with the computer. This is not 100% complete advice, especially for heavy media use, but it is true.

I am lucky (sic) to have seen plenty of drives go down over the years. True story: I'm a sound designer and once a drive in a large external enclosure started crashing. It started making this putrid noise so I grabbed a Mic as fast as possible and recorded that thing. It was a good enough sound to get cleaned up and make its way into my standard sound effects library. It was kind of like a jet engine or dive bomber sound.

And to boot, that drive was actually one of the drives housing my SFX library; so it probably should have cost some kind of premium for that! ](*,)

---

### Post by jdong on 2006-12-19
Yes, that is absolutely true also, defragging basically requires rewriting the fragemented files at least once (up to 10 times with pyfragtools), and that does put added stress to that degree.

On the other hand, you can also argue that by reading a fragmented file and writing it back unfragmented, you are doing yourself a favor in the long run by making those files read with fewer seeks next time around!

Note that pyfragtools by default will stop trying to defragment when the fragment ratio falls below .5 fragments per MB (i.e. 1 fragment every 2MB), which will prevent it from going beserk trying to iron out every last fragment :). Don't circumvent this protection unless you have a really really REALLY good reason to. (I'm not sure if testing a 5-yr warranty is good enough a reason though ;-) )

---

### Post by Daemon Mort on 2006-12-19
Well further investigation shows that pyfragtools does scan and defrag in folders with spaces on FAT32 partions.  The problem was a read/write access problem... It seems that if the partion as a whole is read only, py, doesnt care.  It does respect the folder and files attributes though.  Which is a pain in my behind because the files that need it the most i cant do because of this.

---

### Post by jdong on 2006-12-19
Hmm, well, if the partition is mounted readonly, I can't override that and force the ability to write to it...

As far as preserving attributes, the copy is done with rsync with the archive mode which should preserve all permissions bits. I have no idea if it's EA/ACL-safe...

---

### Post by marco999 on 2007-01-01
I updated the file so that way it will not try to update it. The name is not pyfragtools and the command to run the program is superdefrag instead of just defrag.

This the proper syntax to run it is:

sudo superdefrag /

(U may replace "/" with the directory to defrag)

Thanks.

marco999

---

### Post by jdong on 2007-01-02
Cool. Let's think of a nice creative name for this guy and get a once-and-for-all rename. Then I'd like to submit this to Feisty universe.

---

### Post by Frak on 2007-01-02
I don't know if you want suggestions from other users, but what about:
LinFrag
Short simple and to the point.

---

### Post by jdong on 2007-01-02
Suggestions from anyone are welcome!

---

### Post by yopnono on 2007-01-02
Maybe some one how know to create a pyton GUI for this could do that before sending it to the repo. It's better for new users, also just make the gui open in gksu and all will be fine.

---

### Post by yopnono on 2007-01-02
> **jdong said:**
> Suggestions from anyone are welcome!

any name is fine Lindefrag like the above said, Defrager etc,etc

---

### Post by Sammi on 2007-01-02
What about defragger?

---

### Post by mastergunner on 2007-01-03
I am lost on how to use this little defragger. I mean how do I tell it which drive to defrag? Anyword on a simple GUI based defragger?

---

### Post by jdong on 2007-01-04
You don't tell it a drive to defrag. You tell it a file or a directory that you want to defrag. If you have your external harddrive at /media/usbdisk, you'd issue "defrag /media/usbdisk"

---

### Post by mastergunner on 2007-01-05
Well how do you defrag your hdd that Kubuntu is on?

---

### Post by jdong on 2007-01-05
You would tell it to "defrag /", which is the root. I don't recommend you do this though; defrag should be targeted at specific files that you suspect are fragmented. It's not meant to be run like a Windows defragger (that is, obsessively over the entire hard drive every few days). Linux does not need that kind of defragging.

---

### Post by samir85 on 2007-01-05
One thing I always had on my mind about defragmenting:

Why do I not need to defrag on Linux ? I mean on Windows I have to defrag something like once a month otherwise performance decreases seriously ... 

regards Samir

---

### Post by Frak on 2007-01-05
Because from what I know, Windows writes to drive lazily, writing to wherever there is space to write to, Linux writes data to where it should go, all in one large pack, not a million different spots like on Windows. In turn, no need to defrag, everything isn't fragmented, so there is no reason.

---

### Post by jdong on 2007-01-05
> **samir85 said:**
> One thing I always had on my mind about defragmenting:

Why do I not need to defrag on Linux ? I mean on Windows I have to defrag something like once a month otherwise performance decreases seriously ... 

regards Samir

All the Linux filesystems are designed with allocation policies that minimize the occurrence of fragmentation, and also the severity of fragmentation if it must indeed happen.

In addition, the Linux IO schedulers are able to cope with most degrees of fragmentation, ordering/sorting read requests to better match the on-disk layout.

In the end, unless you:

      (A) Torrent large files that slowly build up to gigabytes over the course of days, then suddenly need to read them back at rapid speeds to, say, burn them to a CD/DVD
     (B) Fill the disk to 90%+ full and use it like that for a prolonged period of time

Linux will not accumulate enough fragmentation for you to perceive any loss in performance.

I have several Linux boxes with ext3 partitions that I've let be for over 2 years now, and checking a fragmentation rate on it yields 2% or 3%, and pyfragtools indicates majority of that fragmentation is in logfiles anyway. XFS has a built-in defragger. On a 1-year-old XFS partition the defragger took around 20 minutes to fully defragment the drive :)

---

### Post by jdong on 2007-01-17
[http://vleu.net/shake/](http://vleu.net/shake/)

Don't know if you guys have seen this, but shake is a defragger that operates on the same principles as Pyfragtools (purely userspace, rewriting files over and over again till their fragmentation falls below a threshold)

Its algorithms and features seem to be much more advanced than pyfragtools, so if you do this a lot, shake is a better alternative :)

---

### Post by atlfalcons866 on 2007-01-19
how do i install it? i am still new to linux i know how install .deb not .rpm or .tar.gz

---

### Post by Frak on 2007-01-19
> **atlfalcons866 said:**
> how do i install it? i am still new to linux i know how install .deb not .rpm or .tar.gz
**.deb**-double click it
**.rpm**-install alien (sudo aptitude install alien) and run this code
```
sudo alien install <location of rpm>
```
**.tar.gz**-install build-essential from synaptic then run this (might not work, refer to README most of the time for things like this.
(P.S. Remember to untar the .tar.gz, tarballs(.tar.gz) by double clicking it and extracting it to a folder somewhere on your computer)

```
cd <location of untared .tar.gz.>
./configure
sudo make
make install
```

If you want to, there is a program in synaptics called "checkinstall" that can make sure that the .tar.gz was installed correctly, then adds an entry into synaptics.

---

### Post by jdong on 2007-01-19
Pyfragtools does not require any compiling and will suffice without the first make command; only make install is required.

Or you can run it directly out of the folder  you unpacked it to (run sudo ./defrag blah)

---

### Post by jongkind on 2007-01-20
This is an excellent tool, jdong. It took away my concerns on file fragmentation of my system. You can read more about this here:

[http://www.ubuntuforums.org/showthread.php?t=203842]("http://www.ubuntuforums.org/showthread.php?t=203842")

grtz, H.

---

### Post by shining on 2007-01-20
> **jdong said:**
> [http://vleu.net/shake/](http://vleu.net/shake/)

Don't know if you guys have seen this, but shake is a defragger that operates on the same principles as Pyfragtools (purely userspace, rewriting files over and over again till their fragmentation falls below a threshold)

Its algorithms and features seem to be much more advanced than pyfragtools, so if you do this a lot, shake is a better alternative :)

This thread made me remember con kolivas also wrote a little defrag tool a while ago. Is it different? :
[http://ck.kolivas.org/apps/defrag/](http://ck.kolivas.org/apps/defrag/)

---

### Post by jdong on 2007-01-20
My tool was heavily inspired by Con Kolivas's defrag script, but I rewrote it in python to make it a bit more customizable, user-friendly,and even intelligent.

It still uses similar defragmentation algorithms and an identical analysis algorithm.

---

### Post by jdong on 2007-01-22
WARNING: I've been able to reproduce some consistent corruptions (mismatched md5sums, one time even damaged bootup sequence) through the use of shake, especially if it is terminated prematurely (i.e. CTRL+C, system freeze, etc)

This does NOT happen with pyfragtools; pyfragtools was designed to operate slowly but reliably in a totally atomic manner. Either a file is completely defragemented or not defragmented at all. There is no half-baked in-between.

---

### Post by chris_ds on 2007-02-11
First of all hello world (first post). =) :popcorn: 

So jdong what defrag tool shall we use now? 
"Shake" or yours?

Well, anyway, I wans't able to compile shake on my system, so I tried pydefrag ^^

It was pretty fast, but please find the time to rename it, so apt won't try to update it with the defrag tool in the repo.

A feature I would like to see in it (well I know you did not write it for that reason) is the ability to defrag free space etc.

By the way I try to say:
I really like this program. =D>

---

### Post by jdong on 2007-02-11
> **chris_ds said:**
> First of all hello world (first post). =) :popcorn: 

So jdong what defrag tool shall we use now? 
"Shake" or yours?

I still recommend pyfragtools over shake for the sake of safety.
> It was pretty fast, but please find the time to rename it, so apt won't try to 
update it with the defrag tool in the repo.

When I find time I'd like to submit it to the Ubuntu repositories as pyfragtools.
> 
A feature I would like to see in it (well I know you did not write it for that reason) is the ability to defrag free space etc.

I've already explained why that wasn't implemented -- safety. To defrag free space one must understand the filesystem and manipulate it at a low-level.

That is not what pyfragtools does, and to make it do that would be to make it a totally different program.

e2defrag, however, does do this, but at a safety loss. Backport the version from Feisty (with prevu) and it'll be able to defrag ext3 properly. However, **do not lose power while using e2defrag**. Trust me ;-). Trust me.

Does e2defrag make things any faster?

I tried it on my test ubuntu setup, and just like on my laptop with pyfragtools -- I cannot make a noticeable performance boost. Linux doesn't need defragging the way that Windows does.

---

### Post by chris_ds on 2007-02-11
OK safety is a very important detail of a system tool. I will use pydefrag.

I forgot to mention that I use pydefrag for windows formatted volumes (fat32 and ntfs). 

I'm happy with ubuntu and it's my main system for 23 hours a day, but when it comes to gaming I have no (real) choice. And as I often transfer files between the two systems at very low free space sometimes, there's a lot of fragmentation.

I don't want to switch to win"experience" and let it run for 3 hours, just for defragmentation, because of my sensitive feeling of safety ^^.

OO's software is no alternative, because I like open source and cannot spend money on something like that at the moment.

---

### Post by Frak on 2007-02-11
> **chris_ds said:**
> OK safety is a very important detail of a system tool. I will use pydefrag.

I forgot to mention that I use pydefrag for windows formatted volumes (fat32 and ntfs). 

I'm happy with ubuntu and it's my main system for 23 hours a day, but when it comes to gaming I have no (real) choice. And as I often transfer files between the two systems at very low free space sometimes, there's a lot of fragmentation.

I don't want to switch to win"experience" and let it run for 3 hours, just for defragmentation, because of my sensitive feeling of safety ^^.

OO's software is no alternative, because I like open source and cannot spend money on something like that at the moment.
I'm sorry for being off topic, but did you try Abiword? Its much more like MS Office than OO is.

And great job Jdong, I used it and loved it, keep on keepin' on.

---

### Post by jdong on 2007-02-11
I have never tested pyfragtools with ntfs-3g. I have no idea if that works or not, but I'd love to know :)

At worst it will fail and refuse to defrag -- pyfragtools only removes the fragmented original file when it's sure the new file is the same as the old one and less fragmented.


And OpenOffice is large and relatively slow -- abiword and gnumeric are lighter alternatives if you don't need all the features of abiword.

The speed of openoffice will improve quite a bit in Feisty due to the new dt_gnu_hash link style.

Also, you can try prelinking your system (search howto's) to gain similar speedups.

---

### Post by reacocard on 2007-02-11
Just tried this, works like a charm. I've added a package for it to my repository. To use it, add these lines to your sources.list:
```
deb http://download.tuxfamily.org/syzygy42 edgy reacocard
deb-src http://download.tuxfamily.org/syzygy42 edgy reacocard
```
then do 
```
sudo apt-get update
sudo apt-get install pyfragtools
```

---

### Post by chris_ds on 2007-02-13
Cool can't wait for feisty (or more RAM) ^^ tried abiword as well, but I really miss some features. Only use it for plain text.

And now back to topic:
Py' works very well with fat32! ...But I'm scared to test it on my ntfs volume, because I don't have enough free space to make backups. 

Hope someone else can test it soon. 

(By the way i actally meant "O & O Defrag" a windows tool for deragmentation)

---

### Post by mooter on 2007-02-13
I added those 2 to the repo list but it needs a pub key.  Thank you nonetheless.

---

### Post by reacocard on 2007-02-13
> **mooter said:**
> I added those 2 to the repo list but it needs a pub key.  Thank you nonetheless.

Oops, forgot that. :oops: To get the key, type this in a terminal.
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
```

---

### Post by chris_ds on 2007-02-17
OK, I tested pyfrag on my ntfs volume with the ntfs-3g driver.

Well it's not working. While analysing it spammed my Konsole with something like "FIBMAP" error or so... (sorry I forgot to write it down, and I'm too old to remember :P )

After a while it said "Volume is not fragmented" but I think the analysis went wrong.


I think I need to test "Shake" on ntfs, too. But I get compile errors:

```

/shake-0.29$ make
gcc -std=gnu99 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_XOPEN_SOURCE=600 -O2 -D_POSIX_C_SOURCE=200112L -Wall -pedantic-errors  -Wcast-align -Wpointer-arith -Wbad-function-cast -DVERSION=\"0.29\" -DNDEBUG -c executive.c -o executive.o
gcc -std=gnu99 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_XOPEN_SOURCE=600 -O2 -D_POSIX_C_SOURCE=200112L -Wall -pedantic-errors  -Wcast-align -Wpointer-arith -Wbad-function-cast -DVERSION=\"0.29\" -DNDEBUG -c judge.c -o judge.o
gcc -std=gnu99 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_XOPEN_SOURCE=600 -O2 -D_POSIX_C_SOURCE=200112L -Wall -pedantic-errors  -Wcast-align -Wpointer-arith -Wbad-function-cast -DVERSION=\"0.29\" -DNDEBUG -c linux.c -o linux.o
linux.c:23:43: error: attr/attributes.h: No such file or directory
linux.c: In function ‘set_ptime’:
linux.c:42: warning: implicit declaration of function ‘attr_setf’
linux.c:43: error: ‘ATTR_DONTFOLLOW’ undeclared (first use in this function)
linux.c:43: error: (Each undeclared identifier is reported only once
linux.c:43: error: for each function it appears in.)
linux.c: In function ‘get_ptime’:
linux.c:55: warning: implicit declaration of function ‘attr_getf’
linux.c:55: error: ‘ATTR_DONTFOLLOW’ undeclared (first use in this function)
make: *** [linux.o] Fehler 1

```

Any suggestions?

---

### Post by jdong on 2007-02-17
ok, FIBIOMAP is not defined by ntfs-3g then; FIBIOMAP is the command used by pyfragtools to measure the amount of fragmentation.

---

### Post by esaym on 2007-02-18
Well I don't know if I found a bug or something or if I did something wrong but right in the middle of it analyzing my hard drive it forced my computer to instantly restart.  My computer has never done anything like this before.  And since it was in the middle of analyzing when it rebooted I got some data lose and the config files for aMule were all trashed.  I was simply trying to analyze a 60gb storage partition I had.

Not sure what happened.  I was only analyzing my hard drive just to see what files were fragmented.  And then I would have some info to give to people that want to complain about fsck showing 5% non-continuous.  But for now I think I am through defragging :oops:

---

### Post by jdong on 2007-02-18
Hmm during the analysis phase it just calls FBIOMAP() a lot of times which is a read-only function asking for the physical position on disk of logical blocks in various files.

It should not cause any destruction -- it doesn't even write to the HD. The only reason it'd hard-reset is if the filesystem already had some silent corruption and this simply exposed it by groping every data block on the disk.

And as far as dataloss, that sounds like standard data corruption after a hard-reset on a non-atomic filesystem. It's a fact of life unfortunately until a fully atomic filesystem is widely available.

---

### Post by esaym on 2007-02-18
> **jdong said:**
> Hmm during the analysis phase it just calls FBIOMAP() a lot of times which is a read-only function asking for the physical position on disk of logical blocks in various files.

It should not cause any destruction -- it doesn't even write to the HD. The only reason it'd hard-reset is if the filesystem already had some silent corruption and this simply exposed it by groping every data block on the disk.

And as far as dataloss, that sounds like standard data corruption after a hard-reset on a non-atomic filesystem. It's a fact of life unfortunately until a fully atomic filesystem is widely available.

Yea I am sure the data loss came from the hard reset and the fact that I use ext3 in writeback data mode. So far it just looks like a couple of config files were lost from the programs that were running at the time.  I don't get why the computer would reboot.  This ubuntu install is only 2 months old.  Fsck just automatically ran on that hard drive I was analyzing like last week and it had no problems.

---

### Post by jdong on 2007-02-18
That's really weird. I really wonder if it was even caused by prevu. Prevu uses three operations in total:

(1) find to build a list of files
(2) fbiomap to analyze fragmentation
(3) rsync to copy, rm to remove.


#1 is a commonplace algorithm, #2 is done by Ubuntu every time it boots (Reading boot files), #3 is also a commonplace algorithm


I don't see how any can really cause a kernel panic/reset....

---

### Post by esaym on 2007-02-19
> **jdong said:**
> That's really weird. I really wonder if it was even caused by prevu. Prevu uses three operations in total:

(1) find to build a list of files
(2) fbiomap to analyze fragmentation
(3) rsync to copy, rm to remove.


#1 is a commonplace algorithm, #2 is done by Ubuntu every time it boots (Reading boot files), #3 is also a commonplace algorithm


I don't see how any can really cause a kernel panic/reset....

I am not sure.  I am running kubuntu if that matters.  Maybe someday after I back up my disks I will try and run this again and see what happens...

---

### Post by Aikanar on 2007-10-11
Thanks, jdong, for creating this utility. :)

I have just used it to defrag my ext3 partitions with excellent results.

I did notice one problem, though: I installed from the .deb in your package, and the package name that it uses (defrag) is the same as one in the Ubuntu repos, so Adept notifier tells me that it needs to be updated.

At first I thought that this was an update to your package which I had just downloaded, but when I let Adept upgrade it, it replaced it by something directly from Ubuntu which doesn't have the capabilties that your defrag utility does.

How can I get Adept notifier to ignore your defrag so that it doesn't keep notiying me about updating it?

Thanks in advane for your help.

///Dave

---

### Post by jdong on 2007-10-11
I stupidly made the package named defrag BEFORE realizing that an incoming Ubuntu package is named identically....

For now I recommend just not using a package. Copy the pyfragtools executable to /usr/local/bin and name it whatever you want.

---

### Post by atlfalcons866 on 2007-10-12
The arcive is broken in gutsy. I tryed to unzip under 7zip under wine and that said it was broken too

---

### Post by jdong on 2007-10-12
[jdong@jdong:/tmp]$ tar xzvf pyfragtools-0.1.tar.gz               (10-12 10:07)


Extracted fine for me in Gutsy

---

### Post by atlfalcons866 on 2007-10-12
what file system would you recommend besides reiserfs?

---

### Post by atlfalcons866 on 2007-10-12
this is what happens when trying to untar
tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by jdong on 2007-10-12
Hmm perhaps your download tool is not correctly working then; it seems fine for me and I just downloaded the tar.gz attachment.

As far as filesystems, my recommendation has been and will be ext3 for the foreseeable future, unless you have specific needs (i.e. large files or small files) that are addressed by another filesystem (JFS/XFS , reiserfs respectively)

---

### Post by FuturePilot on 2007-10-12
The Update Manager wanted me to update this after I installed it and then it didn't work anymore.:confused:
```
sudo defrag /usr/sbin/
Password:
Couldn't determine filesystem type; please run the appropriate
defragmenter (e2defrag, edefrag, xdefrag, mdefrag) directly.

```

---

### Post by Frak on 2007-10-12
> **FuturePilot said:**
> The Update Manager wanted me to update this after I installed it and then it didn't work anymore.:confused:
```
sudo defrag /usr/sbin/
Password:
Couldn't determine filesystem type; please run the appropriate
defragmenter (e2defrag, edefrag, xdefrag, mdefrag) directly.

```
pyfragtools shares the same name (defrag) with the one in the repos, which are both different. The one you updated to is different.

---

### Post by FuturePilot on 2007-10-12
Would it be possible to recompile it with a different name? Or is there something I can do to stop being reminded of an update all the time?
Edit: Never mind. I just locked the version and the update reminder went away.:)

---

### Post by jdong on 2007-10-12
download the tarball, and copy the defrag file in there to /usr/local/bin, and pick whatever name you want.

---

### Post by FuturePilot on 2007-10-12
> **jdong said:**
> download the tarball, and copy the defrag file in there to /usr/local/bin, and pick whatever name you want.

Ah, that works too!:)
Thanks;)

---

### Post by aphirst on 2007-10-19
Thats some quality legend jdong. (heh, DONG :P ) Thanks a bunch ;)

Downloaded, installed, and run PERFECTLY on my Feisty 64 laptop.
Well done! (I wish i could code such immense programs in my spare time...)

*wonders if it could be ported to DSLinux...*

---

### Post by atlfalcons866 on 2007-10-26
i only use this to defrag my 1GB flash drive and 40GB external drive which are both fat32.

---

### Post by deepclutch on 2007-12-10
sorry for the bump!I download lot of torrents into / dir.but i dint find any problem reg speed.so,is it worth using this defragger.also is any updates for pydefragger :)

---

### Post by jdong on 2007-12-10
If you're not having any speed problems, it's pretty pointless to run this. And no, no updates... the concept is simple (it's just copying files around and rewriting them) and really is a dead-end solution until ext3 gains kernelmode defragging hooks.

---

### Post by atlfalcons866 on 2007-12-10
i use jfs for my torrents. JFS has extent support which reduce or eliminate fragmentation. EXT3 dosent but ext4 does.

---

### Post by jdong on 2007-12-10
XFS and reiser3/4 and NTFS all use extents and they are certainly not immune to fragmentation. Fragmentation-while-torrenting will continue to occur until there is a good mechanism for userland to tell the kernel to reserve blocks of space (which is beginning to happen, and has already happened with XFS)

---

### Post by atlfalcons866 on 2007-12-11
JFS is the most prone to fragmentation. The maintainer of jfs even said fragmentation can be a problem on it. I use jfs for a seperate /data partition for torrents and / because i find it is faster than ext3. But i use ext3 on my /home with journal data mode.

---

### Post by jdong on 2007-12-11
IMO JFS is less prone to data fragmentation than most other filesystems, but it doesn't contend with XFS's ability to reduce fragmentation online.

---

### Post by deepclutch on 2007-12-12
so,do you suggest that torrent users etc should make a separate partition for downloads rather than make it part of the / partition?
Also please "explain kernelmode defragging hooks" 
and i read in ext4 wiki that it is going to have "online defragmentation" :?
Thank you for the replies. :)

---

### Post by jdong on 2007-12-12
> **deepclutch said:**
> so,do you suggest that torrent users etc should make a separate partition for downloads rather than make it part of the / partition?

Absolutely. Constantly changing or fragmentation-prone stuff should be isolated on its own filesystem.

> 
Also please "explain kernelmode defragging hooks" 
and i read in ext4 wiki that it is going to have "online defragmentation" :?
Thank you for the replies. :)

It's basically a way to cause defragmentation online, basically you can tell the kernel "Move blocks A, B, C, D from location X to Y" and the kernel does so safely for you. Without such an instruction set we cannot do online defragmentation.

It will be an ext4 and possibly ext3 feature in the future. It already is an XFS feature.

---

### Post by Frak on 2007-12-12
> **atlfalcons866 said:**
> JFS is the most prone to fragmentation. The maintainer of jfs even said fragmentation can be a problem on it. I use jfs for a seperate /data partition for torrents and / because i find it is faster than ext3. But i use ext3 on my /home with journal data mode.
IMO, JFS doesn't fragment as much as Ext3. JFS was created by IBM, and IMHO, its really good for a 17 year old FS.

---

### Post by jdong on 2007-12-12
*cough* JFS2, what we call JFS on Linux, is not 17 years old ;-)

---

### Post by atlfalcons866 on 2007-12-12
well the maintainer of JFS David Kleikamp is helping with ext4.

I switched everything back to ext3 on my hard disk because JFS isn't maintained as much as it use to be. The only thing that i will miss from JFS is the quick fsck time.

I havent used reiser yet how is that fs good at preventing fragmentation? i dont dare go to that file system because from what i hear reiser corrupts easy. 

XFS corrupted on me because i lost power to my computer. With power lost on my computer with JFS and ext3 JFS just took a few extra seconds and ext3 said Recovering Journal.

---

### Post by jdong on 2007-12-13
Yeah ext3 is the clear winner right now for a general purpose filesystem -- not only is it generally solid all-around, it also has a clear upgrade path in sight to a superior successor without full reformats (in fact, it'd barely take a reboot to do an ext4 upgrade!). With that said, and considering that ext2-ext3 was just as easy, it would seem like the ext series takes upgradability very seriously.

Reiserfs handles fragmentation very poorly particularly with torrenting type load.

XFS as you've seen, handles powerdowns very terribly. Ext3 and JFS both handle it well, as does reiserfs, and there's some people I know who SWEAR by JFS's power loss resilience.

As far as journal recovery, ext3 and JFS recovery are both pretty fast, ext3 is a bit slower than JFS, but remember iwth JFS it has a fsck phase that must be completed before remounting read-write (that's where the time consuming journal replay happens). XFS takes the cake with the blisteringly fast journal replay department, I've managed 750GB XFS volumes that could come back online in under a second after a power zap.

---

### Post by altonbr on 2007-12-13
> **jdong said:**
> Yeah ext3 is the clear winner right now for a general purpose filesystem -- not only is it generally solid all-around, it also has a clear upgrade path in sight to a superior successor without full reformats (in fact, it'd barely take a reboot to do an ext4 upgrade!). With that said, and considering that ext2-ext3 was just as easy, it would seem like the ext series takes upgradability very seriously.

Reiserfs handles fragmentation very poorly particularly with torrenting type load.

XFS as you've seen, handles powerdowns very terribly. Ext3 and JFS both handle it well, as does reiserfs, and there's some people I know who SWEAR by JFS's power loss resilience.

As far as journal recovery, ext3 and JFS recovery are both pretty fast, ext3 is a bit slower than JFS, but remember iwth JFS it has a fsck phase that must be completed before remounting read-write (that's where the time consuming journal replay happens). XFS takes the cake with the blisteringly fast journal replay department, I've managed 750GB XFS volumes that could come back online in under a second after a power zap.

I have a feeling you should write a blog article on the comparison of filesystems or start a Wiki with everything that's in that little brain of your's :P

---

### Post by psusi on 2007-12-13
I have been using reiser for a long time but am considering switching back to ext3 because there is no defragger availible for reiser.  Once you get 50-100k messages in a maildir, reiser is rather efficient in storing them and accessing them by name, but doing things like du take eons due to the seek storm while the system rams the disk head back and forth between the directory blocks and the stat blocks.  

IIRC, the defrag package optimizes the order of the names in directories to match the inode order which will help greatly with that problem.  Also it looks like ext3 now has the ability to store small file's data directly in the inode to make them take up less space and access quickly, as well as directory hash indexes to speed up searches in very large directories, so there go the two main reasons to run reiser.

---

### Post by jdong on 2007-12-13
Yep, ext3 also has the defrag tool from the repositories which is an offline, "full" defragmenter. God help you, however, if you manage to cut power during one of those defrag passes. There's a bit of a risk involved in using defrag.

---

### Post by psusi on 2007-12-13
> **jdong said:**
> Yep, ext3 also has the defrag tool from the repositories which is an offline, "full" defragmenter. God help you, however, if you manage to cut power during one of those defrag passes. There's a bit of a risk involved in using defrag.

LOL... that's what UPSes are for ;)

And you DO have a recent backup don't you?  Right? ;)

---

### Post by atlfalcons866 on 2007-12-13
why do they have defraggers if ext3 dosent fragment as much as windows file systems do?

---

### Post by jdong on 2007-12-13
> **atlfalcons866 said:**
> why do they have defraggers if ext3 dosent fragment as much as windows file systems do?
Doesn't fragment as much != doesn't fragment at all. Take an ext3 filesystem for a busy filesystem that's been in use for 10 years, and I'm gonna bet that it's not gonna look pretty!

---

### Post by Gen2ly on 2007-12-13
I'm getting this message too.  I have installed already rsync.  Also I'm not using Ubuntu.  Is there another program that I need?

```
     Error defragmenting. Did the file disappear?
```

I did "sudo make install" and am running the program under sudo.  I see this with any file directory I choose.  Any ideas?

---

### Post by atlfalcons866 on 2007-12-13
i downloaded a ubuntu dvd from bittorrent and it is in 23201extents in ext3 is that normal for ext3? I have 80% free space. Also is there a way to see the largest chunk of free space?

---

### Post by Frak on 2007-12-13
> **atlfalcons866 said:**
> i downloaded a ubuntu dvd from bittorrent and it is in 23201extents in ext3 is that normal for ext3? I have 80% free space. Also is there a way to see the largest chunk of free space?
Try Applications->Accessories->Disk Usage Analyzer

---

### Post by altonbr on 2007-12-13
> **Frak said:**
> Try Applications->Accessories->Disk Usage Analyzer

That doesn't show you the low-level hard drive blocks though, which I think he is referring to...

If not, the program (Disk Usage Analyzer) is called 'baobab' if you need to install it elsewhere.

---

### Post by psusi on 2007-12-14
> **atlfalcons866 said:**
> i downloaded a ubuntu dvd from bittorrent and it is in 23201extents in ext3 is that normal for ext3? I have 80% free space. Also is there a way to see the largest chunk of free space?

WOW, are you sure?  Which program told you this?  If that is true then something is very, very broken.

---

### Post by jdong on 2007-12-14
psusi, I've seen similar things happen, with large torrents especially ones that take more than 48 hours to complete into a 5GB file or so, you will get some enormous number of extents if you don't preallocate on ext3. (reiserfs can sometimes hit 6-digits :D)

---

### Post by atlfalcons866 on 2007-12-14
Azureus preallocates automaticly. But i copied the file to a different location and its only in 126 extents.

To find out how many extents a file is in use filefrag

---

### Post by altonbr on 2007-12-14
@jdong,

Have you considered putting this in a PPA repository in Launchpad?

---

### Post by jdong on 2007-12-14
> **altonbr said:**
> @jdong,

Have you considered putting this in a PPA repository in Launchpad?

If it's ever repackaged in a nonshameful way, yes. Currently it name-clashes with an existing Ubuntu package's binary.

---

### Post by altonbr on 2007-12-14
> **jdong said:**
> If it's ever repackaged in a nonshameful way, yes. Currently it name-clashes with an existing Ubuntu package's binary.

Which I'm experiencing right now...

In Gutsy, it keeps asking to be upgraded to '0.73pjm1-8ubuntu1' and I don't know how to tell it to never upgrade this package...

Anyway, can you not just easily rename the tool to 'pyfragtools'? I think a quick chat with MOTU could get this included for Hardy too...

---

### Post by jdong on 2007-12-14
Yeah I could package it correctly, it should be trivial but my free time is near zilch these few weeks

---

### Post by altonbr on 2007-12-14
> **jdong said:**
> Yeah I could package it correctly, it should be trivial but my free time is near zilch these few weeks

Hey that's fine, I appreciate the time you've put into it thus far anyway!

A note for the future though: What are your thoughts on using [Glade]("http://glade.gnome.org/") and [PyGTK]("http://www.pygtk.org/") and trying to get this included in Ubuntu [main]("https://wiki.ubuntu.com/UbuntuMainInclusionRequirements") (or at least universe)?

I'm sure you're aware of the process as I see you are a package maintainer for a couple packages, are you not? ([https://launchpad.net/ubuntu/+source/azureus](https://launchpad.net/ubuntu/+source/azureus))

---

### Post by jdong on 2007-12-14
I don't know the amount of demand for a special-purpose tool like this... I don't see the merit of turning it into a GUI personally as I can imagine people randomly running this and making framgentation worse, not better.

---

### Post by atlfalcons866 on 2007-12-14
isnt it better not to defrag and let the file system take care of it self?

---

### Post by jdong on 2007-12-14
> **atlfalcons866 said:**
> isnt it better not to defrag and let the file system take care of it self?

99% of the times, yes, but as you've seen there's times that files with 20,000 extents DO get created by various processes and once they're created they will not defrag themselves, ever.

---

### Post by altonbr on 2007-12-15
Well if a desktop-user GUI isn't the idea, I think making 'defrag' available for pure command-line calls, such as using cron, would be highly beneficial.

It seems to have to ask for input from the user after the analysis is done and therefore can not be used for a crontab.

Correct me if I'm wrong though :)

---

### Post by Gen2ly on 2007-12-15
Deframenter for Linux

I'm getting an error while trying to run defrag. 

```
     Error defragmenting. Did the file disappear?
```

I installed already rsync.  Is it possible that there is another program I require?

I installed by "sudo make install" and am running the program under sudo.  

I error happens with any file directory I choose.  Any ideas on how this isn't running?

---

### Post by jdong on 2007-12-15
> **altonbr said:**
> Well if a desktop-user GUI isn't the idea, I think making 'defrag' available for pure command-line calls, such as using cron, would be highly beneficial.

It seems to have to ask for input from the user after the analysis is done and therefore can not be used for a crontab.

Correct me if I'm wrong though :)


There are command-line switches to predefine a max # of passes, in which case it asks for no input from the user.

---

### Post by Gen2ly on 2007-12-15
Oh, btw, I'm using python-2.5.1-r4.  Is it possible the new version of python does this?

---

### Post by g2g591 on 2007-12-15
no python 2.5.1 works just fine. Im using 2.5.1-1ubuntu2 .

---

### Post by altonbr on 2007-12-15
> **jdong said:**
> There are command-line switches to predefine a max # of passes, in which case it asks for no input from the user.

Which are? There is no man page.

---

### Post by jdong on 2007-12-15
It takes --help, right? :D

---

### Post by articpenguin on 2007-12-26
is there a way to see the largest extent of free space?

---

### Post by psusi on 2007-12-27
I don't know of a way to get a number, but you can kind of see it visually by looking at the block map while running e2defrag.

---

### Post by articpenguin on 2007-12-27
isnt e2defrag bad though?

---

### Post by psusi on 2007-12-28
> **articpenguin said:**
> isnt e2defrag bad though?

In what way?

---

### Post by deepclutch on 2008-01-07
> **Dirk.R.Gently said:**
> I'm getting this message too.  I have installed already rsync.  Also I'm not using Ubuntu.  Is there another program that I need?

```
     Error defragmenting. Did the file disappear?
```I did "sudo make install" and am running the program under sudo.  I see this with any file directory I choose.  Any ideas?

I am also facing the same error! :( is there any resolution.defrag is not working with both Debian Sid and Ubuntu gutsy! :(
@jdong:Will you list the possible dependencies of the defrag packages?and if possible the resolution too!Thank You!:)

---

### Post by articpenguin on 2008-01-07
> **psusi said:**
> In what way?

after reading more about ext3. the largest extent of free space is a windows thing. Ext3 just looks for the largest free space to fit a file and place it there unlike windows which compacts every file at the beginning.

---

### Post by articpenguin on 2008-01-07
Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.

---

### Post by jdong on 2008-01-07
> **articpenguin said:**
>  unlike windows which compacts every file at the beginning.

Can you find any documentation that Windows does this? I find it hard to believe that any OS nowadays would use this kind of allocation strategy.

---

### Post by articpenguin on 2008-01-07
i am just saying that out of looking at the windows xp defragmenter analysis. Other people say it too all over the internet. after defragmentation all files are compacted except for small free space area and the rest of the free space after a small amount of blue shades on the bar. I think the small free space is the master file table space.

---

### Post by altonbr on 2008-01-07
> **articpenguin said:**
> i am just saying that out of looking at the windows xp defragmenter analysis. Other people say it too all over the internet. after defragmentation all files are compacted except for small free space area and the rest of the free space after a small amount of blue shades on the bar. I think the small free space is the master file table space.

I know what you're talking about, but I really think they mean "consolidating" not "compacting"...

---

### Post by jdong on 2008-01-07
> **articpenguin said:**
> i am just saying that out of looking at the windows xp defragmenter analysis. Other people say it too all over the internet. after defragmentation all files are compacted except for small free space area and the rest of the free space after a small amount of blue shades on the bar. I think the small free space is the master file table space.

I'm just saying I don't think this is an accurate picture of the NTFS allocation strategy in Windows. I'm absolutely sure it's much smarter than that, perhaps even more advanced than what ext3 does.

Also don't look at the XP defragmenter much -- it's a crippled version of an already crippled defragmenter suite. Any defragmenter that advertises a realtime defragment-each-file-after-write strategy as a FEATURE deserves to be shot! :D

---

### Post by covex on 2008-01-09
This tools is interesting. One note to -a (analysis). It prints the most importat information at the beginning of the output. When you analyze directory with a lot of file, this will overflow the terminal buffer and you see just useless end of output. Also it would be nice if it at least prints help for non root users. For me there is in this case this message:

```

/home/pb/bin/defrag:629: DeprecationWarning: raising a string exception is deprecated
  raise "** ERROR ** This tool requires root/sudo access."
Traceback (most recent call last):
  File "/home/pb/bin/defrag", line 629, in <module>
    raise "** ERROR ** This tool requires root/sudo access."

```

---

### Post by deepclutch on 2008-01-09
OK.I found the error.**defrag** needs **rsync** as dependency.@jdong:pls if possible list the major deps of this package :)

---

### Post by jdong on 2008-01-09
e2fsprogs, python, rsync... that should be it. I'd expect most people to have the first two, and all the cool people have rsync too!

---

### Post by articpenguin on 2008-01-10
> **jdong said:**
> I'm just saying I don't think this is an accurate picture of the NTFS allocation strategy in Windows. I'm absolutely sure it's much smarter than that, perhaps even more advanced than what ext3 does.

Also don't look at the XP defragmenter much -- it's a crippled version of an already crippled defragmenter suite. Any defragmenter that advertises a realtime defragment-each-file-after-write strategy as a FEATURE deserves to be shot! :D

before i ditched vista there were already 3000 fragmented files after a vista install with 12000 fragments. the install was done on a 160GB harddisk. that is bad if you ask me with 61Gbs of free space the largest extent after install.

---

### Post by maxime94 on 2008-02-09
Hi, I know this is ubuntuforums, but i have been trying to make this work on my gentoo with no success :

Error defragmenting. Did the file disappear?

I saw in this thread that this could be caused by a missing rsync, but I have it installed.
Python 2.4.4-r6
Rsync 2.6.9-r5
E2fsprog 1.40.4

Got any idea ?
Don't know any python, but is there a way to print the OSError exception to see what's wrong in more details maybe ?

---

### Post by alecz20 on 2008-03-19
I have a question about this defrag tool

If i set ubuntu Server edition with 2 identical HDD's in RAID 1 configuration, how would the defrag work?

Also, would it be possible to have it defrag one HDD at a time, so in case something happens the redundand drive will provide backup?

---

### Post by jdong on 2008-03-19
> **alecz20 said:**
> I have a question about this defrag tool

If i set ubuntu Server edition with 2 identical HDD's in RAID 1 configuration, how would the defrag work?

Also, would it be possible to have it defrag one HDD at a time, so in case something happens the redundand drive will provide backup?


No. RAID1 disks still show up as only one "disk", one "filesystem" to the OS. Pyfragtools operates on mounted filesystems at the file level, it does not understand or touch raw block devices in any way.

---

### Post by Andrew Sorensen on 2008-03-26
just ran it on my SuSE box (stumbled on this post) looks great.

---

### Post by s3a on 2008-03-29
I tried to find this in the applications menu but then assumed there was no GUI, having read again, there isn't..but, I typed "defrag" in the terminal window and it gave me this:

"deniz@deniz-desktop:~$ defrag
Couldn't determine filesystem type; please run the appropriate
defragmenter (e2defrag, edefrag, xdefrag, mdefrag) directly.
deniz@deniz-desktop:~$"

I don't understand what those options mean but I typed e2defrag and then got:

"deniz@deniz-desktop:~$ defrag
Couldn't determine filesystem type; please run the appropriate
defragmenter (e2defrag, edefrag, xdefrag, mdefrag) directly.
deniz@deniz-desktop:~$ e2defrag
Usage: e2defrag [-Vdrsv] [-i inode-list] [-b bad-inode] [-p pool-size] /dev/name
  -V : print full version information
  -d : debugging mode
  -r : read_only (testing) mode (implies -s)
  -s : show summary information
  -v : verbose (-vv is even more so)
  -n : runs without a picture
deniz@deniz-desktop:~$"

Can someone make it simple for me please? And FAT32's take longer to defragment because they have no journaling system?

What I want to know:
For a simple defrag of any filesystem (like ext3, FAT32, NTFS) what would I type initially and what do the different options mean?

---

### Post by Ux64 on 2008-04-04
There is lot of discussion is this thread.

Is the latest version in first post or is there some other location where I could get latest version?

- Thanks

It seems that the first post in this thread contains what I were looking for. ;)

---

### Post by sebbe1991 on 2008-04-20
> **maxime94 said:**
> Hi, I know this is ubuntuforums, but i have been trying to make this work on my gentoo with no success :

Error defragmenting. Did the file disappear?

I saw in this thread that this could be caused by a missing rsync, but I have it installed.
Python 2.4.4-r6
Rsync 2.6.9-r5
E2fsprog 1.40.4

Got any idea ?
Don't know any python, but is there a way to print the OSError exception to see what's wrong in more details maybe ?

You need to install lsof.

---

### Post by solarwind on 2008-04-29
> **sebbe1991 said:**
> You need to install lsof.

I'm running Arch Linux and I still have that problem.

---

### Post by solarwind on 2008-04-29
> **yopnono said:**
> I did find it, after reading the py script I did find rsync = I did not have it installed. :)

Thanks! That worked perfectly on Arch Linux to fix the problem!

---

### Post by jdong on 2008-04-29
Yeah, sorry, it uses rsync to perform the atomic copy. rsync is in the base ubuntu system.

---

### Post by stmiller on 2008-04-29
/begin rant

You don't really need to "defrag" your hard drive in Linux. Windows vomits bits of files all over the hard drive. Linux does not do this...

/end rant

---

### Post by jdong on 2008-04-29
> **stmiller said:**
> /begin rant

You don't need to "defrag" your hard drive in Linux. Windows vomits bits of files all over the hard drive. Linux does not do this...

/end rant

While this is mostly true (and thoroughly discussed in the README and in my original post), there **are** still some cases where Linux filesystems do not handle file fragmentation in an ideal manner, where this technique can help improve IO performance.

---

### Post by solarwind on 2008-04-29
> **jdong said:**
> While this is mostly true (and thoroughly discussed in the README and in my original post), there **are** still some cases where Linux filesystems do not handle file fragmentation in an ideal manner, where this technique can help improve IO performance.

You know how on winbloze, if you try to open a program, you instantly hear the hard drive clicking away?

In Linux, I never heard this sound, until I ran the defragmenter. I don't know what this sound is (perhaps the head on the hard drive moving back and forth) and I don't know if it's a good or bad thing.

---

### Post by jdong on 2008-04-29
> **solarwind said:**
> You know how on winbloze, if you try to open a program, you instantly hear the hard drive clicking away?

In Linux, I never heard this sound, until I ran the defragmenter. I don't know what this sound is (perhaps the head on the hard drive moving back and forth) and I don't know if it's a good or bad thing.

The clicking sound is the seek noise. That noise generally indicates poor IO performance due to the disk head jumping around the drive. It's neither good nor bad for the drive , it's something that the drive is designed to do as a part of its ordinary operation.

pyfragtools needs to gather tiny bits of information about a lot of files on your disk when you tell it to defrag a certain directory, which is located on different parts of a disk. That's why you hear that noise.

---

### Post by solarwind on 2008-04-29
> **jdong said:**
> The clicking sound is the seek noise. That noise generally indicates poor IO performance due to the disk head jumping around the drive. It's neither good nor bad for the drive , it's something that the drive is designed to do as a part of its ordinary operation.

pyfragtools needs to gather tiny bits of information about a lot of files on your disk when you tell it to defrag a certain directory, which is located on different parts of a disk. That's why you hear that noise.

OOps, that not what I meant. I meant that I hear the noise when I launch a large application after I have defragmented that application's directory. I was asking if that since I hear it more so now (after defragmenting), than before, that if it means better or worse performance.

---

### Post by jdong on 2008-04-30
It likely means worse performance. See warning on the first post about blindly defragmenting large sections of the filesystem.

---

### Post by solarwind on 2008-04-30
> **jdong said:**
> It likely means worse performance. See warning on the first post about blindly defragmenting large sections of the filesystem.

I just defragmented ONE directory which contains my program.

---

### Post by articpenguin on 2008-04-30
i defragmented my flightgear scenery directory and i noticed that the scenery loads a little slower than faster maybe the pyfragtools moved the files far away from the other scenery files talking. All the scenery added upto 500k files.

---

### Post by jdong on 2008-05-01
> **articpenguin said:**
> i defragmented my flightgear scenery directory and i noticed that the scenery loads a little slower than faster maybe the pyfragtools moved the files far away from the other scenery files talking. All the scenery added upto 500k files.


Yeah pyfragtools can't and doesn't make any guarantees about relative fragmentation of a cluster of files. Hence why it probably should never be used with a set of small files ( a quick tar and restore is more appropriate)

---

### Post by solarwind on 2008-05-01
> **jdong said:**
> Yeah pyfragtools can't and doesn't make any guarantees about relative fragmentation of a cluster of files. Hence why it probably should never be used with a set of small files ( a quick tar and restore is more appropriate)

Hmm, so what's the best way to *reverse* the effect of this? What do you mean by tar and restore? Do you mean just tar up the files, delete the originals and extract the tarball?

---

### Post by jdong on 2008-05-01
> **solarwind said:**
> Hmm, so what's the best way to *reverse* the effect of this? What do you mean by tar and restore? Do you mean just tar up the files, delete the originals and extract the tarball?


That's my best recommendation of how to encourage ext3 to write files together.

It's not guaranteed to work, as ext3 makes no contractual obligation about placement of files at all.

---

### Post by solarwind on 2008-05-01
> **jdong said:**
> That's my best recommendation of how to encourage ext3 to write files together.

It's not guaranteed to work, as ext3 makes no contractual obligation about placement of files at all.

But I bet it's likely to work if I have lots of free space (I think). I'll read up on filesystems before making assumptions.

---

### Post by Gripp on 2008-05-01
what about running it on a Wubi install?

not that i'm going to try, but what would happen?

---

### Post by jdong on 2008-05-01
> **solarwind said:**
> But I bet it's likely to work if I have lots of free space (I think). I'll read up on filesystems before making assumptions.


I believe ext2/3, based on berkeley FFS inspiration, does use some heuristics that files inthe same directory or written close to each other in time should go to the same allocation area. Don't quote me on that :D

---

### Post by articpenguin on 2008-05-01
yeah ext3 does try to place files in the same block group.

There are two policies for allocating an inode.  If the new inode is
 * a directory, then a forward search is made for a block group with both
 * free space and a low directory-to-inode ratio; if that fails, then of
 * the groups with above-average free space, that group with the fewest
 * directories already is chosen.

IRC JFS also does this too.

---

### Post by solarwind on 2008-05-04
Wow, tar and untar works really well to regroup the files! HUGE improvement! Thanks jdong!

---

### Post by Ux64 on 2008-05-05
> **stmiller said:**
> 
You don't really need to "defrag" your hard drive in Linux. Windows vomits bits of files all over the hard drive. Linux does not do this...


Yes and no. Did you also check this thread? [http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

I personally think that running defrag a few times a year doesn't do any harm.

Also another interesting point is that ext4 is going to "fix the problem". Why bother fixing it, if it's not a problem?

[quote=Wikipedia]
Online defragmentation

Ext4 will eventually also have an online defragmenter. Even with the various techniques used to avoid it, a long lived file system does tend to become fragmented over time. Ext4 has a tool which can defragment individual files or entire file systems
[/quote]

This is working beautifully. I think that my ext3 drives had supprisingly high fragmentation. Shockingly high fragments / MB ratio is propably caused due small fragmented files. I decided to defrag my system drive, but not to defrag my data drive. Because there is no point to defrag 4 GB files because it's in two fragments. ;)

Vista's defrag now aims to defragment data to 64 megabyte blocks. So allowed level of fragmentation is 1 fragment per 64 megabytes or 0.015 fragments / MB.

Thanks! It did just what is was supposed to do. Results:

```

**System Drive**

Frags/MB Before:         109503.82
Frags/MB After:          259.66

**Data Drive**

Frags/MB Before:         2358.55
Frags/MB After:          0.17


```

---

### Post by s3a on 2008-06-30
Is there a 64-bit version? Because so far, I've got it running only on my laptop (32-bit).

Thanks for the app btw!

---

### Post by solarwind on 2008-06-30
> **s3a said:**
> Is there a 64-bit version? Because so far, I've got it running only on my laptop (32-bit).

Thanks for the app btw!

It's a Python script so it should run anywhere...

---

### Post by s3a on 2008-07-02
The .deb said i386 only. Do I need to compile something?

---

### Post by solarwind on 2008-07-02
> **s3a said:**
> The .deb said i386 only. Do I need to compile something?

No no, just download the source from the top of this thread.

---

### Post by solarwind on 2008-07-13
Just found that this tool works wonders on JFS. On extn filesystems, this seems to worsen the fragmentation problem, but on JFS, it improves it a LOT.

---

### Post by articpenguin on 2008-07-14
> **solarwind said:**
> Just found that this tool works wonders on JFS. On extn filesystems, this seems to worsen the fragmentation problem, but on JFS, it improves it a LOT.

Thats because JFS is not like ext3 with thousands of block groups on large voulmes. JFS only uses 64 to 128AGs.

---

### Post by bigbear2350 on 2008-09-13
Im obessed with linux filesystems i know most of the internals and all there features (B+trees,inode placement) but the one i dont get is reiserfs.

Do you if reiserfs is broken up into block groups like ext3? Does it track files in extents or indirect blocks like ext2/3?

---

### Post by jdong on 2008-09-13
> **bigbear2350 said:**
> Im obessed with linux filesystems i know most of the internals and all there features (B+trees,inode placement) but the one i dont get is reiserfs.

Do you if reiserfs is broken up into block groups like ext3? Does it track files in extents or indirect blocks like ext2/3?
I'm not a filesystem expert but I don't think reiserfs is subdivided into block groups; it tracks files in extents through a B+tree

---

### Post by solarwind on 2008-09-13
> **bigbear2350 said:**
> Im obessed with linux filesystems i know most of the internals and all there features (B+trees,inode placement) but the one i dont get is reiserfs.

Do you if reiserfs is broken up into block groups like ext3? Does it track files in extents or indirect blocks like ext2/3?

I think you could be a great help to me in writing a defragmenter and filesystem optimizer for JFS. Seriously. Can you pm me your email?

---

### Post by bigbear2350 on 2008-09-14
I guess i have to research reiserfs probably not even worth it anymore with hans in jail.

---

### Post by ShirishAg75 on 2008-11-03
Hi Jon Dong, 

Like your tool. 

Please look at this [lpbug]225361[/lpbug]
[]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361")
Now I'm looking for a way so I can use sudo to do my stuff without it coming in every time.

For e.g. I'm having something like this :-

  ```
Pass 1 of 10, 1/25 (4%): 502.1 frags/MB /usr/sbin/popularity-contest
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system
/home/shirish/.gvfs
      Output information may be incomplete.
     Fully defragmented!

```


Can something be done about the output it shows

Specifically

```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system
/home/shirish/.gvfs
      Output information may be incomplete.

```

---

### Post by jdong on 2008-11-03
That comes from "find /" traversing into a user's .gvfs directory which is denied from every user that didn't mount it (i.e. root). There's very little I can do about that error -- you could try using find -xdev instead of just find in the source.

---

### Post by ShirishAg75 on 2008-11-03
> **jdong said:**
> That comes from "find /" traversing into a user's .gvfs directory which is denied from every user that didn't mount it (i.e. root). There's very little I can do about that error -- you could try using find -xdev instead of just find in the source.

I have installed the .deb file, is there anyway I can change something somewhere or would I have to build the whole thing ? 

I don't have much skills so you would have to be explicit about which files, where and how I need to change stuff. Thanks in advance

---

### Post by ShirishAg75 on 2008-11-03
It is an interesting tool, perhaps you can comment a bit on some of the stuff 

```

Pass 1 of 10, 1782/1782 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 3.7)                                               

222222222222222222222222222222222222222222222222222222222222
===> Pass 2 of 10.0 <===    Remaining Fragmentation 21446/178921 (11%)
222222222222222222222222222222222222222222222222222222222222

 Pass 2 of 10, 375/375 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 5.6)                                               

333333333333333333333333333333333333333333333333333333333333
===> Pass 3 of 10.0 <===    Remaining Fragmentation 13655/178921 (7%)
333333333333333333333333333333333333333333333333333333333333

Pass 3 of 10, 318/318 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 13.2)                                              

444444444444444444444444444444444444444444444444444444444444
===> Pass 4 of 10.0 <===    Remaining Fragmentation 11596/178921 (6%)
444444444444444444444444444444444444444444444444444444444444

 Pass 4 of 10, 306/306 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 0.5)                                               

555555555555555555555555555555555555555555555555555555555555
===> Pass 5 of 10.0 <===    Remaining Fragmentation 10555/178921 (5%)
555555555555555555555555555555555555555555555555555555555555

  Pass 5 of 10, 292/292 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 5.9)                                               

666666666666666666666666666666666666666666666666666666666666
===> Pass 6 of 10.0 <===    Remaining Fragmentation 7634/178921 (4%)
666666666666666666666666666666666666666666666666666666666666

 Pass 6 of 10, 264/264 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 11.0)                                              

777777777777777777777777777777777777777777777777777777777777
===> Pass 7 of 10.0 <===    Remaining Fragmentation 6655/178921 (3%)
777777777777777777777777777777777777777777777777777777777777

Pass 7 of 10, 256/256 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 2.4)                                               

888888888888888888888888888888888888888888888888888888888888
===> Pass 8 of 10.0 <===    Remaining Fragmentation 6335/178921 (3%)
888888888888888888888888888888888888888888888888888888888888

  Pass 8 of 10, 251/251 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 9.7)                                               

999999999999999999999999999999999999999999999999999999999999
===> Pass 9 of 10.0 <===    Remaining Fragmentation 5418/178921 (3%)
999999999999999999999999999999999999999999999999999999999999

 Pass 9 of 10, 239/239 (100%): 0.5 frags/MB /usr/share/openssl-blacklist/blacklist.RSA-2048
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (0.5 --> 5.4)                                               

101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010
===> Pass 10 of 10.0 <===    Remaining Fragmentation 5275/178921 (2%)
101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010101010

```

As one can see progressively the number of files come down the biggest changes being in the 1st and the 2nd pass and then it becomes gradual affair. 

After all the passes are done one gets a menu like this 

```

========= COMPLETE ===========
Remaining Fragmented Files:
0.51    /usr/share/openssl-blacklist/blacklist.RSA-2048
0.54    /usr/bin/ecj-gcj
0.55    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0.57    /usr/share/icons/hicolor/icon-theme.cache
2.46    /usr/lib/libguile.so.17.2.0
0.89    /usr/share/midi/freepats/Tone_000/001_Acoustic_Brite_Piano.pat
1.70    /usr/lib/libdb-4.6.so
4.99    /usr/lib/libstlport_gcc.so.4.6
8.81    /usr/share/inkscape/tutorials/tutorial-elements.ca.svg
8.87    /usr/bin/eog
1.92    /usr/lib/libdjvulibre.so.21.0.0
9.10    /usr/bin/dpkg-deb
4.75    /usr/lib/xscreensaver/lattice
9.51    /usr/lib/libsidplay.so.1.0.3
9.57    /usr/bin/install-menu

```

Request :- Now if this listing could be a little more cleared up so it becomes a sequential list  when showing still fragmented file it would be nicer still. 

Now I'll like to know what does the following mean/show 

```

Pass 9 of 10, 2/239 (0%): 8.3 frags/MB /usr/share/doc/xserver-xorg-core/changelog.gz
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (8.3 --> 60.3)                                              

```

What does this denote 

```
No improvement (8.3 --> 60.3)
```

Lastly this is what we are  trying to do :-

```

Pass 1 of 5, 127/1274 (9%): 202.0 frags/MB /var/lib/defoma/pango.d/id-cache.monospace_other
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     Fully defragmented!  

```                     


A quick note, the gvfs thing is a error on my system, yours would be much much cleaner.

---

### Post by jdong on 2008-11-03
> **ShirishAg75 said:**
> It is an interesting tool, perhaps you can comment a bit on some of the stuff 


As one can see progressively the number of files come down the biggest changes being in the 1st and the 2nd pass and then it becomes gradual affair. 


That's correct, and expected behavior -- the best improvement will be made in the first few passes then the benefits drop off.

> 
After all the passes are done one gets a menu like this 
...

Request :- Now if this listing could be a little more cleared up so it becomes a sequential list  when showing still fragmented file it would be nicer still. 

The data is sorted by maximum number of fragments without regard to filesize. The change to frags/MB was made quite late in the development of the tool.


> 
Now I'll like to know what does the following mean/show 

```

Pass 9 of 10, 2/239 (0%): 8.3 frags/MB /usr/share/doc/xserver-xorg-core/changelog.gz
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/shirish/.gvfs
      Output information may be incomplete.
     No improvement (8.3 --> 60.3)                                              

```

What does this denote 


The original file had 8.3 fragments per MB. The attempted defrag resulted in a file with 60.3 fragments per MB. This is worse than before defragmentation, so the candidate "defragmented" file is deleted and we give up on this file for this pass.

> 
A quick note, the gvfs thing is a error on my system, yours would be much much cleaner.

aha, I know now, this error comes from lsof. Redirecting 2>/dev/null will get rid of those errors.

---

### Post by psusi on 2008-11-03
It seems that it should not cross mount points by default, since usually when you run a defrag, you want to defrag a disk, not all disks that are mounted under it.  This will also prevent the gvfs errors.

---

### Post by jdong on 2008-11-03
Well one could argue that pyfragtools doesn't defrag disks -- it defrags files under a directory. And in that case recursing into mountpoints is a reasonable behavior (i.e. make all files in /srv/torrents access faster!)

---

### Post by ShirishAg75 on 2008-11-04
> **jdong said:**
> 
aha, I know now, this error comes from lsof. Redirecting 2>/dev/null will get rid of those errors.

So you think this is ok 

```
 
sudo defrag /home/shirish/Documents/ 2> /dev/null

```

---

### Post by jdong on 2008-11-04
Yes, but why the heck are you defragging documents? That's entirely unproductive.

---

### Post by ShirishAg75 on 2008-11-05
That was just an example, just wanting to know the right way/usage to use the command. Also it makes it easier to use some dummy files on which to try stuff before trying big files like torrents and what not. (Read really big files)

 Although I have come up with an issue whenever I use that command . For e.g. 

```

$ sudo defrag /home/shirish/Documents/ 2> /dev/null

```

Now look at the output :-

```

[sudo] password for shirish: 
Building list of files to analyze... done!

Analyze finished. 9.4 % fragmentation (18 files), 84.8 average frags/MB
Fragmented files:
353.12    /home/shirish/Documents/september2008report.odt
271.51    /home/shirish/Documents/septemberreport.abw.bak~
196.55    /home/shirish/Documents/resume251008.pdf
192.62    /home/shirish/Documents/september2008report.doc
161.88    /home/shirish/Documents/Googles_response_to_orphan_works.pdf
129.66    /home/shirish/Documents/september2008report.abw
58.18    /home/shirish/Documents/paycommresol.pdf
50.97    /home/shirish/Documents/APC_BR800IN_manual.pdf
47.47    /home/shirish/Documents/APC_UPS_500.rar
20.63    /home/shirish/Documents/LongTail.pdf
...


```

Now after coming to ... its kinda waiting for something, it waits for an enormous time, should it be functioning like this?

---

### Post by jdong on 2008-11-05
Yes, that's correct behavior. We need a full list of all the files in your Documents folder, which is built using the "find" command. This requires a stat() call to each file in those directories, which can take sometime. It's unknown how many files there are so I can't really display any useful progress information, not to mention drawing a progress bar for that could double or triple the amount of time the process takes.

---

### Post by ShirishAg75 on 2008-11-05
there could be an optional flag or something like that which will make the progress bar, how do you feel about that?

---

### Post by jdong on 2008-11-05
> **ShirishAg75 said:**
> there could be an optional flag or something like that which will make the progress bar, how do you feel about that?

Please, I beg you to carefully read and understand what I am saying before making suggestions. I just explained that it is not possible to compute a progress bar. A progress bar requires two pieces of information: The number of steps in total and the current number of steps completed. We do not KNOW how many steps there are in total -- that's what we're trying to calculate at this point so that the main defrag process has a progress bar!

The best one can do at that stage is spewing a bunch of dots to the screen which IMO doesn't tell you anything other than your computer's not dead. If you want to do that, write a patch and maintain a bzr branch of that. I'm not interested in wasting my time writing something utterly pointless.

---

### Post by JNelson on 2008-11-14
Does this take into account the free space fragmentation of the filesystem? Or does it just relie on the filesystems allocation policy?

---

### Post by jdong on 2008-11-14
> **JNelson said:**
> Does this take into account the free space fragmentation of the filesystem? Or does it just relie on the filesystems allocation policy?

The latter -- this is a very dumb/naive defragmentation strategy that will probably damage free space fragmentation more than anything else. Until we have a better defrag API such as the one ext4 will be adding in the near future, this is as good as we can get without taking serious risks.

---

### Post by Ux64 on 2008-11-17
> **jdong said:**
> this is a very dumb/naive defragmentation strategy that will probably damage free space fragmentation more than anything else.

100% agree. But it's still better than nothing. 

Here's an old thread about defragmentation. 

[http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

"There is no need for it". ;)

I'm waiting for ext4.

---

### Post by jdong on 2008-11-17
> **Ux64 said:**
> 100% agree. But it's still better than nothing. 

Here's an old thread about defragmentation. 

[http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

"There is no need for it". ;)

I'm waiting for ext4.

Well, I tried to explain in the README file and original post the "need" for defragmentation. You're right that IN GENERAL there is no need to defragment files in Linux, but I point out that in the special case of files that slowly grow (maybe at 1MB per minute) to large sizes (~5GB or more), there could be a good amount of fragmentation (20,000 'fragments', 100 or more per MB) that leads to a noticeable degradation in read performance (10MB/s on a 60MB/s+ capable drive)

For this specific case, pyfragtools manages to defragment the file pretty effectively just by rewriting it in one fell swoop. But, you are absolutely right in general there's no need to do full-disk defragmentation on Linux filesystems, and the pyfragtools documentation specifically discourages this practice too.

---

### Post by Ux64 on 2008-12-04
> **jdong said:**
> Well, I tried to explain in the README file and original post the "need" for defragmentation.

Sorry, I was trying to be sarcastic. It's difficoult often.

Anyway here's one quite new article about ext3 and fragmentation.

[http://www.heise-online.co.uk/open/Tuning-the-Linux-file-system-Ext3--/features/110398/3](http://www.heise-online.co.uk/open/Tuning-the-Linux-file-system-Ext3--/features/110398/3)

And yes, I have been all the asking for defragging tool. I have long experience with disks and file systems. And I know it's "required" to maintain proper performance.

Here's another thread about it in UbuntuForums.

[http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

- Thanks. I monthy run your defrag this defrag tool on system drive. 

On "storage drives" I don't run it, because it's not needed even drives are almost completely full. And files on those ddrives aren't accessed often and even if they're accessed it's not time critical. Like playing avi or mp3.

---

### Post by linuxology on 2008-12-04
marked for later

---

### Post by JNelson on 2008-12-05
Block groups are bad IMO. The metadata structures in ext3 have a giant Overhead. There is one bitmap+One Inode Bitmap per block group, then there is the inode tables. Yeah they increase locatality but in the end when free space starts to shrink ext3 will have trouble finding big gaps of free space for its allocations.

---

### Post by JNelson on 2008-12-05
I  forgot to add that finding free space increases when the total free space in the volume is low. As a typical ext3 500GB filesystem will have around 3.2K Free space bitmaps. IMO There should only be 1 Bitmap per filesystem like in ntfs,HFS+ and i beleive in zfs too. This results in less head seeks to find free space.

---

### Post by jdong on 2008-12-05
XFS solves this by adding an augmented B*-tree that is indexes free space sorted by largest contiguous size.

---

### Post by psusi on 2008-12-05
> **JNelson said:**
> I  forgot to add that finding free space increases when the total free space in the volume is low. As a typical ext3 500GB filesystem will have around 3.2K Free space bitmaps. IMO There should only be 1 Bitmap per filesystem like in ntfs,HFS+ and i beleive in zfs too. This results in less head seeks to find free space.

NTFS and HPFS do not keep the allocation bitmaps all in one spot either.  They are spread throughout the disk just like ext2.  Because of block groups you often only need to check the local bitmap to find a free block in that group, rather than reading the entire bitmap on the far side of the disk.  That means less time spent seeking, and so less time spent allocating a new block.

---

### Post by JNelson on 2008-12-05
> **psusi said:**
> NTFS and HPFS do not keep the allocation bitmaps all in one spot either.  They are spread throughout the disk just like ext2.  Because of block groups you often only need to check the local bitmap to find a free block in that group, rather than reading the entire bitmap on the far side of the disk.  That means less time spent seeking, and so less time spent allocating a new block.


HPFS divides space into bands, NTFS dosent, There is only 1 Bitmap. That bitmap is one of the first 24 MFT records when NTFS is first created. [http://en.wikipedia.org/wiki/NTFS#Metafiles](http://en.wikipedia.org/wiki/NTFS#Metafiles)

6 	$Bitmap 	An array of bit entries: each bit indicates whether its corresponding cluster is used (allocated) or free (available for allocation).

---

### Post by JNelson on 2008-12-05
> **jdong said:**
> XFS solves this by adding an augmented B*-tree that is indexes free space sorted by largest contiguous size.

Is a B*-tree better than a bitmap? I imagine a bitmap is a table right?

---

### Post by jdong on 2008-12-05
> **JNelson said:**
> Is a B*-tree better than a bitmap? I imagine a bitmap is a table right?

Well a bitmap can be a sublinear-access-time data structure too. The XFS implementation is O(1) (constant-time) cheap access to the largest contiguous block of space, and still sublinear time for updating this tree after that space has been used up.

This allows for XFS to allocate things really fast even on fairly full drives.

---

### Post by psusi on 2008-12-05
> **JNelson said:**
> HPFS divides space into bands, NTFS dosent, There is only 1 Bitmap. That bitmap is one of the first 24 MFT records when NTFS is first created. [http://en.wikipedia.org/wiki/NTFS#Metafiles](http://en.wikipedia.org/wiki/NTFS#Metafiles)

6 	$Bitmap 	An array of bit entries: each bit indicates whether its corresponding cluster is used (allocated) or free (available for allocation).

This is not correct.  NTFS takes much from HPFS, including dividing the disk up into groups with bitmaps located between the groups.  The $Bitmap file is an entry in the first 24 MFT records that gives a name to the bitmap data and describes its location.  You can think of it as a file that has fragments spread out over the disk in very specific locations ( between each block group ).  $Bitmap is a convenient way of viewing the bitmap data as a single logical file, but it's data is spread out on the disk.

---

### Post by JNelson on 2008-12-05
> **psusi said:**
> This is not correct.  NTFS takes much from HPFS, including dividing the disk up into groups with bitmaps located between the groups.  The $Bitmap file is an entry in the first 24 MFT records that gives a name to the bitmap data and describes its location.  You can think of it as a file that has fragments spread out over the disk in very specific locations ( between each block group ).  $Bitmap is a convenient way of viewing the bitmap data as a single logical file, but it's data is spread out on the disk.

Do you care to show a link that shows this? I read the inside windows 2000 Book and it dosent say anything about ntfs being divided in to groups

---

### Post by JNelson on 2008-12-05
[http://www.easeus.com/resource/ntfs-disk-structure.htm](http://www.easeus.com/resource/ntfs-disk-structure.htm)

Its divided up into 2 parts.


> NTFS disk is symbolically divided into two parts. The first 12% of the disk are assigned to so-called MFT area - the space which MFT metafile grows into. Any data recording into this area is impossible. The MFT area is always kept empty not to let the most important service file (MFT) be fragmented at growth. The rest 88% of the disks represent usual space for files storage.

---

### Post by psusi on 2008-12-05
> **JNelson said:**
> Do you care to show a link that shows this? I read the inside windows 2000 Book and it dosent say anything about ntfs being divided in to groups

Helen Custer's "Inside NTFS" is a good reference book.

> **JNelson said:**
> [http://www.easeus.com/resource/ntfs-disk-structure.htm](http://www.easeus.com/resource/ntfs-disk-structure.htm)

Its divided up into 2 parts.

That's a bit of a distortion.  The disk is not divided into 2 parts per se, it's just the windows ntfs driver will not allocate the free blocks following the MFT unless the rest of the disk is full.  The size of that reserved area is configurable via a registry parameter.  I'm pretty sure that linux will happily place files there.

One of the advantages of having the $Bitmap file there to describe the location of the bitmap blocks is that in theory, they can be located anywhere, even in a contiguous stretch at the start of the disk, but in practice, they are always spread out in evenly spaced groups when the filesystem is formatted.  At least, that is how Windows' format does it, I'm not positive about the ntfs mkfs in linux, but it probably works the same way.

Similarly, in theory the allocation bitmaps in ext do not have to be located at the start of each volume group before the data blocks; that's just where mkfs puts them.  Their location is specified in the group descriptor so they could go somewhere else.

---

### Post by s3a on 2009-02-16
Is this in the repositories or only downloadable as a .deb installer?

---

### Post by ubnewbie2 on 2009-02-17
> **s3a said:**
> Is this in the repositories or only downloadable as a .deb installer?

Just download the tar attached to the first message in this thread, extract, and run the defrag script.

---

### Post by jdong on 2009-02-17
> **ubnewbie2 said:**
> Just download the tar attached to the first message in this thread, extract, and run the defrag script.

The above is the recommended approach. The deb conflicts with an existing package that provides an (unrelated) defrag command; I wrote the deb a long time ago without realizing this was the case. The script does not really take any installation; it is self-contained and simply requires rsync to be installed (which is the case unless you uninstalled it intentionally)

---

### Post by ubnewbie2 on 2009-02-17
I am thinking of trying this on my mythbuntu machine.  Typical of small mythtv installs, it has a recordings directory where many huge files have been written, deleted, and rewritten many times, sometimes by 3 or more processes at the same time (3 tuners)  I'll bet there's plenty of defragmentation.

The biggest files can be 30GB or more, although 5GB is probably more typical.  The drive is 500GB.  I wonder how much free space I should make before trying to defrag using pyfragtools?  More than 30GB if I want to defrag the big files? ;)    I also wonder how often I will need to run it, as this machine records about 20GB a day (mythtv just deletes the oldest recordings to make room - so the disk can run quite full at times).

There's also a setting in mythtv to force it to leave a specified amount of disk free always.  Maybe I should set that to be bigger, say 50GB ?

---

### Post by jdong on 2009-02-17
Yes -- in general the more free space the less fragmentation you will encounter. For something like a Mythbuntu setup I would leave 25% or more of the disk free to avoid scouring the disk for that last way to fragment the file into 5000 pieces and store it!


Also consider using XFS which performs better for your tasks (more resistent to fragmentation of large files). It also has a built-in defragger that works on much of the same principles as here.

---

### Post by TheUnderTaker on 2009-03-15
ext4+delayed allocation almost eliminates fragmentation for me. I have 155k Files on my 8GB / partition and only 100 of those are fragmented with 32% space used.

---

### Post by jdong on 2009-03-15
> **TheUnderTaker said:**
> ext4+delayed allocation almost eliminates fragmentation for me. I have 155k Files on my 8GB / partition and only 100 of those are fragmented with 32% space used.

Yeah, ext4 and other FS'es using delayed allocation significantly prevent fragmentation of huge files.

---

### Post by angazi on 2009-06-09
Looks promising, just installed it - version from post 1 of this thread - untarred and installed the .deb from the archive on 9.04 server (jeos) running within a VM

Install seemed happy. No issues with dependencies, etc.

However, defrag doesnt appear to be doing much - see below - any ideas?

or is my issue just this

JDong quote "The deb conflicts with an existing package that provides an (unrelated) defrag command; I wrote the deb a long time ago without realizing this was the case" /quote

Thanks

I see output like this ... (edited for brevity)

jira@jira:~$ sudo defrag ~
Building list of files to analyze... done!
                                                                               
Analyze finished. 0.2 % fragmentation (22 files), 71.3 average frags/MB
Fragmented files:
327.42	/home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml~
327.42	/home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml.ori
[...]

How many passes to run? [10] 5
/usr/sbin/defrag:581: DeprecationWarning: integer argument expected, got float
  for k in xrange(0,abs(passes)):

111111111111111111111111111111111111111111111111111111111111
===> Pass 1 of 5.0 <===    Remaining Fragmentation 1568/1568 (99%)
111111111111111111111111111111111111111111111111111111111111

  Pass 1 of 5, 1/22 (4%): 327.4 frags/MB /home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml~
     Error defragmenting. Did the file disappear?

  Pass 1 of 5, 2/22 (9%): 327.4 frags/MB /home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml.ori
     Error defragmenting. Did the file disappear?

[...] etc

---

### Post by angazi on 2009-06-09
Nope, doesnt seem like its related to .deb issue.

Just tried the script approach on 9.04 server.

Have I misunderstood anything or any ideas why it 'aint working for me?

Made defrag existing in pyfragtools-0.1 executable and ...
jira@jira:~/Desktop/pyfragtools-0.1$ sudo ./defrag ~
Building list of files to analyze... done!
                                                                               
Analyze finished. 0.2 % fragmentation (24 files), 79.3 average frags/MB
Fragmented files:
327.42	/home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml~
327.42	/home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml.ori
...
How many passes to run? [10] 1
./defrag:581: DeprecationWarning: integer argument expected, got float
  for k in xrange(0,abs(passes)):

111111111111111111111111111111111111111111111111111111111111
===> Pass 1 of 1.0 <===    Remaining Fragmentation 1902/1902 (99%)
111111111111111111111111111111111111111111111111111111111111


  Pass 1 of 1, 1/24 (4%): 327.4 frags/MB /home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml~
     Error defragmenting. Did the file disappear?

  Pass 1 of 1, 2/24 (8%): 327.4 frags/MB /home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml.ori
     Error defragmenting. Did the file disappear?

  Pass 1 of 1, 3/24 (12%): 226.8 frags/MB /home/jira/.gnome2/accels/gedit
     Error defragmenting. Did the file disappear?

  Pass 1 of 1, 4/24 (16%): 216.4 frags/MB /home/jira/.gnome2/accels/nautilus
     Error defragmenting. Did the file disappear?

  Pass 1 of 1, 5/24 (20%): 128.0 frags/MB /home/jira/.mozilla/firefox/8f1qyzu3.default/secmod.db
     Error defragmenting. Did the file disappear?

  Pass 1 of 1, 6/24 (25%): 90.4 frags/MB /home/jira/.gconfd/saved_state
     File is open for write, skipping...

---

### Post by jdong on 2009-06-09
Make sure rsync is installed. It seems to have disappeared from the stock install since then.

---

### Post by rookcifer on 2009-06-09
> **jdong said:**
> Hey, guess who got bored last weekend on a robotics trip and decided to write a Linux defragger? ;-)



Nice job, but sadly such a tool is as worthless as Linux anti-virus.  This is especially true if you use ext4.

---

### Post by Wiebelhaus on 2009-06-09
Coolness , thanks Jdong , It's very much appreciated !

---

### Post by tcoffeep on 2009-06-10
This is pretty sweet. :)

---

### Post by Ux64 on 2009-06-15
I just figured out that this tool can be used to convert files from ext3 to ext4 before e4defrag is ready. Actually it would be good idea to force copying every file on file system once so conversion would be done for all files. Not only fragmented files.

Btw. This defrag tool naturally works better with ext4 than ext3 because ext4 is more efficient on placing data on disk without fragmenting it.

Any thoughts about that "copy all fiels once" approach?

---

### Post by angazi on 2009-06-15
[QUOTE=angazi;7427608]Nope, doesnt seem like its related to .deb issue.

Just tried the script approach on 9.04 server (and also not working)

Have I misunderstood anything or any ideas why it 'aint working for me?


How many passes to run? [10] 1
./defrag:581: DeprecationWarning: integer argument expected, got float
  for k in xrange(0,abs(passes)):

 Pass 1 of 1, 1/24 (4%): 327.4 frags/MB /home/jira/atlassian-jira-enterprise-3.13.4/edit-webapp/WEB-INF/classes/entityengine.xml~
     Error defragmenting. Did the file disappear?


Aha, thanks for the suggestion,

apt-get rsync did the job 100% :-)

defrag working great now.

---

### Post by Ux64 on 2009-07-04
Does pydefrag too use ext4 pre-alloaction? If it does, it should technically lead to situation where multiple rounds aren't required, because files are defragged on first try. (unless free space is too fragmented).

---

### Post by tcoffeep on 2009-07-05
```
Building list of files to analyze... done!
| /home/lbrandon/.wine/driv [                           ]      3/19753 (  0.0%)Traceback (most recent call last):
  File "./defrag", line 647, in <module>
    run(opts[1][0], threshold, passes)
  File "./defrag", line 554, in run
    f=numfrags(file)
  File "./defrag", line 541, in numfrags
    return frags/(os.path.getsize(file)/1024.0/1024.0)
ZeroDivisionError: float division

```

what happened??


[edit]:

happens in the version in the ppa :

```

Building list of files to analyze... done!
| /home/lbrandon/.wine/driv [                           ]      3/19753 (  0.0%)Traceback (most recent call last):
  File "/usr/sbin/pydefrag", line 669, in <module>
    run(args[0], threshold, passes)
  File "/usr/sbin/pydefrag", line 570, in run
    f=numfrags(file)
  File "/usr/sbin/pydefrag", line 556, in numfrags
    return frags/(os.path.getsize(file)/1024.0/1024.0)
ZeroDivisionError: float division

```

It also does this when doing any folder (for me, anyways).

---

### Post by tcoffeep on 2009-07-05
Okay! I had a friend of mine look at it, and with his suggestion, I editted line 556 :
```

  return frags/(os.path.getsize(file)/1024.0/1024.0)
```

And removed the /(os.path.get[etc]

After that, it began to work again. It seems it was reading wrong or something, and dividing by 0

---

### Post by jdong on 2009-07-07
Ah, good catch. Seems like zero-sized files will trip a division by zero (0/1024/1024 is still zero)

---

### Post by tcoffeep on 2009-07-07
So, I'm looking for a way around it.

Right now,

I have the line doing this :

```

if os.path.getsize(file)/1024.0/1024.0 != 0:
    return frags/(os.path.getsize(file)/1024.0/1024.0)
else:
    sys.exit(file)

```

But that only kills it letting me know what file is the reason for the breaking. I'm looking for a way to move onto the next file, ignoring it. Any ideas?

---

### Post by tcoffeep on 2009-07-07
Highlighted the fix (line 570) :

[http://pastebin.com/fb79a812](http://pastebin.com/fb79a812)

It works now. :)

---

### Post by Supersquirrel on 2009-07-07
I think filesystems should do what HFS+ does.

Keep track of frequently used files and put them in a special area. 

HFS+ uses a metadata zone where all the B-trees are stored like the catalog b-tree and extents b-tree. In the metadata zone is space reserved for frequently used files. HFS+ puts them there and headseeking is reduced since the catalog is at the beginning of the disk along with the hotfile space.

---

### Post by jdong on 2009-07-09
> **Supersquirrel said:**
> I think filesystems should do what HFS+ does.

Keep track of frequently used files and put them in a special area. 

HFS+ uses a metadata zone where all the B-trees are stored like the catalog b-tree and extents b-tree. In the metadata zone is space reserved for frequently used files. HFS+ puts them there and headseeking is reduced since the catalog is at the beginning of the disk along with the hotfile space.

In addition to a hotzone HFS+'s OS X drivers also has automatic idle-priority defragmentation scheduling on files that would benefit from the treatment.

NTFS and Windows also employ some highly intelligent disk optimization techniques; not only are hot files batched together at the front of the disk by ProcessIdleTasks() in advapi32, the OS also uses a time-ordered layout of bootup files that it prefetches as the bootup progresses. In addition, machine learning / AI techniques are used to monitor the pattern of file accesses (and partial file accesses) needed to start up various applications and the result is the creation of a Prefetch bundle for readahead launching of various troublesome applications.

---

### Post by killerabbit on 2009-07-15
when running in my home directory i'm getting an warning saying can't stat() fuse.gvfs-fuse-daemon file system /home/username/.gvfs. Output information may be incomplete. meaning?

---

### Post by ascariz on 2009-07-18
i think we do need defragmenter in linux.
i made a fat32 partition in ubuntu and after a long time, my sytem become slow. i mount my hard disk at windows and defrag the partition, my ubuntu become normal again after boot. so, there is an effect of defragmentation in ubuntu.
I found one software that can defrag the whole drive, folder and files.
The software is Power Defragmenter. You can find it here
[http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)
Of course you need Wine to run it. So, install wine first ok.
After Power Defragmenter installed, when you run it, it will ask to download contig from windows. you need to put the contig in the same folder of Power Defragmenter.
I compressed the complete Power Defragmenter and you can run it just like portable.
you can download it here..
[http://www.mediafire.com/download.php?jwjzzz1mdnw]("http://www.mediafire.com/?sharekey=f35bb7e27bfbecebd2db6fb9a8902bda")

---

### Post by ubdime on 2009-07-19
I'm all late to this thread. The original post was "Last edited by jdong; May 3rd, 2006 at 02:56 PM.."

Is the attachment to pyfragtools-0.1.tar.gz still the newest version? If not, on what page can I find it. Or is there a website? I tried googling and it only led me back here.

---

### Post by ubdime on 2009-07-20
> **ascariz said:**
> i think we do need defragmenter in linux.
i made a fat32 partition in ubuntu and after a long time, my sytem become slow. i mount my hard disk at windows and defrag the partition, my ubuntu become normal again after boot. so, there is an effect of defragmentation in ubuntu.

fragmentation is directly dependent on your filesystem.. but only indirectly dependent on your operating system because most people on linux run ext3.. if you're running fat32, i assume it's because you're dual booting.. in which case, sure, go ahead and dualboot to windows to defrag your fat32 partition

---

### Post by moster on 2009-07-20
> **ubdime said:**
> fragmentation is directly dependent on your filesystem.. but only indirectly dependent on your operating system because most people on linux run ext3.. if you're running fat32, i assume it's because you're dual booting.. in which case, sure, go ahead and dualboot to windows to defrag your fat32 partition

Buddy, if you suggest that ext3 cannot be fragmented you are very wrong. Download movie with transmission torrent and analyze it with filefrag utility. That movie will be so fragmented that will cut transfer rate in half.

---

### Post by ubdime on 2009-07-22
> **moster said:**
> Buddy, if you suggest that ext3 cannot be fragmented you are very wrong. Download movie with transmission torrent and analyze it with filefrag utility. That movie will be so fragmented that will cut transfer rate in half.

"Buddy", what I'm suggesting is that maybe you read posts before you reply. Why would I "suggest" that ext3 can't be fragmented when I asked just the post before about the newest version of pyfragtools. I'm obviously here because I wanted to download it to defrag my own ext3 fs.

I was replying to the poster above me who said that linux definitely needs a defragger because his fat32 fs is slow. While I think that linux/ext3 needs a defragger also, it has nothing to do with fat32, which is a ms fs with bad fragmentation management.

---

### Post by tcoffeep on 2009-07-22
Wow! Talk about aggressive!

Anyways! I really enjoyed using this program! Thank you to the developer. Due to the problems I came across, I had to read the source code and find and fix the problem, and I learnt a lot about Python and gained an appreciation for it, for I always preferred Perl, and I disliked controlled whitespace. Thank you, again!

---

### Post by moster on 2009-07-23
> **ubdime said:**
> "Buddy", what I'm suggesting is that maybe you read posts before you reply. Why would I "suggest" that ext3 can't be fragmented when I asked just the post before about the newest version of pyfragtools. I'm obviously here because I wanted to download it to defrag my own ext3 fs.

I was replying to the poster above me who said that linux definitely needs a defragger because his fat32 fs is slow. While I think that linux/ext3 needs a defragger also, it has nothing to do with fat32, which is a ms fs with bad fragmentation management.

I am very sorry, rage blind me a for minute. I take care of fragmentation manually and I was believing that everything is just fine until I check some of the files. I need defragger, badly.

---

### Post by MartenP on 2009-09-17
No progress. The program with fix by tcoffeep runs but it identififies all files like "fragmented" and the process of defragmentation says "no improvement".

This is the best defragmentation tool for Linux and I would like to see this tool working again. But I don't know Python...

---

### Post by ubongo2008 on 2009-09-17
> **TheCaptain said:**
> O&O has had a defragmenter for Linux for years, i tried it on servers, the database efficiancy went up by... 0%, not measurable.

You can try this out if you have a recent backup and a lot of time on your hands but the real reason one is not provided in ANY distro is that it's not needed, the improvements aren't measurable.


IMHO ext3, ext4 doesn't need something like an defragmenter because of the filesystem  it just doesn't fragment files. maybe in some cases it would be good to pack files near together on the drive but i think ext does not fragment files (nor do SSD's by design)

well at least that is what i learned some time ago in my class

Edit: concerning the time ... i think an backup and restore of the partition will be faster with same benefits if not done sector by sector

EDIT: ok there seems to be some fragmentation too but also seems to be minimal ... no comparison to windows ntfs at all

---

### Post by jdong on 2009-09-18
> **ubongo2008 said:**
> IMHO ext3, ext4 doesn't need something like an defragmenter because of the filesystem  it just doesn't fragment files. maybe in some cases it would be good to pack files near together on the drive but i think ext does not fragment files (nor do SSD's by design)

well at least that is what i learned some time ago in my class

Edit: concerning the time ... i think an backup and restore of the partition will be faster with same benefits if not done sector by sector

EDIT: ok there seems to be some fragmentation too but also seems to be minimal ... no comparison to windows ntfs at all


This is a long long thread, but compelling cases have been made in the first few pages of when ext3 and ext4 indeed DO get fragmented (try downloading a 10GB torrent at 10KB/s without preallocation -- the file will be so fragmented that it'll read back at much less than 10% peak speed). The documentation warns users that in most cases, defragmentation is not necessary.

---

### Post by jirihuf on 2009-09-27
Deleting everything after "frags" worked! Thank you!

---

### Post by Kreative_Station on 2009-10-20
So...I read and read and read, still not able to achieve an answer.  I feel like everyone is always just yammering on about nonsense (even me).

Is there a Defragmenter for Linux? Which one is recommended?:KS

---

### Post by jongkind on 2009-10-20
> **Kreative_Station said:**
> So...I read and read and read, still not able to achieve an answer.  I feel like everyone is always just yammering on about nonsense (even me).

Is there a Defragmenter for Linux? Which one is recommended?:KS


Yes, there is, its called pyfragtools. I'm a happy user.

---

### Post by ibuclaw on 2009-10-20
> **jongkind said:**
> Yes, there is, its called pyfragtools. I'm a happy user.

From what I recall, it's nothing special ...

In pseudo code, it just does this:

```

foreach(file, list)
{
    new_file = sprintf("/.cache/%s", file);
    count = get_extents(file);
    cp(file, new_file);
    new_count = get_extents(new_file);
    if(new_count < count)
        mv(new_file, file);
}

```
With some extra jazzy sauce in the mix.

There is a program that comes part of the e2fs toolkit called **filefrag**, that will tell you the number of extents a file is in, and what number that the filesystem would regard as perfection (hint, the answer isn't always 1 extent, which is something that I think the pyfragtools app blissfully ignores).

Regards
Iain

---

### Post by Supersquirrel on 2009-11-05
HFS+ is the king of filesystems.

---

### Post by Pylade on 2009-12-19
Hello!
Is there a way to run defrag on an amd64 system?

If not why?

Thanks

---

### Post by Xbehave on 2009-12-19
It is a python script it will run on any architecture, however i found a bug.
line 540 reads:
> if frags == 1:
change it to
> if frags <= 1:
I'm not sure how a file can take up 0 extents or if this represents a bug in ext or fragfile, but that will prevent the script crashing and the script will not touch files with 0 extents (is that bad?)

I'm not sure what fragfile's support for newer filesystems is like, it always seams to return a list of "fragmented files" with 0.0 frags/MB  on ext4 and btrfs filesystems.

I will investigate more but the above change **should** get the script working. (i'm testing it on my partitions now but I don't want to trash anything important so testing will be limited)
I'm also lazy so if somebody could explain to me the 0 extents thing i would appreciate it

update, so i wondered why the output always said 0.00 i made a few changes (mainly removing unused code and adding unit support) (current version of my defrag is attached). but to get the frags/MB i had to change the previous change to
```
if frags <= 1 or size == 0:
            return 0
return (frags/(size/1048576))
```

I've tested it on all my partitions (they are ext4/btrfs and everything seams fine), the file is called defrag.txt but it is a python executable, just run it as ./defrag.txt or rename it as something sane then run it, either way it defrags your files (according to the original author (jdong), i know nothing about filesystems but have no reason to doubt him)


it can use pysco on x86 apparently, i'm on x86_64 and can't test that.

---

### Post by Pylade on 2009-12-20
If I want to defrag my /dev/sda7 (though it is formated in ext4 and not full, the fragmentation is over 20 percents).
How to run your script only for it?

Sorry for bad Engish, and thanks you for replying.

---

### Post by Xbehave on 2009-12-20
> **Pylade said:**
> If I want to defrag my /dev/sda7 (though it is formated in ext4 and not full, the fragmentation is over 20 percents).
Download the text file (i've attached a slightly updated version, that allows you to analysis a partition as non-root if you can read the files, also always returns a + change because -0.0% looked silly)

it runs based on mount points, so to run move to your downloads folder and run
```
sudo python defrag.py.txt /mountpoint
```

BTW the script is still jdong's work i just fixed a few bugs i had.

If you want a more permanent install, just run
```
sudo mv defrag.py.txt /usr/sbin/pydefrag
```
then when you want to run it
```
sudo pydefrag /mountpoint
```

p.s i still know nothing about fragmentation, it's possible ext4 is supposed to "fragment files" according to some optimization.

---

### Post by Pylade on 2009-12-20
THANKS YOU VERY MUCH!
It had worked well.
Now, my fragmentation rate is only 1.8 %.

Once again, thanks you for helping.

---

### Post by glnerd on 2009-12-20
thanx pretty kool.

---

### Post by Olaf123 on 2010-01-18
I want to try this tool. It looks good. However: there are 30 pages in this thread with various bugs, improvements and changes to the program. Is there an update to the download on the first page? I would appreciate that very much.

---

### Post by Xbehave on 2010-01-18
> **Olaf123 said:**
> I want to try this tool. It looks good. However: there are 30 pages in this thread with various bugs, improvements and changes to the program. Is there an update to the download on the first page? I would appreciate that very much.
My version (posted above) is the original, but made to work for me by using units, it doesn't have anything from the other 28 pages.
edit: just looked over pages the last 10 pages (19-29), there are no patches and jdong is active (so i'd guess he would have amended the OP if there was a patch before then)

---

### Post by Olaf123 on 2010-01-18
Thanx

---

### Post by mrkazoodle on 2010-02-05
Is running this defrag tool favourable since Ext4? I read somewhere something about e4defrag, another defragging tool for Ext4, which one is 'better'?

---

### Post by Xbehave on 2010-02-06
> **mrkazoodle said:**
> Is running this defrag tool favourable since Ext4? I read somewhere something about e4defrag, another defragging tool for Ext4, which one is 'better'?
I'd guess e4defrag is designed to work with ext4 on a lower level, so is better for ext4, but pyfragtools (and the debug script by ck) work on any filesystem.

---

### Post by Ux64 on 2010-02-21
> **mrkazoodle said:**
> Is running this defrag tool favourable since Ext4? I read somewhere something about e4defrag, another defragging tool for Ext4, which one is 'better'?

When is e4defrag going to be ready? It seems to be just normal open source projects. Years of talking and nothing coming out? Synaptic doesn't seem to find it.

And it isn't pre-installed either:
$ e4defrag
e4defrag: command not found

 - Thanks

---

### Post by FuturePilot on 2010-02-21
> **Ux64 said:**
> When is e4defrag going to be ready? It seems to be just normal open source projects. Years of talking and nothing coming out? Synaptic doesn't seem to find it.

And it isn't pre-installed either:
$ e4defrag
e4defrag: command not found

 - Thanks

It's still not ready upstream [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/321528/comments/26]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/321528/comments/26")

---

### Post by MasterNetra on 2010-02-21
> **Ux64 said:**
> When is e4defrag going to be ready?...

+1

Personally I don't understand why there isn't a defrag utility in Linux distros via default. Sure Linux is more resistant to fragmentation but its not immune to it. One shouldn't have to hunt for a program to defrag the system when it is eventually required.

---

### Post by iceman30ad on 2010-04-20
ok bash me if you like  was a heavy torrenter in lose-dows and have continued the pratice here now i dont have a external hdd i can use or id just bounce my files like i did with ce\me\nt so i need to find a good defragmenter or have some one explain the syntax for running a command with this one  yes i am a noob and if the explanations are already here please sticky them to the first post

---

### Post by Xbehave on 2010-04-20
[http://ubuntuforums.org/showpost.php?p=8531335&postcount=285](http://ubuntuforums.org/showpost.php?p=8531335&postcount=285)

jdong doesn't maintain the fist post any more (fair enough as his python pretty much just works). I'm currently living off a memory pen but if you run into any bugs I'm happy to try and fix them when i get the chance.

p.s most torrent programs let you preallocate to avoid fragmentation, that usually keeps fragmentation fairly low especially if you d/l music and not just movies.

---

### Post by mscir on 2010-05-07
> **Frak said:**
> Because from what I know, Windows writes to drive lazily, writing to wherever there is space to write to, Linux writes data to where it should go, all in one large pack, not a million different spots like on Windows. In turn, no need to defrag, everything isn't fragmented, so there is no reason.

Did you ever consider writing a Windows defragger that would arrange the files on the hdd something like a Linux system would, so the drive would require less defragmentation?

---

### Post by psusi on 2010-05-07
> **mscir said:**
> Did you ever consider writing a Windows defragger that would arrange the files on the hdd something like a Linux system would, so the drive would require less defragmentation?

Windows already has a defragger, the problem is that as soon as you start writing to the disk, it screws it all up again because its block allocator is retarded.

---

### Post by ShadowTek on 2010-05-21
I just copied about 400 GBs of files over LAN from my Ubuntu machine to my dad's WinXP machine's NTFS partition, and every damn bit of what was written to the NTFS partition was fragmented! There were a large number of files, ranging from 1 to 6 GBs each, that each contained anywhere from 10,000 to 60,000 fragments!

  Adding to that sad state of affairs, XP's *defragmenter* won't even *defragment* the damn files; it just spends an hour going over the same crap over and over again, leaving the exact same level of fragmentation in the end!

  This is just pathetic, but my dad wants Windows, so that's what he's going to get. :/


  Fortunately, pyfragtools' defrag *does* work; however, the analyzing process takes an insane amount of time. *mount.ntfs* jumps up to 100% CPU usage, and trying to analyze 132 GBs of data takes about 20 hours on a 2.2 GHz AMD CPU!

It would be nice if I could address whatever is causing this CPU  bottleneck.


  I'm running *defrag* from the .deb install in the first post, from a clean install of 10.04 Desktop 32bit.

  
Edit: The analysis *finally* completed, which I started about this time *yesterday*, and the defrag stage took about an hour after, but the results were successful.
```
========= COMPLETE ===========
Remaining Fragmented Files:
Frags/MB Before:     590.88
Frags/MB After:      0.00
Improvement:         100.0 %
===============================

```

---

### Post by webbertiger on 2010-06-27
For those hitting the problem of ZeroDivisionError, my solution is to change line 541:
```
    return frags/(os.path.getsize(file)/1024.0/1024.0)
```
to the following code block:
```
    filesize=os.path.getsize(file)
    if filesize == 0:
        return 0
    else:
        return frags/(filesize/1024.0/1024.0)
```
So files with 0 size can be skipped and the program will continue to run. See attached file.

---

### Post by mamamia88 on 2010-06-27
any real point to this?

---

### Post by Chame_Wizard on 2010-06-27
I never ever needed one.:lolflag:

---

### Post by Xbehave on 2010-08-14
> **ShadowTek said:**
> 

  Fortunately, pyfragtools' defrag *does* work; however, the analyzing process takes an insane amount of time. *mount.ntfs* jumps up to 100% CPU usage, and trying to analyze 132 GBs of data takes about 20 hours on a 2.2 GHz AMD CPU!

It would be nice if I could address whatever is causing this CPU  bottleneck.

If you use something like htop you can break down cpu usage by type, i'd guess a lot of the bottleneck will be in io-waits and I'd be fairly sure that the bottleneck is in the ntfs drivers as the python doesn't do any real "work" it just asks other programs to (filefrag, find and rsync), these programs themselves just make calls to the filesystem so are unlikely to use much CPU (well apart from rsync that could be the CPU hog if only the move is slow).

Finally you should note that pyfragtools doesn't understand ntfs but windows XP does so, the windows XP defrager will but the files in a better location on the disk (except for system files as it can't move them), so my advice would be 
1) run windows XP defrag to do what it can
2) run pyfrag tools to move the systemfiles

---

### Post by ShadowTek on 2010-08-14
> **Xbehave said:**
> 
Finally you should note that pyfragtools doesn't understand ntfs but windows XP does so, the windows XP defrager will but the files in a better location on the disk (except for system files as it can't move them), so my advice would be 
1) run windows XP defrag to do what it can
2) run pyfrag tools to move the systemfiles

I *did* do things in that order, but, as I said before, XP wouldn't defrag the vast majority of the files (which weren't system files), in spite of the fact that most of the filesystem was empty space.

The whole reason that I had to use pyfrag in the fist place is because XP's defragmenter wouldn't do an acceptable job.

---

### Post by johnviglis on 2011-01-01
Actually there might be a point to all this.

I checked my fragmentation level on a clean installation of 10.10 and the result was fragmentation 0%
The only fragmented files were some files in ~./mozilla and about 10 log files.
The result was:

> ========= COMPLETE ===========
Remaining Fragmented Files:
8.91    /var/log/kern.log
16.55    /var/log/messages
22.57    /var/log/syslog
48.23    /var/log/debug
50.40    /var/log/daemon.log
177.71    /var/log/Xorg.0.log
196.73    /var/log/gdm/:0.log
261.48    /var/log/auth.log
262.56    /home/user/.mozilla/firefox/8kvrt15u.default/cookies.sqlite
434.37    /var/log/user.log
Frags/unit Before:     1479.52
Frags/unit After:      1479.52
Improvement:         0.0 %
===============================
This was the second time I ran the script so no improvement was made, "Frags/unit Before" were about 5000 in the first execution. All the files that remained fragmented were scipped because they were opened for write.
Of cource there was no effect on my pc's performance, and the whole process lasted about 10 minutes. :p


On the contrary :(, I checked the fragmentation on a 10.10 installation, which was a dist upgrade of 10.04, which was a dist upgrade of 9.10, which was a clean installation a few months ago... The hdd capacity is 60GB with 46GB free space.

The sound of the hard working hdd and the increase in boot time brought me to this thread. After 40 minutes of analyzing the whole partition (containing both system and user locations), the result was fragmentation 36.8%

> 
Analyze finished. 36.8 % fragmentation (55473 files), 192.4 average frags
Fragmented files:
511.88    /usr/src/linux-headers-2.6.35-24/include/sound/emu8000.h
511.88    /usr/src/linux-headers-2.6.35-24/arch/blackfin/include/asm/dma-mapping.h
511.88    /usr/share/icons/oxygen/48x48/apps/oxygen.png
511.88    /usr/share/icons/hicolor/48x48/apps/oxygen.png
511.88    /usr/share/icons/Humanity/actions/48/media-eject.svg
511.88    /usr/lib/pymodules/python2.6/orca/scripts/apps/packagemanager/speech_generator.pyc
511.75    /usr/src/linux-headers-2.6.35-24/include/linux/delayacct.h
511.75    /usr/share/kde4/apps/katepart/script/lilypond.js
511.75    /usr/share/icons/Humanity/actions/16/media-seek-backward.svg
511.75    /usr/share/gnome/help/gnomine/C/legal.xml
...
How many passes to run? [10] 

Tomorrow I'll know if this script is effective in such a messy hdd, as well as if the system's performance was increased.

---

### Post by iX9 on 2011-05-11
Hi!

I dont believe pydefrag is working on ext4:

I have 8 GiB ext4 system partition with kubuntu 11.04. It has ~60% used. Then I create 2GiB swapfile there. Big file created on high use of disk - it** must be **fragmented! So I ran pydefrag:

> 
$ sudo defrag /Swap
Building list of files to analyze... done!
                                                                               
Analyze finished. 
/Swap is not fragmented. Go home.
$ 


No fragments?! Hmm.

> 
$ sudo filefrag -v /Swap
Filesystem type is: ef53
File size of /Swap is 2147483648 (524288 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0   364544            2048 
   1    2048   380928   366591   2048 
   2    4096   409600   382975   2048 
   3    6144   423936   411647   2048 
   4    8192   430080   425983   2048 
   5   10240   509952   432127  14336 
   6   24576   716800   524287   4096 
   7   28672   722944   720895   6144 
   8   34816   733184   729087   2048 
   9   36864   737280   735231   2048 
  10   38912   743424   739327   4096 
  11   43008   749568   747519   8192 
  12   51200   798720   757759   2048 
  13   53248   804864   800767   2048 
  14   55296   811008   806911   8192 
  15   63488   835584   819199   2048 
  16   65536   831488   837631   4096 
  17   69632   903168   835583  14336 
  18   83968   919552   917503   2048 
  19   86016   962560   921599  32768 
  20  118784   995328           12288 
  21  131072  1009664  1007615  32768 
  22  163840  1042432            6144 
  23  169984  1220608  1048575   2048 
  24  172032  1269760  1222655  32768                                           
  25  204800  1302528           32768                                           
  26  237568  1335296           32768                                           
  27  270336  1368064           32768                                           
  28  303104  1400832           32768                                           
  29  335872  1433600           32768                                           
  30  368640  1466368           32768                                           
  31  401408  1499136           32768                                           
  32  434176  1531904           32768                                           
  33  466944  1564672            8192                                           
  34  475136  1695744  1572863  32768                                           
  35  507904  1728512           16384 eof                                       
/Swap: 24 extents found
$


By filefrag the file have I thing 24 fragments!
Or am I wrong?

---

### Post by jerrrys on 2011-05-11
i do not have pydefrag installed, its not in my synaptic.  but i think you can take it at face value.  meaning that pydefrag will not see it as fragemented with just 24 frags.  i have used this command in the past to check mine

sudo fsck -vn /dev/sda1

and it always reads clean

---

### Post by TheFerminator on 2012-01-11
I know this is an old thread, but I need to get some .iso images to 0 frags so grub will let me boot them. I ran pydefrag, but they are stil fragmented enough that grub wont load them. I get ERROR 60: ...

---

