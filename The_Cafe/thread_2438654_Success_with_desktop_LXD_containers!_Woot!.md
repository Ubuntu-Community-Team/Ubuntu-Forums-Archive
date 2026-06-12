---
title: "Success with desktop LXD containers! Woot!"
date: 2020-03-15
forum: The Cafe
---

### Post by DuckHook on 2020-03-15
After years of research, almost giving up and, lately, much blood, sweat and tears, I have finally succeeded in getting x11 apps fully working in LXD containers. Note that I'm mainly interested in using it for GUI apps on the desktop. I realize that the server gurus have refined its use for years running massive clusters of cloud containers, but that's not what I was after.

There's no one resource I can point everyone to. If I can find the energy and reproduce/remember my steps, I will post a tutorial on what I did.

I have started migrating some of the apps that I used to jail in VMs into LXD containers. At this point, it must still be considered experimental, but early results are promising.

Disadvantages:
[LIST]
[*]Because of the ultimately insecure nature of x11, containerized apps are not as securely jailed as VMs. Wayland should help on the security front but so far I haven't been able to get LXD to play nicely with Wayland (web sources are even harder to come by).
[*]The default for LXD is ZFS. This required climbing two steepish learning curves, not just one.
[*]Can't run Windows. Restricted to running other Linux distros.
[*]For the average Joe like me, documentation is sparse, highly technical and arcane. I actually gave up a couple of years ago and it took the last three months to finally pin it to the ground.
[*]
[/LIST]
Advantages:
[LIST]
[*]Doesn't eat up HDD space like VMs.
[*]Apps run much faster. In fact, they are almost—if not exactly—at native speed.
[*]Incredibly efficient with system resources: CPU, RAM, storage, everything.
[*]Keeps my base install squeaky clean. I've hived off both WINE and Steam into containers where they can drag in all the 32-bit libraries they want and not pollute my base install.
[*]Ditto with PPAs.
[*]Once you get over the ZFS learning curve, snapshots and clones are awesome.
[/LIST]
I'd love to hear from anyone else who has this set up and running on their desktop. Especially with respect to tweaks and pitfalls to avoid.

---

### Post by EuclideanCoffee on 2020-03-16
Congratulations. Could you please go into what your stack looks like? Are you using docker?

---

### Post by DuckHook on 2020-03-16
No Docker. LXD straight up (that *GULP* you may have detected coming from me is what it feels like too).

My main resource was Simos Xenitelles's [excellent blog]("https://blog.simos.info/how-to-easily-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/"), but with significant, hard won tweaks gathered from at least two dozen other sites.

I fully intend to post the stack, but kindly ask you to be patient, as I am producing a tutorial as I write. Given the current situation in the world, I have nothing but time on my hands, so I've taken on the task of turning my experiences into a tutorial. It should be up in the tutorial subforum in the next day or two. Until then, please bear with me as I don't want to duplicate efforts.

I will post back on this thread once the tutorial is up.

---

### Post by Tadaen_Sylvermane on 2020-03-16
Looking forward with much anticipation. Ive got my server services all broken into separate lxd containers. Desktop would be amazing to add to that accomplishment.

---

### Post by DuckHook on 2020-03-17
Here it is: [https://ubuntuforums.org/showthread.php?t=2438709](https://ubuntuforums.org/showthread.php?t=2438709)

I will edit and tweak it until either knowledge or energy runs out. Please feel free to comment either here or on the tutorial itself.

---

### Post by EuclideanCoffee on 2020-03-17
Fascinating. This would be an excellent thing to add to my tech stack. Thanks for the information!

---

### Post by DuckHook on 2020-03-17
> **EuclideanCoffee said:**
> Fascinating. This would be an excellent thing to add to my tech stack. Thanks for the information!
Please feel free to post back your experiences. I'm curious whether my stack works for others.

---

### Post by DuckHook on 2020-03-20
I've just added a WINE section to this tutorial. Hope everyone finds it useful.

---

### Post by DuckHook on 2020-03-21
&#8230;and now a Steam section.

---

### Post by TheFu on 2020-03-25
I have a low-end nVidia GPU.  Found that only 18.04 is supported for both the hostOS and the Container OS.
[https://docs.nvidia.com/deeplearning/frameworks/support-matrix/index.html](https://docs.nvidia.com/deeplearning/frameworks/support-matrix/index.html)

Hopefully, this will save someone else wasting a few hours.

Got stuck on **sudo apt-get install nvidia-container-runtime**. All the instructions are for Docker + 18.04. Digging deeper lead to the [https://nvidia.github.io/nvidia-container-runtime/ubuntu16.04/](https://nvidia.github.io/nvidia-container-runtime/ubuntu16.04/) repo  ... which returns:
```
# Unsupported distribution! # Check [https://nvidia.github.io/nvidia-container-runtime](https://nvidia.github.io/nvidia-container-runtime)
```
Found a few places on nVidia's site that say 16.04 is supported as a hostOS.

Guess I won't be moving any GUIs into LXD. ;(
I have to use the proprietary nvidia drivers due to local equipment buggy EDID information which needs to be overridden to get any resolutions above 1080p.  Can't understand how people can put up with 1080 when 1200+ higher res monitors have been cheap the last decade.

---

### Post by DuckHook on 2020-03-25
> **TheFu said:**
> …Guess I won't be moving any GUIs into LXD. ;(  …
A crying shame. I was hoping for your input on LXD vs VM. I have an ancient nVidia GPU in my old laptop running nouveau. Will try that and report back.

---

### Post by TheFu on 2020-03-25
> **DuckHook said:**
> A crying shame. I was hoping for your input on LXD vs VM. I have an ancient nVidia GPU in my old laptop running nouveau. Will try that and report back.

I've been watching containers for a long time. Attended lots of training and decided it wasn't fleshed out if you were running important workloads - something beyond showing cat videos.  That was the situation until about 2 yrs ago.  Default settings in many container helper tools were non-secure by default.

LXD was always at the top of my list to try.  I never planned to try Docker for a number of reasons. I won't deploy any docker containers on our infrastructure.  This is a mix of ignorance and annual bone-head security problems with Docker.  When it comes to any docker-like container, if you don't built it yourself, you've just handed over your entire infrastructure to someone else.  I'm not really interested in recreating new docker containers weekly as a patching method.  If I can get the same density and performance from lxd, while retaining a similar patch paradigm, why not.  I just need to be cautious about the VMs that get moved into LXD.  For example, getting a VPN server working seems to require some network + LXD gymnastics I'm not ready to handle, yet.

How secure are LXD containers? Hard to say.  They aren't the industry standard, so they aren't being specifically attacked like KVM and Docker containers are being attacked.

Yesterday, I had to wipe out the ZFS stuff that was automatically generated, create a new LV and mount it into the /var/lib/lxd/ directory to prevent / from filling up.  I am liking that a base OS is just 360MB. That's very nice.

Probably will put an email gateway system into lxd first.  It is tiny. Doesn't have any data and the version of debian running on it has been failing to start networking after patching.  Sometimes it is fine. Other times, it requires a few reboots.  Makes no sense.  I'm blaming systemd - whenever something is working perfectly for 3 yrs, then a patch happens and breaks networking, it is always systemd's fault.  Always.  

I'm afraid that ancient nVidia GPU means you won't find any nvidia drivers compatible with 18.04.  During my last system build, I decided to get a new GPU only because the ones I have laying around are no longer supported since 14.04.  Reckon  I got my $40 worth from each. 

Anyway, I'll be moving some servers into LXD slowly over the next few months, depending on how the first one goes.  I've been slowing reducing the number of VMs here. Started at 25, then got to 20, 15, now down to 8.  Don't think I can go smaller.

Off to reduce some ignorance now. Plenty of reading to do. ;)

---

### Post by DuckHook on 2020-03-26
My needs are not remotely as mission critical as yours. I just wanted to be able to:

[LIST]
[*]Reduce the overhead of running VMs on old, less capable machines,
[*]Sandbox my apps enough to create another effective barrier to the bad guys,
[*]Take snapshots of app states that will only eat up tiny disk space,
[*]Run the odd game at close to native speed.
[/LIST]
LXD sounded perfect when I first heard about it, but that was 3 years ago and it just wasn't ready for prime time&#8212;on the desktop anyway. I struggled mightily with it, but couldn't wrap my head around the needed sorcery. But Simos' website untangled lots of knots, and now that I'm sandboxing app after app, it's just marvellous. Am hiving off into containers all of the stuff that used to bother me so much when left on my host.

I'm aware that it's only as secure as the next CVE, but I'm guessing that it's still a useful addition to security in depth.

---

### Post by mastablasta on 2020-03-26
so the question - why this useful feature is not made user friendly (e.g. script on install, GUI installer etc.)? would it then make it less secure? is it not useful enough?

---

### Post by TheFu on 2020-03-26
> **mastablasta said:**
> so the question - why this useful feature is not made user friendly (e.g. script on install, GUI installer etc.)? would it then make it less secure? is it not useful enough?

Containers are mainly used by enterprises on headless servers. That's where all the action, updates, research is going because enterprises PAY for capabilities.  Enterprise computing is so different from what typical Ubuntu Desktop users do, they cannot really talk with us.  Everything is encrypted on the wire and at rest.  User management is centralized.  There aren't any GPUs.  Serial consoles are key, which I suspect 90% of home Linux users have never seen. Heck, Ubuntu won't boot with just a serial console connected without some GRUB options.

Enterprises don't use virtualbox for server virtualization. Perhaps a few developers do, but most are migrating to Docker containers for deployment.  MSFT didn't have any choice except to create WSL, or they would have lost all the developer desktop OSes.  
> 
[LIST]
[*]    Reduce the overhead of running VMs on old, less capable machines,
[*]    Sandbox my apps enough to create another effective barrier to the bad guys,
[*]    Take snapshots of app states that will only eat up tiny disk space,
[*]    Run the odd game at close to native speed.
[/LIST]

[LIST]
[*]a) Yep. I'm surprised that LXD is about the same as Docker, since LXD does have more overhead being that it runs much more code inside containers.
[*]b) Firejail.
[*]c) LVM has snap shots. So does qcow2 VM storage.
[*]d) This. This has been the harder part.  My attempts to get games from 2002 and earlier to _just work_ have usually failed unless they are really bonehead.  My last attempt was to get C&C running. There are so many dependencies that I gave up, installed the snapd subsystem and tried to use one of those "easy to deploy" game installers.  I own C&C  (The Covert Operations pak), but wasn't able to get it working.  I don't do FPS, but some old flight sims should easily be playable on modern hardware at full speed even with emulation.
[/LIST]


> 
LXD sounded perfect when I first heard about it, but that was 3 years ago and it just wasn't ready for prime time—on the desktop anyway. I struggled mightily with it, but couldn't wrap my head around the needed sorcery. But Simos' website untangled lots of knots, and now that I'm sandboxing app after app, it's just marvellous. Am hiving off into containers all of the stuff that used to bother me so much when left on my host.
The best thing about LXD is the compartmentalization, but with the GUI use, there are a bunch of holes between the container and the hostOS.
Intel has been working on a native VM solution where the host and VMs can share the same GPU (intel only) for a few years. About every 6 months I check it out and see a 2 minute demo on youtube. The demos seem to crash just after they cut the video. It works with about 5th-gen Core i5 CPUs (desktop and mobile) that have an iGPU.  The problem is the packaging. There wasn't any last fall. Rebuilding the kernel was required.  Around June, I'll look again.   GVT - [https://01.org/igvt-g](https://01.org/igvt-g) is their official site. Looks like work as stalled in 2019.

For GUI programs, **firejail** is my answer today.  It can be used with all programs, but then we end up with unusable setups where network-centric programs cannot access any network resources. Sorta pointless. What good is whois if it can't query a remote whois server?

In 2008, I started as CIO at a little startup.  We needed to use virtualization, but didn't have too powerful systems.  Xen with paravirtualization was used. This is sorta like LXD.  The same kernel that runs on the host is shared by all the guests. There were some problems with Xen. We got some new, faster, hardware in 2010 and switched to KVM.  KVM was pretty fast and didn't have the problems we'd had with Xen. Shared kernels bring some problems that aren't obvious at first.

There are many choices today.  Containers have been effectively marketed as a great choice. Google has gone all-in with containers. Read somewhere that each search request is spun up as a separate container, does the search, waits for the URL click, captures all the data they can from the query, then spins down. It happens so fast, we don't notice it.

---

### Post by DuckHook on 2020-03-26
> **mastablasta said:**
> so the question - why this useful feature is not made user friendly (e.g. script on install, GUI installer etc.)? would it then make it less secure? is it not useful enough?
Good question:

[list]
[*]The devs are not focused on the desktop at all. The overwhelming thrust for the technology is in server-space or cloud-space.
[*]Desktop implementation is an afterthought and perhaps not even that. Currently, desktop is a hobbyist's implementation.
[*]It remains very bleeding edge. LXD does not even have man pages yet. It uses ZFS, btrfs or LVM at a minimum. Install scripts and GUI installers are not even on the radar.
[*]It is too technical for the general user because it is not only a huge learning curve in and of itself, but requires a new infrastructure. It took me weeks to learn enough about ZFS alone to feel comfortable enough to utilize it.
[*]Like a lot of amazing technology, technological superiority does not automatically translate into marketability. Other factors are at play (look at desktop Linux vs Windows, reiserfs vs NTFS)[/list]

---

### Post by DuckHook on 2020-03-26
> **TheFu said:**
> &#8230;LVM has snap shots. So does qcow2 VM storage.
Yes they do. And I use both. LVM is great, but has some limitations. I stayed away from ZFS for so long in part because LVM gave me most of what I wanted. The recent purchase of a 4 disk RPi-based micro server&#8212;a process that some prior advice of yours started btw&#8212;had me looking at some sort of equivalent to RAID-Z implementation, and that's one of the areas in which LVM is lacking. Or perhaps I should say: if an LVM solution exists, I couldn't find it.

I find qcow2 to be limited by the more general limitations of VMs. Most of my equipment is ancient by today's standards, but still perfectly usable to Mrs Duckhook and me. VMs are at that inflection point in resource intensity that they bog down such equipment, whereas LXD works just fine.
> The best thing about LXD is the compartmentalization, but with the GUI use, there are a bunch of holes between the container and the hostOS.
This is a legitimate worry. I know that hooking into X opens up a lot of holes. But I figure that a bad payload would have to be specially crafted to take such advantage, and the sites that I visit and files I download are highly unlikely to be compromised in this way. Maybe I'm just being naïve.
> Intel has been working on a native VM solution where the host and VMs can share the same GPU (intel only) for a few years. About every 6 months I check it out and see a 2 minute demo on youtube. The demos seem to crash just after they cut the video. It works with about 5th-gen Core i5 CPUs (desktop and mobile) that have an iGPU.  The problem is the packaging. There wasn't any last fall. Rebuilding the kernel was required.  Around June, I'll look again.   GVT - [https://01.org/igvt-g](https://01.org/igvt-g) is their official site. Looks like work as stalled in 2019.
Interesting. Thx for the link.
> For GUI programs, **firejail** is my answer today.
Curiosity question&#8230; How does firejail differ from apparmor? I really don't want to learn yet another jailing system. We're now already protected by default with apparmor and Selinux. Isn't there a point of diminishing returns? Where additional security comes at the cost of so much complexity and inconvenience that it is no longer pragmatic?

---

### Post by TheFu on 2020-03-27
Apparmor doesn't have nearly the number of profiles that firejail ships with by default.  Plus, creating additional firejail profiles isn't hard. It is basically self-explanatory when looking at a few existing profiles.  Cannot say that about apparmor.

firejail has locally controlled profiles.  
I've not found much need to learn many complexities of firejail.  I use 2 modes.
* HOME directory access allowed
* ZERO directory access allowed

```
firejail firefox
firejail --private firefox
```

To learn the difference, try
```
firejail bash
firejail --private bash
```
Start up each in a different terminal. Look around. See what's there, what's available, and what isn't.  Try using sudo or sudoedit.
Those 5 minutes will explain more than I could in 20 min of typing here.

When I say "HOME directory access", I really mean access to very specific places in the HOME directory.  In /etc/firejail/ are the profiles.   They are pretty easy to understand. Much easier than apparmor. Much.

Firejail's inconvenience is extremely blatant. It never leaves me wondering "why" - I know when I can't see any files in a directory in Firefox, but a bash shell shows it (not firejailed), then it is 100% firejail doing the limitations.  Firejail isn't all or nothing.  We can have 50 different profiles for each program we use. Generally, I have just a few.  "no networking", "no access outside HOME", "no access anywhere."  Sorta like how we mount /tmp/ with noexec as an option to prevent common hacks ... until something like AppImage fails to work because of it.

But you definitely have some excellent points.

---

### Post by DuckHook on 2020-03-27
Thx for all of the above. I *might* give firejail a try, though I've invested so much time into apparmor that I know I'll keep using it. Apparmor is absurdly arcane, but making the effort to understand it does provide one fringe benefit: often, apps misbehave because of apparmor restrictions (some snap apps for example). Knowing how to tune apparmor gives one a fighting chance at fixing such things.

---

### Post by DuckHook on 2020-04-03
I've now added a section: [Running a Full, Separate Distro]("https://ubuntuforums.org/showthread.php?t=2438709&p=13943827#post13943827") to the tutorial.

Running another distro within a container (instead of a VM) has been a long-unfulfilled dream when I started fooling around with containers a few years ago. I'm happy and a bit surprised that it can now be done so easily.

---

### Post by TheFu on 2020-04-03
Have you tried setting a VPN inside a container?  Any tips?

---

### Post by DuckHook on 2020-04-03
> **TheFu said:**
> Have you tried setting a VPN inside a container?  Any tips?
Not yet. I haven't even gotten around to trying things out on that old laptop with the nVidia GPU yet. I promised that first, but the craziness of life has rather sidetracked me (it's scary out there).

It's a worthwhile project, I'm curious too, so will try an implementation and report back. Full disclosure: networking is not my strength. I may have to lean on forum members for help.

At least I managed to install resolvconf and direct the DNS to adguard.com's servers, so browsers no longer show ads. If that's any indication, then VPN shouldn't be too hard, but with the NAT layers and other network complexities, I'm not holding my breath either.

---

### Post by DuckHook on 2020-04-04
> **TheFu said:**
> Have you tried setting a VPN inside a container?  Any tips?
I've now set up a VPN that mostly works. But though it works, it throws an irritating error that I haven't been able to solve. Note that my VPN needs are less demanding than yours—I only need to connect to my provider whereas you've mentioned in the past that you connect to your own server. At any rate, my steps:

[LIST=1]
[*]Install vpn client:```
sudo apt install openvpn
```
[*]Download .ovpn stack from provider:```
sudo wget https://www.privateinternetaccess.com/openvpn/openvpn.zip
```
[*]Unzip to /etc/openvpn/
[/LIST]
So far, so good. These simple steps were all that was necessary for complete success on my host machine. But invoking openvpn within the container only completed partially:
```
ubuntu@xubuntu:~$ sudo openvpn /etc/openvpn/'US California.ovpn'
Sat Apr  4 00:00:34 2020 OpenVPN 2.4.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep  5 2019
Sat Apr  4 00:00:34 2020 library versions: OpenSSL 1.1.1c  28 May 2019, LZO 2.10
Enter Auth Username: **********
Enter Auth Password: **********
Sat Apr  4 00:01:25 2020 TCP/UDP: Preserving recently used remote address: [AF_INET]xxx.xxx.xxx.xxx:1198
Sat Apr  4 00:01:25 2020 UDP link local: (not bound)
Sat Apr  4 00:01:25 2020 UDP link remote: [AF_INET]xxx.xxx.xxx.xxx:1198
Sat Apr  4 00:01:25 2020 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sat Apr  4 00:01:26 2020 [xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx] Peer Connection Initiated with [AF_INET]xxx.xxx.xxx.xxx:1198
Sat Apr  4 00:01:27 2020 TUN/TAP device tun0 opened
**Sat Apr  4 00:01:27 2020 Note: Cannot set tx queue length on tun0: Operation not permitted (errno=1)**
Sat Apr  4 00:01:27 2020 /sbin/ip link set dev tun0 up mtu 1500
Sat Apr  4 00:01:27 2020 /sbin/ip addr add dev tun0 local 10.30.10.6 peer 10.30.10.5
Sat Apr  4 00:01:27 2020 Initialization Sequence Completed
```*Personally identifiable info has been redacted.

I have bolded the error.

The process then stalls after "Initialization Sequence Completed". Fortunately, because the stall occurs only after initialization has completed, the VPN tunnel actually gets created. An IP address query confirms that it's the VPN provider's. The problem is that I must <Ctrl> + <c> to get back to the shell and this collapses the tunnel:```
^C
Sat Apr  4 00:10:38 2020 event_wait : Interrupted system call (code=4)
Sat Apr  4 00:10:38 2020 /sbin/ip addr del dev tun0 local 10.30.10.6 peer 10.30.10.5
Sat Apr  4 00:10:38 2020 SIGINT[hard,] received, process exiting
```
Moreover, because the VPN setup process never completes, the credentials are not recorded and systemd never registers the service, so the tunnel does not survive a reboot. My workaround is to create the tunnel in screen and then detach it. This gives me back my shell and allows me to logout of the session, but it's an ugly, incomplete kludge and there surely has to be a better way.

You asked for hints and I found this link with a possible solution:
[https://forum.proxmox.com/threads/openvpn-in-unprivileged-container.38670/#post-262140](https://forum.proxmox.com/threads/openvpn-in-unprivileged-container.38670/#post-262140)
…but I'm barely technically proficient enough to play with it, so I haven't experimented with it—much less implemented it.

---

### Post by TheFu on 2020-04-04
VPN clients are pretty easy.
It is the VPN server that needs some funky networking, kernel modules, and internal routing that would be the challenges with any container deployment.

---

### Post by DuckHook on 2020-04-04
> **TheFu said:**
> …It is the VPN server that needs some funky networking, kernel modules, and internal routing that would be the challenges with any container deployment.
Way beyond my pay grade. A bit like Yoda asking Luke for guidance. :P

---

### Post by TheFu on 2020-04-04
> **DuckHook said:**
> Way beyond my pay grade. A bit like Yoda asking Luke for guidance. :P

Beyond my pay grade too, it seems.

---

### Post by sudodus on 2020-04-04
I just finished reading your new tutorial. I have not used it, but I hope to get time to do it. Thanks for sharing the result of your great effort :-)

---

### Post by DuckHook on 2020-04-05
> **sudodus said:**
> I just finished reading your new tutorial. I have not used it, but I hope to get time to do it. Thanks for sharing the result of your great effort :-)
This is high praise coming from you, who have been doing it for years. \\:D/ 

Sharing our discoveries is what belonging to this forum is all about. I hope you find it useful and I'd love to hear your results.

FWIW, since implementing it, I've been on a really satisfying mission: hiving off dozens of apps into containers. I've been able to compartmentalize WINE and Steam, and as a result, have successfully done:```
sudo dpkg --remove-architecture i386
```…from my base install. I've also removed all but one PPA from sources.list. It so happens that the only remaining one is… yours! *mkusb* can't be run from a container. Well, technically, it can, but I decided that the contortions needed to map USB to a container are not worth the effort. Accessing the USB bus defeats the purpose of sandboxing anyway so there's little point in compartmentalizing it.

I've basically cleaned up my system to an almost pristine install state. The upcoming network upgrade to Focal should now be trouble free.

I haven't felt this unburdened in years. It's liberating to try out as many new apps as I want without touching my base install. And I just got some old Windows games running again by simply creating a WINE instance based on Trusty. Talk about versatility!

Sorry to sound so giddy, but it's been an amazing series of discoveries. I'm going to keep expanding the tutorial (judiciously), hopefully without making it too unwieldy.

---

### Post by TheFu on 2020-04-05
Been struggling with LXD.  Often, usually, problems like I'm having are due to ignorance, so let's assume that for now.  My ignorance needs to be assumed.

Got my first *play attempt* with LXD working last week.  It was easy, but with less than great storage.  ZFS on a file system, on an LVM setup, wasn't gonna work. Too many disconnected layers and complexity. Performance was poor, as would be expected

**For any VM solution, the storage architecture is the foundation.**  ZFS and LVM storage back-ends haven't worked for me.  Have a few more to try, next will be thin-provisioned LVM.  I'm crossing my fingers.

---

### Post by DuckHook on 2020-04-09
I just tried the whole sandboxing process with a fresh Eoan install on an old(ish) laptop. Uneven results. As per TheFu's last post, I partitioned the SSD to install the OS on a traditional ext4 file system. The rest of the SSD was left empty for a zfs file structure. This has worked out well. Everything installs, zfs pool created without complaints, LXD containers all map to the pool nicely.

Creating Bionic containers also went smoothly. However, Eoan containers don't work with the x11.profile that is in my tutorial. I'm trying to debug/troubleshoot it now. This is not a deal-breaker because I'm okay with Bionic containers for now, but it would be nice to have Eoan containers working. And as time goes on and Bionic approaches EoL, then working current versions will become increasingly important. Perhaps I will reach out to Simos or S Graber for guidance.

---

### Post by kevdog on 2020-04-11
What's the advantage of using this strategy over Docker?  I'm not challenging you I just don't know a lot about LXD.

Nice tutorial by the way.  Reminds me a lot of how Docker operates.

Question about file sharing with the host system.  Can you not do a bind mount similar to docker to share a directory or file with the host?

I'm also curious about zfs within the container.  I've used zfs a lot but I'm definitely no expert.  ZFS is used on FreeNAS and I've done a few Arch installations as VMs using ZFS on root.  As you've stated ZFS snapshotting and cloning is great.  ZFS when done properly however usually likes to be run on bare metal (I say this as I run Arch VMs with ZFS).  Does ZFS utilize the host system's or did you have to allocate a specific amount of RAM to the container on creation?

Really nice tutorial -- I'm sure what you wrote took hours of backend testing and configuring.

---

### Post by DuckHook on 2020-04-11
Hi kevdog,

I wouldn't mind at all even if you were challenging me. Such challenges are usually the route by which I learn new things.

But you are giving me more credit than I deserve. I really know absolutely nothing about Docker. My route to using LXD was purely a curiosity-driven one:
[LIST=1]
[*]My incessant nosiness about all things Ubuntu led to my dabbling with LXD's predecessor, LXC, a few years ago.
[*]Though I understood its usefulness as a containment strategy, LXC was excruciatingly arcane and obscure.
[*]At the time, my interest in it was confined to playing with other distros without incurring the overhead of VMs.
[*]I could never get it to work, so reluctantly dropped it. About a year later, I read about its successor, LXD. It was supposedly easier to use.
[*]After trying to get it to map to X and especially audio, I was unsuccessful so reluctantly dropped it too. Got closer to my goal though.
[*]At beginning of this year I revisited LXD and came across Simos' blog. Finally, success.
[/LIST]
So you see, asking me for a Docker comparison is a bit like asking a grade schooler for a primer on quantum theory. I may understand it in an amateurish do-this-then-that kind of way, but I don't *really* know it.

Of the things that I've read, the following is simple enough for me to understand: [https://linuxhint.com/lxd-vs-docker/](https://linuxhint.com/lxd-vs-docker/)

Actually, *you* may be better placed at telling *me* the difference. If I understand correctly, Dockers would not work at running a full Fedora or Arch distro, whereas LXD would (there are even prebuilt Fedora and Arch containers in LXD). As a case in point, I'm running a full Xubuntu Eoan distro in a container on a Bionic host as I write, and exploring its cool upgraded apps.

> **kevdog said:**
> …Can you not do a bind mount similar to docker to share a directory or file with the host?My research says that it can be easily done. There are many blogs and sites providing instructions. I've never explored it because my objective is the opposite: to harden the sandbox rather than poke holes in it.

> …ZFS when done properly however usually likes to be run on bare metal (I say this as I run Arch VMs with ZFS).  Does ZFS utilize the host system's or did you have to allocate a specific amount of RAM to the container on creation?My ZFS pool is on bare metal. In my main machine, I've given it a full HDD all its own. From there, I hive off datasets, one for LXD, another for personal use, etc. I haven't constrained any of the datasets with quotas. They are allowed to grow unhindered and just use up as much of the shared pool as needed.

Not sure what you are referring to re: RAM. The LXD instances also dip into the shared RAM pool for what's needed. No quotas were imposed at setup, so unless LXD imposes some kind of default quota that I'm not aware of, I don't believe any of my containers are RAM constrained either.
>  I'm sure what you wrote took hours of backend testing and configuring.
Thanks. Yes it did, but the tutorial is as much for self-guidance as it is for public benefit. I use it record my steps so I don't have to reinvent the same wheel again. I will continue to refine it as I discover more features, answers and workarounds.

---

### Post by DuckHook on 2020-04-12
> **DuckHook said:**
> &#8230;I will continue to refine it as I discover more features, answers and workarounds.
Addressing some issues, I've updated prior sections and just added two more: "Problems and Troubleshooting" & "Tips and Tricks".

---

### Post by Skaperen on 2020-04-12
not having read all the posts above, yet, i want to reveal some of my thoughts on this.

others seem to primarily want to containerize services.  i want to, as well, and will be interested.  but, i also want to containerize users.  and the means both the many users i run, myself, as well as other people.  that means when someone logs in, their processes run inside a container just for them, in lieu of a VM just for them.  but does X run in the container (when logging in through LightDM)?  i have been wondering how to do this if the container security is tight.  how can access to the graphical hardware be handled safely?  but then i thought that it really isn't that necessary to run X in the container.  my current thought is to run X in the host in the usual way and put the processes that start the user inside the container specifically constructed for that user.  the network path to X would be made accessible in the user container and the starting process would inherit the reference and credentials.  a Unix socket!

i typically run over a dozen users when i am on my laptop.  i readily switch user with shortcut hotkeys that run the dm-tool command.  for example Alt+f switches to the "forums" user where i go to access the various forums i have icons for.  i have "email" on Alt+e to access various emails i have.  Alt+m is dedicated to Magnature (paid account).  Alt+l isolates Linkedin from everywhere else i visit (they have tried to discover). my various AWS accounts each have different users to isolate them even more.  backups are done in yet another.  userid isolation is an improvement but i want to go even further.

---

### Post by TheFu on 2020-04-13
Anyone setup a Pi-Hole on LXD yet?  Should be a tiny little project, pretty easy.

---

### Post by kevdog on 2020-04-13
Just a question.  I've never used Pi-Hole, however is it going to be different than like pfBlocker on pfSense?

---

### Post by TheFu on 2020-04-16
> **TheFu said:**
> Anyone setup a Pi-Hole on LXD yet?  Should be a tiny little project, pretty easy.

Ok, this morning I setup a pi-hole with local DNS on LXD for a LAN subnet here. Links and a few notes :
[https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454)

Less than 30 minutes for me, if I wasn't multi-tasking, interrupted, etc. If you know what you are doing with LXD and reasonable network skills, should be less than 10 minutes.  I already had a few things setup like a bridge LXD network which came in handy.

Next part of the project is to add DNS-over-HTTPS to the pi-hole.

I still need to go back through all my systems and switch the DNS settings over to the pi-hole.  That will take some time, since I've had DNS issues that really pissed me off a few times to the point that chattr +i /etc/resolv.conf was used on many systems to prevent resolvconf or systemd-resolve from f*)&^#%g with the settings. Undoing that will take a little effort.
Also, I'm torn about cleaning up /etc/hosts files on each system, especially rooted android devices, where it was such a hassle to modify. It is really handy to have LAN name resolution working when outside the network.  The "right" thing to do is fix my VPN so that DNS queries always hit the pi-hole when I'm away. That isn't always easy.

---

