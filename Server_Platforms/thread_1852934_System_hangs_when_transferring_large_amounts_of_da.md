---
title: "System hangs when transferring large amounts of data"
date: 2011-10-01
forum: Server Platforms
---

### Post by ronzo on 2011-10-01
I am using the 64bit server edition of Natty (11.04). When I try to transfer large amounts (hundreds of gigabytes) of data (using rsync or tar) to an external USB disk or to an ISCSI device, the system hangs at some point. 

The only option at this point is pressing the power button for a few secs to shut it down (what almost ruined the filesystem two weeks ago... so I hate to be forced to shut it down that way...). [I have no monitor connected to the server, so I cannot tell if any messages are displayed before it hangs. Pinging or ssh-ing from another machine does not work.]

After having restarted, I cannot find anything that would give me a hint in the log files. :confused:

So... how can I find out what is going on in order to resolve that nasty problem? Any tips/hints/etc. are very much appreciated!

Thanks a lot in advance for your answers!

---

### Post by ian dobson on 2011-10-01
Hi,

Sounds as if it could be a hardware problem.

What happens when you put the disk subsystem under heavy load (multiple dd's). If possible open the file system as readonly (edit your fstab) as long as it's not root. That should reduce the chance of corruption.

maybe running sudo watch --interval=1 'dmesg|tail -40' while hitting the file system might show something.

Regards
Ian Dobson

---

### Post by Jonathan L on 2011-10-01
> **ronzo said:**
> I am using the 64bit server edition of Natty (11.04). When I try to transfer large amounts (hundreds of gigabytes) of data (using rsync or tar) to an external USB disk or to an ISCSI device, the system hangs at some point. 

The only option at this point is pressing the power button for a few secs to shut it down (what almost ruined the filesystem two weeks ago... so I hate to be forced to shut it down that way...). [I have no monitor connected to the server, so I cannot tell if any messages are displayed before it hangs. Pinging or ssh-ing from another machine does not work.]

After having restarted, I cannot find anything that would give me a hint in the log files. :confused:

So... how can I find out what is going on in order to resolve that nasty problem? Any tips/hints/etc. are very much appreciated!

Thanks a lot in advance for your answers!

Hi Ronzo

I'd suggest adjusting your logging settings (ie add /etc/rsyslog.d/99-newfile.conf) to be very verbose into a new logfile, and then try getting it to hang on purpose.  With a spot of luck, and the verbosity high enough, you'll spot something that happens just before the hang.

Just a suggestion.

Kind regards,
Jonathan.

---

### Post by ian dobson on 2011-10-02
Hi,

Also run a memtest (from grub boot menu). You'll need to attach a keyboard/monitor to the server to see whats going on.

Regards
Ian Dobson

---

### Post by ronzo on 2011-10-02
The dmesg-watch-combination shows results:

[136028.780022] Stack:
[136028.780022]  ffff88022fffbe00 0000805000000002 ffff88021cef79a8 000000000000
0000
[136028.780022]  0000000000001000 ffffea00048895c0 0000000000000001 ffffffffa00f
a5a0
[136028.780022]  ffff88021cef79d8 ffffffff81191862 ffff88022388fd40 000000000000
0000
[136028.780022] Call Trace:
[136028.780022]  [<ffffffffa00fa5a0>] ? xfs_get_blocks+0x0/0x20 [xfs]
[136028.780022]  [<ffffffff81191862>] alloc_buffer_head+0x22/0x50
[136028.780022]  [<ffffffff81191d1e>] alloc_page_buffers+0x3e/0xf0
[136028.780022]  [<ffffffffa00fa5a0>] ? xfs_get_blocks+0x0/0x20 [xfs]
[136028.780022]  [<ffffffff81192f12>] create_empty_buffers+0x22/0xe0
[136028.780022]  [<ffffffff81194f99>] __block_write_begin+0x429/0x570
[136028.780022]  [<ffffffff811270a5>] ? __inc_zone_page_state+0x35/0x40
[136028.780022]  [<ffffffff8110be2a>] ? add_to_page_cache_locked+0xea/0x160
[136028.780022]  [<ffffffffa00fa5a0>] ? xfs_get_blocks+0x0/0x20 [xfs]
[136028.780022]  [<ffffffff8110bf99>] ? grab_cache_page_write_begin+0x79/0xc0
[136028.780022]  [<ffffffff81194944>] ? block_write_end+0x44/0x80
[136028.780022]  [<ffffffffa00fa5a0>] ? xfs_get_blocks+0x0/0x20 [xfs]

Is that enough to tell what the problem is? For me it looks like some xfs error...

---

### Post by ian dobson on 2011-10-02
Hi,

Sound like xfs corruption or a bug in the xfs code.

Try running a xfs check, maybe it'll fix it.

I always recommend using ext4, rather than xfs. I don't know how much data you have/if it's possible to move over to ext4, but if you have the space/time maybe try creating a ext4 partition and testing that.

What was the message just above the stack: message?

Regards
Ian Dobson

---

### Post by HermanAB on 2011-10-02
Howdy,

This is a horrid bug in the latest Linux systems.  It affects all new distributions and may have something to do with cgroups.

The only solution is to boot off an old live CD in order to copy large amounts of data to a USB disk.  So don't throw those old Knoppix CDs away...

---

### Post by ian dobson on 2011-10-02
> **HermanAB said:**
> Howdy,

This is a horrid bug in the latest Linux systems.  It affects all new distributions and may have something to do with cgroups.

The only solution is to boot off an old live CD in order to copy large amounts of data to a USB disk.  So don't throw those old Knoppix CDs away...

Got any references?

Regards
Ian Dobson

---

### Post by ronzo on 2011-10-02
> **HermanAB said:**
> Howdy,

This is a horrid bug in the latest Linux systems.  It affects all new distributions and may have something to do with cgroups.

The only solution is to boot off an old live CD in order to copy large amounts of data to a USB disk.  So don't throw those old Knoppix CDs away...

What do you mean? The XFS error or transferring loads of data?

---

### Post by ronzo on 2011-10-02
> **ian dobson said:**
> Hi,

Sound like xfs corruption or a bug in the xfs code.

Try running a xfs check, maybe it'll fix it.

I always recommend using ext4, rather than xfs. I don't know how much data you have/if it's possible to move over to ext4, but if you have the space/time maybe try creating a ext4 partition and testing that.

What was the message just above the stack: message?

Regards
Ian Dobson

I'll try an XFS check (but I fear that that won't fix my problem) and try it again. I'll have to set 'tail' to show more lines...

Unfortunately, I could not read the message above the stack...

---

### Post by ronzo on 2011-10-02
Did an xfs_check (no serious errors were found) followed by an xfs_repair. Then I started rsyncing again and guess what... The system hangs again. Cannot ping or ssh it anymore. And watch/dmesg shows nothing this time...

Do you think it is still an XFS problem? What would you recommend doing next?

---

### Post by ian dobson on 2011-10-02
Hi,

As I've already said, maybe go over to ext4 or open a bug report.

Regards
Ian Dobson

---

### Post by ronzo on 2011-10-03
> **HermanAB said:**
> Howdy,

This is a horrid bug in the latest Linux systems.  It affects all new distributions and may have something to do with cgroups.

The only solution is to boot off an old live CD in order to copy large amounts of data to a USB disk.  So don't throw those old Knoppix CDs away...

Are you pointing in this direction? [http://lists.debian.org/debian-kernel/2011/03/msg01085.html](http://lists.debian.org/debian-kernel/2011/03/msg01085.html)

If yes, I'll try copying the data off the server. But where do I get an old enough LiveCD (like Knoppix 5.2)?

---

### Post by ronzo on 2012-02-09
I fear the RAID controller (3ware 9650SE-4LPML) is the one to blame...
[http://forums.storagereview.com/index.php/topic/28920-3ware-9650se-controller-resets-under-load-on-linux/page__st__80](http://forums.storagereview.com/index.php/topic/28920-3ware-9650se-controller-resets-under-load-on-linux/page__st__80)
[http://kb.lsi.com/KnowledgebaseArticle16212.aspx](http://kb.lsi.com/KnowledgebaseArticle16212.aspx)

I'll post if it was...

---

