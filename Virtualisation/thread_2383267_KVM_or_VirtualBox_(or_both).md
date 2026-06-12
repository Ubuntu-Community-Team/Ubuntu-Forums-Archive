---
title: "KVM or VirtualBox (or both)?"
date: 2018-01-22
forum: Virtualisation
---

### Post by DuckHook on 2018-01-22
This thread is a continuation of: [https://ubuntuforums.org/showthread.php?t=2382751](https://ubuntuforums.org/showthread.php?t=2382751)

At the risk of diverting the discussion from the OPs original topic, for my part, I will say this:

I will be the first to admit that my knowledge is that of the educated layman and not that of a virtualization, hardware or kernel expert. However, in my case, the experience is personal.

On occasion, I run a number of old games in Windows XP and Vista. Specifically, Homeworld and Homeworld 2. Even back in the XP days, these were known to tax the bare metal HW of the time quite heavily. I did not have much hope that they would run well in a virtualized environment and, sure enough, they were unplayable in VBox. Now, I have been using VBox for years and like to think that I know my way around it well enough. Yet, no matter how I tweaked it, HW2 in particular, was unplayable. A few months ago, I decided to slowly make the change to KVM. With no better hope that it would work, I tried the game in KVM. Not only did it run, it was quite playable. A far cry from my experience using VBox.

Other apps and OSes behave likewise. With practically identical settings in both, Kubuntu runs slower in VBox than KVM. It boots up slower, has more mouse jutter, and is noticeably more sluggish. Firing up an app like LibreCAD on top of Kubuntu makes this even more noticeable. LibreCAD slows the system down even more in VBox. The experience in KVM is much snappier.

Nor is this restricted to just one machine. My old laptops (Core2 Duo 2GB RAM) struggle to host a Windows Vista session in VBox. They do not struggle in KVM. I could go on.

It is not my intent to be argumentative. I like VBox, especially its ease of use. But these are real experiences. Anecdotal perhaps, but we hear the same story on these forums with enough regularity that I have high confidence that I am not some outlier.

---

### Post by lammert-nijhof on 2018-01-22
@Duckhook: The graphics anecdote is nice, but it does not prove very much. The questions are many: What video card and which propriety/linux driver? I assume 3D and 2D have been enabled in Vbox. What release of Vbox? Did KVM use pass through? It clearly shows there is a difference in video processing between the two hypervisors. If KVM decides to use pass-through, if dealing with a VM in full screen mode, it would explain the difference. I would really like to understand what causes that difference. Since from time to time I consider to try KVM.

Just my anecdote. I run a lot of 720p YouTube Video in Chromium, I use a propriety Nvidea driver and the difference between bare metal and the Vbox is around:
- real HW: CPU 30%, GPU 40%
- 17.10 VM: CPU 38%, GPU 30%

In KVM, you can specify current and max memory, that allows a more dynamic allocation of memory to the VM by the Host. In Vbox GUI you can only specify max memory and on top of that a large chunk of memory is used by the Host OS. 

My conclusion is that KVM can run better in machines with an amount of memory close to the VM size. I expect it will be better with graphics, if run in full screen mode. If you share the screen between 2 or more VMs, it will be comparable to Vbox, since in my example the difference between bare metal and Vbox-VM is not huge.

---

### Post by vasa1 on 2018-01-23
Is there an idiot's guide to KVM?

I'm using VBox currently to look at Kubuntu Bionic on a modest laptop (i3 dual core CPU with one core and ~4GB RAM given to the guest) and the experience is not intolerable. The only thing I don't have working is drag-n-drop; all the other Guest Addition aspects that I need are fine. But if KVM is more efficient, I would like to try it.

---

### Post by DuckHook on 2018-01-23
> **lammert-nijhof said:**
> @Duckhook: The graphics anecdote is nice, but it does not prove very much.
I beg to differ. On the contrary, it is the only sort of proof that really matters, since it speaks to what a user will actually experience and is not just theory.
> The questions are many: What video card and which propriety/linux driver?
```
lspci -vk | grep -iA10 vga
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbe00000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at e000 [size=256]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon, amdgpu
```
I cannot run any driver other than the open source Radeon on this card.
> I assume 3D and 2D have been enabled in Vbox.
Yes
> What release of Vbox?
At the time, 5.0. Now 5.2. Same relative difference in performance.
> Did KVM use pass through?
No. However spice/QXL is installed and being used.
> I would really like to understand what causes that difference.
Me too!  :)
> Since from time to time I consider to try KVM.
This is the crux of the matter. You are arguing that VirtualBox is equivalent in performance to KVM without actually having run the two side by side. Your arguments are theoretical, whereas mine are experiential and real.
> Just my anecdote. I run a lot of 720p YouTube Video in Chromium, I use a propriety Nvidea driver and the difference between bare metal and the Vbox is around:
- real HW: CPU 30%, GPU 40%
- 17.10 VM: CPU 38%, GPU 30%
But this does not tell me anything at all. You can cite all the numbers you want. It does not substitute for what I've actually seen and felt.
> In KVM, you can specify current and max memory, that allows a more dynamic allocation of memory to the VM by the Host. In Vbox GUI you can only specify max memory and on top of that a large chunk of memory is used by the Host OS. 
Translation: KVM runs faster and is more efficient.
> My conclusion is that KVM can run better in machines with an amount of memory close to the VM size.
:confused:[LIST=1]
[*]How can you possibly "conclude" any such thing without a side-by-side real-world test???
[*]More importantly, if true, this translates again as: for many machines, KVM is faster and more efficient!
[/LIST]
> I expect it will be better with graphics, if run in full screen mode. If you share the screen between 2 or more VMs, it will be comparable to Vbox, since in my example the difference between bare metal and Vbox-VM is not huge.
I hope you will agree that neither your nor my expectations can have any bearing on reality. Reality is what it is. It doesn't (and shouldn't) care what our expectations are. I have provided my experiences. I am open to explanations about why my KVM machines outperform my VBox ones. I am open to any and all suggestions that might improve my VBox machines to equal or surpass KVM performance. But I cannot pretend that my experiences are other than what they are.

I want to make one thing very clear. As the Texans say, I have no dog in this fight. I like both technologies almost equally but for different reasons. VBox in particular was my only VM for years and introduced me to the power and security of sandboxing. I have very fond feelings for it and still run it for a bunch of non-Linux VMs. I also tend to recommend it to newbies because it is far friendlier than KVM. So I am not trying to promote one over the other. However, I am committed to a truthful and real-world-based understanding of the strengths and weakness of both. So far, what I've found is that KVM is superior in performance whereas VBox is superior in user friendliness and ease of use.

I do hope that you eventually get the chance to see them at work side by side. I would be very interested to hear back from you whether your experiences differ from or mirror mine. It would be useful to compare notes.

---

### Post by QIII on 2018-01-23
I don't know if these are as in-depth as you might be looking for, but:

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
[https://help.ubuntu.com/lts/serverguide/virtualization.html](https://help.ubuntu.com/lts/serverguide/virtualization.html)
[https://www.linux.com/learn/intro-to-linux/2017/5/creating-virtual-machines-kvm-part-1](https://www.linux.com/learn/intro-to-linux/2017/5/creating-virtual-machines-kvm-part-1)

are a good start.

My experience is that KVM is far and away better than something like VBox.  Perhaps it is because I have used it for some time, but I think it is somewhat easier to use once you get used to the quirks.  

There's an article on Phoronix (a bit old, 2015) with some objective comparisons.  KVM and Xen outperform VirtualBox except for in a few odd cases, which I can't see any good reason for.

[https://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-virt&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-virt&num=1)

---

### Post by vasa1 on 2018-01-23
Thank, QIII! I'll slowly go through the links.

---

### Post by DuckHook on 2018-01-23
> **vasa1 said:**
> Thank, QIII! I'll slowly go through the links.
@vasa1

Those were exactly the links I used when first delving into KVM about a year ago. I definitely did not find them "idiot" grade. In fact, I found them rather dense. This is entirely due to me being rather dense, but that's just too bad for me.

I will say that, once I figured out the very different world of KVM, it was relatively smooth sailing thereafter. However, getting to that point was not easy for me, though QIII would find just about anything a Sunday picnic.

---

### Post by QIII on 2018-01-23
Nah.

I've spent 30 years trying to figure out Mrs. QIII and I still haven't a clue.

:)

---

### Post by DuckHook on 2018-01-23
> **QIII said:**
> Nah.

I've spent 30 years trying to figure out Mrs. QIII and I still haven't a clue.

:)
…so I'm not alone…

It's good to know I'm in good company.

---

### Post by cruzer001 on 2018-01-23
I have only played with kvm, virtualbox has been my choice.

For a glitch free (guest) experience I find I need:
For testing:  2core/3G ram
For everyday use and gaming:  4core/4G ram

To me those are modest requirements that gives me good performance, but I do wonder (as happen to DuckHook) if gaming could be improved using kvm.

That will probably never happen, but...
I do not consider my laptop good enough to run a VM; maybe kvm is the solution.  I would be a happy camper if I had a VM on my lappy :)

```
kvm-ok
```

---

### Post by KillerKelvUK on 2018-01-23
> KVM or VirtualBox (or both)?

Is "both" feasible now?  I recall trying to get KVM and VB on the same host was a challenge, not done this recently though and a quick google suggests it might be dependent upon which order you start your guests.  Would be interested for any recent experience tips?

@lammert-nijhof, hi I'm picking up your post for the original thread for these quotes...

> So there is no architectural reasons for a difference in performance. 

The clearest reason for this at its core is architectural.  A type 2 hypervisor is in-fact just another application running on the host OS that is subject to the hosts memory, disk, video and security management processes, anything it wants to do must be requested from the host os and thus can be denied, overridden, delayed etc.  Whereas a type 1 hypervisor in effect is the host os and so isn't subject to the same chain of authority and process requests.

> But with the current prices of video cards I would prefer to share that one expensive card between the VMs.

In full agreement hear the hardware has sky rocketed however your desire to share the GFX resources is an interesting point.  Traditional GFX passthrough doesn't deliver this sharing capability but developments with vfio do allow you to share the hosts video hardware acceleration with multiple guest I believe ([https://github.com/qemu/qemu/blob/master/docs/igd-assign.txt](https://github.com/qemu/qemu/blob/master/docs/igd-assign.txt)).  As such I think your comments about development effort and code quality are on point, big names with big budgets support the develop of kvm and vfio.

> The mentioned performance comparison was not very relevant, because it concentrated on large servers with many CPUs (10 cores and 20 threads).

I don't see your logic here sorry, are you suggesting that the underlying results might _materially_ change if you consistently reduce the number of processing cores made available to the guest? 

> Virtualbox is better for running server production databases and Vbox/KVM and XEN are more or less equal in a home environment for e.g audio and video processing. Which completely proves my point!

My read of that linked article was that the testers were suspicious of VB's disk performance characteristics suggesting that VB might not be waiting for write confirmations which it should.  And whilst I agree the margins for video and audio tests were narrow VB still came last...so I don't see how this "...completely proves my point"?

---

### Post by DuckHook on 2018-01-23
> **KillerKelvUK said:**
> Is "both" feasible now?  I recall trying to get KVM and VB on the same host was a challenge, not done this recently though and a quick google suggests it might be dependent upon which order you start your guests.  Would be interested for any recent experience tips?
They won't run concurrently. You must choose one or the other, but not both at the same time. Perhaps you can run them concurrently if you turn off VT-x/AMD-V in both hypervisors, but they would run even more piggish than they already do, and who wants that? What I meant was having both installed. I run VBox for stuff like Minix, Android, etc, primarily because it's not important to squeeze the nth amount of performance out of those VMs, and KVM for everything else.
> A type 2 hypervisor is in-fact just another application running on the host OS that is subject to the hosts memory, disk, video and security management processes, anything it wants to do must be requested from the host os and thus can be denied, overridden, delayed etc.  Whereas a type 1 hypervisor in effect is the host os and so isn't subject to the same chain of authority and process requests.
To be fair, the line between Type 1 and Type 2 have been blurring over the years. VBox is the only Type 2 I am familiar with, but they have been leveraging more Type 1 features with every release, though still not as tightly bound as KVM or XEN. With the steady retirement of old CPUs I think VBox has just felt more comfortable relying on VT-x/AMD-V, which directs a lot of execution straight to the CPU without intervening translation.

In the final analysis, theoretical considerations are just theoretical considerations. It's real-world results that count. I would love to have my VBox VMs run as fast as my KVM ones. VBox is just friendlier to use.

---

### Post by KillerKelvUK on 2018-01-23
Okay well I'm interested enough to try a comparison myself and see what I can learn and share so will throw VB on over the next couple of days to test out some scenarios.

---

### Post by QIII on 2018-01-23
So long as the number of cores and threads was constant across testing of all three hypervisors, the relative performance comparison is valid when scaled.

As to production servers in VBox:  No.  I think you would find very few Admins who do or recommend that.  Rather the opposite.  VBox is great for home/small scale non-production use.

One can use both VBox and KVM on the same machine -- provided only one or the other is running at a time.

---

### Post by lammert-nijhof on 2018-01-23
@DuckHook. 
> [COLOR=#000000]I beg to differ. On the contrary, it is the only sort of proof that really matters, since it speaks to what a user will actually experience and is not just theory.[/COLOR][COLOR=#000000] It speaks to what you do experience with YOUR machine with YOUR settings. As I showed you, I have completely different experience with my machine. For instance I load VISTA in one minute on my Host giving Vista 2GB of memory. That is at least twice as fast as loading on the original laptop; an Inspiron 1521 from 2008 with an [/COLOR]2-core [COLOR=#000000]Athlon at 1.8GHz.[/COLOR]
> [COLOR=#000000]This is the crux of the matter. You are arguing that VirtualBox is equivalent in performance to KVM without actually having run the two side by side. Your arguments are theoretical, whereas mine are experiential and real.[/COLOR] I know it is old fashioned, but sometimes it helps, if you read the manual and that is also true for KVM. Sometimes it beats just trying something :) Besides for practical arguments, see my 1 minute VISTA loading and the next paragraphs: 
> [COLOR=#000000]You can cite all the numbers you want. It does not substitute for what I've actually seen and felt.[/COLOR] You must be joking, my numbers don't count, but your feelings about your comparison do.
> [COLOR=#000000]Translation: KVM runs faster and is more efficient.[/COLOR]
[LIST=1]
[*]How can you possibly "conclude" any such thing without a side-by-side real-world test???
[*]More importantly, if true, this translates again as: for many machines, KVM is faster and more efficient!
[/LIST]
No I stated precisely what I meant, KVM will run better on machines where VM memory requirements and real memory are getting close. That is my conclusion from your report on using your 2GB laptops with Vista in Vbox and KVM. You described that comparison for me. Vista will not run very well, if you also need the memory for the Vbox host OS from that same 2GB. Vista runs good on my 8GB Host, when I reserve 2GB for the Vista VM (better then on my real Inspiron 1521 hardware). That Phoronix article showed that KVM was faster in compilation, while Vbox was faster serving a database and both were more or less equal (within 10%) in many other tasks, like e.g media format processing.
> [COLOR=#000000]I hope you will agree that neither your nor my expectations can have any bearing on reality. Reality is what it is. It doesn't (and shouldn't) care what our expectations are. I have provided my experiences. I am open to explanations about why my KVM machines outperform my VBox ones. I am open to any and all suggestions that might improve my VBox machines to equal or surpass KVM performance. But I cannot pretend that my experiences are other than what they are.[/COLOR]
You talk about your reality and that is completely different from my reality or that of Ryzen 7/GTX1070 owners. That is, why I have to understand, why you get a certain result in a test. I think about changing to KVM, but I want to be convinced for myself that it brings a significant advantage. The work will take days or maybe a week to get all VMs on both desktop and laptop to the same level again,. 
The only advantage of KVM, I see up-to-now, is the more dynamic allocation of memory, which I do not really need, since in my hosts I can run 2-3 VM at the same time and that is sufficient for me.

You experience with Kubuntu/KDE is only partly understandable to me. Probably the Vbox 3D functionality is not very efficient with the standard Linux driver. I noticed a considerable improvement in the Vbox 3D functionallity going from Linux nouveau driver to Nvidea driver. And as additional advantage I now monitor GPU load and VRAM usage with Conky. 

Again I have no good reason yet to start working on the switch, Going from KVM to Vbox I 'require' CPU load improvement, while displaying 1080p60 YouTube videos in Chromium or Firefox in an Ubuntu 17.10 VM. The current figures with Chromium in Ubuntu 17.10 are:

[LIST]
[*]real HW both CPU and GPU close to 50%
[*]Vbox VM CPU close to 70% and GPU is between 25-35%
[/LIST]
If KVM would bring the figures of CPU down close to 60% and the GPU e.g. between 35-45%, I would start trying KVM on my laptop.

---

### Post by DuckHook on 2018-01-23
There really is nothing more to discuss here. I am comparing two apples. You keep trying to compare an apple to your theorizations, and insisting that this constitutes a real comparison.

Until you have actually run the two VM technologies side-by-side, I'm afraid that your assertions will simply remain assertions and we will just be talking past each other.

Good Luck and Happy Ubuntu-ing!

---

### Post by lammert-nijhof on 2018-01-24
[COLOR=#000000][INDENT]
I had to theorize my whole life, we would get requirements from our customers and we had to find a working solution and we had to theorize, how to solve it, what to develop, how much it would cost and we had to estimate e.g. CPU loads. Sorry that I still "theorize". 

So I try to understand your comparison and why you get the results you described. I translate that to my situation, like I did in the past. Your real comparison has no real value for anybody else, then people with the same HW. For example Vista runs lousy in a small Vbox-VM on your 2GB laptop and it runs good in your KVM VM and my 2GB Vbox-VM. Of course! Vista needs all the memory it can get. To be honest Vista did run lousy on my 2GB Inspiron 1521, that is why I definitively switched to Ubuntu. I have no big problems with my VMs including Vista, why would I change? Why should I say KVM is better then Vbox, based on what recent, representative measurements for a typical home situation? 

I like one improvement and that is to bring down the VM-CPU occupation somewhat. My current comparison with Chromium in Ubuntu 17.10 displaying 1080p60 YouTube videos are: [/INDENT]
[/COLOR][COLOR=#000000][INDENT]
[LIST]
[*]real HW both CPU and GPU loads close to 50%
[*]Vbox VM CPU close to 70% and GPU is between 25-35%
[/LIST]
That are measurements and a comparison between real HW and a VM. [/INDENT]
[/COLOR][COLOR=#000000][INDENT]
The CPU ratio of that VM vs Real-HW is 140%, seems OK, but if KVM could bring that figure down to 120%, I would start promoting and trying KVM on my laptop. If somebody has arguments, why KVM could achieve that goal based on [/INDENT]

[LIST]
[*=1]somewhat technical architectural arguments;
[*=1]any comparison between real-HW vs a KVM VM on CPU loads with e.g HD YouTube videos
[/LIST]
[INDENT]It would make me very happy and it could be used for extra or interpolation to my brick.
[/INDENT]
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by Irihapeti on 2018-01-24
This thread has run its course and is going round in circles.

Closed.

---

