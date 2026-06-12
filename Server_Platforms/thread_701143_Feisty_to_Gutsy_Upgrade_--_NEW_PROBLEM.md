---
title: "Feisty to Gutsy Upgrade -- NEW PROBLEM"
date: 2008-02-19
forum: Server Platforms
---

### Post by Treth on 2008-02-19
Ok, so, I've seen a problem similar to this solved several times before.  I have an Ubuntu Feisty server that I've invested a decent amount of configuration into and I want to upgrade rather than freshly install.

I had the problem of the empty versions file, which I corrected.  Every other piece of help I've found solves the 'Failed Upgrade Tool signature' problem, but I also have a 'Failed Upgrade Tool' message.

Any ideas, ladies and gentlemen?

```
root@Server:~# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmpc6cdNA/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1139, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.5/tarfile.py", line 1200, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpc6cdNA/gutsy.tar.gz'
```

---

