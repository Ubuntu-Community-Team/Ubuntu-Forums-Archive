---
title: "upgrade fails from ubuntu server 9.04 to 9.10"
date: 2010-02-24
forum: Server Platforms
---

### Post by FranJPR on 2010-02-24
I  tryed to update ubuntu server from 9.04 to 9.10 a few days ago, but do-release-upgrade failed with the following output.

serv@server:~$ sudo do-release-upgrade
 Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg'
Traceback (most recent call last):
  File "/tmp/tmpreifFc/karmic", line 7, in <module>
    sys.exit(main())
  File "/tmp/tmpreifFc/DistUpgradeMain.py", line 115, in main
    logdir = setup_logging(options, config)
  File "/tmp/tmpreifFc/DistUpgradeMain.py", line 85, in setup_logging
    logging.info("Using config files '%s'" % config.config_files)
  File "/usr/lib/python2.6/logging/__init__.py", line 1451, in info
    root.info(*((msg,)+args), **kwargs)
  File "/usr/lib/python2.6/logging/__init__.py", line 1030, in info
    self._log(INFO, msg, args, **kwargs)
  File "/usr/lib/python2.6/logging/__init__.py", line 1142, in _log
    record = self.makeRecord(self.name, level, fn, lno, msg, args, exc_info, func, extra)
  File "/usr/lib/python2.6/logging/__init__.py", line 1117, in makeRecord
    rv = LogRecord(name, level, fn, lno, msg, args, exc_info, func)
  File "/usr/lib/python2.6/logging/__init__.py", line 272, in __init__
    from multiprocessing import current_process
  File "/usr/lib/python2.6/multiprocessing/__init__.py", line 83, in <module>
    import _multiprocessing
ImportError: No module named _multiprocessing
serv@server:~$


Now, this is what I get:


serv@server:/var/log$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg'
Segmentation fault


I have also tried with the alternate cd:

serv@server:/media/cdrom$ sudo sh /cdrom/cdromupgrade
Segmentation fault


Any idea?


Thanks

---

### Post by jfparis on 2010-02-24
The first error led me to belive that your python set up might be corrupted

you should try to re install it

```
apt-get install --reinstall python2.6 python2.6-minimal 
```

---

### Post by FranJPR on 2010-02-25
Thank you so much!. I reinstalled python and I could start do-release-upgrade successfully. Unfortunately, the process quit because I have another problem. In my jaunty version when I update the repositories I am getting this:


Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

When I executed the upgrade, it started changing the repositories but it said that karmic-updates Release could not be signed or updated and it was returnning to the previous one, afterwards the process was aborted and upgrade quit.

Any clue about this?

---

### Post by FranJPR on 2010-02-27
I read on a thread that someone runned fsck -fy / to fix a broken file and that it solved this bug. It worked for me as well!.

---

