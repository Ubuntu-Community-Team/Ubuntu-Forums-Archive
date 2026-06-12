---
title: "USB suffers from high CPU load"
date: 2021-07-25
forum: Virtualisation
---

### Post by cryptearth on 2021-07-25
So, I got my KVM host up and running as well as my Windows 10 KVM with GPU passthrough. All works the way I planed.
But, for some reason, I experience that USB suffers from high CPU loads. From a YT-video I know that USB pretty much works on a polling paket structure - and although I don't have an oscilloscope handy to verfiy it I guess that's the issue.
I already tried to lower the virtual cpu core count. I also set core pinning so the host has some cores for itself. I even switched from simple usb device redirector to also fully passthrough the usb root hub. Unfortunately it hasn't helped yet. It's even hard to write this post as I currently use high load to verify it. I first noticed audio stuttering as I use an external usb audio interface as my main audio in/out - but also other usb devices, mostly mouse, keyboard and other input devices like gamepad, shows this.

In addition to that: On my host loading it up with high overall system load, like downloading a game from steam which requires network bandwidth, hard disk performance and rather high cpu power as its highly compressed and encrypted data stream which is decrypted and decompressed before written to the disk - I can watch YT while steam is doing its thing in the background. In the KVM running steam inside it makes the kvm pretty much unuseable: usb stutters and drop outs, yt video stuttering (no, not buffering as in not enough bandwidth but stuttering as in a scratched dvd) and the host becomes really slow.

So, although all is working fine when it's idle - as I load up the kvm it makes the whole system behave like it's something retro back from the 90s.

Running the exact same task on the host no matter the host os all is fine - no usb stutters, no YT lagg - just steam downloading the game and don'T bother me.

Has anybody else experienced such weird behaviour? Is there maybe anything I can do about it? I'd like to use the kvm as if I would run win10 natively - the only reason I use a kvm in the first place is to have ubuntu as a ZFS host as I not yet got either ZoL in WSL(v2) running nor do I have the required network for setting up a NAS.

---

### Post by MAFoElffen on 2021-07-25
#1 - I assume you are using a Windows Guest in KVM... That you are using the Windows version of Steam and trying to run a specific Game from Steam...

What version and release of Ubuntu is your Host's OS? What are the spec's of you host? Most important the CPU, how many cores, and how much memory... What is the Video of your host?

How do you have you host set-up and what viewer are you using? What are your problems with that setup?

Why are you not trying to run that same game natively in the Linux version of Steam? Where there would not be any virtual translation of anything or any shared resources? Just asking...

Edit: I apologized... Didn't you post all that in another thread here? (Your spec's?) I don't remember... But I remember you were also doing a video pass-through, weren't you?

---

### Post by cryptearth on 2021-07-25
It's faster for me to just type down the specs instead of use some fancy command - so, here you go:

Board: ASUSU Crosshair V Formula-Z - UEFI v.2201 from Mai 7th 2015
CPU: AMD FX-8350 (8 core (or more specific: 4 CCXs with 2 ALUs each), 4.0GHz)
RAM: 4x 8GB Corsair Vengance 1600MHz 10-10-10-27
passed through GPU: ASUS AMD R9 290X DC2 4GB
host GPU: ZOTAC nVidia GT1030
usb devices: standard usb keyboard and mouse, Roland TRI-Capture USB audio interface
about versions of kernel, qemu, libvirt and all that stuff: whatever the default repos currently has to offer - basically installing a fresh clean system from the 21.04-live-server-amd64.iso followed by apt update and apt upgrade

I tried both just device passthrough as well as full pci passthrough of the usb hub. Played around with number of vcpu cores, core pinning, amount of assigned RAM. Pretty much every tweak I could think about each on its own and incombination.

I googled around and found several threads across multiple platforms over the years - from arch over unraid to debian and ubuntu. It seems to be a re-occuring issue. A bit like the egg-chicken problem: Some hardware works - the host gets some updates - everything breaks - a bug report is filed - and after the next few patches all is back to work as before again ... and about a few months and versions later another user experience about the same issue with just a bit different hardware.

Steam is just an example as I know it's an application that can load the system rather good as it does quite a few things the same time - but I was able to re-produce this issue with pretty much everything that loads the CPU - even with few lines of java code running about twice the number of assigned vcpu cores. At least the core pinning seems to help host background stuff like ZFS - but the issue also happens when I only load the vcpu so the two cores I reserved for the host are pretty much idle while the other cores assigned to the KVM are fully loaded.

What I can think of: As USB is packet based like ethernet there seems a massive packet loss as the physical hardware is either no longer able to poll the devices at the usual rate (which I can't check due the lack of an oscilloscope) - or what ever comes back from the devices doesn't make it through to the KVM. I'm not sure about what's the real issue here.

As it all works clean on the host itself I don't think it's an issue with the kernel or the hardware - but rather with the KVM layer. Not sure if it's libvirt, qemu or the vfio drivers. But as it all just works together I don't have a way to test the individual parts of it.

The main issues, why I'm with this topic for about the past two years:

I once made the mistake to use the fakeraid provided by the AMD 950 soutbridge - and after a couple of drive failures I'm looking for a solution. Windows Storage Spaces might be a solution - but it has a weird layout for dual-parity which makes 7 drives the optimal amount. As far as I understand it it uses only 4 drives for data, 2 drives for parity and the 7th drive for something like some overall stuff ... but due to this it's not the solution for me. ZFS-raidz2 fits my needs way better - but it's only available on linux - the last release for windows was back in mid-2020 and only works on whole drives instead of partitions.
BUT: Although there're many games work on linux natively - and many with Valves Proton (it's a modified WINE) - but due to DRM and anti-cheat crap there'Re some games either only work in single player - or some even not at all.
I also did some tests maybe setting up a NAS - but for some odd reason there'Re some applications (not just games but also other stuff) have problems with mapped network shares. Aside from that I would need to upgrade to 10GBit network - otherwise I'm limited to GBit network - or about 120mb/s net bandwidth - which is about half what a single drive is able to get me with about 200mb/s local attached via S-ATA3.

So, the only option I came up with is use a linux host to provide the ZFS volume and provide it to a windows kvm.

Other options, like upgrading my hardware or network, is currently out of reach as I'm at minimum wage and have to pay of debts - so I just have the money for it but have to use what I have.


But ... anyway ... as you think that no one would read my posts anyway but just ignore it ... feel free. I solved other issues over the years - some stuff just became possible due to evolved kernel and drivers - using the 20.04-LTS I have the issues I had about a year ago. So ... maybe I just have to wait another year for all the stuff to evolve some more and maybe still support my then about 10 years old hardware ... or, maybe it's true what I thought about the first time I tried: My hardware just isn't able to provide what I want to as it's just some pro-sumer level hardware from 2012.

Maybe it all works with modern 10th gen intel or ryzen 5000 series with modern chipsets ... but I can'T effort them - let alone the current over-inflated market prices.

---

### Post by MAFoElffen on 2021-07-27
I hear you on the money and costs... I certainly can't afford any of that of the moment. I have been struggling and do not make what I used to. Most my stuff has been in storage, and I try to make do by being downsized.I keep hearing that Ryzen is great with some things, but is not that supported yet by others.

Sorry that I haven't got back to this sooner. Have been testing VirGL virtio_gpu with another member.

Going through what you said. You said a whole lot. And yes, you have done a whole lot. Trying to seperate it all out. 

While I am doing that, just a quick question... What are you using for your VM Viewer? The display renderer?

---

### Post by MAFoElffen on 2021-07-27
I'm curious on the other things you tried... At least for me... 

If I do Bridged or NAT translation, then I don't have to anything special. Same with just allocating more vcpu's or memory... I can just throw more at it if needed... and the networking in virtio just works for me.

Yes, disk writes are a bit slower on virtio vs. Native. If I do Bridged networking thru BR0 and apply access to my host's NFS share's it does seem to be a bit faster. I do that for testing oVirt. It also helps if I say the vcpu is same as the native host.

Some of these issues are exactly why I gave up on pass-through's and went Native with a Multi-Boot methodology.. Just saying that I wasn't completely satisfied with it for true Gaming response. That's just me... That might not be popular here. But that is just real-world and honest. It doesn't take anymore hardware. You don't lose anything to do it. Somethings I did just needed Windows to do (like you). It's just another technique. Again, just what I learned from doing that. But even with that, I still try to look for other ways to do that. That is why I'm trying to explore virtual_gpu's and VirGL... It won't probably worked out until LTS 22.04 next April, but it's getting there. Well, close to... Depending on the GPU. That doesn't mean I am any less dedicated to try to help you explore that...

---

