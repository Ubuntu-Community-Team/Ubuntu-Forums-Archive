---
title: "How to install 64-bit along side 32-bit without reformatting (GUIDE)"
date: 2008-03-04
forum: System76 Support
---

### Post by gaussian on 2008-03-04
I think that I am not alone among System 76 laptop customers wishing to:

a) keep their original 32-bit installation
b) install 64-bit alongside
c) not reinstall the 32-bit system or copy the whole 32-bit installation to outside disk, copy it back and then debug the original installation to make it work (/etc/fstab, grub-reinstallation etc)
d) turn the original LVM partition into a positive thing

<SHOUTING>
EVERYTHING THAT FOLLOWS BELOW IS SOMETHING YOU DO AT YOUR OWN RISK. THIS IS INHERENTLY RISKY (LIKE ANY REINSTALL/PLAYING WITH PARTITIONS)! THIS IS ALSO NOT OFFICIAL SYSTEM 76 ADVICE (AND CERTAINLY NOT ENDORSED BY SYSTEM 76), I AM JUST A (HAPPY) SYSTEM 76 CUSTOMER SHARING WHAT SEEMS TO WORK FOR ME.
</SHOUTING>

Do not follow this advice if you are not semi-competent working with partitions, grub installation etc.

I personally did not backup before doing this, but that is just because all the data (as opposed to settings/programs) on my laptop is backed up at two different physical locations. 


Tools needed:
-GUTSY (32 or 64-bit) desktop install CD
-GUTSY 64-alternative install CD
-Recommended: Read up on LVM2, parted and partitions in general

Note that I have not yet completed all the steps, the most trivial steps (splitting the boot and 64-bit reinstall) have not been completed yet. I will probably complete that later this week and report back. If this does not work, you should be able to easily undo steps 8-12 to restore your system to original state.

My computer:
DARU2, 160G hard drive formatted as:
-220M /dev/sda1 as boot partition
-148G /dev/sda5 as LVM, containing two logical partitions: root (144G) and swap (4G)

Steps:
1. Boot on GUTSY Desktop CD
2. Activate your network
3. Using GUI (Administration - Software Sources): Activate Universe
As root/sudo:
4. apt-get update (if step 3 did not do this already)
5. apt-get install lvm2 ext2resize
6. modprobe dm-mod
7. vgchange -ay

Now you should have your logical volumes active. In my case this meant that I have /dev/ubuntu/root and /dev/ubuntu/swap as available drives.

IN THE NEXT STEPS(ACCORDING TO MY READING) IT IS CRUCIAL THAT THE FILESYSTEM IS SHRUNK FIRST MORE THAN THE LOGICAL VOLUME. IF YOU DON'T FOLLOW THIS ADVICE YOUR ORIGINAL INSTALLATION WILL GET MESSED UP.

8. chkfs.ext3 -f /dev/ubuntu/root
9. ext2resize /dev/ubuntu/root 70G (This step took about 90 minutes on my computer, and obviously you might need to adjust the 70G number)
10. lvresize -L 72G /dev/ubuntu/root
11. ext2resize /dev/ubuntu/root

Now you have empty space on your LVM. At this stage I would reboot and check that you still have a working computer. Remember, it is not my fault if you don't.

Note: You might be tempted (I tried this) to shrunk the size of the physical LVM partition on the disk now. I tried with pvresize, but that only resizes the LVM filesystem. You would also need to resize (probably delete and recreate) the actual partition with some low-level tool (fdisk?). This I decided is way too risky/hardcore  for me.

Steps to be completed (I don't expect any problems here). THIS IS AS FAR AS I HAVE COMPLETED THE STEPS.

Optional step: create a separate logical DATA partition that will be shared between 32 and 64-bit installation. Move your data there. I would not share the actual home directory between two installations, this might cause problems.


12. Boot back to GUTSY Desktop CD, use parted to reduce the size of your /boot (/dev/sda1) (split it 50-50, the space on the two boot partitions is the scarce thing here). Create an empty (ext3) partition to the space you created.

13. Boot using GUTSY Alternate Install CD. Install GUTSY to a new logical volume inside the LVM. This is step I have not completed, I hope this works. You might or might not have to create this logical volume before starting the Alternate Install. Use the newly created partition as your /boot in the 64-bit installation. Install GRUB on that new partition (so you have separate GRUBs for 64-bit and 32-bit). /boot cannot be installed to an LVM.

14. Boot to your original 32-bit install and edit your /boot/grub/menu.lst to have an option to chainload to the GRUB in the new partition.

I will report back if this is a success, but this is the roadmap I am following at the moment (currently completed step 11).

---

### Post by gaussian on 2008-03-06
I am happy to report that everything (*almost*) went smoothly. I now have a 32-bit/64-bit dual boot DARU2.

*almost part*: After step 12) in my original post my system became unbootable. This was easily cured by using Live-CD to reinstall GRUB. Not a biggie.

---

### Post by steveneddy on 2008-03-08
I just backed up my /home folder and totally reinstalled.

30 minuted later I was done and no need for dual booting.

Who wants the same OS on each partition?

---

### Post by gaussian on 2008-03-08
> **steveneddy said:**
> I just backed up my /home folder and totally reinstalled.

30 minuted later I was done and no need for dual booting.

Who wants the same OS on each partition?

Actually there can be plenty of reasons:
1) I have some commercial (statistical) software that is installed on the 32-bit side that is a pain to reinstall
2) Rebuilding all the old settings is easier when you have a working model (the old 32-bit) on the same computer.
3) I have plenty of data on this computer that would pain to recopy here (I backup my office computer on my laptop with rsync over internet)
4) I was not sure (and did not want to test extensively with the livecd) that everything works perfectly in the 64-bit (multimedia, flash etc). It turns out that even with nswrapper flash does not work as well in the 64-bit environment as in 32-bit (some Webkinz games don't work). It turns out they work well in the chrooted 32-bit environment.
5) Without having tried 64-bit extensively I did not know how easy it is actually to use 32-bit programs with chroot in the 64-bit environment
6) By having saved your 32-bit environment you have already functioning 32-bit side that can be used to chroot to run programs like Skype beta, flash, Opera etc... that can be pain (but not necessary impossible) to use in 64-bit. And yes, I am aware that there is a 64-bit Opera beta.
7) It gives the easy option to revert back to the old installation if you decide that 64-bit was not your thing. And it gives you "all is working" installation that you can use while you tweak your 64-bit.

But in principle you are right, I was not trying to advocate that people do this, I was just providing the information for people who for these or other reasons did not want to make the complete jump and wanted more gradual approach.

---

