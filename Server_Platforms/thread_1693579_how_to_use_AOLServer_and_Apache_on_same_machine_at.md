---
title: "how to use AOLServer and Apache on same machine at different ports"
date: 2011-02-23
forum: Server Platforms
---

### Post by tapas_mishra on 2011-02-23
I am using a Ubuntu virtual machine.Where I installed OpenACS which depends upon AOLServer.To do so I had first shutdown Apache on this machine and then as per instructions given here

[http://openacs.org/xowiki/ubuntu](http://openacs.org/xowiki/ubuntu)

Step 1) 
> aptitude install postgresqlStep 2) 
> aptitude install openacsI had to shutdown Apache to do above installation.
Now the installation finishes.So I can access [http://localhost:8000](http://localhost:8000)

but when ever I try to start Apache on this machine which was shutdown during installation I see the error 
 service apache2 start
>  * Starting web server apache2                                                                                                                                         (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
So I thought may be OpenACS installs AOLServer so Aolserver might be listening on port 80 I check 
> /etc/aolserver4/conf.d/openacs.shand here

> AOL_USER=www-data
AOL_GROUP=www-data
AOL_ADDRESS=192.168.1.15
AOL_PORT=8000
RUN_DAEMON=yes
So AOLServer is not listening on port 80 upto here it is confirmed.

```
 netstat -tualp  | grep 80
tcp  0      0 somemachine.somedimain.:8000 *:*   LISTEN   21321/aolserver4-ns

```so netstat shows only 8000 in  use.
Then why am I unable to start Apache in this case?

---

