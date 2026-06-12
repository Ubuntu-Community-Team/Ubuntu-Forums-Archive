---
title: "New install - Other HDD's? sharing with samba"
date: 2008-09-11
forum: Server Platforms
---

### Post by GodsDead on 2008-09-11
Hey there, i just installed a fresh version of ubuntu 8.04 server edition, all runs fine, with webserver, SSH, samba, DNS, i can view my webserver running =] and can connect via SSH which is ausom! 
I installed webmin first things first, as im not that good with the terminal! :S
Its amazing, found mostly everything, i can add samba shares etc, and just wondered, how do i share my other HDD's?

Because if i go to "Partitions on Local Disks" in webmin they show up, 
```

SCSI device A 	6.04 GB 	ATA FUJITSU MPD3064A 	3 	IDE parameters
SCSI device B 	19.08 GB 	ATA Maxtor 2B020H1 	2 	IDE parameters
SCSI device C 	76.69 GB 	ATA Hitachi HDS72168 	1 	IDE parameters

```

Each details as having a Device file /dev/sdc1 for example, but when i try and assign this Via the webmin interface "Samba Windows File Sharing" -> "create new file share" using the "Directory to share" Browser, i cant see the disks in /dev all i get is:

```

	.initramfs 	60 bytes 	11/Sep/2008 	19:28
	.static 	60 bytes 	11/Sep/2008 	19:28
	.udev 	140 bytes 	11/Sep/2008 	19:29
	bus 	60 bytes 	11/Sep/2008 	19:28
	disk 	100 bytes 	11/Sep/2008 	19:28
	fd 	0 bytes 	11/Sep/2008 	20:38
	input 	280 bytes 	11/Sep/2008 	19:29
	net 	60 bytes 	11/Sep/2008 	19:15
	pts 	0 bytes 	11/Sep/2008 	19:28
	shm 	40 bytes 	11/Sep/2008 	19:29
	snd

```

ALthough through SSH i type in:
```

ls /dev

```

and i get hundreads of files/folders!

i tryed just typeing in "/dev/sdc1" for the "Directory to share", but after i login to the server in windows network, i cant access the folder it created! I can create shares for anything on the OS HDD ( the 6gb one ) but i cant seem to create a share for the otehr HDD's?

Can somebody please help me =]

This is an entirely fresh server install apart from installing webmin for ease!!

Thanks, Tom.

---

### Post by GodsDead on 2008-09-11
Oh i feel like an idiot, i forgot that i had to "mount" the HDDS first -__- haha

for anyone else that had/has this problem:
```

tom@spicy:~$ sudo mkdir /mnt/sdb1
tom@spicy:~$ sudo mount /dev/sdb1 /mnt/sdb1

```

Now will these mounts stay on after reboot? or is this a manual "mount" every time the system starts?

---

### Post by Iowan on 2008-09-11
Check [this]("http://ubuntuforums.org/showthread.php?t=288534") cifs How-To.

---

