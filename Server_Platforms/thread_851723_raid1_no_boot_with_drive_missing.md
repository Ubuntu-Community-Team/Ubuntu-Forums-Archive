---
title: "raid1 no boot with drive missing"
date: 2008-07-06
forum: Server Platforms
---

### Post by mspIggy on 2008-07-06
after 4 days of very hard work, i am finally getting more comfortable with thie ubunty 8.04 server

i have it loaded - actually figured out how to set it up for raid 1 

in testing - the server will not boot with a missing drive...

i a have found this...

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

mentioning some sort of a 'bug' that accounts for this...

and suggests this:
WARNING: There is a serious bug which makes the boot fail if one of the physical disks in the RAID1 set is missing. The following code in /usr/share/initramfs-tools/scripts/local should help. 

martti@ubuntu:~$ sudo vi /usr/share/initramfs-tools/scripts/local
 # The following code was added to allow degraded RAID arrays to start
 if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
  # Try mdadm and allow degraded arrays to start in case a drive has failed
  log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
   /sbin/mdadm --assemble --scan
  log_end_msg
 fi
............. .............

however - the file on current server is different...

# If the root device hasn't shown up yet, give it a little while
        # to deal with removable devices
        if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; 2>&1; then                log_begin_msg "Waiting for root file system..."

                # Default delay is 180s
                if [ -z "${ROOTDELAY}" ]; then
                        slumber=180
                else
                        slumber=${ROOTDELAY}
                fi        


how do i add this - or what really needs to be added to make this work...

---

### Post by windependence on 2008-07-07
You need to have grub loaded on both drives to be able to boot from either one.

-Tim

---

### Post by mspIggy on 2008-07-07
hi tim

i do have grub loaded -- from what i can tell...

i am testing with primary drive out of machine completely...

i went thru grub install process - said it was done...

i would imagine if i put a new harddrive in the primary bay, it would boot - it would work?

---

### Post by windependence on 2008-07-07
As I understand it, grub must be loaded on BOTH drives to be able to boot when one is missing. Makes sense to me. You have to explcitly load grub on the other drive. Since I don't use software RAID, I'm afraid I can't help you there but maybe a quick google will do it.

-Tim

---

### Post by TheGameAh on 2008-07-07
I went through this same exact thing.  I have a detailed post on it here somewhere else.

From what I gather is this.

Indeed, it is a bug.  I have grub also installed on both drives.  Pulling a drive would result in the system not booting.

In the end, I ended up using Debian.

---

### Post by mspIggy on 2008-07-07
your machine boots with debian?...

i found a maybe solution but my files did not look the same....

as noted here in my post...

what is the straight poop on this?

i would really like to use this, but right now i am 'hadicapped'

whats the deal ??

this is very frustrating

many thanks

---

### Post by windependence on 2008-07-07
Buy a RAID card. You'll be glad you did.

-Tim

---

### Post by mspIggy on 2008-07-08
a good raid card for this server is almost 400.oo 

no thanks

can any body here offer up a REAL solution?

many thanks

---

### Post by windependence on 2008-07-08
> **mspIggy said:**
> a good raid card for this server is almost 400.oo 

no thanks

can any body here offer up a REAL solution?

many thanks

OK well first, do you REALLY need RAID? You can mirror the drive a number of ways other than RAID.

You could:

Image the drive using dd which would preserve all the boot information, and then run a cron job to rsync the disk every so often. You would still have a usable copy of your disk and data.

Use both drives in an LVM group and just make sure you have good verifiable backups.

Use one drive for production and back up to the other drive your important information. Then, take an image of your OS before you add any data and save it. If you have a failure, load the image and then restore your data.

Just a few suggestions. Also, you shouod be able to find a controller card cheaper than that. Try eBay or use something other than 3ware.

-Tim

---

### Post by mspIggy on 2008-07-08
hi tim --

4:30 am 

i cannot sleep this is bothering me so much...

i see there are more things to consider...

what about this suggested 'patch' i posted? it just does not seem to fit my file -- is there a way to 'meld' the 2 that you think may work?

many thanks for your suggestion :)

iggy

---

### Post by windependence on 2008-07-08
Well I'm not sure as I don't run software RAID - ever. I have just not had good experiences with it. Some people have and that's great, but most of my stuff is for my customers and is mission critical. That doesn't mean I like to spend money. I buy used equipment when possible, but it is GOOD equipment. recently, I bought 2 brand new RAID cards on eBay for $60 each. If you do a little digging, you can do this too.

-Tim

---

