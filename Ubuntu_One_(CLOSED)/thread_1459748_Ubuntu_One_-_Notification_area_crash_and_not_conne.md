---
title: "Ubuntu One - Notification area crash and not connecting"
date: 2010-04-21
forum: Ubuntu One (CLOSED)
---

### Post by cprofitt on 2010-04-21
Notification area shows that I am not connected... when I click on it it crashes.

CPU utilization is spiking as well.

the contents of the ~/.cache/ubuntoone/oauth-login.log is:

> 
2010-04-21 20:52:38,394:394.510984421 UbuntuOne.Client.Applet DBus Error: Message did not receive a reply (timeout by message bus)
2010-04-21 20:52:38,394:394.998073578 UbuntuOne.Client.Applet DBus Error: Message did not receive a reply (timeout by message bus)
2010-04-21 20:52:38,395:395.343065262 UbuntuOne.Client.Applet DBus Error: Message did not receive a reply (timeout by message bus)


the same entry keeps repeating.

the contents of the ~/.cache/ubuntuone/syncdaemon.log is:

> 
2010-04-21 20:58:41,109 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: INIT; queues: metadata: 0; content: 0; hash: 0, fsm-cache: hit=1 miss=167) ----
2010-04-21 20:58:41,110 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan starting...
2010-04-21 20:58:41,110 - ubuntuone.SyncDaemon.local_rescan - INFO - start scan all shares
2010-04-21 20:58:41,110 - ubuntuone.SyncDaemon - ERROR - Unexpected error
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 182, in <module>
    main(sys.argv)
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 167, in main
    main.start()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/main.py", line 201, in start
    d = self.lr.start()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 60, in start
    for share in to_scan:
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/local_rescan.py", line 85, in _get_shares
    share = self.vm.shares[sid]
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/file_shelf.py", line 132, in __getitem__
    return self._load_pickle(key, self.key_file(key))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/file_shelf.py", line 124, in _load_pickle
    raise KeyError(key)
KeyError: '303420f9-2e9a-47b8-845c-4f7a5fc6608b'


I have tried deleting my keys, deleting the cache and config folders for couchdb and ubuntuone, deleting the web page entry for the computer - then rebooting and trying to re-setup the computer and I get the same symptoms.

Not sure how to proceed.

---

### Post by cprofitt on 2010-04-21
I found the following solution which appears to have worked for me:

> 
sudo rm -rf ~/.local/share/ubuntuone


link: [https://bugs.launchpad.net/ubuntuone-client/+bug/517505](https://bugs.launchpad.net/ubuntuone-client/+bug/517505)

Hope this helps anyone who has the same issue.

---

### Post by duanedesign on 2010-04-21
The 'pickle error' as i call it is broken/corrupted metadata. I realize you got this fixed but I thought I would post this in case any one else experiences this.

What you look for in the ~/.cache/ubuntuone/syncdaemon.log
```

File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/file_shelf.py", line 124, in _load_pickle
raise KeyError(key)
KeyError: '303420f9-2e9a-47b8-845c-4f7a5fc6608b'
``` 

The workaround (using the logs from OP). Take the Key number and put it in the command below. The syntax is ...shares/a/b/c/abc...:

```
python -c "import cPickle, os; print cPickle.load(open(os.path.expanduser('~/.local/share/ubuntuone/syncdaemon/vm/shares/3/0/3/303420f9-2e9a-47b8-845c-4f7a5fc6608b'), 'r'))"
```

that should show the share metadata or the pickle error.

A simple way to recover from this, is to remove the corrupted metadata file, which will be restored on the syncdaemon startup (after connecting to the server a fetch the shares list)

```
rm ~/.local/share/ubuntuone/syncdaemon/vm/shares/3/0/3/303420f9-2e9a-47b8-845c-4f7a5fc6608b
```

for more info see [bug 506559]("https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/506559")

-
-
Thank you,
duanedesign

---

