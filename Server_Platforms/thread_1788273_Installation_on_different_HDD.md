---
title: "Installation on different HDD"
date: 2011-06-22
forum: Server Platforms
---

### Post by benzies on 2011-06-22
Hi There

Just playing around with some installations of Ubuntu Server 10.04.  I'd like to know an option(how to) to install software on a different HDD.

I've got two HDD's, one with 20GB (sda) the other with 100GB (sdb). 

#sudo apt-get install (software) -/media/sdb/(software)??

---

### Post by sanderd17 on 2011-06-22
The software always installs to the same directories, but you can mount your hdd to any directory you want.

take as example a program that installs to /usr/share/. You can set a hdd up so that /usr is on your sda, but /usr/share is on your sdb.

You can follow a tutorial about "creating a separate /home". [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Just replace /home by any directory that you want. Do note that it's a one-to-one relationship: one directory to one partition.

But I do warn you, if something goes wrong, you might need to install ubuntu again.

---

### Post by doas777 on 2011-06-22
well, thats not generally how it works in ubuntu, but there are ways to acheive approximatly what you are going for.

just move your /usr folder to the new drive, and map it to mount to /usr in your fstab.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

the unix/linux filesystem is standardized so that specific resources go in predictable places. it;s not good to mess with that order, but the arrangement of physical disks that any given folder exist on  is up to you, as long as you mount it to its predictable location.

---

### Post by benzies on 2011-06-23
*sigh* although Linux is a flexible OS, I seem to be getting stuck (or needing to perform complex tasks) to get what MS has simplified.

Maybe I'm using the wrong Linux OS, can anyone suggesting anything else?

I gave RHEL a go, but don't want to pay lol!

---

### Post by sanderd17 on 2011-06-23
Fedora is the community version of RHEL. But that won't matter.

If you need to install it on a custom location, you will need to build it from source.

What you also can do is working with symlinks. 
```

ln --help
man ln

```

---

### Post by benzies on 2011-06-23
Yeah I thought about links.  But maybe some sort of registry needs to be developed for the Linux OS?

Thing I'm hating about any community version of red hat (CentOS, Fedora) is they tend to lock up. :(

---

### Post by doas777 on 2011-06-23
thing is though, fedora or any other linux distro will not do what you want. that is simply not the way it works (and tbh, moving the progra~1 dir in windows is not exactly administration free as most apps don't use the environment variable when establishing their install path).

I understand what you are saying, but linux != windows, and you will have a much better experience if you try doing things the linux way. if you fight the os too much, you're gonna have a bad time.

---

### Post by benzies on 2011-06-24
Can you possible suggest a better way to setup my ideal environment?

Servers;

S1 = DNS, DHCP, Virtual Web (virtual addresses apache), SSH Server (single connection to connect to other servers via ssh)
S2 = Storage (with FTP && quota)
S3 = SQL
S4 = Web/Application

I've managed to get a lot of it working.  Still playing around with NFS... Is Ubuntu server the best choice?  It's been my fav so far as it hasn't locked up.  Not once!

Whats an ideal root HDD size (20gb might not be enough)?  Should I be mapping /home to the main storage (as in sdb) HDD? :twisted:

---

### Post by sanderd17 on 2011-06-24
Ubuntu isn't really a server distro, but it works if you are a beginner in server things. If you want to set something up from the bottom, you might need to go to a distro like CentOS. That's a lot more work to set up, but you control every detail of it.

For the root size, I always have 12 GB for root on my desktop, and I've never been above 8GB. I guess with the servers you install, you might go a little higher, but 20GB is certainly enough.

If you install websites on it, you should also see if they are in the root or not.

---

### Post by Gyokuro on 2011-06-24
The linux distribution is not the problem, you can go with RHEL, SuSE, or Ubuntu and can achieve below mentioned goals with every distribution. You can move the NFS service for example on your S2. Concerning your space problem: you can mount space hungry directories to different drives; e.g. /var, /home, /tmp, ... - plenty of documentation of such a task can find via goolge or it's already in the forum: [http://ubuntuforums.org/showthread.php?t=250104](http://ubuntuforums.org/showthread.php?t=250104)

BTW: 2 x 100GB is more reliable (RAID)

HTH

---

