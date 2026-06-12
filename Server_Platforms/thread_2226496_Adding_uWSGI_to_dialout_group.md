---
title: "Adding uWSGI to dialout group"
date: 2014-05-27
forum: Server Platforms
---

### Post by vandorjw on 2014-05-27
Hello Everyone,

I have a django application which connects to several serial devices on the server.
The webserver is nginx, with uwsgi. uWSGI handles all the python processes and runs as the underprivileged user 'uwsgi'
Everything works as expected using the development server, or a python shell. 

When uWSGI tries to connect to the serial devices, it doesn't have permission to do so, even when I made it part of the dialout group.

My problem is identical to this, but there is no answer, or explaination.

[http://stackoverflow.com/questions/9862137/pyserial-permission-denied-when-invoked-by-webserver](http://stackoverflow.com/questions/9862137/pyserial-permission-denied-when-invoked-by-webserver)

If anyone can explain, the difference between a daemon, and regular user.

This is the error I have using a regular user: (development server, running as 'vandorjw')
> 
<class 'serial.serialutil.SerialException'>
Could not configure port: (5, 'Input/output error')
<traceback object at 0x7f24f45caea8>


(This is normal, since the device doesn't exist on my development machine)

This is the error I have using uWSGI Production Server: (running as 'uwsgi')
> 
<class 'serial.serialutil.SerialException'>
[Errno 13] could not open port /dev/ttyS0:
 [Errno 13] Permission denied: '/dev/ttyS0'
<traceback object at 0x7f480f5793f8>


both vandorjw and uwsgi are part of the dialout group.

I don't understand why a regular user has permission, but a user which has /sbin/nologin for a shell, does not.

---

