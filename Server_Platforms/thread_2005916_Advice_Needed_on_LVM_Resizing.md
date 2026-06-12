---
title: "Advice Needed on LVM Resizing"
date: 2012-06-18
forum: Server Platforms
---

### Post by jlacroix on 2012-06-18
Hello everyone, I need a little help deciding the best way I should go about this.

I have a home server (named "Pluto") running Ubuntu 12.04 Server. This server has a 2TB software RAID and is basically a NAS (no display, keyboard or mouse) and handles backups of all my other Linux machines, and also handles copying video files to my other computer that runs Mythbuntu. Windows machines back up to this server too, which is why I use Samba. I access it via SSH and VNC, but I can plug a monitor into it if I need to. Everything works, but I decided to do sharing differently. 

Right now, I have a user named "iris" that contains all the shares. This user only houses the shares, and is not used for anything. I decided that I'm going to get rid of this user account, and make the shares "user-less", meaning that they aren't tied to a user (since the shares are to be accessible by everyone anyway).

I created a directory (/shares) to house all the shares. I configured Samba to point to it and it works, all my machines (Windows and Linux) can write to it. I thought all was well...

...Until I remembered that I only allocated about 30GB to the root partition. It won't house all my shared data (I have 1TB of data used on my machine, 95% of it is my shared data). I was initially thinking I was just going to backup the server, wipe it, and redo it. But I remembered something: I set it up to use LVM, so I should be able to resize to my hearts content, right?

So I can think of three possible (hypothetical) solutions:

1.) Make the root partition and /home not separate, but one big partition and retain the data. (Is this even possible?)

2.) Create a new LVM partition and mount it to /shares

3.) Just simply resize and give more space to root

To recap, my goal is to no longer have my shares in /home/iris but instead to have the shares in their own directory, preferably without losing data. I'll need to resize in order to do this, I just need opinions on perhaps the best way to go about it.

In the case of scenarios 2 and 3 above, I would probably need to be careful not to resize too much and lose data. (I have two current backups of everything, but copying a terrabyte takes ages).

Here is what my disk utilization looks like right now:
```
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/LVMVG-root   29G  2.3G   25G   9% /
udev                    992M  4.0K  992M   1% /dev
tmpfs                   401M  1.8M  399M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                   1001M     0 1001M   0% /run/shm
/dev/mapper/LVMVG-home  1.8T  1.1T  666G  61% /home
/dev/sdc1               1.8T 1009G  732G  58% /media/BackupHDD2

```

Here is my fstab if it matters:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/LVMVG-root /               ext3    errors=remount-ro 0       1
/dev/mapper/LVMVG-home /home           ext3    defaults        0       2
/dev/mapper/LVMVG-swap none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by darkod on 2012-06-18
All three option are more or less the same. And since you don't seem to have 1TiB free anywhere, so you can copy all data at once, and redo the layout, you will have to play bit by bit.

What you could do is:
1. Shrink the filesystem and then the LVMVG-home for 512GiB for example (you have sufficient free space for that).
2. Create the new LVMVG-share logical volume (or work with LVMVG-root if you choose so). Expand the LVMVG-share (or LVMVG-root depending what you decided) to take the whole 512GiB.
3. Move part of the data from LVMVG-home. After that frees the space, again shrink the FS and the LV for another 512GiB for example, or more.
4. Expand LVMVG-share (or LVMVG-root) to take the newly released space.
5. Move the rest of the data.
6. Shrink LVMVG-home again to the size you estimate you will need for the Home folder, since all the data will be on another location.
7. Expand LVMVG-share or LVMVG-root to take the maximum released space.

If you decided to move Home you would have to move the data to /home during the above operations, and then comment out the entry for LVMVG-home in /etc/fstab.

More or less that would be it.

Don't forget, before shrinking a LV you have to shrink the filesystem first.
After expanding a LV you have to expand the filesystem too so that it can use the new space allocated to the LV.

Personally I would go with a new LVMVG-share since it also creates a logical solution for the shared data. While the data is in Home it doesn't stand out as shared data for all, even though it will work in that case too.

You have more than one way to make it work. How you decide to do it depends on you.

---

### Post by jlacroix on 2012-06-19
> **darkod said:**
> All three option are more or less the same. And since you don't seem to have 1TiB free anywhere, so you can copy all data at once, and redo the layout, you will have to play bit by bit.

What you could do is:
1. Shrink the filesystem and then the LVMVG-home for 512GiB for example (you have sufficient free space for that).
2. Create the new LVMVG-share logical volume (or work with LVMVG-root if you choose so). Expand the LVMVG-share (or LVMVG-root depending what you decided) to take the whole 512GiB.
3. Move part of the data from LVMVG-home. After that frees the space, again shrink the FS and the LV for another 512GiB for example, or more.
4. Expand LVMVG-share (or LVMVG-root) to take the newly released space.
5. Move the rest of the data.
6. Shrink LVMVG-home again to the size you estimate you will need for the Home folder, since all the data will be on another location.
7. Expand LVMVG-share or LVMVG-root to take the maximum released space.

If you decided to move Home you would have to move the data to /home during the above operations, and then comment out the entry for LVMVG-home in /etc/fstab.

More or less that would be it.

Don't forget, before shrinking a LV you have to shrink the filesystem first.
After expanding a LV you have to expand the filesystem too so that it can use the new space allocated to the LV.

Personally I would go with a new LVMVG-share since it also creates a logical solution for the shared data. While the data is in Home it doesn't stand out as shared data for all, even though it will work in that case too.

You have more than one way to make it work. How you decide to do it depends on you.
Thank you so much for your response. I began working on it last night, and it seemed to go well. I resized home to end up with 100GB more than it had used, to make sure I didn't under-allocate. After I went through the steps I found on Google ([here]("http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/shrink.html")) to resize it, I was able to re-mount /home and it showed all my files, all seemed well. I decided to restart my server, and now I cannot get into it via SSH anymore, it says "connection: refused". (If you recall, it has no monitor plugged in).

I'm under the impression that it's not actually booting. I'm going to connect a monitor to it this evening and find out if there are any errors.

Correcting errors with LVM would be very beneficial to me, as I've never used LVM before, and I need my practice for my day job in case I ever have to enlarge partitions.

Wish me luck.

---

### Post by darkod on 2012-06-19
Hmmm, it should have continued working fine. Lets see what it says when you have a monitor on it.

You did shrink the filesystem before shrinking the logical volume, right? Did you touch /etc/fstab at all?

Did you decide to create a new LV or to expand the LVMVG-root?

---

### Post by jlacroix on 2012-06-19
> **darkod said:**
> Hmmm, it should have continued working fine. Lets see what it says when you have a monitor on it.

You did shrink the filesystem before shrinking the logical volume, right? Did you touch /etc/fstab at all?

Did you decide to create a new LV or to expand the LVMVG-root?
Yes, I shrank the filesystem first, and then the volume. I did not touch /etc/fstab. I decided to create a new LV, but I did not actually create the new LV yet, I was going to do that after the server came back up.

---

### Post by jlacroix on 2012-06-19
I connected a monitor and was able to see why it didn't finish booting. It's complaining about the filesystem size versus the physical size, and asks me to press F to manually run fsck to fix the errors.

I do that, and it says that serious errors were found. I then press "I" and it boots the rest of the way.

All the above errors reference /home.

However, I have to do this every time it boots.

---

### Post by jlacroix on 2012-06-20
Thanks for the help, I'm marking this solved, I'm going to just wipe and re-do the server. I spent a few hours last night tinkering with it, and figure I'm just wasting my time at this point. When I get back I'll just whack it and then restore from my most recent backup.

Thanks!

---

