---
title: "Ubuntu One cli u1sync errors every time"
date: 2010-01-29
forum: Ubuntu One (CLOSED)
---

### Post by wedg on 2010-01-29
Each time I try to run u1sync it errors. 

The directory is already initialized, won't let me re-initialize...

###

jake@lap-dancer:~/django/projects$ ls -laht
total 16K
drwxr-xr-x 4 jake jake 4.0K 2010-01-29 15:48 ssiui
drwxr-xr-x 4 jake jake 4.0K 2010-01-29 15:41 .
drwxr-xr-x 2 jake jake 4.0K 2010-01-29 15:41 .ubuntuone-sync
drwxr-xr-x 4 jake jake 4.0K 2010-01-21 17:56 ..
jake@lap-dancer:~/django/projects$ 

###

jake@lap-dancer:~/django/projects$ u1sync --quiet --action=clobber-server
Error remotely creating /home/jake/django/projects/ssiui/media/blueprint/src/grid.png: INTERNAL_ERROR
Traceback (most recent call last):
  File "/usr/bin/u1sync", line 29, in <module>
    exit(main(*sys.argv))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 462, in main
    do_main(argv=argv)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 444, in capture_exception
    func()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 423, in run_client
    dry_run=options.dry_run, quiet=options.quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 199, in do_sync
    quiet=quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 202, in upload_tree
    sync_mode=uploader, path=path, quiet=quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 182, in sync_tree
    partial_parent=(path, "", None, True), name=u"")
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 68, in generic_merge
    partial_parent=partial_parent)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 127, in pre_merge
    node_type=merged_node.node_type)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 348, in write_file
    name=name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 711, in create_file
    r = self.defer_from_thread(self.factory.current_protocol.make_file,
AttributeError: 'NoneType' object has no attribute 'make_file'
jake@lap-dancer:~/django/projects$ 

###

jake@lap-dancer:~/django/projects$ u1sync --quiet --action=clobber-server
Traceback (most recent call last):
  File "/usr/bin/u1sync", line 29, in <module>
    exit(main(*sys.argv))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 462, in main
    do_main(argv=argv)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 444, in capture_exception
    func()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 423, in run_client
    dry_run=options.dry_run, quiet=options.quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 168, in do_sync
    remote_tree = client.build_tree(info.share_uuid, info.root_uuid)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 576, in build_tree
    raise ValueError("No content available for node %s" % root_uuid)
ValueError: No content available for node 227e0c80-4360-4755-8b9f-3bf7f8d6c22d
jake@lap-dancer:~/django/projects$ 

###

jake@lap-dancer:~/django/projects$ u1sync --quiet --action=clobber-server
Error uploading content for /home/jake/django/projects/ssiui/media/blueprint/plugins/link-icons/icons/im.png: INTERNAL_ERROR
Error uploading content for /home/jake/django/projects/ssiui/media/blueprint/ie.css: INTERNAL_ERROR
Error uploading content for /home/jake/django/projects/ssiui/voicemail/__init__.pyc: INTERNAL_ERROR
Error remotely creating /home/jake/django/projects/ssiui/voicemail/.models.py.swp: INTERNAL_ERROR
Traceback (most recent call last):
  File "/usr/bin/u1sync", line 29, in <module>
    exit(main(*sys.argv))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 462, in main
    do_main(argv=argv)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 444, in capture_exception
    func()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 423, in run_client
    dry_run=options.dry_run, quiet=options.quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 199, in do_sync
    quiet=quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 202, in upload_tree
    sync_mode=uploader, path=path, quiet=quiet)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 182, in sync_tree
    partial_parent=(path, "", None, True), name=u"")
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 83, in generic_merge
    name=child_name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/genericmerge.py", line 68, in generic_merge
    partial_parent=partial_parent)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 127, in pre_merge
    node_type=merged_node.node_type)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/sync.py", line 348, in write_file
    name=name)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 711, in create_file
    r = self.defer_from_thread(self.factory.current_protocol.make_file,
AttributeError: 'NoneType' object has no attribute 'make_file'
jake@lap-dancer:~/django/projects$

###

There was also one other error that appeared that I can't get it to reproduce now...

I've already checked that the python-ubuntuone-storageprotocol library and other ubuntuone-* packages are up to date.

Is this a common problem or something with a known fix? Is maybe u1sync not stable enough to use yet?

---

### Post by duanedesign on 2010-02-01
wedg,
currently Ubuntu One will only sync the folder ~/Ubuntu One. Copy your ~/django/projects directory into your Ubuntu One folder ~/Ubuntu One/django/projects. The Ubuntu One Team is working on adding the functionality to be able to specify alternate folders.

Please let us know if this helps, or if you experience any other difficulties.

Thank you,
duanedesign

---

