---
title: "Contacts not synching bidirectionally between Evolution and U1"
date: 2010-11-07
forum: Ubuntu One (CLOSED)
---

### Post by silvari on 2010-11-07
[FONT="Tahoma"]**Problem:** Contacts in 'the cloud' don't synch down to my Evolution\CouchDB\UbuntuOne address book. However, new contacts I add locally to my Evolution\CouchDB\UbuntuOne address 
book, do show up in my account at one.ubuntu.com

**Background:**  
[LIST]
[*]Several months ago I signed up for the 'free' UbuntuOne account, and as a result, my 250+ contacts were synched up to the cloud. However this was not done via a synch of Evolution to the cloud; the contacts came from my iPhone, as I had signed up for the free beta of the 'phone synch' product (or whatever it was called at the time). I never bothered with getting my UbuntuOne contacts to appear in Evolution.
[*]Fast forward to a couple weeks ago when I 'upgraded' from 10.04 to 10.10 . I didn't actually upgrade, I wiped my / partition and did a fresh install (however I kept /home, and everything from my account on home showed up just fine when I logged in after 10.10 was installed). 
[*]Then yesterday I decided to pay the $ for the 20GB as well as for the Ubuntu One Mobile service. The latter worked perfectly, I didn't even need to reconfigure my iPhone's Ubuntu One client, I just ran a Synch and changes between my phone and the cloud were synchronized. Yay.
[*]But now I'd like to have my UbuntuOne/iPhone contacts accessible within Evolution. When I first began this endeavour, no contacts were listed under the volution\CouchDB\UbuntuOne AddressBook (except three 'blank' records that I could see existing in the CouchDB). I added three new contacts to that address book, and confirmed that they are now in 'in the cloud' i.e. I can see them when I log into my account on One.Ubuntu.com . But still, none of my other contacts in the cloud, have appeared in the Evolution addressbook.
[/LIST]


I've tried a number of things to make this happen, to now avail. Mostly I've taken steps according to the pages listed here:

  [https://wiki.ubuntu.com/UbuntuOne/FAQ/WhyArentMyContactsSyncing](https://wiki.ubuntu.com/UbuntuOne/FAQ/WhyArentMyContactsSyncing)
  [https://wiki.ubuntu.com/UbuntuOne/Bugs](https://wiki.ubuntu.com/UbuntuOne/Bugs)
  [http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting](http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting)


Below are some messages from ~/.cache/desktop-couch/log/desktop-couch-replication.log  that may be relevant.[/FONT]

2010-11-06 22:40:23,931 DEBUG    Got list of databases from <OAuthCapableServer 'https://couchdb.one.ubuntu.com/'>/_all_dbs?user_id=200963:
    set(['u/ed1/502/200963/contacts', 'u/ed1/502/200963/_users', 'u/ed1/502/200963/bookmarks', 'u/ed1/502/200963/notes'])
2010-11-06 22:40:23,932 DEBUG    want to replipull 'contacts' from static host 'b493835b-b36c-4f9b-a9a4-cc5492205a5d' @ couchdb.one.ubuntu.com
2010-11-06 22:40:23,933 INFO     Connecting to [http://localhost:53966/](http://localhost:53966/).
2010-11-06 22:40:23,966 DEBUG    db exists, and we're ready to replicate
2010-11-06 22:40:23,967 DEBUG    asking 'http://localhost:53966/' to replicate {'url': 'https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts', 'auth': {'oauth': {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'lAJPBXbJobdoVpbAaadUEMxcpYdvLtoXMrMCjYoVXqxNLctUuD'), dbus.String(u'consumer_key'): dbus.String(u'BnH3RxG'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ homebase'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}} to contacts
2010-11-06 22:43:41,016 ERROR    can't replicate 'u/ed1/502/200963/contacts'  'http://localhost:53966/' <== {'source': {'url': 'https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts', 'auth': {'oauth': {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'lAJPBXbJobdoVpbAaadUEMxcpYdvLtoXMrMCjYoVXqxNLctUuD'), dbus.String(u'consumer_key'): dbus.String(u'BnH3RxG'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ homebase'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}}, 'target': 'contacts'}
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 288, in replicate
    content=record)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 985, in post
    **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1035, in _request
    raise ServerError((status_code, error))
ServerError: (500, ('json_encode', '{bad_term,<0.4199.0>}'))
2010-11-06 22:43:41,019 DEBUG    want to replipull '_users' from static host 'b493835b-b36c-4f9b-a9a4-cc5492205a5d' @ couchdb.one.ubuntu.com
2010-11-06 22:43:41,020 INFO     Connecting to [http://localhost:53966/](http://localhost:53966/).
2010-11-06 22:43:41,022 ERROR    can't create/verify '_users' None:53966  oauth=None
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 249, in replicate
    server.CouchDatabase(target_database, create=True, uri=local_uri)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 56, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 155, in __init__
    self._reconnect()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 64, in _reconnect
    super(CouchDatabase, self)._reconnect(uri=uri)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 187, in _reconnect
    if self._database_name not in self._server:
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 124, in __contains__
    self.resource.head(validate_dbname(name))
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1095, in validate_dbname
    raise ValueError('Invalid database name')
ValueError: Invalid database name

---

### Post by silvari on 2010-11-07
Well, there's been some development since yesterday. At some point this started working; in Evolution I can now see all the contacts in my CouchDB\UbuntuOne address book. Hooray, that only took dozen hours or so. (For < 300 contacts.)

So I went ahead and created a new contact on my iPhone; and using the U1 Contacts app, successfully synched with the cloud. I see the new contact when I log into my UbuntuOne account via web browser. Again, Hooray (for real, this time).

However after waiting at least 15 minutes, I did not see this new contact in Evolution. Restarted Evolution a couple times, did not help. After about a half hour I start tailing the logs again...

2010-11-07 19:37:29,619 DEBUG    want to replipush 'u/ed1/502/200963/contacts' to static host 'b493835b-b36c-4f9b-a9a4-cc5492205a5d' @ couchdb.one.ubuntu.com
2010-11-07 19:37:29,621 DEBUG    creating 'u/ed1/502/200963/contacts' couchdb.one.ubuntu.com:443 {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'lAJPBXbJobdoVpbAaadUEMxcpYdvLtoXMrMCjYoVXqxNLctUuD'), dbus.String(u'consumer_key'): dbus.String(u'BnH3RxG'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ homebase'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}
2010-11-07 19:37:29,622 INFO     Connecting to [https://couchdb.one.ubuntu.com/](https://couchdb.one.ubuntu.com/).
2010-11-07 19:37:31,221 DEBUG    db exists, and we're ready to replicate
2010-11-07 19:37:31,222 DEBUG    asking 'http://localhost:53966/' to replicate contacts to {'url': 'https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts', 'auth': {'oauth': {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'lAJPBXbJobdoVpbAaadUEMxcpYdvLtoXMrMCjYoVXqxNLctUuD'), dbus.String(u'consumer_key'): dbus.String(u'BnH3RxG'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ homebase'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}}
--> 2010-11-07 19:38:01,256 ERROR    can't replicate 'contacts'  'http://localhost:53966/' <== {'source': 'contacts', 'target': {'url': 'https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts', 'auth': {'oauth': {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'lAJPBXbJobdoVpbAaadUEMxcpYdvLtoXMrMCjYoVXqxNLctUuD'), dbus.String(u'consumer_key'): dbus.String(u'BnH3RxG'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ homebase'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}}}
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 288, in replicate
    content=record)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 985, in post
    **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1029, in _request
    raise ResourceNotFound(error)
ResourceNotFound: ('db_not_found', 'could not open [https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts/](https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts/)')

2010-11-07 19:46:33,488 DEBUG    want to replipull 'contacts' from static host 'b493835b-b36c-4f9b-a9a4-cc5492205a5d' @ couchdb.one.ubuntu.com
2010-11-07 19:46:33,488 INFO     Connecting to [http://localhost:53966/](http://localhost:53966/).
2010-11-07 19:46:33,540 DEBUG    db exists, and we're ready to replicate
2010-11-07 19:46:33,542 DEBUG    asking 'http://localhost:53966/' to replicate {'url': 'https://couchdb.one.ubuntu.com/u%2Fed1%2F502%2F200963%2Fcontacts', 'auth': {'oauth': {dbus.String(u'consumer_secret'): 'HiddenHiddenHiddenHiddenHidden', dbus.String(u'token'): dbus.String(u'lAJPBXbJobdoVpbAaadUEMxcpYdvLtoXMrMCjYoVXqxNLctUuD'), dbus.String(u'consumer_key'): dbus.String(u'BnH3RxG'), dbus.String(u'name'): dbus.String(u'Ubuntu One @ homebase'), dbus.String(u'token_secret'): 'HiddenHiddenHiddenHiddenHiddenHiddenHiddenHiddenHi'}}} to contacts

Then it just sits there, until...

2010-11-07 19:54:57,808 DEBUG    replicate result:  {'status': '200', 'content-length': '965', 'server': 'CouchDB/1.0.1 (Erlang OTP/R13B)', 'cache-control': 'must-revalidate', 'date': 'Mon, 08 Nov 2010 03:54:57 GMT', 'content-type': 'application/json'}  {'ok': True, 'source_last_seq': 394, 'session_id': 'ccdf4494334dfce50997214c747a9178', 'history': [{'missing_found': 4, 'end_last_seq': 394, 'docs_written': 4, 'start_time': 'Mon, 08 Nov 2010 03:51:11 GMT', 'recorded_seq': 394, 'docs_read': 4, 'session_id': 'ccdf4494334dfce50997214c747a9178', 'start_last_seq': 390, 'end_time': 'Mon, 08 Nov 2010 03:51:12 GMT', 'doc_write_failures': 0, 'missing_checked': 0}, {'missing_found': 0, 'end_last_seq': 390, 'docs_written': 0, 'start_time': 'Sun, 07 Nov 2010 19:53:51 GMT', 'recorded_seq': 390, 'docs_read': 0, 'session_id': '81d200f9e6478ececc3d05891109feb2', 'start_last_seq': 387, 'end_time': 'Sun, 07 Nov 2010 19:53:52 GMT', 'doc_write_failures': 0, 'missing_checked': 0}, {'missing_found': 287, 'end_last_seq': 387, 'docs_written': 287, 'start_time': 'Sun, 07 Nov 2010 19:43:57 GMT', 'recorded_seq': 387, 'docs_read': 287, 'session_id': '3dfb61c053c3a4f2a46fec43d54a9fb9', 'start_last_seq': 0, 'end_time': 'Sun, 07 Nov 2010 19:45:14 GMT', 'doc_write_failures': 0, 'missing_checked': 0}]}
2010-11-07 19:54:57,809 DEBUG    want to replipull '_users' from static host 'b493835b-b36c-4f9b-a9a4-cc5492205a5d' @ couchdb.one.ubuntu.com
2010-11-07 19:54:57,810 INFO     Connecting to [http://localhost:53966/](http://localhost:53966/).
2010-11-07 19:54:57,811 ERROR    can't create/verify '_users' None:53966  oauth=None
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 249, in replicate
    server.CouchDatabase(target_database, create=True, uri=local_uri)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 56, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 155, in __init__
    self._reconnect()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 64, in _reconnect
    super(CouchDatabase, self)._reconnect(uri=uri)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 187, in _reconnect
    if self._database_name not in self._server:
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 124, in __contains__
    self.resource.head(validate_dbname(name))
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1095, in validate_dbname
    raise ValueError('Invalid database name')
ValueError: Invalid database name



At this point I say to myself, "Guess I'll have to wait another dozen hours." But then I go into Evolution, and: THERE IT IS. Surprise. The contact has finally replicated from UbuntuOne down to my local CouchDB, after about 45 minutes. I would not have guessed that had happened, by looking at the log entries above.

I wonder if/where is the setting which controls how frequently desktop-couchdb will attempt to pull new contacts down from the cloud.

---

