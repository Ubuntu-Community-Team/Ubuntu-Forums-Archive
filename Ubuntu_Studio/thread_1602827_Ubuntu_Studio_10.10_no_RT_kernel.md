---
title: "Ubuntu Studio 10.10 no RT kernel"
date: 2010-10-21
forum: Ubuntu Studio
---

### Post by kurotenshi on 2010-10-21
Hi, I installed the studio 10.10 today and was going to install the -rt or -lowlatency kernel for audio work but there isn't any one of those available in the repositories... only the gerenic. Those that mean that there is no longer needed in new kernel versions?

---

### Post by AutoStatic on 2010-10-22
The maintainer for the -rt and -lowlatency kernel packages has stopped working on them: [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime). That's why there are no such packages available for Maverick. Hopefully at least the -rt packages will be back in Natty.

---

### Post by cchhrriiss121212 on 2010-10-22
According to that schedule, rt is being ditched completely in favour of realtime, which does not look too promising:
> the -realtime kernel is a PREEMPT_RT patched kernel based on the vanilla  source tree (not the Ubuntu source). **This kernel will be missing Ubuntu  specific code, patches or security fixes** and it isn't guaranteed to be  compatible with any external software

I find it hard to keep up with all the different kernel swapping in Studio, I'm still using 2.6.31.12-rt21 which has been solid as a rock for some time.

---

### Post by trulan on 2010-10-22
> **cchhrriiss121212 said:**
> According to that schedule, rt is being ditched completely in favour of realtime, which does not look too promising
I guess I'm a little in the dark here - I didn't know there was a difference between -rt and -realtime.  I've been building my own kernels for some time now (vanilla kernel source and PREEMPT-RT patch).  It is true that there is no guarantee it will work with everything, in fact every new version is pretty much guaranteed to break any closed-source binary drivers.  But the same was true for the -rt kernels when they were being maintained, and I don't remember **ever** seeing a security fix being released for an -rt kernel.  Usually UStudio would install with an -rt kernel, and that would be it.  Meanwhile, the generic kernel gets an update every few weeks.

Back to the OP's question:
It is possible to install a realtime kernel in Maverick, but you'll need to get it frm a ppa rather than from the repos.  I think I have the one from here in my Maverick install:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")
But as Autostatic said, there are no packages for Maverick.

So - is the -rt kernel no longer needed?
The best answer I can give is:  try it and see.  I use firewire audio and I definitely get better performance from the -rt kernel.  But that will not necessarily be true for all hardware.  And even firewire is improved enough under Maverick that I could probably get by on the generic kernel.

---

### Post by madeinfamous on 2010-10-22
hell o

trial and error... by yourself,  is better than any question/answer

[https://sites.google.com/site/nueusx/rt-lowl.png](https://sites.google.com/site/nueusx/rt-lowl.png)

pfff, :guitar:

in arts, exactly like music and or pc, it's not the tools, it's the one behind it, that makes things possible,

have a nice weekend! :)

ps: [linux-lowlatency - 2.6.35-17.23]("https://launchpad.net/~falk-t-j/+archive/lucid/+packages?start=225&batch=75")

---

### Post by kurotenshi on 2010-10-22
Thanks everyone, I'll just keep working with the generic for now since I'm still in the process of figuring out linux for music production. I use Ubuntu since like 96 maybe but as far as audio goes windows is still easier for me to work with; I want that to change though.

---

### Post by AutoStatic on 2010-10-22
Then it might be a better option to try 10.04 Lucid Lynx. Then you also have access to some really good multimedia PPA's.

---

### Post by maghoxfr on 2010-10-22
I have 10.04 and it runs just perfect. I've been using ubuntu since 9.04 and I honestly can say that I can't live without jack, patchage etc.

---

### Post by serfcx on 2010-11-04
You could also have a look at Tangostudio, based on 10.04.

Looks good:)

---

### Post by JackSchnippes on 2010-11-04
I just tried the packages from [Alessio's ppa]("https://launchpad.net/%7Eabogani/+archive/ppa"). Yes, there are no packages for 10.10 Maverick in his ppa, but there are for natty. And they work :)  Looky here what mr. bash wants to tell you:

```
 $ uname -a
Linux dozer 2.6.36-1-lowlatency #7~ppa2-Ubuntu SMP PREEMPT Tue Oct 26 13:39:35 UTC 2010 x86_64 GNU/Linux

```Just download the packages below according to your platform and wether you want to go for lowlatency or realtime and install them in **the order you downloaded them**. Either double-click in nautilus or 'sudo dpkg -i package_name.deb' in yer terminal... Please note that I only tested for lowlatency 64bit. Pls post your results! Btw nvidia driver works, too!

**lowlatency 32bit**
```
wget http://launchpadlibrarian.net/58022320/linux-headers-2.6.36-1_2.6.36-1.7_all.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-headers-2.6.36-1-lowlatency_2.6.36-1.7~ppa2_i386.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-image-2.6.36-1-lowlatency_2.6.36-1.7~ppa2_i386.deb
```
**lowlatency 64bit**
```
wget http://launchpadlibrarian.net/58022320/linux-headers-2.6.36-1_2.6.36-1.7_all.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-headers-2.6.36-1-lowlatency_2.6.36-1.7~ppa2_amd64.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-image-2.6.36-1-lowlatency_2.6.36-1.7~ppa2_amd64.deb
```
**realtime 32bit**
```
wget http://launchpadlibrarian.net/58022320/linux-headers-2.6.36-1_2.6.36-1.7_all.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-realtime/linux-headers-2.6.33-29-realtime_2.6.33-29.1_i386.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-realtime/linux-image-2.6.33-29-realtime_2.6.33-29.1_i386.deb
```
**realtime 64bit**
```
wget http://launchpadlibrarian.net/58022320/linux-headers-2.6.36-1_2.6.36-1.7_all.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-realtime/linux-headers-2.6.33-29-realtime_2.6.33-29.1_amd64.deb
wget http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-realtime/linux-image-2.6.33-29-realtime_2.6.33-29.1_amd64.deb
```

---

### Post by heldal on 2010-11-09
The links for realtime kernels above include a header-package from the 2.6.36set. It needs linux-headers-2.6.33-29_2.6.33-29.1_all.deb instead to install (linux-headers-2.6.33-29-realtime_2.6.33-29.1_i386.deb depends on it).

I get slightly worse results for audio using the lowlatency (2.6.36 32-bit) kernel instead of the 2.6.35-23 in 10.10. I've not yet been able to test this 2.6.33-realtime kernel because the module for nvidia-current ( 260.19.12) doesn't link with this version. With 2.6.36-lowlatency I can't run with a jack-setup with latency less than 32ms. With 2.6.35 I can get away with 16ms. (E6600/2GB@2.4Ghz, Xonar-DX audio, UA-25EX audio).

---

### Post by trulan on 2010-11-09
If you're feeling adventurous, take a look at how I got the NVidia driver working with 2.6.33-rt on Maverick:
[http://ubuntuforums.org/showpost.php?p=9975989&postcount=24](http://ubuntuforums.org/showpost.php?p=9975989&postcount=24)
Note that the NVidia driver version number has changed from 
260.19.06 to 260.19.12 since I wrote that, and you'll have to correct that, it won't work to copy and paste my commands.  But the changes to the driver files are all the same.

---

### Post by abstractor on 2010-11-10
Thanks, JackSchnippes, for the advice! I installed the lowlatency kernel version 2.6.36-1.7~ppa2_i386 through Synaptic on my Maverick system after manually installing the headers you linked to, adding Alessio's PPA to my software sources and edited it, replacing 'maverick' with 'natty' in the Distribution field.

And the thing works well for me. Using JACK in a relatively simple setup (playing a bass guitar through an equalizer, compressor and reverb), I have seen 0 (zero) xruns during the few hours of testing at 2.6-millisecond latency:guitar:. With the generic kernel, I would get a few xruns an hour even with latencies above 10 milliseconds and no effects whatever.

---

### Post by 3calm on 2010-11-12
The low latency 32 works a treat in 10.10 so far.

---

### Post by decomp on 2010-11-14
> **3calm said:**
> The low latency 32 works a treat in 10.10 so far.

Is that available in standard ubuntu repos?

---

### Post by heldal on 2010-11-16
> **trulan said:**
> If you're feeling adventurous, take a look at how I got the NVidia driver working with 2.6.33-rt on Maverick

Did that a few days ago, and not all that is required. There's a patch for nvidia's source floating around that takes care of it. The patch (attached) only changes templates in a header-file.

With driver version 260.19.12 and the patch-file in your homedir do (needs adjusting for kernel and driver version):

```
cd /usr/src/nvidia-current-260.19.12
sudo patch -p5 < ~/33rt.patch.txt
sudo dkms build -k 2.6.33-29-realtime -m nvidia-current -v 260.19.12
```

The results however were not that encouraging for me. I've got some very recent hardware which isn't supported in 2.6.33. I'm cleaning up some driver code to improve on latency for those devices, but have chosen to code for kernel 2.6.37 instead. 2.6.37 finally does away with the ioctl-lock that has caused so much grief with low-latency-applications. There are still some glitches in various drivers, but most of the BKL-issues should be sorted in the rc2 release. A 2.6.37-rc2 build should soon be available from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). There is already rc1 packages there which may work for audio for some. Results with 2.6.37-rc1 have gotten close to the rt-pached kernels in my tests.

---

### Post by heldal on 2010-11-16
> **decomp said:**
> Is that available in standard ubuntu repos?

No, the low-latency kernel is not available in standard repos (yet).

low-latency does work, but doesn't really improve much over the standard kernel in my tests. The old rt-patch is rather complex so I don't expect that to be updated for more recent kernels anytime soon. My bet is currently on 2.6.37 which has improved a lot and is getting very close to a preemptible rt-kernel wrt audio-latency in my tests. With 2.6.36-lowlatecy or 2.6.35 I can't get much below 30ms latency without masses of xruns. With 2.6.37-rc1 or 2.6.33-rt I get down to about 5ms on the same hardware.

---

### Post by trulan on 2010-11-16
Thanks for the NVidia patch - I knew there had to be a simpler way, but hey, that was how I got it working - I actually tried using diff to create a patch and thought I had it figured out, but I never was actually able to make it work.

Also, good to know about 2.6.37.  I've already got it installed in Natty so I can test it easily enough.  But until libraw1394 is updated to support daisychaining firewire audio devices, I'm going to be stuck with 2.6.33-rt and unable to really use anything newer here.  The legacy firewire stack has been removed from 2.6.37 as I understand, so that really limits things for me.

And FWIW, the latest message from Thomas Gleixner regarding a new RT patch is "Working on it."  Short and to the point, I guess.

---

### Post by trulan on 2010-11-16
I spoke to soon - the libraw1394 update is out (the source code is out at least), and it works!  Doing some testing on another distro, but I've got my firepods daisy-chained and working on the new firewire stack.  Now **that's** exciting!

---

### Post by Peter7K on 2010-11-17
What would be awesome would be a backport of this [http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1) to lowlatency/rt kernels!

---

### Post by trulan on 2010-11-18
> **Peter7K said:**
> What would be awesome would be a backport of this [http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1) to lowlatency/rt kernels!
If that patch is as good as that article makes it sound, we will have no use for the rt kernels - which is even more awesome really, though maybe a little less exciting.

---

### Post by Peter7K on 2010-11-18
> **trulan said:**
> If that patch is as good as that article makes it sound, we will have no use for the rt kernels - which is even more awesome really, though maybe a little less exciting.

The watching the videos on page two... it's ridiculous how good it looks.  Really, this is a huge leap for Linux.  It's already the fastest, now it's REALLY, by a MILE, the speediest.  I can't wait!

---

### Post by Peter7K on 2010-11-19
[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

Has posted kernels for 32 and 64 bit Ubuntu 10.10.

---

### Post by FretLes on 2010-11-27
I hope you'll forgive a naive question about this...

I'm busy configuring a replacement for my previous (Karmic) recording laptop; the new machine has firewire (for my firebox) and Nvidia.
I'm hoping to use Maverick as a base, so I don't have to worry about Nvidia.

From my reading here and elsewhere, I've concluded that my best bet is to compile a low-latency version of 2.6.37-rc2 (or rc1). I've found the generic version at [http://kernel.ubuntu.com/~kernel-ppa/maimline/v2.6.37-rc2-maverick](http://kernel.ubuntu.com/~kernel-ppa/maimline/v2.6.37-rc2-maverick) so there must be a git tree somewhere that contains the Ubuntu-specific code.

I cloned from kernel.ubuntu.com/ubuntu/ubuntu-Maverick on 10/11/25, and it only goes up to 2.6.35.

My naive question is - Where's that git tree?

Thanks for your indulgence.

---

### Post by trulan on 2010-11-27
...that would be in ubuntu-Natty I believe.

---

### Post by FretLes on 2010-11-27
I realise that there's a 2.6.37-rc2 (and a 3) in the Natty branch, but what puzzles me is that the PPA contains a set of packages for v2.6.37-rc2-maverick., but I can't find the git tree.
Perhaps there'll be a clue in the build log...

I guess there should be no issues using a Natty kernel in a Maverick installation, so I may just leave this as one of life's mysteries and go with the low-latency Natty kernel.

---

### Post by shadghost on 2010-12-08
Seeing how the 2.6.36 got removed form the ppa

[http://launchpadlibrarian.net/60163859/linux-headers-2.6.37-8_2.6.37-8.21_all.deb](http://launchpadlibrarian.net/60163859/linux-headers-2.6.37-8_2.6.37-8.21_all.deb)
[http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-headers-2.6.37-8-lowlatency_2.6.37-8.21~ppa1_amd64.deb](http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-headers-2.6.37-8-lowlatency_2.6.37-8.21~ppa1_amd64.deb)
[http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-image-2.6.37-8-lowlatency_2.6.37-8.21~ppa1_amd64.deb](http://ppa.launchpad.net/abogani/ppa/ubuntu/pool/main/l/linux-lowlatency/linux-image-2.6.37-8-lowlatency_2.6.37-8.21~ppa1_amd64.deb)


are the 3 for 64 bit

---

### Post by shadghost on 2010-12-08
Thoes dont work for 10.10 (well vanalla ubunto)

[https://launchpad.net/~abogani/+archive/ppa/+files/linux-headers-2.6.36-1-lowlatency_2.6.36-1.7~ppa2_amd64.deb](https://launchpad.net/~abogani/+archive/ppa/+files/linux-headers-2.6.36-1-lowlatency_2.6.36-1.7~ppa2_amd64.deb)
[https://launchpad.net/~abogani/+archive/ppa/+files/kernel-image-2.6.36-1-lowlatency-di_2.6.36-1.7~ppa2_i386.udeb](https://launchpad.net/~abogani/+archive/ppa/+files/kernel-image-2.6.36-1-lowlatency-di_2.6.36-1.7~ppa2_i386.udeb)

are the two you had, just moved to thoes locations

---

### Post by angelsguitar on 2011-01-08
Hi all.

Why not try the liquorix kernel? I'm running kernel 2.6.36-2.dmz.8-liquorix-amd64 on Ubuntu Studio 10.10 and it's really an improvement over the generic kernels. Stable so far; although they are really for Debian systems, I've had no problems.

However, I have not tried to install Nvidia drivers, so can't comment on that.

[http://liquorix.net/]("http://liquorix.net/")

---

### Post by angelsguitar on 2011-01-08
> **AutoStatic said:**
> Then it might be a better option to try 10.04 Lucid Lynx. Then you also have access to some really good multimedia PPA's.

I agree. I'm running both Ubuntu 10.10 with [liquorix kernel]("http://liquorix.net/") and 10.04 with packages and kernels from [falktx's ppa]("https://launchpad.net/~falk-t-j/+archive/lucid"), and 10.04 is far superior in performance, package selection, and variety of plugins than 10.10.

---

### Post by cchhrriiss121212 on 2011-01-08
> However, I have not tried to install Nvidia drivers, so can't comment on that.
I have been using liquorix for a few months now and the non-free nvidia drivers install just fine (unlike any of the new rt kernels). Performance is just as good too, and they are much more up-to-date than rt so I can't think of any reason to switch back.

---

### Post by angelsguitar on 2011-01-10
> **cchhrriiss121212 said:**
> I have been using liquorix for a few months now and the non-free nvidia drivers install just fine (unlike any of the new rt kernels). Performance is just as good too, and they are much more up-to-date than rt so I can't think of any reason to switch back.

Did you use the prepackaged drivers from Ubuntu repos or did you build the drivers from source?

---

### Post by angelsguitar on 2011-01-10
> **cchhrriiss121212 said:**
> I have been using liquorix for a few months now and the non-free nvidia drivers install just fine (unlike any of the new rt kernels). Performance is just as good too, and they are much more up-to-date than rt so I can't think of any reason to switch back.

Did you use the pre-packaged drivers from Ubuntu or did you build them from source?

---

### Post by cchhrriiss121212 on 2011-01-10
I used the latest drivers from the nvidia website, and did a manual install. But I know many other users are installing from the repos with no issue.

---

### Post by besneatte on 2011-01-24
In order to get the low latancy stuff to download and install ( the links provided in this thread are broken ) I added the main and source repositories from abogani:

[http://ppa.launchpad.net/abogani/ppa/ubuntu](http://ppa.launchpad.net/abogani/ppa/ubuntu) natty main

Then I had to find and download the correct linux headers:

[http://packages.ubuntu.com/natty/linux-headers-2.6.37-12](http://packages.ubuntu.com/natty/linux-headers-2.6.37-12)

Installed the headers, then from the command line:

sudo apt-get install  linux-headers-2.6.37-12-lowlatency linux-headers-lowlatency linux-lowlatency

rebooted and everything *ALMOST* works fine... unfortunately I have no mouse trackpad when I reboot... haven't tried with an external USB mouse yet....

any thoughts on how to get the mouse to work?

---

### Post by crazee64 on 2011-02-20
Came here looking for -rt kernels for 10.10 as I imagine most will, so to be helpful to those people here is what I did:

Starting with a stock 64 bit maverick install (up to date as of 17/2/2011) I followed the instructions in post #10 for 64 bit lowlatency, but instead grabbed later headers and kernel from launchpad and the ppa -

linux-headers-2.6.38-3_2.6.38-3.30_all.deb
linux-headers-2.6.38-3-lowlatency_2.6.38-3.30~ppa1_amd64.deb
linux-image-2.6.38-3-lowlatency_2.6.38-3.30~ppa1_amd64.deb

Installed in that order. Works fine, xruns are better for me than generic and it didn't break anything with my nvidia binary drivers (260.19.06) or anything else for that matter. 

So if you came here wondering where -rt has gone... this works well!

---

