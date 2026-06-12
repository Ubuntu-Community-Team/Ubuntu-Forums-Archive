---
title: "CIFS: Can't create file because exists, cannot see/delete it because it doesn't"
date: 2021-02-13
forum: Server Platforms
---

### Post by bubukind2 on 2021-02-13
Hi all,

Feels funny to be back here. Been mostly lurking for the last ~15 years and judging by my SSO username it seems like at some point my old one got lost... :razz:
I'm having some trouble with a server that seems to be lying to me. Or rather I think it is confused. :D
In a nutshell, this is my problem:

```

root@muchmuch ~ # cd ~syncthinger/.config
root@muchmuch /home/syncthinger/.config # ls -a
.  ..
root@muchmuch /home/syncthinger/.config # mkdir syncthing
mkdir: cannot create directory ‘syncthing’: File exists
root@muchmuch /home/syncthinger/.config # rm -r syncthing
rm: cannot remove 'syncthing': No such file or directory

```

For context: 
I've been running this Ubuntu VPS for a few years now, and it started out with 16.04.
Yesterday I dragged it to 18.04, then 20.04, and overall the upgrades went butter smooth.[SUP]1[/SUP]
This VPS mounts a CIFS drive to extend the storage for my syncthing install, and it is this network drive that I seem to be having trouble with.

Syncthing has (had? I can't find the docs I went with at the time...) a bit of a special requirement that the database/indexes can't live on a network drive. I only found that out when the local storage ran out, and I had started all my shares in the ~syncthinger folder.
The *data* can live on CIFS without problem though. So my solution was to keep the contents of ~syncthinger/.config/syncthing on the local drive (it's small anyhow) and bind-mount them into their expected location.
Now I cannot bind-mount this anymore, because the folder doesn't exist, but I also cannot create it because it does exist. Kind of a Schroedinger's folder type of situation.

Things I've tried:

    1. Reboot (multiple times for the upgrades, and a few times after that)
    2. Nuke the whole .config folder via rm -rf. Didn't work, folder can't be removed because it isn't considered empty.
    3. Enable the CIFS debugging via ```
echo 3 > /proc/fs/cifs/cifsFYI
``` and watched with dmesg -w as I tried to do the steps shown above, but the output really just reflects what the commands already say:

```

[34344.005454] Status code returned 0xc0000034 STATUS_OBJECT_NAME_NOT_FOUND
[34344.009907] Status code returned 0xc0000035 STATUS_OBJECT

```

4. One thing that *may* be important: two prefixes of this CIFS  are mounted in two different places, to serve different storage needs:

```

root@muchmuch ~ # mount | grep cifs
//cifs-box/backup/camera  on /mnt/backup/camera type cifs  (rw,relatime,vers=3.1.1,cache=strict,username=<username>,uid=1004,forceuid,gid=1003,forcegid,addr=<ipv6-addr>,file_mode=0660,dir_mode=0770,soft,nounix,serverino,mapposix,rsize=4194304,wsize=4194304,bsize=1048576,echo_interval=60,actimeo=1)
//cifs-box/backup/syncthinger_home  on /home/syncthinger type cifs  (rw,relatime,vers=3.1.1,cache=none,username=<username>,uid=1000,forceuid,gid=1000,forcegid,addr=<ipv6-addr>,file_mode=0660,dir_mode=0770,soft,nounix,serverino,mapposix,rsize=4194304,wsize=4194304,bsize=1048576,echo_interval=60,actimeo=1)

```

I have unmounted the other mount for the time being to see if that helps. It doesn't.

So now I'm wondering if this is an issue with my cifs config, or what I  can do about this. The CIFS host is a paid-for service (hetzner hosting)  that I can't administer, so debugging server-side would mean talking to  them. Before I do that I'd just want to make sure it's not a problem on  my side (which... I find much much more probable, given that I don't  make my money setting up cifs, and they do :razz: )

Are there any further debugging steps I could take? Google et al. have been supremely un-useful here, all results seem to be related to not being able to delete a file that *does* exist...
Also, if there is a simple way to make this work more cleanly, avoiding the whole bind-mount stuff and such, I'm all ears. 

Thanks for reading all my rambling, stay safe everyone :)

[SUP]1[/SUP]The only hiccup was [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1874272") which was annoying because I wanted to go to bed, but not so bad. :P

---

### Post by howefield on 2021-02-13
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by bubukind2 on 2021-02-13
Damn, thanks @howefield. Seems I deserve that newbie userid after all :D

Found the thread where I got the info that CIFS is a no-no for the syncthing db; [https://forum.syncthing.net/t/solved-invalid-argument-is-another-instance-of-syncthing-running/12715](https://forum.syncthing.net/t/solved-invalid-argument-is-another-instance-of-syncthing-running/12715)
Not sure it's still current state of affairs though.

---

### Post by LHammonds on 2021-02-14
I know you are root but I still have to wonder if this is a permission issue.  Check the permissions on the folder(s) you are in:

```
ls -la /home
ls -la /home/syncthinger
ls -la /home/syncthinger/.config

```

Try making any other folder/file under the .config folder and parent folder:

```

mkdir /home/syncthinger/testme1
mkdir /home/syncthinger/.config/testme2
```

LHammonds

---

### Post by bubukind2 on 2021-02-15
Thanks for reading. I also thought about permissions issues, mostly because that's what google spits out (and I have encountered before) for the inverse case of not being able to modify files that *do* exist.

```

# ls -la /home
total 52
drwxr-xr-x 14 root        root        4096 Sep 10  2019 .
drwxr-xr-x 22 root        root        4096 Feb 13 01:06 ..
[...]
drwxrwx---  2 syncthinger syncthinger    0 Feb 13 09:56 syncthinger
drwx------  3 syncthinger syncthinger 4096 Feb 13 09:55 syncthinger_syncthingconfig
[...]

# ls -la /home/syncthinger
total 71
drwxrwx---  2 syncthinger syncthinger    0 Feb 15 08:26 .
drwxr-xr-x 14 root        root        4096 Sep 10  2019 ..
[...]
drwxrwx---  2 syncthinger syncthinger    0 Feb 15 08:26 .config
[...]

# ls -la /home/syncthinger/.config
total 0
drwxrwx--- 2 syncthinger syncthinger 0 Feb 13 10:13 .
drwxrwx--- 2 syncthinger syncthinger 0 Feb 13 09:56 ..

```

Both the mkdir commands execute just fine. It really seems to be that one folder that's "burned".

---

### Post by LHammonds on 2021-02-15
It is all owned by the user syncthinger and group syncthinger.  Switch into that user and see if you still have issues modifying the file.

```
su syncthinger
```

LHammonds

---

### Post by bubukind2 on 2021-02-16
I mean... I *was* root already. And evidently I tried that before. But I just tried again, and computer still says no... :confused:

---

### Post by LHammonds on 2021-02-16
The only other thing I can think of is that some process has a lock on it or thinks it has a lock.

In  those scenarios (even on Windows) you could rename the file/folder,  reboot and then you can remove the renamed file/folder.  But that does  not address the initial problem of "something" holding onto it...but it  does help identify the problem.

Due to power problems I cannot access my work computers to try various commands to help you.  Having trouble even staying connected to post this reply. lol

LHammonds

---

### Post by The Cog on 2021-02-16
I think I may have seen something similar when there was confusion about the spelling of a filename - upper/lower case. E.g. on a filesystem that confuses upper and lower case letters, file "foo" may exist, and therefore prevent you creating "Foo" because it already exists. But you can't delete "Foo" because it doesn't exist (only "foo" does). I sometimes wonder if Windows thinks "&#925;&#919;&#937;&#916;" and "&#957;&#951;&#969;&#948;"are the same filename.

---

