---
title: "Automount NAS on boot does not work, manually it does (19.10)"
date: 2019-12-08
forum: Server Platforms
---

### Post by helionism on 2019-12-08
Hi, 

I have a synology drive I mount in /etc/fstab

```
//<ip>/share    /home/tom/Documents/hardeschijf    cifs    username=<user>,password=<pass>,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=tom,forceuid,vers=2.0   0   0
```

On boot the mount does not work. In dmesg is see.
```
[   10.108231] CIFS VFS: Error connecting to socket. Aborting operation.
[   10.108234] CIFS VFS: cifs_mount failed w/return code = -2
```

But when I do sudo mount -a, the drive gets mounted as I expect it.

Can somebody point me in the right direction. Let me know if you if you need more info.

---

### Post by Morbius1 on 2019-12-08
The usual culprit in this situation is timing. The mount expression in fstab is being executed before the network stack is fully operational in Ubuntu so it fails.

One way out of this is to use a systemd automount but you will have to make a change to your mount point to make absolutely sure it works:

[1] Make a new mount point at [highlight]/mnt/hardeschijf[/highlight]

[2] Then unmount the share if it is already mounted: 
```
sudo umount /home/tom/Documents/hardeschijf
```
[3] Then change your fstab declaration to this by adding [highlight]noauto,x-systemd.automount[/highlight]
```
//<ip>/share /mnt/hardeschijf cifs username=<user>,password=<pass>,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=tom,forceuid,vers=2.0,noauto,x-systemd.automount   0   0
```
[4] Then do the systemd 2-step to make sure it's happy:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

Now access /mnt/hardeschijfcifs to make sure everything is there.

A systemd automount works by mounting the share **on access **not on boot or at login. It sounds weird but in practice it's all seamless to the user. Access the mount point and the system will mount the share automatically.

Note: It may work with your original mount point but there is an issue with how the system handles mount points in home directories and under /media. If you notice anytime a mount point is placed there in fstab an icon appears in the side panel of your file manager. Because its "actionable" it makes the automounter think it's being accessed and triggers the mount. That means it will mount at login which may still be too early in the boot process.

---

### Post by hk42 on 2019-12-08
Nice explanation even if I don't have immediate use for it .
Thanks Morbius1

---

### Post by TheFu on 2019-12-08
Would adding the _netdev option to the mount options not solve this too?  That tells mount programs to delay attempt until after the network is up.  From the mount manpage:
```
       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).
```

So, just add it here with the other options.
```
 ... ,_netdev,iocharset=utf8,file_mode=0777,dir_mode=0777, ...
```

I've never used the systemd mount stuff, so it might not work.  Systemd sometimes ignores well understood, well-used, prior settings for reasons only that team understands.

---

### Post by Morbius1 on 2019-12-08
> **hk42 said:**
> Nice explanation even if I don't have immediate use for it .
Thanks Morbius1
If you are going to keep this as a reference until you have a use case there is one more thing you can do and that is to have it automatically unmount when not used. You would do that with another option: [highlight]x-systemd.idle-timeout[/highlight]

So for example if you add  [highlight]x-systemd.idle-timeout=10[/highlight] then the system will unmount the share after 10 seconds of non use.

One way or another we all use systemd - like it or not. Anytime you add something to fstab something called [COLOR=#0000cd]**systemd-fstab-generator **[/COLOR][COLOR=#000000]automatically converts that entry into an applicable systemd unit file. The x-systemd series allows the user more control over the process without having to create the unit file manually.

[/COLOR]

---

### Post by TheFu on 2019-12-08
systemd-fstab-generator - thanks for that pointer.  
That manpage lists a number of things handled differently than the old method for the same parameters.

**autofs** doesn't seem to be impacted. Like to use it for NFS mounts that aren't there always.

Is there a ghost option for the systemd-fstab-generator that works similar to autofs?

---

### Post by helionism on 2019-12-08
Tnx for the help.

I used the suggestion made by [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144") and it worked.

---

### Post by Morbius1 on 2019-12-08
Great!

As per the "ghost" question. I just created an entry in fstab for a new system I'm working on:

//simian.local/public /mnt/SimianPublic cifs guest,noauto,x-systemd.automount,uid=1000 0 0 

> tester@vub2004beta:~$ ls -al /mnt
total 8
drwxr-xr-x  2 root root 4096 Nov 15 02:32 .
drwxr-xr-x 25 root root 4096 Dec  3 11:21 ..

tester@vub2004beta:~$ sudo systemctl daemon-reload
tester@vub2004beta:~$ sudo systemctl restart remote-fs.target
tester@vub2004beta:~$ ls -al /mnt
total 8
drwxr-xr-x  3 root root 4096 Dec  8 13:29 .
drwxr-xr-x 25 root root 4096 Dec  3 11:21 ..
drwxr-xr-x  2 root root    0 Dec  8 13:29 SimianPublic

tester@vub2004beta:~$ touch /mnt/SimianPublic
tester@vub2004beta:~$ ls -al /mnt
total 8
drwxr-xr-x  3 root   root 4096 Dec  8 13:29 .
drwxr-xr-x 25 root   root 4096 Dec  3 11:21 ..
drwxr-xr-x  2 tester root    0 Dec  8 13:48 SimianPublic

systemd will create the mount point automatically if it is not present.

---

### Post by TheFu on 2019-12-08
Thanks.  I'll need to test it here.  ghost option in amd/autofs shows the directory even when the mount hasn't happened.  

Some GUI programs need that to access the storage, assuming a snap isn't blocking access - for our protection.

---

### Post by Morbius1 on 2019-12-08
You didn't read my post. The share wasn't mounted when I did my second "ls -al /mnt" yet the mount point was there. It's owned by root at that point.

When accessed ( touch ) ownership changed to tester ( third "ls -al /mnt" ) as per fstab.

---

### Post by TheFu on 2019-12-09
Not reading is different from not understanding something subtle. 
I missed the subtle result from the  **touch**. Had to get to an appointment. Life gets in the way sometimes and I do need to test out the systemd-mount method with NFS.

If it works fully as expected, it will be an improvement, except where the fstab columns mean something different. I need to study and ponder that a little more. Today, I'm not certain those things matter at all, but I've learned that usually the prior Unix guys had very good reasons for doing something a specific way.

---

### Post by Morbius1 on 2019-12-09
> **helionism said:**
> Tnx for the help.

I used the suggestion made by [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144") and it worked.
I don't know if you will ever come back to the forums but if you could go to the top of this page select **Thread Tools** and then select **Mark this tread as solved **it will be of benefit to others who search for a resolution to this problem.

---

### Post by slickymaster on 2019-12-09
*Thread moved to **Server Platforms**.*

---

