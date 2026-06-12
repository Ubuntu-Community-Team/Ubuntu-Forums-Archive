---
title: "KVM machine disk crash."
date: 2011-01-05
forum: Server Platforms
---

### Post by zbenta on 2011-01-05
I you guys,

I have a KVM virtual machine that has crashed yesterday, when I rebooted it it stated that it had some error in it's harddrive and it was going to recover them. I allowed the procedure to finish and when I accessed the drive some of the data that I had there was gone.
We've installed some ticket software and if we don't recover this data we will loos weeks of work.
Can anyone give me a hand on how to recover the data (if possible)?

Update:

I've searched the logs and I can only see data from 06/12/2010 and from 04/01/2011.
It seams like the virtual disk has reverted to the state it was on the 06/12/2010.
I've searched the /lost+found dir and have no data there.
The virtual machine had already been restarted previously and no data was lost.
I just had problems with it after this crash.

---

### Post by zbenta on 2011-01-07
I've rebooted the virtual machine and once again had the same message stating that i had errors and that the filesystem was going to be checked. I canceled the filesystem check and then the machine started up but still I had not recovered any data.
It seems very strange to me that ubuntu destroy's data when making a filesystem chek.
The format of the virtual disks that I am using is qcow2. Does anyone know if kvm stores any logs of what happens with it's virtual machines?
Has anyone ever seen anything like this?

---

### Post by frostschutz on 2011-01-07
The problem is the unreliable disk / kvm setup, which resulted in the filesystem check in the first place, not the filesystem check itself. 

It's really hard to judge problems like these from the outside. You should make a read only copy of the disks raw data, then another copy of that and run your data rescue experiments on that.

Also if the data is important, regardless whether it's a virtual machine or not, with or without RAID, what you need is BACKUPS!!! Any piece of hardware can fail at any time, and the more complex your software setup is (virtualization) the higher the risk of failure there too. If you don't have backups, the data was not important.

> The format of the virtual disks that I am using is qcow2.You should be able to get at the raw data of these on the host using kvm-nbd, I think.

I dislike image file formats like these, especially the dynamic growing type. What happens if the filesystem on the host runs out of free space? The qcow2 image can not grow and the VM will die with HDD errors.

It's better to give the VMs a real block device (for example LVM partition on the host). This also improves performance a lot (qcow2 management is expensive). The only thing it does not save you is storage space but storage space is cheap so yeah.

Best of luck...

EDIT:
If ticket software means unencrypted/uncompressed plain text messages and plain text attachments, if all else fails, use 'strings' on the raw image. It will give you all plain text that is in there. It won't be particularly useful, but if it was important plain text, such as bug reports and descriptions of problems - as a last resort, that may be better than nothing. Of course with some luck the data is still there but the database table only crashed or something like that. Only you can tell...

---

### Post by zbenta on 2011-01-07
Hi frostschutz,

Thanks for the tips, I've tried using strings on the qcow disk and I got some data out by redirecting the output to a text file.
I searched the resulting file for some text I knew was on my tickets.
I found a lot of tickets that I thought I lost.
Is there any way I can know where strings got the info from?
Can I use any other tool that can give me info about where the data came from?

---

### Post by frostschutz on 2011-01-07
Well, strings is the last resort only. It doesn't tell you anything, not the byte position, not which file it's from (if it's even a file and not free space).

I mean, you can mount read only and then grep -r "something unique" / and see if there are any files that have this text in. Should be a snippet of a lost ticket. This way you can find a file where this is in, if a file for it still exists.

You can also grep the raw image in binary mode to obtain a byte position of the snippet. Then you could open the raw image in a hex editor or similar and see what's around this position (or search for the string in the hex editor in the first place).

You shouldn't do this on the qcow2 though but on the raw device (i.e. what the VM itself works with, without qcow2 metadata getting in the way).

Depending on which file format was being used to store these tickets (database? ...) it may be possible to extract something more useful from there then...

---

### Post by zbenta on 2011-01-10
Hi frostschutz,

Thanks for all the tips.
I've rebooted the machine once again and all the files are now available.
I'm not sure what I have done but probably I've rebooted the machine with the correct virtual drive. Sorry for "newbieness".

---

