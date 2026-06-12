---
title: "Offsite Backup Solution"
date: 2013-02-12
forum: Server Platforms
---

### Post by bubylou on 2013-02-12
My previous solution for backups was archiving  my 13gb of pictures, documents, and other important files to /srv/backup directory. (crontab+tar script) Then the files would sync with my 50gb dropbox account. However that account had its extra storage taken from it and it doesn't look like they will be giving it back.

I have also recently bought 2 new drives and set them all up into a raid 5 array. My storage now looks like this.
4gb swap
16gb /
1.32gb /srv

I could just start using my other dropbox account but that would only really be a temporary solution and certainly not the best. (Dropbox uses ~/Dropbox which was only symlinked to /srv/backup so it would quickly run out of space)

Now im looking for a new place to store my backups.  A free cloud drive would be ideal but i wouldn't mind paying for something if it was justified. Such as it being linux friendly, proper price/storage, and any other useful features. Any advice or perhaps personal setup example would also be greatly appreciated.

One place that came to mind was media fire. They have free 50gb and number of other nice features. However i noticed that free account can be deleted and there is a minimum file size requirement. I could just edit my backup scrip to have them split up but its something to keep in mind. I also only saw an ubuntu gui app, so im wondering how i could get that to work on my headless server. Any media fire users here?

---

### Post by Habitual on 2013-02-12
s3 is one way.

Pricing is [here...]("http://aws.amazon.com/s3/pricing/")

"buckets" they are called and can be mounted via sshfs (installed from source) or a s3cmd (in a repo near you)

sshfs can be mounted via /etc/fstab for persistence.

I may have mis-read the OP.
Are you seeking off-site storage, or a secondary host to ensure reliable backups or using your raid setup?

---

### Post by bubylou on 2013-02-12
Im just looking for some type of cloud space to backup some of my more important files. Just want to make sure that if something were to happen all my irreplaceable files are safe.

---

### Post by LHammonds on 2013-02-12
For home use, I don't trust my files on the web (family pics/videos/documents) so my solution for offsite backup of data files is simply to use USB hard drives.  I use Western Digital's 1.5 TB MyBook.  I have 3 of them.

One stays plugged into my PC all the time and backup jobs run automatically to write to it daily.  At regular times, I swap the USB drive with another I have onsite, then I take the one I just unplugged to work (offsite) and swap it with the one I have there.

This allows a copy to always be offsite and 2 copies onsite.  The one I have onsite that is not plugged in lives inside a broken microwave oven which acts like a faraday cage to protect from lightning/EMP blasts.

LHammonds

---

### Post by chrisguk on 2013-02-12
As already stated above for home use or even small office use.  In fact scrap that even on a large scale use, a good set of disks will some RAID implemented will be a good start.  Then if you really want to ensure your stuff is safe and backed up why not use Bacula?

Its an open source CLI program which is quite complicated to learn but once you have the basics, its a powerful backup solution.  With tonnes of options.

I use it and I had to receive some lessons how to use it from a forum member.  I wont look back now because it has saved my bacon already.

---

### Post by bubylou on 2013-02-12
I don't think you quite understand what im looking for. Im not looking for a program to help make my backups. Im looking for a place to store them on the internet.

---

### Post by CharlesA on 2013-02-12
> **bubylou said:**
> I don't think you quite understand what im looking for. Im not looking for a program to help make my backups. Im looking for a place to store them on the internet.

I've been using [CrashPlan]("http://www.crashplan.com") for a couple months after I saw a recommendation from someone on these forums. You can store your stuff at a friend's place for free, or use their cloud services for a price.

However, if you are just wanting to store files in the cloud, and now really backup to the cloud? According to your OP, you could start another dropbox account, but that sounds like a pain.

I decided on CrashPlan because of their unlimited plan, decent price and slick client.

---

