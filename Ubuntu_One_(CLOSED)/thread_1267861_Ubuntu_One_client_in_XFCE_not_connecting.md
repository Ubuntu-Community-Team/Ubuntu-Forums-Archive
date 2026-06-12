---
title: "Ubuntu One client in XFCE not connecting"
date: 2009-09-16
forum: Ubuntu One (CLOSED)
---

### Post by RavanH on 2009-09-16
Hi,

I posted this question on [https://answers.edge.launchpad.net/ubuntuone-client/+question/82954](https://answers.edge.launchpad.net/ubuntuone-client/+question/82954) before I found out there is a whole section for Ubuntu One on ubuntuforums but maybe someone here can shed some light on this for me... 

> Although I read that Ubuntu One should work on XFCE, I cannot get the client does to connect at all. I start Ubuntu One from the Applications menu then click the tray icon and select Connect... Nothing happens.

Am I doing something wrong?

If I right-click the tray icon and select Go to Web my default browser (Opera) opens my one.ubuntu.com file sharing page. And if I choose Open Folder, thunar opens up like it should...

Side issue: Ubuntu One does not autostart upon login. I suppose I will have to add it manually to the Autostart App list?


Thanks for helping me out! :)

EDIT: **Additional info**
After starting the ubuntuone-client-applet from terminal and clicking Connect, I get this output:
```
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 497, in __bootstrap
    self.__bootstrap_inner()
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 477, in run
    self.__target(*self.__args, **self.__kwargs)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/python/threadpool.py", line 210, in _worker
    result = context.call(ctx, function, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/twisted/python/context.py", line 59, in callWithContext
    return self.currentContext().callWithContext(ctx, func, *args, **kw)
  File "/usr/lib/python2.6/dist-packages/twisted/python/context.py", line 37, in callWithContext
    return func(*args,**kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 372, in ensure_access_token
    store=True)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 243, in acquire_access_token_if_online
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 317, in acquire_access_token
    callback=callback_url)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/oauth.py", line 286, in from_token_and_callback
    parameters['oauth_token'] = token.key
exceptions.AttributeError: 'NoneType' object has no attribute 'key'

```

---

### Post by andrea000 on 2009-09-17
Do you have the apport crash report?

---

### Post by joshuahoover on 2009-09-18
> **RavanH said:**
> Hi,

I posted this question on [https://answers.edge.launchpad.net/ubuntuone-client/+question/82954](https://answers.edge.launchpad.net/ubuntuone-client/+question/82954) before I found out there is a whole section for Ubuntu One on ubuntuforums but maybe someone here can shed some light on this for me... 

Thanks for helping me out! :)

EDIT: **Additional info**
After starting the ubuntuone-client-applet from terminal and clicking Connect, I get this output:
```
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 497, in __bootstrap
    self.__bootstrap_inner()
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 477, in run
    self.__target(*self.__args, **self.__kwargs)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/python/threadpool.py", line 210, in _worker
    result = context.call(ctx, function, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/twisted/python/context.py", line 59, in callWithContext
    return self.currentContext().callWithContext(ctx, func, *args, **kw)
  File "/usr/lib/python2.6/dist-packages/twisted/python/context.py", line 37, in callWithContext
    return func(*args,**kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 372, in ensure_access_token
    store=True)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 243, in acquire_access_token_if_online
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 317, in acquire_access_token
    callback=callback_url)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/oauth.py", line 286, in from_token_and_callback
    parameters['oauth_token'] = token.key
exceptions.AttributeError: 'NoneType' object has no attribute 'key'

```

The good news is that you should get past this error if you update to the latest version of the client. Please try that and if you're still having problems, please report a bug by right-clicking on the Ubuntu One icon and selecting "Report a Problem".

Thanks!

Joshua

---

### Post by RavanH on 2009-09-22
thanks andrea and joshua, for replying.

the latest update did indeed change it all. it works just fine now (coming up with a 'which browser do you prefer' dialog and proceeding to the 'add computer' page) so i am happy :)

---

### Post by joshuahoover on 2009-09-25
> **RavanH said:**
> thanks andrea and joshua, for replying.

the latest update did indeed change it all. it works just fine now (coming up with a 'which browser do you prefer' dialog and proceeding to the 'add computer' page) so i am happy :)

Great news! And thank you for letting us know this fixed the problem for you. :)

---

