---
title: "Unallocated Space Recovery"
date: 2017-06-17
forum: Windows
---

### Post by sidhelps on 2017-06-17
So I had Ubuntu running in Dual Boot with Windows 10 and recently removed ubuntu.
The unallocated space i have left cannot be used for a new drive or as free space so that i can expand an already existing drive.
Please Help.[IMG]https://s4.postimg.org/auebozlrx/Untitled.png[/IMG]

---

### Post by yancek on 2017-06-17
What have you tried and what happened?  You should be able to use windows Disk Management to do that.

---

### Post by sidhelps on 2017-06-17
When I try doing anything with windows Disk Management I get a message saying there is not enough space.
I also tried using easus disk management but it does not show any options for the unallocated space.
I have tried expanding E drive in bothsoft ware but again there is a no space error in Windows Disk Management and EASUS does not show the unallocated space as free space.
Is there any way to format the unallocated area?

---

### Post by coffeecat on 2017-06-17
*Thread moved to **Windows**.*

---

### Post by yancek on 2017-06-17
Generally,  when you want to expand a partition you need to use unallocated space which is 'contiguous' to the other partition.  You can't expand E because that is not the case.  You have the "D" partition immediately before it and a 512MB EFI partition immediately after it.  You have your system with the C:\ partition on the smaller drive with an EFI partition but also an EFI partition on the larger drive.  Was that for UBuntu?  You should be able to simply create another partition out of the unallocated space to use for data on windows.

---

### Post by sidhelps on 2017-06-18
Yes, the 512 mb efi partition was for ubuntu, I tried to delete it with windows Disk Management but there is no option.
Is there a way through command prompt to do this?

---

### Post by yancek on 2017-06-18
Are you able to boot windows from the windows bootloader?  Generally, if you had Ubuntu and booted from it's Grub EFI file you would see the purple Ubuntu screen.  Verify that you are booting directly from from windows without needing the Ubuntu Grub before you make any changes to that second EFI partition.  You might copy the second EFI partition for Ubuntu to another partition as a safety precaution.  Not sure if you can do that in windows so you might need the Ubuntu install media.

When you boot windows and go to the Menu, Administrative Tools, you need to right click on Computer Management and select the option to run as administrator then go to Disk Management and click on the partition you want to remove to highlight it and right click, that should show you a Delete option.

---

### Post by sidhelps on 2017-06-18
I have changed the boot priority to favour windows boot loader. So booting to windows is not a problem.
When i boot via the ubuntu bootloader i see a black screen with a command prompt like interface which is centre justified.
I have tried using disk management as administrator but there is still no option to delete the efi partition, the results were the same when i tried to expand E drive and make a new drive.

---

### Post by yancek on 2017-06-18
You can't expand the E drive to include the unallocated space because you have your 512MB efi partition between them.  Opening Disk Management with run as administrator should give you the delete option.  I see that option on different partitions but obviously not on the system or EFI partition in use.  I expect you would be able to do this with a Linux Live system but you won't be able to do it from the system you had installed as you deleted the partition with system files and the prompt you see is just for Grub bootloader and that won't work.  I don't know why you don't have the option to delete it in windows if it only had Ubuntu files on it and you do have another EFI partition on your windows drive.  You might try posting at a windows forum.

---

### Post by sidhelps on 2017-06-19
Thanks for the help! I shall try my luck at a windows forum. 
Can you advise me on which forum would be best?

---

