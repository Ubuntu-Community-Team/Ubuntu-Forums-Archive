---
title: "Error Downloading Image"
date: 2010-05-21
forum: Server Platforms
---

### Post by sunder.srv on 2010-05-21
Hi all, 
          We are now ready with the cloud setup. When we started downloading one of the UEC's default image,

We ended up with the error,

"Command 'euca-upload-bundle' returned status code 1:
Checking bucket: image-store-1274250068
Traceback (most recent call last):
File "/usr/bin/euca-upload-bundle", line 231, in
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
socket.error: [Errno 113] No route to host
"

Please help us,

---

### Post by cariboo on 2010-05-21
A bump for the move.

---

### Post by sunder.srv on 2010-05-25
U mean ?

---

