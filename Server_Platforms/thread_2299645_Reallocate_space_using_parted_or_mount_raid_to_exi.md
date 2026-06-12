---
title: "Reallocate space using parted or mount raid to existing directory"
date: 2015-10-20
forum: Server Platforms
---

### Post by francesco-dalia27 on 2015-10-20
I'm running a Ubuntu server 14.04.3 LTS.


The partitioning has been created automatically and now I have a problem with root directory space. There is a raid `/dev/md3` with almost 2 TB free and a `/dev/root` mounted on `/` with 20 gb of which 1.2 gb free.


This is my configuration:


```


    # fdisk -l


    WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
    Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
    255 testine, 63 settori/tracce, 243201 cilindri, totale 3907029168 settori
    Unità = settori di 1 * 512 = 512 byte
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Identificativo disco: 0x00000000


    Dispositivo Boot      Start         End      Blocks   Id  System
    /dev/sda1               1  3907029167  1953514583+  ee  GPT


    WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.
    Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
    255 testine, 63 settori/tracce, 243201 cilindri, totale 3907029168 settori
    Unità = settori di 1 * 512 = 512 byte
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Identificativo disco: 0x00000000


    Dispositivo Boot      Start         End      Blocks   Id  System
    /dev/sdb1               1  3907029167  1953514583+  ee  GPT


    Disk /dev/md3: 1978.9 GB, 1978886193152 bytes
    2 testine, 4 settori/tracce, 483126512 cilindri, totale 3865012096 settori
    Unità = settori di 1 * 512 = 512 byte
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Identificativo disco: 0x00000000


    Il disco /dev/md3 non contiene una tabella delle partizioni valida


    Disk /dev/md2: 21.0 GB, 20970405888 bytes
    2 testine, 4 settori/tracce, 5119728 cilindri, totale 40957824 settori
    Unità = settori di 1 * 512 = 512 byte
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Identificativo disco: 0x00000000


    Il disco /dev/md2 non contiene una tabella delle partizioni valida


 
    # df -h
    File system     Dim. Usati Dispon. Uso% Montato su
    /dev/root        20G   17G    1,2G  94% /
    devtmpfs        7,9G  4,0K    7,9G   1% /dev
    none            4,0K     0    4,0K   0% /sys/fs/cgroup
    none            1,6G  792K    1,6G   1% /run
    none            5,0M     0    5,0M   0% /run/lock
    none            7,9G  4,0K    7,9G   1% /run/shm
    none            100M     0    100M   0% /run/user
    /dev/md3        1,8T  295M    1,7T   1% /home

``` 
So basically what I need to do is using the `/dev/md3` for `/dev/root` in order to use all the space available!


Please help me because I never used parted without gui and I don't want to make a mess. Obviously I don't want to lose all the data in `/dev/root` (while I don't care about `/dev/md3`).


**&#8203;EDIT:**


I don't know if I was on the right way, but I thought I could just change the mount point of `/dev/md3` . I unmounted it and mounted on `/` but with no luck. 
Here is my fstab:
```


    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    /dev/md2        /       ext4    errors=remount-    ro,relatime,usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0       0           1
    /dev/md3        /home   ext4    defaults,relatime       1       2
    /dev/sda4       swap    swap    defaults        0       0
    /dev/sdb4       swap    swap    defaults        0       0
    proc            /proc   proc    defaults                0       0
    sysfs           /sys    sysfs   defaults                0       0
    devtmpfs        /dev    devtmpfs        rw      0       0

```



Can I just change the mount point to `/` and reboot the server to make it working ? I mean to have all the space of `/dev/md3` on `/` ?

Thank you very much for your support!

---

### Post by darkod on 2015-10-20
Yes you can, but you have to copy the files too. Only changing the mount point is not enough because when the system is trying to load the OS it finds nothing if you don't copy the files too.

But it is very strange to see /dev/root mounted as /. Was it always like that? Usually you would have a partition like /dev/sda1 or a mdadm array like /dev/md0 mounted as /. But not /dev/root.

The fstab you posted has /dev/md2 as /, not /dev/root.

Lets clear that first because you need to know from where to copy files...

---

### Post by francesco-dalia27 on 2015-10-20
Yes you're right. In fact I tried to change the fstab and then mount -a to reload the fstab but without copying the files i couldn't reach any website. (the fstab showed is not entire, it contains more lines about the websites on /var/www/... ).

Anyway if you notice the df -h output there is /dev/root as file system mounted on / . How can I know exactly what is the truth ?

---

### Post by darkod on 2015-10-20
The 'df -h' should show you the currently mounted partitions/devices. You might have a conflict or a wrong entry in fstab (you said you didn't post all of it) which is really trying to mount /dev/root as /. But that's a conflict of its own because /dev/root are folders inside / and according to that entry it's mounting itself.

Why would fstab show more lines for /var/www/... You doung mount a bunch of folders separately. You can have a line in fstab for /var for example, but usually you don't create them with more depth (folder structure). In fact, if it is /var taking space you can move only /var to /dev/md3, you don't need to move the full /. But first take a good look in fstab to try and figure out why 'df -h' shows /dev/root mounted as /.

Also, if you expect to need to control partition sizes in the future too, you can consider using LVM. That gives you an option to extend logical volumes and keeping the data (if you have free space).

---

### Post by francesco-dalia27 on 2015-10-20
Yes you're right about LVM, but unfortunately I didn't set up the server and partitioning the first time. Anyway I'll post the whole /etc/fstab . I'm using ISPConfig latest version and configured the server following their 'perfect guide'.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/md2        /       ext4    errors=remount-ro,relatime,usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0       0       1
/dev/md3        /home   ext4    defaults,relatime       1       2
/dev/sda4       swap    swap    defaults        0       0
/dev/sdb4       swap    swap    defaults        0       0
proc            /proc   proc    defaults                0       0
sysfs           /sys    sysfs   defaults                0       0
devtmpfs        /dev    devtmpfs        rw      0       0
/var/log/ispconfig/httpd/xxx.it /var/www/clients/client0/web1/log    none    bind,nobootwait,_netdev    0 0
/var/log/ispconfig/httpd/xxx.org /var/www/clients/client0/web5/log    none    bind,nobootwait,_netdev    0 0
/var/log/ispconfig/httpd/xxx.org /var/www/clients/client0/web7/log    none    bind,nobootwait,_netdev    0 0
/var/log/ispconfig/httpd/xxx.it /var/www/clients/client0/web8/log    none    bind,nobootwait,_netdev    0 0
/var/log/ispconfig/httpd/xxx.it /var/www/clients/client1/web9/log    none    bind,nobootwait,_netdev    0 0
/var/log/ispconfig/httpd/xxx.it /var/www/clients/client3/web12/log    none    bind,nobootwait,_netdev    0 0
/var/log/ispconfig/httpd/xxx.it /var/www/clients/client4/web14/log    none    bind,nobootwait,_netdev    0 0
... more sites

```

Anyway I tried to move /var to /dev/md3 changing the second line in fstab in ```
/dev/md3        /var   ext4    defaults,relatime       1       2

``` but the websites weren't available anymore. If I find a way to 'copy' the content of /var , then change the fstab and then paste again the content of /var in the "new var" , do you think it will do the trick ? (even if /var is 15 gb so the only way I can do is to download to my pc and then upload again on the server since I haven't enough space on the server to copy the whole directory).

---

### Post by darkod on 2015-10-20
If you want to move only /var, not the whole /, you can do it while the OS is booted. For copying / you would have to use live mode for example.

Do you have anything in /home? I see /dev/md3 was used as /home. If you change it's use then those files will be gone and it might break something, if it depends on the files in /home.

And if you want to, you can introduce LVM which might help you in the future... Do you want LVM?

---

### Post by francesco-dalia27 on 2015-10-20
Yes for me can be ok only to move /var since is taking 80 % of space on / . 
/home is empty so I don't care of moving /dev/md3 .

So how can I accomplish this task ?

By the way, yes it would be nice to have lvm, the important thing is that I don't lose anything and i can't stop the server nor reboot it.

---

### Post by darkod on 2015-10-20
Well, before starting to work you need to decide about LVM. Because right now md3 is empty according to you and you don't care about little data on it. So the idea would be to use md3 for the LVM physical device. But you have to decide now.

After you move /var data to md3 you will have important data there and won't be able to delete it.

So, only moving /var to md3 or trying with LVM?

---

### Post by francesco-dalia27 on 2015-10-20
What do you suggest ? I'd prefer the easiest and faster way, but if you think that lvm is way much better even if it will take a bit longer, then let's proceed in that way.

---

### Post by darkod on 2015-10-20
Well, it does give more options for the future. You can even move / to the LVM in the future. On the other hand, moving /var to md3 should be enough too if you expect /var to be the biggest part of the system.

It would be much faster to move only /var. Creating the LVM is little more complex and time consuming.

The easiest and faster way is only moving /var to md3, with or without saving the /home data.

---

### Post by francesco-dalia27 on 2015-10-20
Ok so how can I do it without losing data ? 
I thought to do in this way:
- copy var content somewhere (download on my pc)
- change fstab setting /etc/md3 on /var
- copy var content in the new var (upload to the server from my pc)
- pray everything went good and the server works properly 

Am I right or I need to do something else ?

---

### Post by darkod on 2015-10-20
You can copy the var content to your PC as a backup... I was thinking something along these lines:
1. Stop the apache and other services that are using the var files.
2. Copy home content to your PC (much less to copy compared to var).
3. Unmount /home (/dev/md3).
4. Make temporary mount point for /dev/md3 and mount it there (for example /tmpmd3).
5. Move /var content to /tmpmd3. That should keep permissions and ownership intact.
6. Unmount /tmpmd3 and mount /dev/md3 as /var.
7. Copy back the home content to /home (this time home will be in a folder inside /).
8. Adjust fstab so that on next reboot /dev/md3 will be mounted to /var.
9. Start the services you stopped.

That should be it more or less. It would be nice if you could reboot the server too, to make sure it boots ok after the changes.

---

### Post by francesco-dalia27 on 2015-10-20
OK I'll try to do these steps even if I can't keep the server down for long.
Just a question: 
> [COLOR=#000000]5. Move /var content to /tmpmd3. That should keep permissions and ownership intact.[/COLOR]
[COLOR=#000000]6. Unmount /tmpmd3 and mount /dev/md3 as /var.[/COLOR]

Finally shouldn't I move the /tmpmd3 content back to /var ? and how can I do it if /tmpmd3 is not mounted ?

P.S.
My /home is empty so I can skip those steps regarding it , right ?

---

### Post by darkod on 2015-10-20
The /tmpmd3 will be used only as temporary mount point. After you move the data there, it will be in /dev/md3 as a device because that is what you had mounted at /tmpmd3. So, after you mount /dev/md3 at /var, all is good. Don't forget to make a difference between partitions/array devices and the mount points. Mount points are used by the OS but the data is physically on the partitions/arrays.

But you can't move data from /var to /var, that's why you need temp mount point and you mount /dev/md3 as /var.

Your /home seems to have some little data on it according to your df -h:
```
/dev/md3        1,8T  [COLOR=#ff0000]295M[/COLOR]    1,7T   1% /home
```

It might not be anything important for you, but still it might be better to copy it to the PC and later you can put it back. You will also need to delete it from /tmpmd3 before you start moving /var so that there is no confusion with the data that was there.

---

### Post by francesco-dalia27 on 2015-10-20
Ok you perfectly cleared all my doubts. And yes, you're right about home, but I assure you it's nothing important even if I'll backup it anyway.
I think I'm gonna do everything by tonight and let you know if it worked fine.

---

### Post by francesco-dalia27 on 2015-10-25
Since the problem was related to ISPConfig I asked directly on the support forum and they linked me this guide: [https://www.howtoforge.com/use_mount_bind_to_move_the_website_and_email_directory_of_a_ispconfig_server_to_a_new_location](https://www.howtoforge.com/use_mount_bind_to_move_the_website_and_email_directory_of_a_ispconfig_server_to_a_new_location) .

More or less is the same solution @darkod gave me, but with some differences. However everything went fine and now the server is working good again.

Thank you very much for your help anyway :)

---

