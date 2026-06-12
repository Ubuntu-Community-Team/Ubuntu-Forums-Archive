---
title: "Virus That Causes Data Corruption"
date: 2008-12-05
forum: Security
---

### Post by CrusaderAD on 2008-12-05
Has anyone here ever heard of a virus that causes data corruption? Like when the hard drive begins to fail or certain random sectors become corrupt? We're hosting a website and the host keeps having to change the drives because they keep failing. It's happened 3 times. Or do you think that they are just using faulty / used hardware?

---

### Post by hyper_ch on 2008-12-05
I think it's faulty hardware...

---

### Post by CrusaderAD on 2008-12-05
That's exactly what I thought.

---

### Post by hyper_ch on 2008-12-05
did you use the same brand and series?

---

### Post by CrusaderAD on 2008-12-05
Yeah, same everything. Another thing I thought was that our hosting company is restoring or transferring already corrupted data, but they say you can;t do that. Can you transfer corrupt data? I would think so...

---

### Post by AliTabuger7 on 2008-12-05
I believe you can recover data, but it'll probably cost you a fortune. Also, I think the services I've heard other people use usually specialize in NTFS, for obvious reasons. They may be able to handle ext3 as well.

Is it possible that you are doing too many read/writes?
What temperature is it usually?

---

### Post by CrusaderAD on 2008-12-05
I'm not sure of the temp. It's an offsite server hosted by rackspace. Do you think too many hits to the site can cause accelerated corruption?

---

### Post by cariboo on 2008-12-05
It sounds more like they are cloning the drive with corruoted data, a command like dd will make an exact duplicate of the data, corruption and all. It is that, or their backup is corrupt, and they are just restoring with corrupt data.

Jim

---

### Post by The Cog on 2008-12-06
The first virus I ever met personally was the Dark Avenger which corrupted hard disks by overwriting random sectors. Mostly it would hit files, but occasionally hit a directory or even the partition table. This was a DOS virus, of course. It managed to infect LOGIN.EXE in our company file server and caused lots of grief.

---

### Post by CrusaderAD on 2008-12-06
I'm sure they're probably restoring corrupt data. But from what they said, "You cannot backup or transfer corrupt data". I think they're just trying to avoid some serious complaints.

---

### Post by CrusaderAD on 2008-12-09
Here's a response from our hosting company:

"I did run into some issues trying to perform the checkdisk. When I tried to enter the recovery counsel I could not Due to the drive being corrupted. I was able to perform an offline checkdisk to get the results posted. I was able to perform the checkdisk on the D drive but I am unable at the moment to get results for the checkdisk performed on the D. At the moment the drive is corrupt as we know. The first two scans did take a while and the Old_D did not have time within our maintenance window to complete. We can schedule to scan the OLD_D but the problem at this time exist on the C: drive. The file system is corrupt on C: where the system files are located. If you would like for us to Schedule to scan OLD_D we can and we will do our best to get results."

We have the same data sitting on development servers with no problems. It has to be hardware right?

---

