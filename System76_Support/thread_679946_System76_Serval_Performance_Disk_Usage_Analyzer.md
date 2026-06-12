---
title: "System76 Serval Performance Disk Usage Analyzer"
date: 2008-01-27
forum: System76 Support
---

### Post by 982000971 on 2008-01-27
My Serval Performance came with an internal 80 GB hard drive.

My disk space is currently maxed out, I cannot event burn a CD image. Or is it?

-I have an 80 GB drive
-Disk Usage Analyzer says "Total Filesystem Capacity 69.7 GB"
-... "(65.9 Used. 3.8 GB Available)"
-"/ folder reads 47.2 GB used"

Can somebody explain these discrepancies? I know my drive is 80 GB, it says so on my System76 receipt. Yet Disk Usage Analyzer shows a capacity of only 69.7 GB. Furthermore it says most of that is used, but as far as I can tell I can only account for 47.2 GB of actual used disk space.

Please enlighten me, I upgraded to the 80 GB for a reason :(

---

### Post by thomasaaron on 2008-01-28
Well, when you order an 80GB hard drive, it comes with a little less than that actually available, as the OS takes up several gigs of it. Also, whenever you download software, of course, it uses more).

Then there are other little utilities that suck up some memory.

What is the output of this command:
df

---

### Post by 982000971 on 2008-01-28
df output >

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73076804  64626500   4738164  94% /
varrun                 1037172       216   1036956   1% /var/run
varlock                1037172         0   1037172   0% /var/lock
udev                   1037172        80   1037092   1% /dev
devshm                 1037172         0   1037172   0% /dev/shm
lrm                    1037172     34696   1002476   4% /lib/modules/2.6.22-14-generic/volatile

---

### Post by thomasaaron on 2008-01-28
So, your hard drive is 94% used by the applications and storage...

/dev/sda1 73076804 64626500 4738164 **94%**

Other usage includes:
varrun 1037172 216 1036956 **1%** /var/run
udev 1037172 80 1037092 **1%** /dev
lrm 1037172 34696 1002476 **4%** /lib/modules/2.6.22-14-generic/volatile

...equalling 100%.

You're done.  :)

Time to clean off stuff you don't need or get a bigger hard disk.

---

### Post by 982000971 on 2008-01-28
So how do I clean out my system? I know that sounds stupid... but I look at all my files (which I save in my home directory); my music collection, videos, documents, etc, etc and it equals 37.6 GB! my entire /home folder does not exceed 40 GB!! This is the only location I save anything!

Are you saying Ubuntu and it's software accounts for the other 40 GB? Something is amiss here...

---

### Post by thomasaaron on 2008-01-28
That's what it looks like. 

Do you have tons of software downloaded?

Is your system dual booted?

If you have virtual machines on it (maybe a windows vm that you made with vmware server?), that would take up a ton of space too.

Did you reinstall Ubuntu somewhere down the line? If you did, and you chose "Use largest available freespace" then you might have two installations of Ubuntu on your machine, only one of which is usable.)

If you have Partition Manager installed, you can look at your disk and tell me how it is partitioned. Maybe that will reveal something.

There are a lot of possible scenarios.

---

### Post by 982000971 on 2008-01-29
Tons of software? No, in fact I try to keep it to a minimum.

No dual-boot either.

No virtual machine.

I've only upgraded through Synaptic since I've had my laptop.

I installed Gnome partition editor just now to check on partitions. Here is what I see:

/dev/sda1/   ext3   /   70.80 GB   62.73 GB   8.08 GB  boot
/dev/sda2/   extended   3.73 GB   ---   ---   ---
>>/dev/sda5/   linux-swap   ---   ---   ---

The device information reads MODEL ATA ST980825AS, size 74.53 GB, path /dev/sda.

My first and most obvious question is why did System76 advertise a 74.53 GB as being 80 GB (I did after all pay extra to upgrade...)? And furthermore if GParted is saying I have 8.08 GB of unused disk space how come I get warnings if I download anything over 500mb or if I try to burn a cd image? And even then, which numbers are correct? The ones GParted are giving me? The ones Disk Usage nalyzer are giving me? Or the receipt invoice I have from System76..?

Little help please. All I want is to be able to use the disk space I paid for.

---

### Post by thomasaaron on 2008-01-29
> My first and most obvious question is why did System76 advertise a 74.53 GB as being 80 GB (I did after all pay extra to upgrade...)?

That is what I was explaining when I said:
> Well, when you order an 80GB hard drive, it comes with a little less than that actually available, as the OS takes up several gigs of it. Also, whenever you download software, of course, it uses more).

> And furthermore if GParted is saying I have 8.08 GB of unused disk space

That's not what it is saying. That is the area of your partition used to store files necessary for booting your operating system.


> And even then, which numbers are correct? The ones GParted are giving me? The ones Disk Usage nalyzer are giving me? Or the receipt invoice I have from System76..?

All three. Disk Usage Analyzer and GParted might be dicing up the information based on a different set of criteria. And a seventy-something GB hard drive *is* a 80GB hard drive after you subtract the OS.

One final note. You also have swap space on your hard drive which is equal to 2X your RAM. So if you have 2GB of RAM, you have 4GB of swap space reserved.

---

### Post by 982000971 on 2008-01-29
First off, thank you for your continued patience.

[http://compreviews.about.com/od/storage/a/ActualHDSizes.htm](http://compreviews.about.com/od/storage/a/ActualHDSizes.htm)
10-4, I "get" it now. It pisses me off to no end, but I get it... Alright, new expectation: 74.53 GB.

Let me just approach this differently. Can you help me allocate space on my laptop? I don't know where to look, with Disk Usage Analyzer I can account for 42.9 GB. That should mean 31.63 GB to work with. Minus 3.7 GB for the linux-swap. So roughly 28 GB right? I can't believe Ubuntu would require this much disk space to run. Is there anyway to find out what, within Ubuntu, is using all of this space? I only use like 10 software programs I really don't understand why Ubuntu would need so much space.

---

### Post by compholio on 2008-01-30
> **982000971 said:**
> ...
Let me just approach this differently. Can you help me allocate space on my laptop? I don't know where to look ...

Using a terminal go to the folder "/" (type "cd /" and hit enter), now run the command "du -h --max-depth=1".  This command will reveal to you the size of each folder on your drive, your biggest folders will likely be "/home" and "/usr", if not then inspect any folders that are abnormally large.  Now go to your home directory ("cd ~/") and re-run "du -h --max-depth=1", look for abnormally large folders.  When done visit the "/usr" folder and look for large folders, continue this procedure until you narrow down where your space is being consumed.  I recommend opening up a text editor (like "gedit") or a drawing tool (like "dia") and creating a tree of your largest folders.

NOTE: Deleting large folders is a bad idea, I recommend finding what program they are associated with and using Add/Remove to take care of it.  If the large folders are in your home directory then you've probably got a lot of large data files (music or movies) or have installed a lot of games under Wine (the folder "~/.wine").

---

### Post by 982000971 on 2008-01-30
0       ./proc
0       ./sys
4.7M    ./bin
48M     ./boot
84K     ./dev
42M     ./etc
40G     ./home
4.0K    ./initrd
340M    ./lib
8.0K    ./media
4.0K    ./mnt
3.3M    ./opt
19G     ./root
6.5M    ./sbin
4.0K    ./srv
172K    ./tmp
2.6G    ./usr
299M    ./var
62G     .

40G in ./home is expected. That is my music, videos, documents, etc etc that I can account for.

62G total does not count the operating system? This confuses me a bit, shouldn't the total equel 74.53G?

Expanding ./root >>>

8.0K    ./.ssh
4.0K    ./.wapi
108K    ./.gconf
4.0K    ./.gconfd
24K     ./.synaptic
56K     ./.gnome2
4.0K    ./.gnome2_private
4.0K    ./.aptitude
4.0K    ./.yanc42
1.4M    ./.azureus
7.2M    ./.mozilla
92K     ./.gnupg
16K     ./.config
12K     ./.dbus
1.5M    ./.bitpim-files
24K     ./.nautilus
4.0K    ./Desktop
12K     ./.gnome
19G     ./.Trash
1.3M    ./.thumbnails
488K    ./.gstreamer-0.10
4.0K    ./.tvtime
8.0K    ./.unison
28K     ./.xine
4.0K    ./.qt
104K    ./.kde
19G     .

19G ./.Trash !!! Bingo! So there are two trashes. /root Trash is different from the Trash that appears on my Desktop. I did not know that. I just KNEW there was no way I could be using that much disk space. Thank you thank you thank you!

Seriously, thank you thomasaaron and compholio. My problem is solved, I hope this thread helps anyone else who may be as uninformed as I am. I still don't understand what determines which Trash folder gets used but so long as I can easily empty the root one I don't care. Thanks!

---

### Post by compholio on 2008-01-30
> **982000971 said:**
> ...
62G total does not count the operating system? This confuses me a bit, shouldn't the total equel 74.53G?
...
I still don't understand what determines which Trash folder gets used but so long as I can easily empty the root one I don't care. Thanks!

the 62/80 GB needs a bit of explaining:
1) You already get the 1000/1024 issue: ~74.5 GB
2) ext2/3 use 5% of each partition for "reserved space" (this keeps thing runnings smoothly so you never lose files or need to defrag): ~70.8 GB
3) The partitions you've observed named varrun,varlock,udev,devshm, and lrm are all reserved for other important OS functions and take up part of the space of your primary partition (~1GB each): ~65.8 GB

There are some other things, like journaling, but I've never looked into how to calculate them.

Now, which "Trash" folder gets used depends on what user deleted the files.  At some point you must have logged in as "root" and deleted some files as root.  It is recommended that you do not login as root except for administrative reasons (which ubuntu will prompt you for, so you don't need to actually login as the root user).

---

### Post by BrandanLloyd on 2008-01-30
Try running the Disk Usage Analyzer, under Applications, Accessories.  This will give you a pretty display of how you are currently using your hard drive.

---

### Post by BrandanLloyd on 2008-01-30
Oops just ignore my post.  I hadn't refreshed the page to see that the issue was resolved.  Sorry for the noise.

---

### Post by riseringseeker on 2008-02-05
> **982000971 said:**
> 0 

19G ./.Trash !!! Bingo! So there are two trashes. /root Trash is different from the Trash that appears on my Desktop. I did not know that. I just KNEW there was no way I could be using that much disk space. Thank you thank you thank you!

Seriously, thank you thomasaaron and compholio. My problem is solved, I hope this thread helps anyone else who may be as uninformed as I am. I still don't understand what determines which Trash folder gets used but so long as I can easily empty the root one I don't care. Thanks!

19Gb root trash?  How are you deleting files with root privileges? If you are using nautilus, you may already know that you can add a a "Delete" function, bypassing the trash bin.

Places-> Home Folder-> Edit -> Preferences -> Behavior -> Include a Delete command that bypasses Trash.

If you did not know this, doing so might help prevent the problem from happening again.

---

