---
title: "Executable bit"
date: 2011-07-11
forum: Security
---

### Post by gameguy on 2011-07-11
I use java runtime environment a lot, and whenever I try and download a .jar file it doesn't run. I save it onto my data partition, which is NTFS, because it is also my data partition for windows (dual boot). On the NTFS filesystem, I can't change any permissions of anything, like the thing which stops executable bit. Under /home, however, I can change it. I was wondering if there was any way I could turn off it asking me about that. If not is there any way I can keep it on my data partition while still having it not prompt me about executable bit?

Thanks

---

### Post by CharlesA on 2011-07-11
You could mount the data partition as 777, just change the fstab entry.

---

### Post by gameguy on 2011-07-11
There is currently no entry for it in /etc/fstab. It just shows up as a drive in linux which I click on and mounts in /media/Data. I did it on my old computer (just reinstalled linux on a new computer). I want the partition to mount in /data upon boot but don't know how.

---

### Post by doas777 on 2011-07-11
I think the recommendation in that case would be to add it to fstab. I hate to suggest that for ntfs drives unless you boot into windows regularly and do a disk check every once in a while.

check out this advice on ntfs-config:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

it may give you the control you need.

---

### Post by gameguy on 2011-07-22
The partition is auto-mounting in /data.
How do I change it to type 777?
Here's my fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=c4ecd633-e469-4a9a-9243-898c03ca7c60 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_fgihfbdai_SEAGATE3 /home           ext4    defaults        0       2
/dev/mapper/isw_fgihfbdai_SEAGATE1 /data ntfs-3g defaults,user,locale=en_US.utf8 0 0

```

---

### Post by mc4man on 2011-07-22
The reason you need to set as executable is because your java is using the cautious-launcher in it's Exec command. 
Both Wine Windows Program Loader (.exe's) and java are affected, there is no other reason why the bit has to be set

It was decided not to offer you an option to override the cautious-launcher other than setting the bit on each file directly

java is a bit trickier than wine where there is only 1 .desktop and an alternate  direct launch command (wine
If desired the Exec= is in the .desktop of whichever java you are using and typically is found in /usr/share/applications

(you can use synaptic to find the actual name of it;s .desktop and location
You'd then just edit out the cautious-launcher from the Exec= line

Or just go ahead and only run from volumes where you can set permission on file by file basis - your choice and decision if the 'cautious-launcher' is of any value to you

An ex. of openjdk-6-jre as seen on 11.10 (where interesting enough wine-1.2 uses the cautious-launcher, wine-1.3 does not

gksudo gedit /usr/share/applications/openjdk-6-java.desktop
```
[Desktop Entry]
Name=OpenJDK Java 6 Runtime
Name[fi]=OpenJDK Java 6 - ajonaikainen ympäristö
Comment=OpenJDK Java 6 Runtime
Comment[fi]=OpenJDK Java 6 - ajonaikainen ympäristö
[COLOR="Red"]Exec=cautious-launcher %f /usr/lib/jvm/java-6-openjdk/bin/java -jar[/COLOR]
Terminal=false
Type=Application
Icon=openjdk-6
MimeType=application/x-java-archive;application/java-archive;application/x-jar;
NoDisplay=true
```
The red line would be changed to 

```
Exec=/usr/lib/jvm/java-6-openjdk/bin/java -jar %f
```

---

