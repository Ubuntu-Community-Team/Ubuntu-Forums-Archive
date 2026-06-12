---
title: "A fluke? Home data (not a separate partition) preserved after clean reinstall"
date: 2009-06-08
forum: Testimonials &amp; Experiences
---

### Post by aysiu on 2009-06-08
Is this some kind of weird Ext4 thing?

Recently I did a reinstall of Ubuntu.

I had an i386 kernel with Ext4 filesystem.

Then I installed Ubuntu again with an lpia kernel and the Ext4 filesystem.

This was a total clean reinstall with deleting the one big partition and creating a new one big partition. I do not have a separate /home partition.

After the reinstall, all of my /home/username data (settings and files) were preserved. I was all set to copy my backup files back to the computer, but they were already there. Has anyone ever heard of this happening? Any explanations?

---

### Post by ajackson on 2009-06-08
> **aysiu said:**
> This was a total clean reinstall with deleting the one big partition and creating a new one big partition. I do not have a separate /home partition.

After the reinstall, all of my /home/username data (settings and files) were preserved. I was all set to copy my backup files back to the computer, but they were already there. Has anyone ever heard of this happening? Any explanations?
The only thing I can think of is that the whole partitioning bit (ie delete, create, format) failed but you weren't told about it.

---

### Post by aysiu on 2009-06-08
> **ajackson said:**
> The only thing I can think of is that the whole partitioning bit (ie delete, create, format) failed but you weren't told about it.
But somehow the reinstall worked, though. It was a fresh install (none of my old programs were in there) and had the right kernel. All the system settings were from the reinstall.

---

### Post by estyles on 2009-06-08
Doesn't a reinstall specifically overwrite all system directories?  But maybe it would leave /home alone and not overwrite it, if the other poster was right and the delete/repartitioning failed?

---

### Post by aysiu on 2009-06-08
No, if you reinstall and delete a partition and create a new one and install Ubuntu to that new partition, all directories should be gone, not just the system ones.

---

### Post by juancarlospaco on 2009-06-08
Its an Ubuntu feature, you can preserve your /HOME on fresh installs, separated /HOME is not more needed.

I have been done a lot of fresh installs preserving the /home.

---

### Post by aysiu on 2009-06-08
> **juancarlospaco said:**
> Its an Ubuntu feature, you can preserve your /HOME on fresh installs, separated /HOME is not more needed.

I have been done a lot of fresh installs preserving the /home.
Wait... so you're telling me even if I don't have a separate /home partition, somehow the files and settings in my home directory will be preserved?

Um, two responses I have to this are:

1. How is that technically possible?

2. I didn't ask for my settings and files to be preserved. In this case, it worked out nicely, because I did want them preserved, but what if I wanted a clean install? I didn't see an option in Ubiquity for that.

---

### Post by juancarlospaco on 2009-06-08
> **aysiu said:**
> Wait... so you're telling me even if I don't have a separate /home partition, somehow the files and settings in my home directory will be preserved?

Um, two responses I have to this are:

1. How is that technically possible?

2. I didn't ask for my settings and files to be preserved. In this case, it worked out nicely, because I did want them preserved, but what if I wanted a clean install? I didn't see an option in Ubiquity for that.

If you don't have a separate /home partition, the files and settings in your home directory will be preserved.

1)Simply it Delete all folders, but dont touch the /home folder tree.

2)Ubiquity has Command Line options, it can be Unattended too, just like Pirated Windows.
*Newbies may agree this feature, you are an expert, you dont need it but you know what to do.*

Just like computer janitor, newbies like it, experts uninstall it :D

---

### Post by aysiu on 2009-06-08
> **juancarlospaco said:**
> If you don't have a separate /home partition, the files and settings in your home directory will be preserved.

1)Simply it Delete all folders, but dont touch the /home folder tree.

2)Ubiquity has Command Line options, it can be Unattended too, just like Pirated Windows.
*Newbies may agree this feature, you are an expert, you dont need it but you know what to do.*

Just like computer janitor, newbies like it, experts uninstall it :D
But I deleted the partition entirely...

I guess when I created a new partition, the Ubiquity installer then scanned for where the /home directory used to be and then built around that?

If this is the case, I like that feature. Still, there should be an easy way to disable that in case you really want a clean, clean install. A simple checkbox or Advanced setting (along with the Grub location and popularity contest participation).

---

### Post by betrunkenaffe on 2009-06-09
Only way I can possibly see that working is it somehow backing up your entire /home to memory, rebuilding the ext4, installing the new os and then re-writing the /home in... Doesn't sound too plausible to me, unless you have baby /home and large RAM.

Even +swap file wouldn't hold my /home.

Does it show as ext4 or ext3 when you fdisk -l?

I can see a /home preserve happening when you are reinstalling assuming no repartitioning or reformatting. That's simply the installer opting to not overwrite existing /home.

Do you have tech document on how this preserve works?

---

### Post by aysiu on 2009-06-09
Well, *fdisk -l* just says *Linux*, but it's definitely Ext4 in /etc/fstab, and I chose Ext4 during the installation.

I agree with you--this makes no sense. My data and settings make up almost 8 GB, and I have only 2 GB of RAM and no swap partition.

---

### Post by lisati on 2009-06-09
It almost sounds like something for Ripley's "Believe it or not"!

---

### Post by aysiu on 2009-06-09
Believe me, I've done many a clean Ubuntu reinstall (for real and in VirtualBox), and I've never seen anything like this, at least not without a /home partition.

---

### Post by 3rdalbum on 2009-06-09
The only thing I can think of is that Gparted didn't actually delete the partition, it just converted it to Ext4.

---

### Post by aysiu on 2009-06-09
> **3rdalbum said:**
> The only thing I can think of is that Gparted didn't actually delete the partition, it just converted it to Ext4. But the installer still installed a fresh Ubuntu. Plus, my drive had already been Ext4 before.

All my system files had been replaced. None of my additional programs were installed. All the default Ubuntu programs were installed. My kernel was changed. Everything had changed... except my home directory.

---

### Post by ukripper on 2009-06-09
> **aysiu said:**
> 
I guess when I created a new partition, the Ubiquity installer then scanned for where the /home directory used to be and then built around that?



That looks the most probable answer to your own question.

i am sure it has nothing to do with EXT4

---

### Post by aysiu on 2009-06-09
> **ukripper said:**
> That looks the most probable answer to your own question.

i am sure it has nothing to do with EXT4
Has anyone else experienced this, though? Is this, in fact, a new feature in 9.04, as someone else suggested? Or was it some kind of freaky glitch?

---

### Post by Bios Element on 2009-06-09
If it was anyone else I'd think you were nuts. >.> It would be nice to have as a feature though. I know vista backed up the entire previous install in a windowsOLD directory after a re-install.

---

### Post by aysiu on 2009-06-09
I'm not really in the mood to try to repeat the experiment. I would be curious to see if anyone else has experienced this. If not, I'll just write it off as some kind of anomaly.

---

### Post by ninja_numbnuts on 2009-06-09
> **aysiu said:**
> I'm not really in the mood to try to repeat the experiment. I would be curious to see if anyone else has experienced this. If not, I'll just write it off as some kind of anomaly.

I think this happened to me when I reinstalled Hardy after trying to manually install a nVidia driver, but I can't really remember!

---

### Post by 3rdalbum on 2009-06-10
I do remember hearing that one of the features slated for a previous release was to save the home directories even if they are not on a seperate partition. I don't believe they actually announced it in the release notes for that version, but I definitely remember hearing that it was going to be in an Ubuntu release.

---

### Post by tea for one on 2009-06-11
> **aysiu said:**
> I'm not really in the mood to try to repeat the experiment. I would be curious to see if anyone else has experienced this. If not, I'll just write it off as some kind of anomaly.

Good evening

I was very curious and perplexed about your recent installation and re-installation of 9.04 using ext 4 file system so I thought that I would see if I could reproduce the preservation of the home directory.

I used a 9.04 Ubuntu ISO obtained at the end of April.
I created a fresh installation on a spare drive with ext 4.
I created some new documents and copied some mp3s into the home directory and added some bookmarks to Firefox. 
All files/folders were saved (without a separate /home). 
I rebooted and everything was intact as expected.
Next, I reinstalled Ubuntu using the same CD using the same partition.
I selected ext 4 as the file system and only specified one (root ) partition.
My home directory had been overwritten and no longer existed.

Caveat: I did not change the kernel as your first post because that is beyond my level of ability ("Then I installed Ubuntu again with an lpia kernel and the Ext4 filesystem.")

I carefully watched the installation process and read all the dialogue boxes and there were no unusual warnings to preserve or ovewrite existing data.

Therefore, I was unable to reproduce your experience and I would be interested to read about other attempts to preserve the /home directory without using a separate /home partition.

I wish that I had been able to verify your experience but, regrettably, I could not.

---

