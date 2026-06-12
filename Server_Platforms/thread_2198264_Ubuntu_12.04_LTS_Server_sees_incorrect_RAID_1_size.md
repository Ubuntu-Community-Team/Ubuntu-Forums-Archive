---
title: "Ubuntu 12.04 LTS Server sees incorrect RAID 1 size"
date: 2014-01-07
forum: Server Platforms
---

### Post by Almeister9 on 2014-01-07
I have installed 2 x 3TB HDDs into a Gigabyte Z87M-D3HP Motherboard and using the Intel RAID configuration Utility, have set them to RAID 1 (size 3TB)
These are the only two hard drives in the machine.

I then began installing Ubuntu 12.04 LTS Server 64-bit and it noticed that I had a RAID array and asked if I wanted to activate it. I said yes.

When it came to partitioning time, I chose "Use entire disk and set up LVM". As I continued, it gave me a maximum size choice of 801.1GB

Is anyone able to tell me what I did wrong?
Do I need to leave the HDDs as normal in BIOS and setup the RAID 1 array in software in Ubuntu?

Any help here would be greatly appreciated.
Cheers, Al.

*******************
I am editing this original post in this thread so that if anyone else reads it they can find the solution right at the start.

The problem is actually caused by the HDDs being 3TB.

Anything larger than 2TB and the Partition table HAS to be GPT.

The Installer is not able to deal with HDDs larger than 2TB.

You need to set the Partitions up first in a third party application like GParted.
There is a "GParted Live" bootable CD that you can get, or if you use the Desktop Install DVD and boot for it Live, you can use it's version of GParted.

The important thing is on each drive,

1. create a small Partition that has no file system on it, of size at least 1.0MB and set the flag to "biosgrub"
2. Then create your swap Partition and set the flag to 'Raid'
3. Then create your main Partition and set the flag to 'Raid'

Make sure you do this for both HDDs and the Partition sizes are the same on each, then close GParted and re-boot with the 12.04.3 Server Install disk in.

When it gets to the Partitioner, choose 'Manual', and just go straight to the "Configure RAID" option.
Create MD and choose the two partitions for the swap 
Create MD and chose the two partitions for the main one.
click finish and write to disk.

Then within the RAID array, choose the Swap and hit return "Use As" - swap area. finish
Choose the Main Partition and hit return "Use As" - ext4. mount - / (root). finish.

no need to worry about setting bootable flag.

in the Partitioner, go to "Finish and write to disk,

And Job Done. The Installer will continue on its merry way and grub will be installed fine.

This solution was found here:
[http://ubuntuforums.org/showthread.php?t=2109438](http://ubuntuforums.org/showthread.php?t=2109438)
(first reply down)

Thanks to all who tried to help.
Cheers, Al.

---

### Post by Bucky Ball on 2014-01-08
*Thread moved to **Server Platforms**.*

You might have more luck here.

---

### Post by nerdtron on 2014-01-08
> I then began installing Ubuntu 12.04 LTS Server 64-bit and it noticed  that I had a RAID array and asked if I wanted to activate it. I said  yes.

I'm not familiar with intel raid utility but I guess it would be the same as our LSI raid cards.
If you already configured "hardware" raid, meaning the BIOS takes care or the raid, you should not activate RAID in ubuntu. Say your BIOS already handled RAID1 for you, your OS should only see a single hard drive with a capacity of a little less than 3TB.

---

### Post by CharlesA on 2014-01-08
> **nerdtron said:**
> I'm not familiar with intel raid utility but I guess it would be the same as our LSI raid cards.
If you already configured "hardware" raid, meaning the BIOS takes care or the raid, you should not activate RAID in ubuntu. Say your BIOS already handled RAID1 for you, your OS should only see a single hard drive with a capacity of a little less than 3TB.

+1.

It seems odd the installer would create a RAID volume that is 1/3 of the size of the array, assuming you set up RAID1 in the Intel software.

Did you configure the RAID in the BIOS or in another utility?

---

### Post by Almeister9 on 2014-01-08
Hi CharlesA,

The Intel RAID Utility is separate from BIOS but you need to boot into it from post. I have set the SATA setting to RAID in the BIOS and then did the setup as per Motherboard Manual instruction (in Intel RAID Utility)

I will try re-installing Ubuntu Server and saying "no" to activating RAID when Ubuntu Installer asks me. As Nerdtron suggested. I'll see if that works.

Thanks.

---

### Post by Almeister9 on 2014-01-08
Hi Nerdtron,

I have just attempted to install again, twice.

Each time, after setting up the local time, and confirming my location, It tells me that it has detected a RAID array, and would I like to activate it.
Both time I said no, instead of yes, and both times I get a screen that says "Setting up the partitioner" with a progress bar that runs across the screen and once it gets to 100% I then get a blank purple screen with a blank white strip running across the bottom.

hitting space, tab, return, escape, all do nothing except move the cursor around in the white strip at the bottom.

I'm sure I must be doing something wrong, but surely I am not the first person to try to instal Ubuntu Server 12.04 LTS onto a RAID 1 array?

Any further help would be greatly appreciated, because this has me stumped. I have done this before on another system with Ubuntu Server 8.04 LTS with the RAID setup in BIOS and there was no hickups whatsoever, The 8.04 LTS install didn't ask me to activate the RAID array (from memory).

Thanks again for your help.

---

### Post by Almeister9 on 2014-01-08
I Have just run a check on the install disk and it passed.

I am now trying to do a fresh install this time saying "yes" to activating the RAID array, and this time the partioner started, but will not give me the normal install options.
Instead it detects and displays the current partitioning, and if I want to make any changes I have to do them manually, which I am having a very hard time working out how to do.

It is showing the K lvm as 801.1GB and after that shows FREE SPACE of 2.2TB

I am starting to dislike this 12.04 LTS Server. I have never had these problems on older versions, and with older versions, if I do a fresh install, it always gives me the normal options of 
'Use entire disk,
Use entire disk with LVM,
Manually etc.

now I can't even follow the normal tutorials for doing it manually because it is not giving me the normal options.

If anyone can see what is going on here,
your help would be very much appreciated.

Cheers, Al.

---

### Post by Almeister9 on 2014-01-08
I was able to manually wipe the 801.1GB partition and then make a 3TB one but at the very end of the operation at the very last stage when everything is to be written to the disks, it came up with an error saying unable to write to disk during raid 126 or something.

---

### Post by Almeister9 on 2014-01-08
operation not permitted during write on /dev/md126

So I can't make any changes anyway, and can't do a fresh install as that option is no longer available.

"The partition tables of the following devices are changed:
RAIDmd126 device #:RAIDactive device #(read only)RAIDraid1 device #sda[0]RAID126
device #

Write the changes to disks and configure LVM?
Yes.

Operation not permitted during write on /dev/md126

ERROR!!!"

I am going to go back into the Intel RAID Utility and see if I can wipe them from there to get a fresh go at it.

I don't think I should have to resort to GParted, I am just asking to do a fresh install but it seems that option is not offered anymore if you have already tried once or if there is a current Ubuntu OS on the system.

I don't see why it was changed to be like this, it used to just work.

---

### Post by Almeister9 on 2014-01-08
OK, I went back to the Intel RAID Utility and deleted the RAID Array, and re-created it. Healthy RAID 1 array.

This time when I did the instal I said "No" to activating the RAID Array and the partitioner did start, and it gave me the normal, usual partitioning options
entire disk (guided)
entire disk and lvm (guided) etc

so I chose Guided - use entire disk and setup LVM, 

I then takes me to a screen for me to choose which of the two hard drives I want to use.
It is not seeing the drives as a RAID array,

And I am losing hope.

---

### Post by nerdtron on 2014-01-08
Please don't lose hope. I don't think you will successfully configure this Intel RAID. In that case, why don't you skip the Intel RAID utility altogether.
Just make them two separate normal hard drives, then on the Ubuntu installer you configure software raid.
A good video on setting up raid on Ubuntu [http://www.youtube.com/watch?v=z84oBqOxsD0](http://www.youtube.com/watch?v=z84oBqOxsD0)

---

### Post by Almeister9 on 2014-01-08
I am now trying to create a software RAID 1 array, as I have given up on the hardware array.
It just doesn't seem possible on this hardware using 12.04 LTS.

I am using this tutorial
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)
which doesn't work and has incorrect information and also missing steps in it, but fortunately, someone else has discovered the errors in the documentation (and bugs in the system) in this thread:
[http://askubuntu.com/questions/215703/installing-12-04-server-as-a-software-raid-1-mirror-fails-to-boot](http://askubuntu.com/questions/215703/installing-12-04-server-as-a-software-raid-1-mirror-fails-to-boot)
and suggested a work around.
I hope it works, but the first time I have tried I was told by the system that it detected a GPT information but couldn't see a GPT table or something.
I'm trying again now.

Ubuntu Server 12.04.03 LTS 64-bit has been around for quite some time now.

Does nobody use RAID anymore?

---

### Post by Almeister9 on 2014-01-08
Hi Nerdtron,

> Please don't lose hope. I don't think you will successfully configure this Intel RAID. In that case, why don't you skip the Intel RAID utility altogether.
Just make them two separate normal hard drives, then on the Ubuntu installer you configure software raid.
A good video on setting up raid on Ubuntu [http://www.youtube.com/watch?v=z84oBqOxsD0](http://www.youtube.com/watch?v=z84oBqOxsD0)

I am trying your youtube video tutorial, but already , there are differences between the video and my install.

After choosing the FREE SPACE of the first hard drive and creating a Partition, I give it a size of 16GB and teh very next step in the video is a choice to set it as Primary or Logical
My Instal skips this step and goes straight to where do you want it, Beginning or End.

Why the difference?

Also after I choose Beginning, the next screen on your video has the top line as "Use As" but my top line asks for a Name, then is the "Use As".

At this point I am not confident.

---

### Post by nerdtron on 2014-01-08
I just setup a software RAID 10 on our server last year with Ubuntu 12.04.3 LTS. I didn't use LVM along with RAID. So far no problems.

---

### Post by nerdtron on 2014-01-08
Here's my reference when installing software raid.

---

### Post by Almeister9 on 2014-01-08
> A good video on setting up raid on Ubuntu [http://www.youtube.com/watch?v=z84oBqOxsD0](http://www.youtube.com/watch?v=z84oBqOxsD0)

And there we have it.

Set the large Partition to Bootable, by moving the highlight down to "Bootable flag: off" and hitting enter.
And it stays at "off"
hitting enter you can quickly see "computing the state of the new patition table" and a progress bar,

but it stays at "off"

The video has all these comments of people saying "YAY, worked thanks".
That must have been before they changed the install program.

SO another failure.

---

### Post by Almeister9 on 2014-01-08
> Here's my reference when installing software raid. 

I appreciate your help,

but again, your step 27 differs from my install (I get no option for Primary or Logical) and differs from the youtube video you sent me to in that you say to use different file system options than the video

> In Use As, select appropriate file system (ext2 for boot, ext2 for root, swap area for swap)
   NOTE: For /boot, turn ON bootflag option

The video says to use "Physical Volume for RAID" for both the swap and the other.

---

### Post by Almeister9 on 2014-01-08
I can't see how this is going to work If I cant make the partition bootable.

---

### Post by Almeister9 on 2014-01-08
I have now tried all of the different methods, in all of the different ways, and ALL of them fail with error messages before the instal can finish.

Why did they change the instal program?

Is there anyway that I can get the old instal program that all the tutorials use?

---

### Post by Almeister9 on 2014-01-08
Does this mean that I have discovered a bug?

Should I report this bug to someone?

---

