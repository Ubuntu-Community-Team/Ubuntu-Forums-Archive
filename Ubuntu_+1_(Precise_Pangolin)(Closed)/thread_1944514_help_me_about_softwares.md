---
title: "help me about softwares"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tahsin rahman on 2012-03-21
i am using linux mint which is a customized version and i got many softwares such as codeblocks, monodevelop,geaney,cromium browser and so on. now i want to use ubuntu 12.04 . can i use  these softwares in ubunty by copying from linux mint ? how can i do that

---

### Post by Bucky Ball on 2012-03-21
12.04 LTS is still testing and unreleased. Unless you know what you're doing, I wouldn't advise upgrading just yet (especially if you have a functioning machine now). Expect breakages if you do. 

If the only reason for the upgrade is to have the latest I would stick to the old adage, 'If it ain't broke, don't fix it.' Unless you have time on your hands, are ready for a learning curve or want to test and help the developers by posting bug reports.

If you have a spare partition or another (non-essential) computer, install 12.04 LTS to there if you want to familiarise so you have a stable install to fall back on. ;)

---

### Post by nothingspecial on 2012-03-21
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by grahammechanical on 2012-03-21
If the same programs are available in Ubuntu then it should be possible. Whether you install 12.04 Beta 1 or Beta 2 or wait until the end of April if you can get the same programs working in 12.04 then you are off to a good start.

I can tell you this. I am using Chromium right now. So, I guess that once you install 12.04 and install Chromium you can copy the Chromium folders from Linux Mint into the Chromium folders in Ubuntu and then the Ubuntu Chromium will run as if you were using Chromium in Linux Mint.

I suggest that you dual boot into Linux Mint and Chromium.

regards.

P.S. I have just checked in the Ubuntu Software Centre and I found this:

Code::Blocks IDE version 10.05-2
MonoDevelop version 2.8.6.3+dfsg-2
geany version 0.21.dfsg-1ubuntu4

If that is any help in making your decision

---

### Post by jbicha on 2012-03-21
Trying to upgrade from Linux Mint to Ubuntu is not recommended or supported. I'd suggest a clean install. Good luck!

---

### Post by acimi66 on 2012-03-21
If you have /home on it's own partition it should not matter which OS you are running...Am I wrong about that?

---

### Post by Bucky Ball on 2012-03-21
> **acimi66 said:**
> If you have /home on it's own partition it should not matter which OS you are running...Am I wrong about that?

No, as long as in the Ubuntu family (based on Ubuntu) but that doesn't address upgrading Linux Mint to straight Ubuntu which, as mentioned, is not supported. Attempt at own risk. ;)

---

### Post by tahsin rahman on 2012-03-21
so after installing ubuntu,, downloading and installing these softwares will be the best choice ? isnt it ?

---

### Post by cryptotheslow on 2012-03-22
Yes. Preferably backup your files to an external drive - probably advisable to back up everything in your home directory (remember to grab the 'hidden' folders in there which start with a dot .) as well as any other location you know you saved things to.

Only once you are happy you have everything backed up, disconnect that external media then reboot with your Ubuntu CD or USB, take the Try Ubuntu option and use Disk Utility or GParted to remove the partitions Mint is installed in. Then use the Install Ubuntu option to install in the now empty space.

Once you have Ubuntu installed and working to your liking, install the programs you need via software centre or synaptic (install required but recommended). Then plug in that external backup and copy back over the stuff you need.

I think what I'm trying to stress is - make sure you have an external backup. It's all too easy to slip up or for something to go wrong when messing with partitions and a new OS install (no matter how smug it might make you feel to have a separate /home partition, stuff will still go wrong without a backup - murphy said so :P).

---

### Post by 3rdalbum on 2012-03-22
Linux Mint uses the Ubuntu repositories, so almost anything available on Linux Mint is also available for Ubuntu, and just as easy (and free) to install...

I wouldn't recommend trying to save packages from Linux Mint and use them on Ubuntu 12.04. Reason: The current Linux Mint is based on Ubuntu 11.10, and there are probably changes in 12.04 which may cause problems for running the older software. Besides, you want newer versions of your programs, right?

---

