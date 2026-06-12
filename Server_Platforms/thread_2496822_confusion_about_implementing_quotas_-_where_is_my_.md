---
title: "confusion about implementing quotas - where is my error?"
date: 2024-04-14
forum: Server Platforms
---

### Post by drakenstein on 2024-04-14
Hello good gents
I am asking for your help, searching the web didn't solved my problem or i am being a bit dense.
To the problem at hand.
On a Ubuntu server 22.04 i have to implement the quotas for the users. One detail of importance: the server has a mount point called /data and users have their /home on /data/home. So in the fstab a certain disk partition is mounted at /data.
There is no /home mount point, nor can i add one.
What I did was: 
```
apt install quota

```
And added then usrquota and grpquota in /etc/fstab and unmount and remount the /data, all ok.
Then 
```

sudo quotacheck -ugm /data
sudo modprobe quota_v1 -S 5.15.0-89-generic
sudo modprobe quota_v2 -S 5.15.0-89-generic
sudo quotaon -v /data

```

Where my confusion starts.
I can't enable quotaon -v /data/home, nor /home. - Mountpoint(or device) not found or has no quota enabled.
Now, When i succesfully activated quotas on /data, two files were created.aquota.group and aquota.user.

Q:
If i simply move those two files, will allow /data/home to be seen as valid point?
If the quota is enabled on /data, i can simply edquota for a user and will automagically understand that the quota is applied to /data/home/myuser?

So i am stuck here, for the moment and i am asking fot your help. Kinldy point me to the right dirrection.
Thank you in advance,
Rob

---

### Post by drakenstein on 2024-04-14
What i already tried:
checked the files in /etc/mtab.
found /data with aforementioned files. 

tried to execute
```

 quotackeck -cug /data/home 

```
Same error as above.

---

