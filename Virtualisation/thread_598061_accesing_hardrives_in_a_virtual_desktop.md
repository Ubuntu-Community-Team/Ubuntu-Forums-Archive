---
title: "accesing hardrives in a virtual desktop"
date: 2007-10-31
forum: Virtualisation
---

### Post by Jbs63 on 2007-10-31
I was just wondering if this can be done? i have xp booted on a virtual boot in vmware server in UBUNTU but i cant seem tO access my real hardrives can someone tell me how or give me a link to tell me how to do this??

---

### Post by Jbs63 on 2007-10-31
I was just wondering if this can be done? i have xp booted on a virtual boot in vmware server in UBUNTU but i cant seem tO access my real hardrives can someone tell me how or give me a link to tell me how to do this??

---

### Post by Terc on 2007-10-31
You'll need to create new disks on your virtual machine for each real disk you have.

After shutting down your virtual machine:

1. edit your virtual machine
2. click add...  (we will be adding another hard drive)
3. Select Hard Disk, and click Next
4. Choose Use a physical disk
5. Select the disk you want to use, and select use entire disk, click next
6. Select a location to store the vmdk
7. Click Finish.

Repeat these steps for each physical disk you have, then start your virtual machine, it should now be able to detect the disks.

Be careful, this means you can now edit your host machine's disk, you could break something if you don't know what files you are messing with.

It is also important to note that you will not be able to read ext3 drives in windows without installing the ext2 driver found here: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

If you have chosen some other filesystem, you will need to figure that out yourself.

---

### Post by Terc on 2007-10-31
ahem....
[-X
Perhaps you should consider giving people a chance to reply to your thread before creating another...

I answered your question over here:  [http://ubuntuforums.org/showthread.php?t=598061]("http://ubuntuforums.org/showthread.php?t=598061")

Please, create ONE thread per issue, and we'll have a much cleaner forum!

Thanks, and good luck!
;-)

---

### Post by Jbs63 on 2007-10-31
it says its unable to detirmine the bus type

---

### Post by Jbs63 on 2007-10-31
sorry meat.. i just thought i might have put it in the wrong section.. looks like i was wrong

---

### Post by Jbs63 on 2007-10-31
that meant to say sorry mate :P

---

### Post by bodhi.zazen on 2007-10-31
Well, just to add my 2c ...

Add a network share protocol on the host (nfs, sshfs, ftp, http, samba).

Once you set it up, you can make a shared partition that should work across OS and guests.

---

### Post by dyrer on 2007-11-03
> **Terc said:**
> You'll need to create new disks on your virtual machine for each real disk you have.

After shutting down your virtual machine:

1. edit your virtual machine
2. click add...  (we will be adding another hard drive)
3. Select Hard Disk, and click Next
4. Choose Use a physical disk
5. Select the disk you want to use, and select use entire disk, click next
6. Select a location to store the vmdk
7. Click Finish.

Repeat these steps for each physical disk you have, then start your virtual machine, it should now be able to detect the disks.

Be careful, this means you can now edit your host machine's disk, you could break something if you don't know what files you are messing with.

It is also important to note that you will not be able to read ext3 drives in windows without installing the ext2 driver found here: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

If you have chosen some other filesystem, you will need to figure that out yourself.

Settings-->hard Drive?
First IDE or what?
What should I do?
Is looking only for virtual drives

---

### Post by koenn on 2007-11-03
read this again:
> **Terc said:**
> You'll need to** create new disks **on your virtual machine for each real disk you have.

After shutting down your virtual machine:

1. edit your virtual machine
**2. click add.**..  (we will be adding another hard drive)
3. Select Hard Disk, and click Next
**4. Choose Use a physical disk**

...



---

### Post by Jbs63 on 2007-11-05
na that doesnt work because you cant really have 2 computers accesing the same phisical disk at the same time. i found its really actually quite simple with samba though. you just make the drive shared (after installing samba.) then join a windows network and you should be able to access it from any networked computer

---

