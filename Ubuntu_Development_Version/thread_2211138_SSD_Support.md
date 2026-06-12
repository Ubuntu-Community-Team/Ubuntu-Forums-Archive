---
title: "SSD Support"
date: 2014-03-14
forum: Ubuntu Development Version
---

### Post by makitso on 2014-03-14
For reasons, I built my trusty environment on a regular HD.  Once the systems was configured correctly and tested, I copied it to my SSD.  The question is, will the Trusty SSD Trim support work or do I need to do something else.  I do have discard's in the fsbab.

---

### Post by oldfred on 2014-03-14
Not sure how Trusty checks for SSD, but if you installed on HD, that would not have the trim, so you would have to do something to enable it.

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim


 Trim in 14.04
[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)

---

### Post by makitso on 2014-03-14
Thanks.  I had the webupd8 cron job set up prior to 14.04.  However, it's interesting that /etc/cron.weekly does have the fstrim script.  Oh well, I will monitor it. As a side question, does 14.04 require the disable option in fstab?

---

### Post by oldfred on 2014-03-14
If you mean discard not disable, they are two ways of trimming. I would not use both.

With my daily I added a log file entry like this:

 #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

You can modify the trim file to add the log if it does not have it.
I do not know what will happen with weekly, but my daily log shows lots of trim.

---

### Post by NZjelle on 2014-03-15
I have similar question. Looking at the fstrim script in /etc/cron.weekly/ it says:

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  [https://launchpad.net/bugs/1259829](https://launchpad.net/bugs/1259829)). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.

So what should I do if I do not have an Intel or Samsung SSD?

If I heed the warning about data loss on SSD from other brands should I revert to using the discard option in fstab instead?

---

### Post by makitso on 2014-03-16
> So what should I do if I do not have an Intel or Samsung SSD?  If I heed the warning about data loss on SSD from other brands should I revert to using the discard option in fstab instead?

Seems to me that it's not easy to validate that the corn.weekly script is running.  So in my case, I am still going to run my own corn script on a daily basis.  Using the discard option in fstab is not recommended.

---

