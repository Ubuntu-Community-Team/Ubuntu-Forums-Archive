---
title: "OpenERP and Drupal environment don't get along...."
date: 2011-05-20
forum: Server Platforms
---

### Post by Kivech on 2011-05-20
Just posted this message on the OpenERP forums, but I expect more from this community. ):P
> Hi all,

I had OpenERP completely installed and running just fine. All basic install instructions just worked out of the box on Ubuntu 11.04.

Now, we also are going to develop our own web site. For that we needed a web development environment. Due to the small size of our home business, we have to do it all on one PC.

So I went ahead and installed everything needed to get Drupal going, among which I had to install:
LAMP
Drupal
Memcached
Memcache
Postfix
Tomcat
and other packages.

It all works like a charm, but now my openerp-web crashes when I start it with the following message:
```
[20/May/2011:16:17:19] ENGINE Bus STARTING
[20/May/2011:16:17:19] ENGINE Started monitor thread '_TimeoutMonitor'.
[20/May/2011:16:17:19] ENGINE Started monitor thread 'Autoreloader'.
[20/May/2011:16:17:24] ENGINE Error in 'start' listener <bound method Server.start of <cherrypy._cpserver.Server object at 0x26040d0>>
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/wspbus.py", line 147, in publish
    output.append(listener(*args, **kwargs))
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/_cpserver.py", line 90, in start
    ServerAdapter.start(self)
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/servers.py", line 53, in start
    wait_for_free_port(*self.bind_addr)
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/servers.py", line 251, in wait_for_free_port
    raise IOError("Port %r not free on %r" % (port, host))
IOError: Port 8080 not free on '0.0.0.0'

[20/May/2011:16:17:24] ENGINE Shutting down due to error in start listener:
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/wspbus.py", line 184, in start
    self.publish('start')
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/wspbus.py", line 147, in publish
    output.append(listener(*args, **kwargs))
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/_cpserver.py", line 90, in start
    ServerAdapter.start(self)
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/servers.py", line 53, in start
    wait_for_free_port(*self.bind_addr)
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/servers.py", line 251, in wait_for_free_port
    raise IOError("Port %r not free on %r" % (port, host))
IOError: Port 8080 not free on '0.0.0.0'

[20/May/2011:16:17:24] ENGINE Bus STOPPING
[20/May/2011:16:17:24] ENGINE HTTP Server cherrypy._cpwsgi_server.CPWSGIServer(('0.0.0.0', 8080)) already shut down
[20/May/2011:16:17:24] ENGINE Stopped thread 'Autoreloader'.
[20/May/2011:16:17:24] ENGINE Stopped thread '_TimeoutMonitor'.
[20/May/2011:16:17:24] ENGINE Bus STOPPED
[20/May/2011:16:17:24] ENGINE Bus EXITING
[20/May/2011:16:17:24] ENGINE Bus EXITED
Traceback (most recent call last):
  File "/usr/local/bin/openerp-web", line 5, in <module>
    pkg_resources.run_script('openerp-web==6.0.2', 'openerp-web')
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 467, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1200, in run_script
    execfile(script_filename, namespace, namespace)
  File "/usr/local/lib/python2.7/dist-packages/openerp_web-6.0.2-py2.7.egg/EGG-INFO/scripts/openerp-web", line 8, in <module>
    start()
  File "/usr/local/lib/python2.7/dist-packages/openerp_web-6.0.2-py2.7.egg/openobject/commands.py", line 78, in start
    cherrypy.engine.start()
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/wspbus.py", line 184, in start
    self.publish('start')
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/wspbus.py", line 147, in publish
    output.append(listener(*args, **kwargs))
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/_cpserver.py", line 90, in start
    ServerAdapter.start(self)
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/servers.py", line 53, in start
    wait_for_free_port(*self.bind_addr)
  File "/usr/local/lib/python2.7/dist-packages/CherryPy-3.1.2-py2.7.egg/cherrypy/process/servers.py", line 251, in wait_for_free_port
    raise IOError("Port %r not free on %r" % (port, host))
IOError: Port 8080 not free on '0.0.0.0'

```

Obviously, something of what I installed is either occupying the 8080 port or blocking it in some other fashion.

Now the online install document claims that there should be a configuration file for the web client in my home directory, but there isn't.

Does anyone know how I can get my web client to work again, without messing up my web development environment. (Really, that took me two days to install and set up, I'd be really upset if that one were to get ruined.)

The thing is though, that both environments have to run on the same machine, simply because we do not have the budget to create servers.
I'm sure there is a way, but I am not technically apt enough to do it myself and need a hand to get openerp-web running again.

Thanks for reading and any help is very much appreciated.

The whole Drupal environment was quite a heavy delivery, since I went the manual route for flexibility. For an ex-semi-techie, that was not an easy route to take, especially considering that I had to combine about 12 HOWTOs to get everything working properly, dodging errors in many.

Anyway, my Drupal/web-development environment is working properly (as far as I can tell), but the web client module of OpenERP is messed up.

For those that do not know it: it is a module that interfaces with the OpenERP server software to allow people to access the system through their web browser, effectively eliminating the use to install a client on their PC. Very practical for our light weight laptop that we use in combination with my PC.

Normally one would connect by browsing to [http://hostname:8080](http://hostname:8080) and automatically get connected with the OpenERP environment.
Now, however, that does not work anymore with the above error as a result. Do you guys have any idea if I have to configure something in Apache to get this working again? Possibly with instructions, otherwise I'd get lost again in no time. :lolflag:

It's pretty inconvenient for us to be missing this now on my system, so any help would be very much appreciated.

---

### Post by Kivech on 2011-05-20
Ok, I just checked (by advice of the OpenERP forum) using:
> netstat -anp|grep ':8080'
And got as output
```
tcp6       0      0 :::8080                 :::*                    LISTEN      1772/java
```

Beats me what this means though, and if or how I can change that to free up the 8080 port for the OpenERP web module.
Common sense tells me that java is using this to listen, but I could be completely wrong. 

Big question remains how I can make everything work properly together.

I was also advised to set up virtual environments to seperate important environment. But if possible I would avoid that, because that sounds like redoing it all from scratch, and that would take too much time to be honest. If I have to I will, but I'd rather just fix this small problem than go for some rigorous approach.

---

### Post by Kivech on 2011-05-22
Ok, fixed it myself by changing the port setting in the configuration file of the OpenERP web module. Someone in their forums pointed me in the right direction, so now I know where to find it.

So the problem is solved.

---

