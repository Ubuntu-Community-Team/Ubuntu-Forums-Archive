---
title: "Snyc PDA in XP client on Ubuntu"
date: 2008-03-29
forum: Virtualisation
---

### Post by bluewhale on 2008-03-29
Not having any luck after trying various ideas here and via general googling.  I'm trying to sync my Windows Mobile phone/PDA with the XP Pro ( 32 bit ) Client in a VMWare Workstation 6.02 session. All of this installed on Ubuntu 7.10 64 bit. 

I can 'see' flash drives as I plug and unplug them both in Linux as well as in XP. However the smart phone never gets a reaction whether on when it is plugged in or when turned on afterward. 

The USB cable is known good. USB controller is activated on this VM client. 

Any thoughts or pointers?

---

### Post by Whiffle on 2008-03-29
If you plug in the phone, then run "dmesg" in the terminal, what do the last few lines say?  I'm thinking it either a driver issue on the linux side or a permissions issue.

---

### Post by bluewhale on 2008-03-30
Below are the last few lines via dmesg. However prior to pulling this up I found the PDA syncing itself. Or trying to. In order to get it to sync I now have to plug the unit in ( which I've been doing solely for power for a month). 

Once plugged in the Winamp session running on the XP client pauses and a Ubuntu message comes up stating 

The specified device appears to be claimed by another driver (ipaq) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver. 

If I click OK promptly Winamp continues with the music it was playing and the PDA/Phone syncs up. I'm not sure why it calls it an IPAQ as it's not an HP, but pehaps it resembles one. Have also found it does not resolve conflicting files as well as in native XP, but at least I can sync again! 

The other things I've noticed the past few weeks on Ubuntu is the 249 messages suppressed.  Hundreds if not thousands of these. Are they 'normal' in Ubuntu? 

Thanks

Paul

[168460.481743] ipaq 4-1:1.0: device disconnected
[168464.425915] printk: 249 messages suppressed.
[168464.425925] rtc: lost some interrupts at 2048Hz.
[168469.430513] printk: 249 messages suppressed.
[168469.430522] rtc: lost some interrupts at 2048Hz.
[168474.425675] printk: 249 messages suppressed.
[168474.425687] rtc: lost some interrupts at 2048Hz.
[168479.407650] printk: 248 messages suppressed.
[168479.407658] rtc: lost some interrupts at 2048Hz.
[168484.409687] printk: 249 messages suppressed.
[168484.409695] rtc: lost some interrupts at 2048Hz.
[168489.411516] printk: 249 messages suppressed.
[168489.411525] rtc: lost some interrupts at 2048Hz.
[168494.412468] printk: 249 messages suppressed.
[168494.412477] rtc: lost some interrupts at 2048Hz.
[168499.411081] printk: 249 messages suppressed.
[168499.411092] rtc: lost some interrupts at 2048Hz.
[168501.929174] /dev/vmmon[16051]: host clock rate change request 1043 -> 83
[168536.435395] usb 4-1: USB disconnect, address 13
[168558.323180] usb 4-1: new full speed USB device using uhci_hcd and address 14
[168558.519022] usb 4-1: configuration #1 chosen from 1 choice
[168558.522090] ipaq 4-1:1.0: PocketPC PDA converter detected
[168558.524479] usb 4-1: PocketPC PDA converter now attached to ttyUSB0
[168561.809773] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[168561.809808] ipaq 4-1:1.0: device disconnected

---

### Post by Whiffle on 2008-03-30
So the device is being detected, thats good.  Its being claimed by something in ubuntu though, thats not so good.  You might be able to figure it out what that is by running

lsof | grep ttyUSB0

Those other messages about things being suppressed are not normal, I'd make another thread on that.

---

### Post by bluewhale on 2008-03-31
Ok.  I tried running that with a capital O and then with a Zero for the last character of the lsof command. Both resulted in a prompt again after perhaps 5 seconds. 

Did it create a log somewhere that I can check?

---

### Post by snappy46 on 2008-05-01
This might help or maybe not.  I used to use vmware as well and had difficulty seeing my PDA with it.  I would look into the top device menu under USB and it was not there; eventhough I connected it.  

Here's the workaround I used eventhough it does not make any sense.  While keeping the PDA connected I notice that if I plug in a USB stick and then just remove it after a second or 2 all of a sudden my PDA would show up in the device menu.  At that point I would just connect it using the device menu and winXp detected my pda and sync it without any problems.

Sounds weird but it worked for me.

I am now using virtualbox instead of vmware but I haven't been able to sync my PDA at all with it.  My PDA is recognized by virtual box as soon as I plug it in but it won't sync.  I wish I could find a solution for that problem. Oh well nothing is perfect in the computer world....

---

