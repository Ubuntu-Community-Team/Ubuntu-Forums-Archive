---
title: "Cloud images have mis-matched sha256sums - Tampered with?"
date: 2017-06-21
forum: Ubuntu Cloud and Juju
---

### Post by johnsom on 2017-06-21
I am seeing (as well as others) that the current cloud image sha256sums don't match those in the SHA256SUMS file.  Have they been tampered with?

michjohn@devstackpy27:~$ wget [http://cloud-images.ubuntu.com/xenial/current/SHA256SUMS](http://cloud-images.ubuntu.com/xenial/current/SHA256SUMS)
--2017-06-21 07:40:41--  [http://cloud-images.ubuntu.com/xenial/current/SHA256SUMS](http://cloud-images.ubuntu.com/xenial/current/SHA256SUMS)
Resolving cloud-images.ubuntu.com (cloud-images.ubuntu.com)... 2001:67c:1360:8c01::8001, 91.189.92.141
Connecting to cloud-images.ubuntu.com (cloud-images.ubuntu.com)|2001:67c:1360:8c01::8001|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5266 (5.1K)
Saving to: ‘SHA256SUMS’


SHA256SUMS          100%[===================>]   5.14K  --.-KB/s    in 0s


2017-06-21 07:40:42 (748 MB/s) - ‘SHA256SUMS’ saved [5266/5266]


michjohn@devstackpy27:~$ wget [http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-root.tar.gz](http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-root.tar.gz)
--2017-06-21 07:40:53--  [http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-root.tar.gz](http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-root.tar.gz)
Resolving cloud-images.ubuntu.com (cloud-images.ubuntu.com)... 2001:67c:1360:8c01::8001, 91.189.92.141
Connecting to cloud-images.ubuntu.com (cloud-images.ubuntu.com)|2001:67c:1360:8c01::8001|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 201137066 (192M) [application/x-gzip]
Saving to: ‘xenial-server-cloudimg-amd64-root.tar.gz’


xenial-server-cloud 100%[===================>] 191.82M  8.49MB/s    in 26s


2017-06-21 07:41:20 (7.25 MB/s) - ‘xenial-server-cloudimg-amd64-root.tar.gz’ saved [201137066/201137066]


michjohn@devstackpy27:~$ sha256sum xenial-server-cloudimg-amd64-root.tar.gz
04f9bd06a12636ac1e747856de2797a8a17c8ebcfca4714c080912bff90eeca1  xenial-server-cloudimg-amd64-root.tar.gz
michjohn@devstackpy27:~$ grep xenial-server-cloudimg-amd64-root.tar.gz SHA256SUMS
7584d5214285c249a9ae80f98b71d7cc216fd915be2ca40d82a1e4603b7ae257 *xenial-server-cloudimg-amd64-root.tar.gz

---

### Post by #&amp;thj^% on 2017-06-21
Bug filed here: [https://bugs.launchpad.net/cloud-images/+bug/1699396](https://bugs.launchpad.net/cloud-images/+bug/1699396)

---

