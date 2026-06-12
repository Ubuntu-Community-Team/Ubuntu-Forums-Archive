---
title: "Rosegarden says  &quot;System Timer Resolution is too low&quot;"
date: 2008-12-03
forum: Ubuntu Studio
---

### Post by Dbtm on 2008-12-03
Hi. I just installed Ubuntu Studio 8.10 and I want to use Rosegarden for recording audio and midi. 

When I start up Rosegarden I get the message "System Timer Resolution is too low" It suggests I run sudo modprobe snd-rtctimer in the terminal, but I get the message: FATAL: Module snd_rtctimer not found.

It also suggests I may need a "multimedia-optimized kernel". But I'm running Ubuntu-Studio!

Any suggestion will be appreciated.

---

### Post by thorgal on 2008-12-03
type in a terminal:

```

grep CONFIG_HZ /boot/config*

```

what does it say ?

---

### Post by Dbtm on 2008-12-04
thank you for your quick reply! this is what i get:

/boot/config-2.6.27-7-generic:# CONFIG_HZ_1000 is not set
/boot/config-2.6.27-7-generic:# CONFIG_HZ_300 is not set
/boot/config-2.6.27-7-generic:CONFIG_HZ=250
/boot/config-2.6.27-7-generic:# CONFIG_HZ_100 is not set
/boot/config-2.6.27-7-generic:CONFIG_HZ_250=y
/boot/config-2.6.27-9-generic:# CONFIG_HZ_1000 is not set
/boot/config-2.6.27-9-generic:# CONFIG_HZ_300 is not set
/boot/config-2.6.27-9-generic:CONFIG_HZ=250
/boot/config-2.6.27-9-generic:# CONFIG_HZ_100 is not set
/boot/config-2.6.27-9-generic:CONFIG_HZ_250=y

---

### Post by thorgal on 2008-12-04
that's one of your problem. A linux DAW should have this kernel parameter set to 1000Hz. 250Hz is fine for servers but this is very conservative. You will improve the your system by increasing the main timer freq. 

Unless you know how to rebuild a kernel, I suggest you pick some realtime patched kernel by installing a package called linux-rt.
However, if you end up with the latest 2.6.27-rt-something, you will have problems with MIDI. You need an older kernel like 2.6.24 and hopefully, your hardware is all supported by it.

Yeah, this situation sucks a bit. You would think that higher release numbers imply better stuff, but not necessarily ...

---

### Post by Dbtm on 2008-12-05
I just installed linux-rt 3.6.27 using the package manager just to check it out, but I still get the same exact message in Rosegarden. Shouldn't the Grub show a menu at startup?

The package manager didn't show any older kernel versions. :(

---

### Post by thorgal on 2008-12-05
Hi there,

I wish I could help you more on that one but I am not the right person in the end, I tend to customize my system heavily, compile stuff myself, tweak stuff, etc, I am not relying on prepackaged distros like Ubuntu Studio. The goal of such a distro looks more like some sort of utopia than anything else.

Maybe some Ubuntu Studio guru can help here. My advice would be for you to compile your own kernel, disable services that are not necessary and focus on the DAW aspect of your system (drop 3D effects, etc). That's not what you want to go through if you are not into unix / linux sys-admin'ing

---

### Post by Areia on 2008-12-05
> **Dbtm said:**
> I just installed linux-rt 3.6.27 using the package manager just to check it out, but I still get the same exact message in Rosegarden. Shouldn't the Grub show a menu at startup?

The package manager didn't show any older kernel versions. :(

Hi, 
I  guess your RT kernel is not installed because I cannot see it in your "grep" command.

---

### Post by thorgal on 2008-12-05
he installed 2.6.27 after he reported the grep output.

---

### Post by Dbtm on 2008-12-05
I'm willing to rebuild my kernel and tweak it, but I'm a newbie to linux. :( I will deeply appreciate any advice on how to do that.

I got a completely new system, so I'm willing to take any chances and start from scratch. I really really really want to get started making music in linux!  

Thank you.

---

### Post by thorgal on 2008-12-05
I would suggest to install 64Studio. It is a debian distro tailored for audio prod. It is a bit conservative but is really successful for many people. Debian was the seed for Ubuntu so it's not that different. However, if you have fancy hardware that Ubuntu could support nonetheless, chances are you will experience issues with debian. But if you don't mind dropping Ubuntu, I would try 64Studio.

---

### Post by Areia on 2008-12-05
> **thorgal said:**
> he installed 2.6.27 after he reported the grep output.

I've tried to use the new Intrepid(kernel 2.6.27), with no sucess... a lot of things don't work well... I'm back to "Hardy", works perfectly. Try to put "Hardy" and wait until the Ubuntu-Studio team really improve the new Kernel.

---

### Post by Nu music project on 2008-12-06
I just wanted to say that I'm in the same boat, so Ill be watching this. All I want to do is run music software.  If I need to become a programmer to do it then I will learn but I don't know what I need to learn.  Its all very well saying "build a kernal" but I wouldn't know what to put in.

---

### Post by thorgal on 2008-12-06
it's not about becoming a programmer, it's about understanding your system, maintaining it, tweaking, optimizing it, ...

there's an excellent debian howto about how to build your realtime kernel. It is regularly updated :

[http://forums.debian.net/viewtopic.php?t=17035](http://forums.debian.net/viewtopic.php?t=17035)

Try it and report. This applies to ubuntu as well since debian is the underlying OS.

---

### Post by Nu music project on 2008-12-06
> it's about understanding your system, maintaining it, tweaking, optimizing it, ...That's kinda what I meant, but that link isn't a tutorial.

---

### Post by babarosa on 2008-12-07
Hello Dbtm and the others!

If you want to work with Rosegarden and some other audio applications I suggest the following, you will get a very fine working Linux audio station:

Setup a completely fresh Ubuntu 8.04.1 (Hardy Heron) insatllation!
Install the RT-Kernel with "sudo apt-get install linux-rt". The rt-kernel for 8.04.1 works fine, real timer solution is 1000Hz.

Because 8.04.1 is an older version, you will not get the newest apllications from the repositories. BUT: visit "www.getdeb.net" and change the site to version "hardy heron" (beware, the default appearing site shows the software for intrepid ibex, that is 8.10!)

There you get the newest software versions you need: audacity 1.3.6, rosegarden 1.7.2, ardour 2.5.1 (it's not the newest but new ;-)), gimp 2.6.2, ...

8.04.1 to my mind is a good sytem!

Good luck and have patience, Linux is a lot of fun but takes tinkering time!
Greetings from Austria to the whole linux world

---

### Post by Glynubu on 2009-02-20
I found this last suggestion helpful
Thanks

---

### Post by Reeman on 2009-02-20
> **Dbtm said:**
> I just installed linux-rt 3.6.27 using the package manager just to check it out, but I still get the same exact message in Rosegarden. Shouldn't the Grub show a menu at startup?

The package manager didn't show any older kernel versions. :(
You are most likely still booting into the "generic" Unfortunately the realtime is not the default any more so you need to press esc and get to the grub kernel list before booting into a kernel. The new kernel should be down the list and not at the top of the list. Until the 2.6.28 stable come out we are most likely not going to have RT in Ubuntu. I know it sucks but unfortunately there have been too many issues with unreasolved 86_64 video drivers with the real time kernel. 

The devs have had to go back to the realtime patches because the kernel build no longer supports changing the essential sections, and we have to wait for patches again.

---

### Post by serapis5 on 2009-09-06
@reeban & glynubu:

It's been a while, but just an update to all that you talked about.  I am running Intrepid with the same issues as listed above.  I installed the rt kernel from the intrepid repos and Rosegarden has now stopped giving the errors.  Since some questions seemed to arise regarding this in an earlier post, I thought the info might prove useful.

If you edit the /boot/grub/menu.lst you can make the rt kernel default by commenting out all other kernels (## at the beginning of the kernel lines) or by moving the kernel order around so that rt is the top kernel.  Just in case you don't feel like manually selecting the kernel every time.  If I misspelled your names I apologize, and I hope you have found some solutions.

---

### Post by hanzomon4 on 2009-09-14
I'm going to file a bug against the new rt kernels, the timer is set to 250
```
/boot/config-2.6.31-3-rt:CONFIG_HZ_250=y
/boot/config-2.6.31-3-rt:# CONFIG_HZ_300 is not set
/boot/config-2.6.31-4-rt:CONFIG_HZ=250
/boot/config-2.6.31-4-rt:# CONFIG_HZ_100 is not set
/boot/config-2.6.31-4-rt:# CONFIG_HZ_1000 is not set
/boot/config-2.6.31-4-rt:CONFIG_HZ_250=y
/boot/config-2.6.31-4-rt:# CONFIG_HZ_300 is not set

```

---

### Post by fermulator on 2010-06-19
As per [http://ohioloco.ubuntuforums.org/showpost.php?p=9057240&postcount=4](http://ohioloco.ubuntuforums.org/showpost.php?p=9057240&postcount=4), the new system timer can be used:

```
sudo modprobe snd-hrtimer
```

---

