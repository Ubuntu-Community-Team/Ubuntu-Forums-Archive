---
title: "AWS S3 as storage server"
date: 2015-07-12
forum: Server Platforms
---

### Post by info31 on 2015-07-12
Hey guys,

currently i think about to setup an ubuntu server / cluster.

The web directory would be mounted to Amazon S3 as a web storage for all web files.
e.g .php,.html,.css etc.

Would this be a good choice to use S3 as a Storage Server?

In front of the Storage Server i would have two or three little webservers which are synced with GlusterFS and on top of that 
there would be an Amazon Loadbalancer.

So to the Server Pros here: Would this be a good Setup for a large web application?
Or should i better use a dedicated root / ec2 instance for the storage?

---

### Post by Habitual on 2015-07-13
copying large sets of data can be troublesome on S3.
See also [https://www.google.com/#q=serve+apache+from+s3&tbs=qdr:y](https://www.google.com/#q=serve+apache+from+s3&tbs=qdr:y)

---

### Post by lukeiamyourfather on 2015-07-13
This seems like an odd use case scenario but it's possible to do. What would make more sense in general is to store application files like PHP and CSS files on a local file system or network mounted file system where there's minimal latency (since they're used more frequently) and then store less latency sensitive content files like images on S3.

---

