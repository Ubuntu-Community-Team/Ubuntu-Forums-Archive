---
title: "Can't add my computer to U1"
date: 2011-10-01
forum: Ubuntu One (CLOSED)
---

### Post by JCM_Pico on 2011-10-01
Hello,

I recently had to remove my computer from ubuntu one. Now I want to get it back on the cloud, but when I go to System > Preferences > Ubuntu One and click on Manage account, I am not able to connect any device to my account...
Do any one knows how to do this?

PS. - running Ubuntu 10.04

---

### Post by thefasterblueone on 2011-10-01
Maybe this thread will help you.

[http://ubuntuforums.org/showthread.php?t=1297076]("http://ubuntuforums.org/showthread.php?t=1297076")

---

### Post by JCM_Pico on 2011-10-01
> **thefasterblueone said:**
> Maybe this thread will help you.

[http://ubuntuforums.org/showthread.php?t=1297076](http://ubuntuforums.org/showthread.php?t=1297076)


It didn't, the procedure described in that tread did not work for me....
It's very strange since I'm not able to login in ubuntu one from ubuntu neither add my computer in the U1 web page....

---

### Post by JCM_Pico on 2011-10-01
I got this from running ubuntuone-preferences from terminal

```
ubuntuone-preferences 
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/bin/ubuntuone-preferences", line 1084, in got_newcredentials
    self.present()
  File "/usr/bin/ubuntuone-preferences", line 1072, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 748, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 157, in __init__
    ctx=ctx)
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
  File "/usr/lib/python2.6/httplib.py", line 986, in getresponse
    response.begin()
  File "/usr/lib/python2.6/httplib.py", line 391, in begin
    version, status, reason = self._read_status()
  File "/usr/lib/python2.6/httplib.py", line 355, in _read_status
    raise BadStatusLine(line)
BadStatusLine
```

---

### Post by oldos2er on 2011-10-01
Thread moved to Ubuntu One.

---

