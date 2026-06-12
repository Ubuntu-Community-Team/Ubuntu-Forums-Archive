---
title: "[SOLVED] Virtualbox, full-screen video"
date: 2008-12-01
forum: Virtualisation
---

### Post by rossmoore on 2008-12-01
Hi,

I have Hardy installed on my laptop - 2.4GHz Core Duo, with 2Gb RAM. Hardy runs great.

For reasons beyond my control I have some DRM-protected Windows Media Player files I'd like to play. I have vista installed as dual boot, and using this I can play the files.

It's a hassle to reboot every time I want to watch them though. So I installed Virtualbox, and then Vista inside VirtualBox. I'm really impressed generally. I can watch videos in WMP - so long as I don't go full screen. If I go full-screen (that's using the full-screen button in WMP) then the video goes all jumpy.

In VirtualBox I have 1Gb memory put aside for Vista, and 128Mb for video memory. I have enabled the VT-x thing too.

Any ideas for getting video full-screen in Vista, running in VirtualBox on Hardy?

Thanks,
Ross

---

### Post by DGortze380 on 2008-12-01
> **rossmoore said:**
> Hi,

I have Hardy installed on my laptop - 2.4GHz Core Duo, with 2Gb RAM. Hardy runs great.

For reasons beyond my control I have some DRM-protected Windows Media Player files I'd like to play. I have vista installed as dual boot, and using this I can play the files.

It's a hassle to reboot every time I want to watch them though. So I installed Virtualbox, and then Vista inside VirtualBox. I'm really impressed generally. I can watch videos in WMP - so long as I don't go full screen. If I go full-screen (that's using the full-screen button in WMP) then the video goes all jumpy.

In VirtualBox I have 1Gb memory put aside for Vista, and 128Mb for video memory. I have enabled the VT-x thing too.

Any ideas for getting video full-screen in Vista, running in VirtualBox on Hardy?

Thanks,
Ross

Have you installed virtual box guest additions? They tend to help a lot with video issue. (Note: I've only run Ubuntu Guests, not hosts)

---

### Post by xikarrousx on 2008-12-01
generally, vista uses a crap load of memory just to run... so surprisingly enough, you need either more physical (real) memory for your PC or you need to allocate more for vista in VB. give XP a shot in VB, you might have better results...

also, keep in mind you are running TWO operating systems at one time. this is pretty demanding on your computer, especially since vista is so dependent on memory. 

one other thing to try is to disable visual effects in BOTH ubuntu and vista while you are watching videos... actually, that might help a lot!

---

### Post by rossmoore on 2008-12-01
@Dgortze380 - I have installed Guest additions. There were a few different versions on the ISO now that you remind though, so I'll check there's nothing else I can install.

@xikarrousx - You think I'll need more than 1Gb for Vista? I could extend to 1.25 or even 1.5 perhaps, since linux only uses a couple hundred MB. I have tried turning off Compiz and Aero, both to no effect. CPU Usage (as reported in Hardy, the host), while neither operating system is doing anything, is consistently high with one CPU always on 100%. I know they're having to run two operating systems, but while nothing's happening I would hope usage would be lower than that.

---

### Post by DGortze380 on 2008-12-01
> **rossmoore said:**
> 
@xikarrousx - You think I'll need more than 1Gb for Vista? I could extend to 1.25 or even 1.5 perhaps, since linux only uses a couple hundred MB. 

Minimum for Vista is 1GB. I did that for all of a week before a ponied up for 4GB's. I refuse to recommend less than 2GB's for vista regardless of machine specs.

---

### Post by rossmoore on 2008-12-01
Hmm. I run 32-bit Hardy (and Vista), so I'm limited to 3Gb. Is it going to be worth me buying a 2Gb stick to replace one of the two 1Gb sticks in my laptop?

Does anyone have video running fullscreen in Vista as guest on Ubuntu host in VitualBox? Is this something I'm going to achieve (and only achieve) by spending more money?

---

### Post by rossmoore on 2008-12-02
Oh, and I don't have an XP install disk, so I can't use XP in VirtualBox (which I would love to do).

So has anyone got video playback fullscreen in Vista on Virtualbox? I can get it non-fullscreen, but it struggles when it goes fullscreen. It would be great to know so that I can know whether it's worth me getting an extra 1Gb of memory.

---

### Post by xikarrousx on 2008-12-02
im lookin around to see if there is an easy answer to this... did you end up clicking "install guest additions"? If not, try that. 

Memory = yes... it can't hurt getting some. simply put, my vista machine (not in VB) run 1.72 GB of physical ram just to idle. if you want to run vista flawlessly, i think you need a ******** more memory. otherwise, buy xp :)

as for any other related issues with VB and vista and full screen, I was unable to find answers. i think memory is the main issue and maybe its way too much to handle for your cpu.

good luck

---

### Post by rossmoore on 2008-12-02
Thanks. I did a thorough google before coming here. Yeah, maybe I'll try the extra Gb of memory, or maybe I'll try and pick up an XP CD from somewhere. Thanks for the help.

---

### Post by bodhi.zazen on 2008-12-02
You might also try increasing the video memory of the guest.

---

### Post by DGortze380 on 2008-12-02
> **rossmoore said:**
> Thanks. I did a thorough google before coming here. Yeah, maybe I'll try the extra Gb of memory, or maybe I'll try and pick up an XP CD from somewhere. Thanks for the help.

If your computer is newer, you probably have dual channel memory. It's best to install dual channel in matching pairs to avoid boot errors and memory dumps. If you're going to upgrade, I would suggested getting 4GBs (2x2GBs). I know you're only 32-bit, but it tends to work better in a dual channel setup. 

Option 2 - Buy XP instead. I run an XP virtual machine with 1GB and 1GB for OS X, it's faster than the 3GHz 4GB RAM Dual Core in the lab when running Visual Basic '05.

---

### Post by rossmoore on 2008-12-02
Thanks. I had heard that about dual channel memory, but wasn't sure how important it was. More expensive unfortunately. Or I could get hold of a copy of XP... I'll have a look around, see which one is likely to be cheaper. Thanks for all your advice.

Has anyone actually got video working fullscreen like this?

Someone suggested putting video memory up - as in my first post, video memory is already at the max (128Mb).

---

### Post by HotShotDJ on 2008-12-03
> **rossmoore said:**
> Has anyone actually got video working fullscreen like this?I, too, have VirtualBox (official SUN version) with Vista Home Premium installed as a guest OS and Intrepid as the host OS.  I've given the VM 1024 RAM plus 128 VRAM. (My actual hardware is 2048 RAM with Intel Integrated Video).  I tested some of the mpeg1 files I have and playback was jerky, even without going to full screen.

Vista is such a pig.  The only reason I have it is because it was forced on me by Dell.  They REFUSED to give me XP (this was before XP was "retired" by MS and before Ubuntu laptops and P.C.'s were offered).  But they DID give me a $160 (US) refund when I called and complained...  Kind of funny... no refunds if you replace Windows with Linux, but $160 if you ask to replace Vista with XP.

I don't know if throwing more RAM at it will help... part of the problem MAY (or may not) be the virtual video card that VirtualBox uses.  My mom's computer has Win2K running in VirtualBox with Hardy as the host OS.  Next time I visit her, I'll see how video playback is on her machine.

---

### Post by rossmoore on 2008-12-03
Thanks HotShotDJ. I'm in a similar position - I have Vista 'cos that what Dell shipped. I still have dual-boot, but haven't used it since I installed Hardy - except for this DRM media I have. I am a bit worried it's just the virtual video card that means this will never work.

I'd like to confirm it is possible before I shell out about US$60 (?) on either a copy of XP or 4Gb of RAM. Thanks for offering to check it out on you mom's computer, do let me know how it goes.

Does anyone else have a version a little closer to hand they can test it out on, or any other relevant experience?

---

### Post by rossmoore on 2008-12-22
Thanks to everyone who's posted to this forum trying to help out - things seem to be working OK now.

I didn't buy the extra RAM. I did upgrade the version of VirtualBox (just released last week), I enabled the new openGL acceleration. I still had problems with the sample videos that are bundled with WMP11, but I was able to watch AVIs and WMVs downloaded from the internet in full screen without major issues (although full-screen controls weren't all that reliable).

So I'm marking this as solved. I can't give a definitive answer on what solved it, but things seem to be working well enough now after quite a few tweaks.

---

