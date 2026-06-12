---
title: "Fail to install OS on dell t320"
date: 2022-09-01
forum: Server Platforms
---

### Post by sniper8752 on 2022-09-01
I have a raid 1 setup on a dell t320.  I've attached the log of what happened.  It failed to install successfully. I've attached the log file: [https://pastebin.com/62nxe3ta](https://pastebin.com/62nxe3ta)

---

### Post by MAFoElffen on 2022-09-04
Which screen did it fail at? I see it failed at the Partitioner panel. Can you confirm that?

You said you configured RAID 1... In the PERC Card? Or mdadm software RAID in the installer? Because I see this:
```

 [    2.785600] ata1: SATA max UDMA/133 abar m2048@0xdf0ff000 port 0xdf0ff100 irq 38 
 [    2.857176] ata2: SATA max UDMA/133 abar m2048@0xdf0ff000 port 0xdf0ff180 irq 38 
 [    2.865047] ata3: SATA max UDMA/133 abar m2048@0xdf0ff000 port 0xdf0ff200 irq 38 
 [    2.872730] ata4: SATA max UDMA/133 abar m2048@0xdf0ff000 port 0xdf0ff280 irq 38 
 [    2.880350] ata5: SATA max UDMA/133 abar m2048@0xdf0ff000 port 0xdf0ff300 irq 38 
 [    2.887942] ata6: SATA max UDMA/133 abar m2048@0xdf0ff000 port 0xdf0ff380 irq 38 


```
Which with this right before it:
```

 [    2.895416] megaraid_sas 0000:08:00.0: pci id        : (0x1000)/(0x0073)/(0x1028)/(0x1f4e) 
 [    2.902968] megaraid_sas 0000:08:00.0: unevenspan support    : no 
 [    2.910447] megaraid_sas 0000:08:00.0: firmware crash dump    : no 
 [    2.917765] megaraid_sas 0000:08:00.0: JBOD sequence map    : disabled 
 [    2.924909] megaraid_sas 0000:08:00.0: Max firmware commands: 30 shared with default hw_queues = 1 poll_queues 0 
 [    2.938967] scsi host1: Avago SAS based MegaRAID driver 
 [    2.962544] scsi 1:2:0:0: Direct-Access     DELL     PERC H310        2.12 PQ: 0 ANSI: 5 
 [    2.988520] sd 1:2:0:0: Attached scsi generic sg0 type 0 
 [    2.988741] sd 1:2:0:0: [sda] 5859442688 512-byte logical blocks: (3.00 TB/2.73 TiB) 
 [    3.002353] sd 1:2:0:0: [sda] Write Protect is off 
 [    3.009150] sd 1:2:0:0: [sda] Mode Sense: 1f 00 10 08 
 [    3.009229] sd 1:2:0:0: [sda] Write cache: disabled, read cache: disabled, supports DPO and FUA 
 [    3.065158]  sda: sda1 sda2 sda3 
 [    3.072441] sd 1:2:0:0: [sda] Attached SCSI disk 

 
```
where you have one logical 3TB drive setup on a Dell RAID H310 controller. So you possibly have 6TB of storage configured as RAID1 right?

I'm curious on your PERC config,and the individual drives... Can you post that information?

EDIT: 
Could you please post /var/log//installer/subiquity-client-debug.log to a pastebin? That would show which options were entered into the installer... Then run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script and select up to pastebin... You could DL and run it from CLI of the Server Live Install image (select help from any panel that has a title bar, right upper corner, then select enter shell). Or from a browser if using a Desktop Install LiveCD image.

---

### Post by sniper8752 on 2022-09-06
They are 2 3 TB drives.
[https://paste.ubuntu.com/p/TDtxxJSJ7F/](https://paste.ubuntu.com/p/TDtxxJSJ7F/)
[URL="https://paste.ubuntu.com/p/YXm4mdg4T6/"]https://paste.ubuntu.com/p/YXm4mdg4T6/

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290997&stc=1[/IMG]
[/URL]

---

### Post by MAFoElffen on 2022-09-08
That disk layout should have worked and 'there' is not where I see the error... And in the 'system-info' report, I see where fdisk is showing that the storage is part of the PERC Logical Disk...

The Dell PE Servers, as noted by the 'system-info' report elsewhere, shows that it uses a Matrox G200eR2 integrated GPU... For these, in the Kernel Boot parameters, I add this as a boot parameter:
```

video=vesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Where the error dumps out:
```

2022-09-06 14:51:27,212 DEBUG subiquity.ui.ssh:272 User input: {'install_server': True, 'ssh_import_id': None}
2022-09-06 14:51:27,212 DEBUG subiquity.client.controllers.ssh:127 SSHController.done next_screen result=SSHData(install_server=True, allow_pw=True, authorized_keys=[])
2022-09-06 14:51:27,218 INFO subiquity/SSH:112 finish: completed SUCCESS
2022-09-06 14:51:27,218 INFO subiquity/Drivers:107 start: starting UI
2022-09-06 14:51:27,222 INFO subiquity/Drivers:112 finish: (skipped) SUCCESS
2022-09-06 14:51:27,222 DEBUG subiquitycore.tui:228 skipping screen Drivers
2022-09-06 14:51:27,222 INFO subiquity/SnapList:107 start: starting UI
2022-09-06 14:51:27,245 DEBUG subiquity.views.snaplist:420 pre-seeded snaps {'core20', 'lxd', 'snapd'}
2022-09-06 14:51:29,404 DEBUG subiquity.views.snaplist:467 snaps to install {}
2022-09-06 14:51:29,404 DEBUG subiquity.client.controllers.snaplist:53 SnapListController.done next_screen snaps_to_install=[]
2022-09-06 14:51:29,407 INFO subiquity/SnapList:112 finish: completed SUCCESS
2022-09-06 14:51:29,407 INFO subiquity/Progress:107 start: starting UI
2022-09-06 14:54:34,807[COLOR=#ff0000] DEBUG subiquity.client.client:569 show_error_report '1662476074.795521021.install_fail'[/COLOR]
2022-09-06 14:54:40,552 INFO subiquity/ErrorReporter/1662476074.795521021.install_fail/load:107 start: 
2022-09-06 14:54:40,948 INFO subiquity/ErrorReporter/1662476074.795521021.install_fail/load:112 finish:  SUCCESS
2022-09-06 15:05:26,068 INFO subiquity/ErrorReporter/1662476074.795521021.install_fail/upload:107 start: 
2022-09-06 15:05:26,069 DEBUG subiquitycore.common.errorreport:222 dropping CurrentDmesg of length 83190
2022-09-06 15:05:26,069 DEBUG subiquitycore.common.errorreport:222 dropping CurtinConfig of length 3259
2022-09-06 15:05:26,070 DEBUG subiquitycore.common.errorreport:222 dropping CurtinErrors of length 256000
2022-09-06 15:05:26,070 DEBUG subiquitycore.common.errorreport:222 dropping CurtinLog of length 192269
2022-09-06 15:05:26,070 DEBUG subiquitycore.common.errorreport:222 dropping InstallerServerLog of length 106255
2022-09-06 15:05:26,070 DEBUG subiquitycore.common.errorreport:222 dropping InstallerServerLogInfo of length 13549


```
I say that because in your logs, it adds the RAID controller, snaps, then fails at ??? and writes the error to the Curtin Logs... Wait one... (In the middle of imaging a new disk for my main workstation.)

EDIT:
Let me check what is supposed to happen in good debug logs to see which step it failed on. The config options chosen all look good there.

---

### Post by MAFoElffen on 2022-09-09
I don't see any conflicting options selected. At line #125 of your debug log, yours goes to an error... Whereas, successful installs just end that log there, and install. The only thing out of the ordinary, was that I saw you chose to disable both your Ethernet ports(???)

The next log to look at is /var/log/installer/curtin-install.log

---

