---
title: "mdadm semi-broken in 8.10"
date: 2008-08-10
forum: Server Platforms
---

### Post by Ikarius on 2008-08-10
Hokay, so I just got done going through some nasty crud with my ubuntu 8.10 server, and in the process found some uglies.

Background; I was growing an md raid array (data partition only; mounted on /data- NOT a boot or root partition), and the operation was at around 10 hours and still rolling.  (estimate was 15 hours to complete).

I ended up needing to reboot the system before the md reshape completed.

Bug #1: Ubuntu hangs during startup due to the md drive with reshape in progress.  This is apparently due to the "--no-degraded" option set in /etc/udev/rules.d/85-mdadm.rules. 
The system gets to the part of loading hardware drivers, and sits there. This appears to have been reported back with relation to 7.04- see [http://ubuntuforums.org/showthread.php?t=507074&highlight=raid1]("http://ubuntuforums.org/showthread.php?t=507074&highlight=raid1")


Bug #2: Once I figured out how to get past that (ctl-alt-del, drop to root shell), I fiddled with mdadm, and recieved a message about "Failed to restore critical section for reshape, sorry." when attempting to restart the md device.  This turns out to be a bug in the version of mdadm packaged for ubuntu 8.0.4.  The mdadm distributed is release 2.6.3.  From the release notes for mdadm 2.6.4:

```
Release 2.6.4 adds a few minor bug fixes to 2.6.3

Changelog Entries:
    -   Make "--create --auto=mdp" work for non-standard device names.
    **-   Fix restarting of a 'reshape' if it was stopped in the middle.**
    -   Fix a segfault when using v1 superblock.
    -   Make --write-mostly effective when re-adding a device to an array.
    -   Various minor fixes

```

Once I compiled and replaced the system mdadm with version 2.6.4, it was able to resume the reshape.

---

### Post by fjgaude on 2008-08-10
Wow! Thanks for the info... though I've never had such a situation I'm sure others have and will. **mdadm** keeps getting better and better.

Who is going to write a comprehensive book covering all aspects of running mdadm? <smile>

---

### Post by Ikarius on 2008-08-14
And one more note on this....  After convincing mdadm to resume the reshape successfully, I went to resize the ext3 filesystem on the box.  Despite having set a stride of 16 when I created the filesystem(4k fs block, 64k RAID block), ext2online and ext2prepare both thought for some reason that my stride was -1109.  I found an undocumented (not in man page, not in use message) parameter which allowed me to specify the stride for extresize (the offline resize tool) in a changelog I found via google. 



So, all in all, I ran into one init script bug, one bug in mdadm, and a bug in the ext filesystem resizing tools.

I wasn't terribly impressed with my first Ubuntu go-round. :roll:


--Ikarius

---

### Post by fjgaude on 2008-08-14
Well, keep up the good work in finding bugs... you know Ubuntu hasn't been used much until recently as a server... it'll get better in the coming years. As far **mdadm**, I'm sold on it as a replacement for expensive raid cards.

These are the tools I've used to learn software raid:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study **/usr/share/doc/mdadm/FAQ.gz**  and **md.txt.gz**
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

The man pages only go so far, eh?

---

### Post by Ikarius on 2008-08-14
It's not the learning curve I'm having difficulty with.  It's the bugs I'm running into.  I have filed them in the Ubuntu bug system at least.  Hopefully someone will look at them and address them- they're pretty specific and concise, and they're really bugs, not feature requests.  If additional information is needed on any of the bugs I filed, I'll be happy to provide it.

---

### Post by fjgaude on 2008-08-15
Very good... **mdadm** and Ubuntu will be as good as it gets one of these days. Overall, they don't have that far to go.

---

