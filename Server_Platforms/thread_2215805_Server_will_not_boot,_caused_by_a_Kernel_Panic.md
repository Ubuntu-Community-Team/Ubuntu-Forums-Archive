---
title: "Server will not boot, caused by a Kernel Panic?"
date: 2014-04-08
forum: Server Platforms
---

### Post by Euskadi1888 on 2014-04-08
I rent a dedicated server which runs Ubuntu 12.04

Two days ago everything inexplicably went down. I hadn't made any changes or even been logged in at the time.

Now as I don't have physical access to the machine, I am able to perform reboots etc through a web interface. I tried rebooting but got told it was unsuccessful due to a 'kernel panic'. The only thing I'm able to do is to boot into 'rescue mode' which allows me to log in via SSH and mount the file system and look around that way. I've looked at a few of the logs but can't see anything that would suggest what the actual problem is. The most recent entries are just some connections that UFW has denied.

How can I find out what is actually causing the kernel panic?

---

### Post by TheFu on 2014-04-08
Look at the log files.  'dmesg' should show any issues during boot.
Problems at boot when there haven't been changes are likely hardware issues. Not good.

---

### Post by Euskadi1888 on 2014-04-08
What should I be looking for in dmesg? The file isn't timestamped or anything.

I've carried out tests on the HDD, RAM and CPU and it didn't return any errors.

---

### Post by TheFu on 2014-04-08
At every boot, it gets re-written with boot up data. There's something about the normal boot which is failing, but not failing in safe-mode. I'd check
* all disk arrays
* all network devices
* all pci / usb devices

So the hard part is that normal boots don't get far enough for a remote connection, so you cannot see the dmesg output. Do you have a remove console? That is really what is needed here.   Perhaps [http://www.supermicro.com/products/nfo/SMS_IPMI.cfm](http://www.supermicro.com/products/nfo/SMS_IPMI.cfm) ?

---

### Post by Euskadi1888 on 2014-04-08
Honest I haven't got a clue what to do, I've never dealt with a problem this bad!

the dmesg file hasn't been modified since Feb so I don't suppose will have anything useful?

---

### Post by TheFu on 2014-04-08
dmesg is a command to my knowledge.  If there is an old file, that seems to be a hint.  In safe mode, is the main partition read-only?  If that is the situation, an fsck is needed.

BTW - a kernel panic could mean the server is hacked.

---

### Post by Euskadi1888 on 2014-04-08
By safe mode do you mean when I boot in rescue-mode yeah? I'm not sure if it's read only - if I want to view my filesystem I have to run:
> mount /dev/sda1 /mnt
mount /dev/sda2 /mnt/home

After that I can both read and write files to the mounted disk.

I have ran both "e2fsck /dev/sda1" and "e2fsck /dev/sda2" (read it wasn't safe to run this on mounted drives so did so without mounting) and rebooted but it's no different.

---

### Post by TheFu on 2014-04-08
I don't see my systems boot often and don't watch when that happens perhaps every 60 days.
What about plain fsck?
Do you know the diff between safe-mode and normal? I don't.

---

### Post by Euskadi1888 on 2014-04-09
I've ran fsck as well, no luck.

Should I be getting more info than "Kernel Panic"? As I don't have physical access I can't see the machine trying to boot, I'm just hearing that from the people I rent the server from. Should they be giving me more feedback than just those 2 words? Surely Ubuntu offers a more verbose error?

---

### Post by TheFu on 2014-04-09
There is a core file that will show exactly where things are going wrong, but it is hard to debug that without CONSOLE ACCESS.  At this stage, it isn't Ubuntu, it is how UNIX/Linux works.  I've never had a remote server where I didn't have console access and the ability to power it off and on myself.  RIBLO, DRAC, IPMI ... these things all provide that facility.

I have had to deal with Mom's remote PC, but I was cautious about kernel updates so I'd be coming to town within a few days, should anything go wrong.

Is there a bare metal restore that you can perform?

---

### Post by Euskadi1888 on 2014-04-09
I can reinstall the OS but I presume it would involve a format. I'm backing up my data as we speak, have the website files downloaded and have tarballed lib/mysql but it is 500mb and for some reason I can only get download speeds of around 35 kb/sec in rescue mode!!

---

