---
title: "How do I stop finished and persistent processes that take up memory [Ubuntu 15.04]"
date: 2015-12-25
forum: Server Platforms
---

### Post by mohaafan on 2015-12-25
I am running Ubuntu 15.04 x64 OS on a remote VDS server.  I do not have a GUI Desktop installed nor do I plan on installing one. As to my issue,  I notice that a lot of the processes running are those for which the user tasks have been completed. For instance, if I open a file with nano for editing and then close it.  I still see "sudo nano ....." in the list of processes running which I pull up wth the "ps -aux" command.  So at a given point the total memory usage would be like 12%, but when I reboot the server, it would go down to 9%.  How can I make it so that completed tasks don't continue to consume memory?

Thanks for your help in advance.

---

### Post by Bucky Ball on 2015-12-25
*Thread moved to **Server Platforms**.*

Although you are new, you seem to know your way around with servers and may be better server-ed here. ;)

---

### Post by MAFoElffen on 2015-12-25
What would help is posting the output of 
```

pstree -aup

```
Then a snip from top... You mentioned a few things (such as remote) that make me wonder if this is really a matter of a background process not ending, inactive persistence or inactive session.

---

### Post by matt_symes on 2015-12-25
Hi

> **mohaafan said:**
> I am running Ubuntu 15.04 x64 OS on a remote VDS server.  I do not have a GUI Desktop installed nor do I plan on installing one. As to my issue,  I notice that a lot of the processes running are those for which the user tasks have been completed. For instance, if I open a file with nano for editing and then close it.  I still see "sudo nano ....." in the list of processes running which I pull up wth the "ps -aux" command.  So at a given point the total memory usage would be like 12%, but when I reboot the server, it would go down to 9%.  How can I make it so that completed tasks don't continue to consume memory?

Thanks for your help in advance.

I'm with MAFoElffen here. The output of pstree would be useful.

Are you sure nano is being closed ? 

After you close nano it should not appear in the output ps at all, if that was the only instance of nano you had open. 

It sounds like nano may be suspended or something like that. Or even, maybe zombied somehow ?

Anyway, the Linux memory manager will try to cache and buffer as much into memory as it can, following the mantra the 'unused memory is wasted memory'. My media server is currently caching 13G....

Kind regards

---

### Post by mohaafan on 2015-12-25
Hi

Unfortunately, I rebooted the VDS server before I could do "pstree -aup".  So, it is showing about 9% total memory usage right now as it does every time I reboot the server.  I will post the output of "pstree -aup" after some server use.

Thanks.

---

### Post by matt_symes on 2015-12-25
Hi

> **mohaafan said:**
> Hi

Unfortunately, I rebooted the VDS server before I could do "pstree -aup".  So, it is showing about 9% total memory usage right now as it does every time I reboot the server.  I will post the output of "pstree -aup" after some server use.

Thanks.

If you could also post the output of

```
free -m
```

This will show us basic memory usage.

Kind regards

---

### Post by mohaafan on 2015-12-25
Ok. I will do that also. Thanks.

---

### Post by SeijiSensei on 2015-12-25
The basic answer to your question is to use kill or killall.  The first takes a process ID; the second uses the name of the program and will kill all existing instances of that program. The -15 switch tells the program to shut down gracefully.  The -9 switch terminates with extreme prejudice.

Usually it's pretty obvious from looking at "ps ax" which processes are subordinate to others.  I usually try to kill them in reverse order, but sometimes only killing the parent process works.

---

### Post by MAFoElffen on 2015-12-26
Kill <pid#>and was one of my first thoughts... and with Matt on his reasoning. If you start a nano, gedit or vi, when they start those editors under sudo, the session spawning it will show errors because they do not write any temp files if used with root permissions.... But that is not really an error nor a problem ... and should not latch onto unrecoverable memory.(Note 1) When you quit out of any of those editors, the editor closes and you should not see see any processes. Quit and the process ends and disappears. If a process is finished, it should not be there any longer. 

Whereas, the definition of a persistent process in Linux is misleading. A persistent process does/can finish and end (releasing resources when it does), but then is respawned...

Now if for some reason, it did not end and was still running in background, then it would have a process id and you could kill it using kill, without having to reboot. If for some reason it was left as an orphaned or zombie process, then theres ways to kill those, by tracing the spawned process that left the orphaned or zombie process... and killing the parent process first, then the child. 

Next would be that it was a remote session and the session was still actively running processes in a session. Usually when  session ends, then those processes ends. But if the session was still active with active processes... you could then id them to kill the processes and then end that session, to recover those resources.

An unintentional orphaned process is what your description is similar to. Think on that an unintentional orphaned process is a process that was started as a child spawned by a parent process, and the parent process (or the session that the parent was running from) crashes leaving the child process running... or a process that is running waiting on the exit code of another process, but never gets that exit code (because that process crashed without leaving an exit code)... so continues to run...

 I'm not a big fan of rebooting a Linux server as an answer to regain memory. There are other ways to go about that. When thinking of scope and multi-user, I am a big fan of diagnostics, audits and being able to start, stop, pause, and restart services gracefully. As I spent the last few years learning to dig down and use systemd... Anyways...

That is a curiosity. There is something going on ... We just need to find out how what is going on and why. One way might be to setup a cron job to audit intermittent snapshots of what is going on... But how to set up a consistent condition to ID that is the big question. Such as if load or memory used is over ___, then audit the results of ___...

Note #1-- On some servers I use instances of X to host or temporarily run some remote GUI based management tools, but they are instances, which once they quit, release and recover anything they had used in that instance.

EDIT-- My assumption is that since not using an LTS, that this is not a production server(?)

---

### Post by mohaafan on 2015-12-26
I am not using the server as a production server nor a development server, but as requested I have included the info below. 
The server is using about 12% constantly. If I reboot it, it is 9%:

*pstree -aup:*

```
systemd,1 splash  &#9500;&#9472;accounts-daemon,528
  &#9474;   &#9500;&#9472;{gdbus},616
  &#9474;   &#9492;&#9472;{gmain},615
  &#9500;&#9472;agetty,575 --keep-baud 115200 38400 9600 hvc0 vt220
  &#9500;&#9472;agetty,576 --noclear tty7 linux
  &#9500;&#9472;atd,534,daemon -f
  &#9500;&#9472;cron,531 -f
  &#9500;&#9472;dbus-daemon,595,messagebus --system --address=systemd: --nofork ...
  &#9500;&#9472;polkitd,620 --no-debug
  &#9474;   &#9500;&#9472;{gdbus},622
  &#9474;   &#9492;&#9472;{gmain},623
  &#9500;&#9472;rsyslogd,540,syslog -n
  &#9474;   &#9500;&#9472;{in:imklog},612
  &#9474;   &#9500;&#9472;{in:imuxsock},611
  &#9474;   &#9492;&#9472;{rs:main Q:Reg},613
  &#9500;&#9472;sshd,561 -D
  &#9474;   &#9492;&#9472;sshd,5601
  &#9474;       &#9492;&#9472;bash,5653
  &#9474;           &#9492;&#9472;pstree,5668 -aup
  &#9500;&#9472;systemd,5603 --user
  &#9474;   &#9492;&#9472;(sd-pam),5604
  &#9500;&#9472;systemd-journal,187
  &#9500;&#9472;systemd-logind,532
  &#9500;&#9472;systemd-timesyn,328,systemd-timesync
  &#9474;   &#9492;&#9472;{sd-resolve},331
  &#9492;&#9472;systemd-udevd,211



```

[I]free -m:
[/I]
```
total       used       free     shared    buffers     cachedMem:           
987        474        512         12         65        321
-/+ buffers/cache:         88        898
Swap:            0          0          0

```

[I]ps -aux:

[/I]```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMANDroot         1  0.0  0.4  34884  5028 ?        Ss   Dec25   0:01 /sbin/init spla
root         2  0.0  0.0      0     0 ?        S    Dec25   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Dec25   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    Dec25   0:00 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    Dec25   0:00 [rcu_bh]
root         9  0.0  0.0      0     0 ?        S    Dec25   0:00 [rcuos/0]
root        10  0.0  0.0      0     0 ?        S    Dec25   0:00 [rcuob/0]
root        11  0.0  0.0      0     0 ?        S    Dec25   0:00 [migration/0]
root        12  0.0  0.0      0     0 ?        S    Dec25   0:00 [watchdog/0]
root        13  0.0  0.0      0     0 ?        S<   Dec25   0:00 [khelper]
root        14  0.0  0.0      0     0 ?        S    Dec25   0:00 [kdevtmpfs]
root        15  0.0  0.0      0     0 ?        S<   Dec25   0:00 [netns]
root        16  0.0  0.0      0     0 ?        S<   Dec25   0:00 [perf]
root        17  0.0  0.0      0     0 ?        S    Dec25   0:00 [xenwatch]
root        18  0.0  0.0      0     0 ?        S    Dec25   0:00 [xenbus]
root        20  0.0  0.0      0     0 ?        S    Dec25   0:00 [khungtaskd]
root        21  0.0  0.0      0     0 ?        S<   Dec25   0:00 [writeback]
root        22  0.0  0.0      0     0 ?        SN   Dec25   0:00 [ksmd]
root        23  0.0  0.0      0     0 ?        SN   Dec25   0:00 [khugepaged]
root        24  0.0  0.0      0     0 ?        S<   Dec25   0:00 [crypto]
root        25  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kintegrityd]
root        26  0.0  0.0      0     0 ?        S<   Dec25   0:00 [bioset]
root        27  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kblockd]
root        28  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ata_sff]
root        29  0.0  0.0      0     0 ?        S<   Dec25   0:00 [md]
root        30  0.0  0.0      0     0 ?        S<   Dec25   0:00 [devfreq_wq]
root        33  0.0  0.0      0     0 ?        S    Dec25   0:00 [kswapd0]
root        34  0.0  0.0      0     0 ?        S    Dec25   0:00 [fsnotify_mark]
root        35  0.0  0.0      0     0 ?        S    Dec25   0:00 [ecryptfs-kthre
root        47  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kthrotld]
root        48  0.0  0.0      0     0 ?        S<   Dec25   0:00 [acpi_thermal_p
root        49  0.0  0.0      0     0 ?        S    Dec25   0:00 [khvcd]
root        50  0.0  0.0      0     0 ?        S    Dec25   0:00 [scsi_eh_0]
root        51  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_tmf_0]
root        52  0.0  0.0      0     0 ?        S    Dec25   0:14 [scsi_eh_1]
root        53  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_tmf_1]
root        58  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ipv6_addrconf]
root        78  0.0  0.0      0     0 ?        S<   Dec25   0:00 [deferwq]
root        79  0.0  0.0      0     0 ?        S<   Dec25   0:00 [charger_manage
root        80  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kworker/0:1H]
root       126  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kpsmoused]
root       137  0.0  0.0      0     0 ?        S    Dec25   0:00 [jbd2/xvda2-8]
root       138  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ext4-rsv-conve
root       180  0.0  0.0      0     0 ?        S    Dec25   0:00 [kauditd]
root       187  0.0  0.4  29036  4716 ?        Ss   Dec25   0:02 /lib/systemd/sy
root       211  0.0  0.4  42676  4584 ?        Ss   Dec25   0:00 /lib/systemd/sy
root       287  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ttm_swap]
root       311  0.0  0.0      0     0 ?        S    Dec25   0:00 [jbd2/xvda1-8]
root       312  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ext4-rsv-conve
systemd+   328  0.0  0.2  98212  2688 ?        Ssl  Dec25   0:00 /lib/systemd/sy
root       528  0.0  0.8 284556  8772 ?        Ssl  Dec25   0:02 /usr/lib/accoun
root       531  0.0  0.2  28904  2916 ?        Ss   Dec25   0:00 /usr/sbin/cron
root       532  0.0  0.3  28536  3108 ?        Ss   Dec25   0:00 /lib/systemd/sy
daemon     534  0.0  0.1  19180  1916 ?        Ss   Dec25   0:00 /usr/sbin/atd -
syslog     540  0.0  0.5 260132  5200 ?        Ssl  Dec25   0:00 /usr/sbin/rsysl
root       561  0.0  0.5  59644  5560 ?        Ss   Dec25   0:00 /usr/sbin/sshd
root       575  0.0  0.2  15676  2356 hvc0     Ss+  Dec25   0:00 /sbin/agetty --
root       576  0.0  0.2  15856  2148 tty7     Ss+  Dec25   0:00 /sbin/agetty --
message+   595  0.0  0.3  42388  3588 ?        Ss   Dec25   0:00 /usr/bin/dbus-d
root       620  0.0  0.7 278684  7848 ?        Ssl  Dec25   0:00 /usr/lib/policy
root      2055  0.0  0.0      0     0 ?        S    Dec25   0:00 [kworker/0:1]
root      5355  0.0  0.0      0     0 ?        S    07:07   0:00 [kworker/u30:1]
root      5441  0.0  0.0      0     0 ?        S    07:22   0:00 [kworker/u30:2]
root      5600  0.0  0.0      0     0 ?        S    07:23   0:00 [kworker/0:3]
root      5667  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u30:3]
root      5669  0.0  0.0      0     0 ?        S    07:32   0:00 [kworker/u30:0]
root      5674  0.0  0.0      0     0 ?        S    07:34   0:00 [kworker/0:0]
root      5676  0.0  0.0      0     0 ?        S    07:34   0:00 [kworker/0:2]
root      5677  0.2  0.6  93592  6424 ?        Ss   07:34   0:00 sshd: root@pts/
root      5679  0.0  0.4  34188  4180 ?        Ss   07:34   0:00 /lib/systemd/sy
root      5680  0.0  0.1  58272  1476 ?        S    07:34   0:00 (sd-pam)
root      5729  0.6  0.5  22496  5192 pts/0    Ss   07:34   0:00 -bash
root      5742  0.0  0.2  18480  2672 pts/0    R+   07:34   0:00 ps -aux



```

[I]pstree -aup after reboot:

[/I]```
systemd,1 splash  &#9500;&#9472;accounts-daemon,539
  &#9474;   &#9500;&#9472;{gdbus},605
  &#9474;   &#9492;&#9472;{gmain},604
  &#9500;&#9472;agetty,569 --noclear tty7 linux
  &#9500;&#9472;agetty,570 --keep-baud 115200 38400 9600 hvc0 vt220
  &#9500;&#9472;atd,549,daemon -f
  &#9500;&#9472;cron,556 -f
  &#9500;&#9472;dbus-daemon,589,messagebus --system --address=systemd: --nofork ...
  &#9500;&#9472;ondemand,575 /etc/init.d/ondemand background
  &#9474;   &#9492;&#9472;sleep,578 60
  &#9500;&#9472;polkitd,612 --no-debug
  &#9474;   &#9500;&#9472;{gdbus},621
  &#9474;   &#9492;&#9472;{gmain},623
  &#9500;&#9472;rsyslogd,543,syslog -n
  &#9474;   &#9500;&#9472;{in:imklog},609
  &#9474;   &#9500;&#9472;{in:imuxsock},608
  &#9474;   &#9492;&#9472;{rs:main Q:Reg},610
  &#9500;&#9472;sshd,535 -D
  &#9474;   &#9492;&#9472;sshd,695
  &#9474;       &#9492;&#9472;bash,788
  &#9474;           &#9492;&#9472;pstree,801 -aup
  &#9500;&#9472;systemd,697 --user
  &#9474;   &#9492;&#9472;(sd-pam),698
  &#9500;&#9472;systemd-journal,192
  &#9500;&#9472;systemd-logind,542
  &#9500;&#9472;systemd-timesyn,329,systemd-timesync
  &#9474;   &#9492;&#9472;{sd-resolve},334
  &#9492;&#9472;systemd-udevd,212



```[I]

free -m after reboot:

[/I]```
total       used       free     shared    buffers     cachedMem:
987        139        848          4         23         59
-/+ buffers/cache:         55        931
Swap:            0          0          0
```

ps -aux after reboot:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.5  34916  5128 ?        Ss   07:36   0:00 /sbin/init splash
root         2  0.0  0.0      0     0 ?        S    07:36   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    07:36   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/0:0]
root         5  0.0  0.0      0     0 ?        S<   07:36   0:00 [kworker/0:0H]
root         6  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/u30:0]
root         7  0.0  0.0      0     0 ?        S    07:36   0:00 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    07:36   0:00 [rcu_bh]
root         9  0.0  0.0      0     0 ?        S    07:36   0:00 [rcuos/0]
root        10  0.0  0.0      0     0 ?        S    07:36   0:00 [rcuob/0]
root        11  0.0  0.0      0     0 ?        S    07:36   0:00 [migration/0]
root        12  0.0  0.0      0     0 ?        S    07:36   0:00 [watchdog/0]
root        13  0.0  0.0      0     0 ?        S<   07:36   0:00 [khelper]
root        14  0.0  0.0      0     0 ?        S    07:36   0:00 [kdevtmpfs]
root        15  0.0  0.0      0     0 ?        S<   07:36   0:00 [netns]
root        16  0.0  0.0      0     0 ?        S<   07:36   0:00 [perf]
root        17  0.0  0.0      0     0 ?        S    07:36   0:00 [xenwatch]
root        18  0.0  0.0      0     0 ?        S    07:36   0:00 [xenbus]
root        19  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/0:1]
root        20  0.0  0.0      0     0 ?        S    07:36   0:00 [khungtaskd]
root        21  0.0  0.0      0     0 ?        S<   07:36   0:00 [writeback]
root        22  0.0  0.0      0     0 ?        SN   07:36   0:00 [ksmd]
root        23  0.0  0.0      0     0 ?        SN   07:36   0:00 [khugepaged]
root        24  0.0  0.0      0     0 ?        S<   07:36   0:00 [crypto]
root        25  0.0  0.0      0     0 ?        S<   07:36   0:00 [kintegrityd]
root        26  0.0  0.0      0     0 ?        S<   07:36   0:00 [bioset]
root        27  0.0  0.0      0     0 ?        S<   07:36   0:00 [kblockd]
root        28  0.0  0.0      0     0 ?        S<   07:36   0:00 [ata_sff]
root        29  0.0  0.0      0     0 ?        S<   07:36   0:00 [md]
root        30  0.0  0.0      0     0 ?        S<   07:36   0:00 [devfreq_wq]
root        31  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/u30:1]
root        33  0.0  0.0      0     0 ?        S    07:36   0:00 [kswapd0]
root        34  0.0  0.0      0     0 ?        S    07:36   0:00 [fsnotify_mark]
root        35  0.0  0.0      0     0 ?        S    07:36   0:00 [ecryptfs-kthrea]
root        47  0.0  0.0      0     0 ?        S<   07:36   0:00 [kthrotld]
root        48  0.0  0.0      0     0 ?        S<   07:36   0:00 [acpi_thermal_pm]
root        49  0.0  0.0      0     0 ?        S    07:36   0:00 [khvcd]
root        50  0.0  0.0      0     0 ?        S    07:36   0:00 [scsi_eh_0]
root        51  0.0  0.0      0     0 ?        S<   07:36   0:00 [scsi_tmf_0]
root        52  0.0  0.0      0     0 ?        S    07:36   0:00 [scsi_eh_1]
root        53  0.0  0.0      0     0 ?        S<   07:36   0:00 [scsi_tmf_1]
root        54  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/u30:2]
root        58  0.0  0.0      0     0 ?        S<   07:36   0:00 [ipv6_addrconf]
root        59  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/u30:3]
root        78  0.0  0.0      0     0 ?        S<   07:36   0:00 [deferwq]
root        79  0.0  0.0      0     0 ?        S<   07:36   0:00 [charger_manager]
root        80  0.0  0.0      0     0 ?        S<   07:36   0:00 [kworker/0:1H]
root       125  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/0:2]
root       126  0.0  0.0      0     0 ?        S<   07:36   0:00 [kpsmoused]
root       127  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/0:3]
root       137  0.0  0.0      0     0 ?        S    07:36   0:00 [jbd2/xvda2-8]
root       138  0.0  0.0      0     0 ?        S<   07:36   0:00 [ext4-rsv-conver]
root       180  0.0  0.0      0     0 ?        S    07:36   0:00 [kauditd]
root       187  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/0:4]
root       192  0.0  0.3  29036  3352 ?        Ss   07:36   0:00 /lib/systemd/systemd-journald
root       197  0.0  0.0      0     0 ?        S    07:36   0:00 [kworker/0:5]
root       212  0.1  0.4  42588  4548 ?        Ss   07:36   0:00 /lib/systemd/systemd-udevd
root       254  0.0  0.0      0     0 ?        S<   07:36   0:00 [ttm_swap]
root       311  0.0  0.0      0     0 ?        S    07:37   0:00 [jbd2/xvda1-8]
root       312  0.0  0.0      0     0 ?        S<   07:37   0:00 [ext4-rsv-conver]
systemd+   329  0.0  0.2  98212  2700 ?        Ssl  07:37   0:00 /lib/systemd/systemd-timesyncd
root       535  0.0  0.5  59644  5516 ?        Ss   07:37   0:00 /usr/sbin/sshd -D
root       539  0.0  0.6 284556  6696 ?        Ssl  07:37   0:00 /usr/lib/accountsservice/accounts-daemon
root       542  0.0  0.3  28460  3080 ?        Ss   07:37   0:00 /lib/systemd/systemd-logind
syslog     543  0.0  0.3 260132  3492 ?        Ssl  07:37   0:00 /usr/sbin/rsyslogd -n
daemon     549  0.0  0.1  19180  1912 ?        Ss   07:37   0:00 /usr/sbin/atd -f
root       556  0.0  0.2  28904  2852 ?        Ss   07:37   0:00 /usr/sbin/cron -f
root       569  0.0  0.2  15856  2120 tty7     Ss+  07:37   0:00 /sbin/agetty --noclear tty7 linux
root       570  0.0  0.2  15676  2324 hvc0     Ss+  07:37   0:00 /sbin/agetty --keep-baud 115200 38400 9600 hvc0 vt220
message+   589  0.0  0.3  42388  3632 ?        Ss   07:37   0:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
root       612  0.0  0.5 278788  6020 ?        Ssl  07:37   0:00 /usr/lib/policykit-1/polkitd --no-debug
root       695  0.0  0.6  93592  6604 ?        Ss   07:37   0:00 sshd: root@pts/0
root       697  0.0  0.4  34188  4192 ?        Ss   07:37   0:00 /lib/systemd/systemd --user
root       698  0.0  0.1  58304  1504 ?        S    07:37   0:00 (sd-pam)
root       788  0.0  0.5  22496  5312 pts/0    Ss   07:37   0:00 -bash
root       933  0.0  0.2  18480  2708 pts/0    R+   07:41   0:00 ps -aux

```

Thank you for your help

---

### Post by matt_symes on 2015-12-27
Hi

I don't really see where the problem is in your above output.

I can see no rouge processes; no processes that i would not expect to see.

As for memory usage, I'm not sure where you're getting the figures 9% and 12% from as i make it ~5.5% and ~9% after buffers and cache are taken into account and this is pretty respectable. I would expect that this is caused by some processes grabbing more memory as they require it.

I can't really see much wrong with it. Buffer and cache are increasing as you would expect but if there's any memory pressure then they'll be dropped the memory manager.

At the moment I'm not sure what to say. See what others think.

Kind regards

---

### Post by MAFoElffen on 2015-12-27
Agreed. Pasting both sets of outputs into temp db files, sorting and analyzing ... I see 19 processes each that use any memory and/or CPU. They are, for all intensive purposes using the same. Before is 08.%CPU and 6.6% Mem. After is 0.3 %CPU and 6.4% Mem. 

That is not enough to make any kind of conclusion. That close in a snapshot of a moment of time could be nothing (just normal). Unix and Linux load calculations are usually done as an averages over a 15 minute span. So, the next step would be to look at the results of:
```

cat /proc/loadavg

```
From those same 2 system states... but from what I see so far, I do not see anything there worth chasing, that is of any concern so far... It looks as if it is just at idle, not doing much at all. I do not see any stalled or rogue processes.

What is diffrent is your mem free stats... but that could be just from use. What I see as being different in those is what is in cache and buffers. A reboot flushes those out ... but those are also freed from just normal use, on-demand. How much swap do you have allocated on that system?

---

### Post by SeijiSensei on 2015-12-28
I don't see anything in those reports that suggest the server is using up too much memory or CPU.

Remember that Linux uses just about all available memory.  What isn't devoted to running processes is used for caching disk transactions.

What are the figures for load average?  If you run "top" you'll see them at the top of the page:

```
top - 19:36:57 up 166 days,  9:00,  2 users,  load average: 0.03, 0.01, 0.00
```

This is a combination mail/DNS/file server in my home office.  I also run virtual servers at Linode that have pretty similar load averages.

---

