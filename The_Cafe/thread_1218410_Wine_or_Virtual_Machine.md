---
title: "Wine or Virtual Machine?"
date: 2009-07-20
forum: The Cafe
---

### Post by irv on 2009-07-20
I've tried Wine in the past and have it installed on my laptop, but I have had issues trying to get some of the apps I need to run under Wine, so I went to using virtualbox 3.0 and everything just installs runs like it should. I guess this raised a question in my mind. Why would anyone want to run Wine?
I thought this little poll would give others a change to cast there vote for Wine or a virtual machine. This would include VMware, Virtualbox or any other virtual machine over Wine.
What's your input on this?

[ATTACH]121802[/ATTACH]

[ATTACH]121803[/ATTACH]

---

### Post by SuperSonic4 on 2009-07-20
Because wine does run some things well and it's lighter on resources.

Ideally of course there'd be a linux alterative

---

### Post by Mornedhel on 2009-07-20
A VM takes space (as much as is needed for a guest OS to run). Wine requires basically just enough space for the applications themselves ; Wine itself is much lighter than an OS (obviously).

Installing a VM requires a copy of the guest OS. Not so for Wine.

A VM uses a lot of resources (CPU and RAM both). Not so for Wine (well, not much more than the application being run).

There is no way I can run a recent 3D game in a VM. With a little luck, Wine won't have trouble running it.

---

### Post by irv on 2009-07-20
> **SuperSonic4 said:**
> Because wine does run some things well and it's lighter on resources.

Ideally of course there'd be a linux alterative

Yes, I agree with you on the ideal way, but I don't think that will ever happen.

---

### Post by FuturePilot on 2009-07-20
Some thoughts that come to my mind:

[LIST]
[*]Not everyone may have a copy of Windows to run in a VM
[*]Some may not want the overhead of running a VM
[*]Applications ran in Wine integrate better with the host than a VM does
[*]Computer isn't powerful enough to run a VM
[/LIST]

On the other side

[LIST]
[*]Wine can be hit or miss with applications
[*]Most applications are guaranteed to work perfectly in a VM
[*]Isolation from the host machine
[*]Snapshots can make things really easy if anything happens to break
[/LIST]

---

### Post by Mornedhel on 2009-07-20
> **FuturePilot said:**
> [LIST]
[*]Snapshots can make things really easy if anything happens to break
[/LIST]

This is a pro for VMs but not a con for Wine : it's really hard to break a system because some application running under Wine is behaving rudely.

---

### Post by Tibuda on 2009-07-20
Why have you installed Firefox and Adobe Reader in your VM?

---

### Post by irv on 2009-07-20
> **danielrmt said:**
> Why have you installed Firefox and Adobe Reader in your VM?

I have a Netflix account and I watch flicks and when I use IE I had memory problems, and Firefox didn't have this problem. Netflix is not supporting Linux OS so I need to run in a windows OS.
I found after trying this in XP under virtualbox, the movie ran to slow and the sound was not good either. I thought about trying it under Wine, but it might have the same problem. I can't remember why I installed Adobe Reader?

---

### Post by mamamia88 on 2009-07-20
well wine is cheaper duh.  also, you have to wait for windows to boot and if you don't have much ram your system will slow too a creep. i have 2gb ram and if i wanted to run vista the most ram i would dedicate without slowing my system would be 512mb vista would suck on 512mb

---

### Post by SunnyRabbiera on 2009-07-20
Wine for the most part works for me, its not perfect but meh it does its job the best way it can.

---

### Post by irv on 2009-07-20
> **mamamia88 said:**
> well wine is cheaper duh.  also, you have to wait for windows to boot and if you don't have much ram your system will slow too a creep. i have 2gb ram and if i wanted to run vista the most ram i would dedicate without slowing my system would be 512mb vista would suck on 512mb
virtualbox 3.0 is the same price, $0, so I don't know how you can say wine is cheaper? I do agree with you on the RAM issue. Memory is so cheap now, I upgraded my laptop to 4Gig from 2. This lets me have the best of both worlds. I have a dual boot with Vista, and Vista sucks big time. That's why I am running XP SP3 in Virtualbox.

---

### Post by mamamia88 on 2009-07-20
> **irv said:**
> virtualbox 3.0 is the same price, $0, so I don't know how you can say wine is cheaper? I do agree with you on the RAM issue. Memory is so cheap now, I upgraded my laptop to 4Gig from 2. This lets me have the best of both worlds. I have a dual boot with Vista, and Vista sucks big time. That's why I am running XP SP3 in Virtualbox.

yes but add a copy of windows too virtualbox and it's not so cheap and i checked crucial and it looks like my laptop doesn't support 4gb ram so i'm stuck with 2

---

### Post by irv on 2009-07-20
> **mamamia88 said:**
> yes but add a copy of windows too virtualbox and it's not so cheap
Your right again, but this was a CD I bought and was not using so why not put it to uses seeing it was already paid for. I left Vista on the laptop because I bought it pre-installed. Again I am not going to throw it away because I paid for it also.

---

### Post by forrestcupp on 2009-07-20
Wine can run Half-Life 2.  Windows in a VM cannot.  VM's are really pretty limited by the cruddy virtual hardware that they have to emulate.

---

### Post by jomiolto on 2009-07-20
Missing option: neither :P

*If* I did run Windows software, I'd have to go with Wine, since my processor does not support virtualization.

---

### Post by swoll1980 on 2009-07-20
Will Wine ever have usb support?

---

### Post by clonne4crw on 2009-07-20
I use both. I prefer WINE because it isn't nearly as resource-intensive, and it does a much better job with 3D rendering. It's only downside is that it doesn't always work.

I also use VMWare, for what doesn't work in WINE. While it is sometimes slower, it works more effectivley. The only downsides are that (for windows) you need a liscence (sometimes O:) ) and it is a RAM hog.

---

### Post by TheNosh on 2009-07-20
> **swoll1980 said:**
> Will Wine ever have usb support?

what do you mean? i'm pretty sure i've used a usb controller with project 64 before (i could be remembering that wrong though)

---

### Post by Matthewthegreat on 2009-07-20
Wine is free a windows VM is not.

Wine can run 3d games a VM can't run most of them.

Wine doesn't take as much HDD space as a VM.

Wine runs apps at native speed a VM doesn't.

Wine doesn't hog your RAM and CPU like a VM does.

Wine doesn't support Microsoft buying windows for your VM does.

Wine doesn't need to boot up a VM does.


If at all possible I run my windows apps in wine instead of a VM for the above reasons.

---

### Post by irv on 2009-07-21
> **Matthewthegreat said:**
> Wine is free a windows VM is not.

Wine can run 3d games a VM can't run most of them.

Wine doesn't take as much HDD space as a VM.

Wine runs apps at native speed a VM doesn't.

Wine doesn't hog your RAM and CPU like a VM does.

Wine doesn't support Microsoft buying windows for your VM does.

Wine doesn't need to boot up a VM does.


If at all possible I run my windows apps in wine instead of a VM for the above reasons.

Nice post! Have you ever try virtualbox 3.0 yet? I tried VMware back awhile ago, and didn't like it, but I like virtualbox and all my stuff works. I am not a gamer so I have not tried games in virtualbox. The only think, my Netflix run too slow in it.

---

### Post by forrestcupp on 2009-07-21
> **jomiolto said:**
> 
*If* I did run Windows software, I'd have to go with Wine, since my processor does not support virtualization.

You only need hardware virtualization support for Microsoft's VM's, and maybe a few other commercial ones.  You don't need it for vmware or virtualbox.  Mine doesn't support virtualization, either, but I ran vmware just fine.

---

### Post by sirjoebob on 2009-07-21
I think they answer different questions. Wine is great for adding a non-native app to a Linux machine. vbox or equivalent is good for sanboxing, testing, or using OS-specific applications such as netflix. 

Both are well-done implementations that offer us end-users a wide variety of options. However, virtualization requires MUCH more system resources than running individual apps in wine. Wine is also more capable than vbox for Linux-host gaming for games that do run.

---

### Post by jomiolto on 2009-07-21
> **forrestcupp said:**
> You only need hardware virtualization support for Microsoft's VM's, and maybe a few other commercial ones.  You don't need it for vmware or virtualbox.  Mine doesn't support virtualization, either, but I ran vmware just fine.

Hmm, I was under the impression that virtualization was awfully slow without virtualization extension in the processor, but I guess I was wrong.

---

### Post by sirjoebob on 2009-07-21
> **jomiolto said:**
> Hmm, I was under the impression that virtualization was awfully slow without virtualization extension in the processor, but I guess I was wrong.

From my understanding, you don't with virtualbox, etc. it is implemented with a kernel module.

---

### Post by andru183 on 2009-07-21
vm, i use it for bigger scale programs and it dose a better job

---

### Post by forrestcupp on 2009-07-21
> **jomiolto said:**
> Hmm, I was under the impression that virtualization was awfully slow without virtualization extension in the processor, but I guess I was wrong.

I've heard that hardware virtualization doesn't really even make that much of a difference.

Virtualization is awfully slow no matter how you do it.  One tip is that if you use vmware, do a search for how to use the vmware tools.  It gives you much better virtual hardware, and speeds things up significantly.  It's possible to install vmware tools even in the free player that doesn't come with the tools.

---

### Post by irv on 2009-07-21
Before I installed Virtualbox 3.0 and WinXP I had 53.5Gig of hard drive space available on my Ubuntu partition. I now have 48.3Gig. This also included all my apps I installed in WinXP.
[ATTACH]121872[/ATTACH]
When I am running Virtualbox and WinXP I am using 192 MB of RAM, and 12 MB of Video RAM. I also set aside 10Gib of Hard drive space. This is less then I would have used if I was running it native on my system.
I am not a gamer so I don't find any reason to run Wine. I have it installed because I wanted to try it, but I do fine Virtualbox better for my needs. I checked the size of my .virtualbox directory in my home to be 5.2Gib is size. 
I took a couple of screen shot of my system not running virtualbox and XP and while running it.
[ATTACH]121870[/ATTACH]

[ATTACH]121871[/ATTACH]
I have plenty of resources to run both, but I only run virtualbox and XP when I need to. I don't keep it running all the time because I only need it once in awhile.

---

### Post by 3rdalbum on 2009-07-21
> **forrestcupp said:**
> I've heard that hardware virtualization doesn't really even make that much of a difference.

Virtualization is awfully slow no matter how you do it.

Don't confuse virtualisation with emulation. A virtualiser alters some of the direct CPU instructions and memory accesses before sending them to your real hardware, and then modify the response when it comes back; an emulator will actually emulate the entire CPU and entire system in software.

With CPUs that support virtualisation extensions, they can receive the raw instructions and memory addresses and, in hardware, do the modifications necessary.

Of course, virtualisation only works when your guest OS is compiled for the same CPU architecture as your host hardware; emulation can work regardless. Emulation is slow, virtualisation is comparatively fast.

---

### Post by stwschool on 2009-07-21
I find that Wine accomplishes most tasks very very well, and on the rare occasions it doesn't I fire up VirtualBox. Simple really.

---

### Post by forrestcupp on 2009-07-21
> **3rdalbum said:**
> Don't confuse virtualisation with emulation.I guess terms change when hardware changes.  Before there were any CPU's that had those extensions, things like vmware and virtual box *were* called virtualization.  That's why 'vm' stands for virtual machine and virtualbox is called 'virtual'box.  And they have never required those extensions.

So now that we have new hardware, maybe they need to change their names to emware and emulationbox.

> **3rdalbum said:**
> Emulation is slow, virtualisation is comparatively fast.
Is that your experience?  Even though I have a Core2Duo, my particular proc doesn't support hardware accelerated virtualization.  So I don't have any experience with it.  But I've heard it doesn't make a noticeable difference.

Hopefully if your experience is different, what I've heard is wrong.

---

### Post by raymondh on 2009-07-21
VMWare and Virtualbox for me.

---

### Post by sirjoebob on 2009-07-21
I find virtualbox to be a great solution. Also, I would recommend installing the guest additions as it gives you nice options like pointer integration and "seemless mode"

---

### Post by irv on 2009-07-21
I see it 50/50, 18 to 18 at this point.

---

### Post by Matthewthegreat on 2009-07-21
> **irv said:**
> Nice post! Have you ever try virtualbox 3.0 yet? I tried VMware back awhile ago, and didn't like it, but I like virtualbox and all my stuff works. I am not a gamer so I have not tried games in virtualbox. The only think, my Netflix run too slow in it.

Yep, I have virtualbox with a xp machine. I have it so I can run Sony Vegas because I haven't found a good linux alternative.  If I can run a app in wine, I do because I prefer wine.  Mostly I have found linux alternative for all my apps except my games. So, I use wine mainly for games which most of them will not work in a VM.

---

