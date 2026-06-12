---
title: "MDADM raid array - 2 devices failed"
date: 2014-06-02
forum: Server Platforms
---

### Post by raptorhunter2 on 2014-06-02
I logged into the server and 2 devices (out of 4) have failed. I restarted the machine and now I don't know how to fix this.


/dev/sdb:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : f90144d3:34aec212:4a9ce816:8075dd0c
           Name : red:0  (local to host red)
  Creation Time : Mon Aug  1 22:55:15 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860532896 (2794.52 GiB 3000.59 GB)
     Array Size : 17581598208 (8383.56 GiB 9001.78 GB)
  Used Dev Size : 5860532736 (2794.52 GiB 3000.59 GB)
   Super Offset : 5860533152 sectors
          State : clean
    Device UUID : ae9f6b38:fffe49b3:4ef41f7d:bb1e4d15


    Update Time : Mon Jun  2 01:53:40 2014
       Checksum : 64277c09 - correct
         Events : 25430


         Layout : left-symmetric
     Chunk Size : 256K


   Device Role : Active device 2
   Array State : A.A. ('A' == active, '.' == missing)


mdadm --examine /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : f90144d3:34aec212:4a9ce816:8075dd0c
           Name : red:0  (local to host red)
  Creation Time : Mon Aug  1 22:55:15 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860532896 (2794.52 GiB 3000.59 GB)
     Array Size : 17581598208 (8383.56 GiB 9001.78 GB)
  Used Dev Size : 5860532736 (2794.52 GiB 3000.59 GB)
   Super Offset : 5860533152 sectors
          State : clean
    Device UUID : 6b7de697:d6585ce8:bbeccd5e:70229e1a


    Update Time : Wed May 28 20:57:43 2014
       Checksum : dfb12429 - correct
         Events : 25376


         Layout : left-symmetric
     Chunk Size : 256K


   Device Role : Active device 1
   Array State : AAA. ('A' == active, '.' == missing)


mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x2
     Array UUID : f90144d3:34aec212:4a9ce816:8075dd0c
           Name : red:0  (local to host red)
  Creation Time : Mon Aug  1 22:55:15 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860532896 (2794.52 GiB 3000.59 GB)
     Array Size : 17581598208 (8383.56 GiB 9001.78 GB)
  Used Dev Size : 5860532736 (2794.52 GiB 3000.59 GB)
   Super Offset : 5860533152 sectors
Recovery Offset : 3296549736 sectors
          State : clean
    Device UUID : 876f1446:4aa5300b:014f0882:169b84fa


    Update Time : Mon Mar 10 11:53:51 2014
       Checksum : 77e7f14e - correct
         Events : 24910


         Layout : left-symmetric
     Chunk Size : 256K


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)


mdadm --examine /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : f90144d3:34aec212:4a9ce816:8075dd0c
           Name : red:0  (local to host red)
  Creation Time : Mon Aug  1 22:55:15 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860532896 (2794.52 GiB 3000.59 GB)
     Array Size : 17581598208 (8383.56 GiB 9001.78 GB)
  Used Dev Size : 5860532736 (2794.52 GiB 3000.59 GB)
   Super Offset : 5860533152 sectors
          State : clean
    Device UUID : f6ee18dd:bacb5ff0:3626edf3:ea849f4f


    Update Time : Mon Jun  2 01:53:40 2014
       Checksum : f70a3021 - correct
         Events : 25430


         Layout : left-symmetric
     Chunk Size : 256K


   Device Role : Active device 0
   Array State : A.A. ('A' == active, '.' == missing)

---

### Post by TheFu on 2014-06-02
If it was RAID5 and you lost 2 devices and didn't have ANY spares, there is only one thing left to do.

Get those backups ready for a restore.

BTW, the last line there shows that 2 drives are still missing.  Why? Could be bad cables, dead drives, bad SATA ports, no power, ... that will need to be resolved first.

Again, get those previously made backups ready. You are gonna need them.

---

### Post by raptorhunter2 on 2014-06-02
All of the drives are functional and readable, I just need to know how to add them back into the raid array. Please help.

---

### Post by TheFu on 2014-06-02
I think all the data is gone, so you'll need those backups.

Just recreate the RAID using **mdadm** as normal if all the drives are magically available now. Then restore the backups into it.  Here's the ubuntu mdadm guide: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)   google found it.  Ubuntu has lots of how-to guides that are usually very well written at help.ubuntu.com  Also, these forums have many RAID setup discussions with detailed examples.

---

### Post by raptorhunter2 on 2014-06-02
According to the Disk Utility 3 out of 4 disks are healthy and the 4th has "a few bad sectors"

---

### Post by raptorhunter2 on 2014-06-02
I tried to assemble but with the 3 best drives but it says that it "can't find the superblock" and the "device is busy"

Please advise.

---

### Post by TheFu on 2014-06-02
> **raptorhunter2 said:**
> According to the Disk Utility 3 out of 4 disks are healthy and the 4th has "a few bad sectors"

Go buy a new HDD.  Any drive that has a failure like that cannot be trusted for primary data use, IMHO.  If you want, run **badblocks** on it to see how bad it really is - might be good enough for backups.  Is it under warranty still?

Oh ... and I've never used "disk utility" - don't have a clue what that is.  I run servers.

---

### Post by raptorhunter2 on 2014-06-02
Here is mdadm.conf

cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md127 level=raid5 num-devices=5 UUID=5ad42d4a:e216b702:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=966b2f11:c7e5551f:e368bf24:bd0fce41


# This file was auto-generated on Mon, 09 May 2011 14:30:45 -0500
# by mkconf $Id$

---

### Post by raptorhunter2 on 2014-06-02
mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md127
mdadm: no recogniseable superblock on /dev/sdf
mdadm: /dev/sdf has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: no recogniseable superblock on /dev/sda4
mdadm: /dev/sda4 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sda3
mdadm: /dev/sda3 has wrong uuid.
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: looking for devices for /dev/md1
mdadm: no recogniseable superblock on /dev/sdf
mdadm: /dev/sdf has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: no recogniseable superblock on /dev/sda4
mdadm: /dev/sda4 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sda3
mdadm: /dev/sda3 has wrong uuid.
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.

---

### Post by raptorhunter2 on 2014-06-02
mdstat

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sde[0](S) sdc[1](S) sdb[3](S) sdd[4](S)
      11721065792 blocks super 1.0
       
unused devices: <none>

---

### Post by raptorhunter2 on 2014-06-02
I got it back online and it's copying the data off now.

Thanks for nothing.

---

### Post by kosmokramer314 on 2014-06-03
uhh..last I checked you're responsible for your own data...nobody can fix your issues except you, and these forums are to get you pointed in the right direction.  Go be ungrateful somewhere else.  You learned how to fix it..good job....you mad bro?

---

### Post by TheFu on 2014-06-03
> **raptorhunter2 said:**
> I got it back online and it's copying the data off now.
Fantastic - perhaps you could help others by posting the command(s) used?

> **raptorhunter2 said:**
> Thanks for nothing.

Glad it was exactly what you needed to solve this. Happy to be of help!  Please tip your waiters.

What would you have me do?  Provide the exact command that would trash everything on the system, so that I'd be blamed? How could I know the multitude of other details that haven't been provided here?  No thanks. YOU need to be responsible AND understand it.  If you want someone to handle stuff like this for you, lots of people will do that for a price - "monthly support contract" is the search term.

BTW, I still wouldn't trust that drive.  Without knowing the root cause of the original issue, the issue is likely to happen again.

I am sorry that you found my carefully worded replies unhelpful. I really am. Would zero responses have been better?

---

### Post by raptorhunter2 on 2014-06-03
^^ You could start by being helpful instead of making jokes about losing all my data. :-?


And the command I used was simple. mdadm -D showed the array was inactive, but apparently I still had to issue a mdadm --stop command to release the drives and then all I had to do was run mdadm --assemble and it worked great. If I had listened to you I would have given up on ever fixing this. For an expert who's so immersed in the server world that you don't know about "disk utility" that us peasants use, you sure seem to lack the most basic understanding of basic mdadm problems. Maybe next time you should step aside and let someone more knowledgeable handle questions here.

---

### Post by kosmokramer314 on 2014-06-03
> **raptorhunter2 said:**
> ^^ You could start by being helpful instead of making jokes about losing all my data. :-?

having backups ready is no joke... I recently had an issue with MDADM RAID setup and you probably would have found your answer in that post, but you seem to be to cool to search and just want answers.  good luck with that.  :-({|=  <-- playing just for you.

---

### Post by raptorhunter2 on 2014-06-03
^^^ I did find my answer by searching. It took several hours of searching and experimenting and I finally found this simple fix. 

Am I complaining that I didn't get any help from you guys? **No.** 
I'm complaining that I was given a rude dismissive answer by someone that clearly knows nothing about mdadm. His answer could have made me **give up all hope** of getting my data back when apparently it was an easily solvable issue. That's not okay.

---

### Post by rubylaser on 2014-06-05
The problem is solved and a productive conversation seems unlikely to occur going forward.  I have seen TheFu answer several mdadm questions successfully on the forums in the past, so I don't think claiming he is ignorant to mdadm holds much weight. I have personally helped numerous people try to solve issues with mdadm from "experimenting" with commands they found via Google before posting the the forums as a last resort. In most cases, those arrays are hosed and only sometimes recoverable by re-creating the array with the --assume-clean option.  Restoring from backups as an option to recover lost files is never a bad idea.

Also, mdadm is very robust, but it's very easy by trying to help someone fix an issue to cause more harm because you haven't seen the whole picture or understand what lead up to the issue.  This makes providing the steps that lead up to the incident and some of your pertinent info critical for someone to intelligently help you solve a problem (/etc/mdadm/mdadm.conf file, SMART results, dmesg results, etc.).  Finally, there are frequently mdadm questions on this forum, and we are always looking for contributors. So, if you are willing to help others out, I would encourage you to help them with your mdadm knowledge.

---

