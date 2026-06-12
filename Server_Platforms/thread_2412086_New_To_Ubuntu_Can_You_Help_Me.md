---
title: "New To Ubuntu Can You Help Me?"
date: 2019-02-07
forum: Server Platforms
---

### Post by creekwaterx on 2019-02-07
Hi, new to Ubuntu and was having an issue. Sorry if I am in the wrong place. 

I am trying to get MineOS on my Ubuntu server but for some I seem to be stuck on step 1 of a cooking recipe style instructions lol. 
Instructions are [https://minecraft.codeemo.com/mineoswiki/index.php?title=MineOS-node_(apt-get%2Bsystemd)](https://minecraft.codeemo.com/mineoswiki/index.php?title=MineOS-node_(apt-get%2Bsystemd))  and on step one it says to enter 
```
curl -sL https://deb.nodesource.com/setup_8.x | bash -

```
 as root. So I added sudo to the beginning but it returns 
```
## Installing the NodeSource Node.js 8.x LTS Carbon repo...


## Populating apt-get cache...

+ apt-get update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
Error executing command, exiting


```
Why is it saying permission denied if it was run as sudo? Again I apologize for my iggnorance and appreciate any help.

---

### Post by yetimon_64 on 2019-02-07
> **creekwaterx said:**
> ...
Why is it saying permission denied if it was run as sudo?...

Note the error output...
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied) 
```
... would suggest to me that you may have had another package manager application open at the same time you were trying to install with the terminal.

You can only have one application accessing those apt files eg. if you are installing with terminal and have software centre or synaptic package manager or any other apt accessing installer open that would be the likely error output.

Ensure all other package managers / software installer programs are shut down before you run that command in the terminal. If the command you are using can't set the apt file lock then all further processes it tries to do will fail as well.

**Edit:** see next post, more likely the case, that is something I missed.

---

### Post by dmnur on 2019-02-08
When you do this, you're applying **sudo** only to **curl**:
```
sudo curl -sL https://deb.nodesource.com/setup_8.x | bash -
```

What you actually need to do in this case is:
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo bash -
```
Because it's **bash** that needs root rights.

---

### Post by howefield on 2019-02-10
Moved to the "*Server Platforms*" forum.

---

