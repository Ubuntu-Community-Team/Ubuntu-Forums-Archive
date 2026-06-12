---
title: "Ubuntu 15.10 installation of lib_mysqludf_sys Error about missing libmysqlclient15-de"
date: 2016-03-20
forum: Server Platforms
---

### Post by jimspiti on 2016-03-20
Hi

I am using Ubuntu 15.10 64bit and i have trouble installing the mysql udf ([https://github.com/mysqludf/lib_mysqludf_sys](https://github.com/mysqludf/lib_mysqludf_sys)). 


Here's what I'm getting:

```
/usr/lib/mysql/plugin# ./install.sh
Compiling the MySQL UDF
./install.sh: line 23: make: command not found
ERROR: You need libmysqlclient development software installed
to be able to compile this UDF, on Debian/Ubuntu just run:
apt-get install libmysqlclient15-dev

```

apt-get install libmysqlclient15-dev results:

```
E: Unable to locate package libmysqlclient15-dev 
```

But i have already install the libmysqlclient-dev :

```
libmysqlclient-dev is already the newest version.
```

Searching on the net i just edit also the makefile to:

```
LIBDIR=/usr/lib/mysql/plugin
gcc -fPIC -Wall -m64 -I/usr/include/mysql -I. -shared lib_mysqludf_sys.c -o $(LIBDIR)/lib_mysqludf_sys.so
```

But there is no way to install it :(

Any help please?

---

### Post by nerdtron on 2016-03-21
I'm not sure why you want to installa software outside of the repository, but here I see some errors:

to correct this "line 23: make: command not found", you should install the build-essential packages since you are compiling the source code manually:
```
sudo apt-get install build-essential 
```

then, the package libmysqlclient-dev is not the same as libmysqlclient15-dev since they technically have different package names. I'm not sure how to correct this. Maybe the github repository have the package libmysqlclient15-dev?

---

### Post by jimspiti on 2016-03-21
Thanks nerdtron for your reply....

Doesn't work :(

> Compiling the MySQL UDF
Makefile:9: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
ERROR: You need libmysqlclient development software installed
to be able to compile this UDF, on Debian/Ubuntu just run:
apt-get install libmysqlclient15-dev


root@ubuntu-1gb-ams3-01:/usr/lib/mysql/plugin# apt-get install libmysqlclient15-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libmysqlclient15-dev


---

