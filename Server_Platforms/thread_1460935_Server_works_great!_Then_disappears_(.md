---
title: "Server works great! Then disappears :("
date: 2010-04-23
forum: Server Platforms
---

### Post by epheterson on 2010-04-23
I'm using Apache2 to host a site on an Ubuntu Virtual Machine. The site has worked fine forever, over years, and out of the blue it came across this problem.

What happens is when I turn the virtual box on, FTP and HTTP work fine as expected and the site is running dandy. This is the case for about 10 minutes.

Out of the blue, it just stops working. The only way to get it back is to restart the virtual box. I tried restarting just Apache with 
```
sudo /etc/init.d/apache2 reload
``` and
```
sudo apache2ctl restart
```
but this didn't work.

This is sort of a mission-critical situation, if there's any more information I can post, or any insight on what the problem could be, please let me know.

Thanks,
Eric

---

### Post by arrrghhh on 2010-04-23
Is apache running?  ```
ps -A |grep apache
```

---

### Post by epheterson on 2010-04-23
This is before, then after, it goes down:

[IMG]http://bayimg.com/image/bameoaacb.jpg[/IMG]

Oddly, it came back this time on it's own. I do have faith it'll go down again though...

---

### Post by tgalati4 on 2010-04-23
If ubuntu is running under a virtual machine, what is the native OS that is hosting the VM?

Check the log files of the host machine to find errors.

Sounds like a scheduling error or possibly a hard disk problem--causing delays in VM response.

---

### Post by epheterson on 2010-04-23
It's Windows Server 2003, but I have another virtual box running that's hosting its site just fine.

I want to think this type of error wouldn't spill into a VMWare log, no? I just looked through the logs and didn't see anything blatantly obvious, mostly running the box through boot-up.

The site is still up, this is actually a rather long uptime since the problem has started. Perhaps it's ironed the wrinkle out itself, I'll post back if it goes down again. 

If more information could be helpful in diagnosing what's wrong, or if you guys have more suggestions, let me know.

Thanks again,
Eric

P.S. I copied the same command twice in the first post, it's corrected now.

---

### Post by tgalati4 on 2010-04-23
If you don't find any errors in /var/log of the Ubuntu Virtual Machine, then one must look at the host machine.  

Since you stated that the server and the VM had been up for a long period of time, and with no recent updates, I would start to question the hardware, or a problem with vmware interfacing with Windows 2003.

What logging does vmware provide under Windows 2003 server?

---

### Post by arrrghhh on 2010-04-23
Apache is not the issue then... Does the server ever become inaccessible in any other ways other than HTTP?

---

### Post by tgalati4 on 2010-04-23
The only thing I can think of that will ball up an apache server is not being able to write to log files (i.e. the system disk is full) or if the network is down (and that could be a VM interface issue).

It could be a RAM issue.  Run memtest overnight to make sure the RAM is OK.  RAM can fail on 24/7 servers.

---

### Post by epheterson on 2010-04-24
> **arrrghhh said:**
> Apache is not the issue then... Does the server ever become inaccessible in any other ways other than HTTP?

Yes, FTP also goes down. 

The funny thing is that the VMWare box is still connected to the internet, as I can run sudo apt-get update and so on. 

I'm not well versed in Linux command line, perhaps you could walk me through how to export a log and I can share it with you all? The logs I checked were the VMWare logs, not the Ubuntu logs.

Oh, and it did go down again. It just had a decent up-time considering the situation.

Also, I'm running MemTest at the moment and so far 0 errors after 1 pass. I don't suspect this is the problem since, as I mentioned, there is another virtual box running without errors.

---

### Post by tgalati4 on 2010-04-24
How do you check the integrity of a VM image?  If you have a borked VM image and you boot it, would it not behave in a similar fashion?

I would just cut and paste some portions of the log files that contain errors:

For the linux side:

dmesg | grep error

and 

dmesg | grep fail

grep error /var/log/messages

grep fail /var/log/messages

(Do the same for apache log files)

You are on your own for Windows.  I don't use it.

I hope you are not running memtest in the Virtual Machine.  You need to shut down the server, load an Ubuntu Live CD, boot from it and run memtest overnight.  30 complete pass cycles will give you a large population.  This improves statistical confidence to over 95%.

If you have never validated your memory in this server, how do you know it is still fully functional?

If your server uses ECC memory, you will have to go into the configure menu and set ECC for testing.

---

### Post by epheterson on 2010-04-26
So I haven't gotten the logs yet, but I'm not entirely sure if it's necessary -- stay tuned, I suppose. 

In an effort to make navigating the filesystem and managing the server easier, I plopped a GUI atop my Ubuntu Server installation via [this]("http://www.ubuntugeek.com/3171.html") tutorial, even though I'm running 8.1. I believe since then, the site hasn't gone down. I may have shaken up enough under the hood to scare away the gremlin hiding in there. 

I still don't believe it was RAM and I may still post log bits to get a deeper insight of what happened. 

If it goes down again, I'll be back sooner than later. Again, thank you all for your help, you make this free operating system well worth using.

-Eric

---

### Post by epheterson on 2010-04-30
Definitely went down again, I've found the Apache logs, should I be posting in the Django forums instead?

Decryption please?

```
[Sun Apr 25 07:35:35 2010] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sun Apr 25 07:35:35 2010] [notice] mod_python: using mutex_directory /tmp 
[Sun Apr 25 07:35:35 2010] [notice] Apache/2.2.8 (Ubuntu) mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch configured -- resuming normal operations

...

[Mon Apr 26 07:50:58 2010] [error] [client 208.109.236.119] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)

...

[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] mod_python (pid=14188, interpreter='ubuntu.localdomain', phase='PythonHandler', handler='django.core.handlers.modpython'): Application error
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] ServerName: 'ubuntu.localdomain'
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] DocumentRoot: '/var/www/base_html'
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] URI: '/site/profile/iepngfix.htc'
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] Location: '/site/'
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] Directory: None
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] Filename: '/var/www/base_html/site'
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] PathInfo: '/profile/iepngfix.htc'
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] Traceback (most recent call last):
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58]   File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1537, in HandlerDispatch\n    default=default_handler, arg=req, silent=hlist.silent)
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58]   File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1229, in _process_target\n    result = _execute_target(config, req, object, arg)
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58]   File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1128, in _execute_target\n    result = object(arg)
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58]   File "/usr/lib/python2.5/site-packages/django/core/handlers/modpython.py", line 222, in handler\n    return ModPythonHandler()(req)
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58]   File "/usr/lib/python2.5/site-packages/django/core/handlers/modpython.py", line 214, in __call__\n    req.write(chunk)
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] IOError: Write failed, client closed connection.
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1931, in ReportError
    req.write(text)
IOError: Write failed, client closed connection.
[Tue Apr 27 12:48:18 2010] [error] [client 128.59.150.58] python_handler: Dispatch() returned non-integer.
```

---

