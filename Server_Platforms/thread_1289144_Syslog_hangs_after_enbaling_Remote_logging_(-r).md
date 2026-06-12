---
title: "Syslog hangs after enbaling Remote logging (-r)"
date: 2009-10-12
forum: Server Platforms
---

### Post by ragnator on 2009-10-12
Hi all,

Recently I needed to enable remote logging so that I could capture logs from my modem, So I added the -r option in /etc/default/syslogd i.e SYSLOGD="-r"

Now after this I did start getting my modem logs BUT syslog takes a long time to log.

For e.g when I do sudo or ssh or any other command which needs logging it takes a long time for the command to complete.

I did an, strace sudo "echo hi", and notice that it hangs at send () to /dev/log . If I restart sylogkd it starts working for a minute or so and then starts hanging again.

Also, this problem goes away if I remove the -r option. But I do want remote logging :(

Any ideas on what the problem could be? :confused:

Thanks

---

### Post by edthefox on 2009-10-14
try syslog-ng, it's in the repositories

you can find a forum/wiki here -> [http://www.syslog.org/wiki/Syslog-ng/Syslog-ngWiki](http://www.syslog.org/wiki/Syslog-ng/Syslog-ngWiki)

---

### Post by Lars Noodén on 2009-10-14
I assume you are using rsyslogd that comes as default with Ubuntu.

Try opening a new terminal window, stopping rsyslogd and then running manually it in debug mod and watch the output.
```

sudo /etc/init.d/rsyslog stop

sudo /usr/sbin/rsyslogd -d -f /etc/rsyslog.conf
# OR
sudo /usr/sbin/rsyslogd -d -f /etc/rsyslog.conf | less


```

it may be quite verbose, but skim through it.

---

