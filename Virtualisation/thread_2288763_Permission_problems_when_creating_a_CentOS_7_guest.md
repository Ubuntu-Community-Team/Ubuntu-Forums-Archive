---
title: "Permission problems when creating a CentOS 7 guest in qemu/libvirt"
date: 2015-07-29
forum: Virtualisation
---

### Post by sfunk1x on 2015-07-29
I'm running Ubuntu 14.10 with qemu & libvirt-bin 1.2.8.

Currently, I'm getting the following error when I create a VM instance of RHEL7, via virt-manager:

```
Unable to complete install: 'internal error: process exited while connecting to monitor: 2015-07-29T21:18:18.516179Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/centos7_base.org.qemu.guest_agent.0,server,nowait: Failed to bind socket: Permission denied
2015-07-29T21:18:18.516227Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/centos7_base.org.qemu.guest_agent.0,server,nowait: chardev: opening backend "socket" failed
'
```

If I create just a generic container without specifying OS, it "works" - but I haven't bothered going further than bootup because I figured something wasn't right. My search-fu must be weak, too, because the only thread I've been able to find is [this]("https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1393842").

I'm fine if the answer is Ubuntu just uses old versions of libvirt, and I'll find another repo to pull newer packages from.

---

### Post by TheFu on 2015-07-29
Which graphics setup are you using?  Cirrus or VGA? Both of those work.
Which remote desktop setup did you select?  VNC, while slow, is easy to use.

Are you using virt-manager?

BTW, I'm running Cent 7.1 on an ubuntu 14.04 host (both without GUIs)  - no issues related to virtualization - just my lack of understanding the CentOS/RHEL changes to the way Linux works elsewhere are my only issues.

---

### Post by sfunk1x on 2015-07-29
Graphics? 'Default'
Remote Desktop? 'Default'

Using virt-manager to create the instance (this is on my laptop, which is an intel i7 based rig with nvidia 860M).

---

### Post by sfunk1x on 2015-07-29
FWIW, this is the whole trace from details:

```

Unable to complete install: 'internal error: process exited while connecting to monitor: 2015-07-29T22:39:54.330608Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/centos7_base.org.qemu.guest_agent.0,server,nowait: Failed to bind socket: Permission denied
2015-07-29T22:39:54.330660Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/centos7_base.org.qemu.guest_agent.0,server,nowait: chardev: opening backend "socket" failed
'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 91, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1820, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 403, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 467, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3398, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: 2015-07-29T22:39:54.330608Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/centos7_base.org.qemu.guest_agent.0,server,nowait: Failed to bind socket: Permission denied
2015-07-29T22:39:54.330660Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/centos7_base.org.qemu.guest_agent.0,server,nowait: chardev: opening backend "socket" failed


```

---

### Post by TheFu on 2015-07-29
I have never used the "defaults", sorry.

If you like, please post the XML file for the VM.  **virsh dumpxml** does that.
Also - it shouldn't be an issue anymore, but in the old days we had to manually add our userid to the libvirtd group. Check that.

And check the system and libvirt log files to see what they say. Do this on both the VM host system and the system running virt-manager.

---

### Post by SeijiSensei on 2015-07-30
> **TheFu said:**
> just my lack of understanding the CentOS/RHEL changes to the way Linux works elsewhere are my only issues.

Are you talking about systemd, or something else?  Systemd is taking over the world, it appears, and is coming to Ubuntu too from what I've read.  I'm running a CentOS 7 system at Linode now to learn the differences.

Otherwise the only distinctive things about RH-flavored systems are the location of some files and the use of rpm/yum rather than dpkg/apt.

---

### Post by TheFu on 2015-07-30
Actually, CentOS/RHEL have different philosophies than Debian/Ubuntu and that is clear by the administrative requirements.  They aren't worse - just different.

I've been working through some RHEL 7.x training the last few months.

Cent requires a firewall rule for every service. If you setup a new service, opening the port(s) is mandatory because they are closed by default.

root - no need to say more.

/etc/sysconfig/ - chkconfig

They push FTP way too much. FTP should be of limited use, but it is still on the RHEL tests? OTOH, ssh isn't?  

Networking isn't enabled by default. If you setup a static IP, you still have to enable the network as a separate item.

I'm not too scared about systemd - I was, until attending a 2 hr class about it. I'm still worried that something so new is being forced on everyone to solve a problem that only 1% have. It should be optional for another 2 yrs as it becomes proven in production for early adopters. OTOH, the filtering and centralization for logging seems to be AMAZING!  Binary logs have good and bad aspects.

I do love the LVM + RAID + encryption installation options. They blow away Ubuntu's installer.

Anyway, just have to get used to the redhat way. They aren't dumb, that is certain.

BTW, systemd started in Ubuntu 14.04 ... slightly. Came across it when trying to disable the power button on a Chromebook - /etc/systemd/logind.conf is the file.

---

### Post by sfunk1x on 2015-07-30
> **TheFu said:**
> I have never used the "defaults", sorry.

If you like, please post the XML file for the VM.  **virsh dumpxml** does that.
Also - it shouldn't be an issue anymore, but in the old days we had to manually add our userid to the libvirtd group. Check that.

And check the system and libvirt log files to see what they say. Do this on both the VM host system and the system running virt-manager.


Account associations:

uid=1000(sfunk1x) gid=1000(sfunk1x) groups=1000(sfunk1x),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),125(sambashare),131(libvirtd)

I don't believe virsh dumpxml <domainname> will work, because the domain is never saved (the install is never started). The error occurs while it's initializing the VM, after you've clicked the 'Begin Installation' button in Virt-Manager. At least, I haven't figured out what the name/uuid/guid of the domain might be, as none are shown in Virt-Manager and there's nothing under /var/lib/lib-virt but several empty subdirs (sans dnsmasq files).

libvirtd.log:

```


2015-07-30 14:43:53.851+0000: 13345: info : libvirt version: 1.2.8, package: 1.2.8-0ubuntu11.8
2015-07-30 14:43:53.851+0000: 13345: warning : qemuOpenVhostNet:495 : Unable to open vhost-net. Opened so far 0, requested 1
2015-07-30 14:43:54.234+0000: 13345: error : qemuMonitorOpenUnix:309 : failed to connect to monitor socket: No such process
2015-07-30 14:43:54.234+0000: 13345: error : qemuProcessWaitForMonitor:2036 : internal error: process exited while connecting to monitor: 2015-07-30T14:43:54.048139Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/rhel7.org.qemu.guest_agent.0,server,nowait: Failed to bind socket: Permission denied
2015-07-30T14:43:54.048209Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/rhel7.org.qemu.guest_agent.0,server,nowait: chardev: opening backend "socket" failed

2015-07-30 14:44:06.943+0000: 13348: warning : qemuOpenVhostNet:495 : Unable to open vhost-net. Opened so far 0, requested 1
2015-07-30 14:44:07.327+0000: 13348: error : qemuMonitorOpenUnix:309 : failed to connect to monitor socket: No such process
2015-07-30 14:44:07.327+0000: 13348: error : qemuProcessWaitForMonitor:2036 : internal error: process exited while connecting to monitor: 2015-07-30T14:44:07.139998Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/rhel7.org.qemu.guest_agent.0,server,nowait: Failed to bind socket: Permission denied
2015-07-30T14:44:07.140043Z qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/rhel7.org.qemu.guest_agent.0,server,nowait: chardev: opening backend "socket" failed


```


Still not sure what it doesn't have permissions to. Surprised that this kind of blocker was able to reach the wild, frankly (this seems like a very direct method of installing rhel or centos as a vm in ubuntu). I'm able to complete the install if I set the OS type to rhel6, ubuntu, or generic. Probably several others. But I'll get the above error every single time I select RHEL 7.

---

### Post by TheFu on 2015-07-30
Humor me. Please. The installation process happens after the VM settings have been setup.
$ virsh dumpxml <vm-name>
BTW - it is stored in /etc/libvirt/....  they really shouldn't call it a domain. It is a vm-name. Too much confusion about what a "domain" is already and this doesn't help.

I've been doing VMs since the 1990s and have only seen this sort of issue (don't recall the exact errors from 3 yrs ago) when I didn't choose any console access method.

Also, please manually set **VMVGA** as the Video model and set the Display VNC to **VNC**, then
try again.

I've **never** needed to know the UUID for a vm-guest machine. Not once. It simply has never been an issue.

Not sure what the vnet-host issue is.  I always, always, always create a normal Linux bridge outside the VM-stuff and use that.  For a few years, the libvirt-created bridges weren't stable and had performance issues. It was just easier to make my own and use those.  That habit hasn't changed for me.

---

### Post by sfunk1x on 2015-07-30
> **TheFu said:**
> Humor me. Please. The installation process happens after the VM settings have been setup.
$ virsh dumpxml <vm-name>
BTW - it is stored in /etc/libvirt/....  they really shouldn't call it a domain. It is a vm-name. Too much confusion about what a "domain" is already and this doesn't help.


Ok, here ya go.

 ```


virsh dumpxml rhel7

error: failed to get domain 'rhel7'
error: Domain not found: no domain with matching name 'rhel7'


```

Contents of /etc/libvirt:

```

.
./libvirtd.conf
./lxc.conf
./storage
./storage/Downloads.xml
./storage/default.xml
./storage/autostart
./storage/autostart/Downloads.xml
./storage/autostart/default.xml
./hooks
./nwfilter
./nwfilter/no-ip-multicast.xml
./nwfilter/no-other-rarp-traffic.xml
./nwfilter/allow-arp.xml
./nwfilter/clean-traffic.xml
./nwfilter/no-mac-spoofing.xml
./nwfilter/allow-dhcp-server.xml
./nwfilter/allow-dhcp.xml
./nwfilter/no-arp-spoofing.xml
./nwfilter/qemu-announce-self.xml
./nwfilter/no-mac-broadcast.xml
./nwfilter/allow-ipv4.xml
./nwfilter/no-other-l2-traffic.xml
./nwfilter/allow-incoming-ipv4.xml
./nwfilter/no-arp-ip-spoofing.xml
./nwfilter/qemu-announce-self-rarp.xml
./nwfilter/no-ip-spoofing.xml
./nwfilter/no-arp-mac-spoofing.xml
./libvirt.conf
./qemu-lockd.conf
./virt-login-shell.conf
./qemu.conf
./virtlockd.conf
./qemu
./qemu/networks
./qemu/networks/default.xml
./qemu/networks/autostart
./qemu/networks/autostart/default.xml

```

VM was just called 'rhel7' - I'm not seeing any XMLs with contents that reference that. None of the autostart xml files reference the rhel7 VM in any way, and it's not shown in virt-manager (probably because it doesn't finish the creation process)

> **TheFu said:**
> 
I've been doing VMs since the 1990s and have only seen this sort of issue (don't recall the exact errors from 3 yrs ago) when I didn't choose any console access method.

Also, please manually set **VMVGA** as the Video model and set the Display VNC to **VNC**, then
try again.

I've **never** needed to know the UUID for a vm-guest machine. Not once. It simply has never been an issue.

Not sure what the vnet-host issue is.  I always, always, always create a normal Linux bridge outside the VM-stuff and use that.  For a few years, the libvirt-created bridges weren't stable and had performance issues. It was just easier to make my own and use those.  That habit hasn't changed for me.

Yep, had VNC set previously (and it's host default, so unless the GUI is REALLY broken...). Set display to VMVGA. Same issue.

Video of issue here:

[http://sfunk1x.com/virtmgrfail.mp4](http://sfunk1x.com/virtmgrfail.mp4)

---

### Post by TheFu on 2015-07-30
Where are the XML files for the working VMs?  They should be in /etc/libvirt/qemu.
Is **qemu-kvm** package installed?
```

$ dpkg -l |grep kvm
ii  qemu-kvm                              2.0.0+dfsg-2ubuntu1.14
```

The video failed to download.  Some sort of SSL error.

---

### Post by sfunk1x on 2015-07-30
> **TheFu said:**
> Where are the XML files for the working VMs?  They should be in /etc/libvirt/qemu.

What working VMs? I am still trying to create the centos7 VM with the rhel7 profile.

Contents of /var/lib/libvirt/qemu:

```

/var/lib/libvirt/qemu/
/var/lib/libvirt/qemu/channel
/var/lib/libvirt/qemu/channel/target
/var/lib/libvirt/qemu/dump
/var/lib/libvirt/qemu/snapshot
/var/lib/libvirt/qemu/save
/var/lib/libvirt/qemu/capabilities.monitor.sock

```


> **TheFu said:**
> 
Is **qemu-kvm** package installed?
```

$ dpkg -l |grep kvm
ii  qemu-kvm                              2.0.0+dfsg-2ubuntu1.14

```

The video failed to download.  Some sort of SSL error.

Hmm, not sure. Seems to work for everyone else.

```

ii  qemu-kvm                                             2.1+dfsg-4ubuntu6.7                                 amd64        QEMU Full virtualization on x86 hardware

```

Yes, qemu-kvm is installed. As I mentioned before, I can create a rhel6 VM just fine. But when I select rhel7 for profile, it fails.

Also, apparmor is complaining in the syslog:

```

Jul 30 09:49:54 blackbox kernel: [60186.283704] audit: type=1400 audit(1438274994.299:100): apparmor="DENIED" operation="open" profile="libvirt-0fb2b3ea-da19-40f0-a46f-33826b224aa6" name="/sys/devices/system/node/" pid=16973 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
Jul 30 09:49:54 blackbox kernel: [60186.283722] audit: type=1400 audit(1438274994.299:101): apparmor="DENIED" operation="open" profile="libvirt-0fb2b3ea-da19-40f0-a46f-33826b224aa6" name="/sys/devices/system/cpu/" pid=16973 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0

```

These denials don't occur when I change my profile selection from rhel7 to rhel6.

---

### Post by TheFu on 2015-07-30
Got the video - my normal way of grabbing that failed, but wget worked.
Don't use UEFI - stay with BIOS booting and try again, please.
Is there a reason UEFI is needed?

---

### Post by sfunk1x on 2015-07-30
It fails with either default or uefi.

---

### Post by TheFu on 2015-07-30
> **sfunk1x said:**
> It fails with either default or uefi.

I'll re-read the entire thread to see if there is something I've missed. 

I'll try to create a video on this side - so you can see the settings I use. I suspect that doesn't matter, it is probably a system issue.  I cannot do a "localhost" setup - none of my VM servers have any GUI - don't think that should matter.  Here are the pkgs I install:
```

$ sudo aptitude install \
openssh-server virt-manager \
   kvm qemu-kvm qemu-system \
   bridge-utils fail2ban
```

Always disable network-manager - gets in the way of bridge management. Not really an issue yet, based on the errors.

Unrelated - I love OBS, but find it isn't stable beyond about 90 min of recording on Linux. Have you seen that or is it rock solid always?

---

### Post by sfunk1x on 2015-07-30
> **TheFu said:**
> I'll re-read the entire thread to see if there is something I've missed. 

I'll try to create a video on this side - so you can see the settings I use. I suspect that doesn't matter, it is probably a system issue.  I cannot do a "localhost" setup - none of my VM servers have any GUI - don't think that should matter.  Here are the pkgs I install:
```

$ sudo aptitude install \
openssh-server virt-manager \
   kvm qemu-kvm qemu-system \
   bridge-utils fail2ban
```

Always disable network-manager - gets in the way of bridge management. Not really an issue yet, based on the errors.

Unrelated - I love OBS, but find it isn't stable beyond about 90 min of recording on Linux. Have you seen that or is it rock solid always?


I have a feeling that it's something to do specifically with that rhel7 profile. Other folks have complained about the same thing, and very similar errors, but I haven't seen a solution other potentially installing newer packages. I just wanted to avoid finding some random PPA to install the whole qemu chain from.

This setup was just on my laptop. I have a centos7 kvm host running on a nuc at home, and that seems to setup rhel7 profiles just fine, albeit, with no gui - and it's using the bridged networking as you've mentioned. My laptop setup was more or less for testing, so no need to expose them to the internet as a whole - ssh from my laptop to the instance, is all.

I haven't actually used OBS that much. I'm not a huge fan that it creates flv's. I actually converted the video with ffmpeg before I scp'd to my webhost. It's basically a "I need to record what I'm doing right now and this was the quickest solution" kind of deal. Handy that's its available, though.

edit:

Oh yeah, figured out how to NOT record an flv. Always check settings.

---

### Post by TheFu on 2015-07-30
For recording a screen - OBS is overkill. It is designed for video production with multiple video and audio sources.  The flv output does suck.

**simplescreenrecorder** is the easiest answer - or **ffmpeg** if you are comfortable with a long option list. Both will create h.264/aac in either mp4 or mkv containers.

---

### Post by TheFu on 2015-07-30
> **sfunk1x said:**
> I'm running Ubuntu 14.10 with qemu & libvirt-bin 1.2.8.


Support for 14.10 **ended** last week. 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Sorry - I should have noticed that earlier.

---

### Post by sfunk1x on 2015-07-30
Kind of a blunt method, but that basically fixed it. Needless to say I can't ever suggest anyone upgrade from 14.10 to 15.04, which is what I did on my laptop. After about an hour of trying to figure out the nvidia/prime configuration (because the upgrade left two other unsudes drivers installed, and I got a login video flicker/login loop).

But, now it works. Same workflow as I had originally, just creates it as expected.

---

