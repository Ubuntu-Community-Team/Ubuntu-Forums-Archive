---
title: "Getting Trac working on Ubuntu 8.04"
date: 2008-06-16
forum: Server Platforms
---

### Post by damien_d on 2008-06-16
Hello,

I have been attempting to install Trac as a nice interface for my SVN repository I am using for my own projects.  It's running on Ubuntu 8.04 x86_64.  I am following the following instructions:

[http://ariejan.net/2006/12/01/how-to-setup-a-ubuntu-development-server-part-1/](http://ariejan.net/2006/12/01/how-to-setup-a-ubuntu-development-server-part-1/)
[http://ariejan.net/2006/12/02/how-to-setup-a-ubuntu-development-server-part-2/](http://ariejan.net/2006/12/02/how-to-setup-a-ubuntu-development-server-part-2/)

I have successfully gotten the first part running (i.e. web browsing of the SVN repository, but not in Trac), but after I install trac and use the test instructions given by the installer:

tracd --port 8000 /var/lib/trac/matlab

And then navigate to the following using firefox:
[http://localhost:8000/matlab](http://localhost:8000/matlab)

It seems to go blat and spits out the following stacktrace in the terminal:
```

damien@mediabox:/var/lib/trac$ tracd --port 8000 /var/lib/trac/matlab
----------------------------------------
Exception happened during processing of request from ('127.0.0.1', 57338)
Traceback (most recent call last):
  File "/usr/lib/python2.5/SocketServer.py", line 464, in process_request_thread
    self.finish_request(request, client_address)
  File "/usr/lib/python2.5/SocketServer.py", line 254, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib/python2.5/SocketServer.py", line 522, in __init__
    self.handle()
  File "/usr/lib/python2.5/BaseHTTPServer.py", line 316, in handle
    self.handle_one_request()
  File "/var/lib/python-support/python2.5/trac/web/wsgi.py", line 174, in handle_one_request
    gateway.run(self.server.application)
  File "/var/lib/python-support/python2.5/trac/web/wsgi.py", line 87, in run
    response = application(self.environ, self._start_response)
  File "/var/lib/python-support/python2.5/trac/web/standalone.py", line 88, in __call__
    return self.application(environ, start_response)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 430, in dispatch_request
    env.log.exception(e)
AttributeError: 'NoneType' object has no attribute 'log'
----------------------------------------

```

Unfortunately I know pretty much nothing about Apache, python and  web stuff in general.

What config files/other stuff is needed to help solve this?

Cheers
Damien.

---

### Post by damien_d on 2008-06-18
I somehow solved it using the "official" trac instructions:

[http://trac.edgewall.org/wiki/0.11/TracOnUbuntu](http://trac.edgewall.org/wiki/0.11/TracOnUbuntu)

And I have since learned that the "tracd" command is a **substitute** for apache2.  

Better start learning some web admin stuff instead of just programming :)

---

