---
title: "Persistently exposing iSCSI LUNS after a reboot"
date: 2019-07-16
forum: Server Platforms
---

### Post by Neil_Sherin on 2019-07-16
[SIZE=2]Hiya,

I've just set up an Ubuntu 18.04 VM with a second 10GB drive as a test that I want to set up as block storage over iSCSI. The problem is, when I reboot the iSCSI target VM, the LUN dos not show up when running [COLOR=#000000][FONT=&amp]tgtadm --mode target --op show[FONT=arial]

Running a [FONT=century gothic]systemctl restart [/FONT]fixes the issue and the LUN shows up as LUN 1 when running [/FONT][/FONT][/COLOR][COLOR=#000000][FONT=&amp]tgtadm --mode target --op show

[FONT=arial]Here's what I did to set up an iSCSI target:

[/FONT][/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Arial]Assume:[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=Arial]/dev/sdb is the disk to use as an iSCSI LUN[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=&amp]iqn.2019-07.local.nsnetworks:netstorage[/FONT][/COLOR][COLOR=#000000][FONT=Arial] is the target name[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=&amp]192.168.1.30 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]is the IP address of the iSCSI target portal[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=Arial]Setting up the target:[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Install required packages:[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=&amp]sudo su -[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=&amp]apt install -y tgt[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Create iSCSI target (tid 1)[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=&amp]tgtadm --lld iscsi --op new --mode target --tid 1 -T iqn.2019-07.local.nsnetworks:netstorage[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Add logical Unit (lun 1) to iSCSI target (Target ID 1)[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=&amp]tgtadm --lld iscsi --op new --mode logicalunit --tid 1 --lun 1 -b /dev/sdb[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Publish iSCSI target (tid 1) to all IP address[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=&amp]tgtadm --lld iscsi --op bind --mode target --tid 1 -I ALL[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Save configuration for iSCSI target. If you do not save configuration, configuration will be removed after restarting tgtd[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=&amp]tgt-admin --dump |grep -v default-driver > /etc/tgt/conf.d/disk.conf[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Enable service:[/SIZE]
[/LIST]
[SIZE=2][COLOR=#000000][FONT=&amp]systemctl enable tgt[/FONT][/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]Show status[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE][SIZE=2][COLOR=#000000][FONT=&amp]tgtadm --mode target --op show

[FONT=arial]Any help getting the LUN to show up persistently when the iSCSI target is rebooted would be much appreciated!

Many thanks in advance![/FONT][/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][/SIZE]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by Neil_Sherin on 2019-07-17
i then tried to set up a udev mapping to see if that would resolve the issue:


[LIST]
[*][COLOR=#000000][FONT=Arial]Create udev rule for proper device mapping of sdX to iscsi_X on boot[/FONT][/COLOR] 
[/LIST]

[COLOR=#000000][FONT=Arial]Using sdb as an example:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]udevadm info --query=property --name=/dev/sdb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Make a note of the values of:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ID_SCSI_SERIAL[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ID_SERIAL[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ID_SERIAL_SHORT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Create symbolic link for iscsi_1 mapping:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]ln -s /dev/sdb /dev/iscsi_1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Set up udev rule:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]nano /etc/udev/rules.d/70-persistent-drive.rules[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Add the following:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]SUBSYSTEM=="block", ENV{ID_SCSI_SERIAL}=="6000c29831ec9a7d45dc007e6439a6d6", ENV{ID_SERIAL}=="36000c29831ec9a7d45dc007e6439a6d6", ENV{ID_SERIAL_SHORT}="6000c29831ec9a7d45dc007e6439a6d6". SYMLINK+="iscsi_1"[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Reload udev rules:[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]udevadm control --reload-rules && udevadm trigger
[FONT=arial]
On reboot, it still does not expose the LUN. I have to do the following to get the LUN exposed:

[FONT=courier new]ln -s /dev/sdb /dev/iscsi_1
[/FONT][/FONT][/FONT][/COLOR][FONT=courier new][COLOR=#000000]udevadm control --reload-rules && udevadm trigger
systemctl tgt restart

[FONT=arial]Again, any help would be much appreciated.[/FONT][/COLOR]
[/FONT]

---

### Post by darkod on 2019-07-17
Did you go through the official doc in case something there can help you? It seems they are doing it in a different way (hasn't worked with iscsi that much lately myself).
[https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

---

