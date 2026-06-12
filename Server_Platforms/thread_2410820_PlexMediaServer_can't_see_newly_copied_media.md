---
title: "PlexMediaServer can't see newly copied media"
date: 2019-01-21
forum: Server Platforms
---

### Post by hgeri005 on 2019-01-21
Hey guys.

I used to have a Windows Server at home, but a few years back decided to go with Ubuntu instead. For the life of me I can't remember how I made it work back then, but here's how it worked: I kept the NTFS partition containing my Movies, TV Shows, etc... With a lot of trial and error I got everything working. By everything I mean: A samba share I can access from my Windows machines, a plex media server, and a Deluge torrent client I can access from my browser that dumps all new downloads into a certain folder, after which I copy them into their respective folders from a Windows machine.

Now a few days ago I screwed up the entire OS, and decided to get rid of the NTFS partition. So I backed up all my data, reinstalled ubuntu, and moved my data back to /home/myusername/SERVER . Created a samba share, installed plex, deluge, all is fine. Since I didn't have an external HDD at hand, I backed up my data to a laptop through the network. So I mounted that folder to copy my stuff back, and I used "rsync -ah --progress" to see the speed and progress of the restore. As my files started pouring back in to the TV Show's folder, plex started to pick them up. 

However, my library was not up to date, I added a new show, and got a few new episodes of existing shows. Using the deluge download & copy to library from Windows method. What I realised, is that neither the new show, nor the few extra episodes are being picked up by Plex, but the files pouring in from the restore, are recognized. I went into Plex settings, I checked the library folder, and it can see the new folders/files.

Please see the attachments. My example is: The Night Manager, which I just added. It's not picked up by plex, but as you can see it sees the folder as well as the files in it.

Could you guys help me out here? I would greatly appriceate any help!

Regards

Edit: I tried giving rw permission to new folders, that didn't help.

---

### Post by TheFu on 2019-01-21
Please show the output from** ls -al **on the directory and at least 1 of the files.  The 'plex' userid must have at least read-access to media files.

Never forget that Linux/Unix are multiuser.

---

### Post by slickymaster on 2019-01-21
Thread moved to **Server Platforms** for a better fit

---

### Post by hgeri005 on 2019-01-21
> **TheFu said:**
> Please show the output from** ls -al **on the directory and at least 1 of the files.  The 'plex' userid must have at least read-access to media files.

Never forget that Linux/Unix are multiuser.

```
total 2915844drwxrwxrwx+  2 horvath horvath      4096 jan   20 11:18 .
drwxr-xr-x  15 horvath horvath      4096 jan   21 14:39 ..
-rwxrw----   1 horvath deluge  523927367 jan   20 11:15 The.Night.Manager.S01E01                                                                                        .720p.BluRay.x264.ShAaNiG.mkv
-rwxrw----   1 horvath deluge  471347453 jan   20 11:17 The.Night.Manager.S01E02                                                                                        .720p.BluRay.x264.ShAaNiG.mkv
-rwxrw----   1 horvath deluge  497734184 jan   20 11:17 The.Night.Manager.S01E03                                                                                        .720p.BluRay.x264.ShAaNiG.mkv
-rwxrw----   1 horvath deluge  497458799 jan   20 11:17 The.Night.Manager.S01E04                                                                                        .720p.BluRay.x264.ShAaNiG.mkv
-rwxrw----   1 horvath deluge  497890591 jan   20 11:17 The.Night.Manager.S01E05                                                                                        .720p.BluRay.x264.ShAaNiG.mkv
-rwxrw----   1 horvath deluge  497415697 jan   20 11:17 The.Night.Manager.S01E06                                                                                        .720p.BluRay.x264.ShAaNiG.mkv


```
Hm... Might be a stupid question, but how do give permission to all new folders/files automatically for plex?

---

### Post by TheFu on 2019-01-21
TL;DR
```
chmod 664 file-globbing-pattern
chmod o+r Th*  # this is what I'd use

```

Spend 45 minutes working through any *Unix file/directory permissions tutorial*, then spend another 45 minutes with 3 new userid inside 3 different terminals with those userids in 2 different groups and play with every octal permissions mode to see what allows which sort of access.  Once you understand the Owner permissions, the group works the same and so does "other".  Until you see and understand the elegance this model of permissions provides, and something "clicks", you'll always have frustration with all non-Microsoft OSes.  Out of the main 10 OSes in the world today, only 1 doesn't use this permission model, Windows.  All the others do.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is the Ubuntu tutorial, but it applies for **all** Unix-like OSes.
Heed this advice:
> WARNING: Although it's been said, it's worth mentioning in context of a gotcha typo. Please note, Recursively deleting or chown-ing files are extremely dangerous. You will not be the first, nor the last, person to add one too many spaces into the command. 

So, there's the problem.
The solution is to learn about and understand Unix file and directory permissions.
If this is a Unix file system (not NTFS/FAT-whatever), then setting permissions is easy for the "owner", which is horvath in this case. I don't use deluge or BT, so I don't know exactly how that is working.  Also, the files seem to be missing important-to-many-programs extentions like mp4/mkv ... whatever.

Unix permissions are split into 4 groups (actually 4 bytes)
a) Directory (or not) some other permissions are stored in this byte too.
b) Owner (3 fields)
c) Group (3 fields)
d) Other (3 fields) any userid that isn't in the Group or the Owner  <--- this is important
For example:
```
drwxrwxr-x
```
What do we know about this.
a) is is a directory
b) Owner has read, write, and execute permissions
c) Group has read, write, and execute permissions
d) Other has read and execute permissions, but not write

It is common to see the rwx permissions in octal. This is because the permissions are stored in a 32-bit value.
```

Permission Modes

    Number   Ref    Octal Permission Representation
     ===     ===    ==================================
      0      ---    None
      1      --x    Execute 
      2      -w-    Write 
      3      -wx    Execute and write : 1 (execute) + 2 (write) = 3
      4      r--    Read 
      5      r-x    Read and execute : 4 (read) + 1 (execute) = 5
      6      rw-    Read and write : 4 (read) + 2 (write) = 6
      7      rwx    All : 4 (read) + 2 (write) + 1 (execute) = 7
```

So looking at these permissions:```

drwxrwxrwx+  2 horvath horvath      4096 jan   20 11:18 .
-rwxrw----   1 horvath deluge  523927367 jan   20 11:15 The.Night.Manager.S01E01     
```
What we can see is that the 'plex' user and group don't have any permissions to read the files.  They would be in the "Other" permissions, which have no permissions, ---.
Also, the current permissions on the files is 760 in octal, which is seldom used.  Normally, we see 644, 640, 755, 750 permissions on files. If you want 'plex', in the "other" part of the permissions to have read access, leaving the other permissions alone, 
```
chmod o+r The*

```is the command I'd use. But really, I'd fix the permissions for all those files with
```
chmod 755 The*
```

The parent directory permissions have a role in what any specific userid or groupid can do on files inside it.  I'm unsure what the '+' in the last permissions means, sorry.  A quick look at the chmod manpage didn't give the answer either.  Anyway, of you want to force a specific groupid on all the directories and files under a certain level, then using the setgroupid bit would be how I did it.  The why that is set would be **chmod g+s **.  It only has effect when a file or directory is created, so after the file is created, setting it on the parent won't change any existing files or subdirectories.

To make all future TV shows store in the file system have the correct permissions, then the TV/ directory should have these permissions:
```
chmod 755
chmod g+s
```
You might want/need 775 in the first command. I don't know deluge.

The same would apply to all subdirectories, so you should manually modify all the existing directories with those commands. There is a shorter way using directory specific 'find' with a single 'chmod', but that is dangerous for someone who doesn't understand permissions and it can easily break the permissions for all the files touched.  Using 'find' in this way is a good skill test. Once you can use find, then it is probably ok to use it in this way.  I say this as someone who used 'find' and deleted an entire OS on a 3-day old Solaris server long ago.  Be very careful and have backups of anything you can't afford to lose.

---

### Post by hgeri005 on 2019-01-21
It does have the extension (mkv), just copied weirdly. 

And wow... that is one extensive post. I really appreciate you taking the time to educate me on this matter. 

Thank you very much!

---

