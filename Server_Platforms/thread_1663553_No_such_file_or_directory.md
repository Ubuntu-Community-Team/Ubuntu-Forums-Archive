---
title: "No such file or directory"
date: 2011-01-09
forum: Server Platforms
---

### Post by ajcis55 on 2011-01-09
Hey all. Racking my brain trying to figure this out. Hoping for some help.

So, I've got a Ubuntu 10.04 Server edition installed as a VMWare ESXi VM. It's been working great for about 6 months. This morning, after not making any changes, I started seeing some errors. First problem was that my website (managed by apache2) was offline. SSH/ftp didn't work either. So I go through the console through vSphere. Tried a quick ifconfig, and I got this:
```
bash: /sbin/ifconfig: No such file or directory
```mmk. Tried ls /sbin/ifconfig, got this:
```
bash: /bin/ls: No such file or directory
```dir /sbin/ifconfig DOES work. PS also returns the 'no such file or directory' error.

Tried to ping 8.8.8.8:
```
connect: Network is unreachable
```My $PATH appears correct. I have rebooted as well as doing a complete shutdown/power up. No, I don't have a snapshot from last night (or anytime that recent) that I can revert to. I have tried running these commands as root and another sudo user.

Commands known to work: dir, vi, dmesg, rmdir, mkdir, ifup (but it then returns ifconfig not found), shutdown, reboot, fsck (but I chose no to prevent damage)
Commands known NOT to work: ifconfig, ps, ls

Anyone have any ideas? I'll be monitoring this thread pretty close for a few hours so I can provide any answers and try anything recommended pretty quickly.

---

### Post by sj1410 on 2011-01-10
something wired has happen to your server. do a 

updated

&

locate ifconfig

what does it say

---

### Post by ajcis55 on 2011-01-10
Updated is not a valid command?

locate ifconfig returns several locations, including /sbin/ifconfig, /usr/lib/libsh/.backup/ifconfig, and then 4 .gz files.

---

### Post by matt_symes on 2011-01-10
Hi

It should be 

```
sudo updatedb
locate ifconfig
```

You can also use

```
which ifconfig
```

Check your paths

```
echo $PATH
```

Kind regards

---

### Post by matt_symes on 2011-01-10
duplicate post

---

### Post by matt_symes on 2011-01-10
duplicate post

---

### Post by sj1410 on 2011-01-10
> **ajcis55 said:**
> Updated is not a valid command?

locate ifconfig returns several locations, including /sbin/ifconfig, /usr/lib/libsh/.backup/ifconfig, and then 4 .gz files.



oh its updatedb than rerun locate ifconfig

your results shows that ifconfig is present in /sbin/


try again after updatedb

---

### Post by ajcis55 on 2011-01-10
updatedb appeared to run correctly, without any notifications.

Ran locate ifconfig again and had the same result. which ifconfig also return /sbin/ifconfig.

Note that I am currently running commands as root (using sudo su).

---

### Post by sj1410 on 2011-01-10
> **ajcis55 said:**
> updatedb appeared to run correctly, without any notifications.

Ran locate ifconfig again and had the same result. which ifconfig also return /sbin/ifconfig.

Note that I am currently running commands as root (using sudo su).

lets reset the permission

```

chmod 777 /sbin/ifconfig

```

than run it

```

/sbin/ifconfig

```

---

### Post by sj1410 on 2011-01-10
> **ajcis55 said:**
> updatedb appeared to run correctly, without any notifications.

Ran locate ifconfig again and had the same result. which ifconfig also return /sbin/ifconfig.

Note that I am currently running commands as root (using sudo su).

lets reset the permission

```

chmod 777 /sbin/ifconfig

```

than run it

```

/sbin/ifconfig

```

---

### Post by sj1410 on 2011-01-10
> **ajcis55 said:**
> updatedb appeared to run correctly, without any notifications.

Ran locate ifconfig again and had the same result. which ifconfig also return /sbin/ifconfig.

Note that I am currently running commands as root (using sudo su).

lets reset the permission

```

chmod 777 /sbin/ifconfig

```

than run it

```

/sbin/ifconfig

```

---

### Post by sj1410 on 2011-01-10
> **ajcis55 said:**
> updatedb appeared to run correctly, without any notifications.

Ran locate ifconfig again and had the same result. which ifconfig also return /sbin/ifconfig.

Note that I am currently running commands as root (using sudo su).

lets reset the permission

```

chmod 777 /sbin/ifconfig

```

than run it

```

/sbin/ifconfig

```

---

### Post by ajcis55 on 2011-01-10
I get this:
```
chmod: changing permissions of '/sbin/ifconfig': operation not permitted
```

---

### Post by ajcis55 on 2011-01-10
I get this:
```
chmod: changing permissions of '/sbin/ifconfig': operation not permitted
```

---

### Post by sj1410 on 2011-01-10
than you are not root

```

sudo chmod 777 /sbin/ifconfig

```

---

### Post by ajcis55 on 2011-01-10
I can assure you that I have a # prompt, not $. I also just exited back to standard user and ran 
```
sudo chmod 777 /sbin/ifconfig
```
with the same result.

---

### Post by sj1410 on 2011-01-10
than you have a very bad system. everything seems ruined up. reboot your system and attach the following file

/var/log/dmesg

lets see what does it says

---

### Post by ajcis55 on 2011-01-10
This is a virtual machine running on vmware esxi. I don't have any good way of getting the dmesg file off of the machine as the internet is not working on it.

Just to make sure I stated it before, this system was working absolutely fine ~1am yesterday morning, and when I looked again at ~9am, it was trashed. Nothing had changed in that time frame, or really within a few weeks.

---

### Post by ajcis55 on 2011-01-10
This is a virtual machine running on vmware esxi. I don't have any good way of getting the dmesg file off of the machine as the internet is not working on it.

Just to make sure I stated it before, this system was working absolutely fine ~1am yesterday morning, and when I looked again at ~9am, it was trashed. Nothing had changed in that time frame, or really within a few weeks.


Also, I just tried to force a fsck (using shutdown -rF now) and this is what happened after reboot:
[IMG]http://i56.tinypic.com/14kz6kx.png[/IMG]

It didn't seem to run the fsck.

---

### Post by ajcis55 on 2011-01-10
This is a virtual machine running on vmware esxi. I don't have any good way of getting the dmesg file off of the machine as the internet is not working on it.

Just to make sure I stated it before, this system was working absolutely fine ~1am yesterday morning, and when I looked again at ~9am, it was trashed. Nothing had changed in that time frame, or really within a few weeks.


Also, I just tried to force a fsck (using shutdown -rF now) and this is what happened after reboot:
[IMG]http://i56.tinypic.com/14kz6kx.png[/IMG]

It didn't seem to run the fsck.

---

### Post by ajcis55 on 2011-01-10
This is a virtual machine running on vmware esxi. I don't have any good way of getting the dmesg file off of the machine as the internet is not working on it.

Just to make sure I stated it before, this system was working absolutely fine ~1am yesterday morning, and when I looked again at ~9am, it was trashed. Nothing had changed in that time frame, or really within a few weeks.


Also, I just tried to force a fsck (using shutdown -rF now) and this is what happened after reboot:
[IMG]http://i56.tinypic.com/14kz6kx.png[/IMG]

It didn't seem to run the fsck.

---

### Post by matt_symes on 2011-01-10
Hi

Try

```
sudo touch /forcefsck
```

to force the file system check.

Kind regards

---

### Post by chrislynch8 on 2011-01-10
Hate to be the bearer of bad news but this happened to me on a couple of servers about a year ago. I may have posted here, no sure. It affected the same commands on all servers.

ifconfig
ps
ls
top

I beleive it was permissions getting screwed up in an upgrade. I was unable to change the permissions of file as you have seen. I had to boot into the server using a live cd, rename /bin -> /bin_old /sbin -/sbin_old

Any directory that has a file not working and then copy in from a backup I had from the night before. Reboot the server and everything worked after that.

Rgds
Chris

---

### Post by ajcis55 on 2011-01-10
matt, I tried that as well with the same result.

chris, I don't have a backup, and I wasn't doing an upgrade. Is it possible to recover the files from the installation dvd? I do have an iso of that available to mount on the server.

---

### Post by ajcis55 on 2011-01-10
Sorry to bump, but this is a production server that I really, really need up and running asap. Any ideas?

---

### Post by koenn on 2011-01-10
run ls -l over /bin and /sbin and //look at the permissions and ownership// so that at least you know that that's where the problem is. (but it does sound like that is the case)

Yes, you can just copy programs/executable files and they'll probably work if the versions are more or less the same

This time, make a snapshot, so you can roll back if you manage to make things worse

Also, find out first if cp is an external program or a shell builtin, you're going to need it and if fails it because it's in /bin and /bin is being replaced, you'll have a problem


also, 
that idea to chmod 777 - it could have worked, but why would you blindly change permissions (and to a not very sane value at that) without even checking if permissions are the problem ?  (rule of thumb: if someone sugests "chmod 777" as a solution without explaining why chmod and why 777, he's a charlatan)


and lastly:
next time, make backups.
A production server and no recovery strategy ? Good job.

---

### Post by ajcis55 on 2011-01-10
ls doesn't work. I stated that in the first post. So I can't use that to check permissions. 

I've already made a snapshot now that things are broke.

Setting a single file to 777 didn't really bother me because console access is the ONLY access right now. It was something I hadn't tried, so I tried it. I try to avoid arguing with any help I can get.

I didn't have a backup that's that recent because the server runs an image host that gets several hundred image uploads to it per day. Simply restoring to a week ago wasn't a great option for me. I didn't say there is 'no' recovery option.

---

### Post by matt_symes on 2011-01-10
Hi

You should be able to check the permissions using a LiveCD or USB. Mount the partition and check that way.

Kind regards

---

### Post by koenn on 2011-01-10
> **ajcis55 said:**
> ls doesn't work. I stated that in the first post. So I can't use that to check permissions. 
ok, missed that (had my mind on the ifconfig thing)

so, see if you can replace ls with a good copy (eg from the install iso - I hope the commands you need to do that, still work). If that works, you know you might have a solution, and you can still look at permissions first (cause it could also be some other form of fs corruption)



> I didn't have a backup that's that recent because the server runs an image host that gets several hundred image uploads to it per day. Simply restoring to a week ago wasn't a great option for me. I didn't say there is 'no' recovery option. 
You have a problem with the system, not with the data. Do you have recovery options for the system, other than "try to repair it" ?

---

### Post by iiz on 2011-01-10
Hey, I was having similar issues. I couldn't locate files or run commands.

I su'ed to root same thing, sudo was a ditto.

I killed the shell and logged in directly as root. So the shell started as a root user and not as a regular use, everything worked. Still doesn't solve the real issue, but i'm able to access files and make changes.

-nick

---

### Post by ajcis55 on 2011-01-10
iiz, logging in as root didn't work for me.

koenn, I have created a new hdd and installed the same version of ubuntu (10.04) on it. I then mounted the old hard drive and tried to copy the files, receiving the same error.

My backup is a snapshot of the vm, which allows me to restore exactly as the system was at the given date and time. I unfortunately can not specifically restore just the system files, as opposed to the entire drive.

---

### Post by ajcis55 on 2011-01-10
ah. Just got some more info. /bin was deleted except for ls, ps, netstat. /sbin was deleted except for ifconfig. I copied files from the new install over to there. However, these offending files would not allow me to overwrite them. Trying to chown, chmod, rm, or mv these files returns an error operation not permitted. The current owner is shown as root:root, but when I look at it in webmin, I see owner is 112:114.

Really hope I'm getting somewhere here.

---

### Post by koenn on 2011-01-11
You probably have a serious case of fs corruption, in so much that the filysystem is no longer processing your commands to chmod, mv, rm, .... those files. 
(You did try all of that as root, didn't you ?)

at this point, I'd begin to seriously consider reinstalling. 

you could use that new install on the separate disk, and possibly reuse config files from the old system.

I'd suggest using a seperate disk (vmdk) for data ; just mount it somewhere suitable and copy the data.
Kind of an "in place" replacement of the disks. 

Having your system separate from the data helps for future recovery : with system trouble like this, reinstall ; for data problems, restore from a backup on a seperate system/tape/....

a snapshot of the vm is not sufficient backup. If you'd have your system and data on separate disks, and have snapshots of the vmdk's, that would help, but yopu can't do that with vmware snapshots alone, the filesystem under your hypervisor would have to do filesystem snapshots.

---

### Post by nothingtolose on 2012-07-11
Hi,  

I'm on trouble similar like you, last weak. But i fixed it. Below may help you to recovery it.


After restart my server, i can not connect to my server over network. :cry:

Login to console and check it.

# ifconfig

bash: /sbin/ifconfig: No such file or directory 
Hix, wtf (welcome to facebook :grin: ). What's the matter with my server ? :sad:

Let's try reboot it a gain. Hope it can run [-o<

After reboot, it still like that. :cry:

For long time to search internet to find out solution for this trouble but with no luck. :sad: :confused:

"No such file or directory", that mean system can not find that file or that file has been corrupted, i think that.
  
Why i don't refresh this file ?. But how to do that ??? :confused:. It's VMware machine and it has no network connection.
  
There are 2 way (may be more ) to do that:
  
1. Search for ifconfig backup file in my server and copy it to /sbin/
2. Copy ifconfig from another machine to /sbin/
  
Luckily come to me for the firt try. I found the backup of ifconfig in  /usr/lib/libsh/.backup/. I don't know how this file was there. After  copy and restart, network come up.
  
What's the matter if i don't found this file on backup?
  
With option 2, I connect to vsphare cline and Export this virtual server  to .ofv file and import it to vmware workstation running on my Desktop.
  
Copy ifconfig to usb and connect it to imported vmware and then copy to /sbin/.
  
Export it back to .ofv file and import to vmware ESX.
  
Option 2 take long time but it help you haven't to reinstall server and a thousand of software and package; a hundred of time to re-config configure file.
  
Hope this help you.
  
Br.

---

### Post by matt_symes on 2012-07-11
Old thread. Closed.

---

