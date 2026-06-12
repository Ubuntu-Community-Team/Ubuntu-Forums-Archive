---
title: "What would cause video conversion to go REALLY slow on ubuntu-server?"
date: 2008-12-16
forum: Server Platforms
---

### Post by samosamo on 2008-12-16
I have a P4 3.0GHz/1GB ram machine running ubuntu server 8.10.  I am using HandbrakeCLI (from the makers of Handbrake for OSX) to convert many, many divx's to m4v via command line.

This thing converts REALLY slow, the only helpful output the app gives me is "fps" and duration, and by reading that **it takes about ~60 minutes to convert a 200MB DivX to m4v at an average of 9fps.  That's right, NINE fps!!!**  To compare, my 2.4GHz C2D / 4GB RAM iMac does it in 10 minutes at about 45fps.

Is the server kernel not compiled for this type of work?  Is the extra CPU in the iMac making that much of a difference?  The ubuntu box is only using 50% ram.

---

### Post by damis648 on 2008-12-16
Such tasks are better suited for the realtime (rt) kernel, I am sure the server kernel is not really cut out for this kind of work.

---

### Post by samosamo on 2009-01-12
Can anyone verify this?  I would hate to build another machine for this purpose.

---

### Post by hyper_ch on 2009-01-12
just install the rt kernel and boot from that (if that truly is the case)

---

### Post by finite9 on 2009-01-14
> **hyper_ch said:**
> just install the rt kernel and boot from that (if that truly is the case)

You haven't understood what the real time kernel is.  This issue has nothing to do with the rt kernel.

I honestly do not know what the problem could be, but do you have other performance problems unrelated to video conversion?  How do other tasks compare to your desktop?

Try doing the conversion through mencoder to compare to Handbrake.

---

### Post by hyper_ch on 2009-01-14
what is the rt kernel then?

---

### Post by finite9 on 2009-01-14
> **hyper_ch said:**
> what is the rt kernel then?

Trying to call my bluff?  Surely you could Google for it, so I assume you're calling my bluff...

I could simply cut and paste an explanation from a Wiki here.

But lets cut to the chase instead.  Desktop edition does not have the real-time kernel.  Only Studio edition has the rt kernel, due to sound editing requirements.  Desktop edition is more than capable of transcoding video.  I do this regurarly on my Desktop edition Core2Duo 2GHz and get a decent encode rate with Mencoder.  Why would rt kernel help?

The only thing that comes to mind regarding the issue OP is having is that the kernel scheduler in Server edition could be the culprit if there are several processes vieing for time simultaneously, assuming the OP has no other performance issues with his server, as that is one of the major differences between the desktop/server kernel.  Then it could be an idea to install desktop kernel or a vanilla kernel as a test, but rt will likely not make this any better.

---

### Post by aaron.d on 2009-01-14
> **samosamo said:**
> I have a P4 3.0GHz/1GB ram machine running ubuntu server 8.10.  I am using HandbrakeCLI (from the makers of Handbrake for OSX) to convert many, many divx's to m4v via command line.

This thing converts REALLY slow, the only helpful output the app gives me is "fps" and duration, and by reading that **it takes about ~60 minutes to convert a 200MB DivX to m4v at an average of 9fps.  That's right, NINE fps!!!**  To compare, my 2.4GHz C2D / 4GB RAM iMac does it in 10 minutes at about 45fps.

Is the server kernel not compiled for this type of work?  Is the extra CPU in the iMac making that much of a difference?  The ubuntu box is only using 50% ram.

well ... I really don't think an old p4 and a gig of ram is optimal for video/audio production, but how about the kernel? Is it SMP? If you have HT try enabling it, or even disabling, depending on the current state and see if there is any change.

---

### Post by FakeOutdoorsman on 2009-01-14
> **samosamo said:**
> I have a P4 3.0GHz/1GB ram machine running ubuntu server 8.10.  I am using HandbrakeCLI (from the makers of Handbrake for OSX) to convert many, many divx's to m4v via command line.

This thing converts REALLY slow, the only helpful output the app gives me is "fps" and duration, and by reading that **it takes about ~60 minutes to convert a 200MB DivX to m4v at an average of 9fps.  That's right, NINE fps!!!**  To compare, my 2.4GHz C2D / 4GB RAM iMac does it in 10 minutes at about 45fps.

Is the server kernel not compiled for this type of work?  Is the extra CPU in the iMac making that much of a difference?  The ubuntu box is only using 50% ram.

I have a very similar machine as you (P4 3.0GHz, 2 GB ram, 2.6.27 kernel on Arch Linux), and 9 fps does not seem unreasonable depending on the quality settings of the conversion.  In fact, if I use the libx264-hq preset in ffmpeg I get about 8 fps converting from DV.  I am unfamiliar with handbrake, but what is the conversion command or your encoding settings?

---

### Post by theparanoidone on 2009-01-14
The short answer:

Kernel config option:
CONFIG_HZ_1000=y 
CONFIG_HZ=1000
(whereas previously ubuntu was set to a default of 100 hz).

The long answer here:

We were having terrible MySQL perforance... however... video editing vs db concurrent load will both exhibit heavy load for any server.

So we’ve run some tests with sysbench that are heavy write benchmarks.  We appear to have hit some sort of operating system specific wall.  

	Sysbench 50 TRHEADS
OS	ubuntu32	ubuntu64	centos32
syncbinlog 0, WB	5600	12600	3800
syncbinlog 1, WB	348	294	1700
			
	Sysbench 1 THREAD 
OS	ubuntu32	ubuntu64	centos32
syncbinlog 0, WB	4500	6000	2300
syncbinlog 1, WB	3200	4356	2300


The interesting thing to note is, the number of context switches in CENTOS will peak above 10,000  where UBUNTU will struggle to get past 3,000 context switches (doesn’t matter 32 bit or 64 bit).

We also notice that CENTOS has 1,000 intr/s while the system is idle where as ubuntu has 0.  

Our theory is that CENTOS is polling more often to see if it needs to switch contexts  (which under heavy load… it does), and therefore, CENTOS is handling operations more efficiently.  The servers we are testing on are all WriteBack enabled raid servers of different processor speeds (close enough though to get a feel for what is working an what is not working)

We have recompiled the UBUNTU kernel with the following modifications:

CONFIG_HZ_1000=y 
CONFIG_HZ=1000
(whereas previously ubuntu was set to a default of 100 hz).

After making these changes… the system behaves better:

 	Sysbench 50 TRHEADS
OS	ubuntu32	ubuntu64	centos32	ubuntu64 KRN PTCH
syncbinlog 0, WB	5600	12600	3800	14000
syncbinlog 1, WB	348	294	1700	2100


 	Sysbench 1 THREAD
OS	ubuntu32	ubuntu64	centos32	ubuntu64 KRN PTCH
syncbinlog 0, WB	4500	6000	2300	5200
syncbinlog 1, WB	3200	4356	2300	2600


For now this appears to be the culprit (what a pain in the ass… I would never have dreamed in a million years the standard kernel configuration for ubuntu was the problem).

FYI, Here are our sysbench commands (be sure to change your mysql username and password):

./sysbench --num-threads=50 --test=oltp --oltp-test-mode=complex --oltp-table-size=100000 --oltp-distinct-ranges=0 --oltp-order-ranges=0 --oltp-sum-ranges=0 --oltp-simple-ranges=0 --oltp-point-selects=0 --oltp-range-size=0 --mysql-table-engine=innodb --mysql-host=127.0.0.1 --mysql-user=ROOT --mysql-password=PASSWORD prepare

./sysbench --num-threads=50 --test=oltp --oltp-test-mode=complex --oltp-table-size=100000 --oltp-distinct-ranges=0 --oltp-order-ranges=0 --oltp-sum-ranges=0 --oltp-simple-ranges=0 --oltp-point-selects=0 --oltp-range-size=0 --mysql-table-engine=innodb --mysql-host=127.0.0.1 --mysql-user=ROOT --mysql-password=PASSWORD run

---

### Post by finite9 on 2009-01-14
it should be pretty easy to test anyway: boot a live cd of the desktop edition, install the handbrake application, mount the hard drive, and perform a transcode.  Quick check instead of having to install a new kernel.

---

### Post by samosamo on 2009-01-26
It turns out ubuntu-server and it's factory kernel are not the culprit.  I built a new machine:

ubuntu-server x64
Intel Core2Duo Q6600
4GB RAM
HandBrakeCLI built from source

It encodes at a very respectable 53 fps using the iPod setting.  So I guess it was a hardware limitation.  It didn't realize that P4 3ghz was so slow!  Sorry for making a thread about it.

---

### Post by tubezninja on 2009-01-26
No problem.  Wish I had seen this thread sooner, I would've told you that the p4 isn't up to the task. :D

As someone who uses Ubuntu servers for video and audio transcoding, I can confirm that the server kernel is most definitely up to the task.  Using Ubuntu 8.10 server, FFmpeg, a Quad Core processor and a very capable disk array, I've managed to batch transocde up to four video files at once with 50+ fps rates.  Having a lot of RAM to to use a a cache also helps.

---

### Post by BlueSkyNIS on 2009-01-26
Yes, P4 is just slow. I have P4 3GHz/1GB RAM and 9 FPS is just a normal performance. Core2Duos are much faster the Pentium 4.

---

### Post by finite9 on 2009-01-27
I got tired of my Core2Duo laptops performace, so I recently bought a Quad Q9550 2.8GHz with 4GB DDR3-1333MHz ram and 2xWD RE3 1TB discs in a RAID1 array, and padlocked it all up in a nice LianLi tower case :) Running Ubuntu 64-bit server headless.

I have not had chance to rip my home made DV tapes to disc yet, but I cannot wait to see the performance of this thing when I transcode the raw DV to H264/Matroska using Mencoder (i made a custom script) :)

---

### Post by tubezninja on 2009-01-28
> **finite9 said:**
> I got tired of my Core2Duo laptops performace, so I recently bought a Quad Q9550 2.8GHz with 4GB DDR3-1333MHz ram and 2xWD RE3 1TB discs in a RAID1 array, and padlocked it all up in a nice LianLi tower case :) Running Ubuntu 64-bit server headless.

I have not had chance to rip my home made DV tapes to disc yet, but I cannot wait to see the performance of this thing when I transcode the raw DV to H264/Matroska using Mencoder (i made a custom script) :)

As long as your encoding software specifically supports multithreading, you should be fine.  In my experience, the FFMpeg cli tools don't.  But then I get around that but just running 4 jobs at a time to take full advantage of my Core2Quad. :)

---

### Post by FakeOutdoorsman on 2009-01-28
> **scaredpoet said:**
> As long as your encoding software specifically supports multithreading, you should be fine.  In my experience, the FFMpeg cli tools don't.  But then I get around that but just running 4 jobs at a time to take full advantage of my Core2Quad. :)
FFmpeg encoding with libx264 and the "threads" option will take advantage of multiple cores.  Using "-threads 0" will allow x264 to automatically detect the number of CPUs available and choose the correct number of threads.  x264 development is active and using the latest x264 from git will usually give the fastest encodes, especially with newer CPUs such as the Intel Core i7.  I have a guide explaining how to install recent ffmpeg and x264 with usage examples:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

---

### Post by finite9 on 2009-01-29
> **scaredpoet said:**
> As long as your encoding software specifically supports multithreading, you should be fine.  In my experience, the FFMpeg cli tools don't.  But then I get around that but just running 4 jobs at a time to take full advantage of my Core2Quad. :)

Mencoder supports "threads=" just the same as ffmpeg does, but in mencoder you just spec. threads=auto, but in ffmpeg you need to use "-threads 2" and specifically set the amount of threads you want to use.

Even using both cores, it was still taking too long for a 30 minute film.  But everything is relative. It depends on what you're encoding right?  XviD goes way faster than x264, and if you throw in 2 pass, it's even longer, even when sending sound to /dev/null on first pass.  You can *never* have enough processing power.

I just read FakeOutdoorsman's post after clicking send :)

---

