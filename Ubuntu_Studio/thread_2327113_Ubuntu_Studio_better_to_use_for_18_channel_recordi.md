---
title: "Ubuntu Studio better to use for 18 channel recording?"
date: 2016-06-07
forum: Ubuntu Studio
---

### Post by Autodave on 2016-06-07
Currently running Xubuntu 16.04 and having some issues with recording 18 channels at any kind of quality.

Is Ubuntu Studio better for recording than Xubuntu? Is there a difference in the kernel?

I have been reading a lot and have several ideas on what to do to the recording PC to get more performance, but was wondering if Ubuntu Studio would help at all.

Lastly, would I have to completely re-install or is there a front end that I could just install. And where would I get it?

Thanks in advance!

---

### Post by yoshii on 2016-06-08
From what I understand, you could install the ubuntu low-latency kernel and select it at boot time for better performance.  
It is available via apt-get or maybe Synaptic Package Manager.  Search the forums here for more info on it.  

Also, you will want to disable file access time logging in /etc/fstab via the "noatime" keyword.  
Disabling file access logging is supposed to speed up disk actions a lot since file access time logging isn't needed.  
File modification and creation dates are still logged, so it won't mess up your system if you do it right.  

Other than that, I think Ubuntu Studio changes a few permissions settings for some kind of audio group so that audio programs get better performance.  
But that is more complex than I know how to do.  I think the swappiness settings in Ubuntu Studio are the same as in Xubuntu.  

In both Xubuntu and Ubuntu Studio, disabling unneeded services has to be done manually.  
You can create the *.override files and also check the settings in Session and StartUp:Application AutoStart.  

I don't really know that much about the kernel differences.  
I do believe that Ubuntu Studio comes with more audio converter backend programs and they are probably more up to date.  (SoX, FFMPEG, etc).  

I am curious about this topic also, because I have the feeling that Xubuntu is less bloated than Ubuntu without all the creative stuff chosen.  
But this is hard to verify.  

Also, there are the power manager CPU settings which can be changed from On Demand to Performance.  
Here's my main list of tips (still mostly good for v16.04.x too)...
[http://ubuntuforums.org/showthread.php?t=2309922&highlight=informal+tips](http://ubuntuforums.org/showthread.php?t=2309922&highlight=informal+tips)

---

### Post by Autodave on 2016-06-09
Also, you will want to disable file access time logging in /etc/fstab via the "noatime" keyword.  
Disabling file access logging is supposed to speed up disk actions a lot since file access time logging isn't needed.  

First of all, thank you so much for your reply!!

Secondly, I know that I will have to edit that file, but please tell me exactly how to do that. I know where to find it and how to edit it, but exactly what am I adding, subtracting, etc.

Again, many thanks!

---

### Post by CrocoDuck on 2016-06-10
> **Autodave said:**
> 
Is Ubuntu Studio better for recording than Xubuntu? Is there a difference in the kernel?


The lowlatency kernel is a standard kernel with few parameters tweaked in order to make the system able to reach lower audio round-trip latency with higher stability (less buffer overruns). As yoshi2 said, you can install it on your standard Xubuntu. On top of that Ubuntu Studio 16.04 implements standard configuration files interventions that you can find discussed [here]("http://wiki.linuxaudio.org/wiki/system_configuration"). You can replicate them without issues and everything is well explained in details. Skip the RT kernel thing for the time being and test the lowlatency one in the repos first.

I suggest to use [quickscan]("https://github.com/raboof/realtimeconfigquickscan") to help locate areas of interventions. It is very easy to install and run.

Have also a look at my blog page about [Linux audio documentation]("https://thecrocoduckspond.wordpress.com/2015/10/26/pro-audio-linux-documentation/") and [Ubuntu Studio 16.04]("https://thecrocoduckspond.wordpress.com/2016/05/15/a-look-at-ubuntu-studio-16-04/"), maybe they contain useful info for you.

---

