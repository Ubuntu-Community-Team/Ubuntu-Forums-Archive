---
title: "Excessive Increase in Power Consumption"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by donniezazen on 2012-09-17
Hi,

Has anyone noticed a high increase in power consumption in Quantal? I did a clean install yesterday and have a very minimal default setup. Power consumption is constantly reaching around 30W and system temperature lingers around 80C. I have a Core-i7-2620M CPU, 8GB RAM and Nvidia NVS4200/Intel HD 3000 graphic card. I have Bumblebee installed.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1"
```

Thanks.

---

### Post by dino99 on 2012-09-17
Phoronix has already written about the same increasing for now ;)

---

### Post by fictivetoast on 2012-09-21
+1, was hovering around 10W on 12.04, and am now up to 30W on 12.10.  
Lenovo X220 with Intel® Core™ i7-2620M CPU @ 2.70GHz × 4.

Anyone have any advice to bring consumption back down to reasonable levels?

---

### Post by jerrylamos on 2012-09-21
> **fictivetoast said:**
> +1, was hovering around 10W on 12.04, and am now up to 30W on 12.10.  
Lenovo X220 with Intel® Core™ i7-2620M CPU @ 2.70GHz × 4.

Anyone have any advice to bring consumption back down to reasonable levels?Yes, but I don't know if you'd do it.
sudo apt-get install lxde
This is a tower and power consumption no problem.  I check for bugs on Unity then pile LXDE on top because I spent 42 years working on high end main frame computers where speed and efficiency were serious goals.

Used to be you could run 2D however Ubuntu main thrust is 3D Unity Compiz.  I'll bet 12.10 Kubuntu would be distinctly better also.

Why? Because Compiz is designed to be running even when I've got full screen applications up and nothing Compiz does is even visible.  I assume they've got even more plans for Compiz main line code?

Curious if you'd be motivated to try 12.10 Kubuntu or Xubuntu or Lubuntu or Gnome ubuntu or ...

Actually I don't know anything about power consumption - I've got a notebook and a netbook as well but don't have a clue how to measure power.

---

### Post by cariboo on 2012-09-21
Have any of you tried [Jupiter]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")? I know it helped quite a bit on my Compaq netbook, when I was still using it.

---

### Post by effenberg0x0 on 2012-09-21
I have noticed that in machines that are using llvmpipe: In that case the CPU is being used more intensively (instead of passing the graphics load to the GPU).

To check:
```
sudo apt-get install nux-tools
/usr/lib/nux/unity_support_test -p
```

Regards,
Effenberg

---

### Post by dino99 on 2012-09-22
i suppose you mean:

sudo apt-get install nux-tools

(nux-utils is not an available package)

---

### Post by fictivetoast on 2012-09-22
Already running Jupiter and vm-writeback tweaks suggested by powertop, still getting insane power consumption...

---

### Post by effenberg0x0 on 2012-09-22
> **dino99 said:**
> i suppose you mean:

sudo apt-get install nux-tools

(nux-utils is not an available package)

You're right, thanks. I was definitely thinking of mesa-utils && glxgears -info. Old habits die hard.

Regards,
Effenberg

---

### Post by tista on 2012-09-22
Guys,

Now I'm using Quantal Gnome Remix Alpha2 on my VAIO Z (standard voltage i5 & sandy-bridge mobile), then I've also noticed such power-drain on QQ...

So... have everyone tried deeper rc6 states? :)

I've living with this grub parameters:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.powersave=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=4 i915.lvds_downclock=1 pcie_aspm=force iwlwifi.11n_disable=1 i915.i915_enable_fbc=1 intel-audio-powersave=true"
```
Yeah I mean "4" is deeper rc6 state for power-saving...
Then after booting on battery, powertop showed below :

```
The battery reports a discharge rate of 8.21 W
The estimated remaining time is 5 hours, 24 minutes

Summary: 130.1 wakeups/second,  1.9 GPU ops/seconds, 0.0 VFS ops/sec and 1.4% CP

                Usage       Events/s    Category       Description
             36.7%                      Device         Display backlight
              0.8 ms/s      38.9        Interrupt      [49] i915
            649.1 µs/s      15.0        Process        syndaemon -i 2.0 -K -R -t
            245.4 µs/s      10.0        Timer          hrtimer_wakeup
            160.6 µs/s       9.6        kWork          ieee80211_iface_work
              1.2 ms/s       9.4        Interrupt      [6] tasklet(softirq)
            230.8 µs/s       9.2        Timer          tick_sched_timer
            190.9 µs/s       8.3        Process        [rtsx-polling]
            141.8 µs/s       4.0        Process        /usr/lib/mozc/mozc_render
              2.6 ms/s       3.1        Process        /usr/bin/gnome-shell
              5.4 µs/s       2.1        kWork          blk_delay_work
              0.7 ms/s       2.0        Process        /usr/lib/upower/upowerd
            280.1 µs/s       1.8        Process        [jbd2/dm-2-8]
            193.2 µs/s       1.5        Interrupt      [7] sched(softirq)
```

Have anice day!!

tista

**PS**
Forgot to mention...
I've installed "cpufreqd". it could control frequency perfectly for my Z... :)
Now it seems better than granola or hopefully than jupiter!

---

### Post by mc4man on 2012-09-22
Likely not the orig. posted issue as it was 5 days ago but specific to the new unity-6.6
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054088](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054088)

---

### Post by robtygart on 2012-09-22
How do I view my power usage?

---

### Post by fictivetoast on 2012-09-22
> **robtygart said:**
> How do I view my power usage?

Open a terminal:  sudo apt-get install powertop
Then type sudo powertop in the terminal and give it a few seconds to collect usage data.

---

### Post by robtygart on 2012-09-22
Thank you

```
Summary: 171.4 wakeups/second,  0.0 GPU ops/seconds, 0.0 VFS ops/sec and 9.1% CPU use

                Usage       Events/s    Category       Description
            100.0%                      Device         Audio codec hwC0D0: Conexant
              8.3 ms/s      87.1        Process        /usr/bin/konsole
             17.6 ms/s      32.2        Process        kwin -session 10d9d46269000134792157500000018800000_1348334717_793253
             15.9 ms/s      12.0        Process        /usr/bin/plasma-desktop
             23.3 ms/s       8.8        Process        /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
              3.7 ms/s       6.1        Timer          tick_sched_timer
             14.9 µs/s       5.4        Process        [kworker/1:0]
              2.5 ms/s       3.9        Interrupt      [6] tasklet(softirq)
              3.3 ms/s       3.2        Process        /usr/bin/gkrellm --sm-client-id 10d9d46269000134818590200000018110047
              3.0 ms/s       3.4        Interrupt      [18] ohci_hcd:usb3
              0.7 ms/s       4.3        Timer          hrtimer_wakeup
              3.5 ms/s      0.25        Process        /usr/lib/thunderbird/thunderbird
            471.8 µs/s       2.3        Interrupt      [7] sched(softirq)
              2.0 ms/s      0.00        Interrupt      [16] nvidia
            130.5 µs/s       0.6        Process        /usr/bin/krunner
            394.5 µs/s       0.4        Interrupt      [9] RCU(softirq)
              1.1 ms/s      0.05        Process        powertop
              1.1 ms/s      0.00        Interrupt      [0] timer/1
              1.0 ms/s      0.00        Interrupt      [1] timer(softirq)
             52.0 µs/s      0.25        kWork          os_execute_work_item
            136.5 µs/s      0.15        Process        kdeinit4: kded4 [kdeinit]
            322.8 µs/s      0.10        Process        ksysguardd
            530.2 µs/s      0.00        Timer          wl_timer
             96.7 µs/s      0.15        Process        /usr/bin/virtuoso-t +foreground +configfile /tmp/virtuoso_hX1848.ini +wait
             68.9 µs/s      0.15        Interrupt      [9] acpi
             18.9 µs/s      0.15        Process        thunderbird
            392.6 µs/s      0.00        kWork          do_dbs_timer
             28.0 µs/s      0.10        Process        /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
            212.7 µs/s      0.00        Process        [ksoftirqd/1]
            206.4 µs/s      0.00        Interrupt      [19] eth1
            164.5 µs/s      0.00        Timer          nv_kern_rc_timer
            156.0 µs/s      0.00        Timer          delayed_work_timer_fn
             23.9 µs/s      0.05        Process        /usr/bin/klipper
             15.5 µs/s      0.05        Process        /usr/bin/bluedevil-monolithic
              9.9 µs/s      0.05        kWork          rt_worker_func
              7.7 µs/s      0.05        Timer          watchdog_timer_fn
              3.5 µs/s      0.05        Process        /usr/lib/rtkit/rtkit-daemon
              2.1 µs/s      0.05        Process        [flush-8:0]
              0.8 µs/s      0.05        Process        [watchdog/1]

```

---

### Post by fictivetoast on 2012-09-22
> **tista said:**
> Guys,

Now I'm using Quantal Gnome Remix Alpha2 on my VAIO Z (standard voltage i5 & sandy-bridge mobile), then I've also noticed such power-drain on QQ...

So... have everyone tried deeper rc6 states? :)

I've living with this grub parameters:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.powersave=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=4 i915.lvds_downclock=1 pcie_aspm=force iwlwifi.11n_disable=1 i915.i915_enable_fbc=1 intel-audio-powersave=true"
```
Yeah I mean "4" is deeper rc6 state for power-saving...
Then after booting on battery, powertop showed below :

```
The battery reports a discharge rate of 8.21 W
The estimated remaining time is 5 hours, 24 minutes

Summary: 130.1 wakeups/second,  1.9 GPU ops/seconds, 0.0 VFS ops/sec and 1.4% CP

                Usage       Events/s    Category       Description
             36.7%                      Device         Display backlight
              0.8 ms/s      38.9        Interrupt      [49] i915
            649.1 µs/s      15.0        Process        syndaemon -i 2.0 -K -R -t
            245.4 µs/s      10.0        Timer          hrtimer_wakeup
            160.6 µs/s       9.6        kWork          ieee80211_iface_work
              1.2 ms/s       9.4        Interrupt      [6] tasklet(softirq)
            230.8 µs/s       9.2        Timer          tick_sched_timer
            190.9 µs/s       8.3        Process        [rtsx-polling]
            141.8 µs/s       4.0        Process        /usr/lib/mozc/mozc_render
              2.6 ms/s       3.1        Process        /usr/bin/gnome-shell
              5.4 µs/s       2.1        kWork          blk_delay_work
              0.7 ms/s       2.0        Process        /usr/lib/upower/upowerd
            280.1 µs/s       1.8        Process        [jbd2/dm-2-8]
            193.2 µs/s       1.5        Interrupt      [7] sched(softirq)
```




I've passed the suggested grub paramaters on, but am seeing no savings whatsoever :

```

The battery reports a discharge rate of 30.9 W
The estimated remaining time is 2 hours, 51 minutes

Summary: 490.7 wakeups/second,  244.4 GPU ops/seconds, 0.0 VFS ops/sec and 3.5% CPU use

Power est.              Usage       Events/s    Category       Description
  12.7 W    100.0%                      Device         Display backlight
  11.9 W     34.6 pkts/s                Device         Network interface: wlan0 (rtl8192ce)
  1.89 W    100.0%                      Device         Audio codec hwC0D0: Conexant
  1.89 W    100.0%                      Device         Audio codec hwC0D3: Intel
  1.50 W    100.0%                      Device         Radio device: btusb
  354 mW    698.1 µs/s     568.4        Process        smfpd
 59.2 mW      9.4 ms/s      67.7        Process        /usr/lib/firefox/firefox
 5.79 mW      2.8 ms/s      43.3        Process        compiz
 3.37 mW    144.7 µs/s       2.1        Process        gnome-terminal
    0 mW      9.5 ms/s      0.00        kWork          ieee80211_scan_work
    0 mW      3.9 ms/s       4.0        Process        /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -backgro
    0 mW      1.2 ms/s       1.0        Process        /usr/lib/unity/unity-panel-service
    0 mW      1.1 ms/s      17.9        Interrupt      [48] i915
    0 mW      1.0 ms/s      15.4        Timer          hrtimer_wakeup
    0 mW    609.1 µs/s       0.9        Process        indicator-multiload
    0 mW    558.8 µs/s      0.10        Process        /usr/lib/indicator-appmenu/hud-service
    0 mW    538.4 µs/s      0.10        Process        powertop
    0 mW    337.2 µs/s      0.00        Interrupt      [9] RCU(softirq)
    0 mW    317.7 µs/s       0.7        Interrupt      [7] sched(softirq)
    0 mW    245.2 µs/s       1.8        Process        /usr/lib/x86_64-linux-gnu/indicator-application-service
    0 mW    242.4 µs/s      0.00        Interrupt      [40] SATA controller
    0 mW    216.4 µs/s       0.3        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
    0 mW    209.9 µs/s      0.05        kWork          e1000_watchdog_task
    0 mW    200.4 µs/s       0.4        Process        //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
    0 mW    189.9 µs/s      0.00        Interrupt      [4] block(softirq)
    0 mW    163.6 µs/s      0.00        kWork          rtl_watchdog_wq_callback
    0 mW    120.1 µs/s      0.25        Process        /usr/lib/bamf/bamfdaemon
    0 mW    108.4 µs/s       0.8        Process        /usr/lib/upower/upowerd
    0 mW    105.8 µs/s       1.6        Timer          tick_sched_timer
    0 mW     97.9 µs/s       0.4        Interrupt      [1] i8042
    0 mW     96.0 µs/s      0.00        Interrupt      [17] rtlwifi

```

---

### Post by tista on 2012-09-22
> **fictivetoast said:**
> I've passed the suggested grub paramaters on, but am seeing no savings whatsoever :

```

The battery reports a discharge rate of 30.9 W
The estimated remaining time is 2 hours, 51 minutes

Summary: 490.7 wakeups/second,  244.4 GPU ops/seconds, 0.0 VFS ops/sec and 3.5% CPU use

Power est.              Usage       Events/s    Category       Description
  12.7 W    100.0%                      Device         Display backlight
  11.9 W     34.6 pkts/s                Device         Network interface: wlan0 (rtl8192ce)
  1.89 W    100.0%                      Device         Audio codec hwC0D0: Conexant
  1.89 W    100.0%                      Device         Audio codec hwC0D3: Intel
  1.50 W    100.0%                      Device         Radio device: btusb
  354 mW    698.1 µs/s     568.4        Process        smfpd
 59.2 mW      9.4 ms/s      67.7        Process        /usr/lib/firefox/firefox
 5.79 mW      2.8 ms/s      43.3        Process        compiz
 3.37 mW    144.7 µs/s       2.1        Process        gnome-terminal
    0 mW      9.5 ms/s      0.00        kWork          ieee80211_scan_work
    0 mW      3.9 ms/s       4.0        Process        /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -backgro
    0 mW      1.2 ms/s       1.0        Process        /usr/lib/unity/unity-panel-service
    0 mW      1.1 ms/s      17.9        Interrupt      [48] i915
    0 mW      1.0 ms/s      15.4        Timer          hrtimer_wakeup
    0 mW    609.1 µs/s       0.9        Process        indicator-multiload
    0 mW    558.8 µs/s      0.10        Process        /usr/lib/indicator-appmenu/hud-service
    0 mW    538.4 µs/s      0.10        Process        powertop
    0 mW    337.2 µs/s      0.00        Interrupt      [9] RCU(softirq)
    0 mW    317.7 µs/s       0.7        Interrupt      [7] sched(softirq)
    0 mW    245.2 µs/s       1.8        Process        /usr/lib/x86_64-linux-gnu/indicator-application-service
    0 mW    242.4 µs/s      0.00        Interrupt      [40] SATA controller
    0 mW    216.4 µs/s       0.3        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
    0 mW    209.9 µs/s      0.05        kWork          e1000_watchdog_task
    0 mW    200.4 µs/s       0.4        Process        //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
    0 mW    189.9 µs/s      0.00        Interrupt      [4] block(softirq)
    0 mW    163.6 µs/s      0.00        kWork          rtl_watchdog_wq_callback
    0 mW    120.1 µs/s      0.25        Process        /usr/lib/bamf/bamfdaemon
    0 mW    108.4 µs/s       0.8        Process        /usr/lib/upower/upowerd
    0 mW    105.8 µs/s       1.6        Timer          tick_sched_timer
    0 mW     97.9 µs/s       0.4        Interrupt      [1] i8042
    0 mW     96.0 µs/s      0.00        Interrupt      [17] rtlwifi

```

Hi fictivetoast ;)

Oh... what a high power Wifi is employed!?
"rtl8192ce" has these kernel parameters:
```
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C19B839FC0499164FF0AFAD
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.5.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
```

It might make sense that you would try those parameters out, anyway I'm not sure... :P 
And Your LCD panel seems to have so bright backlight? Since My Vaio Z's one (1920x1080 fullHD) has only 897mW at 100% birhgtness setting...

Anyway your i915 would already saved your battery enough... The evil might be in other side I suppose.

Best regards,
Tista

---

### Post by jerrylamos on 2012-09-22
> **fictivetoast said:**
> Open a terminal:  sudo apt-get install powertop
Then type sudo powertop in the terminal and give it a few seconds to collect usage data.
I get:
sudo powertop
Loaded 0 prior measurements
Cannot load from file /var/cache/powertop/saved_parameters.powertop
Cannot load from file /var/cache/powertop//var/cache/powertop/saved_parameters.powertop
Leaving PowerTOP

?

---

### Post by cariboo on 2012-09-22
> **jerrylamos said:**
> I get:
sudo powertop
Loaded 0 prior measurements
Cannot load from file /var/cache/powertop/saved_parameters.powertop
Cannot load from file /var/cache/powertop//var/cache/powertop/saved_parameters.powertop
Leaving PowerTOP

?

Does your system actually have those files?

---

### Post by jerrylamos on 2012-09-23
> **cariboo907 said:**
> Does your system actually have those files?
No, it does not.  I somehow assumed apt-get insall powertop would do a powertop install.  How are those files created?

Thanks.

---

### Post by fictivetoast on 2012-09-23
> **tista said:**
> Hi fictivetoast ;)

Oh... what a high power Wifi is employed!?
"rtl8192ce" has these kernel parameters:
```
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C19B839FC0499164FF0AFAD
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.5.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
```

It might make sense that you would try those parameters out, anyway I'm not sure... :P 
And Your LCD panel seems to have so bright backlight? Since My Vaio Z's one (1920x1080 fullHD) has only 897mW at 100% birhgtness setting...

Anyway your i915 would already saved your battery enough... The evil might be in other side I suppose.

Best regards,
Tista

Agreed that my wifi card eats up power, but even if the wifi usage is resolved I think the real problem is that I'm getting 496.6 wakups/second and upwards of 300 GPU ops/second...

---

### Post by donniezazen on 2012-09-23
Powertop is buggy. I tend to trust overall power usage but individual power usage is not necessarily correct.

My system is performing better with no kernel parameters. Anyways I have never seen any improvements with those parameters.

System temperature do occasionally jump up to 80C and 30W.

---

### Post by effenberg0x0 on 2012-09-23
I have seen weird results from playing for an entire day with Powertop during the PP cycle. After seeing very questionable results, I had placed a wattmeter (something low-end, like [this]("http://en.wikipedia.org/wiki/Kill_A_Watt")) between the outlet and the PC and results were hugely discrepant. Then I did the same with a Fluke equipment (high-end) and reached similar results. Anyone with a multimeter can put it in series with the PSU, measure Amps and do some math to get watts. There are tutorials for that in the web. 

Also: That list of improvements that shows when Powertop finishes running was advising me to disable USB controllers. Doing so caused huge problems for internal and external USB devices for me (not being able to suspend/resume properly, devices that would only work again after a full reboot, etc).
 
I don't wanna bash Powertop, far from that actually. I think it's great software, but I generally advise people to not trust it's results blindly. I think there's a real limitation in how precise it is.

Right now, the biggest change I have seen in power consumption in ordinary users PCs relates to VGA/GPU and OpenGL support. MOst users can''t diagnose that. Generally they:
- Upgraded from a non-accelerated desktop to an accelerated one (using proper GPU drivers or llmvpipe): bigger power usage in both cases);
- Updated from previous Ubuntu with proper GPU drivers to llvmpipe (failed to re-install proper GPU drivers): Bigger power usage.

Regards,
Effenberg

---

### Post by jerrylamos on 2012-09-23
> **effenberg0x0 said:**
> Right now, the biggest change I have seen in power consumption in ordinary users PCs relates to VGA/GPU and OpenGL support. Can I conjecture unity + compiz are making a lot more usage of VGA/GPU and OpenGL?

---

### Post by effenberg0x0 on 2012-09-23
> **jerrylamos said:**
> Can I conjecture unity + compiz are making a lot more usage of VGA/GPU and OpenGL?

Well, using any sort of compositing creates processing for the GPU (direct acceleration) or for the CPU (indirect acceleration). Not using compositing will not create extra processing for the CPU/GPU - it should use less power.

What I meant is that ordinary users, those with no technical skills and/or knowledge about how Ubuntu works, might not notice when, after an upgrade, they transition:
1) from a non-accelerated (2D) desktop to an accelerated (3D) one; or
2) from a accelerated (3D) desktop (working and with with proper drivers) to an indirectly-accelerated (llvmpipe) one.

Users might see an increase in power usage in these 2 cases.

From a technical standpoint, compiz is a compositing window manager. It's one of the first and, thus, a mature one in comparison to other FOSS projects. It has bugs, like everything else, it's not perfect. 

All it does is allow for OpenGL acceleration. The logic for using OpenGL is simple: PCs have GPUs. Considering GPUs have specialized hardware support for OpenGL, and they are designed to render OpenGL better and faster than CPUs, it is smart to delegate processing to the GPU and, thus, offload the CPU. Not only that, OPenGL also allows for effects. 

Windows uses acceleration, and so does MacOS and IOs, and even Android. If we want to compete for the same users, it makes sense for us to at least try to deliver an equivalent experience when it comes to offloading processing to the GPU and proving visual effects in the desktop. 

That's all that is to compiz in Ubuntu. Using an accelerated desktop or not is really not under discussion anymore. It's unrealistic to expect Ubuntu to drop Unity or switch from compiz to something else in short-term. The problem right now, as it has been for some cycles, is that we need to make sure that Ubuntu always detects GPUs properly and always installs the proper drivers, in the most automated and transparent way. 

llvmpipe (indirect acceleration) is good in the sense that it allows Ubuntu to at least boot in most PCs - even without proper VGA drivers. But, the way it is right now, users that could be using proper VGA drivers are relying on indirect acceleration (cpu-based, via llvmpipe) and are not aware of that. They should be and they should be presented with an option to change from llvmpipe to proper vga drivers, so they can make better use of their hardware. If they can use proper VGA drivers and offload processing to the GPU, but they continue to use llvmpipe, they will be relying more on their CPUs, therefore using more power. So the VGA driver detection/install/update process is what is at stake right now and should be improved.

Regards,
Effenberg

---

### Post by jerrylamos on 2012-09-24
> **effenberg0x0 said:**
> ...Not using compositing will not create extra processing for the CPU/GPU - it should use less power....From a technical standpoint, compiz is a compositing window manager. From my view it is how much compositing is being used.  What is needed for a good clear usable desktop?  What is needed for a lot of special effects (tons!) I don't appreciate?  So I make my choices.  At some point I expect my choices to diminish since I'm not the target market.

Jerry

p.s. Here we go: "Two web-apps are on-course to come pre-installed with Ubuntu 12.10: Amazon.com and Ubuntu One Music Store" also animated dash, price ribbons, visual tweaks, OMG ubuntu is excited.  All that stuff is fine for availability - how much will be "pre-installed"?  How big are USB sticks?

---

### Post by donniezazen on 2012-09-25
This is one of the many scenarios I get often in the day. Fan taking up 12W, 6W on wifi and 2W on compiz.
[[IMG]http://i.imgur.com/kVUvFs.png[/IMG]](http://imgur.com/kVUvF)
[[IMG]http://i.imgur.com/NQ0Zus.png[/IMG]](http://imgur.com/NQ0Zu)

---

### Post by effenberg0x0 on 2012-09-25
> **jerrylamos said:**
> From my view it is how much compositing is being used.  What is needed for a good clear usable desktop?  What is needed for a lot of special effects (tons!) I don't appreciate?  So I make my choices.  At some point I expect my choices to diminish since I'm not the target market.

Jerry

p.s. Here we go: "Two web-apps are on-course to come pre-installed with Ubuntu 12.10: Amazon.com and Ubuntu One Music Store" also animated dash, price ribbons, visual tweaks, OMG ubuntu is excited.  All that stuff is fine for availability - how much will be "pre-installed"?  How big are USB sticks?

About Amazon and the lack of opt-in/opt-out (that is being discussed everywhere): I'm not particularly against that feature. I just wish we knew more about Ubuntu Roadmap, as usual. I know there's no roadmap, I just think there should be one. I can't think of a product people will support/adopt/buy without knowing what the plans for it are. Ex: No one really thought about it, but Amazon will never work for Brazilian users. It's absurd. Maybe they will make the code generalised enough so that localized versions could use other (local) providers. And I would use that feature if I could choose which Ubuntu-related project/group/LoCo I would be funding. I'm not sure, right now, what will Canonical use the revenue I generate for. Actually I wasn't even aware they were changing their business model, and that worries me more: is there a problem? Should we be worried about Canonical financial situation? Should we be trying to help it financially somehow? You see, my problem is always with the (lack of) communication. I believe FOSS should be more open regarding information. And lack of official info, lack of transparency, is the source of all FUD.

About UI: I'm not familiar with Windows 8 but up to Windows 7 users could go to "Start / Control Panel / Appearance and Personalization"(*) and customize some things. That includes enabling/disabling "Aero", transparency, etc. MacOS also has some cusotomization options. I believe Ubuntu will have some sort of customization options in the future, simply because they will have to in order to meet the market (end-users/OEM) demands and level with the competing OSs. I just think no one has drafted a serious proposal on what should be customisable, how and why. Unless someone creates a solid set of specs for this, considering serious UX aspects and goals, and proposes it to the people in charge of the design, it's hard to say if, when, how that will happen though. 

Regards,
Effenberg

(*) I'm not sure those are the names used in en_US localization of W7.

---

### Post by jerrylamos on 2012-09-25
In case readers haven't caught wind of this:

"Developer Of Amazon Search Lens Talks About Privacy Issues"

"The recent inclusion of Amazon search results in the Ubuntu Unity Dash has got much criticism and user backlash, chiefly about privacy concerns of the users. While this is a good way for Canonical to earn some affiliate revenue, users are more concerned about a 3rd party site getting to know about their search activity."
[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

Note the reference to "revenue" where Ubuntu is favoring a particular business and the data mining that company does.  There is mention of a communication from Shuttleworth about this which I haven't read.  (have now read one communication from Shuttleworth "they are not paid placement".)

---

### Post by cariboo on 2012-09-25
> **jerrylamos said:**
> In case readers haven't caught wind of this:

"Developer Of Amazon Search Lens Talks About Privacy Issues"

"The recent inclusion of Amazon search results in the Ubuntu Unity Dash has got much criticism and user backlash, chiefly about privacy concerns of the users. While this is a good way for Canonical to earn some affiliate revenue, users are more concerned about a 3rd party site getting to know about their search activity."
[http://mail.aol.com/37001-111/aol-6/en-us/mail/DisplayMessage.aspx?ws_popup=true](http://mail.aol.com/37001-111/aol-6/en-us/mail/DisplayMessage.aspx?ws_popup=true)

Note the reference to "revenue" where Ubuntu is favoring a particular business and the data mining that company does.  There is mention of a communication from Shuttleworth about this which I haven't read.

The link you provided goes to an AOL login page, which is of no use to those of us that don't have an AOL account.

Before going any further with this, I'd suggest you read both Mark Shuttleworth's and Jono Bacon's blog posts on [The Planet]("http://planet.ubuntu.com/")

---

### Post by baizon on 2012-09-25
I've made an update today from 12.04 to 12.10 and my battery live went from 5h to 3,5h (according to the battery indicator). Will report for changes.
I hope it will get fixed...

---

### Post by Appleshare on 2012-10-06
MacBook Pro 5,4 (graphic card NVIDIA Corporation C79 [GeForce 9400M] (rev b1))

Power consumption up to Precise ca. 14 W, in Quantal ca. 20 W. Battery life from 3:45 to 2:30. Playing with powertop tweaks does not help. Up to Precise I always used the nvidia drivers, but backlight control is broken for these, so in Quantal running nouveau. But it looks like it is running Unity 3D, not llvmpipe (?):

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVAC
OpenGL version string:  3.0 Mesa 9.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by Appleshare on 2012-10-06
MacBook Pro - Ubuntu Linux: 21 Watts, OS X: 9 Watts

Posted by Michael Larabel on August 23, 2012



[http://www.phoronix.com/scan.php?page=news_item&px=MTE2Njk](http://www.phoronix.com/scan.php?page=news_item&px=MTE2Njk)

---

### Post by cariboo on 2012-10-06
How doers Ubuntu power usage compare with other Linux distributions?

Comparing a generic operating system designed to run on as many hardware platforms with an operating system specifically designed for the hardware it runs on, really doesn't prove much, except that the kernel devs don't have the same access to hardware specs, as Apple developers do.

---

### Post by Appleshare on 2012-10-06
Obviously Apple has an advantage, but like I wrote, the power consumption increased between Precise and Quantal by 40% (and all pre-Precise releases were much the same as Precise).

I did not post the Phoronix link so much for the comparison to OS X, but to confirm that they have the same 20 W consumption in Quantal as I quoted for my machine.

EDIT: And it's not only a question of decreased utility, but also an environmental one according to Ubuntu's own principles. A few releases back there was a big push to improve power consumption by eliminating even small inefficiencies. And Ubuntu/Canonical explicitly mentioned environmental reasosn for doing so - millions of Ubuntu machines add up. Well, the sum of small improvements that were made back then were wiped out in one strike with Quantal at least for some hardware.

---

### Post by cariboo on 2012-10-06
The power consuption has more to do with the kernel, which Ubuntu really has no control over, they make some customizations the suit the distribution, but other wise, it is pretty well as comes from the kernel developers.

---

### Post by Appleshare on 2012-10-07
So what are you arguing for, that is does not matter or nothing can/should be done? I don't get your point.

---

### Post by cariboo on 2012-10-07
What I'm saying is that out-of-the-box Ubuntu may not be the best solution for your hardware. Try a vanilla kernel available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), try different distributions, to see if the problem has been solved elsewhere.

---

### Post by baizon on 2012-10-07
> **cariboo907 said:**
> The power consuption has more to do with the kernel, which Ubuntu really has no control over, they make some customizations the suit the distribution, but other wise, it is pretty well as comes from the kernel developers.

I can't agree with that. Until last week i used Ubuntu on my laptop, and my battery life was 3:25. After i switched to Xubuntu, which has the same kernel, my battery life went to 5:10. Both System uses the same kernel, so imo it's fixable.

---

### Post by Appleshare on 2012-10-07
> **cariboo907 said:**
> What I'm saying is that out-of-the-box Ubuntu may not be the best solution for your hardware. Try a vanilla kernel available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), try different distributions, to see if the problem has been solved elsewhere.

For the third time, all was reasonably fine from 2009 until and including Precise. And I certainly have no desire to hunt for a different distro, I have been happy with Ubuntu since Warty and just lived through the rather painful transition to Unity.

---

### Post by cariboo on 2012-10-07
> **baizon said:**
> I can't agree with that. Until last week i used Ubuntu on my laptop, and my battery life was 3:25. After i switched to Xubuntu, which has the same kernel, my battery life went to 5:10. Both System uses the same kernel, so imo it's fixable.

Thanks, you just proved my point. :), that for some Ubuntu at this time, may not be right for the hardware they are using

---

### Post by Appleshare on 2012-10-07
> **cariboo907 said:**
> Thanks, you just proved my point. :), that for some Ubuntu at this time, may not be right for the hardware they are using

"Tough luck dude, go away" - I hope that's not Canonical's attidue

---

### Post by cariboo on 2012-10-07
This has gone far enough, I guess I've been a little obtuse, I've suggested trying other distro's so that you can come back and report if others have solved the problem. 

Ubuntu is a community that depends on it's members to help make things better, if you can try other distros, and compare the differences between them and Ubuntu, and create meaningful bug reports, maybe this problem can be resolved before the next LTS release.

---

### Post by funicorn on 2012-10-07
power consumption largely depends on linux kernel. I'm sure u have noticed the different versions of linux kernel used in precise and in quantal.

> **Appleshare said:**
> Obviously Apple has an advantage, but like I wrote, the power consumption increased between Precise and Quantal by 40% (and all pre-Precise releases were much the same as Precise).

I did not post the Phoronix link so much for the comparison to OS X, but to confirm that they have the same 20 W consumption in Quantal as I quoted for my machine.

EDIT: And it's not only a question of decreased utility, but also an environmental one according to Ubuntu's own principles. A few releases back there was a big push to improve power consumption by eliminating even small inefficiencies. And Ubuntu/Canonical explicitly mentioned environmental reasosn for doing so - millions of Ubuntu machines add up. Well, the sum of small improvements that were made back then were wiped out in one strike with Quantal at least for some hardware.

---

### Post by Appleshare on 2012-10-07
> **funicorn said:**
> power consumption largely depends on linux kernel. I'm sure u have noticed the different versions of linux kernel used in precise and in quantal.

Yeah, and there were also different versions in all releases, yet it was not so bad.

---

### Post by Appleshare on 2012-10-07
> **cariboo907 said:**
> This has gone far enough, I guess I've been a little obtuse, I've suggested trying other distro's so that you can come back and report if others have solved the problem. 

Ubuntu is a community that depends on it's members to help make things better, if you can try other distros, and compare the differences between them and Ubuntu, and create meaningful bug reports, maybe this problem can be resolved before the next LTS release.

If you phrase it that way I totally agree, and I've been reporting lots of bugs for Quantal and will continue to do so. It's still a shame, and let me remind you that while my MacBookPro might be a bit exotic hardware for Ubuntu, the original poster in the thread has a Lenovo Thinkpad t420i (according to his signature), which is not exotic at all.

---

### Post by jerrylamos on 2012-10-07
> **cariboo907 said:**
> This has gone far enough, I guess I've been a little obtuse, I've suggested trying other distro's so that you can come back and report if others have solved the problem. Yes, distro Precise Pangolin 12.04 LTS has solved this and a bunch of other B2 problems and anklebiters that we've been reporting.  I've a bunch of things on B2 that don't work right.  Sure feels to some of us like they crammed a bunch of new half-baked stuff into B2 instead of just using B2 to clean off remaining B1 bugs.  Put the new stuff in to 13.04, my opinion, I'm just a user/tester.

My fallback distro is Precise, and perhaps 13.04 Alpha will come out and I can shake 12.10 off my foot.  I'm still reporting/following 12.10 bugs in the meantime.  I'm on holiday using my daughter's MacBook (hardly know how) and will get back to looking at B2 when we're home.

---

### Post by Appleshare on 2012-10-09
I think that since this is happening on bog-standard hardware as well, a warning should be added to the release notes.

---

### Post by Appleshare on 2012-10-10
Good news FYI: When switching from the nouveau drivers to the proprietary nvidia-current, power consumption is reduced by ca. 5 W in idle from ca. 20.5 to ca. 15.5, and around 18 W when stuff is running and using 30% CPU plus frequent disk accesses.

With that consumption when using nvidia-current, Quantal is back in the ballpark of previous Ubuntu releases. So that's good. (And in addition, nvidia-current makes suspend work, which is another thing currently broken with nouveau (LP #1055475)).

However, in Quantal, nouveau seems to be the default for Nvidia cards. And nvidia-current and nvidia-experimental-304 are currently not practical on my MacBookPro because backlight adjustment is broken (another regression). This affects also more usual hardware, see e.g. LP #1046088

---

### Post by pqwoerituytrueiwoq on 2012-10-10
> **Appleshare said:**
> Good news FYI: When switching from the nouveau drivers to the proprietary nvidia-current, power consumption is reduced by ca. 5 W in idle from ca. 20.5 to ca. 15.5, and around 18 W when stuff is running and using 30% CPU plus frequent disk accesses.

With that consumption when using nvidia-current, Quantal is back in the ballpark of previous Ubuntu releases. So that's good. (And in addition, nvidia-current makes suspend work, which is another thing currently broken with nouveau (LP #1055475)).

However, in Quantal, nouveau seems to be the default for Nvidia cards. And nvidia-current and nvidia-experimental-304 are currently not practical on my MacBookPro because backlight adjustment is broken (another regression). This affects also more usual hardware, see e.g. LP #1046088

maybe [backlightx]("http://ubuntuforums.org/attachment.php?attachmentid=225300&d=1349757213") will work for you
run ls /sys/class/backlight/ to see if the where line is right
my backlight works for me using nvidia's drivers but this is not a mac

---

