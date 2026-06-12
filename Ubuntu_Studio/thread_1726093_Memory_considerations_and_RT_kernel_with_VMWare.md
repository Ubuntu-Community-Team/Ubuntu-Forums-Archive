---
title: "Memory considerations and RT kernel with VMWare"
date: 2011-04-10
forum: Ubuntu Studio
---

### Post by ubnewbie2 on 2011-04-10
I have 10.04 lts, with Ubuntu Studio installed. 

I also have some Windows apps I still use for music (for example PG Music's Band_in_a_Box) that I run in a VMWare virtual machine when I need to.

My question is, how much RAM is best for Ubuntu Studio - using Ardour mainly.  My system has 2GB, and I often allow 1GB for the VMWare machine, leaving a bit less than 1GB for linux to run in.  

Is this enough for Ubuntu Studio / Ardour?   RAM is relatively cheap, so is it worth buying another 2GB stick of RAM?

Also, I haven't installed the RT kernel yet and it still seems to be working without xruns - but then I haven't pushed it hard either.  Any problems with VMWare and the RT kernel?

---

### Post by sgx on 2011-04-10
> **ubnewbie2 said:**
> I have 10.04 lts, with Ubuntu Studio installed. 

I also have some Windows apps I still use for music (for example PG Music's Band_in_a_Box) that I run in a VMWare virtual machine when I need to.

My question is, how much RAM is best for Ubuntu Studio - using Ardour mainly.  My system has 2GB, and I often allow 1GB for the VMWare machine, leaving a bit less than 1GB for linux to run in.  

Is this enough for Ubuntu Studio / Ardour?   RAM is relatively cheap, so is it worth buying another 2GB stick of RAM?

Also, I haven't installed the RT kernel yet and it still seems to be working without xruns - but then I haven't pushed it hard either.  Any problems with VMWare and the RT kernel?

There are some recent ubuntu-vmware related discussions at this results page. 

[http://www.google.com/search?q=linux+vmware+problem+%22rt+kernel%22&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=](http://www.google.com/search?q=linux+vmware+problem+%22rt+kernel%22&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=)

I also have 2 gig ram, and moving to 4 gig will be my
next upgrade. I hope to get proficient with linuxsampler and ardour3,
which likely will benefit when using larger .wav and sample format files. Yoshimi, and rakarrack seem OK for now, though my cpu is not
a monster by 2010/11 standards.
Cheers

---

### Post by ubnewbie2 on 2011-04-11
Hmm, not sure whether VMWare will work or not, with the rt kernel, after reading some of that.

If I install the rt kernel and it breaks VMWare, how easy is it to go back to the normal kernel?

Also, I'm not seeing any xruns yet with the normal kernel.  How important is it, to use the rt kernel?

---

### Post by sgx on 2011-04-12
Most setups install a new kernel, and leave it as an option
at boot time, without removing anything. I have 3  kernels and XP to choose from at the moment.
If you are recording/playing music without audible noises,
life is good! To me, xruns without audible traces are irrelevant.
I have never looked for them, but see messages in a terminal sometimes saying they are partying at my expense. There are also rare times when recording dropouts are clearly heard, but the actual recording does not
contain them.
Lack of xruns is a sign of solid configuration. I can run out of ram/cpu easy enough, definitely no doubts when that happens! ;)

The older I get, the more often I say
'if it ain't broke, don't fix it' :)

---

### Post by ubnewbie2 on 2011-04-12
yep, good philosophy always.  Thanks.

---

### Post by trulan on 2011-04-13
It's been a while, but I used to use VMware regularly in a Ubuntu host running RT kernels.  I did have to apply a patch to get the VMWare modules to build on the 2.6.33-rt kernel, IIRC that wasn't needed on 2.6.31-rt.  Once the modules were built, it ran great.  I don't have a link to the patch handy though, like  I said it's been a while.

I was running XP in a virtual machine and giving it 512Mb of my 2Gb ram, but then I never used any memory-intensive programs in windows.  How you balance the memory is going to depend very much on your individual usage.

Edit: I knew I posted a link to the aforementioned patch somewhere.  To quote myself:
> VMWare player - several modules fail, here's a patch:
[http://communities.vmware.com/message/1515928](http://communities.vmware.com/message/1515928)
This patch has a typo and misnames a file.  After running the patch,  rename /usr/lib/vmware/modules/source/vblock.tar to vmblock.tar

But, as has been said before, if it ain't broke, don't fix it - depending on your hardware, particularly your soundcard, the RT kernel could make things worse rather than better.  Me, personally, using a firewire soundcard?  The RT kernel is a must-have on my system.  YMMV.

---

