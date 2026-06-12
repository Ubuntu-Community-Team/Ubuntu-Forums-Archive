---
title: "Complete image of HD and Windows license &quot;transfer&quot; on VM for a newly bought laptop"
date: 2018-01-17
forum: Virtualisation
---

### Post by LastStarDust on 2018-01-17
Hello,
I am pretty sure that what I am going to ask has been already covered somewhere else but, to my best efforts, I couldn't find a web resource that describes in detail what I need. The fact is that in April I am going to buy a new laptop (a Lenovo Carbon X1) and it will come with Windows 10 pre-installed. I would like to install Ubuntu on it, as the only OS and use Windows only sporadically as a Virtual Machine. 

So I have two questions:
[LIST]
[*]How can I create an identical image of the HD, so that if the laptop develops any hardware problem, I can flash the original image back and send it to Lenovo without interfering with the warranty? Lenovo says that you don't loose warranty if you install Ubuntu but they may be not able to repair the PC. And I don't want to find myself in that situation. Is Clonezilla the right software here, isn't it? In case what would be the best course of action?
[*]This is tricky. I would like to transfer the Windows license from the HD to the Virtual Machine. Is it possible? I know that it isn't a question strictly relevant to this forum, nevertheless, it is part of the problem. In case, how can I transfer the license?
[/LIST]

Thank you very much for your help.

---

### Post by sudodus on 2018-01-17
I use Clonezilla, it works well for me. Create an image of the whole drive. Test that you can restore it to another drive (of at least the same size), if you want to be sure that you have a good backup image.

I think Microsoft considers a virtual machine as another machine, and you should have another license for it (or buy a licence, which is not bound to a particular machine, but such a license is much more expensive).

---

### Post by howefield on 2018-01-17
Thread moved to the "*Virtualisation*" forum.

---

### Post by QIII on 2018-01-17
As for transferring the image to a VM -- no, it won't work.  OEM Windows installations are activated and locked to a specific machine.  A VM is a different machine.  Windows would detect that and demand that you re-activate, which will be impossible.

If your warrantee allows (check first!), you could remove the original drive, set it aside and use a different drive for Ubuntu.

Otherwise,  dual booting will work if you are very careful.

---

### Post by KillerKelvUK on 2018-01-17
Hi, so I'm not certain what side of the license legality this falls on so I'm not going to post the details here in case it is in the "grey" zone and thus contravening forum rules.  However I believe I would be permitted to at least advise you google this phrase exactly and select the top link "qemu windows oem smbios", if you get to where I propose then scroll to the post in that forum thread that describes a process for what you seek.  My view is that provided you ONLY EVER use the Windows vm on that same physical hardware platform then you aren't operating in a way that penalises the software house, just outside of there supported operating policies.

---

### Post by LastStarDust on 2018-01-18
> **QIII said:**
> As for transferring the image to a VM -- no, it won't work. OEM Windows installations are activated and locked to a specific machine. A VM is a different machine. Windows would detect that and demand that you re-activate, which will be impossible.

If your warrantee allows (check first!), you could remove the original drive, set it aside and use a different drive for Ubuntu.

Otherwise, dual booting will work if you are very careful.

Thank you for your suggestions. It is good to have other options, too. I have experience with dual-booting, but never when one of the OSs is OEM Windows. Is there any particular precaution to follow in that case?
Anyway, swapping the disk leaves me with the very same problem of having to install a VM for Windows. Because I need Windows from now and then. 
The dual-boot could be a solution but I like the VM option the best, because in that way I would be able to use Windows applications at the same time as Linux ones, that is a great time saver. And I don't want to spend my life battling with Wine.

---

### Post by LastStarDust on 2018-01-18
> **KillerKelvUK said:**
> Hi, so I'm not certain what side of the license legality this falls on so I'm not going to post the details here in case it is in the "grey" zone and thus contravening forum rules. However I believe I would be permitted to at least advise you google this phrase exactly and select the top link "qemu windows oem smbios", if you get to where I propose then scroll to the post in that forum thread that describes a process for what you seek. My view is that provided you ONLY EVER use the Windows vm on that same physical hardware platform then you aren't operating in a way that penalises the software house, just outside of there supported operating policies.

Thank you for the suggestion! Of course, I will only ever use the Windows VM on the same physical hardware. I think I found the discussion that you were hinting at. I would use VMWare as a virtualization software, so I think that it would be actually simpler than that.

---

### Post by KillerKelvUK on 2018-01-18
> I would use VMWare as a virtualization software, so I think that it would be actually simpler than that.

Assuming you aren't meaning an ESXi server on your laptop as I don't see how that gets you where you want then are you talking VMware Workstation?  I've no experience here to assist further sorry but if you can configure a guest in that to the same granularity i.e. SMBIOS info, apci, disk serials and network mac's then crack on, it would be good if you can come back and advise on your success or otherwise.  The only callout I'd make is that Workstation I believe is a type 2 hypervisor as such performance isn't going to be as good as using a type 1 such as qemu with KVM.  Also I'm not sure on what support options you have with VMware from an Ubuntu perspective, I'm sure there will be a community here for it but I dont recall seeing many posters on that topic so you may struggling this way.  Just points to bare in mind, not suggesting you need to change your mind, work with what you are comfortable with.

---

### Post by QIII on 2018-01-18
> **LastStarDust said:**
> Thank you for the suggestion! Of course, I will only ever use the Windows VM on the same physical hardware.

It is not that simple.  The VM is a different machine.  Its hardware abstraction layer presents different virtual hardware to the OS.  It will be identified by the OS as a different machine and will demand re-activation -- which cannot be done because it will have been locked to the physical machine's hardware.  The physical machine's hardware is invisible to the guest OS because it is behind the VM hardware abstraction layer.

A VM is a different machine from the physical machine.

Further, an OEM version installed by the OEM often comes with a Microsoft EULA forbidding its use in a VM.

---

### Post by KillerKelvUK on 2018-01-18
Hey QIII so technically speaking I agree with your points about vm's providing a different HAL than the physical PC and this causing the OEM installation to de-activate.  However the suggested process in the referenced forum posited that using qemu with libvirt allows sufficient hardware markers from the licensed host to be effectively recreated in the guest thus allowing it to activate and once again consume the OEM license the actual physical hardware is allocated.  

> Further, an OEM version installed by the OEM often comes with a Microsoft EULA forbidding its use in a VM.

As for the EULA permissions... [https://www.microsoft.com/en-us/Useterms/OEM/Windows/10/UseTerms_OEM_Windows_10_English.htm](https://www.microsoft.com/en-us/Useterms/OEM/Windows/10/UseTerms_OEM_Windows_10_English.htm) ...sections 2.b. and 2.d.iv. would seem to permit this activity.  However I must admit I have not read the EULA in full, nor have I searched for any competing/conflicting permissions which quite plausibly exist.

---

### Post by DuckHook on 2018-01-18
When I tried this (admittedly ages ago, with XP and Vista), it was possible to change some of the VM markers in the guest to make it look like the bare metal markers underneath. I used exactly the workarounds that are being Googled. I have no problem citing this because both my XP and Vista OEM licenses permitted use in a VM and it was simply a matter of hacking the VM to get it to work. But I had the advantage that both versions came with proper install media and the old-fashioned license key system that would allow pristine reinstallation for a limited number of tries. However, MS soon after went to preinstalled images that are hard-coded to one specific combo of motherboard + other components. Those are much harder to hack and I'm not sure it can be done anymore. All of the instructions that can be found for such hacks are old.

It goes without saying that no one should be doing this without a clear understanding that it is permitted by their license, OEM or otherwise.

MS is very clever at protecting their turf. If they put half as much effort into&#8212;say, improving their file system&#8212;we wouldn't have to keep defragging every week.

---

### Post by QIII on 2018-01-18
I have actually tried qemu & libvert on a full retail disk installation converted to  qcow2, creating a kvm machine matching the HAL (right down to the hash) and it still de-activates.  Being an MCP and a Microsoft Insider, I was able to convince Microsoft to activate the installation from that disk one more time than is usually allowed.

So long as one has the retail version installed on one machine at a time (that is: not on the physical machine and a VM on that same physical machine), the EULA allows for VM installation.

One may also install a purchased OEM disk in a VM, but it is locked to that VM.

---

### Post by DuckHook on 2018-01-18
> **QIII said:**
> …I was able to convince Microsoft to activate the installation from that disk one more time than is usually allowed…
^^^^+

@OP

I was going to suggest exactly what QIII has above… you would have far better luck and far fewer headaches if you would contact your OEM, explain what you are trying to do and ask them to give you another activation key. You would have to download an ISO of Windows, but that can easily be done. OEMs have been known to supply activation keys purely on the basis of good customer care. They buy them in bulk, but be prepared to pay something, though usually not the same as for a retail license. Once you are set, create a set of reinstall media, nuke your current Windows, install Ubuntu, then the VM and don't look back.

---

### Post by LastStarDust on 2018-01-19
Thanks to everybody for the useful insights. Of course, I knew that the hardware of a VM is an abstraction that may not correspond to the physical one. But I for sure don't know the details well enough to fully understand what you said (I will google it anyway and study a bit before even trying anything). I have not purchased the laptop yet, but first thing after purchase, I will contact Lenovo and explain them the situation and hopefully, the will give me another key.
PS for clarity, I was hinting at [WMware]("https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/14_0")[ Workstation Player]("https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/14_0"), the only free product of their line-up, but if you say that qemu gives better performance and customizability I will give it a try.

---

### Post by DuckHook on 2018-01-19
> **LastStarDust said:**
> …I have not purchased the laptop yet, but first thing after purchase, I will contact Lenovo and explain them the situation and hopefully, the will give me another key.
Hint: Contact them *before* you make your purchase. Tell them that your purchase depends in part on their ability to make this work at little/no cost to you.
> PS for clarity, I was hinting at VMWare…but if you say that qemu gives better performance and customizability I will give it a try.
The difference between VMWare and KVM is:
[LIST=1]
[*]VMWare is a retail product, and as such, it is designed to be dead easy to use. VirtualBox is another that you may wish to look into if you want ease of use. It has the additional advantage of being quasi-FOSS and "free" for personal use. The major drawback to both is that they are not natively implemented in the kernel. This is a bigger deal than some suppose.
[*]To my limited knowledge, there are two VM engines that are actually baked into the kernel: KVM and XEN, both fully FOSS. Because they are so intimately bound into the guts of the kernel, they run like greased lightning. Also, extremely flexible and customizable (but you must have the knowledge to customize). Their major drawback—and it is major—is that they are not newbie-friendly at all. There are guides for setting up both—KVM/QEMU is easier than XEN/QEMU—but the documentation does not come close to the level of the commercial/proprietary stuff, and if you ever need to get into the guts of the VM (i.e. customization), it is very arcane.
[/LIST]

---

### Post by lammert-nijhof on 2018-01-21
I do not see any problem installing Ubuntu and install Windows in a VM. I bought 2nd hand computers and they came with a Win Vista and Win 7 stickers. I installed Ubuntu on those machines and re-installed and activated Win Vista and Win 7 in the Virtual Machine running on the HW with the right sticker. Maybe something changed in Windows 10 activation, otherwise use the same procedure. If CPU type and serial number are correct during activation, it should be like re-installing Windows. If you want to be sure, install Virtualbox in Windows and reinstall Windows in the virtual machine.

If you are relatively new to virtualization, you should use Virtualbox. Virtualbox is also tightly integrated into the kernel using the same kernel and hardware functionality as KVM and XEN. Virtualbox is much easier to use and the current overhead is minimal. That difference in performance might have been true 5 years ago, but I doubt whether the others do much better now. On top of it, Virtualbox supports 3D video acceleration and allows the VM to share the HW functions of the video card effectively between Hosts and VMs.

---

### Post by KillerKelvUK on 2018-01-21
> Virtualbox is also tightly integrated into the kernel using the same kernel and hardware functionality as KVM and XEN.

So sure VB exploits the virt capabilities of the hardware via provisions the OS makes for these capabilities but it is still a type 2 hypervisor so saying its "tightly" integrated into the kernel is a bit of a stretch.  VB's use of these capabilities is no different to any other type 2 to my understanding.

> Virtualbox is much easier to use and the current overhead is minimal.

In comparison to what? virt-manager is pretty easy to use and installation of kvm/qemu/libvirt takes care of most basics that a desktop user would need.  Last time I looked the VB UI was pretty feature packed for sure but the number of people coming here who are stuck trying to run the wrong guest architecture is pretty high.  I don't think either solution is ideal for all, maybe VB's documentation is better from what I remember but thats a while ago now.

> That difference in performance might have been true 5 years ago, but I doubt whether the others do much better now.

Erm so this is just plain wrong...performance benefits of a type 1 vs. type 2 are still significant but do vary by use case.  [https://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-virt](https://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-virt) ...this article is a little over 2 years old but it summarises...

> Overall, Xen and KVM were performing well compared to the host's performance. Xen tended to have the most wins while KVM generally came in right behind and the two were very competitive with one another, either are great solutions for Linux virtualization depending upon your specific needs. The VirtualBox results, however, were a bit concerning at least for its stock configuration with it performing poorly near universally in the multi-threaded benchmarks and the behavior in the disk benchmark also being potentially problematic.

---

### Post by DuckHook on 2018-01-21
> **lammert-nijhof said:**
> Virtualbox is also tightly integrated into the kernel using the same kernel and hardware functionality as KVM and XEN.
Mmmm…

It is certainly well integrated, but saying that it is "tightly integrated" may be a stretch. It loads as a module from Oracle; not native to the distro. It requires dkms to keep current with kernel upgrades. Even then, it will not automatically upgrade to the next point version which has caused problems for a number of forum members just recently. Most of all, it must use closed-source binaries for full functionality on the desktop; something that KVM and XEN, being fully FOSS, do not. This last is of importance to some of us.
> Virtualbox is much easier to use and the current overhead is minimal. That difference in performance might have been true 5 years ago, but I doubt whether the others do much better now.

Again, must be careful here. KVM and XEN are type 1 hypervisors. VirtualBox and VMWare are type 2. As type 2 they run slower. I can personally attest to this.
> On top of it, Virtualbox supports 3D video acceleration and allows the VM to share the HW functions of the video card effectively between Hosts and VMs.
True, but not as effectively as HW passthrough which both XEN and KVM support and which, to my knowledge, VirtualBox does not. Not many use HW passthrough—true—but it is much superior to VirtualBox's 3D support which is heavily constrained by its relatively primitive emulated video card.
> If you are relatively new to virtualization, you should use Virtualbox.
I do tend to agree with this conclusion. But it is purely based on ease-of-use and not because VirtualBox is equivalent in power or integration to KVM.

Not trying to be argumentative. Just factual.

Edit: Ninja'd by KillerKelvUK

---

### Post by DuckHook on 2018-01-21
> **KillerKelvUK said:**
> &#8230;virt-manager is pretty easy to use and installation of kvm/qemu/libvirt takes care of most basics that a desktop user would need.  Last time I looked the VB UI was pretty feature packed for sure but the number of people coming here who are stuck trying to run the wrong guest architecture is pretty high.  I don't think either solution is ideal for all, maybe VB's documentation is better from what I remember but thats a while ago now&#8230;
Purely my personal opinion here, but I find VBox much easier to administer than KVM/QEMU/libvirt. I recently moved my virtual images to another partition.

In VBox, the change is child's play. Just open VB Manager navigate to Global Tools &#8594; Hard Disk &#8594; Properties &#8594; name_of_image and change the path to the new location. Easy peasy.

In KVM:
[LIST=1]
[*]You need the command line (for general users, first big drawback).
[*]You need to invoke *virsh* with the *edit* option, which is very poorly documented (second big drawback).
[*]*virsh* uses *nano* which most general users would find intimidating (third big drawback).
[*]You need to know how to do a search and replace in nano of a data-dense XML file to make your changes (fourth big drawback).
[*]If you get just one character wrong, or replace the wrong term, your VM will not launch and you may actually end up borking your config file (fifth big drawback).
[*]Worst of all, getting this info is not for the faint of heart. It is spread all over the internet, and has to be pieced together while sifting through outdated forum posts and having enough research chops to separate the good info from the bad (sixth and biggest drawback).
[/LIST]
In stark contrast, [VBox documentation]("https://www.virtualbox.org/wiki/Documentation") is complete, well written and a model of how such documentation should be done.

I think it's pretty clear that the general user will find VBox and VMWare easier to use and to understand. The fact that they don't run as fast or as efficiently is largely ameliorated by the speed of modern HW. It is high-end users leveraging things like, say, video passthrough for video processing who will find the differences incomparable.

Having said all of that, I still prefer KVM, but for extraneous reasons (like its being fully FOSS) as much as for its performance.

---

### Post by LastStarDust on 2018-01-22
Thank you again for the useful info.

> **DuckHook said:**
> Hint: Contact them *before* you make your purchase. Tell them that your purchase depends in part on their ability to make this work at little/no cost to you.
You are absolutely right. As a scientist, I don't have the knack of doing business (but I should). I will contact them beforehand.

Regarding the VM, I remember using qemu some years ago on a little netbook with limited resources and hard disk space because other VM softwares required too much overhead. I remember it was a pain to set it up, but eventually it worked. But I easily imagine someone less stubborn than me giving up pretty soon. Anyway, you got me curious about trying KVM or XEN. I will use this thread as a starting point to address my issue.

---

### Post by lammert-nijhof on 2018-01-22
Well the only argument you provide, is that KVM and XEN are type 1 hypervisors and Virtualbox is a type 2 hypervisor. That is just jargon and it does not explain anything about performance in 2018. Both types do use the same VTx and AMD-V facilities both have nowadays the same memory management approach for running VMs; So there is no architectural reasons for a difference in performance. If you can explain the architectural difference in some detail, other then type 1 and type 2, I am happy to learn about it. Don't be afraid to go into some detail, because I worked inside propriety OSes (design and coding), that is why I'm supportive, bot not really fanatic about FOSS. In my opinion the only potential difference is caused by better written/reviewed code, more efficient compiler etc. KVM and XEN might have an advantage there, because I hear that the team working on Virtualbox in Oracle is small.

With respect to pass through of video cards that is possible in Vbox too, but still "experimental" and you need to go to the CLI. But with the current prices of video cards I would prefer to share that one expensive card between the VMs.

The mentioned performance comparison was not very relevant, because it concentrated on large servers with many CPUs (10 cores and 20 threads). Besides it has been run with Vbox 5.04 from Oct 2015. Release 5.0 was the first release implementing the VTx and AMD-V facilities, so probably not very well optimized yet. Despite that, KVM/XEN seems better in a server environment for program development. Virtualbox is better for running server production databases and Vbox/KVM and XEN are more or less equal in a home environment for e.g audio and video processing. [COLOR=#800000]Which completely proves my point![/COLOR]

---

### Post by DuckHook on 2018-01-22
Although this debate may indirectly benefit the OP, I'm afraid we are at risk of hijacking LastStarDust's thread. I am happy to continue discussion on a new thread which I shall start shortly. I am interested in whatever tricks you can show me to run VBox faster.

---

### Post by LastStarDust on 2018-04-10
I eventually managed to get everything working. Thanks to everybody for the valuable pieces of advice. For future reference, I am describing the steps that I have taken. I will try to be brief.
[LIST=1]
[*]I wrote to the Japanese Lenovo customer service (I am Italian but I have just moved to Japan) before buying the laptop. As expected it was of no help. They suggested me to go to the University IT centre. I didn't even try. Japanese people are not very flexible especially when you ask for something that is not written in the manual. Moreover, I needed the laptop soon for my research. So I bought it.
[*]First thing after receiving the laptop, I updated the BIOS to the last version since I know that it is very difficult to do this kind of operation within Linux (correct me if I am wrong).
[*]Then I saved the ACPI tables and the license code on a USB drive. Maybe you can do this even after installing Linux. I noticed that the "SLIC" ACPI table was missing (I don't know why. Maybe it was erased during the BIOS update. Maybe it was never there. Anyway I did a complete backup of the drive with Clonezilla.
[*]I completely erased Windows and installed Ubuntu 17.10.
[*]I followed the procedure that @KillerKelvUK kindly suggested. I used qemu. Maybe since the SLIC table was missing Windows failed to activate.
[*]I called the Microsoft customer call centre (the Italian one) and followed all the instructions given by a recorded voice. It was copying and pasting an infinite sequence of digits. But eventually, and surprisingly without any human interaction, I had my VM version of Windows activated.
[*]Happy End
[/LIST]
Thank you again to everybody

---

### Post by KillerKelvUK on 2018-04-10
:-) glad you have this sorted!

Regards 2, in my experience linux makes no difference...avoid Windows based updates to bios, most/all vendors provide an update process from within the BIOS/UEFI itself which is OS agnostic.
And for 3...lol I just found this... [https://github.com/ghuntley/seaslic](https://github.com/ghuntley/seaslic) ...laughed out loud a little when I read the README

---

### Post by LastStarDust on 2018-04-10
You mistyped the link. Please correct it and let me laugh too!

---

### Post by KillerKelvUK on 2018-04-10
Done ;-)

---

### Post by LastStarDust on 2018-04-12
lol
Anyway, now I am trying to use the GUI "Virtual Machine Manager" (that I think is a wrapper around libvirt), but without success.
This is the working little script that I use to start qemu:
```
#!/bin/bash
qemu-system-x86_64 -enable-kvm -hda Windows10.qcow -m 4G -cpu host -smp 4 -vga std \
           -smbios type=1,manufacturer=LENOVO,product=***,version=ThinkPad\ X1\ Carbon\ 6th,\
serial=***,uuid=***,sku=LENOVO_MT_20KH_BU_Think_FM_ThinkPad\ X1\ Carbon\ 6th,family=ThinkPad\ X1\ Carbon\ 6th \
           -smbios type=0,vendor=LENOVO,version=N23ET38W\ \(1.13\ \),date=03/12/2018,release=1.13 \
           -acpitable file=/var/lib/libvirt/images/msdm.bin

```

This is part of the xml file that is edited with the command ```
virsh edit Windows10
```
```
<domain type='kvm' id='18' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
[...]
<qemu:commandline>
<qemu:arg value='-smbios'/>
<qemu:arg value='type=0,vendor=LENOVO,version=N23ET38W (1.13 ),date=03/12/2018,release=1.13'/>
<qemu:arg value='-smbios'/>
<qemu:arg value='type=1,manufacturer=LENOVO,product=***,version=ThinkPad X1 Carbon 6th,serial=***,uuid=***,sku=LENOVO_MT_20KH_BU_Think_FM_ThinkPad X1 Carbon 6th,family=ThinkPad X1 Carbon 6th'/>
<qemu:arg value='-acpitable'/>
<qemu:arg value='file=/var/lib/libvirt/images/msdm.bin'/>
</qemu:commandline>
```
When I try to start the VM I always get the error
```
qemu-system-x86_64: -acpitable file=/var/lib/libvirt/images/msdm.bin: can't open file /var/lib/libvirt/images/msdm.bin: Permission denied
```
I tried to change ownership and permissions of that file without any effect.
Do you know what could be the cause of the error?

---

### Post by KillerKelvUK on 2018-04-12
Sounds like an apparmor deny to me...any suspect entries in your 'dmesg' output?

---

### Post by LastStarDust on 2018-04-14
I think you are right. Here it is the dmesg output:
```
[ 4565.762739] kauditd_printk_skb: 13 callbacks suppressed[ 4565.762740] audit: type=1400 audit(1523688451.723:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-05337619-d4db-4025-a2cc-9cfd368214af" pid=6465 comm="apparmor_parser"
[ 4565.797660] virbr0: port 2(vnet0) entered blocking state
[ 4565.797662] virbr0: port 2(vnet0) entered disabled state
[ 4565.797708] device vnet0 entered promiscuous mode
[ 4565.798529] virbr0: port 2(vnet0) entered blocking state
[ 4565.798531] virbr0: port 2(vnet0) entered listening state
[ 4566.098018] audit: type=1400 audit(1523688452.058:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-05337619-d4db-4025-a2cc-9cfd368214af" pid=6498 comm="apparmor_parser"
[ 4566.141164] audit: type=1400 audit(1523688452.101:27): apparmor="DENIED" operation="open" profile="libvirt-05337619-d4db-4025-a2cc-9cfd368214af" name="/var/lib/libvirt/images/msdm.bin" pid=6512 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=64055 ouid=64055
[ 4566.142531] virbr0: port 2(vnet0) entered disabled state
[ 4566.144323] device vnet0 left promiscuous mode
[ 4566.144325] virbr0: port 2(vnet0) entered disabled state
[ 4566.536173] audit: type=1400 audit(1523688452.496:28): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-05337619-d4db-4025-a2cc-9cfd368214af" pid=6531 comm="apparmor_parser"

```

---

### Post by LastStarDust on 2018-04-14
I solved by following the answer to this question: [https://askubuntu.com/questions/741035/disabling-apparmor-for-kvm?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/741035/disabling-apparmor-for-kvm?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)
Thank you again KillerKelvUK!

---

### Post by LastStarDust on 2018-06-04
@KillerKelvUK
I have been using the Windows 10 virtual machine until now without problems.
Now I would like to update my Ubuntu install to 18.04. Do you think that it would be enough to just paste and copy the VM files and config to the new install or is it needed something more?
Thanks

---

### Post by sudodus on 2018-06-04
If you want a smooth ride, you should wait until the first point release, Ubuntu 18.04.1 LTS is released, late July or early August. By that time 18.04 will be debugged and polished. It might work now, but it is more risky to upgrade.

---

### Post by LastStarDust on 2018-06-04
> **sudodus said:**
> If you want a smooth ride, you should wait until the first point release, Ubuntu 18.04.1 LTS is released, late July or early August. By that time 18.04 will be debugged and polished. It might work now, but it is more risky to upgrade.
I definitely want a smooth ride. So I will wait until 18.04. Anyway, my question is still valid (just postponed).

---

### Post by sudodus on 2018-06-04
I use VirtualBox but I am no expert. Here are my two cents:

Usually you can port the VM files to a new version of Ubuntu. But if there is a (major) upgrade of VirtualBox, you may need some modifications. Anyway, the VDI files (the virtual disk files) should be possible to port.

---

### Post by LastStarDust on 2018-06-04
> **sudodus said:**
> I use VirtualBox but I am no expert. Here are my two cents:

Usually you can port the VM files to a new version of Ubuntu. But if there is a (major) upgrade of VirtualBox, you may need some modifications. Anyway, the VDI files (the virtual disk files) should be possible to port.
  I don't use VirtualBox. I use qemu/libvirt ...

---

### Post by sudodus on 2018-06-04
Sorry. Well, let us look for advice from someone who knows about qemu/libvirt :-)

---

### Post by KillerKelvUK on 2018-06-05
> **LastStarDust said:**
> @KillerKelvUK
I have been using the Windows 10 virtual machine until now without problems.
Now I would like to update my Ubuntu install to 18.04. Do you think that it would be enough to just paste and copy the VM files and config to the new install or is it needed something more?
Thanks

Hi, so if you are doing an upgrade (do-release-upgrade) on your host you shouldn't need to do anything for your guest vm's as all the configuration and files will remain as is.  If you intend to do a clean installation of 18.04.1 then you will need to backup vm storage backend and the guest xml config...

```

virsh dumpxmp *nameofguest* > nameofguest.xml

```

The above gets you a valid config backup, for the vm storage backend just copy the file somewhere safe and using a hash check pre/post to ensure the copy was successful (md5sum or sha256 etc) or using a copy process with inbuild has (rsync).

```

virsh define nameofguest.xml

```

Once you have a clean install the above will use the exported .xml config and create the guest again.  You just then need to edit the config to ensure its pointing at the correct storage backend file (virsh edit *nameofguest*).

---

### Post by LastStarDust on 2018-06-05
Thank you very much! again!

---

