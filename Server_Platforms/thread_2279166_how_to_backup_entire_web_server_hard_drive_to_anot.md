---
title: "how to backup entire web server hard drive to another"
date: 2015-05-21
forum: Server Platforms
---

### Post by allan7 on 2015-05-21
Hi Everyone,

I've been running Ubuntu Server for quite a while but I have never done a descent back up really yet. I did some rsync before but only to backup a portion of the server let's say a couple of directories only. What I wanted to do now is if it's possible to backup the entire hard drive to another so if something happen to the original one I can just plug in the other hard drive and go back online again. I know it's possible but I would like to know the simplest way you guys have in mind. 

Setup:
4 Ubuntu Server 14.04 running under ESXi 4.0

1. Web Server
2. Cloud Server
3. NameServer 1
4. NameServer 2

The only piece out of this 4 virtual server I would like to backup to another physical hard drive is the WEB SERVER portion. The other three aren't really necessary. 

Plan is:
Add another physical HD on the same machine and do the backup


Thanks in advance

---

### Post by allan7 on 2015-05-21
Hi,

Sorry for not reading properly. I will post this to the right one.

Thanks

---

### Post by allan7 on 2015-05-21
Hi Everyone,

I've been running Ubuntu Server for quite a while but I have never done a  descent back up really yet. I did some rsync before but only to backup a  portion of the server let's say a couple of directories only. What I  wanted to do now is to backup the entire hard drive to  another so if something happen to the original one I can just plug in  the other hard drive and go back online again. I know it's somehow possible but I  would like to know the simplest way you guys have in mind. 

Setup:
4 Ubuntu Server 14.04 running under ESXi 4.0

1. Web Server
2. Cloud Server
3. NameServer 1
4. NameServer 2

The only piece out of this 4 virtual server I would like to backup to  another physical hard drive is the WEB SERVER portion. The other three  aren't really necessary. 

Plan is:
Add another physical HD on the same machine and do the backup


Thanks in advance

---

### Post by Royke on 2015-05-21
Hello alan7,

What i did to make backup is install a second system on the same day i received my new ssd drive. Now i'm in trouble on my productionsystem(i use ubuntustudio) and run my untouched system to figure out what is wrong. Using another ubuntu system is also an easy way to make a backup of anything you want. It may be hard to restore but at least it is there. In my whole history of computing i was never able to restore from an official backup program. That is no lie. I do these things by hand and came pretty far with it. Be root when you do these things. I really hope someone else comes with a better answer..

---

### Post by allan7 on 2015-05-21
Thanks for the tip Royke. Using another ubuntu system is what I'm about to do but just holding back a bit more and wait for some other suggestions as I'm also worried how to do a restore if anything goes bad. By the way, any suggestions on how to do it if ever I use another ubuntu system? Rsync should be good enough right?

Cheers

---

### Post by TheFu on 2015-05-22
Normally people use commercial products like Veeam, Trilead, et al to backup ESXi VMs.  VMware seems to mandate a 3rd party backup solution. I've deployed Trilead stuff before. Meh - not as nice as rdiff-backup, IMHO.

However, you **can** treat each of these VMs as physical servers and perform backups using nominal Linux tools, if you like.  dd, ddrescue, partimage, clonezilla, dejadup, duplicity, duplicati, rdiff-backup, and 20 other tools can be used.  Or you can do a mix of tools, since versioned backups really are critical for servers and making an image-based backups is so "windows" and completely unnecessary. Making an image-based backup requires booting off alternate media to ensure no files are left open. That means downtime.

For other virtualization tools, like Xen or KVM, you could use the hostOS to help with backups by taking advantage of LVM's snapshot capability. Alas, you are running ESXi and they want $$$ for backup tools.

So ... I don't do image-based backups. If something really bad happens, I just want to be able to restore within about 30-45 min.  rdiff-backup is the tool that I've found which does the things I need. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the clearest how-to I know for this.  I've had backup religion for over a decade - due a huge amount of data loss. For VMs, I **know** my method works, since it gets tested every few months just so I don't lose practice.  I've posted in these forums multiple times the details of my method.  Be certain to test a restore - since we all know, "backups are hope, tested restores are a plan. You need a plan."

Didn't ESXi 4.0 support end over a year ago? - yep. 5/2014. [https://www.vmware.com/files/pdf/support/Product-Lifecycle-Matrix.pdf](https://www.vmware.com/files/pdf/support/Product-Lifecycle-Matrix.pdf)

---

### Post by bruce-hyatt on 2015-05-22
I would think backing up the configuration file(s) and the /var/www directory would be sufficient. Then you could just paste the backed up files and directories into a new server and you'd quickly be back in business.

- Bruce

---

### Post by cariboo on 2015-05-22
Merged duplicate threads.

---

### Post by Habitual on 2015-05-22
> **bruce-hyatt said:**
> I would think backing up the configuration file(s) and the /var/www directory would be sufficient. Then you could just paste the backed up files and directories into a new server and you'd quickly be back in business.

- Bruce
Hey Bruce,
It's what I use:
```
#!/bin/bash
# 10/05/2013 01:39:12 PM EDT
# running via cron as 59 23 * * * /root/webdump.sh 
mysqldump -u<user>  -p<pass>  <db> > /path/to/db.sql
tar -pczf /tmp/<name>_$(date +%F).tar.gz /path/to/db.sql /var/www/ /etc/apache2/sites-enabled/000-default 
rm /path/to/db.sql
#EOF
```

```
sudo apache2ctl -S
``` will show you the known configuration files for your host.
adjust if necessary.

after it runs, check /tmp/<name>_<*YYYY-MM-DD*>.tar.gz
as it may need additional processing.

Hope that helps.

---

### Post by mastablasta on 2015-05-25
> **TheFu said:**
> 
So ... I don't do image-based backups. If something really bad happens, I just want to be able to restore within about 30-45 min.  rdiff-backup is the tool that I've found which does the things I need. 

yeah i just got it bricked - image was made and it turns out the image was no good. the new one is also not good (well duh it had damaged files when i created it) or perhaps the disk really has issues (waiting for new disk). also i stored 2 more images on another drive before doing any change on server. i can't find them now. :lolflag:

i will get another USB flash drive for system disk. i am thinking about trying rdiff. 

lesson learned = doing backup is easy. restoring is the hard part... :P

> **Habitual said:**
> 
after it runs, check /tmp/<name>_<*YYYY-MM-DD*>.tar.gz
as it may need additional processing.


what may need additional processing? why?

---

### Post by TheFu on 2015-05-25
IMHO ....

Web servers need to hardened.  The default config for most OS installs just doesn't qualify as "hardened." If something is changed from the default, then it needs to be backed up - PERIOD.  That means not just getting the data, DBs, and webserver config files. We need the kernel parm changes, network stack tuning changes, any specialized firewall changes (you do block outbound traffic except in response to web requests right??!@!!), reverse proxy settings, and the hundreds of little things for alarming, monitoring, system configs, system hardware config, any specialized drivers, backup scripts, ... the list goes on and on.  

YOU are the expert on YOUR system. Nobody else can tell you exactly what may or may not need to be backed up.

Be certain to test the backup on bare metal.  Under the stress of doing a restore is not the time to try to remember some small detail for recovery.

Or you can go with image-based backups using any of the tools I've listed above. The issue with this method is that the disks holding all those files must be un-mounted, inactive. Downtime. Find a "save-your-ass" Linux distro, boot into that using the ISO boot facility of the VM software and use any of the image-making backup tools listed already. Of course, if whole drive encryption is used, it is a little more complicated AND absolutely, completely, critical, that good, current, backups exist. I'm partial to **fsarchiver** for this.

Of course, if the hostOS has LVM, we can take a snapshot and use that for our backups without any downtime (even on the hostOS). I don't remember having any way to tell ESXi to take a snapshot with free software.  As I've said before, for ESX/ESXi, most people expect the $1K-$2K cost of backup software and build that into their budget.  It isn't as flexible as the F/LOSS options, but if you aren't too worried about wasting lots of backup storage, those commercials tools are almost 1-click solutions.

---

### Post by Habitual on 2015-05-26
> **mastablasta said:**
> what may need additional processing? why? All I meant you may wish to move it off host by some other "manual" method or secondary script|tool.

Peace.

---

### Post by mastablasta on 2015-05-27
> **Habitual said:**
> All I meant you may wish to move it off host by some other "manual" method or secondary script|tool.

Peace.

ahh it makes sense now. 

I thought some additional tinkering is necessary with the file (permission or something), that's what got me confused.

---

