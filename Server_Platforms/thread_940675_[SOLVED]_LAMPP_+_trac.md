---
title: "[SOLVED] LAMPP + trac"
date: 2008-10-07
forum: Server Platforms
---

### Post by x300 on 2008-10-07
**Dont bother, I've fixed it! :D**

I'm trying to set up track with LAMPP. I know that my websever in LAMPP is working, that my SVN is working, and that trac is working. But I want to use LAMPP's Apacheserver, so I've installed FastCGI with LAMPP, but I get this error when trying to open [http://host/trac](http://host/trac)

```
Oops...

Trac detected an internal error: [Errno 2] No such file or directory: '/home/svn/VERSION'

Traceback (most recent call last):
  File "/usr/share/trac/cgi-bin/trac.cgi", line 20, in <module>
    cgi_frontend.run()
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/web/cgi_frontend.py", line 71, in run
    gateway.run(dispatch_request)
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/web/wsgi.py", line 87, in run
    response = application(self.environ, self._start_response)
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/web/main.py", line 381, in dispatch_request
    env = open_environment(env_path, use_cache=not run_once)
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/env.py", line 571, in open_environment
    env = Environment(env_path)
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/env.py", line 190, in __init__
    self.verify()
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/env.py", line 249, in verify
    fd = open(os.path.join(self.path, 'VERSION'), 'r')
IOError: [Errno 2] No such file or directory: '/home/svn/VERSION'

```

edit: I tried to make me an admin for the trac-page, and it gave almost the same errors:

```
$ trac-admin /home/svn/ permission add usr TRAC_ADMIN
Failed to open environment. [Errno 2] No such file or directory: '/home/svn/VERSION'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/admin/console.py", line 162, in env_open
    self.__env = Environment(self.envname)
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/env.py", line 190, in __init__
    self.verify()
  File "/usr/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/env.py", line 249, in verify
    fd = open(os.path.join(self.path, 'VERSION'), 'r')
IOError: [Errno 2] No such file or directory: '/home/svn/VERSION'
```

---

