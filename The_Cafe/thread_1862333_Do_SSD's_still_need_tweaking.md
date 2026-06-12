---
title: "Do SSD's still need tweaking?"
date: 2011-10-16
forum: The Cafe
---

### Post by wolfen69 on 2011-10-16
Are tweaks still necessary with the new kernel?

---

### Post by oldfred on 2011-10-16
You still want to change a few settings to reduce writes where not absolutely needed.

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by andrewabc on 2011-10-16
Last I checked:
You do need to edit fstab to make it do TRIM (kernel is capable of trim, but for whatever reason developers don't seem to be able to or bother detecting SSD and auto enable trim).

It should partition and align blocks correctly though. Last time (October 2009), I had to manually align blocks and create partitions which was a pain to read tutorials and spend hours trying to setup SSD with linux (win7 does trim and align automatically).

EDIT:
A big question is what SSD you have and what you plan on doing with it. if getting large SSD and not planning on keeping it over 50% full at any time, then tweaks to save on writes not as important.

---

### Post by Copper Bezel on 2011-10-16
Is any of that necessary, or even advisable, though? I mean, I've been using SSDs for almost as long as I've been using Linux (around three years) and don't know what any of those words mean. Hasn't really come up, either. Am I missing out on something? = )

---

### Post by wolfen69 on 2011-10-16
Thanks!

---

### Post by wolfen69 on 2011-10-16
Btw, after a little research, it seems that if you had a 32gb ssd and transferred 10gb a day, it would take 8 years to wear out your drive. Since I only use my netbook maybe once every couple weeks with little to no transferring of files, it seems I have nothing to worry about. But I did the discard thing anyway. Lubuntu 11.10 runs awesome on my Acer netbook with a 60gb ssd.

---

### Post by andrewabc on 2011-10-17
> **Copper Bezel said:**
> Is any of that necessary, or even advisable, though? I mean, I've been using SSDs for almost as long as I've been using Linux (around three years) and don't know what any of those words mean. Hasn't really come up, either. Am I missing out on something? = )

Yes it is necessary.

If your SSD is not aligned properly, then your write speed will be much slower and it will also wear out the SSD much faster.

TRIM keeps the SSD write speed at 90+%. Without TRIM command, if you thrash your SSD, the write speeds will be much slower.

Garbage collection in most SSD will keep speed up over time, but TRIM and alignment are also necessary to get most of your SSD. The other tweaks (write as little as possible to SSD) are not really necessary nowadays unless you either have a small SSD (30gb), or are writing say 30% of SSD capacity per day (which you shouldn't be unless you are using it in production envionment, or torrents).

Align and TRIM are two most important things when setting up SSD. Hopefully linux does both by default, but whenever this question comes up there are no definitive answers sadly. I mean what is the point of linux kernel implementing TRIM before windows had it, but for whatever reason distros are unable to detect SSD and auto enable trim? They expect users to edit fstab to enable it themselves? For something that is simple and required for SSD?

Yes it is very unlikely your SSD will run out of writes. It will fail in other ways before that ever happens.

Looks for anandtech SSD articles all the way back to 2009 for much info on how SSD work.
[Example](http://www.anandtech.com/show/2738/10)

[SSD, TRIM and IOMeter - BeHardware](http://www.behardware.com/art/imprimer/791/) - good article on TRIM. You can end up with 1/2 write speed if not using TRIM command.

---

### Post by Copper Bezel on 2011-10-18
[QUOTE=andrewabc]Align and TRIM are two most important things when setting up SSD. Hopefully linux does both by default, but whenever this question comes up there are no definitive answers sadly.[/QUOTE]

That's what wolfen was referring to, the "discard" option in fstab. It's not enabled without that.

---

### Post by CarlosinFL on 2011-10-18
So what should my /etc/fstab look like to enable TRIM with the discard option?

Here's my /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=24272462-9b08-44ea-9bc4-b64b28918a15 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=e19c5c84-e901-4177-8544-6dbb9a649a35 /boot           ext2    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=54ffa18f-48e1-4fe4-bbb7-5515420a5d43 none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=07e9781b-b0ac-4581-805f-1bc67e36dc7a none            swap    sw              0       0

```

Can someone tell me what I need to do on my / ext4 partition to enable / support TRIM?

---

### Post by Copper Bezel on 2011-10-18
Pretty sure it's just

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=24272462-9b08-44ea-9bc4-b64b28918a15 /               ext4    errors=remount-ro,discard 0       1
# /boot was on /dev/md0 during installation
UUID=e19c5c84-e901-4177-8544-6dbb9a649a35 /boot           ext2    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=54ffa18f-48e1-4fe4-bbb7-5515420a5d43 none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=07e9781b-b0ac-4581-805f-1bc67e36dc7a none            swap    sw              0       0
```

[_Here's_]("http://www.linuxquestions.org/questions/slackware-14/sackware64-current-and-ext4-and-ssd-795003/#5") an example.

---

### Post by CarlosinFL on 2011-10-18
I followed your example but the Vim sytax highlighting in 'red' makes me think somethings wrong:

*screenshot attached*

---

### Post by Copper Bezel on 2011-10-18
No space. The options are separated by only a comma.

Applied it to mine and restarted - nothing broke, anyway. Of course, there's no way to know if it's actually doing anything. = )

---

### Post by Ranko Kohime on 2011-10-18
I lean towards the paranoid side of SSD write reduction, so I've been known to sit watching **iotop**, watching for good opportunities to reduce writes.  Here's the short list:

[LIST]
[*]Set /tmp to ramdisk
[*]Install Ramlog
[*]Move and symlink web browser profiles to a properly-permissioned folder in /var/log
[*]Don't install with a swap partition, use the entire drive for /
[*]~/.xsession-errors can also be moved to the folder in /var/log
[/LIST]

---

### Post by andrewabc on 2011-10-19
> **Ranko Kohime said:**
> [LIST]

[*]Don't install with a swap partition, use the entire drive for /
[/LIST]

You can still use swap partition, when installed just set swappiness preference to 1 so it rarely uses swap. I have no idea how removing swap affects sleep/hibernate on laptops.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by wolfen69 on 2011-10-19
Also, I read that alignment is automatic if you select "use whole drive" during install setup.

---

### Post by Paqman on 2011-10-20
> **andrewabc said:**
> You can still use swap partition, when installed just set swappiness preference to 1 so it rarely uses swap. I have no idea how removing swap affects sleep/hibernate on laptops.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I tend to have swappiness set to 0 on all my machines, regardless of whether they're SSDs or old-fashioned spinny disks. If you've got plenty of RAM swap is pretty superfluous.

Some people do run without swap altogether. It won't affect suspend, but hibernate wouldn't work at all.

---

### Post by ssam on 2011-10-20
> **andrewabc said:**
> You can still use swap partition, when installed just set swappiness preference to 1 so it rarely uses swap. I have no idea how removing swap affects sleep/hibernate on laptops.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

hibernate requires enough swap to copy all of your active RAM to. having the same amount of swap as you have RAM is usually enough. however suppose you have 2GB RAM and 2GB swap, then you open enough programs to be using 2.5GB, then you will not have enough room to hibernate.

Suspend does not need swap because the RAM is kept on.

on my netbook i have a swap partition on my ssd, because sometimes i need more than 2GB of memory. if you move your /tmp into RAM then you will be even more likely to need swap.

noatime, is probably not worth the effort. in the old days (maybe 2 pr 3 years ago) every time you read a file its access time was updated which required a write to disk. this was bad for performance, and not many programs case about access time. so noatime was created to disable this. then someone invented relatime, which only updates the access time if it is older than 1 day. This is good enough for all the programs that care about access time, but removes nearly all the atime writes. relatime is now the default mode.

[https://lwn.net/Articles/244829/](https://lwn.net/Articles/244829/)

---

