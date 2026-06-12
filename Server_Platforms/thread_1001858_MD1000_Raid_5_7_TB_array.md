---
title: "MD1000 Raid 5 7 TB array"
date: 2008-12-04
forum: Server Platforms
---

### Post by nroussi on 2008-12-04
Hi. I am running an Edubuntu Server 8.04.1 with a PERC 5/e controlling an MD1000 as external storage. In the MD1000 I have 15-500GB seagate drives and they operate as a RAID 5 array. I have followed this guide:
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")
I used the command line options first. Out of the 7TB space that was available only 2TB were formated as ext3. The rest was just unallocated space. Then I tried the GUI approach with GParted. I deleted the 2TB partition that was created with the command line mkfs. Then I tried to create a new partition (ext3) but the maximum that it would take is ~400GB. I thought that the maximum size for a volume is 16 TB or am I wrong?

I would like to have all 7TB available as one partition. Is that possible?

Thanks

---

### Post by CrucifiedEgo on 2008-12-04
this tutorial is geared towards fedora, but might be a good starting off point: [http://www.unixgods.org/~tilo/linux_larger_2TB.html](http://www.unixgods.org/~tilo/linux_larger_2TB.html)

---

### Post by nroussi on 2008-12-04
Thanks for the reply. I tried that and then I tried this : [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
But during the formatting one of my drives failed and I had to rebuild the array. Now the main drive of the server which was at /dev/sda is now /dev/sdb. How can I change that?

---

### Post by nroussi on 2008-12-05
Everything is up and running but there is still a problem. Right now I have a 3ware 9650SE with 4 SATA drives in RAID 5 as the main drive on my server and then the MD1000 with 15 drives as the external secondary drive. After everything was configured as mentioned above I run postmark on the 2 arrays and these are the results:
> nicolas@edubuntuS2:~$ sudo postmark
PostMark v1.51 : 8/14/01
pm>help
set size - Sets low and high bounds of files
set number - Sets number of simultaneous files
set seed - Sets seed for random number generator
set transactions - Sets number of transactions
set location - Sets location of working files
set subdirectories - Sets number of subdirectories
set read - Sets read block size
set write - Sets write block size
set buffering - Sets usage of buffered I/O
set bias read - Sets the chance of choosing read over append
set bias create - Sets the chance of choosing create over delete
set report - Choose verbose or terse report format
run - Runs one iteration of benchmark
load - Read configuration file
show - Displays current configuration
help - Prints out available commands
quit - Exit program
pm>set size 10000 10000000
pm>set number 2000
pm>set transactions 2500
pm>set location /monsterDrive
pm>run
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Time:
        217 seconds total
        155 seconds of transactions (16 per second)

Files:
        3263 created (15 per second)
                Creation alone: 2000 files (35 per second)
                Mixed with transactions: 1263 files (8 per second)
        1229 read (7 per second)
        1271 appended (8 per second)
        3263 deleted (15 per second)
                Deletion alone: 2026 files (405 per second)
                Mixed with transactions: 1237 files (7 per second)

Data:
        [B]6337.51 megabytes read (29.21 megabytes per second)
        18248.26 megabytes written (84.09 megabytes per second)[/B]
pm>quit
nicolas@edubuntuS2:~$ sudo postmark
[sudo] password for nicolas: 
PostMark v1.51 : 8/14/01
pm>set size 100000 10000000
pm>set number 2000
pm>set transactions 2500
pm>set location /home/nicolas
pm>run
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Time:
        2842 seconds total
        1370 seconds of transactions (1 per second)

Files:
        3263 created (1 per second)
                Creation alone: 2000 files (1 per second)
                Mixed with transactions: 1263 files (0 per second)
        1229 read (0 per second)
        1271 appended (0 per second)
        3263 deleted (1 per second)
                Deletion alone: 2026 files (106 per second)
                Mixed with transactions: 1237 files (0 per second)

Data:
        [B]6613.14 megabytes read (2.33 megabytes per second)
        18457.72 megabytes written (6.49 megabytes per second)[/B]
pm>quit
As can be seen from the benchmark, the PERC5 test which is the first run, has ~29MB/s but the main drive has only 2.33 MB/s. Is that normal? How can I check if there is a problem with the RAID adapter. Or are these numbers normal?

Thanks

---

### Post by nroussi on 2008-12-11
This is for people that stumble upon this post after a search. I have somehow resolved the issue of the 2MB/s on the 3ware 9650SE-4LPML card. There are 2 solutions. 
First, if you have not purchased a RAID card yet, do not buy 3ware. Their support is just like Canada's military. It's there but useless. Get a PERC5 card from ebay, it will cost the same maybe less. 
Second, if you did get a 3ware card, download the complete-codeset iso and burn it. Reboot from the CD and follow the prompts to update the controller firmware. Remove the CD and reboot. While the computer is booting up press Alt-3 to access the 3ware BIOS. If you have a RAID5 array, enable the Write Cache and set the storsave profile to performance.

This is the result after running the above benchmark after doing these steps:
> PostMark v1.51 : 8/14/01
pm>set size 10000 10000000
pm>set number 2000
pm>set transactions 2500
pm>set location /home/nicolas
pm>run
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Time:
        311 seconds total
        198 seconds of transactions (12 per second)

Files:
        3263 created (10 per second)
                Creation alone: 2000 files (19 per second)
                Mixed with transactions: 1263 files (6 per second)
        1229 read (6 per second)
        1271 appended (6 per second)
        3263 deleted (10 per second)
                Deletion alone: 2026 files (225 per second)
                Mixed with transactions: 1237 files (6 per second)

Data:
[B]        6337.51 megabytes read (20.38 megabytes per second)
        18248.26 megabytes written (58.68 megabytes per second)
[/B]

Now there are some other things that need to be done, like updating the driver, there is something called 3DM2 tool for 3ware and something called CLI. Their support could not answer these questions. Still waiting on them after 4 days to give me a clear answer.

---

