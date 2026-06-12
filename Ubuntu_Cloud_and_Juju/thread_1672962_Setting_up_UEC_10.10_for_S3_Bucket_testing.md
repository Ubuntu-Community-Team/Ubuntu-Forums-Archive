---
title: "Setting up UEC 10.10 for S3 Bucket testing"
date: 2011-01-21
forum: Ubuntu Cloud and Juju
---

### Post by flabr03 on 2011-01-21
I am trying to get a UEC 10.10 environment setup in a test lab to test basic S3 compatability. I know that for the nodes you need a VT enabled system, but reading thru the docs and installing UEC, it looks like walrus is what creates the buckets. Is it possible to install all of the other roles on one beefy node with adaquate disk space and use that to create the buckets, or do I need the NC to create a image that the buckets get associated to?
 
I have no need for EC2 support at this time so I was hoping to get away with a single instance/server configration.
 
Can someone tell me if this is possible?

---

### Post by kim0 on 2011-01-22
Hi!

A standard and supported setup is to install 2 machines like so

- Machine1: CLC + CC + SC + WALRUS
- Machine2: NC

In your case, I suppose you want to install machine1 only, and stop there, and start using it as a S3 server. I haven't tested that, but it looks doable. So perhaps give it a shot and try it

---

