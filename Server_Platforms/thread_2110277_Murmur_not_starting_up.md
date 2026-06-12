---
title: "Murmur not starting up"
date: 2013-01-29
forum: Server Platforms
---

### Post by Code9 on 2013-01-29
Hello, I seem to be having a little bit of trouble with Murmur. I am running an Ubuntu Server. 

I installed the murmur server with 

```
sudo apt-get install mumble-server
```

and then configured it with 

```
sudo dpkg-reconfigure mumble-server
```

and it starts. Upon rebooting, the server does not appear to be running. I am able to start it with 

```

murmurd

```

but the server doesn't have my custom root name and appears different. Any help is much appreciated.


Edit:

It seems to be caused by this:

```

Failed initialization: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'

```

---

