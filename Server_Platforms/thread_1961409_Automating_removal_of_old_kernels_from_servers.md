---
title: "Automating removal of old kernels from servers"
date: 2012-04-19
forum: Server Platforms
---

### Post by Viruk on 2012-04-19
Hi, 

I have had a couple of problems in the last week when some of the ubuntu servers (running on VMware ESXi) ran out of space in /boot due to the different kernels installed during updates. 

I couldn't remove the older kernels due to unmet dependencies:
```
The following packages have unmet dependencies.
  linux-image-generic-pae: Depends: linux-image-2.6.32-40-generic-pae but it is not going to be installed
```
I couldn't meet the dependencies because I didn't have the room. 

I ended up just deleting some of the older files in /boot and managed to meet dependencies and do the outstanding updates and removing older kernels using apt-get remove. 
While looking for a way to remove more of these older kernels, I found the following page: [http://ubuntuforums.org/showthread.php?t=1658648](http://ubuntuforums.org/showthread.php?t=1658648)
This showed the command:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

But it is not quite what I am looking for, I would like to leave an older kernel on the system and then create a cron job to periodically run and prevent the /boot partition filling up. 

I tested a few options (aren't snapshots of VMs helpful!) including the following option from the same thread above: 
```
OLD=$(ls -tr /boot/vmlinuz-* | head -n -2 | cut -d- -f2- | \
    awk '"'"'{print "linux-image-" $0}'"'"' )
if [ -n "$OLD" ]; then
    apt-get -qy remove --purge $OLD
fi
apt-get -qy autoremove --purge
```
However this didn't appear to clear out any space on /boot where the first command did clear out all but the latest versions of files in /boot

Can anyone help me with editing one or the other of these options so that I leave an extra kernel on the system, but also clear the space out in /boot?

Thanks very much :)

---

### Post by CharlesA on 2012-04-19
You cannot remove linux-image-generic-pae package because the kernel depends on it. All you can do is remove the headers and image packages of older kernels.

> **Viruk said:**
> 
Can anyone help me with editing one or the other of these options so that I leave an extra kernel on the system, but also clear the space out in /boot?

You just want one previous kernel right?

```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```

Note - I haven't tested this on 3.x.x kernels, but it should work fine as the pattern matching uses uname -r for the kernel version:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'
linux-headers-2.6.32-34
linux-headers-2.6.32-34-server
linux-headers-2.6.32-35
linux-headers-2.6.32-35-server
linux-headers-2.6.32-38
linux-headers-2.6.32-38-server
linux-image-2.6.32-33-server
linux-image-2.6.32-34-server
linux-image-2.6.32-35-server
linux-image-2.6.32-38-server

```

---

### Post by SeijiSensei on 2012-04-19
I've been thinking about posting a bug report or wishlist item about kernel management.  The installer should really prune very old kernels.  I can see leaving the (N-1)st and maybe even the (N-2)nd, but the ones older than that make little sense.  The installer should also remove the associated stanzas for these kernels from grub.cfg, too.  (This should happen automatically, I think, once the kernel images are deleted and grub-config runs.)

I used to allocate only 256MB to /boot which should be more than ample, but I've doubled that figure on more recent installations to protect against overrunning the partition.  This problem particularly arises if you're running a development release.  I had half-a-dozen 3.2.0-x kernel images in /boot when I checked just now.

Does this make sense to you, too?

---

### Post by josephmills on 2012-04-19
```
dpkg-query -l|grep linux-im*
```
that should match all kernels 

need broken down more 
like 
```
dpkg-query -l |grep linux-im*|awk '{print $2}'
```
or a while loop ?

---

### Post by CharlesA on 2012-04-19
> **SeijiSensei said:**
> I've been thinking about posting a bug report or wishlist item about kernel management.  The installer should really prune very old kernels.  I can see leaving the (N-1)st and maybe even the (N-2)nd, but the ones older than that make little sense.  The installer should also remove the associated stanzas for these kernels from grub.cfg, too.  (This should happen automatically, I think, once the kernel images are deleted and grub-config runs.)

Go for it.

> I used to allocate only 256MB to /boot which should be more than ample, but I've doubled that figure on more recent installations to protect against overrunning the partition.  This problem particularly arises if you're running a development release.  I had half-a-dozen 3.2.0-x kernel images in /boot when I checked just now.

Does this make sense to you, too?

I have everything on one partition so, it doesn't dramatically affect me, but I can see your point. :)

> **josephmills said:**
> ```
dpkg-query -l|grep linux-im*
```
that should match all kernels 

need broken down more 
like 
```
dpkg-query -l |grep linux-im*|awk '{print $2}'
```
or a while loop ?

You can pipe it to dpkg or use xargs. See the command I posted earlier, or [here]("http://charlesa.net/scripts/linux/purgekernel.php"). ;)

---

### Post by volkswagner on 2012-04-19
Perhaps you can take a different approach.

If you upgrade kernel using:
```
 sudo aptitude safe-upgrade
```
Aptitude will automatically remove old kernels.

Then you could create a script to backup images & such to a separate partition plus a cleanup script for the backup location.

If this works for you, it may be safer than going directly at your /boot directory.

---

### Post by CharlesA on 2012-04-19
Hrm, I thought safe-upgrade didn't upgrade kernels? They might be removed because they are marked as obsolete in the newer versions of Ubuntu.

EDIT: I guess you are right:

[http://askubuntu.com/questions/221/how-to-force-installing-kernel-updates-when-using-apt-get-upgrade](http://askubuntu.com/questions/221/how-to-force-installing-kernel-updates-when-using-apt-get-upgrade)

;)

---

### Post by Viruk on 2012-04-19
Thanks for your replies, I'm juggling some other problems at the minute so will look at this more again in the morning. Here's what I've found so far - although I started writing this response before the last couple of suggestions...

I've been doing some testing...

the test system is up to date with everything installed by apt-get update && apt-get upgrade (at the point I took the snapshot)
the output at this point is: 
```
The following packages have been kept back:
  landscape-common linux-generic-pae linux-headers-generic-pae
  linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```
uname -r gives 
2.6.32-39-generic-pae

I'm not sure why this is, as other servers have updated to 2.6.32-40 using only apt-get update and apt-get upgrade

if I run: 
```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```
first thing it does is install headers for 2.6.32-40

```
The following NEW packages will be installed
  linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic-pae
The following packages will be upgraded:
  linux-headers-generic-pae
1 upgraded, 2 newly installed, 38 to remove and 3 not upgraded.
Need to get 10.7MB of archives.
After this operation, 2,218MB disk space will be freed.
```

it then runs through the loop removing headers for old versions, the final few lines of output are: 
```
Setting up linux-headers-2.6.32-40 (2.6.32-40.87) ...
Setting up linux-headers-2.6.32-40-generic-pae (2.6.32-40.87) ...

Setting up linux-headers-generic-pae (2.6.32.40.47) ...
```

however when I cd /boot and ls the output is: 
```
abi-2.6.32-39-generic-pae         memtest86+.bin
config-2.6.32-39-generic-pae      System.map-2.6.32-39-generic-pae
grub                              vmcoreinfo-2.6.32-39-generic-pae
initrd.img-2.6.32-39-generic-pae  vmlinuz-2.6.32-39-generic-pae
lost+found
```

I'm only getting left with 1 kernel version's entries in /boot - any ideas what's going on?
I've even done this multiple times and kept reverting back to the snapshot just to try to rule out any mistakes I could have made, but I've got the same result each time.

I'll try the safeupgrade and let you know what happens then. 
Thanks for the help so far :)

---

### Post by CharlesA on 2012-04-19
You still haven't installed the updated kernel. You would have to make sure the system is totally up-to-date before running that command.

It won't make the system unbootable, thankfully, as it keeps one previous kernel.

```
sudo apt-get dist-upgrade
```

Or 

```
sudo aptitude safe-upgrade
```

Will install the new kernel.

---

### Post by SeijiSensei on 2012-04-19
> **CharlesA said:**
> Go for it.

I added a comment to this bug, which raised a related point about the number of entries in /lib/modules/:  

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690911](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690911)

That bug is from 2010 with no assignment to a developer.  We'll see if my bumping it generates a response.

---

### Post by CharlesA on 2012-04-19
> **SeijiSensei said:**
> I added a comment to this bug, which raised a related point about the number of entries in /lib/modules/:  

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690911](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690911)

That bug is from 2010 with no assignment to a developer.  We'll see if my bumping it generates a response.
Thanks. Hopefully you get somewhere. :)

---

### Post by Viruk on 2012-04-19
I'm going to have to pick this up again in the morning, but I also found this: 
[http://www.linux-archive.org/ubuntu-server-development/633936-distro-provided-mechanism-clean-up-old-kernels-2.html](http://www.linux-archive.org/ubuntu-server-development/633936-distro-provided-mechanism-clean-up-old-kernels-2.html)

---

### Post by Viruk on 2012-04-20
When automatic updates are selected on an Ubuntu server, which updates are applied? 
I thought (aparently wrongly) that it was just the equivalent of apt-get update and apt-get upgrade, but that doesn't appear to be the case. 

I'm about to retest rolling the machine back, fully upgrading and then re-running the command. 

Thanks again for all your help here :)

---

### Post by Viruk on 2012-04-20
OK, so I've rolled back to the snapshot which is running 2.6.32-39-generic-pae, made sure everything is up to date with apt-get update and upgrade and then done apt-get dist-upgrade which has successfully changed the kernel over to 2.6.32-40-generic-pae

I then went on to run: 
```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```

However it has only left the latest version in /boot
Here is the output of ls
abi-2.6.32-40-generic-pae
config-2.6.32-40-generic-pae
grub
initrd.img-2.6.32-40-generic-pae
lost+found
memtest86+.bin
System.map-2.6.32-40-generic-pae
vmcoreinfo-2.6.32-40-generic-pae
vmlinuz-2.6.32-40-generic-pae

The output of dpkg --list | grep linux-image shows: 
ii  linux-image-2.6.32-40-generic-pae   2.6.32-40.87                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic-pae             2.6.32.40.47                      Generic Linux kernel image

Would you expect details of 2.6.32-39-generic-pae to remain based on the script above? Or does the command treat linux-image-2.6.32-40-generic-pae and linux-image-generic-pae as the latest 2 kernels? 

Should entries for more than just 2.6.32-40-generic-pae be left in /boot ?

---

### Post by CharlesA on 2012-04-20
Huh. I run that same command earlier and it left the most recent kernel and one previous one. That is why the head command is in there.

---

### Post by Viruk on 2012-04-20
Yes - I spotted the change and thought that would do the trick. 

I'm re-running through the whole process again to check I haven't done anything stupid....

---

### Post by Viruk on 2012-04-20
Updated using apt-get update and apt-get upgrade 
then did apt-get dist-upgrade which took it from kernel 2.6.32-39 to 2.6.32-40

and logged on to see: 

```
Linux V-Wiki 2.6.32-40-generic-pae #87-Ubuntu SMP Mon Mar 5 21:44:34 UTC 2012 i686 GNU/Linux
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Fri Apr 20 14:41:54 BST 2012

  System load:  0.11               Processes:           94
  Usage of /:   14.2% of 28.04GB   Users logged in:     0
  Memory usage: 6%                 IP address for eth0: x.x.x.x
  Swap usage:   0%

  => /boot is using 92.5% of 227MB

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Fri Apr 20 14:40:50 2012 from x.x.x.x
```

Note the warning about /boot

I then ran:

```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes
```

This removes quite a lot from the system, but even though I've just done the whole thing again I am left with the same files in /boot, here is an output of ls 

```
abi-2.6.32-40-generic-pae
config-2.6.32-40-generic-pae
grub
initrd.img-2.6.32-40-generic-pae
lost+found
memtest86+.bin
System.map-2.6.32-40-generic-pae
vmcoreinfo-2.6.32-40-generic-pae
vmlinuz-2.6.32-40-generic-pae
```

The logon message after this point is: 
```
Linux V-Wiki 2.6.32-40-generic-pae #87-Ubuntu SMP Mon Mar 5 21:44:34 UTC 2012 i686 GNU/Linux
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Fri Apr 20 14:52:59 BST 2012

  System load:  0.0               Processes:           94
  Usage of /:   6.0% of 28.04GB   Users logged in:     0
  Memory usage: 7%                IP address for eth0: x.x.x.x
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Fri Apr 20 14:41:54 2012 from x.x.x.x
```

---

### Post by rubylaser on 2012-04-20
That looks good, those are all of the files you should have after cleaning up your kernels.  How much space is used on /boot now?

```
du -h --max-depth=1 /boot
```

---

### Post by CharlesA on 2012-04-20
Hi,

Can you run this after reverting to the previous snapshot?

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
```

---

### Post by Viruk on 2012-04-20
I've already started testing something else from a rollback :)
```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -2) --assume-yes
```

I changed the "head -n -1" to "head -n -2"

Output from du now: 
```
du -h --max-depth=1 /boot
12K     /boot/lost+found
4.0M    /boot/grub
34M     /boot
```

which looks good :)


I can also test that revised command now CharlesA...

---

### Post by Viruk on 2012-04-20
The output of 

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
```
is

```
linux-headers-2.6.32-21
linux-headers-2.6.32-21-generic-pae
linux-headers-2.6.32-26
linux-headers-2.6.32-26-generic-pae
linux-headers-2.6.32-27
linux-headers-2.6.32-27-generic-pae
linux-headers-2.6.32-28
linux-headers-2.6.32-28-generic-pae
linux-headers-2.6.32-29
linux-headers-2.6.32-29-generic-pae
linux-headers-2.6.32-30
linux-headers-2.6.32-30-generic-pae
linux-headers-2.6.32-32
linux-headers-2.6.32-32-generic-pae
linux-headers-2.6.32-34
linux-headers-2.6.32-34-generic-pae
linux-headers-2.6.32-35
linux-headers-2.6.32-35-generic-pae
linux-headers-2.6.32-36
linux-headers-2.6.32-36-generic-pae
linux-headers-2.6.32-37
linux-headers-2.6.32-37-generic-pae
linux-headers-2.6.32-38
linux-headers-2.6.32-38-generic-pae
linux-headers-2.6.32-39
linux-headers-2.6.32-39-generic-pae
linux-headers-2.6.32-40
linux-image-2.6.32-21-generic-pae
linux-image-2.6.32-26-generic-pae
linux-image-2.6.32-27-generic-pae
linux-image-2.6.32-28-generic-pae
linux-image-2.6.32-29-generic-pae
linux-image-2.6.32-30-generic-pae
linux-image-2.6.32-32-generic-pae
linux-image-2.6.32-34-generic-pae
linux-image-2.6.32-35-generic-pae
linux-image-2.6.32-36-generic-pae
linux-image-2.6.32-37-generic-pae
linux-image-2.6.32-38-generic-pae
linux-image-2.6.32-39-generic-pae
```

---

### Post by Viruk on 2012-04-20
If i edit that to be "head -n -2", the output is the same list with the last line removed - but I suspect you'll have realised that already :)

so by editing the end of that command I can specify how many kernels I want to keep on the system and cron this

thanks again for all your help - I appreciate it

---

### Post by CharlesA on 2012-04-20
Thank you. I must have missed that the last time I tried using it - it looks like the machine I was testing it on was running 2.6.32-40 with the last kernel being 2.6.32-38.

EDIT: I ran it again and it looked like it worked fine with head -n -1.

I'll post the output here:

Not piped to head.

```
**charles@Atlantis:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'**
linux-headers-2.6.32-34
linux-headers-2.6.32-34-server
linux-headers-2.6.32-35
linux-headers-2.6.32-35-server
linux-headers-2.6.32-38
linux-headers-2.6.32-38-server
linux-image-2.6.32-33-server
linux-image-2.6.32-34-server
linux-image-2.6.32-35-server
linux-image-2.6.32-38-server

```

head -n -1

```
**charles@Atlantis:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' |[COLOR="Red"]head -n -1[/COLOR]**
linux-headers-2.6.32-34
linux-headers-2.6.32-34-server
linux-headers-2.6.32-35
linux-headers-2.6.32-35-server
linux-headers-2.6.32-38
linux-headers-2.6.32-38-server
linux-image-2.6.32-33-server
linux-image-2.6.32-34-server
linux-image-2.6.32-35-server

```

head -n -2

```
**charles@Atlantis:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' |[COLOR="Blue"]head -n -2[/COLOR]**
linux-headers-2.6.32-34
linux-headers-2.6.32-34-server
linux-headers-2.6.32-35
linux-headers-2.6.32-35-server
linux-headers-2.6.32-38
linux-headers-2.6.32-38-server
linux-image-2.6.32-33-server
linux-image-2.6.32-34-server

```

---

### Post by Viruk on 2012-04-23
I can restore and re-run those tests later today, I'm not sure what could be different between our systems though. 

I'll post some results when I have chance later in the morning.

---

### Post by Viruk on 2012-04-23
2.6.32-41-generic-pae has become available since Friday, so I have gone back to the last snapshot from last week and made sure it is up to date with everything now. 

Running the commands you specified, my output is:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'
```
outputs:
```
linux-headers-2.6.32-21
linux-headers-2.6.32-21-generic-pae
linux-headers-2.6.32-26
linux-headers-2.6.32-26-generic-pae
linux-headers-2.6.32-27
linux-headers-2.6.32-27-generic-pae
linux-headers-2.6.32-28
linux-headers-2.6.32-28-generic-pae
linux-headers-2.6.32-29
linux-headers-2.6.32-29-generic-pae
linux-headers-2.6.32-30
linux-headers-2.6.32-30-generic-pae
linux-headers-2.6.32-32
linux-headers-2.6.32-32-generic-pae
linux-headers-2.6.32-34
linux-headers-2.6.32-34-generic-pae
linux-headers-2.6.32-35
linux-headers-2.6.32-35-generic-pae
linux-headers-2.6.32-36
linux-headers-2.6.32-36-generic-pae
linux-headers-2.6.32-37
linux-headers-2.6.32-37-generic-pae
linux-headers-2.6.32-38
linux-headers-2.6.32-38-generic-pae
linux-headers-2.6.32-39
linux-headers-2.6.32-39-generic-pae
linux-headers-2.6.32-40
linux-headers-2.6.32-40-generic-pae
linux-headers-2.6.32-41
linux-image-2.6.32-21-generic-pae
linux-image-2.6.32-26-generic-pae
linux-image-2.6.32-27-generic-pae
linux-image-2.6.32-28-generic-pae
linux-image-2.6.32-29-generic-pae
linux-image-2.6.32-30-generic-pae
linux-image-2.6.32-32-generic-pae
linux-image-2.6.32-34-generic-pae
linux-image-2.6.32-35-generic-pae
linux-image-2.6.32-36-generic-pae
linux-image-2.6.32-37-generic-pae
linux-image-2.6.32-38-generic-pae
linux-image-2.6.32-39-generic-pae
linux-image-2.6.32-40-generic-pae
linux-source-2.6.32
```

head -n -1 
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' |head -n -1
```
outputs:
```
linux-headers-2.6.32-21
linux-headers-2.6.32-21-generic-pae
linux-headers-2.6.32-26
linux-headers-2.6.32-26-generic-pae
linux-headers-2.6.32-27
linux-headers-2.6.32-27-generic-pae
linux-headers-2.6.32-28
linux-headers-2.6.32-28-generic-pae
linux-headers-2.6.32-29
linux-headers-2.6.32-29-generic-pae
linux-headers-2.6.32-30
linux-headers-2.6.32-30-generic-pae
linux-headers-2.6.32-32
linux-headers-2.6.32-32-generic-pae
linux-headers-2.6.32-34
linux-headers-2.6.32-34-generic-pae
linux-headers-2.6.32-35
linux-headers-2.6.32-35-generic-pae
linux-headers-2.6.32-36
linux-headers-2.6.32-36-generic-pae
linux-headers-2.6.32-37
linux-headers-2.6.32-37-generic-pae
linux-headers-2.6.32-38
linux-headers-2.6.32-38-generic-pae
linux-headers-2.6.32-39
linux-headers-2.6.32-39-generic-pae
linux-headers-2.6.32-40
linux-headers-2.6.32-40-generic-pae
linux-headers-2.6.32-41
linux-image-2.6.32-21-generic-pae
linux-image-2.6.32-26-generic-pae
linux-image-2.6.32-27-generic-pae
linux-image-2.6.32-28-generic-pae
linux-image-2.6.32-29-generic-pae
linux-image-2.6.32-30-generic-pae
linux-image-2.6.32-32-generic-pae
linux-image-2.6.32-34-generic-pae
linux-image-2.6.32-35-generic-pae
linux-image-2.6.32-36-generic-pae
linux-image-2.6.32-37-generic-pae
linux-image-2.6.32-38-generic-pae
linux-image-2.6.32-39-generic-pae
linux-image-2.6.32-40-generic-pae
```
Note that this has dropped the line: 
linux-source-2.6.32
and not had an impact on the linux-image items - I think this is why we see different results

head -n -2 
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' |head -n -2
```
This outputs as expected, dropping the line:
linux-image-2.6.32-40-generic-pae
```
linux-headers-2.6.32-21
linux-headers-2.6.32-21-generic-pae
linux-headers-2.6.32-26
linux-headers-2.6.32-26-generic-pae
linux-headers-2.6.32-27
linux-headers-2.6.32-27-generic-pae
linux-headers-2.6.32-28
linux-headers-2.6.32-28-generic-pae
linux-headers-2.6.32-29
linux-headers-2.6.32-29-generic-pae
linux-headers-2.6.32-30
linux-headers-2.6.32-30-generic-pae
linux-headers-2.6.32-32
linux-headers-2.6.32-32-generic-pae
linux-headers-2.6.32-34
linux-headers-2.6.32-34-generic-pae
linux-headers-2.6.32-35
linux-headers-2.6.32-35-generic-pae
linux-headers-2.6.32-36
linux-headers-2.6.32-36-generic-pae
linux-headers-2.6.32-37
linux-headers-2.6.32-37-generic-pae
linux-headers-2.6.32-38
linux-headers-2.6.32-38-generic-pae
linux-headers-2.6.32-39
linux-headers-2.6.32-39-generic-pae
linux-headers-2.6.32-40
linux-headers-2.6.32-40-generic-pae
linux-headers-2.6.32-41
linux-image-2.6.32-21-generic-pae
linux-image-2.6.32-26-generic-pae
linux-image-2.6.32-27-generic-pae
linux-image-2.6.32-28-generic-pae
linux-image-2.6.32-29-generic-pae
linux-image-2.6.32-30-generic-pae
linux-image-2.6.32-32-generic-pae
linux-image-2.6.32-34-generic-pae
linux-image-2.6.32-35-generic-pae
linux-image-2.6.32-36-generic-pae
linux-image-2.6.32-37-generic-pae
linux-image-2.6.32-38-generic-pae
linux-image-2.6.32-39-generic-pae
```

I suppose the question is, why does my system show the line "linux-source-2.6.32" when yours doesn't appear to?

---

### Post by Viruk on 2012-04-23
Could that just be because you have run this in the past and the line containing "linux-source-2.6.32" had been removed already? 

I'm going to try running: 
```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -10) --assume-yes
```
to get rid of some of the oldest items, this should also remove the line in question, then I would assume that the original command will perform as you expected and your results showed.

---

### Post by Viruk on 2012-04-23
As expected that removes a lot of items from the list; however it removes all the headers from the list so the output of:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'
```
is as follows:
```
linux-image-2.6.32-30-generic-pae
linux-image-2.6.32-32-generic-pae
linux-image-2.6.32-34-generic-pae
linux-image-2.6.32-35-generic-pae
linux-image-2.6.32-36-generic-pae
linux-image-2.6.32-37-generic-pae
linux-image-2.6.32-38-generic-pae
linux-image-2.6.32-39-generic-pae
linux-image-2.6.32-40-generic-pae
linux-source-2.6.32
```

This still has the last line:
linux-source-2.6.32

This being different to your system seems to explain the difference in our results - I'm just ont sure why this difference exists. As long as I check this on a system before setting up that as a cron job it can be accounted for, but it makes it slightly harder for anyone else reading this to just copy and paste a command that will work on their system.

---

### Post by Viruk on 2012-04-23
When I rerun the vmware-config-tools.pl script, I have to add the headers back in. The command is removing all of these which is not neccessarily what I need - but I'm aware of it and can add them back in easily enough. Its probably better to have to do that than have /boot run out of space :)

---

### Post by CharlesA on 2012-04-23
Hrm, I don't have linux-source installed, so that might be why it isn't acting quite right.

---

### Post by Viruk on 2012-04-23
OK - at least we can see why there's a difference in the behaviour of that now. 

Thanks again for all your help with this :)

---

### Post by hotdoog on 2013-01-07
Aren't we purging too many headers with this?

The head part of the script (or one liner) doesn't make sense to me because the listed output linux-image comes after the linux-headers section.

I propose sorting by the 3rd field then deleting using head to take off 3 lines instead of one.

For example on my system, without a sort:
```
rusl@lucid:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
linux-headers-2.6.32-43
linux-headers-2.6.32-43-generic
linux-headers-2.6.32-44
linux-headers-2.6.32-44-generic
linux-image-2.6.32-43-generic

```
That would preserve linux-imageXXX-44 but delete linux-headerXXX-44. If we are keeping the image don't we also need to keep the headers? (It's all confusing as this is a delete list we are creating so inclusion in this list means purging of the package)

My example using sort:
```
rusl@lucid:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3
linux-headers-2.6.32-43
linux-headers-2.6.32-43-generic
linux-image-2.6.32-43-generic

```
This would be deleting only exactly what we want - correct?

So, in conclusion, this is the one-liner I am personally using to remove old kernel. You must write a number that is a multiple of 3 after "head -n"
```
aptitude purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -57 ) --assume-yes
``` In my case it is 57 since I have a lot of kernels and am using this to only delete the last one. However for a more sane/typical use one might want to keep only 3 kernels - the current and two spares. Then the number would be 6 (2 kernels x 3 packages)

---

### Post by CharlesA on 2013-01-07
The headers would only matter if you need to boot into that previous kernel.

In any case, your method makes it easier to tell what is being removed.

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1

linux-headers-3.2.0-26
linux-headers-3.2.0-26-generic
linux-headers-3.2.0-27
linux-headers-3.2.0-27-generic
linux-headers-3.2.0-29
linux-headers-3.2.0-29-generic
linux-headers-3.2.0-30
linux-headers-3.2.0-30-generic
linux-headers-3.2.0-31
linux-headers-3.2.0-31-generic
linux-headers-3.2.0-32
linux-headers-3.2.0-32-generic
linux-headers-3.2.0-33
linux-headers-3.2.0-33-generic
linux-headers-3.2.0-34
linux-headers-3.2.0-34-generic
linux-image-3.2.0-25-generic
linux-image-3.2.0-26-generic
linux-image-3.2.0-27-generic
linux-image-3.2.0-29-generic
linux-image-3.2.0-30-generic
linux-image-3.2.0-31-generic
linux-image-3.2.0-32-generic
linux-image-3.2.0-33-generic
```

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3

linux-image-3.2.0-25-generic
linux-headers-3.2.0-26
linux-headers-3.2.0-26-generic
linux-image-3.2.0-26-generic
linux-headers-3.2.0-27
linux-headers-3.2.0-27-generic
linux-image-3.2.0-27-generic
linux-headers-3.2.0-29
linux-headers-3.2.0-29-generic
linux-image-3.2.0-29-generic
linux-headers-3.2.0-30
linux-headers-3.2.0-30-generic
linux-image-3.2.0-30-generic
linux-headers-3.2.0-31
linux-headers-3.2.0-31-generic
linux-image-3.2.0-31-generic
linux-headers-3.2.0-32
linux-headers-3.2.0-32-generic
linux-image-3.2.0-32-generic
linux-headers-3.2.0-33
linux-headers-3.2.0-33-generic
linux-image-3.2.0-33-generic

```

---

### Post by hotdoog on 2013-01-07
Is there a reason to keep the old kernels but not have boot potential? I can imagine only academic reasons.

Also, good idea to run aptitude or apt-get with -s option (simulation, no action) to make sure you are doing it right.

---

### Post by CharlesA on 2013-01-07
> **hotdoog said:**
> Is there a reason to keep the old kernels but not have boot potential? I can imagine only academic reasons.

Only if you run into a problem with the current kernel and need to revert to the last working one to fix the problem.

Otherwise there isn't a real reason to keep them around.

---

