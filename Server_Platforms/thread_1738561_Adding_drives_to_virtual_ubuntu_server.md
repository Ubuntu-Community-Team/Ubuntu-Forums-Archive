---
title: "Adding drives to virtual ubuntu server"
date: 2011-04-24
forum: Server Platforms
---

### Post by ChasHutch on 2011-04-24
I use my linux box for everything and it serves me well (AMD64, 6GB, 1GB Video, 25" monitor, fast, quiet, efficient). I run Win XP in Virtual Box along with a 10.10 server for remote access to files, etc.

This desktop has 4TB of internal drive space across 3 physical drives. My question is:

How do I allocate one of the physical drives (1TB) to the virtual server as I am running low on the drive where the VMs (and files) are located.

Thanks
Hutch

---

### Post by ChasHutch on 2011-04-25
After I slept on this, it dawned on me to try adding one of the physical drives via a shared folder in VBox.

I needed to add the VBox Guest Additions first. This turned out to be pretty simple, google "VBox guest additions ubuntu server" for install specifics.  Once I had the guest additions added, I was able to add a shared folder on one of the large physical drives to the guest os.

Trying to access the shared folder was a little more difficult. When trying to cd to the sf_dir created by the VBox share, I did not have permissions. I could root to the dir but not with my ID.  I tried granting my ID permissions but I may not have had the right chmod context. I used webmin and added myself the the vbox group and all seems fine.

Now, if I could just access the guest os remotely, I'd be set.

---

### Post by collisionystm on 2011-04-25
> **ChasHutch said:**
> After I slept on this, it dawned on me to try adding one of the physical drives via a shared folder in VBox.

I needed to add the VBox Guest Additions first. This turned out to be pretty simple, google "VBox guest additions ubuntu server" for install specifics.  Once I had the guest additions added, I was able to add a shared folder on one of the large physical drives to the guest os.

Trying to access the shared folder was a little more difficult. When trying to cd to the sf_dir created by the VBox share, I did not have permissions. I could root to the dir but not with my ID.  I tried granting my ID permissions but I may not have had the right chmod context. I used webmin and added myself the the vbox group and all seems fine.

Now, if I could just access the guest os remotely, I'd be set.


you can also use this command to add yourself to groups

```

usermod -G <group> -a <username>

```

Just install SSH to access it remotely.

```

sudo apt-get install ssh

```

Hopefully your network connection on vbox is set to Bridged so Ubuntu can grab a real ip address......

---

### Post by ChasHutch on 2011-04-25
Thanks for the reply. My wife had surgery today and I knew I had to spend the day in the waiting room with wireless :)

I installed ftp and ssh and have been working on the server all day. Works great!

Thanks

---

