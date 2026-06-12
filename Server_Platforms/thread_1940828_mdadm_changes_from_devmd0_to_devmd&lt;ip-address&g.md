---
title: "mdadm changes from /dev/md0 to /dev/md/&lt;ip-address&gt;:0 on reboot of EC2"
date: 2012-03-14
forum: Server Platforms
---

### Post by Zoramite on 2012-03-14
I am using the Ubuntu 64 bit AMI and I have been trying to get an EBS raid setup. I can set it up fine the first time:

```
sudo mdadm --create --verbose /dev/md0 --level=10 --raid-devices=4 /dev/xvdg /dev/xvdh /dev/xvdi /dev/xvdj
```

And it works as expected:

```
sudo mdadm --detail --scan
ARRAY /dev/md0 metadata=1.2 name=ip-10-194-231-137:0 UUID=11e83c1e:93f9be80:23012aeb:c0ea17b3
```

But when I reboot the instance and do a scan it shows:

```
ARRAY /dev/md/ip-10-194-231-137:0 metadata=1.2 name=ip-10-194-231-137:0 UUID=11e83c1e:93f9be80:23012aeb:c0ea17b3
```

Where is it getting the ```
/ip-10-194-231-137:
``` from? How do I get it to just be ```
/dev/md0
``` on reboot?

---

### Post by rubylaser on 2012-03-14
I'm betting your /etc/mdadm/mdadm.conf file isn't setup correctly.  What's the output of this?

```
cat /etc/mdadm/mdadm.conf
```

You can create a proper file like this
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by Zoramite on 2012-03-14
Most of the config file are stock from the apt-get install, except the last two lines which I added:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Tue, 13 Mar 2012 23:07:43 +0000
# by mkconf $Id$

DEVICES /dev/xvdg /dev/xvdh /dev/xvdi /dev/xvdj
ARRAY /dev/md0 metadata=1.2 name=ip-10-194-231-137:0 UUID=11e83c1e:93f9be80:23012aeb:c0ea17b3
```

I got the ARRAY information from doing a `mdadm --detail /dev/md0` when I created the raid initially.

I just tried rebooting again and now I am getting `/dev/md127` when I do a `df -h`. I tried removing the `name=` as it talks about in [another post]("http://ubuntuforums.org/showthread.php?t=1764861):") and it still shows up as `/dev/md127`.

But, when I did `sudo update-initramfs -u` and restarted it seemed to pick things up correctly. I'm not sure if removing the `name=` portion of the conf file was needed, but the update seems to have done the trick.

---

### Post by rubylaser on 2012-03-15
Nope, the sudo update-initramfs -u is what fixed your problem, but you shouldn't have needed to run it unless you changed something with your array.  Oh well, please mark the thread as solved under the thread tools at the top.

---

