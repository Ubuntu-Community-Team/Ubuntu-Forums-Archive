---
title: "file permissions ... i guess"
date: 2009-11-16
forum: Security
---

### Post by DouglasAdams on 2009-11-16
//sorted

just loaded 9.10 and it's fantastic but...
i have added an extra drive. i formatted it using gparted and labelled it as, say, "/mine"
however, when i try to copy files to it i get the error message "...cannot be copied ... do not have permissions ..." (on the new drive).
i had mounted the new drive by double clicking it and was using drag'n'drop to copy a directory from one of my other drives on display with nautilus.
i have tried doing a sudo start of nautilus from a root terminal but nautilus would not go to the "computer" level.
if i knew how to cd (?) to the new drive i guess i could use chmod 777777777 to change the permissions on the new drive - except that there aren't any files on that drive and i still wouldn't know how to alter the ownership of the new drive, which i guess is the original problem.
i am a noob on linux but i was once pretty handy on dos and this cli stuff isn't that much different - just a new dialect and i can certainly handle that as my mum was a geordie and my dad spoke lanky!
thanks for looking.

---

### Post by Salmus on 2009-11-16
Mount the partition in rw mode ... if you cannot save anything inside it then you mounted it in "read-only".

---

### Post by DouglasAdams on 2009-11-16
double clicking the drives icon in nautilus doesn't give any option to mount as read or read/write. all it does do is ask for my password. so i'd guess that should be rw.
however,
when i checked the drives permissions i got
"the permissions of ... could not be determined"

---

### Post by rookcifer on 2009-11-16
```
sudo chown username /mine 
sudo chgrp username /mine 
sudo chmod -R 700 /mine
```

That should fix it.

---

### Post by DouglasAdams on 2009-11-17
cheers rookcifer.

do i need to go to the disk drive that needs changing first?
or will those commands change all files on every [mounted?] drive?

---

### Post by DouglasAdams on 2009-11-17
problem.
it didn't work (only tried the chown command).
so i re-formatted (w/ gparted) the drive again and re-labelled it.
first attempt (see below) i tried without mounting the drive.
then i mounted it by clicking it the file browser and entering my passy.
then i did the second command (below) - still no joy.
i wondered if it might be cos i've no files on the drive (just formatted).
so i did the same on a pen drive (didn't see why it shud be different).
still the same error - see below.

```
root@Linux:/home/marvin# sudo chown marvin /mine
chown: cannot access `/mine': No such file or directory
root@Linux:/home/marvin# sudo chown marvin /mine
chown: cannot access `/mine': No such file or directory
root@Linux:/home/marvin# sudo chown marvin /64
chown: cannot access `/64': No such file or directory

```

---

### Post by XCan on 2009-11-17
Did Ubuntu really mount it into root? What is the output of ```
 df -h 
``` after you mount it by clicking on it in the file browser?

---

### Post by rookcifer on 2009-11-17
> **DouglasAdams said:**
> cheers rookcifer.

do i need to go to the disk drive that needs changing first?
or will those commands change all files on every [mounted?] drive?

The commands I provided will change ownership and the group to your user name.  The last command will set permissions on the partition so that you have permission to rwx.

It sounds like you aren't entering the proper mount point when you perform the commands.  When I put "/mine" in the command, I assumed you knew that it was just a substitute for what the partition was really named.

---

### Post by koenn on 2009-11-17
> **rookcifer said:**
> 
It sounds like you aren't entering the proper mount point when you perform the commands.  When I put "/mine" in the command, I assumed you knew that it was just a substitute for what the [s]partition[/s] mount point was really named.
this,
or you never got the disk to mount properly.

If it is mounted, you should see it in the output of ```
mount
```
post that output here, so we know what we're talking about

---

### Post by DouglasAdams on 2009-11-17
> **rookcifer said:**
> 
It sounds like you aren't entering the proper mount point when you perform the commands. When I put "/mine" in the command, I assumed you knew that it was just a substitute for what the partition was really named.
yes, i did get that. i just thought that if i renamed my real partition to the named i had used in my post it would be simpler for me to paste my commands and any replies. after all, at this point it's an empty partition so it doesn't matter what it's actually called.

```

root@Linux:/home/marvin# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              12G  2.6G  8.7G  24% /
udev                  1.7G  360K  1.7G   1% /dev
none                  1.7G  216K  1.7G   1% /dev/shm
none                  1.7G  284K  1.7G   1% /var/run
none                  1.7G  4.0K  1.7G   1% /var/lock
none                  1.7G     0  1.7G   0% /lib/init/rw
/dev/sda2             251M   27M  211M  12% /boot
/dev/sda1             7.9G  4.0K  7.9G   1% /windows
/dev/sda5              45G   15G   28G  36% /home
/dev/sda6             651G  198M  618G   1% /media/_mine
``````

root@Linux:/home/marvin# mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /boot type ext4 (rw)
/dev/sda1 on /windows type vfat (rw,utf8,umask=007,gid=46)
/dev/sda5 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marvin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marvin)
/dev/sda6 on /media/_mine type ext3 (rw,nosuid,nodev,uhelper=devkit)
root@Linux:/home/marvin# 
``````

/dev/sda6             651G  198M  618G   1% /media/_mine
/dev/sda6 on /media/_mine type ext3 (rw,nosuid,nodev,uhelper=devkit)
```N.B.
i had labelled the partition using gparted as /mine not _mine

is there something wrong with having a label starting with a "/"  ??
should i try the originally posted commands using the name "_mine"
or is it better to first rename the partition to something that is not "changed" by ... whatever did change it???

---

### Post by koenn on 2009-11-18
> **DouglasAdams said:**
> 
should i try the originally posted commands using the name **/media/_mine**

this

---

### Post by DouglasAdams on 2009-11-18
> **koenn said:**
> this

??
"this"
??
ru saying that the underscore is "special" in Linux.
but why did it change the /mine to _mine?
maybe the underscore is set invisabilty cloak to on?
wow, long time since i last saw that in an os (mainframe techie in a previous life).
plz clarify ... no, not the butter, about the underscore ... or "this"    :)

---

### Post by QLee on 2009-11-18
DouglasAdams,

Why are you logged on as root in marvin's home folder? Are you aware of the implications of this?

And, how did you get logged in as root?

---

### Post by XCan on 2009-11-18
> **DouglasAdams said:**
> ??
"this"
??
ru saying that the underscore is "special" in Linux.
but why did it change the /mine to _mine?
maybe the underscore is set invisabilty cloak to on?
wow, long time since i last saw that in an os (mainframe techie in a previous life).
plz clarify ... no, not the butter, about the underscore ... or "this"    :)

When you click on the hdd in Nautilus, it mounts the hdd into /media/_mine and not /mine. Hence you need to update your commands accordingly, i.e.,
```

sudo chown username /media/_mine 
sudo chgrp username /media/_mine
sudo chmod -R 700 /media/_mine

```

---

### Post by koenn on 2009-11-18
> **XCan said:**
> When you click on the hdd in Nautilus, it mounts the hdd into /media/_mine and not /mine. ... 

which can be seen in the output of the mount command :

```
/dev/sda6 on /media/_mine type ext3 (rw,nosuid,nodev,uhelper=devkit)
```

---

### Post by DouglasAdams on 2009-11-18
> **koenn said:**
> which can be seen in the output of the mount command :
```
/dev/sda6 on /media/_mine type ext3 (rw,nosuid,nodev,uhelper=devkit)
```

yeah, i did notice _mine in the output. that's why i asked:

> **DouglasAdams said:**
> N.B.
i had labelled the partition using gparted as /mine not _mine
is there something wrong with having a label starting with a "/" ??
should i try the originally posted commands using the name "_mine"
or is it better to first rename the partition to something that is not "changed" by ... whatever did change it???

however, obvious question(s) i didn't ask, why doesn't "it" change partition names such as /boot, /, /home
- is it just cos these are "reserved" names?
- is there a list of these "reserved" names (apart from the obvious) that i should avoid?

> **QLee said:**
> DouglasAdams,
1) Why are you logged on as root in marvin's home folder?
2) Are you aware of the implications of this?
3) And, how did you get logged in as root?

1) i am not logged in as root.
2) yes, i am aware and 
   a) that's why i would not do it
   b) that's what i first liked about distro's such as ubuntu not having a root logon
3) see my 2b (above) - afaik

ok, to avoid all the name changing thing, i have re-labelled the partition to simply "mine"
- although i really would appreciate answers to the questions i asked it.

then i tried the commands rookcifer / xcan gave:

```
root@Linux:/home/marvin# sudo chown marvin /media/mine
root@Linux:/home/marvin# sudo chgrp marvin /media/mine
root@Linux:/home/marvin# sudo chmod -R 700 /media/mine
root@Linux:/home/marvin# 

```

does that mean that they worked?

---

### Post by rookcifer on 2009-11-18
> **DouglasAdams said:**
> 
```
root@Linux:/home/marvin# sudo chown marvin /media/mine
root@Linux:/home/marvin# sudo chgrp marvin /media/mine
root@Linux:/home/marvin# sudo chmod -R 700 /media/mine
root@Linux:/home/marvin# 

```

does that mean that they worked?
```

ls -l /media/mine
```

If you see your username as both the owner and group and permissions set to drwx------ then yes it worked.

---

### Post by DouglasAdams on 2009-11-19
yes, yes, YES!
sorry about the meg ryan impression.
everything seems great! i have got my bits set as you said and you [all of you] are just amazing.
i'd still like to know "when" partition names starting with a slash will be changed.
if some names (other than the few obvious one's) are reserved?
are there any other special characters that should [probably] be avoided?
should i be using terminal or root terminal for root type commands?

also, is there a place you would recommend for a noob wanting to know some cli commands please?
thanks again for your time.

---

### Post by QLee on 2009-11-19
[QUOTE=DouglasAdams]
1) i am not logged in as root.
2) yes, i am aware and 
   a) that's why i would not do it
   b) that's what i first liked about distro's such as ubuntu not having a root logon
3) see my 2b (above) - afaik

```
root@Linux:/home/marvin# sudo chown marvin /media/mine
root@Linux:/home/marvin# sudo chgrp marvin /media/mine
root@Linux:/home/marvin# sudo chmod -R 700 /media/mine
root@Linux:/home/marvin# 

```
[/QUOTE]

Well, that seems to indicate differently, notice the root prompt.

Partition labels can have a "/", as a matter of fact I have one that is labeled exactly that "/".

---

### Post by DouglasAdams on 2009-11-19
> **QLee said:**
> Well, that seems to indicate differently, notice the root prompt.

i'm not an expert but ...
the root prefix seems to be when i was using the **root terminal**.
please read back, i ask if i should be using that terminal or the "ordinary" one for root type commands.

> **QLee said:**
> Partition labels can have a "/", as a matter of fact I have one that is labeled exactly that "/".
yes, we all do. i'm no expert but the "/" is the "/root" directory.
you may also have other directories beginning with the slash character, e.g. "/home"
thing is, when i named **my own** dir beginning with a slash, the system seems to have changed it.

---

### Post by QLee on 2009-11-19
[QUOTE=DouglasAdams]i'm not an expert but ...
the root prefix seems to be when i was using the **root terminal**.
please read back, i ask if i should be using that terminal or the "ordinary" one for root type commands.[/QUOTE]

You should have been using your user terminal, that was the purpose of using the sudo with the command you wanted to execute with root permissions.

When you have a root terminal open you are operating with root permissions in your user environment, that has the potential of altering permissions on files so that the user can no longer use them, not recommended.


[QUOTE=DouglasAdams]yes, we all do. i'm no expert but the "/" is the "/root" directory.
you may also have other directories beginning with the slash character, e.g. "/home"
thing is, when i named **my own** dir beginning with a slash, the system seems to have changed it.[/QUOTE]
I stated I have a partition with the label /, what in Windows would be the drive name. That is what I thought you were asking about, a partition name.

The root of the filesystem, the / you are mentioning is part of the filesystem, that is where partitions (volumes; drives) are mounted, they are mounted in the filesystem with the name you have given them at mount, that does not have to be the same as the name of the partition (label).

---

### Post by DouglasAdams on 2009-11-19
> **QLee said:**
> You should have been using your user terminal, that was the purpose of using the sudo with the command you wanted to execute with root permissions.
When you have a root terminal open you are operating with root permissions in your user environment, that has the potential of altering permissions on files so that the user can no longer use them, not recommended.

this is exactly why i asked which one i should be using, so thanks for that.
however, it does sort of beg the question, why are both terminals just as easy to access? wouldn't it be an idea to, at least, make the root terminal more difficult to use in error? or even have some sort of warning to warn of the possible dangers?

> **QLee said:**
> 
I stated I have a partition with the label /, what in Windows would be the drive name. That is what I thought you were asking about, a partition name.
The root of the filesystem, the / you are mentioning is part of the filesystem, that is where partitions (volumes; drives) are mounted, they are mounted in the filesystem with the name you have given them at mount, that does not have to be the same as the name of the partition (label).

i'm a simple person and very easily confused. consequently, for the sake of simplicity, i wanted to do my best to keep my partition names the same as my mount points. this is why i need to know why it does not change the disk label "/home" when it is used for the "/home" mount point yet it did change, for example, the label "/home2", which i planned to use as a backup copy and overflow of the "/home" mount.
which names are "reserved" and would have there first char changed from "/" to "_". is there a list?

---

### Post by QLee on 2009-11-20
[QUOTE=DouglasAdams]this is exactly why i asked which one i should be using, so thanks for that.
however, it does sort of beg the question, why are both terminals just as easy to access? wouldn't it be an idea to, at least, make the root terminal more difficult to use in error? or even have some sort of warning to warn of the possible dangers?[/QUOTE]

It really isn't as easy to get a root terminal open as a user terminal, you must have followed some piece of advice to manage it, not all advice is created equal and some advice may be misunderstood by the person using it and thus cause a problem, that happens a lot here in the forums where user are helping users and everyone has different skill levels and ability to communicate. As a general rule one should consider reading and understanding any commands they are going to use before actually typing them into a terminal. There are manual pages for commands, I always recommend that people use them and I don't mean it in the sense of RTFM. In this specific case, having a root terminal as you did for those change permissions isn't really a problem for what you wanted to do. However, because you are obviously new at this I wanted to caution you for the future.

You might want to have a look at this link to Ubuntu community documentation, it could be a start:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Probably more people will chime in here with links to good information, here are a couple more:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)



[QUOTE=DouglasAdams]i'm a simple person and very easily confused. consequently, for the sake of simplicity, i wanted to do my best to keep my partition names the same as my mount points. this is why i need to know why it does not change the disk label "/home" when it is used for the "/home" mount point yet it did change, for example, the label "/home2", which i planned to use as a backup copy and overflow of the "/home" mount.
which names are "reserved" and would have there first char changed from "/" to "_". is there a list?[/QUOTE]

I understand how these new concepts can seem difficult at first. 

*How* you did, whatever it is you did, isn't going to be easy for us third parties to explain to you as we weren't looking over your shoulder as you did it.

It strikes me that you might still be somewhat confused about labels, the label is the name of the partition (like the drive name in Windows), in this case the one you gave it when you formatted. The mount point (which it seems you are still thinking of as a "name", really isn't a name, it is a location in the file system and that location is where you can choose to mount a partition/volume/drive (actually we are mounting filesystems rather than drives but I'm trying to keep this simple). In GNU/Linux It all becomes one big filesystem, not separate drives like you might be familar with if you've been using Windows. You will want to investigate "mounting" in your reading.

As I mentioned previously, you *can* *label* (name) a partition with a / character, as in your example /home2. That was your question.

Good luck.

---

### Post by DouglasAdams on 2009-11-20
> **QLee said:**
> It really isn't as easy to get a root terminal open as a user terminal

root terminal:
apps > system tools (bottom option) > root terminal (bottom option)
ordinary terminal
apps > accessories (top option) > terminal (next to bottom option)
i would personally say that the ordinary terminal is actually slightly harder to find

> **QLee said:**
> 
I wanted to caution you for the future.

caution accepted and appreciated. as i said, that is why i asked.

> **QLee said:**
> 
It strikes me that you might still be somewhat confused about labels, the label is the name of the partition (like the drive name in Windows), in this case the one you gave it when you formatted.
no, really. i do understand exactly what you are saying about drive labels (names given during formatting) and mount points, file systems

> **QLee said:**
> 
The mount point (which it seems you are still thinking of as a "name", really isn't a name, it is a location in the file system and that location is where you can choose to mount a partition/volume/drive (actually we are mounting filesystems rather than drives but I'm trying to keep this simple).

yes, i do totally understand. i could mount the "/root" file system on a drive named "/home" if i wanted to. but i wanted to keep everything simple. hence, i was trying to mount the file system "/root" onto a drive, well partition really, labelled "/" and the file system "/home" on a partition named "/home" - this just seemed easier to me.
but i also wanted a [larger] "second home" directory. somewhere that i could make a copy my real "/home" file system as well as somewhere i could "archive" files that i no longer needed to access but still wish to retain. the idea being that if my "/home" file system was really massive then access to any file on it would be slower than if it was kept to a more reasonable size.
**this is the point to look over my shoulder**
so i labelled this huge archive partition "/home2" but when i mounted it (by clicking it) it's file system name became "_home2"
from looking at what i had already done with the "required" file systems, i.e. "/home" & "/" i had expected it to use the partition name for the mount.

> **QLee said:**
> 
In GNU/Linux It all becomes one big filesystem, not separate drives like you might be familar with if you've been using Windows
"one big filesystem" ??
i understand this to mean that if /home is running short of space then it can use some of /root ... surely not. what am i not understanding here?
aside: in windows i always kept the installation away from (i.e. on a different drive) the main part of the swap file plus all the temp files i could re-direct. plus i kept my actual data on another totally different drive/partition from everything else.
the ideal for my Linux system would be root and home on different drive/partitions (no problems if you want to totally re-install); a secondary "archived" home type area and my downloads going to yet another drive/partition. plus drive/partition names reflecting their usage, i.e. same as mount points.
i have acheived most of this now (because of your help). yes, i am using "home2 instead of "/home2" but that doesn't matter.
my only outstanding "wish" is to be able to move the default download location from
/home/[username]/downloads
to, say:
/downloads
but i can live with that

> **QLee said:**
> 
You will want to investigate "mounting" in your reading.

i most certainly will.
and i will resist my childish urge to make some sexual joke too  :)

> **QLee said:**
> 
As I mentioned previously, you *can* *label* (name) a partition with a / character, as in your example /home2. 

yes, i did.
However,
when a partition labelled /home2 is mounted the mount point becomes "_home2"

thanks again. i really do appreciate all your help.

---

### Post by QLee on 2009-11-20
> **DouglasAdams]
yes, i do totally understand. i could mount the "/root" file system on a drive named "/home" if i wanted to. but i wanted to keep everything simple. hence, i was trying to mount the file system "/root" onto a drive, well partition really, labelled "/" and the file system "/home" on a partition named "/home" - this just seemed easier to me.[/QUOTE]

That "/root" you mentioned is root's home folder, not the "/" you think it is. It is a bit unfortunate that / also often referred to as "root" and that has the potential to confuse.

[QUOTE=DouglasAdams]"one big filesystem" ??[/QUOTE]
Yup.

[QUOTE=DouglasAdams]i understand this to mean that if /home is running short of space then it can use some of /root ... surely not.[/QUOTE]

Not automagically, unless you are using LVM (there's another search keyword for you) 

[QUOTE=DouglasAdams]what am i not understanding here?[/QUOTE]

Again, it difficult to impossible for me to know what *you* don't understand.

[QUOTE=DouglasAdams]aside: in windows i always kept the installation away from (i.e. on a different drive) the main part of the swap file plus all the temp files i could re-direct. plus i kept my actual data on another totally different drive/partition from everything else.[/QUOTE]

Yup, but Ubuntu isn't Windows and will reguire some re-evaluation and adjustment of method. All that you detail could be done here but some of it isn't necessary. One example, temp files go to a "temp" location, which gets cleared at your next boot, no need to try to "outsmart" Ubuntu, it works well.

[QUOTE=DouglasAdams]the ideal for my Linux system would be root and home on different drive/partitions (no problems if you want to totally re-install) said:**
> 

Yup, lots of us do it that way too. I recommend it. It is possible to do it without re-installing, however, it a bit advanced until you understand the filesystem well enough to avoid mistakes.

[QUOTE=DouglasAdams]
/home/[username]/downloads
to, say:
/downloads
but i can live with that

Well, you'd have permissions to work with it in ~home (your home - /home/[username]/downloads) and at /downloads you would have to do some changes to to permissions and/or the way you mount it if you wanted your user to have all access.


[QUOTE=DouglasAdams]
and i will resist my childish urge to make some sexual joke too  :)
[/QUOTE]
Odd, it came through here. (see I have a sense of humour too, I just prefer to be serious in help forums)


[QUOTE=DouglasAdams]However, when a partition labelled /home2 is mounted the mount point becomes "_home2"[/QUOTE]

If you let the system mount it for you, if you chose to mount it at boot time through "fstab" (filesystem table) you could have more control. (Aha! get ready for another keyword combo, "fstab mounting"

[QUOTE=DouglasAdams]thanks again. i really do appreciate all your help.[/QUOTE]

Well, I imagine a moderator is going to come along and move this to another sub forum, Security probably isn't the appropriate sub forum for this beginner thread.

I think you'll be fine once you digest the documentation and someone here can help you with your specific questions.

---

### Post by DouglasAdams on 2009-11-20
it's getting rather long so i'll mss the quotes.

/root
no, that's what i thought it was - i was being way too simplistic with the name.
and, you're right, i was saying /root to mean /
let's say / not /root

"one big filesystem" ??
ok, i still can't get to grips with this one. lets wait until i've done some reading.

LVM
i almost chose a distro as it offered LVM, so i did the reading then.
can't remember the specifics but LVM was way ahead of the curve in my opinion
- possibly a little too much so. therefore i didn't end up there.

for me to know what *you* don't understand
and difficult for me to explain it for the same reason.

reguire some re-evaluation
but it's clear that my windows premise of keeping system and personal files apart is still valid. 

It is possible to do it without re-installing, however, it a bit advanced until you understand the filesystem well enough to avoid mistakes.
i had a problem my windows system and decided to do a re-build ... upgrade ... eventually, replace everything. i also decided to to bite the bullet and switch to Linux.
my route to karmic was:
mepis; [older] ubuntu; scientific; vector; back to mepis; mandriva; sabayon 4.2; mepis
- over a period of about 2 or 3 weeks, some distros for as little as a few hours.
then sabayon 5.0 for almost 4 weeks.
during that period i moved files from my old windows system and created various new ones, all in the same /home file system.

some changes to to permissions and/or the way you mount it
i'm the only one on this particular machine. kids have there own.
in the event of disaster, i have a fallback machine too (just installed crunchbang).
i sort of "feel" that i would also need some sort of "equate" between my new /downloads and the orig /home/[me]/downloads ... or does the mount do just that.

sorry, i'm from Notlob - home of the dead parrot sketch, peter kay, dave spikey and lots more before them.

fstab mounting
i'll read the ubuntu entry when i'm less tired.
is the gui option being too lazy?

a moderator
story of my life ... :)

I think you'll be fine
nice of you to say that

many, many thanks

---

### Post by koenn on 2009-11-21
it's not all that difficult, really. You just have to get the underlying concept right, then everything else follows logically. (I find this is often the case in Linux, that's one of the things I like about it)

In short, this is how it works: 
* you have a directory hierarchy : / , /boot, /etc, /home/johndoe, ...
* this directory tree is independent of your disks. a system with 1 partition on 1 disk can have the same directory tree as a system with 4 partitions on 1 disk, and the same as a system with 2 or more disks (even if they're not in a raid or use lvm)

* this works because you 'mount' [the contents of] a disk to a directory in the directory tree. The directory where you mount something, is called a mount point. 

so, if you have 1 disk, it's mounted to / 
/ has subdirectories, eg /home, /mnt, /opt, ... You can mount a second disk there, eg disk2 -> /home. If you now create files or subdirectories in /home, they'll physically exist on disk2 - but its path will still simply be /home/jdoe/somefile

You can essentially mount anything anywhere, but there are some conventions, best practices, traditions, and a few constraints

one of the points where you are confused is apparently the 'disk labels'. They're pretty irrelevant, except that you can mount by label in stead of by device name, i.e you can mount 'disk by label' -> mount point in stead of 'device name' -> mount point. But it's the mount points that are relevant, tthe mount points (i.e. directory names) are how you controll how the disk will be accessible in the filesystem hierarchy (and then filesystem permissions will controll *who* can access them)

You can see this in eg /etc/fstab or by running 'mount'

The other thing that probably adds to the confusion is that you let gnome or nautilus handle lots of this, and they may have their own, predefined way of of handling this. Eg. if you just point at a disk and say "mount this", you're actually leaving it up to nautilus/gnome to decide where to mount it, what the mount point should be called, etc. 
If you don't like this, do your mounting by running mount in a terminal.



here are some exercices with disks, partitions and mount points:
[http://users.telenet.be/mydotcom/howto/linux/disks1.htm](http://users.telenet.be/mydotcom/howto/linux/disks1.htm)
and on LVM : [http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)

---

### Post by DouglasAdams on 2009-11-21
your: everything else follows logically
yeah, i'm certainly not used to that.
i'm more used to a system that seems to rely on quantum physics logic, the more you think you understand windows the less you really know about it.    :)
(sorry QLee, it really is an addiction)

i first dipped my toe into the Linux pool with Lindows - how long ago is that?
certainly a long time before Ubuntu!
each time i've tried a distro, i've never had the time to persevere enough to really do anything with it and certainly never managed to get to grips with it. when i've run out of time, or run into the first tiny problem, i have always gone back to windows. it's not helped by my kids needing photoshop and me not being able to find an accounts package i like as much as my old version of quick books.
it didn't take me long to realise that, certainly for me and the way i was trying various distros, the two disk (partition) example you mention, i.e. disk2 -> /home, was the **only** way to go. ever since then, whenever i have installed windows, even on the kids windows laptops, i have partitoned the hd to allow for /, /home & /swap. and yes, i do realise that the disk "names" are irrelevant but they certainly mean a lot to ME when a machine goes down and i've not touched it for a year or more. they instantly remind me that this is where i installed windows, here is the windows data, this is for the windows pagefile ... and likewise for Linux. therefore, it might be "irrelevant" to Ubuntu, it might be "irrelevant" to any distro, it might even be "irrelevant" to you but, in my experience, it's always been a huge help!

i also realise that i'm being really lazy by letting the file manager mount my devices **and** that it will therefore use it's own "defaults" - which might not always be what i would have preferred. but manually mounting drives wasn't an option i even considered as i want my system to totally recover itself after any crash. sorry, i do also know that Linux system don't "crash". make that ... after any reboot.
so the long term was to investigate some other way of mounting my drives and use the cheapest and nastiest method available until then.

i would love you to expand on your "conventions, best practices, traditions, and a few constraints", please.

---

### Post by koenn on 2009-11-21
> **DouglasAdams said:**
> yes, i do realise that the disk "names" are irrelevant    .... it might be "irrelevant" to Ubuntu, it might be "irrelevant" to any distro, it might even be "irrelevant" to you but, in my experience, it's always been a huge help!
they me be relevant to you, but you can't expect an operating system to read your mind. 

> **DouglasAdams said:**
> 
...  manually mounting drives wasn't an option i even considered as i want my system to totally recover itself after any crash.
that's why you list mounts in /etc/fstab, so they'll be established automatically every time you boot.
eg (simplified for clarity)
```

# <file system> <mount point>   <type>  <options>       
/dev/sda1        /               ext3    relatime,errors=remount-ro
/dev/sda5        /home           ext3    relatime 
      
/dev/sda6       none            swap    sw 
            
/dev/scd0       /media/cdrom0   udf,iso9660    user,noauto,exec,utf8 
/dev/fd0        /media/floppy0  auto           rw,user,noauto,exec,utf8 

```


> **DouglasAdams said:**
> 
i would love you to expand on your "conventions, best practices, traditions, and a few constraints", please.
Here are a few examples:

constraints: 
some files that are needed by the system during startup must be on the "/" partition so the system can see them before it mounts the other partitions. /etc is one of those. Makes sense, no ?


traditions and conventions:

the top level directories have traditional names (/etc, /boot, /var) and most programs and system components expect it to be that way. How ever, that doesn't stop you from creating your own, eg /data. 

removable media are usually mounted under /media.

devices are known to the kernel through device names that are represented as files in /dev, eg a disk would be named /dev/hda and a partition on it would be /dev/hda1 or /dev/hda2. That would be /dev/sda etc for devices that are used through a scsi driver. 
Traditionally, you'd use these names to mount the disks, but you can also mount them by UID (or by label, I think)

and so on.

best practices:
when given a large enough disk, it makes sense to have a separate partition for /home on a desktop system. Or even a separate disk. This allows you to reinstall or migrate the system (on / ) without loosing user data and preference settings

Similarly, on servers, it is not unusual that /tmp, /var/log, /srv, ... have their own dedicated partitions, disks, or volumes. The rationale,  design and implementation depends on the circumstances and the exact role of the server in question. Eg, if you do extensive logging, you don't want the server to crash or hang because the logs fill up all available space on the system disk.
Having a server's data (eg the web sites on a web server, the databases of a database server) can help in backup- and disaster recovery strategies - similar to the separate /home for desktop systems 
There are some performance benefits and caveats associated with this as well. 

You can also make a distinction between which parts you need to have rw, which parts you prefer to mount ro, or wich volumes you'd rather see mounted with a 'no exec'
and so on.

But as always, when you understand the underlying concepts and think through the consequences, you can come up with your on 'ideal' solutions.

---

### Post by DouglasAdams on 2009-11-21
> **koenn said:**
> ... you can't expect an operating system to read your mind.
i never did expect this.
however, i also never expected it to ***change*** what i had done,
i.e. /home2 became _home2
i **would** have expected a "lesser operating system" to make changes depending on time of the month, moon, tides, wind direction, ... anything!
yes, i now see what changed it and how to stop that happening but, when i originally asked, it looked like some sort of possible fault.

> **koenn said:**
> 
that's why you list mounts in /etc/fstab, so they'll be established automatically every time you boot.
and that was my long term ideal but, as i said, i was just looking for a cheap & nasty, get me going as quickly as possible with the least possible work.

clearly, fstab is he way to go and, remember i'm saying this before i've finished reading about how to do this, i will be going down that route.

> **koenn said:**
> 
Here are a few examples:

thanks. yes, some do seem obvious.
others i've also got to grips with some time ago, e.g. /dev/[names]
i also find it simple to appreciate, due to my mainframe experience, what you mentioned about web/database locations plus backup and disaster recovery strategies. i am not saying i could sit down and type the necessary cli but i certainly understand the logic of why these things should be done.

i have been thinking a lot about my 'ideal' solution for a long time.
i've worked with computers since 1974, so "i know the questions to ask".
i know that i don't have the knowledge to implement my ideas but, with the help i've received here, and the reading material you've highlighted, i'm sure i will be able to acheive my ideals - not that my "ideal" might not change a little as i learn more.
i've already had one such revelation, that i certainly don't want my default download directory to be within /home - it's simply far too large. there are a few other bits i would at least like to exclude from my backups of /home too. maybe even move those too (unlikely).

anyway,
thanks for you help,
thanks for your time,
thanks for being there when i needed help.

p.s.
i would love a pointer to the master class on your "conventions, best practices, traditions, and a few constraints"

---

### Post by koenn on 2009-11-21
this is a  good start:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
especially the general background info, and the 'purpose' and "rationale' sections
I'm not aware of any comprehensive consolidated "partitions and mounting" resource online, but you can pick up quite a few specifics from howtos (eg a good apache howto will have sensible things to say about partitions and mount options for apache servers and web severs in general).
Other than that, i guess  you'll have to look at book stores for Linux or Unix System Administrator guides and manuals.

---

### Post by QLee on 2009-11-21
> **DouglasAdams said:**
> i never did expect this.
however, i also never expected it to ***change*** what i had done,

Gosh man, when you mentioned a few posts back that you were lazy I didn't understand the full ramifications of your statement.

We've been explaining things and giving you links for a while now and yet you still come back with general questions, rather than specific ones about something you read that you didn't understand, it's as if you don't read what we suggest. And, I expected you to post new threads in a more appropriate sub forum with these beginner questions, that's why I mentioned that, however, it's your choice.

I'll help you to answer this one last question for yourself. I assume the "it" you mention is the system. Well, did "it" actually change your label of the partition?

When you enter sudo blkid, what is the "label" of that partition? If I remember correctly it was your sda6, if so you could just enter sudo blkid /dev/sda6.

--
Edit: Well, maybe you aren't online any longer, I'm not usually here at this time either but I was hanging around for your answer, so we could go on to step 2.


I'm going to go out on a limb, I'm going to assume (oooh, I know how dangerous that is and I could be wrong) that the system did not change the label, so we have to try to figure out how what you have detailed in your post could have happened. Below is the logic I used to come up with one possibility that seems to fit the data.


Okay, so when you let the system mount mount drives for you, does it appear that the system usually uses the drive label (name) as the dir (folder) name in the path under which it is mounted?  

If the answer to that appears to be yes, could the fact that a "/" character is a character not allowed in a directory (folder) name mean that the system has to handle it differently, when you have chosen to label your drive with that specific character in a name that you want to click to mount? 

You assured us you understood  disk labels and mount points, however, I think you might not totally understand that a mount point is not the same as a drive name, a mount point is a location in a filesystem. In fstab you could choose to have the system, at boot time, mount LABEL=/mine at location /media/mine, if that is what you want or you could do the same mounting with the UUID or the device node, it just requires understanding how to do fstab mounting. 
See if this helps: 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

This is sort of an old book by now and not Ubuntu specific, it still might have some information that would be useful for you. You could download in pdf or html and use it until you have the chance and/or funds to buy something newer.
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

It usually more useful to keep the number of questions asked in a post to one or two and not create these long threads that are more difficult to search through. Aha! That made me think of more advice, learn to use the search function of the forum, many of your questions have probably been asked and answered previously  Note: You need not take any of my advice, it's just my opinion.

Since I know you have a sense of humour, I will mention that old mainframe guys are some of the hardest to help, they have preconceptions that get in the way of help. I too was a mainframe guy when the first PCs came out, retired now, you probably are too. Us old mainframe guys can learn, the process is similar to pulling teeth. <chuckle>

I really do believe you will be fine once you digest the documentation.

"Goodbye, and thanks for all the fish."

---

### Post by DouglasAdams on 2009-11-21
> **QLee said:**
> Gosh man, when you mentioned a few posts back that you were lazy I didn't understand the full ramifications of your statement.
tbh, a lot of my posts have not really been asking but trying to say that i do understand various bits
 
> **QLee said:**
> 
could the fact that a "/" character is a character not allowed in a directory (folder) name mean that the system has to handle it differently
a meg ryan moment!
and this is exactly why i asked:
> **DouglasAdams said:**
> is there something wrong with having a label starting with a "/" ??
...
or is it better to first rename the partition to something that is not "changed" by ... whatever did change it???
initially i **had** the idea (but not now), since Linux seems to like it's filesystems starting with a "/" then i would have all my Linux filesystem names start with a slash and, as i mentioned, the drive that filesystem was mounted on named exactly the same. windows labels would not begin with a slash. it seemed a simple way to quickly identify what went where even if i was using something like a ghost disk.

> **QLee said:**
> 
You assured us you understood disk labels and mount points
i do, really.
but i'm only just beginning to learn this new foreign language. i'm going to get my tenses wrong. i've not a clue if a table is male of female. therefore i'm usually having far more problems explaining things to you than i have understanding your replies. 

> **QLee said:**
> 
number of questions
point taken. but, as i said to start with ... etc

> **QLee said:**
> 
they have preconceptions
other than keeping system files and user data apart the only real baggage i carry is that data must be backed up and the easiest way to facilitate doing that is to structure (locate) your data correctly in the first place.

anyway, thanks for all your superb help.

//sorted

---

### Post by QLee on 2009-11-22
[QUOTE=DouglasAdams]
initially i **had** the idea (but not now), since Linux seems to like it's filesystems starting with a "/" then i would have all my Linux filesystem names start with a slash and, as i mentioned, the drive that filesystem was mounted on named exactly the same. windows labels would not begin with a slash. it seemed a simple way to quickly identify what went where even if i was using something like a ghost disk.[/QUOTE]

Well, it isn't so much that GNU/Linux "likes" it's filesystems starting with a / (and you won't find a partition labeled / in most systems) , it's the way "a" filesystem starts, at the root of the filesystem, then there are sub locations off of that.

As I mentioned, Ubuntu is not Windows, the MS system mounts it's filesystem according to how you have structured the partitions on the various physical disks using the concept of drive letter, without the finer-grain control of locating data where the system admin wants it as you can do with Ubuntu.

Poster koenn, gave you a link to a page about the Linux Filesystem Hierarchy, if you didn't like that one here is another from The Linux Documentation Project:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

[QUOTE=DouglasAdams]other than keeping system files and user data apart the only real baggage i carry is that data must be backed up and the easiest way to facilitate doing that is to structure (locate) your data correctly in the first place.[/QUOTE]

Well Doug, the preconception I was most thinking about with old mainframe guys is that we usually assume (because of our age and experience) that we *know* computers and *should* understand this new stuff without starting at square one and reading the documentation first.


[QUOTE=DouglasAdams]//sorted[/QUOTE]

One of the things that helps to make the forum better is, when the questions of a post have been answered, the original poster goes back and edits the subject line of the first post to include [SOLVED] or something like that, I'm sure you can see the sense in that for the time one is searching the archives.

Glad you're off to a good start, you'll probably be answering questions here before long.

---

### Post by DouglasAdams on 2009-11-22
> **QLee said:**
> Well, it isn't so much that GNU/Linux "likes" it's filesystems starting
yeah, this is as a result of my "school boy french" again.

> **QLee said:**
> 
without the finer-grain control of locating data where the system admin wants it
i think you would be surprised just how much fairly fine control i've been using on windows as a matter of course for years. certainly user data, programs (some, not all), temp files and obviously the swap file.
it might not be as fine as the control i can already appreciate you have with Linux but there is always room for a little innovation.

> **QLee said:**
> 
koenn, gave you a link
i like, i like ... i just needed some sleep ... and i have been given a lot of links to work thru.

> **QLee said:**
> 
understand this new stuff without starting at square one and reading the documentation first
certainly not. i just didn't see why i would need to read up on clicking to mount a drive.
when i had the initial "permission" problem i thought it was cos i had clicked with my left hand
(just joking)

> **QLee said:**
> 
original poster goes back and edits the subject line of the first post
dunno if it's just me but i didn't (and still don't when i just tried it again) have access to the subject line of my first post. i figured that typing //sorted (cos i'm a common working class northerner) before the text of my first post was the nearest i could get to doing what you were suggesting. 
actually, i tend to prefer to keep away from [] pairs ... just in case someone in the future ...

//sorted

---

### Post by QLee on 2009-11-22
[QUOTE=DouglasAdams]i think you would be surprised just how much fairly fine control i've been using on windows as a matter of course for years. certainly user data, programs (some, not all), temp files and obviously the swap file.
it might not be as fine as the control i can already appreciate you have with Linux but there is always room for a little innovation.[/QUOTE]

Nah, I probably do understand, I likely did something similar when I administrated Windows systems. As we have discussed previously, because of the differences between OS, one has to amend their approach and one can only do that from knowledge and/or experience.


[QUOTE=DouglasAdams]dunno if it's just me but i didn't (and still don't when i just tried it again) have access to the subject line of my first post. i figured that typing //sorted (cos i'm a common working class northerner) before the text of my first post was the nearest i could get to doing what you were suggesting. 
actually, i tend to prefer to keep away from [] pairs ... just in case someone in the future ...

//sorted[/QUOTE]

The "edit" button down near the right corner of the post should work. The subject line is called "Title" in the forum.

---

### Post by DouglasAdams on 2009-11-22
> **QLee said:**
> one has to amend their approach and one can only do that from knowledge and/or experience.
yup, i see that

> **QLee said:**
> 
The "edit" button down near the right corner of the post should work. The subject line is called "Title" in the forum.
i already used the edit button a few times to put //solved into posts but it did **not** allow me to update the title. however, i've just done it again and noticed an "advanced" button which does allow access to the modification of the thread title which now says "//sorted       {old thread title}".

---

### Post by QLee on 2009-11-22
[QUOTE=DouglasAdams]yup, i see that[/QUOTE]
Oui, mon ami, we have hammered that point for a few days, eh?

My thought is that you "get it", bon. Working with you has been a good experience for me, not always deadly serious but always respectful, just the way Ubuntu forums are supposed to work

---

### Post by DouglasAdams on 2009-11-22
what happened?

---

### Post by DouglasAdams on 2009-11-22
QLee, it's great to be made to feel so welcome.
somehow, when Ubuntu was 1st released and i discovered that it had *Canonical behind it,* i just knew i would end up using it.
i only wish i had stuck with it from day one.

---

### Post by QLee on 2009-11-22
> **DouglasAdams said:**
> QLee, it's great to be made to feel so welcome.

Yeah, and I haven't even signed the Code of Conduct. 

It's just clear that it's easier to help someone who feels welcome and comfortable so they can concentrate on what they are trying to learn. 

Enough of this lovefest, others are probably becoming sick. <G>

---

### Post by cariboo on 2009-11-22
I marked this thread solved, to mark the thread solved, use the Thread Tools at the top of the page.

---

### Post by DouglasAdams on 2009-11-23
> **cariboo907 said:**
> I marked this thread solved, to mark the thread solved, use the Thread Tools at the top of the page.

cheers cariboo, i see that now - my old eyes aren't what they were  :)

---

