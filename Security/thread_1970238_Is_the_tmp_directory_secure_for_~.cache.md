---
title: "Is the /tmp directory secure for ~/.cache?"
date: 2012-04-30
forum: Security
---

### Post by mabo5184 on 2012-04-30
Hi,
 
I have a SSD, so to reduce wear I created a tmpfs in ram for /tmp and I moved my ~/.cache folder to /tmp and created a symbolic link.
 
I was just wondering if there are any seurity concerns in doing this.
 
The computer is a single user desktop setup, so I think in my situation there is no concerns ...

---

### Post by Hungry Man on 2012-04-30
There are probably potential security issues with this.

I suggest you use chmod to set the folder to noexecute.

---

### Post by mabo5184 on 2012-05-01
My fstab file has this entry;
 
[FONT=Courier New]*tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0*[/FONT]
 
So I expect this should have the same effect as chmod?

---

### Post by pqwoerituytrueiwoq on 2012-05-01
keep in mind you will need to recreate the folder in /tmp for your cache at every boot i suggest using /etc/rc.local for this task
like this should work nicely and be secure enough
```
mkdir /tmp/mabo-cache
chown mabo:mabo /tmp/mabo-cache
chmod go-rwx /tmp/mabo-cache
```

---

### Post by mabo5184 on 2012-05-01
Actually, yes your right, I had problems when I created .cache in /tmp, because it's obvious to me now that it disappears after each reboot, so I just created a link between .cache to /tmp, so all the files and folders are just created in /temp rather then /temp/.cache ...
 
Seems to be working ok, but was wondering if there are any security concerns ....

---

### Post by pqwoerituytrueiwoq on 2012-05-01
like that would very likely have issues but if you use the rc.local file with those 3 lines you should be secure and have /tmp cleaner

---

### Post by Hungry Man on 2012-05-01
When a program executes it's loaded into RAM. RAM is your executable space. By moving files into your RAM you are moving them into space that would normally be executable. Because having all RAM executable would be horribly insecure some smart guys invented NX.

I don't know a lot about how Linux handles it let alone how the ramdisks handle it, but the big concern here is that you're loading files into an area of your machine that wants to execute. Blocking execution pretty much solves this.

---

### Post by movieman on 2012-05-02
As suggested up above, I wrote an rc.local script which goes through all the users in /home and creates a set of directories in /tmp for cache, etc, which only have permission for that user. Then each user's home directory links to the relevant directory in there.

It's worked fine so far.

---

