---
title: "is denyhosts working properly?"
date: 2011-05-16
forum: Security
---

### Post by wlraider70 on 2011-05-16
I just set up denyhosts and it worked properly the first time adding lots of ips to the hosts.deny.

I then set it to run every 12 hours noon and midnight.
I wanted to see if ran properly and I got all this.

Does it look like its working?

```


May 15 12:00:01 hyrule CRON[14286]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:01:01 hyrule CRON[14294]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:02:01 hyrule CRON[14302]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:03:01 hyrule CRON[14310]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:04:01 hyrule CRON[14318]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:05:01 hyrule CRON[14326]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:06:01 hyrule CRON[14334]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:07:01 hyrule CRON[14341]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:08:01 hyrule CRON[14349]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:09:01 hyrule CRON[14359]: (root) CMD (python /usr/share/denyhosts/denyhosts_ctl.py -c /usr/share/denyhosts/denyhosts.cfg                  )
May 15 12:09:01 hyrule CRON[14360]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/                   -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)


```

there is more, but its a little redundant.

---

### Post by spynappels on 2011-05-16
Denyhosts is designed to run constantly in the background, not be started and stopped constantly, just start it and forget about it.

---

### Post by wlraider70 on 2011-05-16
really, I get that its a small process just reading a file and adding to a new file, but that seems excessive.

I don't want or need it be always running.

---

### Post by spynappels on 2011-05-16
Denyhosts dynamically blocks hosts which enter the wrong SSH password a number of times (or fail other authentication methods, I'm not sure) based on rules in the denyhosts config file. It adds the IPs it blocks to hosts.deny but it is designed to run as a daemon all the time.

Only running it now and again is like only running your antivirus on Windows for only a few minutes at a time, almost like having no protection at all.

---

### Post by nutznboltz on 2011-06-09
denyhosts showed up on my radar today.  I started drilling into it after my introduction (below.)  It's long so I'll just provide a link and some notable parts of it.

> [b][url=http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=622697]Debian Bug report logs - #622697
Denyhosts default sync leaves >90% unprotected / Server design[/url]
Anne Bezemer / Thu, 14 Apr 2011 01:52:35 +0200 (CEST)[/b]

(Warning: long report)

... any given client will _never_ know of 91.8% of all active crackers.

That's bad, since it renders the whole sync stuff mostly useless.

... Quick checking shows that the central server will happily re-send crackers at least 10-20 times (once 37 repeats).

This means the sync run is not working as advertised.

... the denyhosts central database design is closed-source (Boohoo!), so I can't check what is going wrong. That's the problem with closed-source. ...

---

