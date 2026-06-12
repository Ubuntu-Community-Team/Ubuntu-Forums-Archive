---
title: "Problem of free space"
date: 2018-12-28
forum: Server Platforms
---

### Post by mtyrop on 2018-12-28
Hi,

I have an ubuntu server (16.04_LTS-server 64B) and I have a problem when I try to install a new package, I have this error :
```
E: You don't have enough free space in /var/cache/apt/archives/.
```

I already tried :
```
apt-get clean
apt-get auto-clean
apt-get autoremove
```

But I always have the same problem.

Command df - h :
```
Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  650M  5.7G  11% /run
/dev/md1         20G   20G     0 100% /
tmpfs            32G     0   32G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/md0        282M   54M  209M  21% /boot
/dev/md2        449G   70M  426G   1% /data
tmpfs           6.3G     0  6.3G   0% /run/user/1000
```

As you can see, dev/md1 is full but I didn't found any heavy file/directory.
The system is configured in Raid 5 (if my memory is good).

Do you have any idea ?

Thanks

---

### Post by zorlax on 2018-12-28
I've never configured them myself but could there be a swapfile that has eaten all the space? No temp or logfiles out of control?

I might remember this incorrectly but if the fs is really full you might need to remove something manually before the automated tools will work properly.

---

### Post by Impavidus on 2018-12-29
20GB isn't huge for a root partition, but should be enough on most systems. You have to find out what is using that space.```
sudo du -xh --max-depth=1 / | sort -hr
```
BTW, I see you have a huge data partition that's almost empty. That's slightly peculiar.

---

### Post by spjackson on 2018-12-29
Users' home folder(s) are also on /dev/md1 which have the potential to eat significantly into 20GB.

---

### Post by mtyrop on 2018-12-30
Thank you all for your answers

```
sudo du -xh --max-depth=1 / | sort -hr
20G    /
18G    /root
821M    /usr
431M    /var
411M    /lib
166M    /home
13M    /bin
8.0M    /sbin
4.7M    /etc
972K    /tmp
16K    /lost+found
4.0K    /srv
4.0K    /opt
4.0K    /mnt
4.0K    /media
4.0K    /lib64
```

So the folder 'root' eats all the space, is there anything to do (I'm not at all familiar with Linux)?
About the empty partition, maybe it's related to the RAID mount (not me who installed it) ?

---

### Post by CatKiller on 2018-12-30
> **mtyrop said:**
> So the folder 'root' eats all the space

That is not good.

/root is root's home folder. In normal usage it should be essentially empty. The fact that it's filling up suggests that things have been run as root that really shouldn't be.

---

### Post by Impavidus on 2018-12-30
For comparison, this is what I get:```
$ sudo du -xh --max-depth=1 / | sort -hr
9,8G    /
6,5G    /usr
2,2G    /var
793M    /lib
183M    /opt
140M    /boot
14M    /etc
13M    /bin
12M    /sbin
480K    /root
84K    /tmp
16K    /lost+found
8,0K    /snap
8,0K    /media
4,0K    /srv
4,0K    /mnt
4,0K    /lib64
4,0K    /cdrom

```This is on a laptop, not a server, which explains some of the differences. You have a very lean system, but that /root should be much smaller. Go digging there and find what you can remove.```
sudo du -xh --max-depth=1 /root | sort -hr
```

I was worrying that maybe data that should have ended up on the /data partition had ended up on the root partition, hidden underneath the mountpoint, but that appears not to be the case.

---

### Post by mtyrop on 2019-01-01
Hi all,

I wish you an happy new year :P

Command sudo du -xh --max-depth=1 /root | sort -hr
```
18G    /root/.pm2
18G    /root
9.2M    /root/.npm
4.0K    /root/.nano
```

Command sudo du -xh --max-depth=1 /root/.pm2 | sort -hr
```
18G    /root/.pm2
14G    /root/.pm2/logs
4.0K    /root/.pm2/pids
```

The folder (or file ?) logs is huge, that's normal ? Possibility to clean or delete it ?

---

### Post by CatKiller on 2019-01-01
> **mtyrop said:**
> that's normal ? 
Most people don't run PM2. It's probably not a good idea to run it as root. Only you know what your server is for, and whether those logs are useful. You should look to put those logs somewhere else, at least.

---

### Post by Impavidus on 2019-01-01
Older logs are usually safe to delete. I don't know about pm2 though.

---

### Post by mtyrop on 2019-01-01
It's a NodeJS server.

```
root@sd-X:~/.pm2/logs# ls
server-error-0.log  server-error-1.log  server-out-0.log  server-out-1.log
```

There are 4 files, I should transfer them in /dev/md2 /data ?
```
Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  650M  5.7G  11% /run
/dev/md1         20G   20G     0 100% /
tmpfs            32G     0   32G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/md0        282M   54M  209M  21% /boot
/dev/md2        449G   70M  426G   1% /data
tmpfs           6.3G     0  6.3G   0% /run/user/1000
```

---

### Post by CatKiller on 2019-01-01
> **mtyrop said:**
> There are 4 files, I should transfer them in /dev/md2 /data ?


If you want to keep them, sure. There's probably also a way to make it put the logs there in the first place, so this doesn't happen again.

It's probably also likely that there's a way to run your process manager application as something other than root, which would be a good thing to investigate. Running things as root is generally a Bad Plan, since any vulnerability in that application can then do absolutely anything.

---

### Post by mtyrop on 2019-01-01
Thank you for your assistance ;)

---

### Post by howefield on 2019-01-01
Moved to the "*Server Platforms*" forum.

---

### Post by volkswagner on 2019-01-01
> **mtyrop said:**
> It's a NodeJS server.



There are 4 files, I should transfer them in /dev/md2 /data ?


As others have stated, running programs as root is a bad idea and not a best practice.

For some quick workarounds I would first truncate the largest log file to get some
free space on /.

Depending if you care about the contents of the log files, will determine your course of
action, but you'll likely need to truncate if you can't first copy them to /data.

Use ls -lh to get human readable size of the log files then pick one to truncate like:

```
sudo cat /dev/null > /root/.pm2/logs/server-out-1.log
```

Other workarounds:
You can stop node.js, move the log folder to someplace sane on /data then
symlink to it.

Again this symptom is not related to the bad practice of running the root user, but
the problem has now surfaced and you should heed the warnings :)

---

### Post by mtyrop on 2019-01-03
Thank for your advices :)

---

