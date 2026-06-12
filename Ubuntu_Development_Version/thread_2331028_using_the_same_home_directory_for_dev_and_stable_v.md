---
title: "using the same home directory for dev and stable versions"
date: 2016-07-17
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2016-07-17
I am thinking of installing ubuntu 16.04 alongside 16.10 would i be able to use the same home directory for both. 

i have few scenerios but don't know which would be best. 

1. both using the /home/<username>
2. pick a different user name for other linux system 
3. i seem somewhere you can seperate it by using something like 
/home/testing/<username>
/home/Stable/<username.

guessing you would do part 3 on the mount point section of the installer.

---

### Post by oldfred on 2016-07-17
Best not to share.
Those that say you can, then are doing like you suggest and have different users in same partition.
If sharing actual same /home then updates to programs may conflict with older version.
Example my KeepassX file from 14.04 was converted to a new version for 16.04. So now when I boot 14.04, I only have access to my old KeepassX file.

I normally keep /home inside a smaller / (root) of about 25GB and have many / partitions, one LTS as main working install and others for testing like my 16.10 install. But have all data in /mnt/data which is mounted in every install and all the standard data folders like Documents, Videos, Music, etc are in my data partition and linked back to each install.

---

### Post by terry_gardener on 2016-07-17
> **oldfred said:**
> Best not to share.
Those that say you can, then are doing like you suggest and have different users in same partition.
If sharing actual same /home then updates to programs may conflict with older version.
Example my KeepassX file from 14.04 was converted to a new version for 16.04. So now when I boot 14.04, I only have access to my old KeepassX file.

I normally keep /home inside a smaller / (root) of about 25GB and have many / partitions, one LTS as main working install and others for testing like my 16.10 install. But have all data in /mnt/data which is mounted in every install and all the standard data folders like Documents, Videos, Music, etc are in my data partition and linked back to each install.

thanks for the reply.

---

### Post by terry_gardener on 2016-07-18
> **oldfred said:**
> Best not to share.
Those that say you can, then are doing like you suggest and have different users in same partition.
If sharing actual same /home then updates to programs may conflict with older version.
Example my KeepassX file from 14.04 was converted to a new version for 16.04. So now when I boot 14.04, I only have access to my old KeepassX file.

I normally keep /home inside a smaller / (root) of about 25GB and have many / partitions, one LTS as main working install and others for testing like my 16.10 install. But have all data in /mnt/data which is mounted in every install and all the standard data folders like Documents, Videos, Music, etc are in my data partition and linked back to each install.

i have decided to do it the same way as you did as it seems the cleanest way to do it, separate partition for data. it is the way i use to do it years when i used windows as i reinstalled it regularly and when i read your post it reminded me of it. 

i would like to thank you for the help.

---

### Post by oldfred on 2016-07-18
Back when I still had Windows XP, I started with a shared NTFS data partition for my Firefox & Thunderbird profiles. I then added a Linux formatted data partition for data not needed in Windows and over time converted data to Linux data partition.

I still follow these instructions, although after several installs, I just scripted the edits as UUID of data partition does not change.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

And in my script I include the linking of the folders, but to understand the linking I originally did it one by one manually:
      
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)

---

