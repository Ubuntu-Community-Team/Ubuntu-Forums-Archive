---
title: "Ubuntu One on Lubuntu"
date: 2012-05-19
forum: Ubuntu One (CLOSED)
---

### Post by oslub on 2012-05-19
Hello everyone.

I use Lubuntu on one desktop and Ubuntu on a laptop. Dropbox is my main cloud syncing service but I have created an Ubuntu One SSO account in order to backup my home folders.

At first, I was not able to use Ubuntu One on Lubuntu - after installing it from synaptics, when I tried to open it, nothing happens except opening a blank terminal window. I had to do this tweak to make it work on Lubuntu:
[http://ubuntuforums.org/showthread.php?t=1949533](http://ubuntuforums.org/showthread.php?t=1949533)

After I done this, the Lubuntu bar icons became distinct and logon screen got somewhat misconfigured, having some non-existing usernames in there, but it still works fine so I didn't care much about it.

Now I can open Ubuntu One client and sync files with the cloud service, but I have no option in context menu to sync any other folder in Lubuntu. It only works if I add the files and folders to Ubuntu One parent folder. 

Worse than that, it is causing a failure with Deja Dup backup of my home folder. Here it is what comes up on Deja Dup dialog every time I start Lubuntu:

[HTML]Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1403, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1396, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1247, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/duplicity/commandline.py", line 999, in ProcessCommandLine
    globals.backend = backend.get_backend(args[0])
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 158, in get_backend
    return _backends[pu.scheme](pu)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/u1backend.py", line 74, in __init__
    self.create_volume()
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 323, in iterate
    return fn(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/u1backend.py", line 160, in create_volume
    import ubuntuone.couch.auth as auth
ImportError: No module named couch.auth
[/HTML]Can anyone help me with this? How can I make Ubuntu One sync other folders on Lubuntu? And how to solve this error with Deja Dup backup?

Any help would be much appreciated.

---

### Post by oslub on 2012-05-20
I forgot to mention that this only started to happen when I upgraded from Lubuntu 11.10 to 12.04.

Reinstallation of **ubuntuone-couch** package through synaptics solved it for me. I had to remove it completely and then install again. 

Thread solved.

---

