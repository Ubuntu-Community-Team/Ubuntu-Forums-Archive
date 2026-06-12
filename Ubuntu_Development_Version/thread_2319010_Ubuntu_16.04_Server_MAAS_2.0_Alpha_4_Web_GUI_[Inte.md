---
title: "Ubuntu 16.04 Server MAAS 2.0 Alpha 4 Web GUI [Internal Server Error]"
date: 2016-03-31
forum: Ubuntu Development Version
---

### Post by hlini-h on 2016-03-31
Hi there,

I am having issues with a fresh install of 16.04 MAAS server. The Webgui is failing with an internal server error regiond.log has the following error when I try to reach the web gui. This was working fine in Alpha 3 and I cannot find anything in the launchpad bug tracker on this issue. I used the MAAS option to install through the server iso to set this up. 

Anyone here have any insight into this issue?

```
2016-03-31 11:08:50 [-] /usr/lib/python3/dist-packages/django/templatetags/future.py:25: django.utils.deprecation.RemovedInDjango19Warning: Loading the `url` tag from the `future` library is deprecated and will be removed in Django 1.9. Use the default `url` tag instead.2016-03-31 11:08:50 [HTTPChannel,2,127.0.0.1] 500 Error - /MAAS/accounts/login/
    Traceback (most recent call last):
      File "/usr/lib/python3/dist-packages/django/core/handlers/wsgi.py", line 189, in __call__
        response = self.get_response(request)
      File "/usr/lib/python3/dist-packages/maasserver/utils/views.py", line 227, in get_response
        response = get_response(request)
      File "/usr/lib/python3/dist-packages/maasserver/utils/views.py", line 201, in get_response
        return django_get_response(request)
      File "/usr/lib/python3/dist-packages/django/core/handlers/base.py", line 218, in get_response
        response = self.handle_uncaught_exception(request, resolver, sys.exc_info())
    --- <exception caught here> ---
      File "/usr/lib/python3/dist-packages/django/core/handlers/base.py", line 164, in get_response
        response = response.render()
      File "/usr/lib/python3/dist-packages/django/template/response.py", line 158, in render
        self.content = self.rendered_content
      File "/usr/lib/python3/dist-packages/django/template/response.py", line 135, in rendered_content
        content = template.render(context, self._request)
      File "/usr/lib/python3/dist-packages/django/template/backends/django.py", line 74, in render
        return self.template.render(context)
      File "/usr/lib/python3/dist-packages/django/template/base.py", line 209, in render
        with context.bind_template(self):
      File "/usr/lib/python3.5/contextlib.py", line 59, in __enter__
        return next(self.gen)
      File "/usr/lib/python3/dist-packages/django/template/context.py", line 241, in bind_template
        updates.update(processor(self.request))
      File "/usr/lib/python3/dist-packages/maasserver/context_processors.py", line 27, in global_options
        version = get_maas_version_ui()
      File "/usr/lib/python3/dist-packages/maasserver/utils/version.py", line 87, in wrapped
        _cache[key] = fun(*args, **kwargs)
      File "/usr/lib/python3/dist-packages/maasserver/utils/version.py", line 123, in get_maas_version_ui
        version, subversion = get_maas_version_subversion()
      File "/usr/lib/python3/dist-packages/maasserver/utils/version.py", line 87, in wrapped
        _cache[key] = fun(*args, **kwargs)
      File "/usr/lib/python3/dist-packages/maasserver/utils/version.py", line 108, in get_maas_version_subversion
        branch_version = get_maas_branch_version()
      File "/usr/lib/python3/dist-packages/maasserver/utils/version.py", line 62, in get_maas_branch_version
        revno = shell.call_and_check(("bzr", "revno", __file__))
      File "/usr/lib/python3/dist-packages/provisioningserver/utils/shell.py", line 125, in call_and_check
        process = Popen(command, *args, stdout=PIPE, stderr=PIPE, **kwargs)
      File "/usr/lib/python3.5/subprocess.py", line 947, in __init__
        restore_signals, start_new_session)
      File "/usr/lib/python3.5/subprocess.py", line 1541, in _execute_child
        raise child_exception_type(errno_num, err_msg)
    builtins.FileNotFoundError: [Errno 2] No such file or directory: 'bzr'


2016-03-31 11:08:50 [-] 127.0.0.1 - - [31/Mar/2016:11:08:49 +0000] "GET /MAAS/accounts/login/?next=%2FMAAS%2F HTTP/1.1" 500 223 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.110 Safari/537.36"




```

---

### Post by hlini-h on 2016-03-31
Well that was horribly simple to fix. 


```
apt install bzr
```

---

