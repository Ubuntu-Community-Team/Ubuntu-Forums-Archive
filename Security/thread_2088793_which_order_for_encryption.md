---
title: "which order for encryption?"
date: 2012-11-27
forum: Security
---

### Post by soomon on 2012-11-27
I hope this is the right section, as i am more asking from the performance point of view.

i want to encrypt my data partition. 

i was thinking:
disk > software raid 5 > encryption > lvm > ext4

now i read that performance is much better when you do:
disk > encryption > software raid 5 > lvm > ext4 

because the system spawns 4 threads for en/decryption. 
my source is: [http://superuser.com/questions/305716/bad-performance-with-linux-software-raid5-and-luks-encryption]("http://superuser.com/questions/305716/bad-performance-with-linux-software-raid5-and-luks-encryption")

my system has a  Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
so it has AES-NI.

is that true?
if i choose the same passphrase for all disks, do i have to enter the password multiple times or is once enough for all disks?

thanks & greets,
soomon

---

