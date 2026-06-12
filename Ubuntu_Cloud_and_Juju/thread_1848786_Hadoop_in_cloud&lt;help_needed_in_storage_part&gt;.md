---
title: "Hadoop in cloud&lt;help needed in storage part&gt;"
date: 2011-09-23
forum: Ubuntu Cloud and Juju
---

### Post by rohitkondekar on 2011-09-23
Hello,

I have got a small problem in understanding here, I have setup a small UEC cluster, and i am able to instantiate images. Basically, what i want is to run Hadoop in this cloud. I would first make .img of the os with hadoop installed and the instantiate it. Ok i got this much.

But then if i run some map-reduce task on the vm's instatiated, and later i have to close down the cluster so how to store this data which is generated after map reduce to later use it, for searching content in this data like by using lucene or something.

Because once i close down the vm's all the data would be lost. rite? How to restore the states(i mean in terms of data in hdfs) of the vm's.

Plz, help desperately needed :(

Thanks a lot...

---

### Post by kim0 on 2011-09-23
Just like you'd do it on ec2, you attach an ebs volume, save your data on it before terminating the machines

---

### Post by j13scott on 2011-09-24
thanks for the information...

[electrical power distribution](http://www.aten-usa.com)

---

