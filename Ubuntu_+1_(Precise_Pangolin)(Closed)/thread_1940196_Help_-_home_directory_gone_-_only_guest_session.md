---
title: "Help - home directory gone - only guest session"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Fictitious1 on 2012-03-13
Ok,

I just installed a new SSD and 12.04 LTS - have a 2TB drive I wanted to use as the home directory.  Followed the directions for moving home directory - but here's the kicker -- I did not know everything would not start without home being mounted --- 

My second 2TB drive is a truecrypt mounted volume - ie it only mounts when I log in in this case - How do I go about 1 either undoing the home directory change ? ie reverting to the backup of etc/fstab so that it goes back to normal?  Or how can you make it so that you can have a home directory in a Truecrypt volume?

---

### Post by Bucky Ball on 2012-03-13
Couple of points: 12.04 LTS is pre-release and still testing. Expect breakages. Consequently this thread should be in the Ubuntu +1 (precise pangolin) forum. I have asked mods to move it. 

In the partitioning section of the installation you should have chosen 'Something Else' and put your /home partition where you wanted it then. Much easier. Not much use now of course but if you've just installed would be worth starting again and doing just that.

You say you followed the directions for moving your home folder but have not given a link to what directions those were ...

---

### Post by howefield on 2012-03-13
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by Fictitious1 on 2012-03-14
I was able to fix it.  -  I was able to get the Live CD to boot (Daily Build) - and by renaming the old_home back to home I fixed the problem.

I used this guide to try it, but it does not take into consideration truecrypt volumes, so do not use it if you are trying to move home directory to a truecrypt volume.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


sudo mount /dev/sdc1(or your drive) /mnt gksu gedit /mnt/etc/fstab

mv old_home home


I had not deleted the old_home directory obviously because I could not restart into the desktop to do it (thankfully) so just by renaming it back it fixed the problem.  I will look for another solution for mounting truecrypt volumes on start and using that volume as a /home directory.

---

### Post by Bucky Ball on 2012-03-14
Cool. Could you please mark thread as solved to help others and repost with the other issue. Cheers. ;)

---

