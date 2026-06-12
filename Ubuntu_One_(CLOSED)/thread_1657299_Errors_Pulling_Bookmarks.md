---
title: "Errors Pulling Bookmarks"
date: 2011-01-01
forum: Ubuntu One (CLOSED)
---

### Post by DiagonalArg on 2011-01-01
I'm getting a lot of stuff like this in ~/.cache/desktop-couch/log/desktop-couch-replication.log (below).  Can someone tell me what's up with this??

(Also, an unrelated question, I have some bookmarks that are "read only".  They are produced by a firefox extension that saves some information in the unsorted bookmarks.  I have set the folder to r/w, but am wondering what u1 would do if I had not - both when pulling the bookmarks up to the server and when pushing them back down.)

Thanks all -
DA.


2010-12-31 19:52:45,007 DEBUG    want to replipull 'bookmarks' from static host 'c2575658-1ace-4449-95f7-8ef119d55fd5' @ couchdb.one.ubuntu.com
2010-12-31 19:52:45,007 INFO     Connecting to [http://localhost:54083/](http://localhost:54083/).
2010-12-31 19:52:45,018 DEBUG    db exists, and we're ready to replicate
2010-12-31 19:52:45,018 DEBUG    asking 'http://localhost:54083/' to replicate {'url': 'https://couchdb.one.ubuntu.com/u%2Fb08%2F0cf%2F843038%2Fbookmarks', 'auth': {'oauth': {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidd\
en', dbus.String(u'token'): dbus.String(u'uxHjJHuqcQAXMSSOAQGMlQCEhMPNUBozNWhGIXvvFJrAuzmGjc'), dbus.String(u'consumer_key'): dbus.String(u'YmKYkpr'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ iMac'), dbus.String(u'token_secret'):\
 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}} to bookmarks
2010-12-31 19:52:47,791 ERROR    can't replicate 'u/b08/0cf/843038/bookmarks'  'http://localhost:54083/' <== {'source': {'url': 'https://couchdb.one.ubuntu.com/u%2Fb08%2F0cf%2F843038%2Fbookmarks', 'auth': {'oauth': {dbus.String(u'consume\
r_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'uxHjJHuqcQAXMSSOAQGMlQCEhMPNUBozNWhGIXvvFJrAuzmGjc'), dbus.String(u'consumer_key'): dbus.String(u'YmKYkpr'), dbus.String(u'name'): dbus.String(u'Ubuntu On\
e @ iMac'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}}, 'target': 'bookmarks'}
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 288, in replicate
    content=record)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 985, in post
    **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1035, in _request
    raise ServerError((status_code, error))
ServerError: (500, ('json_encode', '{bad_term,<0.346.0>}'))

---

### Post by DiagonalArg on 2011-01-25
(bump)

Two questions there, any thoughts?  ... Thanks.

---

