---
title: "Server locks up and freezes on large file transfers or operations"
date: 2009-06-16
forum: Server Platforms
---

### Post by davidmigl on 2009-06-16
Running Jaunty 9 desktop on an eMachines T3522 (3 ghz celeron, 512mb, 100 mbps onboard nic). Yesterday, I tried to rsync my home directory on my laptop over. It went along fine until it got to a 700 mb .avi, when it stopped (it remained on the file for at least an hour, at which point it became clear it wasn't going to transfer). 

Today, I was using nautilus (sftp) on my laptop to browse some large RAW and TIF files on the server. I decided I didn't need about 9 gigs worth of stuff so I selected it and hit shift+delete. The server freezes up about halfway through. No response from sftp, ssh, web access, samba, nothing. I have to go to my server closet to physically power cycle the comp and reboot. Doesn't matter whether I'm on wireless or wired with the laptop.

There are two internal hard drives and an external drive. File operation in question was to the external drive, a 1 TB Western Digital MyBook essentials formatted in ext3.

/var/log/messages just says "--MARK--" at the time of the incident. No other relevant messages.

I found another thread where people said this might be due to a hardware issue. I can't underclock/undervolt due to the dumbed down consumer bios on this thing. Short of buying a whole new server, what can I do?

---

### Post by hictio on 2009-06-17
Take a look at this thread "[Large file transfers hardlock server](http://ubuntuforums.org/showthread.php?t=1091406)" to see if there is a hint or something that can help you.

---

### Post by davidmigl on 2009-06-17
Well I guess the first thing I will try is a PCI LAN card. I can't really do memtest right now since all the computers on my home network are using this server's samba shares for their most used files. So now I'm definitely putting emachines on my "never buy again" list, even for $180 at a best buy black friday special! Oh well...

---

### Post by davidmigl on 2009-06-17
Update: I bought a gigabit PCI lan card today, but the problem persists.I will try running memtest when I get a chance.

---

### Post by cariboo on 2009-06-17
Are you partitions formatted as ext4? I know there where some problems with large file transfer with the earlier alpha releases of Jaunty, but through updates, the problem seems to have gone away for most people.

When I rebuilt my server after FreeNAS failed, I formatted all my partitions except for a 10GB / partition as XFS, at the time there were still some question about ext4, and [Phoronix]("http://www.phoronix.com/scan.php?page=home") had a filesystem shootout that showed that XFS was just a tiny bit slower than ext4.

I have since transfered several directories containing from 50GB to 150Gb of data with zero problems.

---

### Post by davidmigl on 2009-06-17
You found the problem. 
The external drive is formatted as ext4. I have an internal drive with the same files on it in NTFS (It was originally in a windows PC, I copied all the files over to the external ext4 for a backup). I tried doing this operation on the interal NTFS drive and it worked, very quickly too.

That is surprising, I guess ext4 hasn't got all the bugs out just yet. Now the problem's going to be finding a place to store all the data on the terabyte drive while I format it to ext3...

Thanks for your help!

---

