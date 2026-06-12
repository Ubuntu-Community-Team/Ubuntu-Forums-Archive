---
title: "Can't remove read-only status"
date: 2012-04-07
forum: Server Platforms
---

### Post by JakeSteel on 2012-04-07
I just started up a server (11.10) yesterday using an old desktop from a friend, and moved some files over to it via FTP. Now I'm trying to get rid of those files, but when I try to remove them it says that they're read-only and thus, they can't.

So I tried using chmod to change the permissions, and was greeted by this:

chmod: changing permissions of '<filename>.sh': Read-only file system

When I check if it's now executable, the permissions haven't changed. Is there anything I can do to get rid of these files short of wiping the harddrive?

P.S: I'm also having issues installing java. I used the following command

```
sudo apt-get install openjdk-7-jre-headless
```

Which seems to work, as it begins reading package lists. But once it reaches 99% it just stops. What am I doing wrong?

P.S.S: I apologize if these are simple issues, I'm very new to this and trying to get some server experience.

---

### Post by iponeverything on 2012-04-07
You seem to be intentionally vague - 

where is the file located?


also look at a tail of the most recent apt log under /var/log/apt -- for possible clues on its hang.

---

### Post by skabople on 2012-04-07
Yeah live boot and run a FSCK. Or kernel parameter init=/bin/bash and at the command line run /sbin/fsck -Cfy

Or just su to root and FTW and just start deleting!

---

### Post by JakeSteel on 2012-04-07
The files are located in /home/rad423/Districtopia [SoP]

The two files I'm trying to delete are craftbukkit.jar and craftbukkit.sh (files for running a Minecraft server).

---

### Post by skabople on 2012-04-07
> **JakeSteel said:**
> The files are located in /home/rad423/Districtopia [SoP]

The two files I'm trying to delete are craftbukkit.jar and craftbukkit.sh (files for running a Minecraft server).

Ok do a 
```
ls -lah /home/rad423/Disteictopia[SOP]
```
And give the output

Also try creating a file with 
```
touch test
```

And output of that as well.

---

### Post by SeijiSensei on 2012-04-07
When you get the "read-only file system" error, it means that Linux has found errors in the filesystem and marked it read-only until they are fixed.  You can fix this problem by rebooting using the "recovery mode" kernel, then choosing the "root shell" option when offered.  At the "#" prompt enter these commands:

```

mount -o remount,rw -n /
touch /forcefsck
shutdown -r now

```

Don't do anything else to the system until it reboots.  It will run a filesystem check at startup and should now enable you to delete those pesky files.

---

### Post by JakeSteel on 2012-04-07
Well I wish I would've seen your advice earlier, but after some fiddling around, what I thought was an endless loop, and then just manually restarting, those files are gone! HUZZAH!

Now I'm trying to install Java, which is going nowhere. It's at "Reading package lists..." and has sat at 0% for a good while now.

---

### Post by skabople on 2012-04-07
Is the server resolving names correctly? Like can you ping [www.google.com?](www.google.com?)

---

### Post by JakeSteel on 2012-04-07
Not a clue, but it did start making progress. It's currently resting on the line "Fetched 79.9 MB in 1min 46s (748 KB/s)", but I'll give it the benefit of the doubt and assume it is still doing something, just taking a while.

---

### Post by skabople on 2012-04-07
Any update?

---

