---
title: "Ubuntustudio or 64studio?"
date: 2008-05-12
forum: Ubuntu Studio
---

### Post by K.Morgan on 2008-05-12
Trying to make a choice between Ubuntustudio and 64studio.  I've been getting people telling me that 64studio is faster and has a real time kernel, but doesn't Ubuntustudio have this?  If both are based on the same kernels and both use real time kernels how can one be better than the other?

Kristian

---

### Post by Stochastic on 2008-05-12
UbuntuStudio has a realtime kernel too.  But that doesn't mean they'll run at the same speed.  At the time of compiling for each binary package, certain option flags are set that make a difference in performance, at boot time different apps are loaded, during normal operations different background apps will run, and the default settings for each distro is different.  Better is a judgment call...  they're both based on Debian so you won't see huge differences if you start really analyzing the systems.  That being said, Ubuntu is an offshoot of Debian (and has moved a fair distance [on the surface] from it, last I checked), and Ubuntu Studio is an adjustment of Ubuntu; Studio64 is a direct offshoot of Debian.  My personal choice comes from the community of development around Ubuntu (it's huge).  Though one might argue that Ubuntu is too big to support a niche such as pro audio production (UbuntuStudio's adjustments for Ubuntu can only do so much), and Studio64 is small enough and independent enough to have more flexibility.  Ubuntu does have a huge array of built in apps and if you plan on doing a variety of tasks on your computer, other than just audio, it may be more usable (and it looks nicer).  But they are fairly similar in the wide world of OSes.  Try both and decide for yourself.  You could even dual boot between the two, while you're test driving them.  After all, it's not like it's a major purchase you're making.

---

### Post by K.Morgan on 2008-05-12
Thanks.  I've been testing 64studio for about a week now and i do like it a lot.  The problem is that my wireless adapter doesn't work with it (Netgear WG111v2).  Tried going down the whole ndsiwrapper route but ends up getting to complicated for me and i give up, so haven't been able to download and install new packages. 

Installed Ubuntustudio yesterday, and out of the box does look better, but again my wireless adapter doesn't work, which is weird as it works fine in Hardy.

So far though i can't really notice any difference apart from the way it looks

Kristian

---

### Post by thorgal on 2008-05-12
Hey! I have the wireless device you mentioned. There's a linux driver for it. I don't understand why it is not recognized. When I plug it to a USB port in my laptop, I can see that the kernel driver rtl8187 (Realtek driver) is loaded.
A wlan0 interface is created. I configure it like this :

sudo iwconfig essid xxxx enc xxxx  (WEP encryption)
and then
sudo dhclient wlan0

It brings up the interface and am connected to the net.

---

### Post by MetalMusicAddict on 2008-05-12
> **Stochastic said:**
> Though one might argue that Ubuntu is too big to support a niche such as pro audio production (UbuntuStudio's adjustments for Ubuntu can only do so much), and Studio64 is small enough and independent enough to have more flexibility.

Ubuntu Studio is just as flexible as 64Studio. Ubuntu Studio is a community distro and not under control of anybody but the people on the team.

Ubuntu Studio and 64Studio are about equal in what they can do to the system.

---

### Post by Stochastic on 2008-05-12
> **MetalMusicAddict said:**
> Ubuntu Studio is just as flexible as 64Studio. Ubuntu Studio is a community distro and not under control of anybody but the people on the team.

Ubuntu Studio and 64Studio are about equal in what they can do to the system.

The argument I was suggesting (not making) was that, if say Ubuntu's main branch decided to delete PuseAudio from their repos, or switch the default audio driver from alsa to oss, Ubuntu Studio would need a lot of work to go against / fix such changes.  64Studio I guess is similarly tied to Debian, but one might argue it's less so (see [http://64studio.com/press_release](http://64studio.com/press_release)). And then again, you're the main man, so to propose such an argument against your statement seems quite silly.  And what do I know, I'm just an end user. 8-[

But yeah, just to clarify I was not suggesting that you were controlled by any one.

Edit: the more I think about this, and look into what's based off what, I realize the argument I was suggesting is kinda stupid.

MMA: out of curiosity, can you speak to any performance comparison between UbieStudio and 64Studio?

---

### Post by MetalMusicAddict on 2008-05-12
> **Stochastic said:**
> The argument I was suggesting (not making) was that, if say Ubuntu's main branch decided to delete PuseAudio from their repos, or switch the default audio driver from alsa to oss, Ubuntu Studio would need a lot of work to go against / fix such changes.
It's a quite simple change really. It's a change in a single file. :P
> 64Studio I guess is similarly tied to Debian, but one might argue it's less so (see [http://64studio.com/press_release](http://64studio.com/press_release)). And then again, you're the main man, so to propose such an argument against your statement seems quite silly.  And what do I know, I'm just an end user. 8-[
Not silly. At least you didn't come out like you knew exactly what you were talking about. Some really take hard-line positions without having a clue. You didn't. ;)
> But yeah, just to clarify I was not suggesting that you were controlled by any one.

Edit: the more I think about this, and look into what's based off what, I realize the argument I was suggesting is kinda stupid.
np. :)
> MMA: out of curiosity, can you speak to any performance comparison between UbieStudio and 64Studio?

Only difference any could actually make is stability (I personally don't see it) but that's really only on a core level since 64 and us share alot of the same packages. Some say Ubuntu Studio's HW support is better.

In the end those guys and our team are closer than you might think. We have a good dialog and work to better things in Debian so things on down the line get the changes.

---

### Post by K.Morgan on 2008-05-13
> **thorgal said:**
> Hey! I have the wireless device you mentioned. There's a linux driver for it. I don't understand why it is not recognized. When I plug it to a USB port in my laptop, I can see that the kernel driver rtl8187 (Realtek driver) is loaded.
A wlan0 interface is created. I configure it like this :

sudo iwconfig essid xxxx enc xxxx  (WEP encryption)
and then
sudo dhclient wlan0

It brings up the interface and am connected to the net.

I know, it's weird, I've never had a problem with it in Ubuntu before, but for some reason UbuntuStudio doesn't seem to know it exists.

Thanks guys for the responses, been using UbuntuStudio for a couple of days now and haven't really run into any problems, or anything that makes me think one is performing better than the other, though i must say i am starting to prefer UbuntuStudio, Oh which one to choose :lolflag:

That's the thing i love about Linux loads of choice and all completely FREE.

Kristian

---

### Post by thorgal on 2008-05-13
I chose debian sid. I tried US but it turned out eventually very unstable (don't know why, I am a very experienced debian user and I administrated it acoordingly). I switched to 64studio and upgraded it to debian sid almost right away. There was no real point in sticking to 64s. I recompiled the kernel to my own taste and needs and now, my studio PC is really stable. I did not need the huge ubuntu app collection, and most of all, the PC is a dedicated box for music work, nothing else.

---

### Post by omgwtflol on 2008-06-18
Do they have the same rt kernel?  If not, is one better than the other?

---

### Post by thorgal on 2008-06-18
I don't think I am wrong by assuming that both ubuntu and 64studio are using the same rt patches from Ingo Molnar. Moreover, ubuntu is deriving a lot of things from debian (64studio is debian). The reciprocal is true as well but not as much. Debian is releasing kernels with its own set of patches and I think ubuntu is inheriting those as well. So in all likelyhood, these kernels should provide the same performance. However, it happened once that 64studio's rt kernel was compiled with a low-mem option (< 1GB), which was ridiculous for ppl who had 1+ GB of RAM.

However, in my system, I use the vanilla kernel from kernel.org, patched with the RT patch (and the bootsplash patch as well, which surprisingly fixes something for the display of text consoles in my PC). I get rock solid performance form the vanilla kernel so I do not see the need to install a precompiled kernel from debian.

---

### Post by defun on 2010-01-02
I know, this thread is really old, but I think the question is still valid.

I started with 64 Studio. It worked quite well when it came to audio, but everything else wasn't that good. In the end I couldn't even upgrade the system because the package sources couldn't be found anymore. So I switched to Ubuntu Studio and everything was nice. (It was my first Ubuntu System.) Except for audio! ;)

The main program you want to use if you need to do semi-professional audio editing in linux is JACK. As a normal user I couldn't even start jackd by default, because I didn't have the right permissions for my firewire audio interface. When that finally worked I got a lot of XRUNs. In 64 Studio I was able to run JACK without ANY xruns. In Ubuntu Studio this wasn't possible as far as I tried.

I want to stick with Ubuntu Studio because I want to use it as a consumer as well as a producer. 64 Studio was bad on the consumer end the last time I checked. But if I can't configure Ubuntu Studio to be a good producer system it's just not good enough.

Any suggestions on how to get rid of xruns in Ubuntu Studio? (Btw: It's a clean install.)

I posted this here because it's also an answer to the question in the thread title: 64 Studio is the better producer system out of the box.

---

### Post by trulan on 2010-01-02
The permissions problem is a real pain - not because it's that hard to fix, but because it trips so many people up right at the moment when impressing them would be a much better plan.  Absolutely everybody who tries to use jack in Ubuntu or Ubuntu Studio will encounter two permissions problems.  If you want to use a firewire device it will be four permissions problems.  Jack needs permission to lock down memory, needs permission to use real time scheduling, raw1394 needs to be assigned to the video group, and your username needs to be added to the video group.  (To put this in perspective it was a bit worse in Jaunty than it is in Karmic - in Jaunty the user also needed to be added to the audio group, and the video and audio groups did not even exist but had to be manually created.)

In regard to your x-runs - what version and flavor of Ubuntu are you using?  What kernel are you running (rt or generic)?  What firewire device are you using?  And what are your jack settings?

---

### Post by defun on 2010-01-04
Version: Ubuntu Studio 9.10, Real time kernel (2.6.31-9-rt which is default in Ubuntu Studio). Firewire device: Presonus Inspire. I played with the jack settings but the same configuration that produced no xruns at all in 64 Studio produces a lot of xruns in Ubuntu Studio. So what I want to understand is where the differences are. The software in Ubuntu Studio is generally newer than in 64 Studio but I doubt that it thereby is slower. The windowmanager and desktop are the same so where's the difference? Could it have something to do with pulseaudio? I guess I should try ending some background processes that are unnecessary. Any suggestions?  (I would reinstall 64 Studio and check the differences myself, but it's really hard if not impossible to use more than 3 partitions on an iMac 24 as far as I know.)

---

### Post by mdrake36 on 2010-01-04
_I just got Karmic Studio Fired up_ and I am simply blown away by how it looks and feels.
I did have a bit of a rowe with the E-machines desktop that I was imposing my will on but I finally got the ISO Img to take and it took beautifully. 
I learned MIDI first on StudioVision (opcode RIP?) and still own a Music Quest engine.
I also used Cubasis to some success.
Downloaded Karmic Studio after I realized that Juanty wasn't handling Latency all that great. The "community" suggested UbuntuStudio.
I am a Synth Geek and was pursuing all things DX7 when I came across Hexter.
I am now a staunch Linux/GNU advocate when it comes to Music and Computers.
Hexter sends shivers down my spine.
I would like to be shure that I am Utilizing the Realtime Kernel capabilities.
I can not speak enough about Midi implimentations so please, put me to work.
I have Juanty Jackalope and Karmic Studio up and running very well. Thank you.

---

