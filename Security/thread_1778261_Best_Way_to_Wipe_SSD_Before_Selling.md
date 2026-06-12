---
title: "Best Way to Wipe SSD Before Selling"
date: 2011-06-08
forum: Security
---

### Post by phpdev on 2011-06-08
I'm selling my Dell Mini 10 that came with Ubuntu on it. I never really used it much, and the only sensitive things on it were some PHP files with MySQL passwords that I can change on the server if need be. I'm not familiar with command line at all, so I'm having trouble figuring out the best way to wipe the SSD. I already reinstalled the OS using the recovery disk from Dell which said it would 'delete' the contents of my hard drive. I'm not sure if the job it did is suitable. What's the best way for me to make sure my data can't be recovered? Is there anything with a GUI I can download to help with this? Thanks in advance.

---

### Post by uRock on 2011-06-08
Moved to Security Discussions.

---

### Post by BrandonC19 on 2011-06-08
> **phpdev said:**
> I'm selling my Dell Mini 10 that came with Ubuntu on it. I never really used it much, and the only sensitive things on it were some PHP files with MySQL passwords that I can change on the server if need be. I'm not familiar with command line at all, so I'm having trouble figuring out the best way to wipe the SSD. I already reinstalled the OS using the recovery disk from Dell which said it would 'delete' the contents of my hard drive. I'm not sure if the job it did is suitable. What's the best way for me to make sure my data can't be recovered? Is there anything with a GUI I can download to help with this? Thanks in advance.

Simply deleting files wont be enough, the drive needs to be what many refer to as "killed" which is have  a series of 0's written to the drive.

The code for this would be:
```
dd if=/dev/zero of=/dev/hda
```
making sure to replace hda with your drive

---

### Post by phpdev on 2011-06-08
Thank you for your help. How do I know what to replace hda with? Is there a way to list the drives to figure out the name?

---

### Post by BrandonC19 on 2011-06-08
You're welcome :)
And yes actually. There are three ways. 
The code ```
fdisk -l
```
System > Administration > Disk utility
System > Administration > System Monitor and select the "File System" tab.

---

### Post by sidzen on 2011-06-08
> **BrandonC19 said:**
> Simply deleting files wont be enough, the drive needs to be what many refer to as "killed" which is have  a series of 0's written to the drive.

The code for this would be:
```
dd if=/dev/zero of=/dev/hda
```making sure to replace hda with your drive

Adding to the above[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP] where /dev/sda is your hdd.

Or use SystemRescueCD and its[ *dban* ]("http://blogostuff.blogspot.com/2005/02/system-rescue-cd.html")utility to do the same
 
Best wishes!

---

### Post by BrandonC19 on 2011-06-08
> **sidzen said:**
> Adding to the above[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP] where /dev/sda is your hdd.

Or use SystemRescueCD and its[ *dban* ]("http://blogostuff.blogspot.com/2005/02/system-rescue-cd.html")utility to do the same
 
Best wishes!
Thanks Sidzen. What do the [PHP]bs=4096 conv=notrunc,syn[/PHP] suffix's do?

---

### Post by phpdev on 2011-06-08
One more question, just to clarify haha ^_^

So my plan is to boot from a Live CD and run that command from the command line, then reinstall the OS from the dell/ubuntu recovery disk it came with. Will wiping the SSD completely prevent me from reinstalling from the recovery disk at all?

Sorry for so many questions!!!!! :p

---

### Post by sidzen on 2011-06-08
block size = 4MB, do not truncate, synchronize

Suggest just give it to him as-is (wiped with zeros), 
unless you desire to practice manual partitioning

---

### Post by BrandonC19 on 2011-06-08
> **phpdev said:**
> One more question, just to clarify haha ^_^

So my plan is to boot from a Live CD and run that command from the command line, then reinstall the OS from the dell/ubuntu recovery disk it came with. Will wiping the SSD completely prevent me from reinstalling from the recovery disk at all?

Sorry for so many questions!!!!! :p
No you will be able to reinstall, all the command does is write 0's all over the disk, ensuring with 99.9% accuracy that the data cannot be recovered.

---

### Post by BrandonC19 on 2011-06-08
> **sidzen said:**
> block size = 4MB, do not truncate, synchronize

Suggest just give it to him as-is (wiped with zeros), 
unless you desire to practice manual partitioning
Thanks again. Saved me from having to crack open a man page.

---

### Post by sidzen on 2011-06-08
@[BrandonC19]("http://ubuntuforums.org/member.php?u=1125533") -- You're welcome!

@OP -- please mark SOLVED when satisfied with the answers posted

---

