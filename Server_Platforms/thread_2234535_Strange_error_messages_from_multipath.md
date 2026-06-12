---
title: "Strange error messages from multipath"
date: 2014-07-15
forum: Server Platforms
---

### Post by Hoppingbull on 2014-07-15
Hi All,

we have had som issues here latly with SAN connected machines and XFS file system. 
Every now and then after a reboot, the SAN connected XFS filesystem does not mount. And when we check the error logs we get that the filesystem is corrupt and needs to be repaird. 

Repairing the file system often results in massive loss of data. In the syslog we can see strange messages connected to multipath as seen below.
Can anyone maybe explain a little what these messages meen? 

Jul 15 10:23:02 : [ 7647.664786] device-mapper: ioctl: Unable to change name on mapped device mpath83 to one that already exists: mpath77
Jul 15 10:23:02 : [ 7647.675465] device-mapper: ioctl: Unable to change name on mapped device mpath71 to one that already exists: mpath78
Jul 15 10:23:02 : [ 7647.708322] device-mapper: ioctl: Unable to change name on mapped device mpath83 to one that already exists: mpath77
Jul 15 10:23:02 : [ 7647.712222] device-mapper: ioctl: Unable to change name on mapped device mpath71 to one that already exists: mpath78
Jul 15 10:23:02 : [ 7647.845576] device-mapper: ioctl: Unable to change name on mapped device mpath90 to one that already exists: mpath70
Jul 15 10:23:02 : [ 7647.879429] device-mapper: ioctl: Unable to change name on mapped device mpath90 to one that already exists: mpath70
Jul 15 10:23:02 : [ 7647.927412] device-mapper: ioctl: Unable to change name on mapped device mpath91 to one that already exists: mpath86
Jul 15 10:23:02 : [ 7647.970334] device-mapper: ioctl: Unable to change name on mapped device mpath92 to one that already exists: mpath88
Jul 15 10:23:02 : [ 7647.975053] device-mapper: ioctl: Unable to change name on mapped device mpath92 to one that already exists: mpath88

Kr
Marcus

---

