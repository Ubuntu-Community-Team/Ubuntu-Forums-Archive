---
title: "Securing my data"
date: 2011-04-02
forum: Security
---

### Post by needhelppeeps on 2011-04-02
One of the worst things that could happen is losing all the data on a machine so that has me thinking about this. Here are my thoughts and I'd like to hear other views.

Backup Media:

CD/DVD: They go bad even if the burn completes successfully, but they are a handy way to keep another copy of stuff as a backup of a backup. Are these actually helped or just give one a false sense of security (well, I can probably get it off DVD anyway)? It helped me once when a file had become corrupt but I did not realize it for a long time. The good copy was on an old DVD.

Tape: Too expensive for home use. Seems only practical in the business world. It also seems like there can be a lot of issues with tapes themselves.

Network Storage: I had a situation where ssh was not copying subfolders several layers deep, so I thought all my data was secure only upon further review realized that not all subfolders were present (this was on Fedora). Is there anyway to create "Samba like" folder access over an encrypted ssh channel? I've seen some NAS devices lose a configuration setting preventing data from copying, but any good backup software alters the user to this.

USB/External Hard Disk: This is currently my favorite way, just plug in a USB to a file server and dump stuff to it, then swap the USB with an identical one for redundancy. Are the hard disks used in most USB devices as good as mid-range laptop hard disks? 

Encapsulated data: Seems to me that anything that encapsulates the data is a possible point of failure. If the tar file becomes corrupt, can you still get all the non-corrupt data? What is the best encapsulation media from a recoverability standpoint? zip, rar, tar, etc? One thing I never liked about DVD was having to split a huge tar into 4GB chuncks. For example, what if the DVD for disk 1 goes bad but disk 2 is still fine, with two separate tars it is not an issue but what about with a split tar?

To encrypt or not? Encryption strikes me as another possible point of failure, because one could lose the key or forget the passphrase. Yet, it's probably not a good idea to have an unencrypted copy of one's financial data on a thumb drive. How to securely encrypt a thumb drive? Does the key stay on the home computer. Seems like if the key is on the thumb drive itself, then it would be no better than a password protected zip since all the finder would need to do is brute force the passphrase. 

Software:
Copy and paste: I like to use copy and paste, then checking the file count and size of the folders. Sometimes Ubuntu does not report the correct folder size in the file manager. For example, when I go to properties it tells me a folder is 50MB, then after tarring it I see that folder was actually 150. Has anyone else seen this? Is there a more reliable way to determine total folder size? 

I know some software can verify the files, so that might be one advantage to an automated solution. I think many use tar, but it seems like if a backup solution uses a custom encapsulation method that would be a major snag if part of the archive becomes corrupt.

Organization:
Having multiple copies is great, but having a mess of folders can lead to losing data due to confusion. How do you organize your backups. On my USBs, I try to keep everything named very clearly. I keep one historic folder which contains a very old copy of stuff in case I need to go way back and recover a file, and one recent folder which contains a recent backup so that I have the latest files. This seems to work well as external hard disk storage stays a head of my internal drives.


Backup Type:
Seems to me that differential, incremental have less use in the home  world, it seems like a home user would be more concerned about the total  body of data than the latest changes, whereas in business the latest  changes might be critical. I suppose for students working on papers and  certain home users that might be the case as well, though. What do you use, full backups everytime? If using DVD, I can see where a diff/inc bacup would be desirable to decrease the amount of media needed.

---

### Post by cariboo on 2011-04-02
I use rsync to backup to my server and an external hard drive, I'm currently using grsync, as I haven't got around to setting up a cron job on this system yet.

---

### Post by Dave_L on 2011-04-02
I just finished setting up [rsnapshot](http://www.rsnapshot.org/) to back up my netbook onto an external USB hard drive.

If you're not confident of the quality of external drives, you can always buy an external drive enclosure, and put your choice of internal drive into it.

---

