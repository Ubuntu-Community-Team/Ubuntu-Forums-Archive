---
title: "Unresponsive server"
date: 2014-06-30
forum: Server Platforms
---

### Post by Sapph1r3 on 2014-06-30
I have an ubuntu 12.04 web server whose upkeep I have inherited.
I don't know much about its setup but have been learning along the way.
I have been taught to maintain it via webmin, but have recently been able to enable my user to use putty.
Randomly this server will become unresponsive and we will be unable to reach it via webmin, putty and the samba share.
We request a hard boot as it is in a remote location.
The only thing we are able to do is ping and get a response.
Below is the output of the top command:

```
top - 11:41:49 up 26 min,  1 user,  load average: 1.07, 1.34, 1.74Mem:   2056336k total,  1531596k used,   524740k free,   296120k buffers
Swap:  3080188k total,        0k used,  3080188k free,   620024k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1107 root      20   0  164m  25m  14m S  0.0  1.3   0:12.78 Xorg
 2191 www-data  20   0  313m  53m 5876 S  0.0  2.7   0:05.35 apache2
 1064 mysql     20   0  858m  64m 7968 S  0.0  3.2   0:04.28 mysqld
 2591 www-data  20   0  304m  46m 3588 S  0.0  2.3   0:03.24 apache2
 2190 www-data  20   0  304m  46m 3540 S  0.0  2.3   0:02.93 apache2
 1230 kdm       20   0  447m  44m  23m S  0.3  2.2   0:02.84 kdm_greet
 2696 www-data  20   0  310m  52m 4092 S  0.0  2.6   0:02.02 apache2
 2697 www-data  20   0  303m  43m 5504 S  0.0  2.1   0:01.93 apache2
 1403 clamav    20   0 49820 1996 1108 S  0.0  0.1   0:01.89 freshclam
 2515 lanam     20   0 17340 1348 1012 R  0.0  0.1   0:01.85 top
 2756 www-data  20   0  314m  52m 5676 S  0.0  2.6   0:01.25 apache2
 2536 root      30  10  4388  904  612 D  0.0  0.0   0:00.99 updatedb.mlocat
    1 root      20   0 24472 2408 1292 S  0.0  0.1   0:00.87 init
 2698 www-data  20   0  296m  35m 4688 S  0.0  1.8   0:00.63 apache2
 2753 www-data  20   0  289m  30m 3316 S  0.0  1.5   0:00.53 apache2
 2754 root      20   0     0    0    0 R  0.3  0.0   0:00.41 kworker/0:0
 1202 bind      20   0  157m  20m 3080 S  0.0  1.0   0:00.34 named
  435 root      20   0 17236  640  444 S  0.0  0.0   0:00.18 upstart-udev-br
```

Please let me know if there is any more information needed.
I also have a thread going in the absolute beginners section, but have not had much feedback there.

---

### Post by slickymaster on 2014-06-30
Moved to the **Server Platforms** sub-forum.

---

### Post by SeijiSensei on 2014-06-30
You need to review /var/log/syslog the next time the machine becomes unresponsive.  There are many possible reasons this could happen:  bad memory, task overload, or perhaps a real kernel crash.  Only the logs will help with diagnosis.

Is this a busy website running a home-grown application that uses MySQL?  If so, you should also make sure that the database is correctly indexed.  Running queries against a large database without good indexes can take a long time and bog down the machine.

---

### Post by Sapph1r3 on 2014-07-01
Thanks for for advice SeijiSensei.
I've been to the machine physically and performed a few reboots.
One just after I got there, and 2 after doing updates.
I've logged into it remotely and have downloaded a few syslogs to have a look at.
Are there any guidelines for reading these logs? 
Being a Windows user, the Linux jargon can be a little confusing.

With regards to websites running on the server...there are a number of websites and about half will use MySQL.

Thanks again

---

### Post by SeijiSensei on 2014-07-01
Are these websites using stock packages like WordPress or ones that you or your users coded themselves?  If the latter, as I said above, large databases with poorly designed indexing can result in very slow performance. 

As for the logs, the first thing I'd look for is "kernel panics."  An example of what they look like is [here](http://unix.stackexchange.com/questions/60574/determining-cause-of-linux-kernel-panic).  

I'd open an SSH session to the server and run "top" so you can monitor system load.  Another thing to monitor with top is memory usage.  How much memory does this server have?  How much swap?  Linux aggressively caches disk transactions, so it's not uncommon for a machine to show all its memory in use. However if the swap usage is high and the cache figure is low, you probably need to add more memory to support the number of simultaneous processes.

---

### Post by Sapph1r3 on 2014-07-02
> **SeijiSensei said:**
> Are these websites using stock packages like WordPress or ones that you or your users coded themselves?  If the latter, as I said above, large databases with poorly designed indexing can result in very slow performance. 

As for the logs, the first thing I'd look for is "kernel panics."  An example of what they look like is [here]("http://unix.stackexchange.com/questions/60574/determining-cause-of-linux-kernel-panic").  

I'd open an SSH session to the server and run "top" so you can monitor system load.  Another thing to monitor with top is memory usage.  How much memory does this server have?  How much swap?  Linux aggressively caches disk transactions, so it's not uncommon for a machine to show all its memory in use. However if the swap usage is high and the cache figure is low, you probably need to add more memory to support the number of simultaneous processes.

The websites vary, some are WordPress, some are Joomla then you have a few that are coded by the users.
Those ones either don't have a database, or if they do, they usually are web developers handling them so it should be okay.

The server bailed on me again about 2 hours ago, I was removing a users website and directory when it just stopped responding.
This was frustrating, but helped me locate the point to look for in the log.
I found a few entries like this, when it came back up:

```
Jul  2 09:00:01 ws3 CRON[9993]: (root) CMD (/etc/webmin/bandwidth/rotate.pl)
Jul  2 09:05:46 ws3 kernel: [78120.248070] INFO: task updatedb.mlocat:9324 blocked for more than 120 seconds.
Jul  2 09:05:46 ws3 kernel: [78120.248076] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul  2 09:05:46 ws3 kernel: [78120.248079] updatedb.mlocat D ffffffff81805060     0  9324   9318 0x00000000
Jul  2 09:05:46 ws3 kernel: [78120.248084]  ffff880037cd79f8 0000000000000082 000000000fe39eae ffff880079dc94a8
Jul  2 09:05:46 ws3 kernel: [78120.248088]  ffff880037cd7fd8 ffff880037cd7fd8 ffff880037cd7fd8 0000000000012a40
Jul  2 09:05:46 ws3 kernel: [78120.248091]  ffff88006dcc9720 ffff88001a254560 ffff880037cd79d8 ffff88007fc132c0
Jul  2 09:05:46 ws3 kernel: [78120.248095] Call Trace:
Jul  2 09:05:46 ws3 kernel: [78120.248106]  [<ffffffff81196350>] ? __wait_on_buffer+0x30/0x30
Jul  2 09:05:46 ws3 kernel: [78120.248111]  [<ffffffff815eff1f>] schedule+0x3f/0x60
Jul  2 09:05:46 ws3 kernel: [78120.248114]  [<ffffffff815effcf>] io_schedule+0x8f/0xd0
Jul  2 09:05:46 ws3 kernel: [78120.248116]  [<ffffffff8119635e>] sleep_on_buffer+0xe/0x20
Jul  2 09:05:46 ws3 kernel: [78120.248120]  [<ffffffff815f07ef>] __wait_on_bit+0x5f/0x90
Jul  2 09:05:46 ws3 kernel: [78120.248123]  [<ffffffff81196350>] ? __wait_on_buffer+0x30/0x30
Jul  2 09:05:46 ws3 kernel: [78120.248125]  [<ffffffff815f089c>] out_of_line_wait_on_bit+0x7c/0x90
Jul  2 09:05:46 ws3 kernel: [78120.248130]  [<ffffffff81081c50>] ? autoremove_wake_function+0x40/0x40
Jul  2 09:05:46 ws3 kernel: [78120.248133]  [<ffffffff8119634e>] __wait_on_buffer+0x2e/0x30
Jul  2 09:05:46 ws3 kernel: [78120.248138]  [<ffffffff811e1cb5>] __ext3_get_inode_loc.isra.21+0x1e5/0x260
Jul  2 09:05:46 ws3 kernel: [78120.248143]  [<ffffffff81183590>] ? iget_locked+0x180/0x190
Jul  2 09:05:46 ws3 kernel: [78120.248146]  [<ffffffff811e269e>] ext3_iget+0x7e/0x490
Jul  2 09:05:46 ws3 kernel: [78120.248149]  [<ffffffff811e7206>] ext3_lookup.part.18+0x56/0x120
Jul  2 09:05:46 ws3 kernel: [78120.248152]  [<ffffffff811e72f5>] ext3_lookup+0x25/0x30
Jul  2 09:05:46 ws3 kernel: [78120.248157]  [<ffffffff81172885>] d_alloc_and_lookup+0x45/0x90
Jul  2 09:05:46 ws3 kernel: [78120.248160]  [<ffffffff81180225>] ? d_lookup+0x35/0x60
Jul  2 09:05:46 ws3 kernel: [78120.248163]  [<ffffffff81174b04>] do_lookup+0x224/0x2c0
Jul  2 09:05:46 ws3 kernel: [78120.248167]  [<ffffffff8117693c>] path_lookupat+0x11c/0x700
Jul  2 09:05:46 ws3 kernel: [78120.248170]  [<ffffffff81174993>] ? do_lookup+0xb3/0x2c0
Jul  2 09:05:46 ws3 kernel: [78120.248174]  [<ffffffff812f5707>] ? __strncpy_from_user+0x27/0x60
Jul  2 09:05:46 ws3 kernel: [78120.248177]  [<ffffffff81176f51>] do_path_lookup+0x31/0xc0
Jul  2 09:05:46 ws3 kernel: [78120.248180]  [<ffffffff81177879>] user_path_at_empty+0x59/0xa0
Jul  2 09:05:46 ws3 kernel: [78120.248184]  [<ffffffff812b7fc4>] ? apparmor_inode_getattr+0x54/0x60
Jul  2 09:05:46 ws3 kernel: [78120.248187]  [<ffffffff815f1dfe>] ? _raw_spin_lock+0xe/0x20
Jul  2 09:05:46 ws3 kernel: [78120.248190]  [<ffffffff8116c748>] ? cp_new_stat+0xf8/0x110
Jul  2 09:05:46 ws3 kernel: [78120.248193]  [<ffffffff811778d1>] user_path_at+0x11/0x20
Jul  2 09:05:46 ws3 kernel: [78120.248195]  [<ffffffff8116c974>] vfs_fstatat+0x44/0x70
Jul  2 09:05:46 ws3 kernel: [78120.248198]  [<ffffffff8116c9be>] vfs_lstat+0x1e/0x20
Jul  2 09:05:46 ws3 kernel: [78120.248200]  [<ffffffff8116cb5a>] sys_newlstat+0x1a/0x40
Jul  2 09:05:46 ws3 kernel: [78120.248204]  [<ffffffff815fa1c2>] system_call_fastpath+0x16/0x1b
Jul  2 09:05:57 ws3 CRON[10182]: (root) CMD (/etc/webmin/status/monitor.pl)
```

I am trying to understand what it all means and if it shows the cause

Gomen sensei, I was in such a panic about the machine, I skipped answering your questions.

Server has 2GB memory and exactly 2.94GB virtual memory

While logged in, I've never seen the memory close to max at all, it's usually at about half, most I've seen is just over a gig used

---

### Post by SeijiSensei on 2014-07-02
The trace says the problem occurred when the system was trying to update the "locate" database.  Since slocate has been around for ages, I rather doubt it's the real source of the problem.

Updatedb was called from a Perl script, /etc/webmin/bandwidth/rotate.pl.  I never use webmin, so I have no idea why you might be running that file.  If it is to rotate logs, I let the logrotate program handle that on my servers.  See if you can disable that rotate.pl script.

The other possibility is bad hardware, specifically bad memory.  If you can take the server out of production, you can try running memtest86 overnight.  You can access it from the boot menu, but you'll need physical access to the machine.

Also I'd install the ["SMART" tools]("https://help.ubuntu.com/community/Smartmontools") and check on the status of your disk drives.  Since updatedb heavily exercises the drives while compiling its database, a bad drive could be the culprit.  Usually, though, the "fingerprint" of drive errors doesn't look like what you've posted.

How old is this machine?  When was the last time anyone cleaned it of dust and debris?  Personally I no longer manage any hardware servers having moved everything to virtual machines at [Linode](http://www.linode.com/).  I got tired of worrying about hard drives and heat dissipation and power outages and all the other annoyances of managing physical servers.  Now I just have a couple of virtual machines sitting on hefty shared servers out in large datacenters with good power, air-conditioning, and big pipes to the Internet.  If you're paying an ISP to house your physical server, I'd strongly recommend you think about migrating to the "cloud."  Linode's prices start at $20/month.  I used to pay $200-300/month to rent physical servers.

---

### Post by Sapph1r3 on 2014-07-02
I've tried updating my kernel as well.
Currently using [COLOR=#333333]Linux 3.0.0-15-generic on x86_64[/COLOR]
When almost at the end, I was asked
 A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified.
And I kept the old version, so its still on the old kernel.
A little stuck on this now.

Update: kernel has been updated and now running 3.5.0-52-generic. So far it has been stable and more responsive (*touch wood*)
Thanks to all the assistance SeijiSensei

---

### Post by Sapph1r3 on 2014-09-25
> **Sapph1r3 said:**
> 

Update: kernel has been updated and now running 3.5.0-52-generic. So far it has been stable and more responsive (*touch wood*)


So much for being optimistic...things always go bad for me when I'm optimistic.
After more then 2 months, the server went into the same unresponsive state about 2 weeks ago.
I had to ask for a hard boot, and am now currently monitoring the situation.
Windows users should not have to admin a Linux server with this minimal knowledge.
I have now been asked to look at event logs, but unlike Windows Logs these logs make less sense to more the more I stare at them.
This humble n00b requires big time assistance.

---

