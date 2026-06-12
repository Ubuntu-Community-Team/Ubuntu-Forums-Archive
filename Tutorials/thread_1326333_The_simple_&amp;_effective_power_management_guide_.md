---
title: "The simple &amp; effective power management guide (how to save battery power)"
date: 2009-11-14
forum: Tutorials
---

### Post by Axx83 on 2009-11-14
v 0.25 - This guide is written for _Ubuntu 9.10 Karmic Koala_

This guide is focused on how to implement most common power management tips, taken from the community and powertop suggestions, in the simplest way. Its aim is to be rock stable and quite effective without putting notebooks at risks. It has been tested by me on a Lenovo Thinkpad X60s with almost exclusively Intel hardware.

**Hard disks**
In Karmic hard drives are managed by a script and gnome-power-manager (g-p-m). The settings are very safe and probably there could still be some power to save but I prefer to play on the safe side with my hard disk.

I decided not to enable laptop-mode and not to play with the values in /usr/lib/pm-utils/power.d/95hdparm-apm or the seconds2sleep in gnome-power-manager.

Probably buying a good solid state drive could get much better results, but they are still very expensive.

**Screen brightness**
In karmic it is handled again by g-p-m, the standard values can be played with though.
Press alt+F2 and type ```
gconf-editor
``` scroll the "apps" section on the left and open "gnome-power-manager". The related part is "backlight". The "brightness_dim_battery" key is defaulted at 50, that means a 50% reduction.

Personally I'm fine with the lowest brightness on my screen. Double click on the key name, in the pop up instead of 50 write 99 (that practically means 100% reduction, but the 100 value gives me problems).

Try different values to see which one is better for you, of course higher value, lower brightness, lower power consumption.

**link power management policy**
This is a tip among the ones suggested by running the powertop program (software center > powertop).
Run gedit (applications>accessories) and paste the following text in the empty document
```
#!/bin/sh

path_host0="/sys/class/scsi_host/host0/link_power_management_policy"
path_host1="/sys/class/scsi_host/host1/link_power_management_policy"
path_host2="/sys/class/scsi_host/host2/link_power_management_policy"
path_host3="/sys/class/scsi_host/host3/link_power_management_policy"
val=max_performance

case "$1" in
	true)
		echo "**lpm policy powersave ON"
		val=min_power
		;;
	false)
		echo "**lpm policy powersave OFF"
		val=max_performance
		;;
esac

# max_performance on AC min_power on battery

if [ -w "$path_host0" ] ; then
	echo $val > $path_host0
fi

if [ -w "$path_host1" ] ; then
	echo $val > $path_host1
fi

if [ -w "$path_host2" ] ; then
	echo $val > $path_host2
fi

if [ -w "$path_host3" ] ; then
	echo $val > $path_host3
fi

exit 0
```
close and save (in your home directory) calling it
```
link_pm_policy
```
Run a terminal (applications>accessories) and paste the following lines one at a time pressing return after each one
```
chmod 755 link_pm_policy
sudo su
install link_pm_policy /usr/lib/pm-utils/power.d/
exit
```
you WILL be asked for your password, just type it in and press return.

**virtual memory dirty writeback**
Again as suggested by powertop.
Run gedit (applications>accessories) and paste the following text in the empty document
```
#!/bin/sh

path_dwc="/proc/sys/vm/dirty_writeback_centisecs"
val=500

case "$1" in
	true)
		echo "**VM dirty writeback 15 seconds"
		val=1500
		;;
	false)
		echo "**VM dirty writeback 5 seconds"
		val=500
		;;
esac

# 5 seconds on AC, 15 seconds on battery

if [ -w "$path_dwc" ] ; then
	echo $val > $path_dwc
fi

exit 0
```
close and save (in your home directory) calling it
```
vm_dirty_writeback
```
Run a terminal (applications>accessories) and paste the following lines one at a time pressing return after each one
```
chmod 755 vm_dirty_writeback
sudo su
install vm_dirty_writeback /usr/lib/pm-utils/power.d/
exit
```
you WILL be asked for your password, just type it in and press return.

**Scheduling policy powersave**
This is managed by a default script that comes with Karmic.

**Usb auto suspend**
This is a key issue for failure of power saving in Linux.
Run gedit (applications>accessories) and paste the following text in the empty document
```
#!/bin/bash
if [ "$1" = "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done

  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done

fi
``` 
close and save (in your home directory) calling it
```
usb_autosuspend
```
Run a terminal (applications>accessories) and paste the following lines one at a time pressing return after each one
```
chmod 755 usb_autosuspend
sudo su
install usb_autosuspend /usr/lib/pm-utils/power.d/
exit
```
you WILL be asked for your password, just type it in and press return.

When starting the notebook with AC on this script doesn't do anything, it is automatically run when going from AC to Battery and it sets usb to autosuspend after 2 secs. NOTE that this could turn off some old usb devices plugged to the computer. To avoid any problem (and save the most battery) DON'T leave usb devices plugged when going from AC to Battery, even better, don't use usb devices when running on battery at all. When using AC there is absolutely no problems at all.

**Intel HD audio**
Karmic has finally added a line to alsa configuration files that turn off the card after few second of inactivity. HDA cards can be named Intel, Nvidia, Ati and others but all should have this power saving active.

**Intel wireless cards**
Since kernel 2.6.30 the behavior of such cards has changed, there is no possibility of tuning the power consumption.

**_Results_**
Running the powertop program ```
sudo powertop -d -t 60
``` these are my results after unplugging the cable
> Cn	          permanenza media
C0 (cpu occupata)      ( 0,7%)
C0		  0,0 ms ( 0,0%)
C1 halt		  0,0 ms ( 0,0%)
C2		  0,2 ms ( 0,0%)
C3		 28,4 ms (99,3%)

P-state (frequenze)
  1,67 Ghz     0,6%
  1333 Mhz     0,0%
  1000 Mhz    99,4%

Wakeup-da-idle al secondo: 35,5	intervallo: 60,0s
Utilizzo energetico (stima ACPI): 11,3W (1,9 ore) 

Cause principali di wakeup:
  27,2% ( 12,6)       <interrupt> : iwl3945 
  22,2% ( 10,3)   <core del kernel> : hrtimer_start_range_ns (tick_sched_timer) 
  16,0% (  7,4)      <IPI kernel> : Rescheduling interrupts 
   6,4% (  3,0)       <interrupt> : acpi 
   4,4% (  2,0)   <core del kernel> : hrtimer_start (tick_sched_timer) 
   4,2% (  1,9)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   3,0% (  1,4)       <interrupt> : uhci_hcd:usb2, i915 
   2,1% (  1,0)            python : hrtimer_start_range_ns (hrtimer_wakeup) 

Suggestion: Enable laptop-mode by executing the following command:
   echo 5 > /proc/sys/vm/laptop_mode
The program is still suggesting me to run laptop-mode which is another way to handle the hard drive (and other variables) but I still prefer to avoid it as it's not recommended by Ubuntu.

**Known issues & things to do**
- The guide could be simplified, creating a package for the scripts but I don't know how to do it.

- The "link pm..." script on some notebooks runs fine but doesn't change the sys value. Let me know if that's your case.

------------------------------------------------------------------------------------
Version 0.25 typo correction and bug inserted
Version 0.2 chmod commands were incorrect
Version 0.1 first post

Special thanks to:
Scragar [related discussion]("http://ubuntuforums.org/showthread.php?t=1324112")
Sdennie [related post]("http://ubuntuforums.org/showthread.php?t=847773&highlight=usb+autosuspend")

---

### Post by Axx83 on 2009-11-18
I'm just replying to see if someone has tested the script and can help me improve it. Thanks

---

### Post by ibrahim.k on 2009-11-18
OMG !! this is so hard for me

---

### Post by Axx83 on 2009-11-18
please tell me what part you found not clear, I'm sure there's a lot of room for improvement, especially to make it easy and quick to install.

---

### Post by zee on 2009-11-20
@Axx83:
How much did your battery life improve?
With my extended battery on my Lenovo x60s I get ~8 hours per battery charge and only 3 hours in Ubuntu Linux.

Grazie!

---

### Post by Axx83 on 2009-11-21
Now I have the 3 cell standard battery on my x60s, it doesn't last very long on Ubuntu or Windows, probably in windows I get +15 minutes with all the settings of lenovo power manager to the minimum. Now i can get circa 2 hours on linux.

The problem is that before these tweaks the computer on Ubuntu did not last more than 55 minutes, which was ridiculous.

The big problem here is the battery:
Actual charge: 22,6 Wh
Last full charge: 27,1 Wh
Factory charge: 28,8 Wh

As you can see even of the original max charge is well below a crappy eeepc standard battery. Can't get much more our of this pc...

But if you have the extended I'm sure it's just a matter of some components not going in to save mode, try installing this guide and let me know.

---

### Post by zee on 2009-11-21
Thanks for the quick reply.

I will definitely try. Maybe the culprit was also the fast & hot Hitachi hard disk that I have now substituted with an Intel SSD ;)

How are the idle temperatures in your laptop? In Ubuntu my CPU was usually hitting 50-55 degrees Celsius.

Bye.

---

### Post by Axx83 on 2009-11-21
Well if you switched to ssd it's a good idea to install from scratch with ext4 partition, I'm sure you will save a good amount of energy.

The temperatures were never above 60c, I checked them with the tpfan program, but anyway the cpu is low voltage, it rarely gets heated

---

### Post by 3rdalbum on 2009-11-22
I think "vm" in this instance stands for "Virtual Memory", not "Virtual Machine". Just a small correction.

I might give this a try on my netbook. If I do, then I'll be sure to create a Debian package around it for you.

---

### Post by X1R1 on 2009-11-25
Just installed, My power consumption is at 12.1W, a lot less than before, thank you. A little recommendation though. If you have to install everything in the same exact place, why not make a SINGLE script instead of separate ones?

---

### Post by Axx83 on 2009-11-25
I thought about that but I think it's better to have individual scripts in case something goes wrong with one component.

By the way once a package is done, there will be no problem anymore, I just need help because I can't make packages myself.

---

### Post by X1R1 on 2009-11-25
PM me when the package is done :D I will like to have it and help you distribute it.

---

### Post by HeadHunter00 on 2009-11-25
Nice tutorial. Helped me a lot.

---

### Post by philipcs on 2009-11-26
Thanks for the tips.
Before the tune, the battery incidator show 4 hours remaining right after full charge.

After i applied these tips, it showing 5.4 hours remaining right after full charge.

Below is the statistic after the tune, anymore thing can be disable to improve the battery life further?

How do I disable the CDROM Polling? is this help as well?

-----------------------------------

PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 120 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 1.1%)
C0		  0.0ms ( 0.0%)
C1 halt		  0.0ms ( 0.0%)
C2		  0.1ms ( 0.0%)
C3		  9.2ms (98.9%)
P-states (frequencies)
  1200 Mhz     0.1%
   800 Mhz    99.9%
Wakeups-from-idle per second : 107.4	interval: 120.0s
Power usage (ACPI estimate): 11.2W (5.4 hours) 
Top causes for wakeups:
  15.1% ( 21.4)           firefox : hrtimer_start_range_ns (hrtimer_wakeup) 
  13.7% ( 19.4)       <interrupt> : ata_piix 
  12.9% ( 18.2)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  11.3% ( 16.0)       <interrupt> : iwl3945 
  10.8% ( 15.2)     <kernel core> : hrtimer_start (tick_sched_timer) 
  10.2% ( 14.4)       <interrupt> : extra timer interrupt 
   7.1% ( 10.0)       <interrupt> : eth0 
   7.1% ( 10.0)     <kernel core> : add_timer (tg3_timer) 
   2.8% (  4.0)     <kernel core> : usb_hcd_poll_rh_status (rh_timer_func) 
   2.7% (  3.9)      <kernel IPI> : Rescheduling interrupts 
   1.2% (  1.7)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.7% (  1.0)     <kernel core> : clocksource_watchdog (clocksource_watchdog) 
   0.6% (  0.8)              Xorg : queue_delayed_work (delayed_work_timer_fn) 
   0.5% (  0.7)     <kernel core> : neigh_periodic_timer (neigh_periodic_timer) 
   0.5% (  0.7)         kblockd/0 : blk_plug_device (blk_unplug_timeout) 
   0.3% (  0.5)   devkit-disks-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.5)   hald-addon-stor : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.4)              phy0 : ieee80211_associated (ieee80211_sta_timer) 
   0.2% (  0.3)       <interrupt> : acpi 
   0.2% (  0.3)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)   gnome-settings- : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)   netbook-launche : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)     <kernel core> : sk_reset_timer (tcp_delack_timer) 
   0.1% (  0.2)   update-notifier : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.2)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)   devkit-disks-da : blk_add_timer (blk_rq_timed_out_timer) 
   0.1% (  0.1)   gnome-power-man : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)            python : sk_reset_timer (tcp_write_timer) 
   0.1% (  0.1)     <kernel core> : add_timer (sta_info_cleanup) 
   0.1% (  0.1)         ssh-agent : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)     <kernel core> : rs_tx_status (iwl3945_bg_rate_scale_flush) 
   0.0% (  0.1)           pdflush : wb_kupdate (wb_timer_fn) 
   0.0% (  0.1)              hald : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.1)          gconfd-2 : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)      avahi-daemon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)            python : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)           pdflush : add_timer (commit_timeout) 
   0.0% (  0.0)   devkit-power-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)     <kernel core> : neigh_timer_handler (neigh_timer_handler) 
   0.0% (  0.0)       <interrupt> : i915 
   0.0% (  0.0)   console-kit-dae : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)           pdflush : blk_add_timer (blk_rq_timed_out_timer) 
   0.0% (  0.0)   hald-addon-stor : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.0)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)           iwl3945 : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)        pulseaudio : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)   devkit-disks-da : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.0)     <kernel core> : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.0)     <kernel core> : igmp_start_timer (igmp_timer_expire) 
   0.0% (  0.0)              cron : hrtimer_start_range_ns (hrtimer_wakeup) 

A USB device is active 100.0% of the time:
USB device  2-1 : HP Integrated Module (Broadcom Corp)

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
  0.0%	USB device  3-1 : Fingerprint Sensor ()
100.0%	USB device  2-1 : HP Integrated Module (Broadcom Corp)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
100.0%	USB device usb2 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.31-15-generic ehci_hcd)

---

### Post by Axx83 on 2009-11-26
press alt+F2 and write```
gksudo gedit /etc/fstab
```you should see at the bottom of the file something related to /dev/cdrom0 or /dev/scd0 or similar.

If you don't then I'm no help. If you do, just type # at the beginning of that line (ONLY that line, leave the rest untouched) restart system and rerun powertop when on battery.

Let me know if that helped.

Anyway, do you know what is that hp/broadcom thing that's showing up ? maybe it's bluetooth or something, I would investigate.

---

### Post by philipcs on 2009-11-26
A USB device is active 100.0% of the time:
USB device 2-1 : HP Integrated Module (Broadcom Corp)

This looks like is either Wifi, Gigabits LAN or Bluetooth.

But I have already disabled Bluetooth in system perferences.

---

### Post by Axx83 on 2009-11-26
definitely not wifi as you have intel wireless 3945 showing on the list (btw the best wifi card for linux) probably bluetooth, try disabling it in the bios (when you turn on the notebook) as see if that changes.

---

### Post by philipcs on 2009-11-26
> **Axx83 said:**
> definitely not wifi as you have intel wireless 3945 showing on the list (btw the best wifi card for linux) probably bluetooth, try disabling it in the bios (when you turn on the notebook) as see if that changes.

I cant see the option in BIOS to disable the Bluetooth.

Any other way to set the bluetooth disabled when boot up?

I am using Ubuntu 9.10 Remix (for netbook), so i cant see the Services in system -> Administration.

---

### Post by Axx83 on 2009-11-26
if the bluetooth is on it should say so in system pref bluetooth

in that menu you could be able to set the notification icon to display

if it's visible rightclick and disable bluetooth

if that doesn't work then it's a bug and you should file a bug report it in launchpad

you could also blacklist the bluetooth modules to load but I have not being able to understand which ones you should blacklist exactly, some things have changed in 9.10

another possibility is to install "bum" in software center, then go to sys adm bootupmamager, once run you just right click on everything that says bluetooth and you stop and disable it

---

### Post by philipcs on 2009-11-26
I have followed your advise to install BUM and disable Bluetooth Services and some other services which is not using battery life improved to 5 hours 31 mins now but below 2 items still running 100%.

100.0%	USB device  2-1 : HP Integrated Module (Broadcom Corp)
100.0%	USB device usb2 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)

Below is the latest result:

PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 120 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.6%)
C0		  0.0ms ( 0.0%)
C1 halt		  0.0ms ( 0.0%)
C2		  0.1ms ( 0.0%)
C3		 16.4ms (99.4%)
P-states (frequencies)
  1200 Mhz     0.4%
   800 Mhz    99.6%
Wakeups-from-idle per second : 60.7	interval: 120.0s
Power usage (ACPI estimate): 11.4W (5.3 hours) 
Top causes for wakeups:
  18.5% ( 16.2)       <interrupt> : ata_piix 
  16.6% ( 14.5)     <kernel core> : hrtimer_start (tick_sched_timer) 
  15.1% ( 13.3)       <interrupt> : iwl3945 
  11.7% ( 10.2)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  11.4% ( 10.0)       <interrupt> : eth0 
  11.4% ( 10.0)     <kernel core> : add_timer (tg3_timer) 
   4.6% (  4.0)     <kernel core> : usb_hcd_poll_rh_status (rh_timer_func) 
   1.9% (  1.7)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   1.8% (  1.6)      <kernel IPI> : Rescheduling interrupts 
   1.1% (  1.0)        checkgmail : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.9% (  0.8)              Xorg : queue_delayed_work (delayed_work_timer_fn) 
   0.6% (  0.5)   hald-addon-stor : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.6% (  0.5)   devkit-disks-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.6% (  0.5)     <kernel core> : neigh_periodic_timer (neigh_periodic_timer) 
   0.5% (  0.5)              phy0 : ieee80211_associated (ieee80211_sta_timer) 
   0.3% (  0.3)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.3)   gnome-settings- : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.3)       <interrupt> : acpi 
   0.3% (  0.2)   netbook-launche : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)   update-notifier : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)   hald-addon-stor : blk_add_timer (blk_rq_timed_out_timer) 
   0.1% (  0.1)   gnome-power-man : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)     <kernel core> : add_timer (sta_info_cleanup) 
   0.1% (  0.1)         ssh-agent : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)              hald : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)           pdflush : wb_kupdate (wb_timer_fn) 
   0.0% (  0.0)          gconfd-2 : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)   devkit-power-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)          gconfd-2 : add_timer (commit_timeout) 
   0.0% (  0.0)     <kernel core> : sk_reset_timer (tcp_delack_timer) 
   0.0% (  0.0)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)      avahi-daemon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)     <kernel core> : rs_tx_status (iwl3945_bg_rate_scale_flush) 
   0.0% (  0.0)          gconfd-2 : blk_add_timer (blk_rq_timed_out_timer) 
   0.0% (  0.0)        kjournald2 : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.0)              cron : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)        pulseaudio : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)         nm-applet : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)          rsyslogd : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)          events/0 : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)        checkgmail : neigh_add_timer (neigh_timer_handler) 
   0.0% (  0.0)           iwl3945 : queue_delayed_work (delayed_work_timer_fn) 

A USB device is active 100.0% of the time:
USB device  2-1 : HP Integrated Module (Broadcom Corp)

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
  0.0%	USB device  3-1 : Fingerprint Sensor ()
100.0%	USB device  2-1 : HP Integrated Module (Broadcom Corp)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
100.0%	USB device usb2 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.31-15-generic ehci_hcd)

---

### Post by Axx83 on 2009-11-27
ok another trial, run
```
lsusb
```
in a terminal and write down the number of that hp/broadcom usb device, look for it on the internet, if it's bluetooth than the only remaining possibility is blacklisting all bluetooth modules.
Otherwise I'm out of clues.

---

### Post by philipcs on 2009-11-27
I got below result:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Looks like BT & Wifi are using the same module?

Is it safe to blacklist this "Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]" without disable the Wifi?

I am confused now since this laptop is using intel wireless 3945 but this result also showed integrated module. :(

---

### Post by Axx83 on 2009-11-27
I have no idea why you have iwl3945 and then this usb wifi/bluetooth controller separated. Anyway it's perfectly safe to disable/blacklist all bluetooth modules because they are loaded separately by Linux.

At this point the only thing that's left is trying to find the bluetooth modules to blacklist and hope that that usb won't be loaded.

Otherwise you're pretty much stuck.

---

### Post by zee on 2009-11-27
I would simply disable Bluetooth in the BIOS (if possible).

---

### Post by Axx83 on 2009-11-27
That is also what I do. I use bluetooth so seldom that the very few times I need it I just enable and then disable it again in the bios, without blacklisting/disabling any module or service. But apparently he can't.

---

### Post by philipcs on 2009-11-28
I have made a mistake. I checked the bios again, I saw the bt disable function. Not sure why I didn't see at the 1st time. Sorry guys.

---

### Post by Axx83 on 2009-11-29
@philipscs
good to hear, let us know if that worked.

@everyone else
Guys I seem to have a problem with the "link power management policy" script. On my thinkpad it works fine, on my friend's acer it seems not to work. If I unplug ac all the other things are run, the pm script says it's run correctly in the logs but when I
```
cat /sys/class/scsi_host/host0/link_power_management_policy
```
the answer is always "max_performance"

What could be the problem ?

Thanks

---

### Post by philipcs on 2009-11-29
here is the result after disable the BT in BIOS:

PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 120 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.5%)
polling		  0.0ms ( 0.0%)
C1 halt		  0.0ms ( 0.0%)
C2		  0.0ms ( 0.0%)
C3		 18.2ms (99.5%)
P-states (frequencies)
  1200 Mhz     0.8%
   800 Mhz    99.2%
Wakeups-from-idle per second : 54.9	interval: 120.0s
Power usage (ACPI estimate): 11.3W (5.2 hours) 
Top causes for wakeups:
  20.7% ( 16.0)       <interrupt> : ata_piix 
  16.7% ( 12.9)       <interrupt> : iwl3945 
  15.1% ( 11.7)     <kernel core> : hrtimer_start (tick_sched_timer) 
  12.9% ( 10.0)       <interrupt> : eth0 
  12.9% ( 10.0)     <kernel core> : add_timer (tg3_timer) 
  10.1% (  7.8)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   2.2% (  1.7)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   1.6% (  1.2)      <kernel IPI> : Rescheduling interrupts 
   1.3% (  1.0)        checkgmail : hrtimer_start_range_ns (hrtimer_wakeup) 
   1.1% (  0.8)              Xorg : queue_delayed_work (delayed_work_timer_fn) 
   0.9% (  0.7)     <kernel core> : neigh_periodic_timer (neigh_periodic_timer) 
   0.6% (  0.5)   hald-addon-stor : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.6% (  0.5)   devkit-disks-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.6% (  0.5)              phy0 : ieee80211_associated (ieee80211_sta_timer) 
   0.3% (  0.3)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.3)   gnome-settings- : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)   netbook-launche : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)   update-notifier : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.1)   devkit-disks-da : blk_add_timer (blk_rq_timed_out_timer) 
   0.1% (  0.1)      avahi-daemon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)         ssh-agent : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)     <kernel core> : add_timer (sta_info_cleanup) 
   0.1% (  0.1)   gnome-power-man : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)              hald : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)           pdflush : wb_kupdate (wb_timer_fn) 
   0.1% (  0.0)       <interrupt> : acpi 
   0.0% (  0.0)          rsyslogd : add_timer (commit_timeout) 
   0.0% (  0.0)          gconfd-2 : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)     <kernel core> : fib6_run_gc (fib6_gc_timer_cb) 
   0.0% (  0.0)   devkit-power-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)     <kernel core> : inet_twdr_hangman (inet_twdr_hangman) 
   0.0% (  0.0)     <kernel core> : rs_tx_status (iwl3945_bg_rate_scale_flush) 
   0.0% (  0.0)   gnome-settings- : cfq_arm_slice_timer (cfq_idle_slice_timer) 
   0.0% (  0.0)           pdflush : blk_add_timer (blk_rq_timed_out_timer) 
   0.0% (  0.0)       <interrupt> : i915 
   0.0% (  0.0)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)          events/0 : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)           iwl3945 : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)        pulseaudio : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)              aptd : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)              cron : hrtimer_start_range_ns (hrtimer_wakeup) 

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
  0.0%	USB device  3-1 : Fingerprint Sensor ()
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb2 : UHCI Host Controller (Linux 2.6.31-15-generic uhci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.31-15-generic ehci_hcd)

---

### Post by philipcs on 2009-11-29
now i got another problem, after i have disabled the BT in bios, my Wireless indicator blue light keep blinking from time to time... weird.

I will try to enable back later and see the ligh will still blink. Weird

---

### Post by koekiemonster on 2009-11-29
usb 2-1 on my laptop is the SD card-reader (MSI-X340)

i used iggykoopa's suggestion:
> 
                                  **Re: powertop suggestion**             
                                                                   you can try removing all the usb modules and see if that works. if not the hard way (I haven't tested this but it should work) is to go to:
/sys/bus/usb/devices
find your device you wanna turn off and go to the power directory i.e.:
/sys/bus/usb/devices/2-2/power
then:
sudo su
to switch to root, then:
echo suspend > level
should suspend the device

edit: and heres [https://bugs.launchpad.net/ubuntu/+s...op/+bug/136549]("https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549") the bug about the grub suggestion
to be able to power it down.
a shorter command is:
sudo su
echo suspend > /sys/bus/usb/devices/2-1/power/level


i'm tried to incorporate it in the usb suspend script, but just adding the echo rule doesn't work

edit: ok i just needed to reinstall the script, now the usb 2-1 device powers down nicely when unplugging the power. (after the second for loop, a row above the fi, i added: echo suspend > /sys/bus/usb/devices/2-1/power/level )

also the link pm script doesn't change the value.

i'm using a fairly fresh install of 64bit ubuntu karmic 9.10 on an MSI-X340

---

### Post by Axx83 on 2009-11-29
You could have written it like this:
```
#!/bin/bash
if [ "$1" = "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done

for i in /sys/bus/usb/devices/2-1/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "suspend" > $i
  done

  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done

if [ "$1" = "false" ]; then

for i in /sys/bus/usb/devices/2-1/power/level; do
	[ "$(cat $i)" = "suspend" ] && continue
	echo "auto" > $i
  done

fi
```
otherwise once you unplug the ac the sd reader is gone until next reboot, plugging ac back in won't submit no command. There may be some mistakes in the script, I'm no expert with shell scripts for sure...

---

### Post by Axx83 on 2009-11-29
regarding link power management I have the same issue on the acer travelmate, but no problem on the lenovo thinkpad. The first has intel 965 chipset the second intel 950, MAYBE that's the issue but I'm not sure.

---

### Post by hiKen on 2011-04-12
Hi

Is it possible to put all the changes in the scripts in the laptop-mode configuration file, instead of installing it to the pm-utils folder?

I am using maverick merkaat.

Besides, is there a way to make ubuntu apply the changes only when it is on battery power?


Cumpz

---

### Post by cmavr8 on 2011-06-11
> **Axx83 said:**
> You could have written it like this:
```
#!/bin/bash
if [ "" = "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done

for i in /sys/bus/usb/devices/2-1/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "suspend" > $i
  done

  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done

if [ "" = "false" ]; then

for i in /sys/bus/usb/devices/2-1/power/level; do
	[ "$(cat $i)" = "suspend" ] && continue
	echo "auto" > $i
  done

fi
```
otherwise once you unplug the ac the sd reader is gone until next reboot, plugging ac back in won't submit no command. There may be some mistakes in the script, I'm no expert with shell scripts for sure...

Has anyone tried this?
I think it has a typo... non-closing if.

---

### Post by rolfen on 2012-06-01
usb_autosuspend made my mouse go, so I skipped that one. (chmod -x).
By the way, I'm on ubuntu 12.04, and these instructions are valid (and still useful). I can't decide if it's a good thing or a bad thing...

---

