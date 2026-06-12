---
title: "Need Help Update and big problems"
date: 2020-03-14
forum: Ubuntu Development Version
---

### Post by paulycalvinmiller on 2020-03-14
The update today has me in a tough situation. at this point I can't boot a bootable usb, I can't enter the bios and I can't load grub so I can't get to recovery. What I do have is Minimal Bash Like Line editing from grub>

when I do LS I get the following output.
(proc) (hd0) (hd0, apple2) (hd0, apple1) (hd0, msdos2) (hd1) (hd1, gpt2) (hd1, gpt1)

Is there a way to tell it to boot the usb so I can just re install? Or can you tell me how to load the kernel so I can get to the Grub boot menu options? I would prefer just to re install.

Thanks



I was able to get to recovery mode. I have access to root shell prompt. but it won't drop to root command line. I tried dpkg but there are errors and its not fixing the broken packages.



/lib/recover-mode/recovery-menu: line 80: /etc/default/rcs" No such file or directory

package dependenices

but dpkg in recovery fails and root shell will not load

I am hoping that maybe an update will happen that will allow dpkg to work?

---

### Post by rbmorse on 2020-03-14
No solutions, but I just experienced the same thing.  They said this could happen...

---

### Post by holiday on 2020-03-14
Me too.

On my other 20.04 machines I have disabled and masked

apt-daily.timer
apt-daily-upgrade.timer
unattended-upgrades

I doubt there is a fix for broken machines unless there is a 'repair' option on the livecd? Don't see anything like it though.

---

### Post by paulycalvinmiller on 2020-03-15
Yeah I am screwed. I believe the only solution is to replace the SSD and start over. PC will not boot to USB or OS. Bios are set correctly. Nothing under the Ubuntu recovery options works. Root terminal will not load and dpkg does not work I would love to thank whatever Ubuntu developer pushed that update through. Maybe they should take a little more time with it. Good Job!

---

### Post by holiday on 2020-03-15
Could you slip the SSD into a USB dock and format it from another machine.

---

### Post by paulycalvinmiller on 2020-03-16
No my computer will not boot to USB even though the bios are set to choose it as the first option. Something to do with the boot loop cause by the currently installed OS. I believe it needs to be removed entirely to remove the current os and then I am hoping that I will be able to boot a bootable USB to re install.

---

### Post by holiday on 2020-03-16
I was thinking you remove the SSD and reformat it. You were talking about discarding it -- I thought you meant. I'm saying you don't have to discard it. You can clean it, put it back in your computer and re-install Ubuntu that way.

There's no doubt your Ubuntu installation is hopelessly broken. I'm talking about the physical disk.

---

### Post by paulycalvinmiller on 2020-03-16
ah okay how would I remove it and reformat. I would appreciate your help. I will start the process of removing it tonight and I will report back once I have it out.

---

### Post by oldfred on 2020-03-16
Have you tried "cold" boot?
That  is full power down and if laptop remove battery. Disconnect mains and hold power switch to drain all power.
Then boot and press correct key to either get into UEFI/BIOS or one time boot key like f12 or f10 check you manual as it varies a lot by vendor.

Fast boot in UEFI settings skips UEFI check on system. It assumes everything is identical both hardware & software settings wise. And that is so fast you do not have time to press any key. Best to have fast boot in UEFI off when making any sort of system change. 
UEFI/BIOS normal boot scans system for what hardware & configuration you have and writes that to drive for operating system to use.

---

### Post by paulycalvinmiller on 2020-03-16
I think I kind of did that. I ran the battery completely down on purpose and left it off for a while. But I am able to get into the bios now. So I can get in there an turn off fast boot. This is what my pc will currently do. It will boot to the grub menu. It offers the configurations options to enter UEFI/Bios. It fails to boot OS. If I go into recovery mode it will not activate net working. It will not complete DPKG. It will not drop to root shell. so none of the recovery options work. It will not boot to USB. This Laptop has not ethernt option, no cd drive and only one USB port. Two Typ C USB ports. I did not have windows on this PC.

I will take it apart tonight and remove the battery as you have said. I think I will also take out the SSD.

---

### Post by paulycalvinmiller on 2020-03-16
okay I have removed the ssd and I have removed the battery and I held the power button. How long to hold the power button? Is there a next step to re format the ssd?

oh I don't think you realized that this battery is no a removable battery.

This ssd cannot plug into a usb from what I can tell. I may just have to replace it.

I ordered a new one on ebay. It was only $32. I can return it if it doesn't work. I actually upgraded to 500 GB as well.

---

### Post by mc4man on 2020-03-16
It seems highly unlikely that an Ubuntu update would prevent you from booting to a live usb and doing a fresh install..

---

### Post by paulycalvinmiller on 2020-03-16
I have a bootable usb that I have used to install Ubuntu with in the past. I have checked the bios and USB is the first selection. I have rebooted the pc numerous times and the USB never boots. It always attempts to boot the broken os. So I don't know what to tell you but that is happening. This is the result of a broken upgrade.

---

### Post by mc4man on 2020-03-16
So you've tried explicitly setting to boot to usb from a boot selection screen (typically a key from F9 thru F12)? 
Or failing to discover that or in case laptop doesn't offer  going into setup/bios > boot options to set usb as 1st device?

---

### Post by paulycalvinmiller on 2020-03-16
yes that option is set up as the 1st options. I really can't understand it either. At this point I have taken the laptop apart and removed the ssd. I am waiting for a new one to arrive.

---

### Post by mc4man on 2020-03-16
Oh well..
Technically if you were to turn machine on without a harddrive you should be presented the opportunity to pick a boot device, ie. the usb device inserted. While of no actual value as nothing to install to it would be interesting..

If your machine does have a boot selection menu that would be preferable to bios setting.. What make and model?

---

### Post by paulycalvinmiller on 2020-03-16
Lenovo Yoga 920. I think when the new ssd get here I should be able to get it worked out.

---

### Post by mc4man on 2020-03-16
Well good luck then.
I've a couple of lenovo's, the boot menu is F12. Though maybe not on a yoga, not sure.
There also could be a novo button, if so and working it opens a screen where boot menu is available, many times the novo button is a small hole with backwards arrow.

---

### Post by oldfred on 2020-03-16
Is it one of these?
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

Issues often common by brand and somewhat similar models. These may have a clue on issues.
Lenovo Yoga S740     [SOLVED] Installation problem
[https://ubuntuforums.org/showthread.php?t=2433373](https://ubuntuforums.org/showthread.php?t=2433373)
Lenovo Yoga 730-15IWL i5-8265U
[https://askubuntu.com/questions/1182889/install-ubuntu-on-lenovo-yoga-730-15iwl-with-a-i5-8265u-cpu-alongside-windows](https://askubuntu.com/questions/1182889/install-ubuntu-on-lenovo-yoga-730-15iwl-with-a-i5-8265u-cpu-alongside-windows)

---

### Post by paulycalvinmiller on 2020-03-19
Thanks for trying everyone. I installed a new SSD and reinstalled Ubuntu. Going to mark as solved. I still can't understand why the PC would not boot from the USB.

---

### Post by Irihapeti on 2020-03-19
If you can, it's not a bad idea to run development releases in a VM, or at least on a second machine. That way, if things go south, you can still use your main install.

---

