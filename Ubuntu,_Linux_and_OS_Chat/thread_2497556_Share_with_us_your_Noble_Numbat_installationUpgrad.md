---
title: "Share with us your Noble Numbat installation/Upgrade Experience"
date: 2024-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by wildmanne39 on 2024-05-09
Noble Numbat was released April 24th, 2024, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Noble Numbat.

This thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2493482](https://ubuntuforums.org/showthread.php?t=2493482)

---

### Post by Irihapeti on 2024-05-09
I've got several (X)Ubuntu systems, some of which I upgraded and others have been fresh installs. The upgrades were basic servers, so maybe not all that surprising that they proceeded without problems.

Anything more complex, I do a reinstall. I expect a few tweaks to be necessary along the way, but I've not encountered anything too serious this time around.

I'm not sure yet what I'll do about my public VPS, but that won't be until July/August. It's had one upgrade, and it might be time to do a fresh install. We'll see.

---

### Post by gezzer2 on 2024-05-10
two computers both had 22.04.4 LTS installed both systems were encrypted on install with the Ubuntu default settings 22.04.4 for the partitioning and installer.

1st. system .. HP 24" AiO .. Ryzen 7 5000 series 5825u zen 3 .. 1TB M2 type SSD .. 64GB DDR4
USB live install 24.04 using default settings for partitioning with encryption. 
 
install failed system was unbootable .. 
reloaded the live installer and deleted all partitions on the SSD, reinstalled with default settings for partitioning with encryption.
systems booted to the desktop had to reset CPU governor to amd_pstate=active and is now working and running fine.

....

2nd. system .. Dell 13" latitude 3380 .. Intel i5 7200u 7th gen .. 275GB 2.5 SSD .. 16GB DDR4
USB live install 24.04 using default settings for partitioning with encryption.

install failed system was unbootable ..
reloaded the live installer and deleted all partitions on the SSD, reinstalled with default settings for partitioning with encryption.
systems booted to the desktop and had problems with screen tearing and CPU/GPU speed.
reset CPU governor to intel_pstate=active no improvement the system became unusable.

rebooted to a install USB live 22.04.4 and reinstalled 22.04.4 with default partitioning and encryption. changed the governor to intel_pstate=active.
laptop is now working perfectly with 22.04.4 .. 24.04 install failed completely and was unusable with this laptop.

just to note both systems have backup HDD's.
1st. system has a 1TB USB HDD and the 2nd. system has a 500GB USB HDD.

just a PS to this. i have now installed Linux Mint Debian Edition (LMDE) on both systems ...

---

### Post by ajgreeny on 2024-05-10
I have an 11 year old desktop machine which had Xubuntu 22.04 and 20.04 as dual boot, sharing a separate /home partition.
I have clean installed 24.04 over the 20.04 version with no big problems noted so far even though it is still sharing the same /home partition.

For some reason which I do not understand my first attempt at a clean install failed completely and the new snap bootstrap installer just froze and sat going nowhere for about 45 minutes so I aborted that attempt and started again.

This second attempt was faultless even though all my settings etc were identical to my first attempt and the shared home has not caused problems so far and the whole system seems to be running smoothly and fast.

Early days but so far looking good!

---

### Post by TheFu on 2024-05-10
Did a fresh install into a KVM/QEMU VM for both Xubuntu and Lubuntu.  For both, I was unable to figure out how to use a manual LVM layout, my preferred storage management system.  All I wanted was LVs for root, home, and swap, nothing too complex.  After screwing around with it in front of 20 or so people at my LUG, I gave up.

Immediately, after install, at the first login, 
Xubuntu wasn't stable.  It locked up 3 times in less than 20 minutes.  The LUG decided it wasn't production ready.  Wiped the storage.

Moved on to Lubuntu.  Besides the LVM problem, this installed cleanly. I experienced zero lock ups. The interface was fast and responsive.  I've been unable to get key-based ssh working. Don't know why, but after 5 minutes of screwing around, moved on.  The Lubuntu VM was the same VM as Xubuntu - 4GB RAM and 1 vCPU (Ryzen 5xxx series).  I didn't wipe the Lubuntu 24.04 install, but it won't be used in production and it won't have data loaded.

Lubuntu seems ready for production with a few issues for my personal needs - LVM and key-based ssh.  I understand that LVM won't be fixed, so I'll be skipping 24.04 until that is addressed - if never addressed, I'll skip 24.04 completely.  When it is time in 2025 to move my production systems to a new release, it cannot be 24.04 based.  The ssh-key problem will likely have a resolution that I just haven't discovered yet.

I still need to try the Server install. Not sure why I'd bother if LVM isn't easily supported.  The lack of LVM support is a huge problem for all our systems. We need the flexibility and long-time enterprise quality of a volume manager. It is central to our storage and backup methods.

---

### Post by #&amp;thj^% on 2024-05-10
Xubuntu here, on zfs-root, clean install. Installer would crash over and over, until I zapped the Drive with No Format chosen.
After that install worked, lacking manual partitioning as said by others.

So this install is more or less a toying around install, and Bug-Triaging. (Not Ready for my usage)  :(

My wish is for Canonical to stop re-inventing the wheel and stick to what made it a desirable Desktop/Server Distro in the first place. (Respectfully spoken)

---

### Post by Dennis N on 2024-05-10
First, I downloaded the Ubuntu 24.04 iso and burned a USB with the installer. I wanted to see if installation to an existing LV might be supported. It wasn't. 

Instead I did a QEMU/KVM install as a virtual machine. I chose the Advanced Features > LVM install as a option. This is the only way to install with LVM. It worked. The result:

Resulting Partitions:

```
Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1128MB  1127MB  fat32              boot, esp
 2      1128MB  3258MB  2130MB  ext4
 3      3258MB  25.2GB  21.9GB

```
This installer insists on a boot partition, even with no encryption. In the previous installer, that was not so. So that's what partition 2 is. Partition 3 is used for the Ubuntu VG and Ubuntu LV.

The resulting sizes:

```
vda                        23.4G
&#9500;&#9472;vda1                        1G
&#9500;&#9472;vda2                        2G
&#9492;&#9472;vda3                     20.4G
  &#9492;&#9472;ubuntu--vg-ubuntu--lv  20.4G

```

I read there are improvements from Gnome 45, but from my end user point of view, its the same as Gnome 45 plus a number of (hopefully temporary) bugs and glitches introduced. 
 
I have to use Wayland in the VM, otherwise, in the Xorg session the cursor is unstable.

A few things I noticed:

You get App Center to browse and install software instead of Ubuntu Software. With App Center, the overview screen in Ubuntu does not search for software as it does with Gnome software (and maybe Ubuntu Software). Since App Center does not support Flatpaks at all, I installed Gnome Software (not Ubuntu Software) which does.

Gnome Shell theme setting no longer appears in Tweaks.  You have to install the "user themes" extension. 

If using DMZ-white cursor, it turns to a box over gnome-shell components like the top panel or the dock.

windows may not open where they were previously closed. Example: Audacious always opens in upper left instead of where I want it. So one must manually move it to the place you want it. This may be the application's problem? The window size is retained, but not the location.

The Info Bar sound visualization no longer works in Audacious.

Bookmarks made in "Places" extension to the host OS no longer automatically mount the location when clicked as they did before. Files still does automount them.

And of course, a couple of extensions have not yet been updated so they don't work.

Probably more to be discovered over time.

Besides these things, the OS works fine. I'm waiting for Software Updater's notice that the upgrade from 23.10 is available. That would give me an LV with 24.04 without erasing my disk. We see how that goes.

---

### Post by VMC on 2024-05-10
Fresh install. Flawless. Obviously hardware is a major factor. No Nvidia for me.

---

### Post by Claus7 on 2024-05-10
Hello,

upgrade went fine more or less from mantic apart from thunderbird issue: it caused a loop during upgrade. I had to install it manually and then continue with the rest of the installation. The good thing is that it was one of the last parts of the upgrade and something that will get fixed till .1 version is released.

I noticed that 0ad and freecad are removed from repositories even if 0ad-data is there.

Sometimes using window tiling, placing a window on the right hand side of the screen resulted in freezing of the computer. I noticed that gnome shell has been updated in the meantime which might solve the issue.

Double clicking on the top panel without having any window maximized results in a trembling movement of desktop icons. This stops if a new application opens. 

Still under wayland Desktop bookmark of nautilus is not there by default.

I noticed too the box-shaped cursors using white ones.

Still gnome flashback does not have the option to copy paste files from/to desktop.

The ram usage I think that is lower compared to previous ubuntu versions: in my case ubuntu wayland uses 1.5 GB, which I consider it much lower from values like >1.7 that I was observing before.

Nice that gnome-system-monitor now is using gkt4.

One thing that I consider an improvement is the size of fonts of gnome shell. They are not so tiny especially in non-hd screens. Also I consider the fonts sharper than before.

I think that the response of the system in general is faster: e.g. opening nautilus, opening documents with LO.

No image thumbnails using desktop icons under wayland.

Applications extension has been renamed to Apps.

Blender "continue anyway" option is not working if a non compatible graphics card is identified.

Firefox snap was not working in my case. Using ppa firefox instead, it complains about a weak algorithm, something that is known and will get fixed soon.

Regards!

---

### Post by TheFu on 2024-05-11
Just installed 24.04 Server.  LVM is there and it is possible to customize through the installer.  I even guessed how to setup a static IP on the first attempt, though that screen in the installer _**REALLY, REALLY, needs examples**_ of the data entry fields to the right of each field to prevent the guessing.

```
**$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint**
NAME            TYPE FSTYPE       SIZE FSAVAIL FSUSE% LABEL MOUNTP
sr0             rom                 2K                      
vda             disk               15G                      
&#9500;&#9472;vda1          part                1M                      
&#9500;&#9472;vda2          part ext4         750M    574M    13%       /boot
&#9492;&#9472;vda3          part LVM2_member 13.2G                      
  &#9500;&#9472;vg02-root   lvm  ext4          10G      7G    23%       /
  &#9492;&#9472;vg02-swap00 lvm  swap         500M                      [SWAP]

**$ df -hT -x squashfs -x tmpfs -x devtmpfs**
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg02-root ext4  9.8G  2.2G  7.1G  24% /
/dev/vda2             ext4  721M   95M  574M  15% /boot

**$ sudo vgs**
  VG   #PV #LV #SN Attr   VSize   VFree 
  vg02   1   2   0 wz--n- <13.25g <2.76g

**$ snap list**
No snaps are installed yet. 

```

So, it appears to me that this is solved on 24.04 Server. 

I need to try the desktop installers again. Perhaps I didn't know what I was doing?  I'd read that changing the VG name at install time wasn't allowed somewhere too.  It was a hassle because I had to remove all the LVs first - renaming would be nice without having to remove the LVs, but it is possible.  Normally, an install takes about 10 minutes. Because I had to figure out the "magic" requirements, took me about 20 minutes.   As you can see, I changed the VG name, LV names, sizes to fit my needs.

Best of all, I have a little free space in the VG for other uses, like creating snapshots for my backup process.  This was a toy server setup just to see that LVM and how much storage would really be needed.  Minimal install with ssh.  No snaps included.    **2.2G used. **Nice.  The days of bloat may be over. We can hope.

Perhaps all my worries about 24.04 server weren't really true.

How do I say this.  ZERO complaints so far (well, beyond systemd).  Small, tight, things work as expected. No extra bloat.  *Golf clap* to the Ubuntu Server team. Nice job.

Sorry, I didn't mean to shock people used to me constantly complaining about small things when Canonical does 10,000 things right.  A clear, autoinstall YAML example would be nice that sets the 1st username, LVM layout, VG/LV names, LV sizes, file system format, static IP addresses, and allows specifying the file URL on the install screen would be nice.  Perhaps this exists somewhere and I just haven't found it.

Just confirmed that 24.04 Lubuntu storage setup doesn't allow LVM.  Can get to the point of selecting the PV for a new VG to use, but there's no list of PVs in the dialog box to choose.  "Create Volume Group" button is gaslighting. That's rude.  It was bad enough that LVM is an allowed type of partition.

Over all, nice job guys.

---

### Post by Dennis N on 2024-05-11
On The Poll Results

I think the terminology in the poll needs clarification. The first three choices are for an "Upgrade". The last three are for an "Install".

"Install" would be used with New (Fresh) Installs.
"Upgrade" is intended to be used if you used an upgrade tool like Software Updater. This can't be done yet (as of May 11), so there should be no votes here. 

Better descriptions are needed. 

Does that make sense?

In a way, new installs are 'upgrades' to what they had before. A few people apparently were thinking this way and voted under upgrade.

---

### Post by #&amp;thj^% on 2024-05-11
> **Dennis N said:**
> On The Poll Results

I think the terminology in the poll needs clarification. The first three choices are for an "Upgrade". The last three are for an "Install".

"Install" would be used with New (Fresh) Installs.
"Upgrade" is intended to be used if you used an upgrade tool like Software Updater. This can't be done yet (as of May 11), so there should be no votes here. 

Better descriptions are needed. 

Does that make sense?

In a way, new installs are 'upgrades' to what they had before. A few people apparently were thinking this way and voted under upgrade.

+1
```


[COLOR="#FF0000"]Upgrade - Worked Flawlessly.
1	9.09%

Upgrade - Worked but had a few things to fix, nothing serious though..
2	18.18%[/COLOR]

Upgrade - Had many problems that I've not been able to solve.
0	0%

Install - Worked flawlessly
4	36.36%

Install - Worked but had a few things to fix.
4	36.36%

Install - Had many problems that I have not been able to solve. 
```
Unless they meant a dirty-install-upgrade>>>Clarity is needed to be acurate

---

### Post by Irihapeti on 2024-05-11
I include "upgrade" as meaning "changed the repo manually and then ran apt full-upgrade", but then, that's just me.

---

### Post by #&amp;thj^% on 2024-05-11
> **Irihapeti said:**
> I include "upgrade" as meaning "changed the repo manually and then ran apt full-upgrade", but then, that's just me.
+1 Me as well , and also a clean install on a different drive.

---

### Post by nicolasdentremont on 2024-05-12
I wanted to swap hard disks between my Windows and Ubuntu, sending windows to the slower HDD and decided to install Noble Numbat while I was at it. This was a fresh new install from a USB drive. The install went quickly and without issue. I can't really compare speeds because I went from Ubuntu 22.04 installed on an older HDD to 24.04 on a newer SSD. It's super fast now.

---

### Post by ajgreeny on 2024-05-12
There's been a few comments about the manual partitioning not working, at least I think that's what people mean.
Maybe this is a problem only if using LVM or ZFS.

Using ext4 I can confirm it is still easy to use manual partitioning reusing an  existing /home partition without formatting and creating  a new root partition.

I admit I have never used anything other than ext partitions, including ext2 ànd ext3; yes I've been using Ubuntu, now Xubuntu, for that long!

---

### Post by #&amp;thj^% on 2024-05-12
> **ajgreeny said:**
> There's been a few comments about the manual partitioning not working, at least I think that's what people mean.
Maybe this is a problem only if using LVM or ZFS.


Nice Catch ajgreeny, that is hitting it right on the head. I need to slow down a bit and include important details.

My grumpy old man syndrome is compulsive at times....:lolflag:

---

### Post by TheFu on 2024-05-12
> **ajgreeny said:**
>  I admit I have never used anything other than ext partitions, including ext2 ànd ext3; yes I've been using Ubuntu, now Xubuntu, for that long!

I can't imagine doing a system install that doesn't include a volume manager for added flexibility and capabilities.  BTW, I remember when ext2 was new.  For a long time, I used JFS so my file systems would be journaled.  I started using LVM around 2001 after using similar Veritas tools (VM and FS) at work on UNIX systems.  Once you get used to the flexibility that a proper volume manager provides, you'll never want to go back.

---

### Post by VMC on 2024-05-13
> **ajgreeny said:**
> There's been a few comments about the manual partitioning not working, at least I think that's what people mean.
Maybe this is a problem only if using LVM or ZFS.

Using ext4 I can confirm it is still easy to use manual partitioning reusing an  existing /home partition without formatting and creating  a new root partition.

I admit I have never used anything other than ext partitions, including ext2 ànd ext3; yes I've been using Ubuntu, now Xubuntu, for that long!

ext4, manual partitioning, format , install all root "/".  Never fails me... I'm as uncomplicated as my looks.

---

### Post by jacobjons on 2024-05-17
First time I installing Linux in roughly 30 years... Full transition from Win11pro... Smooth install, ZFS option selected. Out of the box, I didn't have any hardware or driver issues.

~ System info: Minisforum HX90, AMD Ryzen 9 5900HX, 32GB RAM, 1TB M.2 NVMe, 2x 1TB SSD.

I installed from a Vintoy usb drive with the 24-04 ubuntu desktop iso to my boot M.2 drive. 

*For Windows users, I believe the instructions for making a Vintoy usb drive and adding ISOs is more straight forward, or easier, to understand. Possibly worth inclusion to the documentation?*

Things I encountered, but have not yet researched:
- Even though I selected a full HD install, there is a grub partition. I suspect that I should have removed previous windows partitions before installing ubuntu, on my to resolve list for today.
- Not sure how to install software via GUI. I was able to identify programs from the snapstore website and follow their CLI instillation directions.

I'm sure there are things that I don't know I'm missing, but so far, loving the experience.

---

### Post by qyot27 on 2024-05-17
I always fresh install, but this time I was moving my /home partition to its own NVMe drive, so I had to use gparted in the normal Live session to copy/paste the partition into the new location and delete the old partition once I'd verified things were okay.  While I was at it, also expanded / on the old drive and created a small (~32GB) btrfs partition to experiment with as a shared partition with Windows 10.  That went smoothly, but it wasn't really part of the install process.

I can't remember if Ubuntu Budgie had moved to the new installer with 23.10, but I experienced no issues at all assigning my normal manual partitioning (all normal ext4 partitions).  The only weird thing was the logo change, as I hadn't seen it announced anywhere (and didn't see anyone mentioning it afterward, but I stopped checking after a week or so).

---

### Post by john-newton04 on 2024-05-17
Been using Ubuntu on and off since Warty (4.10). This was probably the smoothest install and working Ubuntu of any flavor - and also smoother than any other distro I've used over the years. (Even beats ChromeOS Flex.)

---

### Post by Tadaen_Sylvermane on 2024-05-17
I recently migrated both my desktop and server from Debian > Ubuntu. For both I did a chroot installation from the Debian side of Jammy. Then following the Debian method upgraded through each interim release Jammy > Kinetic > Lunar > Mantic > Noble. I'm pleased to say that both machines seem to be doing perfectly. Everything is working. No errors to speak of. Just a few minutes ago I saw the first error on my desktop, a timeshift error. I clicked send and that was that. It's running in the background now. Both are attached via my few licenses to Ubuntu Pro and I intend to leave them installed on Noble till the next LTS, or beyond. Depends on my mood.

I can't find a Gnome Shell theme I'm happy with. I'm trying to avoid PPA's and such if possible and keep my installation as pure as I can. I'm using only a very small number of Flatpak packages, Firefox + whatever is default through Snap. And everything else is either apt or manually compiled and installed to /usr/local to keep the system core clean.

I'm quite pleased at the stability thus far. With a few exceptions Ubuntu release upgrades have always been crap shoot in general for me usually on the negative side. In this case I effectively release upgraded 2 machines a total of 4 times each with nary a whisper.

Well done.

---

### Post by BBQdave on 2024-05-19
Had Debian 12 loaded. Decided to try Ubuntu 24.04 and WOW!

Fresh install was fast and smooth :) Loaded my data and I'll set to go.

I like that you can select a basic install, and later load the applications you use. Personal preference: I like that you can adjust colors and function with the DE. I have a background with multiple greys and selected sage for the highlight color. Very nice :)

Applications are fresh, sometimes a challenge with Debian. Ubuntu is very responsive and fast.

Ubuntu 24.04 is loaded on my *travel machine* and meets my needs perfectly :)

---

### Post by Dennis N on 2024-05-23
As mentioned in post #7, I Wanted to install Ubuntu 24.04 in an existing LV. This is impossible using the new Ubuntu Desktop Installer. As mentioned at the end of post #7, I hoped an in-place upgrade from an existing 23.10 would bypass this impossibility. 

Today, while using my Ubuntu 23.10, the "upgrade to new version" notice popped up (exactly 4 weeks after the 24.04 release date). I accepted the upgrade offer. 

Total time from "start the upgrade" to "restart" was 17 minutes, without any problems encountered.

Reboot and success! I now have Ubuntu 24.04 LTS installed, replacing Ubuntu 23.10 in its LV. 

No additional time needed for customizing or installing software. Everyting from 23.10 is still there and working as I left it.

---

### Post by TheFu on 2024-05-23
While an upgrade is an option, this method always leaves some "cruft" behind as different subsystems are replaced.
Last time I attempted to "upgrade" a system, it took 2.5 hours.  Since then, I've wiped and done fresh installs, then restored backup settings/data and loaded the prior packages into the new OS.  A few packages would be missing, but for the most part, the new system would be "mine" and feel like mine in under an hour.  Worst case, I might need to reload the OS in a month to clean out some cruft that the restore process included, but that only happened once across 15 systems, so the restore to new OS does generally work.   Er ... mostly. ;)

If the upgrade works as fast as you experienced, that would be surprising, but a pleasant surprise.  I suspect that my refusal to use non-LTS releases unless absolutely necessary (usually a hardware thing), could be why my upgrades take longer.  A system that's been used for 3 yrs is likely to have more cruft than a freshly installed N-1 release that is immediately migrated to the new LTS (N).

---

### Post by Dennis N on 2024-05-23
>  this method always leaves some "cruft" behind as different subsystems are replaced.

As a final step, the Software Updater does offer to remove unneeded packages. This may just involve running apt autoremove, I'm not sure. It's a "keep all" or "remove" all option (no pick and choose).  I always opt to remove all the unneeded packages.

The 17 minutes is correct as the elapsed time between those two points. I timed it so I could report it.

---

### Post by #&amp;thj^% on 2024-05-23
It still leaves a few things as cruft ie:
```
sudo apt autoremove --purge
[sudo] password for me: 
REMOVING:                       
  libatm1t64*  libpthread-stubs0-dev*  libunibreak5*  libwireplumber-0.4-0*

Summary:
  Upgrading: 0, Installing: 0, Removing: 4, Not Upgrading: 0
  Freed space: 1,340 kB

Continue? [Y/n] 
(Reading database ... 312546 files and directories currently installed.)
Removing libatm1t64:amd64 (1:2.5.1-5.1build1) ...
Removing libpthread-stubs0-dev:amd64 (0.4-1build3) ...
Removing libunibreak5:amd64 (5.1-2build1) ...
Removing libwireplumber-0.4-0:amd64 (0.4.17-1ubuntu4) ...
Processing triggers for libc-bin (2.39-0ubuntu8.1) ...

```
But I'm still picking through left-overs from the upgrade method, though it dose not seem to be as large with my previous upgrades left behind.

---

### Post by Dennis N on 2024-05-23
> It still leaves a few things as cruft
Well, I know that in the last step, 108 'obsolete' packages were removed. These were optional removals. I assume the updater just runs **apt autoremove**.

Also, at the start of the upgrade, is says 145 packages are going to be removed during the upgrade; 265 new packages will be installed. These are apparently not optional actions.

So 145 + 108 total packages removed, and 265 - 145 - 208 = -88, so 88 net fewer packages than I started with.

Running apt autoremove on the new 24.04 system, just 1 package is to be removed: mailcap

---

### Post by #&amp;thj^% on 2024-05-23
The point I was trying to convey is, It's getting better but still leaves a certain amount of old ".conf" behind and few others.

Clean Install is just that, "squeaky clean" no cob webs left to discover.....Just Bugs. LOL

Also your comparison between 23.10 to 24.04 is minimal anyway, like TheFu going to LTS to LTS leaves more than you would think,

---

### Post by guiverc on 2024-05-24
I'll give my latest experience on a system of mine  (was Ubuntu 23.10 Desktop): **Perfect** (*outside of operator forgetfulness*)

- hp prodesk 400 g1 sff (i5-4570, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)

I'd received notification on the box that upgrade to 24.04 was available, but I'd ignored it until today..   Booted into 23.10 [text] terminal, ensured I'd applied all updates, then `do-release-upgrade`... System upgraded fine.. a few prompts/questions, then i was asked to reboot

I reboot, and on switching to text terminal (*habit; I check at text terminal first to get a feel for how the system looks before I switch to GUI*) everything looked good, so switch to sddm/greeter & enter my password.

Alas here I only got 2x black screens & pointer :(, not what I expected (*I expected a desktop/wm session; LXQt actually*).. and here the box was ignored awhile..  until I had some ideas on what had gone wrong & where to look 

Turned out nothing had gone wrong :P, the last thing I'd used the box for was a support question about an `openbox` session (*yesterday or day before*), thus my last GUI login/session was openbox back on 23.10.  Once I'd logged out, and switched to something I use, all was great.

My desktop is a multi-desktop install, and all of Lubuntu (LXQt), Xubuntu (Xfce) & Ubuntu (GNOME) are as expected  (*openbox was too; I just forgotten I'd used it very recently & thus it was default*)..  I'm not talking about my primary machine here (*that box has been running oracular awhile now*) but a nearby secondary machine I can use if I want to use the *primary* box for QA or something else. Its only the 2nd or 3rd *release-upgrade* for that box; so it's not an old install. That install is rather bloated (*multi-desktop for starters*), but mostly Ubuntu repository packages.

---

### Post by TheFu on 2024-05-24
The poll is starting to be useful, but we need more than just 19 votes.  Only 10% had huge issues. That's encouraging considering all the possible wonky configurations there are in the world.

---

### Post by Tadaen_Sylvermane on 2024-05-24
An update. As of now everything is still great. I have however replaced the Snap Firefox with the Flatpak. I had to hunt for my downloads and thought they were getting lost or something. Till that type of thing is fixed I won't be using Snap browsers for sure.

---

### Post by captainmorgan6666 on 2024-08-13
Fresh install or upgrade from mantic does not work at all. Either it freezes during install, reboots during install with broken install, seems to successfully complete install and on reboot does not load UI shell and much more.

Environment: Mantic # System Details Report
---
```

## Report details
- **Date generated:**                              2024-08-13 07:52:00

## Hardware Information:
- **Hardware Model:**                              Apple Inc. MacPro6,1
- **Memory:**                                      32.0 GiB
- **Processor:**                                   Intel® Xeon® E5-1620 v2 × 8
- **Graphics:**                                    AMD Radeon&#8482; HD 7800 Series
- **Graphics 1:**                                  AMD Radeon&#8482; HD 7800 Series
- **Disk Capacity:**                               42.0 TB

## Software Information:
- **Firmware Version:**                            132.0.0.0.0
- **OS Name:**                                     Ubuntu 23.10
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               45.2
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.10.3-061003-generic

Graphics Driver
*-display                 
       description: VGA compatible controller
       product: Tahiti LE [Radeon HD 7870 XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:165 memory:80000000-8fffffff memory:a0700000-a073ffff ioport:3000(size=256) memory:a0740000-a075ffff
  *-display
       description: VGA compatible controller
       product: Tahiti LE [Radeon HD 7870 XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: /dev/fb0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=2560,1440
       resources: irq:167 memory:90000000-9fffffff memory:a0600000-a063ffff ioport:2000(size=256) memory:a0640000-a065ffff

Dmesg amdgpu

[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-6.10.3-061003-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro quiet splash radeon.si_support=0 amdgpu.si_support=1 idle=nomwait intel_idle.max_cstate=1 vt.handoff=7
[    0.085199] Kernel command line: BOOT_IMAGE=/vmlinuz-6.10.3-061003-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro quiet splash radeon.si_support=0 amdgpu.si_support=1 idle=nomwait intel_idle.max_cstate=1 vt.handoff=7
[   13.965217] [drm] amdgpu kernel modesetting enabled.
[   13.965584] amdgpu: Virtual CRAT table created for CPU
[   13.965639] amdgpu: Topology: Add CPU node
[   13.966193] amdgpu 0000:02:00.0: enabling device (0006 -> 0007)
[   13.966744] amdgpu 0000:02:00.0: amdgpu: Fetched VBIOS from VFCT
[   13.966761] amdgpu: ATOM BIOS: 113-C3861LA-029
[   13.966785] kfd kfd: amdgpu: TAHITI  not supported in kfd
[   13.966796] amdgpu 0000:02:00.0: amdgpu: Trusted Memory Zone (TMZ) feature not supported
[   13.969983] amdgpu 0000:02:00.0: amdgpu: VRAM: 3072M 0x000000F400000000 - 0x000000F4BFFFFFFF (3072M used)
[   13.969999] amdgpu 0000:02:00.0: amdgpu: GART: 1024M 0x000000FF00000000 - 0x000000FF3FFFFFFF
[   13.970226] [drm] amdgpu: 3072M of VRAM memory ready
[   13.970233] [drm] amdgpu: 16033M of GTT memory ready.
[   13.971472] amdgpu 0000:02:00.0: amdgpu: PCIE GART of 1024M enabled (table at 0x000000F400000000).
[   13.974631] [drm] amdgpu: dpm initialized
[   14.492623] amdgpu 0000:02:00.0: amdgpu: SE 2, SH per SE 2, CU per SH 8, active_cu_number 24
[   14.809349] amdgpu 0000:02:00.0: amdgpu: overdrive feature is not supported
[   14.809537] amdgpu 0000:02:00.0: amdgpu: Runtime PM not available
[   14.810132] [drm] Initialized amdgpu 3.57.0 20150101 for 0000:02:00.0 on minor 1
[   14.955224] amdgpu 0000:02:00.0: [drm] Cannot find any crtc or sizes
[   14.958332] amdgpu 0000:06:00.0: amdgpu: Fetched VBIOS from VFCT
[   14.958340] amdgpu: ATOM BIOS: 113-C3861LB-029
[   14.958358] kfd kfd: amdgpu: TAHITI  not supported in kfd
[   14.976713] amdgpu 0000:06:00.0: vgaarb: deactivate vga console
[   14.976720] amdgpu 0000:06:00.0: amdgpu: Trusted Memory Zone (TMZ) feature not supported
[   14.977856] amdgpu 0000:06:00.0: amdgpu: VRAM: 3072M 0x000000F400000000 - 0x000000F4BFFFFFFF (3072M used)
[   14.977861] amdgpu 0000:06:00.0: amdgpu: GART: 1024M 0x000000FF00000000 - 0x000000FF3FFFFFFF
[   14.978002] [drm] amdgpu: 3072M of VRAM memory ready
[   14.978006] [drm] amdgpu: 16033M of GTT memory ready.
[   14.979010] amdgpu 0000:06:00.0: amdgpu: PCIE GART of 1024M enabled (table at 0x000000F400000000).
[   14.980490] [drm] amdgpu: dpm initialized
[   15.098767] amdgpu 0000:02:00.0: [drm] Cannot find any crtc or sizes
[   15.237187] amdgpu 0000:02:00.0: [drm] Cannot find any crtc or sizes
[   15.476544] amdgpu 0000:06:00.0: amdgpu: SE 2, SH per SE 2, CU per SH 8, active_cu_number 24
[   15.793405] amdgpu 0000:06:00.0: amdgpu: overdrive feature is not supported
[   15.793622] amdgpu 0000:06:00.0: amdgpu: Runtime PM not available
[   15.795661] [drm] Initialized amdgpu 3.57.0 20150101 for 0000:06:00.0 on minor 2
[   16.016533] fbcon: amdgpudrmfb (fb0) is primary device
[   16.083069] amdgpu 0000:06:00.0: [drm] fb0: amdgpudrmfb frame buffer device
[   25.031265] Modules linked in: apple_gmux(+) fjes(-) hid_magicmouse(+) joydev input_leds apple_mfi_fastcharge mac_hid dm_multipath msr parport_pc ppdev lp parport efi_pstore dmi_sysfs ip_tables x_tables autofs4 btrfs blake2b_generic dm_crypt raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 amdgpu amdxcp drm_exec gpu_sched drm_buddy raid0 radeon uas video usb_storage wmi crct10dif_pclmul drm_suballoc_helper crc32_pclmul polyval_clmulni drm_ttm_helper polyval_generic ghash_clmulni_intel sha256_ssse3 ttm nvme sha1_ssse3 igb drm_display_helper nvme_core firewire_ohci dca ahci xhci_pci nvme_auth cec firewire_core libahci i2c_algo_bit thunderbolt crc_itu_t xhci_pci_renesas rc_core tg3 hid_generic usbhid hid aesni_intel crypto_simd cryptd

Dmesg Error
[   38.683811] gsd-power[2188]: segfault at 8 ip 0000705eb1074d80 sp 00007ffd7bfa1c80 error 4 in libupower-glib.so.3.1.0[15d80,705eb1067000+e000] likely on CPU 3 (core 1, socket 0)
[   39.155264] gsd-power[2568]: segfault at 8 ip 000079c3862d7d80 sp 00007fffdd83dd40 error 4 in libupower-glib.so.3.1.0[15d80,79c3862ca000+e000] likely on CPU 5 (core 2, socket 0)
[   52.943730] gsd-power[3122]: segfault at 8 ip 00007ec82a732d80 sp 00007ffdc47bd3e0 error 4 in libupower-glib.so.3.1.0[15d80,7ec82a725000+e000] likely on CPU 1 (core 0, socket 0)
[   54.622099] gsd-power[3841]: segfault at 8 ip 00007f882d63bd80 sp 00007ffc951e7d90 error 4 in libupower-glib.so.3.1.0[15d80,7f882d62e000+e000] likely on CPU 6 (core 3, socket 0)
[   56.362050] gsd-power[3877]: segfault at 8 ip 000076367609cd80 sp 00007fff2539e4f0 error 4 in libupower-glib.so.3.1.0[15d80,76367608f000+e000] likely on CPU 3 (core 1, socket 0)
[   58.127826] gsd-power[4002]: segfault at 8 ip 00007523107a0d80 sp 00007ffc88c38e10 error 4 in libupower-glib.so.3.1.0[15d80,752310793000+e000] likely on CPU 0 (core 0, socket 0)
[   59.750884] gsd-power[4039]: segfault at 8 ip 00007b359633fd80 sp 00007ffc45736560 error 4 in libupower-glib.so.3.1.0[15d80,7b3596332000+e000] likely on CPU 4 (core 2, socket 0)
[   61.383396] gsd-power[4589]: segfault at 8 ip 00007a19ee7fcd80 sp 00007fffa27fccf0 error 4 in libupower-glib.so.3.1.0[15d80,7a19ee7ef000+e000] likely on CPU 4 (core 2, socket 0)
[   63.108337] gsd-power[5220]: segfault at 8 ip 0000797052c1bd80 sp 00007ffe53966570 error 4 in libupower-glib.so.3.1.0[15d80,797052c0e000+e000] likely on CPU 2 (core 1, socket 0)
[   65.114307] gsd-power[5558]: segfault at 8 ip 0000772113ed7d80 sp 00007ffdb9e60700 error 4 in libupower-glib.so.3.1.0[15d80,772113eca000+e000] likely on CPU 3 (core 1, socket 0)
[   66.904128] gsd-power[5961]: segfault at 8 ip 000078baf0fe9d80 sp 00007ffe9e2e3ce0 error 4 in libupower-glib.so.3.1.0[15d80,78baf0fdc000+e000] likely on CPU 2 (core 1, socket 0)
[   68.632791] gsd-power[6059]: segfault at 8 ip 00007ff0756d7d80 sp 00007ffe16f3c570 error 4 in libupower-glib.so.3.1.0[15d80,7ff0756ca000+e000] likely on CPU 4 (core 2, socket 0)

Dmesg Fail

[    0.419073] pci 0000:15:00.0: bridge window [io  size 0x1000]: failed to assign
[    0.419076] pci 0000:15:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419079] pci 0000:15:06.0: bridge window [io  size 0x1000]: failed to assign
[    0.419084] pci 0000:15:06.0: bridge window [io  size 0x1000]: failed to assign
[    0.419086] pci 0000:15:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419089] pci 0000:15:00.0: bridge window [io  size 0x1000]: failed to assign
[    0.419107] pci 0000:17:00.0: bridge window [io  size 0x2000]: failed to assign
[    0.419109] pci 0000:17:00.0: bridge window [io  size 0x2000]: failed to assign
[    0.419114] pci 0000:18:04.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419118] pci 0000:18:05.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419122] pci 0000:18:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419124] pci 0000:18:05.0: bridge window [io  size 0x1000]: failed to assign
[    0.419128] pci 0000:18:05.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419130] pci 0000:18:05.0: bridge window [io  size 0x1000]: failed to assign
[    0.419133] pci 0000:18:04.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419135] pci 0000:18:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419263] pci 0000:3a:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419266] pci 0000:3a:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419481] pci 0000:5c:00.0: bridge window [io  size 0x1000]: failed to assign
[    0.419483] pci 0000:5c:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419486] pci 0000:5c:06.0: bridge window [io  size 0x1000]: failed to assign
[    0.419489] pci 0000:5c:06.0: bridge window [io  size 0x1000]: failed to assign
[    0.419491] pci 0000:5c:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419494] pci 0000:5c:00.0: bridge window [io  size 0x1000]: failed to assign
[    0.419509] pci 0000:5e:00.0: bridge window [io  size 0x2000]: failed to assign
[    0.419512] pci 0000:5e:00.0: bridge window [io  size 0x2000]: failed to assign
[    0.419515] pci 0000:5f:04.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419518] pci 0000:5f:04.0: bridge window [mem size 0x00200000 64bit pref]: failed to assign
[    0.419521] pci 0000:5f:05.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419524] pci 0000:5f:05.0: bridge window [mem size 0x00200000 64bit pref]: failed to assign
[    0.419526] pci 0000:5f:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419529] pci 0000:5f:05.0: bridge window [io  size 0x1000]: failed to assign
[    0.419532] pci 0000:5f:05.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419535] pci 0000:5f:05.0: bridge window [mem size 0x00200000 64bit pref]: failed to assign
[    0.419537] pci 0000:5f:05.0: bridge window [io  size 0x1000]: failed to assign
[    0.419540] pci 0000:5f:04.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419543] pci 0000:5f:04.0: bridge window [mem size 0x00200000 64bit pref]: failed to assign
[    0.419545] pci 0000:5f:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419832] pci 0000:a3:00.0: bridge window [io  size 0x1000]: failed to assign
[    0.419834] pci 0000:a3:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419836] pci 0000:a3:06.0: bridge window [io  size 0x1000]: failed to assign
[    0.419839] pci 0000:a3:06.0: bridge window [io  size 0x1000]: failed to assign
[    0.419842] pci 0000:a3:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419844] pci 0000:a3:00.0: bridge window [io  size 0x1000]: failed to assign
[    0.419862] pci 0000:a6:04.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419866] pci 0000:a6:05.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419870] pci 0000:a6:04.0: bridge window [io  size 0x1000]: failed to assign
[    0.419872] pci 0000:a6:05.0: bridge window [io  size 0x1000]: failed to assign
[    0.419875] pci 0000:a6:05.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419878] pci 0000:a6:05.0: bridge window [io  size 0x1000]: failed to assign
[    0.419880] pci 0000:a6:04.0: bridge window [mem size 0x00200000]: failed to assign
[    0.419883] pci 0000:a6:04.0: bridge window [io  size 0x1000]: failed to assign
[    1.639365] thunderbolt 0000:16:00.0: device link creation from 0000:15:00.0 failed
[    2.615781] thunderbolt 0000:5d:00.0: device link creation from 0000:5c:00.0 failed
[    3.199709] thunderbolt 0000:a4:00.0: device link creation from 0000:a3:00.0 failed
[    3.532219] ata1.00: failed to read native max address (err_mask=0x1)

Dmesg Broken
[    3.532228] ata1.00: HPA support seems broken, skipping HPA handling

Dmesg Kernel
[    0.000000] Linux version 6.10.3-061003-generic (kernel@sita) (x86_64-linux-gnu-gcc-14 (Ubuntu 14.1.0-5ubuntu1) 14.1.0, GNU ld (GNU Binutils for Ubuntu) 2.42.90.20240720) #202408030740 SMP PREEMPT_DYNAMIC Sat Aug  3 07:53:03 UTC 2024
[    0.084649] Booting paravirtualized kernel on bare hardware
[    0.085328] Unknown kernel command line parameters "splash BOOT_IMAGE=/vmlinuz-6.10.3-061003-generic", will be passed to user space.
[    0.173785] Memory: 32444280K/33524772K available (22528K kernel code, 4521K rwdata, 14236K rodata, 4916K init, 4708K bss, 1080232K reserved, 0K cma-reserved)
[    0.234472] MDS CPU bug present and SMT on, data leak possible. See [https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html](https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html) for more details.
[    0.669880] Loaded X.509 cert 'Build time autogenerated kernel key: acfe868aca82b94eea8937538239ff1de#######'
[    0.761743] Loaded X.509 cert 'Build time autogenerated kernel key: acfe868aca82b94eea8937538239ff1de#######'
[    0.801130] Freeing unused kernel image (initmem) memory: 4916K
[    0.801227] Write protecting the kernel read-only data: 36864k
[    0.801577] Freeing unused kernel image (rodata/data gap) memory: 100K
[    4.317718] [drm] radeon kernel modesetting enabled.
[   13.965217] [drm] amdgpu kernel modesetting enabled.
[   13.966419] [drm] initializing kernel modesetting (TAHITI 0x1002:0x679E 0x106B:0x0126 0x00).
[   14.958036] [drm] initializing kernel modesetting (TAHITI 0x1002:0x679E 0x106B:0x0125 0x00).
[   24.051902] systemd[1]: Listening on systemd-udevd-kernel.socket - udev Kernel Socket.
[   24.056553] systemd[1]: Mounting sys-kernel-debug.mount - Kernel Debug File System...
[   24.057308] systemd[1]: Mounting sys-kernel-tracing.mount - Kernel Trace File System...
[   24.081728] systemd[1]: Mounted sys-kernel-debug.mount - Kernel Debug File System.
[   24.082043] systemd[1]: Mounted sys-kernel-tracing.mount - Kernel Trace File System.
[   24.087689] systemd[1]: Mounting sys-kernel-config.mount - Kernel Configuration File System...
[   24.090176] systemd[1]: Mounted sys-kernel-config.mount - Kernel Configuration File System.

```

---

### Post by him610 on 2024-08-13
Had a spare, empty disk on a fairly new mini computer. Installed Xubuntu LTS 24.04 without any issues.

On second thought: I had an issue trying to *ssh* into the new installation. I posted a question in these forums and got three different good suggestions.

The installation itself went well.

---

### Post by Tadaen_Sylvermane on 2024-09-05
> An update. As of now everything is still great. I have however replaced  the Snap Firefox with the Flatpak. I had to hunt for my downloads and  thought they were getting lost or something. Till that type of thing is  fixed I won't be using Snap browsers for sure.

Refreshing my information on my post earlier. I found that Snap simply cannot comprehend symlinks in some cases. In my case I had a data partition and I symlinked everything other than my /home/$USER/.var which i bind mounted. Since it didn't know what to do with the symlink it would default to /run/user some nonsense. bind mounting my downloads folder solved this issue.

---

### Post by guiverc on 2024-09-05
Just an update, but *release-upgrades* aren't open any longer, with *noble* or 24.04 no longer appearing inside [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release)

[https://lists.ubuntu.com/archives/ubuntu-release/2024-September/006225.html](https://lists.ubuntu.com/archives/ubuntu-release/2024-September/006225.html)

Utkarsh Gupta of the Ubuntu Release team states> That's correct - the upgrade was disabled due to a critical bug in
ubuntu-release-upgrader in the way it's using the apt solver. This is
being worked on and as soon as this is fixed, we'll re-enable the
upgrades.

We're also working on an announcement post/mail so that people are aware. :)


---

### Post by Erik1984 on 2024-09-14
Upgrade notification started showing again in Kubuntu 22.04 and today I upgraded my Kubuntu to Noble. Everything went fine! Thanks to all the devs involved and of course the people testing and reporting bugs so others upgrade experiences are smooth.

---

### Post by zeke2135 on 2024-09-21
Upgraded four machines to 24.04.1 from 22.04.x - two desktops,  two headless machines running mainly mlnidlna and Minecraft servers and booting to run level 3. I have very basic installations and needs on these machines. Hardware is Intel Nuc for the desktops, and Gigabyte brix on the others. I didn't have any problems, and the upgrade retained the small resolved.conf changes I had made to get unqualified name resolution working. I ran the upgrade on the two headless machines over ssh, which is NOT recommended, and I backed up important data, but in my simple case the upgrade worked basically flawlessly. 

I don't know if this story provides any useful info other than giving an example of what's possible for pretty much a baseline situation.:P

---

### Post by dosh on 2024-10-04
Been a while since  had Linux (had ubuntu and few versions earlier a number off years ago). Downloaded onto Thumb drive. Went to set up a dual boot on my Dell Latitude with Windows 10. Went to install it could not find the hard drive. After working out the problem was the disk had Raid On rather than AHCI after swapping it over realised it couldn't find Windows. So after booting into Safe Mode in Windows I was able to change it over for Windows. The install went well. Have had problems with a few programs trying to install with Discover and run especially the game 0ad seems to be folder permissions and mixing up which folder is which in the install and run. Have posted elsewhere for help.

---

