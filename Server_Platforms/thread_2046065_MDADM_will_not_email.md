---
title: "MDADM will not email"
date: 2012-08-22
forum: Server Platforms
---

### Post by Krupski on 2012-08-22
Hi all,

I am running Ubuntu 64 bit server 12.04 with MDADM.

My ISP is Verizon and I cannot get the MDADM email function to work.

I can send successfully send email from other applications, but not MDADM.

Here is my MDADM config file:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR rakrupski@verizon.net

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=d7886510:420a72f3:3c2c359a:50bb1976


```

Then I try to run the test:

mdadm --monitor --scan --test --oneshot

and it seems to complete (returns to the command prompt) but no email gets sent.

Anyone have any ideas why?

NOTE: if this matters Verizon uses SSL for mail on port 465, not standard SMTP on 25.

Thanks!

-- Roger

(edit to add): This may be of some help: It's one of many error messages that "mailq" gave me:

D742141787      819 Wed Aug 22 10:13:20  [email]root@verizon.net[/email]
(host outgoing.verizon.net[206.46.232.12] said: 550 5.7.1 Invalid mail address <root@verizon.net> (in reply to MAIL FROM command))
                                         [email]rakrupski@verizon.net[/email]

---

