---
title: "Xenial KVM-QEMU-Libvirt VGA Passthrough nVidia Graphics To Windows"
date: 2016-09-01
forum: Virtualisation
---

### Post by redger on 2016-09-01
I have a stock standard Xenial KUbuntu install (no PPAs or debs) with KVM-Qemu-Libvirt (and LXC-LXD)

Currently I have kvm VMs running windows with an AMD gpu. These run successfully, no problems

I've now acquired an nVidia GPU and wish to pass it through. I need to use the new "kvm hidden" and "hyperv vendor_id" strings to ensure the nVidia drivers load successfully.

On my newer VM created on Xenial I can use the "kvm hidden" string but not the  "hyperv vendor_id" string 

on my VM created under trusty (and migratde to Xenial) I cannot use either string

when I check the domaincommon.rng file I find support for "kvm hidden" but not "hyperv vendor_id" which seems reasonable since the vendor_id clause was added to libvirt in version 1.3.3 and Xenial seems to have 1.3.1

How do others address this issue ... I see references to people using these clauses on Xenial. Are you installing newer versions of qemu and libvirt via PPAs .... or have I missed something ? :)

thanks for your help

---

### Post by redger on 2016-09-02
**Progress**: I've managed to "upgrade" the Trusty VM to Xenial format. 
Need to use "virsh edit" to change
```
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader type='rom'>OVMF_[vm_name]</loader>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
```
To
```
  <os>
    <type arch='x86_64' machine='pc-i440fx-2.5'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/[vm_name]_VARS.fd</nvram>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
```

And create the VARS.fd file using```
sudo cp /usr/share/OVMF/OVMF_VARS.fd  /var/lib/libvirt/qemu/nvram/[vm_name]_VARS.fd
``` where [vm_name] is the name libvirt knows your vm by

then when the vm is first started you'll get a UEFI error which will eventually (after 3-5 failed restarts) lead to Windows Boot Repair where you can select Advanced and UEFI options. The next restart should work ok after that (seems to rebuild the UEFI vars)

Then we can add the necessary <hidden state='on'> clause using "virsh edit [vm_name]"
```
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
```

Which still leaves me without the necessary <vendor_id state='on' value='whatever'/> clause, which libvirt (virsh edit) rejects

---

### Post by KillerKelvUK on 2016-09-02
Hey redger, its been a while since I've seen you here, hope all is well?

I remember reading about the new hyper-v fixes for nVidia cards and went on a hunt as to where I read about it, turns out it was in AW's slide deck for the recent KVM forum ([http://awilliam.github.io/presentations/KVM-Forum-2016/#/4/2](http://awilliam.github.io/presentations/KVM-Forum-2016/#/4/2))

I've not seen any chatter myself about being able to implement this on 16.04 stock binaries, like you my libvirt is only 1.3.1 although the qemu version should be okay.  I was thinking it might be possible to use custom <qemu:commandline> tags in the xml like in the go old days but I don't even think that would work as libvirt won't allow you to remove the CPU config and the new hyper-v tags need to be put into the -cpu line?  Like you I'm still using the kvm hidden state hack for my GTX 970.

FWIW, the ovmf changes you've needed to make look like they're because you've migrated from a consolidated ovmf+vars image to a split image, which I think is as a result of the libvirt upgrade from Trusty to Xenial and its handling of bios/uefi loaders.  You possibly could have avoided that by sticking with the OVMF-pure.fd and just removing the nvram line, but TBH I'm specu-guessing here :-)

---

### Post by redger on 2016-09-02
hi mate, yes good to hear from you again :)

You're correct about changing the OVMF setup ... I needed to do that in order to enable the KVM Hidden clause, libvirt was rejecting it otherwise (I didn't track through all the templates but it's clearly a difference between the "trusty" template and the "xenial" template as defined through the machine clause)

The best reference source these days is probably the Arch wiki [https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#.22Error_43_:_Driver_failed_to_load.22_on_Nvidia_GPUs_passed_to_Windows_VMs]("https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#.22Error_43_:_Driver_failed_to_load.22_on_Nvidia_GPUs_passed_to_Windows_VMs"). There was extensive discussion of the wiki entry via the mailing list as it was being constructed.

I had toyed with the idea of direct qemu clause, but i'd rather not if I can help it - it's generally better to let libvirt manage everything to ensure consistency and stability. I may yet experiment.

It's probably possible to run windows with nvidia using something similar to my current setup, but I would probably need to remove the hyperv clauses ... which would have performance consequences I would rather avoid.

It's also possible to use a PPA to obtain the latest virtualisation modules eg. [https://launchpad.net/~jacob/+ppa-packages]("https://launchpad.net/~jacob/+ppa-packages") ... but I'm trying to retain a "pure" host at this stage, it's running about 6 LXD & LXC containers plus 4 KVM vms so stability is important hence the desire for a "vanilla" solution.

---

### Post by KillerKelvUK on 2016-09-02
I agree with your sentiments about keeping away from custom qemu lines in the libvirt xml, I ditched them as soon as I was able!  Appreciate the link to the arch discussion, will take a longer read.

Regards the performance impact of removing hyperv, I can honestly say I've not noticed but then having never been able to run Windows with a passed through nVidia with hyperv enabled I've got zero comparability.  I can however say I game away on my 970 without hyperv, albeit a casual Windows gamer...I prefer the laziness of my Xbox :-)

Regards the PPA you linked for updated virt packages...I caution you to consider this you last resort, I stopped using it a long time ago now as some of his builds were broken and there was no easy resolution.  ppa-purge does work but not with libvirt, there is something broken in the packaging which results in a completely borked reversion and its a manual job from here, re-encountered this as a test case in recent weeks.  The ppa-purge problem isn't Jacob's doing and he's a one-man-band I believe so not really in a position to support the masses with his builds.

---

### Post by redger on 2016-09-02
**Progress:** I managed to pass the vendor_id parameter through BUT only by adding a qemu argument, not thru libvirt itself. A bit of a hack, but it seems to work.

Added this to the end of the libvirt definition

```
  <qemu:commandline>
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff,kvm=off,hv_vendor_id=sometext'/>
  </qemu:commandline>

```

Windows now starts under libvirt control (well sort of, since the cpu parameters are not handled via libvirt, they're over-ridden by the above code)

I couldn't just add "-cpu hv_vendor_id=" directly in the above format, I had to override ALL the cpu parameters rather than just expecting to be able to add an additional one. Not a great solution, but perhaps workable for the moment.

Does anyone have a better solution ?

---

### Post by KillerKelvUK on 2016-09-04
Tested this and I *believe* it has worked although the qemu command libvirt executes includes two -cpu parameters?  Based on the fact that my guest started fine and the nVidia drivers loaded I am assuming the later -cpu parameter overrides the former?  Do you know of anyway to confirm if the hyper-v enlightenment's are actually present from within the guest?

FWIW, I ran a Heaven GFX benchmark pre and post change, the end results were the same so I suspect the performance improvements hyper-v brings must manifest under other circumstances.

---

### Post by sye737 on 2016-09-05
I was just retrying to get this working after asking on vfio-users to no avail and what a coincidence. I tried adding the qemu:commandline params under the libvirt but my 750Ti still gives me code 43 on windows 10 :( (passthrough works fine on arch linux guest). This is even though it seems like its passing the command line flags correctly. I think I'll just wait for the release of Xenial where libvirt is finally upgraded from 1.3.1 to resolve this issue.

---

### Post by redger on 2016-09-05
@sye737 .... have you also tried without the hyper-v enlightenments ie. do NOT specify the "hv_" parameters anywhere

Remove the Hyperv section from the "Features".
```
  <features>
    <acpi/>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
```

also remove hypervclock from the clock section
```
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>

```

And modify the additions at the end, to also remove "hv_" elements
```
  <qemu:commandline>
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host,kvm=off,hv_vendor_id=sometext'/>
  </qemu:commandline>
```

Does the driver work now ? or still code 43 ?

@KillerKelvUK ... you may be amused to discover that I don't actually have the new GPU yet (still "on a boat") so cannot test. OTOH I found this for verifying the use of hyper-v enlightenments [https://www.spinics.net/lists/kvm/msg100181.html]("https://www.spinics.net/lists/kvm/msg100181.html") ... and some general background [http://computerperformancebydesign.com/hyper-v-performance-introduction/]("http://computerperformancebydesign.com/hyper-v-performance-introduction/")  and [https://www.linux-kvm.org/images/0/0a/2012-forum-kvm_hyperv.pdf]("https://www.linux-kvm.org/images/0/0a/2012-forum-kvm_hyperv.pdf")

---

### Post by sye737 on 2016-09-05
Sadly I've tried almost every combination of hyperv tags (I've never had the hypervclock timer tag). I also tried the way recommended in vfio-users using a wrapper script to interdict the arguments so only one `-cpu` argument gets passed with the vendor_id set.

```

#!/bin/sh
exec /usr/bin/qemu-system-x86_64 \
  `echo "\$@" | sed 's|hv_relaxed|hv_relaxed,hv_vendor_id=KeenlyKVM|g'`

```

Every example of successful bypass of code 43 seems to come from an Arch/Fedora user that I'm assuming has newer libvirt/qemu.

---

### Post by redger on 2016-09-05
hmmm .. that's unfortunate.

Is this a new Windows install, or an existing install ? Which version of Windows ?

Which version of the nVidia driver ? Some of the older drivers were a bit easier to spoof.

How about the host .. is it a new install (Xenial ?) or an existing (eg. Trusty) or was it an upgrade (to Xenial say) from an "older" install ? That shouldn't make any difference, but you never know ...

As a last resort, have you seen this ... [https://github.com/sk1080/nvidia-kvm-patcher]("https://github.com/sk1080/nvidia-kvm-patcher") - it may be worth a go

---

### Post by sye737 on 2016-09-05
This is an fresh install onto a virtual disk, I can't get the install windows iso to work with gpu passthrough so I installed via QXL. This is currently 16.04 upgraded over a long period so it could be the issue but I doubt it because I'm using all vanilla packages. I think that's the culprit because a lot of the related packages were outdated with 16.04 but updated in Xenial (libvirt, virt-manager, qemu-kvm).

---

### Post by redger on 2016-09-06
have you updated the VM machine definition ... I found I needed the latest UEFI bios, in my case I went from 
machine='pc-i440fx-trusty'
to
machine='pc-i440fx-2.5'

which caused a few heart pounding moments but was eventually accepted ok.

Is the VM a Seabios or UEFI install ? Which version of Windows (XP, 7, 8, 10) ?

Am I correct in assuming that the host is Xenial, upgraded from a prior Ubuntu release, but that the VM is new and you've experienced some trouble starting the install .... and then code 43 once the nVidia drivers are installed ??
If you ten detach the video card from the VM and restart it does Windows recover and revert to the qxl / Spice interface ?

---

### Post by redger on 2016-09-06
have you updated the VM machine definition ... I found I needed the latest UEFI bios, in my case I went from 
machine='pc-i440fx-trusty'
to
machine='pc-i440fx-2.5'

which caused a few heart pounding moments but was eventually accepted ok.

Is the VM a Seabios or UEFI install ? Which version of Windows (XP, 7, 8, 10) ?

Am I correct in assuming that the host is Xenial, upgraded from a prior Ubuntu release, but that the VM is new and you've experienced some trouble starting the install .... and then code 43 once the nVidia drivers are installed ??
If you ten detach the video card from the VM and restart it does Windows recover and revert to the qxl / Spice interface ?

---

### Post by redger on 2016-09-06
have you updated the VM machine definition ... I found I needed the latest UEFI bios, in my case I went from 
machine='pc-i440fx-trusty'
to
machine='pc-i440fx-2.5'

which caused a few heart pounding moments but was eventually accepted ok.

Is the VM a Seabios or UEFI install ? Which version of Windows (XP, 7, 8, 10) ?

Am I correct in assuming that the host is Xenial, upgraded from a prior Ubuntu release, but that the VM is new and you've experienced some trouble starting the install .... and then code 43 once the nVidia drivers are installed ??
If you ten detach the video card from the VM and restart it does Windows recover and revert to the qxl / Spice interface ?

---

### Post by KillerKelvUK on 2016-09-06
> **redger said:**
> @KillerKelvUK ... you may be amused to discover that I don't actually have the new GPU yet (still "on a boat") so cannot test. OTOH I found this for verifying the use of hyper-v enlightenments [https://www.spinics.net/lists/kvm/msg100181.html](https://www.spinics.net/lists/kvm/msg100181.html) ... and some general background [http://computerperformancebydesign.com/hyper-v-performance-introduction/](http://computerperformancebydesign.com/hyper-v-performance-introduction/)  and [https://www.linux-kvm.org/images/0/0a/2012-forum-kvm_hyperv.pdf](https://www.linux-kvm.org/images/0/0a/2012-forum-kvm_hyperv.pdf)

:-) using us as your guinea pigs then lol

The first link you added here advises "for hv_vapic we also need x2apic to be enabled" and so shows the qemu command line as ```
-cpu qemu64,+x2apic,family=0xf,hv_vapic,hv_spinlocks=0xfff,hv_relaxed,hv_time
```.  Will make an adaption and retest but I've just grabbed the WinDBG tools so will do some pre/post observations again.

---

### Post by redger on 2016-09-06
:D good to see a volunteer.

Follow me, I'm right behind you :P

---

### Post by heiko_s on 2016-09-07
Just seen this thread. I've spent the last few days performance optimizing my Windows 10 VM. I'm running Linux Mint 17.3 (Ubuntu 14.04) with qemu 2.1.2 from ppa. Almost all as described in my how-to here: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692").

I've run multiple benchmarks (Passmark 8 mainly, but also Userbenchmark) trying to squeeze out the last inch of performance. Here some conclusions:

1. The hyper-v extensions do have a little impact, but it's so small that it's difficult to quantify. With my Nvidia GTX 970 they do NOT affect 3d performance, but perhaps 2D performance. I doubt it will affect the Heaven benchmark. In general, with GPU passthrough, the graphics card is not affected by any tuning.
2. CPU pinning has more impact, but again nothing to get too excited about. There are several drawbacks to it too.
3. I still have to put it all together - I've run dozens of benchmarks with different settings - but almost all other settings such as -machine q35 or the disk configuration have a much higher impact, usually for the worse if misconfigured or not optimized.
4. Maybe I'm blind but I couldn't find any means of checking whether or not Windows 10 uses the HV enlightenments - does anyone have a clue on how to test that?

Here is what I did:
1. Patched the Nvidia driver under Windows has described here: [https://forums.linuxmint.com/viewtopic.php?f=231&t=229122]("https://forums.linuxmint.com/viewtopic.php?f=231&t=229122")
2. Changed my qemu start script - it now looks like this:
```
taskset -c 0-9 qemu-system-x86_64 \
  -serial none \
  -parallel none \
  -nodefaults \
  -nodefconfig \
  -enable-kvm \
  -name $vmname,process=$vmname \
  -machine q35,accel=kvm,kernel_irqchip=on,mem-merge=off \
  -cpu host,hv_vapic,hv_time,hv_relaxed,hv_spinlocks=0x1fff \
  -smp 10,sockets=1,cores=5,threads=2 \
  -m 20G \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc base=localtime,clock=host \
  -vga none \
  -nographic \
  -soundhw hda \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -device vfio-pci,host=00:1a.0 \
  -device vfio-pci,host=08:00.0 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=c \
  -drive id=disk0,if=virtio,cache=none,format=raw,aio=native,file=/dev/mapper/lm13-win10 \
  -drive id=disk1,if=virtio,cache=none,format=raw,aio=native,file=/dev/mapper/photos-photo_stripe \
  -drive id=disk2,if=virtio,cache=none,format=raw,aio=native,file=/dev/mapper/media-photo_raw \
  -netdev type=tap,id=net0,ifname=tap0,vhost=on \
  -device virtio-net-pci,netdev=net0,mac=00:16:3e:....
```

taskset -c 0-9 is how I pin the VCPUs.

The biggest impact, however, was setting up the CPU governor. My clock rate would not go higher than 3.2 GHz, whereas my 3930K CPU is supposed to enter Turbo and reach 3.8 GHz.

```
cpufreq-set -g powersave
``` after checking that the turbo is enabled did the trick. I don't know why it didn't work in the first place. If I need some extra uumph I set it to "performance".


I should probably ask that on a separate thread: What's the big deal about virt-manager? Why should I want to use it if I anyway have to hack it's XML files?

Here my Userbenchmark results: [https://forums.linuxmint.com/viewtopic.php?f=231&t=197754]("https://forums.linuxmint.com/viewtopic.php?f=231&t=197754") Note: I'm posting under the name powerhouse.

@redger: I think we crossed paths on this forum in the past :-)

---

### Post by redger on 2016-09-08
hi Heiko, I do recall previous discussion :)

**PROGRESS:** I have now received the new card, installed it, blacklisted the Nouveau driver (eventually - didn't realise I had [a] blacklist via Grub [b] regenerate intram-fs), bound it to pci-vfio and then started the VM. The VM started happily, so I removed the AMD drivers, instaleld the nVidia drivers and Bob's your uncle .. it worked !!

Thanks for the links. I read your thread about performance testing. Interesting. For me to conduct realistic performance testing at this stage will probably be more trouble than it's worth since this machine is already running a number if VMs which I am loth to stop for any significant period. These same VMs will probably "corrupt" performance testing. I have a "simple" 4 core Haswell processor in which 3 cores are allocated for guests and the 4th is for the host - that means the VM can "bounce around a bit" and the various VMs are going to interact in such a way that performance will be degraded from time to time - I've traded performance for throughput. For all that I would still like the benefit of all available performance enhancements (within the given constraints).

Why go with libvirt ? I previously used direct qemu command line. Libvirt advantages
[LIST]
[*]Identification of options without having to trawl through screeds of detailed documentation which generally lacks context and usage advice
[*]Parameter validation and consistency checking. This is a particular bugbear since it's easy to either mistype a parameter or choose conflicting parameters
[*]Integrated components & locations eg. apparmor, ovmf etc
[*]Easy access and monitoring through the graphical interface (virt-manager) through a single coherent integrated interface covering multiple VMs 
[*]No need to either run as root or mess around with permissions to be able to execute qemu using my own id(as I once did) 
[*]In the end it's just easier for me to use libvirt and virt-manager eg. I can create a new VM with gpu passthrough etc. in just a few minutes with a high probability of success first time and no need to use the cli
[/LIST]
with respect to having to edit libvirt's xml, that's relatively minor in the scheme of things and is often / generally unnecessary - in this case it's just thanks to nVidia's consumer friendly practices (NOT !)

As for testing the impact of the hyper-v enlightenments I haven't tested the impact yet, not verified that they're in use. 
This is the best hyper-v reference I've found so far [http://computerperformancebydesign.com/hyper-v-performance-introduction/]("http://computerperformancebydesign.com/hyper-v-performance-introduction/") but have yet to find a discussion from someone who's used this to test in a reasonably rigorous manner.
So far I can see games running faster though my historic test cases are not significantly improved in spite of half an order of magnitude (?) increase in GPU power ... a new test case with newer software shows frame rate improved by a factor of about 6 compared to the previous VM setup with a much older AMD graphics card ... but I do not have a bare metal baseline with the new card.
The rubber will meet the road if / when I get on to gpu accelerated deep learning which will be very sensitive to speed of memory transfers

---

### Post by heiko_s on 2016-09-08
Thanks for your reply, redger. I do remember your kvm tutorial here on the forum.

I guess I should try virt-manager, though for me it seems easier to modify a qemu script to make changes, or start a new VM. I will look at virt-manager once I can convince myself to upgrade to 16.04 (or Linux Mint 18) - I'm currently on 14.04 (LM 17.3). Never touch a running system!

As to performance, I have found that GPU performance does NOT vary, unless when the benchmark also heavily employs the CPU. Less than optimal qemu options (I guess that holds true for libvirt/virt-manager, too) can have a devastating effect on disk performance, and even CPU and memory performance can take a dive, but usually much less. This means that you usually won't notice a performance drop in a game, since most games are heavily GPU bound. You will notice a difference with disk-bound I/O heavy tasks, or where both disk and CPU is challenged.

While I haven't done a "benchmark" on it, I noticed yesterday that exporting/resizing a couple of TIFF files to jpg within Lightroom was significantly faster than before my tweaking. This task employs both multiple CPUs and disk I/O. I should probably build a benchmark around this - say converting 100 TIFFs and time it - because this type of benchmarking is much more down to earth than the abstract numbers that Passmark or Userbenchmark provide. The TIFF conversion task shows the performance of the entire system, as I believe Lightroom makes use of the GPU as well (I can turn that feature off and rerun the test).

---

