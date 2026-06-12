---
title: "Wish to automatically mount a cifs/SMB share ..."
date: 2015-04-26
forum: Server Platforms
---

### Post by Simplyred37 on 2015-04-26
Hi all, I've been using Ubuntu for a few years, but never really had to run scripts or edit fstab.

I want to have my NAS (smb://netgear/media/) to be automatically mounted and available to applications, after I reboot or log in.
What what I have read, this can be done by editing the mount entries in the /etc/fstabfile, or by running a script.

Not being an expert, I would like to know the pros and cons of each approach.
I have located a script (auto-mount.sh) which can be found at [https://gist.github.com/6390561](https://gist.github.com/6390561)
I believe that [COLOR=#333333][FONT=Consolas]SHARE should be : [/FONT][/COLOR]SHARE=smb://netgear/media/[COLOR=#333333][FONT=Consolas]
[/FONT][/COLOR]But don't know what MOUNT_POINT should be ...
Also, don't know what I should do with DOMAIN=example.com
Since I am a home user and not on a corporate network/domain, (like at work), should I comment that line ?
Also, the NAS does not require me to provide credentials so my assumption would be that USERNAME and PASSWORD should be commented out ?

Told you I was a noob!
However, I much prefer asking questions and guidance than to edit a bunch critical files and messing up my system ....

Looking forward for your suggestions !!!

Many thanks in advance !!!

dan.....

---

### Post by matt_symes on 2015-04-26
Thread moved to **Server Platforms**.

You may get an answer here.

---

### Post by volkswagner on 2015-04-26
I never used a script to mount, so I can't offer much input here. I can think
of possible benefits to the script like if your network connection is not available
early enough, fstab may fail to mount. The script may be easier to set "when" to run.

The mount point is a directory. Linux mounts partitions at a folder/directory.
Example when installing the operating system you can have on large partition mounted a /
or several partitions mounted in various locations /, /var, /usr, /home, /var/log, /etc, etc....

Some people like to create folders inside of /mnt to desginate an area for user added partitions.

The domain can translate to your workgroup name.

What type of data will you be using for the server? This may sway some decisions on the mount command.
But you likely will want to have control from your logged in user so you may want to mount it with
the user switch.

You can run some tests via command line before finalizing anything (to see how it functions compared to how you'd like it to behave).

```

sudo mkdir /mnt/nas
sudo mount -t cifs //netgear/media/ /mnt/nas -o username=user1,password=secret,domain=workgroup umask=0022,gid=1000,uid=1000
```

Since you don't have user/password you may have to experiment. Depending on the server (or nas device) it may assume user=nobody.

The uid and gid will give user 1000 access. User 1000 is the first human user in ubuntu. To find your actual user id chck /etc/passwd.

```
sudo cat /etc/passwd
```
Look for your username.

---

### Post by darkod on 2015-04-27
You can use scripts if you want to, but the usual way would be to make an entry in /etc/fstab and do it like that. If //netgear can be found by name in the network, you can use it like that. Otherwise you have to use its IP, like //192.168.1.10 for example. The options used in the fstab entry are usually _netdev,guest. The first one tells it that the device is on the network, so it will not try to mount it before the network is running, and the second one that no username and password are necessary.

You can mount it at any empty folder you have created, like /data, /smb, /share etc.

Give that a try in fstab and see how it goes and whether it works as expected:
```
//192.168.1.x/media   /share   cifs   _netdev,guest   0   0
```

---

### Post by electronico_nc on 2015-04-28
I would really recommend to use [autoFS]("https://help.ubuntu.com/community/Autofs") as it gets rid of cases the remote server is not available.
Nicolas

---

