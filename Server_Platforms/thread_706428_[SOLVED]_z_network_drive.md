---
title: "[SOLVED] z: network drive"
date: 2008-02-24
forum: Server Platforms
---

### Post by ttallos on 2008-02-24
I want to create a link to another machine what is the CLI syntax for this

net use  z: \\server\share

this dosent work with the new server

---

### Post by astrotech226 on 2008-02-24
You probably need to install smbfs first:
```

sudo apt-get install smbfs
```

You can then mount the remote "windows" share locally with the mount command.  Create a mount point somewhere:

```
sudo mkdir /mnt/myshare
```

Then mount it:
```

mount -t smbfs -o username=<your_user>,password=<your_password> //server/share /mnt/myshare
```

---

### Post by gameplayer2011 on 2008-02-24
When I try to mount it is says only root users can do that.
What does that mean and how do I fix it?




I was also wanted to do this but I don't know how to access it from my computer.

How can you access it from a windows computer?

---

### Post by astrotech226 on 2008-02-24
> **gameplayer2011 said:**
> When I try to mount it is says only root users can do that.
What does that mean and how do I fix it?

I was also wanted to do this but I don't know how to access it from my computer.

How can you access it from a windows computer?

Sorry about that.  Just put "sudo" in front of it.  That will elevate your privileges to root and allow it.
```

sudo mount -t smbfs -o username=<your_user>,password=<your_password> //server/share /mnt/myshare
```

Accessing your Linux from Windows is a little more complicated.  You need to set up Samba and then a share.  I can explain how to do it from the command line and config files.  Maybe someone else here in the forums can help with a GUI method of doing it.

---

