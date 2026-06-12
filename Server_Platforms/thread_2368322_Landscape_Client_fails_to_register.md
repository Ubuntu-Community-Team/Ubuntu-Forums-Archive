---
title: "Landscape Client fails to register"
date: 2017-08-09
forum: Server Platforms
---

### Post by Zack McCool on 2017-08-09
I have a small network with a collection of Ubuntu machines performing various tasks. I have built a landscape server to manage the others, but I am having a problem registering some of the clients.

3 of the servers are virtual (VBOX), running Ubuntu Server 16.04.3. They all installed and registered fine.

Then, I have 2 physical boxes, neither of which will work. Same process followed for all 5.

Server 1: A DELL desktop (SFF) running Ubuntu Desktop 16.04.3 (server could not install due to nic compatibility, desktop installed fine, and is running in console mode)
Server 2: An Intel NUC running Ubuntu Server 16.04.3

Here is the command line for registering (which worked well for the 3 VMs):
```
sudo landscape-config --computer-title "ServerName" --account-name standalone --url https://192.168.0.32/message-system --ping-url http://192.168.0.32/ping --ssl-public-key /etc/ssl/certs/landscape_server_ca.crt 
```

Here is the result when I attempt to register the client:
```
Request a new registration for this computer now? [Y/n]: 
Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/twisted/python/log.py", line 101, in callWithLogger
    return callWithContext({"system": lp}, func, *args, **kw)
  File "/usr/lib/python2.7/dist-packages/twisted/python/log.py", line 84, in callWithContext
    return context.call({ILogContext: newCtx}, func, *args, **kw)
  File "/usr/lib/python2.7/dist-packages/twisted/python/context.py", line 118, in callWithContext
    return self.currentContext().callWithContext(ctx, func, *args, **kw)
  File "/usr/lib/python2.7/dist-packages/twisted/python/context.py", line 81, in callWithContext
    return func(*args,**kw)
--- <exception caught here> ---
  File "/usr/lib/python2.7/dist-packages/twisted/internet/posixbase.py", line 597, in _doReadOrWrite
    why = selectable.doRead()
  File "/usr/lib/python2.7/dist-packages/twisted/internet/unix.py", line 167, in doRead
    sendmsg.recvmsg, self.socket, self.bufferSize)
exceptions.AttributeError: 'module' object has no attribute 'recvmsg'

Traceback (most recent call last):
Failure: exceptions.AttributeError: 'module' object has no attribute 'recvmsg'

Unhandled error in Deferred:


Traceback (most recent call last):
Failure: exceptions.AttributeError: 'module' object has no attribute 'recvmsg'
Unhandled error in Deferred:


Traceback (most recent call last):
Failure: exceptions.AttributeError: 'module' object has no attribute 'recvmsg'
^CTraceback (most recent call last):
  File "/usr/bin/landscape-config", line 13, in <module>
    main(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/landscape/configuration.py", line 796, in main
    result = register(config, reactor)
  File "/usr/lib/python2.7/dist-packages/landscape/configuration.py", line 694, in register
    assert len(results) == 1, "We expect exactly one result."
AssertionError: We expect exactly one result.
```

Any help would be greatly appreciated. Centralized monitoring and management would be nice...

---

### Post by Zack McCool on 2017-09-18
Bump

Nobody using this outside of the corporate clients?

---

### Post by wildmanne39 on 2017-09-18
*Thread moved to **Server Platforms for a better fit**.*

---

