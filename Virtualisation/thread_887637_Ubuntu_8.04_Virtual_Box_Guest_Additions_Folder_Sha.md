---
title: "Ubuntu 8.04 Virtual Box Guest Additions Folder Sharing"
date: 2008-08-12
forum: Virtualisation
---

### Post by linuxfreak778 on 2008-08-12
I've Been trying to run Ubuntu as a guest in Win Xp. I installed the Guest additions which work great but, I can't get a shared folder mounted. I've been looking everywhere and i can't find help on how to mount it:confused:. please help me.:)

---

### Post by axel206 on 2008-08-12
Hey. Check [here]("http://www.my-guides.net/en/content/view/112/1/1/6/")

It should solve your question. :)

---

### Post by linuxfreak778 on 2008-08-12
Now it says /sbin/mount.vboxsf: mounting failed with the error: Protocol error   ???

---

### Post by axel206 on 2008-08-12
What is the name of the directory you have created for the shares to be mounted? It's the same as me? (/mnt/shared)

---

### Post by linuxfreak778 on 2008-08-12
Yes, /mnt/shared. that's what i did.

---

### Post by SRamsesIV on 2008-09-18
I was having the issue with vboxsf returning a protocol error and discovered that there is a problem if the share name is the same as a local file or directory.  The mount will fail with a protocol error.  Doing the same thing in another directory (i.e. one that doesn't have a node with the same name as the share), will work.

```

# ls -F
share/
# mount -t vboxsf share /mnt/share
/sbin/mount.vboxsf: mounting failed with the error: Protocol error
#
# cd ~
# ls -F
a_file  a_dir/
# mount -t vboxsf share /mnt/share
# ls -F /mnt/share
shared_file  shared_dir/
#

```

---

### Post by smsoftdev on 2009-01-04
1.First of all share a folder of the host operating system using the virtual box interface with a suitable sharename.
2. Open up a terminal
3. Create a directory wherever you want the shared folder and with whatever name you want using the mkdir command
4. Now use this command :

mount -t vboxsf sharename mountpoint

where sharename is the name you used for the folder in the virtual box interface and mountpoint is the location you want the folder to be shared( the directory which you created in the previous step).

--
smsoftdev
[http://smsoftdev-tutorials.blogspot.com/](http://smsoftdev-tutorials.blogspot.com/)

---

