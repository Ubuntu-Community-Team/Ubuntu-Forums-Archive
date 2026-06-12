---
title: "Cannot copy a file to secondary hard disk"
date: 2009-10-30
forum: Security
---

### Post by badaveil on 2009-10-30
[img]http://lh3.ggpht.com/_yJ5Rhn3UxL4/SumFPxrWa6I/AAAAAAAACVo/on2Uy6IqfxY/s800/Screenshot.png[/img]
I had just successfully formatted my secondary hard disk using the Partition Editor but after that I found that I could not copy a file or folder to that hard disk although it was mounted.
[img]http://lh5.ggpht.com/_yJ5Rhn3UxL4/Supat71HZxI/AAAAAAAACWE/DEl2DY2Zn3A/s800/Screenshot.png[/img]
Someone recommended "sudo nautilus" so I tried it and got the following message:

badaveil@pc:~$ sudo nautilus
[sudo] password for badaveil: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nautilus:8828): WARNING **: Unable to add monitor: Operation not supported

Any advice?

---

### Post by badaveil on 2009-10-30
Today, I have just upgraded to from Ubuntu 9.04 to Ubuntu 9.10. The upgrade was clean and successful. Following that, login-ed as an administrator, I decided to format the secondary hard disk Things I found out:

1. The format was effective. It is now possible to copy and paste files and folder to the secondary hard disk. That solves a bug of Ver 9.04. 
2. It is now possible to rename the hard disk (which I did too).
3. Upon reboot, login-ed as administrator and the secondary hard disk auto-mounts. Everything is as I wanted it to be. copy and paste possible. no hiccups  
4. Login-ed as user and the headache comes back... the secondary hard disk is missing in sight neither under the main menu/places/computer. I generally login as a user, only as an administrator when I need to update patch-files so hoping for some advice from any whizkid how to make visible the secondary hard disk.

---

### Post by cariboo on 2009-10-31
Can you manually mount the drive?

Open a terminal and type:

```
sudo fdisk -l
```

Note the device lablel of the drive eg: /dev/sdb1

then in the same terminal:

```
sudo mkdir /media/second
```

you can name the directory anything you want, for this example I'll use second:

```
sudo mount /dev/sdb1 /media/second
```

your second disk should now be mounted. To make it permanent, edit fstab to mount it on boot. 

There are so many different ways to mount a disk using fstab, that you should look at this [howto]("https://help.ubuntu.com/community/Fstab").

I think part of the problem is logging in as root, some config file that should be in your home directory is ending up in /root

---

### Post by badaveil on 2009-10-31
[IMG]http://lh3.ggpht.com/_yJ5Rhn3UxL4/Sux2ajCkK2I/AAAAAAAACYY/UoXGKs0Io-0/s800/Screenshot-2.png[/IMG]

Since I upgraded to Ver 9.10, when I login as user, whilst the secondary HD does not auto-mount which is not serious since it can be found under places, I am perplexed in that after a valid authentication as in pix, the secondary HD disappears.

When I login as administrator all is well.

---

### Post by QLee on 2009-11-01
[QUOTE=badaveil]

When I login as administrator all is well.[/QUOTE]

Just to be sure I understand you correctly, does that statement mean you logged in as root or as user with admin rights?

If the answer is root, what changes did you make to your system to allow this?

---

### Post by badaveil on 2009-11-02
Well guys, 

Thanks for all your help but I have to get on with my work so I thought real hard and then made the decision to delete the use of a user and now I login-in only as an administrator. I've lost my patience on this one.](*,)

---

