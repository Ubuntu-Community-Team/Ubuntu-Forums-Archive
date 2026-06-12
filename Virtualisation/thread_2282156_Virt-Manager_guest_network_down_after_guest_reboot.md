---
title: "Virt-Manager: guest network down after guest reboot"
date: 2015-06-12
forum: Virtualisation
---

### Post by Tim_Drub on 2015-06-12
Hi,

I have a strange problem when I reboot a guest in [FONT=courier new]virt-manager[/FONT]. When my host is booted and I start a VM everything works just fine. But if I reboot or halt the guest and it comes back up there is no network connection anymore inside the VM.

I tried disabling/enabling guest NIC and also did the same on the host, but only a reboot of the host brings back networking.

Some details on my host networking maybe relevant.
In my setup the host connects via WLAN and ethernet is disabled is network.manager. Guests either NAT to WLAN if no ethernet is available or [FONT=courier new]macvtap[/FONT] to [FONT=courier new]eth0[/FONT]. The reason is to not bring my host into customer networks while the virtualized clients are.

This is on Xubuntu 15.04 with [FONT=courier new]virt-manager[/FONT][FONT=courier new] 1.0.1[/FONT]. I did not have the this problem with the same setup in Xubuntu 14.10. It came with the new install of 15.04. 

Any ideas on how to troubleshoot this issue?
Thanks for your support.

Regards
Tim

---

### Post by TheFu on 2015-06-12
Use a manual bridge setup inside the /etc/network/interfaces.  libvirt bridges have always been flaky for me. Also, wifi networking will always be flaky. Wifi isn't as stable as humans believe it is. The computer sees the wild changes in bandwidth over wifi from second to second.

---

### Post by Tim_Drub on 2015-06-12
Thanks Fu for the quick reply.

Well, I don't have any issues with WLAN nor the host network connection, that works just fine.

Furthermore, I need to correct myself that this problem only occurs after a shutdown of the guest VM and then starting it again. Simply rebooting does not create the issue.

I do think this is related to virt-manager/libvirt/network-manager. E.g. if you change the network config of a VM in virt-manager a reboot is not sufficient to apply the new config, one needs to shutdown and restart the machine in order to switch from, e.g. NATed WLAN to MACVTAPed eth0 networking (something I always disliked as other virtualization tools are able to do this while running)

Also, this was working just fine in 14.10 and I have been working half a year without any issues.

I doubt this is related to bridging as the problem also occurs if the VM clients are configured to use NATed WLAN. Shutting down a NATed WLAN guest VM and starting it again, it loses network connection and so far the only way to bring it back is rebooting the host.

---

### Post by TheFu on 2015-06-12
As a method of troubleshooting ... does it work when you use virsh to manage the stop/start of the VM. In short, is the a libvirt issue or a virt-manager issue?

---

### Post by Tim_Drub on 2015-06-12
Good point, will try this.

And sorry again, there are just too many adjusting screws:
You were right, NATed WLAN is not an issue to the contrary what I asserted above.

So I did as you said and I created a classic bridge and the problem disappeared.

I managed to set this up through [FONT=courier new]network-manager[/FONT] what makes me quite happy as we're talking about my laptop here and I really didn't want to disable [FONT=courier new]network-manager[/FONT] as many documentations propose.

I then deleted the classic bridge and used the [FONT=courier new]macvtap[/FONT] device again for bridging to to [FONT=courier new]eth0[/FONT] and yep, the problem is back no matter if started through [FONT=courier new]virsh[/FONT] or [FONT=courier new]virt-manager[/FONT], btw.

Something I found out doing this is that the first time I start a VM the [FONT=courier new]macvtap[/FONT] device is created and its status is [FONT=courier new]up[/FONT] so [FONT=courier new]ifconfig[/FONT] shows it w/o the [FONT=courier new]-a[/FONT] flag. If teh VM is shutdown it seems as if the device is not correctly removed because it persists but the status is [FONT=courier new]down[/FONT]. When the VM is started again the status never changes to [FONT=courier new]up[/FONT] again.

Could it be that this is a libvirt bug on Xubuntu? I expect the [FONT=courier new]macvtap[/FONT] device should be dynamically added and removed again, no?

UPDATE: [FONT=courier new]macvtap[/FONT] device does get removed I just didn't wait long enough ;-) Still when restarted it is recreated but remains in status [FONT=courier new]down[/FONT].

UPDATE #2:
I now tried to bring up the interface manually with this command:
[FONT=courier new]sudo ip link set dev macvtap0 up[/FONT]

Which finishes just fine. But
[FONT=courier new]ip link show macvtap0
10: macvtap0@eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 500
    link/ether 52:54:00:59:19:10 brd ff:ff:ff:ff:ff:ff
[/FONT]
shows status still down. The following shows the [FONT=courier new]syslog[/FONT]

[SIZE=1][FONT=courier new]Jun 12 16:22:46 ... avahi-daemon[2422]: Joining mDNS multicast group on interface macvtap0.IPv6 with address f...:ff:...10.
Jun 12 16:22:46 ... avahi-daemon[2422]: New relevant interface macvtap0.IPv6 for mDNS.
Jun 12 16:22:46 ... avahi-daemon[2422]: Registering new address record for f...ff:...10 on macvtap0.*.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): found matching connection 'macvtap0'
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) starting connection 'macvtap0'
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 1 of 5 (Device Prepare) started...
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 2 of 5 (Device Configure) scheduled...
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 1 of 5 (Device Prepare) complete.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 2 of 5 (Device Configure) starting...
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 2 of 5 (Device Configure) successful.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 2 of 5 (Device Configure) complete.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 3 of 5 (IP Configure Start) started...
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Disabling autoconnect for connection 'macvtap0'.
Jun 12 16:22:46 ... NetworkManager[2439]: <warn> Activation (macvtap0) failed for connection 'macvtap0'
Jun 12 16:22:46 ... NetworkManager[2439]: <info> Activation (macvtap0) Stage 3 of 5 (IP Configure Start) complete.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): deactivating device (reason 'none') [0]
Jun 12 16:22:46 ... avahi-daemon[2422]: Withdrawing address record for f...:ff:f...10 on macvtap0.
Jun 12 16:22:46 ... avahi-daemon[2422]: Leaving mDNS multicast group on interface macvtap0.IPv6 with address f...10.
Jun 12 16:22:46 ... avahi-daemon[2422]: Interface macvtap0.IPv6 no longer relevant for mDNS.
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): device state change: disconnected -> unmanaged (reason 'none') [30 10 0]
Jun 12 16:22:46 ... NetworkManager[2439]: <info> (macvtap0): link disconnected
Jun 12 16:22:46 ... kernel: [  956.640589] IPv6: ADDRCONF(NETDEV_UP): macvtap0: link is not ready[/FONT][/SIZE]

---

### Post by TheFu on 2015-06-13
The libvirt package is the same regardless of Ubuntu version - provided it is the same release and the 32/64 bit.

I've never used network-manager and I'm old, so don't use the "ip" command (though I know it is newer) and I haven't tried suspending a VM in about 8 yrs because I never expected it to work right.

In short, you are doing things that probably should work, but server-VM users tend NOT to do. Time to file a bug?

---

### Post by Tim_Drub on 2015-06-18
OK, so I am back from a small Linux Mint Cinnamon odyssey. I was a little unsatisfied with a few things in Xunbut (e.g. splash screen with encrypted sys drive is blank and only becomes visible when pressing up/down arrows, LightDM logon screen is all grey when a second monitor is attched via DVI, etc.) so I thought I give Mint a try.

Well, it is even worse. Instead of some software hangs catched by Apport in Xubuntu I had complete system freezes only solved by hard system power off.

And the I could not get the macvtap device run at all. Not even when the VM was started for the first time. And the whole bridging thing I managed to setup in Xubuntu didn't not work either. So I quickly reinstalled Xubuntu where the problem is exactly as before. So I now know that this issue is even with a completely new installed system.

I have never filed a bug for Xubuntu nor Ubuntu so where should I address this issue to?

Thanks for your support.

Regards
Tim

---

