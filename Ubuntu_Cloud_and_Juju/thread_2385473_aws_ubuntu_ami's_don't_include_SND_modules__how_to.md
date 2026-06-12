---
title: "aws ubuntu ami's don't include SND modules?  how to include them"
date: 2018-02-20
forum: Ubuntu Cloud and Juju
---

### Post by bmullan2 on 2018-02-20
On AWS EC2 I use Ubuntu 16.04 and have applications that don't need a real sound  device (ie card) but they do at least have to have the Linux **ALSA SND-DUMMY device** installed.   
 
 My use-case is with Containers.. which I see quite a few other people  asking about Sound support for also... just I have yet to see them ask  this question.
 
 Trying the following command line I find that the linux Module SND-DUMMY is not even included in the AWS Ubuntu AMI Linux modules ??
 
 *root@ip-10-180-42-188:~# modprobe snd-dummy ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss*
 *modprobe: FATAL: Module snd-dummy not found in directory /lib/modules/4.4.0-1022-aws*
 *modprobe: FATAL: Module snd-pcm-oss not found in directory /lib/modules/4.4.0-1022-aws*
 *modprobe: FATAL: Module snd-mixer-oss not found in directory /lib/modules/4.4.0-1022-aws*
 *modprobe: FATAL: Module snd-seq-oss not found in directory /lib/modules/4.4.0-1022-aws*
 
 The Reference for the SND-DUMMY for ALSA is found here:
 [https://www.alsa-project.org/main/index.php/Matrix:Module-dummy](https://www.alsa-project.org/main/index.php/Matrix:Module-dummy)

So far I've not been able to find any way to include them either.

Does anyone know of anyway to build a new kernel for Ubuntu on AWS EC2 so it includes the SND modules.

Thanks
Brian

---

### Post by TheFu on 2018-02-21
You don't need a new kernel. You just need the snd-dummy module.
Since the kernels are shared, the hostOS needs it, if containers will make use of it.

But realistically, to have sound work, it is better to transfer the audio data to the machine you are sitting behind for playback almost always.  There might be exceptions, but I can't think of any right now.

---

