---
title: "Host Vista, and VM Ubuntu can not mount NTFS"
date: 2009-05-16
forum: Virtualisation
---

### Post by sunseeker888 on 2009-05-16
Hi Guys


would really appreciate some help please. 

Here's my problem


I have vista 64 bits on the PC.

3 partition are NTFS, anc C: is the OS


Anyway,

I have a drobo and droboshare. My problem droboshare does recognise XFS extension unlike LInux.


I have install Virtualbox on Vista, and Yellow Jackalope. I have managed to get drobo to be loaded on the VM Ubuntu.



All, that I need now is to get the VM Ubuntu to see the 2 NTFS and mount then, which are /dev/sb1 and dev/sda2  



The problem, as it's a VM using fdisk -l, It does not see the other partitions.


How can I make the VirtualM ubuntu mount the partition on the host? Is that possible. I really need to get those data to upload them to my Drobo.


I have the following below, it's obvious it would not work as it's VW on vista, and the partition are different.






++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

# Install gparted (System &#8594; Administration &#8594; Synaptics Package Manager &#8594; search for gparted, mark it for installation and, when it installs, run it from System &#8594; Partition Editor). Look for an NTFS partition &#8211; it is likely to be the one windows is on.
# Having located the partition, write down the name &#8211; it will look something like /dev/hda2. Do this carefully &#8211; this is no time for dyslexia. Now check to see if this is the partition by manually mounting it and looking at the files.
# Open a terminal (Application &#8594; Accessories &#8594; Terminal) and make yourself root by typing sudo -s and pressing enter. You will be prompted for the root password and will then become root. Being root assumes that you know what you are doing &#8211; you could easily cause disaster if you make a mistake, so concentrate. Carefully type this line at the prompt and press enter
# mkdir /mnt/windows
# You may replace /mnt/windows with /mnt/windrv or any other name you prefer. Now, having created the directory that is going to hold your windows files, type the following command carefully at the prompt and press enter
# mount -t ntfs /dev/sda2  /mnt/windows -o "umask=022"

---

