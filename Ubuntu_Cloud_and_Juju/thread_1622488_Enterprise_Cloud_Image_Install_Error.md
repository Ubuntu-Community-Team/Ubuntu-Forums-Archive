---
title: "Enterprise Cloud Image Install Error"
date: 2010-11-15
forum: Ubuntu Cloud and Juju
---

### Post by jugola on 2010-11-15
Hello
I trying to install Ubuntu 10.04 LTS - Lucid Lynx (amd64) image on my cloud but when the download finished this error appear and the image didn't install:

[PHP]Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1289852649
Traceback (most recent call last):
  File "/usr/bin/euca-upload-bundle", line 231, in <module>
    main()
  File "/usr/bin/euca-upload-bundle", line 214, in main
    bucket_instance = ensure_bucket(conn, bucket, canned_acl)
  File "/usr/bin/euca-upload-bundle", line 87, in ensure_bucket
    bucket_instance = connection.get_bucket(bucket)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 275, in get_bucket
    rs = bucket.get_all_keys(headers, maxkeys=0)
  File "/usr/lib/pymodules/python2.6/boto/s3/bucket.py", line 204, in get_all_keys
    headers=headers, query_args=s)
  File "/usr/lib/pymodules/python2.6/boto/s3/connection.py", line 342, in make_request
    data, host, auth_path, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 459, in make_request
    return self._mexe(method, path, data, headers, host, sender)
  File "/usr/lib/pymodules/python2.6/boto/connection.py", line 437, in _mexe
    raise e
socket.error: [Errno 110] Connection timed out[/PHP]

Thanks for your help.

---

### Post by kim0 on 2010-11-16
Hey there jugola,

open the file eucarc that was in the credentials .. there should be a line like

export EC2_URL=http://10.55.56.10:8773/services/Eucalyptus

can you reach that IP address, can you ping it ? can you connect(telnet) to that port 8773 ? If not, the computer you're testing from might be connected to a wrong network segment. Or the installation might just have been incorrect. Let me know what you find

---

