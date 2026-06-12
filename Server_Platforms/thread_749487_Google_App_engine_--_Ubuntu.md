---
title: "Google App engine -- Ubuntu"
date: 2008-04-08
forum: Server Platforms
---

### Post by mohnkern on 2008-04-08
Has anyone installed the Google app engine ([http://code.google.com/appengine/](http://code.google.com/appengine/)) on Ubuntu Gutsy?

I downloaded it, and got it to start up, but the server is generating errors.

It would be great to see a how to on this, maybe if I can get it working.....

---

### Post by ipburbank on 2008-07-20
> **mohnkern said:**
> Has anyone installed the Google app engine ([http://code.google.com/appengine/](http://code.google.com/appengine/)) on Ubuntu Gutsy?

I downloaded it, and got it to start up, but the server is generating errors.

It would be great to see a how to on this, maybe if I can get it working.....

I am having the same problem...

Here is my the result when I type the code:

Traceback (most recent call last):
  File "google_appengine/dev_appserver.py", line 50, in <module>
    execfile(script_path, globals())
  File "/home/istvan/Applications/google_appengine/google/appengine/tools/dev_appserver_main.py", line 351, in <module>
    sys.exit(main(sys.argv))
  File "/home/istvan/Applications/google_appengine/google/appengine/tools/dev_appserver_main.py", line 300, in main
    config, matcher = dev_appserver.LoadAppConfig(root_path, {})
  File "/home/istvan/Applications/google_appengine/google/appengine/tools/dev_appserver.py", line 2450, in LoadAppConfig
    raise AppConfigNotFoundError
google.appengine.tools.dev_appserver.AppConfigNotFoundErro

---

### Post by mohnkern on 2008-07-20
I pretty much ended up abandoning work on this as it was more for purposes of experimentation, rather than utility.

---

### Post by ipburbank on 2008-07-22
I would like to use it seriously, but I can't see to. Can anybody tell me if there is a way of making it work?

---

### Post by loell on 2008-07-22
in hardy it works just fine.

---

### Post by drummingpariah on 2008-07-23
> **loell said:**
> in hardy it works just fine.

I'm in Hardy as well, but am getting the following:

> ./dev_appserver.py helloworld
Traceback (most recent call last):
  File "./dev_appserver.py", line 50, in <module>
    execfile(script_path, globals())
  File "/home/irish/.bin/google_appengine/google/appengine/tools/dev_appserver_main.py", line 351, in <module>
    sys.exit(main(sys.argv))
  File "/home/irish/.bin/google_appengine/google/appengine/tools/dev_appserver_main.py", line 300, in main
    config, matcher = dev_appserver.LoadAppConfig(root_path, {})
  File "/home/irish/.bin/google_appengine/google/appengine/tools/dev_appserver.py", line 2450, in LoadAppConfig
    raise AppConfigNotFoundError
google.appengine.tools.dev_appserver.AppConfigNotFoundError


Did you extract the .zip somewhere special, or just to a generic folder in your ~/ dir?

---

### Post by loell on 2008-07-23
**google.appengine.tools.dev_appserver.AppConfigNotF oundError **

could this be just a config file error?

can you post your app.yml?

---

### Post by ipburbank on 2008-07-23
Here is my app.yaml:

application: helloworld
version: 1
runtime: python
api_version: 1

handlers:
- url: /.*
  script: helloworld.py

I was just doing the helloworld tutorial to figure out the app.yaml, so i copied and pasted from the tutorial.

---

### Post by ipburbank on 2008-07-23
I think I have it!! run the config file, then in the google_appengine directory type:


```
python dev_appserver.py helloworld/
```


this isn't what the tutorial says, but it works for me!

---

