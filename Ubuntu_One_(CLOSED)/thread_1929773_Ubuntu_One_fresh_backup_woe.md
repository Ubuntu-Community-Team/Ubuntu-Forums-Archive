---
title: "Ubuntu One fresh backup woe"
date: 2012-02-22
forum: Ubuntu One (CLOSED)
---

### Post by BigJules on 2012-02-22
A real conundrum. 

After 6 months hassle-free Ubuntu-one backups with Deja-dup on 2 identical machines, had occasion to clean-install again on one (11.10/Unity). That was more than a week ago, and since then I've never been able to do a fresh backup, let alone routine incrementals. It powers away, uploading to U1 fine, folders created, filling - then the backup fails at a random point some hours into it with all kinds of error, the most recent being a 302 unknown and the following which is typical:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1359, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1342, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1202, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/duplicity/commandline.py", line 950, in ProcessCommandLine
    backup, local_pathname = set_backend(args[0], args[1])
  File "/usr/lib/python2.7/dist-packages/duplicity/commandline.py", line 843, in set_backend
    globals.backend = backend.get_backend(bend)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 156, in get_backend
    return _backends[pu.scheme](pu)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/u1backend.py", line 74, in __init__
    self.create_volume()
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 319, in iterate
    return fn(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/u1backend.py", line 161, in create_volume
    answer = auth.request(self.volume_uri, http_method="PUT")
  File "/usr/lib/python2.7/dist-packages/ubuntuone-couch/ubuntuone/couch/auth.py", line 147, in request
    url, method=http_method, headers=headers, body=request_body)
  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 1436, in request
    (response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)
  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 1188, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 1129, in _conn_request
    raise ServerNotFoundError("Unable to find the server at %s" % conn.host)
ServerNotFoundError: Unable to find the server at one.ubuntu.com

Backing up a token < 1MB folder is faultless, even mid-sized ones, but fresh backups never. I've done (some several times) and not in order:
+ Mostly unattended night-time backups, but 23 hrs the longest
+ Tried 11 times; 500, 502, 302 errors, most common is above
+ did test restore on failed backup, succeeded
+ did fresh backup to existing U1 folder, fail
+ changed the U1 folder name to new one, fail
+ did the full-size backup as an incremental to the same U1 folder as a successful token one, fail
+ went thru all the u1sdtool -s, -c and so on, all fine as per a successful state, as does --list-folder and -delete
+ reinstalled Deja-dup
+ reinstalled U1 client
+ reinstalled the entire system

I'm persevering because up until now it's been the best backup solution I've ever had, and there's that identical machine in another room perfectly happy sharing the same U1 account. Mind you, I haven't had a fresh backup on that for a month or so...

I really need to get on top of this as this machine is what I earn my crust with and its making me nervous!

[SOLVED] - see last post below

---

### Post by BigJules on 2012-02-22
Spoke too soon - now the other system has failed with the same errors. Starting to get tedious...

---

### Post by BigJules on 2012-02-25
Well, not so much a Solution as a workaround.

After way too much log decoding, the conclusion is undeniable: Deja Dup is doing its thing 100% while U One is throwing random errors, each of which sends you off up a blind alley. Trial and error came up with a result: It's all down to the traffic numbers in the upload. If this can be reduced to < 1GB at a time the whole thing works flawlessly, nary an error to be seen.

So: a 'fresh' backup has to be done this way. 

Using baobab, see if there are natural < 1GB chunks in the data, if not, create holding folders. I'll call the whole target backup TOP-BAK, and within it the BAK-1, BAK-2, BAK-3 1GB containing folders. Set up Deja Dup to create a new storage folder on U One, in the includes have TOP-BAK alone, in the excludes BAK-2, BAK-3. 

Let her run. A 1st run fresh backup will be completed containing BAK-1 only. 
Then alter Deja Dup to delete BAK-2 out of the excludes, and run again. Deja thinks that you've since added BAK-2 to your data and will treat it all as an ordinary incremental, adding the recent data. 
Then do another, deleting BAK-3 out of the excludes, and the same thing will occur, the actual traffic to the U One servers being limited to what's changed/added only which is < 1GB.

There's a delightful side effect to all of this: where before I was looking at 14 hours or so for a 'fresh' backup, this morning the whole thing was done and dusted within 2 1/2 hours, don't ask why.

+ Useful tips:

(1) Deleting whole folders on your Ubuntu One account instead of individual files, fire up your trusty terminal and enter:

$ u1sdtool --list-folders >folder-id.txt  
This will provide the id numbers of active folders in your Ubuntu One account.

$ u1sdtool --delete-folder=45c7...  
Where 45c7...etc is the number part of the delete target folder id, which of course you'll Ctrl-c from folder-id.txt so as to Shift-Ctrl-v into the terminal)

This command comes with installing Ubuntu One. The man is worth a look.

(2) Properly removing the Ubuntu One client to start afresh:

# rm -rf ~/.local/share/ubuntuone
$ rm -rf ~/.config/ubuntuone
$ rm -rf ~/.cache/ubuntuone
$ rm -rf ~/Ubuntu\ One
Go to Passwords/Keyring and delete Ubuntu One
# apt-get purge ubuntuone-client* python-ubuntuone-storage*

Reboot and:
# apt-get ubuntuone-client* python-ubuntuone-storage*

and perform the usual joining ceremonials

---

