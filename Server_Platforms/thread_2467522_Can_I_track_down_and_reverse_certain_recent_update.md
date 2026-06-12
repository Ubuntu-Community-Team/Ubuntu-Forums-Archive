---
title: "Can I track down and reverse certain recent updates?"
date: 2021-09-29
forum: Server Platforms
---

### Post by Heeter on 2021-09-29
Hi all

Last week I took a big amount of updates to my Ubuntu18LTS KVM server. Since the updates, I have been unable to restart the vms.

I am wondering since I haven't been able to fix the issue created, can I track down and reverse any certain updates?

I do believe it is the one that did something to my keyboard update, because I remember it asking me for which keyboard I wanted to use (Or something like that, looked like a fresh ubuntu install section of the keyboard settings)

Regards

---

### Post by TheFu on 2021-09-29
There are log files for all updates.  /var/log/apt/history*  <--- there should be compressed versions that get rotated monthly. The default seems to keep 12 months + the current month.

  or 

you can use your versioned backups to see what changed, day-by-day going back as long as you have versions.  Generally, I keep at least 90 days, but for high-risk systems like any public services (http/smtp/vpn), I'll keep 180 days.  With a good backup tool, those are surprisingly small.  For example, my email gateway with 180 days of versioned backups is 76MB total.  Since it is just a gateway, it doesn't actually have any data.  It is a receive and forward system. It only holds email if the main email server (which has ZERO internet access) is unavailable.  I do NOT backup /var/log on most systems.  That would make figuring out what an attacker did more difficult, but all the files necessary to recreate the system  (or move to a completely new system) in about 30-45 min are available.

---

### Post by Heeter on 2021-09-29
I am going to cry

Thank you for the help Fu.

---

### Post by ajgreeny on 2021-09-29
There have been some recent updates to various **libvirt** and **qemu** packages, on Sept 9th and again Sept 15th in UK, and presumably everywhere else, which could be the reason for your difficulty, though I have seen no problems with my system, Xubuntu 20.04, still using the 5.4.0-86 kernel.

Are you still using 18.04 as shown in your user info or have you moved on from that and not updated your forum profile?

Incidentally I found that information and the dates of upgrades very easily by running command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` with a further grep suffix to find **libvirt** and **qemu**, ie ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log | grep libvirt
```
Yet another of those incredibly useful but simple uses of the terminal and command line in Linux.

---

### Post by Heeter on 2021-09-29
Yes I am still on 18lts

Would that make a difference? Wow interesting

Thank you for your response, this is the best heads up I have gotten so far on several sites.

Fu has been trying really hard to help too

Regards

---

### Post by Heeter on 2021-09-29
I did those search parameters:

```

root@serv:/home/adminpc# grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log | grep libvirt
/var/log/dpkg.log:2021-09-27 17:14:50 upgrade libvirt-glib-1.0-0:amd64 1.0.0-1 3.0.0-1
/var/log/dpkg.log:2021-09-27 17:16:10 upgrade gir1.2-libvirt-glib-1.0:amd64 1.0.0-1 3.0.0-1

root@serv:/home/adminpc# grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log | grep qemu
/var/log/dpkg.log:2021-09-27 17:14:56 upgrade ipxe-qemu:all 1.0.0+git-20180124.fbe8c52d-0ubuntu2.2 1.0.0+git-20190109.133f4c4-0ubuntu3.2
/var/log/dpkg.log:2021-09-27 17:14:56 upgrade ipxe-qemu-256k-compat-efi-roms:all 1.0.0+git-20150424.a25a16d-0ubuntu2 1.0.0+git-20150424.a25a16d-0ubuntu4
/var/log/dpkg.log:2021-09-27 17:16:00 upgrade qemu:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:00 upgrade qemu-system-common:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:02 upgrade qemu-utils:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:02 upgrade qemu-block-extra:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:03 upgrade qemu-system:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:03 upgrade qemu-user-binfmt:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:03 upgrade qemu-user:amd64 1:2.11+dfsg-1ubuntu7.37 1:4.2-3ubuntu6.17
/var/log/dpkg.log:2021-09-27 17:16:14 upgrade qemu-slof:all 20170724+dfsg-1ubuntu1 20191209+dfsg-1
root@serv:/home/adminpc# 

```

Is there someway I can reverse these updates?

---

### Post by Heeter on 2021-09-29
I just took another update

```

root@serv:/home/adminpc# virsh start mailserv
error: Failed to start domain mailserv
error: internal error: qemu unexpectedly closed the monitor: 2021-09-30T02:38:03.800708Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(48FH).vmx-exit-load-perf-global-ctrl [bit 12]
2021-09-30T02:38:03.800801Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(490H).vmx-entry-load-perf-global-ctrl [bit 13]
2021-09-30T02:38:03.803123Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(48FH).vmx-exit-load-perf-global-ctrl [bit 12]
2021-09-30T02:38:03.803141Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(490H).vmx-entry-load-perf-global-ctrl [bit 13]
2021-09-30T02:38:03.911942Z qemu-system-x86_64: -vnc 0.0.0.0:0: could not read keymap file: 'en-us'

root@serv:/home/adminpc#

```

Looks like its getting worse

---

### Post by TheFu on 2021-09-30
I don't see any libvirt updates in my KVM hosts.
Here's what's installed:
```
$ dpkg -l libvirt*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name               Version        Architecture   Description
+++-==================-==============-==============-==========================================
ii  libvirt-bin        4.0.0-1ubuntu8 amd64          programs for the libvirt library
ii  libvirt-clients    4.0.0-1ubuntu8 amd64          Programs for the libvirt library
ii  libvirt-daemon     4.0.0-1ubuntu8 amd64          Virtualization daemon
ii  libvirt-daemon-sys 4.0.0-1ubuntu8 amd64          Libvirt daemon configuration files
ii  libvirt-glib-1.0-0 1.0.0-1        amd64          libvirt GLib and GObject mapping library
ii  libvirt0:amd64     4.0.0-1ubuntu8 amd64          library for interfacing with different vir
```

Also, my VNC is set to use  **-vnc 127.0.0.1:2 -device virtio-vga**
And I have the CPU set to match the host.

For qemu stuff, I'm on the same release as you.  I suspect it is a config issue, so all the reinstalling won't help.  There's nothing special about my keyboard stuff in the libvirt xml files.  They are all like this:
```
regulus.xml:    <input type='keyboard' bus='ps2'/>
```

For consoles (pure servers), my GPU is :
```
spam3.xml:      <model type='vmvga' vram='16384' heads='1'/>
```
for desktops, I use qxl/spice:
```
regulus.xml:      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
```

BTW, my regulus is for the star. I have hadar, romulus, icarus, and a few other star named systems.  Once setup all the systems at a job to be Mexican food related ... the first system arrived just before lunch and we decided to go out for TexMex. ;)  Burrito, Enchilada, Jalapeno, and the slowest was .... wait for it ... 







guacamole.
My workstation was named Tequila.

About a year later, we got a loaner, single CPU, old, AIX system.  It wasn't worthy of a name in the food, just called it POSC.  Since that time, I've had a posc on my network, always.  It is the oldest, slowest, least capable system.  Today, it is a laptop.

---

### Post by deadflowr on 2021-09-30
The qemu packages show they're moved up to the 20.04 versions, somehow.
What happened there?
Did your apt sources get changed?

---

### Post by Heeter on 2021-09-30
I can't tell looks the same

I guess that I have one more day to fix this.

I am trying now to upgrade to 20LTS

I did this:
```

root@serv:/home/adminpc# do-release-upgrade
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.
root@serv:/home/adminpc#

```

CAn someone let me know what I need to use for upgrading to 20LTS, do-release-upgrade doesn't want to work. Thank you all for being patient with me. Just trying to get this email server running for our workplace

---

### Post by ajgreeny on 2021-09-30
To be doubly sure what you are currently running let's see the output of command ```
lsb_release -a
```

---

### Post by deadflowr on 2021-09-30
What do your /etc/apt/sources.list show?

FTR this shows upgraded packages
```
/var/log/dpkg.log:2021-09-27 17:14:56 upgrade ipxe-qemu:all 1.0.0+git-20180124.fbe8c52d-0ubuntu2.2 **1.0.0+git-20190109.133f4c4-0ubuntu3.2**
/var/log/dpkg.log:2021-09-27 17:14:56 upgrade ipxe-qemu-256k-compat-efi-roms:all 1.0.0+git-20150424.a25a16d-0ubuntu2 **1.0.0+git-20150424.a25a16d-0ubuntu4**
/var/log/dpkg.log:2021-09-27 17:16:00 upgrade qemu:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:00 upgrade qemu-system-common:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:02 upgrade qemu-utils:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:02 upgrade qemu-block-extra:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:03 upgrade qemu-system:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:03 upgrade qemu-user-binfmt:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:03 upgrade qemu-user:amd64 1:2.11+dfsg-1ubuntu7.37 **1:4.2-3ubuntu6.17**
/var/log/dpkg.log:2021-09-27 17:16:14 upgrade qemu-slof:all 20170724+dfsg-1ubuntu1 **20191209+dfsg-1**
```
The bolded strings are focal packages, which s what it upgraded those to.

---

### Post by Heeter on 2021-09-30
Thank you for your help guys:

```

root@serv:/home/adminpc# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal
root@serv:/home/adminpc#

```


```

root@serv:/home/adminpc# cat /etc/apt/sources.list
# 

# deb cdrom:[Ubuntu-Server 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

# deb cdrom:[Ubuntu-Server 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic universe
deb http://ca.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
root@serv:/home/adminpc#

```

Regards and thank you guys again.

---

### Post by TheFu on 2021-09-30
Appears you have a 50% 18.04 system and a 50% 20.04 system.
Something isn't right.

I'd pave the road and start fresh.  "I say we take off and nuke the entire site from orbit. It's the only way to be sure.&#8221;

---

### Post by ajgreeny on 2021-09-30
> **TheFu said:**
> Appears you have a 50% 18.04 system and a 50% 20.04 system.
Something isn't right.

I'd pave the road and start fresh.  "I say we take off and nuke the entire site from orbit. It's the only way to be sure.”
Hmm!
Not sure that's correct. The active lines in your sources are all for focal and all the bionic lines and repos are commented out so I'm really baffled.
However, a new clean start may solve your problems.

I've never upgraded from version to version of my systems so can not really help much more with potential difficulties of version upgrades.

---

### Post by TheFu on 2021-09-30
> **ajgreeny said:**
> Hmm!
Not sure that's correct. The active lines in your sources are all for focal and all the bionic lines and repos are commented out so I'm really baffled.
However, a new clean start may solve your problems.

I've never upgraded from version to version of my systems so can not really help much more with potential difficulties of version upgrades.

I could be confusing Heeter's system with another post here that was all 18.04 the last 7 days.

I've upgraded a KVM host from 10.04 --> 12.04 --> 16.04 --> 18.04 without many issues.  Newer KVM/libvirt machine types still support the older machine types.   That host has been losing VMs the last 2+ yrs, since newer hardware on another system is 10x faster and has 2x more RAM.  That other system was loaded with 18.04 and is still running it.  For example, so systems:
```
<type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
<type arch='x86_64' machine='pc-1.0'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
<type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
```

The pc-1.0 is actually a Xen VM which I migrated from 2008 Xen to KVM in 2010-ish.
Oddly, I don't have any newer VMs, since I cleaned up all the play VMs for 21.04 a few days ago.

Hummmmm.   There's a bug: [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1902654](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1902654)
There is some information in the bug about keyboards and console types when a VM is migrated to  pc-i440fx-wily .... hummmmmm.
Basically, VMs don't like when the hypervisor goes from 18.04 --> 20.04 or later.

---

### Post by Heeter on 2021-09-30
Hey Guys,

Cannot thank you enough for all your input. I really do appreciate for all your quick responses. Means a lot right now, as I don't have too much time to get the mailserver running. 

Is there someway that I can try to just upgrade to 20LTS from this?

Just need to get the VMs backup for a couple of days until I can make a plan on fresh install. Need to anyways, the LVM partitioning on this setup needs to be rethought out too.

Regards

---

### Post by TheFu on 2021-09-30
be  sure to read the bug in my last post. 20.04 could make you have to create a new VM and reload the OS for the mailserver. No upgrade.

---

### Post by Heeter on 2021-09-30
> **TheFu said:**
> be  sure to read the bug in my last post. 20.04 could make you have to create a new VM and reload the OS for the mailserver. No upgrade.

Thank you Fu. Ugh, I misread the bug. I thought that by upgrading, that It would fix it. Good thing that you mentioned that.


](*,)


If any of you can assist me directly, please pm me, :(

---

### Post by ajgreeny on 2021-10-01
> **Heeter said:**
> Hey Guys,

<snip>

Is there someway that I can try to just upgrade to 20LTS from this?

Just need to get the VMs backup for a couple of days until I can make a plan on fresh install. Need to anyways, the LVM partitioning on this setup needs to be rethought out too.

Regards
From the terminal output you showed us ```
root@serv:/home/adminpc# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal
```
it appears that you are already using 20.04, the latest LTS version available, so your inability to boot the VMs is not related to that, unless it is a symptom of moving from 18.04 to 20.04 at some point in the past.
Do you know when you upgraded, or is that all hidden in a mysterious past that you can't remember?

---

### Post by TheFu on 2021-10-01
In the OP, 
> Last week I took a big amount of updates to my Ubuntu18LTS KVM server. Since the updates, I have been unable to restart the vms.
That seems to correlate with when the issue started.
The bug link above says that VMs created in 18.04 and earlier have problems migrating to 20.04 and later under specific situations.  I don't have any 20.04 VM hosts, so I don't know first hand what the exact issue is, but the bug does say something about older virtual motherboards being broken (which had some fixes) and the newer virtual motherboards fix some of the issues.  The console type and keyboard were the issues listed, which seems to map to what Heeter says in post #1 above.
> I do believe it is the one that did something to my keyboard update, because I remember it asking me for which keyboard I wanted to use (Or something like that, looked like a fresh ubuntu install section of the keyboard settings)

Because the repos say 20.04 now (I missed that, thanks for point it out), and last week he had 18.04, that seems relevant.

But we don't know.  I posted my VM XML stuff for the machine types and keyboard so that Heeter could check his.  Haven't see any response on that.

If my email server couldn't receive email for 1 day, I'd be freaking out. If it was work related, my boss would be freaking out.  Long ago, I decided to use an email gateway system which isn't overly complex and can be spun up almost anywhere in 30 minutes that would at least capture inbound email, even if we couldn't read it or reply.  Store and forward, eventually is a good thing rather than having clients see bounced emails, IMHO. That's what I suggested in post #2 above.  That would be my first suggestion.  I run the email gateway in an LXD container, so the overhead is small.  To be fair, I moved it from a full VM about a month ago. So far, so good.  The only down side is that getting the ipset firewall rules working inside lxd needed some extra manual care. Something related to it being a container. I think it is sorted now, but ipset does kick out kernel errors.

After email receipt is possible, then time is available to setup a proper email server.  Doubt I can help with that. We've been running Zimbra since 2008. It is huge and a hog - more than MS-Exchange, but I'm addicted to the enterprise features provided.  OTOH, no way would I put Zimbra directly on the internet.  Access is only possible via the email-gateway for in/out SMTP or by using out VPN for user access either for SMTPS, IMAPS or webmail. No VPN. No access. Period.

Anyway, that is my thought process. Could be wrong.

---

### Post by Heeter on 2021-10-01
> **ajgreeny said:**
> From the terminal output you showed us 
```
root@serv:/home/adminpc# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal
```
it appears that you are already using 20.04, the latest LTS version available, so your inability to boot the VMs is not related to that, unless it is a symptom of moving from 18.04 to 20.04 at some point in the past.
Do you know when you upgraded, or is that all hidden in a mysterious past that you can't remember?

Ugh, don't understand when server took update, it was 18LTS just yesterday morning honestly. There was a bunch of updates that were being held back, but opened up for install yesterday. So I am even more baffled

Mailserver vm has been down since last week, :(  ran out of time today people waiting for me, have the weekend to fix this.

I cannot find a dedicated qemu forums to ask there about this.

```

root@serv:/home/adminpc# virsh start mailserv
error: Failed to start domain mailserv
error: internal error: process exited while connecting to monitor: 2021-10-02T02:31:06.031257Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(48FH).vmx-exit-load-perf-global-ctrl [bit 12]
2021-10-02T02:31:06.031340Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(490H).vmx-entry-load-perf-global-ctrl [bit 13]
2021-10-02T02:31:06.033554Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(48FH).vmx-exit-load-perf-global-ctrl [bit 12]
2021-10-02T02:31:06.033574Z qemu-system-x86_64: warning: host doesn't support requested feature: MSR(490H).vmx-entry-load-perf-global-ctrl [bit 13]
2021-10-02T02:31:06.067380Z qemu-system-x86_64: -vnc 0.0.0.0:0: could not read keymap file: 'en-us'
root@serv:/home/adminpc#

```

Thank you all, for helping me and responding with ideas, I truly appreciate it. 

Regards

---

### Post by Heeter on 2021-10-02
Thank you for all your help guys

---

