---
title: "Ubuntu 22.04 - Anyone try it out yet?"
date: 2022-04-13
forum: Server Platforms
---

### Post by LHammonds on 2022-04-13
I found the [desktop download]("https://cdimage.ubuntu.com/daily-live/current/") (2022-04-09) but did not find a server download.

I installed the desktop version as a virtual machine (under vmware) and noticed a few things but did not get very far since the NIC could never automatically obtain an IP and setting it manually did not allow connection to the Internet.

I did not try very hard such as disabling the GUI manager and setting it up manually in the yaml due to time limitations.  Maybe I just messed something up during setup but figured I'd wait until I got hold of a server installer.

The partition setup looked a lot easier for the uninitiated but the "atomic" option was always easy to pick where it just used the whole hard drive in a big partition.  It got a bit dicey when trying to do my favorite setup using LVM and each of the major folders getting their own partition...but I saw NO option to add custom paths such as /bak.  Could only select from existing, well-known paths.  I went with the atomic option just so I could get past HD setup quickly since removing a partition such as root that was initially set to 2GB and found out it needed to be larger....when removing the 2GB partition, it left a 2GB hole and could not select that 2GB to re-use as part of a 6GB partition.  It seemed like I would have had to remove all partitions I setup after it in order to correct the "gap" created from deleting one.

Anyways, does anyone have a link to a server image if its available?

LHammonds

---

### Post by TheFu on 2022-04-13
[https://releases.ubuntu.com/22.04/](https://releases.ubuntu.com/22.04/) has desktop and server images.

A few good people here have said lots of complementary things about the 22.04 Server and stability. Without all the GUI stuff, the normal packages have been pretty stable for a few months, I hear.

I haven't looked at 22.04 yet. Perhaps in late June. 

As for partitioning and LVM, I've given up using the installer tools and have a little script that I pull over just after the installer gets started and has networking (I switch to a different terminal for this work).  Once all my LVs are just hold I like them, I switch back to the installer to connect the LV to the mount location.  Much less frustrating and faster.

Keep the release candidates updated using zsync daily, if you like. Not much is changing anymore.  The threats of firefox being a snap package are true. Urrrrg.

---

### Post by guiverc on 2022-04-13
I'd likely look at the ISO QA tracker for what is available if you can't find it otherwise.

- [http://iso.qa.ubuntu.com/qatracker/milestones/429/builds](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds)

or if you don't have a specific release in mind, a little higher namely just

- [http://iso.qa.ubuntu.com/qatracker/milestones/](http://iso.qa.ubuntu.com/qatracker/milestones/)


It'll show the current *daily* for Ubuntu Desktop varies on architecture; ie. 20220409 for *amd64*, 20220413 for *arm64* etc.  For Ubuntu Desktop on *amd64* there are also two ISOs to choose from (one with `ubiquity` and another using the *canary* installer)

I just completed my 3rd QA test on Lubuntu *jammy* for the day.

I've been using *jammy* for near six months now, as I use the *development* release on this box; and this box will *bump* to *kk* about 30 hours after release of *jammy* as 22.04 LTS.  

My system is multi-desktop & I use the default Ubuntu Desktop (GNOME) on occasion, but I'm happiest in either LXQt (Lubuntu) or Xfce (Xubuntu).  I have seen more changes in GNOME than the other more *stable* desktops; but that is normal (*only exception was in the cosmic cycle.... Lubuntu's change from LXDE to LXQt maybe described as 'eventful'..*)

---

### Post by gmc1 on 2022-04-14
Just upgraded from 20.4 LTS to 22.04 beta.
Biggest gripe (along with so many others) is Firefox on snap. It's soooo slow.  Takes about 30 secs to open. Previously a a .deb package it was lightening fast.

Looking to see if I can get the .deb file going otherwise might have to look at another flavor of linux.

---

### Post by TheFu on 2022-04-14
Sorry. I didn't mean to derail this thread by mentioning Desktop stuff.  

THIS THREAD IS ABOUT **22.04 SERVER**. No GUI. No GUI programs. LHammonds doesn't have any GUI on his servers.

---

### Post by LHammonds on 2022-04-17
> **TheFu said:**
> [https://releases.ubuntu.com/22.04/](https://releases.ubuntu.com/22.04/) has desktop and server images.
Thanks, that's what I was looking for.  I'll try it out to see if I can do my standard server setup with it or if I have to do some kind of workaround to get the partitions how I like it.

In the last version, I tried reducing my template image to less separate partitions but it only ended up byting me in the tail so I'm going back to full separation for 22.04.

**EDIT #1**: 22.04 Live installer is just as clunky as 20.04 Live installer in regards to partitions.  You have to do the "leave unformatted" trick in order to setup LVM with custom partitions.  Here are the steps I take to [create custom partitions with LVM]("https://ubuntuforums.org/showthread.php?t=2441984&page=2&p=13955557#post13955557").
**EDIT #2**: Correction, installer failed to work.  I did not have networking enabled and wonder if that played a part in the failure.

```

SnapRevision: 3243
SnapUpdated: False
SnapVersion: 22.02.2+git50.c51fa4c9
SourcePackage: subiquity
Title: install failed crashed with CalledProcessError
Traceback (most recent call last):
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtin/commands/main.py", line 202, in main
ret = args.func(args)
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 1886, in curthooks
builtin_curthooks(cfg, target, state)
install_kernel(cfg, target)
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtin/commands/curthooks.py", line 368, in install_kernel
distro.install_packages([kernel_package], target=target)
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtin/distro.py", line 423, in install_packages
return install_cmd('install', args=pkglist, opts=opts, target=target,
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtin/distroy.py", line 303, in run_pat_command
cmd_rv = inchroot.subp(cmd, env=env)
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtisn/util.py", line 780, in subp
return subp(*args, **kwargs)
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtisn/util.py", line 275, in subp
return _subp(*args, **kwargs)
File "/snap/subiquity/3243/lib/python3.8/site-packages/curtisn/util.py", line 139, in _subp
raise ProcessExecutionError(stdout=out, stderr=err,
curtin.util.ProcessExecutionError: Unexpected error while running command.

```

I tried to create the following with a 25GB HD:

1GB /boot

23GB LVG
 |- 6GB /root VG
 |- 0.5GB /home VG
 |- 0.5GB /srv VG
 |- 2GB /usr VG
 |- 2GB /var VG
 |- 1GB /tmp VG
 |- 2GB /bak VG

LHammonds

---

### Post by webbro-2 on 2022-04-21
Wish I could. I'm still quite a noob, who has distro-hopped more than I would like to say. I tried installing 22.04 on a Dell R210ii that is running 21.10. Using a USB, I get to the point where it asks if you want to boot from the HDD, or try Ubuntu Server, select the try option, it starts scrolling the boot data, then the monitor starts reporting that the input is beyond the monitors range capability.

Trying to figure out a fix. Too much old data comes up in my searches.

---

### Post by Doug S on 2022-04-21
I first tried to install 22.04 server on 2021.11.14, which was rather early in the release cycle. I tried as VM guests on both my main debian server and my test 20.04 Ubuntu server. It didn't work on either, but being so early in the cycle I wasn't that worried about it. I tried again today, and again on both host servers, and got the same results. Neither even get very far in booting, so I don't even get to the install or try option.

The commands used were:

 On my older i7-2600K main Debian server:

```
virt-install -n serv-jj -r 8192 \
--disk path=/home/doug/vm/serv-jj.img,bus=virtio,size=50 \
-c jammy-live-server-amd64-2022-04-21.iso \
--network bridge=br0,model=virtio,mac=52:54:00:27:1c:6e \
--video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4 -cpu SandyBridge
```

And on my newer i5-10600K Ubuntu 20.04 test server:

```
virt-install -n serv-jj -r 8192 \
--disk path=/home/doug/vm/serv-jj.img,bus=virtio,size=50 \
-c jammy-live-server-amd64-2022-04-21.iso \
--network bridge=br0,model=virtio,mac=52:54:00:27:1c:6e \
--video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```

Apparmor seems unhappy about something:

```
Apr 21 13:09:19 s19 kernel: [    6.587627] kauditd_printk_skb: 7 callbacks suppressed
Apr 21 13:09:19 s19 kernel: [    6.587629] audit: type=1400 audit(1650571759.556:18): apparmor="DENIED" operation="capable" profile="libvirtd" pid=1011 comm="libvirtd" capability=17  capname="sys_rawio"
Apr 21 16:32:56 s19 kernel: [12224.006949] audit: type=1400 audit(1650583976.370:19): apparmor="DENIED" operation="capable" profile="libvirtd" pid=1011 comm="libvirtd" capability=17  capname="sys_rawio"
Apr 21 16:32:56 s19 kernel: [12224.033213] audit: type=1400 audit(1650583976.397:20): apparmor="DENIED" operation="capable" profile="libvirtd" pid=1011 comm="libvirtd" capability=17  capname="sys_rawio"
Apr 21 16:32:57 s19 kernel: [12225.235556] audit: type=1400 audit(1650583977.599:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-937c569d-e72c-4795-82f3-c30e50d28264" pid=1789 comm="apparmor_parser"
Apr 21 16:32:57 s19 kernel: [12225.328188] audit: type=1400 audit(1650583977.691:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-937c569d-e72c-4795-82f3-c30e50d28264" pid=1793 comm="apparmor_parser"
Apr 21 16:32:57 s19 kernel: [12225.426331] audit: type=1400 audit(1650583977.790:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-937c569d-e72c-4795-82f3-c30e50d28264" pid=1797 comm="apparmor_parser"
Apr 21 16:32:57 s19 kernel: [12225.521598] audit: type=1400 audit(1650583977.885:24): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="libvirt-937c569d-e72c-4795-82f3-c30e50d28264" pid=1801 comm="apparmor_parser"
Apr 21 16:32:57 s19 kernel: [12225.536576] br0: port 2(vnet0) entered blocking state
Apr 21 16:32:57 s19 kernel: [12225.536593] br0: port 2(vnet0) entered disabled state
Apr 21 16:32:57 s19 kernel: [12225.536632] device vnet0 entered promiscuous mode
Apr 21 16:32:57 s19 kernel: [12225.536719] br0: port 2(vnet0) entered blocking state
Apr 21 16:32:57 s19 kernel: [12225.536722] br0: port 2(vnet0) entered forwarding state
Apr 21 16:32:58 s19 kernel: [12225.636426] audit: type=1400 audit(1650583978.000:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-937c569d-e72c-4795-82f3-c30e50d28264" pid=1816 comm="apparmor_parser"
```

I have never had a problem with my 22.04 Ubuntu desktop VM, installed with pretty much the same command.

Just chiming in on this thread, but probably should start my own thread.

EDIT: I forgot that I had already entered [a bug report]("https://bugs.launchpad.net/subiquity/+bug/1950914") about this, which one has to if they are filling in [a testing report]("http://iso.qa.ubuntu.com/qatracker/reports/bugs/1950914") on the QA tracker.
EDIT 2: I found another possibly related [bug report]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/1873803").

---

### Post by LHammonds on 2022-04-22
I just tried the official 22.04 release and got the exact same problem as earlier.

I cannot create a custom LVM without it failing.

hmmm...does not matter if I select "minimized" or not regarding the partition creation issue.

**EDIT:** Interesting...I avoid the "custom storage option" and select the default "use entire disk with LVM" and it works.  Am I the only one that wants to customize my server's partitions?

LHammonds

---

### Post by Tadaen_Sylvermane on 2022-04-22
I intend to be running a kvm virtual machine on my server for awhile to test it with a few services. I did a chroot install of focal then upgraded to jammy on my desktop the other night. Admittedly only a day now but if this last day or so is any indication server will be a treat. I'm very pleased thus far and expect more from server as it doesn't have the risk factors for instability that desktop does. it may replace my debian bullseye for that.

---

### Post by Doug S on 2022-04-26
> **Doug S said:**
> The commands used were:

 On my older i7-2600K main Debian server:

```
virt-install -n serv-jj -r 8192 \
--disk path=/home/doug/vm/serv-jj.img,bus=virtio,size=50 \
-c jammy-live-server-amd64-2022-04-21.iso \
--network bridge=br0,model=virtio,mac=52:54:00:27:1c:6e \
[COLOR="#FF0000"]--video=vmvga[/COLOR] --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4 -cpu SandyBridge
```

And on my newer i5-10600K Ubuntu 20.04 test server:

```
virt-install -n serv-jj -r 8192 \
--disk path=/home/doug/vm/serv-jj.img,bus=virtio,size=50 \
-c jammy-live-server-amd64-2022-04-21.iso \
--network bridge=br0,model=virtio,mac=52:54:00:27:1c:6e \
[COLOR="#FF0000"]--video=vmvga[/COLOR] --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```
EDIT: I forgot that I had already entered [a bug report]("https://bugs.launchpad.net/subiquity/+bug/1950914") about this, which one has to if they are filling in [a testing report]("http://iso.qa.ubuntu.com/qatracker/reports/bugs/1950914") on the QA tracker.

The issue was "[COLOR="#FF0000"]--video=vmvga[/COLOR]", even though that should work fine. I was able to proceed on both hosts by deleting the driver override. On the Ubuntu host it defaulted to "qxl", and on the Debian host it defaulted to "vga".

I was not me that figured this out, it was input on the above referenced bug report.

---

### Post by LHammonds on 2022-04-26
I found out why the desktop and server version of 22.04 was not getting an IP address (for my site).

When I used DHCP, it failed to work, there is very little in the Netplan YAML config...but however its configuring it on the back-end, it is incorrect....well, no longer matches Netplan rules being used.

If you configure a static IP and use the syntax as originally designed since Netplan was introduced in Ubuntu, you will also not be able to communicate over the network:

```

network:
  version: 2
  ethernets:
    ens160:
      dhcp4: false
      dhcp6: false
      addresses: [192.168.1.2/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8,1.1.1.1]

```

gateway4 / gateway6 has been removed and now the configs are no longer valid.  They now need to resemble something like this:

```

network:
  version: 2
  ethernets:
    ens160:
      dhcp4: false
      dhcp6: false
      addresses: [192.168.1.2/24]
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8,1.1.1.1]

```

Not sure what is going on with DHCP option not being able to set the route correctly but I now have a workaround for the installation not being able to setup netplan correctly and thought I'd share.

I could be doing something stupid something doesn't seem right with the installer.

**EDIT:** I did get the static IP configuration working during install but DHCP is still hosed.  Example of the manual settings that worked:
```

IPv4 Method: Manual
Subnet: 192.168.1.0/24
Address: 192.168.1.2
Gateway: 192.168.1.1
Name servers: 8.8.8.8,1,1,1,1
Search domains: 

```

LHammonds

---

### Post by LHammonds on 2022-04-26
I think I am starting to narrow down the problem with the installer handling custom partitions.

It seems to be related to the size of the partitions.  I created a single huge root partition and it worked.  But when I try to fine-tune separate partitions, it fails.  It NEVER says the partition is too small nor does the error message in the log state that either.

But when I am looking at the folder sizes of a finished "minimized" install, I see the /var taking up the most room but even doubling /var during install, it is still not working.

Seems the installation calculations are not dynamic.  I will continue testing but each attempt is eating up a lot of time.

Here is the final result I am looking to obtain:

```

Guided storage configuration - Select "Custom storage layout"
Storage configuration - Set the following and select Done:
 - Select "free space" -> Add GPT Partition, set the following and choose "Create":
 |- Size: 1G
 |- Format: ext4
 |- Mount: /boot
 - Select "free space" -> Add GPT Partition, set the following and choose "Create":
 |- Size: 25G
 |- Format: Leave unformatted
 - Select "Create volume group (LVM), set the following and choose "Create":
 |- Name: LVG
 |- [X] partition 3  30.000G
 |- [ ] Create encrypted volume
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: root
 |- Size: 4G
 |- Format: ext4
 |- Mount: /
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: home
 |- Size: 1G
 |- Format: ext4
 |- Mount: /home
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: srv
 |- Size: 1G
 |- Format: ext4
 |- Mount: /srv
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: usr
 |- Size: 2G    **[COLOR=#ff0000]<--- Turns out this value was too small after trial-n-error[/COLOR]**
 |- Format: ext4
 |- Mount: /usr
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: var
 |- Size: 4G
 |- Format: ext4
 |- Mount: /var
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: tmp
 |- Size: 2G
 |- Format: ext4
 |- Mount: Other -> /tmp
 - Select "free space" under the LVM volume group -> Create Logical Volume, set the following and choose "Create":
 |- Name: bak
 |- Size: 2G
 |- Format: ext4
 |- Mount: Other -> /bak
Confirm destruction action - Select Continue

```

**EDIT #1** - I used a 100GB disk and configured each partition as follows and it worked for "minimized" version (but EXTREMELY too much wasted space)
```

1GB boot
98 GB LVM
 |- 20G root
 |- 10G home
 |- 10G srv
 |- 10G usr
 |- 10G var
 |- 10G tmp
 |- 10G bak

```
So now that I know it can work the way I want, now comes the painful task of determining what is the actual "minimal" size needed for each partition "during install" (why does the installer fail at this task?  Strike that question, I don't care...it needs better error-proofing to handle sizing. Minimized vs not minimized is known before partition setup and thus should know the basic size requirements.  The software selection at the end should know if it will fit based on what was created.)

Here is the result of the "df -h" command immediately after install of a fresh 22.04 minimized server:
```

Filesystem                                                                                    Size  Used Avail Use% Mounted on
tmpfs                                                                                          98M  2.1M   96M   3% /run
/dev/mapper/LVG-root                                                                           20G  2.0G   17G  11% /
/dev/disk/by-id/dm-uuid-LVM-RGRReUfQkk215e83p6Lh3AWe8k1BSMvVF1DBeYN4ZhSghaBSkNGfuujWS1eubs1e  9.8G  2.0G  7.4G  21% /usr
tmpfs                                                                                         486M     0  486M   0% /dev/shm
tmpfs                                                                                         5.0M     0  5.0M   0% /run/lock
/dev/sda2                                                                                     974M  125M  782M  14% /boot
/dev/mapper/LVG-home                                                                          9.8G   48K  9.3G   1% /home
/dev/mapper/LVG-tmp                                                                           9.8G   52K  9.3G   1% /tmp
/dev/mapper/LVG-var                                                                           9.8G  223M  9.1G   3% /var
/dev/mapper/LVG-srv                                                                           9.8G   24K  9.3G   1% /srv
/dev/mapper/LVG-bak                                                                           9.8G   24K  9.3G   1% /bak
tmpfs                                                                                          98M  4.0K   98M   1% /run/user/1000

```

So this is the absolute minimum in use for "minimized" AFTER install (using the "df -h" command):
```

2.0G root
0.1G home
0.1G srv
2.0G usr
0.3G var
0.1G tmp
0.1G bak

```

**EDIT #2**: This sizing worked for "minimized" during install:
```

1GB boot
98 GB LVM
 |- 20G root
 |- 1G home
 |- 1G srv
 |- 5G usr
 |- 5G var
 |- 1G tmp
 |- 1G bak

```

**EDIT #3**: This sizing worked for "minimized" during install (**[COLOR=#00ff00]the current smallest size[/COLOR]**):
```

1GB boot
98 GB LVM
 |- 4G root
 |- 0.5G home
 |- 0.5G srv
 |- 3G usr
 |- 1G var
 |- 0.5G tmp
 |- 0.5G bak

```

**EDIT #4**: This sizing **[COLOR=#ff0000]failed[/COLOR]** for "minimized" during install:
```

1GB boot
98 GB LVM
 |- **[COLOR=#ff0000]3G[/COLOR]** root
 |- 0.5G home
 |- 0.5G srv
 |- 3G usr
 |- 1G var
 |- 0.5G tmp
 |- 0.5G bak

```

**EDIT #5**: Now that I found the minimal size requirements for "minimized" install, I will now look at the full size option.

So this is the absolute minimum in use for "full" AFTER install (using the "df -h" command):
```

2.0G root
0.1G home
0.1G srv
2.2G usr
0.5G var
0.1G tmp
0.1G bak

```

This sizing worked for "full" during install (**[COLOR=#00ff00]the current smallest size[/COLOR]**):
```

1GB boot
98 GB LVM
 |- 4G root
 |- 0.5G home
 |- 0.5G srv
 |- 3G usr
 |- 1G var
 |- 0.5G tmp
 |- 0.5G bak
```

The "minimized" version is a slight decrease in /var and /usr but either way, the minimum partition sizes can be treated as the same which will fit on a 10 GB disk

LHammonds

---

### Post by kevdog on 2022-04-28
Kudos to you LHammond -- I just upgraded my existing 6 Virtualized Ubuntu Servers from 20.04 to 22.04.  On one of the upgrades I found the netplan config file completely overwritted and blank. I'm not sure why that happened however I just edited the netplan config file - I'm using dhcp so it was pretty simple since I have the address assigned at the router level.  Thanks for the writeup however explaining the netplan syntax change -- really irks me when change just seems to be for change sake and no benefit.   apt-key is deprecated in 22.04 (it will still work but probably phased out).  It makes a difference if adding a repository such as docker.  They expect gpg keys in separate files now.  That was kind of a chore to work around -- other than that things seemingly work.   One last thing on the netplan thing -- I've made this comment many times -- what exactly is the purpose of netplan anyway since if uses systemd-networkd as a backend.  Why doesn't Ubuntu just ditch netplan and then you're free to configure networking via systemd-networkd config file (or files)? Syntax is nearly the same as netplan but it doesn't use yaml.  Really it makes not a lot of sense to me.

---

### Post by LHammonds on 2022-04-28
> **kevdog said:**
> I just upgraded my existing 6 Virtualized Ubuntu Servers from 20.04 to 22.04.
Upgrade?  As in an in-place upgrade?   Yikes, I never do that.  I like to make sure I can re-create the server with all the new versions and config files...then migrate the data over to make it run identical to the old version...then switch the IP around to make it production when ready.  But I have the luxury of doing this because all my servers run in a virtual environment...well, except my host OS...which has not been upgraded in years **half grin**

> **kevdog said:**
> really irks me when change just seems to be for change sake and no benefit.
gateway4 has apparently been deprecated for a while now...22.04 finally removed it.  I just never new about it.
The routes option lets you have [multiple IPs with multiple gateways]("https://netplan.io/examples/#using-multiple-addresses-with-multiple-gateways").
From my understanding, netplan is supposed to allow you to have a backend-agnostic system so you can switch out what is used on the backside for networking but the front-end configuration is exactly the same.  I guess the theory is that if all flavors of Linux use netplan, the config setup will be identical across all of them regardless of the backend system.
I don't really care because my setups are usually very basic.  I do not setup servers to be routers (yet).

> **kevdog said:**
> Why doesn't Ubuntu just ditch netplan and then you're free to configure networking via systemd-networkd config file (or files)?
From what I have read, netplan is supposed to allow for a more complex network configuration but I cannot speak about what is better...my junk is fairly simple.

Regarding the research I did yesterday on what partition sizes are "minimum" to keep the installer from crashing like a mad toddler, today's focus is on the reduction of the HD to minimal size.

My last test yesterday was reduction from 100GB to 20GB but it blew up.  I am doing more tests today to see if I just fat-fingered a value wrong yesterday (I was rushing the last test because it was after 5pm)

**EDIT #1**

```

25GB HD - Full server worked
1GB boot
15 GB LVM
 |- 4G root
 |- 0.5G home
 |- 0.5G srv
 |- 3G usr
 |- 1G var
 |- 1G tmp
 |- 2G bak

```

**EDIT #2** - I supposed I did a typo somewhere in the last test yesterday because the 20GB HD worked.  Continuing more tests.

```

20GB HD - Full server worked
1GB boot
15 GB LVM
 |- 4G root
 |- 0.5G home
 |- 0.5G srv
 |- 3G usr
 |- 1G var
 |- 1G tmp
 |- 2G bak

```

**EDIT #3** - I must have done a type yesterday because even this size HD worked.

```

[COLOR=#ff8c00]**15GB HD**[/COLOR] - Full server worked
[COLOR=#ff8c00]**1GB boot**[/COLOR]
[COLOR=#ff8c00]**14GB LVM**[/COLOR]
 |- **[COLOR=#ffa500]4G root[/COLOR]**
 |- [COLOR=#ff8c00]**0.5G home**[/COLOR]
 |- [COLOR=#ff8c00]**0.5G srv**[/COLOR]
 |- **[COLOR=#ff8c00]3G usr[/COLOR]**
 |- **[COLOR=#ff8c00]1G var[/COLOR]**
 |- **[COLOR=#ff8c00]1G tmp[/COLOR]**
 |- [COLOR=#ff8c00]**2G bak**[/COLOR]

```

The numbers above in bold orange is what I will consider a minimum size for an Ubuntu Server 22.04 installation for my base template that will be used for all my various servers in the future (MariaDB, Apache, NextCloud, Orthanc, etc.)

Remember, you can increase partition sizes relatively easy compared to reducing them which is why I like to start at the minimum.  I rollout a template with minimal sizes and increase depending on what service is pushing data to particular particular partitions for growth over time.

LHammonds

---

### Post by kevdog on 2022-04-28
@LHammonds -- so if I'm interpretting your post correctly -- are you saying 15Gb is the minimum HD space for an Ubuntu Server installation.  I see you're using an LVM -- I'm using a zvol -- however in theory these are volumes.  How much RAM are you dedicating to each server on your hypervisor?

---

### Post by LHammonds on 2022-04-28
> **kevdog said:**
> are you saying 15Gb is the minimum HD space for an Ubuntu Server installation.
No, I am saying that is the minimum for "my" configuration which creates separate storage volumes.  This add extra space for each volume but in my virtual environment, I can easily increase the size of any existing disk or add more disks.  You can probably use the atomic partition method and fit it on a 7GB disk...just check further up where I did a "df -h" command to see the total size of all data in use.
A bare-metal installation is handled a bit different though.  Adding another physical disk to an existing volume puts the entire volume at risk when (not if) one of the two disks fail.  In my virtual environment, my network storage has a vast amount of hard drives with multiple RAIDs.  Many disks can fail and my servers will continue running just fine.  There is nothing I need to do at the VM level...all disk replacements are done at the network storage level.

> **kevdog said:**
> How much RAM are you dedicating to each server on your hypervisor?
Each one start off with 1GB RAM and 1 Core from the template I use to roll them out.  Once the server is deployed from template, I adjust the name, IP address, RAM, CPU, storage and partition sizes to match the software and usage requirements.   For example, if I setup MariaDB, I'll increase the RAM a little and add an extra CPU.  I configure the database to run out of /opt so I increase the storage of that partition to hold the database(s) and also increase /bak to ensure it can hold the various backup iterations over time before they start falling off to the purge script.

---

### Post by Doug S on 2022-04-28
For what it's worth, my Ubuntu 22.04 Server VM installation disk usage information (no LVM, minimal install):

```
doug@serv-jj:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           796M  700K  795M   1% /run
/dev/vda2        49G  [COLOR="#FF0000"]6.3G[/COLOR]   41G  14% /
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           796M  4.0K  796M   1% /run/user/1000
```

---

