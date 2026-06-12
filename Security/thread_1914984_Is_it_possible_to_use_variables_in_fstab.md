---
title: "Is it possible to use variables in fstab?"
date: 2012-01-25
forum: Security
---

### Post by tanoloco on 2012-01-25
I would like to add a line like this in fstab

```
/media/data/USERNAME/to-be-mounted	mountingpoint	none	bind
```

Everything is going right if I put my name in place of USERNAME.
But how to use a variable instead, in order it to be the name of the logged current user.

Thanks

---

### Post by Cheesemill on 2012-01-25
This isn't possible.

The fstab file gets processed during start-up before any users are logged on so there is no way of knowing what USERNAME should correspond to.

---

### Post by Grenage on 2012-01-25
I assume you could have a mount script later in the boot process (after the user has been identified).

---

### Post by tanoloco on 2012-01-25
Thanks for your replies.
Yes .. I thought about a mounting script on boot, but I need sudo to mount .. so the user will see a popup on boot asking to retype password for admin tasks I guess (and the user must be a sudoer) .. is there a way to avoid all this? All I want to do is to auto mount some folders on boot depending on username

---

### Post by gsgleason on 2012-01-25
automounts via autofs support this type of functionality.

---

### Post by tanoloco on 2012-01-25
I'm glad to hear about that! :)
Can you also give me a short example please?

---

### Post by tanoloco on 2012-01-25
It seems to me that automount won't help me in my goal. Instead I tested that a boot script has root privileges, (thank you Grenage) so it can come helpful.

Now I'm try to write such a script, the routine as you might know is to create a bash script named foo in /etc/init.d/ and then run```
sudo update-rc.d foo defaults
```

Easy up here.
The problem is: how to get the username of the user just logged-in?

I'm using a test script like
```

#! /bin/sh
# /etc/init.d/blah

touch /var/lock/blah
username=$(id -n -u)
touch /var/lock/${username}

exit 0

```

The result is that two files are created on /var/lock: blah and root!

If I logged-in with user 'john' how can I get this info?

Thanks

---

### Post by Cheesemill on 2012-01-25
```
whoami
```

---

### Post by oldfred on 2012-01-25
I auto edit fstab on a new install, but do have to have sudo. 

```
# make mount points for other partitions
echo $USER
mkdir /mnt/cdrive
#mkdir /mnt/backup

# windows shared NTFS
mkdir /mnt/shared
chown $USER:$USER /mnt/shared
chmod 777 /mnt/shared
mkdir /mnt/data
chown $USER:$USER /mnt/data
chmod 777 /mnt/data
#The big "X" will also not make files executable unless they were executable to begin with.Morbius1
#sudo chmod -R a+rwX /mnt/data

# edit fstab to add mounts, UUIDs of data partitions do not change
cp /etc/fstab /etc/fstab.backup
#Edit fstab first Need to change from UUID to labels, so it works on both portable & DT
str1="# Entry for /dev/sdc6 :"
str2="UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2  "
str3="# Entry for /dev/sda1 :"
str4="UUID=04B05B70B05B6768                      /mnt/cdrive           ntfs-3g  ro   0  0  "
str5="# Entry for /dev/sdc2 :"
str6="UUID=44332FD360AA9657                      /mnt/shared  ntfs-3g   defaults,uid=1000,nls=utf8,windows_names   0  0  "
fname=/etc/fstab
echo $str1 >> $fname
echo $str2 >> $fname
echo $str3 >> $fname
echo $str4 >> $fname
echo $str5 >> $fname
echo $str6 >> $fname
# Verify no errors in fstab & remount with new mounts
mount -a

```

---

### Post by tanoloco on 2012-01-26
whoami leads to the same result :(

---

### Post by Cheesemill on 2012-01-26
You could maybe parse the output of
```
who -q
```
with some sort of awk trickery.

---

