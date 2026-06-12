---
title: "NI Audio Kontrol 1 usb sound card popping, clicks with the 11.04 variants"
date: 2011-07-27
forum: Ubuntu Studio
---

### Post by dilidon on 2011-07-27
Hello,
I got an NI Audio Kontrol 1 external soundcard and it should be quite well supported in linux via alsa drivers. The card is working fine on other distros. So a hardware problem is ruled out. It kind of works out of the box with Ubuntu Natty 11.04 64-bit and also Ubuntu Studio 11.04 x64. It also works on AV Linux and Win 7 x64. Now - the difference is that under Win and AV Linux the card works without any glitches, hickups, noise, scratches in sound. But under a fresh install of both mentioned Ubuntu variants I get a rather annoying and loud irregular short intense noise. After installing Ubuntu Studio I also avoided any updates, as I think the noise appeared in standard Ubuntu after certain updates, which may or may not have been related to the medibuntu repository. Maybe it has to do with pulseaudio but not sure.

Some forums suggested such glitches could originate from USB or Wifi drivers, I plugged out all USB devices and turned off Wireless. The glitces remained. I also tried removing and reinstalling alsa-base as was suggested in one forum dealing with similar issues. Also tried removing .pulse from user's home. Nothing. So now I'm out of simple solutions and must ask for help from you guys to diagnose and solve the problem.

I need it working for audio production and I would prefer to stay in the Ubuntu family as I know my way around in terms of looking for solutions and I Ubuntu has better hardware support for the rest of my gear. However, if I cannot get the sound right on that NI card, that will be an automatic show stopper. It is a rather good and quite well supported sound card and a brand new laptop.

Short specs:
Dell Inspiron R15 / n5110, i5 2410M, nVidia GT52M (drivers not installed because of optimus technology issues), 4 G ram, 7200 rpm, so enough horsepower. It does have USB 3.0... in case that could make some drivers lose it... Fresh and updated Ubuntu Natty 11.04 with medibuntu enabled and gnome 3 installed, fresh *not* updated Ubuntu Studio 11.04 the way it came out of the box.

Any advice as to how to go about it will be greatly appreciated. Thank you.

---

### Post by sgx on 2011-07-30
> **dilidon said:**
> Hello,
I got an NI Audio Kontrol 1 external soundcard and it should be quite well supported in linux via alsa drivers. The card is working fine on other distros. So a hardware problem is ruled out. 
Hi, it might be that a different kernel is needed. 
Is the periods/buffer in qjackctl set to 3 for usb devices?
Have you increased the Timeout (msec) setting?

[http://packages.ubuntu.com/lucid-updates/i386/linux-image-2.6.31-11-rt/download](http://packages.ubuntu.com/lucid-updates/i386/linux-image-2.6.31-11-rt/download)
I used this one in a non-ubuntu setup, but it might be worth a try.

I don't know if the kernel used by avlinux would work, but it
might be worth a shot.

[http://bandshed.net/kernels/](http://bandshed.net/kernels/)  -these are avlinux kernels

 Cheers

---

### Post by sgx on 2011-07-30
"usb 3.0" native instruments problem

this line put in google shows others also have problems with daft usb 3.0 implementations.

Does the kernel you have support 4 gig ram? (pae extensions)
At least one of the ports should be a usb 1-2 combo for compatibility.
Perhaps a bios option to shut down 3.0?

Cheers

---

### Post by dilidon on 2011-08-02
> **sgx said:**
> "usb 3.0" native instruments problem

this line put in google shows others also have problems with daft usb 3.0 implementations.

Does the kernel you have support 4 gig ram? (pae extensions)
At least one of the ports should be a usb 1-2 combo for compatibility.
Perhaps a bios option to shut down 3.0?

Cheers

Thank you for your effort. No success so far.

1) USB 3
The card is plugged into a USB 2.0 port already (have tried all ports). And there is no USB 3.0 disable option in the bios.

2) Kernels
My Ubuntu Natty was running the 2.6.38-10-generic and Ubuntu Studio (11.04) was running the 2.6.38-10-generic kernel (as said, the problem is present in both Ubuntu variants).

Non-natty -rt kernel
Tried the -rt kernel you pointed me to (for amd64 architecture, not i386) but the result was (1) a messed up display resolution (probably drivers, but I didnt even get to fixing that because of points 2 and 3), (2) no sound but only those pops, and (3) a system freeze in 60 seconds after the bootup.

3) PAE
Regarding the -pae kernels - the 64-bit system does not need a -pae kernel as was confirmed on the forums (and also it is not available in the 64 repositories anyways, I checked right after you suggested it, although I was in doubt as to whether I needed it anyways because on a 64-bit system this should not be an issue).

4) Jack
It is not a jack issue as the jack settings do not apply to current situation - the cracks and pops are there already without trying to do anything special (like jack etc). Just a common desktop situation - fire it up, plug the audio device in, turn the music on. Whenever a sound is played (under Ubuntu and U-Studio), a crack or a pop comes as well, and it continues a while after the sound dies... and then it fades away. (It seems to be linked to producing sound, it is not independent or random).

5) Weirdness
At few random boots the problem disappears. Have tried diagnosing by unplugging other devices, by booting up with the card plugged in and without it - have found no correlation between any of this so far.


-Ideas-

Should I perhaps just try a 32-bit version of Ubuntu Studio to see if that's any better? Why would it make any difference though...

Pulseaudio?

(PS. I did not try the AVlinux kernels yet as I wouldn't be 100% sure as to what I was doing anymore - never used a custom kernel, let alone built a kernel from source. Approaching the limits of my current knowledge. Is building kernels from source safe in terms of being able to boot the machine afterwards should something go wrong? (I may be unable to recover in reasonable time without assistance. I simply do not have the luxury of being locked out because of tinkering around for testing:) )

Tnx again.

---

### Post by sgx on 2011-08-02
Hi, if you have a separate /home partition, reinstalls can be
told to not re-format it, so you keep your personal settings
and need not reconfigure everything, saving lots of time.

ps ux will show the running processes, if pulseaudio shows up

killall pulseaudio (or whatever name it goes by)

I would try the 32 bit, and also get jackd working, it is crucial to set the periods/buffer to 3 for a usb device. And jackd is like
asio in windows, a necessity. There are user and permissions
configurations to set up for jackd, but its gui wiki is

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

I would read the links from bottom to top, the bottom one may be all
you need for now. 

This is all beta/alpha software, 64 bit is problematic enough
for commercial systems, so people coding for free, sometimes
with minimal or no documentation, are doing an amazing job
against all odds. My 32 bit system is fast and stable.
Cheers

(Kernels don't have to be compiled, ready made ones can be installed
by synaptic, or dpkg -i kernelxyz.deb) Once it is installed, reboot,
and it should be in the list of boot options, awaiting selection.

---

### Post by trulan on 2011-08-03
There'd be no harm in trying a kernel from AVLinux, except that AVLinux is 32 bit only, so before trying that you'd have to reinstall Ubuntu Studio as 32 bit.  Also it's not awfully hard to build a kernel, but it is a bit of a learning curve.  You won't ruin your system, worst-case would be you'd just build a new kernel that would fail to boot, you can still select you old one at bootup.

---

### Post by psycho_killer on 2011-08-19
dilidon, did you figure this out?  I'm having the exact same problem.  Playing any sound through my Audio Kontrol 1 (with for instance Audacious) results in snaps / crackles / pops in the audio.  Sometimes I also get these glitches when no audio is playing.  It works perfectly in Windows 7 64-bit.

Ubuntu 11.04 64-bit Classic Mode
2.6.38-11-generic
HP dv7t quad
Intel quad core i7-2630QM 2.0 GHz
8GB RAM

---

### Post by sgx on 2011-08-20
Hi, you might want to go through qjackctl and try turning on
all the different options, and combos of them, maybe start with trying higher values for frames/period and period buffer of 3 for usb.
Try other distros in live mode, bodhi, pclinusos minime, macpup
and others are small downloads, avlinux uses a different kernel,
another possibility.

You can also shut down all your house circuits but the one the computer is on, make sure the fridge and all flourescent lighting is unplugged, and when sound is playing, unplug the monitor too. Some interfaces are very sensitive to power quality, and proximity devices.
:popcorn:

---

### Post by psycho_killer on 2011-08-23
Thanks for the suggestions sgx.  I appear to have solved the problem (for now anyway) by installing the -lowlatency kernel.  I followed the instructions here to do so: [http://longspine.com/how-to/real-time-kernel-on-ubuntu-10-10-maverick-meerkat/](http://longspine.com/how-to/real-time-kernel-on-ubuntu-10-10-maverick-meerkat/)

---

### Post by dilidon on 2011-11-30
> **psycho_killer said:**
> dilidon, did you figure this out?  I'm having the exact same problem.

Hey. Sorry for disappearing for a little bit. Got sidetracked for a while. Now back on track. First of all, I appreciate everyone's input. Thank you very much for taking the time to read and respond. Second - the answer is no and yes. The way I solved it on Ubuntu Studio was by simply installing a new 11.10 version 20 minutes ago (still x64, out of curiosity). I have two external sound cards plugged in at the moment - one being the same old NI Kontrol 1 - and everything seems to work perfectly. Out of the box, too. :guitar: Will test and provide further feedback if need be, so anyone else looking for the same information will be up to date. Tnx.

---

### Post by sgx on 2011-12-01
Good to see 11.10 x64 working. Ubuntu could use to get on a roll :)
Cheers

---

