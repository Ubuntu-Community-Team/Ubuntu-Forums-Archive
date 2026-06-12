---
title: "Considering Tarsnap Backup Service again."
date: 2016-01-04
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-01-04
[Tarsnap]("https://www.tarsnap.com/")

I really like the security aspects of this app. For someone like me who only would backup < 1GB of data from my data partition, it would be not only very secure, but also very cost-effective online backups. Though, for larger backups it is still cost effective. [Pricing examples]("https://www.tarsnap.com/deduplication.html")

There is a[ PPA ]("https://launchpad.net/~jtgeibel/+archive/ubuntu/ppa?field.series_filter=trusty")now for it. 

There is a new [GUI]("https://github.com/Tarsnap/tarsnap-gui") for desktop users that, is expected to be offered with more features.

A write up with screenshots for the GUI [here]("https://github.com/Tarsnap/tarsnap-gui/wiki/Tarsnap").

I am happy to see this becoming available for more mainstream Ubuntu users who may want a GUI.

---

### Post by coldraven on 2016-01-05
I would not consider backing up to the "cloud" for several reasons.
Any online service can go down or be forced offline. See here for example [http://www.theregister.co.uk/2016/01/04/linode_back_at_last_after_ten_days_of_hell/](http://www.theregister.co.uk/2016/01/04/linode_back_at_last_after_ten_days_of_hell/)
Tarsnap might just go broke, I don't know their financial status.
It would take me 5 hours to upload 1 GB, memory sticks are cheap and fast.
There's also the legal and spying stuff which is best not mentioned here as it would become a political discussion.

---

### Post by buzzingrobot on 2016-01-05
It's best not to rely on any single approach to backing up important data.  Hardware can break, businesses can vanish or change, catastrophes can strike.

Less the one gig is a very small amount of data. Lots of ways to copy it someplace else. E.g., archive it into one file, burn it to a DVD, burn it to a USB stick, attach it to an email to yourself and let it sit on the server, etc.

I use cloud storage for a large amount of rather innocuous data. If the compromise of data could put me at financial or other risk, it stays off the cloud. The industry justifiably believes consumers will not pay for online services, so consumers should expect any data the create or push online to be massaged for cash until they -- consumers -- change their minds.

---

### Post by mikodo on 2016-01-05
Thank you, for the thoughts to consider folks.

I do save my data on 2 USB sticks. One is in the bank's safety deposit box, and one at home. I switch them out irregularly. Being I have been enthralled with this particular service for a couple of years because of who Colin is, I have gone back and forth on this. I marvel at his wizardly ways. I keep one file well, actually two that are encrypted for my passwords to banking institutions and email passwords and such. One is just a text file using gpg symmetrical and a second copy of that data in KeePassX. I don't think I would be able to take advantage of the de-duplication and compression with these small files but, I can always delete in TarSnap the older archives of them to keep those small files from getting copied too many times. So, I would not be depending on just TarSnap's service solely for backups.

But again, I will consider what you folks have written. I appreciate the advice as always.

Cheers!

Addendum:> **coldraven said:**
> Any online service can go down or be forced offline. See here for example [http://www.theregister.co.uk/2016/01]("http://www.theregister.co.uk/2016/01/04/linode_back_at_last_after_ten_days_of_hell/")
That's a valid concern. I remember when the email service I rely on the most, was hit with two DDoS attacks. I am not sure Colin has the resources and support to attend to that kind of thing.

Protonmail blog: [https://protonmail.com/blog/protonmail-ddos-attacks/](https://protonmail.com/blog/protonmail-ddos-attacks/)

---

### Post by mastablasta on 2016-01-06
you could use more cloud services... I think Copy and Spideroak both encrypt as well as Mega.

---

### Post by Skaperen on 2016-01-06
my cloud backup is AWS.  i do compress before sending and encrypt.  i also do memory sticks (they can be stolen). i also have a couple VPS servers, so the i have "backup diversity".

---

