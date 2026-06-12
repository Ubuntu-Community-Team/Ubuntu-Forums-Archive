---
title: "Issues with Win10 in virt-manager"
date: 2016-12-30
forum: Virtualisation
---

### Post by &amp;*@Fth&amp;% on 2016-12-30
**To start, the relevant hardware/software information:**[INDENT]-i5 4690k @ 4.2GHz, no hyperthreading, 3 out of 4 cores given to guest
[/INDENT]
[INDENT]-500GB SSD dedicated to host, 500GB HDD dedicated to guest (direct passthrough, no write caching)[/INDENT]
[INDENT]     -Intel HD graphics used for host, RX 480 passed directly through to guest[/INDENT]
[INDENT]     -16GB RAM on host, 8GB dedicated to guest
[/INDENT]
[INDENT]-VM is used for gaming, managed through virt-manager interface[/INDENT]
[INDENT]-Windows 10 x86_64 guest, Kubuntu 16.10 host[/INDENT]
[INDENT]-SPICE display[/INDENT]
[INDENT]-Realtek AC97 audio device, drivers installed by rebooting with driver signatures disabled[/INDENT]
[INDENT]-Emulated 16MB VGA card for the in-window display[/INDENT]
 
**The problems:**[INDENT]-_random hitching:_ for some reason, every so often, the entire guest OS locks up for a moment. Sometimes the audio keeps going, sometimes it cuts out, and sometimes it loops the last tiny bit (what I assume is some kind of buffer), but it depends on the game really. MSI Afterburner (I have the graphs going on the fake "monitor" within the virt-manager window, and the games running off a physical monitor connected directly to the RX 480) shows a massive spike in the frametime graph (going from the normal 10-20ms all the way up to 500+ms). There seems to be absolutely no connection between this and any hardware utilization; no spikes in CPU, HDD, RAM, or networking. This only seems to happen while the system is under load, though.
[/INDENT]
[INDENT]
-_ghost keys:_ I've tried 2 different keyboards: one USB, and the other PS/2 - it makes no difference. When walking around and I lift my finger off a movement key, the character keeps walking. Thankfully this one can be stopped by pressing the offending key. I even get random keypresses - the game might pause, open a character stat window, or melee attack without me even pressing the button at all. This happens on the mouse, too. Sometimes I'll release left click and my character keeps shooting, and the mouse sensor stops working entirely. I can't even look around. And even worse, unlike the keyboard ghost keys, I can't make it go away by pressing a button. The mouse completely stops working, and I just have to wait for it to sort itself out. Like the previous issue, this only happens under load.
[/INDENT]
[INDENT]
-_display:_ This is somewhat irrelevant to the previous two, but I might as well kill 2 birds with 1 stone, as the saying goes. Please note that I do not advocate killing birds with stones. Anyway, would it be possible to route the display output of the RX 480 into a window on the host? Remember this is used for gaming, so RDP has too much latency.
[/INDENT]

---

### Post by KillerKelvUK on 2016-12-31
Hey, please can you post back your guest xml config using virsh dumpxml *blahblah *(shout if this is new and you need more instructions).

Also need to know a little more about how you use your setup (the xml will help but try to be clear here)...burning question is whether you are using the virt-manager guest window to capture the keyboard and mouse inputs to control the guest?

As for wanting to get the guest display rendered on the host desktop without lag and usable for gaming...not going to happen.  You can get a perfectly functional remote desktop for non-gaming IMO using either SPICE or xRDP as others here have shown but gaming is just a no go.

Making some big assumptions which your reply will either validate or invalidate but at a guess with your setup having both a physical passthru GFX and emulated GFX you are causing a resource overhead in the guest which is why your "hitching" occurs.  A further guess is you did this to be able to get a SPICE remote desktop so you're keyboard and mouse could operate both host and guest without too much hassle, problem is this is causing the input lags and misses or "ghost keys" as you call them.

So big assumption based recommendations:  
[LIST=1]
[*]Remove the emulated GFX and SPICE display devices and use something like synergy to share your keyboard and mouse between host and guest ([https://symless.com/synergy/)]("https://symless.com/synergy/)...I") I use this for gaming all the time.
[LIST]
[*]If this works and you want to get really lazy and automate the switching of monitor inputs when you start/stop the guest then check if your monitor supports DDC/CI research libvirt hooks and [http://www.ddcutil.com/](http://www.ddcutil.com/) (think I put a post here a while ago but there are others too)
[/LIST]

[*]Apols if you've already considered this but if the monitor connected to the passed-thru GFX card has speakers and your RX480 has an audio chipset then pass through the HDMI audio device associated to the GFX card as well and ditch the emulated AC97 device.
[/LIST]

---

### Post by &amp;*@Fth&amp;% on 2016-12-31
Posted the output of "virsh dumpxml Win10" here: [http://pastebin.com/6rrJWek9](http://pastebin.com/6rrJWek9)

Synergy seems a bit pricey for such a small program, but if it's the only option, I guess I would have to...

I only have one monitor with speakers, and I'd rather not use them if I did because I'd annoy the others around the house, and the sound quality would be terrible anyway. Oddly enough, that monitor doesn't even accept audio over HDMI - I have to plug an aux cable into the back to get it to make any sound. I bet there are some HDMI dongles that separate the audio channel and allow it to be accessed through a standard 3.5mm audio jack, and combined with an audio combiner thingy (assuming they exist) that would work. But as the AC97 device is working fine, I really don't see a reason to set that all up.

Something I forgot to mention in my previous post was that I tried disabling transparent huge pages, and I think it made the hitching a little bit better, but I'm not really sure.

---

### Post by KillerKelvUK on 2016-12-31
Hey, just for future you can post the xml directly into the thread for easier reading/reference, just use CODE tags.

I paid for Synergy as I use it all the time, the price works out when you figure you can use it with lots of vm's and physical desktops but it is more a sysadmin tool repurposed for this need.  If you google around you should be able to grab a nightly build for testing/trial run without having to pay for something that you may fall out with.

Regards your sound then thats your call however the AC97 will undoubtedly glitch and the sound loops you refer to are symptoms to look out for.  There are tweaks I've seen but I'm not experienced with them as I just bought a decent sound card to pass through as well as GFX.

Regards using huge pages, performance improvements are what you should be seeing...never heard of the opposite with them so would suggest any issues are resulting from elsewhere i.e. as per the below.

Regards your XML you aren't using virtio for the disk and network adapters (why some many adapters anyways?), the Windows virtio drivers can be found @ [https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download) this will make a reasonable performance improvement as well as removing the emulated GFX and SPICE displays.

Last observation is to look at a Q35 chipset instead of the i440fx, all the garb says Q35 isn't as well tested however its more current and more seen, I personally haven't had any issues with it for quite sometime now *jinx*

EDIT:

Just caught it...you're passthough the entire HDD (sdb1) so virtio I don't think would apply here...risky move and you may have to look at this as a potential contributor to the issues at a later date.

---

### Post by &amp;*@Fth&amp;% on 2016-12-31
I don't think the sound is really a problem, as those issues seem to only occur while the guest is temporarily frozen. If we fix that, the sound issues should go away. I can't use a separate sound card, as I have an mITX board (only 1 PCIe slot, dedicated to the RX 480) 

So basically I should re-enable THP? I saw several posts on various forums stating that THP could be the cause of the stuttering, and I should disable it, but your explanation of the emulated GPU makes a lot more sense.

In regard to the 3 network adapters, I do realize that it is a bit silly, but virt-manager has 3 different devices the network adapters can connect to, and I didn't really know which one was best, so I used all of them. I assume there are 3 because there's one for each ethernet port on my motherboard and one for WiFi. I still can't seem to get the WiFi working, though.

I passed through the HDD figuring it would improve performance because Windows could write and read directly to/from it, without having to go through a translation layer. I don't really see why this would be risky - should I have the VM access a file from within the drive rather than the drive itself? This seems like a bit of a waste to me, as that would be the only file on the drive.

I don't see any way to change the chipset from within virt-manager. Should I edit the XML manually? Where would that file be located?

---

### Post by KillerKelvUK on 2016-12-31
Huge Pages should really be improving the overall performance of your guest...depending on how you've configured it.  I don't believe your problems would be affected by HP's tho so for now keep it simple and get what you have working properly and then reintroduce HP's so you can properly assess whether it has any negative impact.

Regards networking, that is always a tough nut to crack for the newly initiated and the configuration options vary depending on what you want to do i.e. wired or wireless, NAT vs bridging etc.  My suggestion is as per the HP, remove it all until you have a stable base and then reintroduce, we can work on networking as task.

Storage...so I get your logic and its not an unreasonable assumption however the guest isn't doing all the storage work simply because you've assigned it the entire disk i.e. the disk controller (what run's the sata port) is still connected to the host as you aren't passing that through (nor should you unless you have a very specific build in mind).  The risk is when you aren't running your windows VM...what happens when the host reads the partition table and maps in the drives available..blah blah.  Your chosen method has merits but also negatives i.e. its not very flexible as you can't move or expand the disk.  An alternative is to look at tier'ing your storage for performance gains.  I.e. separate your guest storage so that OS and game installs use a different disk, you could then put the OS part on your SSD so Windows itself would be faster, your slower HDD storage would then be available for the game installs.  You'd need to look into Logical Volumes (LVM) and how they would apply but this would give you flexibility to move and expand storage should you need to at a later date.  For reference using qcow2 images and virtio isn't going to give you native performance levels but the standards and protocols are designed to be as light weight as possible for performance reasons, hence using SSD tactically such for the OS I'd suggest you wouldn't notice/care about the performance lose vs the alternatives.

Regards changing the chipset to Q35, virt-manager doesn't provide this capability so its only possible by editing the guest XML by hand.  However this is like swapping out our motherboard for a different model and expecting Windows just to work through the change in hardware between boots...its risky.  I'd recommend you start with a clean installation to ensure its accomplished without error...see where a split OS vs everything else storage solution starts to make sense?  To change this by hand you'd alter the machine parameter in the OS tags of the XML, see below...

```

<os>
    <type arch='x86_64' machine='pc-i440fx-yakkety'>hvm</type>
    <boot dev='hd'/>
    <bootmenu enable='no'/>
  </os>

```

Doing this however will mean you also then need to change the device and bus references for all/most of the items under the 'device' xml tag further down, its all possible provided you either know what you're doing or are prepare to put the research and testing time in.

---

### Post by &amp;*@Fth&amp;% on 2016-12-31
What I *can* do is create a new virtual machine, set the chipset to Q35 which I can only do when making it, no afterwards (it says this is dangerous to do and difficult to switch back, but I assume you know what you're doing), add a 50GB drive for the OS (what's the best interface - IDE, SATA, SCSI, SD, USB, or VirtIO?), and add another drive (mapped to, say, G:\ in Windows (I don't know how the letters work)) that connects to the HDD, and tell Steam to install to the G drive.

What I get from what you're saying is that directly using the drive makes it annoying to move around the data, and since the drivers are both lightweight and there even if I give the guest "direct" access to the drive, so the performance gain of putting the guest on my SSD will far outweigh the loss of not having direct drive access.

As I understand, once I get Synergy I can remove the mouse, keyboard, SPICE channel, console, and emulated GFX devices from the VM, as Synergy will replace those?

And then the NICs. Basically what I want is if I connect the host to a network, ethernet or WiFi, it shows up like I plugged an ethernet cord into the guest, that lets it access whatever network the host is connected to. I assume that would be a bridge, not VEPA, private, or passthrough? And what device should I use - eno1, enp3s0, or wlp4s0?

---

### Post by KillerKelvUK on 2016-12-31
So yes on creating a new guest selecting Q35 as the best option.

50GB OS drive should be fine if you aren't looking to install much else there i.e. non-games etc.  Virtio is intended as the best bus type for virtual machines as it gives the most direct access to the hardware and thus is more performant so always use this where possible.  Yes you can then add back in the entire HDD as you have it as a second drive in the guest and there is a good hack to get steam to import already downloaded games, I do this myself and it works fine.

Regards the performance point yes I think you have it...using a qcow2 image on a decent SSD will give great results.  (Caveat, the more conversant you get with the technology and configuration options you may very well find better alternatives but for now I recommend you will find this a-okay!)

Synergy will provide you away to seamlessly use your keyboard and mouse on both your host and guest at the same time, check out the video on the site i linked for a clearer view of what you get.  The point is that its completely independent to virt-manager so you dont need to have all that other guff you have in there to get your K&M inputs sent to the guest.  NOTE: I don't think virt-manager will let you remove the basic keyboard and mouse devices, try but if they stay then meh its fine.

Networking...simplest way is to use NAT which is the base configuration virt-manager puts in...NAT means your guest "shares" the IP address of your host and provides the guest the ability to browse the web etc and I believe you should be able to connect to online game servers (although NAT does have some implications here but for now lets say its all peachy).  The downside here with NAT is that you cannot get into the guest from the network, so in my use case I have a guest running ubuntu server and that guest has several web applications that I want to be able to access from my home network i.e. from my laptop.  As NAT doesn't provide the guest with a unique IP address on the local network then I cannot access the web applications as I need a unique IP address to enter into my browser, if this is something you need then this is where a network Bridge comes into play.  A bridge effectively allows your guest to connect into your local network and obtain its own IP address from the DHCP server (likely running on your home router), however a network bridge is more complicated to set up.

---

### Post by &amp;*@Fth&amp;% on 2016-12-31
Well, it turns out that thebQ35 chipset does have problems. Spent the last 2 hours working on it, no dice. Anytime I had the guest set to use the Q35, the whole system would crash upon the installation of the AMD video drivers. I guess I'm using the i440FX. I'll post again once I have Synergy and a few games set up to test for hitching after removing the emulated GPU.

So I can't entirely remove the emulated GPU, or Windows won't boot, but I can remove the SPICE channel and console. Within Windows, I set it to use the real monitor exclusively. Hopefully the emulated GPU won't cause too many problems with its head cut off. If the type of emulated GFX matters, I am currently using Cirrus, but there's also QXL, VGA, VMVGA, and Xen.

I got the network working with only one NIC by creating a virtual network using NAT on IPv4 and routed networking on IPv6 (this is what it set when I told it to use NAT). I have yet to test it with the physical machine connected to WiFi, but it's working so far.

One of these things is not like the other...

[IMG]https://ibin.co/37JP2aubjPrZ.png[/IMG]

---

### Post by KillerKelvUK on 2017-01-01
> **superrobowizard said:**
> So I can't entirely remove the emulated GPU, or Windows won't boot, but I can remove the SPICE channel and console. Within Windows, I set it to use the real monitor exclusively. Hopefully the emulated GPU won't cause too many problems with its head cut off. If the type of emulated GFX matters, I am currently using Cirrus, but there's also QXL, VGA, VMVGA, and Xen.

I got the network working with only one NIC by creating a virtual network using NAT on IPv4 and routed networking on IPv6 (this is what it set when I told it to use NAT). I have yet to test it with the physical machine connected to WiFi, but it's working so far.

Happy new year :-)

You can't boot without the emulated GPU = bad!  Can you explain...are you getting display output on the monitor connected to the passthru GFX or just within virt-manager?

Regards you're problems with Q35 that sounds very odd, I'm running Windows 10 with a Q35 chipset with no issues however granted my passthru is nvidia.

Have you confirmed the GFX devices are being caught by the VFIO-PCI driver at boot and not by their native hardware driver?  Can you post back the result of "lspci -vs [I]insert-your-correct-slot-number-here"

[/I]Also what other module settings are you applying on host boot i.e. have you modified any files or created new file under /etc/modprobe.d/ for example to ignore msrs errors?

---

### Post by KillerKelvUK on 2017-01-01
Regards the memory usage graph, if I recall I think that is typical behaviour without hugepages.  Also have you installed the baloon driver in Windows?  I'd wager that Windows is reporting a lower memory utilisation but with a bunch of memory allocated to reserve, meaning its just grabbing what it can see which qemu reports as usage.

---

### Post by &amp;*@Fth&amp;% on 2017-01-01
With the emulated GPU completely removed, I start the virtual machine, and after 5 minutes there is still no display on the monitor connected to the dGPU, where it normally takes under a minute. I've set within Windows for it to use display 2 exclusively, so hopefully that disables the emulated GFX?

I can boot fine in a VM using the i440FX chipset, but in an **identical** v, except using Q35, the system boots up fine, but then the AMD driver config window pops up, immediately crashes, and then the entire system bluescreens. This can only be seen when using the emulated GFX connected to SPICE, though, as it doesn't even get to the point of initializing the RX 480.

lspci -vs 0000:01:00.0:
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] (rev c7) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Ellesmere [Radeon RX 480]
    Flags: fast devsel, IRQ 16
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=2M]
    I/O ports at e000 [size=256]
    Memory at f7e00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f7e40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: amdgpu

```

I haven't modified /etc/modprobe.d, but I have added a modprobe.blacklist to the GRUB config to keep the AMD driver from grabbing the GPU. Seeing as it works fine with the i440FX on identical settings, I really don't think that's the problem.

What's the balloon driver? I've never heard of it.

Also, Synergy seems to have problems. Even if I enable the relative movement setting, my in-game character spins uncontrollably at the slightest touch of my mouse. Apparently this bug is more than 4 years old, and the developers haven't fixed it, and are constantly jacking up the price of the software. For me, this is a huge issue, meaning the only way for me to realistically control my games is to use Steam in-home streaming, which even at the lowest video settings eats network bandwidth and uses a not-insignificant amount of GPU horsepower for the real-time encoding and decoding of video. If I could completely disable video and audio that would be okay, but I doubt that is even possible. Even if it was, it would be quite inconvenient, and still wouldn't let me play Blizzard games (because our special little snowflake needs his own special little game launcher, even if it's much worse than the one everyone else uses).

---

### Post by KillerKelvUK on 2017-01-01
So I don't have time now to go into detail but you've missed a pretty core part of the setup for a successful GFX passthru, the summary for now is you need to be ensuring the vfio drivers are being loaded on boot, adding a couple of module options to allow for some expanded vm capabilities and ensuring your gfx hardware is being grabbed by the VFIO-PCI module on host boot.  There is an explanation as to why you have a partial working solution but it will be unstable and not as per recommendations unless you address the other issues.

Baloon driver:  Look under Device Manager in Windows...you will probably have an 'Unknown Device' or two unless you've manually removed them from your guest config but the baloon driver enables windows to dynamically alter its memory allocation within the range you configured for the guest.

As for Synergy...when you move the cursor onto the guest desktop hit the scroll lock key on your keyboard, this will lock your keyboard and mouse to the virtual desktop until you press scroll lock again.  This is how you stop the uncontrollable spinning.

---

### Post by &amp;*@Fth&amp;% on 2017-01-01
"Got the balloon drivers installed now.
Thanks for the tip on synergy, it works great now.

So basically it's bad that when the VM isn't running my RX 480 is just sitting there, not attached to any drivers? Is this why I need the emulated GFX to get Windows to boot?
I found [https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#Isolating_the_GPU](https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#Isolating_the_GPU), but it wants me to "add" stuff to config files I don't already have, and then run "mkinitcpio" which responds with a command not found error.

Thank you for helping me so far. I'm just wandering around in a dark room constantly falling over, and I understand it takes a lot of your time to help me back up each time. I realize you're donating your effort to me with no expectation of return other than gratitude, but that is all I can offer you. I apologise for my never-ending stream of user errors and problems.

---

### Post by KillerKelvUK on 2017-01-01
Right I'm back...my better half wanted to go out for a meal hence I was short on time...nice meal tho ;-)

No need to apologies for asking for assistance, thats the point of this forum and we all help each other out here best we can.

So there are plenty of guides about as you linked but you need to recognise what the guide is based on i.e. your link took you to the Arch Linux forum, those guys have done some pretty solid work getting passthrough up and running so its a great source of info but you need to recognise that Arch Linux and Ubuntu Linux are slightly different beasts, some things need to be translated into Ubuntu commands and some things are just specific to Arch or Ubuntu and don't apply elsewhere.

[tl;dr] So the steps you need to go through are...

[LIST=1]
[*]Adding the IOMMU kernel boot parameters into grub (possible you might already have this sorted)
[*]Ensuring the VFIO modules are being loaded on host boot
[*]Applying some optional parameters to selected modules on the host.  This can make the host more tolerant to what the guest tries to do and can stop a full host lockup/reboot as an example.
[*]You need to get the host to load the VFIO-PCI module/driver so that it claims you passthru hardware before radeon/amdgpu driver.
[*](Optional) If your host is booting with UEFI and your RX480 is UEFI capable you may have to look at using OVMF instead of the legacy Seabios currently being applied.
[/LIST]

For the avoidance of doubt, when editing a file I do this via a terminal and use nano as the editor, basically I type "sudo nano /etc/default/grub"  as an example (without the quote marks). So for all of the below I'm assuming that's what you're going to do also, if you have you're own preferred way that does the same well peachy, that's why linux is awesome.
[B]
Ensuring IOMMU is fully enabled[/B]

Simply put you need to ensure you have 'intel_iommu=on' in your grub config.  Edit the _/etc/default/grub_ file and on the line starting "GRUB_CMDLINE_LINUX_DEFAULT=" added the aforementioned kernel parameter so you file looks similar to the following...

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on intremap=no_x2apic_optout"
GRUB_CMDLINE_LINUX=""

```

Its okay if yours has different content as long as you add the 'intel_iommu=on' parameter into that line.  As the file says at the start you need to run a final command to commit these changes so do a "sudo update-grub" to commit them.

The purpose of this change is to ensure IOMMU is turned on and that all your PCI devices are separated out into their own IOMMU group, without this passthrough won't ever work.  You can check whether its been successful by running the script I've attached to this post (iommu.sh), just save this file to your home directory, make sure its executable by "sudo chmod u+x iommu.sh" and then run it "./iommu.sh" and you should get some output similar to this...

```

### Group 1 ###
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
    01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)
    01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)

```

This is only an small excerpt of my output but yours will be a lot longer I suspect, just post the output back here once you have it.  NOTE: Its okay to have a bridge device listed in the same group as your passthru device (as mine has above) but you DO NOT assign this device to the guest leave it well alone.


**Loading the VFIO modules**


So assuming everything is good with IOMMU the next step is simply editing the file _/etc/modules_ and add in 4 new lines at the end (its possible your file is blank apart from the first few commented-out lines).

```

vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd

```

Its possible this step is more a hygiene factor as basically its just making sure these modules/drivers are loaded at boot, I'm not sure but its possible that later kernel versions may do this automatically as a default behaviour, but ensuring they are loaded this way doesn't hurt.

Once you've changed the file you need to commit the changes similar to the grub update, do this with "sudo update-initramfs -u".  After a reboot you can use the 'lsmod' command to list all loaded modules/drivers and you should find them in that output.  No need to post that back just confirm they're their.


**Adding the optional module parameters**

So with this one we're going to create a new file located in the /etc/modprobe.d/ directory.  I called mine "virt-config.conf", what you call it is your choice but it needs to end with the .conf for it to be considered at boot.  So to create the file just go to edit it as though it already existed i.e. "sudo nano /etc/modprobe.d/virt-config.conf" and add in the below lines...

```

options kvm_intel nested=1
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1

```

The first line is the more optional as it allows for nested virtualisation which effectively is allowing a virtual machine to run inside a virtual machine so if you wanted to install virtual box inside your Windows guest you could and it would run just not very fast!  The second line is the one providing the main benefit as it is modifying the KVM module to make it more tolerant to MSRS errors and unsafe interrupts which the guest can generate and what can cause host and guest crashes.

Once you created the file again you need to commit the changes with a "sudo update-initramfs -u" and reboot.  You can verify that the above has worked by looking in the /sys/ tree for the modules and listing the contents of the parameters e.g. "cat /sys/module/kvm/parameters/ignore_msrs" and you should get a "Y" as the output. 


**Loading VFIO-PCI first to ensure it claims your passthru GFX**

This one gets a little trickier as its specific to your hardware and how you want to use it.  Start off with listing your PCI devices in terminal with this specific command "lspci -nn", you'll get something back like the following excerpt...

```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 970] _**[10de:13c2]**_ (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GM204 High Definition Audio Controller _**[10de:0fbb]**_ (rev a1)

```

So the above shows my GTX 970 which is what I pass through to my Windows guest.  The -nn part of the commend used ensures the output incorporates the Vendor and Device ID's for the hardware in each line, these are the letters and numbers in [square brackets] at the end of each line e.g. the [10de:13c2] and [10de:0fbb].  You need to find these ID's for your GFX card as we need to add them into the file created in the previous step, the one you created in the /etc/modprobe.d/ directory, so go ahead an edit that file again and put the following lines at the end...

```

options vfio-pci ids=xxx  *(put your ID's here without the square brackets and if adding more that one device i.e. the audio part of the GFX then comma separate them e.g. 10de:13c2,10de:0fbb)*
softdep radeon pre: vfio-pci
softdep amdgpu pre: vfio-pci

```

So like before once you've amended this file you need to commit the changes with "sudo update-initramfs -u" and reboot.

This is a pretty important step as its basically telling the VFIO-PCI module/driver that it should be looking for a device with the ID's you've specified.  As such when the module is loaded by the host it will claim those devices as its own and ideally it does this before any other module claims them e.g. the native driver for that GFX card.  This is important as its the VFIO-PCI drivers job to mediate passthrough of the physical device to the qemu virtual machine that you are running Windows within.  The 2nd and 3rd lines you added are in an attempt to get VFIO-PCI their first as in some configurations the native device module/driver loads that quickly it claims the GFX device for itself which prevents passthrough.  Basically softdep is saying make VFIO-PCI a dependency for loading the radeon (legacy AMD driver) and/or amdgpu (current AMD driver) drivers aka load VFIO-PCI before you load radeon or amdgpu.

To confirm whether VFIO-PCI has claimed the device as needed you run the same command is you did in a prev post here "lspci -vs 0000:01:00.0" and what you're looking for is shown below...

```

01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. GM204 [GeForce GTX 970]
    Flags: fast devsel, IRQ 16
    Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at ef000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci    [COLOR=#ff0000]**<---THIS IS WHAT YOU NEED**[/COLOR]
    Kernel modules: nvidiafb, nouveau


01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. GM204 High Definition Audio Controller
    Flags: fast devsel, IRQ 17
    Memory at ef080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci   [COLOR=#ff0000]**<---THIS IS WHAT YOU NEED**[/COLOR]
    Kernel modules: snd_hda_intel

```

If this didnt work and the native GFX drivers are shown as in use (don't believe you have this issue based on your previous post) then this is where you may need to blacklist that module/driver to stop it loading.  You can either do that as a kernel parameter pass via GRUB or by adding a line into /etc/blacklist.conf.  I'll not go into detail on this as I think you are sorted for this.


Okay so stopping here, a bit for you to work through here so let us know how you're getting on and we can then review whether the next step with OVMF is needed.

---

### Post by &amp;*@Fth&amp;% on 2017-01-01
This response will be partially to inform you of what I did, and partially to help me keep track of that as well since I'm rebooting a lot.

I already had IOMMU enabled, but I ran the script anyway in case it provides any useful information:
```

### Group 7 ###
    00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
### Group 15 ###
    04:00.0 Network controller: Intel Corporation Wireless 7260 (rev bb)
### Group 5 ###
    00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
### Group 13 ###
    00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
    00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
    00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
### Group 3 ###
    00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
### Group 11 ###
    00:1c.4 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 (rev d0)
### Group 1 ###
    01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aaf0
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
    01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] (rev c7)
### Group 8 ###
    00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
### Group 6 ###
    00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V
### Group 14 ###
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
### Group 4 ###
    00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
### Group 12 ###
    00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
### Group 2 ###
    00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
### Group 10 ###
    00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
### Group 0 ###
    00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
### Group 9 ###
    00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)

```
All I have assigned to the guest here is the RX 480 and it's HDMI audio.

I had to add the VFIO modules to the almost-empty file (just comments). I'm pretty sure they were already being loaded, since it was sort of working, but just in case.

Added the virt-config. What you said makes sense because early iterations of my VM configuration would make my entire system crash or freeze when I started them.

Appending to the virt-config. As the soft-dep makes the modprobe.blacklist=amdgpu in my /etc/default/grub, I removed it.

Yay, that worked!

My /etc/default/grub looks like this:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_THEME=/boot/grub/themes/Grau/theme.txt

```

And my virt-config.conf looks like this:
```

options kvm_intel nested=1
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio-pci ids=1002:67df,1002:aaf0
softdep radeon pre: vfio-pci
softdep amdgpu pre: vfio-pci

```

---

### Post by &amp;*@Fth&amp;% on 2017-01-01
Still won't boot without the emulated GFX, but I assume that will be fixed in later steps.

---

### Post by KillerKelvUK on 2017-01-02
> Appending to the virt-config. As the soft-dep makes the modprobe.blacklist=amdgpu in my /etc/default/grub, I removed it.

Hey so have you confirmed the lspci -vs output and that the kernel driver in use for both devices is vfio-pci?
 
If so and all is as per the steps then the next activity would be to strip your guest config to the bare minimum ensuring no emulated gfx and spice displays etc and collect clean logs, before we make any leap to OVMF we need to make sure nothing else is blocking passthrough.

---

### Post by &amp;*@Fth&amp;% on 2017-01-02
lspci -vs 0000:01:00.:
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] (rev c7) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Ellesmere [Radeon RX 480]
    Flags: fast devsel, IRQ 11
    Memory at e0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [disabled] [size=2M]
    I/O ports at e000 [disabled] [size=256]
    Memory at f7e00000 (32-bit, non-prefetchable) [disabled] [size=256K]
    Expansion ROM at f7e40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci
    Kernel modules: amdgpu

```

Looks fine to me, it says it's using the VFIO driver.
I cloned the VM, so that if I accidentally remove something critical and break everything it won't be breaking the real one.

According to the devices on virt-manager, all I have is:
-3 of my 4 cores allocated
-8GB of my 16gb RAM
-a 40GB SATA disk for the OS
-a 100GB VirtIO disk for games
-one NIC
-a mouse & keyboard (can't be removed, and reportedly removing them manually causes problems)
-an AC97 sound card
-my GPU and HDMI audio passthrough
-an emulated Cirrus GFX card, Windows won't boot without it
-PCI, SATA, and USB 3 controllers

When booting without the Cirrus video card, I also noticed that the CPU usage graph after a moment gets stuck at 33%, and never wavers from that line - seems like it's waiting for something, or stuck in a loop.

---

### Post by KillerKelvUK on 2017-01-02
Okay so all good now, lets grab a couple of logs and then decide whether switching to OVMF will be worthwhile.  Basically we know the guest won't boot but it would be useful to see what the host is saying when the guest is trying to boot.  To do this properly please remove the emulated Cirrus gfx device and any spice/vnc device as well as the AC97 audio, lets get the guest as simple as we can for now.  Once you've done this start the guest and take a note of the exact time if you can to the second and then forget about your virtual machine as we're only interested in what your host is saying.

So on the host open a terminal, wait about 60 seconds and then run the following commands, then from the results just post back the outputs from the time you started the guest until then end of the output...

```

dmesg -T

cat /var/log/syslog

cat /var/log/libvirt/qemu/name-of-your-guest.log

```

The last check isn't to do with your guest but please can you paste the following into a terminal and confirm whether the command returns UEFI or BIOS...

```

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

```


**EDIT:  Please can you confirm if you're still using the i440fx chipset or the Q35...may need you to test both and gather these logs.**

---

### Post by &amp;*@Fth&amp;% on 2017-01-02
The command says I'm using BIOS, which is odd because my motherboard has a UEFI configuration interface.
I also put them on pastebin so you can see them in a bigger window.


dmesg -t ([http://pastebin.com/9BJiqCG2](http://pastebin.com/9BJiqCG2)):
```

microcode: microcode updated early to revision 0x20, date = 2016-03-16
Linux  version 4.8.0-32-generic (buildd@lcy01-34) (gcc version 6.2.0 20161005  (Ubuntu 6.2.0-5ubuntu12) ) #34-Ubuntu SMP Tue Dec 13 14:30:43 UTC 2016  (Ubuntu 4.8.0-32.34-generic 4.8.11)
Command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-32-generic root=UUID=4d1ab9e9-ad28-4acf-b90b-6ced8fb25634 ro quiet intel_iommu=on
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
  Centaur CentaurHauls
x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
x86/fpu: Using 'eager' FPU context switches.
e820: BIOS-provided physical RAM map:
BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
BIOS-e820: [mem 0x0000000000100000-0x00000000a619cfff] usable
BIOS-e820: [mem 0x00000000a619d000-0x00000000a61a3fff] ACPI NVS
BIOS-e820: [mem 0x00000000a61a4000-0x00000000a6c29fff] usable
BIOS-e820: [mem 0x00000000a6c2a000-0x00000000a7105fff] reserved
BIOS-e820: [mem 0x00000000a7106000-0x00000000c798efff] usable
BIOS-e820: [mem 0x00000000c798f000-0x00000000c7ccefff] reserved
BIOS-e820: [mem 0x00000000c7ccf000-0x00000000c7d35fff] usable
BIOS-e820: [mem 0x00000000c7d36000-0x00000000c7e74fff] ACPI NVS
BIOS-e820: [mem 0x00000000c7e75000-0x00000000c9ffefff] reserved
BIOS-e820: [mem 0x00000000c9fff000-0x00000000c9ffffff] usable
BIOS-e820: [mem 0x00000000cb000000-0x00000000cf1fffff] reserved
BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
BIOS-e820: [mem 0x0000000100000000-0x000000042fdfffff] usable
NX (Execute Disable) protection: active
SMBIOS 2.7 present.
DMI: Gigabyte Technology Co., Ltd. Z97N-WIFI/Z97N-WIFI, BIOS F7 09/18/2015
e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
e820: remove [mem 0x000a0000-0x000fffff] usable
e820: last_pfn = 0x42fe00 max_arch_pfn = 0x400000000
MTRR default type: uncachable
MTRR fixed ranges enabled:
  00000-9FFFF write-back
  A0000-BFFFF uncachable
  C0000-CFFFF write-protect
  D0000-E7FFF uncachable
  E8000-FFFFF write-protect
MTRR variable ranges enabled:
  0 base 0000000000 mask 7C00000000 write-back
  1 base 0400000000 mask 7FE0000000 write-back
  2 base 0420000000 mask 7FF0000000 write-back
  3 base 00E0000000 mask 7FE0000000 uncachable
  4 base 00D0000000 mask 7FF0000000 uncachable
  5 base 00CC000000 mask 7FFC000000 uncachable
  6 base 00CB000000 mask 7FFF000000 uncachable
  7 base 042FE00000 mask 7FFFE00000 uncachable
  8 disabled
  9 disabled
x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
total RAM covered: 16302M
 gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 62M
 gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 62M
 gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 62M
 gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 62M
 gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 62M
 gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 62M
 gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 0G
 gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 0G
 gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
 gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
 gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
 gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
 gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
 gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
 gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 62M
 gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 62M
 gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 62M
 gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 62M
 gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 62M
 gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 0G
 gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 0G
 gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
 gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
 gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
 gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
 gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
 gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
 gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 62M
 gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 62M
 gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 62M
 gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 62M
 gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 0G
 gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 0G
 gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
 gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
 gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
 gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
 gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
 gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
 gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 62M
 gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 62M
 gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 62M
 gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 0G
 gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 0G
 gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
 gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
 gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
 gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
 gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
 gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
 gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 62M
 gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 62M
 gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 0G
 gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 0G
 gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
 gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
 gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
 gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
 gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
 gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
 gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 62M
 gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 0G
 gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 0G
 gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
 gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
 gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
 gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
 gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
 gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
*BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
 gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 62M
 gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
 gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 2M
 gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: 2M
 gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: 2M
 gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: 2M
 gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: 2M
*BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -254M
 gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: 2M
*BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1022M
 gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 62M
 gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 6M
 gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 6M
 gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 6M
 gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: 6M
 gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: 6M
*BAD*gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: -250M
 gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: 6M
*BAD*gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1018M
 gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 62M
 gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 14M
 gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 14M
 gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: 14M
 gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: 14M
*BAD*gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: -242M
 gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: 14M
*BAD*gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1010M
 gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 46M
 gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: 46M
 gran_size: 32M     chunk_size: 128M     num_reg: 10      lose cover RAM: 46M
 gran_size: 32M     chunk_size: 256M     num_reg: 10      lose cover RAM: 46M
*BAD*gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: -210M
 gran_size: 32M     chunk_size: 1G     num_reg: 10      lose cover RAM: 46M
*BAD*gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: -978M
 gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 110M
 gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 110M
 gran_size: 64M     chunk_size: 256M     num_reg: 9      lose cover RAM: 110M
 gran_size: 64M     chunk_size: 512M     num_reg: 10      lose cover RAM: 110M
 gran_size: 64M     chunk_size: 1G     num_reg: 9      lose cover RAM: 110M
 gran_size: 64M     chunk_size: 2G     num_reg: 10      lose cover RAM: 110M
 gran_size: 128M     chunk_size: 128M     num_reg: 7      lose cover RAM: 174M
 gran_size: 128M     chunk_size: 256M     num_reg: 9      lose cover RAM: 174M
 gran_size: 128M     chunk_size: 512M     num_reg: 10      lose cover RAM: 174M
 gran_size: 128M     chunk_size: 1G     num_reg: 9      lose cover RAM: 174M
 gran_size: 128M     chunk_size: 2G     num_reg: 10      lose cover RAM: 174M
 gran_size: 256M     chunk_size: 256M     num_reg: 5      lose cover RAM: 430M
 gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 430M
 gran_size: 256M     chunk_size: 1G     num_reg: 6      lose cover RAM: 430M
 gran_size: 256M     chunk_size: 2G     num_reg: 7      lose cover RAM: 430M
 gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 430M
 gran_size: 512M     chunk_size: 1G     num_reg: 6      lose cover RAM: 430M
 gran_size: 512M     chunk_size: 2G     num_reg: 7      lose cover RAM: 430M
 gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 942M
 gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 942M
 gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1966M
mtrr_cleanup: can not find optimal value
please specify mtrr_gran_size/mtrr_chunk_size
e820: update [mem 0xcb000000-0xffffffff] usable ==> reserved
e820: last_pfn = 0xca000 max_arch_pfn = 0x400000000
found SMP MP-table at [mem 0x000fd740-0x000fd74f] mapped at [ffff994c400fd740]
Scanning 1 areas for low memory corruption
Base memory trampoline at [ffff994c40097000] 97000 size 24576
Using GB pages for direct mapping
BRK [0x336233000, 0x336233fff] PGTABLE
BRK [0x336234000, 0x336234fff] PGTABLE
BRK [0x336235000, 0x336235fff] PGTABLE
BRK [0x336236000, 0x336236fff] PGTABLE
BRK [0x336237000, 0x336237fff] PGTABLE
BRK [0x336238000, 0x336238fff] PGTABLE
BRK [0x336239000, 0x336239fff] PGTABLE
BRK [0x33623a000, 0x33623afff] PGTABLE
BRK [0x33623b000, 0x33623bfff] PGTABLE
BRK [0x33623c000, 0x33623cfff] PGTABLE
BRK [0x33623d000, 0x33623dfff] PGTABLE
BRK [0x33623e000, 0x33623efff] PGTABLE
RAMDISK: [mem 0x32f36000-0x35792fff]
ACPI: Early table checksum verification disabled
ACPI: RSDP 0x00000000000F0490 000024 (v02 ALASKA)
ACPI: XSDT 0x00000000C7E3A080 00007C (v01 ALASKA A M I    01072009 AMI  00010013)
ACPI: FACP 0x00000000C7E4A6C8 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
ACPI: DSDT 0x00000000C7E3A190 010538 (v02 ALASKA A M I    00000088 INTL 20120711)
ACPI: FACS 0x00000000C7E73080 000040
ACPI: APIC 0x00000000C7E4A7D8 000072 (v03 ALASKA A M I    01072009 AMI  00010013)
ACPI: FPDT 0x00000000C7E4A850 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
ACPI: SSDT 0x00000000C7E4A898 000BEE (v01 Ther_R Ther_Rvp 00001000 INTL 20120711)
ACPI: SSDT 0x00000000C7E4B488 000539 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
ACPI: SSDT 0x00000000C7E4B9C8 000B74 (v01 CpuRef CpuSsdt  00003000 INTL 20051117)
ACPI: MCFG 0x00000000C7E4C540 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
ACPI: HPET 0x00000000C7E4C580 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
ACPI: SSDT 0x00000000C7E4C5B8 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
ACPI: SSDT 0x00000000C7E4C928 005B5E (v01 SaSsdt SaSsdt   00003000 INTL 20120711)
ACPI: DMAR 0x00000000C7E52488 0000B8 (v01 INTEL  BDW      00000001 INTL 00000001)
ACPI: Local APIC address 0xfee00000
No NUMA configuration found
Faking a node at [mem 0x0000000000000000-0x000000042fdfffff]
NODE_DATA(0) allocated [mem 0x42fdfa000-0x42fdfefff]
Zone ranges:
  DMA      [mem 0x0000000000001000-0x0000000000ffffff]
  DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
  Normal   [mem 0x0000000100000000-0x000000042fdfffff]
  Device   empty
Movable zone start for each node
Early memory node ranges
  node   0: [mem 0x0000000000001000-0x000000000009cfff]
  node   0: [mem 0x0000000000100000-0x00000000a619cfff]
  node   0: [mem 0x00000000a61a4000-0x00000000a6c29fff]
  node   0: [mem 0x00000000a7106000-0x00000000c798efff]
  node   0: [mem 0x00000000c7ccf000-0x00000000c7d35fff]
  node   0: [mem 0x00000000c9fff000-0x00000000c9ffffff]
  node   0: [mem 0x0000000100000000-0x000000042fdfffff]
Initmem setup node 0 [mem 0x0000000000001000-0x000000042fdfffff]
On node 0 totalpages: 4158128
  DMA zone: 64 pages used for memmap
  DMA zone: 21 pages reserved
  DMA zone: 3996 pages, LIFO batch:0
  DMA32 zone: 12693 pages used for memmap
  DMA32 zone: 812308 pages, LIFO batch:31
  Normal zone: 52216 pages used for memmap
  Normal zone: 3341824 pages, LIFO batch:31
Reserving Intel graphics memory at 0x00000000cb200000-0x00000000cf1fffff
ACPI: PM-Timer IO Port: 0x1808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ9 used by override.
Using ACPI (MADT) for SMP configuration information
ACPI: HPET id: 0x8086a701 base: 0xfed00000
smpboot: Allowing 4 CPUs, 0 hotplug CPUs
PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
PM: Registered nosave memory: [mem 0xa619d000-0xa61a3fff]
PM: Registered nosave memory: [mem 0xa6c2a000-0xa7105fff]
PM: Registered nosave memory: [mem 0xc798f000-0xc7ccefff]
PM: Registered nosave memory: [mem 0xc7d36000-0xc7e74fff]
PM: Registered nosave memory: [mem 0xc7e75000-0xc9ffefff]
PM: Registered nosave memory: [mem 0xca000000-0xcaffffff]
PM: Registered nosave memory: [mem 0xcb000000-0xcf1fffff]
PM: Registered nosave memory: [mem 0xcf200000-0xf7ffffff]
PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
e820: [mem 0xcf200000-0xf7ffffff] available for PCI devices
Booting paravirtualized kernel on bare hardware
clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
percpu: Embedded 36 pages/cpu @ffff99506fa00000 s107544 r8192 d31720 u524288
pcpu-alloc: s107544 r8192 d31720 u524288 alloc=1*2097152
pcpu-alloc: [0] 0 1 2 3 
Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4093134
Policy zone: Normal
Kernel  command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-32-generic  root=UUID=4d1ab9e9-ad28-4acf-b90b-6ced8fb25634 ro quiet intel_iommu=on
DMAR: IOMMU enabled
PID hash table entries: 4096 (order: 3, 32768 bytes)
Calgary: detecting Calgary via BIOS EBDA area
Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Memory:  16243364K/16632512K available (8832K kernel code, 1432K rwdata, 3808K  rodata, 1548K init, 1272K bss, 389148K reserved, 0K cma-reserved)
SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Hierarchical RCU implementation.
    Build-time adjustment of leaf fanout to 64.
    RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
NR_IRQS:16640 nr_irqs:456 16
Console: colour dummy device 80x25
console [tty0] enabled
clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
hpet clockevent registered
tsc: Fast TSC calibration using PIT
tsc: Detected 3500.014 MHz processor
Calibrating delay loop (skipped), value calculated using timer frequency.. 7000.02 BogoMIPS (lpj=14000056)
pid_max: default: 32768 minimum: 301
ACPI: Core revision 20160422
ACPI: 6 ACPI AML tables successfully acquired and loaded

Security Framework initialized
Yama: becoming mindful.
AppArmor: AppArmor initialized
Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
mce: CPU supports 9 MCE banks
CPU0: Thermal monitoring enabled (TM1)
process: using mwait in idle threads
Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
Freeing SMP alternatives memory: 32K (ffffffffb06eb000 - ffffffffb06f3000)
ftrace: allocating 33382 entries in 131 pages
smpboot: APIC(0) Converting physical 0 to logical package 0
smpboot: Max logical packages: 1
DMAR: Host address width 39
DMAR: DRHD base: 0x000000fed90000 flags: 0x0
DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
DMAR: DRHD base: 0x000000fed91000 flags: 0x1
DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
DMAR: RMRR base: 0x000000c9e7e000 end: 0x000000c9e8cfff
DMAR: RMRR base: 0x000000cb000000 end: 0x000000cf1fffff
DMAR-IR: IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
DMAR-IR: HPET id 0 under DRHD base 0xfed91000
DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
DMAR-IR: Enabled IRQ remapping in xapic mode
x2apic: IRQ remapping doesn't support X2APIC mode
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
TSC deadline timer enabled
smpboot: CPU0: Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz (family: 0x6, model: 0x3c, stepping: 0x3)
Performance Events: PEBS fmt2+, Haswell events, 16-deep LBR, full-width counters, Intel PMU driver.
... version:                3
... bit width:              48
... generic registers:      8
... value mask:             0000ffffffffffff
... max period:             0000ffffffffffff
... fixed-purpose events:   3
... event mask:             00000007000000ff
NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
x86: Booting SMP configuration:
.... node  #0, CPUs:      #1 #2 #3
x86: Booted up 1 node, 4 CPUs
smpboot: Total of 4 processors activated (28000.11 BogoMIPS)
devtmpfs: initialized
x86/mm: Memory block size: 128MB
evm: security.selinux
evm: security.SMACK64
evm: security.SMACK64EXEC
evm: security.SMACK64TRANSMUTE
evm: security.SMACK64MMAP
evm: security.ima
evm: security.capability
PM: Registering ACPI NVS region [mem 0xa619d000-0xa61a3fff] (28672 bytes)
PM: Registering ACPI NVS region [mem 0xc7d36000-0xc7e74fff] (1306624 bytes)
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
pinctrl core: initialized pinctrl subsystem
RTC time: 18:56:36, date: 01/02/17
NET: Registered protocol family 16
cpuidle: using governor ladder
cpuidle: using governor menu
PCCT header not found.
ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
ACPI: bus type PCI registered
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
pmd_set_huge: Cannot satisfy [mem 0xf8000000-0xf8200000] with a huge-page mapping due to MTRR override.
PCI: Using configuration type 1 for base access
core: PMU erratum BJ122, BV98, HSD29 workaround disabled, HT off
NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
HugeTLB registered 1 GB page size, pre-allocated 0 pages
HugeTLB registered 2 MB page size, pre-allocated 0 pages
ACPI: Added _OSI(Module Device)
ACPI: Added _OSI(Processor Device)
ACPI: Added _OSI(3.0 _SCP Extensions)
ACPI: Added _OSI(Processor Aggregator Device)
ACPI: Executed 15 blocks of module-level executable AML code
ACPI: Dynamic OEM Table Load:
ACPI: SSDT 0xFFFF99505CD43C00 0003D3 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT 0xFFFF99505D31A000 0005AA (v01 PmRef  ApIst    00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT 0xFFFF99505CD1A200 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
ACPI: Power Resource [PG00] (on)
ACPI: Power Resource [PG01] (on)
ACPI: Power Resource [PG02] (on)
ACPI: Power Resource [FN00] (off)
ACPI: Power Resource [FN01] (off)
ACPI: Power Resource [FN02] (off)
ACPI: Power Resource [FN03] (off)
ACPI: Power Resource [FN04] (off)
ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
PCI host bridge to bus 0000:00
pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
pci_bus 0000:00: root bus resource [mem 0xcf200000-0xfeafffff window]
pci_bus 0000:00: root bus resource [bus 00-3e]
pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
pci 0000:00:01.0: System wakeup disabled by ACPI
pci 0000:00:02.0: [8086:0412] type 00 class 0x030000
pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
pci 0000:00:03.0: reg 0x10: [mem 0xf7f34000-0xf7f37fff 64bit]
pci 0000:00:14.0: [8086:8cb1] type 00 class 0x0c0330
pci 0000:00:14.0: reg 0x10: [mem 0xf7f20000-0xf7f2ffff 64bit]
pci 0000:00:14.0: PME# supported from D3hot D3cold
pci 0000:00:14.0: System wakeup disabled by ACPI
pci 0000:00:16.0: [8086:8cba] type 00 class 0x078000
pci 0000:00:16.0: reg 0x10: [mem 0xf7f3d000-0xf7f3d00f 64bit]
pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
pci 0000:00:19.0: [8086:153b] type 00 class 0x020000
pci 0000:00:19.0: reg 0x10: [mem 0xf7f00000-0xf7f1ffff]
pci 0000:00:19.0: reg 0x14: [mem 0xf7f3c000-0xf7f3cfff]
pci 0000:00:19.0: reg 0x18: [io  0xf080-0xf09f]
pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
pci 0000:00:19.0: System wakeup disabled by ACPI
pci 0000:00:1a.0: [8086:8cad] type 00 class 0x0c0320
pci 0000:00:1a.0: reg 0x10: [mem 0xf7f3b000-0xf7f3b3ff]
pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1a.0: System wakeup disabled by ACPI
pci 0000:00:1b.0: [8086:8ca0] type 00 class 0x040300
pci 0000:00:1b.0: reg 0x10: [mem 0xf7f30000-0xf7f33fff 64bit]
pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1b.0: System wakeup disabled by ACPI
pci 0000:00:1c.0: [8086:8c90] type 01 class 0x060400
pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.0: Enabling MPC IRBNCE
pci 0000:00:1c.0: Intel PCH root port ACS workaround enabled
pci 0000:00:1c.0: System wakeup disabled by ACPI
pci 0000:00:1c.3: [8086:8c96] type 01 class 0x060400
pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.3: Enabling MPC IRBNCE
pci 0000:00:1c.3: Intel PCH root port ACS workaround enabled
pci 0000:00:1c.3: System wakeup disabled by ACPI
pci 0000:00:1c.4: [8086:8c98] type 01 class 0x060400
pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.4: Enabling MPC IRBNCE
pci 0000:00:1c.4: Intel PCH root port ACS workaround enabled
pci 0000:00:1c.4: System wakeup disabled by ACPI
pci 0000:00:1d.0: [8086:8ca6] type 00 class 0x0c0320
pci 0000:00:1d.0: reg 0x10: [mem 0xf7f3a000-0xf7f3a3ff]
pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1d.0: System wakeup disabled by ACPI
pci 0000:00:1f.0: [8086:8cc4] type 00 class 0x060100
pci 0000:00:1f.2: [8086:8c82] type 00 class 0x010601
pci 0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7]
pci 0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3]
pci 0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7]
pci 0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3]
pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
pci 0000:00:1f.2: reg 0x24: [mem 0xf7f39000-0xf7f397ff]
pci 0000:00:1f.2: PME# supported from D3hot
pci 0000:00:1f.3: [8086:8ca2] type 00 class 0x0c0500
pci 0000:00:1f.3: reg 0x10: [mem 0xf7f38000-0xf7f380ff 64bit]
pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
pci 0000:01:00.0: [1002:67df] type 00 class 0x030000
pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
pci 0000:01:00.0: reg 0x18: [mem 0xf0000000-0xf01fffff 64bit pref]
pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
pci 0000:01:00.0: reg 0x24: [mem 0xf7e00000-0xf7e3ffff]
pci 0000:01:00.0: reg 0x30: [mem 0xf7e40000-0xf7e5ffff pref]
pci 0000:01:00.0: supports D1 D2
pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
pci 0000:01:00.0: System wakeup disabled by ACPI
pci 0000:01:00.1: [1002:aaf0] type 00 class 0x040300
pci 0000:01:00.1: reg 0x10: [mem 0xf7e60000-0xf7e63fff 64bit]
pci 0000:01:00.1: supports D1 D2
pci 0000:00:01.0: PCI bridge to [bus 01]
pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf01fffff 64bit pref]
acpiphp: Slot [1] registered
pci 0000:00:1c.0: PCI bridge to [bus 02]
pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
pci 0000:03:00.0: reg 0x10: [io  0xd000-0xd0ff]
pci 0000:03:00.0: reg 0x18: [mem 0xf7d00000-0xf7d00fff 64bit]
pci 0000:03:00.0: reg 0x20: [mem 0xf0300000-0xf0303fff 64bit pref]
pci 0000:03:00.0: supports D1 D2
pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:03:00.0: System wakeup disabled by ACPI
pci 0000:00:1c.3: PCI bridge to [bus 03]
pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
pci 0000:00:1c.3:   bridge window [mem 0xf0300000-0xf03fffff 64bit pref]
pci 0000:04:00.0: [8086:08b1] type 00 class 0x028000
pci 0000:04:00.0: reg 0x10: [mem 0xf7c00000-0xf7c01fff 64bit]
pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
pci 0000:04:00.0: System wakeup disabled by ACPI
pci 0000:00:1c.4: PCI bridge to [bus 04]
pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
ACPI: PCI Interrupt Link [LNKA] (IRQs 4 6 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 4 6 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 4 6 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 4 6 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 4 6 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 4 6 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 4 6 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 4 6 *10 11 12 14 15)
ACPI: Enabled 5 GPEs in block 00 to 3F
SCSI subsystem initialized
libata version 3.00 loaded.
vgaarb: setting as boot device: PCI:0000:00:02.0
vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
vgaarb: loaded
vgaarb: bridge control possible 0000:01:00.0
vgaarb: no bridge control possible 0000:00:02.0
ACPI: bus type USB registered
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: pci_cache_line_size set to 64 bytes
e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
e820: reserve RAM buffer [mem 0xa619d000-0xa7ffffff]
e820: reserve RAM buffer [mem 0xa6c2a000-0xa7ffffff]
e820: reserve RAM buffer [mem 0xc798f000-0xc7ffffff]
e820: reserve RAM buffer [mem 0xc7d36000-0xc7ffffff]
e820: reserve RAM buffer [mem 0xca000000-0xcbffffff]
e820: reserve RAM buffer [mem 0x42fe00000-0x42fffffff]
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
hpet0: 8 comparators, 64-bit 14.318180 MHz counter
clocksource: Switched to clocksource hpet
VFS: Disk quotas dquot_6.6.0
VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
AppArmor: AppArmor Filesystem Enabled
pnp: PnP ACPI init
system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
system 00:01: [io  0x0800-0x087f] has been reserved
system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
system 00:03: [io  0x1854-0x1857] has been reserved
system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
system 00:04: [io  0x0a00-0x0a0f] has been reserved
system 00:04: [io  0x0a30-0x0a3f] has been reserved
system 00:04: [io  0x0a20-0x0a2f] has been reserved
system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:05: [dma 0 disabled]
pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
system 00:06: [io  0x04d0-0x04d1] has been reserved
system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
system 00:07: [mem 0xf8000000-0xfbffffff] has been reserved
system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
system 00:07: [mem 0xfed90000-0xfed93fff] could not be reserved
system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
system 00:07: [mem 0xff000000-0xffffffff] has been reserved
system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
system 00:07: [mem 0xf7fe0000-0xf7feffff] has been reserved
system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp: PnP ACPI: found 8 devices
clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
pci 0000:00:01.0: PCI bridge to [bus 01]
pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf01fffff 64bit pref]
pci 0000:00:1c.0: PCI bridge to [bus 02]
pci 0000:00:1c.3: PCI bridge to [bus 03]
pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
pci 0000:00:1c.3:   bridge window [mem 0xf0300000-0xf03fffff 64bit pref]
pci 0000:00:1c.4: PCI bridge to [bus 04]
pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff window]
pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff window]
pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff window]
pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff window]
pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff window]
pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff window]
pci_bus 0000:00: resource 13 [mem 0xcf200000-0xfeafffff window]
pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
pci_bus 0000:01: resource 1 [mem 0xf7e00000-0xf7efffff]
pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf01fffff 64bit pref]
pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
pci_bus 0000:03: resource 1 [mem 0xf7d00000-0xf7dfffff]
pci_bus 0000:03: resource 2 [mem 0xf0300000-0xf03fffff 64bit pref]
pci_bus 0000:04: resource 1 [mem 0xf7c00000-0xf7cfffff]
NET: Registered protocol family 2
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
UDP hash table entries: 8192 (order: 6, 262144 bytes)
UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
NET: Registered protocol family 1
pci 0000:00:02.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
PCI: CLS 64 bytes, default 64
Trying to unpack rootfs image as initramfs...
Freeing initrd memory: 41332K (ffff994c72f36000 - ffff994c75793000)
DMAR: No ATSR found
DMAR: dmar0: Using Queued invalidation
DMAR: dmar1: Using Queued invalidation
DMAR: Setting RMRR:
DMAR: Setting identity map for device 0000:00:02.0 [0xcb000000 - 0xcf1fffff]
DMAR: Setting identity map for device 0000:00:14.0 [0xc9e7e000 - 0xc9e8cfff]
DMAR: Setting identity map for device 0000:00:1a.0 [0xc9e7e000 - 0xc9e8cfff]
DMAR: Setting identity map for device 0000:00:1d.0 [0xc9e7e000 - 0xc9e8cfff]
DMAR: Prepare 0-16MiB unity mapping for LPC
DMAR: Setting identity map for device 0000:00:1f.0 [0x0 - 0xffffff]
DMAR: Intel(R) Virtualization Technology for Directed I/O
iommu: Adding device 0000:00:00.0 to group 0
iommu: Adding device 0000:00:01.0 to group 1
iommu: Adding device 0000:00:02.0 to group 2
iommu: Adding device 0000:00:03.0 to group 3
iommu: Adding device 0000:00:14.0 to group 4
iommu: Adding device 0000:00:16.0 to group 5
iommu: Adding device 0000:00:19.0 to group 6
iommu: Adding device 0000:00:1a.0 to group 7
iommu: Adding device 0000:00:1b.0 to group 8
iommu: Adding device 0000:00:1c.0 to group 9
iommu: Adding device 0000:00:1c.3 to group 10
iommu: Adding device 0000:00:1c.4 to group 11
iommu: Adding device 0000:00:1d.0 to group 12
iommu: Adding device 0000:00:1f.0 to group 13
iommu: Adding device 0000:00:1f.2 to group 13
iommu: Adding device 0000:00:1f.3 to group 13
iommu: Adding device 0000:01:00.0 to group 1
iommu: Adding device 0000:01:00.1 to group 1
iommu: Adding device 0000:03:00.0 to group 14
iommu: Adding device 0000:04:00.0 to group 15
Scanning for low memory corruption every 60 seconds
futex hash table entries: 1024 (order: 4, 65536 bytes)
audit: initializing netlink subsys (disabled)
audit: type=2000 audit(1483383395.576:1): initialized
Initialise system trusted keyrings
workingset: timestamp_bits=40 max_order=22 bucket_order=0
zbud: loaded
squashfs: version 4.0 (2009/01/31) Phillip Lougher
fuse init (API version 7.25)
Allocating IMA blacklist keyring.
Key type asymmetric registered
Asymmetric key parser 'x509' registered
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 248)
io scheduler noop registered
io scheduler deadline registered (default)
io scheduler cfq registered
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
vesafb: mode is 1920x1080x32, linelength=7680, pages=0
vesafb: scrolling: redraw
vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
vesafb: framebuffer at 0xd0000000, mapped to 0xffffad1b02000000, using 8128k, total 8128k
Console: switching to colour frame buffer device 240x67
fb0: VESA VGA frame buffer device
intel_idle: MWAIT substates: 0x42120
intel_idle: v0.4.1 model 0x3C
intel_idle: lapic_timer_reliable_states 0xffffffff
input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
ACPI: Power Button [PWRB]
input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
ACPI: Sleep Button [SLPB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
ACPI: Power Button [PWRF]
thermal LNXTHERM:00: registered as thermal_zone0
ACPI: Thermal Zone [TZ00] (28 C)
thermal LNXTHERM:01: registered as thermal_zone1
ACPI: Thermal Zone [TZ01] (30 C)
GHES: HEST is not enabled!
Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Linux agpgart interface v0.103
brd: module loaded
loop: module loaded
libphy: Fixed MDIO Bus: probed
tun: Universal TUN/TAP device driver, 1.6
tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
PPP generic driver version 2.4.2
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci-pci: EHCI PCI platform driver
ehci-pci 0000:00:1a.0: EHCI Host Controller
ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
ehci-pci 0000:00:1a.0: debug port 2
ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f3b000
ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: EHCI Host Controller
usb usb1: Manufacturer: Linux 4.8.0-32-generic ehci_hcd
usb usb1: SerialNumber: 0000:00:1a.0
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ehci-pci 0000:00:1d.0: EHCI Host Controller
ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
ehci-pci 0000:00:1d.0: debug port 2
ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7f3a000
ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: EHCI Host Controller
usb usb2: Manufacturer: Linux 4.8.0-32-generic ehci_hcd
usb usb2: SerialNumber: 0000:00:1d.0
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ehci-platform: EHCI generic platform driver
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
ohci-pci: OHCI PCI platform driver
ohci-platform: OHCI generic platform driver
uhci_hcd: USB Universal Host Controller Interface driver
xhci_hcd 0000:00:14.0: xHCI Host Controller
xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb3: Product: xHCI Host Controller
usb usb3: Manufacturer: Linux 4.8.0-32-generic xhci-hcd
usb usb3: SerialNumber: 0000:00:14.0
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 14 ports detected
xhci_hcd 0000:00:14.0: xHCI Host Controller
xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb4: Product: xHCI Host Controller
usb usb4: Manufacturer: Linux 4.8.0-32-generic xhci-hcd
usb usb4: SerialNumber: 0000:00:14.0
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
i8042: PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mousedev: PS/2 mouse device common for all mice
rtc_cmos 00:02: RTC can wake from S4
rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
i2c /dev entries driver
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.35.0-ioctl (2016-06-23) initialised: dm-devel@redhat.com
intel_pstate: Intel P-state driver initializing
ledtrig-cpu: registered to indicate activity on CPUs
NET: Registered protocol family 10
NET: Registered protocol family 17
Key type dns_resolver registered
microcode: sig=0x306c3, pf=0x2, revision=0x20
microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
registered taskstats version 1
Loading compiled-in X.509 certificates
Loaded X.509 cert 'Build time autogenerated kernel key: 561085e7eab87c8fbd50a57ab586969dd0c1bc66'
zswap: loaded using pool lzo/zbud
Key type big_key registered
Key type trusted registered
Key type encrypted registered
AppArmor: AppArmor sha1 policy hashing enabled
ima: No TPM chip found, activating TPM-bypass!
evm: HMAC attrs: 0x1
  Magic number: 1:917:947
tty tty4: hash matches
processor cpu2: hash matches
memory memory0: hash matches
rtc_cmos 00:02: setting system clock to 2017-01-02 18:56:36 UTC (1483383396)
BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available.
PM: Hibernation image not present or could not be loaded.
Freeing unused kernel memory: 1548K (ffffffffb0568000 - ffffffffb06eb000)
Write protecting the kernel read-only data: 14336k
Freeing unused kernel memory: 1392K (ffff994f758a4000 - ffff994f75a00000)
Freeing unused kernel memory: 288K (ffff994f75db8000 - ffff994f75e00000)
x86/mm: Checked W+X mappings: passed, no W+X pages found.
random: systemd-udevd: uninitialized urandom read (16 bytes read)
random: systemd-udevd: uninitialized urandom read (16 bytes read)
random: systemd-udevd: uninitialized urandom read (16 bytes read)
random: systemd-udevd: uninitialized urandom read (16 bytes read)
random: udevadm: uninitialized urandom read (16 bytes read)
random: udevadm: uninitialized urandom read (16 bytes read)
random: udevadm: uninitialized urandom read (16 bytes read)
random: udevadm: uninitialized urandom read (16 bytes read)
random: udevadm: uninitialized urandom read (16 bytes read)
random: udevadm: uninitialized urandom read (16 bytes read)
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
hidraw: raw HID events driver (C) Jiri Kosina
FUJITSU Extended Socket Network Device Driver - version 1.1 - Copyright (c) 2015 FUJITSU LIMITED
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
PTP clock support registered
[drm] Initialized drm 1.1.0 20060810
e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
VFIO - User Level meta-driver version: 0.3
r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=io+mem:owns=none
r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffad1b01b96000, 40:8d:5c:bd:03:e2, XID 0c000800 IRQ 29
r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
r8169 0000:03:00.0 enp3s0: renamed from eth0
vfio_pci: add [1002:67df[ffff:ffff]] class 0x000000/00000000
vfio_pci: add [1002:aaf0[ffff:ffff]] class 0x000000/00000000
[drm] amdgpu kernel modesetting enabled.
e1000e 0000:00:19.0 0000:00:19.0 (uninitialized): registered PHC clock
e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 40:8d:5c:bd:03:e4
e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
ahci 0000:00:1f.2: version 3.0
ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x2 impl SATA mode
ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
e1000e 0000:00:19.0 eno1: renamed from eth0
scsi host0: ahci
scsi host1: ahci
scsi host2: ahci
scsi host3: ahci
scsi host4: ahci
scsi host5: ahci
ata1: DUMMY
ata2: SATA max UDMA/133 abar m2048@0xf7f39000 port 0xf7f39180 irq 30
ata3: DUMMY
ata4: DUMMY
ata5: DUMMY
ata6: DUMMY
[drm] DMAR active, disabling use of stolen memory
[drm] Memory usable by graphics device = 2048M
[drm] VT-d active for gfx access
checking generic (d0000000 7f0000) vs hw (d0000000 10000000)
fb: switching to inteldrmfb from VESA VGA
Console: switching to colour dummy device 80x25
[drm] Replacing VGA console driver
[drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[drm] Driver supports precise vblank timestamp query.
vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=io+mem:owns=none
vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
acpi device:16: registered as cooling_device9
input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[drm] Initialized i915 1.6.0 20160711 for 0000:00:02.0 on minor 0
fbcon: inteldrmfb (fb0) is primary device
usb 1-1: new high-speed USB device number 2 using ehci-pci
Console: switching to colour frame buffer device 240x67
usb 2-1: new high-speed USB device number 2 using ehci-pci
usb 3-3: new high-speed USB device number 2 using xhci_hcd
i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
usb 1-1: New USB device found, idVendor=8087, idProduct=8009
usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 6 ports detected
usb 3-3: New USB device found, idVendor=1004, idProduct=626c
usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 3-3: Product: LGE Android Phone
usb 3-3: Manufacturer: LG Electronics Inc.
usb 3-3: SerialNumber: VS9854Gde6a4e5
usb-storage 3-3:1.0: USB Mass Storage device detected
scsi host6: usb-storage 3-3:1.0
usbcore: registered new interface driver usb-storage
usbcore: registered new interface driver uas
usb 2-1: New USB device found, idVendor=8087, idProduct=8001
usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
hub 2-1:1.0: USB hub found
hub 2-1:1.0: 8 ports detected
ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
ata2.00: ATA-8: TRO-SSD7-500GB-PRO, 580ABBF0, max UDMA/133
ata2.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
ata2.00: configured for UDMA/133
scsi 1:0:0:0: Direct-Access     ATA      TRO-SSD7-500GB-P BBF0 PQ: 0 ANSI: 5
usb 3-7: new full-speed USB device number 3 using xhci_hcd
sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/466 GiB)
sd 1:0:0:0: Attached scsi generic sg0 type 0
sd 1:0:0:0: [sda] Write Protect is off
sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 < sda5 >
sd 1:0:0:0: [sda] Attached SCSI disk
random: fast init done
EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
usb 3-7: New USB device found, idVendor=1ea7, idProduct=0066
usb 3-7: New USB device strings: Mfr=0, Product=1, SerialNumber=0
usb 3-7: Product: 2.4G Wireless Mouse&Keyboard
tsc: Refined TSC clocksource calibration: 3499.996 MHz
clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x32734d20948, max_idle_ns: 440795306379 ns
ip_tables: (C) 2000-2006 Netfilter Core Team
systemd[1]:  systemd 231 running in system mode. (+PAM +AUDIT +SELINUX +IMA  +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ  -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD +IDN)
systemd[1]: Detected architecture x86-64.
systemd[1]: Set hostname to <Bens-PC>.
usb 3-8: new full-speed USB device number 4 using xhci_hcd
systemd[1]: Listening on Journal Audit Socket.
systemd[1]: Started Forward Password Requests to Wall Directory Watch.
systemd[1]: Listening on Device-mapper event daemon FIFOs.
systemd[1]: Reached target User and Group Name Lookups.
systemd[1]: Created slice System Slice.
systemd[1]: Listening on udev Control Socket.
systemd[1]: Listening on LVM2 metadata daemon socket.
lp: driver loaded but no devices found
ppdev: user-space parallel port driver
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
systemd-journald[333]: Received request to flush runtime journal from PID 1
usb 3-8: New USB device found, idVendor=25a7, idProduct=2433
usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 3-8: Product: 2.4G Wireless Device
usb 3-8: Manufacturer: 2.4G
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
snd_hda_codec_realtek hdaudioC1D2: autoconfig for ALC892: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
snd_hda_codec_realtek hdaudioC1D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
snd_hda_codec_realtek hdaudioC1D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
snd_hda_codec_realtek hdaudioC1D2:    mono: mono_out=0x0
snd_hda_codec_realtek hdaudioC1D2:    dig-out=0x11/0x1e
snd_hda_codec_realtek hdaudioC1D2:    inputs:
snd_hda_codec_realtek hdaudioC1D2:      Front Mic=0x19
snd_hda_codec_realtek hdaudioC1D2:      Rear Mic=0x18
snd_hda_codec_realtek hdaudioC1D2:      Line=0x1a
RAPL PMU: API unit is 2^-32 Joules, 4 fixed counters, 655360 ms ovfl timer
RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
RAPL PMU: hw unit of domain package 2^-14 Joules
RAPL PMU: hw unit of domain dram 2^-14 Joules
RAPL PMU: hw unit of domain pp1-gpu 2^-14 Joules
input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
AVX2 version of gcm_enc/dec engaged.
AES CTR mode by8 optimization enabled
input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input16
Intel(R) Wireless WiFi driver for Linux
Copyright(c) 2003- 2015 Intel Corporation
iwlwifi 0000:04:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
iwlwifi 0000:04:00.0: L1 Disabled - LTR Enabled
iwlwifi 0000:04:00.0: L1 Disabled - LTR Enabled
usb 3-10: new full-speed USB device number 5 using xhci_hcd
intel_rapl: Found RAPL domain package
intel_rapl: Found RAPL domain core
intel_rapl: Found RAPL domain uncore
intel_rapl: Found RAPL domain dram
audit:  type=1400 audit(1483383397.664:2): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="/usr/lib/libvirt/virt-aa-helper" pid=675 comm="apparmor_parser"
audit:  type=1400 audit(1483383397.664:3): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="/sbin/dhclient"  pid=673 comm="apparmor_parser"
audit: type=1400  audit(1483383397.664:4): apparmor="STATUS" operation="profile_load"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673  comm="apparmor_parser"
audit: type=1400 audit(1483383397.664:5):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=673  comm="apparmor_parser"
audit: type=1400 audit(1483383397.664:6):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="/usr/lib/connman/scripts/dhclient-script" pid=673  comm="apparmor_parser"
audit: type=1400 audit(1483383397.664:7):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="/usr/lib/snapd/snap-confine" pid=676 comm="apparmor_parser"
audit:  type=1400 audit(1483383397.664:8): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper"  pid=676 comm="apparmor_parser"
audit: type=1400  audit(1483383397.664:9): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/sbin/cups-browsed" pid=678  comm="apparmor_parser"
audit: type=1400 audit(1483383397.664:10):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="/usr/sbin/ippusbxd" pid=680 comm="apparmor_parser"
Adding 16630780k swap on /dev/sda5.  Priority:-1 extents:1 across:16630780k SSFS
usb 3-10: New USB device found, idVendor=04d9, idProduct=a06a
usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 3-10: Product: USB Gaming Keyboard
usb 3-10: Manufacturer: E-Signal
ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
usb 3-11: new full-speed USB device number 6 using xhci_hcd
scsi 6:0:0:0: CD-ROM            LGE      Android Platform 0000 PQ: 0 ANSI: 2
sr 6:0:0:0: [sr0] scsi-1 drive
cdrom: Uniform CD-ROM driver Revision: 3.20
sr 6:0:0:0: Attached scsi CD-ROM sr0
sr 6:0:0:0: Attached scsi generic sg1 type 5
usb 3-11: New USB device found, idVendor=8087, idProduct=07dc
usb 3-11: New USB device strings: Mfr=0, Product=0, SerialNumber=0
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
input: 2.4G Wireless Mouse&Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:1EA7:0066.0001/input/input17
Bluetooth: Core ver 2.21
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
usbcore: registered new interface driver btusb
Bluetooth: hci0: read Intel version: 3707100180012d0d00
Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Bluetooth: BNEP socket layer initialized
hid-generic  0003:1EA7:0066.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G  Wireless Mouse&Keyboard] on usb-0000:00:14.0-7/input0
input: 2.4G Wireless Mouse&Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.1/0003:1EA7:0066.0002/input/input18
IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
hid-generic  0003:1EA7:0066.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [2.4G  Wireless Mouse&Keyboard] on usb-0000:00:14.0-7/input1
input: 2.4G 2.4G Wireless Device as /devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/0003:25A7:2433.0003/input/input19
Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
r8169 0000:03:00.0 enp3s0: link down
IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
iwlwifi 0000:04:00.0: L1 Disabled - LTR Enabled
iwlwifi 0000:04:00.0: L1 Disabled - LTR Enabled
hid-generic 0003:25A7:2433.0003: input,hidraw2: USB HID v1.01 Keyboard [2.4G 2.4G Wireless Device] on usb-0000:00:14.0-8/input0
input: 2.4G 2.4G Wireless Device as /devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.1/0003:25A7:2433.0004/input/input20
clocksource: Switched to clocksource tsc
hid-generic  0003:25A7:2433.0004: input,hiddev0,hidraw3: USB HID v1.01 Mouse [2.4G  2.4G Wireless Device] on usb-0000:00:14.0-8/input1
input: E-Signal USB Gaming Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/0003:04D9:A06A.0005/input/input21
hid-generic  0003:04D9:A06A.0005: input,hidraw4: USB HID v1.10 Keyboard [E-Signal  USB Gaming Keyboard] on usb-0000:00:14.0-10/input0
input: E-Signal USB Gaming Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.1/0003:04D9:A06A.0006/input/input22
hid-generic  0003:04D9:A06A.0006: input,hiddev0,hidraw5: USB HID v1.10 Device  [E-Signal USB Gaming Keyboard] on usb-0000:00:14.0-10/input1
iwlwifi 0000:04:00.0: L1 Disabled - LTR Enabled
iwlwifi 0000:04:00.0: L1 Disabled - LTR Enabled
IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
ip6_tables: (C) 2000-2006 Netfilter Core Team
Ebtables v2.0 registered
bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
virbr0: port 1(virbr0-nic) entered blocking state
virbr0: port 1(virbr0-nic) entered disabled state
device virbr0-nic entered promiscuous mode
nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
virbr0: port 1(virbr0-nic) entered blocking state
virbr0: port 1(virbr0-nic) entered listening state
IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
ISO 9660 Extensions: Microsoft Joliet Level 1
ISO 9660 Extensions: IEEE_P1282
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
virbr0: port 1(virbr0-nic) entered learning state
virbr0: port 1(virbr0-nic) entered forwarding state
virbr0: topology change detected, propagating
IPv6: ADDRCONF(NETDEV_CHANGE): virbr0: link becomes ready
virbr0: port 1(virbr0-nic) entered disabled state
device virbr0-nic left promiscuous mode
virbr0: port 1(virbr0-nic) entered disabled state
wlp4s0: authenticate with 00:26:62:68:36:ed
wlp4s0: send auth to 00:26:62:68:36:ed (try 1/3)
wlp4s0: authenticated
iwlwifi 0000:04:00.0 wlp4s0: disabling HT/VHT due to WEP/TKIP use
wlp4s0: associate with 00:26:62:68:36:ed (try 1/3)
wlp4s0: RX AssocResp from 00:26:62:68:36:ed (capab=0x431 status=0 aid=2)
wlp4s0: associated
IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
Guest personality initialized and is inactive
VMCI host device registered (name=vmci, major=10, minor=55)
Initialized host personality
NET: Registered protocol family 40
systemd[1]: apt-daily.timer: Adding 24min 31.976921s random time.
systemd[1]: apt-daily.timer: Adding 4h 13min 32.531807s random time.
usb 3-3: USB disconnect, device number 2
usb 3-3: new high-speed USB device number 7 using xhci_hcd
usb 3-3: new high-speed USB device number 8 using xhci_hcd
usb 3-3: New USB device found, idVendor=1004, idProduct=62c9
usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 3-3: Product: LGE Android Phone
usb 3-3: Manufacturer: LG Electronics Inc.
usb 3-3: SerialNumber: VS9854Gde6a4e5
random: crng init done
audit_printk_skb: 36 callbacks suppressed
audit:  type=1400 audit(1483384144.392:23): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="libvirt-57664241-ddeb-427f-823b-47ed8070a197" pid=2585  comm="apparmor_parser"
audit: type=1400 audit(1483384144.392:24):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="libvirt-57664241-ddeb-427f-823b-47ed8070a197//qemu_bridge_helper"  pid=2585 comm="apparmor_parser"
virbr0: port 1(vnet0) entered blocking state
virbr0: port 1(vnet0) entered disabled state
device vnet0 entered promiscuous mode
virbr0: port 1(vnet0) entered blocking state
virbr0: port 1(vnet0) entered listening state
systemd[1]: apt-daily.timer: Adding 10h 50min 2.495950s random time.
audit:  type=1400 audit(1483384144.656:25): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="libvirt-57664241-ddeb-427f-823b-47ed8070a197" pid=2624  comm="apparmor_parser"
audit: type=1400 audit(1483384144.672:26):  apparmor="STATUS" operation="profile_replace" profile="unconfined"  name="libvirt-57664241-ddeb-427f-823b-47ed8070a197//qemu_bridge_helper"  pid=2624 comm="apparmor_parser"
audit: type=1400  audit(1483384144.760:27): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2688/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
audit:  type=1400 audit(1483384144.764:28): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2689/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
audit:  type=1400 audit(1483384144.768:29): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2690/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
audit:  type=1400 audit(1483384144.784:30): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2692/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
vfio-pci 0000:01:00.0: enabling device (0000 -> 0003)
vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x270
vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1b@0x2d0
vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1e@0x370
virbr0: port 1(vnet0) entered learning state
virbr0: port 1(vnet0) entered forwarding state
virbr0: topology change detected, propagating

```



syslog ([http://pastebin.com/FFg9ViDL](http://pastebin.com/FFg9ViDL)):
```

Jan  2 14:09:01 Bens-PC CRON[2535]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Jan  2 14:09:04 Bens-PC kernel: [  748.074117] audit_printk_skb: 36 callbacks suppressed
Jan   2 14:09:04 Bens-PC kernel: [  748.074117] audit: type=1400  audit(1483384144.392:23): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  pid=2585 comm="apparmor_parser"
Jan  2 14:09:04 Bens-PC kernel: [   748.074270] audit: type=1400 audit(1483384144.392:24):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="libvirt-57664241-ddeb-427f-823b-47ed8070a197//qemu_bridge_helper"  pid=2585 comm="apparmor_parser"
Jan  2 14:09:04 Bens-PC systemd[1]: Started Virtual machine log manager.
Jan   2 14:09:04 Bens-PC NetworkManager[886]: <info>   [1483384144.4300] manager: (vnet0): new Tun device  (/org/freedesktop/NetworkManager/Devices/6)
Jan  2 14:09:04 Bens-PC  NetworkManager[886]: <info>  [1483384144.4338] devices added  (path: /sys/devices/virtual/net/vnet0, iface: vnet0)
Jan  2 14:09:04  Bens-PC NetworkManager[886]: <info>  [1483384144.4338] device  added (path: /sys/devices/virtual/net/vnet0, iface: vnet0): no ifupdown  configuration found.
Jan  2 14:09:04 Bens-PC kernel: [  748.169037] virbr0: port 1(vnet0) entered blocking state
Jan  2 14:09:04 Bens-PC kernel: [  748.169039] virbr0: port 1(vnet0) entered disabled state
Jan  2 14:09:04 Bens-PC kernel: [  748.169104] device vnet0 entered promiscuous mode
Jan   2 14:09:04 Bens-PC NetworkManager[886]: <info>   [1483384144.5067] device (vnet0): state change: unmanaged ->  unavailable (reason 'connection-assumed') [10 20 41]
Jan  2 14:09:04  Bens-PC NetworkManager[886]: <info>  [1483384144.5073] keyfile:  add connection in-memory (85e3ebd0-c570-4544-bec0-f15fc42caf3b,"vnet0")
Jan   2 14:09:04 Bens-PC NetworkManager[886]: <info>   [1483384144.5076] device (vnet0): state change: unavailable ->  disconnected (reason 'connection-assumed') [20 30 41]
Jan  2 14:09:04  Bens-PC NetworkManager[886]: <info>  [1483384144.5080] device  (vnet0): Activation: starting connection 'vnet0'  (85e3ebd0-c570-4544-bec0-f15fc42caf3b)
Jan  2 14:09:04 Bens-PC kernel: [  748.185101] virbr0: port 1(vnet0) entered blocking state
Jan  2 14:09:04 Bens-PC kernel: [  748.185102] virbr0: port 1(vnet0) entered listening state
Jan   2 14:09:04 Bens-PC NetworkManager[886]: <info>   [1483384144.5102] device (vnet0): state change: disconnected ->  prepare (reason 'none') [30 40 0]
Jan  2 14:09:04 Bens-PC  NetworkManager[886]: <info>  [1483384144.5104] device (vnet0):  state change: prepare -> config (reason 'none') [40 50 0]
Jan  2  14:09:04 Bens-PC NetworkManager[886]: <info>  [1483384144.5123]  device (vnet0): state change: config -> ip-config (reason 'none') [50  70 0]
Jan  2 14:09:04 Bens-PC NetworkManager[886]: <info>  [1483384144.5124] device (virbr0): bridge port vnet0 was attached
Jan   2 14:09:04 Bens-PC NetworkManager[886]: <info>   [1483384144.5124] device (vnet0): Activation: connection 'vnet0'  enslaved, continuing activation
Jan  2 14:09:04 Bens-PC  NetworkManager[886]: <info>  [1483384144.5125] device (vnet0):  state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan   2 14:09:04 Bens-PC NetworkManager[886]: <info>   [1483384144.5126] device (vnet0): state change: secondaries ->  activated (reason 'none') [90 100 0]
Jan  2 14:09:04 Bens-PC  NetworkManager[886]: <info>  [1483384144.5366] device (vnet0):  Activation: successful, device activated.
Jan  2 14:09:04 Bens-PC  dbus[839]: [system] Activating via systemd: service  name='org.freedesktop.nm_dispatcher'  unit='dbus-org.freedesktop.nm-dispatcher.service'
Jan  2 14:09:04 Bens-PC systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan  2 14:09:04 Bens-PC dbus[839]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  2 14:09:04 Bens-PC systemd[1]: Started Network Manager Script Dispatcher Service.
Jan  2 14:09:04 Bens-PC nm-dispatcher: req:1 'up' [vnet0]: new request (1 scripts)
Jan  2 14:09:04 Bens-PC nm-dispatcher: req:1 'up' [vnet0]: start running ordered scripts...
Jan  2 14:09:04 Bens-PC systemd[1]: Reloading.
Jan  2 14:09:04 Bens-PC systemd[1]: snapd.refresh.timer: Adding 4h 34min 5.029141s random time.
Jan  2 14:09:04 Bens-PC systemd[1]: snapd.refresh.timer: Adding 4h 16min 23.661023s random time.
Jan   2 14:09:04 Bens-PC kernel: [  748.339034] audit: type=1400  audit(1483384144.656:25): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  pid=2624 comm="apparmor_parser"
Jan  2 14:09:04 Bens-PC kernel: [   748.353144] audit: type=1400 audit(1483384144.672:26):  apparmor="STATUS" operation="profile_replace" profile="unconfined"  name="libvirt-57664241-ddeb-427f-823b-47ed8070a197//qemu_bridge_helper"  pid=2624 comm="apparmor_parser"
Jan  2 14:09:04 Bens-PC kernel: [   748.441891] audit: type=1400 audit(1483384144.760:27):  apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2688/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
Jan  2  14:09:04 Bens-PC kernel: [  748.446159] audit: type=1400  audit(1483384144.764:28): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2689/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
Jan  2  14:09:04 Bens-PC kernel: [  748.449850] audit: type=1400  audit(1483384144.768:29): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2690/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
Jan  2  14:09:04 Bens-PC kernel: [  748.466234] audit: type=1400  audit(1483384144.784:30): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2692/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
Jan  2 14:09:05 Bens-PC kernel: [  748.957004] vfio-pci 0000:01:00.0: enabling device (0000 -> 0003)
Jan  2 14:09:05 Bens-PC kernel: [  748.957181] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x270
Jan  2 14:09:05 Bens-PC kernel: [  748.957188] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1b@0x2d0
Jan  2 14:09:05 Bens-PC kernel: [  748.957193] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1e@0x370
Jan   2 14:09:06 Bens-PC avahi-daemon[802]: Joining mDNS multicast group on  interface vnet0.IPv6 with address fe80::fc54:ff:fee8:c3e7.
Jan  2 14:09:06 Bens-PC avahi-daemon[802]: New relevant interface vnet0.IPv6 for mDNS.
Jan  2 14:09:06 Bens-PC avahi-daemon[802]: Registering new address record for fe80::fc54:ff:fee8:c3e7 on vnet0.*.
Jan  2 14:09:06 Bens-PC libvirtd[977]: host doesn't support hyperv 'relaxed' feature
Jan  2 14:09:06 Bens-PC libvirtd[977]: host doesn't support hyperv 'vapic' feature
Jan   2 14:09:06 Bens-PC virtlogd[2586]: libvirt version: 2.1.0, package:  1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com>  Thu, 01 Dec 2016 09:44:12 +0100)
Jan  2 14:09:06 Bens-PC virtlogd[2586]: hostname: Bens-PC
Jan  2 14:09:06 Bens-PC virtlogd[2586]: End of file while reading data: Input/output error
Jan  2 14:09:06 Bens-PC kernel: [  750.192997] virbr0: port 1(vnet0) entered learning state
Jan  2 14:09:08 Bens-PC NetworkManager[886]: <info>  [1483384148.5266] device (virbr0): link connected
Jan  2 14:09:08 Bens-PC kernel: [  752.205034] virbr0: port 1(vnet0) entered forwarding state
Jan  2 14:09:08 Bens-PC kernel: [  752.205035] virbr0: topology change detected, propagating
Jan  2 14:11:49 Bens-PC systemd[1]: Starting Cleanup of Temporary Directories...
Jan  2 14:11:49 Bens-PC systemd-tmpfiles[2740]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jan  2 14:11:49 Bens-PC systemd[1]: Started Cleanup of Temporary Directories.
Jan   2 14:13:10 Bens-PC kernel: [  993.903676] audit: type=1400  audit(1483384390.215:31): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2765/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
Jan  2 14:13:10 Bens-PC kernel: [  993.964186] virbr0: port 1(vnet0) entered disabled state
Jan  2 14:13:10 Bens-PC kernel: [  993.965253] device vnet0 left promiscuous mode
Jan  2 14:13:10 Bens-PC kernel: [  993.965254] virbr0: port 1(vnet0) entered disabled state
Jan  2 14:13:10 Bens-PC avahi-daemon[802]: Interface vnet0.IPv6 no longer relevant for mDNS.
Jan   2 14:13:10 Bens-PC avahi-daemon[802]: Leaving mDNS multicast group on  interface vnet0.IPv6 with address fe80::fc54:ff:fee8:c3e7.
Jan  2  14:13:10 Bens-PC NetworkManager[886]: <info>  [1483384390.3074]  device (vnet0): state change: activated -> unmanaged (reason  'unmanaged') [100 10 3]
Jan  2 14:13:10 Bens-PC NetworkManager[886]: <info>  [1483384390.3075] device (virbr0): bridge port vnet0 was detached
Jan  2 14:13:10 Bens-PC NetworkManager[886]: <info>  [1483384390.3075] device (vnet0): released from master device virbr0
Jan  2 14:13:10 Bens-PC avahi-daemon[802]: Withdrawing address record for fe80::fc54:ff:fee8:c3e7 on vnet0.
Jan   2 14:13:10 Bens-PC NetworkManager[886]: <info>   [1483384390.3342] device (virbr0): link disconnected (deferring action  for 4 seconds)
Jan  2 14:13:10 Bens-PC NetworkManager[886]:  <info>  [1483384390.3343] devices removed (path:  /sys/devices/virtual/net/vnet0, iface: vnet0)
Jan  2 14:13:10 Bens-PC  dbus[839]: [system] Activating via systemd: service  name='org.freedesktop.nm_dispatcher'  unit='dbus-org.freedesktop.nm-dispatcher.service'
Jan  2 14:13:10 Bens-PC systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan  2 14:13:10 Bens-PC dbus[839]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  2 14:13:10 Bens-PC systemd[1]: Started Network Manager Script Dispatcher Service.
Jan  2 14:13:10 Bens-PC nm-dispatcher: req:1 'down' [vnet0]: new request (1 scripts)
Jan  2 14:13:10 Bens-PC nm-dispatcher: req:1 'down' [vnet0]: start running ordered scripts...
Jan  2 14:13:11 Bens-PC virtlogd[2586]: End of file while reading data: Input/output error
Jan   2 14:13:11 Bens-PC kernel: [  995.417786] audit: type=1400  audit(1483384391.730:32): apparmor="STATUS" operation="profile_remove"  profile="unconfined" name="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  pid=2798 comm="apparmor_parser"
Jan  2 14:13:14 Bens-PC  NetworkManager[886]: <info>  [1483384394.3364] device (virbr0):  link disconnected (calling deferred action)

```



VM log ([http://pastebin.com/JMTR0TLQ](http://pastebin.com/JMTR0TLQ)):
```

2017-01-02  19:09:04.676+0000: starting up libvirt version: 2.1.0, package:  1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com>  Thu, 01 Dec 2016 09:44:12 +0100), qemu version: 2.6.1 (Debian  1:2.6.1+dfsg-0ubuntu5.1), hostname: Bens-PC
LC_ALL=C  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin  QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name  guest=win10-clone,debug-threads=on -S -object  secret,id=masterKey0,format=raw,file=/var/lib/libvirt/qemu/domain-1-win10-clone/master-key.aes  -machine pc-i440fx-yakkety,accel=kvm,usb=off -cpu  Haswell-noTSX,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff -m 8192  -realtime mlock=off -smp 3,sockets=1,cores=3,threads=1 -uuid  57664241-ddeb-427f-823b-47ed8070a197 -display none -no-user-config  -nodefaults -chardev  socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-1-win10-clone/monitor.sock,server,nowait  -mon chardev=charmonitor,id=monitor,mode=control -rtc  base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard  -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global  PIIX4_PM.disable_s4=1 -boot strict=on -device  nec-usb-xhci,id=usb,bus=pci.0,addr=0x3 -device  ahci,id=sata0,bus=pci.0,addr=0x4 -drive  file=/var/lib/libvirt/images/Windows10-x64-clone.img,format=raw,if=none,id=drive-sata0-0-0,cache=writeback  -device  ide-hd,bus=sata0.0,drive=drive-sata0-0-0,id=sata0-0-0,bootindex=1 -drive   file=/var/lib/libvirt/images/Storage-clone.img,format=raw,if=none,id=drive-virtio-disk0,cache=writeback  -device  virtio-blk-pci,scsi=off,bus=pci.0,addr=0x5,drive=drive-virtio-disk0,id=virtio-disk0  -netdev tap,fd=26,id=hostnet0 -device  rtl8139,netdev=hostnet0,id=net0,mac=52:54:00:e8:c3:e7,bus=pci.0,addr=0x6  -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x9 -device  vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x2 -device  virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on

```

---

### Post by KillerKelvUK on 2017-01-02
Hey, so just for future reference keep in mind that linux is a case sensitive OS as such there is a difference between 'dmesg -t' and 'dmesg -T'...its no matter as we can use what you've grabbed but in other situations that little mistake could cost you.

So the immediate jump out is the Apparmor DENIED lines in your dmesg output (near the bottom) although its not obvious what specifically they are denying but it sure is to do with libvirt and the guest in question.  Apparmor can be a nightmare in the virt world, I personally remove it but others will persevere and correct it.  Can I suggest a middle ground for you which is to temporarily disable it with a 'sudo systemctl disable _apparmor_'...think I have the last part of that command wrong (the apparmor reference), can you use tab-completion to ensure the command references the correct service to disable.  Once you've done this you'll need to reboot and test again, your dmesg output should no longer show any lines saying stuff like... 

```

audit: type=1400  audit(1483384144.760:27): apparmor="DENIED" operation="open"  profile="libvirt-57664241-ddeb-427f-823b-47ed8070a197"  name="/proc/2673/task/2688/comm" pid=2673 comm="qemu-system-x86"  requested_mask="wr" denied_mask="wr" fsuid=120 ouid=120
```

Enabling apparmor is easy with 'sudo systemctl enable apparmor[tab-completion-again' and reboot.

Regards the UEFI, just because you're host is UEFI capable does not mean that you have enabled it and installed an OS for UEFI booting.  To install Ubuntu using UEFI you need to select the BIOS/UEFI boot option specifically for running the installation media as UEFI, this way the installation wizard will then following the UEFI install process.  I think without this it rules out testing OVMF unfortunately but there is one more thing we can try if disabling apparmor doesn't resolve the problem.

---

### Post by &amp;*@Fth&amp;% on 2017-01-02
Whoops, should've read more carefully.

It was apparmor.service, btw.
Disabling it removed the messages from dmesg (I used grep), but the VM still didn't start.

---

### Post by KillerKelvUK on 2017-01-03
Okay so, final couple of tests which remove virt-manager and libvirt from the equation.  Can you try running the following command just amend the paths to point to your Windows installation .iso file, success would be you seeing the Windows installer prompt to press any key to start the installation via the monitor input for the passthru GFX card.  On the host you should see the qemu terminal window which you can use to kill the guest, note: you wont have any control over the guest so this is just to test passthru but by adding the x-vga=on parameter to the vfio device.

```

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 2048 -cpu host -smp 4,sockets=1,cores=2,threads=2 -bios /usr/share/seabios/bios.bin -vga none -device i82801b11-bridge,id=pci.1,bus=pcie.0,addr=0x1e -device pci-bridge,chassis_nr=2,id=pci.2,bus=pci.1,addr=0x1 -drive file="/mnt/share/Filestorage/Images/Microsoft Windows 10 Home x64.iso",format=raw,if=none,media=cdrom,id=drive-sata0-0-0,readonly=on -device ide-cd,bus=ide.0,drive=drive-sata0-0-0,id=sata0-0-0,bootindex=1 -device vfio-pci,host=01:00.0,bus=pci.2,addr=0x6,multifunction=on,x-vga=on

```

If the above doesn't work please can you install the OVMF package anyway, might as well test it regardless...

```

sudo apt-get install ovmf

```

Will fire you a command separately for testing ovmf.

---

### Post by &amp;*@Fth&amp;% on 2017-01-03
That worked. When the guest first started my screen filled with multicolored line artifacts around the windows, but they went away when I switched over to the guest and then back to the host (I'm using an HDMI switcher now).

---

### Post by KillerKelvUK on 2017-01-03
So just to be clear your saw the "Press any key to start Windows install" type message from the passthru GFX card?  But there was some colour distortion on the host which you think cleared up by itself after switching inputs?

Did you install OVMF also, we can try to see if that works too as using OVMF we can get a cleaner end solution using virt-manager?

---

### Post by &amp;*@Fth&amp;% on 2017-01-03
I didn't see that message specifically, but it was the standard thing you see after booting to a Windows install disk, a window on a purple background asking me to select the language and keyboard layout.

I didn't install OVMF. I have no idea what that that is, but I assume you'll tell me. I can do that once I get home from school.

---

### Post by KillerKelvUK on 2017-01-03
Great news, well next bit below for when you get home bud.

From the OVMF website ([http://www.tianocore.org/ovmf/](http://www.tianocore.org/ovmf/))..."OVMF is an EDK II based project to enable UEFI support for Virtual Machines. OVMF contains a sample UEFI firmware for QEMU and KVM".  So why are we interested...well in some instances of GFX passthrough there is a problem with VGA Arbitration, I won't profess to know a lot about this you can google for more info but basically the problem is to do with an old VGA process that still needs to be adhered to by new GFX tech and in the virtual passthru world that old VGA Arbitration process breaks.  I think this only applies to those of us who do passthrough from Intel hosts where our CPU has integrated GFX or iGD as Intel calls it.  If you google around for KVM i915 Arbiter patching you'll find quite a bit.  A passthru solution that suffers from this problem typically experiences graphical anomalies on the host with colour bleeds and other odd artifacts, sound a little like what happened to yours when you first ran that qemu command?

Anyways if you are affected with vga arbitration issues you have 3 possible options...1) do nothing and live with the resulting desktop issues on the host. 2) patch your linux kernel to include some new lines of code written by a guy-who-knows-best (Alex Williamson) thats stops the discolourations on the host but which breaks the hosts DRI capabilities so you loose graphical performance for 3D effects.  Or 3) if your hardware and software support it move to using OVMF instead of the legacy Seabios for the virtual guest as this allows for the vga arbitration process to work properly for the passthru gfx and both guest and host work without issue.  Hence lets try OVMF but it would be better if your ubuntu host was installed and booted as a UEFI OS.

So once you've installed the ovmf package you will have 2 new files located at /usr/share/OVMF (remember its case-sensitive).  You can leave the file "OVMF_CODE.fd" where it is but you need to talk a copy of "OVMF_VARS.fd" so 'sudo cp /usr/share/OVMF/OVMF_VARS.fd ~' which will copy it to your home directory.

A new qemu command to test this is below but make sure to correct the file path to the OVMF_VARS.fd file in the command as I've highlighted as well as the path to your windows install .iso.

```

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 2048 -cpu host -smp 4,sockets=1,cores=2,threads=2 -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/home/[COLOR=#ff0000]_**xxx**_[/COLOR]/OVMF_VARS.fd,if=pflash,format=raw,unit=1 -vga none -device i82801b11-bridge,id=pci.1,bus=pcie.0,addr=0x1e -device pci-bridge,chassis_nr=2,id=pci.2,bus=pci.1,addr=0x1 -drive file="[COLOR=#ff0000]**/mnt/share/Filestorage/Images/Microsoft Windows 10 Home x64.iso**[/COLOR]",format=raw,if=none,media=cdrom,id=drive-sata0-0-0,readonly=on -device ide-cd,bus=ide.0,drive=drive-sata0-0-0,id=sata0-0-0,bootindex=1 -device vfio-pci,host=01:00.0,bus=pci.2,addr=0x6

```

With any look you should get the same results as last time but without any impact to your host desktop.

---

### Post by &amp;*@Fth&amp;% on 2017-01-03
Well, it sorta worked. It said to press any key to boot from CD/DVD, which of course I couldn't do, and then brought me to the UEFI interactive shell.

But yes, it did fix the visual artifacts.

---

### Post by KillerKelvUK on 2017-01-03
Good news then.  Get back to virt-manager and when creating a new guest on the main page where you can select the chipset (i440fx or Q35) the dropdown box above allows you to change between BIOS and UEFI/OVMF.  So make sure you select Q35 and UEFI/OVMF and you're good to go, for install just add in your hosts USB keyboard and mouse so you can control the guest and get Windows installed properly and then your AMD drivers.  Let us know how you've gotten on :-)

---

### Post by &amp;*@Fth&amp;% on 2017-01-04
Nope, AMD drivers still bluescreen with Q35 chipset.
With the i440FX, it gets frozen at "Installing AMD Display Driver", and my GPU fans spin up and down erratically. I can move the mouse, but there is no signal from the GPU and Windows does not respond to clicks of any kind, and the time on the clock in the corner does not change. I have the feeling the mouse I'm seeing is a fake one drawn by SPICE or virt-manager.

---

### Post by &amp;*@Fth&amp;% on 2017-01-04
Just tried re-installing windows since maybe it didn't like being migrated across chipsets, and now virt-manager is spewing a zillion "warning: host doesn't support requested feature: CPUID.01H:(EDX/ECX/EC).(something) [bit *]" errors and refuses to start the guest. I've tried several different CPUs, and they all give me some sort of "host doesn't support requested feature" error.

---

### Post by &amp;*@Fth&amp;% on 2017-01-05
Never mind, I fixed it. Maybe the rebooting did it? I have no idea.

---

### Post by KillerKelvUK on 2017-01-05
Yeah clean Windows installation definitely needed with all the changes and driver installs its had.  If I recall correctly the AMD cards have some kind of reset glitch which means a host reboot maybe required from time to time.

Regards those CPU feature log messages, they're common place and mostly harmless, only way to get ride of them is to tell KVM/Qemu to passthrough your hosts full CPU feature set to the guest, to do this change the CPU model in virt-manager to "host-passthrough"...you'll need to type this in as its not in the list.

---

### Post by &amp;*@Fth&amp;% on 2017-01-05
It all seems to be working now. Shame that the Q35 doesn't like the AMD drivers. I'll post again once I have all my software installed, remove the emulated GPU, and get some gaming tests done.

---

### Post by KillerKelvUK on 2017-01-05
What do you mean remove your emulated GPU? Why do you still have that present?

---

### Post by &amp;*@Fth&amp;% on 2017-01-06
Sorry about my slow responses, I've been really busy.

I still had the emulated GPU for setting up things, most relevantly Synergy. Without the emulated GPU or Synergy, I wouldn't have been able to pass through my mouse and keyboard.
I'd done tests to make sure it booted without the emulated GPU, but nothing past that without it.

---

### Post by &amp;*@Fth&amp;% on 2017-01-06
Games seem fantastic. The Witcher 3 still has some hitching, but they're very small and infrequent. I suspect it's the game's fault, since I had absolutely no trouble with Rocket League, and there are reports of the game doing this on real hardware as some sort of Windows 10 issue.

Unfortunately, I have no sound. I'm using the AC97 sound card, and I've installed the AC97 drivers in Windows by disabling driver signature enforcement. Windows seems to be sending sound to the sound card, but nothing comes out of my headphones.

---

### Post by KillerKelvUK on 2017-01-07
Hey, as an alternative to adding in your emulated GPX for setup/admin tasks have a try with passing through your usb keyboard and mouse...these will get you into the guest to do all the admin you like but you will not be able to get back to the host until you either shutdown the guest or unplug and replug the keyboard and mouse.  I've no specific reasoning for not adding into your guest the emulated GFX other than I just don't like Windows carrying multiple configurations/drivers so this is very much just personal preference.

Regards your sound you shouldn't need to install drivers bypassing MS signatures etc.  Switch from AC97 to ich9, that shouldn't need drivers and should route audio back via host, thus if you can play audio on your host then ich9 should work.  (Assuming you've nothing custom/fancy on the host side for audio?)

---

### Post by &amp;*@Fth&amp;% on 2017-01-07
Nope, still no sound. On the host, I'm just using the built-in audio on my motherboard.

---

### Post by KillerKelvUK on 2017-01-07
Okay so I just recreated the same i.e. stripped my windows guest down to remove audio pci passthrough and swapped in AC97, ich6 and ich9 and I get no guest-to-host audio routing.  Quick look in the logs and the guest is being run with QEMU_AUDIO_DRV=none...so how to change, well I had a look in /etc/libvirt/qemu.conf and found the following...

```

# By default, if no graphical front end is configured, libvirt will disable
# QEMU audio output since directly talking to alsa/pulseaudio may not work
# with various security settings. If you know what you're doing, enable
# the setting below and libvirt will passthrough the QEMU_AUDIO_DRV
# environment variable when using nographics.
#
#nographics_allow_host_audio = 1

```

...so I uncommented the parameter and restarted the libvirt-bin service, as a result the logs for the windows guest no longer show QEMU_AUDIO_DRV=none but instead now have a bunch of the following lines repeating over and over...

```

alsa: Could not initialize DAC
alsa: Failed to open `default':
alsa: Reason: No such file or directory
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4292:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4771:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM default

```

This looks like its going in the right direction but hitting the security issues the qemu.conf file was alluding too. A quick google search and you find links like this...[https://bbs.archlinux.org/viewtopic.php?id=215098](https://bbs.archlinux.org/viewtopic.php?id=215098). which looks promising however I haven't and won't be testing it as I don't want to move qemu to be using a different user than current.

My suggestion to you is to mark this thread as solved as your original issue is now dealt with.  Then have a read through the above and do some testing of your own and if you can't resolve it then come back and start a new thread specifically for qemu audio.

---

### Post by &amp;*@Fth&amp;% on 2017-01-07
Ok, thanks for the help.

---

