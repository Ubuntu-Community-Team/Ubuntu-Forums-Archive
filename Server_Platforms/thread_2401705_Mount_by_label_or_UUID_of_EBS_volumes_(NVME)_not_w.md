---
title: "Mount by label or UUID of EBS volumes (NVME) not working with EC2 C5 instances"
date: 2018-09-21
forum: Server Platforms
---

### Post by michael8888 on 2018-09-21
[COLOR=#000000][FONT=verdana]I am unable to mount EBS volumes in C5 instances via UUID or label. For instance this doesn't work with Ubuntu 18.04:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]e2label /dev/nvme1n1 DATA[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]mkdir /data[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]mount -L DATA /data[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]There is no error message, but the volume won't be mounted[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]However, I can mount this way:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]mount /dev/nvme1n1 /data[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I have the same problem when I try to mount via UUID.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]This all works fine in C4 instances.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I need to mount this way because NVME volumes are randomly assigned to device names. This causes problems in fstab if you stop the instance and launch it again. I can mount mount via volume id. However, this then causes problems if you create a new AMI from the instance.

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]This seems to be an Ubuntu issue. I just tried it with Amazon Linux and mounting via labels works there. I also was able to mount a local SSD via label. However EBS volumes don't work.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]This what I see in syslog:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Sep 21 11:50:43 ip-10-0-0-145 kernel: [/FONT][/COLOR][http:// 915.753600]("http://915.753600")[COLOR=#000000][FONT=verdana] EXT4-fs (nvme2n1): mounted filesystem with ordered data mode. Opts: (null)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Sep 21 11:50:43 ip-10-0-0-145 systemd[1]: Unmounted /data.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Sep 21 11:51:47 ip-10-0-0-145 systemd[1]: data.mount: Unit is bound to inactive unit dev-xvdg.device. Stopping, too.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Maybe a Ubuntu bug?[/FONT][/COLOR][COLOR=#000000][FONT=verdana]


[/FONT][/COLOR]

---

