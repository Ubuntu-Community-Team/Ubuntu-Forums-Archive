---
title: "socket server program in Amazon S3"
date: 2013-12-10
forum: Server Platforms
---

### Post by chuchi on 2013-12-10
Hi everyone!

I am planning to upload my website to Amazon S3

Do you know if Amazon S3 allows to execute external scripts on the server? 

I have a socket server program listening for incoming connections for websockets. It is written in PHP, but if Amazon S3 does not allow PHP, I do not care to write it again in JAVA or any other language.

Thank you very much!

---

### Post by Habitual on 2013-12-10
S3 is storage, not an instance.
I believe you can run php files from an S3 bucket.

See [http://docs.aws.amazon.com/AmazonS3/latest/dev/VirtualHosting.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/VirtualHosting.html)

---

### Post by sandyd on 2013-12-11
> **chuchi said:**
> Hi everyone!

I am planning to upload my website to Amazon S3

Do you know if Amazon S3 allows to execute external scripts on the server? 

I have a socket server program listening for incoming connections for websockets. It is written in PHP, but if Amazon S3 does not allow PHP, I do not care to write it again in JAVA or any other language.

Thank you very much!

No - amazon S3 does not allow PHP - it only serves static files.
You will want something like Amazon EC2/webhosting/vps/server for this

---

