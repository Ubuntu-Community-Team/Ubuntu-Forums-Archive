---
title: "Need some help getting a simple trac server running"
date: 2009-06-24
forum: Server Platforms
---

### Post by porchrat on 2009-06-24
OK even though I'm not actually running an Ubuntu server release (I am running a Desktop version that does sometimes function as a small server) I thought this would be the best place to post this, if it isn't then I do apologise and please feel free to move it elsewhere.

OK so I have installed trac (from the repos), I currently run svn to monitor changes to some code, but changes are started to accelerate a little and I need a bug tracker system and a wiki, so trac seemed like the logical choice.

I don't run apache and I don't really want to if I can avoid it (unless it is easy to install and administer and solves my problems - I have no experience with apache).

I haven't yet tried to run trac with SVN because I'm just starting off simple. I have tried starting a standalone (tracd) server using this command:

```
tracd -p 8000 --hostname=localhost /path_to_environment/
```

and it printed nothing which I thought was a little strange. When I tried to navigate to [http://localhost:8000/](http://localhost:8000/) it threw this:

```
Exception happened during processing of request from ('127.0.0.1', 49356)
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
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 363, in dispatch_request
    env_paths)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 456, in send_project_index
    req.hdf = HDFWrapper(loadpaths)
  File "/var/lib/python-support/python2.5/trac/web/clearsilver.py", line 135, in __init__
    raise TracError, "ClearSilver not installed (%s)" % e
TracError: ClearSilver not installed (/usr/lib/python2.5/site-packages/neo_cgi.so: undefined symbol: Py_InitModule4)
----------------------------------------
127.0.0.1 - - [24/Jun/2009 10:51:45] "GET /favicon.ico HTTP/1.1" 404 -
127.0.0.1 - - [24/Jun/2009 10:51:48] "GET /favicon.ico HTTP/1.1" 404 -
```

What exactly does this mean?

I thought I had installed all of the python-oriented dependencies, was there something I missed?

Another thing is that I would like to be able to use an RSA key or something for authentication instead of just using a password and unfortunately I can't find any reference to being able to do that through tracd, does that mean I will need to run this through apache2?

---

### Post by porchrat on 2009-06-24
Just an update, I noticed that it said that clearsilver wasn't installed so I went and checked and the python-clearsilver package is installed.

---

### Post by porchrat on 2009-06-24
For anyone following this, both currently and in the future it looks as though there is a problem with ClearSilver and Hardy 64bit, and that I am going to need to download another version of ClearLight to replace the one Hardy is running at the moment.

[Here]("http://yousefourabi.com/blog/linux/trac-install-broken-on-64bit-ubuntu") is a link to a discussion of this issue.

Fingers crossed.

---

### Post by porchrat on 2009-06-24
OK managed to get SilverClear running properly now. Had to rebuild it (with a slight modification to a few lines to get it running with python 2.5). Turns out the one that comes with Hardy 64bit systems had some bugs, but it is all sorted now.

Now I can get to working with it and figuring out the best setup.

The previous question still stands though. How do I get trac to authenticate with RSA keys instead of with passwords? Has anyone managed to achieve this and if so how did you go about it? All input would be greatly appreciated.

---

