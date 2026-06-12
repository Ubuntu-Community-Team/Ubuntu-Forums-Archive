---
title: "[SOLVED] User specific mount points"
date: 2008-12-24
forum: Ubuntu Brainstorm
---

### Post by geekyhawkes on 2008-12-24
Hi guys n gals;

im fairly new to ubuntu but love the way it works.  The one thing i am really missing from a previous OS is the ability to specify user specific mount points.  My machine is used by several users and i wanted to be able to specify "My documents" style mount points from my nas for each user without cluttering all users desktops.  

Im not sure how large a change it would be, but i was thinking implementation similar to the fstab file, but that is only run when a certain user logs on (maybe fstab_username) or similar.  It could be run after the system fstab file so that all user mount points can still be specified in one place.  

Thanks (and merry Christmas);

Andy

---

### Post by smartboyathome on 2008-12-24
I think why it generally hasn't been done is because, besides HAL, there is not really a good way for users to mount a device without root privelages. And, if you think about it, thats a good thing, as if a program run under a user could mount a device without HAL (which has fine grained security), then they could erase that drive's contents.

---

### Post by geekyhawkes on 2008-12-27
Thats a good point, but i was thinking that the mounts could be setup by someone with root.  If you have a family using ubunutu it would be nice to mount each user directly to their documents on say a nas, and the user wouldnt really need to edit much.

---

### Post by rockin_goliath on 2008-12-30
could you be a little more specific? Your original post is a little difficult to understand. It sounds like you want the home folders of specific users to be on certain partitions, is that right? I'm pretty sure tools exist to accomplish what you want to do.

---

### Post by lensman3 on 2008-12-30
It is already available.  First make each unique user have his/her own logon name.  With the unique logon, each user has an individual mount point.  Under Linux it is generally under the /home directory.  If you wanted you could make individual partitions would be mounted under /home.  

Another options of mounting home directories would be using the "autofs" program/daemon.  On demand each home directory would be mounted as needed and then stay connected and eventually timeout when the person logs off.  Each home directory would have it's own "Desktop" and files.

You could setup "common" shared areas, like songs, movies.  All you would have to do is setup a "group" that the users would belong to.  Users can belong to multiple groups at one time.

I hope this helps.

---

### Post by geekyhawkes on 2009-01-01
Specifically what i am after doing is allowing each user (that has a specific username) to have their own mounted area of my nas.  If i could effect where the home directory is mounted (ie on my nas and not the local hard drive) then it would meet my needs.

---

### Post by bunty on 2009-01-06
you sound very confused. You dont mount anything "on a local drive" you mount the local drive (partition) into the tree somewhere.

If you could explain exactly what you are trying to achieve without such vagaries as "on my nas" I'm sure someone can tell you how to achieve it.

---

### Post by lswb on 2009-01-06
You can do this with permissions and links. Here is an outline of one way to do so. You can change the directory names I use in this example to whatever you want.

Lets say that your NAS is mounted as /data. Create a root-owned directory in data, lets call it users. Set the permissions on /data/users as rwxr-xr-x. Then in /data/users create a directory for each user on your system. These directories are chowned so they are owned by the user and (if desired for privacy of the users) are given permissions rwx------ For simplicity I'll use the username as the directory name.

For example, you have users tom, dick, and harry, the commands so far are something like this:

```

sudo mkdir /data/users
sudo chmod 755 users
cd /data/users

sudo mkdir tom dick harry
sudo chown tom:tom tom
sudo chown dick:dick dick
sudo chown harry:harry harry

sudo chmod 700 tom dick harry

```

Now in each users home directory, create a symbolic link to their directory on the nas. You can use any name you like, for this example lets call it storage

```

sudo ln -s /data/users/tom /home/tom/storage
sudo ln -s /data/users/dick /home/dick/storage
sudo ln -s /data/users/harry /home/harry/storage

```

chown the links to the respective owners if you like, so they can rename them, or the users can just create the links themselves using any name they like. If desired the link can be put on the desktop or anywhere else in the users home directory, and the user can have multiple links pointing to his/her directory on the NAS. For all normal purposes the links can be treated and will appear as a directory to the user but the actual physical location of the files will be on the NAS.

One possible caveat: When using the gui to drag & drop files in/out of the linked directories, copies will be made in the target directory and the original file will remain where it was. This can be a little confusing if you don't expect it. OTOH using "mv" on the cli works as expected. Also when files are deleted from the nas directory, they are really deleted; they won't be recoverable from Trash.

---

### Post by geekyhawkes on 2009-01-07
lswb thanks very much.  What you have described above is exactly what i am after!

---

