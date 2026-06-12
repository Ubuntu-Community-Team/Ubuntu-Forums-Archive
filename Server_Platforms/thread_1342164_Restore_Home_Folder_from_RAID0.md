---
title: "Restore Home Folder from RAID0"
date: 2009-11-30
forum: Server Platforms
---

### Post by jimpenka on 2009-11-30
Hello,

two weeks ago i had a small problem with our Server at the Office. One hard drive of a RAID 0 configuration broke. The broken hard drive had some data on it which had been previously backed up. However, the /home folder was linked to it and was lost in the process. As the other drive kept the / folder, the system was still bootable and all libraries and programs were still there. 

Now i have replaced the broken drive and reconfigured the RAID (this time as 1). However i have to restore the /home folder in some way, so the users can log-on via samba for example. 
I wonder what is the best way to proceed. Reinstall the home folders and passwords manually? Or is there a better way around?

Thanks

---

