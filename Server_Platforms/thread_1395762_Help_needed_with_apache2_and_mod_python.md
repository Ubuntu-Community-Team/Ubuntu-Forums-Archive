---
title: "Help needed with apache2 and mod_python"
date: 2010-02-01
forum: Server Platforms
---

### Post by eggnogg on 2010-02-01
Hello,

after removing nginx and doing the following:

sudo apache2 -k start

i get: 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Feb 01 15:46:07 2010] [warn] NameVirtualHost *:80 has no VirtualHosts


and upon going to localhost i get:

MOD_PYTHON ERROR

ProcessId:      30714
Interpreter:    '127.0.1.1'

ServerName:     '127.0.1.1'
DocumentRoot:   '/htdocs'

URI:            '/'
Location:       '/'
Directory:      None
Filename:       '/htdocs'
PathInfo:       '/'

Phase:          'PythonHandler'
Handler:        'django.core.handlers.modpython'

Traceback (most recent call last):

  File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/usr/lib/pymodules/python2.6/django/core/handlers/modpython.py", line 228, in handler
    return ModPythonHandler()(req)

  File "/usr/lib/pymodules/python2.6/django/core/handlers/modpython.py", line 191, in __call__
    self.load_middleware()

  File "/usr/lib/pymodules/python2.6/django/core/handlers/base.py", line 33, in load_middleware
    for middleware_path in settings.MIDDLEWARE_CLASSES:

  File "/usr/lib/pymodules/python2.6/django/utils/functional.py", line 269, in __getattr__
    self._setup()

  File "/usr/lib/pymodules/python2.6/django/conf/__init__.py", line 40, in _setup
    self._wrapped = Settings(settings_module)

  File "/usr/lib/pymodules/python2.6/django/conf/__init__.py", line 75, in __init__
    raise ImportError, "Could not import settings '%s' (Is it on sys.path? Does it have syntax errors?): %s" % (self.SETTINGS_MODULE, e)

ImportError: Could not import settings 'examples.settings' (Is it on sys.path? Does it have syntax errors?): No module named examples.settings

what should i do?

---

