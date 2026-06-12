---
title: "OS boots into Emergency mode - fsck says its clean"
date: 2017-04-27
forum: Server Platforms
---

### Post by user630702 on 2017-04-27
[COLOR=#111111][FONT=Ubuntu]So I have multipath setup and it seems like if I enable multipath partition in fstab, then everytime the reboots, it goes into emergency mode.

If I disable that in fstab, then server reboots fine.

I ran fsck.ocfs2 /dev/mapper/mpatha-part1 and it says it is clean.

    ```
cat /etc/fstab | grep mpath
    /dev/mapper/mpatha-part1 /mnt/test ocfs2 defaults 0 0 
```

On the console, It shows
    > Started LSB: Load O2CB cluster services at system boot..
    Starting LSB: Mount OCFS2 volume at boot

    Welcome to emergency mode: type journalctl -xb
In journalctl I saw it stated:
    > mount[1077]: mount.cfs2: Unable to access cluster service while trying initialize cluster
    systemd[1]: mnt-origin.mount: Mount process exited, code=exited status=1
    systemd[1]: Failed to mount /mnt/test.
But after I login to Emergency mode, I see that /mnt/test has mounted successfully.
Any suggestions on what to look for next?


[/FONT][/COLOR]

---

### Post by joedkoop on 2017-04-28
Side note: I've never heard of ocfs2. (I Googled it and, yes, it is a thing. Now I know!)

I would replace "ocfs2" in your fstab file with "auto" and see if that helps.
And I don't bother putting "defaults 0 0" at the end either.

Good luck!

---

