---
title: "CD ripping stops, extremely slow with Ratel Ultra"
date: 2010-12-07
forum: System76 Support
---

### Post by neophyte_of_linux on 2010-12-07
Hi, I purchased a Ratel Ultra a few months ago, with 10.04 LTS, and also started a new job so I haven't had time to use it much.  I keep it updated and it is updated.

I have tried to rip a CD with Rythmbox and it was extremely slow and would take on the order of tens of minutes per song, but would eventually just hang up and quit ripping.  I installed Asunder yesterday and had the same problem.

This is a problem because I was planning to rebuild putting favorite tunes into mp3's or ogg's because my last computer cratered - causing me to buy the Ratel.

I need support to resolve this, can anyone help?

---

### Post by tlroche on 2010-12-08
> **neophyte_of_linux said:**
> I have tried to rip a CD with [Rhythmbox] and it was extremely slow and would take on the order of tens of minutes per song, but would eventually just hang up and quit ripping.  I installed Asunder yesterday and had the same problem.

Perhaps a drive problem? You can get some diagnostic information from Disk Utility:

[LIST=1]
[*]put a readable disk in the drive
[*]run either System>Administration>Disk Utility or commandline=`palimpsest &`
[*]select "CD/DVD Drive" from the storage device list
[/LIST]

That should tell you if something is very wrong with the drive.

Unfortunately its "Read-Only Benchmark" will apparently not work at CD/DVD speeds--at least, when I tested just now, it said the drive was too slow to test. I know of CD/DVD benchmarking tools for windows (e.g. Nero DiscSpeed), but not for linux. Hopefully someone else will add that knowledge.

---

### Post by isantop on 2010-12-08
You could also try ripping from a LiveCD or LiveUSB, as that would also rule out a hardware or software issue.

---

### Post by neophyte_of_linux on 2010-12-08
Thanks for replies.  Here is the summary of my finding so far:

1) The DVD/CD multi recorder player will play DVDs and music CDs without any problems.
2) I can burn data files to a CD and to a DVD without any problems.

However, when I attempt to read a music CD and 'rip' with software the above mentioned slowness happens...and it is so slow you can't hardly hear the cd spinning, and eventually everything just stops happening.  Eventually I find a folder in the music directory with a few completed "rips".  So an .ogg or .wav or .mp3 can be created but its not really working right.

Last attempt I made tonight was worse...the cd immediately made lots of clicking sounds and the progress bar never even moved...I eventually had to force a quit.

I used disk analyzer and tried a "read" test on cd in the cdrom drive.  Immediate failure:

Error benchmarking: helper exited with exit code 1: Error reading 104857600 bytes at 104857600 from /dev/sr0 when guesstimating buffer size: Input/output error

Next I will try ripping with working from a LiveUSB as suggested.:popcorn:

---

### Post by Wootyeah on 2011-01-01
I too am having the same problem on my laptop.  Any help would be appreciated.

---

### Post by neophyte_of_linux on 2011-01-19
OK sorry it took me a while to get back to posting because of the holidays.  

Here is latest diagnosis attempt:  I put 10.04LTS (same as Ratel) on memory stick and ran it on that.

To my surprise, I was able to rip _MY PERSONAL PAID FOR CD_ to mp3 in a reasonable time, completely did all tracks with no hang ups.  I was also able to burn a CD in reasonable time too.  Very much like what I would expect and not like the hung up lock up effect I get normally.

So, I would really like to have this fixed, even if I have to have someone at 76 dial into my 'puter and fix it.   Because I am starting up music lessons and not being able to rip and burn music an put on my personal player will be a big disappointment.

Please advise.

---

### Post by isantop on 2011-01-21
I think you're having a software issue, as it worked fine from an Ubuntu LiveCD. 

We can probably fix it, but it may be easier and faster to simply reinstall Ubuntu. You can keep all of your personal files, if you need them.

---

