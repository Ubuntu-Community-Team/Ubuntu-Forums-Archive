---
title: "NFS Server + Mounted sub-dir = Stale Client"
date: 2008-10-26
forum: Server Platforms
---

### Post by pppZero on 2008-10-26
Forgive me if this makes no sense, but its why I'm having a problem :)

The problem on the client is:
```
lucas@stampy:/home/Public$ cd Media
bash: cd: Media: Stale NFS file handle
```

/home Public is exported from ford:/home/Public, as per /etc/exports:
```
/home/Public 192.168.0.75(crossmnt,rw,no_root_squash,async,no_subtree_check)
```

On the server, disks are mounted like so: (trimmed for brevity)
```

/dev/hdb3 /
/dev/sda1 /home/Public
/dev/hdc1 /home/Public/Media

```

ford is the server, stampy(192.168.0.75) is the client. 

Just about every google result i've seen are for mounts turning stale of their own accord, or just not working, but as long as i stay out of /home/Public/Media, the nfs share works fine, its just trying to get into the next mount on the server where the wheels fall off.

As a side note, when I was mounting the same setup with samaba, it worked fine, but people looked at me like a lunatic for using samba between two linux boxen :o

---

