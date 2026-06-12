---
title: "Vivid boots to emergency root shell"
date: 2015-04-09
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-04-09
Well after being on my Trusty partition all of yesterday,
I tried booting into Vivid only to have a root emergency mode.
Snapped a few Pictures.
This happens with all options in grub
eg recovery> systemd> or >upstart and 3 other kernel options
```
inxi -b
System:    Host: Mate-Aspire-M3300 Kernel: 4.0.0-040000rc7-lowlatency x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 15.04 vivid
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.12
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 4048.6GB (37.1% used)
Info:      Processes: 199 Uptime: 1:46 Memory: 558.7/5967.1MB
           Client: Shell (bash) inxi: 2.2.16
```

Checked /etc/default/grub but everything appears to be good.
Just encase someone else reports or confirms here is some of my hardware.
I can get to my desktop with control+d  from that promt;)

Thought I would also show my boot log 
Should a bug be filed?
```
[[32m  OK  [0m] Created slice system-ifup.slice.
[[32m  OK  [0m] Started Show Plymouth Boot Screen.
[[32m  OK  [0m] Reached target Sound Card.
[[32m  OK  [0m] Found device WDC_WD20EADS-00S2B0 5.
         Activating swap /dev/disk/by-uuid/5...4-c40f-47c4-a240-574bfa7ad5b4...
[[32m  OK  [0m] Activated swap /dev/disk/by-uuid/572ce044-c40f-47c4-a240-574bfa7ad5b4.
[[32m  OK  [0m] Reached target Swap.
[[32m  OK  [0m] Started udev Wait for Complete Device Initialization.
         Starting Copy rules generated while the root was ro...
[[32m  OK  [0m] Started Copy rules generated while the root was ro.
[   [31m*[1;31m*[0m[31m*[0m] A start job is running for File Sys... on Root Device (33s / no limit)
[K[[32m  OK  [0m] Started File System Check on Root Device.
         Starting Remount Root and Kernel File Systems...
[[32m  OK  [0m] Stopped target Graphical Interface.
[[32m  OK  [0m] Closed UUID daemon activation socket.
[[32m  OK  [0m] Stopped target Multi-User System.
[[32m  OK  [0m] Stopped Login Service.
[[32m  OK  [0m] Stopped LSB: automatic crash report generation.
[[32m  OK  [0m] Stopped LSB: set CPUFreq kernel parameters.
[[32m  OK  [0m] Stopped LSB: Load kernel modules needed to enable cpufreq scaling.
[[32m  OK  [0m] Stopped LSB: Cleans up any mess left by 0dns-up.
[[32m  OK  [0m] Stopped Deferred execution scheduler.
[[32m  OK  [0m] Stopped LSB: Start NTP daemon.
[[32m  OK  [0m] Stopped killswitch manager.
[[32m  OK  [0m] Stopped LSB: daemon to balance interrupts for SMP systems.
[[32m  OK  [0m] Stopped LSB: disk temperature monitoring daemon.
[[32m  OK  [0m] Stopped Restore /etc/resolv.conf if...ore the ppp link was shut down..
[[32m  OK  [0m] Stopped Run anacron jobs.
[[32m  OK  [0m] Stopped Enable support for additional executable binary formats.
[[32m  OK  [0m] Stopped crash report submission daemon.
[[32m  OK  [0m] Stopped LSB: Tool to automatically ... submit kernel crash signatures.
[[32m  OK  [0m] Reached target Timers.
[[32m  OK  [0m] Stopped monitor and control system power state.
[[32m  OK  [0m] Stopped LSB: PeerGuardian Linux - an IP Blocker.
[[32m  OK  [0m] Stopped Accounts Service.
[[32m  OK  [0m] Stopped LSB: Set the CPU Frequency Scaling governor to "ondemand".
[[32m  OK  [0m] Stopped getty on tty2-tty6 if dbus and logind are not available.
[[32m  OK  [0m] Stopped Make remote CUPS printers available locally.
[[32m  OK  [0m] Stopped Avahi mDNS/DNS-SD Stack.
[[32m  OK  [0m] Closed Avahi mDNS/DNS-SD Stack Activation Socket.
[[32m  OK  [0m] Stopped CUPS Scheduler.
[[32m  OK  [0m] Closed ACPID Listen Socket.
[[32m  OK  [0m] Stopped Regular background program processing daemon.
[[32m  OK  [0m] Stopped System Logging Service.
[[32m  OK  [0m] Stopped Privacy enhancing HTTP Proxy.
[[32m  OK  [0m] Closed CUPS Scheduler.
[[32m  OK  [0m] Stopped Modem Manager.
[[32m  OK  [0m] Stopped Wait for all "auto" /etc/ne...be up for network-online.target.
[[32m  OK  [0m] Stopped LSB: Speech Dispatcher.
[[32m  OK  [0m] Stopped Run Click system-level hooks.
[[32m  OK  [0m] Stopped Initialize hardware monitoring sensors.
[[32m  OK  [0m] Stopped Getty on tty1.
[[32m  OK  [0m] Stopped Wait for Plymouth Boot Screen to Quit.
[[32m  OK  [0m] Stopped /etc/rc.local Compatibility.
[[32m  OK  [0m] Reached target Login Prompts.
[[32m  OK  [0m] Stopped oFono Mobile telephony stack.
[[32m  OK  [0m] Stopped D-Bus System Message Bus.
[[32m  OK  [0m] Closed D-Bus System Message Bus Socket.
[[32m  OK  [0m] Stopped Cgroup management proxy.
[[32m  OK  [0m] Stopped Cgroup management daemon.
[[32m  OK  [0m] Closed Syslog Socket.
[[32m  OK  [0m] Stopped LSB: Starts The Onion Router daemon processes.
[[32m  OK  [0m] Stopped Light Display Manager.
[[32m  OK  [0m] Stopped Permit User Sessions.
[[32m  OK  [0m] Stopped LSB: Openvpn VPN service.
[[32m  OK  [0m] Stopped LSB: Record successful boot for GRUB.
[[32m  OK  [0m] Stopped Network Manager Wait Online.
[[32m  OK  [0m] Stopped Network Manager.
[[32m  OK  [0m] Stopped target Basic System.
[[32m  OK  [0m] Stopped target System Initialization.
        [U] Starting Console System Startup Logging...
         Starting Restore Sound Card State...
[[32m  OK  [0m] Started Emergency Shell.
         Starting Emergency Shell...
[[32m  OK  [0m] Reached target Emergency Mode.[/U]
[[32m  OK  [0m] Reached target Sockets.
[[32m  OK  [0m] Reached target Paths.
[[32m  OK  [0m] Started Restore Sound Card State.
[[32m  OK  [0m] Started Remount Root and Kernel File Systems.
[[32m  OK  [0m] Reached target Local File Systems (Pre).
         Starting Load/Save Random Seed...
         Starting Flush Journal to Persistent Storage...
[[32m  OK  [0m] Reached target Local File Systems.
         Starting LSB: AppArmor initialization...
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting Set console keymap...
[[32m  OK  [0m] Reached target Remote File Systems.
[[32m  OK  [0m] Started Tell Plymouth To Write Out Runtime Data.
[[32m  OK  [0m] Started Load/Save Random Seed.
[[32m  OK  [0m] Started Flush Journal to Persistent Storage.
         Starting Create Volatile Files and Directories...
[[32m  OK  [0m] Started Console System Startup Logging.
[[32m  OK  [0m] Started Set console keymap.
[[32m  OK  [0m] Started Create Volatile Files and Directories.
[[32m  OK  [0m] Reached target System Time Synchronized.
         Starting Update UTMP about System Boot/Shutdown...
[[32m  OK  [0m] Started Update UTMP about System Boot/Shutdown.
         Starting Update UTMP about System Runlevel Changes...
[[32m  OK  [0m] Started Update UTMP about System Runlevel Changes.
[[32m  OK  [0m] Started LSB: AppArmor initialization.
         Starting LSB: Raise network interfaces....
[[32m  OK  [0m] Started ifup for eth0.
         Starting ifup for eth0...
[[32m  OK  [0m] Started LSB: Raise network interfaces..
[[32m  OK  [0m] Reached target Network.
[[32m  OK  [0m] Reached target Network is Online.

```

---

### Post by QDR06VV9 on 2015-04-09
So I could not find anything that gave me any clue as to what has happened, So I had a restore file form 3 days ago when all was still normal.(except for me) LOL
But after rebooting I found the same emergency root prompt which still let me get to my desktop via "control+d"
and no one else seems to be having the same issue.
And this folks is the fun in "bleeding edge" in testing
I need to go take care of my kittens now..
Cheers;)

---

### Post by ventrical on 2015-04-09
I had the "systemctl reboot" errors using systemD on a high octane overclocking single core.  And of course .. kernel panics on anything 5GHz or over. So I had to back peddle to 14.04 (upstart) and now I can get overclocks over 5GHz ... not sure if this is related at all.

 I have to go feed some processors now :) They are all hungry for code.:)

Regards..

---

### Post by QDR06VV9 on 2015-04-09
> **ventrical said:**
> I had the "systemctl reboot" errors using systemD on a high octane overclocking single core.  And of course .. kernel panics on anything 5GHz or over. So I had to back peddle to 14.04 (upstart) and now I can get overclocks over 5GHz ... not sure if this is related at all.

 I have to go feed some processors now :) They are all hungry for code.:)

Regards..
Thought about that but when checking logs I found had had reset mine back to ondemand!
But Thanks for checking in on me, Me and my kittens were getting a bit lonely here. LOL
Thanks my Friend talk to you soon.
Rick

---

### Post by QDR06VV9 on 2015-04-10
The Older I get the less memory I retain.
Ok got things sorted out forgot about some old kernels I had installed along the way.
Cleaned things up(Cruft) all is good now;)
I have done so much fiddling with this install and compiling that it was time to clean house!
But Ventrical you had reminded me about OC CPU,Forgot that I also was overclocking my GPU:oops:
Cavsfan over in the General forums talked about kernels not being removed with the autoremove command and I had also noticed that behaviour, leaveing behind for example
1 header from 4.0 rc4 and a couple of others I wont mention but all is Good.
Back to stock kernel now waiting for kernel 4.0  final.
Not that it matters much but I went back to upstart I do not expect my boot process to be fast due to my setup!
3 Hard Drives with 4 partitions and one External 2 TB Drive(Mainly for back-ups) not to mention USB Thumb drives that I often dont unplug during the boot cycle.
```
me@me-Aspire-M3300:~$ pidof systemd && echo "systemd" || echo "other"
other
me@me-Aspire-M3300:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1
sysvinit

```

---

### Post by ventrical on 2015-04-10
Thanks for the house cleaning reminder as well :) Lots of dust bunnies were building up in the corners and some stuff was growing legs!! :)lol

 I do not know why systemD has problems with overclocking , but , it does on one machine so far.   There is like this silly verbose error telling me that the thermal threshold has been broken .. etc.. or something like that .. (I'll have to check again) and it will kernel panic in upstart at over 5GHz but not on trusty 14.04.  But systemD WILL work at 4.9(n) GHz with 15.04 but there are these two countdown scripts that come up upon bootup... so I'll keep an ryr on that. I doubt if I could do anything from now until release date with that PC .. as I already have other commits that are getting swept under the carpet :)

Regards..

---

### Post by Joel_Schrock on 2015-06-03
So I am having the same problem, only mine is not overclocked, etc, etc. and it is a fresh install. What do I do to force it to fix this issue? I've been nearly tearing my hair out for the last three days or so. I'm sure if I knew more about Ubuntu, I could understand the hidden instructions in the posts above...but that is not the case.

---

