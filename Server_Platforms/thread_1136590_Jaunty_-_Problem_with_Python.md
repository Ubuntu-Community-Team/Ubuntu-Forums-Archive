---
title: "Jaunty - Problem with Python"
date: 2009-04-25
forum: Server Platforms
---

### Post by nfn on 2009-04-25
Hi,

I'm running a VPS at Linode with Ubuntu 8.10. Everything is running well.
Yesterday I setup a new linode to move things to Jaunty (9.04) but I'm facing problems with Python.

I downloaded the server iso and installed in vmware. The problem persists:

I'm running duplicity to backup to S3 using this scripts:
[http://www.linode.com/forums/viewtopic.php?p=14974](http://www.linode.com/forums/viewtopic.php?p=14974)

When I run duplicity-restores.sh "2004-04-23" etc etc in 8.10 everything works well.
In 9.04 I get:

```
root@ubuntu:~/scripts# ./duplicity-restore.sh "2009-04-23" etc etc
/var/lib/python-support/python2.6/boto/utils.py:42: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/var/lib/python-support/python2.6/boto/utils.py:45: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  import popen2, os, StringIO
/var/lib/python-support/python2.6/boto/s3/key.py:23: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 582, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 576, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 539, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 299, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 463, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 437, in integrate_patch_iters
    for patch_seq in collated:
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 338, in yield_tuples
    setrorps(overflow, elems)
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 327, in setrorps
    try: elems[i] = iter_list[i].next()
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 85, in filter_path_iter
    for path in path_iter:
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 98, in difftar2path_iter
    tarinfo_list = [tar_iter.next()]
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 290, in next
    if not self.tarfile: self.set_tarfile()
  File "/usr/lib/python2.6/dist-packages/duplicity/patchdir.py", line 285, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 326, in get_fileobj_iter
    manifest = backup_set.get_manifest()
  File "/usr/lib/python2.6/dist-packages/duplicity/collections.py", line 173, in get_manifest
    return self.get_remote_manifest()
  File "/usr/lib/python2.6/dist-packages/duplicity/collections.py", line 160, in get_remote_manifest
    manifest_buffer = self.backend.get_data(self.remote_manifest_name)
  File "/usr/lib/python2.6/dist-packages/duplicity/backend.py", line 365, in get_data
    assert not fin.close()
  File "/usr/lib/python2.6/dist-packages/duplicity/dup_temp.py", line 118, in close
    assert not self.fileobj.close()
  File "/usr/lib/python2.6/dist-packages/duplicity/gpg.py", line 162, in close
    self.gpg_process.wait()
  File "/var/lib/python-support/python2.6/GnuPGInterface.py", line 639, in wait
    raise IOError, "GnuPG exited non-zero, with code %d" % (e >> 8)
IOError: GnuPG exited non-zero, with code 2

```

---

