---
title: "Expanding Virtual Disk in Attached Storage (MD3000)"
date: 2010-11-20
forum: Server Platforms
---

### Post by igorm80 on 2010-11-20
I have ubuntu server with an attached external storage array Dell MD3000. 

Once the virtual disk gets expanded in the attached storage, what is the procedure to make the os aware of the disk size change?

I have attempted re-scanning the scsi bus with 'echo "- - -"' and partprobe with no success. The storage array console shows the expanded disk size correctly, however the ubuntu continues to see the old disk size.

I have not tried rebooting since I am running production databases on this machine.

Is there a way to pick up the new attached disk sizes without rebooting?

Thanks!

---

