---
title: "PERC H710 Adapter problem after latest update"
date: 2021-08-17
forum: Server Platforms
---

### Post by volkswagner on 2021-08-17
I'm curious if there may be a bug.

According to iDRAC the controller, memory, battery, and disks all have clean bill of health.

I was getting the following messages in kern.log the following day after the auto-update, but I think server usage was low until it showed its ugly face.

```
Aug 17 11:07:56 somers1 kernel: [102347.545358] INFO: task jbd2/dm-0-8:356 blocked for more than 120 seconds.
Aug 17 11:07:56 somers1 kernel: [102347.545432]       Not tainted 5.4.0-81-generic #91-Ubuntu
Aug 17 11:07:56 somers1 kernel: [102347.545475] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 17 11:07:56 somers1 kernel: [102347.545535] jbd2/dm-0-8     D    0   356      2 0x80004000
Aug 17 11:07:56 somers1 kernel: [102347.545540] Call Trace:
Aug 17 11:07:56 somers1 kernel: [102347.545552]  __schedule+0x2e3/0x740
Aug 17 11:07:56 somers1 kernel: [102347.545557]  ? bit_wait_timeout+0xa0/0xa0
Aug 17 11:07:56 somers1 kernel: [102347.545561]  schedule+0x42/0xb0
Aug 17 11:07:56 somers1 kernel: [102347.545564]  io_schedule+0x16/0x40
Aug 17 11:07:56 somers1 kernel: [102347.545568]  bit_wait_io+0x11/0x50
Aug 17 11:07:56 somers1 kernel: [102347.545571]  __wait_on_bit+0x33/0xa0
Aug 17 11:07:56 somers1 kernel: [102347.545575]  out_of_line_wait_on_bit+0x8d/0xb0
Aug 17 11:07:56 somers1 kernel: [102347.545581]  ? var_wake_function+0x30/0x30
Aug 17 11:07:56 somers1 kernel: [102347.545586]  __wait_on_buffer+0x34/0x40
Aug 17 11:07:56 somers1 kernel: [102347.545590]  jbd2_journal_commit_transaction+0xf50/0x17f0
Aug 17 11:07:56 somers1 kernel: [102347.545598]  ? try_to_del_timer_sync+0x54/0x80
Aug 17 11:07:56 somers1 kernel: [102347.545602]  kjournald2+0xb6/0x280
Aug 17 11:07:56 somers1 kernel: [102347.545606]  ? wait_woken+0x80/0x80
Aug 17 11:07:56 somers1 kernel: [102347.545611]  kthread+0x104/0x140
Aug 17 11:07:56 somers1 kernel: [102347.545614]  ? commit_timeout+0x20/0x20
Aug 17 11:07:56 somers1 kernel: [102347.545617]  ? kthread_park+0x90/0x90
Aug 17 11:07:56 somers1 kernel: [102347.545620]  ret_from_fork+0x35/0x40
Aug 17 11:07:56 somers1 kernel: [102347.545629] INFO: task jbd2/dm-2-8:627 blocked for more than 120 seconds.
Aug 17 11:07:56 somers1 kernel: [102347.545682]       Not tainted 5.4.0-81-generic #91-Ubuntu
Aug 17 11:07:56 somers1 kernel: [102347.545724] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 17 11:07:56 somers1 kernel: [102347.545784] jbd2/dm-2-8     D    0   627      2 0x80004000
Aug 17 11:07:56 somers1 kernel: [102347.545786] Call Trace:
Aug 17 11:07:56 somers1 kernel: [102347.545792]  __schedule+0x2e3/0x740
Aug 17 11:07:56 somers1 kernel: [102347.545796]  ? bit_wait_timeout+0xa0/0xa0
Aug 17 11:07:56 somers1 kernel: [102347.545799]  schedule+0x42/0xb0
Aug 17 11:07:56 somers1 kernel: [102347.545802]  io_schedule+0x16/0x40
Aug 17 11:07:56 somers1 kernel: [102347.545806]  bit_wait_io+0x11/0x50
Aug 17 11:07:56 somers1 kernel: [102347.545809]  __wait_on_bit+0x33/0xa0
Aug 17 11:07:56 somers1 kernel: [102347.545812]  out_of_line_wait_on_bit+0x8d/0xb0
Aug 17 11:07:56 somers1 kernel: [102347.545816]  ? var_wake_function+0x30/0x30
Aug 17 11:07:56 somers1 kernel: [102347.545820]  __wait_on_buffer+0x34/0x40
Aug 17 11:07:56 somers1 kernel: [102347.545823]  jbd2_journal_commit_transaction+0xf50/0x17f0
Aug 17 11:07:56 somers1 kernel: [102347.545830]  ? try_to_del_timer_sync+0x54/0x80
Aug 17 11:07:56 somers1 kernel: [102347.545833]  kjournald2+0xb6/0x280
Aug 17 11:07:56 somers1 kernel: [102347.545837]  ? wait_woken+0x80/0x80
Aug 17 11:07:56 somers1 kernel: [102347.545841]  kthread+0x104/0x140
Aug 17 11:07:56 somers1 kernel: [102347.545844]  ? commit_timeout+0x20/0x20
Aug 17 11:07:56 somers1 kernel: [102347.545846]  ? kthread_park+0x90/0x90
Aug 17 11:07:56 somers1 kernel: [102347.545849]  ret_from_fork+0x35/0x40
Aug 17 11:07:56 somers1 kernel: [102347.545874] INFO: task smbd:7275 blocked for more than 120 seconds.
Aug 17 11:07:56 somers1 kernel: [102347.545924]       Not tainted 5.4.0-81-generic #91-Ubuntu
Aug 17 11:07:56 somers1 kernel: [102347.545966] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 17 11:07:56 somers1 kernel: [102347.546025] smbd            D    0  7275    996 0x00000000
Aug 17 11:07:56 somers1 kernel: [102347.546028] Call Trace:
Aug 17 11:07:56 somers1 kernel: [102347.546032]  __schedule+0x2e3/0x740
Aug 17 11:07:56 somers1 kernel: [102347.546037]  ? bit_wait_timeout+0xa0/0xa0
Aug 17 11:07:56 somers1 kernel: [102347.546039]  schedule+0x42/0xb0
Aug 17 11:07:56 somers1 kernel: [102347.546043]  io_schedule+0x16/0x40
Aug 17 11:07:56 somers1 kernel: [102347.546046]  bit_wait_io+0x11/0x50
Aug 17 11:07:56 somers1 kernel: [102347.546049]  __wait_on_bit+0x33/0xa0
Aug 17 11:07:56 somers1 kernel: [102347.546053]  out_of_line_wait_on_bit+0x8d/0xb0
Aug 17 11:07:56 somers1 kernel: [102347.546056]  ? var_wake_function+0x30/0x30
Aug 17 11:07:56 somers1 kernel: [102347.546060]  __wait_on_buffer+0x34/0x40
Aug 17 11:07:56 somers1 kernel: [102347.546066]  __ext4_find_entry+0x306/0x440
Aug 17 11:07:56 somers1 kernel: [102347.546070]  ? ext4_fname_prepare_lookup+0xe8/0x130
Aug 17 11:07:56 somers1 kernel: [102347.546075]  ext4_lookup+0x176/0x270
...trim...
Aug 17 11:11:53 somers1 kernel: [102584.861358] megaraid_sas 0000:08:00.0: NVMe passthru support	: No
Aug 17 11:11:53 somers1 kernel: [102584.861360] megaraid_sas 0000:08:00.0: FW provided TM TaskAbort/Reset timeout	: 0 secs/0 secs
Aug 17 11:11:53 somers1 kernel: [102584.861362] megaraid_sas 0000:08:00.0: JBOD sequence map support	: No
Aug 17 11:11:53 somers1 kernel: [102584.861364] megaraid_sas 0000:08:00.0: PCI Lane Margining support	: No
Aug 17 11:11:53 somers1 kernel: [102584.889628] megaraid_sas 0000:08:00.0: JBOD sequence map is disabled megasas_setup_jbod_map 5680
Aug 17 11:11:53 somers1 kernel: [102584.889634] megaraid_sas 0000:08:00.0: megasas_enable_intr_fusion is called outbound_intr_mask:0x40000000
Aug 17 11:11:53 somers1 kernel: [102584.889640] megaraid_sas 0000:08:00.0: Adapter is OPERATIONAL for scsi:0
Aug 17 11:11:53 somers1 kernel: [102584.891750] megaraid_sas 0000:08:00.0: Reset successful for scsi0.
Aug 17 11:11:53 somers1 kernel: [102584.893575] megaraid_sas 0000:08:00.0: 9249 (2s/0x0020/CRIT) - Controller encountered a fatal error and was reset
Aug 17 11:11:53 somers1 kernel: [102584.893918] megaraid_sas 0000:08:00.0: 9253 (4s/0x0020/FATAL) - Controller cache discarded due to memory/battery problems

```




Here is the update log from yesterday morning:
```
Start-Date: 2021-08-04  06:54:49
Commandline: /usr/bin/unattended-upgrade
Upgrade: libgnutls-openssl27:amd64 (3.6.13-2ubuntu1.3, 3.6.13-2ubuntu1.6), libgnutls30:amd64 (3.6.13-2ubuntu1.3, 3.6.13-2ubuntu1.6)
End-Date: 2021-08-04  06:54:50

Start-Date: 2021-08-16  05:36:34
Commandline: apt-get -y install alsa-ucm-conf language-pack-en language-pack-en-base libdrm-amdgpu1 libdrm-common libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libegl-mesa0 libgbm1 libgl1-mesa-dri libglapi-mesa libglx-mesa0 libssl1.1 linux-generic linux-headers-generic linux-image-generic login mesa-vulkan-drivers openssh-client openssh-server openssh-sftp-server openssl passwd python3-distupgrade ubuntu-advantage-tools ubuntu-release-upgrader-core wireless-regdb
Install: linux-headers-5.4.0-81-generic:amd64 (5.4.0-81.91, automatic), linux-modules-extra-5.4.0-81-generic:amd64 (5.4.0-81.91, automatic), linux-modules-5.4.0-81-generic:amd64 (5.4.0-81.91, automatic), libllvm12:amd64 (1:12.0.0-3ubuntu1~20.04.3, automatic), linux-headers-5.4.0-81:amd64 (5.4.0-81.91, automatic), linux-image-5.4.0-81-generic:amd64 (5.4.0-81.91, automatic)
Upgrade: linux-headers-generic:amd64 (5.4.0.80.84, 5.4.0.81.85), libdrm-nouveau2:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), alsa-ucm-conf:amd64 (1.2.2-1ubuntu0.8, 1.2.2-1ubuntu0.9), openssl:amd64 (1.1.1f-1ubuntu2.4, 1.1.1f-1ubuntu2.5), libegl-mesa0:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.3~20.04.1), linux-image-generic:amd64 (5.4.0.80.84, 5.4.0.81.85), libglapi-mesa:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.3~20.04.1), ubuntu-advantage-tools:amd64 (27.1~20.04.1, 27.2.2~20.04.1), openssh-sftp-server:amd64 (1:8.2p1-4ubuntu0.2, 1:8.2p1-4ubuntu0.3), passwd:amd64 (1:4.8.1-1ubuntu5.20.04, 1:4.8.1-1ubuntu5.20.04.1), language-pack-en:amd64 (1:20.04+20210121, 1:20.04+20210802), libgbm1:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.3~20.04.1), libdrm-amdgpu1:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), python3-distupgrade:amd64 (1:20.04.35, 1:20.04.36), ubuntu-release-upgrader-core:amd64 (1:20.04.35, 1:20.04.36), libdrm2:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), login:amd64 (1:4.8.1-1ubuntu5.20.04, 1:4.8.1-1ubuntu5.20.04.1), openssh-server:amd64 (1:8.2p1-4ubuntu0.2, 1:8.2p1-4ubuntu0.3), libgl1-mesa-dri:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.3~20.04.1), openssh-client:amd64 (1:8.2p1-4ubuntu0.2, 1:8.2p1-4ubuntu0.3), language-pack-en-base:amd64 (1:20.04+20210121, 1:20.04+20210802), libdrm-intel1:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), libdrm-radeon1:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1), mesa-vulkan-drivers:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.3~20.04.1), libssl1.1:amd64 (1.1.1f-1ubuntu2.4, 1.1.1f-1ubuntu2.5), linux-generic:amd64 (5.4.0.80.84, 5.4.0.81.85), wireless-regdb:amd64 (2020.11.20-0ubuntu1~20.04.1, 2021.07.14-0ubuntu1~20.04.1), libglx-mesa0:amd64 (20.2.6-0ubuntu0.20.04.1, 21.0.3-0ubuntu0.3~20.04.1), libdrm-common:amd64 (2.4.102-1ubuntu1~20.04.1, 2.4.105-3~20.04.1)
End-Date: 2021-08-16  05:38:06

Start-Date: 2021-08-16  07:09:10
Commandline: /usr/bin/unattended-upgrade
Remove: linux-image-5.4.0-77-generic:amd64 (5.4.0-77.86), linux-modules-extra-5.4.0-77-generic:amd64 (5.4.0-77.86)
End-Date: 2021-08-16  07:09:24

Start-Date: 2021-08-16  07:09:30
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-5.4.0-77-generic:amd64 (5.4.0-77.86)
End-Date: 2021-08-16  07:09:34

Start-Date: 2021-08-16  07:09:37
Commandline: /usr/bin/unattended-upgrade
Remove: linux-modules-5.4.0-77-generic:amd64 (5.4.0-77.86)
End-Date: 2021-08-16  07:09:38

Start-Date: 2021-08-16  07:09:40
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-5.4.0-77:amd64 (5.4.0-77.86)
End-Date: 2021-08-16  07:09:43
```

One LVM is at 93% capacity. Do you think this could cause the above?
```
/dev/mapper/somers1--vg-cadactive    246G  216G   19G  93% /mnt/sambashares/cadactive
```

Could this be a firmware issue with the new kernel?
The perc controller is running the latest available firmware from 
Dell Dated 2017 (21.3.5-0002).

Should I try booting the previous kernel?
```

root@somers1:/var/log# uname -r
5.4.0-81-generic

root@somers1:/var/log# ls -l /boot
total 143512
-rw-r--r-- 1 root root   237851 Jul  9 11:49 config-5.4.0-80-generic
-rw-r--r-- 1 root root   237851 Jul 15 14:01 config-5.4.0-81-generic
drwxr-xr-x 5 root root     4096 Aug 16 07:09 grub
-rw-r--r-- 1 root root 56410481 Jul 23 06:04 initrd.img-5.4.0-80-generic
-rw-r--r-- 1 root root 56411984 Aug 16 05:37 initrd.img-5.4.0-81-generic
drwx------ 2 root root    16384 Nov  9  2015 lost+found
-rw-r--r-- 1 root root   182704 Aug 18  2020 memtest86+.bin
-rw-r--r-- 1 root root   184380 Aug 18  2020 memtest86+.elf
-rw-r--r-- 1 root root   184884 Aug 18  2020 memtest86+_multiboot.bin
-rw------- 1 root root  4751959 Jul  9 11:49 System.map-5.4.0-80-generic
-rw------- 1 root root  4752515 Jul 15 14:01 System.map-5.4.0-81-generic
-rw------- 1 root root 11768064 Jul  9 12:09 vmlinuz-5.4.0-80-generic
-rw------- 1 root root 11772160 Jul 15 14:05 vmlinuz-5.4.0-81-generic
```



I'm not sure if I should spend more time troubleshooting before
extending the LVM.

Much of this is a bit over my head. 
Should I believe the kern.log over what iDRAC tells me?

---

### Post by MAFoElffen on 2021-08-18
I believe and trust what my iDRAC says in my Dell Servers...

Wondering if just trying the last installed kernel corrects that... To remotely do that, instead at a console, you can reset the priority of that menu item in grub...

If it does, then confirmed and turn in a bug report.

---

### Post by volkswagner on 2021-08-19
Thanks @MAFoElffen,

I rebooted the server to manually select the earlier kernel.
Upon reboot, I saw an error message regarding the battery (BIOS
level before Grub screen), yet nothing logged in iDRAC (and iDRAC
still says all is well).

I'll keep an eye on it.

---

### Post by MAFoElffen on 2021-08-19
For the just-in-cases... (power failures, natural disasters, Zombie Apocalypse, Gremlins, etc.) You can pin how it boots, so it doesn't accidentally reboot to that newer menu item by accident... Gurb2 used to default to the last manually used, but I noticed it doesn't do that on mine anymore.

Look at the Menu Item Item and copy the text within the quotation marks... Edit your Grub Defaults file and go down to the line that says "GRUB_DEFAULT=" and enter that text within the quotation marks:
```
GRUB_DEFAULT="Ubuntu, with Linux 5.4.0-xx"
```
Then update your Grub... Just saying, things happen.

---

