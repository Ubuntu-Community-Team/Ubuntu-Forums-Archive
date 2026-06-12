---
title: "Trying to install Hardy Heron with SCSI attached array"
date: 2009-09-24
forum: Server Platforms
---

### Post by banditti on 2009-09-24
Hello,

I am trying to install Ubuntu Hardy Heron on my server (Dell 2450) with an attached 1.9 TB Promise array. When I get to the partitioning it sees the external SCSI array as SDA and the drives in the server as SDB. I want to be able to set up the server drives as SDA and the external array as SDB and then partition the server drives with / and swap while putting /home on the external array. 

What do I need to do to set the server drives as SDA and the array as SDB?

Any help is appreciated.

---

### Post by KickYerJunk on 2009-09-24
OK...I'm actually the one that posted this. I didn't see that Banditti had logged into the forums on my laptop the other day.

Thanks for any help with this!

---

### Post by sloggerkhan on 2009-09-24
Shouldn't you be setting up arrays/drives using uuids becuase the choice of sda vs sdb vs sdc & etc can be somewhat arbitrary and inconsistant?

---

### Post by KickYerJunk on 2009-09-24
From my readings I understand that UUIDs are used with all versions of Ubuntu since 6.06. I don't know a lot about formatting in Linux and this is the first time I've tried installing with an external array attached. I just don't want Ubuntu booting off my array. I want that to be used strictly for storage. I'm willing to do whatever I need to do to make that happen. 

Thanks!

---

### Post by sloggerkhan on 2009-09-24
Look up how to asign the array disks UUIDs, then use mdadm to build an array using those disks choosing appropriate parameters. Then mount the resulting md* device.

I think even if you build from sd* devs, it will probably make uuids for correct disks on build, but google.

Google for details, and you will be able to get going without too much trouble.

---

