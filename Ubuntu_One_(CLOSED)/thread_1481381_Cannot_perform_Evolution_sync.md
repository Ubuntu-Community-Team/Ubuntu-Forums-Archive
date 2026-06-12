---
title: "Cannot perform Evolution sync"
date: 2010-05-12
forum: Ubuntu One (CLOSED)
---

### Post by LaptopU on 2010-05-12
I know there are syncing problems with Ubuntu One at the moment, but one of my computers is absolutely fine and another one just won't have anything to do with Ubuntu One contact sync.

This is the last part of my desktop couch replication log -

2010-05-12 18:56:28,873 DEBUG    started replicating
2010-05-12 18:56:28,875 ERROR    replication of discovered hosts aborted
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication.py", line 81, in do_all_replication
    dbus_io.get_seen_paired_hosts(uri=local_uri):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/dbus_io.py", line 136, in get_seen_paired_hosts
    pairing_encyclopedia = couchdb_io.get_all_known_pairings(uri=uri)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 193, in get_all_known_pairings
    db = _get_db("management", uri=uri, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 62, in _get_db
    return server.CouchDatabase(name, create=create, uri=uri, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
    self._reconnect()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 176, in _reconnect
    if self._database_name not in self._server:
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 124, in __contains__
    self.resource.head(validate_dbname(name))
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 981, in head
    return self._request('HEAD', path, headers=headers, **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1014, in _request
    resp, data = _make_request()
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1009, in _make_request
    body=body, headers=headers)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 1129, in request
    (response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 901, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 871, in _conn_request
    response = conn.getresponse()
  File "/usr/lib/python2.6/httplib.py", line 984, in getresponse
    method=self._method)
  File "/usr/lib/python2.6/httplib.py", line 330, in __init__
    self.fp = sock.makefile('rb', 0)
AttributeError: 'NoneType' object has no attribute 'makefile'
2010-05-12 18:56:28,877 ERROR    replication of services aborted
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication.py", line 131, in do_all_replication
    couchdb_io.get_static_paired_hosts(port=local_port):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 105, in get_static_paired_hosts
    db = _get_db("management", uri=uri, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/pair/couchdb_pairing/couchdb_io.py", line 62, in _get_db
    return server.CouchDatabase(name, create=create, uri=uri, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
    self._reconnect()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 176, in _reconnect
    if self._database_name not in self._server:
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 124, in __contains__
    self.resource.head(validate_dbname(name))
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 981, in head
    return self._request('HEAD', path, headers=headers, **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1014, in _request
    resp, data = _make_request()
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1009, in _make_request
    body=body, headers=headers)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 1129, in request
    (response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 901, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 871, in _conn_request
    response = conn.getresponse()
  File "/usr/lib/python2.6/httplib.py", line 984, in getresponse
    method=self._method)
  File "/usr/lib/python2.6/httplib.py", line 330, in __init__
    self.fp = sock.makefile('rb', 0)
AttributeError: 'NoneType' object has no attribute 'makefile'
2010-05-12 18:56:28,878 DEBUG    finished replicating

I can see the contacts fine using the Apache web interface.  Can anyone please help?  I don't think this problem is related to the service issues.

---

### Post by Robertjm on 2010-05-12
Well, in the FWIW department, my Funambol plug-in has not been able to authenticate from my Omnia since yesterday evening.

I had a working setup, but something got messed up so I went ahead and reinstalled it. Now, it won't accept my login/pwd at all.

True, this isn't in Evolution, but it illustrates problems with Contacts.

---

### Post by LaptopU on 2010-05-12
It appears there are some serious problems with syncing in that case, what threw me is on another pc with another account it syncs perfectly, I updated someone's existing contact card and within seconds it was updated online.

---

