---
title: "How should I partition my HD?"
date: 2009-02-14
forum: System76 Support
---

### Post by flukeairwalker on 2009-02-14
I just bought a Pangolin laptop that should be arriving on Tuesday. It has 3GB RAM and a 250GB hard drive. I'm going to be using this computer as my main computer for every day home use i.e. e-mail, internet, documents, music, movies, and maybe games if I'm feeling adventurous with Wine. I will be running Ubuntu exclusively. What is the most optimal way to partition the hard drive?

---

### Post by yey365 on 2009-02-14
Everyone has their own preference for partitioning; ubuntu will handle the whole disk unless you want something more specific. I'd go with a 3072gb sawp file (for suspend) a 6-10gb root partition (/) and the remainder as home.

---

### Post by Guille Damke on 2009-02-14
Congratulations for the nice machine! I have a Pangolin too, and I really like it. 
I agree with yey365 on the swap partition size, it is recommended to have at least the amount of your RAM memory so you can suspend the system. You can check this: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

On the other hand, I don't agree about the root partition size. Since you have a 250GB hard disk, I would keep a bigger root partition. I have not installed too many programs yet and already have used 5.2GB. Remember that if you have only a root "/" and a /home partition, the programs you install goes to "/". I think at least 20GB is ok for "/", it is less than 10% of your disk!. In my case, for avoiding problems, I made a 37GB "/", and I feel free to install any program I want.

You can check other threads about this topic in the main forum. Finally, the best setup of your partitions depends on what you need.

---

### Post by linuxlibrarian on 2009-02-14
Got my Pangolin a little over a week ago... Basically Ubuntu's ready to go, aside from setting system time and user account information... I was happy to see that S76 set up the partition in a similar manner to how I've done my desktops in the past... 

/dev/sda1 is the root (/) partition, /dev/sda2 is swap (always strikes me funny when swap isn't the last numbered partition, but I know it's solely psychological on my part) and /dev/sda3 is the /home partition.

I have a 320 GB drive, with 14 gigs of it being the / partition, and the remainder on /home...

Always personally like having /home on a separate partition, keeps settings, files and such persistent over distribution switches/upgrades, etc.

---

### Post by flukeairwalker on 2009-02-14
I'm thinking of 5GB for swap, 10GB for root, and the rest for /home. Do programs install to the root partition? If so, is there a way I can install them into their own partition so I don't have to reinstall them on an OS reinstall?

---

### Post by jdb on 2009-02-14
> **flukeairwalker said:**
> I'm thinking of 5GB for swap, 10GB for root, and the rest for /home. Do programs install to the root partition? If so, is there a way I can install them into their own partition so I don't have to reinstall them on an OS reinstall?

When you install a program it's likely to write in /usr, /etc, /lib, /bin & /var among others.
You're pretty much stuck with reinstalling them if you reinstall the OS.
You can reinstall all your apps from a script which can be as simple as an "apt-get install" line for each app.

All your configurations will be in your home directory so you won't lose those.

If you
sudo mv /var/cache/apt/archives /home
and then
ln -s /home/archives /var/cache/apt/
you will have all the program installation files on the home partition.

Then after a reinstall if you remove the new /var/cache/apt/archives and relink it to the one in /home, you can reinstall all your apts without having to download anything.

jdb

---

### Post by flukeairwalker on 2009-02-15
*blinks* Sorry, I've only been a Linux user for three months now and while I don't mind following instructions for simple tasks such as apt-get install, I'm not yet versed in the command line. So let me see if I got this straight. I move "/var/cache/apt/archives" to "/home" before reinstall. Then after reinstall I remove "/var/cache/apt/archives" and I move"/home/archives" to"/var/cache/apt". This will move all programs to /home and then back to root so I don't have to reinstall or download anything.

Is there any way I can create a partition just for the programs though? Like, what is /var for? Can I create a /var partition and have all programs install there?

---

### Post by jdb on 2009-02-15
> **flukeairwalker said:**
> *blinks* Sorry, I've only been a Linux user for three months now and while I don't mind following instructions for simple tasks such as apt-get install, I'm not yet versed in the command line. So let me see if I got this straight. I move "/var/cache/apt/archives" to "/home" before reinstall. Then after reinstall I remove "/var/cache/apt/archives" and I move"/home/archives" to"/var/cache/apt". This will move all programs to /home and then back to root so I don't have to reinstall or download anything.

Is there any way I can create a partition just for the programs though? Like, what is /var for? Can I create a /var partition and have all programs install there?

The problem is that the programs don't install in /var, thats just where the install files are kept.
Those files are compressed archives (tarballs) that have a .deb suffix.

When the programs are installed by apt-get, the tarballs are un-compressed and the files in them are put in a lot of different places.
Also, actions are taken, such as modifying a file or installing another program that is a dependency.

It's probably not a good idea to move stuff around until you are more comfortable with Linux.

Here is the type of script you can write to load a list of applications.

```
sudo apt-get install build-essential
sudo apt-get install gcc-doc
sudo apt-get install gawk
sudo apt-get install gawk-doc
sudo apt-get install automake
sudo apt-get install autoconf
sudo apt-get install libtool
sudo apt-get install a2ps
sudo apt-get install alien
sudo apt-get install ascii
sudo apt-get install dclock
sudo apt-get install sox
sudo apt-get install gparted
sudo apt-get install gpm
sudo apt-get install gpsbabel
sudo apt-get install gpsman
sudo apt-get install libtk-img
sudo apt-get install imagemagick
sudo apt-get install kstars
sudo apt-get install lm-sensors
sudo apt-get install mailx
sudo apt-get install meld
sudo apt-get install mtools
sudo apt-get install speedcrunch
sudo apt-get install sysinfo
sudo apt-get install traceroute
sudo apt-get install units
sudo apt-get install uudeview
sudo apt-get install wireshark

```

Use a text editor to build a file like the one above.

From the command line:

```
chmod 755 your-file-name
```

That makes the file executable.

To install the applications, from the command line:

```
./your-file-name
```

The ./ tells it to execute a file in the current directory even though it is not in your normal execution path.



jdb

---

### Post by flukeairwalker on 2009-02-15
That. Is. So. Amazing! Thank you for that trick, it has laid all my fears to rest. Now I can comfortably reinstall my OS without fear of having to sift through and remember all programs I had. This is such a time saver.

For my 250 GB HD, Unless someone can convince me otherwise, I'm pretty sure I'm going to go with 5GB for swap, 20GB for root, and the rest for /home. That should be more than enough, especially considering that I don't even know what I'll do with so much space.

---

### Post by thomasaaron on 2009-02-16
Hi, flukeairwalker.

Welcome to the fam.

We install with a 15GB root partition. We tried installing with a 10GB partition, but got complaints that was too small. We've not gotten any complaints with 15GB. You can install an *aweful* lot of software on that.

On modern computers, it is basically a waste of space have more swap space than you have RAM. So, if your computer comes with, say, 4GB or RAM, we create 4GB of swap space.

The remainder of your disk is set up as a separate home partition. If you ever want another partition, you can always shrink you home partition and add new partitions in the freed space.

---

### Post by flukeairwalker on 2009-02-16
Thank you for the welcome! It's relieving to know that I don't have to worry about partitioning the hard drive anymore. I was fretting about this because I see Ubuntu has a ton of partitioning options, and I also heard that partitioning large hard drives makes them faster. But if you guys did it that way, it must work, so I'm not worried about that anymore. Now if only my laptop will arrive before I leave Thursday for vacation...

---

### Post by thomasaaron on 2009-02-16
Contact me at support(at)system76(dot)com, and I'll request a status on your order and see if I can expedite it.

---

### Post by flukeairwalker on 2009-02-16
Thanks for looking into it. I shot you an email.

BTW these are the best forums ever. It was my hate for Vista that drove me to Linux, but it's the community support that has me recommending the OS to all my friends.

---

### Post by Eldera on 2009-02-26
Because I am 73, don't drive, and am isolated in a senior citizen apartment complex, most of my computer skills have been self taught from help screens,etc. This has created a problem where I have gained an understanding of some things fairly advanced and overlooked others simple and basic. 

I purchased a Pangolin the first week in Febuary and am teaching myself to use it. I have had no previous hands on experience with Linux, just read a few books during the last year. 

I am trying to build a mental map of the partitions in my Pangolin and what kind of files are on each.

TA said in post 51, Meet the New System76 Laptops: "We set it up with boot, root, swap(1 x RAM) and the remainder as a separate home partition." (OK so I haven't figured out how to use the BB Code. One thing at a time.)

I assume the boot menu is on the boot partition, and swap is where ram things go when a system hibernates. Correct me if I'm wrong.

Where is the operating system? Is it only on one partition? Is that root?

When installing the files for new applications, do they go on more than one partition?

jdb said in post 6 of this thread: "When you install a program it's likely to write in /usr, /etc, /lib, /bin & /var among others."
and in post 8 "The problem is that the programs don't install in /var, thats just where the install files are kept.

When the programs are installed by apt-get, the tarballs are un-compressed and the files in them are put in a lot of different places."

Are these different places on different partitions, or different places on the same partition? Which partition/s?

I have saved all the data I have created so far in my home folder. Given the defaults as the Pangolin shipped from the factory, is my home folder on the home partition? 

Is there a way to display the partitions and what is on them?

I think if I start with a mental image of the partitions, then the directories on each partition, etc., I will have a better grasp of the "paths" when I get into studying the command line. 

Thank you for any help anyone has time to give.

And, Flukeairwalker, with three months experience, you're an old hand. Enjoy your Pangolin. I know I will just as soon as I figure out what I'm doing.

Eldera

---

### Post by thomasaaron on 2009-02-26
Eldera. You are very astute!
> 
I assume the boot menu is on the boot partition,

Almost. Files necessary for initially booting up the computer are on the boot partition. 

>  and swap is where ram things go when a system hibernates. Correct me if I'm wrong.

Correct.

> Where is the operating system? Is it only on one partition? Is that root?

Yes.

> When installing the files for new applications, do they go on more than one partition?

They typically go on the root partition.

> jdb said in post 6 of this thread: "When you install a program it's likely to write in /usr, /etc, /lib, /bin & /var among others."
and in post 8 "The problem is that the programs don't install in /var, thats just where the install files are kept.

...and all of those directories are on the root partition.

> When the programs are installed by apt-get, the tarballs are un-compressed and the files in them are put in a lot of different places."

Are these different places on different partitions, or different places on the same partition? Which partition/s?

They are put in various directories in the root partition.

> I have saved all the data I have created so far in my home folder. Given the defaults as the Pangolin shipped from the factory, is my home folder on the home partition?

Yes. You have a separate home partition.

> Is there a way to display the partitions and what is on them?

You could run these commands from a terminal...

#For boot partition
ls -a /boot

#For the root partition
ls -a /root

#For the home partition
ls -a /home

And there is nothing in the swap partition.

> I think if I start with a mental image of the partitions, then the directories on each partition, etc., I will have a better grasp of the "paths" when I get into studying the command line.

You really don't need to know anything about partitions to understand paths. A path is a path....

/var/log/syslog is on the root partition, but from a command line perspective, it really doesn't matter what partition it is on. All of that is handled internally by the operating system.

---

### Post by Eldera on 2009-02-26
Thank you,
Eldera

---

### Post by thomasaaron on 2009-02-26
Eldera...

Sorry, to see the files on the root partition, you don't run...

ls -a /root

...You run...

ls -a /

---

### Post by Eldera on 2009-02-26
OK Thank You

---

### Post by Shampyon on 2009-02-26
I've just put together a nice little machine. Intel Core2 Duo E8400 CPU, 2GB RAM and a 640GB HDD. I'm planning on installing Kubuntu 8-10. I was reading the Ubuntu Documentation online and saw the recommended partitioning stats:

[COLOR="Red"]/[/COLOR]______250MB
[COLOR="Red"]/user[/COLOR]______6GB
[COLOR="Red"]/var[/COLOR]______3GB
[COLOR="Red"]/tmp[/COLOR]______100MB
[COLOR="Red"]/home[/COLOR]______(if only one user account) remainder of drive
[COLOR="Red"]swap [/COLOR]______(equal to RAM)

With the size of my drive, I was thinking of using this setup:

[COLOR="Red"]/[/COLOR]______5GB
[COLOR="Red"]/user[/COLOR]______10GB
[COLOR="Red"]/var[/COLOR]______5GB
[COLOR="Red"]/tmp[/COLOR]______10GB
[COLOR="Red"]/home[/COLOR]______remainder of drive
[COLOR="Red"]swap [/COLOR]______4GB (in case I buy more RAM down the track)

I install a LOT of extra software though, and not all of it from the repos. I do a fair bit of DVD ripping/encoding, I download a lot of podcasts, and I occasionally edit video and audio (just basic stuff, nothing fancy). Does they look like adequate partition sizes?

Edit: I just realised I'm in the wrong section, Oops...

---

### Post by jdb on 2009-02-27
> **Eldera said:**
> Because I am 73, don't drive, and am isolated in a senior citizen apartment complex, most of my computer skills have been self taught from help screens,etc. This has created a problem where I have gained an understanding of some things fairly advanced and overlooked others simple and basic. 


Eldera

Eldera,

Just a little info on partitions to help you out.

Disks are divided into chunks called partitions.
On most newer computers the disks are labeled sda, sdb, sdc, etc.
USB disks & USB memory are given the same type of designation.
The partitions on a disk are labeled sda1, sda2, sda3, sdb1, sdb2, etc.

In Linux these are all known as block devices and show up in the /dev directory.

```
ls /dev
```

will show you all your devices.

```
find /dev -type b | sort
```

will show you all your block devices.

A partition must be "mounted" before you can see it's contents.
The "mount point" is just an ordinary directory.
When a partition is mounted on a directory you access the partition just by accessing the directory.
As long as the partition is mounted you can't access anything that was originally in that directory.
For that reason partitions are usually mounted on empty directories.

```
cat /etc/fstab
```

will show all the partitions that are automatically mounted on boot up.
(USB devices usually mount automatically & don't have to be in fstab.)

The command

```
mount
```

will show all your mounted partitions.

```
df -h
```

will show how big they are and how much of them is used.

To find out more about any of the above commands use man, for example

```
man sort
```


jdb

---

