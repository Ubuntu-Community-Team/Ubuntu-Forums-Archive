---
title: "Help File System Is Full /dev/sda1"
date: 2008-12-12
forum: Server Platforms
---

### Post by stock1232 on 2008-12-12
Here is the output for df -h
drew@ubuntudevelopmentserver:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             293G  282G     0 100% /
varrun                248M  268K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   92K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
overflow              1.0M  104K  920K  11% /tmp

I really dont have a clue what is using 282G of disk space. I used disk usage  analyzer to try and see but still nothing. The analyzer says that usr is 72% of the space and under usr directory the share and lib folders are the fullest? Any ideas? I am desperate as I can not save or download anything.

---

### Post by cariboo on 2008-12-12
To remove the archived package files in a terminal run:

```
sudo apt-get clean
```

to remove unused dependencie run:

```
sudo apt-get autoclean
```

I would suggest checking you home directory for any large files that you have downloaded. Try this in a termianl to see which directory is using up the most harddrive space:

```
du -cksh * | sort -rn |head -11
```

for more info on du, check:

```
man du
```

Jim

---

### Post by CrucifiedEgo on 2008-12-12
my usual way of narrowing down disk usage is:
```
cd /
du -h --max-depth=1
```
This shows the usage for each of the root folders.  Then find the biggest one, cd into it, and run the du again.  repeat until you find the culprit.

---

