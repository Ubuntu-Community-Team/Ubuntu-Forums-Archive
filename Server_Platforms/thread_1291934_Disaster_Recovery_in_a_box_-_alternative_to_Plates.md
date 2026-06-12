---
title: "Disaster Recovery in a box - alternative to Platespin Forge?"
date: 2009-10-15
forum: Server Platforms
---

### Post by bluntknife on 2009-10-15
Hi,

I'm trying to discover whether it is possible to replicate the functionality of Novell's Platespin Forge disaster recovery product.
Forge will allow you to make a copy of live servers (not sure whether this is Wintel and Linux based) and store them locally as virtual machines. You can also configure the Forge to make periodic backups of the entire server stack so that the Operating System, Application binaries AND data is backed up frequently to the Forge storage.
In the event of a disaster you can perform a V2P, V2V restore of the failed server or just boot the Forge's local copy of the live server and run it from the Forge. Forge uses an embedded VMware hypervisor for this.

So, using an Ubuntu server is it possible to perform the following?;

1. Create a virtual machine on the Ubuntu server using a live physical or virtual server as the source.

2. Schedule the replication of the source server's disks (the data delta, not the entire set of disks each time) to the Ubuntu server. (wonder if RSYNC can help here or do you need an RSYNC agent or client installed on the source server?!)

3. Restore the copied VM from the Ubuntu server to a new physical or virtual server.

4. Bring the copied server online locally within the Ubuntu server if there are no spare servers to restore the copied server image to.

I'd like to try to create the solution above utilising open source (and supported by Canonical) software, where possible.

Ah, and one more requirement / nice to have / would be to manage all of the above from a headless Ubuntu server via some kind of web interface(s).

I really hope the above is possible somehow and many thanks in advance for any input to my project.

Best regards. :)

---

### Post by Lars Noodén on 2009-10-15
There are more ways to do that than there are systems.  

There are many tools and methods to back up and restore.  Bacula is worth mentioning.  However, [dump](http://manpages.ubuntu.com/manpages/jaunty/en/man8/dump.8.html)/[restore](http://manpages.ubuntu.com/manpages/jaunty/en/man8/restore.8.html)  as is plain old mount+rsync

The directories /etc, /var, and /home hold your data, and maybe /boot.  The rest is replaceable.  Note that some unusual applications might keep data in parts of /opt

> **bluntknife said:**
> 
So, using an Ubuntu server is it possible to perform the following?;

1. Create a virtual machine on the Ubuntu server using a live physical or virtual server as the source.


Yes, but why a VM?  You can do about as much with a filesystem image mounted via loop back.  

> **bluntknife said:**
> 
2. Schedule the replication of the source server's disks (the data delta, not the entire set of disks each time) to the Ubuntu server. (wonder if RSYNC can help here or do you need an RSYNC agent or client installed on the source server?!)


rsync is *the* way to do a delta.  

> **bluntknife said:**
> 
3. Restore the copied VM from the Ubuntu server to a new physical or virtual server.


> **bluntknife said:**
> 
4. Bring the copied server online locally within the Ubuntu server if there are no spare servers to restore the copied server image to.


> **bluntknife said:**
> 
I'd like to try to create the solution above utilising open source (and supported by Canonical) software, where possible.

Ah, and one more requirement / nice to have / would be to manage all of the above from a headless Ubuntu server via some kind of web interface(s).

I really hope the above is possible somehow and many thanks in advance for any input to my project.


webmin would be the first option to look at.  However, it won't work until you first bring up the OS, the web server, and then webmin itself.  To do all that, you need the shell...

A fast way to back-up a system is to use rsync to copy /etc, /var, /home, and /boot to a locally mounted filesystem (e.g. a removeable drive).  Include somewhere a list of installed packages.

```

dpkg --get-selections \ 
 | grep install \
 | grep -v deinstall \
 | awk '{ print  $1 }' \
 | sort \
 > /tmp/my.list.of.installed.packages.txt

```

To restore, choose the 'cli system' option from the install and do the bare bones.  Then while still in the installer live cd system, go to shell, chroot to the installation target, use the list of packages above to restore the packages, then use rsync to restore the data, then reboot and verify.

If you roll your own install cd, you can [include openssh-server](https://help.ubuntu.com/community/Installation/NetworkConsole), plus a server key (so that a password does not need to be stored on the cd)

---

### Post by bluntknife on 2009-10-30
Thanks for your response Lars.

Just to make my main point clearer, I'm not looking to perform a file level backup of the servers because some of the servers may be Windows based.
I am trying to make an image or VM of the live servers (without causing downtime if possible) and store the image on a Ubuntu server.  The Ubuntu server will also have VMware server edition installed incase the copied live server images need to be booted up in the event of a disaster.
I can use Vmware converter for this, as well as some other tools, but what I was trying to do was create an all-in-one solution, automating as many of the tasks as possible.

Best regards.

---

### Post by Lars Noodén on 2009-10-31
Ok.  That sounds more like a question of how to back up virtual machine images.  

If you haven't looked at VirtualBox, then now would be a good time to do so,  Qemu/kqemu, too.  

One of the easier ways to go would be to take advantage of the ability to make [snapshots](http://ubuntuforums.org/showthread.php?t=689982).  
[http://ubuntuforums.org/showthread.php?t=689982](http://ubuntuforums.org/showthread.php?t=689982)

[http://notemagnet.blogspot.com/2008/12/copying-virtual-box-snapshots.html](http://notemagnet.blogspot.com/2008/12/copying-virtual-box-snapshots.html)

---

