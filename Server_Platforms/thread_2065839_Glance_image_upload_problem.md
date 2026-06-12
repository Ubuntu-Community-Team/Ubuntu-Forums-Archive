---
title: "Glance image upload problem"
date: 2012-10-03
forum: Server Platforms
---

### Post by ankitjayswal on 2012-10-03
Hello guys,
I am working on Openstack cloud infrastructure.
I am getting below error while uploading disk image or iso image to glance server.

root@ankit:/home/localadmin/Downloads# glance add name="My Image" is_public=true < ubuntu-12.04-cloud-live-amd64.iso
Uploading image 'My Image'
=========================================================================================================================================[ 99%]  40.1M/s, ETA  0h  0m  0sFailed to add image. Got error:
The request returned 500 Internal Server Error

The response body:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/eventlet/wsgi.py", line 336, in handle_one_response
    result = self.application(self.environ, start_response)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 147, in __call__
    resp = self.call_func(req, *args, **self.kwargs)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 210, in call_func
    return self.func(req, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/glance/common/wsgi.py", line 284, in __call__
    response = req.get_response(self.application)
  File "/usr/lib/python2.7/dist-packages/webob/request.py", line 1086, in get_response
    application, catch_exc_info=False)
  File "/usr/lib/python2.7/dist-packages/webob/request.py", line 1055, in call_application
    app_iter = application(self.environ, start_response)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 147, in __call__
    resp = self.call_func(req, *args, **self.kwargs)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 210, in call_func
    return self.func(req, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/glance/common/wsgi.py", line 284, in __call__
    response = req.get_response(self.application)
  File "/usr/lib/python2.7/dist-packages/webob/request.py", line 1086, in get_response
    application, catch_exc_info=False)
  File "/usr/lib/python2.7/dist-packages/webob/request.py", line 1055, in call_application
    app_iter = application(self.environ, start_response)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 159, in __call__
    return resp(environ, start_response)
  File "/usr/lib/python2.7/dist-packages/routes/middleware.py", line 131, in __call__
    response = self.app(environ, start_response)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 159, in __call__
    return resp(environ, start_response)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 147, in __call__
    resp = self.call_func(req, *args, **self.kwargs)
  File "/usr/lib/python2.7/dist-packages/webob/dec.py", line 210, in call_func
    return self.func(req, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/glance/common/wsgi.py", line 482, in __call__
    request, **action_args)
  File "/usr/lib/python2.7/dist-packages/glance/common/wsgi.py", line 499, in dispatch
    return method(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/glance/api/v1/images.py", line 610, in create
    image_meta = self._reserve(req, image_meta)
  File "/usr/lib/python2.7/dist-packages/glance/api/v1/images.py", line 320, in _reserve
    image_meta = registry.add_image_metadata(req.context, image_meta)
  File "/usr/lib/python2.7/dist-packages/glance/registry/__init__.py", line 145, in add_image_metadata
    return c.add_image(image_meta)
  File "/usr/lib/python2.7/dist-packages/glance/registry/client.py", line 121, in add_image
    res = self.do_request("POST", "/images", body, headers=headers)
  File "/usr/lib/python2.7/dist-packages/glance/common/client.py", line 58, in wrapped
    return func(self, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/glance/common/client.py", line 420, in do_request
    headers=headers)
  File "/usr/lib/python2.7/dist-packages/glance/common/client.py", line 75, in wrapped
    return func(self, method, url, body, headers)
  File "/usr/lib/python2.7/dist-packages/glance/common/client.py", line 562, in _do_request
    raise exception.ClientConnectionError(e)
ClientConnectionError: There was an error connecting to a server
Details: [Errno 111] Connection refused

Note: Your image metadata may still be in the registry, but the image's status will likely be 'killed'.
==========================================================================================================================================[100%] 39.6M/s, ETA  0h  0m 



Please help me... guys... waiting....  :)

---

