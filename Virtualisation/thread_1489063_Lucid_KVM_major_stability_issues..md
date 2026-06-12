---
title: "Lucid KVM major stability issues."
date: 2010-05-20
forum: Virtualisation
---

### Post by SergeiFranco on 2010-05-20
Hi,
We have made a huge mistake and ordered Dell R410 a year ago.
We used Debian Lenny with Xen on our production servers. These Dell R410 are not supported by Xen kernel (no network driver). I have spent weeks trying to get Xen work on it.
I have given up and install Ubuntu 9.04 with KVM. Which was later upgraded to Lucid.

These servers are plagued by stability issues.

For example:

Guest will dissipater randomly (segfault? without leaving anything in logs).

Network will drop out for a moment (creating split-brain with heartbeat).

Network will drop out completely.


The setup is default Lucid 64bit server install, which uses KVM in bridge mode. The problem been with Jaunty as well. 

All these problems occur under moderate disk usage (rsync activity for example).

Guests are debian lenny and ubuntu jaunty.
Hosts are Dell Poweredge R410 with 16GB Ram. Running software Raid1 with LVM on top. Disks are couple of months old WD 500GB.

The errors on guests are as following:
```

[423878.950832] INFO: task pdflush:23 blocked for more than 120 seconds.
[423878.954209] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[423878.957855] pdflush       D ffff88006acd3ca0     0    23      2
[423878.960959]  ffff88006acd3c90 0000000000000046 ffffffff80a65900 ffffffff80a65900
[423878.964347]  ffffffff80a65900 ffffffff80a65900 ffffffff80a65900 ffffffff80a65900
[423878.968174]  ffffffff80a65900 ffffffff80a65900 ffff88006d2b2cc0 ffff88003001c320
[423878.971697] Call Trace:
[423878.973375]  [<ffffffffa0144d4d>] xfs_buf_wait_unpin+0xbd/0x130 [xfs]
[423878.976220]  [<ffffffff8024a6f0>] ? default_wake_function+0x0/0x10
[423878.979104]  [<ffffffffa0144b57>] ? xfs_buf_rele+0x37/0xd0 [xfs]
[423878.981940]  [<ffffffffa0144e2d>] xfs_buf_iorequest+0x6d/0x90 [xfs]
[423878.984793]  [<ffffffffa0149ee5>] xfs_bdstrat_cb+0x35/0x60 [xfs]
[423878.987609]  [<ffffffffa01409cf>] xfs_bwrite+0x6f/0xf0 [xfs]
[423878.989205]  [<ffffffffa013b10f>] xfs_syncsub+0x13f/0x300 [xfs]
[423878.991434]  [<ffffffffa013b317>] xfs_sync+0x47/0x70 [xfs]
[423878.993643]  [<ffffffffa014b8b3>] xfs_fs_write_super+0x23/0x30 [xfs]
[423878.996378]  [<ffffffff802e99fc>] sync_supers+0x8c/0xe0
[423878.998578]  [<ffffffff802b80c2>] wb_kupdate+0x32/0x120
[423879.000772]  [<ffffffff802b99f6>] __pdflush+0x136/0x220
[423879.002789]  [<ffffffff802b9b36>] pdflush+0x56/0x60
[423879.005014]  [<ffffffff802b8090>] ? wb_kupdate+0x0/0x120
[423879.007964]  [<ffffffff802b9ae0>] ? pdflush+0x0/0x60
[423879.009693]  [<ffffffff80268689>] kthread+0x49/0x90
[423879.011313]  [<ffffffff80213979>] child_rip+0xa/0x11
[423879.012788]  [<ffffffff80268640>] ? kthread+0x0/0x90
[423879.014347]  [<ffffffff8021396f>] ? child_rip+0x0/0x11
[423887.233817] ata1: device not ready (errno=-16), forcing hardreset
[423887.236241] ata1: soft resetting link
[423887.467229] ata1.00: configured for MWDMA2
[423887.468727] ata1: EH complete
[423887.645648] sd 0:0:0:0: [sda] 12582912 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[423887.726022] sd 0:0:0:0: [sda] Write Protect is off
[423887.729317] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[423887.913874] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[429349.139745] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[429349.141514] ata1.00: cmd ca/00:08:67:c9:2f/00:00:00:00:00/e0 tag 0 dma 4096 out
[429349.141516]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[429349.145699] ata1.00: status: { DRDY }

```

And so on. 

Never had problems like that with Xen even if the guests where having load average of 100+. While with KVM rsync from one guest to another will cause this to happen on every guest on that machine.
Here is the example of guest definition:
```
<domain type='kvm'>
  <name>myguest</name>
  <memory>131072</memory>
  <currentMemory>131072</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='block' device='disk'>
      <source dev='/dev/vg00/myguest'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
```

As you can see we are using LVM for the guest (it would be very silly to use file in production)

We also use Xen style LVM without partition or boot loader and with external kernel, the load issue affects either of styles.

Right now we will decommission otherwise brand new servers and try to resolve this issue (most likely by buying intel network cards and installing Xen).

I can't believe other people use KVM in their production, perhaps they don't care if their guests crash in worst possible way (semi-dissapearing).

I am at lost here...

EDIT: also another extremely bad behaviour is that kvm machines are treated exactly like any other process, which means they can be swapped. Even though I did not overcommit memory, in many occasions I saw guest being swapped out, eg:
```

Mem:  16455628k total, 15651600k used,   804028k free,  3770560k buffers
Swap:  3903480k total,  1704884k used,  2198596k free,    22344k cached

```
In this case if I add up all the guests it works out 14Gb (which leaves 2Gb for host which is far more than sufficient).
 
I have vm_swappiness set to 0 ...

---

### Post by billycub on 2010-05-21
I am also having very frustrating networking problems with Lucid KVM. It's hard to pinpoint exactly what the issue is; here are the symptoms.

Setup:

- Lucid 64bit installed on dual quad-core (Intel) Dell Precision R710, 32Gb RAM.

- One KVM instance running Windows XP x64 with 16Gb RAM, using bridged networking.  Symptoms occur with both standard (rtl8139?) and virtio network drivers on Windows.

- Note, I am starting KVM from the command line instead of using libvirt & virt-manager, because I need to specify sockets/cores/threads for my CPU. Otherwise Windows XP only uses 2 CPUs.  (As a side note anyone know how to specify cores/sockets/threads in libvirt xml?)

The Problem:

The KVM image starts up fine, and I can remotely access it using VNC.  However, after a few minutes, the remote VNC session will freeze and then exit.  Sometimes I can reconnect, other times it seems gone forever.

However, if I look at the host hardware, the Windows image is still operating and I can interact with it without any trouble.  It seems to be just the networking that is getting hung up. 

An interesting, possibly related detail:  If I shut down the Windows image, the host machine's networking freezes up for many seconds just as the image is exiting.  After the exit is complete and KVM is completely shut down, I can ssh or VNC back into the host machine again without problems.

So, it seems like there is a serious network problem with KVM or bridged networking specifically.

I can't find any log outputs with useful errors.  I wish I knew more about networking; I don't even know which tools to use to try and diagnose exactly what's happening.  Are packets getting lost?  Is something timing out?  

Does anyone have ideas on what I should look at to help pinpoint the bug?

---

### Post by SergeiFranco on 2010-05-23
It looks like no-one has solutions.
Anyway the decision has been made to buy intel network cards, and ditch Ubuntu+KVM as it is obviously not ready for production (or anything more serious than running WinXP).

We will replace Ubuntu+KVM with Lenny+Xen as it is very stable and proven solution.

We cannot afford having machines die randomly, or worse split-brain and causing database corruption.

There are situation where heartbeat goes mental and sits at 100% cpu usage while split-brain in progress and causing havoc on our infrastructure.

All because KVM cannot handle disk IO.

---

### Post by paradoxbound on 2010-05-31
Are you using the "virtio" settings as described [here]("https://help.ubuntu.com/community/KVM/Networking#virtio") since the symptoms you describe seem very similar.

---

### Post by angriukas on 2010-06-01
> **paradoxbound said:**
> Are you using the "virtio" settings as described [here]("https://help.ubuntu.com/community/KVM/Networking#virtio") since the symptoms you describe seem very similar.

I have used virtio drivers for network and for disk (for WinXP/Win7 instances), unfortunately same behavior still exist. 
Network connection is interrupted from 2 seconds up to 10 seconds (it varry) on every guest shutdown and sometimes on guest start-up. There is no difference - running kvm manually or by using eucalyptus cloud.

---

### Post by alastair on 2010-07-28
This is a late reply, hopefully useful. Maybe to the original posters. I also have a new Dell R410 server at work.

My original plan was to install Debian Lenny + Xen, and host some Xen domU's. As said above, Lenny/Xen has been very stable and powerful for us so far.

Unfortunately, the R410 hardware is not very compatible with Lenny - the Broadcom network devices and the RAID card.

```
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet (rev 20)
01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet (rev 20)
03:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon] (rev 02)
```

Getting access to the network devices was OK (load firmware) in Debian 5.05 and later. But to get an installer to see any disks (whether RAID1 or not) needed a latest/daily installer from Debian Testing (Squeeze).

I tried to use Squeeze/Xen but found big problems - Xen stability was bad, host hangs on reboot and other issues. I obviously had real concerns about using Squeeze in a production setting, but was willing to consider it (as being Debian/Xen) - but these issues sealed it. I cannot rely on Squeeze/Xen unfortunately.

So, I installed Ubuntu Server 10:04 amd64 on the host and am now running a KVM Debian Lenny (32 bit) guest. I have had issues and concerns about KVM in the past - but after some testing, it seems to be running OK. It is now in production as our main engineering server (file,CVS,web,wiki etc.) and (fingers crossed) has remained stable.

---

### Post by sendmoreinfo on 2010-11-29
KVM does have problems, yeah.

The "networking freezes up for a few seconds" is likely Launchpad bug 579892 (fix released).

The "networking dies" may be Launchpad bug 579276 (triaged, some patches posted, relevant debian bug is fixed) or 633392 (not diagnosed yet).

Or, guests could freeze completely (even the serial console is dead); that seems to be a bug in kvm-clock clocksource.  Someone produced a useful wrapper to disable it: [http://people.debian.org/~paravoid/kvm-noclock-3.tar.gz](http://people.debian.org/~paravoid/kvm-noclock-3.tar.gz)

---

### Post by gdahlm on 2010-11-29
For the original poster although this is an old thread.

First are the WD drives green drives? if so does the r410 have the sas 6i or a PERC card?

The non RE (RAID EDITION) drives are of little use behind a raid card, they are configured to try and internaly fix errors, when they go away they can be gone for well over 10 seconds which causes the RAID adapter to think they are gone.  You can get away with this if you have the sas 6/ir as it is just a HBA

A few other things you may want to look into is first the IDE virtual disk driver is extremely low performance as it is a fully virtualized device.  This also causes issues with CPU load and disk wait.  I would try virtio block devices.

If you are using lvm backed storage you should also use "cache='none'"  This keeps the hypervisors file cache out of the way and it will dramatically reduce the disk latency.

Also note that linux has several "IO elevators" in which you can choose from.  The default is CFQ which stands for "completely fair queueing" and it works great on a workstation with bare disks but it is horrible if you are using a RAID card or a storage array.

I would recommend elevator on the hypervisor and noop on your linux based guests.

You can set this on the fly to test it before you commit to it.

------------------------------------------------------------------------------
#Script to change the IO elevator to deadline

for pth in /sys/block/{sd,dm}*/queue/scheduler
do
echo "deadline" > $pth 
done
------------------------------------------------------------------------------

All that said I was on fedora for libvirt+qemu-kvm until 10.10 but I have now converted all hosts over to 10.10 and I am very happy.

We have one dual quad core r710 running 6 oracle DB instances and 3 oracle app instances and the users are happier then they were on the old physicals.

Note to do that did require quite a bit of SAN hardware because disk IO is the limiter.

---

