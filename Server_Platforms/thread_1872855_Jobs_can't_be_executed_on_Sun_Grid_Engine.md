---
title: "Jobs can't be executed on Sun Grid Engine"
date: 2011-10-31
forum: Server Platforms
---

### Post by toontu on 2011-10-31
Hi,

I am very new to SGE. I installed it from Ubuntu repository. I have one master host and two execution hosts. All are sumbit hosts. I configured the hosts and users through qmon. Also, the simplest parallel environment. Both execution hosts can be viewed through qmon on the master host.

However, I am having a rather strange problem --

After a job is submitted, the master host will assign it to an execution host. Then, the job will search for the files and directories required to run itself on the EXECUTION host rather than the submit host, which obviously will result in the error of "No such file or directory". When the job is a really simple one such as displaying date, there will be no error but the output file will be left on the execution host rather than the submit host.

I suspect it might be something wrong with how the cluster is configured. But I don't have a clue where is wrong.

Any suggestion/lead is welcome. Cheers!!

---

### Post by cj13579 on 2011-10-31
> **toontu said:**
> the job will search for the files and directories required to run itself on the EXECUTION host rather than the submit host, which obviously will result in the error of "No such file or directory".

This is normal in a grid environment. You need a shared, common file system across all of the nodes in your Grid. If you are just playing and not doing anything mega I/O heavy then NFS would be fine.

HTH.

---

### Post by toontu on 2011-10-31
Many thanks, Chris. TH. I will post back the result. :-)

---

### Post by toontu on 2011-11-01
Hi Chris and others,

I now have a new problem about NFS.

My home directory is encrypted and the directory I want to share is in there. After I modified the /etc/exports file and restart nfs-kernel-server, I got this error:

exportfs: /home/uname/dir does not support NFS export

I tried the same procedure on an unencrypted Ubuntu 10.10 (desktop) machine. Everything is fine. So how do I work out this problem? Disable encryption? Or use another common shared file system?

Many thanks.

---

### Post by cj13579 on 2011-11-01
> **toontu said:**
> exportfs: /home/uname/dir does not support NFS export


There seems to be a couple of threads on this. Some give up and go down the route of samba or setting the share up from elsewhere on the box. Others say to abandon nfs-kernel-server and go for unfs3 instead as it (apparently) handles encrypted stuff better.

Having said the Ubuntu page on NFS [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) suggests that you should only difficulties at boot time and mounting automatically.

I guess the choice is up to you :)

---

### Post by toontu on 2011-11-01
Many thanks, Chris. The choice is truly up to me. :-)

I will probably remove the encryption completely. Although the solution on the Ubuntu page on NFS sounds simple, it does raise another issue. Because it proposes to have a folder under the root directory, every time I write to it, I need to prefix sudo, which I don't think is practical for client machines.

Hope you think this makes sense.

---

### Post by cj13579 on 2011-11-01
I don't think you need to do that. You should be able to do something like:

```
ln -s /home/user/gridstuff /opt/grid
sudo echo "/opt/grid 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)" >> /etc/exports
sudo exportfs -ra
sudo service nfs-kernel-server restart

```

If that doesn't work move all your grid stuff to /opt/grid and make that a share. And give it perms so that everyone can do what they need to with it (avoid 777 if you can)

```
sudo mkdir /opt/grid
cp -pr /home/user/grid/stuff /opt/grid
sudo echo "/opt/grid 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)" >> /etc/exports
sudo exportfs -ra
sudo service nfs-kernel-server restart
```

You'll probs need to tinker with the perms. You may also need to look at making the UIDs and the GIDs the same across the boxes. But either of those should do the trick :s

Mount on the client:

```
sudo mount <master.ip>:/opt/grid /opt/grid
```

You want to keep the paths the same across the nodes so that you can always reference your files easily.

HTH

---

### Post by toontu on 2011-11-01
Many thanks for the suggestions.

I think I have tried the first option. But will have another go tomorrow. Finger crossed.

About the second one. I have some hard-coded code installed in my home directory, which will not work at any other locations. Moving the code will be like reinstalling the whole package. If that's what I have to do, I will probably do that on one of the execution node where the home directory of the same user isn't encrypted. This is the last but easy option.

Good night.

---

### Post by toontu on 2011-11-02
Latest update: No luck about the first option. So have removed the encryption. Everything is fine now.

Chris, many thanks for the discussion. Much appreciated.

---

