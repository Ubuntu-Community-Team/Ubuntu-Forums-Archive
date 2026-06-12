---
title: "Ubuntu &quot;live&quot; Server 20.04 - How to create custom partition /boot + LVM ???"
date: 2020-04-28
forum: Server Platforms
---

### Post by LHammonds on 2020-04-28
**EDIT #3**: Solved.  See [this post for exact steps]("https://ubuntuforums.org/showthread.php?t=2441984&p=13955557#post13955557") on how to accomplish this.  Let's hope Canonical can improve the installer the process is not so convoluted.

I must be an idiot because I cannot figure out the "live" installer for creating the following partition scheme:

/boot - 1G, ext4

LVG volume group
 - /root - 4G, ext4
 - /var - 2G, ext4
 - /home - 1G, ext4
 - /tmp - 1G, ext4
 - /bak - 1G, ext4

The problem is that I have a single 30 GB drive (Virtual Disk) and the storage configuration screen looks like this:

```
To continue you need to: Mount a filesystem at / and Select a boot disk
FILE SYSTEM SUMMARY
  No disks or partitions mounted.
AVAILABLE DEVICES
[ VBOX_HARDDISK_abc123, local disk, 30G ]
[ Create volume group (LVM) ]
USED DEVICES
  No used devices
```

If I select the "local disk" and choose "Use As Boot Device" then my option to create a volume group (LVM) or RAID goes away.

If I select "Create volume group," then the option is to use the entire disk which then removes the option to "select a boot disk" to continue.  I can create a /boot inside the LVM but that is NOT where I want it to reside AND you cannot select it to actually boot from that anyway.

To me, it seems like an infinite loop scenario.  What am I missing that will allow me to do what I have always been doing since Ubuntu 10.04 to use a /boot and and LVM for everything else?

**EDIT #1:**  And before anyone asks, yes...I could add a 1GB disk because it is a virtual machine but I am thinking about the process for a physical machine as well that only "presents" a single disk for the OS to use.

**EDIT #2**: I asked this question on [AskUbuntu]("https://askubuntu.com/questions/1234457/ubuntu-live-server-20-04-how-to-create-custom-partition-boot-lvm-on-a-sin") as well.


LHammonds

---

### Post by darkod on 2020-04-28
I don't have an answer for you, I would just like to sincerely say that I hope the standard -server- ISO will be published soon. Maybe it has slight "delay", the 20.04 is only few days old.

For 18.04 this -server- ISO exists, although I don't know when was it actually published compared to 18.04 release date.

I agree with you, I try to stay clear of -live-server- ISOs. Lets see if 20.04 will allow me to do that too.

---

### Post by darkod on 2020-04-28
Just stumbled onto this. Is this what I think it is, do they call it -legacy-server- now??? (sorry, no time to test in a VM right now)

[http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)

---

### Post by LHammonds on 2020-04-29
I will check out the legacy installer.  I am actually surprised to see it there though after having read this article about a week ago: [Server installer plans for 20.04]("https://discourse.ubuntu.com/t/server-installer-plans-for-20-04-lts/13631")

I would like to "check out" their new installer but if I cannot create a /boot outside of LVM AND create an LVM container, then what's the point of trying it when I cannot get past the first couple minutes of the install?  If you have LVM issues, you cannot boot the system when /boot is contained in it which can cause additional downtime I am not interested in.  The only times I have been really burned due to Linux bugs is at bootup (back in the days of Ubuntu 10.04).

**EDIT:** They are doing an excellent job of hiding that "legacy" ISO image.  I cannot find it anywhere in the "download" navigation on Ubuntu including the [alternative downloads](https://ubuntu.com/download/alternative-downloads) page.  Looking at one of the official [HTTP mirrors](http://mirror.waia.asn.au/ubuntu-releases/20.04/), I only see the live-server and desktop images.

Thanks,
LHammonds

---

### Post by Morbius1 on 2020-04-29
> **EDIT:** They are doing an excellent job of hiding that "legacy" ISO image.

> **Morbius1 said:**
> 
It turns out there are two isos you can download:

** The one that shows up when you search for it: [https://releases.ubuntu.com/20.04/](https://releases.ubuntu.com/20.04/)

** And the one available only if you have the special decoder ring: [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)
It's because of your missing decoder ring.

---

### Post by LHammonds on 2020-04-29
As I look into this "legacy" image, I will look over some of my old posts for server setups that I want to evaluate again:

[Difference between "live" and "alternative" for 18.04](https://ubuntuforums.org/showthread.php?t=2390785) - I noticed the cloud init in the live server image again so this will probably be relevant again.

[Pre-seed auto-installer](https://ubuntuforums.org/showthread.php?t=2381313) - If this legacy image is the old Debian installer, then I probably still cannot do the pre-seed with custom partitions.  I was REALLY looking forward to the [20.04 YAML-based system](https://wiki.ubuntu.com/FoundationsTeam/AutomatedServerInstalls) but if I cannot do what I want in the installer navigation, I bet I cannot make it work in the automated session.

LHammonds

---

### Post by LHammonds on 2020-05-01
Seems you need a decoder ring for the 18.04 non-live installer now as well.  I will have to update my 18.04 tutorials now. Here's the link:

[http://cdimage.ubuntu.com/releases/18.04.4/release/](http://cdimage.ubuntu.com/releases/18.04.4/release/)

**EDIT: **Unless that is the "live" server renamed to how the traditional CD was named...cause I don't see an image with "live" in the name.

LHammonds

---

### Post by LHammonds on 2020-05-02
Where would one go to request from the devs how *they* use the live installer to create a /boot partition and the rest in LVM on a single drive?

EDIT: I asked this question on [Ask Ubuntu](https://askubuntu.com/questions/1234457/ubuntu-live-server-20-04-how-to-create-custom-partition-boot-lvm-on-a-sin) as well.

LHammonds

---

### Post by Doug S on 2020-05-02
> **LHammonds said:**
> Where would one go to request from the devs how *they* use the live installer to create a /boot partition and the rest in LVM on a single drive?You could try the [Ubuntu server e-mail list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-server"). They are quite responsive.

Oh, I see you also did a question on askubuntu. Several canonical serverteam members do troll there.

Also the [Ubuntu server guide]("https://ubuntu.com/server/docs") has moved to discourse for 20.04, and the server team has been contributing quite a lot, as it was so very desperate for subject matter expert help (I didn't look up your issue though).

I had a the same troubles as you finding the "legacy" installer.

I find it odd, that I can dutifully fill out the testing tracker for Ubuntu server throughout the 20.04 release cycle, but it only uses the (now called) "legacy" installer. It was the same for 18.04, I had never heard of, or tried, the "new" installer before release day.

---

### Post by EuclideanCoffee on 2020-05-02
Omg, just seeing this now. This is totally going to put a wrench into our operations.

---

### Post by aljames2 on 2020-05-02
I was able to successfully install 20.04 Server with /boot in separate ext2 partition and LVs for root, home, usr, & var.  Mine is not a VM installation, it's on bare metal.  I used Gparted to wipe a HDD lying around and put in in my server box.  I burned the ISO below and was greeted with the grub "Install Ubuntu Server" option which led me to the options for "Manual" partition setup.

I followed your steps LHammonds in your 18.04 server install.

I downloaded from here:  [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)
This ISO in the list:  [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/ubuntu-20.04-legacy-server-amd64.iso](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/ubuntu-20.04-legacy-server-amd64.iso)

I did read through this some:  [https://discourse.ubuntu.com/t/installation-advanced/11577](https://discourse.ubuntu.com/t/installation-advanced/11577)

---

### Post by TheFu on 2020-05-02
Are you telling the installer included with the server ISO to update to the newest installer? That seemed to provide many more options.

For Mate-desktop, there's no real ability to control LVM unless you setup everything BEFORE launching the installer.  Couldn't even reduce the size of existing LVs.

---

### Post by LHammonds on 2020-05-03
> **Doug S said:**
> You could try the Ubuntu server e-mail list. They are quite responsive.

Also the Ubuntu server guide has moved to discourse for 20.04, and the server team has been contributing quite a lot, as it was so very desperate for subject matter expert help (I didn't look up your issue though).
Thanks.

> **Doug S said:**
> I find it odd, that I can dutifully fill out the testing tracker for Ubuntu server throughout the 20.04 release cycle, but it only uses the (now called) "legacy" installer. It was the same for 18.04, I had never heard of, or tried, the "new" installer before release day.
Same here, I felt like the rug was pulled out from under me.  I started documenting the 20.04 install before release using the "daily builds" but those were NOT the "live" installer which boggled my mind on release day.  I deleted all my prior documentation and tried to re-document the process with 20.04 only to find out I was stuck at the initial stages of install.  Then I was given the special [Cracker Jack secret decoder ring]("https://www.picclickimg.com/d/l400/pict/273679192509_/Vintage-1930s-Cracker-Jack-Toy-Tin-Fortune-Toy.jpg") to find the "legacy" installer.  And I groaned as I re-created the dox I had scrapped since I can currently only use the legacy image to accomplish what I need.

> **aljames2 said:**
> I downloaded from here: [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)
I know about the hidden "legacy server" installer noted earlier in the thread which is the Debian installer.  I already have [documentation underway]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273") on setting up 20.04 using the legacy image but since Canonical is trying to phase it out, we REALLY need to get the new "live" installer working for us.

> **TheFu said:**
> Are you telling the installer included with the server ISO to update to the newest installer?

I saw no option in the installer to "update." Here are the exact steps I take on the "live" installer process:


[LIST=1]
[*]Configure CD to use "ubuntu-20.04-live-server-amd64.iso" and power on. 
[*]Press ENTER to accept English 
[*]Press ENTER to accept English layout 
[*]Press ENTER to accept DHCP settings 
[*]Press ENTER to accept empty proxy 
[*]Press ENTER to accept default mirror URL 
[*]Press Down to highlight "Custom storage layout", press SPACEBAR, press Down to select "Done" and ENTER 
[*]Now I am sitting at the "Storage configuration" screen which I cannot get passed using desired configuration. 
[/LIST]


If I select the "local disk" to only way to add a /boot is to select "Add GPT Partition" and when I do that for /boot, it does select it as a boot device and create the 1G /boot partition but the options to create RAID and LVG are disabled.

If I select "Create volume group," I only have the option to select the entire HD which prevents adding any other partition (such as /boot or the bootable bios_grub partion) outside the LVM.

Thanks for the feedback so far everyone,
LHammonds

---

### Post by TheFu on 2020-05-03
Using the 20.04 "live" Server installer, the offer to get a new installer version happens ...

well, crap.  I don't see it now.  It was definitely there for some 20.04 ... perhaps that was in a desktop?  I know it existed for the 18.04 server last month, but I wouldn't mix up 18.04 server and 20.04 server installs.

Sorry for the wild turkey chase. Not seeing it now, so it must have never existed. ;(

---

### Post by LHammonds on 2020-05-03
> **TheFu said:**
> well, crap.  I don't see it now.(Maybe you had a net installer.  I never saw one since I think they were pointing us to get the 18.04 net installer but I don't even see that in the download navigation anymore.

One thing I "was" using to try and [setup a KVM cluster](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=270) using the "mini.iso" but I'm going to dump that project since it seems like I am re-creating an OS by using a bunch of individual command-line utilities.  I'm going to use Proxmox for my solution which bundles Debian as the OS so I won't be needing a "mini" image for Ubuntu for the immediate future.

LHammonds

---

### Post by bluexmas on 2020-05-04
Here we are again, 2 years later, checking the same live vs alternative installer (or legacy, the name they use) :)
Fortunatly for me, my upgrade cycle is 18 to 22, so I don’t need to put much efforts this release, but still, they announced they will drop the old installer for good on ubuntu 22, so I think we need to update our deployment procedures using this awful “live” iso....

---

### Post by aljames2 on 2020-05-04
This installer is crap.  Hopefully this is not another "false positive" O:)  if so my apologies.

I used GParted to start over & created my Fat32 /EFI partition.  Then I used the live installer on a USB and started with LHammonds steps.


[LIST=1]
[*]Press ENTER to accept English 
[*]Press ENTER to accept English layout 
[*]Press ENTER to accept DHCP settings 
[*]Press ENTER to accept empty proxy 
[*]Press ENTER to accept default mirror URL 
[/LIST]

At this point:

- Select Use entire disk & Set up this disk as an LVM group (This automatically sets aside 1G for /boot as ext4 outside the LVM)...it also automatically places root in a 4G LV within a default (stupidly named) VG.  These are the default things it sets up on the next screen.
- Therefore, to fix the VG name the way you want, you first tab down to the /root LV and delete it.  This frees up the VG to be edited the way you want.  Unfortunately I don't see where to adjust the size of the VG, only the name.  The VG occupies the whole disk.
- Next, highlight and enter on your VG device and select create logical volume and recreate your / root LV.
- Cycle through by entering on your VG again and keep creating LVs the way you want.

I saw nothing about RAID.

Apparently, the Custom Storage Layout only lets us create a variety of physical partitions, but not LVM.

Now at least I have an lsblk showing
```

&#9500;&#9472;sda1         8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2         8:2    0     1G  0 part /boot
&#9492;&#9472;sda3         8:3    0   930G  0 part 
  &#9500;&#9472;LVG-root 253:0    0     4G  0 lvm  /
  &#9500;&#9472;LVG-home 253:1    0     1G  0 lvm  /home
  &#9500;&#9472;LVG-var  253:2    0     4G  0 lvm  /var
  &#9492;&#9472;LVG-usr  253:3    0     4G  0 lvm  /usr

```

As for the VG occupying the rest of the space...if my LVM understanding is correct, we can now shrink the VG at the command line.

---

### Post by TheFu on 2020-05-05
lvreduce is not possible on a mounted LV. You'll need a Try Ubuntu flash or iso if running inside a VM.  And don't forget the -r option to skip the file system stuff. Let LVM reduce/increase the file system as needed.

---

### Post by darkod on 2020-05-05
The lack of flexibility during the "live" installer is something to worry about very much. Especially if they really do get rid of the "legacy" ISO for Ubuntu 22.

On another note, I haven't paid much attention how it was in earlier versions, but when you use a guided "use entire disk" method wouldn't you expect the VG to take the whole disk?

I would expect that from a guided method. The very flexible manual partitioning in the legacy installer is another thing, it allows almost total control of how you want to set up your partitioning.

---

### Post by LHammonds on 2020-05-09
Thanks to sxkx on AskUbuntu (a.k.a. e9dd370f on Ubuntu Hideout Discord).  This person has figured out how to manipulate the installer to handle this situation.

It is a bit odd but works for this situation.

Here are the exact steps to setup the partition how I have outlined:


[LIST=1]
[*]Configure CD to use "ubuntu-20.04-live-server-amd64.iso" and power on.
[*]Press ENTER to accept English
[*]Press ENTER to accept English layout
[*]Press ENTER to accept DHCP settings
[*]Press ENTER to accept empty proxy
[*]Press ENTER to accept default mirror URL
[*]Press Down to highlight "Custom storage layout", press SPACEBAR, press Down to select "Done" and ENTER
[*]Storage configuration - Add boot partition:
Select the available hard disk under "AVAILABLE DEVICES" and press ENTER
Select "Add GPT Partition" and Press ENTER
Size: 1G
Format: ext4
Mount /boot
Select "Create" and press ENTER
[*]Storage configuration - Add LVM partition:
Select the available hard disk under "AVAILABLE DEVICES" and press ENTER
Select "Add GPT Partition" and set the following, select "Create" and press ENTER
 - Size: 
 - Format: Leave unformatted
 - Mount
[*]Select "Create volume group (LVM)" and set these options and press ENTER on "Create":
Name: LVG
[X]: partition 3
[*]Root partition
Select "LVG (new)" and press ENTER
Select "Create Logical Volume" and press ENTER
Set the following and press ENTER on "Create":
 - Name: root
 - Size: 4G
 - Format: ext4
 - Mount: /
[*]var partition
Select "LVG (new)" and press ENTER
Select "Create Logical Volume" and press ENTER
Set the following and press ENTER on "Create":
 - Name: var
 - Size: 2G
 - Format: ext4
 - Mount: /var
[*]Home partition
Select "LVG (new)" and press ENTER
Select "Create Logical Volume" and press ENTER
Set the following and press ENTER on "Create":
 - Name: home
 - Size: 1G
 - Format: ext4
 - Mount: /home
[*]tmp partition
Select "LVG (new)" and press ENTER
Select "Create Logical Volume" and press ENTER
Set the following and press ENTER on "Create":
 - Name: tmp
 - Size: 1G
 - Format: ext4
 - Mount: Other, /tmp
[*]Bak partition
Select "LVG (new)" and press ENTER
Select "Create Logical Volume" and press ENTER
Set the following and press ENTER on "Create":
 - Name: bak
 - Size: 1G
 - Format: ext4
 - Mount: Other, /bak
[*]Select "Done" and press ENTER
[*]Confirm destructive action - Select "Continue" and press ENTER
[/LIST]

If you want to do the same thing but create a RAID, I setup a VM and added two 25 GB hard disks and these are the steps I took to add a /boot partition and the rest in RAID:


[LIST=1]
[*]Select "Custom storage layout"
[*]Select one of the available disks, add GPT partition, 1G, ext4, /boot
[*]Select the same disk again, add GPT partition, add the max amount of space, set format to "Leave unformatted"
[*]Select the next disk, add GPT partition, add the max amount of space, set format to "Leave unformatted"
[*]Select "Create software RAID (md)"
[*]Enjoy.
[/LIST]

---

