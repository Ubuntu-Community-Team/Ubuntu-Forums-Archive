---
title: "no disks detected during install - raid 1"
date: 2011-10-22
forum: Server Platforms
---

### Post by Hazey11 on 2011-10-22
Hey guys,     

Generally I can debug myself out of a hole, but this ones got me  stumped. I've had linux servers since I was a kid, finally got around to  building an actual server rack. The first server got here and i'm  working on it, 2 1TB harddrives with the mobo raid 1 (fake raid) - it's a  super micro mobo and has 2 options for raid (intel and adaptec) - any  big differences between these? I'm now using adaptac as it seems a bit  better.      Regardless what I did: installed zentyal (based on 10.04)  no problems at all, detected the fake raid as one and installed without  issue. Installed with encrypted LVM (at this point the raid setup was  via intel). Well after playing around I decided I don't like zentyal and  I just want a shell, so I went to install ubuntu server 10.04 LTS  vanilla.      

After reading on intel/adaptec that is when I switched the raid to  adaptec from intel (with the original raid array still in tact), I then  set up the raid array realizing it would take forever, but read (from  adaptec forums) that it will continue building during OS install, so I  exited out after starting the build process and booted the ubuntu cd -  come to find it can't detect ANY harddrives and just goes to iSCSI  remote options. So I go back, try switching back to intel raid, same  thing. I can NOT get the fakeraid array to be detected now.      I've  tried undoing the raid and of course can see harddrives then, but any  form of raid via mobo is NOT detected. Is this due to it being encrypted  (stretching here)? Due to swapping raid from intel to adaptec without  breaking apart the raid first? Any ideas?      

I eventually gave up and left adaptec raid panel on build overnight, its  been almost 12 hours and it's at 80% - any help would be appreciated.  I'm thinking it could be because the array isnt built/cleared so i'm  trying that, if that is definitely not the case I have no problem  breaking out of the build to start the install and provide logs.       Before I started that long build process, when install was hung on  detecting any harddrives, I was looking into the logs and could see it  was having trouble picking up the harddrives saying things like unknown  partition table via kernel, raid set was not activated via disk-detect,  but that's all I can remember off the top of my head that stuck out. 

I've looked over the ubuntu fakeraid documents and it says it should  have no problem with 10.04 beyond a few tweaks after install. Obviously  it worked flawlessly the first time around so I did something to mess it  up (mbr?) and can't figure how to revert.      Also have tried  un-raiding the harddrives and installing while rebuilding the partition  table on both harddrives, then rebuilding the fakeraid array via intel  and trying install again to no avail. 

Any and all help of course greatly appreciated :smile: Thanks!

---

### Post by TheR on 2011-10-23
Why don't you forget about this fake raid and use mdadm to create real linux raid ;-)

by
TheR

---

