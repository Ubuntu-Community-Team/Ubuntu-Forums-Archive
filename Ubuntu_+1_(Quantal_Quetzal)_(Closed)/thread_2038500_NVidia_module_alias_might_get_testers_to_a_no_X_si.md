---
title: "NVidia module alias might get testers to a no X situation"
date: 2012-08-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-06
For some reason I can't remember I turned off my desktop yesterday and, as I started it today, I had no X. It stops at plymouth disconnect before lightdm now. 

I have no alternate PPAs (no xorg-edgers, etc) and I apt-get update && apt-get upgrade everyday a couple times. This machine was using NVidia 304.32, installed with the NVidia binary installer.

I went to /var/log/Xorg.0.log and found something I was not expecting (as I had not upgraded VGA drivers before turning off the machine):

> (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Failing initialization of X screen 0
(II) UnloadModule: "nvidia"

Then it gets weirder. See what I had in /var/log/kern.log:
> NVRM: API mismatch: the client has the version 304.32, but this kernel module has the version 302.17.  Please make sure that this kernel module and all NVIDIA driver components have the same version.

I thought hey, 302.17? Am I going mad or something? I *know* I installed 304.32. And before that I had 304.22. Why 302.17? 

I went to check basic stuff. And it just gets weirder:
lsmod | grep -i nvidia shows me a nvidia module loaded. Great, it's probably this mismatched 302.17 version that got in somehow. So I modinfo nvidia and it tells me it's 304.32 at /lib/modules/3.5.0-7-generic/kernel/drivers/video/nvidia.ko!! 

I decided to just re-run NVidia installer, let it do all installation steps, build/load the 304.32 module. And, once again, I get the exact same errors as described above. And modinfo still tells me I got 304.32, not 302.17.

What? I thought I was still sleepy or something. So I went:

```
sudo dkms remove nvidia/304.32 --all (OK)
sudo dkms remove nvidia/304.32 --all (again just to check - not found, good)
sudo ./NVIDIA-Linux-x86_64-304.32.run -K
sudo modprobe -r nvidia
sudo lsmod | grep -i nv (no results, good)
modinfo nvidia (outputs 304.32)
sudo modprobe nvidia (OK)
sudo service lightdm start
```
SAME RESULTS!!

I won't paste it here cause it is impossible. I manually nano'd and used "strings" on nvidia.ko to check the version. It was definitely 304.32. I was on console obviously, I had no hexedit app for console. Fun stuff. 

It took me a while to figure it out:
```
cat /etc/modprobe.d/nvidia-graphics-drivers.conf | grep alias nvidia
alias nvidia nvidia_current

```

:)

Meh. I could have dropped the alias, but I was in berserk mode already.
```
cd /lib/modules/3.5.0-7-generic/updates/dkms/
ls
nvidia.ko
cd nvidia
ls
nvidia_current.ko

```

Silly right? 
```

sudo mv nvidia_current.ko nvidia_current.ko.old
sudo ln -s /lib/modules/3.5.0-7-generic/kernel/drivers/video/nvidia.ko nvidia_current.ko
sudo reboot now
```

Success lol... I kept the alias, so I kept nvidia_current.ko as a link.

So, once again I was fooled by the module alias stuff. I thought I should share this. It's absolutely counterintuitive and you can get into this easily by testing nvidia_current package, simply dist-upgrading or testing xorg-edgers, back to nvidia binary installer, that is, switching between different providers for nvidia stuff. Note to self: *Always* check for module aliases...

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-06
One other thing: This version clearly switches between Performance Levels much faster and smarter than any version I have used previously... To be honest I think I had never seen my VGA at 70ºC and using Perf. Level 0.

[ATTACH]222349[/ATTACH][ATTACH]222350[/ATTACH][ATTACH]222351[/ATTACH]
[ATTACH]222352[/ATTACH][ATTACH]222353[/ATTACH]

Regards,
Effenberg

EDIT: On normal usage, running Chrome with about 20 tabs, thunderbird, Eclipse, some Marlin windows, speedcrunch, Nitro, Rhythmbox, and rdesktop to a Windows 7 VM, my GPU is at level 0 with exactly 50ºC now :) The GPU cooler (the default one that comes with the board) is stalled at 30% Oh, the silence...

---

### Post by Harry33 on 2012-08-07
I have to say the situation of xserver is quite odd in QQ ATM.
It is not a bit better with nvidia-current.

Xserver:
We have xserver 1.12 branch in official main repos (1.12.1.902-1ubuntu1). Here we have video ABI 12.
Then we have xserver 1.13 branch in official proposed repos (1.12.99.902-0ubuntu1). Here it is video ABI 13.
So, enabling proposed repo, you get xserver 1.13.

Nvidia-current:
We have nvidia-current (and nvidia-current-updates) v. 304.32 in official restricet repos. This is for video ABI 12.
Then we just had (before it was deleted today) nvidia-current v.304.32 for video ABI 13 in proposed repos. However, this does not work with 3D desktops.

For the time being it is not a good practice to enable proposed repos.

---

### Post by effenberg0x0 on 2012-08-07
I never really understood how proposed would be managed, or what would be the advantages of having it with no clearly communicated / documented goals, usage, strategy, advantage. I have not been following up with any of this in this cycle. It's the opposite of I had insisted in previous cycles and last UDS (of having a testers-only repo, synced to others repos only once every 24hs (thus delayed 1 day from "bleeding edge") so all testers could always be in sync for at least some hours, making testing together, discussing, comparing, solving problems, developing workarounds, reporting more meaningful. 

During a normal day packages are upload at any time. People might upgrade or not, many times or few, etc. Therefore all reports are either valid and invalid simultaneously (Schroedinger's bug reports?) if testers do not get an opportunity to share the exact same packages, the exact same versions of them, for a small amount of time. Storage is cheap, so there's no real cost in this.

Developing infrastructure and collaboratively created (and documented) processes for testing would empower testers to do what they do best. It should be #1 priority. I frankly don't see how testing will ever evolve to be more effective in any other way. It's 2012. We're not hiding in our basements at late hours, building blackboxes and being tapped by the authorities anymore. Testing should be transparent and move from a loner thing to a community/group activity. We are not moving from the standard loner activity of creating questionable and non-reproducible reports to a group-supported activity.

Each of the guys that decide to invest a part of their time, of their life, to test Ubuntu for free is a valuable asset, much more valuable than any automated stuff, something that the proprietary software industry will never have. Providing basic infrastructure and documented processes, among other cheap things, to empower the work of this contributors could be a game changer for Ubuntu. We have 72 testers today on U+1 team. I don't know how much a software tester makes in US, but here I'd have to pay about USD120K/Year for each of them at least. Multiply that for 72. It's USD8.640.000/Year. I can't see why having about USD9 Million/Year saved in testing, done by passionate people, doesn't motivate some cheap investment in proper infrastructure to empower these people. 

But anyway, that's just my rant :) Lot's of things are indeed changing in comparison to previous cycles and I might be completely wrong. I guess we will only know by RR.

Regards,
Effenberg

---

### Post by jbicha on 2012-08-07
effenberg0, the plan is for all uploads to go through proposed. However, that can't happen until some behind-the-scenes improvements are made. Currently, stuff that's more disruptive or has a probability of "breaking" Quantal for developers or bleeding edge users (such as the next xserver or the unity stack or things that just take a long time to build and will likely otherwise result in archive skew--where amd64 and i386 don't finish building at the same time--examples include GTK, webkit, and LibreOffice) is uploaded to -proposed and then they are manually copied over to quantal when the archive admins think the packages are ready.

As -proposed likely includes broken stuff, it's not recommended to have -proposed enabled on development releases.

I don't believe there are any plans to only let updates go through once a day and it's not clear that doing so would make things any better. You're welcome to start a discussion about that on the mailing lists and see if you can convince the Ubuntu developers that your proposal is better than what currently happens.

---

### Post by effenberg0x0 on 2012-08-07
> **jbicha said:**
> effenberg0, the plan is for all uploads to go through proposed. However, that can't happen until some behind-the-scenes improvements are made. Currently, stuff that's more disruptive or has a probability of "breaking" Quantal for developers or bleeding edge users (such as the next xserver or the unity stack or things that just take a long time to build and will likely otherwise result in archive skew--where amd64 and i386 don't finish building at the same time--examples include GTK, webkit, and LibreOffice) is uploaded to -proposed and then they are manually copied over to quantal when the archive admins think the packages are ready.

As -proposed likely includes broken stuff, it's not recommended to have -proposed enabled on development releases.

I don't believe there are any plans to only let updates go through once a day and it's not clear that doing so would make things any better. You're welcome to start a discussion about that on the mailing lists and see if you can convince the Ubuntu developers that your proposal is better than what currently happens.

Thanks jbicha :) I already proposed this repo (I call it T-1) on the latest UDS QA Blueprints. I strongly believe that having such a repo would improve the changes of us having better/more structured and organized human testing processes (and consequently a greater chance of reproducible and valid bug reports). I tend to look only at the testers POV. I don't think it would be interesting or do any good to developers. I don't think I can sell this idea.

It's exactly the same as when I tried to insist on us having an open, public, easy to use, hardware database for testers, even if took an entire year or more to php it. IMO it would be amazing if I could access a website, click on your handle, click on mine and select "compare hw". We would be able to explore bug reports better, reproduce them with more confidence knowing the hw of the original reporter, easily detect what is hw related and what's not, etc. But as much as that idea sounds wonderful to me, I don't think it would be interesting to anyone but testers lol

Regards,
Effenberg

---

