---
title: "Compare directory between different disk on different PC thorugh ssh"
date: 2017-01-01
forum: Server Platforms
---

### Post by sed_faster on 2017-01-01
Hello folks,

I am trying compare two fodlers in different disk. The diskone was a pc and another disktwo was on another pc!
I tried this command on pc with diskone:
```

diff /path/to/file/in/diskone user@192.175.5.6:/path/to/file/in/disktwo

```

This command don't result. Return something like "no such file or directory". After googled I can understand which it is impossible ran this command just like this between different pc's!
How should I set this software or googled about this subject matter to can do this? I read about a solution wiht software "sync". But I don't know if the best software to do this job!

thanks

---

### Post by volkswagner on 2017-01-01
Depending on what you'd like to compare you can use rsync as in [this thread]("http://stackoverflow.com/questions/19396718/compare-files-in-two-directory-on-remote-server-using-unix") (with the -c switch for compare).

If rsync is not the answer you'll have to mount the remote directory with NFS or SAMBA.

---

### Post by sed_faster on 2017-01-01
After mirror two disk I intend compare, just in case, all files and directory! If the dis it was in the same machine I use the software diff. 
I don't know if sync it is the best option to this job, because I don't know anything about this software. 

I imagine I should change "server2" to ssh user@ip on this command 
```

rsync -n -avrc /abc/home/sample1/* server2:/abc/home/sample2/

```

right?
thanks

---

### Post by SeijiSensei on 2017-01-01
Rsync will connect via SSH as the user running the program.  The most reliable method to ensure full coverage is to run the command as root.  However that's a bit harder with Ubuntu.  The easiest solution is to create an SSH keypair for root with sudo on one machine and export the public key to the other machine.  You'll find many documents online to help with this task.

Rsync is the best and easiest to use software for creating or managing snapshot backups of files and directories.  I use it every day to back up my remote servers to an external drive in my home office.

---

### Post by sed_faster on 2017-01-01
I execute this command:
```

sudo rsync -n -avrc user@192.138.14.745:/media/user/diskone/ /media/disktwo/folder/

```
and I return this report:
```

receiving incremental file list
git/fg.git/objects/pack/
git/fg.git/objects/pack/pack-4e8244618d82b7a8a9a3b520e57b1c5adae62135.idx
git/fg.git/objects/pack/pack-4e8244618d82b7a8a9a3b520e57b1c5adae62135.pack
git/fg.git/refs/heads/
git/fg.git/refs/heads/master

sent 3,041 bytes  received 1,069,251 bytes  948.51 bytes/sec
total size is 13,551,200,408  speedup is 12,637.60 (DRY RUN)

```
What this is means?

---

