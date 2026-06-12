---
title: "Partitioning and free space"
date: 2007-12-14
forum: Windows
---

### Post by tadcan on 2007-12-14
Since my 80GB Hard drive is 2/3rds full it wont support a dual boot. Also some of the pins are damaged.

So as a temporary fix I've bought a new hard drive. After reading up on partitioning I came up with a plan.  To put the new drive in as the master and have the second as the slave. 

I would create a 20 GB partition for XP on the master, then leave the rest blank. Put all the saved stuff on the slave. 

I presume that when I boot up into XP I'll be able to see two disks. 

Anyway if people have some advice please tell because I'm just guessing.

---

### Post by LaRoza on 2007-12-14
Are these disks SATA or PATA or mixed?

Assuming they are PATA, as you seem to think, it will work, but only if you set the jumper to slave.

Don't waste the space on the new disk, use that free space for something.

---

### Post by tadcan on 2007-12-14
Yeah its Pata

Should have said, the free space is to test linux distros. Forgot to ask is it better to leave a black space then for the partitioning software to reduce a partition. 

Sorry its late for me, hope that makes sense.

---

### Post by LaRoza on 2007-12-14
> **tadcan said:**
> 
Should have said, the free space is to test linux distros. Forgot to ask is it better to leave a black space then for the partitioning software to reduce a partition. 


The unallocated space can be used by the distros, that makes sense. They will partition and format during the install.

---

### Post by tadcan on 2008-01-28
The saga continues. Some would say madness. 

I have an old hard drive with XP and a new hard drive that works with linux. Currently with fedora.

1) I need to know I have linux set up before I can migrate. 

2) My hard drive with windows doesn't like linux. With Ubuntu I'm sent to the busybox shell. With fedora it wont load with the XP drive as the slave because of some damaged pins.   

So I have set up the XP drive as the master (IDE) and fedora as the slave. When I boot up it sees XP. Can I tell XP to notice Fedora in the boot.

The painful option is to put XP on half of the new drive, copy the old drive to the new. Then use the other half for linux. Considering my lack of IT skills, hell might freeze over first. 

Any thoughts?

---

### Post by JDorfler on 2008-01-31
Okay, here we go, I am not sure if you have already installed WinXP and Ubuntu yet, but this how I did it. I have a Sager 5680, with a brand new 80 GB HDD, so I have to be careful what I put on and how.

First boot up with your WinXP disk. Using the WinXP partition manager create two partitions. The first one as NTFS, name it WinXP OS, and have it about 20 Gigs. Install your WinXP OS here. After installation, do not download any updates. Immediately after install run your defrag 3 times after you set your Virtual Memory to 0. I don't know why it's the number 3, but a smarter man than I recommended this.

Reboot your PC with your Ubuntu Live disk. There, use the Partition Manager to cut up the rest of your Hard Drive into 3 more partitions. The Second Partition as Ext3 and primary, the third will be your swap. (RAM x 2 = Swap Partition size for me) and the forth will be NTFS. I label this one Programs.
After doing this Install Ubuntu using Ext3 partition in the manual install mode.
Make sure you right click Ext3 and make sure you label it (./) not root or anything else.

Now, what's great about Ubuntu is it reads and writes to NTFS. With this in mind you can always keep your Thunderbird Mail folders in sync with both your WinXP and your Ubuntu.

Now, go back to your WinXP via Grub and set your min and max virtual memory. Again I use RAM x 2 = Virtual Memory. (This helps a lot with fragmentation) Then download ALL your updates. It's a lot, so if you have a slow connection and trust your pc to not lock up, go play a round of golf.

After you get back from your 18, go ahead and take a shower, clean your clubs, inventory your balls, or whatever it is you want to do. Now, I am pretty sure you have a ton programs you want to install. This is where your second NTFS partition comes into play. I named mine, Programs. Make sure you always to a manual install of every piece of software you install, and also make sure it is installed on this second NTFS partition.

Now, to keep your email email synced. Install the latest version of Thunderbird. Go ahead and set up your accounts as normal. DO NOT AUTO DOWNLOAD ANY MAIL! Just set up your accounts. Now. This is the important part, make sure you have all hidden folders able to be viewed. If you don't want to do this WinXP, go ahead and boot into Ubuntu and do this. Use your file manager to copy your email folder from your WinXP OS partition and place it into your Programs partition. The path will be something like this:

Documents and Settings > (Your WinXP Profile Name) > Application Data > Thunderbird > Profiles > (bunch of letters).default > Mail

Copy (do not Cut) the Mail folder and place it anywhere you want in your Programs Partition, but remember where you placed it.

Now, go into your WinXP Thunderbird and got to account settings and the Server Settings to each email account you have on there and change the path to"
Program/Mail/(and that particular mail account's name.)

It's best to use Browse in order to do this.

Go to Ubuntu, download Thunderbird, set up your email accounts, and have Thunderbird look into the exact same folders as you set up in WinXP.

You can also do the same thing as all the above for your Newsgroups as well.

Now, this is a huge warning. If you have an anti-virus program in WinXP like AVG, it will only scan emails that are coming in whilst in WinXP. All emails downloaded in Ubuntu will not be scanned. Thus, if you're not sure about an email whilst in Ubuntu, delete that email from your system immediately before returning to WinXP.

The quick and dirty way of syncing your Lightning is to use the Google Provider extension. Also, using the Foxmarks in Firefox to help you sync your bookmarks in either WinXP or Ubuntu.

Now, you can download your emails until your heart's delight. If you download and read them in Ubuntu, they'll registered as downloaded and read in WinXP, or vise versa. Have fun.

---

### Post by tadcan on 2008-02-01
Thanks for your detailed reply. I'll have to use a free day and give it a go.

---

### Post by JDorfler on 2008-02-01
You're welcome.

---

