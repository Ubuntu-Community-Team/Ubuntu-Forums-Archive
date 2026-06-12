---
title: "Autochecking of the file-system is switched off"
date: 2013-07-03
forum: Ubuntu, Linux and OS Chat
---

### Post by sudodus on 2013-07-03
Hi everybody,

I think since Precise, autochecking the automounted filesystems is switched off. I checked in an installed instance of Saucy recently, and it was still installed without autochecking.

Is this intentional or has somebody overlooked it? After all, there is a sharp warning about it in tune2fs. See the details at the end of this post.

I usually set maximum mount count to 30, and I suggest that we switch it on in Saucy, maybe with a higher number, for example 50, or set a check interval for example once a week or once a month.

sudodus
[HR][/HR]
```
sudo tune2fs -l /dev/sdf3
```
...
Mount count:              5
Maximum mount count:      -1
Last checked: Sat Jun 15 11:39:05 2013
Check interval:           0 (<none>)
...
```
man tune2fs
```
...
-c max-mount-counts

Adjust  the  number  of  mounts  after  which  the  filesystem  will be checked by e2fsck(8).  If max-mount-counts is 0 or -1, the number of times the filesystem  is mounted will be disregarded by e2fsck(8) and the kernel.

Staggering  the  mount-counts at which filesystems are forcibly checked will avoid all filesystems being checked at one time when using journaled filesystems.

You should strongly consider the consequences of  disabling mount-count-dependent checking  entirely.   Bad  disk  drives, cables, memory, and kernel bugs could all corrupt a filesystem without marking the filesystem dirty or in error.  If you are using  journaling  on your filesystem, your filesystem will never be marked dirty, so it will not normally be checked.  A filesystem error  detected  by  the  kernel will  still  force  an  fsck on the next reboot, but it may already be too late to prevent data loss at that point.

See also the -i option for time-dependent checking.
...

---

### Post by roten on 2013-07-03
I think it was very annoying to have to wait for the auto checking. I'm happy to do it manually, when I have time for it. And I think file system corruption happens very seldom nowadays.

---

### Post by pixiq on 2013-07-03
I'd be happy to be reminded by the old auto checking. You could skip it pressing a single key. So I will try to get it working again.

---

### Post by sudodus on 2013-07-03
Yes, we can use ***tune2fs*** to activate autochecking, but I think many people, particularly newcomers, do not know about it. I think it should be active from the installation. As you wrote *pixig*, it is quite easy to skip it if you are in a hurry (and let the computer check the drive next time).

*Roten*, do you know if there is evidence, that the autochecking is no longer worth waiting for?

---

### Post by oldos2er on 2013-07-03
On Saucy right now, but I turn on FSCKFIX=YES in /etc/default/rcS on most Ubuntu installations.

---

### Post by sudodus on 2013-07-03
Thanks for the tip :-)

How does [COLOR=#000000]FSCKFIX=YES relate to the setting that can be viewed and changed with tune2fs (for example to check after 30 mounts)? Is it completely unrelated or is [/COLOR][COLOR=#000000]FSCKFIX=YES the same as setting [/COLOR]'[COLOR=#000000]Maximum mount count'=1 ?[/COLOR]

---

### Post by oldos2er on 2013-07-03
There's some explanation of it [here]("http://askubuntu.com/questions/151025/how-can-i-make-fsck-run-non-interactively-at-boot-time"). Basicly it runs fsck non-interactively, but (as far as I know) it doesn't change the frequency you set with tune2fs. If you have ext3 or ext4 partitions mounted in fstab you might need to adjust the [pass order]("https://help.ubuntu.com/community/Fstab#Pass_.28fsck_order.29") too.

---

### Post by sudodus on 2013-07-04
Thanks again :-) But I don't quite understand. Is there always a simple test nowadays (initiated from /etc/default/rcS) independent of the frequency set with tune2fs?

I ask because at least the slow checking set with tune2fs is definitely switched off (with -1) when I install new versions of Ubuntu. There will never be any such checking until I change the setting. There might be some fast checking, that I do not notice during startup.

Could it be the difference between using the option -f or not (-f to force checking even if the file system seems clean)?

```
 sudo e2fsck <device>
```
and
```
 sudo e2fsck -f <device>
```

---

### Post by oldos2er on 2013-07-04
I don't know, though I believe there is a quick check on each boot which you'll notice if you set up a text boot. I hope someone more knowledgeable will chime in.

---

### Post by sudodus on 2013-07-04
I think so (about a quick check) and hope so (that [COLOR=#000000]someone more knowledgeable will chime in)[/COLOR] too. But who will stand up and declare her/him self to be more knowledgeable than you ;-)

---

### Post by oldos2er on 2013-07-04
Ha! My google-fu gives me an expert's verisimilitude.  :)

---

