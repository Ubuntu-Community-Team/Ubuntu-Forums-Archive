---
title: "Google Calendar app (gcalcli) not working in Ubuntu 13.04"
date: 2013-04-28
forum: The Cafe
---

### Post by sbjaved on 2013-04-28
I'm using Ubuntu 13.04. I use gcalcli to display my google calendar on the desktop using conky. I was using gcalcli (from source) previously on Ubuntu 12.04 and it was working fine. But on 13.04, it fails to authenticate google with an ssl error. It opens a new bowser window and when I click 'grant access' it crashes with an SSL Error.

Here is the error when trying to run gcalcli from terminal:

```
Created new window in existing browser session.
Traceback (most recent call last):
File "/home/saad/Downloads/gcalcli-master/gcalcli", line 2263, in 
BowChickaWowWow()
File "/home/saad/Downloads/gcalcli-master/gcalcli", line 2112, in BowChickaWowWow
client_secret=FLAGS.client_secret
File "/home/saad/Downloads/gcalcli-master/gcalcli", line 460, in init
self._GetCached()
File "/home/saad/Downloads/gcalcli-master/gcalcli", line 548, in GetCached
calList = self._CalService().calendarList().list().execute()
File "/home/saad/Downloads/gcalcli-master/gcalcli", line 501, in _CalService
http=self._GoogleAuth())
File "/home/saad/Downloads/gcalcli-master/gcalcli", line 489, in _GoogleAuth
storage)
File "/usr/local/lib/python2.7/dist-packages/google_api_python_client-1.1-py2.7.egg/oauth2client/util.py", line 128, in positional_wrapper
return wrapped(*args, **kwargs)
File "/usr/local/lib/python2.7/dist-packages/google_api_python_client-1.1-py2.7.egg/oauth2client/tools.py", line 197, in run
credential = flow.step2_exchange(code, http=http)
File "/usr/local/lib/python2.7/dist-packages/google_api_python_client-1.1-py2.7.egg/oauth2client/util.py", line 128, in positional_wrapper
return wrapped(*args, **kwargs)
File "/usr/local/lib/python2.7/dist-packages/google_api_python_client-1.1-py2.7.egg/oauth2client/client.py", line 1283, in step2_exchange
headers=headers)
File "/usr/local/lib/python2.7/dist-packages/httplib2-0.8-py2.7.egg/httplib2/_init__.py", line 1570, in request
(response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)
File "/usr/local/lib/python2.7/dist-packages/httplib2-0.8-py2.7.egg/httplib2/__init__.py", line 1317, in request
(response, content) = self._conn_request(conn, request_uri, method, body, headers)
File "/usr/local/lib/python2.7/dist-packages/httplib2-0.8-py2.7.egg/httplib2/_init__.py", line 1252, in conn_request
conn.connect()
File "/usr/local/lib/python2.7/dist-packages/httplib2-0.8-py2.7.egg/httplib2/_init__.py", line 1021, in connect
self.disable_ssl_certificate_validation, self.ca_certs)
File "/usr/local/lib/python2.7/dist-packages/httplib2-0.8-py2.7.egg/httplib2/__init__.py", line 80, in ssl_wrap_socket
cert_reqs=cert_reqs, ca_certs=ca_certs)
File "/usr/lib/python2.7/ssl.py", line 440, in wrap_socket
ciphers=ciphers)
File "/usr/lib/python2.7/ssl.py", line 198, in __init_
ciphers)
ssl.SSLError: [Errno 185090050] _ssl.c:340: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib
```

I posted the issue on the developer's github page and I was suggested that this was an issue with my python installation in 13.04 and that I should post this on Ubuntu Forums. Anybody has any idea what's going on?

---

