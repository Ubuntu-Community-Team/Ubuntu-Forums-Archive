---
title: "Virtualbox doesn't even work"
date: 2009-05-25
forum: Virtualisation
---

### Post by RealG187 on 2009-05-25
Is it just me or does virtualbox not work? A while ago I made [this thread]("http://kubuntuforums.net/forums/index.php?topic=3090962.0") back when I was using Vista trying to run Ubuntu in a VM, now I am running Ubuntu as my main OS trying to get Windows to work and when I start Windows setup it frezzes on "Setup is now starting Windows 2000"

It makes no sense, VMWare works but Virtualbox just doesn't do it...

---

### Post by Perkins on 2009-05-26
I think it's just you...  I use virtualBox all the time with a variety of different operating systems.  The only time I've gotten the results you describe was when I was playing around and trying to install a VM inside of a VM...

I would guess the most likely culprits would be either lack of resources on your host machine, or incorrect settings concerning virtualization extensions.  Or, possibly, something disrupting the guest's ability to read from the virtual CD drive.  Were I you I would probably start by seeing if I could run/install something else.

---

### Post by RealG187 on 2009-05-26
Okay so I was trying this
[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool)

I tried to install Windows 2000 over the VDI I converted from VMWare. I made a new VDI using Virtualbox and it is now installed sucessfully.

I am trying to install Windows 98, I installed it once but it was laggy. I am trying again.

---

### Post by RealG187 on 2009-05-26
Okay I do the install and after the second reboot (I think) it VM crashes and under the staus it says "aborted" instead of powered on or powered off. I can start it again and it just keeps doing the same thing. Why is it doing this?

---

### Post by Perkins on 2009-05-26
Windows 95 and other DOS-based operating systems might well be laggy, especially on a single-core machine.  They never halt the processor, so they will try to consume an entire CPU.

I'm not sure why it would be crashing on you.  You might try launching it from a console with whatever debug output options you can find enabled.  I believe the command for manipulating machines from the console is vboxmanage, but I don't have my installation in front of me, so I can't double-check that.

---

### Post by RealG187 on 2009-05-26
But if I am running it in a VM it shouldn't try to consume the whole CPU, just the virtual portion.

---

### Post by Perkins on 2009-05-28
VirtualBox hands an entire CPU to the virtual machine.  On Windows NT and later, when the OS is idle, it halts the processor and waits for an interrupt, thereby freeing the unused computing power for use by the host.  More primitive operating systems simply devote all the processor power they have left over to running their main loop.  So when you run them in a VM they will always eat however much CPU time you hand them.  If you only have one core, then it may lag your system a bit.  You could *try* renicing the VB process, though I'm not sure what effect that might have on the guest.

---

### Post by RealG187 on 2009-05-28
So does virtual box handle the CPU differently than VMWare? I am running Windows 98 and it is really slow. Is there a way I can fix this?

---

### Post by bodhi.zazen on 2009-05-29
> **RealG187 said:**
> So does virtual box handle the CPU differently than VMWare? I am running Windows 98 and it is really slow. Is there a way I can fix this?

Sorry to break the news to you, but Windows 98 is no longer supported by Microsoft and Virutualbox never supported windows 98.

IMO qemu and VMWare are your best options.

---

### Post by Perkins on 2009-05-29
VirtualBox handles Windows 98 just fine so long as you don't need the guest additions.  So it depends on what you're trying to do with it.

VirtualBox gives less control over the disposition of your CPU than other virtualization solutions.  The guest gets one CPU, and only one CPU, and you can't tell it that it's a less powerful CPU than the one you have.  Your only control over it is to adjust the priority of the VirtualBox process.

If it's running slowly, then I should ask if the machine you're running it on has support for the virtualization extensions, and if it's multi-cored.  Lack of either one of those will decrease performance, and performance bottlenecks will be especially noticeable with Windows98, DOS, and other simple operating systems.

Were I you, unless I *needed* 98 for something specific, I would probably use 2000 or XP.

---

### Post by RealG187 on 2009-05-29
I am running a new CPU.

Microsoft is stupid, 98 is an awesome OS. It runs really fast compared to anything else.

The only drawbacks are no NTFS or native USB driver, but since I am using in in a VM, Ubuntu handles the USB drivers and file systems.

Windows 98 is in the list under Virtualbox so it looks like it's supported.

> VirtualBox gives less control over the disposition of your CPU than other virtualization solutions.
Seems wierd, you would think VMWare would since it's propriotery and Virtualbox is openn source.

I have XP VMs but XP is slow (well not as slow as this VM with the problems) and 2000 can't run DVD Decrypter for some reason, it keeps saying the installer is corrupt when it is not, and though faster than XP it still can't beat 98)

---

### Post by rliegh on 2009-05-29
You might want to check out the windows 98 entry at the bottom of the page here: 
[http://www.virtualbox.de/wiki/User_FAQ](http://www.virtualbox.de/wiki/User_FAQ)

And see if the utility they recommend fixes your problem or not.

---

### Post by Perkins on 2009-05-30
Microsoft pretty well had to ditch 98.  It was based on DOS, which was based on a pirated copy of CP/M.  They'd been wanting to get that albatross off from around their neck for a while.

I believe I read a thread on the VirtualBox forum at one point saying they were working on improving control of virtual processors.  I have no idea how well that's coming along though.

Oh, and instead of DVDdecrypter under virtual windows, why not use the libdvdcss libraries under linux.  It tends to run faster.

---

### Post by RealG187 on 2009-06-01
What's CP/M?

2000 and XP still have DOS, just not in the same way...

---

### Post by Perkins on 2009-06-02
[http://en.wikipedia.org/wiki/CP/M](http://en.wikipedia.org/wiki/CP/M)

The "DOS" in later versions is actually just an emulated DOS shell on top of their new kernel.  Which is why it has been mostly neutered and lots of the old commands and programs no longer work right.  (Not that most people will ever notice.)

---

### Post by RealG187 on 2009-06-02
Sorry but I don't use Wikipedia anymore...

---

### Post by Perkins on 2009-06-03
Well, then punch CP/M into Google yourself.  Wikipedia was just what was at the top and had a good explanation.

---

### Post by RealG187 on 2009-06-03
Wikipedia always comes up first result on Google, I hate that. I use search wiki to remove it.

---

### Post by Perkins on 2009-06-03
Anyway, there's no reason I know of that Windows 2000 shouldn't run under VirtualBox.  The only time I've seen it freeze on install like that was when it didn't have enough resources to run.  What kind of hardware are you trying to use?

---

### Post by mister_playboy on 2009-06-05
I had the same problem installing 2000 where it would stop running after 5 second into the install... when I turned IO APIC off, it solved the problem.

Give that a try.

---

### Post by RealG187 on 2009-06-05
I had a problem with 2000 but that was when I tried to reuse a VDI image, when I made a new one it worked.

I still have a problem with 98 being extremly slow, where it is really fast in VMWare and I cannot mount USB devices into my VMs!

---

### Post by Perkins on 2009-06-09
To mount USB devices in your VMs get the full version from their website.  It is free for personal use.

---

### Post by RealG187 on 2009-06-09
> **Perkins said:**
> To mount USB devices in your VMs get the full version from their website.  It is free for personal use.I did but can still only do it in VMWare...

---

### Post by bodhi.zazen on 2009-06-09
> **RealG187 said:**
> I did but can still only do it in VMWare...

But you are also using Windows 98 ? VMWare is older then VBox and I would imagine support for windows 98 / 2000 will be spotty in VBox. My impression has been that there is little interest in building backwards compatibility with those OS in VBox.

If you were to try Windows XP or Vista you might have a different experience.

Virtualization is a bit complicated and it depends on the Kernel, not version of Ubuntu. Kernel development is faster then virtualization development on every version of Linux and if you are doing virtualization you may wish to either use Ubuntu 8.04 as a host or have a dedicated box.

Same is true of Fedora, Centos, etc.

If you want a current kernel IMO you are going to be best off with KVM or virtualbox.

I know you want a current kernel on the host and and old guest, but that is asking a lot.

If you run a supported host and supported guest you will have much less in the way of problems.

---

### Post by Perkins on 2009-06-10
I haven't had much call to use the USB passthrough in VirtualBox.  But it doesn't just pass through anything that you plug in automatically.  In the VMM GUI there is a section where you can define rules about which USB devices it should send to the guest.

Windows 98 and DOS work for me without any lagginess.  But they do eat an entire core.  So, if you're running it on a single-core machine it might well be stepping on itself.

---

### Post by RealG187 on 2009-06-10
I do not get a good experience with XP (haven't tried vista). 98 runs really fast in VMWare.

---

