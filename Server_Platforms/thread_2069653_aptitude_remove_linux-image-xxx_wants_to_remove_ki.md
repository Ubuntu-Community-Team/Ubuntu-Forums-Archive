---
title: "aptitude remove linux-image-xxx wants to remove kitchen sink"
date: 2012-10-11
forum: Server Platforms
---

### Post by stormica on 2012-10-11
Hi All, 

I'm trying to do a little maintenance to one of the servers here (10.04, old, I know, but no time to test the upgrade path)

When I run aptitude remove linux-image-2.6.32-28-server, I am told that it wants to remove: 
 apache2-mpm-itk{u} apache2-utils{u} apache2.2-bin{u} apache2.2-common{u}
  libapr1{u} libaprutil1{u} libaprutil1-dbd-sqlite3{u} libaprutil1-ldap{u}
  libupsclient1{u} linux-image-2.6.32-28-server ubufox{u}

That's a lot of stuff to remove to remove a (really) old kernel.... 
Why is this?  It doesn't seem safe, since this server does serve web and has a UPS attached to it, etc.... 
And what are the {u} behind the package names?  You can't google that one. ;) 

The current running kernel is: Linux  2.6.32-42-server #95-Ubuntu SMP Wed Jul 25 16:10:49 UTC 2012 x86_64 GNU/Linux
(Hmm,. interesting... that's actually 2 kernels back now. I'm surprised at that, because it's the only machine here running older than .43...)

Any guidance is appreciated.

P.s. Please be gentle, this is my first Deb based distro.  I used "the other guys" til a couple of years ago when I built this server, some of the deb habits are not ingrained yet.

---

### Post by dsmithhfx on 2012-10-11
I forget the exact procedure (you'll have to google it), but you can 'lock' packages to prevent upgrades & removal. You might find it a lot easier to just leave the old kernel in place, unless you are desperately short of disk space.

---

### Post by stormi on 2012-10-11
Hey (Same person, different account.  I forgot I had one here already.)

Thanks for that info.  I will "assume" then that letting it go ahead would be as dangerous as it looks?

Why would so many packages be tied to the Kernel?  

I notice if I use the same command with one of the other 10 odd kernels, all of them want to remove the same packages, so it doesn't seem like they're tied to the one kernel.   

No,.. I'm not out of space on that server, there's no /boot partition, so it uses the root.  I just wanted to tidy up, like I have on the other servers.

---

### Post by CharlesA on 2012-10-11
Ran this and paste what the output is.

```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```

---

### Post by lykwydchykyn on 2012-10-11
The {u} means "unused", and it indicates that, as far as aptitude knows, the packages listed were installed as dependencies of another package which has been subsequently removed, and it's therefore uninstalling them as a matter of tidyness.

It probably has nothing to do with the fact that you're uninstalling old kernels, it would do it anyway.

This usually happens when you install things using apt-get or tasksel instead of aptitude.  Basically, aptitude keeps its own database of things that you have explicitly installed vs. things that were installed as dependencies, and when you install via other package management front-ends, aptitude's list doesn't get updated.

It could also be that these packages are actually old unnecessary packages that can be safely removed.  Best way to find out is to launch aptitude, search for the packages, and read the description.  If it looks like something you'd rather keep, hit 'm' while the package is highlighted and it will be marked as manually installed.

---

### Post by stormi on 2012-10-11
Hey CharlesA!  You helped me with my last question too!

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubufox libapr1 libaprutil1-ldap apache2-utils libupsclient1 apache2.2-common
  libaprutil1-dbd-sqlite3 apache2.2-bin libaprutil1 apache2-mpm-itk
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-2.6.32-31* linux-headers-2.6.32-31-server*
  linux-headers-2.6.32-32* linux-headers-2.6.32-32-server*
  linux-headers-2.6.32-33* linux-headers-2.6.32-33-server*
  linux-headers-2.6.32-34* linux-headers-2.6.32-34-server*
  linux-headers-2.6.32-35* linux-headers-2.6.32-35-server*
  linux-headers-2.6.32-36* linux-headers-2.6.32-36-server*
  linux-headers-2.6.32-37* linux-headers-2.6.32-37-server*
  linux-headers-2.6.32-38* linux-headers-2.6.32-38-server*
  linux-headers-2.6.32-39* linux-headers-2.6.32-39-server*
  linux-headers-2.6.32-40* linux-headers-2.6.32-40-server*
  linux-headers-2.6.32-41* linux-headers-2.6.32-41-server*
  linux-headers-2.6.32-43* linux-headers-2.6.32-43-server*
  linux-headers-2.6.32-44* linux-headers-2.6.32-44-server*
  linux-headers-server* linux-image-2.6.32-28-server*
  linux-image-2.6.32-31-server* linux-image-2.6.32-32-server*
  linux-image-2.6.32-33-server* linux-image-2.6.32-34-server*
  linux-image-2.6.32-35-server* linux-image-2.6.32-36-server*
  linux-image-2.6.32-37-server* linux-image-2.6.32-38-server*
  linux-image-2.6.32-39-server* linux-image-2.6.32-40-server*
  linux-image-2.6.32-41-server* linux-image-2.6.32-43-server*
0 upgraded, 0 newly installed, 40 to remove and 0 not upgraded.
After this operation, 2,769MB disk space will be freed.
Do you want to continue [Y/n]?I didn't think that apache2.2-common and others were automatically installed, and that they were required for apache to continue to function.... 

Either way, this looks safer.   I guess I should paw through that and find out what it does that's so different than what I was doing.    I know that it's checking the currently running kernel, and looks like it's removing it's headers but not the image for the latest kernel, but that's as far as I get.   

The only thing that concerns me is when I have to reload the virtualbox driver, doesn't it use the headers for that? 

I'd be more comfortable leaving the last couple of kernels though plus the current one.  Is that possible? (the main reason I was doing this manually, and probably the hard way ;) )

---

### Post by CharlesA on 2012-10-11
It will only remove the headers for the previous kernels, the current kernel headers will be fine. ;)

As for:

```
The following packages were automatically installed and are no longer required:
ubufox libapr1 libaprutil1-ldap apache2-utils libupsclient1 apache2.2-common
libaprutil1-dbd-sqlite3 apache2.2-bin libaprutil1 apache2-mpm-itk
```

They should be safe to remove, but to check what you have installed, you can run this:

```
dpkg -l | grep apache2
```

---

### Post by stormi on 2012-10-11
Ahh,.. thank you lykwydchykyn.  I suspected that's what the {u} would be for, but didn't want to ignore it in case I was wrong.  

I didn't realise that using apt-get would cause problems. I have used it for almost everything when installing, upgrading and removing packages.  Am I likely to find a lot more remnants like this?  

I guess I need to sit down and learn how to use aptitude instead.  I did check out a bunch of the apache ones at packages.ubuntu.com, they looked like they -might- be important.  A couple of the others looked like they were extraneous, and I wouldn't have a problem uninstalling them.

---

### Post by CharlesA on 2012-10-11
I don't use aptitude at all but it was my understanding it was just a frontend to apt-get/dpkg.

---

### Post by stormi on 2012-10-11
I find it interesting that it will also remove the headers for the future kernels too.  The server hasn't been rebooted or grub told which kernel I want to use since the kernel update  (last night) and so it's still using the older kernel.  Would the best route then be to just reinstall those headers after doing this purge? 

The problem I can see is:
Reboot to use the new kernel
Virtualbox fails to start and needs kernel driver recompiled
Headers are not present
Recompile fails
Headers must be reinstalled to bring up the downed VBs that are Internet facing
Recompile Virtualbox drivers
start VMs

If I can avoid the middle three steps, the outage is only a couple of minutes and my thin hold on sanity isn't in further jeopardy.  Or am I over-thinking this?


```
dpkg -l | grep apache2
```
ii  apache2-mpm-itk                      2.2.14-5ubuntu8.9                               multiuser MPM for Apache 2.2
ii  apache2-utils                        2.2.14-5ubuntu8.9                               utility programs for webservers
ii  apache2.2-bin                        2.2.14-5ubuntu8.9                               Apache HTTP Server common binary files
ii  apache2.2-common                     2.2.14-5ubuntu8.9                               Apache HTTP Server common files

The first and third -look- like I shouldn't remove them.  I know that common -might- not have been needed, and the itk package seemed like part of the necessary parts of apache2 based on what I read in the descriptions of the other packages.

This server serves our Intranet.  It's alfresco, and a few other web based apps.  I sort 
of don't want to crap that out, and am willing to err on the side of caution as a result. :) 

It would be nice to reclaim the nearly 3GB of space the unused kernels are taking up though, so I will spend some quality time with Aptitude today I guess, so that I can tell it not to remove the apache related stuff then go ahead and run the purge as you recommend.

---

### Post by lykwydchykyn on 2012-10-11
> **stormi said:**
> Ahh,.. thank you lykwydchykyn.  I suspected that's what the {u} would be for, but didn't want to ignore it in case I was wrong.  

I didn't realise that using apt-get would cause problems. I have used it for almost everything when installing, upgrading and removing packages.  Am I likely to find a lot more remnants like this?  

Possibly, but it's hard to say.  I've mixed them in the past, and it's only now and then when I've run into trouble.
> 
I guess I need to sit down and learn how to use aptitude instead.  I did check out a bunch of the apache ones at packages.ubuntu.com, they looked like they -might- be important.  A couple of the others looked like they were extraneous, and I wouldn't have a problem uninstalling them.

Synatax-wise, aptitude is pretty much a drop-in replacement for apt-get, but with a bunch of extra features.  You can usually use them interchangeably, but this particular issue is one of the few things that can crop up if you do.  As long as you're aware of it, and remember to set aptitude straight when it tries to remove half your system, it's no big deal.  It is, of course, safer to use one or the other.  

> **CharlesA said:**
> I don't use aptitude at all but it was my understanding it was just a frontend to apt-get/dpkg.

Properly stated, aptitude and apt-get are both front-ends to APT (libept); they have their own systems for a lot of dependency-related functions, though.  Both ultimately call dpkg for the actual package installation.  Aptitude does not call apt-get, it uses the libept library directly, as I understand it.

---

### Post by CharlesA on 2012-10-11
I've used that command before and it only removed the kernel headers for an installed kernel. However, if you have a kernel installed but not booted into it yet, it might removed those and you'd need to reinstall the kernel headers before rebooting again.

Worse case is you'd need to reinstall apache, if you allow it to remove it, and it might be a newer version than the one installed. I do not know for sure.

---

### Post by stormi on 2012-10-11
> **CharlesA said:**
> I don't use aptitude at all but it was my understanding it was just a frontend to apt-get/dpkg.

It sure looks like a front end.  
I just spent some time in there looking for all of those dependencies.  
Found them all, marked the ones I wanted to keep as manual, as suggested.  

One thing I noticed was that it mentioned 2 broken packages.  I ran an 
[FONT=Arial]apt-get -f install

and it didn't feel the need to install or even report anything.  
This was before I found the last package (the mpm-itk package)

Running it again after finding the last package, it doesn't seem to see any broken packages anymore.  
I guess I'm ready to do the purge? [/FONT]

---

### Post by CharlesA on 2012-10-11
Yeah, should be good now.

Just remember to reinstall the kernel headers for the new kernel before rebooting.

---

### Post by stormi on 2012-10-11
> **lykwydchykyn said:**
> Possibly, but it's hard to say.  I've mixed  them in the past, and it's only now and then when I've run into  trouble.

Synatax-wise, aptitude is pretty much a drop-in replacement for apt-get,  but with a bunch of extra features.  You can usually use them  interchangeably, but this particular issue is one of the few things that  can crop up if you do.  As long as you're aware of it, and remember to  set aptitude straight when it tries to remove half your system, it's no  big deal.  It is, of course, safer to use one or the other.  

Properly stated, aptitude and apt-get are both front-ends to APT  (libept); they have their own systems for a lot of dependency-related  functions, though.  Both ultimately call dpkg for the actual package  installation.  Aptitude does not call apt-get, it uses the libept  library directly, as I understand it.

Excellent, thank you for the clarification.   At least now I know that it is somewhat fallible, especially if I'm using it a little contrary to what it prefers.  More importantly, I know how to perform an attitude adjustment when necessary. :) 


> **CharlesA said:**
> I've used that command before and it only removed the kernel headers for an installed kernel. However, if you have a kernel installed but not booted into it yet, it might removed those and you'd need to reinstall the kernel headers before rebooting again.

Worse case is you'd need to reinstall apache, if you allow it to remove it, and it might be a newer version than the one installed. I do not know for sure.

That's what I'll do then.  I think I found that command first when I initially went looking (one of the virtual servers ran out of space on /boot and I needed to figure this out) but i was uncomfortable with the removal of all of the kernels but the current one.  

Here's my plan: 
run the purge command above
install the headers for the latest kernel and possibly install the latest kernel again too.
update grub to use the latest kernel
reboot
recompile the kernel driver for Virtualbox
start my VMs

Shouldn't apt-get be keeping apache and friends up to date? It should be taken care of with apt-get update & apt-get upgrade shouldn't it?  I could swear I've seen updates for apache in the updates... not lately mind you.

---

### Post by stormi on 2012-10-11
> **CharlesA said:**
> Yeah, should be good now.

Just remember to reinstall the kernel headers for the new kernel before rebooting.

Wow,.. that's scary as hell to watch.  

OK,.. it looked good til the very end: 
> [B]The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub][/B]
Purging configuration files for linux-image-2.6.32-43-server ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-44-server
Found initrd image: /boot/initrd.img-2.6.32-44-server
Found linux image: /boot/vmlinuz-2.6.32-42-server
Found initrd image: /boot/initrd.img-2.6.32-42-server
Found memtest86+ image: /boot/memtest86+.bin
done


Still, it looks fairly minor.  I think the reading I did says that's because there's no "older" kernel than the one I'm running, so I think that means that once I move to using the .44 kernel, the error will be moot? (There are no custom kernels on this machine, never have been, so the bug tracker report I read doesn't apply here.)

I have installed the 44 and 44-server headers.
Do I need whatever was removed by the linux-headers-server* portion of the purge? 

Now I just have to schedule a maintenance window for this evening.  

Thanks very much to all of you!

---

### Post by CharlesA on 2012-10-11
Check to make sure you have vmlinuz and  initrd.img in the root of the drive (/). They should be symlinks to the files in /boot/whatever

Should be ok otherwise.

---

### Post by stormi on 2012-10-11
> **CharlesA said:**
> Check to make sure you have vmlinuz and  initrd.img in the root of the drive (/). They should be symlinks to the files in /boot/whatever

Should be ok otherwise.

Check.  You are correct sir.  Looks like on reboot I will be booting with the .44 kernel:

lrwxrwxrwx   1 root root    32 2012-10-11 01:44 initrd.img -> boot/initrd.img-2.6.32-44-server
lrwxrwxrwx   1 root root    29 2012-10-11 01:44 vmlinuz -> boot/vmlinuz-2.6.32-44-server

I will reboot this evening and report back.  Hopefully with 100% success.  
Good time to add grease to that CPU fan too! :)

---

### Post by stormi on 2012-10-11
I am happy to report complete success.  The server rebooted perfectly.  I'm running the .44 kernel.  

Now to wait and watch to see if it brings any "isms" to troubleshoot, but the main hurdles are cleared.  A great big thank you to all of you gentlemen who helped me out.  :biggrin:

Now I just need to remember how to mark a topic as solved.

---

