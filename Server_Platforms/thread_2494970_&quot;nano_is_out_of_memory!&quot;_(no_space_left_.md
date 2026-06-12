---
title: "&quot;nano is out of memory!&quot; (no space left on device)"
date: 2024-02-02
forum: Server Platforms
---

### Post by civilpolisen on 2024-02-02
```

civilpolisen@lynx:/var/log$ sudo du -sh * | grep G
6.8G    ldap.log
6.9G    slapd.log
civilpolisen@lynx:/var/log$ sudo nano ldap.log
nano is out of memory!
civilpolisen@lynx:/var/log$ 

```

Ubuntu 18.04 and the disk is getting full... Can I just remove these logs (after saving at other location??) and new server log files will be created!?

---

### Post by TheFu on 2024-02-02
Most Linux editors load the enter file init memory when you tell them to edit a file.  It will use real RAM  and swap.

The "right answer" is to use journalctl to limit the size of logs that exist and are allowed to be created. There's a config file for this, journald.conf. It is well commented and there's an excellent manpage.

```
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```
Will get you started.  I've posted other **journalctl** commands in these forums to help people, but those are the ones for immediately reducing the sizes.

In Debian 12, there aren't anymore text log files. Only journald files, so it is best to learn this stuff sooner than later.
As much as I dislike systemd and nearly everything it touched, journald and journalctl are amazing. Wish we'd had that 25 yrs ago.

Of course, developers need to use the system logging tools for them to be 100% used. Nothing will stop developers from writing text logs.


The "wrong answer" is to use the text tools on every Unix system to truncate the logs.  It is wrong because text logs are appended, not prepended, so any truncation will lose new information.  This also has the problem that usually, larger amounts of storage are needed, before the original huge files can be removed.

Another "wrong answer" is to add more swap so you can edit the full file(s).  

If you do need to keep text logs, be certain to check your logrotate settings for the specific file to handle log issues better.  If you are rotating logs monthly, do it weekly.  If you are keeping 10 log files, maybe keep just 5.  If you don't compress log files, add the "compress" option.  And don't just do it for 1 log file, but for all of them over a few MB.

I suppose there are better editors that don't load the entire file into RAM too.  I can't help with that. I use vim. It has the same flaw.

And if you aren't signed up for ESM support on 18.04, you have been running an unsupported release for nearly a year.

---

### Post by SeijiSensei on 2024-02-02
How much RAM do you have? Do you have a swap file/partition?

---

