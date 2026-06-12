---
title: "Maverick Meerkat anybody?"
date: 2010-10-10
forum: Ubuntu Studio
---

### Post by panmanphil on 2010-10-10
I just clicked the upgrade button. Could be an interesting day!

I didn't see anything specifically for ubuntu studio though. I noticed that there will not/may not be any more real time kernel unless somebody else volunteers to maintain the updated kernels though I did see somebody say they got 8ms latency with no xruns with the generic kernel. I'm hoping this gets resolved. I switched from debian unstable so I wouldn't have to build my own kernels anymore ;-)

So, where is ubuntu studio going now? Roadmap of any sort available?

---

### Post by KillKRT on 2010-10-10
Maybe the site hasn't been yet updated...

It seems to be already available, look here:
[http://cdimage.ubuntu.com/ubuntustudio/releases/maverick/release/]("http://cdimage.ubuntu.com/ubuntustudio/releases/maverick/release/")

Bye.

---

### Post by trulan on 2010-10-10
I've been playing around with Maverick since Alpha2.  Good stuff!  The biggest change (as it affects me anyway) in Maverick is the migration from the legacy firewire driver stack to the new Juju driver stack.  This is good news and bad news for Ubuntu Studio firewire audio users.

The good news:  Better performance, better security, easier setup.  No more troublesome raw1394 permissions.

The bad news:  Daisychaining (using multiple devices) is not supported on the new firewire stack.   (should be here in time for 11.04)  So to run multiple firewire interfaces, you will need to do some module blacklisting, and after the modules are in place then you'll have to hash out the proper raw1394 permissions.

As far as the RT kernels go, 2.6.33-rt is the latest patch available.  No definitive word yet on if or when an RT patch for 2.6.35 will be released.  But whether or not the RT kernel is a benefit is largely hardware dependant, and as time goes by the need for it for audio work is decreasing.  I still see a big benefit for firewire audio, even on the new driver stack.  YMMV.

---

### Post by AutoStatic on 2010-10-11
There's a big discussion going on concerning the -rt, -realtime, -lowlatency and -preempt kernels on both the [Ubuntu-Studio-users]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users") and [Ubuntu-Studio-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel") mailing lists. Maverick doesn't have them because Alessio stopped maintaining them and if no one picks up maintaining those kernels future versions might lack them also.
For me a release without a real-time kernel is unusable, so I'll probably skip Maverick. But then I haven't completely migrated to Lucid also. Another thing is the PPA's. FalkTX, Philip5 and yours truly do not package for Maverick. The idea is to join forces (at least FalkTX, me and maybe some others) and to create a dedicated Ubuntu Studio PPA for Natty Narwhal 11.04.

---

### Post by panmanphil on 2010-10-11
I feared as much. The install removed much of my audio software and disabled the ppas. No big deal, I just added in the main packages. But the default generic kernel is an xrun nightmare on my laptop. 

I will continue to run the 2.6.33 kernel I suppose, but will have to consider the pain of building my own for awhile. I had read through a lot of the conversation about this on the mailing lists. Volunteer burnout is a terrible thing.

---

### Post by philip5 on 2010-10-11
> **AutoStatic said:**
> There's a big discussion going on concerning the -rt, -realtime, -lowlatency and -preempt kernels on both the [Ubuntu-Studio-users]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users") and [Ubuntu-Studio-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel") mailing lists. Maverick doesn't have them because Alessio stopped maintaining them and if no one picks up maintaining those kernels future versions might lack them also.
For me a release without a real-time kernel is unusable, so I'll probably skip Maverick. But then I haven't completely migrated to Lucid also. Another thing is the PPA's. FalkTX, Philip5 and yours truly do not package for Maverick. The idea is to join forces (at least FalkTX, me and maybe some others) and to create a dedicated Ubuntu Studio PPA for Natty Narwhal 11.04.

If I get time I will upgrade to Maverick on Wednesday (if I have time as planned) and when I do that I will start porting and updating stuff on my PPA for Maverick too.

---

### Post by sawtdk on 2010-10-11
> **trulan said:**
> I've been playing around with Maverick since Alpha2.  Good stuff!  The biggest change (as it affects me anyway) in Maverick is the migration from the legacy firewire driver stack to the new Juju driver stack.  This is good news and bad news for Ubuntu Studio firewire audio users.

The good news:  Better performance, better security, easier setup.  No more troublesome raw1394 permissions.

The bad news:  Daisychaining (using multiple devices) is not supported on the new firewire stack.   (should be here in time for 11.04)  So to run multiple firewire interfaces, you will need to do some module blacklisting, and after the modules are in place then you'll have to hash out the proper raw1394 permissions.

As far as the RT kernels go, 2.6.33-rt is the latest patch available.  No definitive word yet on if or when an RT patch for 2.6.35 will be released.  But whether or not the RT kernel is a benefit is largely hardware dependant, and as time goes by the need for it for audio work is decreasing.  I still see a big benefit for firewire audio, even on the new driver stack.  YMMV.

Firewire audio is functioning great on my Ubuntu 10.10. Without problems and xruns I can get as low as 2.9 msec latency on the linux-lowlatency kernel from Abogani's ppa. Amazing! 
Now I don't even need the rt-kernel.

---

### Post by trulan on 2010-10-11
> **sawtdk said:**
> Firewire audio is functioning great on my Ubuntu 10.10. Without problems and xruns I can get as low as 2.9 msec latency on the linux-lowlatency kernel from Abogani's ppa. Amazing! 
Awesome!!  That's the kind of stuff we like to hear!
> Now I don't even need the rt-kernel.Everything broke here during alpha testing when they pushed the new version of Xorg through, I got things working again the next day on the generic kernel, but I only realized this morning that the rt kernel still doesn't work in Maverick, I guess I forgot about testing that.  (I need to be able to daisy-chain my two firepods, so my studio computer is going to stay on Lucid for the time being.)  I'm not sure if the problem is with my NVidia GPU or if it's bigger than that - did I understand correctly panmanphil that 2.6.33-rt is working for you in Maverick?

---

### Post by DigitalRazor on 2010-10-12
I played with 10.10 Studio on day number two to find the right combination before I go on vaca. but it may have to wait till I get back - The absence of a low-latency kernel made for an interesting day testing before deploying on my main workstations. On my dual core system however the low latency is needed. If one runs Bristol and have JAKd set up for the lowest latency possible on a dual core setup you might run into x-runs or no x-runs with static in the audio (latency 5.6ms). With Alessio Igor Bogani's 2.6.35 low latency I was able to get to about 2.8 with no xruns running ardour and hydrogen concurrently. The only issue( and its not a biggy since I have a separate system for graphics and video. ) is that it borks my nvidia driver install. I can only chalk that up for my bad attempt to install what I was after instead of doing the complete upgrade then testing a bit at a time. I played with the 2.6.33realtime for maverick and it works pretty well. Again still borking on the nvidia drivers. You maybe wondering why I am so pent up on the nvidia drivers and realtime on all systems.. I am hoping that xadjeo takes advantage of such combination. But with Ardour 3.0 around the corner and the talks of including a video track in the work flow may negate the need to morph such system. Thanks for reading . .thats my 2 cents worth.

Production System: (2)
Dual QuadCore Opteron 
8gig Ram 
UbuntuStudo 10.10 Beta
MSI Speedster (modified for QuadCore Processors) 
Nvidia Chipset


Test System (1)
Dual Core AMD 5000+
2 Gig Ram 
UbuntuStudio Production
MSI mobo
AMD Chipset

---

### Post by sawtdk on 2010-10-12
> **trulan said:**
> Awesome!!  That's the kind of stuff we like to hear!
Everything broke here during alpha testing when they pushed the new version of Xorg through, I got things working again the next day on the generic kernel, but I only realized this morning that the rt kernel still doesn't work in Maverick, I guess I forgot about testing that.  (I need to be able to daisy-chain my two firepods, so my studio computer is going to stay on Lucid for the time being.)  I'm not sure if the problem is with my NVidia GPU or if it's bigger than that - did I understand correctly panmanphil that 2.6.33-rt is working for you in Maverick?

The 2.6.33-rt is working well here, with intel graphics.
The only problem is that pulseaudio has the habbit of crashing on the rt-kernel, so the -lowlatency feels much better for me.

---

### Post by breek on 2010-10-12
well i think there's an error [> here <]("https://wiki.ubuntu.com/UbuntuStudio/10.10release_notes")

> 
Kernels

    * Amd64
          o -generic kernel
          o -preempt kernel
          o -lowlatency kernel
          o -realtime kernel 
    * I386
          o -generic kernel
          o -preempt kernel
          o -lowlatency kernel
          o –realtime kernel 


considering that officially there's only the generic kernel (as it seems) this release seems a bit a regression

---

### Post by DigitalRazor on 2010-10-12
That's a BIG regression in my book. 10.04 is good but 10.10 had things that I was waiting on. Sorry to see Mr Bogani leave the project .. but it is understandable when you have to eat and have a roof over ones head. SO where are these patches for the 2.6.35 kernel so I can patch my own ? for I don't feel like going back to Lucid. or use any version of a generic kernel since I am in x-run hell ... Thanks in advance ...](*,)

---

### Post by DigitalRazor on 2010-10-12
I think I am going to stick with 10.04 LTS until something is worked out with 10.10 I want to thank the developers for 10.04 and extend a heart felt thank you to Mr Bogani and Falk for the PPAs that allowed me to craft a setup I can work with. I may start hacking my own kernel for 10.10 any tutorials as to what to look for would be a great start.. Thanks in advance .. .

---

### Post by trulan on 2010-10-13
The RT patch for 2.6.35 has not yet been released.  If and when it is, I'll give it a go and post my results.  Stay tuned!

---

### Post by marcoharder on 2010-10-13
Based on your expert opinions, guys, should I upgrade from 10.04 to 10.10? My gripe with 10.04 real time kernel is the fact that I couldn't use my Realtek USB wireless adapter [trulan is one of the guys who helped me here in the other thread].
 
I've been hearing great things so far about 10.10, but a few questions:
 
Will the Realtek card work? Really need wireless to work, as my room is too far from the router to make a cable connection to it.
 
Can the generic kernel really support recording now without many xruns?
 
Thanks in advance!

---

### Post by nighthawk77 on 2010-10-13
Hi guys! I plan to run clean install of new Ubuntu10.10 64bit over 32bit 10.04 version. My question is will I be able to use programs like "Pitivi", "Xine" video player and "Ksteamripper" on 64bit version?
I'm novice with ubuntu and so far I'm delighted to use UbuntuStudio for past couple of months :)
Cheers!

---

### Post by madeinfamous on 2010-10-13
*"Maverick Meerkat anybody?"*

oh yeah! :guitar:

[https://sites.google.com/site/nueusx/mm_vanilla_studio.png]("https://sites.google.com/site/nueusx/mm_vanilla_studio.png")

good to me.

---

### Post by nighthawk77 on 2010-10-13
well I've downloaded a full ISO image but get stuck when installing. It boots from the cd ok and let me do to set up keybord layout and time zone but when it comes to  "Partition manager" it seems to freeze and go nowhere. Don't know is it me or cd might not burned properly?

---

### Post by DigitalRazor on 2010-10-13
Not to cause problems for anyone with a stable system ~but here is what I cobbled together that seems to work very well. 
1~ the lowlatency kernel 2.6.35-17)(I think) for 10.04 is floating around on a PPA by falk  by the way of Bogani. I can attest to the fact it works and  really really well (knowing that the Studio spin is not commercially maintained distro of Canonical,  I wish it was) I would hope the fine folks at Canonical would put Mr Bogani on some sort of payroll for the work he has done and hopefully would continue work on this! 

In short I have experienced minimal x-runs at p32,  no xruns at  p64 to 128 (all x2) on a good quad core and decent audio hardware this will do well. Ardour reports latency at 0.7ms ( yes that is right 0.7)!! on a dual core AMD 5000+ ) :guitar: 

The falk ppa seems to be for his own distro for Lucid. Compatibility is pretty good.  It works well just be careful of any other PPAs like for KDENLive and blender - particularly 2.5x since it is not on the main repositories. I have had issues with libraries not wanting to install even if I could see them in the list ( my own inexperience may be the factor to this but since I am designing one system for audio and one for video and graphics I can deal with it . I could have gotten overzealous on the installs..). the 10.04 with the falk PPA is the way to go. of course your mileage may vary.

When I get back from performing I am going to move the installation to a dual quad core opteron and see what the real deal is going to be. As far as for installation woes ... If you haven't done so check your bios and make sure it is completely up to date. Most install issues I have ran into revolves around that. I have had an issue where the processor was the culprit (ie power saving speed doping features) and had to move to a completely different distro all together that could handle it properly. Sorry if this seems long winded but I just wanted to share what I found at the 23rd hour on the 13th day... This combination seems to be as close to 10.10 studio as one can get without hacking it up to death. 

On another note .. if there is someone out there that wants to take me under their wing to learn decent kernel hacking ( at least what to look for ) I am a quick learner - give me the pointers and I can go on from their .. 

One suggestion~ There are dozens of audio distros that use Ubuntu as their core - and now that 10.10 has the ability to parse Debian deb files this maybe good ground for someone to develop something closely resembling Planet CCRMA for Fedora/Centos where depending on what the artist wants to do. A "one stop shop" repository could do this very well I would even settle for a central server network of PPA's ( if one doesn't exist) to share the bandwidth load/cost .

 Making a living is of high importance and I do understand that sometimes the amount of work from one person seems to go monetarily  under-recognized maybe a business plan like Ardour has could be implemented. It comes down to this Quality opensource software has the ability to generate some sort of bank for those that could prevent such things as UbuntuStudio not having a realtime kernel from happening. I am sure this has been broached before .. but with a little push in a nice way, I think this would benefit all.

(Damn Long winded again) all this to say: Ubuntu has the ability to really give the regular user, Digital Content creators and Artists alike to be able to download the base system and then customize via a repository or PPA with little or no effort of the end user if all that contribute can agree on a set base of standards. Yes there are challenges. But after futzing around to get what i want off of a base system and one PPA I think its something those in control should take a long hard look, think about it and put into action in quick order.. 

Best Regards .. thanks for reading.:popcorn:

---

### Post by AutoStatic on 2010-10-14
> **DigitalRazor said:**
> The falk ppa seems to be for his own distro for Lucid. Compatibility is pretty good.  It works well just be careful of any other PPAs like for KDENLive and blender - particularly 2.5x since it is not on the main repositories. I have had issues with libraries not wanting to install even if I could see them in the list ( my own inexperience may be the factor to this but since I am designing one system for audio and one for video and graphics I can deal with it . I could have gotten overzealous on the installs..). the 10.04 with the falk PPA is the way to go. of course your mileage may vary.I would advise against using packages of an older release on Maverick.

> **DigitalRazor said:**
> On another note .. if there is someone out there that wants to take me under their wing to learn decent kernel hacking ( at least what to look for ) I am a quick learner - give me the pointers and I can go on from their .. You might want to consider joining the Ubuntu Studio devel mailing list.

> **DigitalRazor said:**
> One suggestion~ There are dozens of audio distros that use Ubuntu as their core - and now that 10.10 has the ability to parse Debian deb files this maybe good ground for someone to develop something closely resembling Planet CCRMA for Fedora/Centos where depending on what the artist wants to do. A "one stop shop" repository could do this very well I would even settle for a central server network of PPA's ( if one doesn't exist) to share the bandwidth load/cost.There are ideas of setting up a dedicated, specialized Ubuntu Studio PPA for Natty.

> **DigitalRazor said:**
> Making a living is of high importance and I do understand that sometimes the amount of work from one person seems to go monetarily  under-recognized maybe a business plan like Ardour has could be implemented. It comes down to this Quality opensource software has the ability to generate some sort of bank for those that could prevent such things as UbuntuStudio not having a realtime kernel from happening. I am sure this has been broached before .. but with a little push in a nice way, I think this would benefit all.Best way to express these kind of thoughts is to join the Ubuntu Studio mailinglists and to hop on IRC every now and then. The problem with this forum is that about 99% of the Ubuntu devs don't come here.

Best,

Jeremy

---

### Post by DigitalRazor on 2010-10-14
Thank you. I will take that under advisement.

---

### Post by trulan on 2010-10-14
> **marcoharder said:**
> Based on your expert opinions, guys, should I upgrade from 10.04 to 10.10? My gripe with 10.04 real time kernel is the fact that I couldn't use my Realtek USB wireless adapter [trulan is one of the guys who helped me here in the other thread].
 
I've been hearing great things so far about 10.10, but a few questions:
 
Will the Realtek card work? Really need wireless to work, as my room is too far from the router to make a cable connection to it.
 
Can the generic kernel really support recording now without many xruns?
 
Thanks in advance!
I was successful in getting the Realtek module to build on 2.6.33-realtime in Lucid, I posted in the other thread:
[http://ubuntuforums.org/showpost.php?p=9956297&postcount=151](http://ubuntuforums.org/showpost.php?p=9956297&postcount=151)

Also, I got 2.6.33-realtime booting here on Maverick again, it was indeed an issue with the NVidia drivers.  I just had to hand patch nvidia-current (again!  This is getting tiresome...)  Anyway it's running great now.  It's the same set of changes that was needed for this kernel in Lucid.  But since Maverick has nvidia-current-260 and Lucid used nvidia-current-256, it would be a bad idea to use the patched driver from FalkTX's ppa.  (guess I really need to start a ppa of my own for these things - maybe someday.)

---

### Post by Precipitous on 2010-10-15
> **trulan said:**
> I was successful in getting the Realtek module to build on 2.6.33-realtime in Lucid, I posted in the other thread:
[http://ubuntuforums.org/showpost.php?p=9956297&postcount=151](http://ubuntuforums.org/showpost.php?p=9956297&postcount=151)

Also, I got 2.6.33-realtime booting here on Maverick again, it was indeed an issue with the NVidia drivers.  I just had to hand patch nvidia-current (again!  This is getting tiresome...)  Anyway it's running great now.  It's the same set of changes that was needed for this kernel in Lucid.  But since Maverick has nvidia-current-260 and Lucid used nvidia-current-256, it would be a bad idea to use the patched driver from FalkTX's ppa.  (guess I really need to start a ppa of my own for these things - maybe someday.)
I am curious as to what you had to do to get the kernel to work. What do you mean by "hand patching" the driver? What Nvidia card/driver do you use? I have a GeForce 7300 LE and I can boot to the generic kernel, but not to the Low Latency or Realtime ones. With them I just get a command prompt. I am desperate for a fix...

---

### Post by trulan on 2010-10-15
I have an NVidia GeForce 6150 LE (onboard)
Hand-patching=manually editing and correcting some files (since I don't yet know how to write a patch that does this automatically).

Every time they release a new RT kernel patch, it seems to break the NVidia drivers.  To fix it, first install nvidia-current on the generic kernel and make sure that is working.  Then, the fun begins.  These commands can be run while booted on the generic kernel.

For the low-latency kernel, all you should need to do is build and install the dkms module:
```
sudo dkms build -m nvidia-current -v 260.19.06 -k 2.6.32.24.25
sudo dkms install -m nvidia-current -v 260.19.06 -k 2.6.32.24.25
```2.6.32.24.25 may not be the correct number for the lowlatency kernel, I don't have it installed, I just grabbed the kernel number from abogani's ppa.

For the real time kernel, it gets a bit harder:  (remember to save each file after editing.)
```
sudo gedit /usr/src/nvidia-current-260.19.06/nv-linux.h
```Go to line 245.  In it and the next few lines (through line 254), change every instance of 'atomic' to 'raw', so it looks like this:
```
typedef raw_spinlock_t         nv_spinlock_t;
#define NV_SPIN_LOCK_INIT(lock)   raw_spin_lock_init(lock)
#define NV_SPIN_LOCK_IRQ(lock)    raw_spin_lock_irq(lock)
#define NV_SPIN_UNLOCK_IRQ(lock)  raw_spin_unlock_irq(lock)
#define NV_SPIN_LOCK_IRQSAVE(lock,flags) raw_spin_lock_irqsave(lock,flags)
#define NV_SPIN_UNLOCK_IRQRESTORE(lock,flags) \
  raw_spin_unlock_irqrestore(lock,flags)
#define NV_SPIN_LOCK(lock)        raw_spin_lock(lock)
#define NV_SPIN_UNLOCK(lock)      raw_spin_unlock(lock)
#define NV_SPIN_UNLOCK_WAIT(lock) raw_spin_unlock_wait(lock)
#else
```Next, go to line 818 and change semaphore_init(mutex) to sema_init(mutex,1), like this:
```
#if defined(CONFIG_PREEMPT_RT)
#define NV_INIT_MUTEX(mutex) sema_init(mutex,1)
#else
```Next, patch the patches.  I'm not sure that this is necessary - I did this first, and didn't bother to change it back.  But since you've come this far, you might as well:
```
sudo gedit /usr/src/nvidia-current-260.19.06/patches/rt_preempt_31.patch
```Change semaphore_init(mutex) to sema_init(mutex,1), as above.
```
sudo gedit /usr/src/nvidia-current-260.19.06/patches/nvidia_rt_compat.patch
```Change every instance of 'atomic' to 'raw' in this file.

Then finally, build and install the dkms module:
```
sudo dkms build -m nvidia-current -v 260.19.06 -k 2.6.33-23-realtime
sudo dkms install -m nvidia-current -v 260.19.06 -k 2.6.33-23-realtime
```As long as the build completed successfully, everything should work when you reboot.

I really should learn to write this up in a proper patch (or better yet build it in my own ppa) but that's not something I've learned how to do as of yet.  For now, I resort to hand-patching things.

---

### Post by Precipitous on 2010-10-15
Trulan:

Thank you for your beautifully detailed instructions - they are exactly what I have been looking for...  I can't wait to get home from work and try them out!

---

### Post by sheehanje on 2010-10-15
I've had no luck with Studio lately on my desktop.  Either Lucid or Meerkat ...

It installs, then I get to a certain point and the system freezes and my monitor goes into powersave...

I haven't tried too much with it seeing 9.10 was working ok, and my laptop has 10.04 ...  I decided a couple nights ago to try installing 10.10 (not studio), then install all the studio specific stuff..  That's how I had to get 9.10 working ....

So, to make a long story short, I get everything installed, then I tried the low-latency kernel that someone else said worked well here (I do use firewire, but I'm figuring if low-latency will get me even ~5ms, I'll be happy) ...  Unfortunately, booting into that kernel gives me the same freeze ... 

I'm using an ATI graphics card btw...  Like I said, I haven't really bothered to really work this through yet, as I devoted weeks to stabilising my laptop set-up, but I now want to get the Desktop up and going as I will be splitting off my two systems...  I was daisy chaining an ART Tube Fire 8, and a Presonus FP10 with a few glitches on the laptop.  I know I can't do that with the new JuJu stack, but I what I really want is two separate systems connected via NetJack.  I can then put the drums in an isolated room with one of the computers/interfaces and just use a long Cat5e cross over to patch them into the main system...  This will also allow me to avoid the daisy chain problem...

Time to start some digging ...

---

### Post by Precipitous on 2010-10-16
Trulan:

I can never thank you enough for posting the detailed instructions for hand patching the Nvidia Current driver. You single handedly saved me from x-run hell, kept me from having to revert everything back to Lucid, and restored my faith in UbuntuStudio. You truly rock!

---

### Post by Peter7K on 2010-11-10
> **trulan said:**
> I have an NVidia GeForce 6150 LE (onboard)
Hand-patching=manually editing and correcting some files (since I don't yet know how to write a patch that does this automatically).

Every time they release a new RT kernel patch, it seems to break the NVidia drivers.  To fix it, first install nvidia-current on the generic kernel and make sure that is working.  Then, the fun begins.  These commands can be run while booted on the generic kernel.

For the low-latency kernel, all you should need to do is build and install the dkms module:
```
sudo dkms build -m nvidia-current -v 260.19.06 -k 2.6.32.24.25
sudo dkms install -m nvidia-current -v 260.19.06 -k 2.6.32.24.25
```2.6.32.24.25 may not be the correct number for the lowlatency kernel, I don't have it installed, I just grabbed the kernel number from abogani's ppa.

For the real time kernel, it gets a bit harder:  (remember to save each file after editing.)
```
sudo gedit /usr/src/nvidia-current-260.19.06/nv-linux.h
```Go to line 245.  In it and the next few lines (through line 254), change every instance of 'atomic' to 'raw', so it looks like this:
```
typedef raw_spinlock_t         nv_spinlock_t;
#define NV_SPIN_LOCK_INIT(lock)   raw_spin_lock_init(lock)
#define NV_SPIN_LOCK_IRQ(lock)    raw_spin_lock_irq(lock)
#define NV_SPIN_UNLOCK_IRQ(lock)  raw_spin_unlock_irq(lock)
#define NV_SPIN_LOCK_IRQSAVE(lock,flags) raw_spin_lock_irqsave(lock,flags)
#define NV_SPIN_UNLOCK_IRQRESTORE(lock,flags) \
  raw_spin_unlock_irqrestore(lock,flags)
#define NV_SPIN_LOCK(lock)        raw_spin_lock(lock)
#define NV_SPIN_UNLOCK(lock)      raw_spin_unlock(lock)
#define NV_SPIN_UNLOCK_WAIT(lock) raw_spin_unlock_wait(lock)
#else
```Next, go to line 818 and change semaphore_init(mutex) to sema_init(mutex,1), like this:
```
#if defined(CONFIG_PREEMPT_RT)
#define NV_INIT_MUTEX(mutex) sema_init(mutex,1)
#else
```Next, patch the patches.  I'm not sure that this is necessary - I did this first, and didn't bother to change it back.  But since you've come this far, you might as well:
```
sudo gedit /usr/src/nvidia-current-260.19.06/patches/rt_preempt_31.patch
```Change semaphore_init(mutex) to sema_init(mutex,1), as above.
```
sudo gedit /usr/src/nvidia-current-260.19.06/patches/nvidia_rt_compat.patch
```Change every instance of 'atomic' to 'raw' in this file.

Then finally, build and install the dkms module:
```
sudo dkms build -m nvidia-current -v 260.19.06 -k 2.6.33-23-realtime
sudo dkms install -m nvidia-current -v 260.19.06 -k 2.6.33-23-realtime
```As long as the build completed successfully, everything should work when you reboot.

I really should learn to write this up in a proper patch (or better yet build it in my own ppa) but that's not something I've learned how to do as of yet.  For now, I resort to hand-patching things.

Sorry for the noobishness, but how do I get the Natty Abogani kernel to patch using 10.10?  Thanks.

Is it from this post? [http://ubuntuforums.org/showthread.php?t=1602827](http://ubuntuforums.org/showthread.php?t=1602827)

I'm not really sure how to tell it what directory to use :(
```

$ sudo dkms build -m nvidia-current -v 260.19.06 -k 2.6.36-1 
Error! Your kernel headers for kernel 2.6.36-1 cannot be found at
/lib/modules/2.6.36-1/build or /lib/modules/2.6.36-1/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.36-1 package.
```

---

### Post by trulan on 2010-11-10
What is the version number of the kernel you are trying to use?

Also, post the output of:
```
ls /usr/src
```
so I know a little better what we're working with here.  I believe you just have some version numbers wrong.

---

### Post by Peter7K on 2010-11-10
linux-image-2.6.36-1-lowlatency
Linux kernel image for version 2.6.36 on x86/x86_64


bcmwl-5.60.48.36+bdcom           linux-headers-2.6.36-1
hdjmod-1.28                      linux-headers-2.6.36-1-lowlatency
hdjmod-1.28.dkms                 nvidia-current-260.19.06
linux-headers-2.6.35-19          nvidia-driver
linux-headers-2.6.35-19-generic  nvidia-driver.run
linux-headers-2.6.35-22          NVIDIA-Linux-x86-260.19.12.run
linux-headers-2.6.35-22-generic


the Hdjmod are packages for my Hercules controller to work in Mixxx.

Another thing of note is that while I have nvidia-current 260.19.06, I am in fact using the nvidia 260.19.12 driver, and I have it set to automatically update on kernel installation:
[http://www.omgubuntu.co.uk/2009/10/automatically-install-your-nvidia-driver-for-new-kernels-hands-free/](http://www.omgubuntu.co.uk/2009/10/automatically-install-your-nvidia-driver-for-new-kernels-hands-free/)

EDIT: Also.. I was just checking to make sure I had @audio - rtprio 99 and @audio - memlock unlimited, in 10.10... strangely my /etc/security/limits.d/audio.conf file does not exist even though according to [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) it should...  Funny because installing jackd should have created that file.  Though it's not as relevant it appears that even though the file now exists ```
JACK: unable to mlock() port buffers: Cannot allocate memory
09:54:20.758 ALSA connection change.
09:54:22.765 Server configuration saved to "/home/peter/.jackdrc".
09:54:22.767 Statistics reset.
09:54:22.770 Client activated.
09:54:22.771 JACK connection change.
09:54:22.772 JACK connection graph change.
cannot lock down memory for RT thread (Cannot allocate memory)
```

---

### Post by Pablo_F on 2010-11-10
> ...jackd should have created that file.

Not exactly, afaik. The jackd postinst script should have invited you to gain the rtprio and memlock privileges by writing the relevant lines to /etc/secutiry/limits.d/audio.conf, but you could have declined the invitation and therefore this file was not created.

You can invoke the script at any moment with the command:

sudo dpkg-reconfigure -p high jackd

Cheers! Pablo

---

### Post by Peter7K on 2010-11-10
> **Pablo_F said:**
> Not exactly, afaik. The jackd postinst script should have invited you to gain the rtprio and memlock privileges by writing the relevant lines to /etc/secutiry/limits.d/audio.conf, but you could have declined the invitation and therefore this file was not created.

You can invoke the script at any moment with the command:

sudo dpkg-reconfigure -p high jackd

Cheers! Pablo

I've actually tried that :)

It asks for my password and that's all, no query for configuring audio, etc.. very strange.

And I *do* remember it asking me that when I installed, and I did accept.. very strange.

---

### Post by Pablo_F on 2010-11-10
Hi, 

I just tested this in maverick. I was wrong indeed. You need either:
```

sudo dpkg-reconfigure -p high jackd1
```

if you have jackd1 installed (not default) or:

```
sudo dpkg-reconfigure -p high jackd2
```

if you have jackd2 (the default jackd in maverick)

Cheers! Pablo

---

### Post by trulan on 2010-11-10
> **Peter7K said:**
> Another thing of note is that while I have nvidia-current 260.19.06, I am in fact using the nvidia 260.19.12 driver, and I have it set to automatically update on kernel installation:
[http://www.omgubuntu.co.uk/2009/10/automatically-install-your-nvidia-driver-for-new-kernels-hands-free/](http://www.omgubuntu.co.uk/2009/10/automatically-install-your-nvidia-driver-for-new-kernels-hands-free/)
Ah, okay.  So you're using the driver from NVidia, not the Ubuntu package.  I've done that before too but it's been a while...You don't want to use dkms to build the module then.  You need to extract the source files, do your edits, then build and install the module manually.  (every time you run the .sh file from nvidia it will overwrite any edits you do).  I'll dig into my notes from a while back and see if I can figure out how that is done...

Also, it doesn't look like you have any headers installed for 2.6.33-rt - you'll need those to get the nvidia driver to build on the realtime kernel.

---

### Post by Peter7K on 2010-11-11
> **Pablo_F said:**
> Hi, 

I just tested this in maverick. I was wrong indeed. You need either:
```

sudo dpkg-reconfigure -p high jackd1
```

if you have jackd1 installed (not default) or:

```
sudo dpkg-reconfigure -p high jackd2
```

if you have jackd2 (the default jackd in maverick)

Cheers! Pablo

Worked beautifully, thanks Pablo!

And Trulan:
I was going to just use the lowlatency kernel and not the realtime, was halfway through installing the realtime stuff to test that out at the time of posting ;)
I appreciate you taking the time to show me how to build the kernel with that NVIDIA driver, thanks!

---

