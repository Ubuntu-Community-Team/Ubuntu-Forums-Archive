---
title: "POP!_OS Won't Boot After Upgrading to RTX 2017"
date: 2020-04-19
forum: Ubuntu/Debian BASED
---

### Post by austinpena on 2020-04-19
[COLOR=#1A1A1B]Problems before upgrade:

[LIST]
[*]5+ minute boot time (on SSD)
[/LIST]
Problems after

[LIST]
[*]Computer  won’t wake up after suspension 1/4 of the time, meaning I have to  restart. This would be fine but the 5 minute restart gets old

[*]Boot stalling at Dell screen before I can choose my boot manager. Currently trying to get it to even boot
[/LIST]
Update: I was able to select the boot manager with f12 but it still hangs on the “dell” logo
Any recommendations? I raised a github issue about the boot time to no response.

[/COLOR]

---

### Post by CelticWarrior on 2020-04-19
Welcome.

A few questions:
[LIST=1]
[*]Is this a desktop or laptop? Dell model?
[*]What is a RTX 2017? Isn't it a Nvidia Graphics **RTX2070**?
[*]How did you install Pop_OS? And which version? There's one that includes Nvidia drivers and other that needs those drivers installed after the OS. The "Nvidia version" should work on System76 hardware, I'm not sure it install correctly in other brands.
[*]Why Pop_OS? Really? It's a Ubuntu based distro mainly geared towards System76 own models and the last version is based on the old Ubuntu 18.04. RTX2070 is newer so it makes Pop_OS a stupid choice. Try Ubuntu 20.04 and make sure to tick that option for installation of third-party drivers, codecs, etc.
[/LIST]

---

### Post by austinpena on 2020-04-19
Hi CelticWarrior!
1.
Computer is a Dell Desktop XPS 8700
2.
Typo, yes it is an RTX 2070 super
3.
I installed Pop os 19.10, the Nvidia version. Shouldn't that be the correct one because I have Nvidia hardware?

4.
Because I fell for the hype. I want to work with the most stable OS at this point for development, and I think that it should Ubuntu.
I will try to boot Ubuntu 20.04 now and will update my post.

I know to you the help you're giving might be trivial, but to me it means a lot. Thank you for taking the time out of your day to help me.

---

### Post by CelticWarrior on 2020-04-19
Make sure you're booting and consequently installing in UEFI mode.
Also disable Secure Boot in UEFI as it prevents loading some drivers, namely Nvidia's.

---

### Post by austinpena on 2020-04-19
I was planning on using Rufus to create my bootable drive. Is that the recommended software to achieve what you laid out above?

---

### Post by CelticWarrior on 2020-04-19
You can use Rufus but pay attention to the settings before burning: You want GPT/UEFI and/or just use the alternative DD method.
For Windows Balena Etcher is reliable and easier to use because it has no settings except the ISO file and target selection (it uses DD and only DD by default which provides a bit-by-bit copy of the hybrid Ubuntu ISO resulting in a bootable USB for BIOS or UEFI systems).

Also of note is the actual firmware (UEFI/BIOS) settings where, for better results, you want to have "UEFI only" or similar, i.e., disable anything mentioning legacy boot (not legacy USB support or legacy video, if applicable) or CSM. And again, Secure Boot OFF and optionally Fast Boot OFF (if applicable).

---

### Post by oldfred on 2020-04-19
Rufus seems to have two options on creating installer. One says MBR, CSM (UEFI) and other gpt UEFI. Not everyone knows CSM means BIOS boot. ISO is configured for either UEFI or BIOS, but installer may make it one or the other.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Be sure to have good backups before any changes.

Some older Dell seemed to need Legacy enabled, but set boot to UEFI. Newer systems need legacy turned off.
My old Haswell based Dell. has these settings.
Under Advanced: USB enable, On board device, AHCI.
Under boot: Secure Boot off, Load legacy, USB boot enabled, Boot mode UEFI. You need fast boot off in UEFI, as that assumes no system changes, and you are changing system around.
But then every USB installer has two boot modes UEFI:flash or flash where flash is name or label of flash drive. And one with just name is the BIOS/legacy/CSM boot mode.

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

See also link in my signature below.

---

### Post by austinpena on 2020-04-19
Thank you.

One big thing is that I've been successfully running Pop for a while.

> Some older Dell seemed to need Legacy enabled, but set boot to UEFI. Newer systems need legacy turned off.
My old Haswell based Dell. has these settings.
Under Advanced: USB enable, On board device, AHCI.
Under boot: Secure Boot off, Load legacy, USB boot enabled, Boot mode  UEFI. You need fast boot off in UEFI, as that assumes no system changes,  and you are changing system around.
But then every USB installer has two boot modes UEFI:flash or flash  where flash is name or label of flash drive. And one with just name is  the BIOS/legacy/CSM boot mode.

So in order to do this, I go to my Bios settings right? Unfortunately I can't even access this right now.

> Dell typically needs UEFI update, if SSD also SSD firmware update. 
Same here, I'll have to update after I get ubuntu up and running unless you know of another way. It's my impression that I've been getting auto updates through Dell's software though.

> Often better to have UEFI Secure boot off. Older Dell seemed to need  legacy on, but still select UEFI to boot (without secure boot). Newer  systems need legacy off to boot in UEFI mode.

I will be sure turn this off once I can access BIOS. Which is still impossible.

> And in Windows you need Windows fast start up off as that sets  hibernation flag and then Linux NTFS driver cannot see the NTFS  partitions. Note that Windows updates may turn fast start up back on.

This is off thankfully.

Thank you for the helpful link down there as well.

---

### Post by austinpena on 2020-04-19
As another update, when booting I only get 
> F2: Boot Options 
and then the F12 option.

---

### Post by oldfred on 2020-04-19
With Dell it should be either f2 or Delete key to get into UEFI.
If issues, you may have left fast boot on.
Fast boot assumes no system changes and just boots using whatever your configuration was before.
Often then you have to do a full "cold" boot. Or totally power down, if laptop remove battery, hold power switch for at least 10 sec to drain any remaining power and then boot & press correct key to get into UEFI.

Windows, grub & Ubuntu have ways to get into UEFI directly.
Grub has this:
menuentry 'UEFI Firmware Settings' $menuentry_id_option 'uefi-firmware' {
    fwsetup

Ubuntu/systemd has this:
Reboot into UEFI:
sudo systemctl reboot --firmware
sudo systemctl reboot --firmware-setup

---

### Post by austinpena on 2020-04-19
>  					With Dell it should be either f2 or Delete key to get into UEFI. 
Unfortunately it's not working.
> If issues, you may have left fast boot on.
I can almost 100% guarantee that I turned this off. I had issues with it before and ended up turning it off.

To confirm it, I've been removing the power cable and tried to press F2 or the DEL key on boot and couldn't get it.

Unfortunately, one issue is that as I'm trying to boot with my live USB and hold "shift" (I'm trying to dualboot windows) nothing happens. What options do I have with this scenario?

---

### Post by austinpena on 2020-04-19
I think I'm going to see if Boot repair works. I'm flashing it to my USB now.
Edit: nothing yet

---

### Post by oldfred on 2020-04-19
Do not use Boot-Repair ISO.
Just use the Ubuntu live installer and add ppa to install Boot-Repair to flash drive. You have to do that every time since flash drive installer cannot be updated, except in memory.
ISO is older and does not show as much info.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

