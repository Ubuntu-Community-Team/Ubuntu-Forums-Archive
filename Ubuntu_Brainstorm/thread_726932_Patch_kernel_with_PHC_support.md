---
title: "Patch kernel with PHC support"
date: 2008-03-17
forum: Ubuntu Brainstorm
---

### Post by Supermattt on 2008-03-17
"Linux Processor Hardware Control is a patch for the Linux kernel that provides a userspace interface to control the core voltage of a computer processor(s).

The main use of this interface is to lower the core voltage of a laptop's CPU ("undervolt") "

[https://www.dedigentoo.org/trac/linux-phc/](https://www.dedigentoo.org/trac/linux-phc/)

I gained many precious minutes of battery on my laptop in decreasing the maximum voltage of my CPU ( Core 2 Duo ).


This patch can't be added just like a module, it requires a modification in the core of the kernel and it can't be used at this time with Ubuntu default kernel.


I admit that hhis feature is made for expert people, but add it into the kernel doesn't cost much and can be very usefull for whom want to use it.

Thanks for your time :)

---

### Post by Supermattt on 2008-03-19
up ?:popcorn:

---

### Post by gnomeuser on 2008-03-19
Any suggestion that starts with "patch the kernel" should be followed with "why is this not upstream yet and what is lacking for it to be upstream".

---

### Post by info2 on 2008-03-23
PHC could be added as a module because it is (in versions above 0.3) just patching acpi-cpufreq but not the entire kernel. 

But the project needs developers.
Currently it is just supporting Intel CPUs (Centrino Mobile and Core / Core2)... an early version of a patch for AMD-CPUs is available, too but needs to be polished and documentated.

The best solution would be to write a new kernel module that includes all functions of phc. An early set of ideas is available.

But because of missing developers and support I stopped working on on this project and the GUI.

A couple of developers with AMD and Intel CPUs would change my moods :)

---

### Post by 23meg on 2008-03-23
> **gnomeuser said:**
> Any suggestion that starts with "patch the kernel" should be followed with "why is this not upstream yet and what is lacking for it to be upstream".

Or just a link to [https://wiki.ubuntu.com/KernelPatches](https://wiki.ubuntu.com/KernelPatches).

---

### Post by Ares Drake on 2008-04-04
I unfortunately have no programming experience other than html and php, but I am very interested in this topic! I own a Core2Duo notebook and would gladly help if I can be of any help.

---

### Post by helgesdk on 2008-04-11
It seems linux-phc and a GUI tool (PHCTool) is now available at [http://phc.athousandnights.de/](http://phc.athousandnights.de/)

Going to try it out in Hardy :)

---

### Post by helgesdk on 2008-04-16
I'm getting awesome results with the linux-phc patch. I've lowered all voltages by ~30% without any stability issues. This results in the max temperature dropping from ~80-85 °C to ~60-65 °C at full load.

I've even created an installation/compile script for Hardy and an automatic undervolter.
Also included in the .tar.gz is my pre-compiled acpi-cpufreq module for kernel 2.6.24-16-generic (probably works for other 2.6.24 subversions).
Unpack the .tar.gz and do an 'svn up' to retrieve linux-phc patches from the public repositories.
Run 'linux-phc.bash' to compile your own kernel module and 'linux-phc-optimize.bash' to begin undervolting.
To use the pre-compiled acpi-cpufreq module, backup and replace '/lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko' with 'ubuntu-2.6.24-acpi-cpufreq.ko'.

Note that some Centrino systems might use speedstep-centrino instead of acpi-cpufreq.
I strongly recommend reading the official guides in order to determine what's right for your system.

Anyway, use at your own risk :)

---

### Post by smartboyathome on 2008-04-16
From what they said on the Gentoo site, it may damage your CPU to have this installed, since it hasn't been tested (and coming from the Gentoo site says something to me :)). Therefore, I think it would be safer to leave this out until more testing is done.

---

### Post by coolos on 2008-04-26
I use the phc patch on my laptop for some months, and nothing bad happened : my processor (pentium M) runs cool, and for a longer time.
I didn't hear about anybody who had broken a cpu using this, and undervolting is said to be safe under other OS.
I had many cpu freezes when i tried to adjust the voltage to the minimal stable settings, and all was OK when i rebooted. 

The phc project is really a good idea, as my laptop is now silent (no fan noise) and the power consumption is a lot lower.

---

### Post by Ares Drake on 2008-04-26
> **helgesdk said:**
> I'm getting awesome results with the linux-phc patch. I've lowered all voltages by ~30% without any stability issues. This results in the max temperature dropping from ~80-85 °C to ~60-65 °C at full load.

I've even created an installation/compile script for Hardy and an automatic undervolter.
Also included in the .tar.gz is my pre-compiled acpi-cpufreq module for kernel 2.6.24-16-generic (probably works for other 2.6.24 subversions).
Unpack the .tar.gz and do an 'svn up' to retrieve linux-phc patches from the public repositories.
Run 'linux-phc.bash' to compile your own kernel module and 'linux-phc-optimize.bash' to begin undervolting.
To use the pre-compiled acpi-cpufreq module, backup and replace '/lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko' with 'ubuntu-2.6.24-acpi-cpufreq.ko'.

Note that some Centrino systems might use speedstep-centrino instead of acpi-cpufreq.
I strongly recommend reading the official guides in order to determine what's right for your system.

Anyway, use at your own risk :)


AWSOME! Thank you so much for your work. Unfortuantely I read your post just a second too late as I have already made my own module. :)
No matter what I would like to use your optimisation tool. Does it work for Core2Duo (mobile) chips as well? I am running a T7200. In the script it only seems to check for cpu0 but not cpu1, so is dual core supported?

I am new to both programming and undervolting, so sorry if that question might be dumb :)

---

### Post by Medo42 on 2008-04-27
Undervolting can give huge savings under load: My Toshiba Satellite A100 (Core2Duo T5200) with both cores running cpuburn eats up 56 watts with stock voltages, when I undervolt everything to the lowest it drops to 44 watts, and the CPU fan naturally runs slower. I never had any stability issues with that setting using NHC under Windows. Having installed a patched acpi-cpufreq.ko under Linux now, there hasn't been any proplem so far with that either.

---

### Post by norman_h on 2008-04-27
I'm running an older notebook with a Dothan processor on default 8.04 which suffers from overheating due to running at full speed permanently.

I have hacked a kernel patch together which allows my Dothan to run at lower speeds (and lower temperatures).  Way to tired to post a cleaned up version of it right now.

What cores are your duos based around?

---

### Post by Ares Drake on 2008-04-27
Okay I got it running and want to share my observations with you, maybe they are of some help.

1) Another big "Thanks" to helgesdk. His tar.gz file is really awsome and makes installing PHC support as easy as copying the module acpi-cpufreq.ko to the right folder and rebooting! =D>

2) The optimizer script is also very good, however not perfect on dual cores. Let me explain why: It uses the program burnmmx to stress the cpu and then determine how much current the cpu needs under full load. However it uses only one instance of burnmmx which stressed only one of my cores - the other was idle. So I was afraid the needed current might be accidentely determined as falsely to low.
No big deal, there is an easy solution: Just run a second (parallel) instance of burnmmx: In a terminal just type:
```
burnmmx

```
and exit with strg + C when done.
Maybe you can further improve the script so that it checks for a cpu1 and if present runs a second instance of burnmmx, helgesdk?

Well that is pretty much all what is needed to get undervolting running. Finally I want to give my 2 cents on the savety of the whole procedure:

Undervolting notebook processors is not uncommon. My older notebook (Toshiba S1) even came with a Windows utility that did automatic undervolting preinstalled. So the "undervolted" processor is nothing dangerous.

The way to get there might be, if no care is taken.
What might happen:
1) The voltage controls stability and temperature. The higher the voltage the higher the temp, but without *_enough_* voltage the cpu wont be stable and your PC will lock up. In fact with the above procedure we are trying to find the minimum stable voltage to get the cpu as cool as possible. The energy saved will increase battery life as well.

2) So if you were to INCREASE the voltage, you would rise the temperature. This might damage the cpu in case it got too hot - obvious one. (Though all Intel (probably AMD as well) mobile chips are equiped with safety cut off mechanisms afaik) However with the optimizer scipt it automatically REDUCES the voltage so harm to your hardware is very unlikely.

3) To find the named "minimum" voltage, the optimizer scipt needs to test if the cpu runs stable at every voltage setting. So in case it gets too low, your notebook will lock up. Then afterwards the script knows what is too low and will stay safely above.
That sth gets damaged by locking up is rather unlikely - overclocking my desktop machine in younger years I experienced it at least a hundred times and never fried anything.

4) While locking up however you linux and all open applications crash as well. Wich might result in data loss. Be prepared to see the fsck utility at next boot up checking for data integrity. And let it run :) Also don't open any files while running the optimizer script. Furthermore, before doing this optimization, unmount as much partitions as possible to reduce the risk.

Once the scipt finishes (you need to run it several times, once for every freqency your cpu is capable of), no more lock-ups are to be expected as the script now knows the individual critical voltage for your cpu and will stay savely above.

With all these precautions I think it is rather save to undervolt.

I was able to reduce my voltage 18 steps on max frequency and to minimum on the other freqs, wich improves noise and battery life substancially.

Good luck!

---

### Post by Melf on 2008-05-01
On success story (so far :) to post:

First i downloaded the tar from helgesdk (big thanks :) and unpacked it.

Then i backed up the acpi-cpufreg.ko in /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/ and copied it over with the module from helgesdk.

And after restart it seems to be working :) I also tried the optimalisation script, it works but only tests one cpu (i have the T2450 Core Duo).

BTW, it seems the PHCtool is finally in installable condition and working nicely with helgesdks module :)
How to get it working (found on [http://wiki.ubuntuusers.de/):](http://wiki.ubuntuusers.de/):)
First you need the subversion package.
Then to install it: 
svn co [http://phctool.googlecode.com/svn/trunk/](http://phctool.googlecode.com/svn/trunk/) phctool
You can run the tool with "sudo ./phctool.py" from its directory :)
more about PHCtool: [https://sd-2431.dedibox.fr/trac/linux-phc/wiki/UsingPHCtool](https://sd-2431.dedibox.fr/trac/linux-phc/wiki/UsingPHCtool)

---

### Post by excogitation on 2008-05-01
I went through compiling that acpi-cpufreq.ko once (2.6.24.12?) and then the kernels started changing so often, I decided to do it again once the final version of Hardy came out.

The kompiled version did that faster :-)

---

### Post by Ares Drake on 2008-05-02
> **excogitation said:**
> I went through compiling that acpi-cpufreq.ko once (2.6.24.12?) and then the kernels started changing so often, I decided to do it again once the final version of Hardy came out.


You don't have to recompile each time a new kernel comes out. Just save a copy of your acpi-cpufreq.ko module file somewhere as backup - in your home dir for example. During a kernel upgrade the original file will be replaced with a newer one, wich you can backup again and replace with your old backup.

For only minor kernel changes it seems to work perfectly.

---

### Post by excogitation on 2008-05-02
Thanks, I thought so, but I didn't know.

Next time I'll try that first.

---

### Post by Roby86 on 2008-05-02
I'm using AMD Turion X2 TL-56....when I got to PHC page, there is no modules for my processor, even it's listed in the modules, I think it's K8.

Is AMD Turion X2 even supported by PHC?

Thanks...

---

### Post by gawron on 2008-05-03
OOps. Hardy kernel has just been updated to 2.24.17 and this precompiled module does not work anymore. Specifically:
```

 acpi_cpufreq: disagrees about version of symbol struct_module
```

Hmmmm, could you be so nice and prepare a version for this updated kernel? Pretty please ;-)

---

### Post by atlas95 on 2008-05-03
I have a core2duo T7500, the patch support it? I must select something special during the menuconfig?

I'm compiling normaly for the moment...I hope this work !!
Thanks a lot

---

### Post by Ares Drake on 2008-05-04
> **gawron said:**
> OOps. Hardy kernel has just been updated to 2.24.17 and this precompiled module does not work anymore. Specifically:
```

 acpi_cpufreq: disagrees about version of symbol struct_module
```

Hmmmm, could you be so nice and prepare a version for this updated kernel? Pretty please ;-)

Yeah I will do that this afternoon, in about 8h.

Edit:
Version .17 doesn't seem to be out to german mirrors as of yet. Can't get it at least so I postpone the new module to sometime tomorrow.

---

### Post by gawron on 2008-05-04
> **Ares Drake said:**
> Yeah I will do that this afternoon, in about 8h.

Edit:
Version .17 doesn't seem to be out to german mirrors as of yet. Can't get it at least so I postpone the new module to sometime tomorrow.

Right - I had hardy-proposed selected in Synaptic and it was installed from there. I guess that it might take couple of days before it hits the main repository...

---

### Post by D-- on 2008-05-05
> **gawron said:**
> OOps. Hardy kernel has just been updated to 2.24.17 and this precompiled module does not work anymore. Specifically:
```

 acpi_cpufreq: disagrees about version of symbol struct_module
```

Hmmmm, could you be so nice and prepare a version for this updated kernel? Pretty please ;-)

Here I come to save the da~y!

---

### Post by Roby86 on 2008-05-05
Once again, is Turion X2 supported in PHC??

All the job is to overwrite the file "D--" has posted?

---

### Post by D-- on 2008-05-05
1. Back up your current /lib/modules/2.6.24-17-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko
2. Copy in the one I posted
3. Install the undervolt script supplied by the people who actually make linux-phc
4. Configure
5. ???
6. **PROFIT!**

---

### Post by jhwilliams on 2008-05-05
This isn't working for me:

Using the module you provided:
```
$ modinfo acpi-cpufreq.ko
filename:       acpi-cpufreq.ko
alias:          acpi
license:        GPL
description:    ACPI Processor P-States Driver
author:         Paul Diefenbaugh, Dominik Brodowski
srcversion:     E92705B54F4E63FA296FADA
depends:        freq_table,processor
vermagic:       2.6.24-16-generic SMP mod_unload 
parm:           acpi_pstate_strict:value 0 or non-zero. non-zero -> strict ACPI checks are performed during frequency changes. (uint)

```

It doesn't "work" on boot, and:

```
$ sudo modprobe -i acpi-cpufreq 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): Invalid module format

```

I'm running Hardy 8.04 up to date as of today (on gb mirrors):

```
$ uname -a
Linux salmon 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```

What am I missing?

---

### Post by jhwilliams on 2008-05-05
> **jhwilliams said:**
> ```
vermagic:       2.6.24-16-generic SMP mod_unload
```

Woops. That one above was a modinfo on mine. This is yours:
```
vermagic:       2.6.24.3 SMP mod_unload 586 
```

586 vs. x86_64 ... that'll do 'er.

[edit]

Well, I managed to get one of those compiled. This is for Generic x86_64 kernels - not the core2 duo type. Download it at [http://www.jamesonwilliams.com/bin/acpi-cpufreq.ko.tar.bz2](http://www.jamesonwilliams.com/bin/acpi-cpufreq.ko.tar.bz2).

---

### Post by regme on 2008-05-06
Wow, tried the precompiled and the undervolting script for 2.6.24-16 and I saw massive decreases in voltage, with the top speed going from a VID of 40 down to 12 (thats 28 steps) and the biggest drop from 36 down to 1 (35 steps), and have seen noticeable decreases in operating temps and noise.

Thanks again for making the patch so easy!

---

### Post by Roby86 on 2008-05-06
Sorry folks, I am really dumb about ubuntu stuff, I've been learning a month ago when I installed it for the first time.So D-- :)

1. Back up your current /lib/modules/2.6.24-17-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko
**(I understand that completely)**
2. Copy in the one I posted - **also this one**
3. Install the undervolt script supplied by the people who actually make linux-phc-**which undervolt script-please link,description,anything...**
4. Configure - **also on this one**

I've been doing fine with RMClock on Windows XP, but I didn't manage to understand this...

Thanks a lot!

---

### Post by XRayA4T on 2008-05-06
I had a hassle that it said device busy when I tried to modprode acpi-cpufreq. I noticed that under Hardy Heron I was running speedstep and not acpi-cpufreq. By rmmod speedstep-centrino I could the modprobe acpi-cpufreq

---

### Post by excogitation on 2008-05-06
regme: you should probably leave a margin for error (e.g. it's getting warmer, ...)

Is it possible to also patch the speedstep-centrino.ko (since that would be the better choice for those Intel foks - including me).

---

### Post by Ares Drake on 2008-05-07
> **Roby86 said:**
> 
3. Install the undervolt script supplied by the people who actually make linux-phc-**which undervolt script-please link,description,anything...**
4. Configure - **also on this one**


Have a look at the link helgesdk provided in this thread. It has the undervolt-script witch probes for the lowest save voltage at any freq and writes them to a text-file.
You than have to echo them into the right config file for them to work, see in that tar file, there might be a help file.

Edit: see my post above regarding using this undervolt-script on dual-cores.

---

### Post by sdumasp2 on 2008-05-07
> **excogitation said:**
> Is it possible to also patch the speedstep-centrino.ko (since that would be the better choice for those Intel foks - including me).

Hello,
I'm also waiting for speedstep-centrino to be upgraded so that i could use the Hardy kernel instead of still using Gutsy's one...
But how did you manage to make acpi-cpufreq work for you?!
I tried lots of time, with Gutsy's kernel, Hardy's one, different releases of the patch... nothing's workins for me...
Thank you!

---

### Post by MilkeySUFC on 2008-05-07
Hey guys, 

Two questions:

1) I've installed phc correctly (I think), how do I check?

2) When running the optimizer script, it has installed cpuburn (I've checked synaptic) but running 'burnmmx' in terminal errors with unknown command meaning the optimizer can't run it either. How do I make cpuburn commands globally available?

TIA,
Milkey

---

### Post by D-- on 2008-05-07
> **excogitation said:**
> Is it possible to also patch the speedstep-centrino.ko (since that would be the better choice for those Intel foks - including me).

For reference, I built the acpi-cpufreq module for -17 earlier this thread. I have been using acpi-cpufreq since Gutsy. In Edgy and Feisty I used speedstep-centrino. My processor is a 2GHz Pentium M and I have noticed very little difference in heat levels between the two in my use since late 2006.

---

### Post by Ares Drake on 2008-05-08
> **MilkeySUFC said:**
> Hey guys, 
1) I've installed phc correctly (I think), how do I check?


I made a howto from all this info here and elsewhere and placed it here: [http://ubuntuforums.org/showthread.php?p=4908896#post4908896]("http://ubuntuforums.org/showthread.php?p=4908896#post4908896")

---

### Post by equiszeta on 2008-05-10
hi, i have installed the acpi_cpufreq module, but i cannot write neither pch_controls nor phc_vids, when i try with sudo echo this return an "access denied" message. what should i do?

ps. i'm working with 8.04 installed from win xp using wubi.

thanks.

---

### Post by excogitation on 2008-05-10
equiszeta: type sudo -s -> password,
then run your echo command again.

---

### Post by thekip on 2008-05-13
Here's a post of mine about finding the best possible Vcore for your specific cpu (no duo core experience here).

---

### Post by MilkeySUFC on 2008-05-14
> **thekip said:**
> Here's a post of mine about finding the best possible Vcore for your specific cpu (no duo core experience here).

Where?? :confused:

---

### Post by cormano on 2008-06-04
Hi there, anyone nice enought to provide a precompiled module for the new -18 kernel release? Or even better, dummy-proof instructions to do it yourself? Thanks.

---

### Post by excogitation on 2008-06-15
> **cormano said:**
> Hi there, anyone nice enought to provide a precompiled module for the new -18 kernel release? Or even better, dummy-proof instructions to do it yourself? Thanks.

[http://ubuntuforums.org/showthread.php?t=786402&highlight=phc](http://ubuntuforums.org/showthread.php?t=786402&highlight=phc)

---

### Post by mxsteini on 2008-06-25
10 Minutes ago I follewed the howto
[http://ubuntuforums.org/showthread.php?t=786402&highlight=phc]("http://ubuntuforums.org/showthread.php?t=786402&highlight=phc")

AND IT WORKED :guitar: :guitar: :guitar:

Here is my result.

Attention!!!

Save the original Version!!!

---

### Post by smartboyathome on 2008-06-25
Your howto link isn't working. It has ... instead of the full link.

---

### Post by lithorus on 2008-06-26
> **smartboyathome said:**
> Your howto link isn't working. It has ... instead of the full link.
I think he meant to paste this :
[http://ubuntuforums.org/showthread.php?t=786402&highlight=phc](http://ubuntuforums.org/showthread.php?t=786402&highlight=phc)

---

### Post by mxsteini on 2008-06-26
Hey you,
thanks ... fixed the link.
A few month ago I said to myself "I will never compile a module".
Now I was so happy that this thing was working in 10 minutes.:)

---

### Post by Brokensoul on 2008-07-02
> **helgesdk said:**
> I'm getting awesome results with the linux-phc patch. I've lowered all voltages by ~30% without any stability issues. This results in the max temperature dropping from ~80-85 °C to ~60-65 °C at full load.

I've even created an installation/compile script for Hardy and an automatic undervolter.
Also included in the .tar.gz is my pre-compiled acpi-cpufreq module for kernel 2.6.24-16-generic (probably works for other 2.6.24 subversions).
Unpack the .tar.gz and do an 'svn up' to retrieve linux-phc patches from the public repositories.
Run 'linux-phc.bash' to compile your own kernel module and 'linux-phc-optimize.bash' to begin undervolting.
To use the pre-compiled acpi-cpufreq module, backup and replace '/lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko' with 'ubuntu-2.6.24-acpi-cpufreq.ko'.

Note that some Centrino systems might use speedstep-centrino instead of acpi-cpufreq.
I strongly recommend reading the official guides in order to determine what's right for your system.

Anyway, use at your own risk :)

thanks a lot, you did great for noobs like me ! this was a feature I missed a lot from windows (used Rmclock)

---

