---
title: "Please help me! - MySQL stopped working"
date: 2009-03-10
forum: Server Platforms
---

### Post by wattaman on 2009-03-10
Hi!
I just noticed, when I got home today, that the MySQL wasn't running on my server, making my websites useless, of course. Yesterday everything was fine.
I need to know how it stopped, who stopped it, it was hacked, it was an installed script (is it possible!?). I have no ideea where to look.
I have Webmin installed on my server, which is v8.04.
Please point me to the right direction, I'm really affraid this will happen again... in it will, I'll lose my sites members in no time.
Thank you!

P.S. Now I started it again from within WebMin's panel. A few ideas on how to secure it would also be appreciated. MySQL is 5.0.51

---

### Post by hyper_ch on 2009-03-10
have a look at the systlog.

Security is an ongoing process. Best to learn to setup all things manually without webmin. That way you can start troubleshooting if problems arise.

---

### Post by wattaman on 2009-03-10
> **hyper_ch said:**
> have a look at the systlog.

Security is an ongoing process. Best to learn to setup all things manually without webmin. That way you can start troubleshooting if problems arise.

I try to find it

---

### Post by wattaman on 2009-03-10
OK. I've done it.
Where is systlog?

---

### Post by hyper_ch on 2009-03-10
/var/log

---

### Post by wattaman on 2009-03-10
Found it.
I can see in the syslog many lines that say:
> kernel: Out of memory: kill process 18297 (mysqld) score 42454 or a child
kernel: Killed process 18297 (mysqld)
and a few lines after that:
> mysqld_safe[23423]: Number of processes running now: 0
mysqld_safe[23432]: restarted

Is this what stopped it? Is there a way to fix it or to make it not happen again?

---

### Post by hyper_ch on 2009-03-10
how much ram have you?

---

### Post by wattaman on 2009-03-10
I have 2GB of ram and the CPU is 1,7, if I remember well. Usually it takes around 500MB, as I can see in Webmin.
I do have some scripts that run at night and sometimes are using 1,7-1,8GB ram, but they never made me problems.

---

### Post by hyper_ch on 2009-03-10
how much diskspace?

---

### Post by wattaman on 2009-03-10
289.47 GB total, 36.57 GB used

---

### Post by hyper_ch on 2009-03-10
no clue :(

---

### Post by wattaman on 2009-03-10
K, thanks!
Well, hopefully it won't happen too soon, what can I say !?!

---

### Post by warp99 on 2009-03-10
Sometimes the memory that the kernel is using is not flushed and released quickly enough to be reclaimed by another process. This tends to slow down MySQL quering and may have been the reason for your out-of memory issues.

You can make some tweaks to your /etc/sysctl.conf file in order to free up memory faster. As an example I have these for my MySQL database that MythTV uses:

```
# Control the degree the kernel prefers to swap when trying to free memory (default 60)
vm.swappiness=0

# Reclaim cache memory faster for directory and inode objects (default 100)
vm.vfs_cache_pressure=10000

# Let dirty data consume this percentage of memory (default 10)
vm.dirty_ratio = 1

# Let dirty active data consume this percentage of memory (default 5)
vm.dirty_background_ratio = 1

# Wake up pdflush to write to disc (default 500)
vm.dirty_writeback_centisecs = 250

# How old data can be before it should be considered dirty and written to disk (5min) (default 3000)
vm.dirty_expire_centisecs = 3000

```

This doesn't mean that you should use these exact tweaks, but some may help. This link was very helpful in getting memory management working more effective:

[http://www.westnet.com/~gsmith/content/linux-pdflush.htm](http://www.westnet.com/~gsmith/content/linux-pdflush.htm)

Some of the parameters no longer work, but the theory behind the tuning process is still very valid.

---

### Post by wattaman on 2009-03-13
Thanks, Warp99... your information is gold, however my brain can't process it :) I've tried to search infos on the web about about the terms you use in that conf file and explanations on what they can do (for noob, obviously) but couldn't find too much.

Anyway, I have a cron that scans the web for rapidshare links (e search engine for rapidshare) and it's database has a table of 500MB now; also, another cron makes backups of databases every 2 days.
Question is: _could this cause the problem_? Now I've deactivated the crons to see if it happens again, cause tomorrow the server was down, again
Thanks again!

---

### Post by BkkBonanza on 2009-03-13
I have an idea that may help with tracking down why your memory got used up. You could setup a cron to gather data every 5 minutes (or whatever). A useful tool for seeing the system usage state is "top" but usually it's used in interactive mode. You can run it from a cron and store a snapshot in a file so that you can browse it later.

A command like this,

top -bn 1

will output one snapshot of the system state. So use a pipe like this,

top -bn 1 >> top.log

to capture a series of snapshots in one file called top.log. Add that command to your crontab and then when something happens you can browse the top.log to see what was doing it and how it happened. You may even see over time that memory use and a certain app is going upwards and that would help clue you in.

After you have captured data you can use,

less top.log to browse the file. Or if you know certain things to look at then grep can help too. Anyway, hope that helps a bit with the detective work. If you end up determining that mysql itself is using memory then you can find resource via google about tweaking the my.cnf config file to control how much memory it uses.

---

### Post by wattaman on 2009-03-13
> **BkkBonaza said:**
>  Anyway, hope that helps a bit with the detective work. If you end up determining that mysql itself is using memory then you can find resource via google about tweaking the my.cnf config file to control how much memory it uses.

I'm a noob - any information helps. Thank you!
So, if I make the cron 'top -bn 1' to run every 5 minutes, then I'll see all the snapshots takes using the 'top -bn 1 >> top.log' command, have I understood right?

---

### Post by wattaman on 2009-03-24
I think I found the problem, but I still need some help. I think the MySQL was crashing because I had 2 crons starting at the same time, one to backup all databases and another one to scrap feeds from news sites and publish them in a wordpress installation. The second needs a lot of resources.

Anyway, I need someone to take a look at this and to tell his/hers opinion. At 4A.M. both crons mentioned above started to run, the second one keeped running from 4 to almost 5A.M. Somewhere at 4,30, in the syslog, I got this:
> Mar 24 04:36:23 F031 kernel: mysqld invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar 24 04:36:24 F031 kernel: Pid: 24875, comm: mysqld Not tainted 2.6.26.5 #1
Mar 24 04:36:25 F031 kernel:  [<c0257105>] oom_kill_process+0x4e/0x19b
Mar 24 04:36:25 F031 kernel:  [<c0257529>] out_of_memory+0x14e/0x17f
Mar 24 04:36:25 F031 kernel:  [<c0259303>] __alloc_pages_internal+0x2be/0x360
Mar 24 04:36:25 F031 kernel:  [<c02593b1>] __alloc_pages+0x7/0x9
Mar 24 04:36:25 F031 kernel:  [<c025acc2>] __do_page_cache_readahead+0x86/0x164
Mar 24 04:36:25 F031 kernel:  [<c025b0a2>] do_page_cache_readahead+0x3d/0x47
Mar 24 04:36:25 F031 kernel:  [<c02569d0>] filemap_fault+0x165/0x331
Mar 24 04:36:25 F031 kernel:  [<c025fb8e>] __do_fault+0x48/0x429
Mar 24 04:36:25 F031 kernel:  [<c0262ffc>] handle_mm_fault+0x522/0xc4d
Mar 24 04:36:25 F031 kernel:  [<c03e713e>] elv_next_request+0x124/0x131
Mar 24 04:36:25 F031 kernel:  [<c0461f1a>] scsi_request_fn+0x28c/0x2e2
Mar 24 04:36:25 F031 kernel:  [<c024a347>] clocksource_get_next+0x39/0x3f
Mar 24 04:36:25 F031 kernel:  [<c0228836>] do_page_fault+0x4a2/0x8e0
Mar 24 04:36:25 F031 kernel:  [<c023d05f>] run_timer_softirq+0x30/0x16d
Mar 24 04:36:25 F031 kernel:  [<c0239f1f>] __do_softirq+0x75/0xe1
Mar 24 04:36:25 F031 kernel:  [<c0228394>] do_page_fault+0x0/0x8e0
Mar 24 04:36:25 F031 kernel:  [<c058945a>] error_code+0x72/0x78
Mar 24 04:36:25 F031 kernel:  =======================
Mar 24 04:36:25 F031 kernel: Mem-info:
Mar 24 04:36:25 F031 kernel: DMA per-cpu:
Mar 24 04:36:25 F031 kernel: CPU    0: hi:    0, btch:   1 usd:   0
Mar 24 04:36:25 F031 kernel: CPU    1: hi:    0, btch:   1 usd:   0
Mar 24 04:36:25 F031 kernel: Normal per-cpu:
Mar 24 04:36:25 F031 kernel: CPU    0: hi:  186, btch:  31 usd: 162
Mar 24 04:36:25 F031 kernel: CPU    1: hi:  186, btch:  31 usd: 166
Mar 24 04:36:25 F031 kernel: HighMem per-cpu:
Mar 24 04:36:25 F031 kernel: CPU    0: hi:  186, btch:  31 usd: 182
Mar 24 04:36:25 F031 kernel: CPU    1: hi:  186, btch:  31 usd: 179
Mar 24 04:36:25 F031 kernel: Active:483277 inactive:481 dirty:0 writeback:0 unstable:0
Mar 24 04:36:25 F031 kernel:  free:12066 slab:6275 mapped:32 pagetables:3346 bounce:0
Mar 24 04:36:25 F031 kernel: DMA free:7988kB min:68kB low:84kB high:100kB active:2708kB inactive:0kB present:16256kB pages_scanned:26929 all_unreclaimable? yes
Mar 24 04:36:25 F031 kernel: lowmem_reserve[]: 0 873 1984 1984
Mar 24 04:36:25 F031 kernel: Normal free:39780kB min:3744kB low:4680kB high:5616kB active:786244kB inactive:1924kB present:894080kB pages_scanned:82581 all_unreclaimable? no
Mar 24 04:36:25 F031 kernel: lowmem_reserve[]: 0 0 8887 8887
Mar 24 04:36:25 F031 kernel: HighMem free:496kB min:512kB low:1704kB high:2896kB active:1144268kB inactive:0kB present:1137600kB pages_scanned:3476140 all_unreclaimable? yes
Mar 24 04:36:25 F031 kernel: lowmem_reserve[]: 0 0 0 0
Mar 24 04:36:25 F031 kernel: DMA: 1*4kB 0*8kB 1*16kB 1*32kB 0*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 1*4096kB = 7988kB
Mar 24 04:36:25 F031 kernel: Normal: 3902*4kB 2492*8kB 10*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB = 39800kB
Mar 24 04:36:25 F031 kernel: HighMem: 32*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
Mar 24 04:36:25 F031 kernel: 820 total pagecache pages
Mar 24 04:36:25 F031 kernel: Swap cache: add 0, delete 0, find 0/0
Mar 24 04:36:25 F031 kernel: Free swap  = 0kB
Mar 24 04:36:25 F031 kernel: Total swap = 0kB
Mar 24 04:36:25 F031 kernel: 516016 pages of RAM
Mar 24 04:36:25 F031 kernel: 286640 pages of HIGHMEM
Mar 24 04:36:25 F031 kernel: 5683 reserved pages
Mar 24 04:36:25 F031 kernel: 97898 pages shared
Mar 24 04:36:25 F031 kernel: 0 pages swap cached
Mar 24 04:36:25 F031 kernel: 0 pages dirty
Mar 24 04:36:25 F031 kernel: 0 pages writeback
Mar 24 04:36:25 F031 kernel: 32 pages mapped
Mar 24 04:36:25 F031 kernel: 6275 pages slab
Mar 24 04:36:25 F031 kernel: 3346 pages pagetables
Mar 24 04:36:25 F031 kernel: Out of memory: kill process 1870 (mysqld) score 37495 or a child
Mar 24 04:36:25 F031 kernel: Killed process 1870 (mysqld)
Mar 24 04:36:25 F031 kernel: mysqld invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar 24 04:36:25 F031 kernel: Pid: 24874, comm: mysqld Not tainted 2.6.26.5 #1
Mar 24 04:36:25 F031 kernel:  [<c0257105>] oom_kill_process+0x4e/0x19b
Mar 24 04:36:25 F031 kernel:  [<c0257529>] out_of_memory+0x14e/0x17f
Mar 24 04:36:25 F031 kernel:  [<c0259303>] __alloc_pages_internal+0x2be/0x360
Mar 24 04:36:25 F031 kernel:  [<c02593b1>] __alloc_pages+0x7/0x9
Mar 24 04:36:25 F031 kernel:  [<c025acc2>] __do_page_cache_readahead+0x86/0x164
Mar 24 04:36:25 F031 kernel:  [<c025b0a2>] do_page_cache_readahead+0x3d/0x47
Mar 24 04:36:25 F031 kernel:  [<c02569d0>] filemap_fault+0x165/0x331
Mar 24 04:36:25 F031 kernel:  [<c025fb8e>] __do_fault+0x48/0x429
Mar 24 04:36:25 F031 kernel:  [<c027dde0>] core_sys_select+0x1d1/0x267
Mar 24 04:36:25 F031 kernel:  [<c021b9cc>] apic_timer_interrupt+0x28/0x30
Mar 24 04:36:25 F031 kernel:  [<c0262ffc>] handle_mm_fault+0x522/0xc4d
Mar 24 04:36:25 F031 kernel:  [<c0460e10>] scsi_next_command+0x25/0x2f
Mar 24 04:36:25 F031 kernel:  [<c03e713e>] elv_next_request+0x124/0x131
Mar 24 04:36:25 F031 kernel:  [<c0461f1a>] scsi_request_fn+0x28c/0x2e2
Mar 24 04:36:25 F031 kernel:  [<c03e8fd6>] blk_run_queue+0x18/0x27
Mar 24 04:36:25 F031 kernel:  [<c0460fdb>] scsi_end_request+0x5f/0x68
Mar 24 04:36:25 F031 kernel:  [<c0228836>] do_page_fault+0x4a2/0x8e0
Mar 24 04:36:25 F031 kernel:  [<c0228394>] do_page_fault+0x0/0x8e0
Mar 24 04:36:25 F031 kernel:  [<c058945a>] error_code+0x72/0x78
Mar 24 04:36:25 F031 kernel:  =======================
Mar 24 04:36:25 F031 kernel: Mem-info:
Mar 24 04:36:25 F031 kernel: DMA per-cpu:
Mar 24 04:36:25 F031 kernel: CPU    0: hi:    0, btch:   1 usd:   0
Mar 24 04:36:25 F031 kernel: CPU    1: hi:    0, btch:   1 usd:   0
Mar 24 04:36:25 F031 kernel: Normal per-cpu:
Mar 24 04:36:25 F031 kernel: CPU    0: hi:  186, btch:  31 usd: 200
Mar 24 04:36:25 F031 kernel: CPU    1: hi:  186, btch:  31 usd: 150
Mar 24 04:36:25 F031 kernel: HighMem per-cpu:
Mar 24 04:36:25 F031 kernel: CPU    0: hi:  186, btch:  31 usd: 182
Mar 24 04:36:25 F031 kernel: CPU    1: hi:  186, btch:  31 usd: 179
Mar 24 04:36:25 F031 kernel: Active:483352 inactive:696 dirty:0 writeback:0 unstable:0
Mar 24 04:36:25 F031 kernel:  free:11933 slab:6275 mapped:57 pagetables:3346 bounce:0
Mar 24 04:36:25 F031 kernel: DMA free:7988kB min:68kB low:84kB high:100kB active:2708kB inactive:0kB present:16256kB pages_scanned:26929 all_unreclaimable? yes
Mar 24 04:36:25 F031 kernel: lowmem_reserve[]: 0 873 1984 1984
Mar 24 04:36:25 F031 kernel: Normal free:39248kB min:3744kB low:4680kB high:5616kB active:786320kB inactive:2784kB present:894080kB pages_scanned:73224 all_unreclaimable? no
Mar 24 04:36:25 F031 kernel: lowmem_reserve[]: 0 0 8887 8887
Mar 24 04:36:25 F031 kernel: HighMem free:496kB min:512kB low:1704kB high:2896kB active:1144268kB inactive:0kB present:1137600kB pages_scanned:3476630 all_unreclaimable? yes
Mar 24 04:36:25 F031 kernel: lowmem_reserve[]: 0 0 0 0
Mar 24 04:36:25 F031 kernel: DMA: 1*4kB 0*8kB 1*16kB 1*32kB 0*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 1*4096kB = 7988kB
Mar 24 04:36:25 F031 kernel: Normal: 4142*4kB 2330*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB = 39304kB
Mar 24 04:36:25 F031 kernel: HighMem: 32*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
Mar 24 04:36:25 F031 kernel: 995 total pagecache pages
Mar 24 04:36:25 F031 kernel: Swap cache: add 0, delete 0, find 0/0
Mar 24 04:36:25 F031 kernel: Free swap  = 0kB
Mar 24 04:36:25 F031 kernel: Total swap = 0kB
Mar 24 04:36:25 F031 kernel: 516016 pages of RAM
Mar 24 04:36:25 F031 kernel: 286640 pages of HIGHMEM
Mar 24 04:36:25 F031 kernel: 5683 reserved pages
Mar 24 04:36:25 F031 kernel: 97840 pages shared
Mar 24 04:36:25 F031 kernel: 0 pages swap cached
Mar 24 04:36:25 F031 kernel: 0 pages dirty
Mar 24 04:36:25 F031 kernel: 0 pages writeback
Mar 24 04:36:25 F031 kernel: 57 pages mapped
Mar 24 04:36:25 F031 kernel: 6275 pages slab
Mar 24 04:36:25 F031 kernel: 3346 pages pagetables
Mar 24 04:36:25 F031 kernel: Out of memory: kill process 3902 (mysqld) score 37495 or a child
Mar 24 04:36:25 F031 kernel: Killed process 3902 (mysqld)
Mar 24 04:36:28 F031 mysqld_safe[4556]: Number of processes running now: 0
Mar 24 04:36:28 F031 mysqld_safe[4558]: restarted
It repets a few times.

My question is, _am I write about the cronjobs? The crons are doing this?_ does the quoted text tell you something, 'cause I'm looking at it like a morron and don't understand too much.
Thank you very much!

---

### Post by BkkBonanza on 2009-03-26
Your dump there does have some interesting things but doesn't really tell me what's responsible. What I see,

oom-killer is the kernel killing mysqld because it's an easy target. It uses a lot of memory and won't cause any system instability so it gets nuked.

You don't have any swap space defined. It's unclear from this just how much memory you have and what's consuming it. If you have full control of the machine then I'd suggest you really should have some swap space. In a situation like this it would give you a lot more headroom. Things would slow down as they start to swap but you wouldn't end up oom.

I still think that doing some periodic logging would give you a picture of what is going on. Yes, the cron would run a snapshot ervery 5 minutes and then your log file would allow you to see how the memory use is changing over time and what process is using it up. Create the cron like this,

crontab -e

Then add a line like this and save it. 

5 * * * * top -bn 1 >> top.log

This will add the cron as the current user, which should be adequate to see top data. It will create top.log in your home directory. Have a look at the file with 

less top.log 

to see if you can tell. Especially when your other crons run the backup and feed processing. If you suspect a certain program, eg. mysqld is the culprit then you can try,

cat top.log | grep mysqld

and it will show you only the lines with mysqld in them and that would help see clearly how it's use is changing over time. You will need a bit of info to help read the top output. Probably the easiest value to watch is the %Mem column as it is showing you what % of total memory is being used by each program. The other 3 memory columns VIRT, RES, SHR also are helpful but require more knowledge to undertsand.

I think if you do this you'll have a picture of memory usage over time pretty quickly.

---

### Post by wattaman on 2009-03-26
I have a swap partition for virtual memory... maybe is too big, it has 4GB.

I've created the cron, I suppose all I can do from now on is check the logs from time to time, I've also schedules all the crons to run at separate intervals, some of them were running the same time.

I have 2-3 more question before I'll close this:
- How do I exit the *less top.log*? I'm using putty, dunno if it matters, but I can't exit that and I'm closing it and open it again now, which is a little annoying;
- In webmin, under the MySQL Server Configuration, I have this **Skip locking of table files?** and **Allow big tables?** set to **No** - would it be better if I'll set them to **Yes**, instead?
- there's a cron to restart mysql I can use? It would be usefull if I don't have access to the internet for a long time, for example, and the mysql stops again.

Thank you!

---

### Post by BkkBonanza on 2009-03-26
Just hit q to get out of less.

I don't think you need to worry about those settings for mysql in webmin. Skip table locking improves performance. And big tables, not sure, but likely not an issue for you.

To monitor mysqld the proper way is to use upstart. That entails adding a script to the /etc/event.d directory and then a bunch of steps to remove and re-insert the startup scripts in /etc/rc.d. The info you need is given on this page below but it's perhaps a bit complicated to put in place if you're not familiar with the startup system in Ubuntu.

[http://forum.slicehost.com/comments.php?DiscussionID=2370](http://forum.slicehost.com/comments.php?DiscussionID=2370)
(that page talks about monit - wherever he says monit, just think mysqld)

An easier temporary approach would be to write a script that checks for mysqld running and if it's not then to start it. Then add that to a 5 minute cron. Not really the right way but I guess it would work.

---

### Post by wattaman on 2009-03-26
Thanks, man! The script thing is a good ideea. I've found one but is not working, maybe someone can figure it out. Here's the script to restart mysql if is not working:
> 
#!/bin/bash
#
# This script is licensed under GNU GPL version 2.0 or above
#

# mysql server hostname
MHOST="localhost"

#path to MySQL daemon start/stop script.
MSTART="/etc/init.d/mysql start"

# Email address to send notification
EMAILID="username@domain.com"

# path to mail program
MAILCMD="$(which mail)"

# path mysqladmin
MADMIN="$(which mysqladmin)"

MAILMESSAGE="/tmp/mysql.fail.$$"

# see if MySQL server is alive or not
$MADMIN --defaults-file=/etc/mysql/debian.cnf ping 2>/dev/null 1>/dev/null

if [ $? -ne 0 ]; then
        echo "" >$MAILMESSAGE
        echo "Error: MySQL Server is not running/responding ping request">>$MAIL
MESSAGE
        echo "Hostname: $(hostname)" >>$MAILMESSAGE
        echo "Date & Time: $(date)" >>$MAILMESSAGE
        # try to start mysql
        $MSTART>/dev/null
        # see if it is started or not
        o=$(ps cax | grep -c ' mysqld$')
        if [ $o -eq 1 ]; then
                sMess="MySQL Server MySQL server successfully restarted"
        else
                sMess="MySQL server FAILED to restart"
        fi
        # Email status too
        echo "Current Status: $sMess" >>$MAILMESSAGE
        echo "" >>$MAILMESSAGE
        echo "*** This email generated by $(basename $0) shell script ***" >>$MA
ILMESSAGE
        echo "*** Please don't reply this email, this is just notification email
 ***" >>$MAILMESSAGE
        # send email
        $MAILCMD -s "MySQL server" $EMAILID < $MAILMESSAGE
else # MySQL is running  and do nothing
        :
fi
# remove file
rm -f $MAILMESSAGE


And here's the error I get:
> /root/check_mysql: line 50: syntax error near unexpected token `else'
/root/check_mysql: line 50: `else # MySQL is running  and do nothing
'


The script is from [here]("http://www.wptextads.com/blog/2007/09/20/how-to-restart-mysql-from-cron-after-it-suddenly-shuts-down/").

*I'm also reading about the monit tool right now, but in case is too complicated for me, the script above will do just fine...*

---

