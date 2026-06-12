---
title: "About MXLinux"
date: 2021-11-30
forum: The Cafe
---

### Post by satimis on 2021-11-30
Hi all,

Has any folk tried MX Linux ?

MX Linux
[https://mxlinux.org/](https://mxlinux.org/)

On searching;
Vapoursynth is available for MXLinux as a Flatpak

I need to test Vapoursynth, a video editing software

Thanks

Regards

---

### Post by TheFu on 2021-12-01
My LUG has a few users and over the last few months we've installed it and played around.  It is lite and doesn't use systemd.  One of the guys only runs linux from a USB3 flash drive with persistent storage. He's been doing that for years.  I don't know whether any other OS is on his machine.  He's a few timezones away, but joins the LUG meeting almost every week.

Flatpaks run on Ubuntu.  They aren't tied to any specific Linux OS. Install the flatpack service and install whatever flatpaks you like on Ubuntu ... it is an alternative to snaps with more local control possible. The local admin has control, as it should be.

I've been looking to rework my video editing the last few weeks to finally get away from MS-Windows.  Comskip is the start of the process to remove commercials (mostly TV recordings).  

I'll take a quick look at Vapoursynth. Thanks for mentioning it.  Ah ... seems to be intended as a scripting language library to feed options into tools that compress videos. Not my need. I'm not sure how to call a library/tool from outside a flatpak constrained container to fit into workflows.  

Perhaps if you say the type of video editing you do, someone might be able to make suggestions?  
Mine is pretty simple. I just want to take recorded broadcast shows, remove any commercials accurately and transcode to a more efficient codec. That is typically, 
.ts ( mpeg2 TS; 1 hour long) --> text cut file --> mpeg2 (40-44 min) --> h.264 (or HEVC) final output.
Typically, that will convert a 4-5GB file to about 1.2G after commercials and transcoding.  My players handle h.264 in hardware, but anything else is software (including mpeg2), so the resolution matters.

BTW, comskip will output avisynth skip files.  The skip files are easy. The problem is that areas to skip in a video have start-stop locations  that are 100% the opposite for what cut marks would be.  Basically, they mark were the commercials are when I need where the commercials are not. The data is there, just shifted 1 time entry off.

Most video editors drop extra audio tracks and subtitles/captions.  mkvmerge "does the right thing" always, so I want to cut using the text cut file with mkvmerge. Wrote an updated script this morning, mkvchapt-2-mkvmcut, to take comskip generated mkv-chapter XML and create an mkvmerge command based on a few assumptions. It needs more testing, but it is very close to ready. The flaw in this process is that comskip can visually show cut points for the native comskip "txt" format, but not for the other output options like mkv-chapter, videoredo, edl, edlx, or the other 5+ formats supported.  My script doesn't work with input files that have spaces in the name. Quoting the inputfile didn't help. ;(

mpeg 480p is easy and plays on anything used currently.
mpeg 720p will stutter on some players.
mpeg 1080i always stutters on players.
h.264 at 1080p or less resolution plays perfect on all the devices.

I don't have any 4K content. That's a $200 network ATSC v3.0 tuner, which I don't have. Only about 5 stations here broadcast 4k content.

---

### Post by dirtydog01 on 2021-12-01
I tried MX Linux, thought it was ok. Not using it now.

---

### Post by satimis on 2021-12-01
> **TheFu said:**
>  - snip -
I've been looking to rework my video editing the last few weeks to finally get away from MS-Windows.  Comskip is the start of the process to remove commercials (mostly TV recordings). 

- snip - 
In the last 1~2 months I have been working hard to rework my old video captured with Sony V8 Video Camera in about 1990.  Most the suggested solutions found by me work on MS Windows.  I found difficulties even in installing the softwares suggested on Win10.  I'm running 3 Win10 VMs here for the testing but without any progress therefore I start the idea coming back to Linux

Following YouTube shows what I need

How to Sharpen Blurry Video in Premiere Pro
[https://www.youtube.com/watch?v=_MPUJhcY-As](https://www.youtube.com/watch?v=_MPUJhcY-As)

But it is on Adobe Premiere Pro

Now I'm testing Kdenline running on Ubuntu 20.04 and it seems a little hope to me.  But the funny thing is I can't export the editted video.  I can't find the export button.

I tried;
File -> OpenTimelineIO Export

Error popup;```

python3 could not load opentimelineio module
```

Please refer to attached screenshots

---

### Post by satimis on 2021-12-01
> **dirtydog01 said:**
> I tried MX Linux, thought it was ok. Not using it now.
Thanks for your info

I'll test it on a VirtualBox VM

Regards

---

### Post by TheFu on 2021-12-02
Sorry, I avoid KDE software.

I've had problems running real videoeditors in VMs.  They **really** need direct access to the GPU. Some refuse to work without that access, IME.
As for sharpening videos, I have no experience with that sort of filter.  The math for it says it isn't possible to do better than the original, so definitely don't expect miracles.

I found this: [https://forum.videohelp.com/threads/392684-Best-software-for-sharpening-blurry-video](https://forum.videohelp.com/threads/392684-Best-software-for-sharpening-blurry-video) which has some techniques.  Looks like they recommend reducing the resolution until the video is sharp, then let the new processing increase the resolution while keeping it sharp. Can't go from 320i --> 480p, but perhaps halfway between.
One of the oddest suggestions (to me) was to rotate the video 90 deg and run the resolution down and back up with sharpening filters on that axis too.

Lots of trial and error.  Well outside my experience.

---

### Post by satimis on 2021-12-02
> **TheFu said:**
> 
I've had problems running real videoeditors in VMs.  They **really** need direct access to the GPU. Some refuse to work without that access, IME.

I prefer carrying testing on VM.  In case of problem, I just delete the VM and clone a new VM.  For bare-metal OS, I have to reinstall OS.

I'm prepared installing KVM/QEMU on the new 2TB NVME PCIe 4.0x4 SSD, mentioned on another posting.  On searching I found documents saying KVM/QEMU can forward GPU?

> 
 - snip -
I found this: [https://forum.videohelp.com/threads/392684-Best-software-for-sharpening-blurry-video](https://forum.videohelp.com/threads/392684-Best-software-for-sharpening-blurry-video) which has some techniques.  Looks like they recommend reducing the resolution until the video is sharp, then let the new processing increase the resolution while keeping it sharp. Can't go from 320i --> 480p, but perhaps halfway between.
One of the oddest suggestions (to me) was to rotate the video 90 deg and run the resolution down and back up with sharpening filters on that axis too.

Before I have made heavy searching on Internet.  But almost 99% suggestions are working on MS Windows

---

### Post by TheFu on 2021-12-02
> **satimis said:**
>  I'm prepared installing KVM/QEMU on the new 2TB NVME PCIe 4.0x4 SSD, mentioned on another posting.  On searching I found documents saying KVM/QEMU can forward GPU?

Yes, that can be done, but it is non-trivial and requires a second GPU assigned exclusively to the VM that is high-end (passthru doesn't work with the cheaper GPUs), some BIOS settings, some MB settings (VT-d enabled), and kernel settings (IOMMU).  The instructions to accomplish these are non-trivial and hardware dependent.  I think every new kernel requires going through the passthru setup again too.

There are some very interesting, new, methods for better GPU performance inside VMs that don't use GPU passthru.  I've never had the correct hardware to use those or the correct kernel to patch with the alpha kernel modules.  I was happy with QXL being 20x faster than VNC.  I understand there are virtio-based GPU passthru available if you are willing to patch your kernel and qemu.  

I know that Intel was working on shared GPU techniques. Think they called it GVT-g [https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide](https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide) ... the last youtube video from Intel that I saw showing it off was pretty buggy and crashed. Only specific Intel iGPUs worked.  I retired my only Intel desktop about 2 months ago after years of service. It had a supported iGPU, but was only a Pentium and was used as a headless server running a few VMs that could have been run on a raspberry Pi.

But, yes.  GPU passthru can be accomplished to VMs with multiple caveats.  For the last 10 yrs, the required steps have been 10 pages long, so we aren't at the "checkbox" simplicity stage.  I'm not trying to talk you out of KVM/qemu + libvirt.  That's what I use and switched from Xen and virtualbox to it about 10 years ago. Still very happy with that choice and I wouldn't go back to any of the prior hypervisors today.

---

### Post by Dennis N on 2021-12-02
> Has any folk tried MX Linux ?
Yes, a few years ago. It did not meet my needs, since the installer did not support LVM. All my non-VM installs use LVM now. But, it appears the newest installer will support LVM to some extent. It's about time. From their release notes (Oct 2021):
> New installer partition selection/management area, including some lvm support if lvm volume exists already....
The desktop offerings do not include Gnome - only KDE, XFCE, and Fluxbox, the release notes say. I like using Gnome, so that's a negative for me.

---

### Post by T6&amp;sfpER35% on 2021-12-02
i used it awhile back on a laptop that iv'e sold now , it worked great i loved it.
sadly for some reason it doesn't want to boot properly (just black screen with curser) after installation on my desktop.(plus my VPN doesn't support MX)
so yea ...but MX is nice in my opinion,very lightweight and FAST

---

### Post by satimis on 2021-12-03
Hi all,

Now I have MX Linux up running as VirtualBox VM.  It is working nicely.

The only problem encountered by me now is files sharing.  I have Guest Addition installed by unable to connect the share-folder of Ubuntu 20.04 host.  After sorting out this problem I'll start testing Vapoursynth

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
The problem of files sharing also solved.  I'll clone a new VM of MX Linux starting testing Vapoursynth

**[COLOR="#FF0000"]My MXLinux VM[/COLOR]**
Pls refer to attached screenshot

Regards

---

### Post by satimis on 2021-12-04
Hi  TheFu

I have installed Vapoursynth on MX-21 Linux, version 21, with following steps;

On Terminal
$ sudo apt update

$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

Login as administrator

$ flatpak install flathub org.bitbucket.mystery_keeper.VapourSynthEditor

That is all.  This installation method works seamlessly.

To start Vapoursynth running on Terminal;
$ flatpak run org.bitbucket.mystery_keeper.VapourSynthEditor

VapourSynthEditor started.  Pls refer to attached screenshot

This installation method is rather simple and straightforwards

You can try.  I'm now searching documents/tutorials re using vapoursynth.  I don't think the steps are similar to AviSynth

Regards

---

### Post by kc1di on 2021-12-04
I have used MX linux - Particularly like thier KDE edition.  Works well on my hardware here.

---

### Post by satimis on 2021-12-04
Hi TheFu,

Further to my posting #12 above;

flatpak is on Ubuntu 20.04 repo

$ sudo apt install flatpak

Install vapoursynth

Run
$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

Login

$ flatpak install flathub org.bitbucket.mystery_keeper.VapourSynthEditor

To run vapoursynth;
$ flatpak run org.bitbucket.mystery_keeper.VapourSynthEditor

Now VapourSynth is running on Ubuntu 20.04

Pls refer to attached screenshot

I clone an Ubuntu 20.04 VM to make this test

Regards

---

